# Research Progress — 2026-06-05

The single sharpest research signal of the gap window: **MCP-eval professionalized in 14 days.** Three new benchmarks — **MCPAgentBench, ETOM, MSB** — replaced the era of mock-tool agent evals. Plus a unified **test-time scaling framework** for general LLM agents that adopts MCP as its backbone. *The eval bar moved.*

Tags: `#arxiv #research #benchmarks #mcp #agents #eval #ttscaling`

---

## 1. The MCP-eval triple: MCPAgentBench + ETOM + MSB {#1-mcpagentbench}

**The shift:** Across late 2025 and into mid-2026, agent evaluation moved through three distinct generations:

1. **Mock-tool** (AgentBench, SWE-bench original) — synthetic tools, closed sandbox.
2. **Real-application** (TheAgentCompany, Toolathlon/Tool-Decathlon, MCP-Atlas) — real apps but typically curated/cleaned interfaces.
3. **Real-MCP-server with distractors** (MCPAgentBench, ETOM, MSB) — actual MCP servers scraped from production marketplaces, with adversarial / distractor tools that mirror real-world noise.

This 3rd generation is what shipped in the gap window. The triple:

### MCPAgentBench (arXiv 2512.24565)

A real-world task benchmark for evaluating LLM agent MCP tool use, constructed from:

- **841 authentic tasks**
- **20,000+ MCP tools** scraped from **MCP Marketplace, GitHub, Hugging Face**
- **Dynamic sandbox environment** with **distractor tools** in each task's candidate list
- Metrics for **task completion rate** AND **execution efficiency** (tokens, steps, latency)

### ETOM (arXiv 2510.19423)

A **five-level benchmark** for evaluating **tool orchestration** within the MCP ecosystem — graded by orchestration complexity (single-tool → multi-tool sequential → parallel → conditional → meta-orchestration).

### MCP Security Bench / MSB (arXiv 2510.15994)

Benchmarks **attacks against the Model Context Protocol** in LLM agents — prompt injection through tool descriptions, malicious-tool installation, cross-tool data exfiltration. The cyber-side complement to MCPAgentBench's functional side.

**Plus:** "Benchmark Test-Time Scaling of General LLM Agents" (arXiv 2602.18998) adopts **MCP as the backbone** of a unified framework for testing how agents scale at inference time across tool/task surface complexity.

**Sources:**
- [arXiv 2512.24565 — MCPAgentBench: A Real-world Task Benchmark for Evaluating LLM Agent MCP Tool Use](https://arxiv.org/abs/2512.24565) `[primary]`
- [arXiv PDF — MCPAgentBench](https://arxiv.org/pdf/2512.24565) `[primary]`
- [arXiv 2510.19423 — ETOM: A Five-Level Benchmark for Evaluating Tool Orchestration within the MCP Ecosystem](https://arxiv.org/pdf/2510.19423) `[primary]`
- [arXiv 2510.15994 — MCP Security Bench (MSB): Benchmarking Attacks Against Model Context Protocol in LLM Agents](https://arxiv.org/pdf/2510.15994) `[primary]`
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/pdf/2602.18998) `[primary]`
- [GitHub — VoltAgent/awesome-ai-agent-papers (2026 curated list)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [GitHub — weitianxin/Awesome-Agentic-Reasoning](https://github.com/weitianxin/Awesome-Agentic-Reasoning) `[aggregator]`

### Why it matters to you

- **Job lens:** Reading even one of these papers end-to-end and citing it in an interview puts you above 90% of candidates. **Pick MCPAgentBench** — it's the one that maps most directly to the Opus 4.8 dynamic-workflow demo you're shipping this weekend. Reading time: ~90 minutes including the appendix. ROI per hour: highest of anything in this edition.
- **Startup lens:** **The eval-as-a-service category is now well-defined.** Three different attack surfaces (functional tasks, orchestration complexity, security) each justify their own evaluation product. Judgment Labs is the leading commercial player; the *vertical* equivalents (Eval-for-Healthcare-Agents, Eval-for-Finance-Agents) are unfunded.
- **Insight:** Anthropic and Google now both publish *agent* benchmark numbers on **MCP-Atlas** (Gemini 3.5 Flash: 83.6%; recent Opus claims comparable). The publishing labs *want* this becoming the standard, because real-MCP eval favors the labs investing most in MCP — which is Anthropic. **Watch for whether Anthropic publishes against MCPAgentBench in release notes within 30 days.** If yes, MCPAgentBench is the new "GPQA Diamond" for agents.

---

## 2. Test-time scaling for general LLM agents — a unified framework {#2-ttscaling}

**Paper:** *"Benchmark Test-Time Scaling of General LLM Agents"* (arXiv 2602.18998).

**Core claim:** Recent LLMs exhibit *effective* test-time scaling abilities — given more thinking time / more reasoning tokens, they get better — but there's an **evaluation gap**: most existing benchmarks don't measure whether *agents* (not just LLMs) can:

1. Infer user intent at increasing task complexity.
2. Select correct tools from a *large, noisy* tool surface.
3. Scale their performance *predictably* under a unified evaluation framework.

The paper introduces such a unified framework using **MCP as the backbone** for tool exposure.

**Sources:**
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/pdf/2602.18998) `[primary]`
- [HTML version — arXiv 2602.18998v1](https://arxiv.org/html/2602.18998v1) `[primary]`

### Why it matters to you

- **Job lens:** Test-time scaling is the *direct* research-side analog of the **`/effort` slider in Claude Opus 4.8** ([`01` §3](./01-big-lab-moves.md#3-opus-4-8)). Being able to talk about how the Opus 4.8 effort levels (`low → medium → high → xhigh → ultracode`) instantiate the test-time-scaling research, citing this paper, is a *deep* interview answer that connects product to research.
- **Startup lens:** A *cost-aware effort-level recommender* — "for this task at this risk-tolerance, here's the effort level that minimizes total cost-of-completion" — is a wedge that lives directly on top of `/effort`. Likely an open-source library before it's a startup; founder opportunity goes to whoever ships the OSS lib + the SaaS dashboard together.
- **Insight:** The research is now *ahead* of the product in formalizing what `/effort` actually is. Read the paper and you'll understand `/effort` better than most Anthropic users. Use that.

---

## 3. Survey for the weekend — Agentic Reasoning {#3-survey}

The **Agentic Reasoning for Large Language Models** survey is the highest-ROI single read for synthesizing the last 12 months of agent research into a three-layer taxonomy (**foundational / self-evolving / collective**) — flagged in [2026-05-22/04 §2](../2026-05-22/04-research-progress.md#2-agentic-reasoning-survey). The companion GitHub curates the related work.

**Sources:**
- [GitHub — weitianxin/Awesome-Agentic-Reasoning](https://github.com/weitianxin/Awesome-Agentic-Reasoning) `[aggregator]`
- [arXiv 2503.16416 — A Survey on Evaluation of LLM-based Agents](https://arxiv.org/html/2503.16416v2) `[primary]` (complementary eval-side survey)

### Why it matters to you

- **Job lens:** A 90-minute weekend read of one survey gives you the *vocabulary* to discuss agent design at the level a frontier-lab interviewer expects. Better ROI than another LeetCode hour.
- **Startup lens:** Surveys reveal *gaps* — the layers least covered in the three-layer taxonomy are the layers where startups can defensibly claim novelty. Read with a "what's missing here?" eye.
- **Insight:** The field has *matured* enough to have a real survey-and-taxonomy stage. That maturity is itself a signal — the next 12 months will reward depth over novelty.

→ Cross-link: [`03` §1 dynamic workflows playbook](./03-practical-skills-and-tools.md#1-dynamic-workflows) · [`03` §4 MCP verification stack](./03-practical-skills-and-tools.md#4-mcp-verification).
