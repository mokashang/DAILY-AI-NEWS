# Career & Startup — 2026-11-11

The 28 days moved the career map in two directions at once. **Up:** eval-authoring (trajectory-level now shipping as a product at Arize / Langfuse / DeepEval), model-router design (4D tunable: model × effort × fast-mode × cache), MCP-with-security authoring (10K servers, "wrap an API" is over), cyber-defender adjacency (Mythos 5.2 + Gemini 4 Argon both gate on verified defender status), and the brand-new **pre-IPO disclosure engineering** lane at Anthropic. **Down:** single-vendor coding fluency (the Nov 12 Cursor cutoff is Exhibit A), raw prompting, and the AI/ML pay premium itself — **1.29× non-AI, down from 1.34×** per FutureProofing's Levels.fyi analysis.

Tags: `#careers #startups #fde #mle #sde #router #mcp #cyber #ipo #compensation`

---

## 1. The skill re-price (28-day update) {#1-reprice}

### Priced UP

- **Trajectory-level eval authoring + layered LLM-judge eval.** Arize now ships agent trajectory evaluators as a first-class product; Langfuse, DeepEval, and OpenAI Evals all moved in the same direction in Oct. The frame has shifted from **"final-answer accuracy"** to **"did the trajectory stay on-rail, cost-stable, and reversible."** SWE-bench Verified is explicitly called out as no longer a frontier metric. **If your MCP server portfolio can emit a trajectory trace that a judge model scores on cost + reversibility + grounding, you are in demand.**
  - Sources: [Arize trajectory evaluators](https://arize.com/docs/ax/evaluate/agent-trajectory-evaluations) · [Morph LLM eval guide](https://www.morphllm.com/ai-agent-evaluation) · [Splunk: SWE-bench not a deployment gate](https://www.splunk.com/en_us/blog/artificial-intelligence/agent-evaluation-framework.html)

- **Model-router design with two-dimensional pricing.** Fable 5.2's **Fast Mode at 2× standard rate** plus Haiku 5.5 effort levels plus cached vs standard pricing = the router now decides across **(model × effort × fast-mode × cache state)**. **The "which Claude / which effort / which lane" matrix is the interview-differentiator of Q4 2026.**
  - Sources: [Implicator: Fable/Mythos 5.2 price cut](https://www.implicator.ai/anthropic-fable-5-2-mythos-5-2-price-cut/) · [SDTimes: Fable 5.2 release](https://sdtimes.com/ai/anthropic-introduces-claude-fable-5-2/) · [`03` §4](./03-practical-skills-and-tools.md#4-haiku-effort-levels)

- **Pre-IPO disclosure engineering / ESG-safety reporting.** **Anthropic's public S-1 (Oct 26, ticker ANT, Nasdaq; debut week of Nov 16)** opens a brand-new career lane this week: engineers who can translate model-capability evidence into **prospectus-safe disclosures**, risk-factor language, and S-1-amendable eval reports. Watch Anthropic Policy, Research-Governance, and ESG-engineering postings in the next 30 days.
  - Sources: [PPC.land: Nasdaq ANT filing](https://ppc.land/anthropic-files-for-nasdaq-ipo-with-16-3bn-in-first-half-revenue/) · [Yahoo/Benzinga](https://finance.yahoo.com/markets/stocks/articles/anthropic-files-confidential-1-1-181246257.html) · [sec-api.io S-1 analysis](https://sec-api.io/insights/anthropic-ant-s-1-ipo-sec-filing-analysis) · [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo)

- **MCP server authoring with security / governance built in.** MCP crossed **10,000 active public servers and 97M monthly SDK downloads**; **41% of enterprise software orgs have MCP in limited-or-broad production.** The surviving MCP niche is **controlled access to secure resources** — a server that gates a sensitive data source with a per-tool audit log is worth more in Nov 2026 than a generic "expose a REST API over MCP."
  - Sources: [Simon Willison 10-22](https://simonwillison.net/2026/sep/20/hn-49779718) · [Stacklok: State of MCP 2026](https://stacklok.com/resources/state-of-mcp-in-software-2026/) · [Nordic APIs: 10 MCP stats](https://nordicapis.com/10-interesting-mcp-statistics/) · [`03` §5](./03-practical-skills-and-tools.md#5-mcp-at-10k)

- **Cyber-defender adjacency.** Google **Gemini 4 Argon (Sept 30)** locked to **Fairwind Program** (cyber-defenders only); **Anthropic Mythos 5.2** gated through three-tier Cyber Verification Program. **"Are you a verified cyber-defender org?" is now the access criterion for frontier capability.** The adjacent move: get into a **Tier-1 CVP partner (CrowdStrike / Palo Alto / Dragos / Nozomi)** *this quarter* — hiring surface shipping ahead of OpenAI's and Anthropic's direct Solutions pipelines.
  - Sources: [Decrypt: Gemini 4 Argon cyber-top](https://decrypt.co/379784/gemini-4-google-flagship-tops-ai-models-cybersecurity) · [InfoWorld: Argon trusted-few](https://www.infoworld.com/article/4229615/google-makes-gemini-4-ai-model-available-to-a-trusted-few.html) · [`01` §4](./01-big-lab-moves.md#4-gemini-4-argon)

### Priced DOWN

- **Single-vendor coding-agent fluency.** The **Nov 12 OpenAI → Cursor cutoff** (SpaceX closed Anysphere acquisition Aug 14, OpenAI pulls API 90 days later) is the first real-world vendor-pull in frontier AI and makes "I know Cursor + GPT" weaker as a résumé line. The 2026 Anthropic enterprise coding share is reportedly **54%, up from 42% six months prior** (Menlo Ventures); portfolios that are **vendor-neutral by architecture** (router + MCP-agnostic tooling) price up, portfolios deep in one IDE / one model price down.
  - Sources: [OpenAI blog: Cursor decision](https://openai.com/blog/our-decision-on-cursor-following-its-acquisition-by-spacex) · [Cybernews: cutoff Nov 12](https://cybernews.com/ai-news/openai-cursor-spacex-contract-termination/) · [Menlo via Pasquale Pillitteri](https://pasqualepillitteri.it/en/blog/github-copilot-cursor-claude-code-ai-coding-showdown-2026) · [`01` §3](./01-big-lab-moves.md#3-openai-cursor-cut)

- **Raw prompting / "which model" fluency.** Fable 5.2 at $8/$40 + 2× Fast Mode + Haiku 5.5 effort levels = model-choice has become a 4-dimensional tunable, and the question "which Claude for X" is further deprecated. Interviewers want the **router**, not the prompt. Cross-ref: [2026-10-14/05 §1](../2026-10-14/05-career-and-startup.md).

- **AI-engineer salary premium (compressing).** FutureProofing's Levels.fyi analysis: AI/ML premium at **1.29× non-AI engineers, down from 1.34×** — still a premium, gap closing as more SWEs re-skill.
  - Source: [FutureProofing — AI engineer salary trends](https://www.futureproofing.dev/resources/hire-ai-engineer-hub/ai-engineer-salary-trends)

Tags: `#reprice #skills #trajectory-eval #router #mcp #cyber #ipo #compensation`

---

## 2. Apply plan — 2 FDE apps + 3 others this week {#2-apply-plan}

### Primary (submit today, 60 min)

**1. OpenAI — Forward Deployed Software Engineer, Public Sector · Washington DC / Seattle / SF · $255K–$405K base · open**
→ [openai.com/careers/forward-deployed-software-engineer-gov-washington-dc/](https://openai.com/careers/forward-deployed-software-engineer-gov-washington-dc/)

> **One-liner:** "Post-Cursor-cutoff router + MCP server + eval harness demo — the exact artifacts your public-sector deployments will need in Q1 2027."

Why this lane now: Anthropic Pentagon-broken in Oct, Anthropic IPO is a public filing, OpenAI public-sector FDE has the **most predictable demand curve** of any frontier-lab role for the next two quarters.

**2. Anthropic — Solutions Architect, Applied AI (Beneficial Deployments) · SF · $240K–$270K base · open**
→ [jobs.accel.com/companies/anthropic/jobs/70192283](https://jobs.accel.com/companies/anthropic/jobs/70192283-solutions-architect-applied-ai-beneficial-deployments)

> **One-liner:** "I've built an MCP server with trajectory-level evals and a cost-aware router across Fable 5.2 / Haiku 5.5 / Gemini 4 — would love to deploy that playbook into mission-driven orgs."

### Secondary (partner-firm / adjacent, submit this week)

**3. McKinsey QuantumBlack — AI Engineer / GenAI Engineer** — Academy partner (Oct 2 cohort). **Least-crowded path into the Claude Frontier Academy nomination funnel**, which remains nomination-only with first credentials in **early 2027**.
→ [Anthropic Frontier Academy](https://claude.com/programs/frontier-academy) (nomination route)

**4. Deloitte — Integration Engineer II, AI & Engineering · Raleigh hybrid · $101K–$136K · posted 9 days ago** — partner-firm Academy pipeline. Lower band but plugs the Track B path.
→ [ZipRecruiter listing](https://www.ziprecruiter.com/Jobs/Ai-Integration-Engineer/-in-Raleigh,NC)

**5. Palantir — Forward Deployed Engineer, Commercial** — Palantir Q3 printed **U.S. commercial > U.S. government** for the first time, revenue **+96% YoY to $2.31B**, 2026 outlook raised to $8.53B. The **commercial FDE funnel is the single hottest "AI deployment" lane outside the labs right now.**
→ [Fortune Nov 2 — Palantir Q3](https://fortune.com/2026/11/02/palantir-q3-results-stock-ai-trade-selloff/) · [Futurum: US Commercial overtakes](https://futurumgroup.com/?p=97554)

### The 55-minute version (if you only have tonight)

| :00–:15 | OpenAI FDE Gov submit | DC posting (highest band) | Cover lead: Nov 12 Cursor cutoff → vendor-migration portfolio |
| :15–:30 | Anthropic Beneficial Deployments SA submit | SF posting | Cover lead: Post-Cursor Router weekend artifact |
| :30–:45 | Patch public MCP server README | 5-line "Vendor-neutral by design — swap backends via config" | Converts artifact into evidence for apps 1 & 2 |
| :45–:55 | 3 cold emails | (a) McKinsey QuantumBlack / Bain Vector / Deloitte AI Institute AI engineer, (b) Anthropic Solutions Architect (LinkedIn), (c) fal engineer (just raised $1.3B, hiring spike incoming) | One sentence, one artifact link, one specific ask |

Tags: `#apply #fde #solutions-architect #academy #palantir`

---

## 3. Funding / wedge map update {#3-wedges}

### NEW wedges opened (Oct 14 → Nov 11)

**(a) Post-Cursor migration tooling / model-switching infra.** The Nov 12 OpenAI → Cursor cutoff is the loudest "you have one vendor" lesson in a year. **Open the 60–90-day window now** with a drop-in config generator or SaaS that re-routes Cursor-shaped stacks to Fable 5.2 + Gemini 4 fallback + Mythos 5.2 for cyber-sensitive paths. **This is the weekend artifact.** → [`03` §3](./03-practical-skills-and-tools.md#3-post-cursor-router)

**(b) Sovereign AI deployment tooling.** Palantir Q3 explicitly named "sovereign AI" (post-training open-weight models on a customer's own data inside AIP) as the driver of its **96% YoY** growth. Wedge: **post-training + serving-inside-firewall tooling for mid-market (sub-F500) sovereign deployments** — Palantir only covers the top ~150. The gap below is a **$20–50M ARR wedge inside 24 months.**
- Source: [Constellation — Palantir sovereign AI](https://www.constellationr.com/insights/news/palantirs-q3-highlights-enterprise-inflection-point-due-sovereign-ai-llm)

**(c) Agent identity / least-privilege audit as a product.** Mintive (Oct 29) is first in; CB Insights' agentic-AI M&A count hit ~80 in 2025 and runs higher in 2026. **Identity-for-agents** (short-lived credentials, per-tool capability scoping, forensic audit trail) is the layer **MCP left out when it went stateless-core in March.**
- Source: [Agentic AI M&A tracker](https://newmarketpitch.com/blogs/news/agentic-ai-ma-tracker) · [`02` §3](./02-new-emerging.md#3-mintive-agent-identity)

**(d) MCP-security + stateful-session bolt-on.** The March 2026 MCP stateless-core update removed session context from the protocol — enterprise tools still need stateful interaction, so a **session-layer SaaS on top of MCP has a 12-month window** before Anthropic re-absorbs it.
- Source: [Stacklok — State of MCP 2026](https://stacklok.com/resources/state-of-mcp-in-software-2026/)

**(e) Vendor-switch eval harness as a product.** Something between Vals.ai (benchmark leaderboard) and Arize (production trajectory monitor), aimed at CTOs who need a **single number to justify a Claude ↔ GPT ↔ Gemini swap under board pressure.** Gemini 4 Argon's "leads 12-of-18 benchmarks" claim is already contested by Bloomberg — an **independent** harness has credibility to sell.

### Wedges that just got CROWDED / closed

- **Agent observability (crowded, likely closed for a cold-start founder).** Cisco acquired Galileo, Arize + Langfuse + DeepEval are mature, OpenAI Codex Security Cloud absorbs the "just watch my agents" ask. Don't start a company here in Nov 2026 unless you have a wedge below (identity, cost, or security).

- **Voice-AI infrastructure (consolidating).** Deepgram → Daily (Oct 29) brings speech + real-time audio/video together; combined with Wispr Flow's ongoing talks and xAI's STT/TTS GA, the "voice OS" layer has 3 anchors. Found at the wrong level of the stack = crushed.
  - See [`02` §4](./02-new-emerging.md#4-voice-consolidation).

- **Customer-service agents, generalist.** Sierra ($15B / 3 acquisitions in 2026), Decagon ($131M Series C at $1.5B, pricing per resolved ticket), Automation Anywhere → Boost.ai (Oct 7) = **general CS-agent category is priced like mature SaaS.** Vertical-specific CS (trades, logistics, healthcare intake) is still open; horizontal is not.
  - Sources: [Sierra via Neuronfeed](https://neuronfeed.com/category/ai-customer-support) · [Decagon $131M Series C](https://www.eesel.ai/blog/decagon-ai-lands-131m-funding-now-a-top-conversational-ai-startup-valued-at-1-5b) · [CXNetwork Nov 6 roundup](https://www.cxnetwork.com/cx-experience/news/every-cx-start-up-funding-deal-you-need-to-know-november-6)

### Named deals in the window (for the funding watchlist)

See [`02` §1](./02-new-emerging.md#1-funding-barbell) for the Nov 2–6 roundup: fal $1.3B / $16B; Applied Compute $350M / $3.25B; Nooks $500M General Catalyst CVF; Ocient $100M; Automation Anywhere → Boost.ai $1.2B; Salesforce → Loops; Sapiom $35M; Runable $21M; RapidCanvas $29M.

Tags: `#wedges #cursor #sovereign-ai #agent-identity #mcp #evals #crowded`

---

## 4. OSS trending / repo signals (Oct 14 → Nov 11) {#4-oss-signals}

- **D4Vinci/Scrapling** — ~92K stars. Web-scraping framework with built-in MCP server integration. **Signal:** MCP is the default distribution channel for infra tools now — if you're building a dev tool, ship an MCP adapter from day one.
- **DeusData/codebase-memory-mcp** — ~32K stars. Codebase-memory server for coding agents. **Signal:** memory + retrieval is the next layer above "call-a-tool."
- **github/github-mcp-server** — 19,809 stars (+136 recent). **Microsoft/playwright-mcp** — 18,635 stars (+289 recent). **Signal:** **first-party vendor MCP servers** are the pattern worth cloning — pick a product you'd fund, ship the MCP server for it before they do, publish, get the maintainer-handoff conversation.
- **Pattern-level observation (OSS Insight July → November):** center of mass is shifting from "list a tool" → **"remember state + bound scope."**

**What each tells you:** build at the **stateful + bounded** layer of MCP, not the "wrap an API" layer. Publish early; the land-grab hasn't closed.

Sources:
- [CoddyKit — OSS roundup](https://www.coddykit.com/pages/blog-detail?id=5130015) `[aggregator]`
- [OSS Insight live MCP ranking](https://ossinsight.io/trending/ai) `[aggregator]`

Tags: `#oss #github #mcp #memory #vendor-mcp`

---

## 5. New comp data in-window {#5-comp-data}

**Named postings:**
- **OpenAI Forward Deployed SE, Public Sector — DC:** **$255K–$405K** base. [Posting](https://openai.com/careers/forward-deployed-software-engineer-gov-washington-dc/)
- **Anthropic Applied AI Architect, Industries — NY:** **$240K–$315K** base. [Mirror](https://www.indexventures.com/startup-jobs/anthropic/applied-ai-architect-industries/)
- **Anthropic Solutions Architect, Applied AI (Beneficial Deployments) — SF:** $240K–$270K base.
- **Anthropic Recruiting Solutions Engineer — SF:** $270K flat (posted July 21).
- **Peraton Data & AI Integration Engineer (TS/SCI cleared):** $119K–$143K (Reston VA).
- **Deloitte Integration Engineer II, AI & Engineering:** $101K–$136K hybrid (Raleigh).
- **LightEdge Sr. AI Integration Engineer:** $97K–$131K (Lenexa KS).

**Market medians:**
- Base avg **$184,757** / total **$211,243** (Built In).
- noon.ai job-posting median base **$215K** / average base **$227K**.
- Levels.fyi self-reported median total comp **$211K** (9,500+ profiles).
- Senior remote median **~$206,600** (KORE1).
- **Frontier-lab medians: OpenAI $635K TC, xAI $665K TC.**
- **AI/ML-engineer premium: 1.29× non-AI (compressing from 1.34×).**

**Layoff context:**
- Challenger: tech-sector cuts **139,156 in H1 2026 (+83% YoY), 23% AI-cited.**
- Layoffs.fyi: **36% of 2026 layoffs AI-driven (up from 16% in 2025).**
- **Meta: 600 AI-unit cuts announced Oct 22, Nov 21 termination date** — Zuckerberg told staff "no more company-wide layoffs in 2026," suggesting selective cuts continue.

Sources:
- [ThirstySprout — AI engineering salary](https://www.thirstysprout.com/post/ai-engineering-salary) `[analysis]`
- [noon.ai — 52 AI compensation benchmarks 2026](https://www.noon.ai/blog/articles/52-ai-compensation-benchmarks-2026) `[analysis]`
- [FutureProofing — pay-trend](https://www.futureproofing.dev/resources/hire-ai-engineer-hub/ai-engineer-salary-trends) `[analysis]`
- [Compare the Cloud — 90K AI-driven layoffs](https://www.comparethecloud.net/news/ai-drove-more-than-half-of-2026s-tech-layoffs-as-oracle-amazon-and-meta-lead-a-90000-job-wave) `[secondary]`
- [Outlook — Meta 600 AI cuts Nov 21](https://www.outlookbusiness.com/corporate/meta-to-cut-600-ai-jobs-months-after-billion-dollar-hiring-spree) `[secondary]`
- [People Matters — Meta "no more company-wide"](https://www.peoplematters.in/news/strategic-hr/meta-promises-no-more-company-wide-layoffs-in-2026-after-cutting-8000-jobs-49864) `[secondary]`
- [Dice — AI jobs on LinkedIn's fastest-growing 2026 list](https://www.dice.com/career-advice/ai-related-jobs-top-linkedins-fastest-growing-roles-list-for-2026) `[secondary]`
- [Ramp AI Index](https://ramp.com/data/ai-index) `[primary monthly tracker]`

Tags: `#comp #frontier-lab-tc #fde #integration-engineer #layoffs #meta`

---

## Action for this Wednesday (60 min)

→ **Submit 2 apps + ship one portfolio patch + 3 cold emails, before 11:59 PM PT.** Table in [§2 above](#2-apply-plan).

## Weekend artifact (one thing to ship)

→ **"Post-Cursor Router"** — public GitHub repo, published by Sunday night, **tweet scheduled for Mon Nov 16 9 AM PT (rides the Anthropic IPO debut news cycle).** Spec in [`03` §3](./03-practical-skills-and-tools.md#3-post-cursor-router). **Three loops closed in one artifact:** Cursor-migration wedge, vendor-neutral router story, eval-authoring skill demo.

---

## Watchlist deltas vs 2026-10-14

### NEW threads to add

- 🆕 **Anthropic IPO public filing (ticker ANT, Nasdaq).** S-1 Oct 26, debut target week of Nov 16, raising **$100B+ at $1.5T–$2T**. $33.24B revenue 9 months through Sept 30. Watching: pricing range, first-day pop, lock-up schedule, **Pentagon-break disclosure language**, T&S / Research-Governance hiring spike post-listing.
- 🆕 **Fable 5.2 + Mythos 5.2 price cut (Nov 9).** $8/$40 per 1M (-20%), cached $0.20, Fast Mode 2×. Watching: whether OpenAI / Gemini match within 30 days; whether Fast Mode becomes a routing primitive separate from effort level.
- 🆕 **OpenAI → Cursor termination (Nov 12 — tomorrow).** First real vendor pull in frontier AI; watching for "vendor-neutral by contract" procurement requirements in F500 RFPs.
- 🆕 **fal $1.3B Series F / $16B valuation.** AI-inference infra consolidation; watching Replicate / Together / Modal / Fireworks responses.
- 🆕 **Gemini 4 Argon locked to Fairwind.** Access-tier-gating as the new norm for frontier models; watching whether Fairwind opens beyond cyber by Q1 2027.
- 🆕 **Skills → Plugins Enterprise cutover Nov 30.** 19 days; silent fail if admin doesn't toggle.
- 🆕 **Meta 600 AI-unit cuts (Nov 21 term date), TD Lab spared.** Watching: where Meta rehires; whether "no more company-wide layoffs in 2026" commitment holds.
- 🆕 **Palantir sovereign AI narrative (Q3 2026).** US commercial > US gov for the first time; watching for sub-F500 sovereign-deployment wedge activation.
- 🆕 **MCP at 10K servers / 97M monthly SDK downloads.** Watching: stateful-session bolt-ons, security-tier MCP servers, whether Anthropic ships an official stateful-session extension by Q1.
- 🆕 **Microsoft Ignite Nov 17–20 + Autopilot pricing.** The $/seat that re-prices the agent-runtime market.
- 🆕 **NVIDIA Q3 FY27 earnings Nov 17 or 18.** Consensus $108–109B; capex-thesis pivot point correlated with Anthropic IPO pricing.

### Threads to CLOSE / supersede

- 🟢 **Anthropic confidential S-1 → public S-1 (Oct 26).** [Supersedes the 2026-05-22 confidential-filing row.]
- 🟢 **Code w/ Claude San Francisco + London + Tokyo (May–June 2026) — concluded.**
- 🟢 **Haiku 5.5 (Oct 7):** keeps the worker tier but superseded upward by Fable 5.2.

### Threads to ESCALATE

- ⬆️ **Model-fluency as tunable, not a choice.** Effort levels (Haiku 5.5) + Fast Mode (Fable 5.2) + cached pricing + sub-tier access = 4D routing. Highest-return skill for Nov–Dec 2026.
- ⬆️ **FDE partner-firm Academy track.** Still nomination-only; first credentials early 2027. Watching: self-apply window, cohort stats, whether partner firms publish "Academy-eligible" badges.
- ⬆️ **Pentagon-break knock-on into OpenAI / xAI public-sector hiring.** OpenAI Public Sector FDE band ($255K–$405K) is the directly observable consequence.
- ⬆️ **MCP authoring recipe:** stateful + bounded + audited is the new bar.

### ACTIONS.md updates (this week's apply tasks)

1. Submit **OpenAI Forward Deployed SE, Gov (DC/Seattle/SF)** — Wed night.
2. Submit **Anthropic Solutions Architect, Applied AI (Beneficial Deployments)** — Wed night.
3. Submit **McKinsey QuantumBlack / Deloitte AI Integration Engineer II** — Thu.
4. Submit **Palantir FDE, Commercial** — Fri.
5. **Patch public MCP server README** with vendor-neutral + audit-log + short-lived-cred callouts — tonight.
6. **Ship Post-Cursor Router repo + Show HN + schedule tweet for Mon 9 AM PT** — Sat–Sun.
7. **3 cold emails** per the Wed template — Wed.
8. **Admin check:** confirm Skills = ON in Claude org settings (or ping admin) before Nov 30.
9. **Calendar block Microsoft Ignite Nov 17–20** and **NVIDIA Q3 FY27 earnings Nov 17/18** — both inside Anthropic IPO pricing week.

---

## Thread status snapshot vs 2026-10-14

- **Frontier Academy (Oct 2):** 🟡 holding — no cohort stats yet.
- **Pentagon break (Oct 5):** 🔴 stalled publicly — disclosure item in S-1.
- **Haiku 5.5 (Oct 7):** 🟢 superseded by Fable 5.2.
- **Cyber Mission (Oct 8):** 🟢 extended — Mythos 5.2 flows through CVP tiers.
- **Singapore (Oct 14):** 🟡 holding — post-IPO APAC hiring curve starts after listing.
- **Usage Policy (effective Nov):** 🟢 in effect.
