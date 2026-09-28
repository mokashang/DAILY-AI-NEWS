# TL;DR — 2026-09-27 (Sunday)

Sixty-second skim. **Sunday review of the week the frontier flipped to price + governance + tenant-fabric — and setup for a T-2 that could redraw the map again.** Between **Mon Sept 21** and **Sat Sept 26**, five converging stories landed: (1) **the price collapse** — [Opus 5.5 + GPT-6 Sol/Luna, Sept 22](../2026-09-24/01-big-lab-moves.md) — the pacing coalition failed inside 20 days; (2) **Claude did science** — [novel enzyme discovery, Sept 23](../2026-09-24/01-big-lab-moves.md#3-anthropic-biolab), Feng Zhang endorsed; (3) **the UN gavel** — [Amodei + Altman at the Security Council](../2026-09-24/01-big-lab-moves.md#4-un-security-council); (4) **Dreamforce week** — [AIforce + Claudeforce + Autopilot + Agent 365 + Muse Charm + Qwen −95%](../2026-09-26/01-big-lab-moves.md); (5) **the S-1 window narrowed to end-of-September**. **This coming week: T-2 to OpenAI DevDay (Tue Sept 29, Fort Mason SF); T-3 to Anthropic's public S-1 window close; T-3 to California SB 1047 signature deadline (Wed Sept 30 23:59 PT — Newsom's decision on the 10^26-FLOP + $100M-compute frontier-model bill).** For you: **finish the router-to-MCP shim from yesterday, ship it publicly today, and stage a router-diff for whatever DevDay drops on Tuesday.**

---

1. **Sunday synthesis — 5 converging stories, one frame.** The frame that ties this week together: **the frontier moved from *shipping models* to *shipping surfaces*.** Opus 5.5 + Sol/Luna were the last "just a new model" launches of the quarter; Dreamforce/Autopilot/Muse Charm/Qwen −95% were about **whose surface holds the customer**. → [`01` §1](./01-big-lab-moves.md#1-week-synthesis) `#recap #labs #agents #surfaces`

2. **T-2 to OpenAI DevDay (Tue Sept 29, Fort Mason SF).** The consensus watchlist (per [2026-09-20 predictions doc](../2026-09-20/03-practical-skills-and-tools.md)): GPT-6 tier extensions, agent runtime deltas, Sponsored Agents metrics update, Codex feature parity with Claude Code, and — most importantly for you — **DevDay's answer to Autopilot + Agent 365** (the governance-fabric layer Microsoft owned this week). → [`01` §2](./01-big-lab-moves.md#2-devday-t2) `#openai #devday #agents #governance`

3. **T-3 to California SB 1047 signature deadline (Wed Sept 30 23:59 PT).** Newsom's decision on the *Safe and Secure Innovation for Frontier AI Models Act*. Applies to models trained with **>10^26 FLOPs AND >$100M in compute**. Pre-training safety protocol, shutdown capability, third-party audits (SB 813 + AB 1405 auditor registry already signed Sept 9), whistleblower protections. **Either outcome creates a hiring signal** — signature accelerates lab-internal AI-safety-eval hiring; veto pushes the same energy into the federal EO redraft. → [`01` §3](./01-big-lab-moves.md#3-sb-1047) `#policy #california #sb1047 #compliance`

4. **T-3 to end of the Anthropic public-S-1 window.** [Sept 26 update](../2026-09-26/01-big-lab-moves.md#3-anthropic-s1) narrowed the public-filing window to end of September (first-trade target October per [Sept 23 slip to November list](../2026-09-23/01-big-lab-moves.md#4-anthropic-ipo-slip); revenue trajectory $9B → $65B → $110B+ modeled). Read it the day it lands: segment revenue mix, Claude Code line item, risk factors (esp. the Sept 18 Sherman-Act suit disclosure), international split. → [`01` §4](./01-big-lab-moves.md#4-anthropic-s1-window) `#anthropic #ipo #public-markets`

5. **This weekend's ship: the router-to-MCP shim + 6 governance primitives.** If you did [Saturday's project](../2026-09-26/03-practical-skills-and-tools.md#1-router-shim), publish the repo + LinkedIn carousel today; if you didn't, this is a 3-hour build. Include Opus 5.5 + GPT-6 Sol/Luna + Batch-tier routing branches. Add the 6 governance primitives (tenant identity · scoped delegation · audit log · cost cap · tool allowlist · rate-limit ceiling) so the artifact reads as "agent-in-prod-ready," not just a demo. → [`03` §1](./03-practical-skills-and-tools.md#1-publish-router) `#weekend #router #mcp #governance #portfolio`

6. **Weekend research read: DolphinBench + Jev-Mem synthesis.** The [Sept 26 agent-memory-eval canon](../2026-09-26/04-research-progress.md) — **DolphinBench (arXiv 2609.24971)** + **Jev-Mem (2609.23986)** + **MemCalib (2609.24259)** + **EverMemBench (2602.01313)** — is now the reading list. Read DolphinBench closely, skim the other three, ship a **500-word `NOTES-dolphinbench.md`** to your portfolio repo. Time budget: 90 minutes total; ROI: senior-agent-eng interview answer for the rest of Q4. → [`04` §1](./04-research-progress.md#1-memory-eval-synthesis) `#arxiv #agents #memory #weekend`

7. **Career reprice check-in.** The trio that held all week: **routing + eval-authoring + MCP-server author-experience** = the sub-$300K skills; **agent governance (identity + audit + allowlist + cost-cap)** = the $300K+ premium tier; **AI safety evaluation (SB 1047-shaped)** = the emerging Q4 lane. Update LinkedIn headline to: `AI Integration Engineer · Anthropic-stack · MCP + agent governance` (per [Sept 26 recommendation](../2026-09-26/05-career-and-startup.md#2-integration-lane)). → [`05` §1](./05-career-and-startup.md#1-reprice-check) `#careers #reprice #linkedin`

8. **Weekly rollup thread — the 5 stories that mattered this week.** Per the [`weeks/`](../weeks/) folder convention, this Sunday's rollup: (a) Price war → routing artifact; (b) Claudeforce + Autopilot → tenant-fabric era; (c) Amazon Seller Central agents → marketplace-agent thesis; (d) Anthropic biolab + ART discovery → AI-for-science lane; (e) DolphinBench + Jev-Mem → memory-eval canon. → [`05` §2](./05-career-and-startup.md#2-weekly-rollup) `#recap #weekly`

---

## One thing to DO this Sunday

→ **Publish the router-to-MCP shim + governance primitives + a `NOTES-dolphinbench.md` — all three, before Monday morning.** Router repo: GitHub with README, 5-case eval, price/quality plot, and the 6 governance primitives wired in. LinkedIn: single carousel: `problem → primitives → demo gif → eval table → link`. `NOTES-dolphinbench.md`: 500 words in the same repo. Combined, this is **the artifact triple** that answers every FDE / AI Integration / Solutions interview loop through Q4 2026 — and it primes you to ship a router-diff on Wednesday for whatever DevDay drops Tuesday.

## Watchlist deltas

- 🆕 **California SB 1047 signature deadline Wed Sept 30 23:59 PT:** new thread. Whichever way it goes, AI-safety-eval engineering hiring reprices Monday morning. Companion bills SB 813 + AB 1405 (auditor registry) already signed Sept 9.
- 🆕 **T-2 to OpenAI DevDay (Tue Sept 29, Fort Mason SF):** promoted from [Sept 20 predictions doc](../2026-09-20/03-practical-skills-and-tools.md). DevDay's answer to Autopilot + Agent 365 is the highest-signal watchlist item.
- ➡️ **Anthropic public S-1 (from [2026-09-26](../2026-09-26/01-big-lab-moves.md#3-anthropic-s1)):** T-3 to end of the filing window. Set an SEC alert on `Anthropic` and watch [anthropic.com/news](https://www.anthropic.com/news) for the Monday-morning drop.
- ➡️ **MCP-server cascade (from [2026-09-26](../2026-09-26/02-new-emerging.md#2-mcp-cascade)):** Salesforce + Amazon + Microsoft + Eventtia in 5 days. Watch which mid-cap SaaS ships MCP next 2 weeks (HubSpot / Zendesk / Adobe / Workday are the parity candidates).
- ➡️ **Router artifact + governance primitives (from [2026-09-26](../2026-09-26/03-practical-skills-and-tools.md#1-router-shim)):** ship deadline TODAY (Sunday). Ship late = worthless.
- ⬇️ **"Ship a new model on Sunday":** deprecated. No frontier lab ships weekend releases anymore (the last was Fable 5.1 on Sept 1); model announcements now cluster around DevDay/Dreamforce/Connect windows.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §2 DevDay T-2](./01-big-lab-moves.md#2-devday-t2) + [`01` §3 SB 1047 T-3](./01-big-lab-moves.md#3-sb-1047) |
| 20 min | [`03` §1–2](./03-practical-skills-and-tools.md) — publish the router + governance + notes |
| Today | [`03` §1](./03-practical-skills-and-tools.md#1-publish-router) — ship the artifact triple by 8 PM PT |
| Tonight | [`04` §1](./04-research-progress.md#1-memory-eval-synthesis) — DolphinBench read + `NOTES-dolphinbench.md` |
| Monday AM | Update LinkedIn + submit 3 applications ([`05` §1](./05-career-and-startup.md#1-reprice-check)) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
