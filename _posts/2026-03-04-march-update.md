---
layout: post
title: Récap' IA – Mars 2026
tags: [IA, Qwen, Agents, Multimodal, Actualités]
---

Une semaine chargée avec de nombreuses avancées : éditeurs d'images physiques, avatars VR temps réel, génération de polices vectorielles, modèles Qwen optimisés, robots humanoïdes, et bien plus.

<!--more-->

## VBVR — Raisonnement Vidéo avec WAN2.2

**VBVR** (Very Big Video Reasoning) est un framework ajouté au générateur vidéo WAN2.2 qui permet de raisonner sur des vidéos. Le framework est capable de résoudre des puzzles visuels comme identifier des caractères, formes ou animaux, simuler des phénomènes physiques (équilibre de fluides, rotation 3D) et suivre des instructions séquentielles complexes.

Le modèle atteint un score de **68,5%** sur les benchmarks de raisonnement visuel, surpassant Sora 2 et V3.1 (souvent <50%). Le framework et le dataset (310 GB, 1M d'exemples) sont open-source.

---

## TTT-LRM — Reconstruction 3D par Test-Time Training

**TTT-LRM** (Test Time Training for Long-context Auto-regressive 3D Reconstruction) génère des modèles 3D réalistes à partir de photos. Il utilise l'entraînement "test-time" pour apprendre rapidement des photos d'entrée et capture des détails subtils comme les textes, textures et fils.

Le modèle fait **moins de 4 GB**, le rendant compatible avec la plupart des GPU grand public. Le code est disponible sur GitHub.

---

## DreamID Omni — Génération Vidéo Multi-Inputs par ByteDance

Nouveau générateur vidéo acceptant **texte + image + voix** en entrée. Il permet la génération de deepfakes réalistes avec voix de référence, le support de **multiples personnages** avec voix synchronisées et l'édition de vidéos existantes (remplacement visage + voix).

L'open-source est prévu pour mars 2026.

---

## Quiver Arrow — Génération SVG State-of-the-Art

Modèle spécialisé dans la génération de **graphiques vectoriels (SVG)**. Il permet la création de logos, icônes et designs complexes avec une résolution infinie (mathématique, non pixel).

Le service est actuellement gratuit (20 SVG gratuits) et surpasse les modèles généralistes comme GPT-5, Gemini et Claude pour les SVG.

---

## Solaris — Gameplay Minecraft Multi-Joueurs

Générateur de vidéos Minecraft en **perspective simultanée de deux joueurs**. L'innovation majeure est la compréhension des perspectives des deux joueurs dans la même scène.

Le dataset comprend **6,32 millions de frames** par joueur. Le modèle fait **29,2 GB** (nécessite GPU haut de gamme). Les applications incluent les robots autonomes multiples et jeux interactifs.

---

## VideoMT — Segmentation Vidéo par Vision Transformer

Un modèle lightweight qui transforme un vision transformer en modèle de **segmentation vidéo**. Il atteint **160 frames/seconde**, soit 5-10x plus rapide que les approches existantes.

Le modèle utilise une astuce de "query propagation" pour suivre les objets. Le code open-source est disponible.

---

## VecGlypher — Création de Polices Vectorielles

Générateur de **glyphes et polices vectorielles** à partir de texte ou d'image. Il crée tous les caractères d'une police à partir d'un aperçu et génère les contours vectoriels.

Le modèle surpasse GPT-5, Gemini et Claude en qualité de génération. Il est open-source avec des instructions d'installation disponibles.

---

## Unitree Go2 & Agibot G2 — Démonstrations Robotiques

**Unitree Go2** est un robot quadrupède avec une vitesse max de **5 m/s** et une charge utile de **105 kg** (6x son poids). Son design IP54 est résistant à l'eau, idéal pour terrains difficiles et sauvetage.

**Agibot G2** est un robot industriel avec **26° de liberté** (corps), **5°** (taille/jambes) et **19°** (mains). Il offre une précision sub-millimétrique pour l'assemblage, équipé de la puce Nvidia Jetson T5000 (**2000+ TFLOPS**) et d'une batterie hot-swap avec recharge autonome.

---

## LavaSR — Enhanceur Audio Ultra-Léger

Améliore la qualité audio avec un modèle de seulement **50 MB**. Il atteint **5000x temps réel** sur GPU et **60x** sur CPU, fonctionnant même sur mobile.

Disponible sur Hugging Face et Google Colab.

---

## Qwen 3.5 — Variantes Grand Public

Alibaba publie des versions plus petites de Qwen 3.5 :

| Modèle | Taille | VRAM requis |
|--------|--------|-------------|
| Qwen 3.5-2B | 2B paramètres | ~2 GB |
| Qwen 3.5-35B | 35B paramètres | ~35 GB |
| Qwen 3.5-27B (quantized) | 27B paramètres | **10-12 GB** |

Les performances sont comparables à GPT-5 Mini et Claude Sonnet. La version 27B quantifiée ne nécessite que **10 GB** de VRAM.

---

## EgoScale — Apprentissage Robot par Vidéo (Nvidia)

Système permettant aux robots d'apprendre des tâches complexes en **regardant des vidéos** d'humains. Le dataset comprend **20 000 heures** de vidéos en perspective humaine couvrant des tâches comme plier des vêtements, utiliser des outils, la cuisine et le jardinage.

Le modèle "Vision-Langage-Action" est combiné. GitHub : coming soon.

---

## Doc-to-LoRA & Text-to-LoRA — Mémoire Persistante

Deux méthodes pour compresser documents et instructions dans des adaptateurs LoRA.

**Doc-to-LoRA** encode des documents entiers (même avec images) dans un LoRA. Le modèle peut répondre sans relire le document et fonctionne avec des documents plus longs que la fenêtre de contexte. Marche aussi avec les images même avec un modèle text-only.

**Text-to-LoRA** compile des instructions complexes en LoRA, permettant une mémoire persistante des styles, formats et tâches.

---

## PhysicEdit — Édition d'Images Physiquement Précise

Éditeur d'images comprenant les **phénomènes physiques**. Il gère la réfraction correcte (paille dans verre d'eau), les effondrements, étirements, décomposition, la congélation, condensation et fusion.

Le modèle surpasse Nano Banana en précision physique et est basé sur Qwen ImageEdit 259.

---

## Generated Reality — Vidéos Interactives VR

Génère des vidéos interactives basées sur les **mouvements de tête et de mains**. Un casque VR enregistre les mouvements et un texte prompt génère l'environnement.

Actuellement : **11 FPS**, qualité perfectible. Code : coming soon.

---

## MMHNet — Effets Sonores par Sony (Audio pour Vidéo)

IA de Sony générant des **effets sonores pour vidéos** jusqu'à 5 minutes. **MMHNet** (Multimodal Hierarchical Networks) combine approche hiérarchique + architecture Mamba pour un audio synchronisé avec les actions vidéo.

Code : coming soon.

---

## Sarah — Avatar VR Temps Réel

Générateur d'**avatars complets en réalité virtuelle** avec interaction temps réel. Les mouvements corporels sont dynamiques et naturels, avec un contact visuel ajustable qui répond aux mouvements de l'utilisateur.

Dataset open-source, modèle : à venir.

---

## LoraWeb — Éditeur d'Images par Nvidia

Éditeur unique nécessitant **trois images** en entrée : image "avant" exemple, image "après" exemple et image à transformer.

Le transfert de style est précis grâce au framework modulaire avec LoRAs. Open-source sur GitHub.

---

## TLDR — Qwen3.5 : Vers des Agents Multimodaux Natifs

**Qwen3.5-397B-A17B** est le premier modèle open-weight de la série Qwen3.5, un modèle natif vision-langage qui excelle en raisonnement, codage, capacités d'agent et compréhension multimodale.

L'architecture hybride compte 397 milliards de paramètres totaux, mais seulement 17 milliards activés par passage — combinant attention linéaire (Gated Delta Networks) et sparse mixture-of-experts pour une efficacité remarquable. La fenêtre de contexte est de 256-1M tokens.

Les performances sont compétitives, rivalisant avec GPT-4.5, Claude 4.5 Opus et Gemini-3 Pro sur de nombreux benchmarks.

---

## TLDR — Comparaison Qwen3.5-397B-A17B vs Claude Sonnet 4.6

| Caractéristique | Qwen3.5-397B-A17B | Claude Sonnet 4.6 |
|-----------------|-------------------|-------------------|
| **Contexte** | 262K tokens | 1M tokens |
| **Prix (input/output)** | $0,39 / $2,34 par M tokens | $3 / $15 par M tokens |
| **Latence (p50)** | 1,80s | 1,54s |
| **Throughput (p50)** | 48 tok/s | 40 tok/s |
| **Modalités input** | texte, image, vidéo | texte, image |
| **Max output tokens** | 66K | 128K |
| **Providers** | 5 | 3 |

**Avantages Qwen3.5** :
- **7,7x moins cher** en input, **6,4x moins cher** en output
- **Débit supérieur** (48 vs 40 tok/s)
- **Support vidéo natif** en input
- **Open-weight** : peut être auto-hébergé

**Avantages Claude Sonnet 4.6** :
- **Contexte 4x plus large** (1M vs 262K tokens)
- **Latence légèrement inférieure** (1,54s vs 1,80s)
- **Output tokens max plus élevés** (128K vs 66K)
- **Maturité écosystème** : plus de providers établis

---

*Sources : [Qwen Blog](https://qwen.ai/blog?id=qwen3.5) | [Artificial Analysis](https://artificialanalysis.ai)*