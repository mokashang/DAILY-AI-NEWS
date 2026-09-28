# Practical Skills & Tools — 2026-09-09

Four things you can do this week. **One is a 30-minute toggle that cuts your Claude cost by 25–45%** and it's the single highest-ROI change of the month. One is a keyword refresh for LinkedIn (10 min). One is the weekend artifact that answers three interview questions in one repo. And one is the Karpathy-agentic-engineering framing you should know cold for every applied-AI screen this fall.

Tags: `#practical #caching #fable-51 #mcp #agents #karpathy #prompt-engineering #cost #cli`

---

## 1. Enable prompt caching on Claude tonight — 25–45% cost cut, ~30 minutes {#1-cache-reads}

**Why now:** Fable 5.1 (2026-09-01) cut **cache-read pricing 75%**: from $1.00/MTok to **$0.25/MTok**. Cache writes unchanged at $12.50/MTok for a 5-minute cache. Anthropic's own math: **~25% cheaper on typical workloads, ~45% cheaper on highly-agentic workloads.** ([`01` §3](./01-big-lab-moves.md#3-fable-51))

Any workflow that repeatedly sends the same *system prompt + tools list + few-shot examples* will benefit. Agent loops (per-step retries, planner/worker/verifier chains, MCP-tool-heavy pipelines) benefit *most* — because their cache-hit rate is highest.

### How to turn it on (Anthropic Messages API)

Add `cache_control: { type: "ephemeral" }` to the last content block you want cached. Everything **up to and including** that block gets a cache-write on first request and cache-reads on every subsequent request within 5 minutes.

```python
import anthropic
client = anthropic.Anthropic()

# One-shot: cache the system prompt + tool definitions
resp = client.messages.create(
    model="claude-fable-5-1",
    max_tokens=1024,
    system=[
        {"type": "text", "text": "You are a careful, verifier-first agent…"},
        {"type": "text", "text": LONG_STABLE_TOOLS_MANIFEST,
         "cache_control": {"type": "ephemeral"}}   # <— mark the cache boundary
    ],
    messages=[{"role": "user", "content": user_turn}]
)
print(resp.usage)
# Look for cache_creation_input_tokens (first call) then cache_read_input_tokens (later)
```

### The 4 places to try it

1. **Stable system prompt** — the block you don't change per request. Highest hit rate.
2. **Tools / MCP manifest** — usually thousands of tokens, changes rarely. Cache-write once, save on every tool loop step.
3. **Few-shot examples** — 5–10 canonical examples that stay fixed. Great for classification / extraction pipelines.
4. **Long documents you retrieve once, chat over many times** — a codebase file, a policy PDF, a schema.

### The trap to avoid

If your prefix **changes even one token**, you get a cache-miss and eat the 25% cache-write premium. The rule: **stable parts first, dynamic parts last.** If your system prompt injects a timestamp — move it to the user message. If your tools list is dynamically constructed — freeze it.

### Cost-log recipe (this is the portfolio artifact)

For one week, log for every Claude call:
- `input_tokens`, `cache_read_input_tokens`, `cache_creation_input_tokens`, `output_tokens`
- Effort setting (if Opus 5)
- Model ID
- Wall time

Compute:
- **Effective input rate:** `(input_tokens * base_input + cache_read * cache_rate + cache_write * cache_write_rate) / total_input`
- **Cache hit rate:** `cache_read / (cache_read + input_tokens + cache_creation)`

Screenshot the "before caching / after caching" per-call cost. **That's your FDE interview artifact.**

**Sources:**
- [Anthropic — prompt caching docs](https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [VentureBeat — Anthropic's Claude Fable 5.1 and Mythos 5.1 arrive with a 75% cost reduction for Fable cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`

### Why it matters to you

- **Job lens:** *"Cut our agent cost 40% by moving stable prefixes into `cache_control` and freezing our tools manifest — trace attached"* is a **top-decile line** on a resume. Very few applicants have run this end-to-end with real numbers; the ones who have get FDE screens.
- **Startup lens:** If you sell a Claude-based product, caching is the **most immediate margin lift available** in September. You are not going to buy a cost cut this size anywhere else.
- **Insight:** Cache-first design is a *distinct discipline* from prompt engineering. Prompt engineering optimizes for quality per token; **cache-first prompt design optimizes for stable-prefix-length and mutation-locality**. That framing is going to be a hiring signal in Q4 as more teams discover it.

---

## 2. MCP 2026-07-28 migration checklist — the deployment floor is now stateless {#2-mcp-migration}

**Why now:** MCP `2026-07-28` finalized six weeks ago as stateless-by-default. If you built an MCP server before July 28, it still works over the compatibility shim — but you can't scale it horizontally with plain HTTP load-balancers, and clients using the new spec expect stateless-mode responses.

### 20-minute audit

Check your server against:

1. **No `initialize`/`initialized` handshake?** New spec removes it. If your server requires session establishment before first tool call, migrate.
2. **`Mcp-Session-Id` header removed?** New spec drops it. Session state must live in the client, not the server, or in an out-of-band store you control.
3. **`_meta` field on every request?** Protocol version + client info + client caps now travel inline per-request. Your handlers should read `_meta`, not connection state.
4. **OAuth 2.1?** Auth flow updated; if you still use API-key-in-header, keep it (deprecated but functional) but plan the OAuth migration for December.
5. **Server Cards published?** New capability discovery mechanic. Publish one; makes your server discoverable to registry-based clients.

### The migration tools

- **Anthropic's `mcp-lint 2.0`** ([primary tooling]) — CLI checker for spec compliance.
- **`mcp-migrate`** (community) — scaffolds spec-2026-07-28-compliant handlers from a `2025-*` server.

**Sources:**
- [New Relic — MCP is going stateless: What the new spec means for AI agents](https://newrelic.com/blog/ai/mcp-is-going-stateless) `[analysis]`
- [VentureBeat — MCP just got its biggest update ever](https://venturebeat.com/infrastructure/mcp-just-got-its-biggest-update-ever-heres-what-changes-for-ai-agents) `[secondary]`
- [Obot — MCP 2026 Roadmap: Stateless Core, Extensions & Enterprise Readiness](https://obot.ai/blog/mcp-is-growing-up-the-2026-roadmap-takes-shape/) `[analysis]`

### Why it matters to you

- **Job lens:** An MCP-2026-07-28-native server on your GitHub is an interview signal, but a **migration case study** (before/after diff + a p95 latency graph) is stronger. Pick a small existing MCP server (yours or one you know well), migrate it, write it up in a README.
- **Startup lens:** If you sell an MCP server as a paid product, migration to stateless-native lets you drop your infra cost — most legacy MCP servers were VMs with session storage; new ones can be **plain HTTP behind a load balancer**, container-per-request. That reprices your gross margin.
- **Insight:** MCP going stateless is quietly the **most important protocol-maturation** of the decade in agent infra — it turns "MCP server" from "long-lived service" into "stateless HTTP endpoint," which means **serverless AWS Lambda / Cloud Functions / Cloudflare Workers become the default deploy target**. This changes the operational cost model for a whole class of tools.

---

## 3. Karpathy's agentic-engineering framing — know it cold for every AI screen {#3-karpathy-framing}

**Why now:** Karpathy joined Anthropic (May 2026), and his *Sequoia AI Ascent 2026* talk + the four-rule `CLAUDE.md` playbook have quietly become **the shared vocabulary** of applied-AI interviews at Anthropic, OpenAI, and top applied-AI startups.

### The four rules for `CLAUDE.md` (Karpathy)

1. **Think before coding, state assumptions.** Force the model to plan and enumerate assumptions before writing any code. This is where quality wins are hidden — most bugs come from unstated assumptions.
2. **Simplicity first.** Minimum code that solves the problem, then stop. Prevents "helpful" over-engineering that hides bugs.
3. **Surgical changes.** Touch only what you must. Prevents scope-creep across the codebase.
4. **Goal-driven execution.** Define success criteria before starting. Prevents drift.

### The "agentic engineering" vs. "vibe coding" distinction

- **Vibe coding:** accept whatever the model writes, iterate on outputs.
- **Agentic engineering:** design specs, supervise plans, inspect diffs, write tests, run evals, manage permissions, isolate worktrees.

Karpathy's frame: **LLMs and RL automate what you can verify.** If you can't design a verifier, you can't scale the workflow. The interview question this maps to: *"How would you verify this agent's output at scale?"*

**Sources:**
- [Karpathy — Sequoia Ascent 2026 summary](https://karpathy.bearblog.dev/sequoia-ascent-2026/) `[primary]`
- [Andrej Karpathy's AI Engineering Playbook (2026)](https://www.aibuilderclub.com/blog/karpathy-ai-engineering-playbook) `[analysis]`
- [Karpathy's Four Recommendation Rules for a Better AGENTS.md](https://aridanemartin.dev/blog/karpathy-4-lines-claude-md/) `[analysis]`
- [Towards AI — How to Master AI Coding Agents: A Practical 2026 Guide](https://pub.towardsai.net/how-to-master-ai-coding-agents-from-vibe-coding-to-agentic-engineering-d4bdde5cbabb) `[analysis]`

### Why it matters to you

- **Job lens:** *Karpathy's four rules + verifier-first framing* is the mental model for **any coding-agent interview screen** this fall. Add three sentences to your resume: *"Design agent workflows verifier-first (Karpathy framing): success criteria, plan-then-code, surgical diffs, per-step evals."* You'll pass the first-round screen at half the FDE roles on the market with that alone.
- **Startup lens:** If you build a developer-facing AI product, ship a `CLAUDE.md` **or its equivalent** (a config file that encodes house style + verifier rules) *inside your product*. This is now table stakes for developer trust; Cursor, Cline, and Cognition all ship variants.
- **Insight:** The Karpathy "agentic engineering" framing is *the* professional identity a lot of engineers are settling into for 2026–2027 — and it maps cleanly onto senior-SWE compensation bands. It is the "DevOps 2010" moment: a specialty title that pays because it makes the whole team's shipping velocity real.

---

## 4. Weekend artifact — the cache-first agent (2–3 hours) {#4-weekend-artifact}

**Ship this weekend.** One repo, three interview questions answered.

### The build

- **Orchestrator:** Fable 5.1 (`claude-fable-5-1`) with a **stable system prompt + tools manifest** marked `cache_control: ephemeral`. Plans the task, decomposes into 3–5 subtasks.
- **Workers:** Claude Sonnet 5 (medium effort). Each subtask a fresh worker call.
- **Verifier:** Claude Haiku 4.5 (low effort). Every worker output goes through the verifier before the orchestrator sees it.
- **Tools:** a **fresh MCP 2026-07-28 stateless server** exposing 2–3 tools (a file read/write, a shell run, a search). Deploy as a Cloudflare Worker or a Lambda for the aesthetic — this shows you understand the new deploy pattern.
- **Log:** per-call CSV with `(model, effort, input_tokens, cache_read_tokens, cache_write_tokens, output_tokens, wall_ms, verifier_verdict)`.

### The task

Pick something real, small, and verifiable. A **task from your own life** works best:
- Rewrite three CS-application cold-outreach emails from a rubric.
- Summarize a 5-paper reading list into a 1-page synthesis (grad school prep).
- Refactor a small utility library in your GitHub for readability.

Verifiability matters more than ambition — the point is the **workflow-and-cost story**, not the domain.

### The write-up

`README.md` with:
1. What the agent does (2 sentences)
2. Architecture diagram (screenshot of a Mermaid render)
3. Cost log summary: total cost, cache-hit rate, per-subtask breakdown
4. What you'd do next (single paragraph)

Screenshot the log. **Post to LinkedIn Sunday evening** with a 3-sentence framing. This becomes the FDE-interview artifact you cite from now until Christmas.

### Why it matters to you

- **Job lens:** This artifact answers three FDE-interview questions in one repo — (a) *"Show me an agent workflow you designed"* (orchestrator + verifier), (b) *"How do you think about cost?"* (cache log), (c) *"How do you integrate real tools?"* (MCP 2026-07-28 server). It is on-thesis for every Applied AI role hiring this fall.
- **Startup lens:** The same architecture is a **product prototype** for any "agent-for-domain-X" wedge. Swap the tools + task, keep the cache/verifier scaffolding — you have a first working demo.
- **Insight:** The weekend project that lands you a job in September 2026 is *not* the biggest thing you can build. It's the **smallest thing that shows all three of: model routing, cost awareness, verifier composition**. That triangulation is the current mid-level applied-AI bar.

---

*Compiled from: Anthropic docs · Karpathy blog · Sequoia Ascent talk · Towards AI · New Relic · VentureBeat · Obot. Test the caching recipe against your own workflow tonight; the numbers will vary but the *direction* is stable — cached workflows are cheaper.*
