# Practical Skills & Tools — 2026-07-25

Two things that ship *this week* on your Anthropic stack and directly change the artifacts on [`ME.md`](../ME.md). **(1) The Opus 5 `effort` toggle** — a per-call knob you can wire into any agent team by tonight — is the single highest-leverage cost lever added since prompt caching. **(2) MCP 2026-07-28** finalizes Monday, and every MCP server you've published needs a migration PR by August. Together they turn "I built a Claude agent" into "I built a production-grade Claude agent, on-spec, with a documented cost/quality curve" — which is the FDE / Applied AI Engineer interview in one sentence.

Tags: `#playbook #claude-code #opus-5 #effort-toggle #mcp #stateless #migration #agents #portfolio #cost`

---

## 1. The Opus 5 `effort` toggle: per-subtask cost/quality routing on ONE model {#1-opus-5-effort}

The old cost lever (from [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) was **which model in which seat** — Opus planner + Sonnet workers + Haiku verifier, ~40% cheaper than all-Opus. Opus 5 adds a *second* lever inside the same model:

**The lever:** each Opus 5 request accepts `effort: "low" | "medium" | "high"`, trading reasoning depth for latency and cost per subtask — without changing the model ID your team runs on.

| Seat | Effort | Why |
|---|---|---|
| **Orchestrator / planner** | `high` | The plan is the expensive-reasoning payoff; get it right, cheaper executions cascade from there |
| **Worker (spec'd subtask)** | `medium` | Default. Well-scoped work; medium reasoning is usually indistinguishable from `high` on bounded tasks |
| **Verifier / adversarial reviewer** | `medium`–`high` | Cheap to run redundantly; you want it *sharper* than the worker it's checking |
| **Formatter / summarizer / label-picker** | `low` | Deterministic-ish work — spend the tokens elsewhere |

**Combine with the old model-seat lever, don't replace it.** A production 2026 agent team is now a **matrix** of (model, effort) per seat: an Opus-5-planner-high + Opus-5-worker-medium + Haiku-verifier team is materially cheaper *and* smarter than last month's Opus-planner + Sonnet-workers team.

**The reliability primitive still applies verbatim** ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)): **plan-first, don't implement.** The `effort=high` planner drafts; you annotate; you send back **"address all notes, don't implement yet."** Only then do the `effort=medium` workers execute.

**One-hour project you can ship tonight (portfolio artifact):**
1. Pick a real repo (yours or an OSS project you know).
2. Have Claude Code build a small orchestration script that runs the same "add a feature + tests" task three times — once at each effort level.
3. Log: **wall-clock, input tokens, output tokens, cache-read tokens, subagent count, tests-passing-on-first-run, tests-passing-after-one-fix.**
4. Publish a one-page README: *"Opus 5 effort levels on a real coding task — the cost/quality frontier."*
5. Tag it `#claude-opus-5 #effort-routing`; screenshot the table for interviews.

**Pair with prompt caching (still the biggest lever overall).** With Sonnet 5's 1M context at $3/$15 (intro $2/$10 through Aug 31) and Opus 5 at $5/$25, prompt caching stays the biggest per-dollar move: `cache_control: {"type": "ephemeral"}` on the last block of any stable prefix, cache **write** = 1.25× input, **read** = 0.10× input (90% off). Every reused prefix that isn't cached is money on fire.

**Sources:**
- [Anthropic — Introducing Claude Opus 5 (effort parameter)](https://www.anthropic.com/news/claude-opus-5) `[primary]`
- [Anthropic Prompt Caching Docs — platform.claude.com](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [Vellum — Claude Opus 5 Benchmarks Explained](https://www.vellum.ai/blog/claude-opus-5-benchmarks-explained) `[analysis]`
- [Agentbrisk — Prompt Caching Deep Dive: Cut Anthropic API Costs by 90%](https://agentbrisk.com/blog/prompt-caching-deep-dive-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** *"Per-subtask effort routing + prompt caching, on Opus 5, with a documented cost/quality curve"* is a stronger resume line than any generic "used Claude Code" bullet. It's literally what an [FDE loop at Anthropic](./05-career-and-startup.md#2-fde-market) scores on the customer-conversation round.
- **Startup lens:** Effort routing **is the margin lever** for any Claude-for-X product in 2026. If you can't answer "what effort level for what subtask" for your product, your gross margin is fragile — a competitor who can will underprice you sustainably.
- **Insight:** Effort levels move model routing from an **API-tier decision** to a **compiler-level decision**. Expect Anthropic to add finer-grained knobs (per-tool effort, effort-adaptive budgets) over the next two releases. Build your telemetry now so you can react to those knobs as they land — the teams already logging per-call cost will just add columns.

---

## 2. Migrate your MCP servers to the 2026-07-28 stateless spec (deadline: this week) {#2-mcp-migration}

The [MCP 2026-07-28 spec finalizes Monday](./02-new-emerging.md#4-mcp-stateless). If you've published any MCP server, migrating **before September** is the difference between "server author on the current spec" and "server author on last quarter's spec." The former is worth a resume line; the latter is not.

**Server-author migration checklist (concrete steps):**
1. **Remove session state.** Delete `Mcp-Session-Id` header handling and any in-memory / DB session-store code. Any request can hit any instance.
2. **Read client metadata from `_meta`.** Everywhere your handler was reading connection-scoped state, switch to `request._meta.*` instead.
3. **Update response headers.** Add `MCP-Protocol-Version: 2026-07-28`. Accept `Mcp-Method` and `Mcp-Name` on requests so a load balancer / API gateway can route per tool.
4. **Replace `initialize` with `server/discover`.** Publish capabilities at `/.well-known/mcp-server-card` (Server Card) so clients discover you before connecting.
5. **Refactor interactive prompts.** Anything that used SSE for server-to-client input now returns an `InputRequiredResult { inputRequests, requestState }`; the client re-issues the original call with responses populated.
6. **Migrate any 2025-11-25 experimental Tasks API code** to `tasks/get | tasks/update | tasks/cancel`.
7. **Add OAuth 2.1** — single Google/GitHub sign-in flow to connect. No JSON config required by the client.
8. **Test back-compat** — decide whether you'll dual-support the old spec (safer for existing users) or hard-cut (simpler codebase). Anthropic's guidance leans toward dual-support for 90 days.

**Portfolio move (repo-level):** run through this list on your own public MCP server, then **write it up** — *"Migrating a Public MCP Server to the 2026-07-28 Stateless Spec: 8 Steps and 3 Things That Broke."* That single blog post is a stronger interview signal than the migration itself, because it demonstrates you *understood* the spec change, not just followed a script.

**Sources:**
- [MCP Blog — 2026-07-28 Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [Digital Applied — MCP Goes Stateless: Migration Guide](https://www.digitalapplied.com/blog/mcp-2026-07-28-spec-stateless-migration-guide) `[secondary]`
- [WorkOS — MCP 2026 Spec + Agent Authentication](https://workos.com/blog/mcp-2026-spec-agent-authentication) `[analysis]`
- [GitHub Changelog — GitHub MCP Server on 2026-07-28 spec](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification/) `[primary]`

### Why it matters to you

- **Job lens:** Every FDE and Applied AI Engineer role in H2 2026 will list MCP experience. "Migrated a production MCP server to the 07-28 spec with load-balancer-ready statelessness" is a **specific, current, verifiable** version of that skill — most applicants will still be showing 2025-vintage servers.
- **Startup lens:** **MCP Apps + Server Cards** open a distribution channel that didn't exist last month. Any vertical SaaS you'd build (or founding-engineer at) should evaluate shipping an MCP surface *first*, then a web UI. If a Claude user can discover your capability from `.well-known` and connect with one OAuth click, you've cut acquisition cost meaningfully — and you've made your product a **first-class citizen inside the Anthropic ecosystem** that's now leading enterprise share ([`02` §5](./02-new-emerging.md#5-anthropic-economic-index)).
- **Insight:** Stateless + OAuth is when a protocol **becomes boring** — and boring protocols are the ones that get built on at scale. HTTP became boring in ~2000; REST in ~2010; MCP is having its 2026 moment. The 60 days after a protocol becomes boring are historically the best window to build servers on it, before the platform layer fills in.

---

## 3. Bonus tips worth adopting this week

- **`/fork` vs. `/subtask` in Claude Code (v2.1.212+).** `/fork` now creates an **independent background session** (own entry in `claude agents`) that survives compaction; `/subtask` is the classic in-session isolated-context subagent. Also new per-session caps: `CLAUDE_CODE_MAX_SUBAGENTS_PER_SESSION=200`, `CLAUDE_CODE_MAX_WEB_SEARCHES_PER_SESSION=200`, and MCP tool calls over 2 min auto-background via `CLAUDE_CODE_MCP_AUTO_BACKGROUND_MS`. — [Claude Code Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- **Nested subagents to depth 3 by default (v2.1.219, 2026-07-24).** Combined with the June-landed depth-classifier (rejects duplicative spawns), you can build **planner → workers → verifiers** hierarchies inside a single Claude Code run. Cap with `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH=2` if you want tighter cost bounds. Use `--forward-subagent-text` (v2.1.211) in headless mode to see depth-2+ output stream. — [ofox.ai deep-dive](https://ofox.ai/blog/claude-code-nested-subagents-2026/) `[analysis]`
- **The Anthropic large-scale migration pattern.** Anthropic published (2026-07-16) the recipe they used to move Bun from Zig→Rust in <2 weeks: rulebook + dep map → categorize tests (unit/integration/external) → external tests become **parity oracle** run against both old and new code → validate the LLM-judge on both correct *and* deliberately-broken output → orchestrate hundreds of parallel subagents through **8 phase gates + 3 rounds of adversarial review** → final parity diff. The pattern is directly stealable for any migration or big-refactor task. — [Anthropic — How Anthropic runs large-scale code migrations with Claude Code](https://claude.com/blog/ai-code-migration) `[primary]`
- **Simon Willison's fireside with Cat + Thariq (Claude Code team, 2026-07-21).** If you read one thing from a practitioner this week, this is it. — [simonwillison.net/2026/Jul/21/fireside-chat-cat-thariq](https://simonwillison.net/2026/Jul/21/fireside-chat-cat-thariq/) `[analysis]`

---

## 4. This weekend's artifact: the one repo that answers three interview questions

You already have the **dual-model sanitiser** safety project and the **MCP-server + eval** portfolio queued ([`ME.md`](../ME.md)). This weekend, **fold both into one** and add today's news:

- **Orchestration:** Opus 5 planner (`effort=high`) + Opus 5 worker (`effort=medium`) + Haiku verifier — §1.
- **Verification:** the agent is evaluated against **your migrated 07-28 MCP server** (§2), not a mock. Show it discovering the tool from the Server Card, connecting via OAuth, and refusing an injected malicious instruction.
- **Cost:** log **tokens per step, per model, per effort level**. Produce a table. Compute per-run $ at current API prices.

Write the README so a hiring manager can read it in 90 seconds and see: *(a) you understand agent orchestration in 2026-shape (effort + model + verifier); (b) you can build against the real MCP spec, not a mock; (c) you can talk about margin and quality in the same paragraph.* That is the FDE / Applied AI Engineer interview in a repo.

→ Cross-link: [`04` §1 the eval bar you're clearing — LHTB](./04-research-progress.md#1-lhtb) · [`05` §2 FDE market that hires on exactly this](./05-career-and-startup.md#2-fde-market) · [`ACTIONS.md`](../ACTIONS.md) · [`ME.md`](../ME.md).
