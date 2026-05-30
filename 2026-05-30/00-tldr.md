# TL;DR — 2026-05-30 (Saturday)

Sixty-second skim, **eight-day-gap edition**. **The crown passed.** This week **Anthropic closed a $65B Series H at a $965B post-money valuation — surpassing OpenAI's $852B for the first time** — and on the *same day* shipped **Claude Opus 4.8** (88.6% SWE-bench Verified, fast mode **2.5× faster + 3× cheaper**, leading browser-agent at 84% Online-Mind2Web, new **"dynamic workflows"** in Claude Code). The Anthropic-stack focusing decision in [`ME.md`](../ME.md) just got the strongest possible market validation: **your chosen platform is now the most-valued private AI company on earth, the best-performing flagship model on coding/agents, and shipping the most aggressive cost cuts simultaneously.** Meanwhile **Cognition raised $1B at $26B** (Devin/Windsurf; $492M ARR — *53× revenue multiple*), **OpenRouter hit $1.3B with CapitalG** (25T tokens/wk — 5× in 6 months), and **Groq is raising $650M** for its inference-neocloud second act after Nvidia's $20B not-acqui-hire. Saturday is ship day — your weekend artifact is now obvious.

---

## What you missed (since 2026-05-22)

| Date | Headline | Why it mattered |
|---|---|---|
| Tue 5/26 | **OpenRouter $113M Series B at $1.3B** (CapitalG lead) | AI-gateway category gets Alphabet validation; 25T tokens/wk |
| Wed 5/27 | **Cognition $1B at $26B** (Lux/General Catalyst/8VC) | Devin maker; **90% of its own code is AI-written**; $492M ARR |
| Thu 5/28 | **Anthropic $65B Series H @ $965B** + **Claude Opus 4.8** + **Mythos Preview** | The single biggest valuation flip + the strongest flagship model of 2026 |
| Fri 5/29 | **Groq raising $650M** for inference neocloud | Chip-startup-to-cloud pivot; the post-acqui-hire playbook |
| All week | **142K tech layoffs in 2026** while AI infra spend tops **$700B** | The bifurcation hardens: legacy SWE/HR down, AI-applied up |

---

1. **Anthropic surpasses OpenAI: $965B > $852B, first time ever.** $65B Series H led by Altimeter/Dragoneer/Greenoaks/Sequoia; **$47B revenue run-rate** (was $44B 19 days ago); Amazon committed $5B of the $15B hyperscaler tranche; Micron/Samsung/SK hynix strategic. Dario + Daniela Amodei each ~$8B paper net worth. → [`01` §1](./01-big-lab-moves.md#1-anthropic-crown) `#anthropic #funding #valuation`

2. **Claude Opus 4.8 shipped (same day).** **88.6% SWE-bench Verified** (vs 87.6% Opus 4.7) · **69.2% SWE-bench Pro** · **74.6% Terminal-Bench 2.1** · **93.6% GPQA Diamond** · **1890 Elo GDPval-AA** · **84% Online-Mind2Web** (the strongest computer-use/browser-agent score tested). **Fast mode 2.5× faster, ~3× cheaper.** New **"dynamic workflows"** in Claude Code for large-scale problems. Same price as 4.7 ($5/M in, $25/M out). → [`01` §2](./01-big-lab-moves.md#2-opus-4-8) `#anthropic #claude #model-release`

3. **Cognition $1B at $26B post-money — and 90% of its own code is now AI-written.** Lux/General Catalyst/8VC co-lead; Founders Fund + Ribbit + Atreides participate. Enterprise customers include Goldman, Citi, Mercedes-Benz, US Army & Navy. **$492M ARR = 53× multiple** vs public-SaaS 8–15×. **Valuation 2.5×'d in 8 months** ($10.2B → $26B). → [`02` §1](./02-new-emerging.md#1-cognition) `#funding #agents #coding`

4. **OpenRouter $113M Series B at $1.3B (CapitalG lead).** Volume **25T tokens/week** — 5× in 6 months, ~100T/mo. Investors include NVentures, ServiceNow, MongoDB, Snowflake, Databricks Ventures, a16z, Menlo. **Multi-model routing as infra category** is now permanent. → [`02` §2](./02-new-emerging.md#2-openrouter) `#funding #infra #routing`

5. **Groq raising $650M for inference-neocloud second act.** $650M is **guaranteed** (Disruptive + Infinitium backstopped). Follows Nvidia's **$20B non-exclusive licensing deal** in Dec 2025 that paid out **$7.6B to shareholders (~$64/share)** in Feb 2026. Template for the post-not-acqui-hire pivot. → [`02` §3](./02-new-emerging.md#3-groq) `#funding #chips #inference`

6. **Practical: Opus 4.8 dynamic workflows + Sonnet workers ≈ the new cost-aware default.** With fast mode 3× cheaper and dynamic workflows native, the **Opus orchestrator + Sonnet worker** pattern carried over from 2026-05-22 now runs **~60% cheaper than week-ago all-Opus** at *better* SWE-bench. Run this benchmark on your own repo this weekend; the metering deadline (June 15) is **T-16**. → [`03` §1](./03-practical-skills-and-tools.md#1-opus-4-8-routing) `#claude-code #cost #orchestration`

7. **Research: AI research agents are *narrowing* scientific exploration** (arXiv 2605.27905, May 27). 4 agent frameworks × 6 LLMs generated **37,802 ideas** from shared seed literature — and converged. Counter-thread to Karpathy's "Claude-accelerates-Claude" mandate ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)): **automation introduces homogeneity unless you design against it.** This is the research wedge to claim. → [`04` §1](./04-research-progress.md#1-research-agents-narrow) `#research #arxiv #agents`

8. **Skill read of the week:** the **valuation flip + Opus 4.8 + dynamic workflows + OpenRouter scale + research-agent homogeneity** are *one* story — **the agentic stack is now the platform, and the moats are routing, cost-control, eval-against-real-tools, and exploration-diversity.** Each of those is a hireable specialty. → [`05` §1](./05-career-and-startup.md#1-anthropic-stack-validated) `#careers #skills`

---

## One thing to DO this Saturday (ship day)

→ **Ship the v0 dual-model "Opus-4.8-orchestrator + Sonnet-4.6-worker" benchmark on your own repo.** Carries the Friday 5/22 dual-model sanitiser ([2026-05-22/05 §1](../2026-05-22/05-career-and-startup.md#1-karpathy-signal)) into the post-Opus-4.8 world. Spec: pick *one* real coding task in your repo (≥3 files touched, ≥1 test), run it 3 ways — **(a)** all Opus 4.8, **(b)** all Sonnet 4.6, **(c)** Opus 4.8 orchestrator + Sonnet 4.6 workers with the new **dynamic workflows** flag. Log **cost / wall-clock / test-pass rate** per run. Publish the table on LinkedIn Sunday night with "Opus 4.8 dynamic workflows" and "model routing" in the headline. Three interview questions answered in one artifact: orchestration, cost-awareness, and real-tool verification. **See [`03` §1](./03-practical-skills-and-tools.md#1-opus-4-8-routing) for the exact recipe.**

---

## Watchlist deltas

- ✅ **Anthropic raise:** **CLOSED $65B @ $965B** (was "imminent" for 3+ weeks). Status flips 🟡→🟢-closed.
- ✅ **Anthropic flagship model cadence:** **Opus 4.8 shipped May 28** (60 days after 4.7). The 8-week flagship-refresh cadence is now empirical.
- 🆕 **Anthropic > OpenAI valuation:** new thread — watch whether this flips back at OpenAI's S-1 reveal (~Sept) or sticks; first time a private AI co overtook the OpenAI mark.
- 🆕 **Claude Mythos Preview:** new thread — "advanced cybersecurity" model in limited preview; pairs with the (still-postponed) EO cyber-clearinghouse half.
- 🆕 **Cognition / Devin enterprise traction:** new thread — Goldman + Citi + Mercedes + US Army/Navy customer logos are the strongest *enterprise* agentic-coding validation to date.
- 🆕 **OpenRouter / multi-model routing as a category:** new thread — 25T tokens/wk + CapitalG cap-table is "AI gateway" graduating from feature to category.
- ➡️ **OpenAI confidential S-1 / Sept IPO:** still pre-roadshow. **Anthropic's $965B raise is now the comp** — OpenAI's $852B is "stale." Watch for S-1 amendment / valuation re-mark.
- ➡️ **Trump AI EO:** still **postponed**; tech billionaires (Zuckerberg/Musk/Sacks) named as the lobbyists who pulled it. Pre-deployment-eval lane stays *delayed-not-dead*.
- ➡️ **Anthropic Agent SDK metering (June 15):** **T-16 days.** Your weekend artifact *is* the mitigation.
- 🆕 **Tech-layoff macro:** **142K cuts YTD in 2026** while hyperscalers commit **$700B** in 2026 capex (~2× 2025). The bifurcation is now the dominant career signal.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Anthropic crown + Opus 4.8 in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-opus-4-8-routing) Opus 4.8 routing recipe + [`04` §1](./04-research-progress.md#1-research-agents-narrow) research-homogeneity paper |
| This weekend | Ship the artifact in [`05` §3](./05-career-and-startup.md#3-saturday-artifact) — Sunday-night LinkedIn post timing |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
