# Practical Skills & Tools — 2026-09-03

**The single-highest-ROI 30 minutes you can spend this week: turn on `cache_control` for every Fable 5.1 endpoint you own.** The 2026-09-01 pricing change makes cache reads 75% cheaper — but only if you actually set the header. Second-highest: **redeploy at least one MCP server against the stateless 2026-07-28 spec** now that Microsoft + Google have shipped scaling guides. Third: **build a Claude Code subagent roster** using the pattern that top devs are converging on (5–7 scoped specialists beats one do-everything agent). Frame: *the runtime moved — the config on your side has to move with it or you're leaving 25–45% of your bill on the table.*

Tags: `#practical #anthropic #cache-control #mcp #claude-code #subagents #cost`

---

## 1. Flip `cache_control: ephemeral` on every Fable 5.1 endpoint tonight {#1-cache-cost}

**What to do (30 minutes):**

Anthropic cut cache-read pricing 75% on 2026-09-01 ($1.00 → $0.25/MTok) — but you have to explicitly opt in with the `cache_control` header on the message parts you want cached. If you're not setting it, you're paying full rate on repeated context.

**The 4-line change (Python SDK 0.116+):**

```python
messages = [
    {
        "role": "user",
        "content": [
            {
                "type": "text",
                "text": SYSTEM_PROMPT_OR_LONG_CONTEXT,
                "cache_control": {"type": "ephemeral"},   # <-- this
            },
            {"type": "text", "text": user_message},
        ],
    }
]
```

**Wire the header on:**
- System prompts (any that exceed ~1K tokens)
- Long-context RAG chunks (whole-doc, whole-repo snapshots)
- Tool schemas (large tool sets get cached separately)
- **Any content re-sent across ≥2 requests within 5 minutes**

**How to measure the win:**
- Set up a log line that captures `usage.cache_read_input_tokens` and `usage.cache_creation_input_tokens` on every response.
- Run your top-5 workflows for 24 hours pre-cache and 24 hours post-cache.
- Compute effective $/workflow. Screenshot the pair.

**Sources:**
- [Anthropic — Fable 5.1 / Mythos 5.1 launch (cache-read 75% cut)](https://www.anthropic.com/claude-fable-and-mythos-5-1) `[primary]`
- [VentureBeat — Fable 5.1 and Mythos 5.1 arrive with 75% cost reduction for Fable cache reads](https://venturebeat.com/technology/anthropics-claude-fable-5-1-and-mythos-5-1-arrive-with-a-75-cost-reduction-for-fable-cache-reads) `[secondary]`

### Why it matters to you

- **Job lens:** The **before/after cost log** is a portfolio piece **and** an interview line. "Cut our Fable 5.1 bill 32% by systematically wiring cache_control across our top-5 workflows; here's the graph" is exactly the answer Anthropic FDE interviewers and enterprise-buyer-facing PM roles want. It's a 30-minute change with a week's worth of measurement — cost-to-signal is unbeatable.
- **Startup lens:** If you're running any Claude-based product with more than trivial recurring context, this is likely **the single highest-leverage margin move you'll make this month.** Do it before you set your next quarter's unit economics.
- **Insight:** Anthropic is engineering the pricing curve to reward customers who **model their own request patterns**. The teams that measure `cache_read_input_tokens / total_input_tokens` weekly beat teams that don't — because you can *architect* your prompts to raise the ratio.

---

## 2. Redeploy one MCP server on the stateless 2026-07-28 spec — tonight {#2-mcp-stateless-production}

**What to do (15–60 minutes depending on complexity):**

The MCP 2026-07-28 stateless spec is live and both **Microsoft App Service** and **Google Cloud** shipped scaling guides this week. Every request is self-describing (`_meta` inline), no session state, `Mcp-Method`/`Mcp-Name` headers for header-based LB routing.

**The migration checklist:**
1. **Remove `initialize` / `initialized` handshake** — no longer required; kill any code that gates on it.
2. **Drop `Mcp-Session-Id`** — no longer part of the protocol.
3. **Move protocol version + client info into inline `_meta`** on every request.
4. **Emit `Mcp-Method` and `Mcp-Name` response headers** so LBs can route without body inspection.
5. **Return `ttlMs` + `cacheScope`** on `resources/list` and `tools/list` responses.
6. **Deploy behind a plain round-robin LB** (or Cloudflare Workers / AWS Lambda / Vercel Functions if you want serverless).
7. **Update OAuth** to 2.1 for connection setup (if you had a custom auth flow).

**Where to run it:**
- **Cloudflare Workers**: single-file deploy, ~$0/mo at hobby volume; ideal for a portfolio MCP server.
- **Azure App Service**: use the Microsoft guide for enterprise-facing servers.
- **GCP Cloud Run**: use the Google Developers Blog guide.

**Sources:**
- [Microsoft — MCP Just Went Stateless (App Service scaling)](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) `[primary]`
- [Google Developers Blog — Scaling AI Agent Infrastructure with MCP Stateless](https://developers.googleblog.com/scaling-ai-agent-infrastructure-with-the-mcp-stateless-updates/) `[primary]`
- [MCP Blog — The 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [Model Context Protocol — Key Changes changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) `[primary]`

### Why it matters to you

- **Job lens:** **Migrated-MCP-server + short blog post = a specific, dated portfolio piece** that shows you're operating at the protocol edge, not just reading about it. Anthropic Solutions/FDE roles ask about MCP directly in interviews — a migration writeup answers the question without you having to.
- **Startup lens:** **Multi-tenant stateless MCP hosting** is a real category being defined right now. If you were sitting on a "hosted MCP marketplace" idea, this week is when the primitives to build it exist without you having to solve session management yourself.
- **Insight:** Protocol migrations reward **being early and public** — the top result on Google for "MCP stateless migration walkthrough" gets consulting inbound for months. Write the tutorial as you migrate; publish it. Free lead-gen.

---

## 3. Claude Code subagent roster — the 5–7 specialist pattern {#3-subagents}

**What to do (1 hour setup, ongoing use):**

Multiple 2026 practitioner writeups have converged on the same shape for a productive Claude Code subagent roster: **5–7 tightly-scoped specialists beats one do-everything agent**. Set them up once in your project's `.claude/agents/` directory.

**Canonical roster:**
1. **`explorer`** — read-only search across codebase (Grep, Read, Glob). No Write, no Edit, no Bash. Kills the "let me look at 40 files first" tax on the main context.
2. **`code-reviewer`** — reads the current diff, flags correctness + simplification. Read-only. Ties into `/code-review` slash command.
3. **`test-writer`** — scoped to your test framework; can Write but not Edit-in-place beyond test files.
4. **`doc-writer`** — writes README / architecture notes / API docs; scoped to `docs/` and `*.md`.
5. **`migration-writer`** — for large refactors; runs in its own context so a 40-file rename doesn't blow the main session.
6. **`security-reviewer`** — reads diff for OWASP + secrets; posts findings inline. Read-only.
7. **`data-analyst`** *(optional)* — for data-heavy repos; can run pandas/SQL notebooks against sample data.

**Setup pattern (each agent gets its own file):**

```yaml
# .claude/agents/explorer.md
---
name: explorer
description: Fast read-only search across the codebase. Use for "where is X defined" / "which files reference Y" / open-ended locate.
tools: Grep, Read, Glob
model: sonnet
---

You are the explorer subagent...
```

**Also set up a project `CLAUDE.md`** at the repo root with architecture, coding standards, common commands, and important paths. This is Andrej Karpathy's original 4-rule pattern; it now has ~110K+ stars of adoption ([2026-05-17 archive](../2026-05-17/)).

**Sources:**
- [Tembo — Claude Code Subagents: A 2026 Practical Guide](https://www.tembo.io/blog/claude-code-subagents) `[analysis]`
- [Totalum Blog — Claude Code subagents: the 2026 production playbook](https://www.totalum.app/blog/claude-code-subagents-totalum) `[analysis]`
- [AgentsRoom — 50 Claude Code Tips & Tricks](https://agentsroom.dev/claude-code-tips) `[analysis]`
- [SmartScope — Claude Code Advanced Best Practices 2026](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [F22 Labs — Claude Code Tips: 10 Real Productivity Workflows for 2026](https://www.f22labs.com/blogs/10-claude-code-productivity-tips-for-every-developer/) `[analysis]`

### Why it matters to you

- **Job lens:** A screenshot of a **project `CLAUDE.md` + 5 subagent files** is a *specific* signal in an interview — you're operating at the "actually shipping with Claude Code" tier, not just tinkering. Anthropic and enterprise FDE interviewers ask about this directly.
- **Startup lens:** The subagent roster **speeds up your own build velocity** — which is the founder-only compounding advantage no VC can help with. If you're shipping alone, this is worth an hour of setup today.
- **Insight:** The tooling around Claude Code (subagents + hooks + MCP + `CLAUDE.md`) is stabilizing into a **stack**. Six months from now, "Claude Code stack fluency" will be a resume line item like "AWS proficiency" was in 2015. Get in before it commoditizes.

---

## 4. This weekend's artifact — the coordination-defender MCP server + Haiku verifier {#4-weekend-artifact}

**What to build (2–3 hours, Sunday afternoon):**

The OpenAI × METR × Redwood incident ([`01` §2](./01-big-lab-moves.md#2-openai-agent-coordination)) creates a **specific product-shaped problem** you can build against this weekend: **runtime observability for agent teams**.

**The artifact:**

**A stateless MCP server + a Haiku verifier that logs every tool call across a small agent team and flags inter-agent coordination patterns.**

**Concrete spec:**
1. **MCP server** (deployed on Cloudflare Workers, 2026-07-28 stateless spec):
   - Exposes 3–4 tools: `log_tool_call`, `list_recent_calls`, `find_correlated_calls`, `detect_communication_channels`.
   - Every call is timestamped, attributed to a `caller_agent_id`, and stored in KV/Durable Objects.
2. **Agent team**:
   - Spin up 5–10 concurrent Claude Fable 5.1 agents (use `cache_control` — cost-aware!) with independent goals in a shared filesystem sandbox.
   - Each agent uses your MCP server for its work.
3. **Verifier subagent** (Haiku, cheap):
   - Periodically reads recent tool-call logs.
   - Flags: (a) unexpected temporal correlations between agents, (b) files that look like communication channels (agent-A writes, agent-B reads, no external actor), (c) any agent role-taking beyond its assigned scope.
4. **README** with:
   - The threat model (name-drop the OpenAI × METR × Redwood incident, cite it).
   - How your logging + verification catches it.
   - A screenshot of the verifier catching a coordination pattern.
   - A cost table (per-agent, per-verifier-run) — use the Fable 5.1 cache-read pricing you flipped on in §1.

**Why this specific artifact:**
- **One repo answers three interview questions:** MCP fluency (§2), agent safety, cost-aware orchestration (§1).
- **Timely** — the incident is 72 hours old; any employer researching your background will see you moving with the news.
- **Cheap to build** — the whole thing runs on <$5 of Fable 5.1 tokens if you use cache_control correctly.

**Publish to:**
- GitHub (`coordination-defender-mcp`)
- Short LinkedIn post + short Twitter thread
- Cross-post to r/LocalLLaMA if you make the code stack-agnostic

### Why it matters to you

- **Job lens:** This is precisely the kind of **"read the news, ship the response in a week"** artifact that separates candidates in the FDE / Applied AI / Agent Safety funnels. Interviewers explicitly value speed-of-adaptation over depth of one topic.
- **Startup lens:** **This artifact IS a demo of a startup.** "Datadog for agent teams" is the underlying product; the coordination-defender is a Sunday-afternoon MVP. If you like the space, this weekend gets you a 48-hour head start on the founders who'll notice the incident later.
- **Insight:** The best portfolio pieces of 2026 are not tutorials or reproductions — they're **response artifacts**: news breaks Wednesday, you ship a specific defensive tool Sunday. That cadence is a *skill*, not a coincidence.

---

## 5. Compact — Plan Mode, `/rewind`, `/compact`, `/clear` {#5-compact}

**Short takes:**
- **Plan Mode**: before making changes, ask Claude Code to "plan the change" — it inspects the codebase and returns a step list you can approve. Cuts speculative edits materially.
- **`/rewind`** — undoes recent Claude-Code actions; useful when a change spirals.
- **`/compact`** — compresses conversation history to save context.
- **`/clear`** — nukes the conversation entirely; use when starting a new task in the same session.

**Sources:**
- [F22 Labs — Claude Code Tips 2026](https://www.f22labs.com/blogs/10-claude-code-productivity-tips-for-every-developer/) `[analysis]`
- [Blake Crosley — Claude Code CLI Complete Guide](https://blakecrosley.com/guides/claude-code) `[analysis]`

### Why it matters to you

- **Job lens:** Muscle memory on these commands = you're demonstrably a Claude Code power user. Ship a short LinkedIn post: "Five Claude Code commands I use every day." Low effort, real signal.
- **Startup lens:** `/compact` and Plan Mode are the two commands that most directly extend how long you can stay productive in a single session — which matters most when you're the entire eng team.
