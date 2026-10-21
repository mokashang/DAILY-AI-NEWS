# Career & Startup — 2026-09-27

Sunday reprice check + weekly rollup + wedge log refresh. **This week didn't change the trio (routing + eval-authoring + MCP-server author-experience) but added a fourth: agent governance (identity + audit + allowlist + cost cap).** The Wed–Thu axis (DevDay + SB 1047 signature) could add a fifth (AI-safety-eval engineer) by Thursday morning.

Tags: `#careers #reprice #wedges #recap #linkedin`

---

## 1. Sunday reprice check — the 4-item skill stack {#1-reprice-check}

**The current stack** (post-Sept 22 price war, post-Dreamforce/Autopilot/Muse tenant-fabric week):

| Skill | Value trajectory | Current TC band (best proxy) | Why this week |
|---|---|---|---|
| **Model-routing + evals** | ▲ (still climbing) | $180–280K base | Price war = router matters more, not less |
| **MCP-server author-experience** | ▲ (rising fast) | $200–260K base + $30K MCP premium | 5 F500-scale MCP surfaces in 5 days |
| **Agent governance** (identity/audit/allowlist/cost-cap) | ▲▲ (new premium tier) | $260–330K base | Agent 365 + Anthropic Verification make this a first-class discipline |
| **AI safety evaluation** (SB 1047-shaped) | 🟡 pending Wed | $220–320K base at labs; $180–280K at auditors | Wed Sept 30 CA signature deadline |
| **Vertical-agent product engineering** | ▲ | $170–240K base + vertical premium | Claudeforce/Autopilot/Amazon Seller Central all vertical this week |
| **"Latest-model fluency"** | ▼ | Deprecated as a standalone skill | 4 model launches in 30 days — nobody's current |
| **General-purpose AI copilot for X** | ▼ | Deprecated wedge | Microsoft Autopilot subsumes most of it |

**Concrete Sunday-evening actions:**

- **LinkedIn headline:** `AI Integration Engineer · Anthropic-stack · MCP + agent governance` (per [2026-09-26 recommendation](../2026-09-26/05-career-and-startup.md#2-integration-lane)).
- **Skills section:** add / promote **MCP, agent governance, model routing, prompt caching, LangGraph, LangChain, evaluation, tenant identity, audit logging, cost observability.** Delete: any 2024-era generic "AI" tags without a specialty modifier.
- **Portfolio README:** cross-link the router + MCP server + `NOTES-dolphinbench.md` at the top of your GitHub profile.
- **Monday morning 8 AM PT: 3 applications:**
  1. **Anthropic Solutions Engineer / FDE** (multiple current openings; use the S-1-lands narrative as your cover-letter framing).
  2. **Baseten AI Infrastructure Engineer** ($1.5B Series F — active hiring).
  3. **Reach lane:** whichever of {Anthropic AI Safety Fellowship (if open), OpenAI Residency 2027, Google DeepMind Early Career, Isomorphic Applied Research Engineer} matches best.
- **Wed after SB 1047 decides:** add / de-emphasize "AI Safety Evaluation" in headline depending on outcome; either way, keep the vocabulary in the Skills section.

**Sources:**
- [Kore1 — AI Engineer Salary 2026: $145K–$310K (Real Offer Data)](https://www.kore1.com/ai-engineer-salary-guide/) `[analysis]`
- [Motion Recruitment — 2026 Machine Learning Engineer Salary Guide](https://motionrecruitment.com/it-salary/machine-learning) `[analysis]`
- [Robert Half — AI/ML Engineer Salary Updated for 2026](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[analysis]`
- [Uvik Software — AI Engineer Salary 2026](https://uvik.net/blog/ai-engineer-salary/) `[analysis]`
- [Open Data Science — The 12 Most In-Demand AI Job Roles in 2026](https://opendatascience.com/12-in-demand-ai-job-roles-2026-how-to-get-hired/) `[analysis]`
- [Axial Search — AI Engineering Jobs Analysis](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [2026-09-26/05 §2 integration-lane hiring map](../2026-09-26/05-career-and-startup.md#2-integration-lane) `[primary — this repo]`

### Job lens · Startup lens · Insight

- **Job lens:** The 4-item stack is what fits on a LinkedIn headline + About + top-3 portfolio artifacts. That's the *whole* Q4 differentiator; skip any 2024-era generic "AI" keywords.
- **Startup lens:** If you're founding, the same 4 skills define your **team-of-1 competence surface** — you can credibly interview a first hire against them.
- **Insight:** The reprice cycle is now **weekly**, not quarterly. Build the habit of a **Sunday 15-min LinkedIn/README refresh** — cost nothing, keeps your surface area at the frontier.

---

## 2. Weekly rollup — 5 stories that mattered this week {#2-weekly-rollup}

Per the [`weeks/`](../weeks/) folder convention (Sunday rollup), the 5 stories that mattered Sept 21–27:

1. **The price collapse** (Sept 22). Opus 5.5 + GPT-6 Sol/Luna. The pacing coalition died in 20 days. → [`01` §1 recap](./01-big-lab-moves.md#1-week-synthesis) · full detail [2026-09-24](../2026-09-24/).
2. **Claudeforce + Autopilot + Muse Charm — the tenant-fabric week.** F500 UI became optional; agent-in-the-tenant is the new default. → [2026-09-26/01](../2026-09-26/01-big-lab-moves.md).
3. **Amazon opened Seller Central to Claude agents on Bedrock** (Sept 23). Marketplace-agent thesis got a real reference customer. → [2026-09-25/01 §4](../2026-09-25/01-big-lab-moves.md#4-amazon-agents).
4. **Anthropic biolab + ART discovery** (Sept 23). Feng-Zhang-endorsed autonomous scientific discovery — first widely-publicised by a general AI. → [2026-09-24/01 §3](../2026-09-24/01-big-lab-moves.md#3-anthropic-biolab).
5. **The memory-eval canon consolidated** — DolphinBench + Jev-Mem + MemCalib + EverMemBench, 4 papers in 30 days. Memory-as-routing frame hardens. → [`04` §1](./04-research-progress.md#1-memory-eval-synthesis) · [2026-09-26/04 §1](../2026-09-26/04-research-progress.md#1-dolphinbench).

**One thing I'd want you to internalize from the week:** *Q3 2026's biggest story is that the price of the model no longer determines competitive advantage; the surface + the tenant fabric + the eval regime do.* Any career or product strategy still oriented around "which model is best today" is missing the frame — pivot to surfaces and governance.

**Sources:** all internal cross-links above.

### Job lens · Startup lens · Insight

- **Job lens:** In an interview: "the week's frame was the pivot from *models* to *surfaces + tenant fabric*." That single sentence signals you read past the launch headlines.
- **Startup lens:** If you're a founder, the 5-story rollup is your **investor-update-template** for this week. Ship it — investors reward founders who track the frontier at this altitude.
- **Insight:** Weekly rollup as a discipline is a **repeat-Sunday habit** — build it into your ScheduleWakeup or calendar. 20 minutes / Sunday for 12 months = 52 rollups = a portfolio-worthy body of writing.

---

## 3. Wedge log refresh — what's still fundable at seed with 1 design partner {#3-wedge-log}

Ranked by "raiseable at seed with a working demo + 1 design partner":

1. **Community MCP-server for an incumbent that hasn't shipped one yet** — HubSpot / Zendesk / Adobe / Workday (see [`02` §1](./02-new-emerging.md#1-mcp-parity-candidates)). Founder-team-of-1 friendly. High-conviction.
2. **Agent-identity + verifiable-actor layer** — the primitive every marketplace + payments + tenant-fabric primitive needs (see [`02` §2](./02-new-emerging.md#2-agent-primitive-substrate)). Founder-market fit needs a security background.
3. **Memory + governance service** — audit-logged, per-tenant, DolphinBench-shape metrics (see [`04` §1](./04-research-progress.md#1-memory-eval-synthesis)). Under-supplied.
4. **`.claude/`-bundle-as-a-product for regulated industries** — SOC2 / HIPAA / SB-1047-shaped pre-packaged skills+hooks+CLAUDE.md bundles. Founder-team-of-1 friendly.
5. **AI-safety-eval + audit tooling for the SB 813 auditor registry** — customer list is public; product is engineering-tractable. Timing depends on Newsom Wed Sept 30.
6. **RSI-observability tooling** — measurement + regression detection for recursive-improvement loops (see [`04` §3](./04-research-progress.md#3-rsi-wave)). Fits well with an academic ML background.
7. **Model-migration tooling** — auto-port prompt suites + eval suites when the underlying model changes (Opus 5.5 launch made this need concrete).
8. **Vendor-neutral agent governance library** — the counter to Microsoft-Autopilot / Anthropic-Verification-lock-in.

**Concrete Sunday action:** pick **one** wedge that fits your background + circumstances. Draft a 1-page memo (problem, wedge, MVP scope, 1-page competitive map, first design-partner target). Put it in `~/notes/wedges/2026-09-27-<slug>.md`. Sleep on it. If it still reads clean Monday morning, ping 2 mentors + 2 potential design partners.

**Sources:**
- [2026-09-26/05 §3 wedge log baseline](../2026-09-26/05-career-and-startup.md#3-wedge-log) `[primary — this repo]`
- [Blog.mean.ceo — AI Startup Funding News September 2026](https://blog.mean.ceo/ai-startup-funding-news-september-2026/) `[aggregator]`
- [Crunchbase — 10 Biggest Funding Rounds this week](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-robotics-ecommerce-quince/) `[secondary]`
- [Y Combinator RFS 2026](https://www.ycombinator.com/rfs) `[primary]`
- [Air Street Capital — State of AI 2026](https://www.stateof.ai/) `[analysis]`

### Job lens · Startup lens · Insight

- **Startup lens:** Wedges 1 and 4 are the most compatible with a solo grad-student founder — low capital-intensity, clear customer-persona, don't require pre-existing insider relationships. Pick one, ship a working MVP by mid-October. The other 6 wedges better fit team-of-2+ founders with specific relationships.
- **Job lens:** Even if you're not founding, a **wedge memo** in your portfolio proves **you can think like a founder** — a specific hiring signal at Anthropic Solutions, Sierra, Decagon, and any early-stage FDE role.
- **Insight:** The seed-round bar in Q4 2026 is **one paying design partner + a non-flat weekly-active-usage line.** Don't overshoot; get to that bar and raise.

→ Cross-link: [`03` §1 router-and-governance artifact](./03-practical-skills-and-tools.md#1-publish-router) · [`02` §2 agent-primitive substrate](./02-new-emerging.md#2-agent-primitive-substrate) · [`01` §3 SB 1047 T-3](./01-big-lab-moves.md#3-sb-1047).
