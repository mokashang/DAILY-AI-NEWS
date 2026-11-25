# New & Emerging — 2026-11-25

Three threads this week: **capital kept moving even as public AI equity cooled** (Isomorphic $5B, Model ML $250M, Assort $120M), the **chip-price-deflation debate got a loud public call** from Databricks' Ali Ghodsi that NVIDIA's $130B Q4 guide implicitly disputes, and the **ANT-triggered multiples-compression trade** started to reshape private-market pricing expectations for Q1 2027 rounds.

Tags: `#funding #infra #compute #startups #vertical-ai #bio`

---

## 1. Isomorphic Labs closes $5B Series C — largest AI-for-science round of 2026 {#1-isomorphic-5b}

**What happened (2026-11-16):**
- Isomorphic Labs (Alphabet / DeepMind drug-discovery spinout) closed a **$5B Series C** — reported on multiple funding trackers with no single sanctioned press release yet.
- Previous round: **$2.1B four-corner (Thrive + GV + Alphabet + Lilly), 2026-05**.
- **~2.4× uplift in 6 months** suggests at least one anchor pharma bought a major position at this round, likely locking in a right-of-first-refusal on a program slate.

**Sources:**
- [AI Funding Tracker (SuperpowerDaily)](https://superpowerdaily.com/signals/funding) `[aggregator]`
- [Blog.mean.ceo — AI Startup Funding News Nov 2026](https://blog.mean.ceo/ai-startup-funding-news-november-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** AI-for-science is **the single most defensible research-adjacent lane for a CS grad with any bio/chem/physics coursework**. Isomorphic + **Xaira + EvolutionaryScale + Latent Labs + Inceptive** is a 5-company set that hires on **domain-adjacent CS** (structured prediction, protein LMs, geometric DL) *more than* on PhD alone. If you have an undergrad biology minor or a summer in a wet lab, this track isn't closed to you.
- **Startup lens:** $5B at this valuation implies **AI-for-science still gets priced on scientific milestones, not revenue multiples** — the one lane that *escaped* the ANT-triggered multiples-compression trade. If you're incubating around a specific disease class, dataset, or wet-lab integration, the capital is there.
- **Insight:** Watch whether Isomorphic's next IND filing date leaks before year-end. **The real test of AI drug discovery as a business, not a research program, is Phase II readouts in 2027–2028** — and this round is sized to fund clinical operations, not just inference.

→ Cross-link: [`04` §4 — AlphaGenome 2 + science-first foundation models](./04-research-progress.md#4-science-first-models)

---

## 2. Model ML raises $250M Series B — financial-services-first AI agent + data-room platform {#2-model-ml}

**What happened (2026-11-17):**
- **Model ML** announced a **$250M Series B**, co-led by **General Atlantic and QED Investors**.
- Positioning: **"financial-services-native agent platform"** — deal rooms, model-governance, due-diligence agents for banks and asset managers.
- Pattern-matches to the **Rox (sales, $100M) + Decagon (customer service) + Nooks (revenue-share capital)** cohort: a **vertical agent product in a regulated segment where enterprise logos pay a premium**.

**Sources:**
- [AI Funding Tracker (SuperpowerDaily) — Model ML entry](https://superpowerdaily.com/signals/funding) `[aggregator]`
- [Blog.mean.ceo — November 2026 funding roundup](https://blog.mean.ceo/ai-startup-funding-news-november-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** Model ML is likely **hiring ~30 FDE/Solutions-shaped roles in the next two quarters** at post-$250M scale. Financial-services AI means **SOC 2 Type II + FedRAMP-flavored compliance-aware engineering** — a hireable niche that is *not* commodity model fluency. Target titles: Forward Deployed Engineer, Deployment Architect, Customer Solutions Engineer.
- **Startup lens:** **QED on the cap table is the tell**. QED has the best track record of any fintech-focused fund in the past decade, and they're taking a ~$30–$50M check into an agent platform. **The wedge "vertical compliance + model agent" is now a confirmed category**, not a thesis. If you're building one of the adjacent-but-not-overlapping lanes (insurance ops, treasury operations, risk reporting), you have ~6–12 months before a competitor bakes that wedge in too.
- **Insight:** **Model ML + Rox + Decagon + Harvey + Sierra** = the "vertical agent with regulated-industry gating" pattern is now a *dominant* 2026 fundraising archetype. The generic "horizontal AI assistant" thesis is dead for Series B+ raises.

→ Cross-link: [`05` §2 — Thanksgiving-window applications include Model ML](./05-career-and-startup.md#2-thanksgiving-window)

---

## 3. The chip-price-deflation debate: Databricks (Ghodsi) vs. NVIDIA Q4 guide {#3-chip-price-debate}

**What happened (2026-11):**
- **Ali Ghodsi (Databricks CEO)** told The Information that he expects a **"major drop in AI chip prices"** on the horizon.
- **NVIDIA's Q4 FY27 guide**, issued Nov 19: **$130B revenue (±3%) ex-China**. Gross margin **71–72%**, a *modest* step-down from the Vera Rubin ramp, but still 70%+. **No evidence of pricing pressure** from either hyperscaler or custom-silicon competition in the near-term guide.
- Context: **OpenAI × Broadcom 10 GW Ethernet-backed custom chip deployment H2 2026 → 2029** (from previous edition) is the single largest medium-term threat to NVIDIA's rack-scale lock-in. But "deployment through 2029" is not "price crash in 2026."

**Sources:**
- [The Information — Databricks CEO predicts major drop in AI chip prices](https://www.theinformation.com/articles/databricks-ceo-predicts-major-drop-in-ai-chip-prices) `[analysis]` (paywalled)
- [Futurum Group — NVIDIA Q3 FY27 supply commitments](https://futurumgroup.com/?p=98250) `[analysis]`
- [TechPowerUp — NVIDIA $115.8B Q3, $130B Q4 guide](https://www.techpowerup.com/354965/nvidia-reports-q3-2026-earnings-of-usd-115-8-billion) `[secondary]`

### Why it matters to you

- **Job lens:** Hiring in **GPU-aware SRE, inference-platform, and NVIDIA-ecosystem roles stays hot through 2027** on the strength of NVIDIA's forward guide. **"AI chip prices will crash by 2026Q4"** is now an officially contested call — do not build a career thesis on it. If you're deciding between an **inference-platform startup (fal, Replicate, Modal, Baseten, Together)** and a **custom-silicon play (Groq, Cerebras, SambaNova, Etched)**, the near-term risk-adjusted bet is still the NVIDIA-adjacent lane.
- **Startup lens:** **Any pitch that depends on GPU spot prices falling 30%+ before 2027H2 should be de-risked by assuming NVIDIA pricing holds at 2026 levels through all of 2027.** If the thesis still works, it's a real thesis. If not, rebuild unit economics.
- **Insight:** Watch **SemiAnalysis (Dylan Patel)** for the first independent-analyst take on the Ghodsi call. If SemiAnalysis endorses it, update priors. If not, treat it as a **customer-of-NVIDIA-wants-lower-prices** quote.

→ Cross-link: [`01` §2 — NVIDIA Q3 FY27 + Q4 $130B guide](./01-big-lab-moves.md#2-nvidia-q3-fy27)

---

## 4. The ANT-triggered AI-trade selloff: what private rounds look like now {#4-ai-trade-selloff}

**What happened (2026-11-19 → 2026-11-24):**
- Day 1 ANT pop +17%, Day 6 ANT below offer **(-26.5% from debut)**.
- **NVIDIA, AMD, Micron all sold off into NVIDIA's own Q3 beat** on Nov 19.
- **Reuters / Capital Economics commentary:** record-breaking Anthropic IPO "has failed to rekindle enthusiasm for tech stocks."
- Finimize summary: **"Anthropic's big IPO didn't save the AI trade."**

**Secondary signal:**
- **Palo Alto / Snowflake / Cloudflare / DDOG** all down on the week, confirming the sector-wide multiples compression (not an ANT-specific story).
- **Small-cap AI startups** (public-tradable: SoundHound, C3.ai, BigBear, etc.) outperformed on the week, which is the **"junk rally"** pattern that typically marks a late-cycle wobble, not a bear turn.

**Sources:**
- [Decrypt — NVIDIA, AMD, Micron sink as Anthropic closes 17% above IPO price](https://decrypt.co/383669/nvidia-amd-micron-ai-stocks-sink-anthropic-ipo-price) `[secondary]`
- [Finimize — Anthropic IPO pops but AI stocks stay skittish](https://finimize.com/content/anthropics-ipo-pops-but-ai-stocks-stay-skittish) `[analysis]`
- [Finimize — Anthropic's big IPO didn't save the AI trade](https://finimize.com/content/anthropics-big-ipo-didnt-save-the-ai-trade) `[analysis]`
- [Kotak Neo — Anthropic falls below IPO price, -26.5% from debut](https://www.kotakneo.com/news/stocks/anthropic-share-price-falls-below-ipo-price-nasdaq-debut/) `[secondary]`

### Why it matters to you

- **Job lens:** **Public-market multiples compression leaks into private rounds within 30–60 days.** Series A/B/C rounds closing in **Dec 2026 – Feb 2027 will price 20–40% lower than the same company would have priced in September**. Positive translation for an applicant: **fewer competing offers from hyper-funded startups → the realistic Series A/B startups actually close hires and pay cash + reasonable equity**. Negative translation: **total comp at hypergrowth AI-native startups drops noticeably** (equity component).
- **Startup lens:** If you're raising in the next 90 days, **cut your ask by 25%** and raise against a lower valuation with a clean 3-year runway. If you're being approached by inbound investors, **take the lower-valuation term sheet over the higher-valuation one with aggressive liquidation preferences** — the LP sentiment toward AI is turning, and preferences stack fast.
- **Insight:** **Do not fire optimistic pitch-deck decks into this market.** The marginal partner across SC/USV/a16z saw their seed-stage AI book get re-marked this quarter and is defensive. Lead with: **real customer logo, measured retention, 70%+ gross margin**. If you don't have all three, go back and build them.

→ Cross-link: [`05` §3 — ANT lockup → 2027 attrition timeline](./05-career-and-startup.md#3-ant-lockup-timing)

---

## 5. Secondary rounds worth noting this week {#5-other-rounds}

- **Assort Health** — **$120M Series C** to expand patient-journey AI agents. Healthcare-vertical agent on the Decagon pattern. [[tracker](https://superpowerdaily.com/signals/funding)] `[aggregator]`
- **Steno (legal AI)** — **$49M Series C**, total capital to $150M. Vertical-legal agent, Harvey-pattern. [[tracker](https://superpowerdaily.com/signals/funding)] `[aggregator]`
- **LanceDB** — **$57.5M Series B**, Bessemer + Innovation Endeavors. Open-source vector / multi-modal DB — the "post-Pinecone" architectural layer. [[tracker](https://superpowerdaily.com/signals/funding)] `[aggregator]`

**Why it matters:** The week's funding is **all vertical-agent (Assort, Steno) or infra-pick-and-shovel (LanceDB)**. **No horizontal "AI chatbot for X" raise shows up on the list.** The category is dead for 2026-end Series A+.

→ Cross-link: [`05` §4 — portfolio target list update](./05-career-and-startup.md#4-portfolio-target-list)

---

## Lens roll-up for New & Emerging

- **Job:** Model ML + Assort + Steno all opening **~20–50 FDE-shaped roles each over the next 6 months**. LanceDB's $57.5M also opens **infra roles at a smaller company with more individual leverage**. Target application set: Model ML, Assort, Steno, LanceDB, Isomorphic + the five AI-for-science names ([`02` §1](#1-isomorphic-5b)).
- **Startup:** Isomorphic $5B says **AI-for-science still gets priced on science milestones**; Model ML + Assort + Steno say **vertical-agent is the live archetype**; LanceDB says **infra-adjacent open-source has fundability**. Everything horizontal / wrapper-style was absent from the funding week.
- **Insight:** **ANT below offer in six days is the private-market pricing signal of the quarter.** Expect Q1 2027 rounds to price 20–40% below Sept comps. Negotiate accordingly.
