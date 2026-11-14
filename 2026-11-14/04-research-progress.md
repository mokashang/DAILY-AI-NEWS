# Research Progress — 2026-11-14

The last 30 days leaned heavily on three threads: **AI-assisted mathematics crossing from benchmarks into (contested) open-problem claims**, **robotics foundation models going open-weight and multi-embodiment**, and a new wave of **RL-for-reasoning work that treats training infrastructure — not model size — as the frontier**. For a job hunter, each of these points at concrete hiring motions: proof-verifier engineers, VLA fine-tuners, and RL-systems people.

Tags: `#arxiv #research #agents #robotics #rl #math #memory #interpretability`

---

## 1. OpenAI claims AI-generated proofs in math, CS, and physics (announcement, Oct 26, 2026) {#1-openai-proofs}

**What they did:** OpenAI said its models produced **three novel research artifacts** — a **disproof of the Exponential Time Hypothesis (verified in Lean)**, results in harmonic analysis, and a claimed proof related to **Yang–Mills existence** — framed as "raw research data" rather than peer-reviewed results.

**Key result:** The **ETH disproof** is the most concrete: a Lean-checkable artifact that, if it survives review, would overturn one of the pillars of fine-grained complexity. The **Yang–Mills claim** is being openly contested on physics blogs (4gravitons, Nov 6), and OpenAI has **not** released the full manuscripts yet; treat as a provocation, not a settled result.

**Sources:**
- [OpenAI — First proof submissions](https://openai.com/index/first-proof-submissions/) `[primary]`
- [OpenAI — Research acceleration: view inside](https://openai.com/index/research-acceleration-view-inside-openai/) `[primary]`
- [Unite.ai — OpenAI says its models produced three proofs](https://www.unite.ai/openai-says-its-models-produced-three-proofs-in-math-cs-and-physics/) `[analysis]`
- [LetsDataScience — OpenAI claims Yang–Mills / ETH refutation](https://letsdatascience.com/news/openai-claims-proofs-of-yang-mills-existence-and-eth-refutat-3ded6200) `[analysis]`

### Why it matters to you

- **Job lens:** **Formal-methods talent (Lean, Coq, Isabelle) just became the scarcest complement to frontier LLMs.** "LLM + proof assistant" is a real job family now inside OpenAI, DeepMind, and Harmonic. A public Lean tactic library or lean4 translation project is résumé-worthy today.
- **Startup lens:** The **verified-artifact pattern — model proposes, verifier accepts — is the template every "AI scientist" startup is now chasing.** Domain-specific verifiers (circuits, cryptography, drug safety) are the moat, not the model.
- **Insight:** **Watch the review cycle, not the announcement.** The ETH story will be decided by whether the Lean proof reduces to known tactics or introduces genuinely new combinatorial structure.

---

## 2. Runway Praxis-1 — video pretraining → robot control (Sep–Oct 2026, open weights) {#2-praxis-1}

**What they did:** Runway shipped a **27B-parameter MoE diffusion transformer** that predicts **video and robot actions jointly**, bootstrapped from the same video pretraining as their generative video models, then adapted to multiple robot bodies with **LoRA**.

**Key result:** **46.2% success across 1,200 episodes on NVIDIA's RoboLab-120** (self-reported #1), vs. **42.9% for FLUX 3 Action, 36.8% for Cosmos3 Nano, 28.0% for π0.5**. **Open weights under Apache 2.0** on Hugging Face — unusual for a frontier VLA.

**Sources:**
- [Runway — Introducing Praxis-1](https://runway.com/research/introducing-praxis-1) `[primary]`
- [Runway — Praxis-1 video pretraining to robot control](https://runway.com/research/praxis-1-video-pretraining-to-robot-control) `[primary]`
- [Runway — Praxis-1 now available](https://runway.com/news/praxis-1-is-now-available) `[primary]`
- [The Robot Report — Runway introduces Praxis-1](https://www.therobotreport.com/runway-introduces-praxis-1-world-action-model-robotics/) `[analysis]`

### Why it matters to you

- **Job lens:** **VLA fine-tuning (LoRA on embodiment-specific demos) is now a hireable skill** at any robotics shop that can't train a 27B model from scratch — which is nearly all of them.
- **Startup lens:** Open weights + LoRA adaptation **collapses the "do we train our own model?" question** for robotics startups. The defensible layer moves to **data-collection rigs and eval harnesses**.
- **Insight:** **A video-generation company shipping a competitive VLA is the clearest sign yet that world-model pretraining is the dominant paradigm** — pixels in, actions out, with the same transformer in the middle.

---

## 3. NVIDIA GR00T 2 — foundation world-action models (whitepaper, Nov 2026) {#3-gr00t-2}

**What they did:** NVIDIA released the **GR00T 2 whitepaper** describing a next-gen foundation model that **predicts future visual observations alongside actions** (a "world-action model"), with code slated for **December**.

**Key result:** Architectural pitch: joint video + action prediction gives better generalization and dexterity than action-only VLAs. GR00T 2 is positioned as the reference open stack for humanoid + manipulator training. Numbers vs. Praxis-1 and π0.5 will be **the comparison to watch** when code ships.

**Sources:**
- [NVIDIA — GR00T 2 project page](https://research.nvidia.com/labs/gear/gr00t-2) `[primary]`
- [NVIDIA — GR00T 2 whitepaper (PDF)](https://research.nvidia.com/labs/gear/gr00t-2/assets/gr00t2_whitepaper.pdf) `[primary]`

### Why it matters to you

- **Job lens:** NVIDIA **GEAR** and **Isaac** teams are hiring around this stack; **"sim-to-real with foundation VLAs"** is the exact phrase to put on a résumé.
- **Startup lens:** If you're building a humanoid or warehouse manipulator, the choice is now **GR00T 2 vs. Praxis-1 vs. π-series** — picking one in advance of GR00T 2's code release is a real strategic bet.
- **Insight:** The convergence on **"predict video + action jointly"** across NVIDIA, Runway, and DeepMind's Gemini Robotics is **not a coincidence** — it's the field agreeing on the loss function for embodied foundation models.

---

## 4. MiMo-V2.6 — RL for self-improvement in large foundation models (arXiv 2610.11959, Oct 8, 2026) {#4-mimo-v26}

**What they did:** Xiaomi's **MiMo** team **open-sourced the full stack** — training dynamics, RL environments, and a scaled-RL framework — for pushing foundation models toward **self-improvement via reinforcement learning**.

**Key result:** The paper positions **RL (not supervised scaling) as "the central training paradigm"** for frontier models, and backs that with **reproducible environments + training logs** — a notable departure from the usual closed-RL recipes at the frontier labs.

**Sources:**
- [arXiv 2610.11959 (papers.cool)](https://papers.cool/arxiv/2610.11959) `[primary]`
- [RL Frontier Digest](https://nbot.ai/curator/s89vt7es/highlights/881db7e1-e495-4e94-8509-9e43884916b6) `[analysis]`

### Why it matters to you

- **Job lens:** **RL engineers who can run GRPO-style pipelines at scale remain scarce**; open artifacts like this are the **fastest on-ramp to interviews** at Anthropic, DeepMind, xAI, and the Chinese labs.
- **Startup lens:** **Verifier design is where the margin lives** — MiMo publishes the environments, which means your startup's moat is the **task distribution + reward shaping**, not the RL algorithm.
- **Insight:** **"Scaled RL + self-improvement" has quietly replaced "scaled pretraining" as the loudest hypothesis for the next capability jump.** Expect NeurIPS 2026 to be dominated by variants of this.

---

## 5. Long-Lived Agent Memory benchmark (arXiv 2611.05450, Nov 3, 2026) {#5-long-lived-agents}

**What they did:** Huang et al. introduce a **benchmark for experience lifecycles in evolving environments** — testing whether agents can both **selectively maintain** and **effectively use** long-term memory over many sessions, rather than treating memory as a static vector store.

**Key result:** Even when the correct experience is recorded, **agents routinely fail to retrieve or apply it** — isolating "selective maintenance" and "effective use" as **separate, under-measured failure modes**. The benchmark is the first of its kind to decouple those axes.

**Sources:**
- [arXiv 2611.05450 (papers.cool)](https://papers.cool/arxiv/2611.05450) `[primary]`
- [Memory in the Age of AI Agents (survey context)](https://arxiviq.substack.com/p/memory-in-the-age-of-ai-agents) `[analysis]`

### Why it matters to you

- **Job lens:** **"Agent memory engineer" is becoming its own role** at Cognition, Adept, and the agentic-SaaS wave — this benchmark gives you a concrete framework to talk about in interviews.
- **Startup lens:** Every production agent startup is bolting on memory layers (Mem0, Letta, Zep); a benchmark that separates **write-side from read-side failure modes** gives founders a real eval instead of vibes.
- **Insight:** **Memory is turning into the next alignment-shaped problem** — easy to add, hard to evaluate, and likely to be where agents quietly regress in production.

---

## 6. MRTPO — Multi-Reward Token-level Policy Optimization (arXiv 2610.21439, Oct 15, 2026) {#6-mrtpo}

**What they did:** A new RL method for training language models against **several verifiable rewards simultaneously**, assigning each reward's advantage only to the tokens the **corresponding verifier actually inspects** — a per-token credit-assignment fix for multi-objective RL.

**Key result:** Faster convergence and higher final performance on **text-to-SQL, multi-constraint instruction following, and tool calling** vs. standard GRPO-style baselines. The **token-level verifier-scoped credit assignment** is a clean, portable idea.

**Sources:**
- [arXiv 2610.21439 (papers.cool)](https://papers.cool/arxiv/2610.21439) `[primary]`
- [RL Research Navigator](https://nbot.ai/curator/2ejl49k5/highlights/2d027b0f-cc49-4cff-b3a2-38a4366df6d8) `[analysis]`

### Why it matters to you

- **Job lens:** If you've done any GRPO/DPO/PPO work, this is the kind of paper to **reproduce on a weekend and link from your résumé** — it's small enough to run on 1–2 GPUs with a toy verifier.
- **Startup lens:** Any product whose model needs to **satisfy multiple hard constraints at once** (compliance, formatting, tool-use correctness) can prototype on MRTPO instead of hacking reward blends by hand.
- **Insight:** **Multi-reward RL is where the SFT → RL → agent pipeline stops being a clean handoff and starts needing real algorithmic care.** Expect more papers like this through NeurIPS and ICLR 2027.
