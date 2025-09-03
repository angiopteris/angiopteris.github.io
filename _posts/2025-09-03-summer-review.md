layout: post
title: Summer 2025 AI Review — Text & Agents
tags: \[AI, Summer2025, LLM, Agents, RAG, Enterprise, Robotics, Security]
-------------------------------------------------------------------------

## TL;DR (Text & Agents first)

* **Frontier models & architecture**: brief highlights on **ChatGPT-5**, Google’s **“banana” models**, and the **HRM** (Hierarchical/Hybrid Reasoning/Memory) method for model architecture—key drivers behind stronger multi-step reasoning, longer context, and tool-use.
* **Agentic workflows (enterprise)**: repo-scale coding agents (OpenHands), governed RAG (observability, hybrid search, attribution), and eval harnesses shift focus from raw accuracy to latency/cost/deflection and human acceptance.
* **Local-first stacks**: Ollama desktop + Open WebUI + vLLM for on-prem; open-weight coder/thinking models (e.g., Qwen3 variants) viable on consumer GPUs.
* **Document intelligence**: Docling + docTR + Unstructured → clean chunks → long-context LLM; measurable gains in summarization, policy extraction, and compliance QA.
* **Security & safety**: sandbox tools, rate limits, allowlists, and audit trails for agents; prompt-injection hardening becomes table stakes.
* **Vision/audio (quick hits)**: FLUX for edits/control, Wan/HunyuanVideo for T2V/I2V (FramePack for longer clips); faster-whisper + XTTS-v2/OpenVoice V2 for ASR/TTS.

---

## Demo: Google “banana” model (video)

<video controls>
  <source src="https://storage.googleapis.com/gweb-uniblog-publish-prod/original_videos/ImageEditingGemini_Inline_XZuiDzE.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

---

## Text & Agents: practical notes

* **Coding & repos**: multi-file refactor and test-repair improved; pair Ghidra headless (for binaries) or static analyzers (for code) with a *Coder/Thinking* LLM for hypotheses and scripting.
* **RAG patterns**: hybrid lexical+vector, domain chunking, and per-answer tracing. Track cost/latency per query; cache aggressively; prefer small task-tuned models for high-QPS endpoints.
* **Agent guardrails**: capability scoping (least privilege), filesystem/network sandboxes, tool outcome validation, and structured logs for replay.

---

## Minimal stacks

* **Docs** → docTR (OCR) → Docling/Unstructured (structure) → RAG store → long-context LLM (Qwen3\*)
* **Code** → repo graph + tests → planning agent (OpenHands) → human-in-the-loop PRs
* **ChatOps** → retrieval tools + function calling → policy-aware agent actions

---

## Repos & links

* OpenHands: [https://github.com/All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands)
* Ollama desktop: [https://ollama.com/blog/desktop-app](https://ollama.com/blog/desktop-app)
* Qwen3: [https://github.com/QwenLM/Qwen3](https://github.com/QwenLM/Qwen3)
* Open WebUI: [https://github.com/open-webui/open-webui](https://github.com/open-webui/open-webui)
* Docling: [https://github.com/DS4SD/docling](https://github.com/DS4SD/docling) • docTR: [https://github.com/mindee/doctr](https://github.com/mindee/doctr) • Unstructured: [https://github.com/Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured)