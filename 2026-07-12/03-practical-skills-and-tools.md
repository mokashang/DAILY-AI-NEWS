# Practical Skills & Tools — 2026-07-12

Three things you can do today or this week. **(1)** Reprice your Claude-Code stack for Sonnet 5 (default in Claude Code, 1M native context, $2/$10 promo through Aug 31). **(2)** Adopt the 8-rule Claude-Code hygiene set that consistently shows up across the July 2026 practitioner writeups. **(3)** Pre-stage the 3-model comparison table so you can publish 15 minutes after Wednesday's Gemini 3.5 Pro reveal.

Tags: `#claude-code #sonnet-5 #subagents #mcp #cost #hygiene #practical`

---

## 1. Reprice your Claude-Code stack for Sonnet 5 (2-hour Sunday task) {#1-sonnet5}

**What happened:** **Claude Sonnet 5 became the default in Claude Code on June 30**, with:
- **1M-token native context.**
- **Promotional pricing: $2 input / $10 output per Mtok, through Aug 31.**
- Substantial coding-tool-use gains over Sonnet 4.6.

Additional platform changes: **Claude in Chrome is GA**, **background subagents by default**, **Claude Desktop on Linux in beta**, and Anthropic Enterprise gets **admin analytics, model-level entitlements, and spend alerts**.

**Sources:**
- [Releasebot — Claude Updates by Anthropic (July 2026)](https://releasebot.io/updates/anthropic/claude) `[aggregator]`
- [Releasebot — Claude Code Updates by Anthropic (July 2026)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Anthropic Release Notes](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`

### Do this today

The May-22 Opus-orchestrator + Sonnet-worker split assumed Sonnet 4.6 at then-current prices. With Sonnet 5 promo-priced at $2/$10 (through Aug 31), the **arithmetic shifts:**

1. **Baseline: Sonnet-5-only orchestration** — one model handling both plan and execution. For most refactors ≤10 files, wall-clock difference is small and the cost falls to *below* half of Opus-orchestrator + Sonnet-4.6-worker.
2. **Escalation trigger: "plan hallucinated"** — if Sonnet-5-only produces a plan that mis-identifies which files to touch, escalate to **Opus 4.7 for plan only**, then re-hand to Sonnet 5 for execution. Use `/effort low` on Sonnet by default; reserve `/effort high` for the escalation.
3. **Cost log a MUST.** Log per-run token spend to a local file (`~/.claude/costs.jsonl`) and diff weekly. Anthropic's new spend-alerts help but only past the threshold — you want the trend before the alert.

The **1M context** means you can now feed *entire mid-sized repos* into a single turn — but this is a *cost trap*. If your repo is 400K tokens, that's **$0.80 per prompt at promo prices, several dollars at list.** Prefer `@file` mentions and subagent-delegated reads.

**Deliverable this Sunday (2 hours):**
- Set Sonnet 5 as your default (`claude config set model claude-sonnet-5` or the GUI equivalent).
- Update your project's `CLAUDE.md` with the new default and the escalation rule.
- Run 3 real tasks you would have run this week, log tokens, and compare to your May-22 baseline.
- Publish the numbers as a **LinkedIn post + repo README section**. Every recruiter for Anthropic Solutions / Deployment / FDE-adjacent roles will read that post as *domain competence*, which is the exact evidence bar mentioned in [Perspective AI's 2026 FDE hiring trends](https://getperspective.ai/blog/2026-fde-hiring-trends-what-1000-job-posts-reveal) `[analysis]`.

### Why it matters to you

- **Job lens:** *Anyone can prompt.* **Very few candidates can defend a per-token cost model with logs.** The published-numbers artifact is the version of the "MCP server" portfolio piece from [ME.md](../ME.md) with better market timing this week.
- **Startup lens:** If your COGS is Anthropic-side, the Sonnet 5 promo pricing is a **60-day margin holiday** (through Aug 31). Use it to *raise your headline pricing while your costs stay low* — not to give the savings back.
- **Insight:** The moat isn't "which model" — it's "which model, per step, at what cost." **Model-routing is the compounding skill of 2026.**

→ Cross-link: [2026-05-22/03 §1 the agent-team cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. The 8-rule Claude-Code hygiene set (adopt tonight) {#2-hygiene}

**What happened:** July 2026 practitioner writeups converge on a small, reproducible hygiene set for Claude Code — mostly *token discipline* and *scope discipline*, both of which get more valuable as sessions get longer with 1M-context Sonnet 5.

**Sources:**
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Developers Digest — Claude Code Agent Teams, Subagents, and MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [4sAPI Blog — Master Claude Code 2026: CLAUDE.md & Sub-Agent Workflows](https://blog.4sapi.com/blog/claude-code-2026-claude-md-subagent-workflows) `[analysis]`
- [Blake Crosley — Claude Code CLI: The Complete Guide (Hooks, MCP, Skills)](https://blakecrosley.com/guides/claude-code) `[analysis]`

### The set

| # | Rule | Why |
|---|---|---|
| 1 | **`/clear` between unrelated tasks.** | Prevents cross-task context contamination. Costs nothing. |
| 2 | **`/compact` proactively** — before context bloats, not after. | Summarizing on your terms costs 1–2 turns; summarizing under duress costs a retry. |
| 3 | **`CLAUDE.md` under 200 lines.** | Every project-load reads it into context; 1000-line CLAUDE.md burns tokens on every turn. |
| 4 | **`@file` mentions instead of "search for X."** | Every avoided `Glob`/`Grep` is a subagent's-worth of tokens saved. |
| 5 | **Delegate verbose tasks to subagents (default in Sonnet 5).** | 20 file reads + 12 greps stay in the subagent; your main context sees the final report. This is the single highest-leverage move for keeping main contexts small. |
| 6 | **Turn off unused MCP servers per project.** | Each connected server injects tool definitions into every turn. On old sessions, this alone can be 5–15K tokens/turn. |
| 7 | **`/effort low` by default, escalate on failure.** | Reasoning cost is per token generated; low-effort works for 80% of turns. |
| 8 | **One subagent per specialized responsibility with different tool needs.** | The recommended refactor team: main (plan/integrate) · backend subagent · frontend subagent · test subagent · review subagent. |

### Do this tonight (30 min)

1. Open your most-used project. Read your `CLAUDE.md`. If it's >200 lines, refactor to a table of contents + linked docs.
2. Audit which MCP servers your project actually calls. Disable the rest for this project (not globally).
3. Add 4 subagent definitions if you don't have them: `backend`, `frontend`, `test`, `review`. Even boilerplate ones are enough; you can customize as you use them.
4. Set an alias: `alias cc-low="claude --effort low"` and use it as your default entry.

### Why it matters to you

- **Job lens:** These are the *observable* habits that separate someone who "uses Claude Code" from someone who "ships production work through Claude Code." Interview-time question: *"When your Claude Code session got too big, what did you do?"* — the answer should include `/compact`, subagent delegation, and MCP-server pruning by name.
- **Startup lens:** For a small team, the difference between rules-followed and rules-ignored is roughly *2× developer-hours-per-feature*. Make these house rules; enforce in code review.
- **Insight:** Anthropic ships the same discipline internally (see: the CLAUDE.md-under-200-lines rule, which the CC docs now recommend directly). Adopting the same discipline is a signal that you *think about the system the way Anthropic does* — worth mentioning explicitly in Solutions/FDE cover letters.

→ Cross-link: [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md) — the prompt-caching + `CLAUDE.md` playbook still applies; this is the operational hygiene layer on top.

---

## 3. Pre-stage the 3-model comparison table for Wednesday Jul 15 12:30 PM PT {#3-io-day-table}

**What happened:** With **Gemini 3.5 Pro scheduled July 17** ([`01` §4](./01-big-lab-moves.md#4-gemini-35-pro)) and **GPT-5.6 already GA** ([`01` §2](./01-big-lab-moves.md#2-gpt56)) and **Claude Sonnet 5 the default** ([`03` §1](#1-sonnet5)), for the first time this year there are **three architecturally distinct reasoning surfaces you can compare on the same day**. This mirrors the May 20 pattern: **publish the comparison table 15 minutes after the launch stream**, tuned for LinkedIn/Twitter distribution to Solutions/FDE-adjacent recruiters.

### The pre-stage template (fill in Wednesday)

```
| Model                    | Context     | Reasoning tier         | List price ($/M in – out)          | Best for                                 | Sources |
|--------------------------|-------------|------------------------|------------------------------------|------------------------------------------|---------|
| Anthropic Claude Sonnet 5| 1M native   | (single model)         | $2 / $10 (promo through Aug 31)    | Coding, tool-use, long context          |  ??     |
| OpenAI GPT-5.6 Sol       | ??          | (single model)         | ??                                 | Bio/chem/cyber; 54% coding-token efficiency | ?? |
| Google Gemini 3.5 Pro    | 2M reported | Deep Think ($250 Ultra)| ?? (API pricing not yet posted)    | Long-context math, SVG, image           |  ??     |
```

Add 3 short columns of your own opinion, sourced from your Sunday cost-log run:
- **Per-task cost, 1 real refactor.**
- **Wall-clock, same refactor.**
- **When *not* to use it.**

### Do this now (30 min pre-stage)

1. Open a **draft LinkedIn post** with the table skeleton above. Save as draft; don't publish.
2. Open a **draft repo README section**. Same table.
3. Add a *dated placeholder*: **"Updated: 2026-07-15 12:30 PM PT — 15 minutes after Google's Gemini 3.5 Pro release."**
4. Set a phone reminder for **12:15 PM PT Wed Jul 15**.

Wednesday: watch the stream 12:00–12:15, fill in the two `??` columns you don't have, publish at 12:30.

### Why it matters to you

- **Job lens:** LinkedIn timing on model-comparison posts is *ruthlessly binary*. Post within 30 minutes of a launch → recruiter feeds pick it up as "this person tracks the frontier." Post 24 hours late → nobody cares. The pre-stage is 90% of the work; the day-of edit is 10%.
- **Startup lens:** If Gemini 3.5 Pro ships with the reported specs, your product's *model routing table* needs a re-eval Wednesday afternoon — specifically, whether any hot-loop tasks should route to Deep Think.
- **Insight:** You've now watched this pattern land twice (May 20 Gemini 3.5 Flash; July 17 Gemini 3.5 Pro). Add "publish comparison table within 30 min of launch" to your durable weekly-cadence discipline. It's the closest thing to a *free* LinkedIn compounding asset.

→ Cross-link: [2026-05-20/03](../2026-05-20/03-practical-skills-and-tools.md) — the original May 20 comparison-table playbook.
