# Practical Skills & Tools — 2026-09-26

**Saturday = weekend-project day.** If yesterday's TL;DR nudged you to refresh the router with Opus 5.5 + Sol/Luna + Batch, today's job is one level up: **wire the router to consume an MCP server so your agent can *invoke* a tool, not just pick a model**. Every artifact in this file is Saturday-shippable in 2–6 hours. All price numbers are current as of Sept 26 close.

Tags: `#claude-code #mcp #agents #routing #cost #tools #weekend-project`

---

## 1. The router-to-MCP shim: how to turn Friday's model-router into Saturday's agent-runtime {#1-router-shim}

**What & why:** Your router chooses a model per task. That's necessary but not sufficient — every enterprise-agent job in Q4 2026 asks for a *tool-calling* agent, not just a router. The upgrade is small (~60 LOC on top of the router from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)): expose your router as an MCP client, mount one MCP server (start with `filesystem` or a hosted one), route by (task-type, tool-need), log per-tool cost + latency.

**Ship checklist (~3 hours):**

1. **Pick a base MCP server** you don't have to build:
   - `filesystem` (official reference)
   - `github` (official reference) — great for a portfolio demo
   - `postgres` (official) — great for interview demos of "agent hits real DB"
   - `slack` or `notion` — great for consumer-flavor demos
2. **Add MCP-client wiring** to the router. Anthropic Agent SDK ≥ Sept 2026 has native MCP-client support. Cursor / Claude Code / OpenClaw all consume the same protocol.
3. **Extend the router's decision matrix** — add a `tool_need` axis: none / read-only / write. Route write-tools through the more capable model (Opus 5.5 or GPT-6 Sol); route read-only through Luna or Gemini 3.8 Flash.
4. **Cost dashboard**: log `(model, tool_calls, tokens_in, tokens_out, latency_ms, tool_cost, model_cost)` per request. A 20-line SQLite table + one Grafana / DuckDB / Metabase view is enough for the portfolio.
5. **Publish** to GitHub with MIT license + a README that includes: architecture diagram, price/quality frontier plot, per-tool-call cost table, screenshot of the dashboard.

**5-case eval to include (per [2026-09-24/03 §3](../2026-09-24/03-practical-skills-and-tools.md#3-router-extension)):**

| # | Task type | Right model | Right tool | Notes |
|---|---|---|---|---|
| 1 | Extraction (structured) | Luna | none | pure LLM, cheapest tier |
| 2 | Coding assist (small edit) | Sol / Gemini 3.8 Flash | filesystem MCP | write-file test |
| 3 | Long-context Q&A over docs | Opus 5.5 | filesystem MCP (read) | tests cache-read pricing |
| 4 | Multi-hop agentic tool use | Opus 5.5 | github MCP | tests SWE-bench-shape task |
| 5 | Bulk labeling | Luna (batch) | none | tests OpenRouter Batch API |

**Sources:**
- [Anthropic Agent SDK docs](https://docs.claude.com/en/api/agent-sdk/overview) `[primary]`
- [Model Context Protocol — official servers](https://github.com/modelcontextprotocol/servers) `[primary]`
- [OpenRouter Batch API pricing](https://openrouter.ai/openai/gpt-6-luna) `[primary]`
- [Claude Opus 5.5 API pricing](https://www.aipricing.guru/news/claude-opus-5-5-api-pricing-september-2026/) `[secondary]`
- [alexop.dev — Claude Code Explained (2026): MCP, Skills, Subagents, Hooks & Plugins](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`

### Why it matters to you

- **Job lens:** Every Q4-2026 FDE / Applied AI / AI Integration Engineer JD asks for **"builds agents that call real tools with real cost accounting."** This artifact answers that in one repo. Concrete: ship by Saturday 8 PM PT, post to LinkedIn Sunday with the price/quality plot, ping 3 recruiters Monday.
- **Startup lens:** The same repo is the **investor-facing artifact** for a "cost-aware agent orchestrator" thesis. Every Series-A pitch will show a similar plot — being able to speak to yours from personal experience *without* being the founder is a hiring differentiator at any early-stage AI startup.
- **Insight:** The router-to-MCP shim is a small piece of code, but it **maps one-to-one to the market's shape this week**: model-tier price cuts (Opus 5.5 / Sol / Luna / Qwen) × MCP-standard tool interop (Salesforce Headless 360 / Amazon Selling Partner / Microsoft Agent 365). Your repo is a *live-model* of the entire Q4 2026 architecture in <300 LOC. That's more useful than any single benchmark.

---

## 2. Agent governance — the new eval axis every senior interview will hit {#2-agent-governance}

**What & why:** Microsoft Agent 365 (Sept 25, [`01` §2](./01-big-lab-moves.md#2-microsoft-copilot)) crystallizes what was already implicit: **agents in production need identity, monitoring, security policy, and spend control**. The interview question this quarter is not "have you built an agent" but **"have you built a *governed* agent"**. Six things every senior-level agent build should now do:

1. **Per-agent identity** — Auth0 / Okta / Azure AD tenant identity, not a shared API key.
2. **Per-tool allowlist + denylist** — enforced at the router, not the agent (rules > prompts).
3. **Per-request cost cap** — router aborts if projected cost exceeds threshold; log the abort event.
4. **Immutable audit trail** — append-only log of `(agent_id, tool_call, request, response, cost)`. SQLite + WAL is enough at portfolio scale.
5. **Rate limiting + burst limiting** — per identity, per tool, per hour.
6. **Human-in-the-loop escalation** — auto-escalate any tool call with `write` scope AND cost > $threshold to a Slack/PagerDuty approver.

**Weekend polish (2 hours):** add these six primitives to your router-to-MCP shim from §1. Even a *toy* implementation makes the repo interview-ready for regulated-industry FDE roles (Legal / Finance / Life Sciences / Healthcare).

**Sources:**
- [Futurum — Microsoft Copilot Becomes an Agentic Work Platform (Agent 365 detail)](https://futurumgroup.com/insights/microsoft-copilot-becomes-an-agentic-work-platform/) `[analysis]`
- [Anthropic Agent SDK — Hooks](https://docs.claude.com/en/api/agent-sdk/hooks) `[primary]`
- [Firecrawl — 14 Best Claude Code Skills for Developers in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) `[analysis]`

### Why it matters to you

- **Job lens:** For **Anthropic Applied AI, OpenAI FDE, Sierra Customer Eng, Cognigy, Decagon, PwC/Deloitte AI Practice**, "governance-aware agent" is the discriminator between L4 / L5 offers. Concrete: name-check Agent 365, MCP-server-tool-scoping, per-tool allowlist, and "audit trail as evidence of SOC 2 Type II readiness" in a technical screen and you jump a level.
- **Startup lens:** "Agent governance" is the wedge for **any founder who has been in F500 IT or GRC for >2 years**. The market's ready — Salesforce, Microsoft, Amazon all shipped the same shape this week and none of them have a dedicated governance product. Named wedges: agent-firewall, agent-DLP, agent-audit-log-as-a-service. Design partner ask: 3 F500 CIOs willing to pilot in Q1 2027.
- **Insight:** The **enforcement primitive matters more than the reasoning primitive** in Q4 2026 enterprise deploys. A model that's 5% smarter but 100% ungoverned loses every RFP to a model that's 5% dumber but SOC 2 / HIPAA / FedRAMP compliant. Skill-priority order for this quarter: (i) identity/audit, (ii) MCP-server design, (iii) eval-authoring, (iv) model routing, (v) reasoning-quality tuning. Reversed from what interview prep looked like 6 months ago.

---

## 3. Voice cost worksheet — Qwen-Audio 3.1 vs Deepgram/OpenAI/ElevenLabs {#3-voice-worksheet}

**What & why:** Qwen-Audio 3.1's up-to-95% cut means every voice-vertical unit-economic model in your STARTUPS.md needs a re-run tonight. Direct comparison (all $/hour of audio, approximate; sources cited):

| Provider | ASR $/hr | TTS $/hr | Realtime $/hr | Notes |
|---|---|---|---|---|
| **Qwen-Audio 3.1** (Sept 24) | **~$0.03** | ~$0.30 | ~$0.60 | 95%/70%/85% cut. Alibaba Cloud endpoint |
| **OpenAI Whisper API** | ~$0.36 | — | — | list pricing, no batch |
| **Deepgram Nova 3** | ~$0.43 | — | — | list; enterprise discounts apply |
| **ElevenLabs Turbo v3** | — | ~$1.50–$3.00 | — | depends on character count; consumer-grade quality |
| **OpenAI Realtime API** | — | — | ~$2.40 in / $12 out per hour | GPT-6 tier; premium |

**Worksheet template (60 min):** for one voice-vertical wedge you're evaluating, populate:

1. **CAC** (marketing + sales cost to sign 1 customer)
2. **ARPU** ($/customer/month)
3. **Voice-token consumption per customer per month** (hours of audio × 3600 sec)
4. **Voice cost per customer per month** (current provider) vs (Qwen-Audio 3.1 provider)
5. **Payback period** (CAC ÷ (ARPU − voice cost − hosting)) — with each provider
6. **Sensitivity**: at what customer scale does self-hosting break even on Qwen-Audio open weights?

**Sources:**
- [The Decoder — Alibaba launches Qwen Audio 3.1 with new models and slashes AI audio prices by up to 95%](https://the-decoder.com/alibaba-launches-qwen-audio-3-1-with-five-new-models-and-slashes-ai-audio-prices-by-up-to-95-percent/) `[secondary]`
- [Deepgram pricing](https://deepgram.com/pricing) `[primary]`
- [OpenAI API pricing](https://openai.com/api/pricing/) `[primary]`
- [ElevenLabs pricing](https://elevenlabs.io/pricing) `[primary]`

### Why it matters to you

- **Job lens:** A completed worksheet is a **30-min interview conversation** for any voice-AI-adjacent role (Wispr Flow, Retell, Vapi, Bland, Sierra Voice, Decagon Voice, ElevenLabs itself). "I re-ran our unit economics after the Qwen-Audio 3.1 cut" is *the* opening line this week.
- **Startup lens:** If the payback period changed by more than 3× under the new pricing, your voice-vertical wedge just moved from "not fundable" to "seed-shape." Filter your STARTUPS.md accordingly. If it didn't change, the wedge is not voice-cost-sensitive and you should ignore Qwen — focus on your actual moat.
- **Insight:** **China-provider price arbitrage is a valid Q4 2026 strategy for pre-seed / seed startups** because compliance overhead is low at that stage. It becomes a liability at Series A when enterprise procurement asks about data residency. Design accordingly: build to *provider-abstract* voice interfaces from day one so you can swap Qwen → Deepgram at the moment your first regulated enterprise customer signs.

---

## 4. Weekend playbook — Sept 26 (Sat) → Sept 27 (Sun) {#4-weekend}

**Saturday (4–6 hours):**
1. **09:00–13:00** — ship the router-to-MCP shim from §1. Repo public, MIT, README with plot.
2. **13:00–14:00** — voice-cost worksheet from §3 for your one active STARTUPS.md wedge.
3. **14:00–17:00** — add the 6 agent-governance primitives from §2 to the shim.
4. **20:00** — post to LinkedIn (screenshot + price/quality plot + one-line "why this matters").

**Sunday (2–3 hours):**
1. **09:00–10:30** — read one paper: **DolphinBench: Mapping the Pareto Frontier of Agent Memory** (per [`04` §1](./04-research-progress.md#1-dolphinbench)). Write a 500-word summary. Post to your personal blog / Substack / GitHub as `NOTES-dolphinbench.md`.
2. **10:30–12:00** — update **APPLICATIONS.md** (target 5 net-new applications submitted this week: 3× Anthropic + 2× funded startup). Update **STARTUPS.md** with the Qwen-Audio 3.1 re-priced wedges. Update **ACTIONS.md** with next-week's tasks.
3. **12:00–13:00** — draft 3 cold DMs (to Meta Muse Applied AI, one Salesforce Claudeforce SME, one Microsoft Copilot Autopilot PM) — send Monday 8 AM PT.

**Total: ~7–9 hours over the weekend = one shipped artifact + one paper summary + 5 applications + 3 cold DMs. That's the full quarterly cadence per [ME.md](../ME.md).**

**Sources:**
- [scriptbyai — Claude Code Resource List 2026](https://www.scriptbyai.com/claude-code-resource-list/) `[analysis]`
- [alexop.dev — Claude Code Full-Stack Explained](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [Totalum — Claude Agent SDK in 2026: Plans, Credits, Shipping](https://www.totalum.app/blog/claude-agent-sdk-totalum-2026) `[analysis]`

### Why it matters to you

- **Job lens:** By Sunday night, you have (i) one shipped MCP-native agent repo, (ii) one paper summary, (iii) 5 apps out, (iv) 3 cold DMs scheduled. That's a **week's worth of hiring-signal in a single weekend** during the highest-velocity hiring window of Q4.
- **Startup lens:** The Sunday DolphinBench summary is *the* founder-conversation opener for anyone raising in "agent memory" — a category that got a benchmark this week. Being 48 hours ahead of the trend on this specific paper is worth 3 investor intros.
- **Insight:** The best jobs and best startups in Q4 2026 will go to people who **turned this week's news into next week's artifacts**, not people who read this week's news and stored it in their heads. Cadence > intensity. The weekend project shipped is worth 10× the weekend project planned.

→ Cross-link: [`00-tldr.md` one-thing-to-do](./00-tldr.md#one-thing-to-do) · [ACTIONS.md](../ACTIONS.md) · [STARTUPS.md](../STARTUPS.md) · [APPLICATIONS.md](../APPLICATIONS.md).
