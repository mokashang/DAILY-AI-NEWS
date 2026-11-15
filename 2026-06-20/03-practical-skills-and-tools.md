# Practical Skills & Tools — 2026-06-20

The 20-minute file: **one thing to install + practice this weekend.** The pick this week: the **six primitives** of the 2026 Claude Code stack — most people use two; the hiring signal is that you use all six well. Plus: the **plan-first agent reliability loop** (you've seen it in earlier editions; this is the canonical writeup), and the **June-15-metering bill audit** that's due now that the meter is live.

Tags: `#claude-code #agents #sdk #mcp #subagents #hooks #cost`

---

## 1. The six primitives of the 2026 Claude Code stack — learn them in order {#1-stack}

**What to learn:** Anthropic's June docs + the wave of practitioner writeups have converged on **six primitives** for extending Claude Code from "chat in a terminal" into a real agent system. They compose. The hiring signal is **using all six well**, not just CLAUDE.md + skills.

| # | Primitive | What it does | Hours to learn | Hours to master |
|---|---|---|---|---|
| 1 | **CLAUDE.md** | Repo-level system prompt + conventions for Claude Code | 0.5 | 2 |
| 2 | **Skills** | Reusable, model-callable capability files (a function the agent can call by name) | 1 | 4 |
| 3 | **Subagents** | Specialized sub-Claude-Code instances Claude spawns for parallel/independent work | 1 | 6 |
| 4 | **Slash commands** | Named, parameterised workflows you trigger by `/` | 0.5 | 2 |
| 5 | **Hooks** | Event handlers (pre-tool-call, post-tool-call, on-exit) that gate or annotate behavior | 2 | 8 |
| 6 | **MCP servers** | Open protocol; expose any tool/data source to any agent | 4 | 12+ |

**The discipline that ties them together** (synthesised from the June practitioner posts):

> *Narrow task → smallest useful tool set → run the agent loop on real examples → only then add memory, retrieval, approvals, and multi-agent collaboration.*

In other words: **don't compose primitives until one primitive works.** Most failed agent projects compose six things; most successful ones do one well.

**Sources:**
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Smart-Webtech — Claude Code: Workflows and Best Practices 2026](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/) `[analysis]`
- [Developers Digest — Claude Code Dynamic Workflows: The Complete Guide](https://www.developersdigest.tech/blog/claude-code-dynamic-workflows-guide) `[analysis]`
- [Anthropic — Use the Claude Agent SDK with your Claude plan](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [Helply — How to Create AI Agents With the Claude Agent SDK (2026)](https://helply.com/blog/create-ai-agent-using-claude-agent-sdk) `[analysis]`
- [Designveloper — How To Build An Agent With Claude: From Workflow To Agent](https://www.designveloper.com/blog/how-to-build-an-agent-with-claude/) `[analysis]`
- [MindStudio — What Is the Claude Agent SDK? How It Differs from the Claude API](https://www.mindstudio.ai/blog/what-is-claude-agent-sdk-vs-claude-api) `[analysis]`

### Why it matters to you

- **Job lens:** **Map each primitive to an interview answer.** Most candidates can talk through (1) CLAUDE.md and (4) slash commands. The differentiation is in (3) **subagents** ("when do you spawn one vs. handle it in the main loop?"), (5) **hooks** ("when have you used a pre-tool-call hook to gate an action?"), and (6) **MCP servers** ("walk me through one you've shipped"). For FDE / AI Integration Engineer roles — these are *the* questions. Your weekend MCP server ([`05` §3](./05-career-and-startup.md#3-weekend-artifact)) is the *demonstrable* answer to (6); a 30-line example of each in your portfolio repo answers the rest.
- **Startup lens:** Think of the six primitives as **the six things every business workflow needs to encode**. If you wrap them around a vertical (legal contract review, dental scheduling, claims triage), you have an **opinionated agent package** that beats raw "we'll integrate Claude for you" pitches because customers can *see* what you've built. The under-priced primitive is **(5) hooks** — that's where compliance, audit, approval-workflow, and governance live, and where most agent products fail in enterprise procurement.
- **Insight:** The **cost-lever pattern** ([2026-05-22/03 §1 Opus-orchestrator + Sonnet-worker](../2026-05-22/03-practical-skills-and-tools.md)) is itself a **subagent + slash-command + hook composition**: orchestrator (main loop, Opus), worker subagents (Sonnet), slash-command to spin them up, hooks to log per-step cost. **One mental model, one bill, six primitives.**

→ Cross-link: [2026-05-22/03 §1 cost lever](../2026-05-22/03-practical-skills-and-tools.md) · [`04` §1 the eval stack that *measures* whether your primitive composition works](./04-research-progress.md#1-eval-stack) · [`05` §3 weekend artifact](./05-career-and-startup.md#3-weekend-artifact).

---

## 2. The plan-first agent reliability loop (the canonical write-up) {#2-plan-loop}

**What to learn:** For non-trivial agent tasks (anything beyond a one-shot answer), the **June-2026 reliability primitive** that the practitioner community has converged on:

1. **Plan first.** Ask Claude to write the plan as a numbered list. *Do not let it touch tools yet.*
2. **Annotate the plan.** You go through line by line: "skip 2," "add a step for X between 4 and 5," "step 7 needs source citations." This is the cheapest possible eval cycle.
3. **"Address all notes; do not implement yet."** Claude reissues the revised plan.
4. **Iterate until the plan is right.**
5. **"Now implement."** The agent loop executes against the agreed plan, *with hooks logging per-step cost.*
6. **Verify against real tools** (cite [`04` §1 MIMeBench / agent-eval survey](./04-research-progress.md#1-eval-stack)) — not against mocks.

The non-obvious move is **step 3**. Anthropic's practitioners say this is what separates one-shot agents from agents you can run unattended: a model with a plan that the human pre-approved + per-step verification is a different reliability regime from "go figure it out."

**Sources:**
- [Smart-Webtech — Claude Code: Workflows and Best Practices 2026](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/) `[analysis]`
- [Designveloper — How To Build An Agent With Claude: From Workflow To Agent](https://www.designveloper.com/blog/how-to-build-an-agent-with-claude/) `[analysis]`
- [Developers Digest — Claude Code Dynamic Workflows: The Complete Guide](https://www.developersdigest.tech/blog/claude-code-dynamic-workflows-guide) `[analysis]`
- [Anthropic — Building agents with the Claude Agent SDK (docs)](https://docs.claude.com/en/api/agent-sdk/overview) `[primary]`

### Why it matters to you

- **Job lens:** This is **the single most universally-asked agent-design interview question** as of June 2026 ("how do you make a long-running agent reliable?"). The plan-first → annotate → revised-plan → implement → verify loop is the answer; the interview signal is that you *name the step* ("address all notes, don't implement yet") and can sketch the **hook that logs per-step cost** while the loop runs.
- **Startup lens:** Sell the *plan-approval moment* to enterprise customers as the **audit checkpoint**. Compliance/procurement is more comfortable with "Claude proposed this plan, your senior engineer approved it, here's the audit log of the executed steps" than with "the agent did some stuff." That's why the plan-first loop is what every Anthropic Solutions demo opens with — and why your demo should too.
- **Insight:** The loop reframes the eval question from *"is the model good enough?"* to *"is the *plan* correct?"* You evaluate a paragraph of text, not a multi-step tool execution — **the cheapest possible eval surface**. That's the same idea as the [TrajAD verifier ([2026-05-17/04](../2026-05-17/04-research-progress.md))] research thread, productised.

→ Cross-link: [`04` §1 eval stack](./04-research-progress.md#1-eval-stack) · [2026-05-17/04 §3 TrajAD](../2026-05-17/04-research-progress.md) · [2026-05-22/03 §1 cost-lever pattern](../2026-05-22/03-practical-skills-and-tools.md).

---

## 3. The June-15 metering audit (now overdue — 30-min task tonight) {#3-metering-audit}

**What to do:** Anthropic's [June 15 metering change](../2026-05-16/03-practical-skills-and-tools.md) is **live as of 5 days ago**. Programmatic Claude (Agent SDK, `claude -p`, GitHub Actions, OpenClaw) now bills against a separate credit pool at API list rates. **Tonight's task:**

1. Open the Anthropic console → **Usage** → filter to **Agent SDK / programmatic** since June 15.
2. Identify the **top-3 most expensive subagents or skills** in your usage. If you don't know, log this with hooks — pre/post-tool-call hooks dump cost per step (the same hook from §1 → primitive 5).
3. **Route the cheapest 70% of those calls to Sonnet** (the cost-lever pattern from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md)). Keep Opus for orchestration + the hardest 30%.
4. Re-run the same workload. **Expect ~40% bill reduction.**
5. Save the cost-trace artifact for your weekend-MCP-server README ([`05` §3](./05-career-and-startup.md#3-weekend-artifact)).

This is *the* highest-ROI 30 minutes of the weekend. The metering change has been telegraphed for a month; **everyone got the email and most people haven't acted on it.** The audit artifact (a markdown table of "before / after / % reduction / which model per step") is a 1-page LinkedIn post that doubles as an interview talking point.

**Sources:**
- [Anthropic — Use the Claude Agent SDK with your Claude plan (billing)](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [2026-05-16/03 — original metering announcement coverage](../2026-05-16/03-practical-skills-and-tools.md) (archive)
- [2026-05-22/03 §1 cost-lever pattern](../2026-05-22/03-practical-skills-and-tools.md) (archive)

### Why it matters to you

- **Job lens:** "Show me your AI infra cost dashboard" is a Senior FDE / Solutions interview question now. A 1-page table with **per-route cost numbers from your own bill** answers it convincingly. Most candidates will hand-wave.
- **Startup lens:** If you're building on Claude, **your COGS just got newly legible.** Build a *cost-per-customer-action* table for whatever feature you ship — it's both the input to pricing decisions and a moat (most competitors won't measure this until their margin collapses).
- **Insight:** The shift from "subsidized programmatic Claude" to "list-price programmatic Claude" is **the first time agent costs are a real operational lever**. The skill you're building is *cost-aware routing*, which generalizes beyond Anthropic — it's the same skill you'll need on Gemini 3.5 Pro / Flash split, on GPT-5/o-series routing, on local vs hosted. **One skill, infinite applicability.**

→ Cross-link: [`05` §3 weekend artifact uses this cost trace](./05-career-and-startup.md#3-weekend-artifact) · [2026-05-22/03 §1 cost lever](../2026-05-22/03-practical-skills-and-tools.md).
