---
layout: post
title: Revue IA - Été 2025
tags: [IA, Open-Source, LLM, Actualités]
---

Partage de quelques nouvelles sur les avancées concernant les modèles, agents, local-first, RAG et capacités multimodales. Cette mise à jour propose un tour d’horizon des derniers progrès — de ChatGPT-5 et GPT-OSS20b/120b aux modèles « banana » de Google, en passant par les frameworks open-weight comme Qwen3, ainsi que des agents de codage.

<!--more-->

## TLDR

* **Modèles & architecture** : Sortie de **ChatGPT-5**, les modèles **« banana »** de Google, et la méthode **HRM** (Hiérarchique/Hybride Raisonnement/Mémoire) pour l’architecture des modèles — moteurs clés d’un raisonnement multi-étapes plus fort, d’un contexte plus long et d’un meilleur usage des outils.
* **Workflows agentiques (entreprise)** : agents de codage à l’échelle dépôt (OpenHands), RAG (observabilité, recherche hybride, attribution), et bancs d’évaluation qui déplacent le focus de la précision brute vers la latence/le coût et l’acceptation humaine.
* **“local-first”** : Ollama desktop + Open WebUI + vLLM pour l’on-premise ; modèles open-weight de codage/raisonnement (p. ex. variantes de Qwen3) exploitables sur GPU grand public.
* **RAG documentaire** : Docling + docTR + Unstructured → segments propres → LLM à long contexte ; Plus simple d'utilisation (exemple ollama)
* **Sécurité & sûreté** : outils en sandbox, limites de débit, listes d’autorisations et traces d’audit pour les agents ; le durcissement contre l’injection de prompts devient incontournable.
* **Vision/audio (aperçus rapides)** : FLUX pour l’édition/contrôle, Wan/HunyuanVideo pour T2V/I2V (FramePack pour des clips plus longs) ; faster-whisper + XTTS-v2/OpenVoice V2 pour ASR/TTS.

---

# Leaderboard

![Leaderboard as of September 2025](/images/leaderboard_2025-09-03.png "Leaderboard")


## Génération de code

Le nouveau modèle de Open AI ChatGPT5 offre des capacités d'écriture de code plus complexe, plus long et plus cohérent.

Claude 4.1 est aussi capable de se genre de génération mais de moindre qualité.

## Les modèles commerciaux maintiennent un positionnement très compétitif

Encore plus fort que les versions "cheap" les version pro permettent souvent d'améliorer encore les performances. Certains multiplie les abonnements afin d'exploiter des capacités différentes (OpenAI, Ahtropic, etc.)

## Démo : modèle « banana » de Google

<video controls>
  <source src="https://storage.googleapis.com/gweb-uniblog-publish-prod/original_videos/ImageEditingGemini_Inline_XZuiDzE.mp4" type="video/mp4">
  Votre navigateur ne supporte pas la balise vidéo.
</video>

---

## Local-first

* **Docs** → docTR (OCR) → Docling/Unstructured (structure) → RAG store → LLM à long contexte (Qwen3\*)
* **Code** → graphe de dépôt + tests → agent de planification (OpenHands) → PRs avec humain dans la boucle
* **MCP** → outils de recherche + appels de fonctions → actions d’agent

---

## Repos & liens

* OpenHands : [https://github.com/All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands)  
* Ollama desktop : [https://ollama.com/blog/desktop-app](https://ollama.com/blog/desktop-app)  
* Qwen3 : [https://github.com/QwenLM/Qwen3](https://github.com/QwenLM/Qwen3)  
* Open WebUI : [https://github.com/open-webui/open-webui](https://github.com/open-webui/open-webui)  
* Docling : [https://github.com/DS4SD/docling](https://github.com/DS4SD/docling) • docTR : [https://github.com/mindee/doctr](https://github.com/mindee/doctr) • Unstructured : [https://github.com/Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured)
