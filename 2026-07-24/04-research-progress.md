# Research Progress — 2026-07-24

The research signal converging this month: **outcome leaderboards are done, process traces are in.** A cluster of arXiv papers published in the last three weeks converges on the same claim — the way agents *fail* matters more than whether they finish, and evaluations built around trajectory analysis, skill decomposition, and safety-pragmatism tradeoffs give you a signal that a single success rate hides. This is the research face of the same shift you see in **Bespoke Labs' funding** ([`02` §1](./02-new-emerging.md#1-bespoke-environments)) and **OpenAI Presence's pre-deployment simulation** ([`01` §2](./01-big-lab-moves.md#2-openai-presence)) — and it slots directly on top of yesterday's **long-horizon-agent + memory** front ([2026-07-23/04 §1](../2026-07-23/04-research-progress.md#1-long-horizon)).

Tags: `#research #arxiv #benchmarks #agents #evaluation #safety`

---

## 1. From outcome leaderboards to process-trace benchmarks {#1-process-benchmarks}

**What happened:** A convergent set of new arXiv papers is pushing agent evaluation from **"did the agent solve the task?"** to **"how did it get there, at which skill, at what safety cost?"** The four with the highest signal-to-noise this month:

### **AgentAtlas — Beyond Outcome Leaderboards for LLM Agents** ([arXiv 2605.20530](https://arxiv.org/html/2605.20530v1))

Argues explicitly that single-number leaderboards are actively misleading for agents, because two agents with the same success rate can have wildly different **efficiency, safety, and generalization profiles**. Proposes a **multi-dimensional atlas** built from trajectory features: **tool-call efficiency, redundant-action rate, safety-margin, decomposition depth, retry patterns.** The most-cited *position* paper of the summer for anyone building agent products. Adjacent to [yesterday's Long-Horizon Terminal-Bench](../2026-07-23/04-research-progress.md#1-long-horizon) — Long-Horizon-TB provides the *task substrate*; AgentAtlas provides the *evaluation philosophy* over it.

### **AgenticDataBench** ([arXiv July 2](https://letsdatascience.com/news/researchers-release-agenticdatabench-for-llm-data-agents-f3a2fd61))

Instantiates the AgentAtlas philosophy in a concrete domain: **data agents across 15 domains × 5 real-world B2B fintech workflows**. Grades not on "was the final SQL right" but on **skill-level performance** — did the agent handle **schema inspection, joins, cleaning, visualization, and business-context reasoning** at each step? Ships with a **GitHub testbed + Hugging Face dataset** for reproduction. First benchmark of the year where you can *see* which specific data-analyst skill the frontier models are still weak at.

### **ManagerBench — the safety-pragmatism trade-off in autonomous LLMs**

Measures a specific failure mode of managed agents (Presence, Managed Agents, ADK): under production pressure, do agents **pragmatically bend safety constraints** to get a customer unstuck? Ships a small task family that pits *policy-compliant refusal* against *customer-outcome success*, with fine-grained scoring on the tradeoff curve. **Directly relevant** to anyone deploying a governed agent in a customer-facing role — and it maps to the [OpenAI×HF containment breach story](../2026-07-22/01-big-lab-moves.md#1-openai-hf-breach) with uncanny precision: the reason HF had to reach for GLM-5.2 was *US models couldn't distinguish defender from attacker* — the pragmatism dial was set wrong.

### **Terminal-Bench — hard, realistic CLI tasks**

Benchmarks agents at **real terminal use** — long multi-step shell workflows, filesystem operations, package installs, environment reproduction, log parsing. The closest research proxy for "can this agent do what a working SWE does at a keyboard." Complements **SWE-bench** (Git-repo-scoped) by covering the *systems* side of engineering. Pairs with **Long-Horizon-Terminal-Bench** from [yesterday's edition](../2026-07-23/04-research-progress.md#1-long-horizon).

### The connecting thesis

All four rest on the same claim, in different form: **evaluation should look like a *replay*, not a *score*.** You watch the trajectory, decompose the skills, and grade the tradeoffs — you don't just check the final answer. Combined with the also-recent **"Evaluation and Benchmarking of LLM Agents: A Survey"** ([arXiv 2507.21504](https://arxiv.org/pdf/2507.21504)) — which taxonomizes ~80 recent agent benchmarks and was tracked in the [2026-07-06/04 practitioner list](../2026-07-06/04-research-progress.md) — the field now has both the philosophy and the map.

**Sources:**
- [arXiv — AgentAtlas: Beyond Outcome Leaderboards for LLM Agents (2605.20530)](https://arxiv.org/html/2605.20530v1) `[primary]`
- [Let's Data Science — Researchers Release AgenticDataBench for LLM Data Agents (Jul 2)](https://letsdatascience.com/news/researchers-release-agenticdatabench-for-llm-data-agents-f3a2fd61) `[secondary]`
- [arXiv — Evaluation and Benchmarking of LLM Agents: A Survey (2507.21504)](https://arxiv.org/pdf/2507.21504) `[primary]`
- [arXiv — HAS-Bench: LLM-Based Human-Agent Systems under Configurable Human Participation (2607.04329)](https://arxiv.org/pdf/2607.04329) `[primary]`
- [arXiv — Automated Benchmark Auditing for AI Agents and LLMs (2605.26079)](https://arxiv.org/pdf/2605.26079) `[primary]`
- [arXiv — DeepResearch Bench: A Comprehensive Benchmark for Deep Research Agents (2506.11763)](https://arxiv.org/pdf/2506.11763) `[primary]`
- [arXiv — Act As a Real Researcher: A Suite of Benchmarks Evaluating Frontier LLMs and Agentic Harnesses in Research Lifecycle (2606.07462)](https://arxiv.org/pdf/2606.07462) `[primary]`

### Why it matters to you

- **Job lens:** The interview question is shifting from *"which benchmark scores did you get?"* to *"what did your agent's failure trajectories look like, and how did you fix them?"* — because the people hiring you (FDE, Solutions, MLE at frontier labs) can no longer trust a single number, and they know it. **Practical move:** on any of your public agent projects, add a **"Failure Mode Analysis"** section to the README — 3 failure trajectories, what caused each, what you changed. That single section outperforms any leaderboard mention. Direct extension of the subagent-logging hook from [`03` §2 weekend micro-project](./03-practical-skills-and-tools.md#2-claude-code-defaults) — the log IS your trajectory-capture tool.
- **Startup lens:** **AgentAtlas is a thesis paper for eval-tooling startups** — it names the exact metrics (tool-call efficiency, redundant-action rate, safety-margin, decomposition depth, retry patterns) that a productized eval harness needs to compute. Bespoke Labs ([`02` §1](./02-new-emerging.md#1-bespoke-environments)) is one instance; there's room for **language-specific** (Python agents, TypeScript agents, shell agents) and **vertical** (data agents, CX agents, security agents) versions. If you were looking for a wedge that's *rigorous, novel, and buyer-legible*, this is the strongest one all summer.
- **Insight:** Watch the *citations arrow*. AgentAtlas is a **position paper** — its value depends on how many downstream benchmarks and products adopt its multi-dimensional atlas. AgenticDataBench already did, in a specific domain. Every time you see a new agent benchmark this fall that grades on more than one axis, it's a data point that the atlas approach is winning. This is the kind of "which paper is quietly restructuring the field" signal that pays off if you catch it early — **reference AgentAtlas in an interview or a project README now**, before it becomes the standard citation.

→ Cross-link: [`02` §1 Bespoke Labs — the productized instance of this thesis](./02-new-emerging.md#1-bespoke-environments) · [`03` §2 subagent logging as a lightweight trajectory-capture tool](./03-practical-skills-and-tools.md#2-claude-code-defaults) · [2026-07-23/04 §1 the long-horizon-agent + memory front (task substrate)](../2026-07-23/04-research-progress.md#1-long-horizon) · [2026-07-22/04 §1 AgentRedBench + AGENTREDGUARD (the security instance of the same shift)](../2026-07-22/04-research-progress.md#1-agentredbench) · [2026-05-22/04 §1 MCP-Atlas / Toolathlon real-tool benchmarks (the eval-substrate lineage)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).
