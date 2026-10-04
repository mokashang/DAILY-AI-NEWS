# TL;DR — 2026-06-08 (Monday)

Sixty-second skim. **Apple closes the loop with Gemini, the IPO wave goes from "filing" to "trading," and Anthropic shows what an AI-built-by-AI company actually looks like.** **WWDC 2026 keynote at 10 AM PT today** — Bloomberg, TechCrunch and MacRumors all converge on **a Gemini-powered Siri**, a redesigned **App Intents / Apple Intelligence Extensions** surface, and an LLM-Siri public preview shipping in iOS 27 — i.e., Apple resolves the 2025–26 Siri vacuum by *licensing the model* and keeping the distribution. Meanwhile the public-markets thread keeps compounding: **Anthropic confidentially filed an S-1 on June 1** (after a **$65B Series H at a $965B post-money** and **$47B ARR run-rate**), **SpaceX prices its IPO Thursday June 11 (NASDAQ "SPCX," ~$1.75T)** as the precedent print, and **OpenAI's confidential S-1 from May 22** is in SEC review. Underneath all of it: **>80% of code merged into Anthropic's production codebase in May was authored by Claude itself** — the Karpathy hire's thesis, now a disclosed metric. For you: the **Apple/Gemini move is the platform layer settling**; the **Anthropic-self-build number is the skill signal**; **WWDC's Extensions API + Anthropic's Q2 IPO arc together rewrite the next 90 days of your apply/build calendar.**

---

1. **WWDC 2026 keynote at 10 AM PT TODAY — Siri runs on Gemini.** Bloomberg's Gurman + TechCrunch + MacRumors all converge: Apple licenses Gemini as the LLM backbone behind a rebuilt Siri (public preview in iOS 27), ships a redesigned **App Intents / Apple Intelligence Extensions** surface for third-party agents, and unveils **iOS 27 / macOS 27** with system-level AI hooks. Apple resolves the 2025–26 Siri-delay narrative by **licensing the model and keeping the distribution** — the cleanest "platform layer settles" moment of 2026. → [`01` §1](./01-big-lab-moves.md#1-wwdc) `#apple #wwdc #siri #gemini #ios27 #extensions`

2. **Anthropic confidentially filed an S-1 on June 1 — $965B post-money, $47B ARR.** Series H closed at **$65B raise / $965B post** ([Anthropic press, May 28](https://www.anthropic.com/news/series-h)), pulling forward from the prior "October 2026" target and **overtaking OpenAI in the IPO race**. The $47B ARR + Q2 profitability + the IPO triangle = three signals all confirming the same thing: Anthropic is the *most stable* frontier-AI employer right now. → [`01` §2](./01-big-lab-moves.md#2-anthropic-s1) `#anthropic #ipo #series-h #valuation`

3. **SpaceX prices its IPO this Thursday (June 11), trading Friday on NASDAQ as "SPCX" at ~$1.75T** — the largest IPO ever. It's not pure AI, but it's the **precedent print** the Anthropic + OpenAI offerings calibrate against. **Public-market AI is no longer a thought experiment; it starts in 96 hours.** → [`02` §1](./02-new-emerging.md#1-spacex-ipo) `#ipo #public-markets #spacex`

4. **Anthropic disclosed that >80% of code merged into its production codebase in May 2026 was written by Claude.** This is the Karpathy-hire thesis ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) showing up as a *disclosed operating metric*, plus a public call by Anthropic for **all frontier labs to agree on a coordinated way to slow/pause if self-improvement outruns oversight**. Self-build became the benchmark; coordination became the policy ask. → [`01` §3](./01-big-lab-moves.md#3-anthropic-self-build) · [`04` §3](./04-research-progress.md#3-self-build-coordination) `#anthropic #self-improvement #coordination`

5. **Claude Opus 4.8 shipped May 28 — 88.6% SWE-bench Verified, 69.2% SWE-bench Pro, 74.6% Terminal-Bench 2.1; "Fast mode" 2.5× faster + 3× cheaper; 4× less likely to silently let bad code through.** It's the model the >80%-of-merged-code number is being achieved on, *and* the new orchestrator-of-choice for the Opus-orchestrator/Sonnet-worker pattern. **Re-baseline your `~/.claude/CLAUDE.md` and your cost-router today.** → [`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline) `#claude #opus-4-8 #benchmarks #practical`

6. **Emerging: Microsoft shipped 7 in-house MAI models — none trained by OpenAI.** **MAI-Thinking-1** (reasoning flagship), **MAI-Code-1-Flash** (coding), **MAI-Image-2.5**, plus four others. Microsoft was the most-conspicuous "we'll just buy from OpenAI" customer; **going in-house at this scale is the loudest M&A-stack signal of the quarter** and reprices every "AI Engineer" job at MSFT/Azure. → [`02` §2](./02-new-emerging.md#2-msft-mai) `#microsoft #foundation-models #independence`

7. **Funding: Generalist AI $400M (robotics, $2B post; Radical Ventures); Flourish $500M (brain-inspired foundational AI; Bezos + Lux + GV); AlphaSense $350M ($7.5B post, AI enterprise market-intel + workflow orchestration); Cognition $1B at $26B post (Devin, $492M ARR, 50%/mo enterprise growth for 6 months); Ramp $750M (spend-management AI).** Concentration continues; vertical-AI + robotics still the two non-frontier categories pulling $100M+ rounds. → [`02` §3](./02-new-emerging.md#3-funding-wave) `#funding #cognition #robotics #vertical-ai`

8. **Research: MLEvolve (arXiv 2606.06473) — a self-evolving multi-agent framework for end-to-end ML algorithm discovery,** Retrospective Memory (cold-start KB + dynamic global memory), SOTA on MLE-Bench under a 12-hr budget. The academic counterpart to Anthropic's >80%-merged number — *automate the ML researcher, not just the dev.* → [`04` §1](./04-research-progress.md#1-mlevolve) `#arxiv #mle #self-evolving #multi-agent`

9. **Career: FDE compensation report (1,200 surveyed) — base $130–300K, senior at frontier labs $400–500K TC; Palantir 51 open roles, OpenAI 31, Databricks 12, Mistral 11, Cohere 10; total 224 FDE roles across 39 AI companies, 118 hirers system-wide.** The lane I've been calling "AI Integration Engineer" now has its **first published compensation benchmark**. → [`05` §1](./05-career-and-startup.md#1-fde-comp) `#fde #careers #compensation`

---

## One thing to DO this Monday

→ **Watch the WWDC keynote live at 10 AM PT (1 PM ET).** Then by EOD: (a) update your `Apple Intelligence Extensions` line item on the resume / LinkedIn — the spec lands today and the first-mover keyword window is ~10 days; (b) **upgrade Claude Opus 4.7 → 4.8 in your `CLAUDE.md` orchestrator config and rerun your cost trace** ([`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline)); (c) **apply to one FDE role from the Palantir/OpenAI/Databricks slate** using today's published comp band as your floor ([`05` §1](./05-career-and-startup.md#1-fde-comp)). Three artifacts, ninety minutes.

## Watchlist deltas

- 🟢 **Anthropic Series H + IPO path:** **CLOSED + ADVANCED** — $65B raise at $965B post-money confirmed May 28; **confidential S-1 filed June 1** (3+ months earlier than the May-22 "October" framing). Watchlist row flips from 🟡 to 🟢; new sub-thread: Anthropic-vs-OpenAI IPO timing-race.
- 🟢 **Claude Opus 4.8:** **SHIPPED May 28** (was ⚪ in 2026-05-22 watchlist) — SWE-bench Verified 88.6%, Fast mode 3× cheaper, $5/$25 regular pricing held. Watchlist row flips ⚪ → 🟢.
- 🆕 **WWDC 2026 + Apple-Gemini partnership:** new thread — watch (a) whether Gemini is *exclusive* or a multi-vendor picker like the rumored Extensions surface; (b) Claude/OpenAI inclusion or absence; (c) ship date of LLM-Siri public preview; (d) Apple Intelligence Extensions developer-availability date.
- 🆕 **SpaceX IPO (June 11 pricing, June 12 trading, NASDAQ "SPCX," ~$1.75T):** new thread — the precedent print for Anthropic + OpenAI; watch first-day pop and S-1 disclosure detail.
- 🆕 **Microsoft MAI in-house model suite:** new thread (was ⚪) — watch whether Azure OpenAI Service positioning shifts; FDE / Solutions hiring at MSFT; whether MAI-Code-1-Flash ships into Copilot defaults.
- 🆕 **Anthropic >80% Claude-authored code + frontier-lab pause-coordination call:** new thread — watch (a) whether OpenAI / DeepMind / xAI respond with their own metric; (b) any RSP/policy update referencing self-improvement coordination.
- 🆕 **xAI Grok V9-Medium (1.5T params, 3× current model size, mid-June release window):** new thread — release date; pricing; coding-agent benchmarks (Grok Build is the wedge).
- 🆕 **Cognition $1B / $26B post / $492M ARR:** confirmed (from prior 🟡 row) — watch hiring volume and the Devin v3 release window.
- ➡️ **OpenAI confidential S-1 (May 22):** still in SEC review; Anthropic now timing-ahead.
- ➡️ **Anthropic Agent SDK metering (June 15):** **T-minus 7 days.** Final-week toggle reminder + cost-router prep — the Opus-orchestrator/Sonnet-worker pattern in [`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline) is the direct mitigation.
- ➡️ **Code w/ Claude Tokyo (June 10):** **T-minus 2 days.** Watch for an APAC-customer SDK announcement and any Apple/Anthropic surface-area mention post-WWDC.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the WWDC keynote in [`01` §1](./01-big-lab-moves.md#1-wwdc) (read after 10 AM PT) |
| 20 min | [`01` §2–3](./01-big-lab-moves.md) (Anthropic S-1 + self-build metric) + [`04` §1](./04-research-progress.md#1-mlevolve) (MLEvolve) — the three deepest signals |
| Today (90 min) | WWDC keynote livestream + Opus 4.8 `CLAUDE.md` update + 1 FDE application (see "One thing to DO") |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-opus-48-baseline) — re-baseline orchestrator + cost trace before June-15 metering |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
