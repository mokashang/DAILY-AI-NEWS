# TL;DR — 2026-06-07 (Sunday)

Sixty-second skim. Sunday-after-the-Saturday — builds on [2026-06-06](../2026-06-06/) (Glasswing operational + Anthropic Rule-135 S-1 + WWDC T-2 + Claude self-coding >80%) and [2026-06-04](../2026-06-04/) (Anthropic filed + Opus 4.8 + multi-model priced). **The arc this weekend: Anthropic beat OpenAI to the IPO line, Apple is about to hand its AI front door to Google, and the AI-finds-the-bugs market just went international.** **Anthropic's confidential S-1 with the SEC (filed June 1)** stands at a **~$965B valuation** (post the $65B Series H) and a **~$47B run-rate** — the first frontier lab to formally start the IPO process, ahead of OpenAI's September target. **Tomorrow (Mon June 8, 10 AM PT)**, Tim Cook gives his final WWDC keynote, where Apple is expected to ship a **rebuilt Siri powered by a custom 1.2-trillion-parameter Gemini model** (~$1B/yr licensing) and a **multi-AI "Search or Ask" panel** routing to Siri / ChatGPT / Gemini. And on the security side, **Anthropic expanded Project Glasswing to 150+ partners across 15+ countries** (power, water, healthcare, comms, hardware) with **Claude Mythos surfacing 23,019 vulnerabilities** in a month of scanning. The picture for you: **the public-market turn is now real**, **the multi-provider OS layer (your iPhone) is now real**, and **agentic security is becoming a global category, not a US one**.

---

1. **Anthropic confidentially filed an S-1 — first frontier lab to formally start the IPO process.** Filed **June 1**, on a **~$965B valuation** following the **$65B Series H** that closed in late May, with a **~$47B run-rate** as of May 2026. Targeting an **October 2026** listing (so ~30 days ahead of OpenAI's September window — the order has flipped). → [`01` §1](./01-big-lab-moves.md#1-anthropic-s1) `#anthropic #ipo #public-markets`

2. **Apple WWDC 2026 tomorrow — "All Systems Glow," Cook's farewell, and Siri-on-Gemini.** Apple has reportedly **licensed a custom 1.2-trillion-parameter Gemini model from Google (~$1B/yr)** as the backbone of rebuilt Siri's cloud intelligence; a **system-wide "Search or Ask" panel** lets users route to Siri / ChatGPT / Gemini — turning the iPhone into a **multi-provider AI marketplace.** Cook hands off to **John Ternus on Sept 1.** → [`01` §2](./01-big-lab-moves.md#2-wwdc) `#apple #google #gemini #wwdc`

3. **Anthropic Project Glasswing scaled internationally.** **+150 partners in 15+ countries** (power, water, healthcare, communications, hardware). **Mythos has flagged 23,019 potential vulnerabilities** across 1,000+ open-source projects, **~6,200 high/critical**, **>90% confirmed valid** on independent review — including a forge-certificates exploit in **wolfSSL** (used by billions of devices). The bottleneck is now **patching**, not finding. → [`01` §3](./01-big-lab-moves.md#3-glasswing) `#anthropic #security #mythos #critical-infra`

4. **OpenAI's frontier models go on AWS (June 2).** GPT-5.5 + Codex callable from existing AWS infra — direct distribution shift; OpenAI is no longer Azure-only at the cloud layer. **Microsoft countered the same week**: at Build, it unveiled **MAI-Code-1-Flash** (its first code model) and **MAI-Thinking-1** (reasoning) — partial decoupling from OpenAI dependence. → [`02` §1](./02-new-emerging.md#1-distribution-shift) `#openai #aws #microsoft #coding-models #distribution`

5. **The funding rounds you should know from this week.** **Suno $400M Series D (Jun 3)** · **NewLimit $435M Series C (Jun 2)** · **Generalist AI $400M (Jun 4, embodied/robotics)** · **Collate $95M Series A (Jun 3, data-platform)** · **Opal Security $23M (Jun 5, identity)**. The pattern: **vertical AI tied to hard-to-replace workflows + AI-infra** is where the checks are still landing. → [`02` §2](./02-new-emerging.md#2-funding) `#funding #series-d #robotics #vertical-ai`

6. **The consensus 2026 Claude Code stack is now five layers.** **CLAUDE.md** (project rules, always-on) + **MCP servers** (external tools/data) + **skills** (reusable workflows) + **hooks** (automation + safety) + **subagents** (isolated research/review). The decision rule: *"if it must be true every turn → CLAUDE.md; sometimes-procedure → skill; auto-script → hook; would fill main ctx → subagent."* → [`03` §1](./03-practical-skills-and-tools.md#1-five-layer-stack) `#claude-code #mcp #subagents #hooks #skills`

7. **Research: agents are now being asked to engineer their own RL post-training.** **Agent² RL-Bench** (arXiv 2604.10547) tests whether LLM agents can design + run agentic-RL post-training — the operational form of the **Karpathy-at-Anthropic** thesis (use Claude to accelerate Claude). Plus a **unified review of LLM-agent memory/skills/protocols/harness** (arXiv 2604.08224) — the closest thing to a 2026 textbook for the field. → [`04` §1](./04-research-progress.md#1-agent2-rlbench) `#arxiv #benchmarks #agentic-rl #post-training`

8. **Career read for the weekend:** the AI job market has split sharply. **MLE roles +41.8% YoY**, but **new-grad SWE hiring at top companies fell ~50%**. **Frontier-lab senior comp $470–630K median (top tail $1M+)**, vs **enterprise MLE $170–245K total.** The path *into* the top tail still runs through **production artifacts + public expertise + 6–12 month relationship-building** — not applications. **OpenAI Residency 2026** is open (`$220K`, 6 months, designed for non-ML backgrounds). → [`05` §1](./05-career-and-startup.md#1-bifurcation) `#jobs #mle #compensation #residency`

---

## One thing to DO this Sunday

→ **Pre-stage your WWDC monitoring doc (60 min)** so you're not improvising at 10 AM PT tomorrow. Set up: (1) a one-page table with columns *prediction / actual / source / implication* covering the **Gemini-in-Siri**, **multi-AI Search-or-Ask**, **App-Intents-for-agents**, and **foldable-iPhone** rumors; (2) the **Anthropic S-1 watchlist row** in your repo updated with what to look for in the eventual public version (revenue mix, Microsoft-comparable terms, Colossus cost line); (3) **finish the dual-model sanitiser artifact carry-over from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact)** with one real MCP server + per-step cost table — this is the project that survives one more week of slippage **only if you ship it today**.

## Watchlist deltas

- 🔻🟢 **Anthropic IPO path:** **flipped 🟡 → 🟢 (formally filed June 1)** — the order swapped with OpenAI (Anthropic ahead). Watch for the public S-1 (revenue mix, R&D %, Colossus cost line, customer concentration).
- 🆕 **Apple → Google Gemini for Siri (~$1B/yr; 1.2T-param custom):** new thread — Apple's *multi-provider* posture (Siri/ChatGPT/Gemini panel) is the consumer mirror of the enterprise pattern; tracks Apple Extensions SDK (iOS 27).
- 🆕 **Microsoft MAI-Code-1-Flash + MAI-Thinking-1:** new thread — Microsoft no longer purely an OpenAI-dependent stack at the model layer; watch the price/perf vs Codex and Claude Code.
- 🆕 **Project Glasswing international expansion (150+ partners, 15+ countries):** new thread — agentic-SOC + AI-vulnerability disclosure is the Mythos commercial story; watch for the first formal CVE-class disclosure attributable to Mythos.
- 🆕 **OpenAI on AWS:** new thread — distribution surface, not just compute. Watch whether Anthropic responds with deeper Azure distribution.
- ⬇️ **OpenAI S-1 / Sept 2026 IPO:** still 🟡 — no public filing confirmation since the [2026-05-22 "as early as today"](../2026-05-22/01-big-lab-moves.md#2-openai-s1) line; competitive pressure from Anthropic's June 1 filing is the new variable.
- ➡️ **Trump AI executive order:** still 🔴-stalled from [2026-05-22](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) — no re-scheduled signing date.
- ➡️ **Karpathy → Anthropic pre-training:** 🟢 confirmed and seated; watch what this team *ships* (the operational test of the [Agent² RL-Bench](./04-research-progress.md#1-agent2-rlbench) direction).
- ➡️ **Anthropic Agent SDK metering (June 15):** **T-minus 8 days.** This is the *last* full weekend before the meter flips — the audit / batching / model-routing work needs to land today or tonight.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Anthropic S-1 ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)) + WWDC preview ([`01` §2](./01-big-lab-moves.md#2-wwdc)) |
| 20 min | [`03` §1](./03-practical-skills-and-tools.md#1-five-layer-stack) (5-layer Claude Code stack) + [`04` §1](./04-research-progress.md#1-agent2-rlbench) (Agent² RL-Bench + memory/skills/protocols review) |
| Today | Pre-stage tomorrow's WWDC monitoring doc + close the dual-model-sanitiser artifact |
| This week | The **June 15 metering** prep window closes Friday — see [`03` §2](./03-practical-skills-and-tools.md#2-metering-prep) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
