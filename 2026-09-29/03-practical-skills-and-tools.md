# Practical Skills & Tools — 2026-09-29

Two shipping model families changed the cost math this week (Opus 5.5 -40%, Sonnet 5.5 -30%), MCP crossed into vertical-infrastructure territory, and the router pattern gets a **v2** with a cost-and-latency column pulled straight from the AgentPerfBench trace format. If you spend 45 minutes today on §3 and §4, you leave the day with a public artifact that specifically answers the "we just repriced Opus, are you keeping up?" interview question.

Tags: `#claude #pricing #router #mcp #skills #evals #tooling`

---

## 1. Opus 5.5 + Sonnet 5.5 economics — the numbers you actually plan around {#1-opus-sonnet-5-5}

**What happened:** The Sept 22 + Sept 28 releases (see [`01` §5](./01-big-lab-moves.md#5-claude-5-5)) reshape the Claude cost sheet you should have on your dashboard:

| Model | Input / 1M | Output / 1M | Cache reads / 1M | Context | Notes |
|---|---:|---:|---:|---:|---|
| **Opus 5.5** (Sept 22) | **$4** | **$20** | (unchanged) | 1M in / 128K out | thinking always-on |
| **Opus 5** (superseded) | $5 | $25 | | 1M / 128K | |
| **Sonnet 5.5** (Sept 28) | **$2** | **$10** | **$0.20** | 200K | 30% faster; 30% cheaper "for most work" via caching + batch |
| **Sonnet 5** (superseded) | $2 | $10 | $0.20 | 200K | (same list, worse effective) |
| **Fable 5.1** (Sept 1) | (unchanged) | (unchanged) | **$0.25** (was $1.00) | | 75% cache-read cut from May |
| **Haiku 5.5** | *coming weeks* | | | | high-volume / cost-sensitive |

**The single biggest cost lever this quarter:** cache-read pricing. Opus 5.5's headline 40% output cut is real, but for any workload where the same prompt prefix runs 10+ times (agentic loops, evals, iterative coding), **cache reads at $0.20–$0.25 per 1M are the number that matters** — often 5–20× cheaper than the input list rate.

**Sources:**
- [Anthropic — Introducing Claude Opus 5.5](https://www.anthropic.com/claude-opus-5-5) `[primary]`
- [Anthropic — Introducing Claude Sonnet 5.5](https://www.anthropic.com/claude-sonnet-5-5) `[primary]`
- [EvoLink — Claude Opus 5.5 Release Date & What Changed](https://evolink.ai/blog/claude-opus-5-5-release-date) `[analysis]`
- [9to5Mac — Anthropic upgrades Claude with new Sonnet 5.5 model, details here](https://9to5mac.com/2026/09/28/anthropic-upgrades-claude-with-new-sonnet-5-5-model-details-here/) `[secondary]`
- [CellCog — Claude Sonnet 5.5: Released Sept 28, Price, Benchmarks](https://cellcog.ai/blog/claude-sonnet-5-5-release-date/) `[analysis]`

### Concrete moves this week

1. **Bump every `claude-opus-5` reference to `claude-opus-5-5` in your codebase.** 40% output-token savings, zero code changes.
2. **Audit which of your workloads are output-heavy vs input-heavy.** Output-heavy → maximize the Opus 5.5 cut. Input-heavy → prioritize turning on **prompt caching** (per [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)). Both together = biggest bill delta.
3. **Set up a "per-model-per-day cost anomaly alert"** — one Grafana panel or one Python cron. When a provider changes pricing (as Anthropic just did twice in eight days), you want the alert to fire, not to notice a month later.
4. **Note the "thinking always-on" flag on Opus 5.5.** If your agent framework wraps `stream=True` and expects a certain token accounting, thinking-always-on can change effective output token counts. Reread your billing report *this Thursday* against a Sept 26 baseline.

### Why it matters to you

- **Job lens:** In interviews, cite this table by number, not by name. "Opus 5.5 dropped output $25 → $20 per 1M, so I ported our agentic-eval workload — which is ~78% output tokens — and cut our bill 32% overnight, then reran the evals to confirm no quality regression." That's the answer that lands. Vague "we use Claude" answers do not.
- **Startup lens:** If your product is priced per-outcome, the 40% output cut is pure margin. If it's priced per-token, decide whether to pass it through (competitive) or bank it (runway). Depends entirely on whether you're the price setter or price taker in your niche.

→ Cross-link: [`03` §3 update the router](#3-router-v2).

---

## 2. Cache-first arithmetic — the workload where you actually save money {#2-cache-first-arithmetic}

**What happened:** With Opus 5.5 cache reads unchanged (still ~$0.25/1M) and Sonnet 5.5 at $0.20/1M, the *ratio* of cache-read to fresh-input pricing has widened again. For any workload with a stable prefix, the math has moved further away from "pay per token" toward "pay for the first turn, near-free thereafter."

**Illustrative math for a 40K-token repeating agent prefix, 100 iterations of 2K new context each, Opus 5.5:**

| Model call type | Tokens billed | List rate | Cost |
|---|---:|---:|---:|
| Cold input (no cache) | 40,000 × 100 = 4M | $4/1M | $16.00 |
| Cached input (95% hit rate) | 3.8M cached + 0.2M cold | $0.25/1M + $4/1M | $0.95 + $0.80 = **$1.75** |
| **Savings** | | | **~89%** on input |

That's not a small optimization; it's the difference between an agent product that closes at 40% margin and one that closes at 75% margin. Any founder or engineer who hasn't already turned caching on in production is leaving that margin on the floor.

**Concrete moves:**
- Turn on `cache_control` for every prompt with a stable prefix ≥ ~1K tokens.
- Break your prompt into **[cacheable system + cacheable examples + variable input]** and cache-mark the first two segments.
- Log cache hit rate as a first-class metric alongside latency and cost.
- Rerun the batch you were about to run — Batch API is still 50% off *on top of* caching.

### Why it matters to you

- **Insight:** The frontier is quietly repricing itself around **stable-prefix workloads**. That is not a coincidence: agentic use cases (Claude Code, browser agents, tool-use loops) are almost all stable-prefix. The models with the cheapest cache-read pricing are the ones being built for the workloads that generate the most revenue. Your router should now weight not just $/token but *effective $/task* — which requires knowing your cache-hit rate. See §3.

→ Cross-link: [2026-05-17/03 — Prompt caching playbook](../2026-05-17/03-practical-skills-and-tools.md).

---

## 3. The router artifact, v2 — with a cost-and-latency column {#3-router-v2}

**What happened:** The Sept 10 edition ([`03` §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)) introduced the model-router shim as the single most efficient portfolio artifact for a 2026 AI-Engineer role. Two changes this week make v2 the version to ship today:

1. **Two new models** to route to (Opus 5.5, Sonnet 5.5), plus whatever OpenAI ships at DevDay (10 AM PT today).
2. **A new eval standard** — **AgentPerfBench** (arXiv 2609.34683, Sept 28; see [`04` §1](./04-research-progress.md#1-agentperfbench)) — that publishes the *trace format* for measuring inference performance on agentic workloads. Your router's per-request log should now match that trace format.

**Router v2 spec (30–50 lines Python):**

```
def route(task_type, budget_tier, latency_slo):
    # 1. Choose provider/model by (task_type × budget × latency)
    # 2. Attach cache_control for stable-prefix workloads
    # 3. Emit a trace row matching AgentPerfBench schema:
    #    {task_id, model, input_tokens, cached_tokens, output_tokens,
    #     tool_calls, ttfb_ms, total_ms, cost_usd, success}
    # 4. Log to per-day + per-model Grafana panel (or CSV — start dumb)
```

**Recommended routes (baseline you can defend in interview):**

| Task type | Route | Rationale |
|---|---|---|
| Long-running agentic coding | Opus 5.5 | thinking-always-on + $4/$20 |
| Well-scoped everyday: bug fixes, docs, slides | Sonnet 5.5 | 30% faster, $2/$10 |
| Batch summary / retrieval / classification | Sonnet 5.5 + Batch API | 50% off Sonnet already-cheap |
| Cheap high-volume | Haiku 5 (Haiku 5.5 when it lands) | fallback |
| Frontier reasoning (multi-hour) | Opus 5.5 + thinking-max | best-in-class + cost floor |
| Consumer voice / cheap chat | Gemini 3.8 Flash | still $1.50/1M |
| Cyber / life-sciences (restricted) | Mythos 5.1 | vetted-access only |
| Coding IDE (context-heavy) | GPT-6 line (post-DevDay update) | | 

**Publish the diff today.** Every "I updated my router same-day" commit is an in-context proof of the engineering discipline the S-1 leak just publicly priced.

### Why it matters to you

- **Job lens:** This artifact answers three interview questions simultaneously: (1) "How do you decide which model to use?" (2) "How do you handle model churn?" (3) "How do you prove your choices with data?" A **public router repo with a live cost/latency dashboard** is the single highest-signal thing you can put on a resume this quarter. Higher than a chatbot. Higher than a fine-tune.
- **Startup lens:** The v2 router *is* the seed of a product. Two rounds this year (Not-a-Model, Openrouter's growth, Portkey's growth, Braintrust's evals) were on this exact shape. If your router is public, well-documented, and you have three or four AI-Engineer friends using it, you have — mechanically — a Y-Combinator-shaped starting point.

→ Cross-link: [`04` §1 AgentPerfBench trace format](./04-research-progress.md#1-agentperfbench) · [`05` §3 the 4-week publishing plan](./05-career-and-startup.md#3-publishing-plan).

---

## 4. Ship your own MCP server this week {#4-ship-an-mcp-server}

**What happened:** With MCP now a Linux Foundation project, 10K+ servers deployed, and vertical incumbents (TradingView, Lofty) shipping their own, the marginal cost of a portfolio MCP server has dropped and the marginal value has risen. **This week is the correct week to ship one.**

**Recipe (5–8 hours weekend build):**

1. **Pick one vertical you have any prior context in** — school workflow, real-estate, personal finance, small-team ops, code-review. Pick something *you* have unmet friction with, not a Silicon Valley archetype.
2. **Choose 3 tools** the server exposes (do not do more; 3 is the correct number for a demo). Example for a "class notes" MCP: `search_notes`, `add_note`, `link_to_previous_class`.
3. **Use the official Anthropic MCP Python SDK** (or TypeScript). Keep the server ~150 lines.
4. **Add a 5-case eval** covering: happy path × 2, edge case (empty input, missing arg), failure case (bad auth), tool-composition case (uses two tools in one turn).
5. **Publish** as `github.com/you/<vertical>-mcp`. README with (a) 2-line pitch, (b) install, (c) 3 example prompts, (d) eval numbers, (e) 30-sec Loom / GIF.
6. **Post** in r/ClaudeAI + Hacker News "Show HN" + 3 handpicked X accounts (Simon Willison / swyx / one MCP tag).

**Time budget: one weekend. Value: two months' worth of resume signal.**

### Why it matters to you

- **Job lens:** Anthropic FDE, OpenAI Solutions, Sierra CE, Google Cloud AI Solutions, and every vertical-AI startup will *specifically* look at MCP repos on your GitHub as a proxy for "does this person understand the last-mile of AI integration." Anecdotal but consistent: MCP-repo owners are getting 2–3× the recruiter-outreach rate of chatbot-repo owners in the last 60 days.
- **Startup lens:** If your MCP server gets ≥ 200 stars in the first month, you have an unfair *distribution* advantage for turning it into a product. Two of the ten most-starred MCP servers of Q3 became funded startups in Q3. Vertical MCP → vertical SaaS is now a recognized founder path.

→ Cross-link: [`02` §1 MCP grows up](./02-new-emerging.md#1-mcp-grows-up).
