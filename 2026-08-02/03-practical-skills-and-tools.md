# Practical Skills & Tools — 2026-08-02

Hands-on workflows, tools, prompting, productivity. Act on this today or this weekend.

---

## 1. Migrate one MCP server to the 2026-07-28 stateless spec this weekend {#1-mcp-stateless-migration}

**Why this is the highest-leverage 2-day investment of the summer.** The **2026-07-28 spec shipped Monday** with all four Tier-1 SDKs supporting it same-day ([`02` §3](./02-new-emerging.md#3-mcp-stateless-shipped)). Anyone with a **public before-and-after migration commit history** on a real MCP server has a top-of-search-results portfolio artifact for **at least 90 days**. That is not an exaggeration; the market is small enough right now that you can be findable.

**Migration checklist.** Do these in order — each step is independently ship-able.

1. **Pick a small existing server**, ideally 3–8 tools. If you don't have one, use the [MCP TypeScript SDK server template](https://github.com/modelcontextprotocol/typescript-sdk); a filesystem or GitHub-search server works fine.
2. **Delete the initialize handshake** — no more `initialize` / `notifications/initialized`. Move `protocolVersion` + client capabilities into `_meta` on every request.
3. **Remove the session header.** No `Mcp-Session-Id`; no server-side session store. If your server had any session-scoped state, refactor it into per-request context (or lift it into your database, keyed on user/tenant).
4. **Add `Mcp-Method` + `Mcp-Name` headers on every request** and, on the server side, make sure they match the request body's method/name (helpful invariant to log during migration).
5. **Add `ttlMs` + `cacheScope` to your list and resource results.** Even conservative TTLs (30s) let clients dedupe redundant reads.
6. **Verify with a plain L7 load balancer.** Round-robin between 2 stateless server instances behind Nginx or Cloudflare; this is the whole point of the migration.
7. **Wire OAuth 2.1** at connection time (or, if you're behind a proxy, at the proxy). Do NOT skip this — most enterprise adoption starts here.
8. **Publish a `MIGRATION.md`** in your repo. Before/after topology diagram, cold-start latency numbers, load-balancer config, and — if you can measure it — cost delta per 1K requests.

**Expected time**: 4–6 hours if you know the codebase, 8–10 if you're picking up a new SDK. Do it Saturday afternoon; publish Sunday evening.

**Sources.**
- [The 2026-07-28 Specification — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/) [primary]
- [Key Changes — MCP Changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) [primary]
- [MCP Just Went Stateless — Microsoft Community Hub](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) [secondary]
- [MCP 2026-07-28 migration guide — Agentic AI Foundation](https://aaif.io/blog/mcp-2026-07-28-whats-changing-and-how-to-migrate) [analysis]

**Why it matters to you.**

- **Job.** This artifact answers three interview questions at once — **protocol currency** (shipped-spec migration within a week of release), **cost/scaling awareness** (LB topology, TTL choices, cold-start numbers), and **agent-integration depth**. In the FDE / Applied-AI loop specifically, "walk me through the last thing you shipped" gets a substantially better answer this Monday than last Monday.
- **Startup.** If you're pre-forming, **the compatibility-shim + migration-consulting wedge is 2–4 weeks wide**. Enterprise customers with pinned older SDK versions will pay for a service that speaks both dialects during their transition. This is a real, small, and finite market.
- **Insight.** MCP has now had **its first "grew up" release** — a protocol that started as an Anthropic side project last year has become the shared substrate for at least Anthropic, Google (WebMCP), Microsoft (Azure App Service tooling), and OpenAI. Watch the **Server Cards** and **MCP Apps** primitives; a marketplace dynamic emerging around those is the next enterprise-value inflection.

`#mcp #stateless #migration #protocol #portfolio`

---

## 2. Claude Code power-user muscle memory: what actually earns its keep in 2026 {#2-claude-code-power-user}

**The consolidation.** After ~6 months of Claude Code / Codex / Cursor / Aider all iterating rapidly, a small stable set of practices earn their keep across all of them. This section is deliberately short; **the value is in doing these, not in reading them.**

1. **Slash `/clear` between unrelated tasks.** A fresh session with a sharper prompt beats a long session full of failed attempts. If the agent has gone down the wrong path twice, `/clear` and restart with a better spec.
2. **Plan mode first, edit mode second.** The Anthropic team explicitly recommends this. Ask for a plan; read the plan; *then* say "address all notes and implement." Skipping plan mode is the #1 reversible reason your changes look plausible but don't work.
3. **`/simplify` after any batch of changes** — runs parallel agents that review for reuse, quality, efficiency, and CLAUDE.md compliance. Cheap, catches real issues, no downside.
4. **Right tool for the layer:**
   - **Hooks** → enforce **rules** (never commit without tests passing, always run `terraform plan` before `apply`, etc.).
   - **Skills** → contextual **knowledge** the agent needs on demand (deploy runbook, API-spec walkthrough).
   - **Subagents** → **delegation boundaries** (do this in a fresh window, don't burn the parent context).
   - **CLAUDE.md** → **always-on** project guidance; keep it short.
5. **Scope prompts tight.** Name the file, name the scenario, name the check that proves the task is done. "Add error handling" is a bad prompt. "In `auth/session.py`, when `refresh_token()` returns 401, log at `ERROR`, clear the cached session, and return `AuthExpired` — write a pytest that exercises the 401 path" is a good prompt.
6. **`terminals-first` mental model.** With agents doing the typing, your leverage is on **specifying outcomes, constraints, and verification** — not on typing speed.
7. **Turn a repeated task into a skill.** If you do something more than once a day, check it into `.claude/skills/<name>/SKILL.md`; the payoff shows up inside a week.

**Sources.**
- [Claude Code power user tips — Claude Help Center](https://support.claude.com/en/articles/14554000-claude-code-power-user-tips) [primary]
- [10 Claude Code Best Practices for Agentic Coding: A 2026 Guide — OpenHands](https://www.openhands.dev/blog/claude-code-best-practices-agentic-coding) [analysis]
- [Claude Code Advanced Best Practices: 11 Practical Techniques for Hooks, Subagents & Context Management — SmartScope](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) [analysis]
- [Prompt engineering best practices for 2026 — Anthropic Claude Blog](https://claude.com/blog/best-practices-for-prompt-engineering) [primary]
- [A Guide to Claude Code 2.0 and getting better at using coding agents — sankalp's blog](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) [analysis]

**Why it matters to you.**

- **Job.** In any Applied-AI / FDE loop, **"how do you use Claude Code" is now a real, unfaked interview question** — an interviewer can tell the difference between someone who /clears habitually and someone who doesn't. The good-answer template: **name the tool layer, name the trigger, name the outcome** ("I use hooks for the CI-must-be-green rule because I want the guardrail to be at repo scope; I use CLAUDE.md for the deploy checklist because that's per-project").
- **Startup.** **Team-level productivity hinges more on tool discipline than on model choice** at this point. If you're evaluating a co-founder or an early hire, watch how they use Claude Code for 15 minutes. That signal is stronger than most technical interviews.
- **Insight.** **The 2026 "practice > tool" pattern is generalizing.** The delta between mediocre and excellent Claude Code use is much larger than the delta between Claude Code and its closest competitors. Invest accordingly.

`#claude-code #productivity #tools #hooks #skills #subagents`

---

## 3. Take advantage of Sonnet 5 launch pricing before it reverts (Aug 31) {#3-sonnet-5-launch-pricing}

**What.** Sonnet 5 launched **2026-06-30** at **$2 / $10 per MTok (input / output)** as launch pricing **through August 31, 2026**. After that, standard pricing reverts to **$3 / $15 per MTok**. That's a 33% / 33% raise coming, on a model that's already the default for Free + Pro plans and is available to Max/Team/Enterprise.

**Benchmarks worth citing.** SWE-bench Verified **72.7%** (vs. Opus 4.8 **79.4%** and Sonnet 4.6 **62.3%**), Terminal-bench **76.1%**, and one knowledge-work benchmark where it edges past Opus 4.8. Positioned as "the most agentic Sonnet" with browser + terminal tool use and multi-step planning that used to require Opus.

**Concrete actions this week (do them, don't just read them):**

1. **Audit your own bill.** Log into the Claude Platform dashboard; check the last 30 days of Sonnet-tier calls. If you have any repeatable batch job on Sonnet, **run it once this weekend** while the input cost is $2/MTok instead of $3.
2. **Re-evaluate any Opus-only workload** — Sonnet 5's Terminal-bench 76.1% + SWE-bench 72.7% means many workloads that were on Opus 4.8 "for reliability" can move to Sonnet 5 for **half the cost**. Set an eval this week (100 real examples of the workload); if Sonnet 5 hits 90%+ of Opus 5's quality on your benchmark, switch.
3. **Set a calendar reminder for Aug 30** to re-audit before the price change lands.
4. **Update your CLAUDE.md model-selection rule** to explicitly encode "Sonnet 5 unless benchmark shows otherwise."

**Sources.**
- [Introducing Claude Sonnet 5 — Anthropic](https://www.anthropic.com/news/claude-sonnet-5) [primary]
- [Claude Sonnet 5: Release Date, Pricing, API & Benchmarks — Coursiv](https://coursiv.io/blog/claude-sonnet-5) [analysis]
- [What's new in Claude Sonnet 5 — Claude Platform Docs](https://platform.claude.com/docs/en/about-claude/models/whats-new-sonnet-5) [primary]
- [Claude Sonnet 5 Benchmarks Explained — Vellum](https://www.vellum.ai/blog/claude-sonnet-5-benchmarks-explained) [analysis]
- [Claude Opus 5 vs Sonnet 5: Benchmarks, Pricing & Which to Use (July 2026) — Coursiv](https://coursiv.io/blog/claude-opus-5-vs-sonnet-5) [analysis]

**Why it matters to you.**

- **Job.** **Cost-aware model selection is a skill that shows up in interviews now.** If you can walk into an interview and say "I evaluated Sonnet 5 vs. Opus 5 on my own workload, kept the planner on Opus 5 at `effort=high`, moved the worker to Sonnet 5, ran a Haiku verifier, and saved 45%," you are answering three interview questions in one story: architecture, evaluation, and cost.
- **Startup.** **The workhorse tier repriced *again*** — Sonnet 5 launch pricing is 33% below the incoming standard, and Gemini 3.6 Flash claims 17% token reduction on top of its own price. Your product's unit economics that were computed against Sonnet 4.6 or Opus 4.8 are stale; **redo them this month before you talk to any investor**.
- **Insight.** **Every 6–10 weeks in 2026 has produced a workhorse-tier reprice.** The rational response is to **assume this cadence continues for at least Q3–Q4 2026** and design your architecture around routing (not around a single-model dependency).

`#anthropic #sonnet-5 #pricing #cost-aware #routing`

---

## 4. This weekend's artifact (recommended) {#4-weekend-artifact}

Ship **one** repo that answers three interview questions at once. All of the pieces already exist in your archive; this weekend assembles them.

**The build.**

- **Fresh MCP server on the 2026-07-28 stateless spec** ([§1](#1-mcp-stateless-migration)) — 3–5 real tools; deploy behind Nginx round-robin; publish a `MIGRATION.md` if you migrated an existing server, or `DESIGN.md` if it's greenfield.
- **Orchestration**: **Opus 5 planner (`effort=high`) → Sonnet 5 worker (`effort=medium`) → Haiku verifier**, running against the fresh MCP server. Two-pass: (1) planner emits a plan against the tool catalog; (2) worker executes; (3) verifier grades each step and rolls back on failure. This is the [TrajAD pattern](../2026-05-19/04-research-progress.md) applied to the current model lineup.
- **Cost log**: per-step token count, per-step model, per-step wall time. Aggregate to per-task cost. Log to a JSONL so a screenshot fits in a PR body.
- **README**: one paragraph on why you built it, one on how to run it, one paragraph tying it to the **2026-07-28 spec + Sonnet 5 launch pricing** so the timeliness is legible.

**Time budget.** Saturday afternoon: MCP migration + verifier scaffolding. Saturday evening: orchestration wiring. Sunday morning: eval + cost log. Sunday afternoon: README + publish.

**Distribution.** Post the repo Sunday evening. Include the cost-log screenshot in the tweet/LinkedIn post. Tag `#MCP` `#ClaudeCode`. Send the link cold to **2 Anthropic Applied-AI / FDE recruiters Monday morning** (see [`05` §2](./05-career-and-startup.md#2-fde-and-meta-cohort) for the shortlist).

**Why it matters to you.**

- **Job.** Three interview questions answered by one artifact: orchestration (Opus/Sonnet/Haiku), real-tool verification (MCP-Atlas / Toolathlon adjacent, per [2026-05-22 04](../2026-05-22/04-research-progress.md)), and cost predictability (per-step log). That's the exact triangle Applied-AI hiring managers say they wish candidates showed.
- **Startup.** The **verifier pattern is the demo you show a founder-brand agent-startup** — it's a small piece of the real product, and it's the piece founders keep telling their team to build "someday."
- **Insight.** **Timeliness is signal.** Any artifact using the shipped spec inside 10 days is a signal on its own — recruiters and founders are pattern-matching on "who is *reading* the release blog vs. who is *building* against it."

`#weekend-artifact #mcp #orchestration #verifier #cost`

---

## 5. Small workflow tip: audit your Claude spend on the 4th of every month {#5-monthly-audit}

Personal rule from `ME.md`: **audit AI spend on the 4th of the month**. Applies here because:

- **Sonnet 5 launch pricing expires August 31.** Your August-4 audit is a normal check; your **September-4 audit will be a genuine before/after comparison** if you've routed any Opus-4.8 workloads to Sonnet 5 launch pricing.
- **MCP migration** ([§1](#1-mcp-stateless-migration)) shifts your deploy cost profile — LB + stateless workers vs. sticky-session. Capture the September delta.
- **The Agent SDK metering change** (from [2026-05-16](../2026-05-16/00-tldr.md)) is now old news but the **routine is still worth keeping** — treat any month you skip the audit as a month you lost money.

Set the audit as a recurring calendar event today. 15 minutes.

`#personal-rule #audit #cost`

---

## Cross-cutting: the practical shape of the summer

- **The workhorse tier is where the game is.** Sonnet 5 + Gemini 3.6 Flash + GPT-5.6 all repriced or improved in July. Cost-aware routing is the highest-ROI skill this quarter.
- **MCP is the protocol layer.** The 07-28 spec is not "one more incremental release" — it's the "grew up" moment. Everything downstream (marketplace, enterprise adoption, ecosystem tooling) hinges on it.
- **Practice > tool.** The delta between mediocre and excellent Claude Code use is bigger than the delta between Claude Code and its competitors. Invest in the *practice*, not the tool selection.
