# Big Lab Moves — 2026-07-16

**The compute-buildout gets ratified in real dollars, and Google is T-1 to its comeback shot.** TSMC's Q2 earnings landed this morning at a **record $40.2B revenue with HPC (AI) now 66% of the mix** — the "is the AI buildout plateauing?" question answered *no, still accelerating*. Tomorrow (Fri Jul 17) is Google's targeted **Gemini 3.5 Pro GA** on a ground-up rebuild that was delayed a full month. Under both: **the [FLI Summer 2026 AI Safety Index](../2026-07-11/) sits as the reference scorecard for the whole quarter**, and Anthropic's [Blomfield → Compute](../2026-07-14/01-big-lab-moves.md) + [Samsung 2nm chip talks](../2026-07-14/01-big-lab-moves.md) + [Cowork on phone](../2026-07-11/01-big-lab-moves.md) threads carry with one new marginal update: **read them sequenced with each other, not in isolation.**

Tags: `#tsmc #compute #chips #google #gemini #anthropic #safety #assurance #cowork #agents`

---

## 1. TSMC Q2 2026 — record $40.2B revenue, HPC = 66% of mix, capex raised {#1-tsmc-q2}

**What happened:** Taiwan Semiconductor reported **Q2 2026 earnings this morning (Thu Jul 16 US time)**:

- **Revenue: $40.2B** — record, beat the ~$40B street consensus, up ~33% YoY vs Q2 2025's $30.07B.
- **Net profit: NT$706.56B, +77.4% YoY** — record.
- **HPC (AI-related) revenue = 66% of total mix**, up from the 61% flagged in yesterday's [2026-07-15/00 TSMC preview](../2026-07-15/00-tldr.md).
- **June alone: +67.9% YoY** — the acceleration is monthly, not just quarterly.
- **N3 sold out through year-end**; N2 ramp on track for 2027.
- **2026 capex raised to $52–56B** (previously $46–50B). Full-year revenue guide raised to **>30% USD growth**.

**Why this specific print matters:** Every high-end AI accelerator on the market — **NVIDIA Blackwell + Rubin, AMD MI-series, Google TPU 8t/8i, AWS Trainium 2/3, hyperscaler custom silicon** — fabs at TSMC and packages in TSMC's advanced packaging (CoWoS). This print was the *first opportunity* to see whether the AI infrastructure buildout that has consumed advanced-node capacity for three years is **decelerating, plateauing, or still accelerating.** Answer: **still accelerating.** HPC share stepped up 5 percentage points **in a single quarter** — an acceleration inflection, not a leveling.

**Sources:**
- [TradingKey — TSMC Second Quarter Net Profit Surges 77.4% to Record, AI Chip Demand Drives Results Above Estimates](https://www.tradingkey.com/analysis/stocks/us-stocks/262033904-tsmc-q2-profit-77-percent-record-hightradingkey) `[secondary]`
- [Forbes — TSMC's Second Quarter Will Test Whether The AI Buildout Has A Ceiling](https://www.forbes.com/sites/drewbernstein/2026/07/09/tsmcs-second-quarter-will-test-whether-the-ai-buildout-has-a-ceiling/) `[analysis]`
- [TechTimes — TSMC Q2 Earnings July 16: Three CoWoS Signals That Test AI's Spending Ceiling](https://www.techtimes.com/articles/320142/20260711/tsmc-q2-earnings-july-16-three-cowos-signals-that-test-ais-spending-ceiling.htm) `[analysis]`
- [Yahoo Finance — TSMC Q2 Earnings Preview: Why Should You Buy TSM Stock Before July 16?](https://finance.yahoo.com/markets/stocks/articles/tsmc-q2-earnings-preview-why-190000466.html) `[secondary]`
- [The Investing Engineer — TSMC Earnings Preview: What Taiwan's Chip Giant Will Report on July 16](https://investingengineer.com/tsmc-earnings-preview-july-16-2026/) `[analysis]`
- [Forbes — What Taiwan Semiconductor's Earnings Can Tell Investors About Its 2026 Outlook](https://www.forbes.com/sites/investor-hub/article/taiwan-semiconductor-earnings-h2-2026-outlook/) `[analysis]`

### Why it matters to you

- **Job lens:** A **still-accelerating HPC share at TSMC is the strongest possible tailwind for the whole AI-infra hiring lane** — from compute-partnerships (see [`§4` Anthropic Compute team](./01-big-lab-moves.md#4-anthropic-carry)) through model-serving to on-prem/sovereign infra. The specific under-supplied lane: **CoWoS packaging + advanced-packaging supply-chain roles**. TSMC, Amkor, ASE, and every hyperscaler are hiring for this — search "advanced packaging" + "AI accelerator" JD keywords tonight.
- **Startup lens:** Two data points to internalize before you finalize your Q3 wedge: (a) **compute supply is not the binding constraint** — the throat of the AI stack is now **model-cadence + integration-labor**, not chips or fabs; (b) **hyperscaler capex is going up not down** — TSMC's raised guide + the earlier Google/Broadcom 3.5 GW deal + the South Korea $880B commitment all rhyme. If your wedge relied on "compute will get scarce and I'll broker it," the H2 macro is against you. If your wedge is on the model-consumer side (agents, evals, workflows, verticals), you have wind at your back.
- **Insight:** **The AI-buildout ceiling was tested today and did not appear.** Every founder-thesis or investor-thesis that quietly assumed "we're near saturation" needs to be re-priced. This is the *most important single earnings print* of Q3 for the AI sector — because it dissolves the strongest bear case (supply-side plateau). Read the market's reaction *tomorrow* for the fastest re-pricing signal.

→ Cross-link: [2026-07-15/00 TSMC Q2 preview](../2026-07-15/00-tldr.md) — the "AI = 61%" preview turned into "AI = 66%" print; the [`§4` Anthropic carry](./01-big-lab-moves.md#4-anthropic-carry) — Samsung 2nm talks make even more sense against this backdrop.

---

## 2. Gemini 3.5 Pro — T-1 to July 17 GA (2M ctx + Deep Think) {#2-gemini-pro-t1}

**What's expected tomorrow (Fri Jul 17):** Google's **Gemini 3.5 Pro** targeted GA — the **ground-up rebuild** that slipped past its June deadline (per [2026-07-11/01](../2026-07-11/01-big-lab-moves.md), [2026-07-13/00](../2026-07-13/00-tldr.md)).

**What is known / expected:**
- **Context window: 2M tokens** — largest of any production frontier model at GA.
- **Deep Think mode** — extended inference-time compute; spends more reasoning cycles at the cost of latency + tokens. Likely gated behind a premium tier (rumored $250/mo Ultra).
- **Expected pricing (enterprise-preview leaks, unconfirmed):** **$12–15 / 1M input · $36–45 / 1M output**, with **long-context surcharges above 200K tokens**. This would land it *notably above* Sonnet 5 intro ($2/$10) and GPT-5.6 Terra ($2.50/$15) on price — Google would be pricing for Deep Think value, not competing on token cost.
- **Public API still shows** `gemini-3.5-flash` and `gemini-3.1-pro-preview` as of July 13; **no `gemini-3.5-pro` endpoint** yet.
- **No model card, no official benchmark suite, no confirmed pricing.** Everything above tagged `[rumor]` until Google's Fri Jul 17 announce.

**Sources:**
- [AIToolsRecap — Gemini 3.5 Pro Targets July 17 — 2M Context, Deep Think, and the Unrestricted Frontier Model Google Needs Right Now](https://aitoolsrecap.com/Blog/gemini-3-5-pro-july-17-launch-specs-pricing-2026) `[rumor]`
- [Developers Digest — Gemini 3.5 Pro Developer Guide: 2M Context Window and Deep Think Mode](https://www.developersdigest.tech/blog/gemini-3-5-pro-developer-guide-2026) `[analysis]`
- [DEV.to — Gemini 3.5 Pro: 2M Context, Deep Think, and the Post-Fable-5 Frontier](https://dev.to/akaranjkar08/gemini-35-pro-2m-context-deep-think-and-the-post-fable-5-frontier-2p60) `[analysis]`
- [Nokia Power User — Google Gemini 3.5 Pro Leak Reveals Deep Thinking Mode, 2M Context Window, and Major AI Upgrades](https://nokiapoweruser.com/google-gemini-3-5-pro-leak-deep-thinking-2m-context-window/) `[rumor]`
- [Geeky Gadgets — Gemini 3.5 Pro Leaks Detail New Deep Think Reasoning](https://www.geeky-gadgets.com/google-gemini-3-5-pro-leaks/) `[rumor]`

### Why it matters to you

- **Job lens:** **Google Cloud + DeepMind hiring windows for Gemini 3.5 Pro-adjacent Solutions Engineer / Applied AI roles open the moment it ships.** Post-launch is when the FDE / Solutions requisitions land. Track the Google Cloud jobs page **every Friday for the next 4 weeks**.
- **Startup lens:** If Gemini 3.5 Pro ships at the leaked $12–15 / $36–45 price with 2M ctx, **it repositions the frontier as *three-tier by price*: cheap fast (Gemini 3.5 Flash, GPT-5.6 Luna), mid workhorse (Sonnet 5, GPT-5.6 Terra), premium reasoning (Gemini 3.5 Pro + Deep Think, GPT-5.6 Sol, Fable 5).** Your product needs a *pricing tier map* — which task runs at which tier — not a single-model bet. Update the [2026-07-09 four-price routing table](../2026-07-09/03-practical-skills-and-tools.md) tomorrow morning with the actual Gemini 3.5 Pro numbers.
- **Insight:** If Gemini 3.5 Pro **ships** tomorrow, the "Google can't compete at frontier" narrative dies for Q3 and it becomes a real three-horse race again. If it **slips** a second time, the narrative crystallizes and every 2027-planning founder assumes "build for Anthropic + OpenAI, ignore Google." Tomorrow's ship-or-slip is one of the most consequential Q3 signals — set a calendar alert for **8:00 AM PT Fri Jul 17**.

→ Cross-link: [2026-07-11/01 DeepMind exodus that made Gemini 3.5 Pro so pivotal](../2026-07-11/01-big-lab-moves.md) · [2026-07-09 four-price routing table (baseline to update)](../2026-07-09/03-practical-skills-and-tools.md).

---

## 3. FLI Summer 2026 AI Safety Index — Anthropic top at C+ (still the quarter's reference doc) {#3-fli-safety-index}

**What it is:** The **Future of Life Institute's Summer 2026 AI Safety Index** (published July 7, still the reference doc a week later) graded **9 leading AI companies** on **37 indicators** across **6 domains** (Risk Assessment · Current Harms · Safety Frameworks · Existential Safety Strategy · Governance & Accountability · Information Sharing).

**Overall grades:**
- **Anthropic — C+** (top; leads 5 of 6 domains)
- **OpenAI — C** (leads Risk Assessment on strength of broader external red-team engagement)
- **Google DeepMind — C**
- **Meta — D+** (improved vs prior index)
- **Z.ai — D**
- **Alibaba Cloud — D**
- **xAI — F**
- **DeepSeek — F**
- **Mistral — F**

**The "moving goalpost" finding:** Anthropic, OpenAI, Google DeepMind, and Meta have all **weakened or voided commitments to pause unilaterally if red-lines are approached**, some by adding *competitor-contingent* conditions. Reviewers argue this has "undermined safety frameworks across the board." Three companies received failing grades — one each from the US (xAI), China (DeepSeek), and Europe (Mistral) — a politically-symmetric distribution.

**Why it's on today's edition:** The Index is the *durable* July 2026 reference the whole quarter's safety-and-assurance career narrative hangs on. When the (postponed) US pre-release EO returns to signing, or when EU CAISI cites specific indicators, or when enterprise procurement teams cite the Index in RFPs — **the 37-indicator rubric is the vocabulary they will use.** If you have not yet learned it, do it this week.

**Sources:**
- [Future of Life Institute — AI Safety Index Summer 2026](https://futureoflife.org/ai-safety-index-summer-2026/) `[primary]`
- [FLI — Executive Summary (PDF)](https://futureoflife.org/wp-content/uploads/2026/07/AI-Safety-Index-Report_010726_2Pager.pdf) `[primary]`
- [TIME — The Latest AI Safety Rankings Are In. Nobody Gets an A](https://time.com/article/2026/07/07/ai-safety-rankings-openai-anthropic-meta/) `[secondary]`
- [MIT Sloan Management Review — Anthropic Tops 2026 AI Safety Index, But No AI Firm Earns Above a C+](https://www.mitsloanme.com/article/anthropic-tops-2026-ai-safety-index-but-no-ai-firm-earns-above-a-c/) `[secondary]`
- [Axios — AI companies retreat from safety pledges](https://www.axios.com/2026/07/07/report-ai-safety-pledges) `[secondary]`
- [Seoul Economic Daily — Global Big Tech Retreats on AI Safety Pledges, Experts Warn](https://en.sedaily.com/news/2026/07/08/global-big-tech-retreats-on-ai-safety-pledges-experts-warn) `[secondary]`

### Why it matters to you

- **Job lens:** The **safety-eval / AI-assurance career lane** now has a **public scoring rubric you can name-drop**. Add these terms to your resume + LinkedIn tonight: "pre-deployment evaluation," "safety framework maturity," "external red-team engagement," "incident disclosure," "model-release governance," "capability elicitation." See [`05` §1](./05-career-and-startup.md#1-assurance-lane) for the 30-minute action.
- **Startup lens:** Two founder wedges the Index makes legible: (a) **"safety-eval as a service"** — help mid-tier labs (Meta, Z.ai, Alibaba, DeepSeek) close *specific* indicators rather than commission full framework audits; (b) **"AI procurement scorecard"** — an internal tool for enterprises that maps FLI-style indicators onto their vendor list, monetized as a Claude/GPT vendor-neutral overlay.
- **Insight:** Read the "moving goalpost" finding as the *most important* takeaway. When labs allow their own pause-commitments to become **conditional on competitor behavior**, the *coordination equilibrium collapses toward "keep shipping."* This is exactly what a public scorecard is designed to interrupt — it re-anchors the reputational cost to *your own past commitments*, not to competitor behavior. **The Index is a coordination device disguised as journalism.**

→ Cross-link: [2026-05-22/01 §1 the postponed pre-release EO](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) — federal scoring lane delayed; FLI stepped into the vacuum. · [`05` §1 the assurance career lane](./05-career-and-startup.md#1-assurance-lane).

---

## 4. Anthropic carry — Blomfield + Samsung + Cowork, read sequenced {#4-anthropic-carry}

**What already shipped this month:**
- **Tom Blomfield → Anthropic Compute** (announced Jul 13; covered [2026-07-14/01](../2026-07-14/01-big-lab-moves.md)). Monzo/GoCardless co-founder, YC GP since 2023, on leave from YC to join under **Tom Brown (Chief Compute Officer)**. Zero infra background. Second consumer-legible non-research hire in nine weeks after [Karpathy → pre-training (May 19)](../2026-05-22/01-big-lab-moves.md#3-karpathy).
- **Anthropic × Samsung 2nm SF2 custom Claude inference chip — early talks** (first reported Jul 2 by The Information; consolidated [2026-07-14/01](../2026-07-14/01-big-lab-moves.md)). Samsung's Gate-All-Around nanosheets; estimated 30–50% cheaper per token if it ships; volume 2028+. **Clive Chan (ex-OpenAI chip design) also hired** in the same window.
- **Claude Cowork went cloud-native on web + mobile Jul 7** (covered [2026-07-10/01](../2026-07-10/01-big-lab-moves.md)); **iOS + Android app on Jul 10** (covered [2026-07-11/01](../2026-07-11/01-big-lab-moves.md)); **doubled usage limits through Aug 5**.

**Today's marginal update — read these three sequenced:**

1. **The Samsung chip talks (Jul 2)** open the possibility of a custom inference stack.
2. **Clive Chan (ex-OpenAI chip design) hired** in the same week — that's the *research/design* seat that has to own the technical spec.
3. **Blomfield → Compute (Jul 13)** — that's the *operator* seat that has to own the vendor-negotiation, procurement, and long-cycle-supply decisions the custom chip creates.
4. **Cowork went cross-device** and **usage limits doubled through Aug 5** — that's the *demand curve* that Justifies the custom silicon (if agents run 24/7 on your phone, inference cost is now the primary product knob).

The four moves are one *strategy* — vertical integration of the compute stack for a *specific* workload (long-horizon phone-native agent inference) at a *specific* cost floor. **Read the July calendar as "Anthropic just staffed the custom-silicon program end-to-end and lit up the demand curve that pays for it."** That's the read-in for your Anthropic-stack ME.md decision.

**Sources (consolidated, already covered):**
- [TechCrunch — Anthropic is discussing a new custom chip with Samsung (Jul 2)](https://techcrunch.com/2026/07/02/anthropic-is-discussing-a-new-custom-chip-with-samsung/) `[secondary]`
- [Tech Funding News — Monzo co-founder Tom Blomfield takes leave from Y Combinator to join Anthropic (Jul 13)](https://techfundingnews.com/monzo-co-founder-tom-blomfield-takes-leave-from-y-combinator-to-join-anthropic/) `[secondary]`
- [Anthropic — Claude Cowork on web and mobile (Jul 7)](https://claude.com/blog/cowork-web-mobile) `[primary]`
- [TechCrunch — Claude Cowork expands to mobile and web (Jul 7)](https://techcrunch.com/2026/07/07/the-coding-agent-wars-are-spilling-into-the-rest-of-the-office-claude-cowork/) `[secondary]`
- [ExplainX — Anthropic Hiring Spree 2026: John Jumper, Karpathy, Talent](https://explainx.ai/blog/anthropic-hiring-spree-2026-john-jumper-karpathy-talent-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Watch for **Anthropic Solutions / FDE JDs that name "custom silicon pilot," "inference cost optimization," or "compute program management"** — those requisitions are the direct downstream of the Blomfield + Chan hires. Expect the first postings in **~4 weeks** as the program formalizes.
- **Startup lens:** The **cheap-inference platform wedge just narrowed further.** Every month that Blomfield's Compute team + the Samsung talks + Cowork demand curve mature, the *neutral third-party inference platform* looks more like a commodity, and the *frontier-lab-native inference stack* looks more like the strategic asset. Adjust your platform bets accordingly.
- **Insight:** The four moves are one **playbook**: pick the workload (long-horizon phone-native agents), pick the silicon path (Samsung 2nm), staff the technical seat (Chan) and the operator seat (Blomfield), light up the demand curve (Cowork + doubled limits). **This is how the next-decade AI stack gets built — not a single announcement, a coordinated four-part sequence.** Watch for OpenAI's parallel version in Q4.

→ Cross-link: [2026-07-14/01 §2 Anthropic × Samsung consolidated](../2026-07-14/01-big-lab-moves.md) · [2026-07-11/01 Cowork iOS/Android + Karpathy hire follow-up](../2026-07-11/01-big-lab-moves.md).

---

## Cross-link: what these four stories share

TSMC (§1) is the **compute-supply proof point**. Gemini 3.5 Pro (§2) is the **model-supply cadence test**. FLI (§3) is the **governance scorecard**. The Anthropic carry (§4) is the **vertical-integration playbook**. Together they answer: *"in H2 2026, what is the frontier optimizing for?"* Answer: **not raw capability**, but **cost per useful token × verified reliability × strategic control of the stack** — with capability held roughly constant across Anthropic, OpenAI, and (T-1) Google.
