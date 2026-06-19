# Practical Skills & Tools — 2026-06-19

Act-on-it-tonight. The Claude Code June drop is the single biggest practical update since the agent SDK launched: **subagents can now spawn subagents (5 levels deep)**, `/cd` lets you change working directory mid-session without rebuilding the prompt cache, and **Artifacts** turn session work into live shareable web pages. Combined with **Workload Identity Federation (GA June 17)** = keyless auth across SDK + Claude Code, plus **doubled rate limits**, the entire orchestration stack from [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md) needs a small but real rewire this weekend. And on the **cost** side: the Agent SDK metering went live on June 15 — the cost-routing skill is now load-bearing on every bill, not theoretical.

Tags: `#claude-code #subagents #playbook #cost #orchestration #identity #artifacts #portfolio`

---

## 1. The Claude Code June drop — install + reconfigure tonight {#1-claude-code-june-drop}

**Headline features (all in production now):**

| Feature | Why it matters | How to use it |
|---|---|---|
| **`/cd <path>`** — move the session to a new working dir mid-conversation | No more rebuilding prompt cache when you switch repos / sub-modules / branch worktrees | Drop into the new dir, keep your plan + context; especially useful when an orchestrator agent dispatches workers into separate repos |
| **Subagents-spawn-subagents (5-level cap)** | The orchestration tree from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) is now **recursive** — Opus planner → Sonnet specialist → Haiku verifier → … up to 5 levels | Use to push *plan-then-verify-then-implement* deeper without losing context; cap nesting in your team config to 3 unless you have a budget reason |
| **`--safe-mode`** | Starts Claude Code with all customizations disabled — the "control variable" run when something breaks | The first command in any "is it me or is it Claude Code today?" debugging session |
| **`fallbackModel`** (configures up to 3) | Survive a model outage / rate-limit hit without your whole agent team going down | Configure: Opus 4.7 → Sonnet 4.6 → Haiku 4.5. Now your orchestrator can keep running through a single-model degradation |
| **Artifacts in Claude Code** | Sessions produce **live, shareable web pages** — PR walkthroughs, incident pages, dashboards, checklists update in place | Replace your Notion-doc-of-the-week with a live artifact link in next sprint review |
| **Workload Identity Federation (GA June 17)** | **Keyless auth** across API endpoints, SDKs, Claude Code; service accounts; guided setup; Admin API for programmatic identity mgmt | The first thing to enable in any team/enterprise context — no more long-lived API tokens in CI/CD |
| **Doubled rate limits + raised Opus API limits** | The orchestration team from May 22 can now run more aggressively; Opus-as-orchestrator is more durable | Re-run your cost trace from last month — both throughput and cost shape will have changed |

**Sources:**
- [Claude Code Docs — What's New (official changelog)](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Releasebot — Claude Code Updates by Anthropic, June 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Anthropic News — Workload Identity Federation GA](https://www.anthropic.com/news) `[primary]`
- [Blog.mean.ceo — Claude Code News, June 2026 (STARTUP EDITION)](https://blog.mean.ceo/claude-code-news-june-2026/) `[analysis]`
- [MEXC — Claude Code enhancements boost autonomy with new features](https://www.mexc.com/en-GB/news/claude-code-enhancements-boost-autonomy-with-new-features/148686) `[secondary]`

### The reconfiguration recipe (45 min, tonight)

1. **Update.** `npm i -g @anthropic-ai/claude-code@latest` (or your package manager equivalent).
2. **Enable `fallbackModel`.** In `~/.claude/config`, set Opus 4.7 → Sonnet 4.6 → Haiku 4.5. *This single line is the most underrated reliability primitive of the June drop.*
3. **Wire Workload Identity Federation.** Replace your long-lived API key with the new keyless flow; rotate any old key out of CI/CD. (See guided setup in the docs.)
4. **Reset depth caps.** In your agent-team config, set the recursion depth to **3** (not the 5-level max) unless you've budgeted for a deeper run; the cost amplification on a 5-deep tree is meaningful.
5. **Run the cost-trace baseline again.** Repeat the [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) exercise — Opus orchestrator + Sonnet workers, but now with `fallbackModel` configured and depth-3 nesting. Compare token cost vs the May baseline; the doubled rate limits change parallelism economics.
6. **Convert one Notion doc → Artifact.** Pick the next PR walkthrough or status dashboard you'd normally write in Notion and ship it as a Claude Code Artifact instead. Shareable link goes in your portfolio.

### Why it matters to you

- **Job lens:** The interview line that wins this week: *"After the June 15 metering and the `fallbackModel` shipped, I redesigned my agent team around depth-3 recursion + fallback-chain reliability and re-measured cost — here's the trace."* That is *exactly* the FDE / Solutions / Integration job described as a sentence. It signals you read the changelog the day it dropped *and* you re-baselined your work.
- **Startup lens:** `fallbackModel` is the first time a major lab has shipped a **graceful-degradation primitive** as a first-class feature. The market is telling you reliability-during-model-degradation is now a product surface — there's a wedge for **observability of agent reliability across the fallback chain** (alerting when the team is running on the fallback for >X% of steps). That's a Datadog-for-agents-shape startup.
- **Insight:** Every Claude Code release in 2026 has added an *enterprise-IT surface* (identity, governance, audit) alongside a *developer-UX surface* (subagents, `/cd`, artifacts). That dual cadence is the IPO-readiness signal — Anthropic is shipping the things public-market enterprise buyers ask for in due diligence. Read every future drop with that lens.

---

## 2. The cost-routing skill is now load-bearing (Agent SDK metering, June 15) {#2-cost-routing-live}

**What changed:** As of **June 15, 2026**, Agent SDK / programmatic-Claude usage is metered against a **separate credit pool at API list rates** (per the change tracked since [2026-05-16](../2026-05-16/)). The cost-routing exercise from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — Opus orchestrator + Sonnet workers + Haiku verifier — is no longer "preparation." It's the actual line item on your bill, every day, starting now.

**The 30-minute audit (do this Sunday):**

1. **Pull last 30-day usage** from the Anthropic billing dashboard, broken down by model + by API key.
2. **Identify your top-cost agent script.** It's almost always the one with the most Opus calls inside a tight loop.
3. **Apply the orchestrator/worker split** to that script — single Opus planner + 2-4 Sonnet workers.
4. **Add a Haiku guard** as continuous-on verifier (the TrajAD pattern from [2026-05-19/04](../2026-05-19/04-research-progress.md)).
5. **Configure `fallbackModel`** so the team doesn't spike to Opus when Sonnet rate-limits.
6. **Re-run.** Document the % cost reduction with model-level token breakdown.

That single audit, screenshotted, is a **portfolio artifact + interview anchor + due-diligence-for-your-own-startup financial-model exercise** simultaneously.

**Sources:**
- [2026-05-16 — Agent SDK metering announcement](../2026-05-16/01-big-lab-moves.md) `[primary, archive]`
- [2026-05-22/03 §1 — orchestrator/worker cost recipe (Opus + Sonnet ≈ 40% cheaper)](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) `[primary, archive]`
- [Claude Code Docs — `fallbackModel` configuration](https://code.claude.com/docs/en/whats-new) `[primary]`

### Why it matters to you

- **Job lens:** The cost-trace artifact closes three interview questions in one screenshot: orchestration, reliability (via `fallbackModel`), cost-awareness. Put it at the top of your portfolio README this weekend.
- **Startup lens:** Your COGS is tokens. Your gross margin is the orchestrator/worker split — *full stop*. The companies that lose in 2026 are the ones that didn't model this rigorously when metering went live. The ones that win are the ones who treat cost as a *product feature* (a "savings dashboard" for the user) — see Exaforce's "fewer tokens per investigation" pitch from [2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce).
- **Insight:** **Metering is the moment "vibes about cost" become "numbers about cost."** Most people will discover their agent stack is 2-3× more expensive than it needs to be when the first bill arrives in late June. Be the one who discovered it *first* and shipped a workflow to fix it. That timing is the differentiation.

---

## 3. Three small workflow upgrades that compound {#3-small-upgrades}

Quick wins worth installing tonight:

- **Pin `--safe-mode` as your first debugging step.** Whenever Claude Code feels "off," that's the first command — establishes whether the issue is your config or upstream.
- **One `CLAUDE.md` per repo, one global.** The trending Karpathy `CLAUDE.md` template ([2026-05-15/03](../2026-05-15/03-practical-skills-and-tools.md), [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)) is the canonical starting point — fork it.
- **Convert your "weekly status update" doc to a Claude Code Artifact.** Pick the recurring doc you most-often update and ship it as an Artifact — it becomes a live shareable URL that updates in place. Pattern: PR walkthroughs, incident pages, sprint dashboards. Reduces context-switching by 1-2× per week.

**Sources:**
- [Claude Code Docs — Best Practices (official)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Karpathy `CLAUDE.md` template (trending #1, ~109K stars)](https://github.com/karpathy) `[primary]` *(archived from [2026-05-17](../2026-05-17/03-practical-skills-and-tools.md))*

### Why it matters to you

- **Job lens:** Three tiny daily-workflow markers that signal "I run this stack at production discipline." None of them require a project — all three you can install in one evening.
- **Startup lens:** Each is a *tool-shaped wedge* if you go deep on it: the safe-mode habit suggests an "agent stack debugger"; the CLAUDE.md ecosystem suggests a "team-level CLAUDE.md template registry"; Artifacts suggest a "Notion-replacement for agentic teams." Pick the one closest to your own pain.
- **Insight:** Workflow superpowers compound *daily.* A 5-minute habit that saves 15 minutes a day is the cheapest leverage you'll ever buy — and the only thing standing between you and shipping the next portfolio artifact one week sooner.
