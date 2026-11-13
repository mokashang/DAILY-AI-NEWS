# TL;DR — 2026-09-19 (Saturday)

Sixty-second skim. **The IPO IS the story now — and the sequence flipped.** Since our last edition (Sept 10), **Anthropic pushed its IPO to November at a $2 trillion valuation with Nvidia lined up for a ~$10B cornerstone check** (Reuters via Bloomberg, Sept 11); **Sam Altman told Fortune OpenAI will NOT go public in 2026** (walking back the Q4 target we tracked from May 22); **Anthropic disclosed that Claude now leads 26% of its own R&D** running ~30,000 internal agents (Bloomberg / Washington Post, Sept 17); **California Governor Newsom signed an executive order fast-tracking an AI "kill switch" framework** (Sept 18, Nov 16 report deadline); and **the three biggest labs are meeting weekly to stand up a FINRA-style self-regulator** (Sept 18). Plus: **DeepSeek V4.1-Flash** blew up the price/quality frontier (552B MoE, 1M ctx, MIT-licensed, ~$0 marginal). For you: **the compute-era hiring wave is here** ($517B of Anthropic compute commitments = $517B of downstream infra/deployment jobs), and **the "verification / eval / safety" lane just got a state-level tailwind** in California.

---

1. **Anthropic → November IPO, ~$2T valuation, up to $100B raise, Nvidia mulling $10B cornerstone.** WSJ (Sept 18) confirms the calendar move; Reuters (Sept 11) broke the Nvidia stake. Anthropic annualised revenue jumped from **~$9B end-2025 → ~$65B end-July**, with management projecting **$190–200B by 2028**. → [`01` §1](./01-big-lab-moves.md#1-anthropic-november-ipo) `#anthropic #ipo #nvidia`

2. **Sam Altman: OpenAI is NOT going public in 2026** — pushed to 2027 (Fortune, mid-Sept), reversing the Q4 target we tracked from [2026-05-22](../2026-05-22/01-big-lab-moves.md#2-openai-s1). CFO Friar: "we have flexibility." **Anthropic goes first now.** → [`01` §2](./01-big-lab-moves.md#2-openai-postpones) `#openai #ipo #timing`

3. **Anthropic: Claude "leads" 26% of its own R&D, up from ~0% in February.** **~30,000 internal agents** at any given time; 1 in 47,000 decisions blocked. Recursive self-improvement stops being a metaphor. → [`01` §3](./01-big-lab-moves.md#3-claude-26-percent-rd) `#anthropic #agents #recursive`

4. **California Newsom signs AI "kill switch" executive order (Sept 18)** — working group has until **Nov 16** to recommend the framework; independent monitors inside labs also on the table. Builds on SB 53 (2025) + SB 813 (2026). → [`01` §4](./01-big-lab-moves.md#4-newsom-kill-switch) `#policy #california #safety #jobs`

5. **FINRA-style AI standards body** — OpenAI's Chris Lehane confirms Anthropic, Google and OpenAI have been meeting **for weeks** to design a voluntary pre-release testing body, per Hassabis's July proposal. Antitrust waiver: not needed, they say. → [`01` §5](./01-big-lab-moves.md#5-finra-for-ai) `#policy #governance`

6. **DeepSeek V4.1-Flash (Sept 10) — 552B-param native-multimodal MoE, 1M ctx, MIT-licensed, outperforms V4-Pro.** New Causal Encoder-Decoder architecture (8B active on input, 16B on output). This is the **first frontier-quality open model that beats its own paid flagship.** → [`02` §1](./02-new-emerging.md#1-deepseek-v41-flash) `#deepseek #open-source #multimodal`

7. **Anthropic + Nscale $45B cloud deal, ~460 MW in West Virginia** — one of a wave of "smaller, faster" data-center deals both Anthropic and OpenAI are chasing (CNBC, Sept 18). **$517B in total Anthropic compute commitments now** (up from $180B in early summer). → [`02` §2](./02-new-emerging.md#2-nscale-compute-wave) `#compute #datacenter #anthropic`

8. **Practical: Anthropic Smart Reports for Enterprise (beta) + Claude Code Sept updates.** Smart Reports auto-detects "which repeated patterns are worth packaging as shared Skills" — read: **Anthropic just built the tool that industrializes the Skills refactor** from [2026-09-10/03 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree). Claude Code shipped managed MCP servers, unattended headless permissions, `claude plugin eval`, `/output-style`. → [`03` §1](./03-practical-skills-and-tools.md#1-smart-reports) `#claude #skills #claude-code`

9. **Research: Anthropic Economic Scenario Explorer (Sept 11)** — three US-economy 2030 scenarios. **Extreme case: 15% annual GDP growth, but 11.9% overall unemployment and 17.9% among knowledge workers, wages –10%.** Not a forecast — an interactive tool. **This is the most important AI-economics artifact of 2026** for anyone planning a career or startup. → [`04` §1](./04-research-progress.md#1-econ-scenario-explorer) `#anthropic #economics #labor`

10. **Career: two big re-prices this week.** (a) **The "compute-era" jobs** — 5GW → 10GW Anthropic build-out + $45B Nscale + $105B OpenAI/Ohio = data-center / networking / power-systems / MLOps roles now bidding against SWE for the same grads. (b) **The California AI-safety / verification lane** picked up a state-mandated tailwind — expect job postings for "independent verification org" (SB 813) and "kill-switch engineering" inside labs to spike in Q4. → [`05` §2](./05-career-and-startup.md#2-reprice) `#careers #compute #safety #ai-engineer`

---

## One thing to DO this Saturday

→ **Ship your model-router artifact (from [`03` §3 2026-09-10](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)) with DeepSeek V4.1-Flash added as the "cheap open-weight" route.** Log per-request cost. Publish. Sat-morning project, ~2 hours: because **the router is now a 4-provider artifact** (Anthropic, OpenAI, Google, DeepSeek) — the fourth column is what your peers will not have by Monday. Details in [`03` §2](./03-practical-skills-and-tools.md#2-deepseek-router).

## Watchlist deltas

- 🆕 **Anthropic November IPO / Nvidia $10B cornerstone:** upgraded from Sept-window to Nov-window with concrete banker + anchor-investor pipe. Track filing date, S-1 disclosure of Claude Code revenue mix.
- 🆕 **OpenAI IPO → 2027:** demoted. Order-of-market is now Anthropic-first, unambiguously.
- 🆕 **Claude runs 26% of Anthropic R&D — recursive-self-improvement, measured:** brand new metric. Track the number monthly; it will be in the S-1.
- 🆕 **California AI kill switch EO — Nov 16 report:** new gating event. If the working group recommends independent verification, SB 813 becomes the fastest-growing niche in AI compliance hiring.
- 🆕 **FINRA-style self-regulator standing up:** watch for a public announcement of the body's name + charter before year-end.
- 🆕 **DeepSeek V4.1-Flash MIT-licensed:** first open model to convincingly outrun its own paid flagship. Update your router.
- 🆕 **$517B Anthropic compute stack (Amazon + Google/Broadcom + Nscale + more):** watch the delivery timeline — this is the "can they actually build it" question that will price the IPO.
- ➡️ **Model fatigue thread (from 2026-09-10):** still live; DeepSeek Sept 10 + Tavus Phoenix 4.5 + Qwen-Drive Sept 15 all shipped this window.
- ⬇️ **"OpenAI first to IPO" thesis:** dead. Rewrite any application essay that quoted it.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-november-ipo) (Anthropic IPO) + [`01` §3](./01-big-lab-moves.md#3-claude-26-percent-rd) (26% R&D) |
| 20 min | [`04` §1](./04-research-progress.md#1-econ-scenario-explorer) — spend the time with the Economic Scenario Explorer; then [`03` §1–3](./03-practical-skills-and-tools.md) |
| Today | [`03` §2](./03-practical-skills-and-tools.md#2-deepseek-router) — add DeepSeek V4.1-Flash to your router |
| Tonight | [`05` §2](./05-career-and-startup.md#2-reprice) — re-anchor your job list around compute-era + verification-lane roles |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
