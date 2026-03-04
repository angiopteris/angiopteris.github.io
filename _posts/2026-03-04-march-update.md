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

