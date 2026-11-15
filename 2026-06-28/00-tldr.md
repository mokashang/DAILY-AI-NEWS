# TL;DR — 2026-06-28 (Sunday)

Sixty-second skim. **The weekend the talent barrier fell — and China started copying the output.** Two stories landed in the same 48-hour window on Wednesday Jun 24, and they're the same dynamic seen from opposite sides: **Bloomberg confirmed Jonas Adler + Alexander Pritzel — both internally rated key Gemini contributors, both ex-AlphaFold collaborators of John Jumper — are leaving Google for Anthropic**, making **four senior DeepMind departures in six days** (Jumper + Adler + Pritzel → Anthropic; Shazeer → OpenAI). Simultaneously: **Anthropic disclosed to the US Senate Banking Committee that Alibaba ran 28.8 million distillation exchanges via ~25,000 fraudulent accounts** (Apr 22 – Jun 5) — the largest publicly-acknowledged scraping campaign against any frontier API ever. Underneath both: **Anthropic's ARR has crossed $30B with >1,000 customers paying >$1M annualized (doubled in <2 months)**, plus the **3.5 GW Broadcom/Google TPU partnership from 2027** — the financial gravity behind the talent flow. For you: the **coding × pre-training × AI-for-science staffing pillars are now public**, your **named JD vocabulary for next week's applications**, and the **September–October pre-IPO window is the last clean entry point** before the post-S-1 applicant flood.

---

1. **Adler + Pritzel → Anthropic — 4 senior DeepMind exits in 6 days.** Per Bloomberg (Wed Jun 24): Adler (Google AI coding) + Pritzel (Google pre-training); both ex-AlphaFold collaborators of John Jumper, who jumped 48h earlier. With Shazeer's parallel Google → OpenAI move 48h before that, this is **the loudest pre-IPO talent flow of 2026** — and the **explicit staffing map for Anthropic's product roadmap**: coding × pre-training × AI-for-science. → [`01` §1](./01-big-lab-moves.md#1-adler-pritzel) · [`05` §1](./05-career-and-startup.md#1-talent-signal) `#anthropic #deepmind #talent #pretraining`

2. **Anthropic accuses Alibaba of 28.8M distillation exchanges via ~25K fraudulent accounts.** Filed with the US Senate Banking Committee Jun 10, public Jun 24. **"Largest known distillation attack on Anthropic to date."** Alibaba shares fell >4% on the day. First time a frontier lab has *named* a state-aligned competitor as a specific IP-extraction actor at this scale; new template (named entity, scoped window, exchange + account counts, Senate disclosure path) will be copied. → [`01` §2](./01-big-lab-moves.md#2-alibaba-distillation) `#anthropic #alibaba #distillation #policy`

3. **Anthropic ARR >$30B; >1,000 customers >$1M annualized (doubled in <2 months); 3.5 GW Broadcom/Google TPU from 2027.** The financial gravity behind both stories above. Growth curve: $87M (Jan 24) → $1B (Dec 24) → $9B (end 25) → $14B (Feb 26) → $19B (Mar) → $30B (Apr) → $44–47B (May). Salesforce took ~20 years to reach $30B; Anthropic did it in <3. → [`01` §3](./01-big-lab-moves.md#3-anthropic-30b) `#anthropic #revenue #compute #broadcom`

4. **"Agentjacking" — new attack class at 85% exploit rate across 2,388 orgs.** Markdown injection inside *fake* Sentry error reports (or any telemetry stream) → AI coding agent reads as legit debug guidance → executes attacker's "fix." Weaponizes the *observability* surface as the injection vector. Pairs with the Alibaba story to mint a new category — *agent-input governance / adversarial-input sanitization* — bigger than either piece alone. → [`02` §1](./02-new-emerging.md#1-agentjacking) `#security #agentjacking #agents`

5. **API-abuse-detection + output-provenance becomes a fundable category.** The direct downstream of the Alibaba disclosure: every frontier API needs *bot-and-distillation detection* infra; today it's bespoke and Anthropic-internal. Horizontal-SaaS template = *"Cloudflare for frontier-API providers."* Anchor customer is a Tier-2 lab (Cohere / Mistral / sovereign-AI). Expect first $5–20M seeds inside 8 weeks. → [`02` §2](./02-new-emerging.md#2-abuse-detection-wedge) `#startups #funding #abuse-detection #provenance`

6. **Research: SciAgentArena (arXiv 2606.12736, Jun 10) — 200 real scientific tasks across single-cell/spatial omics, drug discovery, EHR, genetics; stepwise verification; agent-agnostic environment.** Headline finding isn't *win-vs-fail* — it's *unevenness*: agents work in well-specified data-analysis workflows; struggle on open-ended exploration. This is the **eval substrate for the Jumper/Adler/Pritzel AI-for-science team**; read end-to-end before any AI-for-science interview. → [`04` §1](./04-research-progress.md#1-sciagentarena) `#research #benchmarks #science #ai-for-science`

7. **Practical: ship two artifacts this Sunday.** **(a) Trusted-channel proxy** for your coding agent — 90 min, mitigates agentjacking, ~50 LOC; **(b) Claude Code discipline reset** against the June 26 official best-practices doc — scoped CLAUDE.md, skills-vs-subagents split, `/usage` per-agent cost attribution, Opus-orchestrator/Sonnet-worker routing. Pair them as one weekend; that's two CV-defensible artifacts both directly traceable to this week's news. → [`03` §1](./03-practical-skills-and-tools.md#1-trusted-channel-proxy) · [`03` §2](./03-practical-skills-and-tools.md#2-discipline-reset) `#claude-code #practical #portfolio`

8. **Career frame:** the **September–October pre-IPO window** (Anthropic October listing path; OpenAI reportedly slipping to 2027) gives you an **exogenous 60-day calendar** — apply by mid-Jul to clear 8–12wk interview loops *before* the public S-1 flood. Vocabulary to lift verbatim from this week's news for cover letters: *coding × pre-training × AI-for-science* (the staffing pillars), *adversarial-query detection / agent-RBAC / output provenance* (the new sub-lane). → [`05` §3](./05-career-and-startup.md#3-ipo-window-plan) `#career #ipo #anthropic #fde`

---

## One thing to DO this Sunday

→ **Ship the [trusted-channel proxy](./03-practical-skills-and-tools.md#1-trusted-channel-proxy) (90 min) AND complete the [Claude Code discipline reset](./03-practical-skills-and-tools.md#2-discipline-reset) (20 min) — both before bed.** Then publish a short LinkedIn post titled *"What I shipped the weekend agentjacking was disclosed."* That post + the two repos = the single most efficient set of artifacts you can put in front of an Anthropic / OpenAI / Cohere T&S recruiter on Monday morning. The IPO calendar above ([`05` §3](./05-career-and-startup.md#3-ipo-window-plan)) starts firing tomorrow — earn the right to that calendar by spending today shipping.

## Watchlist deltas

- 🆕 **DeepMind → Anthropic talent flow (Adler + Pritzel, Jun 24):** new thread — 4 senior departures in 6 days; explicit pre-IPO equity motive. Watch the *5th and 6th* names over the next 30 days; if the pattern hits 6+, Google will be forced into a public retention package (precedent-setting for Series-C-and-later AI comp resets).
- 🆕 **Anthropic vs Alibaba (Jun 24):** new thread — first frontier lab to publicly name a state-aligned competitor as an IP-extraction actor at scale. Watch (a) Alibaba's response (silence so far), (b) whether OpenAI files a parallel letter, (c) whether the federally-cleared-customer list ([Mythos 5](../2026-06-27/01-big-lab-moves.md#2-mythos5)) acquires a *second axis* (traceability, not just trustworthiness), (d) Alibaba share-price drift.
- 🆕 **Agentjacking (85% exploit rate, 2,388 orgs):** new thread — agent-input-governance is a *named category* now. Watch first $5–20M seed in either *agent-RBAC* or *trusted-channel-proxy* tooling inside 8 weeks; watch Anthropic / OpenAI public guidance updates on agent-input sanitization.
- 🔻 **OpenAI Sept 2026 IPO:** continues from [2026-06-27 deltas](../2026-06-27/00-tldr.md#watchlist-deltas) — **reported slip to 2027** holds; Anthropic likely beats OpenAI to public markets. Status: 🟡-stalled.
- ➡️ **Anthropic October IPO path:** still live. **Confidential S-1 filed Jun 1**, ARR now >$30B and growing. Watch the public S-1 (~15 days pre-roadshow) for segment-level revenue mix.
- ➡️ **Federal whitelisting as release paradigm (from [2026-06-27](../2026-06-27/00-tldr.md#watchlist-deltas)):** still live; the Alibaba disclosure adds a *second* axis (traceability) to the cleared-list framing.
- ➡️ **Karpathy → Anthropic recursive Claude-trains-Claude team:** still live from [2026-05-22](../2026-05-22/01-big-lab-moves.md#3-karpathy); no new shipping signal, but the [Adler/Pritzel hires](./01-big-lab-moves.md#1-adler-pritzel) materially deepen the bench for that team.
- ⬇️ **Inference-economics megaround thread (from [2026-06-27](../2026-06-27/00-tldr.md#watchlist-deltas)):** slower week for mega-rounds in the Jun 22–26 window (Seedcamp Fund 7 was the anchor at $220M + $100M select); the *threat-surface* widened instead. Expect seed-stage rounds in the new categories (agent-RBAC, distillation-detection) over the next 8 weeks.

---

## Gap note

Today is **Sunday Jun 28**. The repo skipped Jun 26 (Thursday in the synthetic chronology); the Jun 27 edition labeled itself Friday. This Sunday edition writes to *current state of play* (per [`daily-pipeline.md`](../daily-pipeline.md) anti-pattern: *"don't backfill stale news"*) and brings the WATCHLIST into June-28 alignment.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 Adler/Pritzel](./01-big-lab-moves.md#1-adler-pritzel) + [`01` §2 Alibaba](./01-big-lab-moves.md#2-alibaba-distillation) |
| 20 min | [`04` §1 SciAgentArena](./04-research-progress.md#1-sciagentarena) — the eval substrate for AI-for-science |
| Today | [`03` §1 trusted-channel proxy](./03-practical-skills-and-tools.md#1-trusted-channel-proxy) + [`03` §2 discipline reset](./03-practical-skills-and-tools.md#2-discipline-reset) — two artifacts, one Sunday |
| This week | [`05` §3 IPO-window 60-day calendar](./05-career-and-startup.md#3-ipo-window-plan) — apply Anthropic + Google + OpenAI by Friday |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
