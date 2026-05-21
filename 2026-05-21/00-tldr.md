# TL;DR — 2026-05-21 (Thursday)

Sixty-second skim. **The state steps in; the machine does new math; the compute bill comes due.** In ~48 hours: **Trump signs an AI/cybersecurity executive order today** asking labs to hand models to the government 14–90 days *before* release (the first US federal pre-release framework); Anthropic's Colossus tenancy is now **contractual in SpaceX's S-1 — $1.25B/month through 2029 (~$15B/yr)**, landing as Anthropic projects its **first profitable quarter ~2 years early**; and an OpenAI **general-purpose model autonomously disproved an 80-year-old Erdős conjecture**, verified by Princeton's Noga Alon. The frontier framing moved from yesterday's "cheapest-good-enough + best rails" to **"who the regulator can reach, who can pay the power bill, and whose model can do net-new science."** And separately: **today, 8 AM PT, the Meta-alumni outreach window opens** — execute the plan.

---

1. **Trump's AI executive order — pre-release model review goes federal (signing today).** Voluntary framework: developers **provide covered models to the government 90 days pre-release** (+ pre-access for critical infra like banks); labs are lobbying for **14 days**. Driven by cyber-risk (Mythos, GPT-5.5-Cyber named). OpenAI + Anthropic at the table. → [`01` §1](./01-big-lab-moves.md#1-trump-eo) `#policy #regulation #release-review`

2. **Anthropic's compute bill, in writing: $1.25B/month to xAI through 2029 (~$15B/yr, $40B+ total) — disclosed via SpaceX's S-1.** Entire **Colossus 1**: 300 MW, 220K+ GPUs (H100/H200/GB200). The May-9 *rumor* is now a *filed liability*. → [`01` §2](./01-big-lab-moves.md#2-anthropic-colossus) `#anthropic #xai #compute #colossus`

3. **Anthropic projects its first profitable quarter — ~$559M operating profit, ~2 years early; Q2 revenue ~$10.9B.** Demand (~80× YTD) so far exceeds supply that they'll pay $15B/yr for capacity. Read: **aggressive revenue-role hiring**, and a de-risked bet on the Anthropic stack. → [`01` §2](./01-big-lab-moves.md#2-anthropic-colossus) · [`05` §4](./05-career-and-startup.md#4-anthropic-hiring) `#profitability #hiring`

4. **An OpenAI general-purpose model disproved a central Erdős conjecture (planar unit-distance problem, 1946).** Found an infinite family of better constructions by connecting geometry to **algebraic number theory**; verified by **Noga Alon + Thomas Bloom**. First prominent open math problem advanced autonomously by a *general* model. → [`04` §1](./04-research-progress.md#1-erdos) `#math #research #discovery`

5. **OpenAI turns ChatGPT into an ad platform.** Self-serve **ChatGPT Ads Manager**, CPC bidding, **no minimum spend** — targeting $2.5B ad revenue this year → $100B by 2030. Direct contrast with **Anthropic's ad-free pledge** — two divergent platform business models to build on. → [`01` §3b](./01-big-lab-moves.md#3-openai) · [`02` §1](./02-new-emerging.md#1-ads-surface) `#openai #ads #business-models`

6. **The measurement apparatus races to keep up.** A live-benchmark wave answers "did the model generalize or memorize?": **LemmaBench** (live research-grade math), **RepoReason** (repo-level reasoning), plus single→multi-agent eval, test-time-scaling, and PostTrainBench. Capability + its measurement co-evolve. → [`04` §2](./04-research-progress.md#2-benchmarks) `#benchmarks #evaluation #arxiv`

7. **The skill re-price.** Cheap inference + real discovery → **verification/eval design** and **cost-aware routing** got scarce & valuable; raw "I can prompt a model" got commoditized. Alon/Bloom *verifying* the proof is the job now. → [`05` §2](./05-career-and-startup.md#2-reprice) `#skills #careers #eval`

8. **A new career lane the EO just created:** **pre-deployment evaluation / model-release governance / AI assurance** — inside labs, inside banks (named in the order), and at eval/GRC startups. Thin queue; your eval + sanitiser artifacts are directly on-thesis. → [`05` §3](./05-career-and-startup.md#3-eo-lane) `#fde #assurance #regulation`

---

## One thing to DO this Thursday

→ **Send your 10 pre-staged Meta-alumni DMs at 8 AM PT** ([`05` §1](./05-career-and-startup.md#1-meta-outreach)) — segment by pool (displaced / redirected-to-AI / spinning-out), reference *their* work not the layoff, log each in `apps/meta-alumni-tracker.md` with a 90-day follow-up. This is a 48–72 hour reciprocity window; specificity and speed beat polish. **If you only do one thing today, do this** — then this weekend ship the hook-guarded MCP mini-agent + cost trace ([`03` §2](./03-practical-skills-and-tools.md#2-artifact)).

## Watchlist deltas

- 🆕 **Trump AI executive order (pre-release model review, 14–90 day window):** new thread — track the *final number* (14 = labs win on velocity; 90 = security hawks win); opens the pre-deployment-eval career lane.
- ✅ **Anthropic ↔ Colossus 1 (rumored 2026-05-09) → CONFIRMED & CONTRACTUAL:** $1.25B/mo through 2029 via SpaceX S-1. Close the "is it real" thread; open a "compute-as-the-binding-constraint" thread.
- 🆕 **Anthropic first profitable quarter (~$559M op profit, 2 yrs early):** new thread — strengthens the ME.md Anthropic-stack focusing decision; revenue-role hiring signal.
- 🆕 **OpenAI Erdős result (general model → novel proof):** new thread — watch *reproducibility/generality* follow-ups; if independent groups replicate across problems, the AI-research labor market reprices.
- 🆕 **ChatGPT Ads Manager (no minimum spend):** new thread — agent-mediated commerce/attribution wedge; watch whether Anthropic holds the ad-free line.
- ➡️ **Anthropic Agent SDK metering (June 15):** T-minus 25 days — orchestration/subagents multiply spend; pair the new Claude Code stack with per-step cost attribution.
- ➡️ **Gemini 3.5 Flash price war / WebMCP (Chrome 149):** still live from 2026-05-20; cost-router + WebMCP demo remain the week's top artifacts.
- ⬇️ **Google I/O prediction thread:** resolved 2026-05-20; Gemini Spark beta now rolling to AI Ultra "next week" — minor follow-up only.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + the EO mechanism in [`01` §1](./01-big-lab-moves.md#1-trump-eo) |
| 20 min | [`04` §1–2](./04-research-progress.md) — the Erdős proof + the live-benchmark wave (verification is the through-skill) |
| Today | [`05` §1](./05-career-and-startup.md#1-meta-outreach) — send the 10 DMs at 8 AM PT; log them |
| This weekend | [`03` §2](./03-practical-skills-and-tools.md#2-artifact) — ship the hook-guarded MCP mini-agent + cost trace |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
