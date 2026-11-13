# TL;DR — 2026-09-24 (Thursday)

Sixty-second skim. **The price collapse arrived, Claude did science, and the UN gavel fell — all inside 48 hours.** On **Sept 22**, Anthropic released **Claude Opus 5.5** at a **20% price cut vs Opus 5 and 40% lower total cost than Fable 5.1** (which it beats on agentic benchmarks); ~90 minutes later OpenAI shipped **GPT-6 Sol + GPT-6 Luna at 50% off** the GPT-5.6 line, formalising a three-tier family (Astra/Sol/Luna). On **Sept 23**, Anthropic opened a **life-sciences lab in the Bay Area** and disclosed that **Claude autonomously discovered a novel CRISPR-adjacent enzyme system (ART)** using 950 agents / 21 hours / 210M tokens — endorsed by Feng Zhang. Same day at **UN Security Council**, **Amodei + Altman personally pleaded for international AI regulation** (bio-weapons ban, verification, incident notification). Sora API dies today (Sept 24). For you: **the "cost-aware model routing" skill just got *more* valuable, not less** — three price tiers × four labs × weekly cadence = the router is the single interview-differentiating artifact of Q4 2026.

---

1. **Anthropic Opus 5.5 (Sept 22) — Fable-beating performance at 40% lower cost.** $4/$20 per 1M in/out (vs Opus 5 at $5/$25), cache reads **60% off to $0.20/1M**, "fast mode" at 2× price for 2.5× speed. Beats Fable 5.1 on key agentic benchmarks despite Fable being 150% more expensive. Typical workload cost drops ~40% (partly from fewer tokens used). → [`01` §1](./01-big-lab-moves.md#1-opus-5-5) `#anthropic #pricing #agents`

2. **OpenAI GPT-6 Sol + Luna (Sept 22, ~90 min after Opus 5.5) — 50% API price cut, three-tier family formalised.** Sol at $2/$10 per 1M (half of Opus 5.5), Luna at $0.10/$0.50 (clerical-workhorse tier), Astra stays at $10/$50. OpenAI spokesperson: **prices are permanent, not promotional.** Coordinated slowdown over. → [`01` §2](./01-big-lab-moves.md#2-gpt-6-sol-luna) `#openai #pricing #model-releases`

3. **Anthropic opens a wet lab; Claude autonomously discovers a novel CRISPR-adjacent enzyme system (Sept 23).** New Bay Area BSL-1/2 lab. Discovery: **"array-associated reverse transcriptases" (ART)** — reverse transcriptase + partner gene + evenly-spaced DNA repeat array. Method: **~950 Claude agents combed a DNA-sequence database for 21 hours, 210M tokens**, one flagged the repeat pattern. **Feng Zhang (CRISPR pioneer): "genuinely intriguing, merits further investigation."** First public autonomous scientific discovery credited to a general AI. → [`01` §3](./01-big-lab-moves.md#3-anthropic-biolab) `#anthropic #research #agents #bio`

4. **UN Security Council — Amodei + Altman ask for international AI regulation (Sept 23–24).** Amodei: three proposals — (a) narrow global ban on AI bio-weapons; (b) evaluation/verification systems for cross-country commitments; (c) common testing standards + incident-notification network. Altman: "important decisions" belong in democratic institutions "accountable to the people they serve" (implicit China carve-out). Frames a new career lane: **AI safety/eval infra as international standards work.** → [`01` §4](./01-big-lab-moves.md#4-un-security-council) `#policy #un #safety #eval`

5. **Sora API shuts down TODAY.** All Sora-2 endpoints go dark Sept 24; consumer app died Apr 26. Videos you generated are yours; server-only content is deleted. **Migration playbook:** Runway, Kling, Veo 3 for video-gen dependencies — ship the swap this weekend if you built on it. → [`02` §1](./02-new-emerging.md#1-sora-api-shutdown) `#openai #video #api-deprecation`

6. **Twelve Labs $100M Series B (video-understanding) + Stability AI $76M with UMG/Sony/Warner/EA/AMD Ventures.** Twelve Labs = the video-search primitive underneath every "search my archive" agent workflow. Stability's cap table now anchored by **music labels + a AAA game publisher + a chip vendor** — rights-cleared training data as a competitive moat. → [`02` §2](./02-new-emerging.md#2-funding-round) `#funding #video #rights`

7. **Practical: the three-tier routing rubric your router needs by Friday.** Use **Luna / Gemini 3.8 Flash / Muse Spark 1.3** for clerical (summaries, tagging, structured extraction) at $0.10–0.75/1M; **Sol / Opus 5.5** for coding + long agentic sessions at $2–4/1M; **Astra / Fable 5.1** only when the eval requires the extra 5–10 pts. Log per-request tier + cost. Publish the eval. → [`03` §1](./03-practical-skills-and-tools.md#1-three-tier-routing) `#claude-code #routing #eval`

8. **Practical (Claude Code): the four-primitive discipline is now the community consensus.** Every 2026 best-practice guide converges on **Hooks (enforcement) / Skills (long-lived expertise loaded when relevant) / Subagents (isolated parallel work) / CLAUDE.md (always-on project guidance).** Prefer *less* parallelism — each subagent re-reads CLAUDE.md and skills from scratch; parallel pays only when tasks are truly independent. → [`03` §2](./03-practical-skills-and-tools.md#2-four-primitive-discipline) `#claude-code #skills #hooks #subagents`

9. **Research: DolphinBench — Pareto frontier of agent memory (arXiv 2609.24971, Sept 21).** Latest in a Q3 wave (EvoMemBench, MemTools, ART for reverse-transcriptase discovery itself) making **agent memory the hottest research vertical of Q3 2026.** The "lifelong agent" frame from May's edition ([2026-05-19](../2026-05-19/04-research-progress.md)) is now empirically-benchmarked, not aspirational. → [`04` §1](./04-research-progress.md#1-dolphinbench) `#arxiv #memory #agents #benchmarks`

10. **Career: hiring holds, salary bands split, "AI Engineer" up 143% YoY.** US market ~**49,200 open AI-engineer positions**, **3.2:1 demand/supply**. **AI-eng median TC $242K**, mid-level base $160–210K + 15–25% bonus; MLE median $197K. **70% of roles are mid/senior IC** — only 2% Director+. **Over 75% now seek domain experts, not generalists** — pick a vertical this week. → [`05` §1](./05-career-and-startup.md#1-hiring-map) `#careers #salary #jobs`

---

## One thing to DO this Thursday

→ **Extend the router shim from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) to route to Opus 5.5 / Sol / Luna** using the new price points. Add a **fourth eval case: "novel-discovery-style multi-step retrieval + reasoning"** — because the ART result is a peek at the workload that will be the interview question of Q4 (long-horizon, tool-heavy, evaluation by scientific merit not string match). Publish. Details in [`03` §3](./03-practical-skills-and-tools.md#3-router-extension).

## Watchlist deltas

- 🆕 **Second inference-price collapse of Q3 (Sept 22):** new thread. First was Fable 5.1 cache-reads on Sept 1; today Opus 5.5 + Sol/Luna add a per-token cut and a three-tier family. Watch whether Google + Meta match by end of week — if they do, **the reference cost of a "cheap fast inference" job just dropped ~50% in 3 weeks.**
- 🆕 **Anthropic wet lab + autonomous scientific discovery:** new thread. First AI-credited discovery with a domain-expert public endorsement. Track (a) reproducibility (independent lab verifies ART?); (b) whether OpenAI / DeepMind announce competing labs (DeepMind arguably already has Isomorphic — but Isomorphic is *drug design*, not open discovery).
- 🆕 **UN Security Council AI session:** new thread. Amodei's three specific proposals give the shape of a possible bio-weapons treaty; watch UN First Committee follow-up in October.
- 🆕 **Sora API shutdown TODAY:** ends thread — video-gen dependencies on OpenAI Sora are all dead by 5pm PT. Migration workload for anyone who built on it.
- ➡️ **Model fatigue (from 2026-09-10):** three of the four Sept 1–3 models now have priced-down / capability-up refreshes within 3 weeks. **Release cadence is holding — but pricing cadence just accelerated.**
- ➡️ **Anthropic IPO (from 2026-09-10):** still watching for filing date. The lab announcement + Opus 5.5 pricing are both S-1-shaped narrative — "we ship science and we ship price cuts."
- ⬇️ **"Latest model" fluency:** further deprecated. The task now is *routing across three tiers per lab*, which nobody memorises.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-opus-5-5) (Opus 5.5) + [`01` §3](./01-big-lab-moves.md#3-anthropic-biolab) (Anthropic biolab) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — three-tier routing rubric + Claude Code four-primitive discipline + the router extension |
| Today | [`03` §3](./03-practical-skills-and-tools.md#3-router-extension) — extend the router, log the costs, publish |
| Tonight | [`04` §1](./04-research-progress.md#1-dolphinbench) — DolphinBench + the ART method paper style; you'll want to reference both in Q4 interviews |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
