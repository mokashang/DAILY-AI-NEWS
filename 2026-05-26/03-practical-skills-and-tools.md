# Practical Skills & Tools — 2026-05-26

You've packaged a **Skill** ([2026-05-23/03 §1](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills)) and re-modeled your **agent spend** ([2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-metering)). Today's 20 minutes connect them: the **Skills vs MCP vs Subagents decision** — the three ways to extend Claude Code, each with very different *context-token* costs. Getting this architecture right is the difference between a setup that's cheap and one that silently burns tens of thousands of tokens before it does any work — which, with **June-15 metering at T-20**, is now a priced mistake.

Tags: `#claude-code #skills #mcp #subagents #cost #playbook`

---

## 1. Skills vs MCP vs Subagents — pick the cheap primitive {#1-skills-vs-mcp}

The three extension mechanisms, by **context cost** and **right use**:

| Primitive | Context cost | Use it for | Cost note |
|---|---|---|---|
| **Skills** | **~100 tokens until activated** | Teaching Claude **"how to do X"** — a reusable procedure it loads on demand | Cheapest by far; the body loads only when the trigger fires (cf. the `SKILL.md` trigger discipline, [2026-05-23/03 §1](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills)) |
| **MCP servers** | **~55K tokens for a typical 5-server setup, *always on*** | **Accessing external systems** (DBs, SaaS APIs, your infra) | Every connected server injects tool defs into *every* request — use **Tool Search** to load on demand (−~95%) and **disable unused** via `/mcp` |
| **Subagents** | A **fresh context window** per delegation | **Delegating a bounded task** so it doesn't pollute the main context | Pin each to **Sonnet** (Opus only for the orchestrator); cap tools in YAML ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) |

**The rule of thumb:** reach for a **Skill** first (cheap, on-demand), an **MCP server** only when you genuinely need to touch an external system, and a **subagent** when a task is big enough to warrant its *own* context. Most people over-use always-on MCP servers and under-use Skills — exactly the habit the June-15 meter punishes.

**Sources:**
- [Analytics Vidhya — 23 Claude Code token-saving tips](https://www.analyticsvidhya.com/blog/2026/05/tips-for-claude-code-token-saving/) `[analysis]`
- [k21academy — Claude Code: Skills vs Sub-agents vs MCP](https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/) `[analysis]`
- [Anthropic — Claude Code: manage costs (official docs)](https://code.claude.com/docs/en/costs) `[primary]`

### Why it matters to you

- **Job lens:** "I know *when* to use a Skill vs an MCP server vs a subagent, and what each costs in context tokens" is a senior-sounding, very current answer in any agent-tooling interview — and it's the literal architecture decision an FDE makes wiring Claude into a client's stack on a budget. Pair it with the cost re-model ([2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-metering)) for a complete story.
- **Startup lens:** This *is* your product's per-request COGS. A vertical-agent that over-loads MCP servers pays ~55K tokens of overhead on every call before it earns a cent — choosing the cheap primitive is the margin between a profitable product and a leaky one.
- **Insight:** June 15 is forcing a skill that was always *good* engineering to become *priced* engineering. The pattern repeats across the archive — **cost-awareness is moving from optional to mandatory.** Build the instinct now, on your own setup, while mistakes are cheap.

→ Cross-link: [2026-05-23/03 §1 the `SKILL.md` unit of value](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills) · [2026-05-25/03 §1 the spend re-model](../2026-05-25/03-practical-skills-and-tools.md#1-metering) · [2026-05-22/03 §1 the agent-team split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. Today's artifact move: the one-screen "architecture + cost" diagram {#2-artifact}

You now have the pieces — the **Skill** you packaged, the **agent-team split**, the **spend re-model**, and the **Skills/MCP/subagent decision** above. **Assemble them into one screen:** a diagram of your agent's architecture annotated with **which primitive, which model, and the token cost of each node** — at the top of your portfolio repo's README.

### Why it matters to you
- **Job lens:** A single annotated diagram that says "here's how I architected this agent for *capability and cost*" out-communicates paragraphs to a skimming recruiter — and answers the FDE question "how do you keep a client's bill predictable?" in one image.
- **Startup lens:** Relabel the same diagram "per-request COGS" and it's your **unit-economics slide.**
- **Insight:** The strongest artifacts are *composites* — one picture answering orchestration, verification, and cost at once. You've spent the week accumulating the parts; today is assembly.

→ Cross-link: [2026-05-23/03 §2 the weekend-execution artifact](../2026-05-23/03-practical-skills-and-tools.md#2-artifact) · [`ACTIONS.md`](../ACTIONS.md).
