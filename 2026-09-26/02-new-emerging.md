# New & Emerging — 2026-09-26

Post-Dreamforce, post-Meta-Connect, post-Copilot-refresh: the emerging layer of the week is **the price floor for voice** (Alibaba Qwen-Audio 3.1 cuts up to 95%) and **the emergence of "agent-native middleware"** — the SDKs and MCP servers being shipped this week to bridge legacy SaaS to frontier agents. Funding is quieter than last week; **infra + integration** wedges are where new company energy is landing.

Tags: `#alibaba #qwen #voice #pricing #mcp #agents #funding #open-source #startup`

---

## 1. Alibaba Qwen-Audio 3.1 — five-model voice stack, up to 95% API price cut {#1-qwen-audio}

**What happened (Sept 23–24):** Alibaba's Qwen team shipped **Qwen-Audio 3.1**, a five-model voice stack:

- ASR (upgraded)
- TTS (upgraded)
- Realtime (upgraded)
- **ASR-Next** — audio understanding with multi-speaker identification, timestamps, emotion detection, ambient-sound recognition
- **TTS-Next** — generates voice + effects + background audio in a single pass

Pricing cuts:
- **ASR: up to −95%**
- **TTS: ~−70%**
- **Realtime: ~−85%**

Positioning: **Qwen is now setting the floor on enterprise voice API pricing.** Any team locked into Deepgram, ElevenLabs, or OpenAI ASR contracts should re-run cost-per-hour math before the next renewal window.

**Sources:**
- [AI Weekly — Alibaba Ships Qwen-Audio 3.1 Stack, Cuts Voice APIs Up to 95%](https://aiweekly.co/alerts/alibaba-ships-qwen-audio-31-stack-cuts-voice-apis-up-to-95) `[aggregator]`
- [The Decoder — Alibaba launches Qwen Audio 3.1 with new models and slashes AI audio prices by up to 95%](https://the-decoder.com/alibaba-launches-qwen-audio-3-1-with-five-new-models-and-slashes-ai-audio-prices-by-up-to-95-percent/) `[secondary]`
- [Renascence — Qwen-Audio 3.1: Alibaba Cuts AI Voice Pricing by 95%](https://www.renascence.io/news/78111/qwen-audio-3-1-alibaba-cuts-ai-voice-pricing-by-95) `[secondary]`
- [Qwen on X — Meet Qwen-Audio-3.1](https://x.com/Alibaba_Qwen/status/2102687258990026993) `[primary]`

### Why it matters to you

- **Job lens:** The **voice-AI application layer got a −95% floor overnight**. Every voice-vertical startup you've been tracking (Wispr Flow, Retell, Vapi, Bland) is now competing against a price where the *model* is nearly free, and product differentiation shifts to **latency, orchestration, and integration**. If you interview at a voice-AI company this week, ask "how does the Qwen-Audio 3.1 pricing change your unit economics" — a good candidate has a specific answer; a bad one doesn't know. That question is your differentiator.
- **Startup lens:** A voice-vertical wedge that was "too expensive" two weeks ago may now clear. Concrete: **realtime transcription for medical consults + insurance-claim automation** was gated on ~$0.50/hour Deepgram pricing; if Qwen-ASR drops that to ~$0.03/hour, the vertical is suddenly buildable at seed-stage economics. Filter: does your wedge scale on *tokens of voice* rather than seat-count? If yes, the Sept 24 price cut just improved your CAC:LTV by 2–5×.
- **Insight:** Watch the **US → China voice API arbitrage** open. Any enterprise buyer whose procurement can accept an Alibaba API endpoint (data-residency + SOC 2 + regional deployment) will save 70–95% for the next 6 months. Enterprise procurement being what it is, that arbitrage will drive **Deepgram + ElevenLabs to cut US-side pricing 40–60% inside 90 days**. Model this into your unit economics now.

→ Cross-link: [`03` §3 the voice cost worksheet](./03-practical-skills-and-tools.md#3-voice-worksheet).

---

## 2. Eventtia + a cascade of MCP-server ships — the "add-MCP-to-legacy-SaaS" trend hardens {#2-mcp-cascade}

**What happened:** On **Sept 25**, **Eventtia** announced a native MCP server connecting its event-management platform to Claude, ChatGPT, Gemini, Copilot, and Cursor. It's a mid-cap SaaS announcement, but the *pattern* — a legacy SaaS shipping an MCP server as its Q4 flagship — is now happening across categories:

- **Salesforce Headless 360** — 60+ tools (per [`01` §1](./01-big-lab-moves.md#1-dreamforce-aiforce))
- **Amazon Seller Central Selling Partner plugin** (Sept 23, per [2026-09-25/01 §4](../2026-09-25/01-big-lab-moves.md#4-amazon-agents))
- **Eventtia MCP server** (Sept 25)
- **Microsoft Agent 365** as an MCP-consumer host (Sept 25, per [`01` §2](./01-big-lab-moves.md#2-microsoft-copilot))

**Sources:**
- [The Agile Brand Guide — Yesterday's MarTech, AI & CX News — September 26, 2026](https://agilebrandguide.com/yesterdays-martech-ai-cx-news-september-26-2026/) `[aggregator]`
- [AI Weekly — Daily Edition Sept 25](https://aiweekly.co/ai-news-today/edition/2026-09-25) `[aggregator]`

### Why it matters to you

- **Job lens:** Every mid-cap SaaS that ships an MCP server in Q4 will need **1–3 MCP-integration engineers** (server author, customer-support engineer, docs/DevRel). This is a **hidden hiring surge** happening below the news line — 500+ mid-cap SaaS companies at ~2 openings each = ~1,000 unadvertised roles in Oct-Nov. Practical: search LinkedIn + `who's hiring` on HN with query `"MCP" OR "Model Context Protocol"` and cold-outreach the head of engineering; don't wait for the JD to post.
- **Startup lens:** The **MCP-as-a-service wedge is now real, not hypothetical**. Two shapes: (a) **"MCP-server-in-a-box"** — a low-code builder for legacy SaaS to ship an MCP server in 2 weeks instead of 2 quarters (Retool + Zapier + Cloudflare shape); (b) **MCP-server-catalog** — the "npm for MCP tools" (curated, versioned, revenue-share with tool authors). Not clear yet whether Anthropic itself takes (b); if not, a startup can plausibly build it. The precedent to study is `smithery.ai` and the community MCP registries — none are enterprise-ready as of this week.
- **Insight:** **MCP is now the dominant standard for agent-to-tool interoperability.** Every major surface — Anthropic, OpenAI (via ChatGPT connectors), Google (Gemini Enterprise), Microsoft (Copilot), Amazon (Bedrock + Seller Central), Salesforce (Headless 360) — either speaks MCP natively or has committed to a bridge. Being "MCP-fluent" is now a 2027 baseline skill, not a 2026 differentiator; **the differentiating skill is MCP-*server design* — schema choices, tool granularity, error semantics, cost-aware tool exposure**. That's the interview-differentiator layer for the next 6 months.

→ Cross-link: [`03` §2 MCP-server-design checklist](./03-practical-skills-and-tools.md#2-agent-governance) · [`05` §2 the MCP integration lane](./05-career-and-startup.md#2-integration-lane).

---

## 3. Funding — quieter week, but agentic-AI still dominant {#3-funding}

**What happened:** No mega-round crossed the wire this week to rival Instinct ($250M Series B, [2026-09-10/02 §1](../2026-09-10/02-new-emerging.md#1-funding-barbell)) or Cognition ($2B Series E, per Crunchbase). Two structural facts to note:

- **H1 2026 total: $510B raised across startups**, more than *all of 2025*. OpenAI + Anthropic captured **$217B** of that half — ~43%.
- **Cognition (Devin) now at ~$3.9B raised total**, latest Series E ~$2B at $48B valuation (a16z + Accel lead).

**Sources:**
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: AI, Energy And Biotech Lead The Way](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-energy-biotech-joulent/) `[secondary]`
- [Second Talent — AI Startup Funding and Investment Statistics (Sep 2026)](https://www.secondtalent.com/resources/ai-startup-funding-investment/) `[analysis]`
- [New Market Pitch — Top Agentic AI Startups by Fundraising (2026)](https://newmarketpitch.com/blogs/news/agentic-ai-top-startups-fundraising) `[aggregator]`

### Why it matters to you

- **Job lens:** The **funding barbell is confirmed**: two frontier labs eating half the capital + everyone else fighting for the other half. If you want frontier-scale comp, apply to Anthropic / OpenAI / DeepMind / xAI / Meta AI (the "big-5" of frontier labs). If you want early-employee equity leverage, apply to funded startups **whose product wraps an agent primitive newly re-priced this week** — voice (post-Qwen), CRM-agent (post-Claudeforce), marketplace-agent (post-Amazon), consumer-device (post-Muse Charm). Concrete filter: has the startup shipped an MCP-native surface in the last 30 days? If yes, they are hiring integration engineers now.
- **Startup lens:** Founders should read the funding data as **"be #1 in a category, or don't raise"**. The barbell means the middle is dead — a "35th-best voice-AI startup" won't clear a $10M Series A in Q4 2026. Wedge honesty test: could you get to $1M ARR in 12 months if venture money paused? If no, the wedge is not fundable in this environment. Apply your STARTUPS.md re-rank tonight.
- **Insight:** OpenAI + Anthropic capturing ~43% of half-year AI capital = **the *distribution* of the second half of 2026 will be even more concentrated once the two IPOs close**. Public-market money will flood in *after* the S-1s land, not before. Private-market Series A/B founders should not expect a valuation rebound until Q1 2027 at the earliest.

→ Cross-link: [`05` §2 integration lane vs frontier-lab lane](./05-career-and-startup.md#2-integration-lane).

---

## 4. Open source — Nemotron + Koa, and the return of the vertical open model {#4-open-source}

**What happened:** Salesforce's Dreamforce announcement of **Koa** — a CRM-specific reasoning model built with NVIDIA on the **Nemotron** family — is notable for what it isn't: not a frontier general model, not a fine-tune of Claude or GPT-6. It's an **open-weight vertical model**, purpose-built for a domain (CRM).

The pattern to watch:
- **NVIDIA Nemotron 3 Nano Omni** (open-source, 30B-A3B hybrid Mamba-Transformer, [2026-05-11](../2026-05-11/00-tldr.md))
- **DeepSeek V4** (MIT license, runs on Huawei Ascend, [2026-05-08](../2026-05-08/00-tldr.md))
- **Koa** (Sept 2026, CRM-vertical, built on Nemotron)

Vertical open-weight models fine-tuned to enterprise domains are the **third layer of the frontier stack** after (i) general frontier models and (ii) proprietary vertical adapters.

**Sources:**
- [Salesforce Ben — Dreamforce '26 recap](https://www.salesforceben.com/salesforce-launches-aiforce-at-dreamforce-26-ai-replaces-the-ui/) `[secondary]`
- [Moor Insights — Dreamforce 2026](https://moorinsightsstrategy.com/field-notes/at-dreamforce-2026-salesforce-goes-all-in-on-agentic-ai/) `[analysis]`

### Why it matters to you

- **Job lens:** **Vertical open-model fine-tuning + eval** is an under-hired lane. Enterprise verticals (CRM, healthcare, legal, finance) will each want one Koa-analog in the next 12 months. That's a pattern that hires **ML engineers who can (a) fine-tune on Nemotron or a similar open base, (b) build a domain-specific eval suite, (c) integrate with an MCP-native agent surface**. Direct target companies: **Databricks, Snowflake, Cohere, Together AI, Fireworks, Baseten, Modal, PwC/Deloitte** vertical practices.
- **Startup lens:** The vertical-open-model wedge is real for **any regulated vertical where a proprietary frontier model can't be self-hosted for compliance reasons** (healthcare / defense / legal / EU-only data-residency). A startup can plausibly build "the Koa for [vertical]" as a $5–15M ARR business — smaller than a frontier lab, but a real defensible practice with 5–20 employees.
- **Insight:** The **"vertical open model + MCP-native agent" combo** is the emerging Q4 2026 enterprise reference architecture. Study Koa's release notes when they land; that's your template for founder pitches and for FDE case studies over the next quarter.

→ Cross-link: [`01` §1 Claudeforce + Koa in the same platform](./01-big-lab-moves.md#1-dreamforce-aiforce) · [`04` §3 vertical-eval methodology](./04-research-progress.md#3-vertical-eval).
