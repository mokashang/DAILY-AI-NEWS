# New & Emerging — 2026-09-29

Two structural shifts landed at once: **MCP became public infrastructure** (Anthropic donated it to the Linux Foundation last December, and this quarter the *vertical* MCP servers arrived — TradingView, Lofty, next), and **Meta made its enterprise pivot** with Muse for Small Business and MongoDB's CJ Desai to lead the enterprise platform. Underneath: **the Series A funnel is narrower and jumboer** — Profound $180M, Arcee $150M, Temporal $550M — all AI-adjacent, all at valuations that would have been Series B math in 2024.

Tags: `#mcp #standards #agents #meta #smb #funding #barbell #verticals`

---

## 1. MCP grows up as public infrastructure {#1-mcp-grows-up}

**What happened:** Two MCP-server launches this week, both from vertical incumbents, both signaling that MCP has crossed the "AI-lab tooling" threshold into "public infrastructure that any B2B company deploys as a matter of course":

- **Sept 28 — Lofty MCP Server** for real-estate brokerages. Secure connection layer between Lofty's platform, brokerages' custom AI agents, and other MCP-compatible AI tools.
- **Sept 16 — TradingView MCP Server** (public beta) for Essential-tier-and-above users. Connects TradingView accounts to Claude across web/desktop/mobile/Claude Code, plus other MCP-compatible assistants.

**Adoption numbers to internalize:**
- **10,000+ MCP servers deployed in production** (as of mid-2026)
- **97M+ MCP SDK downloads per month**
- **December 2025:** Anthropic donated MCP to the **Linux Foundation's Agentic AI Foundation** — MCP is now vendor-neutral, community-governed.

**Sources:**
- [Manila Times / GlobeNewswire — Lofty Launches MCP Server to Give Brokerages an Open Foundation for Their AI Strategy](https://www.manilatimes.net/2026/09/28/tmt-newswire/globenewswire/lofty-launches-mcp-server-to-give-brokerages-an-open-foundation-for-their-ai-strategy/2434139) `[primary]`
- [TradingView Blog — MCP Server public beta](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[secondary]`
- [Agentic AI Foundation (Linux Foundation) — MCP Is Growing Up](https://aaif.io/blog/mcp-is-growing-up) `[primary]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`
- [TechCrunch — AI's most important protocol is getting a little bit easier to use (July 20)](https://techcrunch.com/2026/07/20/ais-most-important-protocol-is-getting-a-little-bit-easier-to-use/) `[secondary]`
- [Wikipedia — Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) `[secondary]`

### Why it matters to you

- **Job lens:** A **public, vertical MCP server** on your GitHub is the highest-signal single artifact you can publish this week for an FDE / AI-Integration Engineer / Solutions Engineer role. **Concrete recipe:** pick a vertical (legal, real estate, healthcare, finance, e-commerce) you have any prior context in; identify one canonical workflow in that vertical (e.g., pulling comparable-sales data for a real-estate agent, or filing a legal complaint); build a 3-tool MCP server that surfaces that workflow to Claude / GPT / Gemini; publish with a README, a 30-sec demo GIF, and a 5-case eval. This is the **2026-09 version of the "portfolio project"** — and unlike a chatbot, it demonstrates *distribution* thinking (you understand where the AI meets the customer's real system).
- **Startup lens:** The **10,000+ MCP servers / 97M/mo SDK downloads** number is the tell that MCP is past the "will it stick?" phase and into the "who wins the wrapper economy?" phase. Two categories now fundable: (a) **MCP-server-as-a-service for verticals** — a Segment.com-style platform that lets a mid-market SaaS vendor ship an MCP server without hiring an AI team ($5–20M ARR wedge, 24-month build); (b) **MCP-security / MCP-observability / MCP-governance** — every enterprise deploying 10+ MCP servers needs a control plane. First mover advantage; category unclaimed. This is a **cleaner startup story than "another agent framework"** because MCP is now a standard, not a bet.
- **Insight:** The pattern to remember: **standards go through three phases — lab-tooling → public infrastructure → regulated substrate.** MCP is finishing phase 2 and entering phase 3 this quarter (Linux Foundation donation last December + Anthropic S-1 disclosures = regulatory pressure inevitable). When a standard enters phase 3, the *dominant business model shifts from selling the standard to selling compliance-with-the-standard.* That's the wedge.

→ Cross-link: [`01` §1 Anthropic S-1](./01-big-lab-moves.md#1-anthropic-s1-leak) · [`03` §4 shipping your own MCP server](./03-practical-skills-and-tools.md#4-ship-an-mcp-server).

---

## 2. Meta Muse for Small Business — Zuckerberg's enterprise pivot lands {#2-meta-muse-sb}

**What happened:** Two Meta announcements today (Sept 29) that, taken together, are the clearest sign in 12 months that Meta's AI strategy has moved beyond consumer:

- **Muse for Small Business** ships today. Connects the Muse agent to **Asana, Zoom, Intuit, Box, Canva, Slack, and Meta Ads** (professional Instagram + Facebook profiles). Positioned squarely against Anthropic's Claude for Small Business (May 13) and OpenAI's Business tier.
- **Meta Enterprise Platform** announced with **MongoDB CEO CJ Desai** leading it. Will include a Muse agent, a business agent, and a coding tool.

Backdrop: **Muse (the consumer app) launched Sept 8; 3.4M downloads in three weeks.** Meta's fastest AI product ramp. Sept 25 TechCrunch framing: "Meta is putting its muscle behind Muse as the AI app takes off." Meta's May 20 layoff (~8,000, 10% of workforce) freed the headcount for this rebuild.

**Sources:**
- [CNBC — Meta launches Muse for Small Business as Zuckerberg pushes beyond consumer AI market](https://www.cnbc.com/2026/09/29/meta-launches-muse-for-small-business-zuckerberg-pushes-enterprise-ai.html) `[secondary]`
- [CNBC — Meta's Muse agent is attacking one of the economy's most profitable weak spots (Sept 27)](https://www.cnbc.com/2026/09/27/meta-muse-ai-personal-agent.html) `[secondary]`
- [TechCrunch — Meta is putting its muscle behind Muse as the AI app takes off (Sept 25)](https://techcrunch.com/2026/09/25/meta-is-putting-its-muscle-behind-muse-as-the-ai-app-takes-off/) `[secondary]`
- [TechCrunch — Everything new coming to Meta's AI agent Muse (Sept 23)](https://techcrunch.com/2026/09/23/everything-new-coming-to-metas-ai-agent-muse/) `[secondary]`
- [Meta — Introducing Muse Spark](https://about.fb.com/news/2026/04/introducing-muse-spark-meta-superintelligence-labs/) `[primary]`

### Why it matters to you

- **Job lens:** The **CJ-Desai-to-lead-Meta-enterprise** hire is your target signal. When a MongoDB-veteran CEO joins to build an enterprise platform inside a consumer company, they hire **the same shape of team they know how to hire**: enterprise solutions engineers, developer-relations, partner engineering, VP-of-eng-for-a-specific-vertical. That team will be posted inside 30 days. Watch Meta's careers page under "AI Products" / "AI Infrastructure" starting mid-October. This is a **less-crowded lane than Anthropic Solutions or OpenAI FDE** because Meta hasn't been on the target list for AI-Solutions candidates all year — arb window open through EOY.
- **Startup lens:** **Muse for Small Business's integration list is your competitive map.** Asana, Zoom, Intuit, Box, Canva, Slack, Meta Ads — those seven surfaces are the *default* small-business software stack. Any startup building for that stack has to now assume **Muse is a default option for their customer.** But: Muse being a default means Muse being a *general* agent — a narrower, task-specific agent that goes deeper on one workflow can still win. Reposition your pitch as "Muse-plus-depth" rather than "Muse-competitor."
- **Insight:** The **consumer-Muse-to-enterprise-Muse** sequence is a repeat of Meta's WhatsApp playbook — win on distribution, add monetization behind the wall. If it works, it will do so at a scale Anthropic (no consumer surface) and OpenAI (paid-only consumer) can't match. The **distribution asymmetry** between the three now looks like: Meta owns free-consumer + emerging-SMB; OpenAI owns paid-consumer + enterprise; Anthropic owns depth-with-developers + regulated verticals. Three different companies now, on three different economic models.

→ Cross-link: [`05` §1 hiring map](./05-career-and-startup.md#1-safety-repriced).

---

## 3. The Series A funnel gets jumboer — Profound / Arcee / Temporal {#3-funding-barbell}

**What happened:** The last two weeks of September 2026 saw three funding rounds that redefine the Series A/B ceiling in AI:

- **Profound — $180M Series D at ~$1.8B valuation.** AI marketing software. This is a *fifth-round* at 10× revenue, in a subcategory (AI-native marketing tooling) that didn't exist as an investable category two years ago.
- **Arcee AI — $150M Series B at >$1B valuation.** Open-source-model / small-model specialist. Model-choice-and-fine-tuning-as-a-service. Valuation jumped from ~$300M at Series A ~14 months prior.
- **Temporal Technologies — $550M for AI infrastructure.** Durable-execution runtime, positioning itself as the substrate below agent frameworks. The largest single AI-infrastructure round of Q3.

Broader trend: **>70% of Series A rounds of $100M+ went to AI-focused startups in Q3.** Median Series B for AI companies now ~$143M valuation (Eqvista). Investors demand *proof* — the 2023–2024 hype-cycle bar is gone.

**Sources:**
- [Crunchbase News — Jumbo-Sized Series A Rounds Are On The Rise](https://news.crunchbase.com/venture/megaround-seriesa-ai-chips-robotics-2026/) `[secondary]`
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: Large Rounds For AI Infrastructure, Space Tech And Investment Management Lead](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-space-fintech-temporal/) `[secondary]`
- [Eqvista — AI Startup Fundraising Trends 2026 (Seed to Series B)](https://eqvista.com/ai-startup-fundraising-trends/) `[analysis]`
- [CRV — AI Startup Funding: What Investors Look for in 2026](https://www.crv.com/content/ai-startup-funding) `[analysis]`

### Why it matters to you

- **Startup lens:** The **new Series A ceiling is functionally a Series B ceiling** — $100M rounds are now table stakes for a hot AI-native SaaS at ~$500M–$1B post. That's the good news. The bad news: the **proof bar** to clear it is real revenue (not usage, not waitlist). Profound's $1.8B at Series D implies ARR in the $70–150M range to justify the multiple. If your startup wedge doesn't have a credible path to $10M ARR inside 18 months, the jumbo-round door is closed to you. The **wedge test**: name your first 5 paying enterprise customers by revenue tier and average contract value, and if you can't, the round shape you should be raising is *seed extension*, not *jumbo Series A*.
- **Job lens:** These three companies (Profound, Arcee, Temporal) are all hiring at exactly the seniority band a CS grad + 1–2 yr experience can hit — **Applied AI Engineer, ML Engineer, Solutions Engineer, Growth Engineer.** All three are in the **~50–200 headcount** band where a hire has real optionality (comp band $180K–$260K + meaningful equity). The under-covered lane is **Temporal** — durable-execution engineering is a rare skillset and the company will lean into distributed-systems hires more than AI-generalists.
- **Insight:** The **funding barbell** from the Sept 10 edition ([`02` §1](../2026-09-10/02-new-emerging.md#1-funding-barbell)) has hardened: **frontier + vertical-with-proof funds; everything else waits.** But there's a new *third* pole emerging — **AI infrastructure with recurring revenue** (Temporal is the paradigmatic example) — that is being priced like frontier but with SaaS margins. If you're a founder, this is the third barbell arm and the most defensible.

→ Cross-link: [`01` §2 the $518B compute stack](./01-big-lab-moves.md#2-518b-buildout).
