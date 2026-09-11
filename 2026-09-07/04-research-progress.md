# Research Progress — 2026-09-07

The frontier stopped shipping "look how fast we can generate" and started shipping **"look how thoroughly we can verify."** Fermat's Last Theorem in Lean is the moment; the arXiv weeklies converge on the same theme. Framing: *if the last 24 months were about generation, the next 12 are about verification. The papers this month all say so.*

Tags: `#research #lean #formal-methods #verification #arxiv #agents #multi-agent #prove2me #benchmarks`

---

## 1. Formalizing Fermat's Last Theorem in Lean — 13M lines, 11 days, 29,000 supporting theorems {#1-fermat-lean}

**What happened:** Anthropic published the paper + blog on **2026-09-04**. Claude, orchestrated by a Claude Code-based multi-agent harness through an open-source tool called **Prove2Me**, produced the **first end-to-end machine-checked proof of Fermat's Last Theorem in the Lean proof assistant**.

**Concrete stats:**
- **Duration**: ~11 days of wall-clock (started ~Aug 22, finished ~Sep 2).
- **Proof size**: **>13 million lines** of Lean — the **largest Lean proof ever written** by any means.
- **Supporting theorems**: **~29,000** intermediate theorems formalized as part of the FLT proof, across many areas of math never before formalized.
- **Compute**: **~6 billion output tokens** over the run.
- **Model**: an internal Anthropic research model (blog phrasing; not specified whether Fable 5.1 or an unreleased research checkpoint).
- **Human input**: "limited high-level input from humans" — read as: theorem statement + a high-level proof-graph shape.
- **Comparison point**: the Mathlib community and Kevin Buzzard's Xena Project had been planning a multi-year human-led formalization effort for FLT. Anthropic's blog acknowledges the parallel work; Buzzard's blog title reads simply "FLT: Anthropic has beaten me to it."

**Sources:**
- [Anthropic — Formalizing Fermat's Last Theorem (research blog)](https://www.anthropic.com/research/formalizing-fermats-last-theorem) `[primary]`
- [Anthropic — Formalizing Fermat's Last Theorem in Lean (paper PDF)](https://www-cdn.anthropic.com/9e431dff043da6538d99d6c2d231b670aa3da263.pdf) `[primary]`
- [Anthropic on X — Sep 4 announcement thread](https://x.com/AnthropicAI/status/2095947707605266436) `[primary]`
- [Xena Project (Kevin Buzzard) — FLT: Anthropic has beaten me to it](https://xenaproject.wordpress.com/2026/09/04/flt-anthropic-has-beaten-me-to-it/) `[expert]`
- [SiliconANGLE — Anthropic uses Claude to formalize proof of Fermat's Last Theorem](https://siliconangle.com/2026/09/04/anthropic-uses-claude-to-formalize-proof-of-fermats-last-theorem/) `[secondary]`
- [Tech Times — Fermat's Last Theorem Machine-Checked](https://www.techtimes.com/articles/326745/20260905/fermats-last-theorem-machine-checked-claude-completes-11-days-what-took-years-plan.htm) `[secondary]`
- [AI Wiki — Formalization of Fermat's Last Theorem (Anthropic, 2026)](https://aiwiki.ai/wiki/fermats_last_theorem_formalization) `[secondary]`

### Why it matters

- **For CS-grad-student research direction:** If you're within reach of any formal-methods, program-synthesis, or type-theory group, this is the moment to reach out to a professor. The Prove2Me pattern generalizes beyond Lean: to Coq, Isabelle, Rocq, F*, and — critically — to **software verification** (Dafny, Verus). A multi-agent-with-verifier thesis has never had better preprint support.
- **For your project portfolio:** See [`03` §4](./03-practical-skills-and-tools.md#4-multi-agent-lean-lessons) — the transferable primitives (graph-shaped decomposition + external cheap verifier + retry budgets) are the specific things to demo.
- **Long-arc insight:** This is a **specific rebuttal to the "LLMs cannot verify their own math" thesis** and, more importantly, to the "LLMs are BS generators" argument by Bender et al. **A machine-checked proof at this scale is not BS-detectable — it either type-checks in Lean or it doesn't.** Read this as an **epistemological event**, not just a research result. The philosophical debate about what LLMs "understand" now has a 13-million-line existence-proof against the strong "understand nothing" position — at least for math.
- **Follow-through to watch:** Which theorem falls next? Riemann hypothesis is the obvious target but a false lead (proof strategy is not known); Poincaré-conjecture-in-Lean is unexciting (already known-provable); **the practical extension** is *software correctness* — Amazon Web Services has been formalizing s2n / SAP has been formalizing HANA — a Prove2Me equivalent for **software formal verification** would collapse a $10B+ per year enterprise-verification market. Track it.

---

## 2. arXiv theme convergence — "verification-centric" agent design {#2-verification-centric}

**What's converging (Aug–Sept 2026 preprints):**

- **"Do Coding Agents Need Executable World Models, Simplification, and Verification to Solve ARC-AGI-3?"** — arxiv 2607.15439. Empirical evidence that *verification* (not just simulation, not just simplification) is the missing primitive for the highest tier of ARC-AGI. Argues that coding agents need an **exact replay verification** step.
- **"Marco DeepResearch: Unlocking Efficient Deep Research Agents via Verification-Centric Design"** — argues that **reliable verification is critical during both training and inference** for deep research agents, and that verification-centric harness design closes the gap between agent-generated research and expert-produced research.
- **"From Fluent to Verifiable: Claim-Level Auditability for Deep Research Agents"** — arxiv 2602.13855. Framework for making every claim inside an agent's research output *individually auditable* against source evidence. Practical: extends the JADE per-claim eval pattern we tracked at [2026-05-19](../2026-05-19/).
- **"Autonomous Research Agents: A Survey of AI Scientists and the Verification Gap"** — arxiv 2608.05179. Survey paper that names the gap explicitly — the field has been building "AI scientists" without a verification story, and the paper argues that's the single-biggest blocker to trustworthy autonomous science.
- **KG-CoI** — chains reasoning through **graph-attested facts** to detect fabricated intermediate steps in LLM chain-of-thought.
- **BioDisco** — couples knowledge-graph reasoning with literature retrieval + iterative feedback to evaluate novelty in biomedical claims.
- **Agent Flight Recorder** — **tamper-evident audit trails with on-chain anchoring** for long-horizon tool-using agents. Adjacent to the audit story; the interesting bit is the anchoring pattern (borrowed from blockchain).
- **FROAV** — visual workflow orchestration + LLM-as-a-Judge for RAG-based agent-pipeline evaluation.

**Sources (arxiv):**
- [awesome-ai-agent-papers (VoltAgent) — curated 2026 collection](https://github.com/VoltAgent/awesome-ai-agent-papers) `[curated]`
- [arXiv 2607.15439 — Do Coding Agents Need Executable World Models, Simplification, and Verification to Solve ARC-AGI-3?](https://arxiv.org/abs/2607.15439) `[primary]`
- [arXiv 2602.13855 — Claim-Level Auditability for Deep Research Agents](https://arxiv.org/html/2602.13855v1) `[primary]`
- [arXiv 2608.05179 — Autonomous Research Agents: A Survey of AI Scientists and the Verification Gap](https://arxiv.org/html/2608.05179v1) `[primary]`

### Why it matters

- **Research direction insight:** This is a **field-level thesis lock-in.** August–September 2026's preprint pipeline reads like "we all noticed the same thing at once": verification is the primitive we skipped. If you're writing a first-year research statement, this is where the field-in-motion is — pick a sub-problem of verification (formal-methods integration, hybrid-symbolic checks, provenance tracing, per-claim auditability, or the Agent Flight Recorder direction) and you're in a **hot area 12 months before it's crowded**.
- **For your startup pitch:** The verification-in-the-loop story is now defensible in a pitch deck because it has arxiv-level support, not just Anthropic-blog support. Cite two of these papers next to your product description. VC pattern-match improves.
- **Insight:** Verification is *specifically* what large-scale RL for LLMs has been optimizing against (RL from verifiable rewards / RLVR). What the September papers add is that **inference-time verification** is as important as **train-time verification**. The Fermat-in-Lean result is the extreme case: **all** verification is inference-time (Lean kernel checks each step). The next paper wave will be about **cheap inference-time verifiers** — small models trained specifically as judges on domain-specific check tasks (basically Anthropic Haiku 4.5 but domain-fine-tuned).

---

## 3. Related — the "cyber SKU split" is now a research pattern too {#3-cyber-sku-split}

Not a paper — a **structural pattern** that solidified this week. **Three frontier labs now formally ship restricted-access cybersecurity SKUs**:
- **OpenAI Daybreak** (GPT-6 Astra advanced cyber capability).
- **Anthropic Mythos 5.1** (Fable 5.1 weights under vetted-org access review; roots in original Claude Mythos from [2026-05-06](../2026-05-06/)).
- **Google Gemini 3.8 Flash Cyber** (new, vetted defenders only).

**Research implication:** The **AI safety research community now has a live regulatory-in-practice testbed.** Every one of these SKU splits is a real deployment decision that safety researchers can study — who gets access, under what NDA/audit, how the safe-subset is enforced in the general SKU, and (most interesting) whether the **general SKU can be RL'd back into the Critical-tier behavior via jailbreak or fine-tuning**.

**Where to publish:** the alignment forum + arxiv cross-post on "empirical study of frontier cyber SKU splits" is a wide-open lane. No paper yet as of this edition.

**Sources:** see [`01` §1](./01-big-lab-moves.md#1-fable-mythos-5-1), [`01` §3](./01-big-lab-moves.md#3-gemini-3-8-flash), [`01` §4](./01-big-lab-moves.md#4-gpt-6-astra) for the primary lab announcements. Adjacent policy: [Media.Defense.gov CSI on MCP security (June 2)](https://media.defense.gov/2026/Jun/02/2003943289/-1/-1/0/CSI_MCP_SECURITY.PDF) `[primary]`.

### Why it matters

- **For research direction:** If you're at all interested in AI safety / alignment / policy, the *empirical* study of these SKU splits is a paper waiting to be written. Method: interview access, review of published system cards, and — where you can get consented access — capability probes. That's a strong first paper for a safety-adjacent grad student.
- **For applying to Fellows:** This is a **direct hook** to Anthropic Fellows Cohort 3 (see [`05` §1](./05-career-and-startup.md#1-fellows-reopens)). A 1-page proposal on "empirical study of frontier cyber SKU deployment governance" is a strong angle if you can write it.

---

## 4. Bit-parts (worth a bookmark, not a deep read) {#4-bit-parts}

- **Prove2Me repository** — the open-source tool Anthropic used for FLT. As of Sept 7 the repo is either still-being-linked or newly public depending on when you read; check the Anthropic blog for the current link. Reading its architecture is time well spent for anyone building agent-team-with-verifier systems.
- **karpathy/autoresearch** — 630-LOC autonomous ML experimentation loop, single-GPU. Not new (March 2026) but re-relevant every time a small-open-weight model drops. → [`02` §5](./02-new-emerging.md#5-quick-hits).
- **PerceptUI** — LLM agents as human-aligned synthetic users for UI/UX evaluation. Persona-conditioned framework; reaches human-level realism via contrastive reflection fine-tuning. Nice paper if you're interested in the UX-eval-with-LLMs sub-field.
- **Rebuttal Agent** — strategic persuasion in academic rebuttal via theory of mind. Novel in that it explicitly models the reviewer's mental state. Worth reading before your next paper's rebuttal round.
- **CiteLLM** — agentic platform for trustworthy scientific reference discovery. Nice complement to the verification thread — this is the citation-side story.
- **Agent Audit** — a security-analysis system for LLM agent applications; frames agent apps as its own vulnerable class and proposes an audit workflow.

**Sources (all arxiv, curated by [awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers)):**
- PerceptUI, Rebuttal Agent, CiteLLM, HindSight, Agent Audit — see the curated list; individual arxiv IDs are updated weekly.

---

## 5. What's *not* moving (and that's information too) {#5-notmoving}

- **Robotics / embodied.** Project Pilot / Drone-Bench from [2026-07-25](../2026-07-25/#4-project-pilot) held — no follow-up paper this month that materially moved the frontier on scene-reconstruction-as-blocker. Watch NVIDIA GTC Fall (November?) for the next embodied leg.
- **World models / Sora-lineage video generation.** No new frontier release in the last two weeks; the Sora 2 / Veo 3 lineage is quiet. If you're a video-first grad student, watch OpenAI + Google for the next drop before you re-anchor your research direction.
- **RL for LLMs / post-training.** The On-Policy Distillation sweep from [2026-05-10](../2026-05-10/) → [2026-05-12](../2026-05-12/) has cooled from "sweep" to "steady wave" — still lots of papers but no new **paradigm shift** since spring. If you're picking a research direction, that suggests you'd be entering a mature field, not a hot one.

**Insight:** When a set of areas quiets down while others heat up, that's the **field's Bayesian update.** Verification is the direction; robotics and video are cyclical; RL post-training is mature. If you have 6 months of research runway before a proposal, spend them on verification.

---

_See_: [`03` §4](./03-practical-skills-and-tools.md#4-multi-agent-lean-lessons) for how to steal the Prove2Me pattern for your own portfolio · [`05` §1](./05-career-and-startup.md#1-fellows-reopens) for how the FLT + verification thesis maps to a Fellows application.
