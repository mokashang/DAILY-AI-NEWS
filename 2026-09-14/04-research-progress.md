# Research Progress — 2026-09-14

The frontier moved on two tracks this week. **Pretraining** got a serious token-efficiency proof point (Next Concept Prediction hits OLMo-3-7B's loss at ~half the tokens). **Reasoning** got two more challengers to CoT-based approaches — Looped Flows crossed 58.8% on ARC-AGI-1 without any verbalized chain-of-thought, and a stochastic-dynamics view of answer distributions gave people a new lens on what's actually happening inside a "thinking" model. Plus a fresh action-level agent-reproduction benchmark and a native-4K unified-visual-intelligence release from SenseTime.

Tags: `#arxiv #pretraining #reasoning #arc-agi #agents #evals #multimodal #memory`

**Sanity-check disclaimer:** arXiv IDs below are in the 2609.xxxxx range (Sept 2026 submissions). Titles and summaries are compiled from web-search excerpts (alphaXiv, HyperAI, HF Papers trending, awesomepapers) rather than direct paper reads — worth a quick sanity-check on arXiv before quoting in interviews.

---

## 1. NCP-ArchPreview — Latent Space Language Models via Next Concept Prediction (2609.10715) {#1-ncp}

**Trending #1 on HF Papers this week.**

**What's novel:** An **8.9B pretraining recipe** that augments next-token prediction (NTP) with **Next Concept Prediction (NCP)** — a second objective predicting the *next concept* from a **product-quantized concept vocabulary built from the model's own hidden states.** The concept vocabulary is learned online; the model predicts both tokens and concepts jointly.

**Headline results:**
- Hits **OLMo-3-7B's final pretraining loss** using only **51.3% of the training tokens.**
- Beats OLMo-3-7B by **+2.45 pts on downstream macro-average**, **+5.99 on GSM8K.**

**Why it matters:** Concrete evidence that **latent/concept-level objectives can materially improve token-efficiency of pretraining at real scale.** The pure-NTP scaling law that has dominated 2020–2025 has a live challenger. If this pattern holds at 30B+ scale, the token-cost dynamics of pretraining just changed for everyone, including the frontier labs that are training on close-to-exhausted public token corpora.

Also: the "the model learns its own concept vocabulary" pattern connects to the [Sept 2 arXiv 2512.13564 "Memory in the Age of AI Agents"](../2026-09-10/) thread — both point at *representation of experience* as the next big lever.

- **arXiv:** [2609.10715](https://arxiv.org/abs/2609.10715) `[primary]`
- **HF Papers:** [Trending](https://huggingface.co/papers/trending) `[aggregator]`

### For your interviews next week

"OLMo-3-7B's final loss at 51.3% of tokens" is the number to memorize. If asked "what's new in pretraining this quarter?", NCP-ArchPreview is the highest-signal one-liner. Bonus points: contrast it with the [Sept 3 GPT-6 Astra release](../2026-09-10/01-big-lab-moves.md) — Astra is scale + data curation, NCP is a new objective — and note that the labs will *combine* both.

---

## 2. Thinking with Looped Flows (2609.11801) — 58.8% ARC-AGI-1, no CoT tokens {#2-looped-flows}

**What's novel:** A **looped-flow architecture** that does iterative refinement in latent space — **no chain-of-thought tokens, no visible reasoning trace.** The model runs internal loops over its own residual stream; only the final answer is materialized as tokens.

**Headline results:**
- **58.8% on ARC-AGI-1** — well past the 50% mark that most 2025 models struggled to cross.
- **12.2% on ARC-AGI-2** — meaningful signal on the harder benchmark.
- **Beats prior looped-model SOTA across 6 reasoning benchmarks** including multi-solution tasks.

**Why it matters:** Adds to the small-model latent-reasoning wave (BDH-CQ, Tiny Recursive Models) — the emerging alternative story to "make reasoning traces longer + train on more reasoning traces." If latent-loop reasoning scales, it competes directly with the CoT-heavy approach OpenAI + Anthropic have been pursuing, and it does so **without the token-per-token inference cost** that CoT drags along.

Second-order: if latent-loop reasoning also generalizes, the *interpretability* story gets harder — you can't inspect a reasoning trace that never leaves the model's activations. Watch how the alignment community responds to this over the next quarter.

- **arXiv:** [2609.11801](https://arxiv.org/abs/2609.11801) `[primary]`

### For your startup wedge

Latent-loop reasoning + [Positron's 288 GB memory per die (§02 §2)](./02-new-emerging.md#2-positron) = the physical stack for "reason in latent, answer in tokens" apps at 10M-context. If you're founding, the *"cheap-to-run reasoning agent"* wedge just got a plausible architecture.

---

## 3. Answer-Distribution Trajectories — a stochastic-dynamics view of LLM reasoning (2609.09030) {#3-answer-trajectories}

**What's novel:** Instead of endpoint-only evaluation of chain-of-thought (compare final answer to gold), this paper **tracks the full predictive distribution over final answers at each reasoning step** — treating the reasoning trace as a stochastic process.

The trajectory analysis surfaces:
- **"Breakthrough" moments** where entropy collapses onto the right answer.
- **Early-legible fates** where the answer is already 90% determined by step 3, and the rest is theater.
- **Collapse vs. convergence** distinctions in failure cases — did the model *lose* the right answer, or *never converge* to it?

**Why it matters:** New **evaluation primitive** for reasoning models. This kind of distribution-over-time analysis is exactly what a plugin-eval report (see [`03` §1](./03-practical-skills-and-tools.md#1-plugin-eval)) should track. Likely to become a standard citation when analyzing "why does my agent fail on X kind of question."

- **arXiv:** [2609.09030](https://arxiv.org/abs/2609.09030) `[primary]`

### For your portfolio

Fold this framing into your router artifact: log per-step answer-distribution entropy alongside cost + latency. That's a level of eval discipline that literally no FDE candidate will have on their GitHub in Q4 2026. Cheap edge.

---

## 4. AgentActionBench — action-level agent-reproducibility grading (2609.11117) {#4-agentaction}

**What's novel:** **NLPCC 2026 Shared Task 11.** A **process-oriented benchmark** for agents that reproduce experiments from ML / AI4Science papers. Grades **intermediate actions**, not just final numbers — did the agent set up the environment correctly, did it fetch the right dataset, did it call the right training loop, before we even check the final metric.

**Why it matters:** Complements [Terminal-Bench-Science (52.6% Fable 5.1 on Sept 1)](../2026-09-10/01-big-lab-moves.md#1-model-fatigue) — the "can an agent re-run the paper" bar is now getting proper action-level rubrics, not just final-metric-matching. Expected to become a citation on frontier-lab agent evals within a quarter.

- **arXiv:** [2609.11117](https://arxiv.org/abs/2609.11117) `[primary]`

### For your eval suite

Steal the *rubric structure* even if you don't run the whole benchmark. When you write your 5-case plugin-eval suite (§03 §1), don't just grade final output — grade **the tool calls, the ordering, the retries.** That's the AgentActionBench discipline in miniature.

---

## 5. SenseNova-U1.5 — native unified visual intelligence (2609.11929) {#5-sensenova}

**What's novel:** SenseTime's **8B Mixture-of-Transformers** unified understanding + generation model, **encoder-free / VAE-free**, supporting **native 4K.** Multi-expert on-policy distillation for aesthetics, bilingual text rendering, infographics, multi-reference editing.

**Why it matters:** Adds a data point on how the **encoder-free camp** (a la GPT-4o image generation, ByteDance Bagel) is scaling. If SenseTime's tech report holds up to reproduction, "native multimodal at 4K without a separate VAE / image encoder" becomes a viable architecture — which in turn is a headwind for **CLIP-encoder + diffusion-decoder** pipelines that dominated 2024–2025 image gen.

Also: SenseTime shipping an open-ish tech report is a signal that Chinese labs are increasingly happy to disclose architecture details on domestically-served models, even as [Anthropic's threat report (§01 §2)](./01-big-lab-moves.md#2-threat-intel) escalates the distillation front. Two-track strategy: publish the architecture, protect the weights + data.

- **arXiv:** [2609.11929](https://arxiv.org/abs/2609.11929) `[primary]`

---

## Honorable mentions

- [Multi-Stage Rule-Chaining for Compositional Cognitive Reasoning (2609.10654)](https://arxiv.org/abs/2609.10654) `[primary]` — extends the rule-composition thread from May's `LemmaBench` era.
- [LAST-CQ — What Drives Recovery in Agentic Text-to-Cypher (2609.12746)](https://arxiv.org/abs/2609.12746) `[primary]` — the *self-refinement* mechanics under the AgentActionBench-style rubric.

---

## Weekly synthesis

Two of this week's papers (NCP + Looped Flows) attack the **efficiency frontier** — get more model quality per token, per FLOP, per inference dollar. Two (Answer-Distribution Trajectories + AgentActionBench) attack the **eval frontier** — grade what's actually happening under the hood, not just the endpoints. The frontier is moving simultaneously on both — and that geometry, more than any single paper, is what makes the pacing accord ([`01` §1](./01-big-lab-moves.md#1-pace-the-frontier)) plausible: **there's plenty of research headroom to move faster on efficiency and evals while the labs slow the shipped-model release cadence.**
