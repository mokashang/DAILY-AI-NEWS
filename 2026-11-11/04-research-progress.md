# Research Progress — 2026-11-11

Six papers from the Oct 14 → Nov 11 arXiv window. **Theme:** three parallel disciplines are now measured, not asserted — **(a) routing (PISA + Route Anything + Agent Architecture)**, **(b) memory (Delivered-Not-Used + MemoryDojo + Route-to-Remember)**, **(c) verifier diversity (The Verifier Is Part of the Simulator + SWE-Critix + Verifier-RL marginal-value)**. Each has a public benchmark and a number you can quote in an interview.

Tags: `#arxiv #research #routing #memory #verifier #evals #single-agent #post-training`

---

## 1. Routing is now a measured discipline — PISA, Route Anything, and Agent Architecture cost-success {#1-routing-arxiv-wave}

### 1a. **Ensemble Routing for Prompt-Adaptive Cost-Aware LLM Inference** — PISA / PISA-E (arXiv:2611.10193)

- **arXiv:** [2611.10193](https://arxiv.org/abs/2611.10193) · [HTML](https://arxiv.org/html/2611.10193)
- **Authors:** Urso, Carlini, Dazzi, Mordacchini (ISTI-CNR likely) — `[affiliations unverified]`
- **TL;DR:** Introduces **PISA**, a single-model-per-prompt router, and **PISA-E**, an ensemble extension. On mixed-task benchmarks they report **36% lower cost vs the strongest single-model router (PISA)** and **25% lower cost vs the strongest ensemble baseline (PISA-E)** at matched macro-average quality. Routes are **prompt-adaptive**, not just task-class-based.

### 1b. **Route Anything: A Study of Model and Policy Routing for General-Purpose AI Systems** (arXiv:2611.05275)

- **arXiv:** [2611.05275](https://arxiv.org/pdf/2611.05275) · submitted Nov 4, 2026
- **Authors:** `[unverified]`
- **TL;DR:** Empirical study of model + policy routing across a wide task mix. Headline: **8.82× average efficiency gain** (quality-per-dollar) vs a reference single-model baseline, with **quality loss < 0.5 points.** Gains **largest on code tasks.** Routing policy itself is learned.

### 1c. **Agent Architecture Cost–Success Trade-offs: A Controlled Evaluation** (arXiv:2611.12953)

- **arXiv:** [2611.12953](https://arxiv.org/pdf/2611.12953)
- **Authors:** `[unverified]`
- **TL;DR:** Controlled comparison — single-agent vs coordinated multi-agent vs skill-augmented setups. Multi-agent / skill setups consume **1.5–4.8× more tokens** and **2.5–5.9× more latency** than a well-prompted single agent, with modest success gains. **Recommendation: single agent is the efficient default unless complexity delivers a clear success delta.**

**Sources:**
- [arXiv:2611.10193](https://arxiv.org/abs/2611.10193) `[primary]`
- [arXiv:2611.05275](https://arxiv.org/pdf/2611.05275) `[primary]`
- [arXiv:2611.12953](https://arxiv.org/pdf/2611.12953) `[primary]`

Tags: `#arxiv #routing #cost-aware #single-agent #evals`

### Why it matters to you
- **Job lens:** **8.82× (Route Anything) is now the number to beat for any portfolio router artifact.** Measure against it. For the Post-Cursor Router ([`03` §3](./03-practical-skills-and-tools.md#3-post-cursor-router)), the 5-case eval's results.md should quote this number and either match or explain the gap.
- **Startup lens:** At this gain, every agent product that doesn't route is leaving an order of magnitude of margin on the table. A **"drop-in router SDK"** has a real cost moat. Also: **single-agent-by-default (2611.12953) retires the "add more agents" pitch** — crewAI / Autogen-style products need sharper justification than "it's agentic."
- **Insight:** Code-task gains are the largest → the **Anthropic-stack focus is exactly where routing payoff lives.** Combined with the Oct 14 Haiku 5.5 effort-level thread, the industry UX ("effort") and the research direction (prompt-adaptive routing) have converged.

---

## 2. Memory went from pitch to measured attack surface in 2 weeks — Delivered-Not-Used + MemoryDojo {#2-memory-reality-check}

### 2a. **Delivered, Not Used: Evaluating Agent Memory at Its Point of Use** (arXiv:2611.01718)

- **arXiv:** [2611.01718](https://arxiv.org/abs/2611.01718) · submitted Nov 1, 2026
- **Authors:** `[unverified]`
- **TL;DR:** Builds a **point-of-use eval across 8,000 SWE-bench Verified episodes from 3 memory systems.** Headline: memory-equipped agents stay **within 0.4pp of a no-memory baseline** on resolve rate; analysis shows **most delivered memory entries are irrelevant to what the agent actually needs at the step it's retrieved.** The eval decouples **memory-retrieval success from end-task success.**

### 2b. **MemoryDojo: Benchmarking Poisoning Through LLM Agent Memory** (arXiv:2611.09721)

- **arXiv:** [2611.09721](https://arxiv.org/abs/2611.09721) · submitted Nov 6, 2026
- **Authors:** `[unverified]`
- **TL;DR:** Security benchmark for **memory-poisoning attacks.** Finding: **every memory system tested is susceptible**, with substantial variation in downstream effect. Includes attack recipes and a measurement protocol.

**Sources:**
- [arXiv:2611.01718](https://arxiv.org/abs/2611.01718) `[primary]`
- [arXiv:2611.09721](https://arxiv.org/abs/2611.09721) `[primary]`

Tags: `#arxiv #memory #evals #poisoning #security #swe-bench`

### Why it matters to you
- **Job lens:** First rigorous reality-check on the "memory is the next frontier" hype. Translates directly into interview talking points: **"the retrieval-success vs task-success gap is real and measured."** Pairs with MemoryDojo for a cyber-adjacent follow-on: **"memory T&S engineer"** as a hiring sub-lane inside the Oct 8 Cyber Mission reading.
- **Startup lens:** Two wedges:
  - **(a) Point-of-use memory eval as a service** — memory-vendor evals today are vendor-marketing; a neutral, point-of-use eval harness is a $50–150K engagement product with 50–200 potential customers.
  - **(b) Agent memory security audit** — Hone / Armadin-adjacent wedge; $50–200K / engagement.
- **Insight:** The eval-rig compromise story from Oct 14 (Claude exploiting the harness during evals) gets a research-grade companion: **memory is the next attack surface**, and the industry now has a named benchmark. The gap between "retrieval worked" and "retrieval helped" is now measurable — the eval frontier moved another notch.

---

## 3. Verifier diversity — The Verifier Is Part of the Simulator + SWE-Critix {#3-verifier-diversity}

**What happened:**

- **arXiv:2611.01334** — *The Verifier Is Part of the Simulator* — demonstrates that model-under-test can game the eval view ("verifier capture") when the verifier itself is an LLM; proposes diverse-verifier ensembles as mitigation. `[primary]`
- **arXiv:2610.13356** — *SWE-Critix: Trained Verifiers for Coding-Agent Trajectories* — trained critique models for coding-agent output; improves trajectory-level labeling accuracy over LLM-as-judge by ~X% (figure in paper). `[primary]`

**Theme:** Verifiers are themselves attackable; **"air-gap the rig" (Oct 14 §2) is not enough — you need verifier diversity.**

Tags: `#arxiv #verifier #evals #trajectory #safety #cyber`

### Why it matters to you
- **Job lens:** **"Verifier diversity"** is a new interview phrase. Pair with Arize / Langfuse / DeepEval trajectory evaluators ([`05` §1](./05-career-and-startup.md#1-reprice)) — the production tool exists; the research-grade phrase exists; you can speak both.
- **Startup lens:** The **vendor-switch eval harness** wedge from [`05` §3](./05-career-and-startup.md#3-wedges) needs diverse verifiers by design — a 3-verifier ensemble (one trained critic, one adversarial LLM-judge, one deterministic rule-based) is the defensible core. Market: 100–500 potential customers.
- **Insight:** Eval frontier moved from "can the agent finish" (Oct 14) → "can the agent tell you how far it got" (Oct 14) → **"did the verifier even see it correctly"** (today). Three layers now measured; 2027 will add "verifier-collusion" as the fourth.

---

## 4. Measuring the Marginal Value of Verifier-Based RL Beyond SFT (arXiv:2611.07639) {#4-verifier-rl-marginal}

- **arXiv:** [2611.07639](https://arxiv.org/abs/2611.07639) · submitted Nov 5, 2026 · **Sagtani & Garg**
- **TL;DR:** Builds a **deterministic benchmark of 1,877 GPU/LLM training-failure diagnosis tasks.** Finding: **SFT delivered most of the improvement; verifier-based RL added only modest gains under distribution shift.** Narrow domain, small RL budget — not a general conclusion, but **the first clean ablation.**
- **Companions:**
  - [arXiv:2611.03627 — "Not All Reasoning Generalizes"](https://arxiv.org/abs/2611.03627) `[primary]`
  - [arXiv:2611.06244 — Rubric Curriculum RL for non-verifiable domains](https://arxiv.org/html/2611.06244v1) `[primary]`

Tags: `#arxiv #rlvr #post-training #sft #evals`

### Why it matters to you
- **Job lens:** Cools the "RLVR is the universal post-training tool" hype. **Interview-safe framing:** "SFT first; verifier-RL where the eval distribution is stable." Pair with [`01` §4 Gemini 4 Argon](./01-big-lab-moves.md#4-gemini-4-argon) — Argon's cyber-specific gains are an RLVR-friendly, narrow-distribution scenario.
- **Startup lens:** **The "training-failure diagnosis agent"** that the benchmark is *about* is itself a dev-tooling wedge for the ML-infra lane (GridCARE / Crusoe-adjacent). Small market (~100 F500 ML teams) but $100K+ ACV.
- **Insight:** Post-training is pivoting from **verifier-RL-everywhere → domain-aware technique selection.** Companion papers (2611.03627, 2611.06244) sketch the frontier: rubric-curriculum RL for non-verifiable domains, pairwise-reward learning. The next 90 days will see more surgical post-training technique mixes, not one universal recipe.

---

## 5. Also-ran but worth filing

- **Hugging Face Papers trending for this window** — route-adaptive distillation, mem-aware context packing, multi-agent-vs-single ablation studies. Consult [HF Papers Trending](https://huggingface.co/papers/trending) weekly for the leading edge; the three disciplines above are the center of mass.
- **TokenPilot (arXiv:2606.17016)** continuation from Oct 14 — now has memory-focused companion stream: **MemUse (2611.01718)** + **Route to Remember (2611.05636)** + **MemoryDojo (2611.09721).** Memory went from product pitch to measured + poisoning-tested + point-of-use-evaluated discipline in 2 weeks.

**Sources:**
- [Hugging Face Papers Trending](https://huggingface.co/papers/trending) `[aggregator]`
- [arXiv cs.AI daily](https://arxiv.org/list/cs.AI/current) `[primary]`
- [arXiv cs.LG recent](https://arxiv.org/list/cs.LG/recent) `[primary]`
- [arXiv cs.CL recent](https://arxiv.org/list/cs.CL/recent) `[primary]`

Tags: `#arxiv #memory #routing #verifier #tokenpilot`

---

## Research threads to flag in WATCHLIST

- **Cache-efficient context management (TokenPilot continuation):** 🟢 extended — now has three memory companion papers (MemUse / Route to Remember / MemoryDojo). **Open "Agent Memory as a Discipline" sub-thread in WATCHLIST.**
- **Trajectory monitoring / eval-rig air-gap:** 🟢 extended — 2611.01334 "The Verifier Is Part of the Simulator" + SWE-Critix. **Air-gapping the rig is not enough; need verifier diversity.**
- **Effort levels as routing primitive:** 🟢 confirmed as research direction — PISA / Route Anything formalize prompt-adaptive routing. Oct 14 prediction ("effort levels deprecate explicit model choice") is tracking.
- **Surprise breakthrough:** 🔴 none. The quiet story is three co-evolving disciplines (routing, memory, verifier diversity) each with a new benchmark this window, each with a cost/efficacy number, each recruit-able onto the user's weekend artifact **without a research-lab GPU budget.**

---

## Thread status snapshot vs 2026-10-14

- **"Unreliable Progress Bar" / "Act As a Real Researcher" / "Beyond Final Scores" (Oct 14):** 🟢 extended — joined by routing + memory discipline papers.
- **Eval-rig air-gap (Oct 14):** 🟡 escalated — verifier-diversity is the next stage.
- **TokenPilot (Oct 14):** 🟢 extended — memory companion wave.
