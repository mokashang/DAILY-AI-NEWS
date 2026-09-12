# Practical Skills & Tools — 2026-07-01

**Two things you can do tonight, both directly downstream of yesterday's Sonnet 5 launch.** First: **swap your existing Opus-orchestrator / Sonnet-worker agent team** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) **to Sonnet-5-on-both** — same reliability loop, ~50% lower cost while the $2/$10 promo lasts. Second: **rewire your eval to catch provider-side model drift** — the Fable-5 shutdown made this urgent, the Sonnet 5 default-swap in Claude Code makes it *mandatory*. Both are portfolio-artifact-shaped: each answers a specific interview question.

Tags: `#claude-code #sonnet-5 #mcp #agents #cost #evals #orchestration #hooks`

---

## 1. The Sonnet-5 dual-model orchestration playbook {#1-sonnet-5-orchestration}

**What to build:** a **two-agent team** where a Sonnet-5 orchestrator plans, delegates, and reviews, and a second Sonnet-5 instance (or Haiku 4.5 for cheap sub-steps) executes. The **plan → annotate → "address all notes, don't implement yet"** loop from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) still works — you're just swapping the models underneath it.

**Concrete recipe (Claude Code v2.1.197):**

```markdown
# CLAUDE.md — pinned model version (do NOT rely on defaults; they drift)
Primary model: claude-sonnet-5-20260630
Worker model: claude-sonnet-5-20260630   # or claude-haiku-4-5 for cheap sub-steps
Fallback model: claude-sonnet-4-6         # rollback lane if Sonnet 5 misbehaves

# Reliability loop (do not skip):
1. Ask the orchestrator to PLAN first — no code, just the plan
2. Annotate the plan (inline comments, questions, corrections)
3. Say "address all notes; DO NOT implement yet"
4. Only after the plan converges: "now implement"
```

**Cost math — why this is a ≈50% saving vs. yesterday's team:**

| Team | Orchestrator | Worker | Per-1M-token cost (in/out avg) | Delta |
|---|---|---|---|---|
| Old (2026-05-22) | Opus 4.8 ($15/$75) | Sonnet 4.6 ($3/$15) | ~$9 avg blended | baseline |
| New (Sonnet-5 dual, promo) | Sonnet 5 promo ($2/$10) | Sonnet 5 promo ($2/$10) | ~$6 avg blended | **≈33% cheaper immediately** |
| New (Sonnet-5 promo + Haiku 4.5 sub-workers) | Sonnet 5 promo | Haiku 4.5 | ~$4 avg blended | **≈55% cheaper** |
| Post-Aug-31 (standard $3/$15) | Sonnet 5 std | Sonnet 5 std | ~$9 avg blended | back to baseline |

**Key tactical additions from the Claude Code v2.1.197 release:**
- **Scoped `.mcp.json`** — only the MCP servers you actually use. **Narrowest-credential principle:** read-only GitHub token for `github-mcp`, no write scopes unless the task requires them.
- **One safety hook** — pre-tool-use hook that blocks writes to `~/.ssh`, `~/.aws`, `.env*`, `.git/config`, and any absolute path outside the repo root.
- **One reusable skill** for the loop above so you don't retype it each session (`~/.claude/skills/plan-annotate-implement.md`).
- **Subagents only when research or review would pollute the main context** — this is the *only* rule about subagents that matters; ignore the rest until you feel actual context-pollution pain.

**Sources:**
- [Anthropic — Introducing Claude Sonnet 5](https://www.anthropic.com/news/claude-sonnet-5) `[primary]`
- [Releasebot — Claude Code updates July 2026 (v2.1.197 changelog)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Claude Code Docs — What's new](https://code.claude.com/docs/en/whats-new) `[primary]`
- [okhlopkov.com — Claude Code Setup 2026: MCP Servers, Hooks, Skills](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]`
- [Nimbalyst — Claude Code Skills: A Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-skills-guide/) `[analysis]`
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[analysis]`
- [MarkTechPost — Claude Code Guide 2026: 25 features with examples + demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Toolsbase — Claude Code Features Guide 2026 — 65 capabilities explained](https://toolsbase.dev/en/reference/claude-code-features) `[analysis]`

### Why it matters to you

- **Job lens:** The "I have a dual-model agent team on Sonnet 5, here's the cost trace, here's the reliability loop" answer is **the FDE interview answer of Q3 2026**. Ship this, capture 10 real runs to a CSV (see [§2](#2-eval-drift)), put the CSV + a README in a public repo. That artifact directly addresses the *"describe an agent you deployed"* question every FDE/Solutions role asks.
- **Startup lens:** The **cost delta between promo and standard pricing** is 33-55% — that's your **arbitrage margin as an integrator**. If you're building a vertical agent for a client, price your contract on **standard-pricing economics** and run on **promo pricing** through Aug 31 — that's real margin dropped straight into your P&L for 60 days.
- **Insight:** The promotional pricing isn't a discount — it's an **Anthropic-side option to buy your adoption before OpenAI GA's GPT-5.6**. Read your calendar accordingly: **Sept 1 is a soft cliff**; either you've amortized the switching cost to a competitor by then, or you're locked in at $3/$15. Decide *before* Aug 15, not on Aug 31.

→ Cross-link: [`§2` the eval you need to catch model drift](#2-eval-drift) · [`01` §1 the launch itself](./01-big-lab-moves.md#1-sonnet-5) · [2026-05-22/03 §1 the earlier version of this playbook](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. Eval-under-provider-drift — the ~90-minute build {#2-eval-drift}

**Why now:** Fable 5 was globally dark for **19 days**, then a *new safety classifier* changed its behavior on July 1 without a version bump. Sonnet 5 became the *default* in Claude Code v2.1.197 — meaning anyone who hadn't pinned an explicit model version had their agent's brain silently swapped. **Silent provider-side model changes broke an unknown number of production agents this week.** Your eval has to catch that.

**What to build (the minimum eval):**

1. **A frozen test set (10–20 items)** — inputs + *expected* outputs, or *expected properties* (e.g., "output is valid JSON with keys A, B, C" or "response length within [50, 200] words").
2. **A daily scheduled run** that hits the current pinned model *and* the current default model on the same test set.
3. **A drift metric** — pass rate, or property-satisfaction rate. Log to a CSV keyed by `(date, model_id, item_id, passed)`.
4. **A cheap Haiku 4.5 judge** for open-ended outputs — score 1-5, with a 1-sentence rubric per test item.
5. **An alert** — cron + a shell script that pings you (webhook, email, whatever) when the day's pass rate drops >X% from the trailing 7-day median. (Do NOT skip this — an eval you don't get alerted on is a folder of numbers, not an eval.)

**Cost math:** at $1/$5 per Mtok (Haiku 4.5), a daily 20-item eval with a 1-Kb prompt + 500-token judge output = **~$0.03/day**. That's a rounding error against the cost of one production agent behaving wrong for a week.

**Sources:**
- [Anthropic — Claude Sonnet 5 (pinned model IDs)](https://www.anthropic.com/news/claude-sonnet-5) `[primary]`
- [Anthropic — Platform pricing (Haiku 4.5 rates)](https://platform.claude.com/docs/en/about-claude/pricing) `[primary]`
- [Cybersecurity Dive — Anthropic reactivates Fable, Mythos with new safety classifier (behavior change without version bump)](https://www.cybersecuritydive.com/news/anthropic-ai-mythos-fable-reenable/824214/) `[secondary]`
- [MarketScale — 19-day shutdown: what enterprises learned](https://www.marketscale.com/industries/software-and-technology/fable-5-and-mythos-5-are-back-what-the-19-day-shutdown-taught-every-enterprise-about-ai-as-infrastructure) `[analysis]`
- [Nimbalyst — Claude Code Skills guide](https://nimbalyst.com/blog/claude-code-skills-guide/) `[analysis]`

### Why it matters to you

- **Job lens:** *"How do you catch it when a provider silently swaps a model?"* is a top-3 question in Solutions / FDE interviews at every AI-integrator shop and lab-Solutions team. Ship the eval + the CSV + one paragraph of README titled *"what happened on 2026-06-30 when Sonnet 4.6 became Sonnet 5 in my env, and how my eval caught it"* → that's the story.
- **Startup lens:** *"Model continuity / drift monitoring"* was the wedge already flagged in [`02` §1](./02-new-emerging.md#1-spacex-cursor) — building the eval for yourself *is* the MVP for that wedge. Same code, two audiences.
- **Insight:** The transition from "eval as vibes" to "eval as **regression test**" is the single largest professional-maturity gap in AI engineering right now. Cross that gap this week and you're ahead of ~70% of self-described AI engineers on LinkedIn.

→ Cross-link: [`01` §2 Fable-5 return incident](./01-big-lab-moves.md#2-fable-return) · [2026-05-19 JADE per-claim eval](../2026-05-19/04-research-progress.md).

---

## 3. Fifteen-minute wins for this week {#3-quick-wins}

Short list; do at least three by Friday.

- **Pin your model IDs** in every config, CLAUDE.md, and `.mcp.json` today. `claude-sonnet-5-20260630`, `claude-haiku-4-5-20251001`, `claude-opus-4-8`. Never `claude-sonnet` alone — it drifts.
- **`claude mcp login`** for any MCP server that has real credentials — moves the token out of your dotfiles into the credential store. `claude mcp logout` to clear it when done.
- **Enable prompt caching** on any workflow that reuses >2K tokens of system prompt — 60-90% input-cost savings (unchanged from [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)).
- **Update your `CLAUDE.md`** to reference the plan → annotate → implement loop as *the* project convention, not just yours personally — makes it show up in every session automatically.
- **Add a hook** that blocks writes outside the repo root (`~/.claude/hooks/` — pre-tool-use). One safety hook does more for reliability than three prompt-engineering tricks.
- **Kill the MCP servers you're not using.** Every server in `.mcp.json` is context tax on every session — the "narrowest configuration" principle from Anthropic's own guides.

Sources:
- [Claude Code Docs — What's new](https://code.claude.com/docs/en/whats-new) `[primary]`
- [okhlopkov.com — Claude Code Setup 2026](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]`
- [Superdev Academy — Claude AI 2026 Guide: 10 hidden features](https://www.superdevacademy.com/en/blogs/claude-ai-2026-guide-coding-tips-tricks) `[analysis]`
- [Suprmind — Claude features 2026: Projects, Artifacts, Memory, Computer Use, Skills, MCP](https://suprmind.ai/hub/claude/features/) `[aggregator]`

### Why it matters to you

- **Job lens:** These are the tiny visible signals a recruiter or hiring manager reads off your public repo. *"They pin model versions"* = they've been burned by drift. *"They have a hook that blocks unsafe writes"* = they've thought about production. *"Their `.mcp.json` has 3 servers, not 15"* = they optimize for context economy. These are Solutions/FDE-shop hiring signals. Free.
- **Startup lens:** The same practices scale to your production stack — you're not learning them for interviews, you're learning them for the fact that a $2/token slip on the wrong route can eat a day of runway.
- **Insight:** The *aesthetics* of a Claude Code setup are now readable — minimalism reads as maturity, kitchen-sink reads as noise. Curate accordingly.
