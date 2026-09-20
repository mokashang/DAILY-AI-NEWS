# New & Emerging — 2026-08-02

New models, protocols, startups, funding, and second-tier tools that will matter in 30–90 days. Curated for a CS grad student pursuing startups + SDE/MLE/AI roles.

---

## 1. Palo Alto Unit 42 documents DeepSeek + Hermes Agent used autonomously against 460+ targets — Claude and OpenAI refused, DeepSeek did not {#1-deepseek-hermes}

**What happened.** On **2026-07-30**, Palo Alto Networks' **Unit 42** published a detailed writeup of an AI-enabled autonomous cyber-attack campaign attributed to `knaithe` / `KnYuan`, a **Zhuhai, China–based, Chinese-speaking threat actor**.

The technical setup:

- **DeepSeek** served as the reasoning agent (decision-making).
- **Hermes Agent** — an open-source agentic AI framework — served as the orchestrator.
- **Telegram** was the human-to-agent control surface: a single command initiated a **scan → research → exploit** pipeline against **460+ internet-facing targets** (largely across Asia).
- The operator largely stepped back after issuing the initial command; the pipeline **enumerated targets, sourced public exploits, and attempted exploitation autonomously**.

**The finding that matters for the industry.** Unit 42 explicitly documents that **Claude and OpenAI refused the offensive requests. DeepSeek did not.** This is the **first widely-cited empirical writeup** where an in-the-wild campaign lets us point at safety refusals as a **defensive artifact with real teeth**, not a lab benchmark line.

**Sources.**
- [Chinese-Speaking Threat Actor Harnesses AI Models for Autonomous Cyberattacks — Unit 42 (Palo Alto Networks)](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/) [primary]
- [Chinese Hacker Commands DeepSeek via Telegram to Launch Autonomous Attacks — The Hacker News](https://thehackernews.com/2026/07/chinese-hacker-commands-deepseek-via.html) [secondary]
- [DeepSeek Ran Autonomous Cyberattacks That Claude and OpenAI Safety Controls Blocked — TechTimes (Aug 1)](https://www.techtimes.com/articles/322582/20260801/deepseek-ran-autonomous-cyberattacks-that-claude-openai-safety-controls-blocked.htm) [secondary]
- [Hacker uses DeepSeek AI to autonomously attack vulnerable servers — BleepingComputer](https://www.bleepingcomputer.com/news/security/hacker-uses-deepseek-ai-to-autonomously-attack-vulnerable-servers/) [secondary]
- [Unit 42 uncovers AI-enabled autonomous hacking campaign — IT Brew](https://www.itbrew.com/stories/unit-42-uncovers-ai-enabled-autonomous-hacking-campaign) [secondary]

**Why it matters to you.**

- **Job.** **Agentic-security engineer** is the exact role that just became easier to sell in an interview loop — you can point at this writeup as the *why*. The specific portfolio artifact that lands: a **small reproduction of the "single Telegram command → agent pipeline" architecture, safely** (e.g., against your own CTFd instance or a permissioned pentest lab), plus a **cost + refusal-rate comparison across Claude / GPT / DeepSeek / a local model**. That maps to at least three role families — **AI-security research** (Anthropic Frontier RT, Google DeepMind Safety), **enterprise AI-red-team consulting** (Google Cloud, Deloitte, PwC), and **CISO-side agent evaluation** (banks, telcos, GRC startups).
- **Startup.** **The "safety-refusals as commercial artifact" pitch is now live** — a two-sentence version: *"we help enterprise buyers pick the model whose refusals are worth something, and we run the eval quarterly."* The competitor to price against is the CISO's incumbent GRC tool (Vanta / Drata) which doesn't currently ship an AI-model-refusal-benchmark. The wedge is a **standardized enterprise-facing "refusal battery"** that a CISO can hand to procurement.
- **Insight.** For Anthropic and OpenAI, this is the **best marketing they will get all year** — a **third-party threat-intel writeup** confirming their controls hold under real adversarial pressure. Expect both to cite Unit 42 in **RFP responses** for the next two quarters. The **narrative pairing** with Anthropic's Frontier Red Team publication two days earlier ([`01` §4](./01-big-lab-moves.md#4-anthropic-frontier-red-team)) is a playbook, not a coincidence — study the sequence.

`#security #agents #deepseek #hermes-agent #safety-value`

---

## 2. California SB 942 (as amended by AB 853) operative today — C2PA provenance mandatory for 1M+ user GenAI providers {#2-sb-942}

**What happened.** As of **2026-08-02**, the **California AI Transparency Act (SB 942, amended by AB 853)** is operative. Generative-AI providers with **1M+ California monthly users** must, at minimum:

- Embed **C2PA-compatible content-provenance metadata** in AI-generated images, video, and audio.
- Offer a **free public AI-detection tool**.
- Allow users to add a **visible AI-generated label** to output.
- **Not strip provenance metadata**, and **not distribute tools designed to strip it**.

**AB 853** additionally extended the same regime to **large online platforms, generative-AI hosting platforms, and capture-device manufacturers** — meaning the requirement propagates through the stack, not just to the model providers.

The August-2 alignment is deliberate: it matches **EU AI Act Article 50** synthetic-content marking / deepfake-labeling requirements ([`01` §1](./01-big-lab-moves.md#1-eu-ai-act)), giving providers a **single compliance target** across the two largest regulated markets.

**Sources.**
- [SB 942: California AI Transparency Act — Digital Democracy (CalMatters)](https://calmatters.digitaldemocracy.org/bills/ca_202320240sb942) [primary]
- [Bill Text — SB-942 California AI Transparency Act — LegInfo](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202320240SB942) [primary]
- [California AI Transparency Act (SB 942): 2026 Compliance Guide — AI Laws by State](https://www.ailawsbystate.com/blog/california-ai-transparency-act-sb-942) [analysis]
- [California AI Transparency Law: What Businesses Need to Disclose — Secure Privacy Blog](https://secureprivacy.ai/blog/california-ai-transparency-law) [analysis]

**Why it matters to you.**

- **Job.** **Provenance / trust-and-safety engineer** at any of the major GenAI platforms is now a real budgeted headcount, not a policy slot — the audit deadline is *now*. The concrete skill stack that maps: **C2PA spec** ([content credentials](https://c2pa.org/)), **watermarking research** (SynthID, Meta's Stable Signature), and **detection-tool product design**. The portfolio artifact: a **repo demonstrating C2PA sign-and-verify on an AI-generated media pipeline**, with a **detector API endpoint** and a per-request cost log. That single repo also positions you for the **EU Article 50 side** — same underlying skill.
- **Startup.** Two openings just appeared: (a) **turnkey C2PA compliance for the second-tier GenAI providers** who aren't going to build their own pipeline for a CA + EU compliance line item; (b) **detection tool as a public-facing brand exercise** — the largest providers have to build these, and the enterprise-brand version ("here's the detector that certifies this image is real") is a defensible wedge. Note SB 942 also requires the ability to **remove provenance is prohibited**, which locks the format in — no race-to-the-bottom competitor can strip it as a feature.
- **Insight.** **This is the second regulatory chess move that lines up the C2PA standard as the de facto global provenance format** (EU Article 50 + CA SB 942 + Adobe/Microsoft/Sony pushing it in-product). If you had a lingering doubt about picking C2PA vs. an alternative for a personal project, that doubt is now resolved. Also worth noting: **provenance requirements land on the *output* side of the model, not the model itself** — this is easier to comply with than most people think, and easier to add as a feature to an existing product than to retrofit at inference time.

`#california #sb-942 #c2pa #provenance #ab-853`

---

## 3. MCP 2026-07-28 stateless spec — first weekend of shipped SDKs {#3-mcp-stateless-shipped}

**What happened.** The **Model Context Protocol 2026-07-28 specification** — flagged in [2026-07-25 §4](../2026-07-25/00-tldr.md) as "shipping Monday" — **shipped on July 28** with **all four Tier-1 SDKs** (Python, TypeScript, C#, Java) supporting it same-day. This weekend is the first weekend where the shipped spec is generally available.

The five changes to internalize:

1. **Stateless protocol core.** The `initialize` / `notifications/initialized` handshake is gone. Every request carries its **protocol version + client capabilities in `_meta`**. The **session header is gone.**
2. **`Mcp-Method` and `Mcp-Name` headers** for L7 routing — gateways route on header values instead of inspecting the request body. Servers now sit behind a **plain round-robin load balancer**; no sticky sessions, no shared session store.
3. **Cacheable list / resource results** with **`ttlMs`** + **`cacheScope`** so clients know how long a result is fresh. CDN-friendly.
4. **New primitives**: **MCP Apps** (bundled experiences), **Tasks** (long-running operations), **Server Cards** (self-describing metadata for discovery).
5. **OAuth 2.1** as the connection-time auth model; **Multi Round-Trip Requests** for streaming and long-poll patterns; **formal extensions framework** so vendors can layer without forking the spec.

**Sources.**
- [The 2026-07-28 Specification — Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/) [primary]
- [The 2026-07-28 MCP Specification Release Candidate — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) [primary]
- [Key Changes — Model Context Protocol changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) [primary]
- [MCP Just Went Stateless — What the 2026 Spec Changes About Scaling on App Service — Microsoft Community Hub](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) [secondary]
- [MCP 2026-07-28: From Local Tool to Distributed Protocol — Agentic AI Foundation](https://aaif.io/blog/mcp-2026-07-28-whats-changing-and-how-to-migrate) [analysis]
- [MCP 2026 Roadmap: Stateless Core, Extensions & Enterprise Readiness — Obot](https://obot.ai/blog/mcp-is-growing-up-the-2026-roadmap-takes-shape/) [analysis]

**Why it matters to you.** Full migration steps + skill-map are in [`03` §1](./03-practical-skills-and-tools.md#1-mcp-stateless-migration). Short version:

- **Job.** MCP-migration engineers are being paid this week; this is the highest-leverage 2–3 day skill investment of the summer. Any public-repo migration on a real (even toy) MCP server is a **first-page portfolio artifact** for at least 90 days.
- **Startup.** The **compatibility-shim layer** (dual-serve old + new spec for enterprise clients that can't migrate on July 28) is a two-week wedge with a real buyer. Also: any **agent-orchestration product** that assumed sticky sessions now has an easier deployment story — revisit the roadmap.
- **Insight.** Watch what the **Server Cards + MCP Apps** primitives make discoverable — this is the piece of the spec most likely to create a marketplace dynamic (an "npm for MCP servers") over the next 6 months.

`#mcp #protocol #stateless #oauth #migration`

---

## 4. Google canceled AI Studio mobile app despite 800K+ preorders {#4-google-ai-studio-cancelled}

**What happened.** On or around **2026-07-31 / 2026-08-01**, Google canceled its planned **AI Studio mobile app** for iOS and Android — the standalone consumer front-end for Gemini-powered agent workflows — **despite drawing 800,000+ preorders** since I/O 2026.

Details are covered in [`01` §6](./01-big-lab-moves.md#6-google-gemini-robotics-2); the datum matters here because **it opens a specific product wedge**.

**Sources.**
- [AI News Today, August 2 — AI Weekly](https://aiweekly.co/ai-news-today) [aggregator]
- [AI News. August 1, 2026 — Crypto Integrated](https://www.cryptointegrat.com/p/ai-news-august-1-2026) [aggregator]

**Why it matters to you.**

- **Startup.** The **mobile-first agent front-end wedge is now open**. Google chose not to compete in a category with **800K demonstrated demand**. The winning product is **not** "another ChatGPT app" — it's a **model-agnostic agent shell** that picks the right underlying model per task, keeps context across models, and shows the user a clean receipts trail (which model, which tool, what it cost). The demand signal is verified; the incumbent is missing.
- **Job.** For a CS grad who has an iOS or Android side-project, **shipping a decent MCP-backed mobile agent this quarter** is a strictly stronger portfolio artifact than yet another web dashboard. It maps onto **Applied AI / consumer-agent** teams at Anthropic, OpenAI, xAI, and Perplexity.
- **Insight.** Enterprise > consumer is still the 2026 pattern for the big labs. The **third-party consumer-agent surface remains the underserved category**.

`#google #ai-studio #mobile #consumer-agents`

---

## 5. Emerging funding: Neko Health, Radical Numerics, Katalyze AI, AI-agent tier {#5-emerging-funding}

**What happened.** July 2026 funding notes worth carrying into August:

- **Neko Health — $700M Series C (Jul 10)** — preventive health, largest single round of the month.
- **Radical Numerics — $50M seed (Jul 10, Emergence Capital lead)** — the largest "seed" outside frontier-model labs this quarter; signals continued conviction that the *tooling around* frontier models is undercapitalized relative to the labs themselves.
- **Katalyze AI — $10.5M (Jul 15)** — AI-driven biomanufacturing; the vertical-AI-for-regulated-industries thesis that hardened over May continues.
- **~$37M across three AI-agent rounds (early July, Jul 1–6)** — the agent-startup tier is still funding steadily but at smaller round sizes; **the platform layer is where the winner-take-most bets are concentrating**.

Market-level: **AI startups took $242B in Q1 2026 (~80% of all global VC)**; AI captured **>70% of global Q2 funding**, up from <50% a year earlier.

**Sources.**
- [AI Agent Startup Funding Tracker: Q3 2026 (July Update) — Gravity Fast](https://gravity.fast/blog/ai-agent-funding-tracker-q3-2026/) [aggregator]
- [50 Top AI Funded Startups (July 2026) — AI Funding Tracker](https://aifundingtracker.com/top-50-ai-startups/) [aggregator]
- [Latest AI Startup Funding News and VC Investment Deals 2026 — Crescendo AI](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) [aggregator]
- [North American Startup Funding Shattered Records in First Half of 2026, Driven By AI — Crunchbase](https://news.crunchbase.com/venture/na-startup-funding-ma-shattered-records-ai-q2-2026/) [secondary]

**Why it matters to you.**

- **Startup.** **The signal in the noise: seed rounds outside the labs are getting larger, not smaller.** Radical Numerics at **$50M seed** is a data point that "tooling around frontier models" (evaluation, orchestration, RL infrastructure) is where non-lab money is flowing. If you're pre-forming a company, **position around a piece of that stack** rather than trying to compete with a lab.
- **Job.** **Two under-priced hiring lanes to look at:** (a) any Series-A that closed in **agent tooling / evaluation** in the last 60 days (they'll be the ones hiring #4–#10 engineers this week), and (b) **biomanufacturing / regulated-vertical AI** (Katalyze, Chapter Medicare, Marloo — quiet, well-funded, invisible to most CS-grad job searches).
- **Insight.** **Q2 >70% AI concentration of global VC is not sustainable** — expect a correction narrative to appear in H2 2026 (probably late-October, timed to earnings). Ride the current window; **don't build a startup that requires 2026-era funding-market conditions to survive.**

`#funding #agents #seed #biomanufacturing`

---

## Cross-cutting: what to watch this week

- **Compliance stack (EU + CA)** — first Commission information-request under the AI Act; first CA public-detector product from a 1M+ user provider; first C2PA-embedded output from a top-3 lab.
- **Cyber-agent responsibility narrative** — who quotes the Unit 42 finding in their next RFP response.
- **MCP marketplace signal** — who ships the first public Server Card / MCP Apps directory in the 07-28 spec.
- **Consumer-agent mobile wedge** — who ships a serious mobile agent shell against Google's canceled AI Studio.
- **OpenAI Astra follow-up** — do the "10 math results" survive independent verification within 2 weeks? That's the tell for whether the S-1 narrative sticks.
