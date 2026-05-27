# New & Emerging — 2026-05-24

The emerging category this weekend isn't a startup — it's a **research-product space taking shape in real time: "agents that do research."** Three benchmarks in one window (PostTrainBench, InnovatorBench, test-time-scaling-of-agents) are all measuring whether an agent can do real ML/scientific work autonomously, under a budget. When the *measurement* infrastructure for a capability shows up this fast, it means the *products* are close behind — and there's a picks-and-shovels layer worth seeing now.

Tags: `#research #agents #emerging #benchmarks #self-improvement #startups`

---

## 1. "Agents that do research" — a category forming around its own benchmarks {#1-agents-as-researchers}

**What's emerging:** A coherent category is crystallizing out of a few simultaneous papers (full detail in [`04` §1](./04-research-progress.md#1-test-time-scaling)):

- **PostTrainBench** — can agents automate **LLM post-training** under bounded compute? ([2026-05-23/04 §1](../2026-05-23/04-research-progress.md#1-posttrainbench))
- **InnovatorBench** — can agents conduct **innovative LLM research** (not just reproduce known results)?
- **Test-Time Scaling of General LLM Agents** — how should an agent **spend inference-time compute** (reasoning, tool calls, retries) under uncertainty?

The thread tying them together: the labs are **staffing the "AI does AI R&D" loop** (Karpathy → Anthropic pre-training automation, [2026-05-22 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)), and the research community is **building the rulers to grade it.** That synchrony — hire + benchmark + survey, all at once — is what a forming category looks like before it has a name.

**Sources:**
- [arXiv 2603.08640 — PostTrainBench](https://arxiv.org/abs/2603.08640) `[primary]`
- [arXiv 2510.27598 — InnovatorBench](https://arxiv.org/pdf/2510.27598) `[primary]`
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1) `[primary]`
- [arXiv 2601.12538 — Agentic Reasoning for LLMs (the survey that frames it as "layer-2 self-evolving")](https://arxiv.org/abs/2601.12538) `[primary]`

### Why it matters to you

- **Job lens:** This category will hire **two profiles**: research engineers who can *build* the agents (lab-internal, competitive) and — more accessibly for you — engineers who can build the **infra around them**: experiment orchestration, compute budgeting, eval/verification of agent-proposed changes. That second profile is the **AI Integration / platform** lane pointed at the research org instead of the customer. Frame your orchestration + cost + eval portfolio at *that* org.
- **Startup lens:** The picks-and-shovels under "agents that do research": **(1) compute-budget schedulers** (spend a fixed GPU pool across many agent-run experiments), **(2) eval/verification harnesses** for agent-generated training changes (the recurring "verify the work" wedge), **(3) experiment-orchestration + provenance** (what did the agent try, why, at what cost). The labs build the *agents*; they'll buy the *substrate* — and per [2026-05-23 §1](../2026-05-23/02-new-emerging.md#1-consolidation), "buy" increasingly means "acqui-hire your team."
- **Insight:** The most defensible bets sit **one layer below the capability everyone's excited about.** Everyone wants to build the research-agent; far fewer are building the boring, durable substrate (budgeting, eval, provenance) that every research-agent needs. As with cost-control and verification, **the unglamorous layer gets *more* valuable as the agents get better.**

→ Cross-link: [`04` §1 the benchmarks in detail](./04-research-progress.md#1-test-time-scaling) · [2026-05-23/02 §1 the acqui-hire exit for substrate startups](../2026-05-23/02-new-emerging.md#1-consolidation) · [`STARTUPS.md`](../STARTUPS.md).
