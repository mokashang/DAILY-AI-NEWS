# TL;DR — 2026-06-16 (Tuesday)

Sixty-second skim. **Yesterday was the deadline; today is the data.** **Anthropic's Agent SDK metering went live June 15** — the credit-split this archive has tracked since [2026-05-16](../2026-05-16/01-big-lab-moves.md#1-meter) is now real for every Pro/Max/Max-20x subscriber, **and the same morning Anthropic retired the original Claude 4 (Sonnet/Opus `…-20250514`) from the API** — a double hit a lot of programmatic users absorbed in 24 hours. Meanwhile the macro reframed under the radar over the last three weeks: **Anthropic filed a confidential S-1 on June 1 at a ~$965B post and is reportedly targeting a $1.75–1.8T IPO**, **OpenAI followed on June 8** (Sept-2026 listing window), **Apple opened iOS 27 to third-party AI Extensions at WWDC** (1.5B-device default-Siri slot up for grabs, fall 2026), **Anthropic shipped Fable 5 + Mythos 5 at Code w/ Claude Tokyo (June 9–10)** — Mythos *publicly available, guardrailed* for the first time — and **two yesterday rounds (NewCore $66M agent-identity, Hydra Host $100M GPU marketplace w/ NVIDIA on the cap table)** prove the agentic-stack picks-and-shovels lanes are now funded. For you: **the metered-Claude regime is now the baseline you build on**, and **every interview question about your Anthropic-stack focusing decision now has three weeks of *public* validating events behind it.**

---

1. **Anthropic Agent SDK metering is LIVE — Day 1.** As of yesterday (June 15) Agent SDK + `claude -p` + Claude Code GitHub Actions + third-party agents are billed off a **separate monthly credit pool** ($20 Pro / $100 Max-5x / $200 Max-20x) at **full API list rates, no rollover.** Interactive Claude Code TUI and claude.ai chat stay on the subscription. **Same morning, the original Claude 4 Sonnet/Opus (`-20250514`) retired from the API.** → [`01` §1](./01-big-lab-moves.md#1-metering-day-1) `#anthropic #pricing #agent-sdk #claude-code`

2. **Anthropic filed a confidential S-1 on June 1; OpenAI on June 8.** Anthropic at ~**$965B post** (Series H closed pre-filing) reportedly targeting **$1.75–1.8T** at listing with up to **$75B raise**; OpenAI ~**$852B → $1T+** in Sept window (Goldman/Morgan Stanley/JPM). **Both frontier labs are now S-1-confidential at the same time** — never happened before. → [`01` §2](./01-big-lab-moves.md#2-both-s1) `#openai #anthropic #ipo #public-markets`

3. **Anthropic launched Fable 5 + Mythos 5 at Code w/ Claude Tokyo (June 9–10).** Fable 5 = **public, guardrailed sibling of Mythos** (the model that had been EU-restricted since May); +10% on some benchmarks vs Opus 4.8; **GA on Claude API, Platform, Code, Enterprise consumption plans, AWS, GCP, Microsoft Foundry day-one**. **Mythos 5** ships to vetted defenders. The 4.x → 5.x cycle is the fastest Anthropic has ever run. → [`01` §3](./01-big-lab-moves.md#3-fable-5) · [`02` §1](./02-new-emerging.md#1-fable-5-distribution) `#anthropic #fable-5 #mythos-5 #models`

4. **Apple WWDC opened iOS 27 to third-party AI "Extensions"** (June 8, Tim Cook's final keynote as CEO): Claude / ChatGPT / Gemini / Grok can be set as **default Siri / Writing Tools / Image Playground provider** via a dedicated App Store marketplace. **Beta now; fall 2026 ship.** **1.5B-device default-AI slot is up for grabs** — the single biggest distribution shift of the cycle. → [`01` §4](./01-big-lab-moves.md#4-apple-extensions) `#apple #ios27 #extensions #distribution`

5. **Yesterday's funding double — both pure-play picks-and-shovels for the agent layer.** **NewCore $66M** (Cyberstarts/Index/Evolution; $300M post; Tel Aviv; ex-IDF intel founders) — **identity for human + machine + AI-agent** workforces; phishing-resistant MFA + split-key architecture at platform level. **Hydra Host $100M** (Kindred lead; **NVIDIA on cap table**, ARK Invest, Founders Fund, Comcast Ventures, PEAK6, Magnetar) — **GPU marketplace** across 50+ data centers w/ Brokkr AI Factory OS. → [`02` §2](./02-new-emerging.md#2-identity-and-compute) `#funding #identity #gpu #agentic`

6. **Practical: the meter-aware Claude Code starter kit you should deploy tonight.** Prompt caching (`cache_read_input_tokens` ≥ confirmed positive), Opus-orchestrator/Sonnet-worker split (~40% cheaper, [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)), per-step cost log, and the **`/billing` audit run** ([2026-05-16](../2026-05-16/03-practical-skills-and-tools.md)) — together they convert the metering shock into a portfolio artifact. → [`03` §1](./03-practical-skills-and-tools.md#1-meter-aware-starter) `#claude-code #cost #subagents #cache`

7. **Research: agentic-eval moves from benchmarks to real production traces.** **MCP-Atlas** and **Toolathlon** ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) are now joined by a wave of **"agentic trace evaluation"** preprints on arXiv testing whether models can be graded by their *transcripts* — the same primitive that makes the new metering bill auditable. → [`04` §1](./04-research-progress.md#1-trace-eval) `#arxiv #eval #agents #observability`

8. **Career signal of the cycle: FDE pay-band CONFIRMED at $665K–$750K TC (L4–L5) at Anthropic/OpenAI** ([MarkTechPost / Sundeep Teki recruit-guide]), 55–70% equity. **The "AI Integration Engineer" lane you committed to in ME.md is now the highest-paid IC ladder in tech** — by a wide margin and growing. → [`05` §1](./05-career-and-startup.md#1-fde-tc) `#fde #careers #integration-engineer`

---

## One thing to DO this Tuesday

→ **Run your Claude Code billing audit *today, not Friday*.** Pull `/billing` + the Agent SDK separate-pool dashboard, log a 7-day per-task token-cost table, and write a 1-page LinkedIn post titled *"What changed for me on June 15 — and the 3 settings I flipped."* It doubles as: (a) the Personal Claude Billing Audit artifact you've been carrying since [ME.md](../ME.md), (b) a portfolio piece dated to a known industry event, (c) the cleanest "I-shipped-the-day-after" signal you can put in front of an Anthropic Solutions recruiter while the 30-day search window is open. **30 min, ships today.**

## Watchlist deltas

- 🟢 **Anthropic Agent SDK metering (June 15):** **CONFIRMED LIVE.** Closed thread. Replaced by **"Day-1 metering economics"** new thread — track per-token effective cost vs old plan, how many programmatic users were silently blocked, vendor SDK responses (Zed, Cursor, Cline, Aider), and whether Anthropic publishes overage policy.
- 🟢 **Original Claude 4 retirement (`…-20250514`):** **CONFIRMED June 15.** Closed thread. Anyone still pinning those model IDs in production silently broke yesterday.
- 🆕 **Anthropic S-1 confidential filing (June 1) + $1.75–1.8T IPO target:** new thread. Track the public S-1 (revenue by product, Colossus economics, ad-free policy disclosure), roadshow timing vs OpenAI.
- 🆕 **OpenAI S-1 confidential filing (June 8):** new thread. Goldman/Morgan Stanley/JPM trio; Sept-2026 listing window; watch the **ad-revenue and Microsoft-rev-share lines** the public S-1 will eventually disclose.
- 🆕 **Fable 5 + Mythos 5 (June 9):** new thread. First *public* Mythos-class model from Anthropic; +10% on some benchmarks vs Opus 4.8; track distribution velocity on the three clouds + Foundry.
- 🆕 **Apple iOS 27 Extensions (WWDC June 8):** new thread. Beta now, fall ship; watch **which third-party AI defaults Apple highlights in the App Store marketplace** at the Sept iPhone event.
- 🆕 **NewCore $66M / agent-identity category:** new thread. Watch for follow-on rounds in agent-identity, agent-credentials, agent-permission tooling (a thin lane just got priced).
- 🆕 **Hydra Host $100M / decentralized GPU marketplace:** new thread. Watch NVIDIA's next strategic-invest in compute infra; whether the "long-tail data center" thesis attracts $500M+ follow-ons.
- ➡️ **OpenAI S-1 confidential filing:** updated from 2026-05-22 to **confirmed June 8** (not "as early as today May 22"). Anthropic moved first.
- ➡️ **The IPO wave as asset-class shift:** intensifying — both labs S-1-confidential simultaneously rewrites the employer-risk calculation.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the metering Day-1 read + the both-S-1s context in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`01` §3](./01-big-lab-moves.md#3-fable-5) (Fable 5 distribution) + [`05` §1](./05-career-and-startup.md#1-fde-tc) (FDE comp-band confirmed) — the two highest-personal-signal items |
| Today | The 30-min Claude billing audit + LinkedIn post (see "One thing to DO" above) |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-meter-aware-starter) — the meter-aware Claude Code starter kit |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
