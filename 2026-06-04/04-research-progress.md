# Research Progress — 2026-06-04

The **MCP-benchmark wave** that [2026-05-22/04 §1](../2026-05-22/04-research-progress.md) introduced (MCP-Atlas, Tool Decathlon / Toolathlon) hardened into a **category of evals** this week — and crucially, **the security half landed alongside the capability half**. Below: four arXiv landings worth knowing the names of, plus the largest empirical MCP-usage study to date.

Tags: `#arxiv #benchmarks #mcp #agents #security #verification`

---

## 1. The MCP-benchmark wave: capability + security in the same fortnight {#1-mcp-benchmark-wave}

**The four papers + one study, in one table:**

| Paper | What it measures | Why it matters |
|---|---|---|
| **MCP-AgentBench** (arXiv 2509.09734) | Real-world language-agent performance via MCP-mediated tools. **33 operational MCP servers · 188 distinct tools · 600 systematically designed queries · 6 categories.** | The capability bar: "can your agent *discover and use* tools across a real, heterogeneous server fleet?" |
| **MCPMark** (arXiv 2509.24002) | Stress-tests realistic and comprehensive MCP use under load + diversity. Frames MCP as the standard interface giving LLMs "eyes and hands." | The reliability bar: same surface, but under stress. |
| **MCPAgentBench** (arXiv 2512.24565) — distinct from MCP-AgentBench above | Dynamic sandbox environment; metrics for tool selection ability, task completion rate, execution efficiency. | The *efficiency* bar — not just "did it work," but "how cheaply / quickly." |
| **MCPTox** (arXiv 2508.14925) | **Tool poisoning attacks** on real-world MCP servers — adversarial baseline. | The first dedicated security benchmark for **the supply-chain risk MCP introduces** (an agent trusts a tool it discovered). |
| **MCPSecBench** (arXiv 2508.13220) | Systematic security benchmark + playground for testing MCP protocol-level behavior. | The protocol-level security bar — paired with MCPTox covers tool + protocol attack surfaces. |
| **"How are AI agents used? Evidence from 177,000 MCP tools"** (arXiv 2603.23802) | Empirical study of 177,436 agent tools created Nov 2024 → Feb 2026, across public MCP server repos. | **The composition data: 67% of agent tools are software-development tools; 90% of MCP server *downloads* are dev tools.** Tells you where the surface area actually is. |

**Sources:**
- [arXiv 2509.09734 — MCP-AgentBench: Evaluating Real-World Language Agent Performance with MCP-Mediated Tools](https://arxiv.org/abs/2509.09734) `[primary]`
- [arXiv 2509.24002 — MCPMark: A Benchmark for Stress-Testing Realistic and Comprehensive MCP Use](https://arxiv.org/pdf/2509.24002) `[primary]`
- [arXiv 2512.24565 — MCPAgentBench: A Real-world Task Benchmark for Evaluating LLM Agent MCP Tool Use](https://arxiv.org/pdf/2512.24565) `[primary]`
- [arXiv 2508.14925 — MCPTox: A Benchmark for Tool Poisoning Attack on Real-World MCP Servers](https://arxiv.org/pdf/2508.14925) `[primary]`
- [arXiv 2508.13220 — MCPSecBench: A Systematic Security Benchmark and Playground for Testing MCP](https://arxiv.org/pdf/2508.13220) `[primary]`
- [arXiv 2603.23802 — How are AI agents used? Evidence from 177,000 MCP tools](https://arxiv.org/abs/2603.23802) `[primary]`

### Why it matters to you

- **Job lens:** **The verification-against-real-tools skill from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) just got five citable methodologies.** When you write your portfolio README, name-drop **MCP-AgentBench (33 servers / 188 tools / 600 queries)** as your *method*, and **MCPTox + MCPSecBench** as the *security threat model*. Solutions / FDE interviews ask "how do you know your integration is robust?" — those are the names you cite.
- **Startup lens:** The 177K-tools study tells you **where the MCP supply currently lives: 67% dev tools, 90% of downloads dev tools.** Translation — **the consumer-MCP layer is *under-supplied*** relative to what the Apple Extensions surface ([`01` §3](./01-big-lab-moves.md#3-wwdc)) will demand. There's a non-obvious wedge here: **a small, polished, security-vetted MCP server pack for consumer/SMB use cases** (calendar, email, drive, notion, billing) — bundled with eval-tested safety properties.
- **Insight:** The structure of this week's research output mirrors the structure of the product output. **Capability (MCP-AgentBench / MCPMark) and security (MCPTox / MCPSecBench) landed in the same arXiv window — exactly when Anthropic shipped dynamic workflows + Apple positioned Extensions for users.** Researchers and product teams are converging on the same problem: *MCP is the standard, and the next year is about hardening it.* That's where defensive skill investment compounds.

→ Cross-link: [`03` §1 dynamic workflows playbook (uses these as the verification methodology)](./03-practical-skills-and-tools.md#1-dynamic-workflows) · [2026-05-22/04 §1 MCP-Atlas / Toolathlon](../2026-05-22/04-research-progress.md) · [`02` §1 OpenRouter (the *routing* surface that needs this verification)](./02-new-emerging.md#1-openrouter).

---

## 2. Adjacent: the agentic-AI research thread continues (carried watchlist) {#2-adjacent}

Not new today, but worth knowing they're still alive — these threads continue to land follow-on work weekly:

- **Real-tool agent eval** (continued from [2026-05-22/04 §1](../2026-05-22/04-research-progress.md)): MCP-Atlas / Toolathlon / Tool Decathlon. The Toolathlon "**32 apps, 604 tools**" figure remains the largest published real-tool eval surface.
- **PostTrainBench / recursive-improvement research** (continued from [2026-05-21/04](../2026-05-21/04-research-progress.md)): the *staffed* face of this is now **Karpathy's pre-training team at Anthropic** ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)).
- **Conformal prediction over agent messages** ([2026-05-20/04 CommCP](../2026-05-20/04-research-progress.md)) — the statistical underpinning of "I can give a *confidence* over an agent's claim." Useful primitive for any verifier-pattern build.
- **Multi-agent vs single-agent under matched compute** ([2026-05-09](../2026-05-09/04-research-progress.md) Stanford result) — single-agent wins at matched compute, but **dynamic workflows ([`01` §2](./01-big-lab-moves.md#2-opus-4-8)) blur this** because the orchestrator + workers count as one "session." Watch for the Stanford follow-up that re-runs the comparison post-dynamic-workflows.

**Why this matters:** the **arXiv → product** loop is shorter than it has ever been. Two months from the Stanford "single-agent wins" paper, dynamic workflows ship as a feature — they're a *response* to the paper, not independent of it. Reading arXiv is now a leading indicator of next quarter's product, not a side hobby.

→ Cross-link: [`03` §1 dynamic workflows](./03-practical-skills-and-tools.md#1-dynamic-workflows) · [2026-05-22/01 §3 Karpathy → Anthropic pre-training](../2026-05-22/01-big-lab-moves.md#3-karpathy).
