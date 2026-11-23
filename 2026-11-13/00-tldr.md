# TL;DR — 2026-11-13 (Friday)

Sixty-second skim. **The thirty days since the Oct 14 edition compressed into one week.** On **Nov 9 Anthropic shipped Claude Fable 5.2 + Mythos 5.2** at **$8 / $40 per 1M (uncached in/out, down from $10 / $50 — a ~20% API cut)**, with **65 on the Artificial Analysis Intelligence Index** (ahead of Gemini 4 Carbon), **76.3% CyScenarioBench (vs 61.7% on 5.1)**, **89.6% CVE Rediscovery (vs 78.3%)**, and **~30% faster output** than 5.1 — frontier intelligence just got cheaper *and* the top-of-stack shifted back to Anthropic for the first time since September. On **Nov 10 Anthropic filed S-1/A Amendment No. 2 and launched the IPO roadshow** at a **$70–$78 price range** (825M Class A shares; Nasdaq symbol **ANT**); **pricing is expected Nov 18, first-trade Nov 19**, **implied diluted valuation ~$1.02T at $78** (bankers reportedly pushing toward $1.5T on the roadshow book) — **by next Thursday, Anthropic is the first frontier lab public**, and the equity pool you've been investing your résumé into becomes a liquid, S-1-disclosed hiring map. Same day, **Anthropic launched Claude Meetings / Whiteboards / Sheets**, and **today Nov 13 Claude Meetings went to Google Meet beta** — the workplace-software wedge opens 72 hours before pricing. Also today: **a Claude.ai + Claude Code auth outage** gave the IPO week its first stability-narrative moment, at the worst possible hour. Underneath: **Google shipped Gemini 4 Carbon (Nov 10)**, **OpenAI shipped Images 2.6 (Nov 4)** with GPT-Image-2.6 **Flare** (speed) / **Sunburst** (precision), **xAI defaulted Grok API text watermarking (Nov 7)** and shipped **Grok Bot 1.0** (team coding, Nov 11), and **Rox $100M Series B at $1.3B** and **Laza Medical ~$160M Series B** anchor a quieter funding week. **Re-price of the week: a tradable Anthropic reshapes compensation design in the whole ecosystem — RSU grants replace options for new Anthropic hires post-lockup, partner-firm equity packages reset, and your 2027 offer-negotiation playbook changes this month, not next quarter.**

---

1. **Anthropic IPO roadshow launched (Nov 10) — ANT on Nasdaq, $70–$78 range, 825M Class A shares, pricing ~Nov 18 / first-trade ~Nov 19.** S-1/A Amendment No. 2 on file with the SEC. 801.35M shares offered by Anthropic + 23.65M by existing stockholders. Reuters calculates **~$1.02T implied diluted** at $78; FT reports bankers testing demand up to **$1.5T+** on the roadshow book. **This is the first frontier lab to become a public company** — the S-1 is the best segment-by-segment revenue/hiring map you will ever read for the lab you've been investing your portfolio into. → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) `#anthropic #ipo #ANT #equity`

2. **Claude Fable 5.2 + Mythos 5.2 shipped (Nov 9) — $8 / $40 per 1M (uncached in/out), ~20% cut, 65 on Artificial Analysis Intelligence Index, ~30% faster, 76.3% CyScenarioBench, 89.6% CVE Rediscovery, 75.3% Terminal-Bench-Science.** Fast mode **$16 / $80**; batch mode **$4 / $20**. Fable 5.2 is broadly available; **Mythos 5.2 is restricted to Anthropic-verified cybersecurity and life-sciences orgs**. The frontier re-topped the intelligence leaderboard the day before the roadshow — not an accident. → [`01` §2](./01-big-lab-moves.md#2-fable-mythos-52) `#claude #fable #mythos #pricing #benchmarks`

3. **Claude Meetings → Google Meet beta TODAY (Nov 13); Claude Meetings / Whiteboards / Sheets all launched Nov 10 for Team + Enterprise.** Claude joins Google Meet as a **visible participant** (identifies itself in chat, auto-exits if an unauthorized external joins), drafts timelines + plans live, answers questions in meeting chat, pulls from connected work apps, and dumps notes + action items into claude.ai after. Teams support "coming." **The workplace-software wedge went live 72 hours before pricing day.** → [`01` §3](./01-big-lab-moves.md#3-claude-meetings) `#anthropic #workplace #meetings #productivity`

4. **Claude.ai + Claude Code auth outage TODAY (Nov 13).** Login failures across chat and coding tools; Anthropic investigating. Reliability narrative during IPO week is now priced in — watch for a status-page post-mortem in the final prospectus or an 8-K-equivalent amendment. → [`01` §4](./01-big-lab-moves.md#4-outage) `#anthropic #outage #sre`

5. **Google Gemini 4 Carbon shipped (Nov 10) — limited access; Anthropic still tops the intelligence index.** Google's frontier model landed the same day as the Anthropic roadshow — the only IPO-week counter-release Google could stage. Gemini API also announces automatic rerouting of `gemini-2.5-pro` / `gemini-2.5-flash` to newer models from Dec 1. → [`01` §5](./01-big-lab-moves.md#5-gemini-4-carbon) `#google #gemini #release`

6. **OpenAI Images 2.6 shipped (Nov 4) across ChatGPT + Codex + API — GPT-Image-2.6 Flare (fast) vs Sunburst (precision).** Dev teams pick per-call: Flare for iteration, Sunburst for final. The "effort-level" primitive is now a cross-vendor pattern (Anthropic Haiku 5.5 effort levels, Grok 4.7 modes, OpenAI Images 2.6 modes). → [`02` §1](./02-new-emerging.md#1-openai-images-26) `#openai #images #multimodal`

7. **xAI shipped Grok Bot 1.0 (team-oriented coding agent, Nov 11) and put Grok 4.7 on AWS Kiro (Nov 10); Grok API text watermarking defaulted-on Nov 7 across seven models.** xAI is now **the only frontier lab with content-provenance on by default** — a Trust & Safety position OpenAI and Anthropic have left open. → [`02` §2](./02-new-emerging.md#2-grok-bot) `#xai #grok #watermark #coding-agents`

8. **Funding — Rox $100M Series B @ $1.3B (Nov 11, General Catalyst + March Capital, SF, AI research agents) + Laza Medical ~$160M Series B (GE HealthCare lead, AI healthcare).** Plus a reported but unconfirmed **$12B / $41B Series B for Prometheus** (physical AI; Bezos + Vik Bajaj) — single-source, treat as rumor until SEC Form D appears. → [`02` §3](./02-new-emerging.md#3-funding) `#funding #series-b #agents #healthcare`

9. **Research: four Nov arXiv landmarks — 2611.11645 (math research infrastructure for people-and-agents), 2611.06764 (access control survey for AI agents), 2611.03092 "Avatar Intelligence" (persistent personal agents), 2611.12941 (agentic governance; NeurIPS 2026), 2611.12966 "BuySideFlow" (point-in-time investment-research benchmark).** Theme of the month: **agents as a civic/institutional object**, not a model property. The eval frontier moved from "can it finish" (Oct) to "who owns what it did" (Nov). → [`04` §1](./04-research-progress.md#1-november-arxiv) `#arxiv #agents #governance #access-control`

10. **Practical: the IPO-week Claude Code checklist (Fable 5.2 default + 30-day billing audit + CLAUDE.md under 200 lines + dual-model cost-router).** Also: how to run a "visible-AI-in-meetings" demo this weekend with the new Google Meet integration — the single highest-leverage Monday-morning show-and-tell at any employer with a Google Workspace footprint. → [`03` §1](./03-practical-skills-and-tools.md#1-fable-52-checklist) · [`03` §2](./03-practical-skills-and-tools.md#2-meetings-demo) `#claude-code #productivity #billing`

11. **Career — Capital One Senior AI Engineer 4 (foundation models + agentic systems, Nov 6), Amazon AWS Neuron SDE I (Nov 10), Microsoft ML Research Engineer (Nov 11), Databricks + OpenAI + Stripe + Flexport FDE postings fresh this week.** **Enterprise foundation-model teams** are the under-priced lane right now — Capital One, JPMC, and Morgan Stanley are hiring MLE/AI-Eng faster than the frontier labs this month, pre-IPO. → [`05` §2](./05-career-and-startup.md#2-apply-plan) `#jobs #enterprise #foundation-models #fde`

12. **Re-price of the week: public-market Anthropic changes your comp math.** Pre-IPO Anthropic options (previously illiquid at $900B+ paper mark) become **post-IPO RSUs at a known price**, and the 180-day lockup ends ~mid-May 2027. **Any Anthropic (or Anthropic-partner) offer you consider this quarter needs an explicit post-lockup clause.** Partner-firm FDE packages reset too — PwC, Deloitte, Accenture equity pools get re-benchmarked against ANT, not against the private secondary. → [`05` §1](./05-career-and-startup.md#1-reprice) `#careers #comp #equity`

---

## One thing to DO this Friday

→ **Read Anthropic's S-1 Risk Factors + Management's Discussion (MD&A) sections tonight — 90 minutes.** Not the whole 400-page document; just those two sections. Why: the Risk Factors enumerate every lane Anthropic worries about publicly — DoD exposure, concentration in Claude Code ARR, Palantir unwind, model-evaluation airgap failure, EU/UK regulatory surface — **and each of those is an interview-grade talking point you can use next week when applying to Anthropic Solutions, OpenAI FDE, or any partner-firm GenAI role.** MD&A gives you the revenue segmentation (consumer Pro/Max vs API vs Enterprise) that tells you exactly which team to apply to. Second thing (20 min): set a calendar alert for **Nov 18 after-hours** (pricing) and **Nov 19 9:30 AM ET** (first trade) — if ANT opens >$95, re-read the partner-firm apply plan in [`05` §2](./05-career-and-startup.md#2-apply-plan); if <$78, re-read §2's "cooling-market pivot" paragraph. Details in [`05` §3](./05-career-and-startup.md#3-ipo-week-moves).

## Watchlist deltas

- 🆕 **Anthropic IPO (ANT) — pricing Nov 18 / first-trade Nov 19:** new thread. Track: (a) final price vs $70–$78 range, (b) first-day close, (c) lockup expiry (~mid-May 2027), (d) first 10-Q (early 2027) and what it reveals about the Pentagon-break revenue hole and Frontier Academy cost line.
- 🆕 **Fable 5.2 as new intelligence-index leader at $8/$40:** new thread. Watch for OpenAI / Google reprice responses in Dec, and whether Gemini 4 Carbon public benchmarks dethrone it before Christmas.
- 🆕 **Claude Meetings / Whiteboards / Sheets:** new thread. Workspace software suite play — track adoption inside the Frontier Academy partner firms first. Teams support is the tell for the Microsoft relationship.
- 🆕 **Nov 13 Anthropic outage:** new thread. Watch for the post-mortem and whether it changes anything in the final prospectus.
- 🆕 **"Avatar Intelligence" as a research frame (arXiv 2611.03092):** new thread. Persistent personal agents = the long-horizon memory thesis crystalizing into a paradigm.
- ➡️ **Claude Frontier Academy (from 2026-10-14):** still nomination-only. Track the first self-apply opening, probably Q1 2027 if the first cohort delivers.
- ➡️ **Pentagon-Anthropic break (from 2026-10-14):** no new ruling. The IPO prospectus should disclose any DoD revenue concentration — read for it.
- ➡️ **Haiku 5.5 / effort-level routing (from 2026-10-14):** router playbook still the weekend artifact of record. Fable 5.2 + Haiku 5.5 is the new default pair.
- ➡️ **Model fatigue (from 2026-09-10):** Fable 5.2 + Mythos 5.2 + Gemini 4 Carbon + Images 2.6 + Grok Bot 1.0 all in a 7-day window. Buyer disorientation at year-high.
- ⬇️ **"Frontier lab is private" framing:** fully deprecated as of Nov 10. Equity, comp design, and S-1 readability are now live career tools.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo) (IPO — the reshape story) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–3](./05-career-and-startup.md) — IPO + Fable 5.2 + Meetings + the comp-math reset + Friday apply plan |
| Today | Read S-1 Risk Factors + MD&A (90 min) — see "One thing to DO" above |
| This weekend | [`03` §2](./03-practical-skills-and-tools.md#2-meetings-demo) — build the Google-Meet-plus-Claude demo and record a 90-second screencast for LinkedIn Monday morning |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
