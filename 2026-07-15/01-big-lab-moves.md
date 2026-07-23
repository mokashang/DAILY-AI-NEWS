# Big Lab Moves — 2026-07-15

Wednesday's frame: **the infrastructure layer under the AI story just posted its earnings, the international policy split just went live, and Anthropic quietly opened its sixth distribution channel of Q3.** TSMC's Q2 preview (out Monday; full earnings tomorrow) shows **AI chips at 61% of revenue and N3 sold out through year-end** — the compute buildout is real and priced in. Beijing's **anthropomorphic-AI rules took effect today**, forcing Doubao (345M MAU) and Qwen to disable agent features that Western labs face zero equivalent restrictions on. And Anthropic **launched Claude for Teachers yesterday** — free premium access for verified US K-12 educators, FERPA-compliant, AFT-negotiated, with Detroit Public Schools as the first pilot district and a public teaching-skills repo on GitHub. Read together: **the chips are the tailwind, the regulatory divergence is the geographic wedge, and the education channel is the next Anthropic vertical after Legal / Small Business / Personal Finance / Finance / Science.**

Tags: `#labs #tsmc #chips #anthropic #education #china #policy #regulation`

---

## 1. TSMC Q2: AI chips are 61% of revenue, N3 sold out, capex raised {#1-tsmc-q2}

**What happened:** On **Monday July 13** TSMC released its June + Q2 preliminary revenue and set the stage for Thursday's full earnings (July 16). The numbers ratify the entire compute story that every other headline this year has assumed:

- **June revenue:** NT$442.68B, **+67.9% YoY**, a new monthly record (+6.2% over May's prior record of NT$416.98B).
- **Q2 2026 revenue:** NT$1.27T ≈ **$39.62B (+36% YoY)**, edging above the top of the company's own $39.0–$40.2B guide.
- **AI chips = 61% of Q2 sales.** Company frames the driver as "the transition from generative AI to agentic AI."
- **N3 sold out through year-end.** N3 is the process node running nearly every leading AI GPU/CPU shipping in 2026.
- **2026 capex raised to the high end of $52–$56B**; full-year 2026 revenue guide now **>30% USD growth**.
- **Q2 net profit** estimated **+58.8% YoY** (LSEG SmartEstimate).
- Full earnings + Q3 outlook + updated capex land **tomorrow, Thursday July 16**.

**Sources:**
- [CNBC — TSMC reports 68% surge in June revenue](https://www.cnbc.com/2026/07/13/tsmc-june-revenue-rises-percent-ahead-second-quarter.html) `[secondary]`
- [Seoul Economic Daily — TSMC June revenue jumps 68%, Q2 seen at record high](https://en.sedaily.com/international/2026/07/13/tsmc-june-revenue-jumps-68-percent-q2-seen-at-record-high) `[secondary]`
- [Yahoo Finance — TSMC Q2 revenue beats guidance as June sales surge 68%](https://finance.yahoo.com/markets/stocks/articles/tsmc-q2-revenue-beats-guidance-115145349.html) `[secondary]`
- [TSMC Form 6-K — June 2026 revenue release](https://www.sec.gov/Archives/edgar/data/0001046179/000104617926000447/tsm-revenue20260713.htm) `[primary]`
- [Investing Engineer — TSMC earnings preview July 16](https://investingengineer.com/tsmc-earnings-preview-july-16-2026/) `[analysis]`
- [TechTimes — TSMC Q2 earnings July 16: three CoWoS signals](https://www.techtimes.com/articles/320142/20260711/tsmc-q2-earnings-july-16-three-cowos-signals-that-test-ais-spending-ceiling.htm) `[analysis]`

### Why it matters to you

- **Job lens:** TSMC's "AI = 61%, N3 sold out, capex up" print is the **hard-number vindication of every hyperscaler infra hiring wave you've been tracking** — CoreWeave/Nebius/Together/Meta Compute/SB Neo and the Anthropic-Google-Broadcom 3.5GW TPU deal. The two adjacent hiring lanes are (a) **AI-infrastructure engineer** (GPU / TPU / interconnect / capacity planning — sits under CoreWeave-alt neoclouds and the labs' own infra orgs) and (b) **inference-cost engineer** — the person who owns "how many tokens per dollar per successful task" as a KPI. Both grow directly with TSMC's capex line. Add "AI infra capacity" and "inference cost engineering" to your applied-role vocabulary; both are less-crowded than the FDE flood.
- **Startup lens:** N3 sold-out is a **supply-side scarcity signal** that lasts through 2026 and probably H1 2027. Two founder plays: (1) **route around** the scarcity — anything that meaningfully reduces tokens or moves work to older nodes (edge inference, quantized workers, small-model routing) captures the arbitrage; (2) **build on top of** the scarcity — infra pricing tools, capacity forecasting, GPU-hour marketplaces (see also [Meta Compute, 2026-07-02](../2026-07-02/01-big-lab-moves.md#2-meta-compute) and [Together AI $800M / SB Neo, 2026-07-03](../2026-07-03/02-new-emerging.md)). Both are picks-and-shovels bets under a proven macro.
- **Insight:** The narrative that "AI capex is a bubble" has to reckon with **the physical layer showing +36% YoY and rising**. That doesn't mean prices for individual companies are right; it means **the *demand* is real, and the constraint is *manufacturing capacity*, not app-layer willingness to pay.** In practice: the labs' compute deals ([Anthropic-Colossus 1, 2026-05-21](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus); [Anthropic-Google-Broadcom 3.5GW, 2026-07-13](../2026-07-13/)) are locking in scarce supply years ahead — which is *why* Anthropic is [exploring Samsung 2nm (2026-07-14 §1)](../2026-07-14/01-big-lab-moves.md#1-anthropic-samsung). Read every "AI is expensive" pricing move (Anthropic Sonnet 5 metering / OpenAI cache breakpoints / Uber's token-tier rebellion) as **downstream of TSMC's supply constraint**, not just of vendor greed.

→ Cross-link: [`03` §2 the cross-provider prompt-cache lever](./03-practical-skills-and-tools.md#2-cache-lever) · [2026-07-14/01 §1 Anthropic-Samsung 2nm](../2026-07-14/01-big-lab-moves.md#1-anthropic-samsung).

---

## 2. China's anthropomorphic-AI rules take effect TODAY — Doubao (345M MAU) + Qwen agent features go dark {#2-china-anthropomorphic}

**What happened:** The **Interim Measures for the Administration of AI Anthropomorphic Interactive Services** — co-issued April 10 by the Cyberspace Administration of China (CAC) with NDRC, MIIT, Ministry of Public Security, and SAMR — take effect **today, Wednesday July 15**. The measures apply to any AI product "designed to replicate how humans think, speak, and present themselves in order to maintain ongoing emotionally-oriented interactions."

- **Bans:** any content designed to trigger strong emotional reactions in minors; any behavior that creates attachments strong enough to substitute for real-life relationships; use of private user conversations for training.
- **Enforcement events today:**
  - **ByteDance's Doubao** (China's most-used AI app, **~345M MAU**) disables its agent feature. Notice cites "product function adjustments." Related agent chat data becomes non-viewable / non-recoverable **after Oct 15**.
  - **Alibaba's Qwen** disables its "humanlike interactive agents + user-created agent functions" (already partially cut on July 10); broader "Qwen agent functions and services" go offline today.
- **Framing:** CAC cites radicalization, data privacy, psychological and physical harm, and compulsive use. Western labs face **no equivalent restriction** in their home jurisdictions.

**Sources:**
- [Bloomberg — ByteDance, Alibaba pull AI companions as Beijing tightens rules](https://www.bloomberg.com/news/articles/2026-07-06/bytedance-alibaba-pull-ai-companions-as-beijing-tightens-rules) `[secondary]`
- [SCMP — ByteDance and Alibaba to disable humanlike AI custom agents as new rules loom](https://www.scmp.com/tech/big-tech/article/3359482/bytedance-and-alibaba-disable-humanlike-ai-custom-agents-new-rules-loom) `[secondary]`
- [TechNode — Doubao and Qwen to shut down AI agent features on July 15](https://technode.com/2026/07/06/bytedances-doubao-and-alibabas-qwen-to-shut-down-ai-agent-features-on-july-15/) `[secondary]`
- [TechTimes — China AI companion law takes effect: Doubao and Qwen shut down](https://www.techtimes.com/articles/320525/20260715/china-ai-companion-law-takes-effect-doubao-qwen-shut-down-millions-lose-chat-data.htm) `[secondary]`
- [The Next Web — China's AI companion rules force Doubao, Qwen shutdowns](https://thenextweb.com/news/china-humanlike-ai-agent-rules) `[secondary]`
- [Artificial Intelligence News — What Beijing is really going after](https://www.artificialintelligence-news.com/news/china-ai-companion-rules/) `[analysis]`

### Why it matters to you

- **Job lens:** The **compliance-engineering** function that has been building in the US around the [Colorado AI Act (2026-06-30)](../2026-06-30/01-big-lab-moves.md#1-colorado-day-1) and [Anthropic v. DOD (2026-06-29)](../2026-06-29/01-big-lab-moves.md#1-anthropic-dod) just gained an international dimension. **"Regional-AUP engineer" / "cross-jurisdictional model policy" / "consumer-agent product policy"** are all real hire titles for anyone (Meta, Apple, ByteDance-US, TikTok, Snap, Discord) whose product ships human-shaped conversational features into multiple regulatory regimes. This lane pairs directly with the assurance-lane 3-sublane keyword tree ([2026-06-30/05 §3](../2026-06-30/05-career-and-startup.md#3-policy-lane)) — add "consumer-AI compliance" as the fourth sublane.
- **Startup lens:** For **consumer-facing conversational products (Replika, Character.ai, Talkie, Kindroid, Meta AI Companion, xAI Ani)** the immediate question is: *does our product design shorten or lengthen our runway when equivalent rules land in a US or EU jurisdiction?* CA and EU regulators watch CAC precedents — this is a **12–24 month forward indicator** for anything companion-shaped. Wedges that hold up under a "no manipulation of minors, no fake persistent identity, no training on private convo" future: **utility-shaped agents** (task, research, reminder, tutor) over **relationship-shaped agents.** Bank the Detroit-Anthropic-partnership frame from §3 as the reference model.
- **Insight:** The single biggest policy signal of the day is that **the US-China regulatory gap is now visible in shipped product**, not just in white papers. Chinese labs will get *more constrained* on consumer surfaces while their compute (via Meituan LongCat, DeepSeek, Alibaba Qwen open-weights) races the US on frontier capability — a bifurcation that mirrors, in mirror image, the [Anthropic-China-loophole crackdown (2026-07-04)](../2026-07-04/01-big-lab-moves.md#1-china-loopholes). Expect **two divergent product footprints per lab by 2027**: consumer-facing (tightly constrained; heavy identity + minor + convo-privacy rules) and enterprise-facing (looser; audit-log-heavy). Build a career or a product knowing that split is on the roadmap.

→ Cross-link: [`05` §3 assurance lane extended to consumer-AI compliance](./05-career-and-startup.md#3-consumer-compliance) · [2026-07-04/01 §1 Anthropic-China-loophole crackdown](../2026-07-04/01-big-lab-moves.md#1-china-loopholes).

---

## 3. Anthropic launches Claude for Teachers — free premium for US K-12, FERPA-aligned, AFT-negotiated, Detroit pilot {#3-claude-for-teachers}

**What happened:** Anthropic launched **Claude for Teachers** on **Tuesday July 14** — free premium Claude access for verified US K-12 educators, structured as a distinct product with education-specific privacy and skill tooling. Details:

- **Access:** premium Claude features + a library of teaching-specific "skills" + curriculum connections mapped to standards in **all 50 states**. Teachers who sign up before **June 30, 2027** get a full year of free access.
- **Privacy stack:** data not used for model training; **K-12 Data Processing Addendum written to comply with FERPA**; terms **co-developed with the American Federation of Teachers (AFT).**
- **Ecosystem integrations at launch:** ASSISTments, Brisk Teaching, Canva Education, Coteach, Diffit, Eedi, MagicSchool, Snorkl and others.
- **Pilot deployment:** Anthropic will run a **pilot evaluation in the Detroit Public Schools Community District.**
- **Open-source component:** teaching-skills repository published on GitHub.
- **Eligibility:** 18+, verified K-12 educators only.

**Sources:**
- [Anthropic — Introducing Claude for Teachers](https://www.anthropic.com/news/claude-for-teachers) `[primary]`
- [The Hill — Anthropic launches free Claude for Teachers](https://thehill.com/policy/technology/5968601-claude-for-teachers-launch/) `[secondary]`
- [Forbes — Anthropic launches AI for Teachers](https://www.forbes.com/sites/danfitzpatrick/2026/07/14/anthropic-launches-ai-for-teachers/) `[secondary]`
- [EdSurge — Anthropic introduces Claude for Teachers](https://www.edsurge.com/news/anthropic-introduces-claude-for-teachers) `[secondary]`
- [ETIH EdTech News — Anthropic opens Claude for Teachers free to US K-12](https://www.edtechinnovationhub.com/news/anthropic-opens-claude-for-teachers-free-to-us-k-12-educators) `[secondary]`
- [TechTimes — Anthropic makes Claude free for all US K-12 teachers](https://www.techtimes.com/articles/320533/20260715/anthropic-makes-claude-free-all-us-k-12-teachers-standards-aligned-agentic-ai.htm) `[secondary]`

### Why it matters to you

- **Job lens:** This is Anthropic's **sixth vertical channel of 2026** (Legal → Small Business → Personal Finance → Finance → Science → **Teachers**) in ~10 weeks. The hiring pattern is now legible: each vertical launch adds an **applied-team pod** with a Solutions/FDE lead + one policy-partner-facing role (here, AFT + district partnerships) + engineers for the standards + skills + integrations layer. **"Anthropic Applied — Education"** and **"Solutions Engineer — K-12 / EDU"** are the JD shapes to LinkedIn-alert for. Adjacent shops: MagicSchool, Diffit, Canva Education, Brisk Teaching all just gained a preferred-partner status; their eng/DE/PM roles are the second-order hiring wave.
- **Startup lens:** The **vertical-Claude template as founder playbook** ([2026-07-06/02 §6](../2026-07-06/02-new-emerging.md#6-vertical-template)) now has **six data points** to pattern-match on: pick a domain, wrap Claude with a policy/privacy layer + a skill library + partner integrations + a named-district-or-firm pilot. The domains Anthropic has NOT yet done — cybersecurity ops, construction, logistics, insurance underwriting, veterinary, municipal government — are all still open. Note that the *K-12 pilot with a large urban district (Detroit)* is the exact shape a founder would use to sell into any regulated buyer.
- **Insight:** The **AFT co-development** is the tell. Anthropic is investing in policy-partner distribution — a union endorsement solves the "is this safe?" objection at 1.7M members' scale in a way sales never could. Read that back through the [Gates Foundation deal (2026-05-17)](../2026-05-17/01-big-lab-moves.md), the [Pentagon email release (2026-07-04 §2)](../2026-07-04/01-big-lab-moves.md#2-pentagon-emails), and the [new constitution (2026-07-03 §4)](../2026-07-03/01-big-lab-moves.md#4-constitution): Anthropic is systematically building **institutional legitimacy as distribution**. That's a durable moat OpenAI does not have and is unlikely to replicate quickly given its ad-monetization posture ([2026-05-21/02 §1](../2026-05-21/02-new-emerging.md#1-ads-surface)).

→ Cross-link: [`05` §1 Anthropic vertical-pod hiring lanes](./05-career-and-startup.md#1-anthropic-verticals) · [2026-07-06/02 §6 vertical template as founder playbook](../2026-07-06/02-new-emerging.md#6-vertical-template).
