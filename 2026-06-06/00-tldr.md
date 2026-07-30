# TL;DR — 2026-06-06 (Saturday)

Sixty-second skim. **The IPO race went public, the security layer went operational, and Apple's about to pick its AI vendors — all in 96 hours.** **Anthropic confidentially filed an S-1 with the SEC on June 1** (Rule 135 announcement) on the back of a **$65B Series H at ~$965B post-money** and **~$47B ARR run-rate** (4.7× YoY) — the first frontier lab to *announce* an IPO path, ~10 days after OpenAI's still-silent May-22 filing. **Project Glasswing scaled to ~150 orgs across 15+ countries on June 2** with a launch-partner roster of AWS · Apple · Broadcom · Cisco · CrowdStrike · Google · JPMorgan · Linux Foundation · Microsoft · NVIDIA · Palo Alto — and **10,000+ critical-severity vulnerabilities already surfaced** since April. **WWDC keynote is Monday June 8, 10 AM PT** — iOS 27 Extensions expected to open Siri to Claude, ChatGPT, and Gemini. And the operational reminder: **Claude was fully down on June 5** (~hours, full restoration 18:27 UTC). For you: **apply to one Anthropic role this weekend** with the failover-router artifact attached, **pre-stage the WWDC live-monitoring grid tonight**, and **read Agent² RL-Bench tomorrow** — it's the measurement layer for the Karpathy-Anthropic pre-training-automation mandate.

---

1. **Anthropic confidentially files an S-1 (Jun 1) — first lab to *announce* an IPO path.** Rule 135 notice; $65B Series H at ~$965B post-money; ARR ~$47B (4.7× YoY); confidential draft = bookrunner-friendly first step (no timing, ticker, or share count yet); 15-day pre-roadshow window for the *public* S-1 — that's the S-1 to actually read for the segment-level revenue mix. **The Anthropic-stack focusing decision in ME.md just got its third independent confirmation in 2 weeks.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #s1 #public-markets`

2. **Project Glasswing operational at scale: ~150 orgs / 15+ countries / 10K+ critical CVEs surfaced since April.** Launch partners: AWS · Apple · Broadcom · Cisco · CrowdStrike · Google · JPMorganChase · Linux Foundation · Microsoft · NVIDIA · Palo Alto Networks. Cohesity added this round. **Anthropic restates: no public release of Mythos-class models** — but warns "6–12 mo until other labs ship Mythos-class without safeguards." → [`01` §2](./01-big-lab-moves.md#2-glasswing-self-coding) `#glasswing #mythos #cyber #anthropic`

3. **Claude now writes >80% of its own code** (up from <10% Feb 2025). Anthropic leadership: "trajectory toward fully autonomously designing and developing its own successor" — explicitly flags recursive-self-improvement loss-of-control risk. This is the **operational measurement** of the Karpathy/Anthropic pre-training-automation mandate from [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy). → [`01` §2](./01-big-lab-moves.md#2-glasswing-self-coding) `#recursive-improvement #anthropic #pretraining`

4. **WWDC keynote T-2 (Mon June 8, 10 AM PT).** iOS 27 Extensions expected to plug **Claude, ChatGPT, and Gemini** into Siri / Writing Tools / Image Playground; standalone Siri 2.0 chat app; multi-vendor model picker. **Apple goes from picking *one* AI partner (ChatGPT in iOS 26) to running a vendor marketplace.** → [`01` §3](./01-big-lab-moves.md#3-wwdc-extensions) `#apple #wwdc #ios-27 #siri #extensions`

5. **Hark $700M Series A at $6B post (May 21) — personal-AI-hardware gets its anchor.** Parkway lead + **NVIDIA + AMD + Intel + Qualcomm** all in the syndicate (four chipmakers, multiple direct competitors). Brett Adcock (Figure.AI, Archer) seeded with $100M of his own; ~$800M raised before shipping a product. First multimodal models this summer. **The silicon-vendor consensus is the loudest signal.** → [`02` §1](./02-new-emerging.md#1-hark) `#hark #hardware #funding #series-a #personal-ai #wearables`

6. **Operational reality check — Claude down June 5.** claude.ai + API + Code + Cowork all hit; infrastructure issue, not a breach; full restoration 18:27 UTC. **The 3-provider failover router has been on your ME.md punch list for 4 weeks; this is the second qualifying event** (post-Colossus concentration risk, 2026-05-09). Saturday weekend artifact. → [`03` §1](./03-practical-skills-and-tools.md#1-failover-router) `#outage #failover #multi-vendor #routing`

7. **Anthropic Fast mode now defaults to Opus 4.8 at $10/$50 per MTok, ~2.5× speed.** Re-do your model-selector tonight (15 min) — the "Opus is too expensive to default to" mental model is stale. Re-benchmark one representative chain on Sonnet 4.6 / Opus 4.7 / Fast Opus 4.8 and add the table to the failover-router README. → [`03` §2](./03-practical-skills-and-tools.md#2-fast-mode-opus) `#opus-4-8 #pricing #fast-mode #routing`

8. **Research — the measurement layer for "AI improves AI" just landed.** **Agent² RL-Bench** (MSR, arXiv 2604.10547) — 6 tasks × 3 levels, scoring *whether LLM agents can autonomously engineer agentic RL post-training* — the literal benchmark for the Karpathy mandate. Pairs with **single-agent beats multi-agent at matched compute** (arXiv 2604.02460) and the **Externalization 4-axis survey** (arXiv 2604.08224). One survey + one benchmark + one position paper = the interview vocabulary for the month. → [`04`](./04-research-progress.md) `#research #arxiv #post-training #benchmarks #single-vs-multi-agent`

---

## One thing to DO this Saturday

→ **Ship the 3-provider failover router + per-request cost log** ([`03` §1](./03-practical-skills-and-tools.md#1-failover-router)). One repo, one README, one demo gif. **The README answers three interview questions in three paragraphs** — provider-outage handling (motivate w/ Jun 5), cost control (per-request cost row), routing decision (the rule + observed mix). Then **apply to one Anthropic Solutions/FDE/Integration role this weekend with the artifact attached** ([`05` §1](./05-career-and-startup.md#1-anthropic-hiring)) — before the post-S-1 application flood arrives in ~2 weeks. **Tonight (10 min):** pre-stage the WWDC monitoring folder + hypothesis list ([`03` §3](./03-practical-skills-and-tools.md#3-wwdc-discipline)). **Sunday morning:** read Agent² RL-Bench ([`04` §1](./04-research-progress.md#1-agent2-rl-bench)).

## Watchlist deltas

- 🆕 **Anthropic S-1 (Rule 135 announcement):** new thread — watch for the *public* S-1 (15-day pre-roadshow window), segment-level revenue mix (API vs ChatGPT-analog vs Claude Code vs Solutions vs Mythos/Glasswing), Microsoft/AWS terms in the prospectus, and ticker/exchange. Compare against OpenAI's path which remains *unannounced* despite the May-22 confidential filing.
- ⬆️ **Project Glasswing:** status 🟡 → 🟢 OPERATIONAL — 150 orgs / 10K+ CVEs / 12-platform launch roster. Watch for the **next $100M+ AI-SOC round** (Exaforce category, [2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce)) and whether Anthropic stands up a dedicated **Mission Engineer — Critical Infrastructure** hiring posture.
- 🆕 **Claude self-coding >80%:** new thread — track whether this number gets independent verification, whether Anthropic publishes the measurement methodology, and whether the [Agent² RL-Bench](./04-research-progress.md#1-agent2-rl-bench) scoring framework gets adopted as the standard.
- 🆕 **WWDC June 8 / iOS 27 Extensions:** new thread (carrying [2026-05-07/01 iOS 27 multi-AI Extensions](../2026-05-07/01-big-lab-moves.md) forward to its public surface). Pre-keynote hypothesis grid in [`03` §3](./03-practical-skills-and-tools.md#3-wwdc-discipline).
- 🆕 **Hark $700M Series A at $6B (May 21):** new thread — first multimodal models summer 2026; track the silicon-vendor syndicate (NVIDIA+AMD+Intel+Qualcomm) for similar plays at other personal-AI-hardware startups in the next 60 days.
- 🆕 **Claude June-5 outage:** isolated thread — track whether status.anthropic.com publishes a post-mortem (and the **MTTR delta** if it does); use this as the operational anchor for the multi-vendor router README.
- 🆕 **Fast mode default = Opus 4.8 @ $10/$50/MTok, ~2.5× speed:** new pricing-tier row in models thread — watch for OpenAI / Google parity announcements; the "Opus is the expensive default" assumption flips.
- ➡️ **OpenAI confidential S-1 (May 22):** still no Rule 135 / public announcement as of Jun 5 per multiple trackers — watch the announcement-or-silence read: it's a *style differential* signal vs Anthropic. (Carried from [2026-05-22/01 §2](../2026-05-22/01-big-lab-moves.md#2-openai-s1).)
- ➡️ **Karpathy → Anthropic pre-training automation team:** still active — now empirically anchored by the >80%-self-coding stat ([`01` §2](./01-big-lab-moves.md#2-glasswing-self-coding)) and the [Agent² RL-Bench](./04-research-progress.md#1-agent2-rl-bench) measurement framework.
- ➡️ **Anthropic Agent SDK metering (June 15):** T-9 days. Set up the failover router *before* metering hits, so the cost-routing log already has baseline data.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the Anthropic S-1 + Glasswing in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`04` §1](./04-research-progress.md#1-agent2-rl-bench) (Agent² RL-Bench) + [`02` §1](./02-new-emerging.md#1-hark) (Hark / silicon-vendor signal) — the two deepest signals |
| Tonight (15 min) | [`03` §2](./03-practical-skills-and-tools.md#2-fast-mode-opus) — re-benchmark one chain on Fast Opus 4.8 |
| Tonight (10 min) | [`03` §3](./03-practical-skills-and-tools.md#3-wwdc-discipline) — pre-stage WWDC notes/claims/post folder |
| Saturday (4–6 hr) | [`03` §1](./03-practical-skills-and-tools.md#1-failover-router) — ship the 3-provider failover router |
| Saturday/Sunday | [`05` §1](./05-career-and-startup.md#1-anthropic-hiring) — apply to one Anthropic Solutions/FDE role with the artifact attached |
| Sunday | [`04` §1](./04-research-progress.md#1-agent2-rl-bench) — read Agent² RL-Bench end-to-end |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
