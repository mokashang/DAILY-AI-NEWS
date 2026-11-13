# TL;DR — 2026-06-29 (Monday)

Sixty-second skim. **The week Anthropic sued the federal government — and Colorado's AI Act goes live tomorrow.** Over the weekend the **Department of Defense demanded Anthropic make Claude available for "all lawful purposes," including lethal autonomous weapons and mass domestic surveillance**; **Anthropic filed *two* federal lawsuits (CA + DC)** alleging unconstitutional First-Amendment retaliation and that Trump exceeded statutory authority — the most consequential lab-vs-government legal confrontation to date. Same window: **the US government partially lifted the Mythos 5 export-control ban** for ~100 cleared "critical infrastructure defenders" (the [`2026-06-27`](../2026-06-27/01-big-lab-moves.md#2-mythos5) framing now has both axes — trustworthiness *and* traceability — operative). Tomorrow (**Tue Jun 30**) the **Colorado AI Act becomes the first comprehensive state AI law in the US to actually take effect** — high-risk AI in employment, education, housing, healthcare, financial services, government, insurance, legal. The pre-IPO 60-day calendar from [`2026-06-28/05 §3`](../2026-06-28/05-career-and-startup.md#3-ipo-window-plan) just acquired a *Colorado compliance* lane that didn't exist three days ago.

---

1. **Anthropic sues the federal government over DOD demand.** Two federal lawsuits (Northern District of CA + DC) over DOD's demand that Claude be available for "all lawful purposes" — *including LAWs and mass domestic surveillance*. Anthropic's claim: **First-Amendment retaliation** for its Acceptable Use Policy + **Trump exceeded statutory authority**. The first time a frontier lab has pre-emptively litigated against the government over use-case scope. → [`01` §1](./01-big-lab-moves.md#1-anthropic-dod) `#anthropic #policy #dod #lawsuit #first-amendment`

2. **Mythos 5 partially relifted for ~100 cleared critical-infrastructure defenders.** Continuation of the [`2026-06-17`](../2026-06-17/01-big-lab-moves.md#1-fable-suspension) → [`2026-06-27`](../2026-06-27/01-big-lab-moves.md#2-mythos5) thread: the export-control suspension is now *re-opened with a federally-cleared whitelist* (no Fable 5 relift yet). The "federal whitelist" release paradigm is now the *default* release mode for capability-restricted models. → [`01` §2](./01-big-lab-moves.md#2-mythos-relift) `#anthropic #mythos5 #policy #export-controls`

3. **Colorado AI Act takes effect Tue Jun 30 — first comprehensive US state AI law to actually go live.** Regulates *high-risk AI systems* used in **employment, education, housing, healthcare, financial services, government services, insurance, legal services** for CO residents. Vendor + deployer obligations both apply (impact assessments, consumer rights, attorney-general enforcement). NY, CA, IL drafts now have a working precedent to copy. → [`01` §3](./01-big-lab-moves.md#3-colorado-ai-act) `#policy #colorado #regulation #high-risk-ai #compliance`

4. **DeepMind → Anthropic continues — the 5th and 6th names to watch this week.** No new public departure since [Adler + Pritzel ([2026-06-28/01 §1](../2026-06-28/01-big-lab-moves.md#1-adler-pritzel))], but the pattern is now 4 in 6 days; Google's retention package decision lands inside the next 14 days (the implicit deadline before the public-S-1 quiet period locks). → [`05` §1](./05-career-and-startup.md#1-talent-watch) `#anthropic #deepmind #talent #ipo`

5. **API-abuse-detection seeds — the first cohort starts pricing.** Following the Alibaba disclosure ([2026-06-28/02 §2](../2026-06-28/02-new-emerging.md#2-abuse-detection-wedge)), the named wedge (*"Cloudflare for frontier-API providers"*) is now seeing seed-stage pitch traffic; first 2–3 rounds expected to print in July. **Add this category to [`STARTUPS.md`](../STARTUPS.md) this week.** → [`02` §1](./02-new-emerging.md#1-abuse-detection-pricing) `#startups #funding #abuse-detection #provenance`

6. **Practical Monday: ship the Colorado AI Act compliance memo before bed.** 1-page memo explaining how a Claude-Code-built agent would document compliance with the *high-risk* designation; pairs with the [trusted-channel proxy from yesterday](../2026-06-28/03-practical-skills-and-tools.md#1-trusted-channel-proxy) and the [Claude Code discipline reset](../2026-06-28/03-practical-skills-and-tools.md#2-discipline-reset). Three artifacts → one weekend → on-thesis for the new compliance-engineering lane. → [`03` §1](./03-practical-skills-and-tools.md#1-colorado-compliance) `#practical #colorado #compliance #portfolio`

7. **Research: long-horizon benchmark wave hardens** — **SWE-EVO**, **LongCLI-Bench**, **EvoCodeBench**, **Code Review Agent Benchmark** (Devin / Claude Code / Codex / PR-agent head-to-head), and **LLM-as-an-Investigator** (Jun 11) all push the eval bar from *single-turn correctness* to *sustained-agent viability*. The eval-design skill is now the under-priced specialty. → [`04` §1](./04-research-progress.md#1-long-horizon-benchmarks) `#research #benchmarks #arxiv #agents`

8. **MCP crossed 10K public servers + 97M monthly downloads + Linux Foundation AAIF governance + OAuth 2.1 in spec + Cisco MCP security tooling at RSA.** The protocol is settled infrastructure; differentiation moved *up the stack*. The MCP-server portfolio item in [`ME.md`](../ME.md) needs OAuth + 5-tool depth + eval to still differentiate. → [`03` §2](./03-practical-skills-and-tools.md#2-mcp-infra) `#mcp #linux-foundation #oauth #security`

---

## One thing to DO this Monday

→ **Ship the Colorado AI Act compliance memo + apply to two FDE roles by Wednesday.** The compliance memo ([`03` §1](./03-practical-skills-and-tools.md#1-colorado-compliance)) is a 90-minute portfolio piece that *did not exist three days ago* — first-mover advantage on a real keyword that hiring managers will start grep'ing this week. The two FDE applications ([`05` §2](./05-career-and-startup.md#2-fde-apps-this-week)) lift directly off [`2026-06-28/05 §3`](../2026-06-28/05-career-and-startup.md#3-ipo-window-plan) — Anthropic FDE/Applied AI is the on-thesis lead. **The pre-IPO 60-day calendar starts firing today; the Colorado lane is the freshest entry vocab on it.**

## Watchlist deltas

- 🆕 **Anthropic vs DOD federal lawsuits (CA + DC):** new thread — first pre-emptive frontier-lab-vs-government litigation. Watch (a) DOJ response posture, (b) whether Microsoft / Palantir / Scale file amici on the *other* side, (c) whether OpenAI / Google publicly distinguish their AUPs, (d) the docket-management calendar (motions to dismiss likely 30–45d).
- 🆕 **Colorado AI Act live Tue Jun 30:** new thread — first comprehensive US state AI law in force. Watch (a) which vendors update their AUPs/RAIDs in the first 30 days, (b) first enforcement action (probably announced within 90d to set precedent), (c) NY/CA/IL legislative response — copy or differentiate, (d) whether "high-risk" gets a Colorado-AG technical definition (this is where Claude-vs-GPT-vs-Gemini *gets graded by a state*).
- ➡️ **Mythos 5 partial relift (~100 critical-infra orgs):** continues from [2026-06-17 suspension](../2026-06-17/01-big-lab-moves.md#1-fable-suspension) → [2026-06-27 cleared-customer framing](../2026-06-27/01-big-lab-moves.md#2-mythos5). No Fable 5 relift yet. Watch when (if) Fable 5 follows.
- ➡️ **DeepMind → Anthropic talent flow:** continues from [2026-06-28/01 §1](../2026-06-28/01-big-lab-moves.md#1-adler-pritzel). 4 in 6 days. The 5th–6th names + Google's retention announcement land in the next 14 days.
- ➡️ **Alibaba distillation (Senate Banking, Jun 10/24):** continues from [2026-06-28/01 §2](../2026-06-28/01-big-lab-moves.md#2-alibaba-distillation). No Alibaba public response yet; no parallel OpenAI letter yet.
- ➡️ **Anthropic Oct IPO path / >$30B ARR:** continues from [2026-06-28/01 §3](../2026-06-28/01-big-lab-moves.md#3-anthropic-30b). Watch the public S-1 (~15d pre-roadshow); the DOD lawsuit is now a *risk-factor disclosure* item.
- ➡️ **Agentjacking + API-abuse-detection seed cohort:** continues from [2026-06-28/02 §1](../2026-06-28/02-new-emerging.md#1-agentjacking) and [§2](../2026-06-28/02-new-emerging.md#2-abuse-detection-wedge). First 2–3 seed rounds expected in July.
- ⬇️ **MCP at 10K servers + AAIF + OAuth 2.1 + Cisco security tooling:** moves from "emerging" → "settled infrastructure." Differentiation is now *which* MCP tools you build, against *which* auth + audit policy.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 DOD lawsuit](./01-big-lab-moves.md#1-anthropic-dod) + [`01` §3 Colorado AI Act](./01-big-lab-moves.md#3-colorado-ai-act) |
| 20 min | [`05` §2 FDE applications playbook (this week)](./05-career-and-startup.md#2-fde-apps-this-week) + [`04` §1 long-horizon benchmark wave](./04-research-progress.md#1-long-horizon-benchmarks) |
| Today | [`03` §1 Colorado compliance memo](./03-practical-skills-and-tools.md#1-colorado-compliance) — 90 minutes; ship before bed |
| This week | Cross-reference [`2026-06-28/05 §3 IPO-window 60-day calendar`](../2026-06-28/05-career-and-startup.md#3-ipo-window-plan) — apply to 3 Anthropic + 3 Google + 2 OpenAI by Friday |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
