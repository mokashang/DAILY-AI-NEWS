# Research Progress — 2026-05-23

The frontier-of-*measurement* thread from the past two days (MCP-Atlas, Toolathlon — "can the agent do real work?") gets a companion this Saturday: the frontier-of-*capability* produced a result that's hard to wave away. **An OpenAI general model autonomously disproved an 80-year-old open conjecture in mathematics**, and a **Fields medalist** called it "a milestone." That's the empirical core under Jack Clark's "Nobel within 12 months" claim ([`01` §3](./01-big-lab-moves.md#3-jack-clark)). Paired with it: the **eval literature is converging on test-time scaling and single-→multi-agent comparison** as the way to measure these systems honestly. Capability and its measurement, co-evolving — read both to stay credible.

Tags: `#research #math #reasoning #agents #benchmarks #test-time-scaling #arxiv #evaluation`

---

## 1. The math milestone: a general model disproved an 80-year conjecture {#1-math-milestone}

**What happened:** This week **OpenAI disclosed that one of its general-purpose models autonomously disproved Erdős's unit-distance conjecture** (a planar-geometry open problem ~80 years old) — producing an **infinite family of better constructions**, with the result **verified by mathematicians including Noga Alon and Thomas Bloom**, and **Fields medalist Tim Gowers calling the proof "a milestone in AI mathematics."** This archive first logged the result on [2026-05-21/01 §3](../2026-05-21/01-big-lab-moves.md); the new development is the **independent verification + the Gowers endorsement**, which moves it from "impressive demo" to "the field's most decorated people are signing off."

Why it's a milestone and not a stunt:
- It's a **general** model (not a narrow math system) advancing a **prominent open problem** central to a field — not a competition benchmark with known-shaped answers.
- The output is **checkable**: an explicit construction that mathematicians can (and did) verify, which sidesteps the "is the model just bluffing?" problem.
- It's the **concrete evidence** behind the week's bigger claims — Jack Clark's "AI + human Nobel within 12 months" ([`01` §3](./01-big-lab-moves.md#3-jack-clark)) reads very differently once a general model has done *this*.

**Sources:**
- [BuildFastWithAI — AI News Today, May 23, 2026 (math milestone item)](https://www.buildfastwithai.com/blogs/ai-news-today-may-23-2026) `[aggregator]`
- [2026-05-21/01 §3 — the original disclosure in this archive](../2026-05-21/01-big-lab-moves.md) `[archive]`
- [arXiv 2602.24173 — LemmaBench: a live, research-level benchmark for LLM mathematics](https://arxiv.org/pdf/2602.24173) `[primary]`

### Why it matters to you

- **Job lens:** "AI-for-science / research-agent" stops being speculative. Roles that pair **domain rigor + agent orchestration + verification** (the Isomorphic Labs / AIRS-Bench lane, [2026-05-19](../2026-05-19/04-research-progress.md)) now have a flagship proof point to reference. If you have *any* math/science depth, this is the moment to frame it as "I can verify and orchestrate AI-generated research output," not "I know the domain."
- **Startup lens:** The bottleneck this exposes is **verification of AI-generated discovery.** A model can now *propose* a result; someone (or something) has to *check* it. The durable wedge is the **verification harness for AI-generated research** — the same eval-against-reality thesis as MCP-Atlas/Toolathlon ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)), pointed at math/science output. *LemmaBench* (arXiv 2602.24173) is the open-source proof this is buildable.
- **Insight:** The result is impressive **because it's checkable.** That's the whole lesson — as models generate more (proofs, code, designs), the scarce, compounding skill is **cheap, trustworthy verification.** Every capability jump *raises* the value of being the person/tool that can confirm the output. Bet there.

→ Cross-link: [`01` §3 Jack Clark's Nobel timeline](./01-big-lab-moves.md#3-jack-clark) · [2026-05-22/04 §1 verify-against-reality](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).

---

## 2. The eval literature converges: test-time scaling + single-→multi-agent comparison {#2-eval-convergence}

**What it is:** Two strands of the agent-evaluation literature are converging on the questions deployment teams actually have:

- **"Benchmark Test-Time Scaling of General LLM Agents"** (`arXiv 2602.18998`) — measures how agent performance scales when you spend *more compute at inference* (more steps, more samples, more verification passes). This is the empirical backbone of the **cost-vs-quality routing** decision you've been building toward all week: it tells you *when* spending more test-time compute actually buys accuracy and when it just burns tokens.
- **"A Comprehensive Evaluation of LLM Reasoning: From Single-Model to Multi-Agent Paradigms"** (`arXiv 2601.13243`) — directly compares single-model reasoning against multi-agent setups under matched conditions, continuing the "is multi-agent actually worth it?" thread this archive has tracked since the Stanford "single-agent beats multi-agent under matched compute" result ([2026-05-09](../2026-05-09/04-research-progress.md)).

Together they answer: **how much should I scale, and should I use one agent or many?** — the two decisions that determine both your bill and your reliability.

**Sources:**
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/pdf/2602.18998) `[primary]`
- [arXiv 2601.13243 — A comprehensive evaluation of LLM reasoning: from single-model to multi-agent paradigms](https://www.arxiv.org/abs/2601.13243) `[primary]`
- [arXiv 2601.12538 — Agentic Reasoning for LLMs (the survey that frames both)](https://arxiv.org/abs/2601.12538) `[primary]`

### Why it matters to you

- **Job lens:** These two papers give you **defensible answers** to the most common agent-design interview questions: *"when does test-time scaling pay off?"* and *"single agent or multi-agent?"* Citing the test-time-scaling result + the single-vs-multi comparison signals you make these calls from evidence, not vibes — directly relevant to the cost-aware-routing skill the market is re-pricing up ([2026-05-22/05 §2](../2026-05-22/05-career-and-startup.md#2-reprice)).
- **Startup lens:** "Test-time scaling has diminishing returns past point X for task class Y" is a **margin insight.** If your product's COGS is inference, knowing the *scaling curve* for your task class is the difference between a profitable and an unprofitable price point. Measure it on your own workload before you set pricing.
- **Insight:** Notice the synchrony again — a **capability milestone** (§1), a **test-time-scaling** benchmark, and a **single-vs-multi-agent** comparison, all landing together. The field is simultaneously pushing capability *and* getting disciplined about *measuring its cost.* Read with both: build toward the capability, price it with the measurement.

→ Cross-link: [2026-05-09/04 single-agent vs multi-agent under matched compute](../2026-05-09/04-research-progress.md) · [2026-05-22/03 §1 the cost lever these papers justify](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-22/04 §2 the agentic-reasoning taxonomy](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey).
