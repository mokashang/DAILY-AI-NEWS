# TL;DR — 2026-06-05 (Friday)

Sixty-second skim. **This edition closes a 14-day gap (last edition 2026-05-22), and the regime changed inside that window.** **Anthropic beat OpenAI to the confidential IPO filing (June 1)** — and **closed a $65B Series H at a $965B post-money** (May 28) that vaulted it past OpenAI's $852B to become **the most valuable private AI company on the planet** for the first time. **Claude Opus 4.8 shipped May 28** — 41 days after 4.7, with **dynamic workflows** that orchestrate **up to 1,000 subagents** from one prompt and **~4× less likely to let coding flaws slip unflagged**. **Microsoft fired the autonomy shot at Build 2026** (June 2) with **MAI-Thinking-1 + six in-house models** — explicitly framing it as breaking OpenAI dependency. **Gemini 3.5 Flash is now the default in Search globally** (Terminal-Bench 76.2%, MCP-Atlas 83.6%). The frame for you: **the platform you've focused on (Anthropic) just took the #1 valuation seat AND shipped the biggest single-session capability jump of the year — and three of the four headlines below are job openings in disguise.**

---

1. **Anthropic filed a confidential S-1 on June 1 — *before* OpenAI.** Morgan Stanley + Goldman Sachs + JPMorgan leading; $1T-class debut targeted as soon as Q4 2026. Bloomberg: "Anthropic's first-mover IPO edge set to widen lead over OpenAI." → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) `#anthropic #ipo #public-markets`

2. **Anthropic closed a $65B raise at $965B post-money (May 28) — surpassing OpenAI's $852B for the first time ever.** Revenue run rate **$47B (up from $30B earlier in 2026)**; trailing-12-month revenue ~$10B. CNBC headline: "Anthropic tops OpenAI as most valuable AI startup." → [`01` §2](./01-big-lab-moves.md#2-anthropic-65b) `#anthropic #funding #valuation`

3. **Claude Opus 4.8 (May 28) + dynamic workflows.** Opus 4.8 ships with **`/effort` (xhigh / ultracode), dynamic workflows up to 1,000 parallel subagents, cheaper "fast mode," and roughly 4× fewer un-flagged coding flaws vs 4.7**. *Repo-scale migrations from kickoff to merge in a single session* are now the demoed primitive. → [`01` §3](./01-big-lab-moves.md#3-opus-4-8) · [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows) `#anthropic #claude #claude-code #agents`

4. **Microsoft Build 2026 (June 2): MAI-Thinking-1 + 6 in-house models.** MAI-Thinking-1 = 35B-active params, **256K context**, **trained from scratch on commercially-licensed data with no third-party distillation**; MAI-Code-1-Flash for code-gen, MAI-Image-2.5, MAI-Transcribe-1.5. Nadella's word of the keynote: **"optionality."** → [`01` §4](./01-big-lab-moves.md#4-microsoft-mai) `#microsoft #models #independence`

5. **Gemini 3.5 Flash is now the default model in Google Search AI Mode, globally.** Benchmarks: **Terminal-Bench 76.2%, GDPval-AA 1656 Elo, MCP-Atlas 83.6%, CharXiv 84.2%** — **outperforms Gemini 3.1 Pro at <½ the cost.** Gemini 3.5 **Pro** in testing, ships "next month." → [`01` §5](./01-big-lab-moves.md#5-gemini-35) `#google #gemini #search #agents`

6. **OpenAI ships in parallel (June 4):** GPT-5.5 Instant rolling out to all ChatGPT users as default; new **GPT-Rosalind biology capabilities** (genomics/transcriptomics/sequence/structure); **real-time audio + translation models for agents** GA; self-serve **ChatGPT Ads** open to all. → [`01` §6](./01-big-lab-moves.md#6-openai-june-4) `#openai #voice #ads`

7. **Emerging — Robotics-AI just got its first two $100M+ rounds in a single week.** **Rhoda AI $450M Series A** (FutureVision — robotic intelligence on video-predictive control), **Genesis AI $105M seed** (foundational robotics model **GENE-26.5**). Pair with **Verge Labs launch (May 27)** — frontier lab on **12K+ human CNS samples** for disease biology. → [`02` §1](./02-new-emerging.md#1-robotics-foundation-models) · [`02` §3](./02-new-emerging.md#3-verge-labs) `#robotics #funding #verticals`

8. **Research: MCP-eval just professionalized.** **MCPAgentBench (arXiv 2512.24565)** — **841 real-world tasks, 20,000+ MCP tools** scraped from MCP Marketplace + GitHub + Hugging Face, **dynamic sandbox + distractor tools**. Pairs with **ETOM** (5-level tool-orchestration) and **MCP Security Bench**. The eval bar moved from "mock tools" → "your real stack with distractors and adversaries." → [`04` §1](./04-research-progress.md#1-mcpagentbench) `#benchmarks #mcp #arxiv #agents`

9. **Career — the AI lane is taking the rest of tech's oxygen.** AI Engineer postings **+143% YoY**; AI-skill wage premium **25% → 56% in 12 months**; MLE openings **+59%** while general SWE postings sit **49% below pre-pandemic**; 148,092 tech layoffs YTD. → [`05` §1](./05-career-and-startup.md#1-job-market) `#jobs #career #ml-engineer #fde`

---

## One thing to DO this Friday

→ **Ship a one-page Opus 4.8 *dynamic workflow* demo** — pick a tightly-scoped task (a 200-LOC dead-code sweep across a small repo, or a per-route security audit), run it twice — once **`/effort ultracode`**, once **standard Opus** — and **log per-step token cost + wall-clock + reviewer-edit-rate**. This artifact answers, in *one* repo link: orchestration, real-tool verification (via MCPAgentBench citation), and per-step cost — the three skills that just got repriced upward (see [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows) and [`05` §3](./05-career-and-startup.md#3-skill-repricing)). **And** — **T-minus 10 days to June 15 Agent SDK metering** — toggle the credit setting tonight if not already done ([`03` §2](./03-practical-skills-and-tools.md#2-june-15-checklist)).

---

## Watchlist deltas (14-day catch-up)

- ✅ **Anthropic $30–50B raise**: **CLOSED at $65B / $965B post (May 28).** Status 🟡→🟢. ([`01` §2](./01-big-lab-moves.md#2-anthropic-65b))
- ✅ **Anthropic October IPO path**: **Confirmed via confidential S-1 (June 1).** Anthropic *led* OpenAI to file. Status 🟡→🟢. ([`01` §1](./01-big-lab-moves.md#1-anthropic-ipo))
- 🟡 **OpenAI confidential S-1**: filed in late May per Bloomberg's "race" framing; lead bank set is Goldman + MS; Anthropic now setting the IPO calendar. Status remains 🟡.
- 🆕 **Claude Opus 4.8 / Dynamic Workflows**: new thread — watch reliability under 1000-agent ceilings, eval reports on "honesty" claim, Claude Code Enterprise pricing for dynamic-workflows access. ([`01` §3](./01-big-lab-moves.md#3-opus-4-8))
- 🆕 **Microsoft MAI model line**: new thread — watch which Foundry customers pin to MAI-Code-1-Flash, whether MAI-Thinking-1 enters Arena, and Azure-OpenAI commit step-downs. ([`01` §4](./01-big-lab-moves.md#4-microsoft-mai))
- ✅ **Gemini 3.5 Flash GA**: now default in Search globally; Gemini 3.5 Pro in testing → "next month." Status 🟢.
- 🆕 **Robotics-AI foundation-model category ($100M+ rounds)**: Rhoda AI $450M Series A + Genesis AI $105M seed in the same week; new thread to track follow-ons. ([`02` §1](./02-new-emerging.md#1-robotics-foundation-models))
- 🆕 **Verge Labs (CNS disease biology foundation models)**: new thread — first PR data, first Anthropic-style "vertical lab" beyond Isomorphic. ([`02` §3](./02-new-emerging.md#3-verge-labs))
- 🆕 **MCPAgentBench / ETOM / MSB (MCP-eval triple)**: new thread — watch which leaderboards labs publish first; whether Anthropic adds an internal MCP-Atlas-style metric to release notes. ([`04` §1](./04-research-progress.md#1-mcpagentbench))
- 🟡 **Meta Superintelligence Labs reshape**: 600 more cuts in legacy AI orgs (post-May-20 wave); Wang's "fewer conversations, more scope" framing. Watch attrition of legacy FAIR staff to Anthropic / Microsoft MAI / new labs. ([`01` §7](./01-big-lab-moves.md#7-meta-600))
- ➡️ **Anthropic Agent SDK June 15 metering**: T-10. The toggle is still manual; usage-credits overflow is opt-in. ([`03` §2](./03-practical-skills-and-tools.md#2-june-15-checklist))
- ➡️ **Trump AI/cybersecurity executive order**: still postponed since May 22 — no rescheduled signing reported in the gap window.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. |
| 5 min | This file + [`01` §1–3](./01-big-lab-moves.md) (Anthropic IPO + $65B + Opus 4.8) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows) (dynamic workflows playbook) + [`04` §1](./04-research-progress.md#1-mcpagentbench) (MCP-eval triple) — the deepest signals |
| Today | [`03` §2](./03-practical-skills-and-tools.md#2-june-15-checklist) (T-10 metering checklist) |
| Tonight | Ship the **one-page Opus 4.8 dynamic-workflow demo** with per-step cost trace |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
