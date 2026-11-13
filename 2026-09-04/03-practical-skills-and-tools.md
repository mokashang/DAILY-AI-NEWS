# Practical Skills & Tools — 2026-09-04

Four concrete moves you can ship this weekend without waiting for the market to stabilize. Prioritized by cost-per-hour of effort × visibility of the artifact.

Tags: `#tools #caching #routing #reliability #mcp #artifacts #anthropic #openai`

---

## 1. Fable 5.1 cache-read rewrite — the cheapest optimization on your Claude workflows this week {#1-fable-caching}

**The move:** rewrite one of your MCP-server or agent prompts to move as much text as possible **behind a stable cache boundary**, then benchmark cost-per-call before/after.

**Why now:** Anthropic dropped **cache read pricing from $1.00 → $0.25 per MTok on Fable 5.1** (see [`01` §2](./01-big-lab-moves.md#2-fable-51)) — a **75% reduction**. Cache writes stayed at the standard "1.25× input" rate. This changes the arithmetic for any workflow with a stable 5K+ token system prompt or tool-schema block.

**Recipe (30–90 min):**

1. **Pick one Claude API call in your current portfolio** that has a large stable prefix (a tool schema, a system prompt, a knowledge doc, or a few-shot example set). Aim for **≥10K tokens of stable content**.
2. **Refactor to move that content into a `cache_control: {type: "ephemeral"}` block** in the first system message segment. Keep the variable per-request content after the cache boundary.
3. **Instrument.** Log `usage.cache_creation_input_tokens`, `usage.cache_read_input_tokens`, `usage.input_tokens`, and `usage.output_tokens` on every call. Compute cost per call in dollars using the current price sheet.
4. **Warm the cache** by hitting the endpoint once with the stable prefix (this is the write; costs 1.25× input rate; TTL is 5 min by default, or 1h if you request the beta).
5. **Run 20 real requests.** Compare mean cost/call to your pre-refactor baseline.
6. **Screenshot the log.**

**Expected result:** for workflows where cached tokens dominate the request (agents with large tool schemas, RAG pipelines with stable persona prompts, MCP servers with rich tool descriptions), **30–50% reduction in per-call cost** is realistic. Higher if your prompt was cache-friendly but you weren't using caching at all.

**Portfolio artifact:** a short README + one chart + one code snippet, published to your public repo. **This is the single strongest FDE-screen signal you can produce in <2 hours.** Bonus: it renews an out-of-date artifact from your [Opus 5 effort-toggle work called on 07-25](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort) with a currently-relevant pricing angle.

**Sources for the pricing table & mechanics:**
- [VentureBeat — 75% cost reduction for Fable cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`
- [Anthropic — Prompt caching (docs)](https://docs.claude.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [Anthropic Newsroom — Fable 5.1 announcement](https://www.anthropic.com/news) `[primary]`

---

## 2. Astra routing — when and how to actually pay 2.5× for GPT-6 Astra {#2-astra-routing}

**The move:** wrap your **primary Fable 5.1 call** with a **subtask-scoped Astra escalation** only for the specific request patterns where its capability edge justifies the price.

**Why now:** GPT-6 Astra is $10 in / $50 out per MTok (see [`01` §1](./01-big-lab-moves.md#1-gpt6-astra)) — **2.5× the price of GPT-5.6 Sol** and **1× Fable 5.1's headline** but Fable 5.1's cache reads win the majority of chat-shaped workflows on unit economics. Use Astra for the subtasks where it dominates:

**Route to Astra when:**
- **OSWorld-style computer use** — Astra 72.6% at ~47% less time/task than Sol; on a subtask where you're driving a real browser or OS, the time savings clear the cost delta.
- **Hard math verification** — FrontierMath T4 97.6%; use as a *verifier* on math-heavy reasoning that a cheaper model drafted, not as the primary generator.
- **Novel/adversarial coding subtasks** where you've seen Sol / Fable 5 / Opus 5 fail — worth trying Astra `effort=medium` once before you fall back to human intervention.

**Do NOT route to Astra by default when:**
- You have a cached large context (Fable 5.1 wins on unit economics with the new cache-read price).
- The task is a chat/knowledge/RAG default — Fable 5.1 medium is fine.
- Latency matters and the Fast mode cost (2× standard, so $20/$100) would blow the budget.

**Implementation pattern (Python-ish pseudocode):**

```python
async def solve(subtask):
    if subtask.type in ("computer_use", "math_verify", "novel_code_retry"):
        return await astra_call(subtask, effort="medium")
    return await fable_call(subtask, cached_prefix=SYSTEM_PROMPT)
```

Log every escalation with (subtask, primary_cost, escalated_cost, outcome_ok). After 100 real calls, you know the escalation rate and the marginal value.

**Sources:**
- [DataCamp — GPT-6 Astra: Features, Benchmarks, and Pricing](https://www.datacamp.com/blog/gpt-6-astra) `[analysis]`
- [BenchLM — GPT-6 Astra Benchmarks & Pricing (September 2026)](https://benchlm.ai/models/gpt-6-astra) `[aggregator]`

---

## 3. Multi-vendor hardening — turn the Sept-3 tri-outage into a portfolio artifact {#3-multi-vendor-hardening}

**The move:** wrap your primary Anthropic (or OpenAI) call in a **timeout + circuit-breaker + explicit fallback** that switches to a cross-vendor model at a **prompt-equivalent** level.

**Why now:** ChatGPT + Claude + Grok all had disruptions in a similar Sept-3 window (see [`02` §3](./02-new-emerging.md#3-tri-outage)). "We use multi-vendor" is now the entry-level answer at any FDE / Solutions interview; the differentiated answer shows the **fallback quality** and the **cost delta**.

**Reference implementation (5 hours, publishable Sunday):**

1. **Extract your primary Claude prompt** into a **provider-agnostic prompt object** with three renderers: Anthropic, OpenAI, Google (or Grok as a third).
2. **Set a per-vendor SLA budget:** e.g., Anthropic call must return within 12s and status 2xx or you fall to OpenAI Sol (or Astra `effort=low` for cost).
3. **Wrap each vendor call in a circuit-breaker** (fail 3-of-5 in 30s → open circuit for 60s, then half-open). `pybreaker`, `resilience4j`, or a custom implementation is fine.
4. **Log:** primary attempt, latency, outcome; if fallback, log the fallback vendor, latency, cost delta, and whether the response passed a quality gate you define.
5. **Ship a dashboard** — even a static Grafana or Streamlit page — showing: 24h fallback rate, cost delta of fallbacks, quality-gate pass rate on fallbacks.

**What the artifact says about you:** "I have shipped a production-quality multi-vendor abstraction, with observability, and I have real data on fallback quality." This is a **top-decile** portfolio piece for any Applied AI Engineer / FDE / Platform Engineer screen.

**Reference tools (any one; not endorsements):**
- LiteLLM, OpenRouter, Portkey (provider-abstraction libs)
- `pybreaker` (Python circuit breaker)
- OpenTelemetry for tracing across vendor calls

**Sources:**
- [AIdapted — AI News, September 4, 2026](https://www.aidapted.ro/en/articles/ai-news-september-4-2026-nvidia-astra-anthropic/) `[aggregator]`
- [AI Weekly — Sept-2 daily digest](https://aiweekly.co/ai-news-today) `[aggregator]`

---

## 4. MCP 2026-07-28 stateless — the migration is now the standard, ship one server this weekend {#4-mcp-standard}

**The move:** stand up **one small public MCP server on the 2026-07-28 spec**, deploy it behind a plain round-robin LB (Fly.io, Render, Cloudflare Workers, or an nginx + docker-compose on a $5 VPS), and commit the code + a 5-case eval to your public repo.

**Why now:** The 2026-07-28 spec is now the deployment standard. Handshake removed (SEP-2575), `Mcp-Session-Id` header removed (SEP-2567), every request self-describes via `_meta`, new `server/discover` method. Any request lands on any server instance — **no sticky sessions, no shared session store, no deep packet inspection at the gateway.** Google Developers Blog, Microsoft App Service, and the MCP Blog have all shipped official migration guides.

**Recipe (4–6 hours):**

1. **Pick a small useful tool surface** (3 tools). Suggestions that are visible on your job goals: "audit-my-anthropic-usage" (parses billing CSV, flags cache miss %); "summarize-my-arxiv-week" (given ORCID or a keyword set); "check-my-fde-portfolio" (a lint against your public repo for the 5 things an FDE screen looks for).
2. **Implement in the language you interview in.** Python (`mcp` SDK), Node/TS (`@modelcontextprotocol/sdk`), or Go all have current SDKs.
3. **Follow the stateless pattern:** every tool call carries `_meta`, no in-memory session state, use a KV store (Cloudflare KV, Redis, DynamoDB) for anything you must persist.
4. **Deploy behind a plain round-robin LB.** For portfolio: Fly.io or Render is easiest; the LB is included, cold-start visible in metrics.
5. **Write 5 eval cases** in a script that hits the deployed URL. Log pass/fail.
6. **README should include:** the OAuth 2.1 auth flow (even if simple), the load-test result showing 2 instances behind LB serving alternating requests, and a screenshot of a Claude Desktop or Claude Code session using the server.

**Portfolio artifact:** a public repo + a live URL + 5 passing evals + a README that explicitly names the 2026-07-28 spec compliance. **This is on-thesis to your active portfolio focus** ("Public MCP server (3 tools, 5-case eval, README, demo gif)" per [ME.md](../ME.md#active-portfolio-artifacts)).

**Sources:**
- [MCP Blog — The 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [MCP Blog — Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [modelcontextprotocol.io — Key Changes changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) `[primary]`
- [Google Developers Blog — Scaling AI Agent Infrastructure with MCP Stateless](https://developers.googleblog.com/scaling-ai-agent-infrastructure-with-the-mcp-stateless-updates/) `[secondary]`
- [Microsoft Community Hub — MCP Just Went Stateless — What the 2026 Spec Changes About Scaling on App Service](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) `[secondary]`
- [Obot — MCP 2026 Roadmap](https://obot.ai/blog/mcp-is-growing-up-the-2026-roadmap-takes-shape/) `[analysis]`

---

## 5. Assemble: the weekend artifact spec {#5-weekend-artifact}

If you do only one thing, do this **combined** artifact — it hits three interview questions at once:

**Title:** *"Fable 5.1 vs. Astra vs. Sol on a real MCP-server workflow, with cache accounting."*

**Deliverables:**
- The MCP server from §4, deployed on the 2026-07-28 spec, behind an LB.
- Its tool calls **routed via §2's escalation logic** (default Fable 5.1 with §1's caching; escalate to Astra on OSWorld-style / math-verify / novel-code subtasks).
- Wrapped in §3's multi-vendor fallback so a Fable outage transparently switches to Sol.
- A one-page write-up: cost/call table, fallback rate, escalation rate, cache-hit rate. Post to portfolio + one LinkedIn/X.

**Time budget:** 8–10 hours across Fri evening + Sat + Sun morning. Ship Sunday afternoon. Cross-link from ME.md.

**Sources rolled from §§1–4 above.**
