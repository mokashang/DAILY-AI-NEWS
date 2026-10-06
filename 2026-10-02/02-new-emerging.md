# New & Emerging — 2026-10-02

MCP leaves Anthropic stewardship for a cross-lab foundation, long-horizon agent runtime becomes the funded startup wedge of Q4, and the week's three biggest rounds all land in one thesis: **"agents that keep running when the user stops looking."**

Tags: `#mcp #open-standards #agents #funding #vc #robotics #inference #startups`

---

## 1. MCP donated to the Agentic AI Foundation — Anthropic/Block/OpenAI co-founders, Google/MS/AWS/Cloudflare/Bloomberg backers {#1-mcp-foundation}

**What happened:** The **Model Context Protocol** — originally shipped by Anthropic in Nov 2024 and ratified as a de-facto industry standard across most of 2025–26 — has been **donated to the newly-formed Agentic AI Foundation**:

- **Co-founders:** Anthropic, Block, OpenAI.
- **Backers:** Google, Microsoft, AWS, Cloudflare, Bloomberg.
- **Scope:** MCP spec governance, implementation reference, security review, ecosystem coordination.

Separately, the ecosystem passed a funding milestone: **MCP-related security startups raised a combined $3.6B in 2026**, with **$40M specifically earmarked for MCP transport + auth hardening** (streamable HTTP + OAuth 2.1 with PKCE — see [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-mcp-mature)).

**Sources:**
- [SoftwareStrategiesBlog — $3.6B in funding + 10 Agentic AI security startups reshaping 2026](https://softwarestrategiesblog.com/2026/03/28/agentic-ai-security-startups-funding-mna-rsac-2026/) `[analysis]`
- [MCP Directory — Claude Code Best Practices 2026 (incl. MCP governance notes)](https://mcp.directory/blog/claude-code-best-practices) `[aggregator]`
- [Anthropic — Model Context Protocol docs](https://modelcontextprotocol.io/) `[primary]`

### Why it matters to you

- **Job lens:** MCP-at-foundation is a strong hiring signal for **"MCP server author"** as a specialist role. Three concrete roles to add to your apply-list this week: (1) **MCP infrastructure engineer** at any of the backing companies (Google, MS, AWS, Cloudflare, Bloomberg all run MCP servers behind their enterprise AI products); (2) **MCP security auditor** at the Foundation itself (small team, new org, hiring); (3) **MCP consulting / FDE lane** at the frontier labs — every enterprise rollout now goes through MCP, and the "write 5 custom servers in a week" skill is explicitly interview-asked.
- **Startup lens:** Three wedges got sharper. (a) **MCP server marketplaces** — directory, discoverability, versioning (the npm of MCP); (b) **MCP eval & observability** — once there are 10K servers in the wild, buyers need "which one is reliable + secure" data; (c) **vertical MCP server portfolios** — ship 20 Legal MCP servers, 20 Finance MCP servers, and the vertical becomes defensible by SKU count, not model quality. Pick a vertical you know (yours could be *CS student / academic* tools or *immigration + grad-student admin*) and ship 3 servers this weekend.
- **Insight:** Moving MCP out of Anthropic was **required for the Anthropic IPO** at $2T — the S-1 would otherwise have shown MCP as a strategic asset that invited every antitrust question. The move is dressed up as neutrality, but the timing (3–4 weeks before the IPO roadshow) is the giveaway. The upside: MCP governance now has a credible multi-vendor floor, which is good for everyone building on top.

---

## 2. Funding — long-horizon agent runtime is the Q4 2026 wedge {#2-funding}

**What happened:** This week's three biggest AI startup rounds all land in one thesis: **agents that keep running when the user stops looking.**

- **Rhoda AI — $450M Series A** (public launch): unveils **FutureVision**, a robotic-intelligence platform built on **video-predictive control**. Flagship bet: embodied agents that reason about physical action over multi-minute horizons.
- **8090 Solutions — $135M**, led by Salesforce 1. Enterprise-software platform with **coordinated multi-agent builders**. Co-founder/CEO: **Chamath Palihapitiya** (first operator-mode return since Social Capital). Founded 2024, so this is a very fast Series B equivalent at the enterprise agent layer.
- **Sail Research — $80M at $450M post**: inference infra specifically for **agents that run for hours or days**. The thesis: existing inference stacks (vLLM, SGLang, TGI) are optimized for interactive QPS and lose money on long-running workloads; Sail re-engineers for that.

Context (not new this week, but newly relevant with Rhoda's launch): **Mercor + CrewAI + Implement AI + Axelera AI** all raised in Q3 (per Wikipedia / Crunchbase tracker). Agentic infra remains the single biggest funded category of 2026.

**Sources:**
- [Crescendo — Latest AI Startup Funding News and VC Deals 2026](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) `[aggregator]`
- [aifunding.me — AI Agent Funding 2026](https://aifunding.me/ai-agent-funding) `[aggregator]`
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: AI, Energy And Biotech Lead The Way](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-energy-biotech-joulent/) `[secondary]`
- [Eqvista — AI Startup Fundraising Trends 2026 (Seed to Series B)](https://eqvista.com/ai-startup-fundraising-trends/) `[analysis]`

### Why it matters to you

- **Job lens:** All three companies will hire aggressively in Q4. The specific lanes:
  - **Rhoda AI** = **ML + robotics + video + generative world models** — if you have *any* robotics or vision background, DM their head of research now; a Series-A announcement always triggers 10-20 req posts in the first 2 weeks.
  - **8090 Solutions** = **enterprise FDE / Integration Engineer / Multi-Agent Orchestration** — exactly your target lane, Salesforce-anchored (which maps to the Salesforce / Sierra / Decagon branch in [ME.md](../ME.md#job-search-targeting-as-of-latest-edition)).
  - **Sail Research** = **inference infra + distributed systems + GPU scheduling** — if you've shipped anything with vLLM / SGLang, this is a direct pitch opportunity ("I'll re-benchmark your stack vs vLLM on 24-hour workloads").
- **Startup lens:** The pattern is clear and your own wedge thesis should be rechecked against it: **the three biggest Q4 agent rounds are all about "the agent runs long."** That maps to a startup opportunity that is **currently undercontested**: **long-horizon-agent observability** — logging, state inspection, replay, debugging for agents that run for hours. The incumbents (Datadog, Honeycomb, LangSmith, Arize) are all optimized for request-response. Build the "Playback for Dots/Managed Agents/Antigravity agents" product. 3-month version, free tier for solo devs, enterprise plan for teams.
- **Insight:** 8090's Salesforce-leadership (not just backing — *leading* the round) is the quiet signal: Salesforce has given up on building the agent-stack internally and is **outsourcing the IP capture** via lead investments. This is a repeatable pattern — expect Workday, ServiceNow, SAP, Adobe to each lead one agent-startup round in the next 90 days. Build with that in mind if your wedge is enterprise.

---

## 3. Secondary: Dots as a new "cloud-resident agent" primitive (crosscut) {#3-dots-primitive}

**What happened:** OpenAI's **Dots** (full detail in [`01` §3](./01-big-lab-moves.md#3-openai-devday)) is the first mainstream consumer-facing persistent agent. Three competing primitives now exist at the same altitude:

- **OpenAI Dots** — in ChatGPT, consumer-first, per-agent cloud computer.
- **Anthropic Managed Agents / "Dreaming"** — in the Agent SDK, developer-first.
- **Google Antigravity 2.0 Managed Agents** — in Vertex, enterprise-first.

Three different starting points, converging on the same primitive: **the agent is a long-lived entity with its own compute, memory, and identity.**

**Sources:**
- [Wikipedia — Google Antigravity](https://en.wikipedia.org/wiki/Google_Antigravity) `[secondary]`
- [OpenAI Developer Community — DevDay 2026](https://community.openai.com/t/devday-2026-announcements-and-developer-resources/1402006) `[primary]`

### Why it matters to you

- **Job lens:** "Persistent agent architect" is a brand-new job title with ~0 established candidates. Hire pool fills in Q4 2026 → Q1 2027. If you ship a demo on any of the three primitives this month and write a 500-word post comparing them, you are **top-50 globally** on this niche by December. That's a hiring edge worth 1–2 TC bands.
- **Startup lens:** The convergence means the **"neutral orchestration layer across Dots + Managed Agents + Antigravity agents"** is now a shippable wedge. A thin SDK that lets a product team spawn/retrieve/destroy any of the three primitives behind a common interface. Build it. (If you're wondering whether this is big enough to be a company — the answer is only if the three primitives *stay* roughly equivalent. If one dominates, the SDK becomes a wrapper of nothing.)
- **Insight:** Watch where **identity** gets owned. Dots has an identity per Dot (per-ChatGPT-user). Managed Agents has identity-per-SDK-key. Antigravity ties to Google Cloud IAM. **Whichever lab solves cross-platform agent identity first owns the next primitive layer.** Likely candidate: whoever ships "sign in to Service X as the agent you are, not the user who created you" — probably Anthropic or Cloudflare in Q1 2027.

→ Cross-link: [`01` §3 OpenAI DevDay — Dots](./01-big-lab-moves.md#3-openai-devday) · [`03` §1 Router v2](./03-practical-skills-and-tools.md#1-router-v2).
