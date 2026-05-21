# Practical Skills & Tools — 2026-05-21

Act-on-it-today. This week's highest-leverage skill is **orchestration**: by 2026, Claude Code (and equivalents) stopped being "smart autocomplete" and became a **programmable agent runtime** — commands, subagents, skills, memory, hooks, and MCP are composable primitives. The people who get hired and the founders who ship fast are the ones who **wire these together**, not the ones who type better prompts. Below is a concrete, do-it-this-weekend setup.

Tags: `#playbook #claude-code #mcp #subagents #hooks #agents #orchestration #portfolio`

---

## 1. The 2026 Claude Code orchestration stack — set it up tonight {#1-orchestration}

The mental model that matters: **a main agent owns planning + integration; bounded specialist subagents do the work, each with its own context window, prompt, and tool permissions.** That's how you keep a long task from blowing the main context — exactly the problem this news repo's own tooling solves with subagents.

**The five primitives, and the one-line reason each exists:**

| Primitive | What it buys you | First thing to do |
|---|---|---|
| **`CLAUDE.md`** | Persistent project memory (conventions, commands, do/don'ts) | Drop the Karpathy template in every repo root (you flagged this 2026-05-17) |
| **Subagents / agent teams** | Parallel, context-isolated specialists (review, tests, QA, security) | Define one `code-review` + one `test-runner` subagent |
| **MCP servers** | The agent can *operate your real tools*, not just edit files | `claude mcp add` your issue tracker + DB + one external API |
| **Hooks** | Deterministic guardrails on the edit loop (CI-but-closer) | Add a "run tests before stop" + "lint before commit" hook |
| **Skills / commands** | Reusable, named workflows you invoke on demand | Wrap your most-repeated multi-step task as one command |

**The line worth internalizing:** *"MCP is the difference between an agent that edits files and an agent that can operate your actual workflow."* Connect it to issue trackers, databases, monitoring, browser automation, design tools, internal APIs — then ask the agent to *implement a ticket end-to-end*, not just write a function.

**Useful hook patterns (steal these):** run tests before the agent stops · block edits to generated files · lint before commit · require an issue ID in the branch name · run a security scan after any dependency change.

**Sources:**
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Developers Digest — Claude Code agent teams, subagents & MCP: the 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [CloudZero — Claude Code agents in 2026: agent view, subagents, teams, and what parallel sessions cost](https://www.cloudzero.com/blog/claude-code-agents/) `[analysis]`
- [Arcade.dev — Claude Code routines: 5 production workflows + MCP setup](https://www.arcade.dev/blog/claude-code-routines-mcp-setup/) `[analysis]`

### Why it matters to you

- **Job lens:** "Designed a multi-subagent workflow with MCP tool access and hook-based guardrails" is a **far stronger resume line than "used Claude Code."** It maps 1:1 to what an FDE/Integration Engineer does for a client: wire the agent into the customer's real systems and put safety rails on it. Build the setup once, screenshot the architecture, write a one-paragraph README — that's a portfolio artifact in an evening.
- **Startup lens:** This *is* the FDE-as-a-service / vertical-agent build pattern. Your MVP for any "Claude-for-X" wedge is: a `CLAUDE.md` encoding the domain, 2–3 MCP servers into the customer's stack, subagents for the recurring sub-tasks, hooks for the compliance rails. You can stand up a credible demo for a design-partner in a day.
- **Insight:** **Mind the June 15 Agent SDK metering (T-25 days).** Subagents and parallel sessions multiply token spend fast — the orchestration power you're gaining is exactly what the new metering will price. Pair this setup with **per-step cost attribution** (your cost-router artifact) so you can *show* the spend, not get surprised by it. Cost-awareness is now part of "knows how to use the tools."

---

## 2. This weekend's artifact: a hook-guarded, MCP-wired mini-agent + its cost trace {#2-artifact}

A single shippable thing that demonstrates everything above and answers three interview questions at once.

**Build (3–4 hrs):**
1. A small repo with a real `CLAUDE.md` (conventions + commands).
2. One **MCP server** you wrote (3 tools — reuse your in-progress public MCP server from ME.md).
3. Two **subagents** (`code-review`, `test-runner`) and two **hooks** (tests-before-stop, lint-before-commit).
4. A **cost trace**: log tokens per subagent step and produce a tiny table/chart of "what this task cost, by step."

**Write (30 min):** a README section — *"How I'd wire this for a client, and how I'd keep their bill predictable."* That sentence is the FDE/Solutions interview in one line.

**Why this beats a generic demo:** it simultaneously shows orchestration (subagents/hooks/MCP), production discipline (guardrails), and cost-awareness (the trace) — the three things the price-war + metering shift made scarce and valuable (see [`05` §2](./05-career-and-startup.md#2-reprice)).

→ Cross-link: [2026-05-20 §4 the 3-provider cost router](../2026-05-20/03-practical-skills-and-tools.md) · [2026-05-17 §2 `CLAUDE.md` template](../2026-05-17/03-practical-skills-and-tools.md) · [`ACTIONS.md`](../ACTIONS.md).
