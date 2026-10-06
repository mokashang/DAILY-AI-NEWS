# Career & Startup — 2026-10-02

Three re-prices this week: **salary data crystallized** (frontier labs now $300–795K median TC); **the "persistent agent architect" lane opened** (zero-population job title, Q4 hiring wave); **"model-current fluency" fell to zero** (Argon took the Vals crown 30 days after Fable 5.1 took it). Your Friday action list is tight and ships this weekend.

Tags: `#careers #salary #hiring #startups #playbook #fde #mle`

---

## 1. The Q4 2026 salary + hiring map {#1-salary-map}

**What crystallized this week:** Four 2026 salary trackers (Interview Kickstart, 365 Data Science, Kore1, Signify, Axial Search) published updated numbers, and FinalRound published its Q4 state-of-the-market. The pattern is now stable enough to treat as planning data.

### Headline numbers (US, 2026 Q4)

| Role | Base (median) | TC (median) | Top-tier (frontier labs) |
|---|---|---|---|
| **AI Engineer (generalist)** | $134K–$193K | **$242K** | **~$795K median at OpenAI** |
| **MLE (generalist)** | $148K | $212K | **$290K–$490K** (Anthropic) · **$430K** (Meta) · **$290K** (Google) |
| **MLE (entry, 0–2 YOE)** | $90K–$135K | $115K–$160K | $250K–$350K (frontier labs, with equity) |
| **MLE (senior, 5+ YOE)** | $180K–$280K | $350K–$550K | $600K+ |
| **AI Engineer (LinkedIn Gen-Z/millennial median base)** | — | **$166K** | — |

### Market structure facts

- **AI/ML engineer talent shortage: 63%.** **500K+ open roles globally.**
- **Generalist SWE roles down 25% from 2023 peak.** The split from AI/ML roles is now structural, not seasonal.
- **70% of ML-engineering postings are mid-level/senior IC.** Only **2% Director+**. This is a **flat org-chart hiring market** — meaning IC craftsmanship still wins, management ladder is bottlenecked.
- **ML postings keep climbing QoQ** — no seasonal softening heading into year-end.
- **Geo premium**: SF, NYC, Seattle at **+25-40% national median**. Remote at parity or small discount.

### The "fastest-growing AI roles" shortlist (2026)

Per Open Data Science + HeroHunt + FutureProofing:

1. **AI Engineer / AI Integration Engineer** (your lead lane; see [ME.md](../ME.md#current-focusing-decision-re-evaluate-monthly))
2. **MLE** (traditional ML production)
3. **FDE / Forward-Deployed Engineer / Solutions Engineer** (frontier labs + Palantir/anthropic-adjacent)
4. **Persistent Agent Architect** (brand new post-DevDay; see §2 below)
5. **Memory Systems Engineer** (post-DolphinBench; see [`04` §1](./04-research-progress.md#1-memory-wave))
6. **Model Router / Decisions-API Engineer** (post-OpenAI DevDay)
7. **MCP Server Author / Infrastructure Engineer** (post-Agentic AI Foundation)
8. **Pre-deployment Eval / AI Assurance Engineer** (re-opened by the Amodei+Altman pacing truce)

**Sources:**
- [Interview Kickstart — Machine Learning Engineer Salary 2026](https://interviewkickstart.com/blogs/articles/machine-learning-engineer-salary) `[aggregator]`
- [Axial Search — The State of the ML Engineering Job Market in 2026](https://axialsearch.com/insights/ml-engineering-jobs) `[analysis]`
- [FutureProofing — AI Engineer Salary Trends 2026: Ranges & Premiums](https://www.futureproofing.dev/resources/ai-talent-gap/ai-engineer-salary-trends) `[analysis]`
- [365 Data Science — MLE Job Outlook 2026: 1,000+ Postings](https://365datascience.com/career-advice/machine-learning-engineer-job-outlook/) `[analysis]`
- [Signify Technology — MLE Salary Benchmarks (US Market 2025-2026)](https://www.signifytechnology.com/news/machine-learning-engineer-salary-benchmarks-us-market-2025-2026/) `[analysis]`
- [Kore1 — ML Engineer Salary 2026: $128K–$186K Base by City & YOE](https://www.kore1.com/ml-engineer-salary-guide/) `[analysis]`
- [HeroHunt — Fastest Growing AI Roles in 2026](https://www.herohunt.ai/blog/fastest-growing-ai-roles-in-2026-data-and-rankings/) `[analysis]`
- [FinalRound AI — Software Engineering Job Market 2026](https://www.finalroundai.com/blog/software-engineering-job-market-2026) `[analysis]`
- [Open Data Science — The 12 Most In-Demand AI Job Roles in 2026](https://opendatascience.com/12-in-demand-ai-job-roles-2026-how-to-get-hired/) `[analysis]`
- [Cadence — ML engineer salary in 2026](https://cadence.withremote.ai/blog/ml-engineer-salary-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Your Q4 2026 apply list, re-ranked by **(underpopulation × TC × fit with ME.md)**:
  1. **Anthropic Solutions / FDE / Integration** — IPO-pre-roadshow hiring surge is coming, target an Oct 20 application window to be in the pre-S-1 queue.
  2. **OpenAI Dot Infrastructure Engineer** — brand new job family, 0 established candidates.
  3. **Google Vertex AI / Antigravity 2.0** — the Argon release opens a hiring wave; Vertex Agent Platform PM/eng especially.
  4. **8090 Solutions** ([`02` §2](./02-new-emerging.md#2-funding)) — Series-A momentum + Salesforce-adjacent FDE lane.
  5. **Sail Research** — if you want infra lane; small team, large funding, builds exactly the primitive your router v2 would benefit from.
  6. **Pre-deployment eval** (Anthropic AI Safety Fellowship, OpenAI Safety hires, UK AISI, US CAISI) — reopened by the pacing truce.
- **Startup lens:** The flat org-chart market says one specific thing to you: **the IC-craft bar is higher than the manager bar**. Interviewers want the artifact, not the title. Your weekend router-v2 + MEM-1 ship IS your resume for the next 12 weeks.
- **Insight:** The $795K OpenAI median is a *selection* number, not a *target* number — it reflects the exceptional-only hires OpenAI makes. The useful planning number is the **$300–490K Anthropic range**, which is the realistic range for a CS-grad entering in a specialist AI-Engineer lane with 1–2 portfolio artifacts. Plan comp conversations around that number.

---

## 2. The skill re-price of the week {#2-reprice}

### Up (invest this weekend)

1. **Persistent-Agent Architecture** — ship a Dot (or Managed Agents or Antigravity equivalent). The job title doesn't exist yet; whoever has a public artifact in the lane in Q4 2026 will be interviewed by every major lab in Q1 2027.
2. **Memory Eval Authoring** — DolphinBench-style memory evals ([`04` §1](./04-research-progress.md#1-memory-wave)). Author a new case this weekend.
3. **Multi-Model Routing** — Router v2 is the single highest-leverage portfolio artifact of Q4 2026 ([`03` §1](./03-practical-skills-and-tools.md#1-router-v2)).
4. **MCP Hosted-SaaS Pattern** — OAuth 2.1 + streamable HTTP opens the SaaS-MCP-server pattern ([`03` §2](./03-practical-skills-and-tools.md#2-claude-code-mcp-mature)).

### Flat (maintain)

- Prompt engineering (now expected baseline, not differentiating).
- MCP server authorship basics (shipped it in May; still earning).
- Standard eval authoring (now expected baseline; the differentiator is **memory evals**).

### Down (deprecated this week)

1. **"Which lab is winning" fluency** — Argon #1 for ~30 days max; the question is unanswerable at the top.
2. **"Latest model knowledge" as a resume line** — do not list specific model versions; they're stale in 30 days.
3. **Single-vendor expertise (prompt-tuned on Opus)** — the market is now four frontier models within noise distance. Multi-vendor fluency IS the floor.

### Why it matters to you

- **Job lens:** The 4 "up" items ladder exactly into the 8 "fastest-growing roles" above (§1). Pick one artifact → one role → one company → one outreach a week.
- **Startup lens:** The "up" items are also your startup wedge shortlist. Persistent-agent architecture + memory eval + routing are three independent $5–10M-ARR wedges, each individually buildable in 6 months.
- **Insight:** The up/flat/down framing holds a lesson: **the deprecated skills were the ones that depended on labs standing still.** The durable skills depend on **comparing** labs (routing, eval), **composing** them (persistent agents, memory), or **grading** them (eval authoring). Build in the compositional + comparative lanes; those don't deprecate on the next model release.

---

## 3. Your Friday → weekend action list {#3-actions}

Published separately in [ACTIONS.md](../ACTIONS.md) but here as a self-contained plan:

### Tonight (90 min)

- [ ] Ship **Router v2** to GitHub with Argon + Sol in the table and the 5-case eval re-run. ([`03` §1](./03-practical-skills-and-tools.md#1-router-v2))
- [ ] Tweet / LinkedIn-post the router v2 PR with the scoreboard screenshot.

### Saturday (3 hours)

- [ ] Add the **MEM-1 case** (DolphinBench-inspired) to the router eval. ([`03` §3](./03-practical-skills-and-tools.md#3-memory-lane))
- [ ] Migrate your Claude Code setup to **deferred tool loading** + install the 6-skill shortlist. ([`03` §2](./03-practical-skills-and-tools.md#2-claude-code-mcp-mature))
- [ ] Read **DolphinBench abstract + methodology** (25 min).

### Sunday (2 hours)

- [ ] Draft one **500-word post** comparing **Dots vs Managed Agents vs Antigravity-managed-agents** (persistent-agent primitives). ([`02` §3](./02-new-emerging.md#3-dots-primitive))
- [ ] Apply to **2 FDE / AI Engineer roles**: one at Anthropic (pre-IPO hiring surge), one at 8090 Solutions or a frontier lab.
- [ ] Pre-stage your **Anthropic application for Oct 20** (to be in the pre-S-1 queue before mid-November roadshow).

### This week (ongoing)

- [ ] DM 3 current Anthropic engineers to be in the first-wave alumni-founder network when the IPO lands.
- [ ] Add **"persistent-agent architecture"** to your LinkedIn headline (0 competitors in your search area in Q4 2026).
- [ ] Monthly AI-spend audit (your personal rule, 4th of month — this is Oct 4).

→ Cross-link: [ME.md focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly) · [`03` §1 Router v2](./03-practical-skills-and-tools.md#1-router-v2) · [`04` §1 memory wave](./04-research-progress.md#1-memory-wave).
