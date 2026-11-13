# Research Progress — 2026-08-02

arXiv, benchmarks, breakthroughs. What's moving the frontier this week and which pieces are worth reading if you have 45 minutes.

---

## 1. MCP 2026-07-28 Specification — formalized publication {#1-mcp-2026-07-28}

**What.** The **2026-07-28 Model Context Protocol Specification** — largest revision since MCP launched last year — went live 5 days ago with formal blog + changelog + updated Tier-1 SDKs. It closes a **10-week release-candidate window** during which SDK maintainers validated against real workloads.

**Why it belongs in the research file, not just the tools file.** MCP 07-28 is the **first protocol-layer specification in the LLM agent space to explicitly encode enterprise deployment concerns** — statelessness, header-based L7 routing, cache scoping, and OAuth 2.1 authentication are all *research decisions* about how agent protocols should compose at scale. The paper-shaped writeup you'd want to read is the [changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) itself.

**Sources.**
- [The 2026-07-28 Specification — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/) [primary]
- [Key Changes — MCP Changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) [primary]
- [MCP 2026-07-28: From Local Tool to Distributed Protocol — Agentic AI Foundation](https://aaif.io/blog/mcp-2026-07-28-whats-changing-and-how-to-migrate) [analysis]
- [MCP 2026 Roadmap: Stateless Core, Extensions & Enterprise Readiness — Obot](https://obot.ai/blog/mcp-is-growing-up-the-2026-roadmap-takes-shape/) [analysis]

**Why it matters to you.**

- **Job.** Working understanding of the 07-28 spec is fresh enough that even senior candidates haven't internalized it yet. Read the changelog line-by-line **once**; be able to explain **why stateless** ("horizontal scaling with plain L7 LB, no session store, CDN-friendly cache scoping") and **why OAuth 2.1** ("enterprise auth story stops requiring per-vendor extensions") in interview.
- **Startup.** The **extensions framework** is the sub-piece worth studying — it's the mechanism by which vendors can layer without forking. Any startup that sits on the MCP protocol needs to make an early decision about which of its extensions become **spec-track** vs. **vendor-specific**.
- **Insight.** **This is the first time an LLM-agent-space protocol has felt "operationally boring" in a good way.** Boring is what enterprise adoption needs. Watch for what the *next* revision consolidates — my expectation is a Server Cards / discovery-layer standardization by end of 2026.

`#mcp #protocol #stateless #oauth #spec`

---

## 2. MLGym — framework and benchmark for AI research agents {#2-mlgym}

**What.** **MLGym** is a recent framework and benchmark for advancing AI research agents — i.e., agents that themselves *do* ML research. Sits alongside earlier work like **Agentifying Agentic AI** (AAAI 2026 WMAC) that focuses on the coordination/structured-reasoning layer for agents to be *actually* agentic vs. reactive.

**Complementary papers worth tracking:**

- **HAS-Bench** — evaluating LLM-based **human–agent systems** under configurable human participation. The right benchmark for FDE-style deployments where a human is in the loop.
- **Dynamic Capability Scoping for Enterprise AI Agents** (ICML 2026 Agents in the Wild workshop) — synthetic dataset + three-source permission architecture. Relevant if you're doing anything that touches enterprise ACLs from an agent.
- **Understanding Persuasion in Long-Running Agents** — one of the more concerning eval papers of the summer; worth reading before you build anything customer-facing.
- **The Evolution of Tool Use in LLM Agents: From Single-Tool Call to Multi-Tool Orchestration** — survey-style; useful catch-up read if you missed the tool-use wave.

**Sources.**
- [Agentifying Agentic AI (AAAI 2026 WMAC) — arXiv 2511.17332](https://arxiv.org/html/2511.17332v2) [primary]
- [HAS-Bench — arXiv 2607.04329](https://arxiv.org/pdf/2607.04329) [primary]
- [Understanding Persuasion in Long-Running Agents — arXiv 2602.00851](https://arxiv.org/pdf/2602.00851) [primary]
- [The Evolution of Tool Use in LLM Agents — arXiv 2603.22862](https://arxiv.org/pdf/2603.22862) [primary]
- [Act As a Real Researcher — arXiv 2606.07462](https://arxiv.org/pdf/2606.07462) [primary]
- [A Visionary Look at Vibe Researching — arXiv 2604.00945](https://arxiv.org/pdf/2604.00945) [primary]
- [LLM Research Papers: The 2026 List (January to May) — Sebastian Raschka](https://magazine.sebastianraschka.com/p/llm-research-papers-2026-part1) [analysis]

**Why it matters to you.**

- **Job.** For MLE / AI-research-adjacent roles, **familiarity with the current research-agent benchmark landscape** is the differentiator. Read the MLGym setup + HAS-Bench methodology; be able to explain **why "human participation is configurable"** matters (interview one-liner: "because deployed FDE workflows have variable human oversight and the eval has to match the deployment shape, not the ideal-benchmark shape").
- **Startup.** If your product touches **agent orchestration or evaluation**, subscribe to the MLGym repo and read one HAS-Bench-style paper per week. It's the fastest way to keep your product roadmap ahead of what buyers will start asking about.
- **Insight.** The research field has **moved from "can this agent do X" to "under what human-oversight regime does this agent hold up"** — that reframe is going to drive the next 12 months of eval work. Plan portfolio and product around evaluation-in-context, not benchmark-max.

`#arxiv #agents #mlgym #has-bench #benchmarks`

---

## 3. Plan-and-Act + Agent-R1 — planning depth + end-to-end RL for long-horizon agents {#3-plan-and-act}

**What.** Two threads worth carrying:

- **Plan-and-Act** — improves planning of agents for long-horizon tasks. The pattern (plan first, act second) is the same principle behind Claude Code's plan mode ([`03` §2](./03-practical-skills-and-tools.md#2-claude-code-power-user)); this line of research is quantifying **why the plan-first structure beats "just prompt the model to think step by step."**
- **Agent-R1** — training powerful LLM agents with **end-to-end reinforcement learning**. Belongs in the same reading list as the **on-policy distillation** wave from May ([2026-05-11 through 2026-05-14](../2026-05-14/04-research-progress.md)) and last edition's **two RL post-training compute-allocation papers** ([2026-07-25 §2–3](../2026-07-25/04-research-progress.md)).

Related methodological work:

- **A Visionary Look at Vibe Researching** — arXiv 2604.00945; interesting reframe of "vibe coding" as a research practice.
- **Act As a Real Researcher** — arXiv 2606.07462; suite of benchmarks evaluating frontier LLMs + agentic harnesses across the research lifecycle.

**Sources.**
- [Plan-and-Act research (survey/tracking) — Raschka LLM Papers 2026 Part 1](https://magazine.sebastianraschka.com/p/llm-research-papers-2026-part1) [analysis]
- [Understanding Persuasion in Long-Running Agents — arXiv 2602.00851](https://arxiv.org/pdf/2602.00851) [primary]
- [Act As a Real Researcher — arXiv 2606.07462](https://arxiv.org/pdf/2606.07462) [primary]
- [A Visionary Look at Vibe Researching — arXiv 2604.00945](https://arxiv.org/pdf/2604.00945) [primary]

**Why it matters to you.**

- **Job.** For MLE / RL-adjacent roles, being able to name the **plan-and-act vs. reactive** distinction in an interview is a small but real signal. The Agent-R1 line of work also lands in **RL-for-agents** interview questions ("how would you train an agent end-to-end") — you don't need to have implemented it, but you should be able to explain the tradeoffs (**reward sparsity + credit assignment across long horizons vs. simpler SFT + verifier**).
- **Startup.** If you're building an **agent for a specific long-horizon workflow** (research, procurement, customer onboarding), the practical implication is: **plan-and-act structure is now the empirical baseline**, not a nice-to-have. Ship it that way from V0.
- **Insight.** The **reactive-agent vs. plan-first-agent divide** is going to be a bigger design question than most teams expect. It affects UX (does the user see the plan before execution?), evaluation (do you grade the plan or the outcome?), and cost (planning is often free relative to execution, so front-loading it is efficient).

`#arxiv #planning #rl #agent-r1 #plan-and-act`

---

## 4. First empirical evidence that AI safety refusals have real defensive value (Palo Alto Unit 42) {#4-safety-refusal-empirical}

**What.** The **Palo Alto Networks Unit 42** writeup covered fully in [`02` §1](./02-new-emerging.md#1-deepseek-hermes) is a research-relevant datum because it is the **first widely-cited in-the-wild campaign** where a red-team writeup can point at a **safety-refusal delta between providers** as the operative variable.

Concretely: **DeepSeek** completed the offensive tasks in the campaign; **Claude and OpenAI** refused. The delta was **not** discovered on a benchmark — it was discovered by a threat actor testing the models against real targets and choosing the model whose refusals were absent.

**This turns "safety refusal" into a measurable defensive artifact.** Previously, refusal-rate benchmarks (Anthropic's own **HarmBench**, [SEAL](https://arxiv.org/abs/2311.14324), etc.) could show that Model A refused N% of harmful prompts more often than Model B, but the *utility* of that refusal in a real adversarial context was implied, not demonstrated. Unit 42 demonstrates it.

**Research-agenda implications.**

- **Refusal-quality benchmarks need a "cost-of-defection" axis** — i.e., not just "did the model refuse" but "did the refusal actually change what the adversary could achieve." Unit 42 shows the empirical shape; the research literature has to catch up.
- **Provider-differentiated refusal architectures** become studyable. Anthropic's constitutional AI, OpenAI's RLHF+system-prompt layering, DeepSeek's (relative) absence, and Meta's open-weight publication all become datapoints in the same empirical study rather than three separate philosophy debates.
- **Red-teaming methodology** should now include **provider-cross-check** as a standard step in any writeup of an LLM-enabled attack.

**Sources.**
- [Chinese-Speaking Threat Actor Harnesses AI Models for Autonomous Cyberattacks — Unit 42](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/) [primary]
- [DeepSeek Ran Autonomous Cyberattacks That Claude and OpenAI Safety Controls Blocked — TechTimes](https://www.techtimes.com/articles/322582/20260801/deepseek-ran-autonomous-cyberattacks-that-claude-openai-safety-controls-blocked.htm) [secondary]
- [Frontier Red Team — Anthropic](https://www.anthropic.com/research/team/frontier-red-team) [primary]

**Why it matters to you.**

- **Job.** If you're targeting **AI-safety adjacent roles** (Anthropic Frontier RT, DeepMind Safety, xAI red-team, or bank/consulting AI-assurance), this Unit 42 writeup is the **best 30-minute research read of the summer**. It's short, it's causal, and it hands you an argument that "safety work has commercial value" — an argument you will need in interview against the "safety is a cost-center" prior.
- **Startup.** The pitch template is in [`02` §1](./02-new-emerging.md#1-deepseek-hermes). At the research level, the **methodology gap between refusal benchmarks and this real-world evidence** is a viable PhD-thesis-shaped hole; if you're deciding between a startup and a PhD, this specific gap could tip you either way.
- **Insight.** **The commercial argument for safety just got its "the market speaks" moment** — for the first time, a threat-intel firm has documented model selection based on refusal profile. Expect this to reshape the next 12 months of policy conversations, especially in the EU where the AI-Act enforcement window ([`01` §1](./01-big-lab-moves.md#1-eu-ai-act)) is now live.

`#arxiv #safety #refusals #red-team #unit-42`

---

## 5. Anthropic Sonnet 5 benchmark landscape (published context) {#5-sonnet-5-benchmarks}

**What.** Sonnet 5 (Jun 30) results as they've settled after ~5 weeks of independent evaluation:

- **SWE-bench Verified: 72.7%** (Sonnet 4.6 was 62.3%; Opus 4.8 is 79.4%; Opus 5 hit 96.0% at launch per [2026-07-25 §1](../2026-07-25/01-big-lab-moves.md#1-opus-5))
- **Terminal-bench: 76.1%** (Sonnet 4.6 was 55.4%)
- **Anthropic agentic-coding benchmark: 63.2%** (Sonnet 4.6 58.1%, Opus 4.8 69.2%)
- **Knowledge-work benchmark**: Sonnet 5 (80.4%) actually **edges past Opus 4.8 (74.6%)** — the first Sonnet-tier model to do so on a headline knowledge benchmark.

**Why this belongs in the research file.** The **Sonnet-5-beats-Opus-4.8 on a knowledge benchmark** result is a real inversion — historically the Opus tier has dominated knowledge tasks by a comfortable margin. It changes the "which model do I use for research/summarization" default, and it changes the research question about **whether model-tier corresponds to task-difficulty stratification** (the honest answer looks increasingly like "not cleanly").

**Sources.**
- [Introducing Claude Sonnet 5 — Anthropic](https://www.anthropic.com/news/claude-sonnet-5) [primary]
- [Claude Sonnet 5 Benchmarks Explained — Vellum](https://www.vellum.ai/blog/claude-sonnet-5-benchmarks-explained) [analysis]
- [Claude Sonnet 5: Benchmarks, Pricing, and What Developers Need to Know — Cosmic JS](https://www.cosmicjs.com/blog/claude-sonnet-5-benchmarks-pricing-developers) [analysis]
- [Claude Opus 5 vs Sonnet 5 — Coursiv](https://coursiv.io/blog/claude-opus-5-vs-sonnet-5) [analysis]

**Why it matters to you.**

- **Job.** In interview loops that ask you to **defend a model choice**, the Sonnet-5-on-knowledge-tasks result is a clean way to show you're reading benchmark deltas rather than trusting model-tier priors. Interview line: "for the knowledge-summarization sub-task I ran Sonnet 5 because the Vellum eval shows it edges Opus 4.8 on the knowledge benchmark at a third of the cost — I only escalate to Opus 5 for the planning stage."
- **Startup.** **Recompute your model-selection matrix.** If you had a "knowledge = Opus, code = Sonnet" default, this is the month to test whether that default still holds against your own workload. The economics of routing changed again.
- **Insight.** **Benchmark inversions between tiers are now normal enough that any 6-month-old routing decision needs a re-test.** Set a quarterly recurring calendar event to re-run your top-3-workload evals against the current model lineup.

`#anthropic #sonnet-5 #benchmarks #swe-bench #knowledge-work`

---

## What to add to your queue

If you have 45 minutes this weekend, read in this order:

1. **The MCP 2026-07-28 changelog** — [§1](#1-mcp-2026-07-28). 10 minutes.
2. **The Palo Alto Unit 42 writeup** — [§4](#4-safety-refusal-empirical). 20 minutes. The most consequential single read of the week.
3. **The Vellum Sonnet 5 benchmark writeup** — [§5](#5-sonnet-5-benchmarks). 15 minutes; the number that changes your routing this month.

Skip the arXiv papers this week unless you're specifically prepping for an MLE interview. The regulatory + security stories dominate the news value.
