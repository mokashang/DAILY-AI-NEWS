# New & Emerging — 2026-07-21

Two currents worth tracking today: **capital keeps concentrating in agentic verticals** (Harvey, Lovable, Glean, Emergent, Hebbia, Neko all closed in the last two weeks — enterprise-automation agents captured ~58% of July's AI dollars), and **the agent-infrastructure standard is quietly re-architecting itself** — the **MCP 2026-07-28 spec release candidate** dropped, taking the protocol **stateless** and adding **UI (MCP Apps)** and **long-running work (Tasks)**. If you're picking a wedge, both currents point the same way: **pick a vertical, then own the agent-plumbing under it.**

Tags: `#funding #agents #vertical #mcp #infra #verticalized-ai`

---

## 1. The July funding wave — enterprise-agent verticals dominate {#1-funding-wave}

> **Carry note:** the July funding table in this section was first assembled on [2026-07-20 §5](../2026-07-20/02-new-emerging.md#1-vertical-funding) — repeated here because the *aggregate posture* is what the specialty-lane pick in [`05` §2](./05-career-and-startup.md#2-specialty-moat) has to be responsive to *this week*. Read the table as a reference, not a headline.

**What happened:** July 2026 has been one of the largest AI-funding months of the year. **AI-agent startups alone raised ~$1.8B across 12+ deals**, average valuation up ~40% QoQ to ~$280M, with **Sequoia, Index, and Andreessen Horowitz** leading deal flow. Headliners:

| Company | Round | Amount | Valuation | Wedge |
|---|---|---|---|---|
| **Harvey** | Series C | $200M | $2.1B | Legal-vertical agents |
| **Lovable** | Series B | $200M | $2.8B | AI app-builder / vibe-coding platform |
| **Glean** | Series D | $180M | $2.7B | Enterprise search + agentic workflows |
| **Emergent** | Series C | $130M | $1.5B | AI coding for entrepreneurs / SMBs |
| **Hebbia** | Series B | $130M | $1.0B | Long-doc analysis for finance & law |
| **Neko Health** | Series C | $700M | — | AI-enabled preventive diagnostics |

**Sector concentration:** **Enterprise automation agents captured ~58% of July's total AI capital**; **developer tooling agents** raised $420M at an average Series-A valuation of $185M.

**Sources:**
- [AI Funding Tracker — Latest deals & rounds 2026](https://aifundingtracker.com/ai-startup-funding-news-today/) `[aggregator]`
- [AI Funding — AI Agent Startup Funding July 2026: Trends & Analysis](https://aifunding.me/insights/ai-agent-funding-july-2026) `[analysis]`
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: AI, Energy and Biotech](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-energy-biotech-joulent/) `[secondary]`
- [Blog.mean.ceo — AI Startup Funding News, July 2026](https://blog.mean.ceo/ai-startup-funding-news-july-2026/) `[analysis]`
- [Tech Startups — Venture Capital & Startup Funding Roundup, July 6, 2026](https://techstartups.com/2026/07/06/venture-capital-startup-funding-roundup-july-6-2026/) `[secondary]`
- [Crescendo AI — Latest AI Startup Funding News](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups) `[aggregator]`

### Why it matters to you

- **Job lens:** These rounds are **not "hire 500 engineers" rounds**; they're **"hire 30–80 very specific engineers"** rounds. Series-B/C at $1–3B valuations translates to a hiring shape where the *specialty* matters more than the *count*. Read each company's careers page against your ME.md focus (**AI Integration Engineer / FDE**): Harvey and Hebbia want AI engineers **who can speak the vertical** (contracts, regulatory filings, 10-Ks); Glean and Emergent want **agent-orchestration + eval** builders. **Warm intro > cold apply** at this stage — pick 2, follow the CTO/head-of-eng on X, and comment-with-substance for two weeks before you DM.
- **Startup lens:** The **"enterprise automation agents captured 58%"** stat is the sharpest signal in this list. If you're building, this tells you where the buyers actually are: **regulated workflows that produce a document a human currently reads** (contracts, disclosures, prior authorizations, underwriting memos, tax filings, clinical notes). Undernoticed corollary: the **AI-app-builder** category (Lovable, and the wave behind it) is *not* the same buyer as the enterprise wedge — it's **prosumer + long-tail SMB**. Pick your buyer before you pick your product.
- **Insight:** Cross the funding data with July's **model releases** (Fable 5, Sonnet 5, GPT-5.6, Gemini 3.5 Pro, Grok 4.5 beta, Kimi K3): the **model layer is commoditizing** exactly as **vertical-agent capital compounds**. That's not coincidence — it's the same market recognizing that **application-layer moats now come from workflow depth, tool integrations, and eval capital, not model quality per se.** Karpathy's move ([2026-05-22 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) is the *research* face of the same shift; this funding table is the *revenue* face.

→ Cross-link: [`05` §2 — how to translate this into a job-search shortlist](./05-career-and-startup.md#2-specialty-moat) · [2026-05-22 §2 — Exaforce SOC-agent parallel](../2026-05-22/02-new-emerging.md#2-exaforce).

---

## 2. MCP 2026-07-28 spec release candidate — stateless, MCP Apps, Tasks {#2-mcp-rc}

**What happened:** The **Model Context Protocol** — the de-facto agent-tool-integration standard — dropped its **2026-07-28 specification release candidate** with the biggest structural changes since MCP shipped. Beta SDKs for **Python, TypeScript, Go, and C#** are live now; the **final spec ships Jul 28** (one week from today).

The four big changes, and what each unlocks:

1. **Stateless core.** The **initialize handshake is gone** and there is **no protocol-level session**. Servers can now run behind a **plain round-robin load balancer**, route on the **`Mcp-Method` header**, and let clients **cache `tools/list` responses** for as long as the server's declared `ttlMs` allows. **Net effect:** MCP now scales like any other stateless HTTP service — no sticky sessions, no shared session store.
2. **MCP Apps.** Tools can return **interactive UI components** rendered directly in the conversation, in **sandboxed iframes**, communicating via **JSON-RPC over `postMessage`**. **Net effect:** the tool call is no longer just a text blob; it can *ship a widget* — a datepicker, a plot, a form, a preview — that the user interacts with inline.
3. **Tasks extension.** A standard shape for **long-running work** that outlives a single request. **Net effect:** you can finally model "kick off a build, notify me when done" or "run this eval overnight" inside MCP instead of hacking around it with polling.
4. **Auth aligned with OAuth / OIDC.** Cleaner integration with the standards enterprise IdPs already speak. **Net effect:** the "MCP is a security black box" objection from CISOs largely goes away.

Plus: a **formal deprecation policy** — the spec now has adults-in-the-room versioning.

**Sources:**
- [MCP Blog — The 2026-07-28 MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [MCP Blog — Beta SDKs for the 2026-07-28 MCP Spec Release Candidate Are Here](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/) `[primary]`
- [MCP Blog — The 2026 MCP Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) `[primary]`
- [The New Stack — MCP's biggest growing pains for production use will soon be solved](https://thenewstack.io/model-context-protocol-roadmap-2026/) `[analysis]`
- [TokenMix Blog — MCP Protocol Updates 2026: 9 Spec Changes, RC Migration Map](https://tokenmix.ai/blog/mcp-updates-changelog-every-protocol-change-2026) `[analysis]`

### Why it matters to you

- **Job lens:** The **stateless-HTTP** change is *the* interview-ready detail. It means the operational profile of MCP servers now matches what SRE/platform teams already know — the "we can't run this in prod" objection collapses. Anyone who can say in an interview *"I migrated my MCP server to the 2026-07-28 stateless core, published `ttlMs` on `tools/list`, and put it behind an ALB"* has a **90-second, technically-specific, current answer** to "what have you built recently?" — the single hardest thing to have at this moment.
- **Startup lens:** **MCP Apps is the biggest sneaky wedge here.** For the first time, the *tool provider* controls a piece of UI **inside the assistant surface** — that inverts the old assumption that assistants are "the app." Any vertical SaaS that ships a great MCP App experience gets **inline surface area** across every MCP-capable client (Claude Desktop, Cursor, Cline, Continue, ChatGPT if/when). Think: your CRM's opportunity-editor as an inline widget instead of a link. That's a moat that used to require a chrome extension or a native app; now it requires a good MCP App.
- **Insight:** The trajectory here mirrors what happened with HTTP + REST + OAuth in 2005–2012 — the *protocol* got serious, and the market for *integrations* exploded. MCP's stateless + auth + Tasks upgrade is the equivalent moment. **The next 12 months of agentic products will be defined by who ships good MCP Apps first**, not by who has the best model. Portfolio bet: **one MCP server + one MCP App + one Tasks-backed long-running action**, in a vertical you can talk about with authority. See [`03` §1](./03-practical-skills-and-tools.md#1-mcp-stateless) for the recipe.

→ Cross-link: [`03` §1 — the RC-upgrade recipe](./03-practical-skills-and-tools.md#1-mcp-stateless) · [`03` §2 — Claude Code subagent streaming, another MCP-adjacent lever](./03-practical-skills-and-tools.md#2-claude-code-subagents).
