# Practical Skills & Tools — 2026-06-01

Two things to ship this week, both small and direct. **First**, re-route the agent-orchestration pattern you built [over the previous weekend](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — the orchestrator is now **Opus 4.8**, not Opus 4.7, and your README's claimed numbers improved without you doing any code work. **Second**, with **June 15 only 14 days out**, do the **Anthropic Agent SDK metering audit tonight** — this is the last full work-week of subsidy. The third item: **Codex CLI v0.134.0** finally has **OAuth for streamable HTTP MCP** — if you've been gating your MCP server behind an API-key-in-env hack, this weekend is the moment to swap it to real auth. And the cross-runtime thread to seed: **start a "which model did I route to for which task, and what did it cost" log** — that's the eval/verification skill the job market now prices, not raw prompting.

Tags: `#claude-code #opus #routing #cost #orchestration #mcp #codex #june-15 #playbook`

---

## 1. Re-route orchestrator to Opus 4.8, re-run the cost log {#1-opus-48-routing}

**What to do tonight (45 min):** Update the **dual-model agent-team pattern** from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) — the **Opus orchestrator + Sonnet worker** split that the archive's [Monday "one thing to do"](./00-tldr.md#one-thing-to-do-this-monday) already names. The structural pattern is unchanged; the numerator improved:

- **Orchestrator role**: `claude-opus-4-8` (was 4-7) — the planner that decomposes work, reviews subagent output, and decides when to stop.
- **Worker role**: `claude-sonnet-4-6` — handles the bulk of the discrete sub-tasks; cheap enough to call many of in parallel.
- **Verifier role** (optional): `claude-haiku-4-5` — runs as a final-pass review (the **TrajAD-style rollback** primitive from [2026-05-19/04](../2026-05-19/04-research-progress.md)) — flags bad worker output before the orchestrator integrates it.

What to *actually* do tonight, in order:

1. **Open every project README in your portfolio**, ctrl-F **"Opus 4.7"**, **"Claude Opus"** (unversioned), and **"Anthropic's frontier model"** — replace each with **"Claude Opus 4.8 (released 2026-05-28)"** with the date so the freshness signal is visible.
2. **Add a `cost-log.md`** to your dual-model sanitiser project that captures: input tokens / output tokens / cost / wall-clock per orchestrator step, and the same for each worker call. The eval that matters is **cost-per-successful-task**, not capability alone.
3. **Re-run your eval suite** (the 5-case eval from [`ME.md`](../ME.md#active-portfolio-artifacts)) and capture the **before/after numbers** with Opus 4.7→4.8 substitution. Even if the substitution is automatic, the *act of measuring* is the artifact.
4. **Commit the cost log to GitHub** with a screenshot in the README. *This is the eval artifact recruiters now grep for.*

**Sources / required reading:**
- [Anthropic news (Opus 4.8 + model lineup)](https://www.anthropic.com/news) `[primary]` — official release notes land here
- [Claude Platform release notes](https://platform.claude.com/docs/en/release-notes/overview) `[primary]` — canonical changelog (June-15 model deprecation also lives here)
- [Fortune — Anthropic releases Claude Opus 4.8](https://fortune.com/2026/05/29/anthropic-raises-65-billion-at-record-965-billion-valuation-promises-mythos-ai-model-in-wide-release-in-coming-weeks-releases-claude-opus-4-8/) `[secondary]`
- [shareuhack — Cursor vs Claude Code vs Windsurf 2026](https://www.shareuhack.com/en/posts/cursor-vs-claude-code-vs-windsurf-2026) `[analysis]` (Composer 2.5 pricing comparison for the routing table)
- See also: [2026-05-22/03 §1 the pattern as originally introduced](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)

### Why it matters to you

- **Job lens:** **The interview question this primes you for is "tell me about a time you optimized agent cost without losing quality."** Having a `cost-log.md` with real before/after numbers (Opus 4.7→4.8 substitution effect, parallel-worker batching effect, Haiku verifier effect) means you answer that question with a screenshot, not a paragraph. That's the difference between a "good candidate" and an "obvious hire" at the **AI Integration Engineer / FDE / Solutions** level.
- **Startup lens:** This same pattern is **the unit-economics moat of every Claude-native B2B product**. If your model-routing layer beats your competitor's by 40% at the same quality, you can either price 30% lower or extend your runway 60%. That's not a feature; it's a *moat*. Make it explicit in pitch decks: *"our agent cost-per-task on representative workloads, vs naive Opus-only baseline."*
- **Insight:** The skill that just got more valuable is **measurement under model churn** — the model lineup is going to ship a meaningful upgrade every 2–6 weeks for the rest of 2026. The portfolio artifact that wins is **the harness, not the result**: a re-runnable eval that produces a fresh cost/quality number every model release. Build the harness once, run it forever.

→ Cross-link: [`01` §2 Opus 4.8 release](./01-big-lab-moves.md#2-opus-48) · [2026-05-22/03 §1 the pattern](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`04` §1 efficient-benchmarking research](./04-research-progress.md#1-efficient-benchmarking).

---

## 2. Anthropic Agent SDK metering — T-14 audit checklist {#2-june-15-audit}

**What to do this week (one focused 90-min block):** As of today, you are **14 days** from the [June 15 Agent SDK metering change first reported on 2026-05-16](../2026-05-16/01-big-lab-moves.md). The structural facts haven't changed:

- **Programmatic Claude** — Agent SDK, `claude -p`, Claude Code GitHub Actions, third-party agents using your subscription — moves off your Claude subscription limit onto a **separate monthly credit pool** at **API list rates, no rollover**.
- **Credit pool by tier:** Pro **$20/mo** · Max-5x **$100/mo** · Max-20x **$200/mo**.
- **Interactive Claude.ai, terminal Claude Code, Claude Cowork are NOT affected.**
- **Same date (June 15) retires Sonnet 4 and Opus 4 from the API** — if any of your code paths still hard-code those model strings, they break that day.
- **The Agent SDK June 15 credit doesn't auto-activate** ([2026-05-18 silent-failure warning](../2026-05-18/03-practical-skills-and-tools.md)) — you must manually toggle it. **5-minute fix; silent failure if skipped.**

**The 90-min audit checklist:**

1. **Pull your last 30 days of Anthropic billing.** Console → Billing → Usage → CSV export. Sort by API key.
2. **Identify every programmatic surface** — *which* API keys generate spend, *what* job ran them, *which* model they hit. Anything via Agent SDK / `claude -p` / GH Action is on the meter June 15.
3. **Pick a target monthly budget** (likely your current spend, possibly +20% for slack). Compare to the credit-pool ceiling at your tier (Pro $20 / Max-5x $100 / Max-20x $200). If you're over the ceiling, **either upgrade tier or move workloads to the API** (where you pay per-token but with no monthly cap surprise).
4. **Toggle the Agent SDK credit** (Console → Plan → enable "Agent SDK Credit" — name may vary; check release notes). If you're not 100% sure it's enabled, log into your account on June 16 morning and check that the meter started.
5. **Hard-code model-string replacements**: every `claude-sonnet-4` → `claude-sonnet-4-6`, every `claude-opus-4` → `claude-opus-4-8`. Search-and-replace your entire codebase, then run your eval to confirm nothing regressed.
6. **Write a 3-paragraph post on your blog/LinkedIn** documenting (a) what you found in the audit, (b) what you changed, (c) what the cost diff was. **This is the artifact** — a personal Claude billing audit is one of the items in [`ME.md`'s active portfolio list](../ME.md#active-portfolio-artifacts).

**Sources:**
- [Anthropic — Higher usage limits for Claude and a compute deal with SpaceX](https://www.anthropic.com/news/higher-limits-spacex) `[primary]` (context: why limits doubled before June 15)
- [InfoWorld — Anthropic puts Claude agents on a meter across its subscriptions](https://www.infoworld.com/article/4171274/anthropic-puts-claude-agents-on-a-meter-across-its-subscriptions.html) `[secondary]`
- [Devtoolpicks — Anthropic Splits Claude Subscriptions: What Changes for Indie Hackers on June 15](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[analysis]`
- [Codersera — Anthropic's June 15 Billing Change: What Every Claude Code & Agent SDK User Must Do](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/) `[analysis]`
- [Apiyi — Anthropic June 15 Claude subscription billing overhaul: 5 key points](https://help.apiyi.com/en/anthropic-claude-subscription-agent-sdk-billing-split-june-2026-en.html) `[analysis]`
- [Claude Platform — Release notes overview](https://platform.claude.com/docs/en/release-notes/overview) `[primary]` (model deprecation dates)

### Why it matters to you

- **Job lens:** A **public personal-billing audit writeup** is the single highest-leverage artifact you can ship this week — it demonstrates **operational discipline + cost literacy + writing**, all three of which the FDE / Solutions / Integration roles screen heavily for. Most candidates can prompt; few can run their own AP-style audit. Be the second.
- **Startup lens:** This is also the **dress rehearsal for B2B AI pricing literacy** — if you're going to charge customers for Claude-backed work, you need to understand the [provider-cost model that Anthropic itself just changed](../2026-05-16/01-big-lab-moves.md). The startup-relevant lesson: **avoid pricing models that pass through unbounded provider cost to customers** — Anthropic just demonstrated how fast that ceiling can move.
- **Insight:** The deprecation of Opus 4 / Sonnet 4 on the same day as the metering change is **a deliberate "fresh start" moment** — Anthropic is recompiling its customer base around the new model + new pricing simultaneously. Read it as: *Anthropic is willing to take short-term customer pain to make the next 18 months of platform economics cleaner.* That's the behavior of a company optimizing for a public-market quarterly cadence ([`01` §2 Opus 4.8](./01-big-lab-moves.md#2-opus-48)).

→ Cross-link: [2026-05-16/01](../2026-05-16/01-big-lab-moves.md) (first announcement) · [2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md) (silent-failure warning).

---

## 3. Codex CLI v0.134.0 — OAuth for streamable HTTP MCP servers {#3-codex-cli-mcp}

**What to do this weekend (2 hours):** Take **one of your existing MCP servers** and harden it with **OAuth-gated streamable HTTP** — using the **Codex CLI v0.134.0 (May 26)** primitives. This is the **enterprise-grade MCP demo** that the FDE/Solutions interview process loves.

The structural change in Codex CLI v0.134.0:

- **`/history` conversation search** — a bigger UX feature than it sounds; means you can demo "the same agent across yesterday's, today's, and tomorrow's session" continuity.
- **`--profile` as canonical model/runtime selector** — your cross-model routing logic now has a clean API to target.
- **Per-server MCP env targeting** — each MCP server gets its own scoped env, so you can demo a single agent talking to *three* MCP servers (one prod, one staging, one personal) without env conflicts.
- **OAuth for streamable HTTP MCP transports** — the one that actually unlocks enterprise sales.

The recipe:

1. **Pick your simplest MCP server** (your portfolio MCP server from [`ME.md`](../ME.md#active-portfolio-artifacts), or a fresh one if you don't have one yet — see Simon Willison's Playwright MCP guide linked below for the 30-min starter).
2. **Add OAuth (Auth0 / Clerk / GitHub App / Workspace OAuth — pick the one you already have an account for)** in front of the streamable HTTP transport.
3. **Configure both Claude Code and Codex CLI** to call your server using the same OAuth flow. This is the *cross-runtime fluency* signal from [`02` §3](./02-new-emerging.md#3-codex-cli).
4. **Record a 90-sec demo video** showing: (a) Claude Code calling the MCP server through OAuth; (b) Codex CLI calling the same server with the same OAuth; (c) the server log showing the bearer tokens were validated.
5. **Embed the video in the MCP server's README** alongside the cost log from [`§1`](#1-opus-48-routing).

**Sources / required reading:**
- [OpenAI — Codex Changelog](https://developers.openai.com/codex/changelog) `[primary]`
- [Releasebot — Codex Updates by OpenAI - May 2026](https://releasebot.io/updates/openai/codex) `[aggregator]`
- [Simon Willison's TILs — Using Playwright MCP with Claude Code](https://til.simonwillison.net/claude-code/playwright-mcp-claude-code) `[primary]` (the canonical "MCP starter" tutorial)
- [Simon Willison — claude-code tag](https://simonwillison.net/tags/claude-code/) `[primary]` (best ongoing practitioner notes)
- [alexop.dev — Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks Explained](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [Shrivu Shankar — How I Use Every Claude Code Feature](https://blog.sshh.io/p/how-i-use-every-claude-code-feature) `[analysis]`
- [Trail of Bits — claude-code-config (opinionated defaults)](https://github.com/trailofbits/claude-code-config) `[primary]` (reference config from a security-focused team)
- [IntuitionLabs — Claude Skills vs. MCP: A Technical Comparison for AI Workflows](https://intuitionlabs.ai/articles/claude-skills-vs-mcp) `[analysis]`

### Why it matters to you

- **Job lens:** **An OAuth-gated MCP server with a 90-sec demo video** is the single best "FDE artifact" you can build in a weekend right now. It shows: (a) you understand MCP (table-stakes), (b) you understand enterprise auth (the reason most MCP demos *fail* the procurement gate), and (c) you're already thinking cross-runtime. Apply with this in your portfolio in the *body* of the application — not just the resume — to Anthropic Solutions, OpenAI FDE, Sierra, Cursor, and any consulting AI-engineer role.
- **Startup lens:** This *is* the wedge from [`02` §3](./02-new-emerging.md#3-codex-cli) — **vertical MCP servers behind enterprise SSO**, sold per-seat. The 2-hour build is the *prototype* of that wedge. If the demo lands well in interviews, that's an indirect validation signal for the startup version. The market does not yet have a clear leader here.
- **Insight:** The thing that's *commoditizing* is "I can prompt a model and get output." The thing that's *appreciating* is **"I can ship a multi-runtime, auth-gated, cost-observable, eval-covered agent that an enterprise can deploy without a security review breakdown."** Every line in this section is a step toward the latter.

→ Cross-link: [`02` §3 Codex CLI release](./02-new-emerging.md#3-codex-cli) · [`05` §1 the FDE / Solutions hiring lane](./05-career-and-startup.md#1-comp-refresh).

---

## 4. MCP hygiene: keep the server count low, prefer HTML over Markdown for Claude output {#4-mcp-hygiene}

**Two small but high-impact tactical tips that surfaced in late May:**

**A. MCP server count discipline.** Per Simon Willison's notes and the broader practitioner consensus: **2–3 MCP servers is the sweet spot; 10+ degrades context.** When MCP tool descriptions exceed **~10% of context**, Claude starts auto-deferring tool details and loads them on demand — which means you've paid for context window space that the model isn't actually using directly. The practical default: **start with one MCP server per task, not one per "tool I might use someday."**

**B. HTML > Markdown as Claude's output format** for structured documents. Per **Thariq Shihipar (Claude Code team at Anthropic)** in *"Using Claude Code: The Unreasonable Effectiveness of HTML"* (covered on Simon Willison's blog, May 8 2026): asking Claude to emit **HTML** rather than Markdown yields more reliable structure for **tables, multi-level nesting, and embedded styling** — and the model has been trained on far more HTML than Markdown. Direct application: **for your reports, dashboards, or generated docs, ask for HTML and let the rendering layer downstream handle it** (e.g., Pandoc to PDF / DOCX, or just open in a browser).

**Sources:**
- [Simon Willison — claude-code tag (running notes incl. HTML/Markdown thread and MCP discipline)](https://simonwillison.net/tags/claude-code/) `[primary]`
- [Simon Willison's TILs — Using Playwright MCP with Claude Code](https://til.simonwillison.net/claude-code/playwright-mcp-claude-code) `[primary]`
- [Druce.ai — Speedrunning the Claude Code learning curve](https://druce.ai/2026/02/claude-code) `[analysis]`
- [alexop.dev — Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks Explained](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [Hyperdev — When "Claude Code for Productivity" Meets Reality](https://hyperdev.matsuoka.com/p/when-claude-code-for-productivity) `[analysis]` (a useful skeptical view)

### Why it matters to you

- **Job lens:** Both tactics are **screened-for in technical FDE / Solutions interviews** disguised as "tell me how you'd debug a Claude integration that's slower than expected." If your answer mentions **"tool-description percentage of context"** unprompted, you're in the top decile of interviewees on that question.
- **Startup lens:** The MCP-server-count discipline is **directly relevant to product design** — if you're building a Claude-native B2B product, you have an architectural decision: *do I expose 30 MCP tools to the model, or do I expose a routing-layer "meta-tool" that exposes 30 tools through 3?* The latter is the better architecture in 2026.
- **Insight:** The "unreasonable effectiveness of HTML" insight generalizes beyond Markdown: **the model is best at the formats it was most exposed to in training**, and the *underlying* distribution of training data favors HTML / Python / JSON / TypeScript over their newer-but-cleaner alternatives. Match your output format to the model's distribution, not to your editor's defaults.

→ Cross-link: [`§3 OAuth-gated MCP server`](#3-codex-cli-mcp) · [2026-05-17/03 Karpathy CLAUDE.md playbook](../2026-05-17/03-practical-skills-and-tools.md).
