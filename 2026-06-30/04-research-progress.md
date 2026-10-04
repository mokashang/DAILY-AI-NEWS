# Research Progress — 2026-06-30 (Tuesday)

The May–June research signal is **the eval stack is the bottleneck, not the model.** Long-horizon benchmarks, cheaper-substrate methodology papers, and AI-for-science evaluation environments all converge on the same point. Today's reading list pulls the four most-citable pieces.

Tags: `#arxiv #benchmarks #agents #eval #cost`

---

## 1. The June 2026 eval stack — six papers in one reading list {#1-eval-stack}

**What happened:** The long-horizon benchmark wave hardened across June. Today's list pulls **the six papers worth knowing this week**, grouped by what they unlock:

**Cheaper substrate (what to run):**

- **Efficient Benchmarking of AI Agents (arXiv 2603.23749)** — optimization-free protocol: evaluate only on tasks with **30–70% historical pass rates** → **44–70% reduction** in eval cost with high rank fidelity. The cheap way to publish a credible head-to-head on a student budget.
- **Holistic Agent Leaderboard (arXiv 2510.11977)** — argues eval is *infrastructure*-bottlenecked, not just methodology-bottlenecked; standardizes execution environment + per-step token/latency/tool-call traces + scaffolding-decoupled comparisons.

**Long-horizon real-world (what to measure on, carries from [2026-06-29/04 §1](../2026-06-29/04-research-progress.md#1-long-horizon-benchmarks)):**

- **SWE-EVO** — software-engineering tasks evolving over time; tests sustained-agent viability.
- **LongCLI-Bench** — long, stateful CLI sessions.
- **EvoCodeBench** — code base changes across versions.
- **Code Review Agent Benchmark** — Devin / Claude Code / Codex / PR-agent head-to-head.

**Specialty (where the next frontier wave hits):**

- **SciAgentArena (arXiv 2606.12736, Jun 10)** — 200 real scientific tasks across single-cell / spatial omics, drug discovery, EHR, genetics; **the eval substrate for the Jumper / Adler / Pritzel cohort** ([`01` §4](./01-big-lab-moves.md#4-anthropic-sf-science)). Headline finding: agents work on well-specified data analysis but struggle on open-ended exploration.

**Sources:**
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents](https://arxiv.org/abs/2603.23749) `[primary]`
- [arXiv 2510.11977 — Holistic Agent Leaderboard](https://arxiv.org/pdf/2510.11977) `[primary]`
- [arXiv 2606.12736 — SciAgentArena](https://arxiv.org/abs/2606.12736) `[primary]`
- Carries from [2026-06-29/04 §1](../2026-06-29/04-research-progress.md#1-long-horizon-benchmarks) for SWE-EVO / LongCLI-Bench / EvoCodeBench / Code Review Agent Benchmark
- [VoltAgent — awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers) `[secondary]` — keep open in a tab

### Why it matters to you

- **Job lens:** Drop **"30–70% middle-band evaluation protocol"** + **"scaffolding-decoupled per-step trace"** into your interview vocabulary. Almost no candidate at the new-grad level uses this language; both are direct interview-prompt answers ("how would you benchmark agents on a budget?").
- **Startup lens:** The eval-as-a-service wedge ([STARTUPS.md](../STARTUPS.md)) keeps strengthening. The Efficient Benchmarking + HAL combo lets a small team build a credible evaluation substrate at 30% of the cost of a brute-force one. Pair with the SciAgentArena environment for the AI-for-science vertical layer.
- **Insight:** Knowing the eval stack is the high-leverage version of knowing the model stack. Models change every quarter; eval methodology compounds for years.

→ Cross-link: [`01` §4 the SciAgentArena tie-in](./01-big-lab-moves.md#4-anthropic-sf-science) · [`05` §2 the FDE application talking points](./05-career-and-startup.md#2-this-week-fde).

---

## 2. The discipline-pillar framing — RigorBench (5 discipline pillars) and the Code Review Benchmark {#2-discipline-pillars}

**What happened:** [2026-06-27/04](../2026-06-27/04-research-progress.md) introduced **RigorBench** — *plan/verify/recover/abstain/atomic-commits* as the **5 discipline pillars** that empirically separate strong from weak agents. The June Code Review Agent Benchmark independently surfaces 4 of the same 5 dimensions in its scoring rubric.

The interesting implication: **the next-gen agent benchmark is less "did it succeed" and more "did it move through the right discipline pillars."** This maps closely to the Holistic Agent Leaderboard's per-step trace standard.

**Sources:**
- Carries from [2026-06-27/04](../2026-06-27/04-research-progress.md) `[primary citations there]`
- [arXiv 2510.11977 — HAL](https://arxiv.org/pdf/2510.11977) `[primary]`

### Why it matters to you

- **Job lens:** The 5 pillars are perfect interview vocabulary. They are also actionable in your own portfolio: write a 1-pager titled "How my <X> agent moves through the 5 RigorBench discipline pillars" with a per-step trace screenshot.
- **Startup lens:** The discipline-pillar framing is a candidate *product surface* — a runtime layer that emits per-step rigor scores, sold to agent-deploying teams who need to prove discipline to auditors (Colorado AI Act §3 of `01`, anyone?).
- **Insight:** The field shifted from "is the agent smart?" to "is the agent disciplined?" inside 12 months. That's a mature-field move.

---

## 3. Uncertainty quantification + abuse detection — the operational research thread {#3-uq-abuse}

**What happened:** Two operational research threads worth tracking this week:

- **Uncertainty Quantification in LLM Agents (arXiv 2602.05073)** — taxonomy of epistemic / aleatoric / computational uncertainty; mitigation depends on type. The *generative* form of the Appier "Answer, Refuse, or Guess?" thread from May.
- **API-abuse detection / output provenance** (post-[Alibaba 28.8M-distillation-exchanges disclosure](../2026-06-28/02-new-emerging.md#2-abuse-detection-wedge)) — surveys and one or two methodology papers are now circulating; the standard approach pairs a *classifier* over query patterns with *output-side cryptographic markers* that survive paraphrasing.

**Sources:**
- [arXiv 2602.05073 — Uncertainty Quantification in LLM Agents](https://arxiv.org/pdf/2602.05073) `[primary]`
- Carries from [2026-06-28/02 §2](../2026-06-28/02-new-emerging.md#2-abuse-detection-wedge) for abuse detection

### Why it matters to you

- **Job lens:** UQ vocabulary is a Tier-1 differentiator for AI Safety / Responsible AI roles. Five minutes of skim today, one line in your application this week.
- **Startup lens:** UQ-aware orchestration + abuse-detection together = the agent-governance product surface ([`02` §1](./02-new-emerging.md#1-abuse-detection-pricing)). Runlayer ($30M) is the closest funded player; founding-engineer roles in the seed cohort.
- **Insight:** UQ is the *missing layer* in most production agents. The fact that it's a survey-worthy topic in June 2026 (not a textbook chapter) is your edge.

---

## Short list — also worth knowing

- **Evaluation and Benchmarking of LLM Agents: A Survey (arXiv 2507.21504)** — the canonical map of the eval landscape; cite it.
- **Evolutionary Perspectives on the Evaluation of LLM-Based AI Agents (arXiv 2506.11102)** — taxonomy paper, useful for context.
- **NatureBench / EnterpriseClawBench / CoffeeBench / Autodata** — carries from [2026-06-27/04](../2026-06-27/04-research-progress.md). The frontier-agents-vs-published-SOTA gap (17.8% on NatureBench without web search) is the most-cited single number this month.

→ Cross-link: [`05` §2 the FDE application talking points](./05-career-and-startup.md#2-this-week-fde).
