# Research Progress — 2026-09-05

Two consecutive weeks of benchmark drift and new evaluation infrastructure. **GPT-6 Astra saturated ARC-AGI-3 (99.9%) and FrontierMath T4 (97.6%)** — likely ending the leaderboard race and inviting the next round of contamination arguments. **PI-Mem (arXiv:2608.03048)** claims practical 3.6M-token contexts training-free-ish; **CivBench (arXiv:2609.02459)** is the first MCP-native long-horizon strategy benchmark; **LHTB and Terminal-Bench 2.0** confirm long-horizon terminal tasks are the actual coding-agent ceiling (median still unsolved by 21 frontier models); **ProgRouter (arXiv:2608.25992)** formalizes the escalate-only-when-needed routing pattern that becomes the compiler-level design your career depends on ([`03` §1](./03-practical-skills-and-tools.md#1-four-way-router)). **CORE-Bench v3** reframes coding-agent research as a *retrieval* problem — even top agents miss the correct file ~30% of the time on large repos. Frame: *the field is unbundling "reasoning" into distinct capability axes and building distinct evals for each.*

Tags: `#research #arxiv #benchmarks #arc-agi #frontier-math #long-context #pi-mem #mcp-benchmarks #civbench #lhtb #core-bench #prog-router #osworld #glm-53-flash #ai-trader`

---

## 1. GPT-6 Astra saturates ARC-AGI-3 and FrontierMath T4 — the benchmark flip {#1-astra-benchmarks}

**What/where:** Artificial Analysis published Astra numbers hours after the 2026-09-03 release:

- **ARC-AGI-3: 99.9%** (prior SOTA: 62.7%).
- **FrontierMath Tier-4: 97.6%.**
- **ExploitBench: 100%.**
- **OSWorld 2.0: 72.6% at ~47% less wall-time than GPT-5.6 Sol.**
- Astra ships at $10 in / $50 out per MTok — 2.5× GPT-5.6 pricing. Positioned as reasoning flagship, not workhorse.

Expect a wave of contamination critiques and adapter-harness disputes — Artificial Analysis notes provider-adapter differences and that ARC-AGI-3 evaluation harness has quietly evolved.

**Sources:**
- [Artificial Analysis — Benchmarking GPT-6 Astra](https://artificialanalysis.ai/articles/benchmarking-gpt-6-astra) `[analysis]`
- [The New Stack — OpenAI GPT-6 Astra benchmarks](https://thenewstack.io/openai-gpt6-astra-benchmarks/) `[secondary]`
- [BenchLM — ARC-AGI-3 leaderboard](https://benchlm.ai/benchmarks/arcagi3) `[analysis]`

### Why it matters

- **Job:** **"Contamination auditing" and "adapter-integrity verification"** are the near-future eval skillsets — expect Astra's numbers to be re-run by third-party labs (Epoch, Scale AI Evals, Anthropic evals team) within weeks. If eval work interests you at all, subscribe to Epoch's newsletter and start reading their methodology critiques — this is exactly the pipeline that leads to a Fellows-style research role.
- **Startup:** **The static-benchmark era is ending in real time.** New evals need to be either (a) private and continuously refreshed (like AI-Trader — [§7](#7-also-worth)) or (b) rooted in real-world artifacts the model can't have seen (like Senior SWE-Bench). **Founder opportunity:** "eval-as-a-service against your own proprietary corpus" is a wedge banks and law firms will pay $500K+/yr for.
- **Insight:** **When a benchmark saturates, the ceiling of the field visible to outsiders resets to whatever the next unsaturated eval is.** Astra hitting 99.9% on ARC-AGI-3 means François Chollet will publish ARC-AGI-4 (or a new eval class entirely) inside 90 days. **Track the new benchmark launches, not the saturated ones** — they're where actual progress will be measured.

---

## 2. PI-Mem — Parallel-Iterative Memory pushes practical context to 3.6M tokens {#2-pi-mem}

**What/where:** **arXiv:2608.03048** — Dawei Liu et al., posted early Aug 2026, indexed widely in the Aug 22 – Sep 5 window.

- Processes all chunks in parallel and **iteratively refines a shared compact memory** conditioned on current state, then merges selected evidence back.
- Claim: **matches or beats retrieval and recurrent-memory baselines at 3.6M-token contexts** with roughly constant memory during generation.
- Training-free-ish at inference — light adapter fine-tune, no full retrain.

Companion paper: **arXiv:2508.15294** (Multiple Memory Systems for Long-term Agent Memory) — extends the pattern to episodic + semantic memory separation.

**Sources:**
- [arXiv:2608.03048 — PI-Mem](https://arxiv.org/abs/2608.03048) `[primary]`
- [arXiv:2508.15294 — Multiple Memory Systems for Long-term Agent Memory](https://arxiv.org/html/2508.15294v1) `[primary]`

### Why it matters

- **Job:** **Long-context / memory** as a specialty is competitive but concentrated — a handful of teams (Anthropic memory, OpenAI infra, Google DeepMind Gemini long-context, and a wave of new startups like Mem0) drive the state of the art. Reading PI-Mem and reproducing its ablation on a 1M-token repo is the sort of side-project that lands a memory-team interview.
- **Startup:** **The wedge underneath PI-Mem is "compact memory-representation for agentic loops."** If your product's context is dominated by rehashing the same long doc every turn, a PI-Mem-style memory abstraction on top of your inference call is a real efficiency win. Startup thesis: **"Redis for agent memory"** — a durable, indexed, semantic memory store with an MCP interface.
- **Insight:** **The interesting frontier of long context is no longer "how big is the window" but "how do you compact it as it grows."** Native 1M-token windows are now table stakes across Anthropic, Google, Meta. The next moat is *staying under budget on tokens that matter* — PI-Mem is one of the first serious training-free-ish takes.

---

## 3. CivBench — MCP-native long-horizon strategy benchmark in Civilization VI {#3-civbench}

**What/where:** **arXiv:2609.02459v1**, submitted **2026-09-02**.

- Uses **MCP** to give agents structured control of Civ VI as a controllable long-horizon environment. First serious open-ended strategy-game benchmark built **natively on MCP** rather than bespoke game-agent wrappers.
- Result: frontier agents (GPT-5.6 Sol, Claude Opus 5) still fail multi-era objectives; all tested agents complete **<20% of full games** under strict scoring.
- Complements **MCP-Bench (arXiv:2508.20453)** and **MCP-Atlas** (Scale) by adding sustained multi-hour horizons.

**Sources:**
- [arXiv:2609.02459 — CivBench](https://arxiv.org/abs/2609.02459v1) `[primary]`
- [arXiv:2508.20453 — MCP-Bench](https://arxiv.org/abs/2508.20453) `[primary]`

### Why it matters

- **Job:** **Long-horizon agent evaluation** is one of the youngest specialties in the field — the CivBench + MCP-Bench + MCP-Atlas triangle is the current SOTA. Anthropic and DeepMind are both hiring eval-first research engineers. **Reading these three papers in a weekend + writing a 500-word comparison post is a legitimate research-engineer interview conversation.**
- **Startup:** **"Verified MCP tool marketplace with continuous eval"** is an under-served category. CivBench-style dynamic environments let you certify tool-use quality, not just tool-use presence. Startups in this lane are early enough to define the standard.
- **Insight:** **MCP as an eval substrate matters more than MCP as a distribution substrate.** If every serious agent benchmark of 2027 is MCP-native, MCP wins by inertia even if a technically-better protocol emerges. Bet accordingly.

---

## 4. LHTB & Terminal-Bench 2.0 — the long-horizon coding ceiling {#4-lhtb}

**What/where:** **arXiv:2607.08964 (LHTB)** — 46 long-horizon terminal tasks, dense reward grading.

- Average run: **9.9M tokens over ~231 episodes and 85 minutes.**
- Under a 90-min budget: top model reaches **~15% pass@1 at partial reward, ~11% at perfect reward**. Median task unsolved by every one of **21 frontier models**.
- **Terminal-Bench 2.0** (89 hard tasks): frontier still <65%.

**Sources:**
- [arXiv:2607.08964 — LHTB](https://arxiv.org/abs/2607.08964) `[primary]`
- [Terminal-Bench — News](https://www.tbench.ai/news) `[primary]`

### Why it matters

- **Job:** **Anthropic FDE and OpenAI FDE take-homes are increasingly LHTB-flavored** — real long-horizon terminal debugging, not toy leetcode. If you can practice one LHTB-style task per weekend (even a synthetic one), that's a differentiated interview signal.
- **Startup:** **Coding-agent SOTA is saturating on the wrong axis.** SWE-bench Verified is at 95% but LHTB is 15%. The gap is real business opportunity: **agentic tooling that helps *humans* stay in the loop on long-horizon coding tasks** (better checkpointing, better replay, better rollback) is a genuinely under-served category.
- **Insight:** **The reason median long-horizon terminal tasks stay unsolved isn't reasoning capability — it's compounding execution errors.** Every step compounds; 90-minute tasks have hundreds of steps; a 99% per-step success rate still fails end-to-end. This validates the ProgRouter / verifier-loop / checkpoint-and-rollback school of agent design.

---

## 5. ProgRouter — progress-guided multi-agent orchestration under cost tradeoffs {#5-prog-router}

**What/where:** **arXiv:2608.25992**, Songyuan Li et al., **EMNLP 2026 Findings**.

- Predicts **task-progress during execution** and routes between weaker/stronger models per step — jointly optimizing quality and $ cost across collaborative workflows.
- Reports **~2–4× cost reduction at parity** on standard multi-agent tasks.
- Pairs well with **"Learning What to Retain: Gated-Memory Routing"** (EMNLP 2026 main) and RL-for-orchestration work (arXiv:2605.02801).

**Sources:**
- [arXiv:2608.25992 — ProgRouter](https://arxiv.org/abs/2608.25992) `[primary]`
- [arXiv:2605.02801 — RL for LLM-based multi-agent orchestration traces](https://arxiv.org/abs/2605.02801) `[primary]`

### Why it matters

- **Job:** ProgRouter is **the academic backbone for the four-way router artifact from [`03` §1](./03-practical-skills-and-tools.md#1-four-way-router)**. Citing it in your interview conversation immediately signals "I read the paper that formalizes what I built" — the sort of signal FDE interviewers weigh heavily against candidates who just glued APIs.
- **Startup:** **The routing category will consolidate around a "progress-aware" default** — most current routers are static (task-tag → model-choice). Startups building the next-generation router should design for **runtime progress prediction as a core primitive**, not a bolt-on.
- **Insight:** **Cost-aware routing is now the compiler pass of agent design.** The equivalent of `-O2` for LLM systems. Expect ProgRouter (or a successor) to be commoditized into the frontier-lab SDKs within 6 months.

---

## 6. CORE-Bench v3 — retrieval is the coding-agent bottleneck {#6-core-bench}

**What/where:** **arXiv:2606.11864**, v3 posted **2026-08-24**. Reframes the SWE-bench evaluation stack:

- Agents must navigate real repo state, locate files/functions, and filter near-duplicate distractors before any patch is written.
- **Retrieval accuracy explains most of the variance in end-to-end SWE-bench Pro success.**
- **Top agents still miss the correct file ~30% of the time on large repos.**

Companion: **arXiv:2608.09802 (SWE-Bench ProMax)** — held-out benchmark, top models ~23%.

**Sources:**
- [arXiv:2606.11864 — CORE-Bench v3](https://arxiv.org/abs/2606.11864) `[primary]`
- [arXiv:2608.09802 — SWE-Bench ProMax](https://arxiv.org/abs/2608.09802) `[primary]`

### Why it matters

- **Job:** **"Retrieval-aware coding-agent evaluation"** is a fresh niche. Cursor / Windsurf / Anthropic Claude Code teams are all hiring engineers with strong RAG + code-indexing intuition. This is the eval design your side-project should showcase.
- **Startup:** **Better code-retrieval-for-agents is a moat that's actually defensible** — the incumbents' retrieval is heuristic (BM25 + embedding + LSP). Startups can win on smarter symbol-graph traversal + call-graph-aware embeddings.
- **Insight:** **SWE-bench Verified is functionally saturated (top-5 within 4 points).** The next real progress metric is CORE-Bench-flavored, or SWE-bench Pro Max, or Senior SWE-Bench (from [`02` §7](./02-new-emerging.md#7-also-worth)). Track these; the Verified leaderboard is now a marketing chart.

---

## 7. Also worth flagging {#7-also-worth}

- **GLM-5.3-Flash architecture teardown** — Sebastian Raschka blog post 2026-08-26 documents Zhipu's GLM-5.3-Flash: sparse MoE, hybrid attention combining KV-decoupled attention (KDA) + MLA/DSA, four-stream multi-head-collateral (mHC) residual path. Public weights — strongest fully-open frontier architecture disclosed this cycle. [Raschka blog](https://sebastianraschka.com/blog/) `[primary]`
- **AI-Trader — first fully-automated live LLM finance benchmark.** Runs LLM agents against real market feeds; reports rolling PnL as the metric. Template for "living" evals resistant to contamination. [HF Papers Trending](https://huggingface.co/papers/trending) `[primary]`
- **OSWorld-Verified saturating.** Qwen3.8 Max 86.1%, Claude Fable 5 / Mythos 5 at 85% — top-3 within 1.1 pts. [BenchLM](https://benchlm.ai/benchmarks/osworld-verified) `[analysis]`
- **SWE-bench Multimodal v2 fully open-sourced Sept 1** — 480 tasks. [CodeSota](https://www.codesota.com/browse/agentic/swe-bench) `[analysis]`
- **Karpathy at Anthropic pretraining** has been publicly arguing "don't skip fundamentals for agents" — the mood-piece of the window. Extends the thread from [2026-05-22](../2026-05-22/). [Wikipedia](https://en.wikipedia.org/wiki/Andrej_Karpathy) `[secondary]`
- **Raschka video "How Claude Watermarks AI-Generated Text"** (48-min walkthrough) — timely given ongoing AI-content-provenance policy debate. [Raschka blog](https://sebastianraschka.com/blog/) `[primary]`

---

## 8. Cross-links {#8-cross-links}

- Practical: [`03` §1 four-way router](./03-practical-skills-and-tools.md#1-four-way-router) — ProgRouter in production
- Big Lab: [`01` §2 Astra ships](./01-big-lab-moves.md#2-gpt-6-astra) — the benchmark saturation story
- Emerging: [`02` §7 Senior SWE-Bench + Fable 5.1 SWE-bench Pro #1](./02-new-emerging.md#7-also-worth) — the next-gen eval landscape
