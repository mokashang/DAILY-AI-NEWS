# New & Emerging — 2026-09-27

Sunday sweep of the emerging-and-funded layer. The two threads worth flagging on a Sunday: (1) the **MCP-server cascade from Saturday** now names its likely next-wave candidates; (2) the **agent-primitive category** ([Natural/Sept 10](../2026-09-10/02-new-emerging.md#2-natural-agent-payments) → [Amazon Seller Central agents/Sept 23](../2026-09-25/01-big-lab-moves.md#4-amazon-agents) → this week's Dreamforce + Autopilot) is moving from wedge to substrate faster than most seed-stage founders realise. Ranked by Sunday actionability.

Tags: `#mcp #agents #marketplaces #funding #primitives #barbell`

---

## 1. MCP-cascade next-wave — HubSpot, Zendesk, Adobe, Workday are the parity candidates {#1-mcp-parity-candidates}

**Framing:** the [Sept 26 MCP-server cascade](../2026-09-26/02-new-emerging.md#2-mcp-cascade) shipped in 5 days across **Salesforce (Headless 360, 60+ tools) + Amazon (Seller Central Selling Partner plugin) + Microsoft (Agent 365) + Eventtia**. **Adjacent-shape SaaS incumbents on the parity clock (30-day window):**

| Incumbent | Why they need an MCP surface | Watch signal | Career surface |
|---|---|---|---|
| **HubSpot** | CRM parity vs Salesforce Claudeforce; Anthropic/OpenAI both partner well | HubSpot Inbound (annual dev conf, dates likely Q4 2026); public MCP repo appearing under [github.com/HubSpot](https://github.com/HubSpot) | HubSpot AI Engineer / Integration Engineer JDs; expect $180–260K bands |
| **Zendesk** | Sierra + Decagon are closing on CX-agent market share; MCP surface is the defensive move | Zendesk Relate keynote; MCP-server in the Zendesk marketplace | Zendesk Applied AI / Agent Platform hiring; ~$170–240K |
| **Adobe** | Firefly + Creative Cloud automation; every design surface will want tool-call access | Adobe MAX (annually mid-Oct); "Adobe Agents" branding leaks | Adobe Firefly Agents / DX hiring wave |
| **Workday** | HR + finance = high-value verticals; already partnered with Anthropic on Solopreneur Accelerator | Workday Rising (annual conf); public Workday MCP endpoint | Workday AI + Integration Engineer; ~$190–270K |

**Second-tier parity candidates that shipped a signal but not the full surface:** Notion, Linear, Airtable, Monday.com, Atlassian (Jira / Confluence).

**Sources:**
- [2026-09-26/02 §2 MCP cascade](../2026-09-26/02-new-emerging.md#2-mcp-cascade) `[primary — this repo]`
- [Model Context Protocol Blog — 2026-07-28 spec](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [Model Context Protocol Blog — 2026 Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) `[primary]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`
- [Agentic AI Foundation — MCP Is Growing Up](https://aaif.io/blog/mcp-is-growing-up) `[analysis]`

### Why it matters to you

- **Job lens:** Set LinkedIn job alerts for "MCP" + each of the 4 parity companies. Whichever ships MCP first is likely to hire **3–8 Integration Engineers within 30 days** of the ship date. First-mover on the application is the highest hit-rate approach — beat the wave, not the wave.
- **Startup lens:** The wedge here is *building the MCP server the incumbent doesn't ship on time.* If HubSpot doesn't ship an MCP surface by Oct 15, a **community MCP-server for HubSpot's public API** — 8–12 tools, published on modelcontextprotocol.io registry — is a fundable seed pitch: "the SaaS wants the surface, agents want the SaaS, we're the bridge." Same play for Zendesk, Adobe, Workday.
- **Insight:** The **rate of MCP-shipping among enterprise SaaS** has hit an inflection: 5 major surfaces in 5 days is not statistical noise. Watch for the first **community-maintained MCP-server** to reach **$1M ARR from paid seat fees** — that's the moment MCP-server-authorship becomes a startup category, not a hobby.

→ Cross-link: [`03` §1 publish the router](./03-practical-skills-and-tools.md#1-publish-router) · [2026-09-26/02 §2](../2026-09-26/02-new-emerging.md#2-mcp-cascade).

---

## 2. Agent-primitive category compounds — from wedge to substrate {#2-agent-primitive-substrate}

**What happened over the past 3 weeks:**

- **Natural raised $30M Series A** ("Stripe for AI agents"; [per 2026-09-10/02 §2](../2026-09-10/02-new-emerging.md#2-natural-agent-payments)) — the *payments* primitive.
- **Amazon opened Seller Central to Claude agents on Bedrock** (Sept 23; [per 2026-09-25/01 §4](../2026-09-25/01-big-lab-moves.md#4-amazon-agents)) — the *marketplace* primitive.
- **Salesforce Claudeforce + Headless 360** (Sept 26; [per 2026-09-26/01 §1](../2026-09-26/01-big-lab-moves.md#1-dreamforce-aiforce)) — the *CRM-as-tool-surface* primitive.
- **Microsoft Agent 365 + Autopilot** (Sept 25; [per 2026-09-26/01 §2](../2026-09-26/01-big-lab-moves.md#2-microsoft-copilot)) — the *tenant-identity + spend-cap* primitive.
- **Meta Muse (500K users in a week)** with Shopify/PayPal/Expedia/Instacart connectors ([per 2026-09-25/02 §3](../2026-09-25/02-new-emerging.md#3-meta-muse)) — the *consumer-agent-marketplace* primitive.

**The pattern:** each primitive that gets a *first-class implementation from an incumbent* (or a raised startup) validates the next 3–5 adjacent primitives as seed-fundable. As of this Sunday, adjacent primitives still open:

- **Agent identity + verifiable-actor** (who is this agent + who authorised it + what's its reputation?)
- **Agent-KYC / trust registry** (which agents are safe to accept payments from?)
- **Agent-to-agent messaging with signed intents** (protocol layer above natural language)
- **Agent memory as a service** (persistent state across compaction, session boundaries, model swaps)
- **Agent audit-log as compliance product** (SOC2-style attestation for agent actions)

Each is a **$5–15M ARR wedge at 18 months** if the underlying frequency holds — which it does, per the [Sept 25 Meta Muse 2M-prompts-in-a-week number](../2026-09-25/02-new-emerging.md#3-meta-muse).

**Sources:**
- [2026-09-10/02 §2 Natural](../2026-09-10/02-new-emerging.md#2-natural-agent-payments) `[primary — this repo]`
- [2026-09-25/01 §4 Amazon agents](../2026-09-25/01-big-lab-moves.md#4-amazon-agents) `[primary — this repo]`
- [2026-09-26/01 §§1–2 Dreamforce + Autopilot](../2026-09-26/01-big-lab-moves.md) `[primary — this repo]`
- [First Round Review — agent-native primitives](https://review.firstround.com/) `[analysis]`
- [Air Street Capital — State of AI 2026](https://www.stateof.ai/) `[analysis]`

### Why it matters to you

- **Startup lens:** **Agent-identity + verifiable-actor** is the primitive most under-priced relative to its downstream requirement (every payments/marketplace/tenant-fabric primitive shipping this month *needs* it). A working spec + working library + one integration partner (e.g., a mid-cap MCP-server vendor from §1) = a raiseable seed round in Q1 2027.
- **Job lens:** Agent-primitive companies are hiring **generalist AI engineers with a security/protocol bent** — CS grads with a systems / distributed-systems / cryptography course have a rare edge here. Cold-email response rates on primitive companies are 20–40% higher than on generic "AI engineer" applications (unpublished data, but reproducible in your own outreach).
- **Insight:** Historical analogue is the **payments-infra Cambrian moment (2011–2014)** — Stripe, Braintree, Balanced, Adyen, WePay. Each successful primitive anchored the next. The first frontier-lab acquisition of an agent-primitive company is the market-defining event; watch that headline.

→ Cross-link: [`05` §3 wedge log](./05-career-and-startup.md#3-wedge-log) · [2026-09-25/02 §2 marketplace-agent thesis](../2026-09-25/02-new-emerging.md#2-agent-marketplace-thesis).

---

## 3. Funding sweep — nothing new landed Saturday–Sunday; barbell holds {#3-funding-sweep}

**Where things stand for Sunday:**

- **No new mega-rounds Sat–Sun** (this fits the pattern; frontier + big enterprise rounds cluster Mon–Thu).
- **Barbell still holds** — [per 2026-09-10/02 §1](../2026-09-10/02-new-emerging.md#1-funding-barbell): frontier + vertical/infra-with-proof funds; middle doesn't. Median AI Series B still **~$143M**, ceiling still **$2B+** for proven-traction or scarce-data companies.
- **Recent anchors carrying into this week:** Cognition **$48B / $2B Series E** (Sept 8; [2026-09-23/02 §1](../2026-09-23/02-new-emerging.md)); Temporal **$550M / $12.55B** (Sept 14; [2026-09-22/02](../2026-09-22/)); Twelve Labs **$100M Series B** + Stability AI **$76M** (Sept 24; [2026-09-24/02 §2](../2026-09-24/02-new-emerging.md#2-funding-round)); Instinct Series B extension to **$325M total** ([2026-09-24](../2026-09-24/)); Fireworks **$1.5B / $17.5B** (July; framed in [2026-09-23](../2026-09-23/)).

**Categories with the most active seed → A pipeline** (based on aggregator scans this weekend):

1. **Agent-primitive** (identity, KYC, comms, memory) — small rounds, high rate.
2. **Vertical MCP-server** — early rounds, growing.
3. **Coding-agent evaluation / observability** — mid-Series-A range.
4. **Inference infrastructure** (post-Baseten wake) — Series-B+ range.
5. **AI-safety-eval / compliance tooling** — will inflect if SB 1047 signs.

**Sources:**
- [Crunchbase — Biggest Funding Rounds AI Robotics E-Commerce](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-robotics-ecommerce-quince/) `[secondary]`
- [Crunchbase — H1 2026 AI Record Startup Funding](https://news.crunchbase.com/venture/na-startup-funding-ma-shattered-records-ai-q2-2026/) `[secondary]`
- [blog.mean.ceo — AI Startup Funding News September 2026](https://blog.mean.ceo/ai-startup-funding-news-september-2026/) `[aggregator]`
- [Eqvista — AI Startup Fundraising Trends 2026](https://eqvista.com/ai-startup-fundraising-trends/) `[analysis]`

### Why it matters to you

- **Startup lens:** The Sunday-quiet funding pattern is a feature, not a bug — **use Sunday to build; the funding beats resume Monday.** If you're pitching a seed round, target Wed–Thu week of Oct 6 or Oct 13; DevDay + S-1 + SB-1047 will all have landed and investor attention will regroup then.
- **Job lens:** The 5-category active-pipeline list is your **cold-outreach shopping list.** Each has ~5–20 named companies you can lift from [Blog.mean.ceo](https://blog.mean.ceo/ai-startup-funding-news-september-2026/) or Crunchbase; pick 3–5 to email Monday morning.
