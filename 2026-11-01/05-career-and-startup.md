# Career & Startup — 2026-11-01

Three concrete deliverables this week: **(1) apply to the Anthropic Applied AI Engineer, Enterprise req (Oct 20) + the Deloitte Associate GenAI Engineer req that explicitly targets your grad window**; **(2) ship one vertical MCP server by Sunday night**; **(3) read the Anthropic S-1 cover-to-cover the day it hits EDGAR.** The 18-day window re-priced four skills *up* and one *down*. The FDE market is at its 2026 high (**300 live tracked roles on Oct 26**); comp data holds (**Anthropic Applied AI L4–L5 FDE $665K–$750K TC**); Deloitte's new req fits your graduation window exactly; and the Frontier Academy is still nomination-only through the partner-firm path. The S-1 roadshow starts the week of Nov 9 — your pre-IPO equity-opportunity window is **~60–90 days from today.**

Tags: `#careers #fde #skills #s1 #startups #mcp #deloitte #anthropic #applied-ai`

---

## 1. The skill re-price, November edition — "the frontier flipped and the S-1 is public; disclosure-reading becomes a skill" {#1-reprice}

**What re-priced UP this month:**

- **S-1 disclosure reading.** When the Anthropic S-1 hits EDGAR, the Risk Factors + MD&A sections are a 2-hour read that returns more than any specific technical artifact this quarter. Specific to you: it discloses Business API vs. Claude.ai consumer vs. Enterprise revenue mix, Pentagon-track legal exposure, PBC governance mechanisms (LTBT, Public Benefit Fund), and talent-concentration risk — the exact map of where to put your 2026–2028 effort. **Build a 20-slide "AI founder's / AI engineer's S-1 reading guide" this month** and publish it. Reading cross-ref: [`01` §1 S-1 filing](./01-big-lab-moves.md#1-s1-filing).
- **MCP-first product authorship.** With 47K registered servers but ~0 non-dev-tool verticals shipped (Financial Cents is the exemplar, Oct 20), the window is wide. The weekend MCP server you ship is **the single highest-signal 72-hour deliverable** of the Q4 interview cycle. See [`03` §5](./03-practical-skills-and-tools.md#5-aws-labs-mcp).
- **Agent Skills authorship (with AAIF badge).** Linux Foundation project, 1M skills + 280M installs at donation. Publishing one Agent Skill moves your résumé line from "I used a product" to "I contributed to a Linux Foundation project." See [`01` §3 Agent Skills donation](./01-big-lab-moves.md#3-agent-skills-donation).
- **Policy-adherence + behavioral-adequacy eval authoring.** The three new axes from October's arXiv (**sustained-progress, policy-adherence, behavioral-adequacy**) are now the frontier of eval authoring. See [`04` §1 BizAgentBench + behavioral-adequacy paper](./04-research-progress.md#1-october-arxiv). Add all three + air-gap + recovery-rate to every eval template you ship.
- **Cost-aware agent design with cache hit-rate as SRE metric.** The prompt-caching math + the API 2026-10-21 cutover (which invalidated some prior caches) elevated cache-hit-rate from a nice-to-have to the agent-cost SRE PR. See [`03` §7 prompt-caching discipline](./03-practical-skills-and-tools.md#7-prompt-caching).
- **Clearance-track + civilian-govtech positioning (post-Pentagon / GSA 40%).** Civilian-govtech + the OpenAI DC Public Sector lane are both opening. For an 18–24 month route, a cleared GenAI Engineer stage at Accenture (Chantilly, VA) is now a legible path. See [`02` §4 OpenAI Public Sector](./02-new-emerging.md#4-openai-public-sector) + [`§2`](#2-apply-plan).

**What re-priced DOWN this month:**

- **Model-category "fluency."** Gemini 4 Carbon's 59 beat Opus 5.5's 58 on the Intelligence Index at ~half the price. **The frontier-model-pick is now a quarterly refresh, not a résumé line.** "Experience with Gemini 4 / GPT-6 / Claude Opus 5.5" is the "experience with React" of 2017 — expected, not differentiating. Resume language: lead with **primitives** (effort levels, MCP tool-description budgeting, Agent-Skills authorship, context-ops, policy-adherence scoring, continuous-review measurement).
- **"I built one agent."** Still table stakes. One agent + published eval (with the five axes above) + cost dashboard + MCP tool-spec: **that** is differentiating.
- **Latest-model-release name-dropping.** The Oct 14 edition flagged this; it's accelerated with the Carbon release. One of the three sentences at the top of every FDE résumé should now be about *primitives you compose*, not models you've used.

→ Cross-link: [`§2`](#2-apply-plan) apply plan · [`§3`](#3-portfolio) portfolio · [`04` §5 discipline](./04-research-progress.md#5-air-gap).

---

## 2. This week's apply plan — 2 Anthropic + 1 Deloitte + 1 Scale AI + 1 ingress-track Accenture {#2-apply-plan}

**Priority 1 (today / tomorrow — before the S-1 effectiveness window):**

| Role | Posted | Why apply | Where |
|---|---|---|---|
| **Anthropic Applied AI Engineer, Enterprise** | **2026-10-20** | Direct Anthropic path, in-window posting, pre-IPO equity window ~60–90 days | Anthropic careers portal — Applied AI team |
| **Anthropic Applied AI Architect, Strategic Enterprise Tech** | **2026-10-16** | Same lane, more senior framing; if the Applied AI Engineer gets a "stretch" tag, go here instead | Anthropic careers portal |
| **Deloitte Associate GenAI Engineer** | current | **Explicitly targets May 2025 – May 2026 grads, Summer 2026 start — your window exactly** | apply.deloitte.com |
| **Scale AI Frontier Agents Engineer (Forward Deployed Engineering)** | **2026-10-19** | FDE-labeled; frontier agents angle; still early-cycle | Scale AI careers |

**Priority 2 (this week — pipeline for 2027):**

| Role | Why | Timing |
|---|---|---|
| **Accenture Senior GenAI Engineer** (multi-agent systems) | Req asks for "open-source contributions or thought leadership" — your MCP portfolio is exactly that | This week |
| **Accenture Senior AI Engineer, Chantilly VA** (requires **active TS/SCI**) | **The clearance-ingress path to OpenAI Public Sector in 18–24 mo.** Skip unless clearance intent is yes | This week if yes to clearance |
| **Databricks Senior FDE, Bengaluru** | Python/Scala + 2-of-3 clouds + Spark + CI/CD | This month if APAC posture is tolerable |
| **Direct-apply portal check:** McKinsey QuantumBlack, Bain Vector | Reqs may exist but aren't on aggregators | Weekend |

**What to say in the pitch (Anthropic Applied AI Engineer email / cover):**

> *"I'm applying as a graduating CS student committed to the Anthropic agentic stack, with an active portfolio in MCP servers and cost-aware agent design. In the last 30 days I shipped (1) a vertical MCP server for [SaaS] with a 5-case BizAgentBench-style eval reporting goal-pass + policy-adherence, (2) a Claude Mod live-cost meter on Claude Code `v2.1.287`+, (3) a public writeup of the API `2026-10-21` migration diff across 3 projects. Links below. I'd like to talk to the Enterprise Applied AI team about the Oct 20 posting — specifically how your deployment architecture handles the policy-adherence vs. goal-completion split from BizAgentBench."*

Three artifacts named, three primitives referenced (effort levels implicitly via "cost-aware"; MCP; policy-adherence). This reads as a candidate who's shipped, not spoken.

**What to NOT do:**

- **Skip Meta** for AI-track applications — hiring freeze/reassignment pattern means net AI headcount is churning, not growing ([`B6` previous research](#)).
- **Watch, don't apply to** OpenAI Public Sector senior reqs yet — 7+ years + federal customer experience gates most. Route via Accenture Chantilly if clearance is a yes.
- **Skip Mercor engineering postings** as top priority — data-labeling consolidation is capital-intensive, litigation-heavy, and not your lane.

**Sources (jobs tracker + the specific reqs):**
- [landedjobs — Forward-Deployed Engineer jobs release 2026-10-26 (300 live)](https://github.com/landedjobs/forward-deployed-engineer-jobs/releases/tag/jobs-2026-10-26) `[primary tracker]`
- [FDE Jobs List — Forward Deployed Engineer Jobs](https://fdejobslist.com/) `[aggregator]`
- [Startup.jobs — Forward Deployed Engineer, Oct 2026](https://startup.jobs/roles/forward-deployed-engineer) `[aggregator]`
- [Deloitte — Associate GenAI Engineer (US)](https://apply.deloitte.com/en_US/careers/JobDetail/Deloitte-Technology-US-Associate-GenAI-Engineer/350160) `[primary]`
- [Accenture — Senior GenAI Engineer, Belgium (multi-agent req)](https://www.accenture.com/be-en/careers/jobdetails?id=R00318995_en) `[primary]`
- [Accenture (via Dice) — Senior AI Engineer, Chantilly VA (TS/SCI)](https://www.dice.com/job-detail/b7953910-e6c5-44ff-8eb0-715ed3af2620) `[aggregator]`
- [OpenAI careers — AI Deployment Engineer, Public Sector, Federal Civilian, DC](https://openai.com/careers/ai-deployment-engineer-public-sector-federal-civilian-washington-dc/) `[primary]`
- [Dataford — Accenture GenAI Engineer interview guide 2026](https://dataford.io/interview-guides/accenture/genai-engineer) `[analysis]`

→ Cross-link: [`01` §1 S-1 pre-IPO window](./01-big-lab-moves.md#1-s1-filing) · [`§3`](#3-portfolio) portfolio.

---

## 3. Portfolio — three artifacts to ship by Nov 15 {#3-portfolio}

**Artifact 1 (this weekend, 4 hours): Vertical MCP server.**

See [`03` §5](./03-practical-skills-and-tools.md#5-aws-labs-mcp) for the step-by-step. Specifications you commit to on your README:
- 3 tools: `search_*`, `get_*`, `create_or_update_*`
- 5-case eval using **BizAgentBench policy-vs-goal split** (goal-pass + policy-adherence as two numbers)
- Pricing-with-Haiku-5.5 estimate per full run (now easy to compute — see [`03` §3 API credits bundled](./03-practical-skills-and-tools.md#3-api-credits))
- Context-ops layer: `compact / forget / elevate` as peer-tools (per [`04` §2](./04-research-progress.md#3-context-as-environment))
- 30-second demo gif
- Published to GitHub + MCP Registry + wrapped as Agent Skill → AAIF

**Artifact 2 (next weekend, 6 hours): Claude Mod — live cost + cache-hit-rate meter.**

See [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-releases). Specifications:
- Panel renders in Claude Code v2.1.287+ (Claude Mods)
- Reads session-level token + cost + cache-hit metrics live
- Alerts at <70% cache hit-rate (per [`03` §7](./03-practical-skills-and-tools.md#7-prompt-caching))
- Published to the Claude Code plugin registry

**Artifact 3 (Nov 15): Personal Claude billing audit.**

See [`03` §7](./03-practical-skills-and-tools.md#7-prompt-caching). Specifications:
- 90-day CSV from Console
- Effective cache hit-rate per project
- Per-session effective cost
- One-pager titled "Three mistakes that cost me $47 this month" (or whatever your real number is)
- Published to your blog + LinkedIn

**Why this specific triad:** Together these three artifacts cover **MCP authorship + Claude Mod authorship + cost-engineering discipline** — the three skills most-repriced-UP this month ([`§1`](#1-reprice)) in a single portfolio package. For a Deloitte / Accenture / Anthropic Applied AI loop, this is a complete read-ahead.

→ Cross-link: [`03` §1 API cutover](./03-practical-skills-and-tools.md#1-api-cutover) · [`03` §5 AWS Labs MCP](./03-practical-skills-and-tools.md#5-aws-labs-mcp) · [`04` §5 air-gap discipline](./04-research-progress.md#5-air-gap).

---

## 4. Startup — the four wedges still open after the W26 batch {#4-wedges}

**Wedge 1: MCP-native agent IAM / policy runtime.** Agentic Fabriq ("Okta for agents," YC W26) and Salus (policy-aware agent runtime, YC W26) don't fully cover the **MCP-specific** case: signed tool calls, per-tool permission trees, policy-adherence scoring, and signed Agent Skill registries. Window to the first mover is open through Q1 2027.

**Wedge 2: Vertical-SaaS MCP servers as a product line.** Financial Cents did one on Oct 20. 50+ more verticals have none. Pick 2 adjacent verticals (e.g., legal + legal-adjacent compliance) and ship an MCP-first *product line*, not a single server. Series-A story: "the MCP integration layer for [vertical cluster]."

**Wedge 3: Continuous-review-measurement platform.** Simon Willison called the question ("how do you *measure* continuous review?"); the behavioral-adequacy paper (82.8%/33.8%) gave the frontier number. **Nobody has shipped the dashboard yet.** This is a 6-month product that an FDE team at every Fortune 500 Claude customer will procure. Series-A story: "the Datadog of agent-generated code review."

**Wedge 4: GSA-ready Claude deployment template.** With the 40% civilian discount ([`01` §4](./01-big-lab-moves.md#4-gsa-discount)), state and local governments will procure Claude at scale. A startup that ships the **GSA Schedule-ready Claude deployment** (SRG IL4/IL5 posture, StateRAMP, policy-adherence eval, FedRAMP posture docs, continuous-review measurement) sells into ~100 state agencies on predictable timelines. Low glamour, high ARR, defensible compliance moat.

**Wedges that are NOT open (consolidation phase):**

- **General-purpose model routing** — 6+ venture-backed players (Sapiom $35M with Anthropic as investor, OpenRouter $113M, Concentrate AI, Martian, TrustedRouter, Not Diamond). Reposition your router artifact as **"evaluation harness for routing strategies"**, not "a router."
- **General-purpose agent monitoring** — Moda (YC W26), Hone ($60M seed, 2026-10-14 edition) — crowded.
- **Data-labeling** — Mercor + Scale + Surge consolidation phase; capital-intensive, litigation-heavy, specialist.

### Decision rule for a seed offer this quarter

The $11M median AI seed means a founding-engineer offer today at a Nov-funded seed co. has mid-single-digit % equity that still beats SWE-FAANG expected value **if the co. gets to Series A inside 24 months.** AI-labeled seeds raise fast but die faster. **Due-diligence rule:** at any seed offer, check the lead investor's prior AI-batch success rate (last 10 companies: how many reached Series A within 24 months) before signing. If it's <40%, pass.

**Realistic exit at your altitude:** **$3M–$30M acqui-hire** into one of OpenAI (10 YTD), Anthropic (5 YTD, Vercept most recent), Legora (5), Harvey (4), Sierra (3), Cursor (3), Cohere (2), or an Apple/Microsoft/Amazon. Co-founder math: a 4-engineer acqui-hire at $20M nets each engineer-founder ~$3–5M depending on equity split. Optimize for **team-size tightness and engineering density** over broad hiring.

→ Cross-link: [`02` §5 acqui-hire wave](./02-new-emerging.md#5-acquihire-wave) · [`02` §6 YC W26](./02-new-emerging.md#6-yc-w26) · [`02` §7 October funding snapshot](./02-new-emerging.md#7-october-funding).

---

## 5. Comp — the Q1 2027 anchor numbers {#5-comp}

Carryover from the Oct 14 edition, refreshed with October reporting:

| Role | TC band | Source |
|---|---|---|
| **Anthropic Applied AI Engineer L3** (mid) | ~**$300K** TC | Levels.fyi + Perspective 2026 FDE comp report |
| **Anthropic Applied AI L4–L5 FDE track** | **$665K–$750K** TC | Perspective 2026 FDE comp report (1,200 FDEs) |
| **Anthropic Applied AI L6** (principal) | ~**$1.2M** TC | Levels.fyi |
| **Anthropic SWE median** | ~**$600K** TC | Levels.fyi May 2026 cut |
| **OpenAI SWE median** | **$555K–$795K** | Levels.fyi May 2026 |
| **OpenAI FDE top band** | **$330K–$370K base + equity** | Recruiting from Scratch |
| **Palantir Forward Deployed SWE** | **$171K–$295K** (median $211K package) | Recruiting from Scratch — below Anthropic Applied AI L3 band |
| **Startup Staff/Lead FDE** | **$240K–$290K base + equity** | Recruiting from Scratch |
| **AI Engineer new grad (non-frontier)** | **$135K–$180K base** | BetonAI, 2026 roundup |

**Negotiation anchors for Q1 2027:**
- Anthropic L3 Applied AI Engineer: **ask $300K+ TC** with sign-on + L3 equity grant
- Deloitte / Accenture GenAI Engineer: **$200K–$280K TC** target
- Scale AI Frontier Agents Engineer FDE: **$250K+ TC** target
- Any frontier-lab staff-level loop: **$500K+ TC** target
- Palantir FDE: now **below** Anthropic Applied AI L3 — reversal from mid-2025. Use as a reach-up ladder, not a destination.

**Sources:**
- [Perspective — 2026 FDE compensation report, 1,200 FDEs](https://getperspective.ai/blog/2026-forward-deployed-engineering-compensation-report-1200-fdes) `[analysis]`
- [GSDC — 2026 FDE Salary Report PDF](https://gsdcdata.gsdcouncil.org/gsdc/pdf/GSDC-2026-FDE-Salary-Report.pdf) `[analysis]`
- [Pin.com — AI compensation salary guide 2026](https://pin.com/blog/ai-compensation-salary-guide) `[analysis]`
- [BetonAI — AI engineer salaries 2026, $135K new grads to $405K prompt engineers](https://betonai.net/?p=1896) `[analysis]`
- [Recruiting from Scratch — FDE salary guide, AI startups 2026](https://www.recruitingfromscratch.com/blog/forward-deployed-engineer-salary-guide-what-ai-startups-pay-in-2026) `[analysis]`

→ Cross-link: [`§2`](#2-apply-plan) apply plan · [`01` §1 S-1 pre-IPO equity window](./01-big-lab-moves.md#1-s1-filing).

---

## 6. One-line summary

**This week:** apply to Anthropic Applied AI Engineer + Deloitte Associate GenAI Engineer; **this weekend:** ship the vertical MCP server; **this month:** read the Anthropic S-1 cover-to-cover the day it lands on EDGAR; **this quarter:** stage the three-artifact portfolio (vertical MCP server + Claude Mod + personal billing audit). Everything else is tactical noise.
