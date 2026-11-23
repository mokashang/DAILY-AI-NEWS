# Practical Skills & Tools — 2026-05-24 (Sunday)

Hands-on workflows — Sunday = set the week's plan, then ship one thing.

---

## 1. The countdown: June 15 Agent SDK metering is T-minus 22 days {#1-countdown}

**The deadline.** On **June 15**, programmatic Claude (Agent SDK, `claude -p`, GitHub Actions, OpenClaw, etc.) moves to a **separate credit pool billed at API list rates** ([2026-05-16/03](../2026-05-16/03-practical-skills-and-tools.md)). The credit **does not auto-activate — there's a manual toggle** ([2026-05-18/03 §2](../2026-05-18/03-practical-skills-and-tools.md)); skip it and your automations silently fail on the 15th. This week is the **last clean window** to do three things that are also portfolio-grade:

1. **Audit** your programmatic spend (which agents call Claude, how many tokens, what cadence). A two-week trace is your baseline.
2. **Harden cost** with the documented levers:
   - **Subagent context hygiene** — return conclusions, not transcripts. When research touches many files, a subagent runs in its own context, does "20 reads + 12 greps + 3 dead ends," and returns only the answer. Rule before delegating: *"will I need this output again, or just the conclusion?"*
   - **Opus orchestrator + Sonnet workers ≈ 40% cheaper** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)).
   - **Prompt caching** — 60–90% input savings ([2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)).
3. **Toggle** the Agent SDK credit setting now (5 minutes).

- **Sources:** [Anthropic — News / release notes](https://www.anthropic.com/news) `[primary]` · [Claude Code — best practices](https://code.claude.com/docs/en/best-practices) `[primary]` · [Tembo — Claude Code Subagents: 2026 guide](https://www.tembo.io/blog/claude-code-subagents) `[analysis]`

**Why it matters to you.**
- **Job:** "How would you cut an agent product's inference bill 40–80% without hurting quality?" is a live interview question. Your spend-audit + the three levers *is* the answer, with your own numbers.
- **Startup:** Per-task cost is the line between a viable agent product and a money-loser. The audit is your unit-economics dry run.
- **Insight:** The metering change is a forcing function — build the cost muscle every agent builder needs anyway.

`#claude-code #cost #metering #deadline #caching #subagents`

---

## 2. This week's ship + audit — package it as a Skill {#2-this-week}

**The move.** Yesterday's edition made the point that the unit of value moved from "a good prompt" to **"a good Skill"** — `SKILL.md` (trigger, not summary) + scripts + gotchas + eval ([2026-05-23/03 §1–2](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills)). This week, **package the migration artifact as exactly that Skill** so the SaaSpocalypse ([`02` §1](./02-new-emerging.md#1-saaspocalypse)) is the README's headline:

> **Skill: "Replace N seats of [Salesforce/ServiceNow/Zendesk] with one governed agent workflow."**
> - `SKILL.md` — a **trigger** description (when Claude should invoke it), not a summary.
> - A **cost-logger** helper script (Opus-planner / Sonnet-worker token table) → ties straight into §1's audit.
> - A `gotchas.md` from running it against **one real MCP server** (cite MCP-Atlas / Toolathlon, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)).
> - A **dual-model "sanitiser"** in front of untrusted-input tools + a **5-case eval** (3 tool-use + 2 injection-refusal).
> - README opens with the **cost table**: seats × $/seat/mo vs. your agent's $/1000 tasks.

**4–6 hours, scoped.** Pick ONE workflow you understand (ticket triage / invoice approval / lead enrichment). Drop the audit's baseline number into the README — *"this workflow costs $X/1000 tasks vs. $Y of license it replaces"* is the whole pitch in one line.

**Why it matters to you.**
- **Job:** One publishable Skill = **four interview answers** (orchestration · real-tool verification · cost · reusability) **+** the SaaSpocalypse migration question, with real numbers.
- **Startup:** It's also a **customer-discovery demo** for migration-as-a-service ([`05` §1](./05-career-and-startup.md#1-week-setup)) and a **Workday × Anthropic Solopreneurship** application asset ([2026-05-23/05 §2](../2026-05-23/05-career-and-startup.md#2-weekend-execution)).
- **Insight:** The artifact and the June-15 deadline are the *same work* — building the cost muscle and the portfolio piece are one task.

`#claude-code #skills #portfolio #cost #saaspocalypse #mcp`

---

### Cross-links
- The Skill unit + weekend-artifact framing: [2026-05-23/03 §1–2](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills)
- The cost levers: [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)
- Career framing: [`05` §1](./05-career-and-startup.md#1-week-setup)
