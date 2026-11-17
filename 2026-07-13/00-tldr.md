# TL;DR — 2026-07-13 (Monday)

Sixty-second skim. **Resuming after a 7-week gap.** The frontier didn't wait: **GPT-5.6 (Sol · Terra · Luna) went public Thursday** after a Commerce-Dept gated preview, **Meta shipped Muse Spark 1.1** (1M-ctx, agentic, first paid Meta Model API), and **Gemini 3.5 Pro targets Thursday (July 17)** on a scrapped-and-rebuilt base. Underneath the model wave, **Apple filed a 41-page trade-secret suit against OpenAI + its io Products hardware subsidiary**, naming **400+ ex-Apple employees**, the Chief Hardware Officer, and "show-and-tell" recruiting sessions with real Apple components. And the deepest signal for your career math: **Anthropic's Claude Corps fellowship applications close Friday** ($85K, 1,000 slots, $150M pool), **TCS is spinning up 5,900–8,900 forward-deployed engineers**, and Anthropic + Google + Broadcom locked in **3.5 GW of new TPU compute**. **The FDE lane went from thesis to global-hiring gold rush inside 8 weeks.**

---

1. **Apple sues OpenAI + io Products (filed July 10).** 41-page trade-secrets complaint in N.D. Cal. names **CHO Tang Yew Tan** + former Apple engineer **Chang Liu**; alleges recruiting of **400+ ex-Apple employees**, Liu exploited an auth flaw to download **1,000+ pages of hardware docs**, Tan ran **"show-and-tell" sessions where candidates brought Apple hardware samples**. Apple wants an injunction + product-redesign order on OpenAI hardware. → [`01` §1](./01-big-lab-moves.md#1-apple-openai) `#apple #openai #hardware #lawsuit`

2. **GPT-5.6 goes fully public — Sol / Terra / Luna + GPT-Live (July 9).** After Commerce-Dept gated preview to ~20 orgs, OpenAI opened access across ChatGPT, Codex, and API. **Sol $5/$30 · Terra $2.50/$15 · Luna $1/$6 per M tokens.** Altman: Sol is **~54% more token-efficient** than 5.5 on coding. **GPT-Live-1 / mini** ships full-duplex voice (listens while it speaks). → [`01` §2](./01-big-lab-moves.md#2-gpt-56) `#openai #gpt-5-6 #voice #pricing`

3. **Muse Spark 1.1 = Meta's first agent-native paid API (July 9).** 1M-ctx, native tool + computer use, active context management, main-or-subagent role. Benchmarks: **MCP-Atlas 88.1 · JobBench 54.7 (vs Opus 4.8 48.4 / GPT-5.5 38.3) · HLE-with-tools 62.1 · Finance Agent v2 57.2.** API $1.25/$4.25 per M + $20 free credits. Zuckerberg returned to X after 3 years to announce. → [`02` §1](./02-new-emerging.md#1-muse-spark) `#meta #muse-spark #agents #pricing`

4. **Gemini 3.5 Pro targets Thursday, July 17 — on a full architectural rebuild.** Google scrapped the 2.5 Pro base and started over. **Reported 2M context + Deep Think reasoning + autonomous workflows**, but *every* spec (including the date) is third-party sourced — the public API today still lists only 3.5-flash + 3.1-pro-preview. → [`01` §3](./01-big-lab-moves.md#3-gemini) `#google #gemini #rebuild #reasoning`

5. **Anthropic × Google × Broadcom — 3.5 GW of TPU compute** (announced last week; multi-GW capacity starting 2027, mostly US). For scale: **1 GW ≈ Anthropic's entire compute fleet at the start of 2026.** Anthropic run-rate revenue **$30B** (up from ~$9B at end of 2025). → [`01` §4](./01-big-lab-moves.md#4-anthropic-compute) `#anthropic #google #broadcom #tpu #compute`

6. **Career + startup gold rush around FDEs — this week's most actionable lane.** **Claude Corps fellowship: $85K, 1,000 slots, $150M pool — applications close Fri, July 17** (100-fellow Oct cohort). **TCS building 5,900–8,900 FDEs** (1–1.5% of associates). **OpenAI Deployment Co + Anthropic × Blackstone JV** already staffed. Comp: Anthropic FDE **$300K–$1.2M TC** by level. → [`05` §1](./05-career-and-startup.md#1-claude-corps) · [`05` §2](./05-career-and-startup.md#2-fde-goldrush) `#fde #careers #anthropic #claude-corps`

7. **Anthropic's J-lens paper — the first tractable "seat of thought" experiment in a frontier model.** New interpretability lens; identified a **~25-concept "J-space"** carrying **<10% of activation variance** that behaves like the **global-workspace** in consciousness neuroscience. **Open-sourced, live demo at neuronpedia.org/jlens.** → [`04` §1](./04-research-progress.md#1-jspace) `#research #interpretability #anthropic #consciousness`

8. **Practical: Claude Code + MCP hygiene as a shipped skill.** Sweet spot **3–6 MCP servers**, `ENABLE_TOOL_SEARCH=true` for large tool sets, `.claude/rules/` for path-specific loading, disable unused w/ `/mcp`, prefer CLI (`gh`, `gcloud`) over MCP when one command suffices. **Auto-mode default now on Bedrock/Vertex/Foundry**, Claude Code desktop shipped a **built-in browser**. → [`03` §1](./03-practical-skills-and-tools.md#1-mcp-hygiene) `#claude-code #mcp #practical`

---

## One thing to DO this Monday

→ **Submit Claude Corps application before Friday, July 17.** $85K, 100 slots in Cohort 1, in-person year at a nonprofit host — this is the closest thing to a paid Anthropic residency for early-career candidates ([`05` §1](./05-career-and-startup.md#1-claude-corps)). If you're already targeting Anthropic FDE/Solutions, a Corps year is a legible on-ramp with `#claude` on every project. Even if you don't get in, the artifact you build for the application (a nonprofit-fit workflow using Claude) is a portfolio piece. **Also today**: migrate any code calling `deepseek-chat` / `deepseek-reasoner` — hard cutoff **July 24, 15:59 UTC** ([`03` §4](./03-practical-skills-and-tools.md#4-deepseek)).

## Watchlist deltas (returning after gap)

- 🆕 **Apple v. OpenAI trade-secret suit:** new thread — track discovery timeline; determines whether **OpenAI hardware roles freeze** vs. accelerate. Blast radius: io Products, ex-Apple silicon/on-device candidates.
- 🆕 **GPT-5.6 family fully public:** track (a) whether the pre-release Commerce review becomes normal practice, (b) how Sol adoption reshapes the **coding-agent cost curve** given the 54% token-efficiency claim.
- 🆕 **Muse Spark 1.1 = Meta's paid-API turn:** first Meta model with an official paid endpoint. Signals Meta's return to *product* competition (post-Superintelligence Labs restructure).
- 🆕 **Gemini 3.5 Pro rebuild (Thu July 17):** unusual signal — Google scrapped and restarted the base. If it lands with claimed specs, it's the **first 2M-ctx frontier model** shipping.
- 🆕 **Anthropic × Google × Broadcom 3.5 GW:** compute path to 2027 now contracted; the revenue path ($30B run-rate) is what services it. The IPO watchlist thread from 2026-05-22 remains alive.
- 🆕 **Claude Corps ($150M / 1,000 fellows):** new thread — the largest structured on-ramp Anthropic has funded; watch cohort 1 outcomes as a leading indicator of Anthropic's talent-development thesis.
- 🆕 **TCS 5,900–8,900 FDEs:** the FDE role is now a *global consulting hiring pattern*, not a lab-side quirk. Watch Infosys / Wipro / Accenture follow.
- 🆕 **China overseas AI restrictions (Reuters, July 7):** MOFCOM + Alibaba/ByteDance/Z.ai meetings on tiered export controls. If enacted, closes the arbitrage of running Chinese open-weights offshore.
- 🆕 **DeepSeek deprecation (T-11 days):** `deepseek-chat` / `deepseek-reasoner` retire **July 24, 15:59 UTC**. **`deepseek-reasoner` → v4-flash (thinking)**, NOT v4-pro — silent capability downgrade if you don't remap explicitly.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Apple/OpenAI suit in [`01` §1](./01-big-lab-moves.md#1-apple-openai) + Claude Corps deadline in [`05` §1](./05-career-and-startup.md#1-claude-corps) |
| 20 min | [`04` §1](./04-research-progress.md#1-jspace) (J-lens) + [`02` §1](./02-new-emerging.md#1-muse-spark) (Muse Spark benchmarks) — the two deepest signals |
| Today | Apply to Claude Corps + migrate DeepSeek calls |
| Tonight | Set up 3–6 MCP server profile in Claude Code + enable `ENABLE_TOOL_SEARCH=true` ([`03` §1](./03-practical-skills-and-tools.md#1-mcp-hygiene)) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
