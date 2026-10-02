# TL;DR — 2026-05-26 (Tuesday)

Sixty-second skim. **Back from the long weekend into the week the valuation crown actually changes hands — if the ink dries.** **Anthropic's ~$30B round at a $900B pre-money is *closing this week* but is still NOT officially signed** ([terms agreed 2026-05-23](../2026-05-23/01-big-lab-moves.md#1-spacex-s1); status [2026-05-25/01 §2](../2026-05-25/01-big-lab-moves.md#2-anthropic-status)) — the moment it closes, Anthropic passes OpenAI's ~$852B to become **the most valuable private AI company on earth.** That's the watch-item of the week. The forward-looking story: **Apple registered `genai.apple.com` ahead of WWDC (Mon June 8)**, where a **multi-AI Siri "Extensions" framework** and a **Gemini-powered Siri** are expected — putting the model wars on ~1B+ iPhones. And capital kept barbelling: **Brett Adcock's Hark raised >$700M at $6B** with every major chipmaker on the cap table. For you: **execute this week's apply plan before the close-news thickens the queue, and finish the June-15 cost work.**

---

1. **Anthropic's ~$30B / $900B-pre round is closing THIS WEEK — still not signed.** Co-leads Dragoneer / Greenoaks / Sequoia / Altimeter (≥$2B each), Founders Fund + General Catalyst in. Close it and Anthropic **tops OpenAI's ~$852B** (a 2.4× re-rate from Feb's $380B). **The single highest-value confirmation to catch this week.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-close) `#anthropic #funding #valuation`

2. **Apple registers `genai.apple.com` ahead of WWDC (Mon June 8); multi-AI Siri "Extensions" + a Gemini-powered Siri expected.** iOS/iPadOS/macOS 27 are expected to let users pick **ChatGPT, Gemini, or Claude** inside Siri, the rebuilt Siri reportedly on a **custom Gemini model** via Private Cloud Compute. **WWDC keynote is June 8** (correcting earlier "June 9"). → [`01` §2](./01-big-lab-moves.md#2-apple-wwdc) `#apple #google #gemini #siri #wwdc`

3. **Emerging: AI *hardware* keeps drawing mega-rounds — Brett Adcock's Hark raised >$700M at $6B**, with **NVIDIA, AMD Ventures, Intel Capital, Qualcomm Ventures, Brookfield, Salesforce Ventures** all in. When every chipmaker co-invests, it's a bet on a new platform surface. → [`02` §1](./02-new-emerging.md#1-hark) `#funding #hardware #robotics`

4. **The IPO cohort clock ticks: SpaceX's roadshow (~June 4) → SPCX listing (~June 12) is now the nearest catalyst.** SpaceX prices first (~$1.75T, [2026-05-23/01 §1](../2026-05-23/01-big-lab-moves.md#1-spacex-s1)) — and its first-day arc sets the multiple OpenAI (Sept) and Anthropic (Oct) get judged against. → [`02` §2](./02-new-emerging.md#2-ipo-clock) `#ipo #public-markets #spacex`

5. **Practical (today's 20 min): the Skills vs MCP vs Subagents decision table.** A **Skill ≈ 100 tokens** until activated; a typical **5-server MCP setup ≈ 55K tokens, always on.** Skills for "how-to," MCP for external systems, subagents for fresh-context delegation. The architecture layer under [05-23's SKILL.md](../2026-05-23/03-practical-skills-and-tools.md#1-claude-skills) and [05-25's metering re-model](../2026-05-25/03-practical-skills-and-tools.md#1-metering) (T-20). → [`03` §1](./03-practical-skills-and-tools.md#1-skills-vs-mcp) `#claude-code #skills #mcp #subagents #cost`

6. **Research: agents-over-literature grounding — PaperArena + CLAIM-BENCH.** Can an agent *use tools to reason over real papers* and trace **claim → evidence**? It's the science-domain instance of the reality-interface theme running through [05-25's TerminalWorld/AI-Trader](../2026-05-25/04-research-progress.md#1-benchmarks) and [05-24's memory-as-a-system](../2026-05-24/04-research-progress.md#1-memory-synthesis) arcs. → [`04` §1](./04-research-progress.md#1-paperarena) `#research #agents #benchmarks #grounding`

7. **Career data behind the bifurcation: ML-engineer openings ~+59% vs the 2020 baseline while overall tech sits ~−36%.** AI skills now appear in **~42% of software JDs** (8% in 2022, ~6×); multi-AI-skill workers command **~43% more**; AI/MLE midpoint **~$170,750.** Cuts concentrate in **mid-career generalists.** → [`05` §1](./05-career-and-startup.md#1-bifurcation-data) `#jobs #careers #data #mle`

8. **Career (startup): AI seed valuations carry a ~42% premium** (median pre-money ~$17.9M); net-new dollars concentrate in **agentic retrieval + agent-code security.** Capital for non-frontier founders is, in absolute terms, the best it's been — the binding constraint is a *defensible problem*, not money. → [`05` §2](./05-career-and-startup.md#2-seed-premium) `#vc #seed #startups`

---

## One thing to DO this Tuesday

→ **Execute [Sunday's 4-application plan](../2026-05-25/05-career-and-startup.md#1-week-ahead) — starting with the Anthropic app — TODAY, before the round-close confirmation thickens the queue.** Lead your resume with the committed lane (*"Forward-Deployed / AI Integration Engineer — production agents, cost-aware, verified against real tools"*), reference the Karpathy pre-training direction ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)), and attach the cost re-model artifact from [2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-metering). ([`05` §1](./05-career-and-startup.md#1-bifurcation-data))

## Watchlist deltas

- ➡️🔥 **Anthropic ~$30B / $900B round:** **closing window is NOW** — still not signed as of today. Watch anthropic.com + Bloomberg daily; this is the week's top confirmation.
- 🆕 **Apple WWDC (June 8) / `genai.apple.com` / Gemini-powered Siri:** new thread — watch for the multi-AI "Extensions" SDK and whether Claude is a launch option; ~1B+ device distribution at stake. (Corrects WWDC date to June 8.)
- 🆕 **Hark (Brett Adcock) >$700M / $6B:** new thread — watch what it builds; the all-chipmaker cap table signals a hardware-platform bet.
- ➡️ **SpaceX SPCX (~June 12, roadshow ~June 4):** nearest IPO catalyst; prices the cohort.
- ➡️ **Anthropic Agent SDK metering (June 15):** **T-20** — finish the re-model ([2026-05-25/03 §1](../2026-05-25/03-practical-skills-and-tools.md#1-metering)).
- ➡️ **Gemini 3.5 Pro (June):** the reasoning-tier counterpart to Flash; watch the launch + pricing.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the round-close watch + Apple/Gemini-Siri in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-skills-vs-mcp) (Skills vs MCP cost architecture) — do it, don't just read it |
| Today | [`05` §1](./05-career-and-startup.md#1-bifurcation-data) — file the Anthropic app + this week's 3 others |
| This week | [`05` §2](./05-career-and-startup.md#2-seed-premium) — if startup-leaning, the seed-premium read |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
