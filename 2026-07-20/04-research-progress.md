# Research Progress — 2026-07-20

The theme this week: **agent evaluation is getting an infrastructure layer.** Three papers I want on your reading list; all three keep the "verify against real tools, at real cost" thread going that we opened on [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks). The **Holistic Agent Leaderboard (HAL)** is the missing multi-model, multi-benchmark, cost-normalized infrastructure — it's the *plumbing* the whole field has been asking for. **HAS-Bench** tackles configurable human participation — the missing dial in "human-in-the-loop" evaluation. **AlphaEval** turns evaluation into a first-class *production* concern. Plus two more you should be aware of: the **research-lifecycle benchmark** ("Act As a Real Researcher") and **DeepResearch Bench**.

Tags: `#research #arxiv #benchmarks #agents #evaluation #hal #has-bench #alphaeval`

---

## 1. Three real-agent benchmarks that will show up in your interview loop {#1-agent-benchmarks}

**What landed:**

### 1a. Holistic Agent Leaderboard (HAL) — the missing infrastructure

**Paper:** *Holistic Agent Leaderboard: The Missing Infrastructure for AI Agent Evaluation* (arXiv 2510.11977).

**What it does:** Provides a **standardized, multi-benchmark, multi-model, cost-normalized** leaderboard for AI agents. The pain point: prior agent leaderboards are per-benchmark, per-lab, and — critically — *do not normalize by cost*, so an "agent that wins" often just spent 10× more tokens to get there. HAL normalizes on cost and provides a canonical evaluation pipeline any team can drop into.

**Why the paper number is worth knowing:** it's the paper that makes agent leaderboards *comparable* — i.e., the *ImageNet moment for agent eval infrastructure*.

**Sources:**
- [arXiv 2510.11977 — Holistic Agent Leaderboard: The Missing Infrastructure for AI Agent Evaluation](https://arxiv.org/pdf/2510.11977) `[primary]`

### 1b. HAS-Bench — human-agent systems with configurable participation

**Paper:** *HAS-Bench: Evaluating LLM-Based Human-Agent Systems under Configurable Human Participation* (arXiv 2607.04329).

**What it does:** Introduces a benchmark where the **degree of human intervention is a knob you turn** — 0% (fully autonomous) to 100% (human-in-the-loop-on-every-decision). Then measures agent performance *as a function of that knob*, exposing which failures come from the agent vs. from the interaction design.

**Why it matters:** Most "agentic" products in the wild are actually **human-agent systems** (a Solutions Engineer or a customer approving each step). HAS-Bench is the first benchmark that reflects that reality and gives you a way to *design* the human-collaboration surface deliberately.

**Sources:**
- [arXiv 2607.04329 — HAS-Bench: Evaluating LLM-Based Human-Agent Systems under Configurable Human Participation](https://arxiv.org/pdf/2607.04329) `[primary]`

### 1c. AlphaEval — evaluating agents in production

**Paper:** *AlphaEval: Evaluating Agents in Production* (arXiv 2604.12162).

**What it does:** Formalizes the difference between *benchmark evaluation* (frozen dataset, offline) and *production evaluation* (live traffic, distribution shift, cost & latency budgets, feedback loops). Proposes a set of *in-situ* metrics — reliability under distribution shift, cost-per-successful-completion, degradation curves — and shows they correlate poorly with static benchmark rank.

**Why it matters:** This is the paper that gives *language* to what customers actually pay for. When a Solutions/FDE candidate says "I evaluate agents in production," they should be citing AlphaEval's framing.

**Sources:**
- [arXiv 2604.12162 — AlphaEval: Evaluating Agents in Production](https://arxiv.org/pdf/2604.12162) `[primary]`

### Why it matters to you

- **Job lens:** For interview prep, **read HAL end-to-end this week; skim HAS-Bench and AlphaEval.** The specific interview move: when asked "how would you evaluate an agent for our product?" — cite HAL for the multi-model + cost-normalized framing, cite AlphaEval for the production-metric distinction, cite HAS-Bench if the buyer's product has any human-in-the-loop surface. **This is the *exact* vocabulary that will separate you from candidates who talk about "GPT vs Claude accuracy."**
- **Startup lens:** HAL is a **standard being formed in real time.** Contribute a benchmark or a wrapper to the HAL pipeline for your vertical (legal, code, medical) — that's a public credibility artifact that costs a weekend to build and returns 2 years of "I contributed to *the* agent leaderboard."
- **Insight:** Two months ago on [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) we flagged MCP-Atlas and Tool Decathlon as the shift from *mock* to *real* tools. HAL/HAS-Bench/AlphaEval are the shift from *evaluate the model* to *evaluate the deployed system*. **The next 12 months of agent research will be dominated by evaluation-infrastructure work, not by novel agent architectures.** Your skill-investment ratio should reflect that (~60% eval / verification, ~40% novel architecture).

→ Cross-link: [`03` §2 the tier-picker as a mini-HAL for your stack](./03-practical-skills-and-tools.md#2-provider-router) · [2026-05-22/04 §1 MCP-Atlas / Toolathlon (the prior evolution step)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)

---

## 2. Act As a Real Researcher + DeepResearch Bench — evaluating research-lifecycle agents {#2-research-lifecycle}

**Papers:**
- *Act As a Real Researcher: A Suite of Benchmarks Evaluating Frontier LLMs and Agentic Harnesses in Research Lifecycle* (arXiv 2606.07462).
- *DeepResearch Bench: A Comprehensive Benchmark for Deep Research Agents* (arXiv 2506.11763).

**What they measure:** Both evaluate agents on the **end-to-end research lifecycle** — literature discovery, source triangulation, claim verification, synthesis, cited writeup. "Act As a Real Researcher" formalizes *what a real researcher does* as a sequence of decomposable tasks; DeepResearch Bench provides the eval corpus and scoring rubric.

**Why they matter (paired):** These are the closest published benchmarks to what a **customer-facing research assistant / analyst product** actually gets asked to do. If you're building for a research-heavy vertical (biotech, law, finance, consulting), the benchmark rubric doubles as a **product spec**.

**Sources:**
- [arXiv 2606.07462 — Act As a Real Researcher](https://arxiv.org/pdf/2606.07462) `[primary]`
- [arXiv 2506.11763 — DeepResearch Bench: A Comprehensive Benchmark for Deep Research Agents](https://arxiv.org/pdf/2506.11763) `[primary]`

### Why it matters to you

- **Job lens:** The "research lifecycle" framing is the vocabulary of any **AI-analyst / AI-associate** product (Hebbia, Glean, Rogo, EliseAI). Interview move: "I benchmarked our agent against DeepResearch Bench and found X% degradation on the *source-triangulation* step" — that's a specific, testable finding.
- **Startup lens:** **The gap between benchmark score and product-fit is enormous** — a research-agent that scores 70% on DeepResearch Bench can still be commercially useless if it fails on the *citation-integrity* sub-metric. Study the benchmark's rubric decomposition; that's *the* map of where a wedge product can beat a generalist Claude/GPT wrapper.
- **Insight:** Together with HAL/HAS-Bench, this is the same message: **the "agent research" beat is moving from architecture papers to eval papers.** For a CS grad student choosing a research direction, this is a *signal to align* — evaluation infrastructure is where publication and industry co-invest right now.

---

## 3. Efficient Benchmarking of AI Agents + Agent-ValueBench + LiveClawBench {#3-adjacent-benchmarks}

Three shorter callouts that round out the evaluation-infrastructure picture:

- ***Efficient Benchmarking of AI Agents*** (arXiv 2603.23749) — how to run agent benchmarks *cheaply* when each eval costs real money. Sampling strategies, early-stopping, importance-weighted rollouts. **Read this before you spend your Claude budget on a full HAL run.**
- ***Agent-ValueBench: A Comprehensive Benchmark for Evaluating Agent Values*** (arXiv 2605.10365) — evaluates whether agent behavior aligns with a specified value system across many decision points. **Practical use:** the vocabulary is what a "responsible AI" or "AI-safety-adjacent-eng" role asks for.
- ***LiveClawBench: Benchmarking LLM Agents on Complex, Real-World Assistant Tasks*** (arXiv 2604.13072) — the Anthropic-ecosystem answer to real-tool eval. Pairs well with the MCP-Atlas / Toolathlon thread ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)).

**Sources:**
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents](https://arxiv.org/pdf/2603.23749) `[primary]`
- [arXiv 2605.10365 — Agent-ValueBench](https://arxiv.org/pdf/2605.10365) `[primary]`
- [arXiv 2604.13072 — LiveClawBench](https://arxiv.org/pdf/2604.13072) `[primary]`
- [arXiv 2602.05073 — Uncertainty Quantification in LLM Agents: Foundations, Emerging Challenges, and Opportunities](https://arxiv.org/pdf/2602.05073) `[primary]` — bonus survey worth reading if you're picking a research direction; contains a mini-survey of 44 LLM-agent benchmark papers from Feb 2023 to Feb 2026.

### Why it matters to you

- **Job lens:** If you're writing a research statement (grad school apps, PhD, industry-lab residency), the **Uncertainty Quantification survey** is the single most efficient orientation paper — a curated 44-paper reading list embedded in the intro. Read the intro; pick 3 papers to go deep.
- **Startup lens:** Agent-ValueBench is the kind of paper *nobody* thinks about until a customer sues them. Treat it as a **defensive-eval reading list** — if you're building an agent that acts on customer data or money, the value-alignment eval is a due-diligence item enterprise buyers will start asking for by end of year.
- **Insight:** The 44-paper mini-survey embedded in the uncertainty paper is the tell that **the field has enough agent-benchmark work to survey**. That's the transition point from "novel research" to "engineering discipline" — and it's exactly when a well-executed engineering product tends to break out of the pack.

→ Cross-link: [ME.md — research-adjacent focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly) · [`05` §2 the CAISI/eval-lane career pitch](./05-career-and-startup.md#2-caisi-lane)
