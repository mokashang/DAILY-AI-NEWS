# Research Progress — 2026-06-24

The 30-day arc on agent benchmarks: from **real-tool eval** (05/22's MCP-Atlas / Toolathlon) → to **real-world enterprise workflows + verifier-of-verifiers**. The two-step move: (a) **planning** got its own diagnostic benchmark (APB, 4,209 cases × 22 domains); (b) **vertical workflows** got long-horizon (thousand-day) sims (RetailBench) plus scientific-pipeline ground-truth (Nature meta-analysis); and (c) **the verifier itself** became a research subject ("Verifying the Verifiers," ICLR Workshop RSI). The frontier of *measurement* moved from "tools" to "trajectories under uncertainty."

Tags: `#research #arxiv #benchmarks #planning #verification #agents #iclr`

---

## 1. The new agent-benchmark wave: planning, real-world workflows, and verifier-checking {#1-planning-and-real-world-benches}

**Three June-2026 arXiv drops to skim this weekend.** Each captures one face of the same shift — *agent eval is moving from "did it use the right tool" to "did it plan, sustain, and self-verify over a real horizon."*

### Agent Planning Benchmark (APB) — arXiv:2606.04874

- **What it is:** A **planning-specific diagnostic benchmark**: 4,209 multimodal cases across 22 domains.
- **Five settings, building from easy to hard:** holistic planning · feedback-conditioned step-wise planning · robustness under extraneous tools · broken-tool conditions · unsolvable tasks (the most under-rated condition — does the agent *know* it can't finish?).
- **Why it matters:** answers the question MCP-Atlas couldn't ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) — *not "can the agent find the tool"* but *"can the agent build and revise a plan when tools break or the task is impossible."*

→ [arXiv 2606.04874 — Agent Planning Benchmark: A Diagnostic Framework for Planning Capabilities in LLM Agents](https://arxiv.org/abs/2606.04874) `[primary]`

### RetailBench — arXiv:2606.15862

- **What it is:** A **data-grounded retail-operations simulation**. Models a single-store supermarket as a partially-observable decision process.
- **Scale:** **thousand-day** simulations. Agent must manage pricing, replenishment, supplier selection, shelf assortment, inventory aging, customer feedback, external events (e.g. weather, holidays), and cash-flow constraints.
- **Why it matters:** the first benchmark that explicitly stresses **long-horizon coherence with cash-flow constraints** — the closest published proxy for "could you actually run a small business with an agent." This is *the* benchmark for vertical-agent founder-thinking.

→ [arXiv 2606.15862 — RetailBench: Benchmarking long-horizon reasoning and coherent decision making of LLM agents in realistic retail environments](https://arxiv.org/abs/2606.15862) `[primary]`

### Benchmarking LLM Agents on Meta-Analysis Articles from Nature Portfolio — arXiv:2606.17041

- **What it is:** Evaluates agents on the **full retrieval → screening → synthesis pipeline** of scientific meta-analysis, with ground-truth answers from published Nature-portfolio meta-analyses.
- **Why it matters:** end-to-end scientific-workflow ground truth at peer-review quality — extends the [SciAgentArena (~200 tasks)](https://arxiv.org/list/cs.AI/current) thread into specifically the *meta-analysis* subdomain that the [Karpathy-at-Anthropic / automate-AI-research](../2026-05-22/01-big-lab-moves.md#3-karpathy) thread points at.

→ [arXiv 2606.17041 — Benchmarking LLM Agents on Meta-Analysis Articles from Nature Portfolio](https://arxiv.org/abs/2606.17041) `[primary]`

### Why this matters to you (the three together)

- **Job lens:** "Agentic evaluation" job descriptions are starting to specify the *evaluation regime* — planning-only, real-world workflow, or verifier-checking. Knowing which is which and what each tests for is now the difference between *generic ML literacy* and *role-specific signal*. Pick **one** of these three and read it cover to cover before Friday — that one becomes a 30-second talking point on call.
- **Startup lens:** **RetailBench is the most important of the three for founders** — it's the closest peer-reviewed proxy for "is this agent fundable as a vertical-SMB product." If your STARTUPS.md has any vertical-AI wedge (legal, supply-chain, healthcare-back-office), benchmark your prototype against RetailBench's failure modes.
- **Insight:** The eval bar moved twice in 30 days — from *"mock tools" → "real tools"* ([2026-05-22](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) → now from *"single-action correctness" → "long-horizon, cash-constrained, self-verifying."* Each move makes the *verification* skill more valuable, not less. The 05/22 thesis ("verification is the new prompting") just held for another month.

→ Cross-link: [2026-05-22/04 §1 real-tool benchmarks](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [`03` §3 the Patch-the-Planet artifact uses the verification primitive](./03-practical-skills-and-tools.md#3-patch-planet-artifact) · [`05` §2 the re-priced skill list](./05-career-and-startup.md#2-fde-10x).

---

## 2. "Verifying the Verifiers" — the verifier itself becomes a research subject {#2-verifying-verifiers}

**What it is:** A paper accepted to the **ICLR 2026 Workshop on Recursive Self-Improvement (RSI)** that directly studies **how to know whether an agent verifier is itself correct.** Title: *"Verifying the Verifiers: Failure Attribution for Agentic Benchmark Diagnostics and Training Data Curation."*

**Why this is interesting:** the 05/22 archive (and most agent research before it) treats "the verifier" as an oracle. This paper points at the recursion — *if the verifier can be wrong, what verifies the verifier?* The proposed approach: **failure attribution** — trace each verifier error back to its root cause and use the attribution to (a) diagnose the benchmark, (b) curate training data for the next verifier generation.

**Sources:**
- [ICLR 2026 Workshop RSI — accepted papers list](https://recursive-workshop.github.io/papers.html) `[primary]`
- [Vector Institute — Agentic AI evaluation strategies (companion analysis)](https://vectorinstitute.ai/agentic-ai-evaluation-strategies/) `[analysis]`
- [QuantumBlack (McKinsey) — Evaluations for the agentic world](https://medium.com/quantumblack/evaluations-for-the-agentic-world-c3c150f0dd5a) `[analysis]`

### Why it matters to you

- **Job lens:** The next 12 months of AI-assurance / pre-deployment-eval hiring (the EO-Clearinghouse-driven lane) will explicitly ask: *"Whose verification do you trust, and why?"* Reading this paper gives you the language to answer.
- **Startup lens:** "Verifier-attribution-as-a-service" — a tool that explains *why* an agent verifier flagged or missed something — is a thin, unbuilt layer for the eval-stack market. Watch for the first $5M seed in this category.
- **Insight:** Every layer of an agent stack eventually gets meta-leveled. *Prompts → prompt-eval → eval-eval.* Plan your skill investments around being **one layer up** from where the field is — the value lives there.

---

## 3. Smaller arXiv items worth one line each {#3-other-research}

- **Auditing Multi-Agent LLM Reasoning Trees Outperforms Majority Vote and LLM-as-Judge** — arXiv:2602.09341. The tree-audit primitive is the cleanest way to extract signal from multi-agent traces. Cite it when you write your subagent-economics note ([`03` §2](./03-practical-skills-and-tools.md#2-subagent-economics)).
- **Why Reasoning Fails to Plan: Planning-Centric Analysis of Long-Horizon Decision Making in LLM Agents** — arXiv:2601.22311. Pair with APB above for a fuller "why planning is the bottleneck" frame.
- **DeepAgent: A General Reasoning Agent with Scalable Toolsets** — arXiv:2510.21618. The scalable-toolset framing is the architectural counterpart to the real-tool benchmark wave.
- **Holistic Agent Leaderboard: The Missing Infrastructure for AI Agent Evaluation** — arXiv:2510.11977. Infrastructure layer; not novel research but the right reference for "where is the agent eval ecosystem going."

Sources: see [arXiv cs.AI current](https://arxiv.org/list/cs.AI/current) `[primary]` for the live list.
