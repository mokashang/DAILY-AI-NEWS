# New & Emerging — 2026-09-20

Vertical Claude gets its capital-markets edition, Google puts agent-spend caps in an enterprise SKU (the first cloud lab to admit that agent bills are a real product problem), and the private-market funding narrative continues to bifurcate: **frontier + infra winners keep printing $B+ rounds; everyone else needs proof + a defensible data or IP moat** (Crunchbase / Qubit Capital both frame this consistently through September).

Tags: `#anthropic #verticals #wealthtech #gemini #enterprise #agents #cost-control #funding #frontier`

---

## 1. Claude for Financial Advisors — the anti-ads B2B answer to OpenAI Sponsored Agents {#1-claude-financial-advisors}

**What happened:** On **Sept 14–16**, Anthropic launched **Claude for Financial Advisors** — an AI layer that connects Claude to the tools wealth managers already use. Depth of the day-one integration list is the story:

- **Custodians / asset managers / wealthtech:** Charles Schwab, BlackRock, Vanguard, Addepar, Envestnet, iCapital, Orion, SS&C Black Diamond, Wealthbox, Wealth.com, Zocks.
- **Previously available (carried over):** Microsoft 365, Salesforce, DocuSign, Box, FactSet, S&P Global, Morningstar.
- **Coverage tasks:** research, meeting prep, portfolio reviews, documentation, prospect intake, compliance screening. **Human-in-loop preserved for** investment recommendations + client communications + other consequential decisions.
- **Pricing:** **~$70–120/user/month** (Claude Co-Work seat + Financial Advisors plug-in, plug-in itself is free). **First-of-month usage credit** for firms requesting a license before end of September.

This is Anthropic's **third vertical** in the [Legal → Small Business → Financial Advisors](../2026-05-13/00-tldr.md) cadence. Forbes framed it: **"Anthropic Launches Claude For Advisors With Schwab And BlackRock."**

**Sources:**
- [Bloomberg — Anthropic Expands Into Finance With Claude Tool Linking Advisors to Analytics](https://www.bloomberg.com/news/articles/2026-09-14/anthropic-pitches-new-claude-tool-for-financial-advisors) `[secondary]`
- [The Daily Upside — Anthropic Moves Deeper into Financial Services with Claude for Advisors](https://www.thedailyupside.com/advisor/industry-news/anthropic-moves-deeper-into-financial-services-with-claude-for-advisors/) `[secondary]`
- [WealthManagement.com — Anthropic Launches Claude for Financial Advisors Tool](https://www.wealthmanagement.com/artificial-intelligence/anthropic-launches-claude-for-financial-advisors) `[secondary]`
- [Forbes (Markman) — Anthropic Launches Claude For Advisors With Schwab And BlackRock](https://www.forbes.com/sites/jonmarkman/2026/09/16/anthropic-launches-claude-for-advisors-with-schwab-and-blackrock/) `[secondary]`
- [Wealth Solutions Report — Anthropic Launches Claude For Financial Advisors](https://www.wealthsolutionsreport.com/anthropic-launches-claude-for-financial-advisors/) `[secondary]`
- [Global Banking & Finance — Anthropic targets financial advisers with new Claude tool](https://www.globalbankingandfinance.com/anthropic-targets-financial-advisers-new-claude-tool/) `[secondary]`
- [Lucidate substack — Claude for Financial Services (walkthrough)](https://lucidate.substack.com/p/claude-for-financial-services) `[analysis]`

### Why it matters to you

- **Job lens:** The 12-connector day-one integration list = **12 FDE / Solutions Engineer counterparties Anthropic needs to staff against**. Match roles to connectors: someone owns the Addepar integration, someone owns the Envestnet integration, and so on. **Search "Anthropic Solutions Engineer wealth" + "Anthropic FDE financial services"** on the careers page every 72 hours through October — these roles are opening in batches. If you have any capital-markets / RIA / wealthtech exposure (even a summer at a broker-dealer), *lead* with it in cover letters — it's the differentiator for these roles vs. the generic-FDE applicant pool.
- **Startup lens:** The wedge unlocked is **compliance-first Claude adoption in RIAs** — the ~15,000 US RIAs manage $128T AUM, are mostly under 50 employees, and can't build agent infra themselves. Founder plays: (a) **AI Compliance Officer** as a productized service — sell to sub-100-employee RIAs the SEC-audit-ready log + guardrail suite around Claude for Financial Advisors; (b) **automated compliance-screening add-ons** to the Claude Financial Advisors seat (the plug-in is free — the value shifts to the workflow layer); (c) **niche competitors** to Zocks (meeting-transcript-to-CRM) that focus on the sub-$1B RIA — Zocks has raised enough that mid-market is well-served but the long-tail isn't.
- **Insight:** The connector list is a **kingmaker signal.** Schwab, BlackRock, and Vanguard were named first — Fidelity was *not*. Fidelity is famously slow to integrate outside AI; expect a Fidelity-native competitor (or a Google-Cloud-plus-Fidelity story) inside 12 months. Ditto Morgan Stanley Wealth Management ($4.5T AUM), which has its own internal LLM ("AskResearchGPT"). This map is the **wealthtech vendor-selection playbook of 2027** — if you're pitching startups in this space, memorize which side of the Anthropic connector list each incumbent falls on.

→ Cross-link: [`01` §5 OpenAI Sponsored Agents — the ads-side counterpoint](./01-big-lab-moves.md#5-openai-sponsored-agents) · [`05` §1 hiring map](./05-career-and-startup.md#1-hiring-map).

---

## 2. Gemini Enterprise ships agent-spend caps + $0 base tier + up-to-20% token discounts {#2-gemini-enterprise}

**What happened:** Google shipped a **new Gemini Enterprise pricing structure** in mid-September:

- **Pay-as-you-go pricing** on the API tier (was flat-fee-only).
- **Up to 20% token discounts** at volume.
- **Monthly caps on agent spending** — configurable per-agent, published as a first-class product feature.
- **$0 base subscription tier** — Gemini Enterprise no longer requires an upfront commit.
- Product framing: Gemini as a **"supervised digital worker"** across files, screens, documents, code, and Google services.

Google is also opening the **combine-built-in-tools-with-custom-function-calls-in-one-API-request** pattern — meaning you don't have to choose between Google's tool ecosystem and your own; you send both in a single request. This is *convergent* with Anthropic's Managed Agents primitive but with **Google-Cloud-native billing controls Anthropic hasn't shipped yet.**

**Sources:**
- [blog.mean.ceo — Google Gemini News, September 2026 (Startup Edition)](https://blog.mean.ceo/google-gemini-news-september-2026/) `[aggregator]`
- [Google DeepMind Blog](https://deepmind.google/blog/) `[primary]`
- [Suprmind — Google Gemini 2026: Models, Features, Pricing, and Accuracy](https://suprmind.ai/hub/gemini/) `[analysis]`

### Why it matters to you

- **Job lens:** The addition of **monthly caps on per-agent spending** as a *product feature* creates an under-served role at Google Cloud + at enterprise clients: **"Agent FinOps engineer"** — someone who owns the per-agent budget, spend-alert, and cost-attribution stack the same way SREs own uptime. Levels.fyi hasn't priced this yet; my guess is **$180K–$260K base + refresh** for a Google-Cloud-native FinOps-plus-agent-ops hybrid. Watch job req titles containing "FinOps" + "agent" over the next 60 days.
- **Startup lens:** Google's move is a **tell that agent-bill runaway is happening at scale** across their enterprise base. That means the **agent-cost-observability / router-with-guardrails / spend-cap-as-a-service** category has *cross-cloud* demand (Google's move + Anthropic's June 15 metering means both major frontier stacks now bill programmatically). Founder wedges: (a) an **agent-observability SaaS** that plugs into Anthropic + OpenAI + Gemini + Bedrock and gives you one dashboard with per-agent budgets; (b) a **prompt-cache-optimization service** priced on % of savings; (c) **agent-cost linting** for CI — refuse to merge a PR that increases per-request agent cost beyond a budget threshold. All three are $5–20M ARR wedges inside 18 months.
- **Insight:** The $0 base tier is a **pricing weapon aimed squarely at Anthropic's Team / Enterprise seats** — Google is willing to give away Gemini Enterprise access to grow token-billed revenue, betting that once agents are integrated the switching cost is prohibitive. This is Amazon-Prime economics applied to enterprise AI: **the CapEx is Google's, the elasticity is the customer's.** Anthropic's response will tell you a lot — if Anthropic drops price on Claude for Financial Advisors's seat model in the next 60 days, Google's move worked.

→ Cross-link: [`03` §1 context engineering — the technique that lowers your Gemini bill without changing model](./03-practical-skills-and-tools.md#1-context-engineering) · [WATCHLIST — Gemini pricing thread](../WATCHLIST.md).

---

## 3. Frontier funding — Cognition ~$40B talks, Poolside $12B with $1B NVIDIA, Perplexity in $30B+ talks with NVIDIA {#3-cognition-poolside}

**What happened:** The private-market layer keeps concentrating on frontier + AI-infrastructure names:

- **Cognition (Devin)** entered **early talks with investors at ≥$40B valuation** (Bloomberg, August), up from **$26B in May 2026** ([2026-05-12/00](../2026-05-12/00-tldr.md)).
- **Poolside AI** — **NVIDIA invested $1B for a direct equity stake at a $12B valuation** and separately paid **$6B for a non-exclusive technology licensing deal.**
- **Perplexity** — **NVIDIA in talks to invest at $30B+ valuation** (late August), up from ~$20B (Sept 2025) → ~$23B (Series E-6, Jan 2026).

Meanwhile, seed to Series B tightened. **88% of AI-related startup funding YTD ($319B) has gone to US-headquartered companies.** **AI Cluster Cloud attracts ~50% of AI-infra capital from ~30% of deals** — the biggest checks going to fewer, bigger names.

**Sources:**
- [Wikipedia — Cognition AI](https://en.wikipedia.org/wiki/Cognition_AI) `[aggregator]`
- [BigGo Finance — Nvidia Bets Billions on Perplexity and Poolside](https://finance.biggo.com/news/7eba8002-05cc-427e-b7f2-3cd70207c09b) `[secondary]`
- [Value Add VC — Perplexity AI: Revenue, Funding & Valuation (2026)](https://valueaddvc.com/company/perplexity-ai) `[analysis]`
- [Wikipedia — Poolside AI](https://en.wikipedia.org/wiki/Poolside_AI) `[aggregator]`
- [Wellows — 85 Hottest AI Startups to Watch in 2026](https://wellows.com/blog/ai-startups/) `[analysis]`
- [Crunchbase News — The AI Startup Funding Boom Is Not A Global Phenomenon](https://news.crunchbase.com/venture/us-ai-startup-funding-boom-data/) `[secondary]`
- [Qubit Capital — AI Startup Trends 2026](https://qubit.capital/blog/ai-startup-fundraising-trends) `[analysis]`

### Why it matters to you

- **Job lens:** Cognition at $40B means **Devin's engineering / applied-AI / customer-eng bench needs to double this cycle** just to justify the multiple. The team is famously small — even a modest scale plan is 100+ hires. Devin-adjacent skills (agent orchestration + long-horizon planning + verified-code-execution primitives) are what interviews will screen on. If you have a "coding agent" side project on GitHub, this is the two months to publish and cross-post.
- **Startup lens:** NVIDIA's Perplexity + Poolside pattern is the **"chip-maker-as-anchor-LP"** move — Jensen picking commercial-model + coding-model bets that keep GPUs sold. It replicates SoftBank Vision Fund 1 dynamics but with a strategic instead of speculative return function. If you're a founder in a category NVIDIA cares about (models, inference, agent-infra, robotics), a **strategic round from NVIDIA is available at a valuation premium** — and one you should structure carefully (right of first refusal on chips vs. lock-in trade-off).
- **Insight:** The **Perplexity → $30B+** move is worth noting for one specific reason: Perplexity's *actual* revenue is small relative to that number, and its Comet browser has struggled against Chrome/Edge Copilot. The valuation reads as **NVIDIA underwriting a "consumer-AI-runs-on-GPUs" call option** — not a pure DCF. Reading NVIDIA's investment book is the *sharpest* window into what Jensen thinks the next 3 years look like: **Cognition (agentic coding), Poolside (coding models), Perplexity (consumer search + browser), OpenAI (frontier + hardware), Anthropic (frontier + verticals)** — all GPU-heavy, all long-tail-inference. The pattern says: **inference is going up, not down, over the next 24 months, even with Fable 5.1's cache-read discount.**

→ Cross-link: [`01` §1 Anthropic Nasdaq — the public-market side of the same barbell](./01-big-lab-moves.md#1-anthropic-nasdaq) · [WATCHLIST — Cognition raise thread](../WATCHLIST.md).

---

## 4. Micro-signals — worth 30 seconds each {#4-micro-signals}

- **OpenAI DevDay 2026 — Sept 29, Fort Mason SF.** T-9 days. Applications closed July 10; keynote livestreamed. Also: **DevDay Exchanges** in Bengaluru, Tokyo, Seoul, Paris, Berlin, London, São Paulo, Mexico City = the *most globally distributed* AI dev-conference footprint of 2026. Sources: [OpenAI DevDay 2026](https://openai.com/index/devday-2026/) `[primary]` · [gadgetbond](https://gadgetbond.com/openai-devday-2026-september-29-san-francisco/) `[secondary]`.
- **Paul Christiano joined the OpenAI Foundation Board (Sept 9).** ARC founder + alignment-heavyweight moving to OpenAI's non-profit governance seat = **the alignment community's second-highest-signal internal move of 2026** (after Karpathy joining Anthropic pre-training, [2026-05-22](../2026-05-22/)). Watch whether the OpenAI Foundation publishes an alignment mandate in Q4. Source: [OpenAI Newsroom](https://openai.com/news/company-announcements/) `[primary]`.
- **OpenAI supports California youth AI safety bill (Sept 8).** OpenAI's first *explicit* endorsement of state-level AI-safety legislation. Notable because California is Anthropic's home turf and the AB-1064-successor bills will define what "responsible AI" looks like at both companies' IPOs. Source: [OpenAI Newsroom](https://openai.com/news/company-announcements/) `[primary]`.
- **Google Gemini Omni — starting with video.** DeepMind's family for "creating from mixed inputs," beginning with video. This is the [Gemini Omni thread from May](../2026-05-19/00-tldr.md) crystallizing into a product line. Source: [DeepMind — News](https://deepmind.google/blog/) `[primary]`.
- **PORTS-Pike (Ohio) — OpenAI's next data-center site.** Partners: SB Energy, NVIDIA, DoE. Adds to the ~50 GW OpenAI is committed to (per [2026-05-21/01 §Colossus](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus)). Long-cycle infra story: watch for the announcement of the local hiring wave (typically 500–2,000 roles for a site of this scale). Source: [OpenAI Newsroom](https://openai.com/news/company-announcements/) `[primary]`.
- **China State-TV attacked Anthropic's privacy overhaul (mid-Sept).** Framing: "US Intel data sharing risk." First state-media attack on Anthropic specifically = Anthropic has arrived as a **first-tier frontier lab** in geopolitical framing. Source: [AI Weekly — Anthropic News Today, September 19](https://aiweekly.co/ai-news-today/anthropic-news) `[aggregator]`.
- **GitHub trending in agent-infra:** **Claude Code**, **Tencent BrowserSkill**, **affaan-m/ECC**, **Hermes-Agent**, **NanoBot**, **mem0**, **thedotmack/claude-mem**, **SuperMemoryAI/supermemory**, **n8n** — the memory + skill + local-first stack keeps consolidating. Sources: [OSSInsight — Trending AI](https://ossinsight.io/trending/ai) `[aggregator]` · [caramaschiHG/awesome-ai-agents-2026](https://github.com/caramaschiHG/awesome-ai-agents-2026) `[aggregator]`.

### Why they matter to you (compressed)

- **Job:** Add "OpenAI Foundation" and "PORTS-Pike" to your Anthropic + OpenAI careers-page watchlist.
- **Startup:** The memory + skill + local-first GitHub cluster is a *founder-catalog* — pick one repo, contribute meaningfully, use the contribution as your Anthropic-application signal.
- **Insight:** State-media attention to Anthropic + explicit legislative support at OpenAI = **the two labs are being *treated* like peer public entities before either files an S-1.** That's a leading indicator of a smooth listing for both.

---
