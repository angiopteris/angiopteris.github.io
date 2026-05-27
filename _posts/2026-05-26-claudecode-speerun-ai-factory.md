---
layout: post
title: "Claude Code : Analyse + Speed-run AI Factory en 30 min"
tags: [Claude Code, Proxmox, DevOps, Agents, Sécurité]
---

Deux sujets techniques : petite analyse de Claude Code, puis montage d'une machine d'AI coding isolée en 30 minutes chrono — Proxmox, VM, réseau cloisonné, environnement prêt à coder ou l'inférence.

meetup https://www.meetup.com/grenoble-open-artificial-intelligence-meetup-group/events/314150636/?slug=grenoble-open-artificial-intelligence-meetup-group&eventId=314150636

<!--more-->

---

## 0. What's up OpenRouter ?

OpenRouter agrège le trafic de centaines de milliers de développeurs vers tous les grands modèles. C'est un des meilleurs baromètres réels de l'usage — pas des benchmarks marketing, du trafic API en production.

### Volume : x15 en un an

![Top Models — weekly usage OpenRouter](/images/OpenRouter-rankings-20260527.png)

En juin 2025, OpenRouter traitait environ **2T tokens par semaine**. Fin mai 2026 : **~30T**. Quinze fois plus en douze mois.

La croissance n'est pas linéaire. Elle s'accélère nettement à partir de **mars 2026**, ce qui coïncide avec la généralisation des agents de coding (Claude Code, Codex CLI, Cursor en mode agent). Les agents consomment des tokens en rafale — une session de travail peut en générer autant qu'un millier de conversations classiques. C'est eux qui tirent la courbe vers le haut.

### Parts de marché : la surprise DeepSeek

![Market Share — token share by model author OpenRouter](/images/OpenRouter-marketshare-20260527.png)

| Rang | Provider | Tokens | Part |
|------|----------|--------|------|
| 1 | **Anthropic** | 2,38T | 20,7% |
| 2 | **DeepSeek** | 2,28T | 19,8% |
| 3 | Google | 1,53T | 13,3% |
| 4 | Tencent | 1,14T | 9,9% |
| 5 | OpenAI | 1,1T | 9,5% |

Le signal global : l'open-weight a gagné la bataille du volume. Les modèles fermés restent leaders sur les tâches haute valeur (agents complexes, coding critique), mais le gros du trafic est parti vers des alternatives plus économiques pour le trafic à faible valeur ajoutée / mode éco.

---

## 1. Le leak de Claude Code — Le moteur de skills décortiqué

Le code source de Claude Code a fuité, puis Anthropic l'a rendu open-source. Ce qui est intéressant n'est pas le system prompt — c'est l'architecture du moteur de skills.

### La distinction fondamentale : skill ≠ tool

```
Tool call  →  exécuter une action maintenant     (Read, Edit, Bash…)
Skill call →  charger une procédure dans le contexte  (/review, /security-review…)
```

Une skill n'est pas un outil bas niveau. C'est un **prompt enrichi chargé dynamiquement**. Après chargement, Claude reprend la boucle normale et appelle ensuite les vrais tools si la procédure le demande.

### Le flux complet en 4 temps

**① Découverte — `loadSkillsDir.ts`**

Au démarrage, le loader lit les skills disponibles (managed, user, project, bundled, legacy). Chaque skill est un fichier `SKILL.md` avec un YAML qui contrôle son comportement :

```yaml
disable-model-invocation: false   # le modèle peut-il l'invoquer seul ?
userInvocable: true                # accessible via /slash ?
context: fork                      # exécution dans un sous-agent ?
agent: ...                         # quel sous-agent ?
effort: high                       # niveau d'effort transmis au modèle
```

Chaque `SKILL.md` devient une **commande de type `prompt`** — pas exécutée tout de suite, juste rendue disponible.

**② Filtre — `getSkillToolCommands()`**

Toutes les commandes ne sont pas accessibles au modèle. `getSkillToolCommands()` filtre :
- garde uniquement `type === "prompt"`
- exclut celles marquées `disableModelInvocation`
- inclut les sources `/skills`, bundled, legacy, plugin, MCP

Résultat : Claude voit une **liste courte et filtrée**, ~1 % de la fenêtre de contexte. Le contenu complet de chaque skill n'est chargé qu'à l'invocation — économie de contexte intentionnelle.

**③ Déclenchement — décision du modèle, pas un `if`**

L'activation d'une skill dépend de l'appel de `SkillTool` par le LLM : elle est soit impérative en utilisant `/slash`, soit déclenchée automatiquement si la skill est pertinente et disponible.

C'est une **contrainte bloquante** : si Claude reconnaît qu'une skill correspond, il doit émettre un `tool_call` vers `SkillTool` avant toute réponse.

**④ Exécution — deux chemins**

```
SkillTool.validateInput()
  normalise le nom → findCommand() → vérifie type + permissions
      ↓
  Permission check (deny → allow → auto-allow → ask)
      ↓
  Skill normale               Skill avec context: fork
       ↓                              ↓
processPromptSlashCommand()    executeForkedSkill()
       ↓                       (sous-agent séparé)
getPromptForCommand()
  remplace args + variables ${CLAUDE_SKILL_DIR}, ${CLAUDE_SESSION_ID}
  construit les messages finaux
       ↓
registerSkillHooks() + addInvokedSkill()
       ↓
return { newMessages, shouldQuery: true, allowedTools, command_permissions }
```

Le `shouldQuery: true` est la clé : la skill **ne répond pas directement**. Elle injecte de nouveaux messages/instructions et **relance la boucle modèle**. Claude est réinterrogé avec le contenu complet de la skill dans son contexte, puis appelle `Read`, `Edit`, `Bash`… selon les instructions reçues.

### Ce que ça implique concrètement

**`CLAUDE.md` = instruction de confiance prioritaire.** Le loader le place au-dessus du message utilisateur dans la hiérarchie. Mettez vos conventions, contraintes de sécurité et outils custom dedans.

**Les skills sont extensibles.** Un fichier `SKILL.md` dans `~/.claude/skills/` ou `.claude/skills/` du projet suffit pour créer un workflow custom invocable par le modèle ou par `/slash-command`.

**Le mode `fork` isole les sous-agents.** Pour les tâches risquées (audit sécurité, migrations), `context: fork` exécute la skill dans un contexte séparé — les erreurs ne polluent pas la conversation principale.

**Les permissions s'accumulent par skill.** Chaque skill peut étendre les `allowedTools` de la session via `contextModifier`. Un `/deploy` peut s'auto-autoriser `Bash` sans que ce soit autorisé globalement.

---

## 2. Speed-run — AI Factory en 30 minutes

Objectif : partir d'une machine nue avec Proxmox installé, arriver à une VM isolée réseau avec Claude Code opérationnel et un workflow git propre.

### Architecture cible

```
Machine physique (Proxmox)
└── VM Ubuntu 24.04
    ├── Réseau : bridge isolé + règles firewall
    ├── Claude Code CLI
    ├── Node.js / Python / Git
    └── Workspace cloné, CLAUDE.md configuré
```

L'isolation réseau protège la machine hôte et limite la surface d'attaque si un agent part exécuter quelque chose d'inattendu.

### Étape 1 — VM Proxmox (5 min)
Pour les curieux, le serveur:
Pour les disques https://diskprices.fr/ 
Disque principal - nvme FIKWOT FN955 2TB
NZXT H6 Flow | CC-H61FB-01 | - https://www.amazon.fr/dp/B0C89FCDFP
MSI B760 Gaming Plus - https://www.amazon.fr/dp/B0BZD3BMZL
CPU Intel® Core™ i5-12400F  - https://www.amazon.fr/dp/B09MDFH5HY
32GO DDR5
GPU - Leboncoin - RTX 3090 FE > (les FE ont un meilleur système de refroidissement)

1: Installation de proxmox:

Paramètres BIOS : 
UEFI
Primary Display = Integrated Graphics
Intel Virtualization Technology (VT-x) = Enabled
Intel VT-d = Enabled

Pour installer proxmox:
https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso

On utilise balena etcher https://etcher.balena.io/ pour flasher la clé usb.

On suit les étapes d'installation classiques, on choisit une IP, un mot de passe fort (on l'enregistre dans le gestionnaire de mots de passe), etc.
On se connecte sur l'UI avec l'user root

Dans l'UI on clique sur le serveur, on va dans "repositories" on désactive pve enterprise, on active pve no subscription: Add > pve-no-subscription

On va dans le node shell, 
apt update && apt upgrade -y


Si GPU,
nano /etc/default/grub  
on ajoute ou modifie la ligne GRUB_CMDLINE_LINUX_DEFAULT en utilisant:
GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on" dans /etc/default/grub
Cela permettra de passer le GPU à la VM

Si VM windows:
https://www.microsoft.com/fr-fr/software-download/windows11 - Télécharger l’image disque Windows 11 (ISO) pour les appareils x64

on télécharge les drivers windows pour proxmox selon la doc https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers
https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/?C=M;O=D

Lors de l'installation, à l'étape des drivers, on c

#### Configuration VM (QEMU)

| Paramètre | Valeur |
|-----------|--------|
| Memory | 25 GiB |
| Processors | 6 cores (1 socket) — type `host` |
| BIOS | OVMF (UEFI) |
| Display | VirtIO-GPU |
| Machine | pc-q35-10.0 |
| SCSI Controller | VirtIO SCSI single |

#### Stockage

| Disque | Options |
|--------|---------|
| Hard Disk (scsi0) | `iothread=1`, `size=500G` |
| EFI Disk | `efitype=4m`, `pre-enrolled-keys=1`, `size=1M` |
| TPM State | `version=v2.0`, `size=4M` |

#### Réseau

| Paramètre | Valeur |
|-----------|--------|
| Driver | `virtio` |
| Bridge | vnet isolé (SDN) |
| Firewall | activé |

#### PCI — GPU passthrough

| Paramètre | Valeur |
|-----------|--------|
| Device | `0000:01:00.0` |
| Mode | Raw Device |
| Primary GPU | Enabled |
| All Functions | Enabled |
| PCI-Express | Enabled |

### Étape 2 — Règles Firewall

Trois règles simples : bloquer le trafic sortant vers le LAN physique, autoriser uniquement le gateway du vnet.

| # | Type | Action | Destination | Log |
|---|------|--------|-------------|-----|
| 0 | out | DROP | 192.168.1.0/24 | debug |
| 1 | out | ACCEPT | 192.168.1.254/32 (vnet gw) | — |
| 2 | in | ACCEPT | 192.168.1.254/32 (vnet gw) | — |

#### SDN — VNet & Zone

| VNet ID | Zone | Type |
|---------|------|------|
| `vnetusf` | unsafe | simple |

DHCP range : `10.10.10.10` → `10.10.10.100`


```bash
# Créer la VM via CLI (ou UI)
qm create 200 --name ai-factory --memory 8192 --cores 4 \
  --net0 virtio,bridge=vmbr1 \
  --cdrom local:iso/ubuntu-24.04-server.iso \
  --scsi0 local-lvm:32
```

### Étape 3 — Setup environnement (10 min)

Dans la VM Ubuntu ou Windows fraîchement installée :

On va dans la console, on a accès à l'écran de la machine
On backup ou snapshot la VM maintenant (avant ou après programme tiers)

Installation programme tiers (quelques idées)

Parsec / chromeRemoteDesktop ou autre, une fois installée ce sera plus pratique d'utiliser le remote desktop plutot que la console proxmox.
vscode + extension cline
Windirstat

Claude code & on se connecte à claude avec cline

Pinokio (génération locale par IA seulement si GPU, si pas de GPU > utiliser le service vastai c'est bien et pas cher pour une VM GPUfié à distance)

### Étape 4 — Git workflow (5 min)
On ajoute la clé ssh pour github ou on la crée

ssh-keygen -t ed25519 > on la place dans ~/.ssh/
On ajoute la clé dans github 
...

On fork un répertoire,
On clone notre répertoire forké localement
On ouvre le dossier avec vscode
On lance claude, il fait des diffs
On utilise le commit "cline" pour analyser les diffs avec le repo distant
on commit/push/sync/etc...

Merci pour la lecture.
##### Happy 2026 #######

Auteur: Lucas Boulé