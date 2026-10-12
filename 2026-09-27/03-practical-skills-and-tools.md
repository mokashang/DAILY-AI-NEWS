# Practical Skills & Tools — 2026-09-27

Sunday is a *publication* day, not a *build* day. Three things to ship by 8 PM PT:

1. **Publish the router-to-MCP shim + 6 governance primitives** (Saturday's build; today's public release).
2. **Publish `NOTES-dolphinbench.md`** — a 500-word memory-eval-canon summary.
3. **Stage a router-diff branch** so you can push a DevDay-response update in ~30 minutes Tuesday night.

Tags: `#router #mcp #governance #agent-eval #portfolio #weekend #devday-prep`

---

## 1. Publish the router-to-MCP shim + 6 governance primitives {#1-publish-router}

**What this is:** the completed version of Saturday's project ([2026-09-26/03 §1](../2026-09-26/03-practical-skills-and-tools.md#1-router-shim) + [§2](../2026-09-26/03-practical-skills-and-tools.md#2-agent-governance)). If you got a working local version yesterday, today = README + demo gif + LinkedIn carousel. If you didn't ship yesterday, today = **3-hour compressed build + publish**.

**The router (v3 — post-Sept-22 price war):**

```python
def route(task_kind: str, ctx_len: int, budget_tier: str, batchable: bool) -> str:
    # Cheapest for offline batch — always try batch first
    if batchable and task_kind in {"summary", "tag", "extract"}:
        return "openrouter:batch:gpt-6-luna"          # $0.05 / $0.25 per 1M
    # Clerical / workhorse tier
    if task_kind in {"summary", "tag", "extract"} or budget_tier == "low":
        return "gpt-6-luna"                            # $0.10 / $0.50
    # Coding, tool-use, agentic long horizons
    if task_kind in {"code", "agent-tool-use", "computer-use", "chart-recognition",
                     "multi-disciplinary-reasoning"}:
        return "claude-opus-5.5"                       # $4 / $20; cache $0.20
    # Cheap general-purpose reasoning
    if task_kind in {"general-reasoning", "chat"}:
        return "gpt-6-sol"                             # $2 / $10
    # Long-context knowledge work, cache-heavy
    if task_kind == "long-context-qa" and ctx_len > 200_000:
        return "claude-fable-5.1"                      # $3 / $15; cache-friendly
    # Peak reasoning only when eval demands
    if task_kind == "peak-reasoning":
        return "gpt-6-astra"
    return "claude-opus-5.5"
```

*Numbers approximate — always verify each provider's live pricing before deploying. Sources tabulated at bottom.*

**The 6 governance primitives** (mount each as an MCP wrapper or middleware):

1. **Tenant identity.** Every request carries a `tenant_id` header; agent responses stamped with same. Enables per-tenant memory + audit.
2. **Scoped delegation tokens.** Short-lived, tool-scoped signed capabilities (JWT with `aud=<tool>`, `scope=<verb:resource>`, `exp` short). Never pass raw API keys.
3. **Audit log.** Append-only stream of `(tenant, agent, tool, args_hash, timestamp, cost_usd)`. Ship to an object store; queryable via one SQL view.
4. **Cost cap.** Per-tenant + per-agent-instance USD ceiling with soft-warn at 80% and hard-stop at 100%. Wire into your router's pre-hook.
5. **Tool allowlist.** Explicit list of allowed MCP tools per tenant/agent. Deny-by-default. Enforced at the MCP-client layer.
6. **Rate-limit ceiling.** Per-tenant tokens-per-minute + tool-calls-per-minute. Prevents runaway agents from bricking your bill on a single stuck loop.

Wrap each as a **PreToolUse hook** (per the [2026-09-24 Claude Code four-primitive discipline](../2026-09-24/03-practical-skills-and-tools.md)) so misuse is a compile-time error, not a production one.

**Publish checklist (Sunday, before 8 PM PT):**

- [ ] GitHub repo public. README with problem → solution → run steps → results.
- [ ] 5-case eval table in the README. Include per-request cost + latency + tier.
- [ ] Price/quality plot as `plots/pareto.png`.
- [ ] Demo gif in the README (Claude Code invoking the router; ~15 sec).
- [ ] `LICENSE` (MIT is fine).
- [ ] LinkedIn carousel post (5 slides: problem → 3 primitives → demo gif → eval table → link).
- [ ] Cross-post to X and Anthropic Community Discord.

**Sources for pricing (verify before publishing):**
- [Anthropic — Claude Opus 5.5](https://www.anthropic.com/claude-opus-5-5) `[primary]`
- [OpenAI Pricing](https://openai.com/api/pricing/) `[primary]`
- [Google — Gemini API Pricing](https://ai.google.dev/pricing) `[primary]`
- [Artificial Analysis — model pricing + benchmark tracker](https://artificialanalysis.ai/) `[analysis]`
- [OpenRouter — Batch API](https://openrouter.ai/docs/features/batch) `[primary]`
- [MacRumors — Claude Opus 5.5](https://www.macrumors.com/2026/09/22/anthropic-claude-opus-5-5/) `[secondary]`
- [Yahoo Finance — Claude 5.5 Release](https://finance.yahoo.com/technology/ai/articles/anthropic-claude-5-5-release-185148663.html) `[analysis]`
- [2026-09-24/03 §1 three-tier routing rubric](../2026-09-24/03-practical-skills-and-tools.md) `[primary — this repo]`
- [2026-09-26/03 §§1–2 router-shim + governance](../2026-09-26/03-practical-skills-and-tools.md) `[primary — this repo]`

### Why it matters to you

- **Job lens:** Every FDE / AI Integration / Solutions role interview between Sept 28 and Q1 2027 is going to ask "walk me through your routing + governance decisions." A published repo with the 6-primitive skeleton is a **10-minute interview slam-dunk** that no non-portfolio candidate can compete with.
- **Startup lens:** If you're founding, the router+governance repo *is* the demo you show first. It also doubles as the **proof-of-competence** every design-partner asks for before signing.
- **Insight:** The 6 primitives aren't optional — they're the *minimum surface area* for any agent that touches production data. When SB 1047 signs (or its federal successor lands), these become the *statutorily-expected* controls; ship them now while they're still a differentiator, not a checkbox.

→ Cross-link: [`01` §2 DevDay stage a diff](./01-big-lab-moves.md#2-devday-t2) · [`05` §1 skill reprice](./05-career-and-startup.md#1-reprice-check).

---

## 2. Publish `NOTES-dolphinbench.md` — the 500-word memory-eval synthesis {#2-notes-dolphinbench}

**Why:** the [Sept 26 memory-eval canon](../2026-09-26/04-research-progress.md#1-dolphinbench) is now the reading list. **DolphinBench (arXiv 2609.24971) + Jev-Mem (2609.23986) + MemCalib (2609.24259) + EverMemBench (2602.01313)** = 4 papers, all released in the last 30 days. Reading DolphinBench closely + skimming the other three gives you the vocabulary for **memory-as-routing** — a phrase you'll want in your senior-agent-eng interviews for the rest of Q4.

**Suggested structure for `NOTES-dolphinbench.md` (~500 words):**

- **What the benchmark measures.** Pareto frontier of agent memory across accuracy × cost × latency. 200 tasks/persona.
- **The 4-way canon.** How DolphinBench + Jev-Mem + MemCalib + EverMemBench triangulate the same underlying question (agent memory has a joint accuracy/cost/latency budget; measure all three).
- **The "memory-as-routing" idea.** Memory isn't a single primitive; it's a routing decision (which sub-store, which retention window, which access pattern) — same as model routing.
- **Where it maps to your router.** Add a `memory_tier` axis to your router: `hot-store` (in-context), `warm-store` (session cache), `cold-store` (vector DB + retrieval); each with a cost/latency signature.
- **Open question.** No paper yet on **memory + governance** (audit-log on which memory read/write, per tenant). Founder wedge.

Publish inside the same repo as the router artifact. Cross-link.

**Sources:**
- [arXiv 2609.24971 — DolphinBench](https://arxiv.org/abs/2609.24971) `[primary]`
- [arXiv 2609.23986 — Jev-Mem](https://arxiv.org/abs/2609.23986) `[primary]`
- [arXiv 2609.24259 — MemCalib](https://arxiv.org/abs/2609.24259) `[primary]`
- [arXiv 2602.01313 — EverMemBench](https://arxiv.org/abs/2602.01313) `[primary]`
- [2026-09-26/04 §1 DolphinBench](../2026-09-26/04-research-progress.md#1-dolphinbench) `[primary — this repo]`

### Why it matters to you

- **Job lens:** In interview: "how would you evaluate agent memory in production?" → "I'd start with the DolphinBench methodology — measure accuracy, cost, and latency jointly rather than optimising one — and route memory the same way I route models: hot/warm/cold with per-tier cost + latency SLOs." That's a senior-level answer memorized in 15 minutes.
- **Startup lens:** The unfilled wedge is **memory + governance**: an audit-logged, per-tenant-scoped memory service with DolphinBench-shape metrics. Seed-fundable Q1 2027 if you can ship a working library.

→ Cross-link: [`04` §1 memory-eval synthesis](./04-research-progress.md#1-memory-eval-synthesis).

---

## 3. Stage a router-diff branch for DevDay Tuesday {#3-stage-devday-diff}

**Why now:** DevDay is Tuesday Sept 29. Whatever OpenAI ships (a new GPT-6 variant, a governance primitive, a pricing shift), you want a **router update pushed the same night** — that's a very high-signal "I can move at the pace of the frontier" artifact.

**Preparation checklist for the diff:**

- [ ] On your published router repo, create branch `devday-2026-response`.
- [ ] Add empty scaffolding for two probable branches: `if task_kind == "<new-variant>"` and a governance-primitive wrapper (in case DevDay ships an Agent 365-analogue).
- [ ] Draft a placeholder LinkedIn post: "**DevDay diff — [X] shipped, here's the router update in [Y] lines**". Publish once you push.
- [ ] Set a reminder for **Tuesday 6 PM PT** to check the OpenAI blog + The Decoder + TechCrunch.

**Sources (Tuesday to watch):**
- [OpenAI News](https://openai.com/news/) `[primary]`
- [OpenAI DevDay](https://openai.com/devday/) `[primary]`
- [The Decoder](https://the-decoder.com/) `[secondary]`
- [TechCrunch AI](https://techcrunch.com/category/artificial-intelligence/) `[secondary]`
- [Artificial Analysis](https://artificialanalysis.ai/) `[analysis]`

### Why it matters to you

- **Job lens:** Cadence-of-shipping is itself a signal. "Router shipped Sunday; DevDay-response diff shipped Tuesday" beats "router shipped Sunday" by an order of magnitude in interview-story leverage.
- **Insight:** Pre-staging the branch is the trick — most people wait until DevDay lands and then take 2–3 days to react. Being ready for the diff means you *are* the diff, publicly, within hours.
