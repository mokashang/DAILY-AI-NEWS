# TL;DR — 2026-09-23 (Wednesday)

Sixty-second skim. **Price-war Wednesday — the pacing petition failed inside 20 days.** Between yesterday afternoon and this morning, **Anthropic shipped Claude Opus 5.5 (40% cheaper than Opus 5, Fable-5.1-class quality, #1 on Artificial Analysis Intelligence Index)** and **OpenAI shipped GPT-6 Sol + GPT-6 Luna (roughly 50% cheaper than GPT-5.6)** — the two labs whose CEOs signed the 1,100-employee pacing letter three weeks ago released dueling price cuts within hours of each other. Meanwhile **the UN Security Council convenes today at UN HQ** — Altman, Amodei, Delangue, Bengio brief the 15-member council chaired by the French FM; and **Anthropic's IPO slipped from October to November at a targeted ~$2T valuation** (Q3 numbers before pricing). Under the noise: **the frontier's business model just re-anchored on price-per-intelligence, not intelligence itself.** For you: **the router artifact you should have shipped last week is now the interview-differentiating deliverable of Q3 2026** — the market just proved routing is where the money lives.

---

1. **Anthropic Opus 5.5 released Sept 22 — Fable-5.1-class at 40% lower cost, #1 on Artificial Analysis Intelligence Index.** $4/M input · $20/M output · **$0.20/M cached reads** (60% off Opus 5); 1M-token context; June 2026 cutoff; 30%+ faster output; beats GPT-6 Astra on agentic coding, knowledge work, multidisciplinary reasoning per Anthropic's own numbers. → [`01` §1](./01-big-lab-moves.md#1-opus-55) `#anthropic #opus55 #pricing`

2. **OpenAI GPT-6 Sol + Luna released same window — API prices cut ~50%.** Sol: $2/M in · $10/M out (from $4/$20). Luna: **$0.10/M in · $0.50/M out** (from $0.20/$1.20). Both improve on GPT-5.6 benchmarks; positioned as the enterprise workhorses under GPT-6 Astra. Fortune framing: "dueling models as AI price wars heat up." → [`01` §2](./01-big-lab-moves.md#2-gpt-6-sol-luna) `#openai #gpt6 #pricing`

3. **UN Security Council AI briefing TODAY (Sept 23) — Altman, Amodei, Delangue, Bengio brief the 15-member council.** French FM Jean-Noël Barrot chairs during the UNGA week; US + China both speak. Altman is expected to push **shared benchmarks for capability + safeguards**. First time frontier-lab CEOs collectively address the Security Council. → [`01` §3](./01-big-lab-moves.md#3-un-security-council) `#policy #un #governance`

4. **Anthropic IPO slips October → November at potential ~$2T valuation.** Retail-money pre-IPO fund inflows are the reported cause of the slip — lets Anthropic ship Q3 numbers before pricing. Filed S-1 June 1; underwriters Goldman, JPMorgan, Morgan Stanley; annualised revenue > $65B end-July, investors modelling >$110B by year-end. → [`01` §4](./01-big-lab-moves.md#4-anthropic-ipo-slip) `#anthropic #ipo #public-markets`

5. **Cognition (Devin) hit $48B on Sept 8 — a16z + Accel lead $2B Series E.** ARR jumped $492M → ~$900M in four months; targeting $4–5B by year-end; clients include Mercedes-Benz, NASA, Goldman Sachs. TechCrunch framing: "AI coding is far from a winner-take-all market." Puts a floor under the whole autonomous-coding-agent thesis. → [`02` §1](./02-new-emerging.md#1-cognition-48b) `#funding #cognition #coding-agents`

6. **Practical: the price cuts just rewrote your cost-router.** If you were routing to Fable 5.1 for coding, **switch to Opus 5.5** (same quality tier, 40% cheaper, 60% cheaper cached reads). If you were routing to GPT-5.6 for cheap batch summarisation, **switch to GPT-6 Luna** (~50% cheaper, better benchmarks). Rerun your cost dashboard by end of Wednesday. → [`03` §1](./03-practical-skills-and-tools.md#1-reroute-now) `#pricing #router #cost-observability`

7. **Practical: Claude Code 2026 caching discipline (Anthropic engineering blog).** Never swap tools or models mid-session. Treat cache-hit-rate as an uptime SLO. Avoid subagents that outlive the cache TTL. Move the volatile bits (turn-by-turn conversation, tool results) to the tail so the stable prefix (system, tools, CLAUDE.md) stays cached. → [`03` §2](./03-practical-skills-and-tools.md#2-cache-discipline) `#claude-code #prompt-caching #agents`

8. **Research: Anthropic's own paper on Claude accelerating biomolecular modeling — 30+ open-source tools optimized ~4× in <4 weeks, single-node prediction for >10K-token systems, FlashPairformer 2.7–2.9× on triangle attention, $150 GPU spend replacing prior $10K campaigns.** Open-sourced with a $1M Adaptyv Bio protein design competition. Blueprint for a **"Claude as your senior systems engineer"** workflow that generalises far past biology. → [`04` §1](./04-research-progress.md#1-biomolecular-optimization) `#anthropic #biology #systems-optimization`

9. **Research: arXiv agent-memory wave hardens — LongMemEval-V2, "Memory for Autonomous LLM Agents" (3-D taxonomy: temporal scope × representational substrate × control policy), "Agentic Context Management" (memory-as-lifecycle).** Agent memory is now a first-class benchmarkable subsystem. **This is the eval skill's next arena.** → [`04` §2](./04-research-progress.md#2-agent-memory) `#arxiv #agents #memory #evals`

10. **Career: AI/ML engineering hiring stays hot — ML postings ~490/week, no seasonal softening.** Median MLE base **$197K**, AI engineer **$176K**, staff MLE $230–310K; Bain modelling 1.3M US AI jobs by 2027 against ~645K talent supply. **The "AI slowdown" narrative did not slow hiring — it accelerated the wage premium for people who can prove ROI.** → [`05` §1](./05-career-and-startup.md#1-hiring-map) `#careers #salary #hiring`

---

## One thing to DO this Wednesday

→ **By EOD: rerun your model-router against the new price sheet and publish the diff.** Two tables: (1) old cost/1K requests per task class vs. new; (2) old p50 latency + quality vs. new. One paragraph on what you're switching. Push to your public repo, LinkedIn post with the tables inline. **This is the artifact that catches the "why should we hire you now" question the price war just created.** Details in [`03` §1](./03-practical-skills-and-tools.md#1-reroute-now) and [`03` §3](./03-practical-skills-and-tools.md#3-router-diff-artifact).

## Watchlist deltas

- 🆕 **Price-war Wednesday:** new thread. Anthropic + OpenAI both cut ~40–50% within one release window; the pacing petition (2026-09-10) is functionally dead. Track whether Google/Meta match by end of September — they must, or lose enterprise share.
- 🆕 **Anthropic IPO slips to November:** update to the 2026-09-10 IPO thread. Watch for the Q3 revenue disclosure — if ARR clears $80B run rate, the $2T target holds; if not, expect the roadshow to reframe on margins.
- 🆕 **UN Security Council AI session:** new policy thread. First frontier-CEO briefing to the Council; watch for any communiqué language on "capability benchmarks" — that's the seed of the international eval standard.
- 🆕 **Cognition $48B:** new coding-agents thread. Not one winner; the coding-agent market clears at multi-player scale. Every dev-tools YC application this month gets re-scored against Cognition's numbers.
- ➡️ **Fable 5.1 cache economics (2026-09-10):** superseded by Opus 5.5 — same tier of quality, cheaper still. Rerun the audit.
- ➡️ **Model-router artifact (2026-09-10):** now urgent, not optional. The price cuts moved the deadline.
- ⬇️ **"Which model is smartest?" as a career skill:** further deprecated. **"Which model at what price for this workload?" is what the market is paying for this week.**

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-opus-55) + [`01` §2](./01-big-lab-moves.md#2-gpt-6-sol-luna) (the dueling price cuts) |
| 20 min | [`03` §1–3](./03-practical-skills-and-tools.md) — reroute-now table + Claude Code cache discipline + the router-diff artifact template |
| Today | [`03` §3](./03-practical-skills-and-tools.md#3-router-diff-artifact) — publish the router diff |
| Tonight | [`04` §1](./04-research-progress.md#1-biomolecular-optimization) — read Anthropic's biomolecular paper as a workflow template you can copy into any legacy codebase |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
