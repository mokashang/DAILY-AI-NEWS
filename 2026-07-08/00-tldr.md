# TL;DR — 2026-07-08 (Wednesday)

Sixty-second skim. **The frontier is being repriced from three sides at once — capital, sovereignty, and geography — and the day's news is the receipt.** **Anthropic overtook OpenAI on revenue *and* on secondary-market valuation** (Fortune, Jul 7) — the first time either has happened; **run-rate revenue is now >$30B, up from ~$9B end-of-2025** (Anthropic, Jul 6). **OpenAI's answer is *political*: a proposed 5% equity donation (~$42.6B) to a US sovereign wealth fund modeled on Alaska's oil vehicle** (CNBC/TechCrunch/FT, Jul 2–3) — with the pitch extended to Anthropic/Google/Meta as a category-wide precedent. **Anthropic's answer is *infrastructural*: a 20-year, $19B TeraWulf lease on 401 MW in Hawesville, KY** (Anthropic/CNBC, Jul 6) — first power late 2027. **And the ground shifted underneath both**: **Chinese open-weight models (GLM 5.2, Kimi K2.5/K2.7 Code) now account for 30–46% of enterprise API tokens on US developer platforms** at **~1/5 the cost** on comparable agentic benchmarks (CNBC, Jul 7). For you: **the map of "who's winning and where the work is" got rewritten this week — Anthropic became the reference lab, cost-aware model routing became a first-class skill, and the entry-level lanes narrowed further.**

---

1. **Anthropic overtakes OpenAI on revenue AND secondary valuation.** Fortune confirmed both firsts on Jul 7; Anthropic's own Jul 6 post pegs **run-rate revenue >$30B** (vs ~$9B end-of-2025 — a **>3×** jump in ~6 months). → [`01` §1](./01-big-lab-moves.md#1-anthropic-crossover) `#anthropic #openai #revenue`

2. **Anthropic × TeraWulf: $19B / 20 years / 401 MW in Kentucky.** Announced Mon Jul 6. First-power **late 2027**; site is a former aluminum smelter with existing transmission/fiber (accelerates buildout). TeraWulf stock +17% pre-market. → [`01` §2](./01-big-lab-moves.md#2-terawulf) `#anthropic #compute #infra`

3. **OpenAI proposes a 5% US-government equity stake (~$42.6B) via a sovereign wealth fund** (Alaska-Permanent-Fund model). Extended as a **category** proposal for Anthropic/Google/Meta. Precedent: the Aug-2025 10% Intel stake + Nvidia/AMD China revenue-share deals. → [`01` §3](./01-big-lab-moves.md#3-openai-swf) `#openai #policy #public-markets`

4. **Chinese open-weight models are now 30–46% of enterprise API tokens on US dev platforms.** GLM 5.2 lands within 1pp of Opus 4.8 on a leading agentic bench at **~1/5 the cost**; Coinbase defaulted to GLM 5.2 + Kimi K2.7 Code and **cut its AI bill ~50%** even as usage grew. → [`02` §1](./02-new-emerging.md#1-china-cost) `#china #open-source #cost #routing`

5. **Taktile $110M Series C (Goldman Sachs).** *Agentic decision platform* for banks/insurers — 95% B2B underwriting automation, 75% fewer AML false positives; one large insurer projects **$90M+/yr** claims-processing savings. Reads as the **agentic-fintech reference deal** of Q3. → [`02` §2](./02-new-emerging.md#2-taktile) `#funding #agents #fintech`

6. **JADEPUFFER — the first documented end-to-end agentic ransomware.** Sysdig (Jul 7): LLM-driven agent chained recon → cred theft → lateral movement → destruction over an internet-facing Langflow instance (CVE-2025-3248); adapted mid-attack (failed login → working fix in **31 seconds**). Encrypted 1,342 Nacos items with a key that **was never exfiltrated** — paying didn't restore data. → [`02` §3](./02-new-emerging.md#3-jadepuffer) · [`05` §3](./05-career-and-startup.md#3-defense-lane) `#security #agents #ransomware`

7. **Practical: the "cost-router + prompt-cache stack" is the July-Aug lever.** Claude Sonnet 5 promo pricing (**$2/$10 per Mtok, 1M ctx, through Aug 31**) + static-context-first prompt structure for cache hits + optional Chinese-model fallback for eval-tier work = **50%+ cost cut with no measurable capability loss on non-frontier work**. → [`03` §1](./03-practical-skills-and-tools.md#1-cost-router-stack) `#claude-code #cost #prompt-caching`

8. **Research: real-tool agent evaluation deepens.** **AgenticDataBench** (arXiv 2607.01647, Jul 2) — 15 domains + 5 real B2B fintech workflows, reproducible testbed. Pairs with **BuilderBench** (open-ended exploration), **AgenticPay** (multi-agent negotiation), **Terminal-Bench** (CLI agent tasks), and **CLAWSBench** (productivity-agent safety). The bar continues to move from "toy tools" toward *production workflows*. → [`04` §1](./04-research-progress.md#1-agent-evals) `#arxiv #benchmarks #agents`

9. **Meta ships Muse Image** — first image model from **Meta Superintelligence Labs** (Alexandr Wang). Reasoning-before-generation, multi-image blending, real-time web context; beats Google's Nano Banana 2 on multiple evals, sits just behind GPT Image on overall quality. → [`02` §4](./02-new-emerging.md#4-muse) `#meta #image #superintelligence-labs`

---

## One thing to DO this Wednesday

→ **Ship the cost-router artifact.** Turn last week's Opus-orchestrator/Sonnet-worker split ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) into a **runnable notebook + README** that:
1. Uses **Sonnet 5** with the **$2/$10 promo price** as the default worker (cite the promo window).
2. Adds a **prompt-cache-first prompt template** (static context at the top).
3. Adds a **Chinese-model fallback path** (GLM 5.2 via OpenRouter) for eval/non-critical steps — with a **cost delta table** and a one-paragraph note on **when *not* to route offshore** (data-residency, IP, export controls).
4. Publish + LinkedIn post it, tagged `#AIIntegrationEngineer`. **This artifact now answers four interview questions in one repo**: orchestration, verification-against-real-tools, cost-routing, and data-governance.

## Watchlist deltas

- 🆕 **Anthropic > OpenAI (revenue + secondary valuation):** new thread — track whether this holds through the OpenAI IPO S-1 window ([2026-05-22/01 §2](../2026-05-22/01-big-lab-moves.md#2-openai-s1)) and how the OpenAI–SWF proposal changes the pitch.
- 🆕 **Anthropic × TeraWulf $19B / 401 MW / KY:** new thread — first-power **late 2027**. Watch for parallel Anthropic infra deals; the Google/Broadcom **3.5 GW** TPU deal from April is the other half of this map.
- 🆕 **OpenAI → US sovereign wealth fund (5%, ~$42.6B):** new thread — if extended and accepted, changes **every** AI-lab's cap table + creates a **public-benefit AI stake** that could reshape the "join a frontier lab" risk/reward.
- 🆕 **Chinese open-weight enterprise share (30–46%):** new thread — track Ramp AI Index confirmation, Coinbase-style headlines, and whether the US floats an export/licensing response.
- 🆕 **Taktile $110M / agentic-fintech decision layer:** new thread — the FDE/Integration lane in banks/insurers just gained a well-funded reference customer.
- 🆕 **JADEPUFFER / first agentic ransomware:** new thread — the **agentic-SOC** hiring lane ([2026-05-22/02 §2 Exaforce](../2026-05-22/02-new-emerging.md#2-exaforce)) just got a demand-side proof point.
- ➡️ **Anthropic profitability + IPO path:** still live from 2026-05-21/22 — the >$30B run-rate compresses the timeline.
- ➡️ **OpenAI confidential S-1 / Sept 2026 IPO:** still live from 2026-05-22 — SWF proposal is the political countermove.
- ➡️ **Karpathy → Anthropic pre-training team:** still live from 2026-05-22.
- ⬇️ **Trump AI executive order:** still stalled since 2026-05-22; the SWF pitch is now the more likely policy vehicle.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Anthropic-crossover in [`01` §1](./01-big-lab-moves.md#1-anthropic-crossover) + Chinese-cost item in [`02` §1](./02-new-emerging.md#1-china-cost) |
| 20 min | [`03` §1 cost-router stack](./03-practical-skills-and-tools.md#1-cost-router-stack) — set it up today, get the promo pricing while it's live |
| Today | [`05` §2 reprice: "reference lab" flipped](./05-career-and-startup.md#2-reference-lab) — update your target-company ordering |
| This weekend | [`04` §1 AgenticDataBench + BuilderBench](./04-research-progress.md#1-agent-evals) — pick one to reproduce and post about |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
