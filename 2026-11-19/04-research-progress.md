# Research Progress — 2026-11-19

No named-lab paper landed in the Nov 14–19 window (the Nov 5 METR Anthropic-acceleration assessment + OpenAI's 10 Lean-formalized proofs are still the active cross-week threads). The arXiv frontier moved on **agent decision theory, prompt-injection methodology, "effort-level" replication risk, and the next generation of world-action models after Praxis-1 / GR00T 2**. Three of this week's papers are directly usable as **FDE portfolio eval harnesses**.

Tags: `#arxiv #agents #prompt-injection #world-models #metr #post-training`

---

## 1. Jeveration: System-1 generators that bypass deliberation (arXiv 2611.24738) {#1-jeveration}

**Who:** NUS. **Top-of-HF-Daily-Papers, 78 upvotes.**

**Claim:** Fast "System-1" generator models bypass deliberation on routine tasks — reopens the fast/slow routing debate for inference economics. Potentially a successor framing to Haiku's **effort levels** (where reasoning depth is a tunable knob) by splitting the model itself into a **generator + deliberator**.

**Sources:**
- [Hugging Face Daily Papers (Nov 19 snapshot)](https://huggingface.co/papers) `[primary]`
- [arXiv 2611.24738](https://arxiv.org/abs/2611.24738) `[primary]`

### Why it matters to you

- **Insight:** If generator-deliberator split becomes standard, **"model routing"** turns into **"intra-model mode routing"** — collapsing a chunk of the router-startup wedge back into the labs. Watch Anthropic's next model card for a "System-1 / System-2" descriptor.
- **Portfolio use:** Build an eval that compares System-1 generator cost per request vs. full-model cost — that's a clean MLE-interview artifact.

---

## 2. Threshold Theory of Plan Commitment — when agents should repair vs replan vs abandon (arXiv 2611.19663) {#2-plan-commitment}

**Who:** Tewari (independent / academic).

**Claim:** Derives an **optimal threshold policy** for the repair / replan / abandon decision in agent plans — the first formal treatment of plan-commitment under cost uncertainty.

**Why it's useful:** Most production agents today either over-commit to failing plans (cost blowout) or under-commit (thrash). This paper gives you a **ready-made decision procedure** to plug into your agent's control loop.

**Sources:**
- [arXiv 2611.19663](https://arxiv.org/abs/2611.19663) `[primary]`

### Why it matters to you

- **Job lens:** This is **exactly** the kind of paper an FDE hiring manager will ask you about if you claim "agent control-plane" experience. Read it. Implement a small version of the threshold rule in a demo. Cite the paper in your README.
- **Startup lens:** Agent-control-plane startups (LangChain's new territory with the GIC round, see [`02` §1](./02-new-emerging.md#1-langchain)) will integrate papers like this into their default middleware within 60 days. If your product has a custom control loop, build it with threshold theory baked in from day one.
- **Insight:** **Agent decision theory is where ML research joins operations research.** This is a research-lite lane: you don't need a pure-ML PhD to contribute, you need to read OR/decision-theory papers. Good hedging bet for applied-researcher roles.

---

## 3. PIPETTE: prompt-injection purple-teaming (arXiv 2611.24362) {#3-pipette}

**Who:** Unnamed (indie / small-group).

**Claim:** Purple-team framework for prompt injection on LLM agents. Combines red-team adversarial inputs with blue-team detection on a single evaluation substrate. Benchmarks across agent configurations and MCP tool-call paths.

**Why it's useful:** The first **open eval substrate** for prompt-injection robustness that spans the full agent + tool-call surface.

**Sources:**
- [arXiv 2611.24362](https://arxiv.org/abs/2611.24362) `[primary]`

### Why it matters to you

- **Job lens:** Wrap PIPETTE around your public MCP server this weekend. One failure trace + a fix PR is **the fastest path to a credible security-eval portfolio artifact**. See [`03` §4](./03-practical-skills-and-tools.md#4-pipette) for the step-by-step.
- **Startup lens:** Any agent product you sell into regulated verticals (finance, healthcare, legal) will be asked "do you run prompt-injection testing?" — PIPETTE is a clean procurement answer.
- **Insight:** Prompt injection moved from research abstraction to **procurement-checklist mandate** in 2026. PIPETTE is the inflection paper.

---

## 4. Thinking Harder Doesn't Lead to Better Choices (arXiv 2611.22033) {#4-thinking-harder}

**Who:** University of Chicago.

**Claim:** Replication study on reasoning-effort / chain-of-thought depth for **LLM shopping agents** finds that more reasoning effort **raises confidence but not accuracy**. Direct replication risk for the **effort-level product pattern** Haiku 5.5 / Opus 5.5 productized in October.

**Why it's important:** This is a **user-facing calibration problem**: if your agent is more confident when it's wrong, you have a worse product than if it's just wrong. Shopping is the first vertical where this effect is cleanly measured — expect follow-up replications in legal, medical, and financial agents within 90 days.

**Sources:**
- [arXiv 2611.22033](https://arxiv.org/abs/2611.22033) `[primary]`

### Why it matters to you

- **Job lens:** **Calibration evaluation** is now a hireable sub-role at every applied-AI company. If you can show one experiment where you measure confidence-accuracy gap on a real task, that's a research-lite FDE/Applied Scientist portfolio piece.
- **Startup lens:** If you built any "high effort level = better answer" UX affordance, audit it before shipping to customers. Confidence miscalibration is **the quietest way to ship a bad product**.
- **Insight:** **Effort levels are a UX surface, not a quality dial.** Treat them like a power-user toggle, not a magic wand — most customer-value is delivered at mid-effort with the dial hidden.

---

## 5. HINT-WAM + StrideWorld — the post-Praxis-1 / GR00T 2 wave (arXiv 2611.24789, 2611.24408) {#5-vla-followup}

**What's new:**
- **HINT-WAM (2611.24789)** — Hindsight-Informed Training for **World Action Models**. Successor method to the Praxis-1 / GR00T 2 open-weight VLA class. Applies **hindsight relabeling** to video + action streams. Indie group; 22 HF upvotes.
- **StrideWorld (2611.24408)** — SJTU benchmark targeting **scene rigidity and action consistency**. The next-layer eval harness after Praxis-1 and GR00T 2 leaderboards.
- **Code World Model 2.0 (2611.22925)** — inclusionAI's long-horizon controllable video generation; real competitor to Runway Praxis-1 on the video-prior side.

**Sources:**
- [arXiv 2611.24789 — HINT-WAM](https://arxiv.org/abs/2611.24789) `[primary]`
- [arXiv 2611.24408 — StrideWorld](https://arxiv.org/abs/2611.24408) `[primary]`
- [arXiv 2611.22925 — Code World Model 2.0](https://arxiv.org/abs/2611.22925) `[primary]`

### Why it matters to you

- **Job lens:** VLA / world-model engineers at NVIDIA, Google Robotics, Runway, Figure, Apptronik, Physical Intelligence pay **$350–600K TC** for applied scientists. The qualification bar used to be a robotics PhD; with open weights + public eval harnesses, **a public StrideWorld result + a HINT-WAM re-implementation is now a qualifying portfolio** at startup scale.
- **Startup lens:** World-action models are the **"AWS 2008"** of embodied AI — the primitives are open but the application layer is wide-open. Vertical VLA wedges (warehouse picking, apparel QC, construction progress) are under-staffed.
- **Insight:** **If you already know how to evaluate VLAs, 2027 is your year.** The leaderboards are young enough that early contributors become the named experts.

---

## 6. METR Anthropic R&D acceleration carryover (Nov 5) — awaiting Anthropic's response {#6-metr-carryover}

**What happened (Nov 5, still active):**
- **METR** published an assessment finding Anthropic's **model-capability improvement rate is ~2× its March 2024–Oct 2025 pace**, with **~80% of the acceleration attributed to internal AI use** (Claude helping ship Claude).
- Anthropic promised a **first-party response "in coming weeks."** As of today, Nov 19, that response has not landed.
- Separately: **OpenAI's 10 Lean-formalized proofs** (also Nov 5) are now **shaky** — ≥3 manuscripts withdrawn, and an independent preprint found the Lean formalization of the Navier–Stokes result doesn't match the paper's informal proof. **"Clean Lean build" ≠ "proven theorem"** is the emerging consensus critique.

**Sources:**
- [METR — Anthropic R&D acceleration assessment](https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment) `[primary]`
- [NPR — Navier-Stokes Lean critique](https://www.npr.org/2026/09/22/nx-s1-5968588/openai-navier-stokes-problem-mathematicians-learn-little)
- [Noze.it — Ten mathematical results with a Lean certificate (critique)](https://www.noze.it/en/insights/mathematics-lean-certificate-verifiable/) `[analysis]`

### Why it matters to you

- **Job lens:** If METR's ~80% internal-AI-use number holds up, **"I use Claude Code daily to ship faster"** goes from résumé line to **de facto job requirement** at Anthropic + anyone copying their internal practices. Make sure your public GitHub shows weekly commits from a Claude-Code-heavy workflow.
- **Startup lens:** METR's numbers are the **most credible "AGI is accelerating R&D" evidence of 2026**. Use it in investor decks as source material; don't quote it loosely.
- **Insight:** **The Navier-Stokes critique matters more than the Lean "proof."** It's the first empirical demonstration that "Lean build passes" can be hollow — because the formalization can drift from what the paper claims to prove. This will become a 2027 methodology-reform agenda in formal-methods + math-LLM research.

---

## Honorable mentions (not detailed, but worth tracking)

- **2611.17639** — **"What LLM Agents See and What Users Say"** — new Claude and GPT models **always open a counted second record then never act on it**. A measurable, named tool-use pathology.
- **2611.23068** — **"The Resolution Hypothesis"** — self-improving agents bottlenecked by improvement detection, not generation.
- **2611.21366** — **ALIVE: Making Streaming Video Models Interactive** — early infra for "join and act" (Claude Meetings parallel).
- **2611.23824** — **Evidence-Based Credit Assignment for Search-Augmented LMs** — one of the week's few new post-training methods.
