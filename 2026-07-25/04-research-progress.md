# Research Progress — 2026-07-25

Two clean themes this fortnight: **long-horizon agent evals got a lot harder** (LHTB) and **RL post-training got a real cost accounting** (two solid papers). Plus **Anthropic Frontier Red Team + Andon Labs published Project Pilot** — an embodied drone benchmark that isolates *scene reconstruction* as the blocker for real-world autonomy. Treat this file as a scan of what a builder should care about; the SOURCES.md `Tier 2` list is the authoritative daily-feed rotation.

Tags: `#arxiv #benchmarks #agents #rl #post-training #interpretability #embodied #evals`

---

## 1. Long-Horizon-Terminal-Bench (LHTB) — the new hard-eval floor for coding agents {#1-lhtb}

**Paper:** *Long-Horizon-Terminal-Bench: A Benchmark for Long-Horizon Terminal Agents.* Zongxia Li et al. **arXiv:2607.08964** (2026-07-11). Project: [zli12321.github.io/LHTB](https://zli12321.github.io/LHTB/).

**Claim in one sentence:** 46 long-horizon terminal tasks (SWE, ML experiment reproduction, scientific computing, multimodal analysis) with **dense subtask-graded rewards** — where the strongest agent tested hits only **15.2% pass@1** at 0.95 partial credit and **10.9%** at full credit.

**The delta:**
- Task runs are large: **~9.9M tokens, ~231 episodes, ~85 min wall-clock per task on average**. Orders of magnitude beyond Terminal-Bench and SWE-bench Verified.
- **Dense per-subtask rewards** replace binary pass/fail — you can see *where* an agent falls off a cliff, and the reward signal is usable for RL, not just leaderboards.
- **9 task categories** including SWE, ML reproduction, scientific compute, interactive games, multimodal analysis.

**Sources:**
- [arXiv:2607.08964](https://arxiv.org/abs/2607.08964) `[primary]`
- [Hugging Face — Paper page](https://huggingface.co/papers/2607.08964) `[analysis]`
- [Project site — LHTB](https://zli12321.github.io/LHTB/) `[primary]`

### Why it matters to a builder

- **The right eval to point at when someone claims their coding agent "solves real work."** Frontier agents are in the low teens on hours-long tasks. Anyone marketing 90%+ agent success on real repos is measuring the wrong thing.
- **Dense subtask rewards** make LHTB usable as an **RL training signal**, not just a benchmark — expect open-weights teams to fine-tune against it within a quarter.
- **Capacity planning number:** ~10M tokens per task is a useful anchor for anyone building persistent multi-hour agent products. At Opus 5 rates that's ~$100 per successful task at high effort — real money that has to be modeled into product pricing.

---

## 2. Where Should RL Post-Training Compute Go? — a FLOP-accounting framework for GRPO {#2-rl-compute-allocation}

**Paper:** *Where Should RL Post-Training Compute Go? Model Size, Search, Learning, and Feedback.* Patrick Wilhelm, Odej Kao (TU Berlin). **arXiv:2607.13389** (2026-07-15).

**Claim in one sentence:** Introduces a **decomposed FLOP-accounting framework for GRPO** — separating **rollout/search**, **policy update**, and **reward-model evaluation** — and shows the optimal compute split is **conditional on model size, budget, reward type, and eval target.** No single recipe wins.

**The delta:**
- Prior work reports RL post-training as one lump-sum FLOP number; this decomposes it into **three trade-off axes** you can actually optimize.
- Empirical **"conditional allocation frontiers"** on LoRA-adapted Qwen2.5.
- Concrete guidance for: *"bigger policy vs longer training vs more rollouts vs stronger reward model"* under a fixed budget.

**Sources:**
- [arXiv:2607.13389](https://arxiv.org/abs/2607.13389) `[primary]`
- [arXiv HTML](https://arxiv.org/html/2607.13389) `[primary]`

### Why it matters to a builder

- If you're doing **GRPO-style RL post-training** in-house (fine-tuning Qwen, Llama, or DeepSeek base models with verifiable rewards), this is the first paper that gives you a **defensible way to argue for compute reallocation** — instead of just "add more GPUs."
- Pairs directly with **SLAI T-Rex** ([§5](#5-slai-t-rex)) — that team's efficiency win depends on making exactly these trade-offs correctly.

---

## 3. Understanding Reasoning from Pretraining to Post-Training (the chess paper) {#3-chess-scaling}

**Paper:** *Understanding Reasoning from Pretraining to Post-Training.* Group across NYU (Pavel's lab), Modal, UCLA, UIUC, Columbia. **arXiv:2607.16097** (~2026-07-17). Code: [github.com/pavelslab-nyu/pre2post-chess](https://github.com/pavelslab-nyu/pre2post-chess).

**Claim in one sentence:** Uses **chess as a controlled testbed** — pretrained models 5M–1B parameters on human games → SFT on tree-search traces → RL on puzzles — to derive a **joint pretraining-plus-RL scaling law** showing pretraining loss is a *predictive* signal for downstream RL gains.

**The delta:**
- RL post-training results are usually at one model scale; this maps returns to RL compute as a function of pretraining choices (size, data).
- **Verifiable environment** (puzzle solutions) removes reward-hacking confounds that muddy RLHF ablations.
- Provides a **mechanistic answer** to "what does RL actually do" — the paper decomposes behavior changes across the pipeline.

**Sources:**
- [arXiv:2607.16097](https://arxiv.org/abs/2607.16097) `[primary]`
- [alphaXiv — 2607.16097](https://www.alphaxiv.org/abs/2607.16097) `[analysis]`
- [GitHub — pre2post-chess](https://github.com/pavelslab-nyu/pre2post-chess) `[primary]`

### Why it matters to a builder

- Concrete evidence for the **"pretrain harder before you RL"** thesis. Teams choosing where to spend budget between base training and RL now have a scaling law to point at.
- If you're training **small models to reason** (agent controllers, verifiers, cheap sub-model policies), this argues you should **not skimp on the base**. Directly relevant if you're playing in the small-model-as-verifier space (which composes with Opus 5's effort toggle in [`03` §1](./03-practical-skills-and-tools.md#1-opus-5-effort)).

---

## 4. Project Pilot / Drone-Bench (Anthropic Frontier Red Team × Andon Labs) {#4-project-pilot}

**Release:** [Anthropic — Project Pilot](https://www.anthropic.com/research/project-pilot) (2026-07-24). Andon Labs collaboration.

**Claim in one sentence:** An embodied drone benchmark that decomposes "locate-and-follow a person via indoor quadrotor" into **5 sub-tasks — Reconstruct, Localize, Navigate, Detect, Follow** — reproduced in simulation and scored across 15 frontier models. **Claude Fable 5** is the first model to clear the baseline on **4 of 5 sub-tasks**; **Reconstruct** blocks end-to-end real-drone autonomy for *everyone*.

**The delta:**
- One of the **few sim + real-drone evaluations** from a frontier lab — tests VLMs on a real hardware loop, not just synthetic navigation.
- **Longitudinal frontier-model sweep** (GPT-4o → o1 → o3 → Gemini 2.5/3.1 Pro → Opus 4/4.5/4.7/4.8 → Fable 5 → GPT-5/5.2/5.5/5.6 Sol) — you can see the capability slope explicitly.
- **Specific failure mode** identified: **monocular scene reconstruction** from the drone's video stream, not planning or reasoning.

**Sources:**
- [Anthropic — Project Pilot](https://www.anthropic.com/research/project-pilot) `[primary]`
- [Anthropic — Frontier Red Team](https://www.anthropic.com/research/team/frontier-red-team) `[primary]`

### Why it matters to a builder

- **If you're shipping any embodied / camera-in-the-loop agent, the bottleneck is spatial reconstruction, not the LLM.** Build accordingly — bring your own SLAM / 3D scene model rather than relying on the VLM to do it.
- Puts an **early empirical marker** on the drone-autonomy timeline that safety and policy people will cite for the next 12 months. Reference it in any embodied-agent interview.
- Aligns with the [Humanoid $1.35B round](./02-new-emerging.md#3-humanoid) — same seam (LLM/VLM planner ↔ perception ↔ low-level controller), same skill vocabulary.

---

## 5. SLAI T-Rex — Full-parameter post-training of DeepSeek-V4 on Ascend SuperPOD {#5-slai-t-rex}

**Paper:** *SLAI T-Rex: An End-to-End System for Full-Parameter Post-Training of the DeepSeek-V4 Family on Ascend SuperPOD.* SLAI team (Ascend / Huawei ecosystem). **arXiv:2607.20145** (~2026-07-22).

**Claim in one sentence:** End-to-end system + data pipeline for full-parameter post-training of the trillion-parameter DeepSeek-V4 MoE family on **Ascend SuperPOD**, hitting **34.22% MFU** (2.93× the open-source baseline recipe) and **71.81% zero-shot Pass@1** on operations-research tasks (+3.98pp over GPT-5.4-Mini, +11.27pp over base DeepSeek-V4-Flash).

**The delta:**
- Concrete engineering numbers on **trillion-parameter MoE post-training outside the NVIDIA stack** — hierarchical parallelism, comm-overlap, custom kernels.
- **10K SFT dataset built with solver-verified synthetic OR problems** (four task categories, three problem representations) — a reusable recipe for **verifiable-reward SFT in a niche domain.**
- Demonstrates a **mid-sized team can push a domain-specialized fine-tune past frontier general models** on that domain.

**Sources:**
- [arXiv:2607.20145](https://arxiv.org/abs/2607.20145) `[primary]`

### Why it matters to a builder

- **Rare public MFU / throughput data** on MoE post-training — useful for budgeting your own big-model runs.
- **The solver-verified synthetic SFT pattern generalizes:** pick any domain with a symbolic verifier — SQL correctness, TLA+ spec satisfaction, LEAN proofs, SMT-solver — and you can bootstrap a domain-expert model without human labels. This is a real startup wedge, especially adjacent to the [three-lab consolidation](./01-big-lab-moves.md#3-amazon-agi-lab) making general-purpose post-training a losing bet.

---

## Also worth knowing (adjacent, cited for context)

- **Anthropic "J-lens" / Global Workspace paper (2026-07-06)** — Jacobian-based interpretability that surfaces the words a model is *silently considering*. Open-source repo `anthropics/jacobian-lens` (Apache-2.0, 2026-07-02). Practical use: detect eval-awareness and prompt-injection responses that never appear in output. Just outside our window, but the tool is live now.
- **Anthropic GRAM — Gradient-Routed Auxiliary Modules (2026-07-08)** — dual-use knowledge isolated into removable compartments (virology, cyber, nuclear). Preliminary; not in production. — [anthropic.com/research/off-switch-dual-use](https://www.anthropic.com/research/off-switch-dual-use)
- **CausalDS (arXiv:2607.08093, 2026-07-09)** — synthetic-SCM causal-reasoning benchmark for data-science agents. Six frontier agents get humbled on "decline to answer when unidentifiable." Good foil for anyone claiming their agent is an analyst.
- **Caveat on citations:** the arXiv proxy blocks direct abstract fetches from this session — numeric deltas above come from paper pages and search snippets. Read the PDFs before quoting specific effect sizes in an interview.

→ Cross-link: [`03` §1 how LHTB and Opus 5 effort interact in an agent team](./03-practical-skills-and-tools.md#1-opus-5-effort) · [`05` §2 the eval vocabulary that scores in an FDE interview](./05-career-and-startup.md#2-fde-market).
