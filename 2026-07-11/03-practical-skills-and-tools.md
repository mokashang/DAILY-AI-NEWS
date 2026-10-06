# Practical Skills & Tools — 2026-07-11

Act-on-it-this-weekend. The May-22 orchestration playbook (Opus-planner + Sonnet-workers + Haiku-verifier) is still your baseline, but two upgrades landed inside the last month that materially change your cost + reliability curve: **code-execution-with-MCP** (tools presented as code on a filesystem, loaded on demand) and the **federated-orchestrator** topology (kills the "god orchestrator" anti-pattern). Both slot cleanly into the artifact you already have queued. And the **Claude Cowork mobile + Routines** wave from [`01` §2](./01-big-lab-moves.md#2-cowork) means the artifact now ships with **a phone-native, schedule-fired demo mode** — which is exactly the shape recruiters remember.

Tags: `#playbook #claude-code #mcp #agents #orchestration #cost #routines #mobile`

---

## 1. Code-execution-with-MCP + federated orchestration — the July upgrade to the May-22 playbook {#1-code-exec-mcp}

**The problem the May-22 playbook still has:** an Opus orchestrator that loads *every* MCP tool definition into context every turn — cheap on tokens the first turn, quadratically expensive on long agent runs (each tool schema is re-attended every round, and you can't easily filter the return values before they hit the model). The June-15 metering makes that visible on your bill.

**The July fix — code-execution-with-MCP:** present MCP tools as **code on a filesystem** that the model reads on demand, rather than a preloaded manifest.

- **Load tools on demand** — the orchestrator reads the tool definition *when it decides to call it*, not before.
- **Filter data before it reaches the model** — you can wrap the tool call in a small transform (deduplicate, project columns, summarize) inside the code-execution step, so the model only sees the useful shape.
- **Execute complex logic in a single step** — instead of "call tool → observe → call another tool → observe → …" (which multiplies per-turn context cost), a code-execution block can chain calls locally and return one aggregated result.
- **Net effect:** at the *tool-heavy* end of a run (MCP-Atlas / Toolathlon shapes — see [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)), typical token savings look like **~30–60%** with equal or better task success.

**The topology upgrade — federated orchestration:** the May-22 diagram had one orchestrator agent owning plan + integration + delegation. That works up to ~5 workers; it falls apart when you scale because the orchestrator becomes (i) a throughput limiter and (ii) a single failure domain (schema drift in one worker's return values pollutes the orchestrator's context, and every downstream worker inherits the pollution).

The **federated topology** replaces it with:
- A **thin ingress layer** — user-facing, holds approval checkpoints, no domain state.
- **Per-domain sub-orchestrators** — each owns one subgraph of the work (e.g., "the retrieval subgraph," "the codegen subgraph," "the verification subgraph"), each with its own bounded worker pool.
- **Explicit A2A (agent-to-agent) hand-offs** — Google's A2A protocol pairs with MCP: **MCP governs how agents connect to tools; A2A governs how agents connect to each other.** Use both.
- **Schema-versioned tool contracts** — every MCP tool exposes an explicit schema version; the orchestrator refuses to route a call to a worker whose version doesn't match. Kills the schema-drift pollution.

**Sanity settings still apply from the field-tested list:**
- `temperature=0.1` for tool-calling to keep dispatch deterministic.
- `max_loops = 2–3` per agent for most tasks. If a subagent needs more, that's the signal you should split it, not raise the ceiling.

| Update the May-22 team like this | Model | Role |
|---|---|---|
| **Ingress / user surface** | Sonnet 5 (or Opus 4.7 on hard days) | Approval checkpoints, no state |
| **Domain sub-orchestrator (planner)** | Opus 4.7 | One per domain (retrieval / codegen / verify) |
| **Workers** | Sonnet 5 (introductory $2/$10 through Aug 31) | Bounded, single-purpose |
| **Verifier / guard** | Haiku 4.5 | Always-on; runs the TrajAD-style rollback loop |

**Sources:**
- [Anthropic Engineering — Code execution with MCP: building more efficient AI agents](https://www.anthropic.com/engineering/code-execution-with-mcp) `[primary]`
- [GetKnit — MCP agent orchestration: chaining, handoffs, and multi-agent patterns explained](https://www.getknit.dev/blog/advanced-mcp-agent-orchestration-chaining-and-handoffs) `[analysis]`
- [Deepak Gupta — Top 10 MCP servers & agent frameworks for enterprise 2026 (includes federated pattern)](https://guptadeepak.com/tools/top-10-mcp-frameworks-2026/) `[analysis]`
- [Neel Shah / Medium — Top 10 MCP servers for AI agent orchestration in 2026](https://medium.com/devops-ai-decoded/top-10-mcp-servers-for-ai-agent-orchestration-in-2026-78cdb38e9fba) `[analysis]`
- [Elegant Software Solutions — MCP 2026 agent-to-agent communication guide (A2A + MCP pairing)](https://www.elegantsoftwaresolutions.com/blog/mcp-2026-agent-to-agent-communication-guide) `[analysis]`
- [Skywork — Prefect MCP server: the AI engineer's guide to orchestration-aware agents](https://skywork.ai/skypage/en/prefect-mcp-server-ai-engineers-guide/1980825004055269376) `[analysis]`

### Why it matters to you

- **Job lens:** *"I upgraded the agent team from a single orchestrator to a federated topology + MCP-code-execution and cut token cost ~40% while adding schema-versioned tool contracts"* is a **staff-engineer-level artifact story.** It answers three interview questions in one — cost, reliability, and API contract design. Put a one-page architecture diagram in your GitHub with `before/` and `after/` folders. Screenshots of the token graph pre- and post-refactor are the closer.
- **Startup lens:** Federated + versioned schemas *is* the durable-vendor-lock-in: once a customer's Claude Sonnet workers are running against your MCP contracts, swapping to GPT-5.6 Sol or Grok 4.5 becomes a config change, not a rebuild. **You are selling the topology, not the model.** That's the highest-margin thing you can sell into a shop that has one AI budget line and multiple vendors to keep honest.
- **Insight:** Every generation of infra reprices *which layer is scarce*. In 2024 it was context. In 2025 it was tools. In **mid-2026 it is *the observability + versioning + routing layer between agents.*** Skill-invest there — schema versioning, per-step cost tracing, A2A handshakes — and you are one layer above the thing everyone else is competing on.

→ Cross-link: [2026-05-22/03 §1 the Opus/Sonnet/Haiku baseline this upgrades](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-22/04 §1 real-tool benchmarks (validate against MCP-Atlas)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).

---

## 2. Weekend artifact: ship a Cowork-fired mobile Routine with an MCP tool + a public README {#2-artifact}

You've had the **dual-model sanitiser** artifact queued since [2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project); [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) added real-tool verification + cost. **This weekend, add mobile-first operation** — the surface that just went live on both sides of the frontier. One artifact now answers **four** interview questions: orchestration, verification-against-real-tools, cost, *and* production operation.

**60-min plan (Saturday afternoon):**

1. **Install Claude Cowork on your phone** (iOS or Android). Sign in with your existing Anthropic account. Confirm push notifications on. → 5 min
2. **Pick one real Routine** you'd actually use every week. My default pick for a CS grad: **weekly arXiv scanner for your subfield** — the Routine polls `arxiv.org` for new papers matching 3–5 tag queries + your own bookmarked authors, drops a summary into a Markdown file in your GitHub repo, and pings you when done. Alternatives: PR-babysitter for a repo you care about; a Monday-morning inbox triage; a competitive-lab weekly digest. → 5 min
3. **Wire it as a Routine on Claude Code on the web** with a schedule trigger (Fri 6 PM or Mon 6 AM). Add one **MCP tool** (an arXiv fetcher; there is at least one public one, or write a 40-line wrapper). Add a **schema version tag** to the tool ([§1 discipline](#1-code-exec-mcp)). → 20 min
4. **Log token usage per step**: `/usage` gives you the breakdown post-run. Screenshot the run trace. → 5 min
5. **Screenshot the phone push notification** landing after the schedule fires. → 5 min
6. **README section (20 min):** *"How I'd wire this for a client: pick a repeat task, fire it on a schedule, route by model tier, log per-step cost, deliver output through the surface the user actually watches (their phone)."* Include: architecture diagram (mermaid), the tool schema with version, the routing table, the cost log, the push-notification screenshot.

**Interview-ready one-line summary:** *"I built and operate an autonomous mobile-first knowledge agent — Opus-4.7 planner + Sonnet-5 workers + Haiku-4.5 verifier, MCP-code-execution over one real tool, fired by schedule, monitored via mobile push — and I can show you the token-cost trace."*

That sentence maps 1:1 to the **Anthropic Solutions / OpenAI FDE / any-frontier-lab Integration Engineer** job description this quarter.

**Sources:**
- [Anthropic — Claude Code Routines on the web (in Week 28 changelog)](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Totalum — Claude Agent SDK in 2026 (routines-shaped patterns)](https://www.totalum.app/blog/claude-agent-sdk-totalum-2026) `[analysis]`
- [Emerging AI — Claude changed: the July 2026 way to use it](https://emergingai.substack.com/p/claude-changed-the-july-2026-way) `[analysis]`
- [Gradually — Claude Code changelog (July 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`

### Why it matters to you

- **Job lens:** This is the single highest-leverage artifact you can produce this weekend. It slots into every interview loop currently on your call sheet. Ship it before you touch resume edits or LeetCode this week — the marginal return dominates.
- **Startup lens:** The Routine pattern *is* the founder MVP for "a Claude-for-X service." Ship one Routine for one profession + one MCP tool that reads their systems + one screenshot of the mobile output. You are 90% of the way to a paying customer conversation.
- **Insight:** The recruiter-scan reality — *"engage 80% more with GitHub projects featuring runnable code or live demos"* — matters more this cycle than any past cycle, because they're comparing your work to a rising tide of GPT-generated projects that look plausible but don't run. **A runnable, scheduled, observable demo is now the credential.**

→ Cross-link: [`05` §3 weekend action](./05-career-and-startup.md#3-weekend) · [2026-05-22/05 §3 the Meta reply thread you continue this week](../2026-05-22/05-career-and-startup.md#3-meta-followup).

---

## 3. Micro-tips landing this week (each one is a 10-min setup) {#3-microtips}

- **Turn on `xhigh` effort in Claude Code for hard debugging sessions.** New effort level in Week 28. Use `/effort` mid-session to dial up/down; keep default at `high`, escalate to `xhigh` only when a session stalls. Cost jumps noticeably — audit with `/usage` after.
- **Move any personal CLI use to the native Claude Code binary.** Dropping the Node runtime dependency + auto-update on lower memory = faster cold start, cleaner CI use. First-run migration is one command.
- **Set API-key expirations (never `Never`).** New console feature. 90-day rolling keys with an email reminder are the right default — cuts the tail risk of a leaked key surviving a repo history rewrite.
- **`temperature=0.1` for every MCP tool call.** Deterministic dispatch. Only raise it if you want *generative* output at the tool step (rare).
- **Cap `max_loops = 3` per agent by default.** If a subagent hits it, split the subagent, don't raise the ceiling.
- **Use A2A + MCP together, not one or the other.** MCP = tools. A2A = other agents. Sub-orchestrators should communicate via A2A; tools stay behind MCP.
- **Wrap every MCP tool in a `SCHEMA_VERSION`.** Refuse mismatched calls. Prevents schema-drift pollution ([§1](#1-code-exec-mcp)).
- **On desktop, use Claude Code's in-app browser** when you're doing anything web-based — it observes what the model sees, which makes debugging screen-driven agent tasks a lot cheaper.
- **Turn on the Anthropic reflection dashboard** for a week and audit which prompts you actually repeat — those are your first three Routine candidates.

**Sources:**
- [Claude Code — What's new (Week 28)](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Anthropic — Enabling Claude Code to work more autonomously](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously) `[primary]`
- [MindStudio — Code with Claude 2026: 5 new agent features Anthropic just shipped](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features) `[analysis]`

### Why it matters to you

Small things compound. Getting 8 of these right this weekend is worth more than reading two more blog posts about agents. **Do six.**

→ Cross-link: [`ACTIONS.md`](../ACTIONS.md) · [`WATCHLIST.md`](../WATCHLIST.md).
