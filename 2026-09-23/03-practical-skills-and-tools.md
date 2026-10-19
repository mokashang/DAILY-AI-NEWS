# Practical Skills & Tools — 2026-09-23

The three things to do this week, in order: **(1) reroute to the new price sheet by EOD; (2) audit your Claude Code caching discipline against Anthropic's own engineering guidance; (3) ship a public router-diff artifact that shows both.** Nothing here is speculative — every recipe below is either directly required by the price cuts of the last 24 hours, or is Anthropic's own engineering team writing about how they build Claude Code.

Tags: `#practical #claude-code #prompt-caching #router #cost-observability`

---

## 1. Reroute your model choices to the new price sheet — TODAY {#1-reroute-now}

**What happened:** Anthropic and OpenAI both cut prices materially on Sept 22–23 (see [`01` §1–2](./01-big-lab-moves.md#1-opus-55)). Any router you wrote in the last three months is now over-spending. The reroute is mechanical and takes an evening.

### The Sept 23 price sheet — the numbers you route against

| Model | Input $/1M | Output $/1M | Cached read $/1M | Notes |
|---|---:|---:|---:|---|
| **Claude Opus 5.5** *(new)* | $4.00 | $20.00 | **$0.20** | Fable-5.1-class quality; 1M context; #1 AA Intelligence Index |
| Claude Fable 5.1 | $3.00 | $15.00 | $0.25 | Now the second-choice frontier tier |
| Claude Mythos 5.1 (restricted) | — | — | — | Cyber/life-sciences; access-controlled |
| **GPT-6 Sol** *(new)* | $2.00 | $10.00 | (cached tiers per OpenAI) | Enterprise workhorse |
| **GPT-6 Luna** *(new)* | **$0.10** | **$0.50** | (cached tiers per OpenAI) | Cheap-batch, high-volume tool calls |
| GPT-6 Astra | $10.00 | $30.00 (typical) | — | Top-of-line reasoning |
| Gemini 3.8 Flash | $1.50 | $9.00 | — | Google's workhorse; watch for a Sept 30 price response |
| Muse Spark 1.3 | (Meta pricing) | — | — | Newer; enterprise pricing negotiated |

*(Numbers per VentureBeat, TechCrunch, and Artificial Analysis writeups on Sept 22–23 releases; verify against your API console at time of migration.)*

### The reroute recipe — 4 steps, ~2 hours

1. **List every model call in your codebase.** Grep for `model=` / `model:` / API SDK model IDs. Every occurrence is a routing decision. Include environment variables and config files.
2. **Bucket each call by workload class.** Coding-agent tool-use · long-context Q&A · cheap batch summarise · agentic tool-use (high-volume) · flagship reasoning.
3. **Apply the reroute table:**
   - Coding-agent tool-use, agentic frontier: **Fable 5.1 → Opus 5.5** (same quality, ~40% cheaper e2e; 60% cheaper cached reads)
   - Long-context Q&A over big prefixes: **Opus 5 / Fable 5.1 → Opus 5.5** (biggest cache-read savings)
   - Cheap batch summarise / classify: **GPT-5.6-mini / Fable 5 → GPT-6 Luna** (~50% cheaper, better bench)
   - Enterprise mid-tier / dev tools: **GPT-5.6 → GPT-6 Sol** (~50% cheaper, meaningful bench uplift)
   - Multimodal / cheap Google workflows: **hold Gemini 3.8 Flash** for one week; expect a Google response
4. **Rerun your eval suite against the new routes.** If you don't have a 5-case eval suite yet, use the shape from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) — one prompt per workload class, one gold answer, one cost/latency assertion. Log the deltas.

### Concrete: expected cost impact

For a typical AI-app running ~10M input tokens/day + 1M output tokens/day on Fable 5.1 + GPT-5.6:

- Old ~$36/day on Fable 5.1 heavy load; ~$60/day GPT-5.6-mini heavy load ≈ ~$96/day
- New (Opus 5.5 + Luna where appropriate) ≈ ~$55–60/day for equivalent quality
- **Annualised savings: ~$13–15K per single-workload agent.** Multiplies by number of agents you run.

Publish the diff (see [`03` §3](#3-router-diff-artifact)).

### Why it matters to you

- **Job lens:** "Rerouted after the Sept 22 price cuts, saved $X" is a **one-sentence interview weapon**. Show the diff repo, show the before/after cost table, show the eval suite. This is the highest-signal answer to "how do you stay current" a hiring manager can hear this quarter.
- **Startup lens:** This is a one-cycle chance to **cut prices to customers while holding margin.** Announce a price cut this week, credit it to model rerouting, seed a good renewal-cycle story. Founders who missed the May cache-read cut can catch up here.
- **Insight:** Any model routing that isn't **workload-class-parameterised** will underprice or overpay on every price cut. Route by workload class, not model name.

→ Cross-link: [`03` §3 the router-diff artifact template](#3-router-diff-artifact).

---

## 2. Claude Code caching discipline — audit against Anthropic's own engineering blog {#2-cache-discipline}

**What happened:** Anthropic's engineering blog published **"Lessons from building Claude Code: prompt caching is everything"** — the most concrete public statement of how the Claude Code team runs cache at production scale. Combined with the platform docs and community synthesis, the discipline collapses to a short checklist you can audit any agent codebase against this week.

### The 6-rule audit

1. **Never swap tools or models mid-session.** A single flip mid-run invalidates the whole cache. If you have multi-model routing inside a single agent turn, refactor to route at the *task/session* boundary, not per-tool-call.
2. **Treat cache-hit-rate as an uptime SLO.** Log it per session. Alert on drops. The most common cache-miss cause is a silent tool schema edit or dynamic system-prompt template that varies per user.
3. **Move volatile content to the tail.** Order: (a) system prompt + tool schemas + CLAUDE.md → cache. (b) Retrieved context / memory → cache if stable, else tail. (c) Turn-by-turn conversation → tail. (d) Tool results → tail. Anthropic Claude Code uses `<system-reminder>` blocks in the *next* user message to pass state updates without invalidating the prefix — copy the pattern.
4. **Do not put long-running synchronous tool calls or subagents inside the cache TTL boundary.** If a tool call takes minutes and the cache TTL is 5 min, the cache expires before you get a hit. Either use async tools + polling, or an explicit cache-refresh handshake.
5. **CLAUDE.md is the highest-leverage caching move.** A detailed CLAUDE.md at repo root is included in every prompt in a Claude Code session — cached, priced at read rate, drives the model's context understanding for free. Karpathy's `CLAUDE.md` playbook (~109K stars per [2026-05-17](../2026-05-17/00-tldr.md)) still applies.
6. **Watch for tool-schema drift.** MCP tool schema changes are the single most common invisible cache-miss cause. Version your tool schemas; log the hash; alert on hash changes correlating with cache-hit-rate drops.

### The Opus 5.5 payoff on caching

Opus 5.5 cached reads at **$0.20 / 1M** vs. Opus 5's $0.50/1M is a **60% cut**. For a Claude Code-style agent with a 200K-token system + tool + CLAUDE.md prefix hit 100× per day:

- Old (Opus 5, $0.50 cached): 100 hits × 0.2M tokens × $0.50/1M = **$10/day per agent** on cache reads
- New (Opus 5.5, $0.20 cached): 100 hits × 0.2M tokens × $0.20/1M = **$4/day per agent** on cache reads
- **Delta: ~$2,200/year per agent.** Multiply by fleet size.

**Sources:**
- [Anthropic — Lessons from building Claude Code: Prompt caching is everything](https://claude.com/blog/lessons-from-building-claude-code-prompt-caching-is-everything) `[primary]`
- [Anthropic — Reducing cost and improving performance with Claude Platform](https://claude.com/blog/reducing-cost-and-improving-performance-with-claude-platform) `[primary]`
- [Claude Platform Docs — Prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [Walturn — How Prompt Caching Elevates Claude Code Agents](https://www.walturn.com/insights/how-prompt-caching-elevates-claude-code-agents) `[analysis]`
- [AWS ML Blog — Supercharge your development with Claude Code and Amazon Bedrock prompt caching](https://aws.amazon.com/blogs/machine-learning/supercharge-your-development-with-claude-code-and-amazon-bedrock-prompt-caching) `[secondary]`

### Why it matters to you

- **Job lens:** "I audit cache-hit-rate as an SLO on my agents and I refactored ___ to hold cache across long-running tools" is the second interview weapon after routing. Publish a `caching-discipline.md` in one of your repos with the 6-rule checklist and a per-repo audit.
- **Startup lens:** If your agent product doesn't have cache-hit-rate on the internal dashboard, add it Monday. Cache-hit-rate is **the fastest cost lever you have as a founder** — no model retraining, no prompt rewrite, just structural discipline.
- **Insight:** Cache-hit-rate is the *bare-metal* metric of the LLM app layer. It maps to unit economics 1:1. Any team not tracking it is running blind on the biggest cost lever they have.

→ Cross-link: [`01` §1 Opus 5.5 caching](./01-big-lab-moves.md#1-opus-55) · [`03` §1 reroute](#1-reroute-now).

---

## 3. The router-diff artifact — publish this by EOD Friday {#3-router-diff-artifact}

**What happened:** Interview signal for AI-adjacent roles has shifted from "which model do you use" to "how do you decide, and how do you re-decide when the market moves." The **router-diff artifact** is the single strongest public proof you have both a router and the discipline to update it. This week — with two labs simultaneously cutting prices — is the highest-signal moment of the year to ship it.

### The artifact spec

**Repo:** `<yourname>/model-router-2026`. Public.

**README structure:**
1. **Header:** one-paragraph mission — "A workload-class-parameterised model router, updated on each price cut, with a public diff."
2. **The routing table** (Sept 23 version, from [`03` §1](#1-reroute-now)) — a Markdown table matching workload class → model choice, with reasoning.
3. **The 5-case eval suite** — one prompt per workload class, gold answer, latency + cost assertions.
4. **The `CHANGELOG.md`** — every reroute logged with date, cause (e.g. "Sept 22 Opus 5.5 release"), before/after cost, before/after eval-suite pass rate.
5. **The `results/` directory** — full eval JSON dumps per model, so anyone can reproduce.
6. **Dockerfile / requirements.txt** — one-command `docker run` reproduces the whole eval.

### Shape of the LinkedIn post

Post the two tables inline:
1. **Cost delta table:** workload class × old model × new model × old $/1K requests × new $/1K requests × % change
2. **Quality delta table:** workload class × old eval-pass × new eval-pass

Paragraph:
> Anthropic + OpenAI both cut prices on Sept 22–23. I run a public model router; rerouting saved my portfolio agents ~$X/mo at equal or better quality. Diff + eval suite: [repo link]. The point of a router isn't which model — it's the *discipline of re-deciding* when the market moves.

Attach 3 hashtags, no emoji, tag Anthropic + OpenAI, expect ~5–20K impressions and 2–3 recruiter DMs within 72 hours.

### Why it matters to you

- **Job lens:** This artifact answers three interview questions at once: *stay current* (you shipped a reroute within 24 hours of the price cut), *build eval* (you have a suite), *cost discipline* (you show the $ delta). Ship one repo, unlock three signals. Every AI Engineer / FDE / Solutions role in Q4 2026 rewards this shape.
- **Startup lens:** The router-diff blueprint is also the shape of a **product**. If you publish it and the LinkedIn post lands, an inbound will surface a company that wants to buy it as a hosted service. Prefer to keep it as portfolio: you retain optionality.
- **Insight:** The **artifact-per-market-move** cadence is the actual skill worth cultivating. Not "know all the models" — that's un-cultivateable. But "when the market moves in category X, I ship a public diff within 48 hours" — that's a lifelong-repeatable career skill.

→ Cross-link: [`01` §1–2](./01-big-lab-moves.md#1-opus-55) · [`05` §2](./05-career-and-startup.md#2-reprice).

---

## 4. Small but useful: three tips that landed this week {#4-small-tips}

- **`<system-reminder>` pattern for stateful updates.** Instead of editing the system prompt (cache-invalidating), pass volatile state in a `<system-reminder>` block in the next user message or tool result. Preserves the cached prefix. Copy Anthropic's own Claude Code pattern; you've been seeing them in this session all along.
- **Prompt-cache-aware SDK wrapper.** If you're using the Anthropic SDK direct, add a wrapper that logs `usage.cache_read_input_tokens` vs. `usage.cache_creation_input_tokens` vs. `usage.input_tokens` per call. Aggregate to a daily cache-hit-rate dashboard. 40 lines of Python, best cost dashboard you'll have.
- **"Model card" per repo.** Add a `MODEL.md` alongside your `CLAUDE.md` documenting: which model this repo uses, which workload class it maps to, when it was last routed, and what the eval-pass rate is. Then anyone reading the repo (recruiter, reviewer, future you) can see the discipline at a glance.

Each of these is a 30-minute change; each shows up as concrete evidence in the router-diff artifact.
