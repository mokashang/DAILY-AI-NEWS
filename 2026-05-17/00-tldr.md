# TL;DR — 2026-05-17 (Sunday)

Sixty-second skim. Sunday is the **pre-game day** of the week: light news volume, but Google I/O is T-minus 2 (Tuesday 10 AM PT). The entire edition is built around: (1) close out yesterday's two weekend actions (billing audit + MCP server), (2) prep your Monday-morning I/O viewing plan, (3) cash the FDE-hiring spike that landed this week.

---

1. **Google I/O 2026 is T-minus 2 days (Tuesday May 19, 10 AM PT).** Pre-keynote signal hardens around: **Gemini "Omni"** (unified image+video+audio + natural-language video editing — UI strings + leaked clips from a Gemini Pro tester confirm), **Gemini 4 / 3.5** (depending on naming), **Aluminium OS** (Android+ChromeOS desktop convergence, OEMs locked), **Android XR glasses Gen 2** (Samsung Galaxy XR + rumored Gentle Monster partnership), **"Gemini Spark"** proactive agent, and a new wave of Google Cloud / Vertex agent SDKs. Block 10 AM–1 PM PT Tuesday. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#1-io-tminus-2) `#google #io2026 #gemini #omni #aluminium-os #xr`
2. **Anthropic + Gates Foundation: $200M, 4-year partnership.** Announced May 14, deeper coverage landing through the weekend: grants + Claude usage credits + technical support across **global health (polio, HPV, eclampsia/preeclampsia, vaccine R&D), education (K-12 tutoring + literacy/numeracy apps in sub-Saharan Africa and India), and economic mobility (smallholder-farming agriculture).** This is **Anthropic's 5th distinct distribution channel lit up in 10 days** (after PE-deployment JV May 7, Claude for Legal May 12, PwC × 30K cert May 14, Claude for Small Business May 13, and now a global-development / mission channel). → [`01-big-lab-moves.md`](./01-big-lab-moves.md#2-anthropic-gates) `#anthropic #gates-foundation #global-health #distribution`
3. **OpenAI Codex shipped to ChatGPT mobile (May 14, all plans incl. Free/Go).** Your phone is now a **control surface** for Codex sessions running on your laptop, devbox, or remote env: start work, inspect threads, review diffs, approve commands, switch models, follow terminal output — from the train. Preview launches as **OpenAI confirms ~4M weekly Codex users**. macOS desktop-app required at launch; Windows coming. → [`01-big-lab-moves.md`](./01-big-lab-moves.md#3-codex-mobile) `#openai #codex #mobile #coding-agents`
4. **Forward Deployed Engineer postings spiked ~800% in 2026 — Google Cloud alone has 59 open FDE roles, 12 tagged Applied AI.** Salesforce, Anthropic, Palantir, OpenAI, Cohere, Databricks, Scale AI, Ramp, EY (UK & Ireland) all actively hiring. Senior base: **$215–310K**; total comp at frontier-lab competitors **regularly $500K+**. This is the *single most underpriced career lane right now*, and your existing MCP / Anthropic-stack portfolio is the keyring. → [`05-career-and-startup.md`](./05-career-and-startup.md#1-fde-800-percent) `#jobs #fde #integration-engineer #anthropic #google-cloud`
5. **The highest-ROI tactical move *this Sunday*: turn on prompt caching on any project you ship.** Cache hits cost **10% of standard input price** (90% input savings); breakeven after **3+ reads in the 5-min TTL** (or 5+ reads in 1-hour TTL). Combine with **Haiku-for-cheap + Sonnet-for-hard model routing + Batch API for non-realtime (50% off)** and you can run pipelines **80–90% cheaper than naive Opus calls**. With Anthropic's Agent SDK metering live in 29 days, this is no longer a nice-to-have. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#1-prompt-caching) `#claude-api #cost-optimization #caching #agent-sdk`
6. **Karpathy's `CLAUDE.md` skills file is now at ~109K GitHub stars after 28 consecutive weeks on Weekly Trending.** The 65-line file encodes **four principles** (Think Before Coding · Simplicity First · Surgical Changes · Goal-Driven Execution) and addresses **four LLM failure patterns** (silent assumptions never verified · code/abstraction hypertrophy · collateral changes nobody asked for · absence of verifiable success criteria). If you don't have a `CLAUDE.md` in every project root by tonight, you're leaving 30%+ agent-coding quality on the floor. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#2-claude-md) `#claude-code #karpathy #agentic-coding #playbook`
7. **arXiv weekend wave: DyTopo (dynamic agent communication topology rewiring at each round) · AIRS-Bench (20 research tasks from real ML papers benchmarking science agents) · TrajAD (runtime agent-trajectory verifier with precise rollback) · "Agentic AI Orchestration Should Be Bayes-consistent" position paper.** The empirical foundation for "*which agent architecture for which job*" keeps thickening week over week. → [`04-research-progress.md`](./04-research-progress.md#1-dytopo) `#research #agents #benchmarks #verification`
8. **Sunday Action — Two 30-minute tasks before bed:** (a) **add `CLAUDE.md` to all your active project roots** (copy Karpathy's 65 lines, customize 3 lines for your stack), (b) **enable prompt caching on the highest-volume system prompt in your hottest project.** Both are reversible, both compound for the rest of 2026, and both pair perfectly with the [billing audit](../2026-05-16/03-practical-skills-and-tools.md#1-billing-audit) you (hopefully) ran yesterday. → [`03-practical-skills-and-tools.md`](./03-practical-skills-and-tools.md#5-sunday-action)

---

## One thing to DO this Sunday night

→ **Open every active project on your machine. For each:**
1. Drop in a `CLAUDE.md` at the repo root (start from [Karpathy's template](https://github.com/forrestchang/andrej-karpathy-skills), customize 3 lines for your stack/conventions).
2. Find the longest system prompt or tool-spec block in the project. Add `cache_control: {type: "ephemeral"}` on it (must be ≥2048 tokens for Sonnet 4.6, ≥4096 for Opus 4.7).
3. Run one real call against it and check the response headers for `cache_creation_input_tokens` (first call) and `cache_read_input_tokens` (subsequent calls).

**Total time: ~30 min/project · Expected savings: 60–90% input cost on cached portions, indefinitely.** Detailed recipe inside [`03`](./03-practical-skills-and-tools.md#1-prompt-caching) — and this is the *cheapest insurance against the June 15 metering change* you can buy this weekend.

## Watchlist deltas

- 🆕 **Anthropic × Gates Foundation $200M / 4-year:** new thread — Anthropic's 5th distinct distribution channel in 10 days; first mission-driven non-profit channel; watch for OpenAI / DeepMind parity moves in next 60 days
- 🆕 **OpenAI Codex mobile (4M weekly Codex users disclosed):** new thread — first "phone-as-control-surface" coding agent UI; watch Windows support timing + whether Anthropic ships Claude Code mobile parity
- 🆕 **FDE postings +800% YoY · Google Cloud 59 open:** new thread — moves into the "Jobs & Hiring Signals" tracker; pair with the AI Integration Engineer lane you committed to last week
- 🆕 **Prompt caching default playbook (60–90% savings):** new thread under "Practical Skills" — becomes the canonical pre-June-15 mitigation
- ⬆️ **Google I/O 2026:** T-minus 2 days — Omni leak: clips now public from at least one Gemini Pro tester; daily-quota burn signal (86% in 2 prompts) suggests ~10-sec clip cap
- ⬆️ **Karpathy `CLAUDE.md`:** ~109K GitHub stars; 28 weeks #1 on Weekly Trending
- ➡️ **Anthropic Agent SDK metering (June 15):** T-minus 29 days — no Anthropic email yet (expected June 8)
- ➡️ **Anthropic $30–50B raise at ~$950B:** no term sheet today
- ➡️ **Anthropic/Stainless deal:** no close yet
- ➡️ **Meta May 20 layoffs (8,000):** 3 days out — recruiter pings should spike May 21
- ➡️ **arXiv "Cattle Trade" multi-agent benchmark:** no replication scores from labs yet

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the I/O T-2 section in `01-big-lab-moves.md` |
| 20 min | `03-practical-skills-and-tools.md` — turn on prompt caching + drop `CLAUDE.md` into your projects |
| Sunday night | Apply to 2 FDE roles using your existing MCP / Claude artifacts as proof (`05`) |
| Monday AM | Re-read this `00-tldr` + the I/O viewing playbook in `03` so Tuesday's keynote lands clean |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
