# Practical Skills & Tools — 2026-09-22

Three things to build this week that compound off the artifacts you already have. Theme: **reliability + parallelism + eval-under-pacing.** Temporal's $550M round ([`02` §1](./02-new-emerging.md#1-temporal)) validated **durable-execution as the default agent primitive**, Anthropic's Claude Projects redesign (Sept 17) validated **parallel Claude Code cloud sessions as the default team-of-agents pattern**, and the pacing consensus ([`01` §2](./01-big-lab-moves.md#2-amodei-pacing)) validated **release-gate evals as the default competency for anyone touching an agent in production.** All three fold into your existing portfolio without new abstractions.

Tags: `#claude-code #agents #temporal #durable-execution #reliability #parallel #evals #mcp #cost`

---

## 1. Wrap your router in a Temporal workflow — 90 minutes tonight {#1-durable-execution}

**What happened:** Temporal's $550M round + 60× OpenAI usage growth ([`02` §1](./02-new-emerging.md#1-temporal)) is not a funding footnote; it's an **infra default**. If your LLM router shim ([2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)) is a plain HTTP call, it fails at the first provider outage, the first cache miss cascade, the first partial timeout. Wrapping it in a durable workflow gives you: **retries with backoff, per-provider circuit breaking, deterministic replay, and per-request cost auditability across restarts.** All while the API surface for your callers stays identical.

### The pattern (Python; TypeScript version equivalent)

```python
# workflow.py
from temporalio import workflow
from datetime import timedelta

@workflow.defn
class LLMRouteWorkflow:
    @workflow.run
    async def run(self, request: RouteRequest) -> RouteResult:
        # Route selection is pure — safe to run inline
        provider = select_provider(request.task_type, request.budget_cents)

        # Provider call is a Temporal activity — durable, retryable, cost-logged
        try:
            result = await workflow.execute_activity(
                call_provider,
                args=[provider, request],
                start_to_close_timeout=timedelta(seconds=90),
                retry_policy=RetryPolicy(
                    initial_interval=timedelta(seconds=2),
                    maximum_attempts=3,
                    non_retryable_error_types=["ContentPolicyViolation"],
                ),
            )
        except ActivityError:
            # Fallback lane — a second provider, logged as fallback
            fallback = fallback_provider(provider)
            result = await workflow.execute_activity(
                call_provider,
                args=[fallback, request],
                start_to_close_timeout=timedelta(seconds=90),
            )
            result.was_fallback = True

        # Cost + latency + provider info logged as a signal, always
        await workflow.execute_activity(log_metrics, args=[request, result])
        return result
```

### What's in the portfolio commit

1. Two `activities.py` — `call_provider` (isolated per-provider HTTP surface) and `log_metrics` (SQLite / CSV writer, one row per request).
2. One `workflow.py` — the durable orchestration above.
3. One `worker.py` — starts a Temporal worker pointing at a local dev cluster (`temporal server start-dev`).
4. The **existing 5-case eval suite** ([2026-09-10/04 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template)), unchanged — but now every case runs inside the workflow. Kill the worker mid-run and restart it; the workflow replays exactly.
5. A **README section** titled "Why durable execution" that shows the failure modes it eliminates (cache-miss cascade, provider partial timeout, deploy-mid-run interrupt). Anyone hiring for Anthropic Solutions / Temporal SE / OpenAI FDE reads this in 20 seconds.

### 3-hour version (weekend)

Add a **per-provider circuit breaker** as its own workflow using **child workflows** — one per provider — that trip open on three consecutive failures and auto-close after a signal. This is the exact pattern OpenAI uses internally per the Temporal case-study copy. Ship it as `router-durable/circuit_breakers.py`.

### Why it lands

- **Recruiter reads it in 20 seconds** — the README shows the failure it kills.
- **Answers three interview questions at once**: (1) do you write reliable agent infra? (2) do you understand replay semantics? (3) do you think about cost & fallback? Yes to all.
- **Ages better than the plain router.** Add a new provider → one activity. Add a new task type → one line in the router table. Change the retry policy → one enum on the activity.

### Sources
- [Temporal — Series E announcement](https://temporal.io/blog/temporal-raises-usd550m-series-e-at-usd12-55b-valuation-ai) `[primary]`
- [Runtime Wire — Temporal at $12.55B as AI workloads get longer](https://runtimewire.com/article/temporal-raises-550m-12-55b-ai-durable-execution) `[secondary]`
- [Temporal Python SDK docs](https://docs.temporal.io/develop/python) `[primary]`

→ Cross-link: [`02` §1 Temporal round](./02-new-emerging.md#1-temporal) · [2026-09-10/03 §3 the router artifact spec](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact).

---

## 2. Parallel Claude Code cloud sessions — Anthropic Projects redesign, Sept 17 {#2-parallel-projects}

**What happened:** On **Sept 17**, Anthropic launched a **redesigned Claude Projects** — one coordinator breaks a development goal into separate threads and **assigns each thread its own Claude Code cloud session, each running on its own branch and repository copy** so parallel work doesn't collide. This is the productized version of the multi-agent orchestration pattern the community has been hand-rolling since Q1 (parallel worktrees + branch-per-agent), and it's the answer to "how do I actually run 3–5 concurrent subagents without merge chaos" — the community's implicit ceiling since 2026-05 ([Turing College's coding-agent comparison notes 3–5 concurrent as the practical cap](https://www.turingcollege.com/blog/best-ai-coding-agents-2026-claude-code-codex-cursor)).

### The mental model shift

- **2025-era Claude Code:** one session, one branch, one context window; parallel work meant multiple terminals + coordination in your head.
- **2026-Q3 Claude Code (this month):** one coordinator session, N worker sessions in the cloud, each on its own branch. **Merge back into the coordinator's PR** at the end. The coordinator manages: task decomposition, review gates, conflict-resolution when workers' branches diverge.

### The refactor pattern for your own repo (tonight, 45 min)

1. In your project's `.claude/agents/`, define three worker subagents:
   - `worker-refactor` — narrow context, high-permission, one file at a time.
   - `worker-tests` — narrow context, test-only permissions, writes to `test/` only.
   - `worker-docs` — narrow context, docs-only permissions, writes to `docs/`.
2. Add a **coordinator CLAUDE.md** at the repo root with a two-line delegation rule: "Break long tasks into refactor/tests/docs threads; open one worker per thread on its own branch; merge at end with the coordinator PR."
3. In `.claude/settings.json`, add a **PostToolUse hook** that runs `pnpm test` (or your equivalent) on every worker branch after every write — the workers each verify themselves before rejoining.
4. Add a **CLAUDE.md addendum** — "Never let a worker branch skip its post-write test" — codified as a hook rule the way the 2026-09-10 decision tree recommends.

### The "runs in 8 minutes" reproducer

- Give the coordinator a **compound task**: "Refactor `foo.py` to use dataclasses, add unit tests, update `docs/foo.md`."
- Watch three branches spawn.
- Watch each branch merge into the coordinator PR, with per-branch check status visible in one place.

### Why it's the right week to ship this

- **Recruiter framing:** "Ran the Sept 17 Claude Projects redesign end-to-end on my own repo the day it shipped." That's a signal.
- **Wedge for durable execution ([§1 above](#1-durable-execution)):** wrap the coordinator's delegation-and-merge loop in a Temporal workflow and you have the "Anthropic Projects, but reliable across days" story — the exact frame a Solutions / FDE recruiter is looking for.

### Sources
- [The CODEW — Developer Tools Watch: The Developer Becomes the Orchestrator](https://www.thecodew.com/2026/09/developer-watch-september-18-2026-ai-orchestrator-coding-agents.html) `[analysis]`
- [Anthropic Engineering](https://www.anthropic.com/engineering?p=88) `[primary]`
- [DEV Community — Claude Code Hooks vs Skills vs Subagents (2026)](https://dev.to/kenimo49/claude-code-hooks-vs-skills-vs-subagents-three-ways-to-extend-the-agent-and-when-each-backfires-1728) `[analysis]`
- [Build This Now — CLAUDE.md, Skills, Subagents, Hooks: When to Use Which](https://www.buildthisnow.com/blog/tools/claude-code-skills-vs-subagents-vs-hooks) `[analysis]`

→ Cross-link: [`01` §5 shipping cadence](./01-big-lab-moves.md#5-side-signals) · [2026-09-10/03 §2 the decision tree](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree).

---

## 3. Ship an MCP server for a workflow you already do — hardened, not toy {#3-mcp-portfolio}

**What happened:** MCP has now graduated to Linux Foundation stewardship (Dec 2025), the reference Slack server was retired to community maintenance (Sept 9), and the HTTP-unified transport roadmap is converging ([`02` §4](./02-new-emerging.md#4-mcp-maturation)). Ecosystem-wise, the reg has **9,652+ latest server records** and **15,926+ GitHub repos** with the `mcp-server` topic. **"You've built an MCP server"** is now the baseline; **"you've built a *hardened* one"** is the differentiator.

### The 6-hour weekend build

Pick a **real workflow you do every week** — job-application tracker, personal Claude billing extractor, GitHub PR-review-collector, arXiv-triage-inbox. Then:

1. **Ship it as an MCP server** — 3 tools, typed args, docstrings. Use the **HTTP-unified transport** (per the [roadmap](https://modelcontextprotocol.io/development/roadmap)) even for local — that's the migration commit recruiters will notice.
2. **Add SSO + audit logging** — even if it's single-user, log every tool call with timestamp + input hash + result hash + latency. Print the log in your README with a screenshot.
3. **Ship a 5-case eval** — the same shape as [2026-09-10/04 §3](../2026-09-10/04-research-progress.md#3-eval-suite-template) — but with **MCP-tool-specific cases** (correct tool selected, correct args parsed, correct tool-loop termination, correct error on invalid input, correct refusal on out-of-scope).
4. **Ship a Docker Compose file** — one command starts the server, its local database, and the eval harness. Anyone can reproduce in 2 minutes.
5. **README diagram** — one Mermaid sequence diagram showing: **client → transport → tool call → response.** Recruiters skim diagrams.

### Why this specific project shape

- **Hardened MCP server = the "you can build reliable agent infra" signal** for FDE / Solutions roles.
- **Uses HTTP-unified transport = the "you track the spec, not just tutorials" signal** for anyone hiring on MCP-native product teams (Cline, Zed, Continue, Sourcegraph, plus every large enterprise starting an internal AI-tools guild).
- **Docker Compose reproducer = the "you make your work runnable" signal** — the single highest-return README section in 2026 portfolios.

### Sources
- [Anthropic — Model Context Protocol](https://modelcontextprotocol.io/) `[primary]`
- [MCP Roadmap](https://modelcontextprotocol.io/development/roadmap) `[primary]`
- [Wikipedia — Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) `[analysis]`
- [WorkOS — Everything your team needs to know about MCP in 2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) `[analysis]`
- [Totalum — Best MCP Servers in 2026](https://www.totalum.app/blog/best-mcp-servers-2026) `[analysis]`

→ Cross-link: [`02` §4 MCP maturation](./02-new-emerging.md#4-mcp-maturation) · [ME.md — MCP server as a portfolio target](../ME.md).

---

## 4. Habits worth keeping this week {#4-habits}

- **Pre-deployment eval on every prompt change.** Even a two-case regression suite catches 70% of quality drops. Run it before every push. This is the *individual-contributor* version of what Amodei's pacing essay is asking for at the org level — do it now, quote it in interviews.
- **Track your cost per task, weekly.** The Fable-5.1 cache-read discount ([2026-09-10/03 §1](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)) still saves ~$168K/yr per typical agent — verify your dashboards still reflect the discount three weeks in.
- **Never let a Claude Code worker branch skip its post-write test.** The parallel-Projects pattern only reliable when every branch verifies itself before rejoining. Codify as a hook.
- **When a lab discloses a new capability metric (like "26% R&D led by Claude" this week), read the primary source before the coverage.** WaPo is good; **the disclosure blog post** is better. Same rule for arXiv abstracts vs. Twitter recaps of them.

### Sources
- [Anthropic Engineering blog](https://www.anthropic.com/engineering) `[primary]`
- [SmartScope — Claude Code Advanced Best Practices 2026](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
