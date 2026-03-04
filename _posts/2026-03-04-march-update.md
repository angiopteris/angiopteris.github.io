---
layout: post
title: Récap' IA – Mars 2026
tags: [IA, Qwen, Agents, Multimodal, Actualités]
---

Une actualité chargée avec de nombreuses avancées : éditeurs d'images physiques, avatars VR temps réel, génération de polices vectorielles, modèles Qwen optimisés, robots humanoïdes, et bien plus.

<!--more-->


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

Résumé AI-search https://www.youtube.com/watch?v=8grIT-xK50M
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


<!--more-->

---

BLEND: 

## 🟢 Open Source Models & Frameworks

### Large Language Models (LLM) & Multimodal
- **Qwen 3.5 (Alibaba)**: Multimodal 397B MoE (17B active) featuring a 1M token context window. Excellent at reasoning, coding, document/video understanding, capable of coding 3D games and solving visual Sudoku puzzles natively.
- **Qwen 3 Coder Next**: 80B MoE (3B active) agentic coding model capable of autonomous tool usage and self-correction. Compatible with OpenClaw.
- **MiniMax M2.5**: High performance reasoning/coding model costing just $1/hr for 100 tokens/s. Capable of deep Excel analysis and complex document creations natively.
- **MiniCPM-o 4.5**: Omnimodal 9B parameter model (23.4GB) natively supporting text, audio, image, and video in/out. Excels at live streaming voice interactions and analyzing visual puzzles.
- **GLM-5**: Highly capable reasoning agent matching top closed models on Humanities Last Exam and ARC AGI benchmarks.
- **GLM OCR (Zhipu)**: 2.6GB OCR model cleanly parsing complex tables, math formulas, and handwritten notes—significantly outperforming Gemini and GPT.
- **Step 3.5 Flash**: 196B MoE (11B active) open weights model. Very fast (100-300 t/s), leading benchmarks in reasoning and deep agentic research tasks.
- **Intern S1 Pro**: 1T MoE (22B active) specializing in advanced scientific reasoning (chemistry, life science). 
- **Nan Beige 4.13B**: Ultra-small 3B model achieving state-of-the-art benchmark scores for its size, capable of 500+ round agentic tool executions without external search inputs.
- **Tiny AA (Cohere Labs)**: 3.35B parameter base model supporting 70+ languages. Highly efficient and fast.

### Audio, Speech & Music
- **AEP 1.5**: State-of-the-art music generator requiring <4GB VRAM. Fast (10s generation on a RTX 3090). Supports "repainting" parts of a track and high-grade cover generation.
- **Moss TTS**: Production-grade family of TTS models (8B & 1.7B). High quality voice cloning, long expressive conversational dialogs, and real-time low-latency inference.
- **Kitten TTS**: Ultra-lightweight TTS models (14M, 40M, 80M parameters) under 25MB, capable of running in real-time on CPUs or mobile phones.
- **Audio X**: Unified model generating audio from text, images, or videos. Can also perform audio inpainting, track extension, and sound effect generation.
- **Soul X Singer**: Voice cloner requiring <3s of reference voice plus a melody hum to create sung lyrics (<3GB VRAM).
- **Just Dub It**: Video dubber applying multi-language localized lip-sync based on the LTX2 architecture.
- **Mo TTS**: Minimalist 100M parameter TTS (244MB) optimized for expressive English and Japanese readings.

### Image, Video & 3D
- **Qwen Image 2**: 7B unified image omni-model. Generates complex topographical and diagrammatic inputs precisely at 2K resolution in seconds, with built-in editing.
- **Anchorwave**: Open source interactive video world generator based on CogVideo X enabling WASD 3D world navigation with persistent memory.
- **Louv**: Generates ultra high-res, highly detailed 2K & 4K photorealistic videos.
- **Monarch RT**: Real-time video generation running at 16 FPS on a single RTX 5090 using specialized architecture.
- **OmniMat Zero**: Removes video objects along with their specific reflections and shadows, capable of exporting transparent background layers.
- **Fast VMT**: Transfers camera flow and object motion coordinates from one video stream to a newly generated scene.
- **FreeFuse**: Framework allowing combination of dozens of LoRAs without interference or facial distortion bleeding.
- **Context Forcing**: Workflow enabling 2-10x longer sustained video generations with minimal inconsistencies.
- **Skin Tokens**: Estimates rig skeletons for 3D models (characters and animals) to prep them for immediate animation.
- **Zuna Thought to Text**: 380M parameter BCI foundation model designed to denoise and reconstruct messy EEG brainwave signals.
- **Veto Pix**: Edits images by converting layers to editable vector shapes, allowing the repositioning, reshaping, or deletion of specific elements.

---

## 🔴 Proprietary Models & Integrations

### General Purpose & Code Agents
- **Claude Opus 4.6 (Anthropic)**: The newest and smartest generalized model hitting 68.8% on ARC AGI 2, indicating massive progress in learning unseen problem patterns. Very strong, but slower and expensive.
- **GPT-5.3 Codex (OpenAI)**: Self-improving agentic coding model testing highly in OS World mastery. The new "Codex Spark" variant offers 1,000+ token/s for near-instant execution tasks. 
- **Gemini 3 Deep Think (Google)**: Research-tailored variant crushing ARC AGI 2, Humanity's Last Exam, and achieving a 3455 ELO on Codeforces.
- **Gemini 3.1 Pro (Google)**: Rapid iterative update leading industry benchmarks multimodally.
- **Seed 2.0 (ByteDance)**: LLM specialized in visual reasoning and long horizon sequential automation.
- **Pico Claw**: Highly optimized OpenClaw alternative requiring only 10MB of memory and booting in 1 second.

### Vision, Video & Music
- **Seed Dance 2.0 / Alive / FS Video (ByteDance)**: Dominant suite of video tools. 'Alive' natively supports text/audio/img-to-video with coherent sound/lip-sync, and 'FS Video' yields 5-second 720p generations in 18s (tested on H100s).
- **Ray Pie (Luma AI)**: 1080p native video generator offering faster and more consistent rendering with deep prompt-intent understanding.
- **3D Move (Kling)**: Video-to-video processing mapping reference character movement onto new subjects while offering real-time camera manipulation (zooming, orbiting).
- **Edit Yourself**: Talking-head clip editor adjusting lip sync to seamlessly add or remove spoken sentences without hard cuts.
- **Paper Banana (Google)**: Multi-agent system rendering raw data frames into professional, styled academic diagrams accurately.
- **Interact Avatar (Tencent)**: Generates 2D avatars capable of interacting physically with props within the video element based on strict prompt timings.
- **Duo Gen (Nvidia)**: Sequential multimodal generation chaining step-by-step images coherently from a single prompt.
- **Text-to-4D**: Prompt to dynamic 3D scenes producing environmental simulations directly editable in Blender.
- **LIIA 3 (Google)**: Free multimodal music generator integrated straight into the Gemini workflow.
- **DeepGen 1.0**: High-fidelity multimodal image generation and editing suite.

---

## 🦾 Robotics & Next-Gen Hardware

### Agility & Swarm
- **Unitree G1**: Demonstrated extreme acrobatics (multi-meter flips, nunchuck operations) and durability (130,000+ steps in -47°C environments).
- **Husky Framework**: Taught robots advanced outdoor skateboarding maneuvers through complex physical stabilization learning.
- **L7 (Robot Era)** & **AGI Bot**: Bringing human flexibility with spinning kicks and high-torque sword dancing while maintaining center of mass.
- **Titan-01 (Westlake Robotics)**: Tele-operated bipeds mapped natively through VR/haptic rigs for physical-risk substitution tasks.
- **Inter Prior**: Physics-driven virtual matrix teaching robots object interactions logically before physical world deployments.

### Chips
- **Talis HC1 AI Chip**: "Software-in-silicon". A hardware paradigm hard-coding Llama 3.1 natively into transistors without software overhead. Emitting 17,000 tokens per second (40x faster than Nvidia B200) whilst drawing 10x less power. The future of instant, local inference.
https://www.forbes.com/sites/karlfreund/2026/02/19/taalas-launches-hardcore-chip-with-insane-ai-inference-performance/

