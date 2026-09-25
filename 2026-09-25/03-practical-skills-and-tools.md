# Practical Skills & Tools — 2026-09-25

Three tactical things that will change your production bill and your GitHub before Monday: **Opus 5.5 economics**, the **OpenRouter Batch API**, and a **5-line router refresh** you can push tonight.

Tags: `#claude #openrouter #agents #pricing #cost-router #claude-code #skills`

---

## 1. Opus 5.5 economics — the 20-minute audit that saves you 30–40% {#1-opus-55-economics}

**The math to memorize (per 1M tokens):**

| | Input | Output | Cache read | Notes |
|---|---|---|---|---|
| **Opus 5.5** (Sept 22, 2026) | **$4** | **$20** | **$0.20** | Extended thinking always-on; 1M ctx; 128K max out |
| Opus 5 | $5 | $25 | $0.50 | — |
| Fable 5.1 (est.) | ~$10 | ~$50 | $0.25 | Prior flagship |
| Sonnet-tier (est.) | ~$3 | ~$15 | ~$0.30 | Workhorse |
| Haiku (est.) | ~$0.80 | ~$4 | ~$0.10 | Volume |
| **GPT-6 Astra** (est.) | ~$15 | ~$75 | — | Prestige tier |
| **GPT-6 Sol** | $2 | $10 | — | Mid-tier |
| **GPT-6 Luna** | **$0.10** | **$0.50** | — | Cheapest reasoning tier |

**The 20-minute audit (do this today):**

1. **Export last 30 days of API spend** by model. Most providers have a CSV on the dashboard; if not, sum from your own logs.
2. **Classify each call by task type** — coding, long-context Q&A, cheap batch summary, agentic tool-use, extraction, sentiment. (If you don't have this metadata, add it now.)
3. **Recompute cost at the new tier map**:
   - Coding / agentic tool-use → **Opus 5.5**
   - Long-context Q&A → **Opus 5.5** (or Sonnet if latency-critical)
   - Cheap batch summary / extraction → **GPT-6 Luna** or **Haiku** *in OpenRouter Batch* → half again cheaper
   - One-shot generation with brand voice → **Fable 5.1** (only if you've already tuned prompts for it)
4. **Set an alert** at your current daily spend as a hard ceiling. When routing is right, actual spend will drift below the alert; that gap is your monthly savings.

**Extended-thinking-always-on caveat:** Opus 5.5 charges *thinking tokens* against your output budget. Every call now uses ~2–3× more output tokens than the same prompt on Opus 5. Two mitigations:
- **Cap `max_tokens`** explicitly on every call (128K is a *ceiling*, not a target).
- Route latency-sensitive paths to **Fast Mode** (2× price, 2.5× speed) *only* where the UX needs it.

**Sources:**
- [Anthropic — Claude Opus 5.5 model docs (via llm-stats aggregate)](https://llm-stats.com/models/claude-opus-5-5) `[primary/aggregator]`
- [VentureBeat — Opus 5.5 beats Fable 5.1 at 60% cheaper API price](https://venturebeat.com/technology/anthropic-releases-claude-opus-5-5-beating-fable-5-1-on-key-agentic-benchmarks-at-60-cheaper-api-price) `[secondary]`
- [Finout — Claude Opus 5.5 Pricing 2026: What Anthropic's New Flagship Actually Costs](https://www.finout.io/blog/claude-opus-5.5-pricing-2026-what-anthropics-new-flagship-actually-costs) `[analysis]`
- [Codersera — Claude Opus 5.5: Complete Guide](https://codersera.com/blog/claude-opus-5-5-complete-guide-2026/) `[secondary]`
- [Digital Applied — Claude Opus 5.5 Breaking Changes](https://www.digitalapplied.com/blog/claude-opus-5-5-launch-pricing-benchmarks-2026) `[secondary]`

### Why it matters to you

- **Job lens:** A saved-screenshot before/after ("last-30-day cost by model, $X → $Y") is a **1-page portfolio artifact** that lands better in an FDE interview than any GitHub star. It proves you look at real numbers.
- **Startup lens:** Bake this audit into your onboarding runbook. Every new eng hire's week-1 task is: "reproduce the router audit on our current traffic." Two benefits — you catch drift, and you train the new hire on the actual $-shape of your product.

---

## 2. OpenRouter Batch API — the "did-I-miss-a-free-lunch" playbook {#2-batch-api}

**The claim:** any request that doesn't need a sub-second answer can now go through OpenRouter's Batch API for **~50% off** across 70+ models, with median 7-min turnaround.

**The playbook:**

1. **Inventory your async workloads** — grep your codebase for background workers, cron jobs, nightly evals, embedding re-index, sentiment sweeps, offline enrichment. Every one of these is a batch candidate.
2. **Add `batch: true`** to the OpenRouter request. That's the entire code change on the happy path. (Details in the [Batch API Quickstart](https://openrouter.ai/docs/batch-quickstart).)
3. **Add a batch fallback** — if the batch queue exceeds your SLA (rare, but possible on the p99 = 10.3 hr tail), fall back to the standard endpoint. 5 lines.
4. **Measure per-request cost before/after.** Log the model, the batch flag, and the actual $ charged. Expect a **35–50% reduction on the workloads that migrate.**

**When *not* to batch:**
- Real-time user-facing calls (chat, agent tool-use, live coding assist).
- Small volumes where the batch overhead exceeds the savings (< ~100 requests/batch is usually not worth it).
- Anything where a single request must be strictly ordered against subsequent calls.

**Combined with Luna at $0.10/$0.50:** batch-Luna = **~$0.05 / $0.25 per 1M** on a reasoning-capable model. That's the current floor of the market.

**Sources:**
- [OpenRouter Blog — Batch API launch](https://openrouter.ai/blog/announcements/batch-api/) `[primary]`
- [OpenRouter Docs — Batch API Quickstart](https://openrouter.ai/docs/batch-quickstart) `[primary]`
- [SuperpowerDaily — half-price AI requests](https://superpowerdaily.com/posts/openrouter-adds-batch-api-with-half-price-ai-requests-for-non-urgent-work) `[secondary]`

### Why it matters to you

- **Job lens:** If your public GitHub already has the router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact), add a `--batch` flag by end of week. That's a real feature, not a demo, and it's exactly the shape of PR an FDE hiring manager expects to see in a candidate's public history.
- **Insight:** The Batch API tells you something structural about the market: **latency-tolerant workloads have separated into their own SKU tier.** That's the same thing that happened to compute (spot instances) 10 years ago. Watch for **model-provider-native batch SKUs** to arrive within 90 days — OpenAI, Anthropic, Google will not leave OpenRouter alone as the sole batch-cost-arbitrageur.

---

## 3. The 5-line router refresh — do it tonight {#3-router-refresh}

**Prereq:** the router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact). If you didn't ship it two weeks ago, start there tonight.

**Tonight's 5-line change:**

```python
# router.py — minimal diff for 2026-09-25 model landscape
ROUTES = {
    "code_agent":     {"model": "anthropic/claude-opus-5-5",  "batch": False},
    "code_oneshot":   {"model": "openai/gpt-6-sol",           "batch": False},
    "long_qa":        {"model": "anthropic/claude-opus-5-5",  "batch": False},
    "bulk_extract":   {"model": "openai/gpt-6-luna",          "batch": True},   # <- Batch API
    "sentiment":      {"model": "anthropic/claude-haiku-4-5", "batch": True},   # <- Batch API
    "brand_voice":    {"model": "anthropic/claude-fable-5-1", "batch": False},
    "vision":         {"model": "google/gemini-3-8-flash",    "batch": False},
}
```

**And the 5-case eval to keep it honest:**

```python
# eval.py — one asserting case per route
EVAL_CASES = [
    ("code_agent",   "Refactor this Python function to be async and add type hints: ...", {"contains": "async def"}),
    ("long_qa",      "Given this 200KB spec, list the 5 hardest edge cases for feature X.", {"min_items": 5}),
    ("bulk_extract", "Extract company + amount + date from these 500 news headlines.",       {"min_rows": 490}),
    ("sentiment",    "Classify each of these 1000 tweets as {pos, neg, neutral}.",           {"labeled": 1000}),
    ("vision",       "Read the receipt in this image; return items[] with unit_price.",      {"has_items": True}),
]
```

**Instrumentation to add (one line per call):**

```python
log.info(json.dumps({
    "route": route,
    "model": ROUTES[route]["model"],
    "batch": ROUTES[route]["batch"],
    "cost_usd": response.usage.cost_usd,
    "latency_ms": elapsed,
    "task": task_hash,
}))
```

**Push the PR tonight with a `README.md` update showing:**
- Model choices per route with links to today's model announcements.
- One-line "why this model here" per route.
- A screenshot of the eval passing.
- One `docs/cost.md` file with the per-1K-user-turn cost table under the new routing.

**Sources:**
- [Base router artifact — 2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)
- [OpenRouter Docs — Batch API Quickstart](https://openrouter.ai/docs/batch-quickstart) `[primary]`
- [F22 Labs — Claude Code Tips: 10 Real Productivity Workflows for 2026](https://www.f22labs.com/blogs/10-claude-code-productivity-tips-for-every-developer/) `[secondary]`

### Why it matters to you

- **Job lens:** This PR alone is the **best single-day resume-line you can produce this quarter.** It shows: (1) awareness of Sept 22 releases, (2) cost discipline, (3) real evals, (4) instrumented observability. That is the four-corner FDE spec.
- **Startup lens:** Same PR, deployed to your prod router, drops your cost of goods 25–40% *for free*. If you have investors on the cap table, send them a screenshot of the before/after — it's a quiet but *very* trust-building signal about how you run the shop.

---

## 4. Claude Code — the September 2026 CLAUDE.md decision-tree, refreshed {#4-claude-code-decision-tree}

**What's changed since [2026-09-10/03 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree):** the four primitives (Hooks / Skills / Subagents / CLAUDE.md) are unchanged, but the *volume* of published community MCP servers crossed **1,000+** (per the [2026 practitioner guides](https://medium.com/data-science-collective/effective-claude-code-workflows-in-2026-what-changed-and-what-works-now-c93ebc6f8f50)), which forces a new rule:

**The five-or-six-server rule.** A short tool list keeps the agent focused; more than six MCP servers in one project consistently *degrades* Claude's routing. Pick five:
1. **Filesystem** (built-in).
2. **Git / GitHub** (repo state).
3. **Search / grep** (repo-scoped).
4. **One infra server** (Docker / K8s / your cloud).
5. **One vertical server** (Slack, Linear, Sentry, Figma — whichever your team lives in).

Anything else, put behind a **Skill** — Skills are the right container for "context this project needs occasionally," MCP is the right container for "capability this agent needs continuously."

**Also**, since Opus 5.5 has extended thinking always on, **Plan Mode does slightly less lifting than before** — the model already reasons at length by default. Use `/plan` when you want the *user-visible reasoning*, not because you need better reasoning.

**Sources:**
- [Medium (Sean Moran) — Effective Claude Code Workflows in 2026](https://medium.com/data-science-collective/effective-claude-code-workflows-in-2026-what-changed-and-what-works-now-c93ebc6f8f50) `[secondary]`
- [okhlopkov — My Claude Code Setup After 4 Months of Daily Use (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[secondary]`
- [iwoszapar — Claude Code Best Practices: CLAUDE.md and Checks](https://www.iwoszapar.com/p/claude-code-best-practices) `[secondary]`
- [Carmelyne Thompson — Mastering Claude Code (2026): Workflow Mastery](https://carmelyne.com/mastering-claude-code-part-2-workflow/) `[secondary]`
- [Nimbalyst — Claude Code MCP Setup: A Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-mcp-setup/) `[secondary]`
- [Frugal Testing — Claude AI and MCP Servers Guide 2026](https://www.frugaltesting.com/blog/claude-ai-and-mcp-servers-the-developers-practical-guide-for-2026) `[secondary]`

### Why it matters to you

- **Job lens:** A `CLAUDE.md` in every one of your repos with the four-primitive discipline and the five-server limit is a **stealth interview signal** — every FDE hiring manager who audits your GitHub sees it, whether or not they mention it.
- **Insight:** The community MCP-server explosion is a **discoverability crisis in the making**. Whoever ships the first **"MCP registry with real quality signal + curated packs by role"** wins a small but real market. Sub-weekend prototype territory.
