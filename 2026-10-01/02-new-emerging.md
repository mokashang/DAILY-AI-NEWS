# New & Emerging — 2026-10-01

Funding stays barbell-shaped: **frontier-adjacent infra on one side, long-horizon-agent + vertical SaaS on the other.** The squeezed middle (generic LLM wrappers, undifferentiated "chat with your data") is openly deprecating. Three A/B announcements in the last 10 days make the barbell concrete.

Tags: `#funding #startups #agents #infrastructure #robotics #enterprise`

---

## 1. Sail Research $80M Series A · Rhoda AI $450M Series A (stealth exit) · Nexthop AI $500M Series B {#1-sail-rhoda-nexthop}

**What happened:** Three A/B rounds, three different barbell positions:

- **Sail Research — $80M Series A, Kleiner Perkins lead.** Focus: **long-horizon AI agent infrastructure**. Translation: the plumbing for agents that run for hours/days/weeks — memory, resumption, checkpointing, deterministic replay. This is the "fleet management" category *under* the application layer (where Dots sits). Signal: Kleiner leading a Series A at $80M is **unusually large** — the category is now considered A-fundable at near-B check size.
- **Rhoda AI — $450M Series A, out of stealth.** Focus: **FutureVision** platform for *robotic intelligence*. Signal: the embodied-agent / physical-AI thesis has survived the Q2 2026 "disembodied AI eats everything" narrative. Rhoda joins Physical Intelligence, Skild, and 1X in the "post-Figure wave" of well-capitalized robot-foundation-model startups.
- **Nexthop AI — $500M Series B.** Focus: **AI-switching / networking infrastructure** — the physical plumbing for AI data centers. Signal: the infra barbell weight is still rising; **Nexthop + CoreWeave + Crusoe + Lambda** is the "AI-infra starter kit" every CIO ends up budgeting against.

The **squeezed middle** (what *didn't* raise this cycle): generic LLM wrappers, non-vertical consumer chat apps, undifferentiated "AI-powered CRM." Flywheel: no moat → no retention → no pricing power → no funding.

**Sources:**
- [Crescendo AI — Latest AI Startup Funding News and VC Investment Deals 2026](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) `[aggregator]`
- [Crunchbase — North American Startup Funding Shattered Records in First Half of 2026, Driven by AI](https://news.crunchbase.com/venture/na-startup-funding-ma-shattered-records-ai-q2-2026/) `[secondary]`
- [Eqvista — AI Startup Fundraising Trends 2026 (Seed to Series B)](https://eqvista.com/ai-startup-fundraising-trends/) `[analysis]`

### Why it matters to you

- **Job lens:** Sail Research is a **~15–30 person company post-A** — the "first 20 engineering hires" window is open **through Q4 2026**. Comp: $180–230K base + 0.4–1.2% equity for an SDE joining as hire #10–20. **Email the CEO this week** (classic ~$500M post-money raised-recently founder is still reading their inbox for CS-grad applicants with on-topic projects). Rhoda AI is a sweeter chase if you have *any* robotics background — but their L2 base is **already $230–280K + equity** because the post-$450M A hiring bar is Bay-Area-rate from day one. Nexthop AI is where you go if the AI-infra lane in [ME.md](../ME.md) ("adjacent track: GridCARE / Crusoe / Sphere AI") is still live for you.
- **Startup lens:** Three concrete founder prompts the market just answered: (a) **"Can agent-infrastructure be an $80M Series A?"** — yes. (b) **"Is robotic foundation-model-plus-platform still fundable at mega-A even after the 2025 'disembodied AI' narrative?"** — yes. (c) **"Does AI networking still need its own category outside the hyperscalers?"** — yes. Taken together: *vertical and infrastructural specificity beats horizontal application* in the Oct 2026 funding environment. If you're pitching a startup in Q4, your deck's first slide should answer **"what layer / what vertical"** before anything else.
- **Insight:** The salient second-order effect is **the next 12 months of M&A**. Rhoda's $450M lets it buy 3–5 smaller robotic/foundation-model shops; Nexthop's $500M lets it roll up DC-networking startups; Sail will be an acquisition target for Anthropic or OpenAI inside 24 months (long-horizon memory + resumption is a feature the frontier labs need to ship, not build from scratch). For your startup-vs-job [ME.md](../ME.md) decision: **joining a Sail-shaped company at month 8 is a 24-month path to "exit via acqui-hire into Anthropic as a founding Solutions Engineer."** That's a legitimate path to the frontier lab that doesn't go through the Anthropic careers page.

→ Cross-link: [`05` §1 hiring map](./05-career-and-startup.md#1-comp-benchmarks) · [2026-09-30 §6 Ema Series B](../2026-09-30/02-new-emerging.md#1-ema-b).

---

## 2. The DevDay plugin economy — 4,000+ apps as a market signal {#2-devday-plugins}

**What happened:** OpenAI shipped DevDay with **4,000+ apps accessible to Dots** out of the gate. Within 48 hours, three second-order startups are already visible in launch Trajectory:

- **Dot-store directories** — curated / rated plugin listings, a la "best Dots for a legal associate" or "best Dots for an SDR." *Yelp for agents.*
- **Dot-pack bundles** — pre-configured sets of 5–8 Dots for a role (e.g. "founder's Dot pack" = calendar + email + CRM + Linear + travel + light analytics).
- **Dot-governance consoles** — enterprise administrators who need to grant / revoke app access across their org's Dots. **This is the biggest open wedge.**

Note: Plugin Extensions on top of Dots is **essentially the ChatGPT app-store surface** — a developer platform in the shape of OpenAI's commercial moat. If you ever thought "I wish I'd been there for the iPhone App Store launch," this is the closest 2026 analogue.

**Sources:**
- [Analytics Insight — OpenAI DevDay 2026](https://www.analyticsinsight.net/openai/openai-devday-2026-the-biggest-ai-announcements-explained) `[secondary]`
- [The Neuron Daily — Dots and ChatGPT's Agent OS](https://www.theneurondaily.com/p/openai-launched-dots-20-more-tools) `[aggregator]`
- [TechBuzz — DevDay 2026](https://www.techbuzz.ai/articles/openai-devday-2026-dots-agents-launch-new-funding-talks) `[secondary]`

### Why it matters to you

- **Job lens:** The 2026 version of "I shipped an iOS app in 2008" is **"I shipped a Dot that got 10K installs in Oct 2026."** This is a weekend-sized GitHub artifact that will land senior / staff engineering interviews at Anthropic, OpenAI, and the entire integrator vertical for the next 6 months. Specifically: ship a Dot that solves **a specific pain point for a specific role** (e.g., "L4 PM at a seed-stage company who's trying to pre-draft weekly status reports"). The point isn't the Dot — it's the *demonstrated-end-to-end* evidence.
- **Startup lens:** Three fundable wedges from the plugin economy — all **$5–20M-ARR possible inside 24 months**:
  1. **Dot governance for enterprises** — SSO, DLP, cost caps, approval workflows per Dot per user per team. Buyer: Head of IT at a 500–5,000-person enterprise. Will-they-pay: yes, $20–50/user/month.
  2. **Vertical Dot packs** — productized Dot bundles for specific roles (SDR, financial advisor, L&D specialist). Buyer: team or department lead. Will-they-pay: yes, $100–300/user/month with meaningful stickiness.
  3. **Dot analytics / A-B testing** — multi-Dot per-user experiments, cost-per-outcome. Buyer: ops / RevOps leaders. Will-they-pay: yes, $500–2000/month at mid-market scale.
- **Insight:** The *platform risk* here is real — OpenAI can (and historically does) crush any wedge that becomes too valuable by shipping it in-house. The founders who survive the next 24 months are the ones who build at the **cross-platform** layer (Dots + Anthropic subagents + Google Agent-Builder behind one admin console), not inside OpenAI's platform. **If your startup is Dots-only, your 2027 roadmap is "sell to OpenAI or die."**

→ Cross-link: [`01` §5 DevDay 48h](./01-big-lab-moves.md#5-devday-48h) · [`03` §3 ruling-post artifact](./03-practical-skills-and-tools.md#3-ruling-post).

---

## 3. The barbell visible by category {#3-barbell}

A snapshot of what's getting A/B funded in Sept–Oct 2026 vs what's not:

**Funded (barbell weights):**
- **Agent infrastructure** (Sail Research $80M · prior: Hyperbolic · Decagon ops layer)
- **Vertical enterprise agents** (Ema $77M Series B — enterprise SaaS replacement; prior Decagon / Sierra / Cognigy at CX)
- **Robotic / embodied AI foundation models** (Rhoda $450M · Physical Intelligence · Skild · 1X)
- **AI-specific networking + compute** (Nexthop $500M · Crusoe · CoreWeave · Lambda)
- **AI-first productivity primitives at agent-native scale** (Natural "Stripe for agents" from [2026-09-10 §4](../2026-09-10/02-new-emerging.md#2-natural-agent-payments))

**Not funded (squeezed middle):**
- Generic LLM wrappers with no vertical / no data moat
- Horizontal "AI copilot for everything" apps
- Pure-prompt-engineering tools without eval or governance surface
- Me-too chatbots without multi-model / multi-vendor abstraction

**Sources:**
- [Crescendo AI — Latest VC Investment Deals in AI Startups](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) `[aggregator]`
- [Crunchbase — H1 2026 AI Startup Funding Record](https://news.crunchbase.com/venture/na-startup-funding-ma-shattered-records-ai-q2-2026/) `[secondary]`

### Why it matters to you

- **Job lens:** Target the barbell. **Early engineer** at a Sail / Rhoda / Nexthop-shape company (first-20 hires, post-A, pre-B) is the single highest-expected-value seat for a CS grad in Q4 2026 — upside through equity, resume-quality through the funding velocity, learning-rate through the "small team, large problem" dynamics.
- **Startup lens:** If your founding idea sits in the squeezed middle, **pivot before you raise, not after.** The pre-seed check that funds a horizontal LLM wrapper in 2026 doesn't exist; investors have memory, and the 2024–2025 wrapper graveyard is fresh.
- **Insight:** The barbell will tighten as the frontier labs ship more product surfaces (Dots, LSVP, Claude Skills). The surviving middle will be the thin layer that *multi-vendor-abstracts* — the one place frontier labs can't credibly ship.

→ Cross-link: [`01` §5 DevDay 48h](./01-big-lab-moves.md#5-devday-48h) · [`05` §2 skill re-price](./05-career-and-startup.md#2-reprice).
