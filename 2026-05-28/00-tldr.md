# TL;DR — 2026-05-28 (Thursday)

Sixty-second skim. **The week the Big-4 fell to Claude, the agent-coders got paid, and *routing* became a category.** Six days since the last edition — and the picture sharpened in three directions at once. **Big-4 capture: KPMG (May 19/20) put Claude in front of all 276,000 employees in 138 countries** — three of four major professional-services firms (Deloitte, PwC, KPMG) are now on Claude inside ~60 days, with KPMG's Digital Gateway *natively embedding* Claude Cowork + Managed Agents (not bolted on). **Agent-coding got priced: Cognition (Devin) raised $1B at $26B post (May 27) — 2.5× up in 8 months, on $492M ARR with 50% MoM enterprise growth.** And the most under-priced infra category got a check: **OpenRouter — $113M Series B at $1.3B led by CapitalG (May 26), 100T tokens/month, 5× growth in 6 months.** Underneath: **Claude Code shipped self-hosted sandboxes + MCP tunnels + a security plugin (May 26)** — the agent-runtime now runs *inside your perimeter*. **Mythos toggle briefly appeared in Claude Code on May 25** before being pulled — the public-release path is visibly forming. And **Pope Leo XIV released the first AI encyclical, "Magnifica Humanitas," with Anthropic's Chris Olah on stage (May 25)** — frontier-AI is now a *cultural* asset class, not just a financial one.

For you: **the Big-4 capture rewrites the FDE/Solutions TAM** (every Big-4 office is now a Claude-implementation customer), **Cognition's print is the new comp floor** for agent-coding eng, and **OpenRouter validates the routing skill you're already building.**

---

1. **KPMG × Anthropic — Claude embedded for 276K employees in 138 countries.** Announced May 19, fully detailed since: Claude Cowork + Managed Agents API natively inside KPMG's **Digital Gateway** (tax, legal, PE). Anthropic names KPMG **preferred partner for private equity**. Big-4 score: Deloitte (early 2026) + PwC (May 14) + KPMG (May 19) = **3 of 4 in 60 days.** This is the FDE/Solutions TAM expansion. → [`01` §1](./01-big-lab-moves.md#1-kpmg) `#anthropic #enterprise #big4 #fde`

2. **Cognition (Devin) raises $1B at $26B post-money — 2.5× in 8 months.** Lux + General Catalyst + 8VC co-lead; Ribbit, Atreides, Founders Fund follow on. **$492M ARR; enterprise usage growing 50% MoM for 6 months straight.** Customers Mercedes-Benz, NASA, Goldman, Santander. Agent-coding is now a priced category — and Cognition is the comp anchor. → [`02` §1](./02-new-emerging.md#1-cognition) `#funding #agent-coding #devin`

3. **OpenRouter $113M Series B at $1.3B — CapitalG leads.** NVentures + ServiceNow + MongoDB/Snowflake/Databricks Ventures + a16z + Menlo Ventures. **400+ models · 8M users · 100T tokens/month (5× in 6 mo).** Model-routing/governance/optimization just got endorsed as a primary category — by Alphabet's growth fund. Your billing-audit + 3-provider-router artifacts are now on-thesis. → [`02` §2](./02-new-emerging.md#2-openrouter) `#funding #routing #infra #marketplaces`

4. **Claude Code shipped self-hosted sandboxes + MCP tunnels + a security plugin (May 26).** Managed Agents can now run tool execution in **your** infrastructure (or Cloudflare / Daytona / Modal / Vercel) while the agent loop stays on Anthropic; agents reach **your private MCP servers** via tunnel. New `/plugins` security guidance plugin monitors edits/diffs/commits in real time. The enterprise security perimeter just opened. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-sandbox) `#claude-code #managed-agents #mcp #security`

5. **Mythos toggle visible in Claude Code on May 25, then pulled.** First time **Mythos-class** model selection has appeared in a *public-facing* surface. Anthropic confirmed it's preparing a "Mythos 1 Preview" path through Claude Code + Claude Security; general release "in the near future, once we've developed the far stronger safeguards we need." The Mythos rollout has begun, slowly. → [`01` §3](./01-big-lab-moves.md#3-mythos-toggle) `#anthropic #mythos #safety #rollout`

6. **Codex updates (May 27): tax agents + Skills governance + Appshots.** OpenAI published "Building self-improving tax agents with Codex" (productionizing agents that update themselves against changing tax rules). **ChatGPT Enterprise Skills** got admin governance, upload risk-scanning, compliance-log expansion. Codex on macOS gained **Appshots** (screenshot + text from any frontmost app into Codex). The bar for "agentic coding" keeps moving — same week Cognition got paid for being ahead of it. → [`03` §2](./03-practical-skills-and-tools.md#2-codex-updates) `#openai #codex #agents #enterprise`

7. **Pope Leo XIV: "Magnifica Humanitas" — first AI encyclical, with Anthropic's Chris Olah on stage (May 25).** Explicitly frames AI as "the Industrial Revolution of our time." Not a market signal — a *cultural* one: the largest institution on Earth has framed the AI moment, and put an interpretability researcher on the stage. The non-market half of the AI conversation just got serious. → [`01` §2](./01-big-lab-moves.md#2-encyclical) `#policy #culture #anthropic #safety`

8. **Skill read of the week:** the four checks this week (KPMG, Cognition, OpenRouter, Anthropic Claude Code update) **all reward the same skill stack**: orchestrate Claude inside an enterprise perimeter, route across models for cost, verify against real tools, and quantify per-step. *Your* portfolio thesis matches the capital allocation. → [`05` §2](./05-career-and-startup.md#2-skill-stack) `#careers #skills #portfolio`

---

## One thing to DO this Thursday

→ **Apply to one KPMG/PwC/Deloitte "AI Engineer — Client Delivery" role today** ([`05` §1](./05-career-and-startup.md#1-big4-lane)) — the Big-4 just bought Claude licenses for ~1M employees combined and they don't yet have the implementation headcount; this lane has a 30–60 day open window before postings explode. Use Cognition's $26B print and KPMG's Digital Gateway as cover-letter anchors. **Also tonight:** install the new `/plugins` Claude Code security plugin ([`03` §1](./03-practical-skills-and-tools.md#1-claude-code-sandbox)) — 5 min, ships into your existing project.

## Watchlist deltas

- 🆕 **KPMG × Anthropic Big-4 capture (3/4 firms in 60 days):** new thread — watch for **Ernst & Young** to complete the sweep, plus first Digital-Gateway-equivalent at PwC/Deloitte. The FDE TAM is being *built* in front of you.
- 🆕 **Cognition $1B at $26B post / Devin $492M ARR:** new thread — watch for the next agent-coding mega-round (Cursor next? Replit?) and whether the 50% MoM enterprise-growth claim holds in Q3.
- 🆕 **OpenRouter $113M / $1.3B (CapitalG):** new thread — watch for the next routing/marketplace round (LiteLLM equivalent), whether OpenRouter becomes acquisition target, and whether the "router as primitive" pitch survives Gemini 3.5 Flash's price war.
- 🆕 **Claude Code self-hosted sandboxes + MCP tunnels:** new thread — watch for first published enterprise reference architectures (Cloudflare / Daytona / Modal / Vercel will each ship templates within 30 days).
- 🆕 **Mythos public-rollout path forming:** thread escalated from rumor → public — watch for the first official "Mythos 1 Preview" announcement on red.anthropic.com or Claude Code release notes.
- 🆕 **"Magnifica Humanitas" / Pope Leo XIV AI encyclical:** new cultural thread — watch for downstream Vatican AI ethics framework, and whether other faith/civic institutions follow.
- ➡️ **OpenAI confidential S-1 (Sept 2026 IPO):** still live from 2026-05-22 — the public S-1 will be the org-chart-by-revenue map. No new news this week; "cheap AI" thesis emerging as a risk factor.
- ➡️ **Anthropic October 2026 IPO + $30B/$900B raise:** still live — reported to potentially **surpass OpenAI's $852B March valuation** at close.
- ➡️ **Karpathy → Anthropic pre-training automation team:** still live — no public artifacts yet; first ship expected mid-to-late June.
- ⬇️ **Trump AI EO postponement:** stalled — no rescheduled signing this week; pre-deployment-eval career lane remains "scheduled, not staffed."

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + KPMG and Cognition in [`01` §1](./01-big-lab-moves.md#1-kpmg) + [`02` §1](./02-new-emerging.md#1-cognition) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-sandbox) (Claude Code update — install tonight) + [`04`](./04-research-progress.md) (constraint-violation benchmarks: the eval skill keeps repricing up) |
| Today | [`05` §1](./05-career-and-startup.md#1-big4-lane) — apply to 1 Big-4 AI-engineering role + [`05` §3](./05-career-and-startup.md#3-meta-week2) Meta-alumni Week 2 follow-up |
| Tonight | Install the Claude Code `/plugins` security guidance plugin + try one self-hosted sandbox run |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
