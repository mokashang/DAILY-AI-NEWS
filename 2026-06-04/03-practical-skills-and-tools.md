# Practical Skills & Tools — 2026-06-04

Act-on-it-today. Two changes this week reshuffle the practical playbook: **Opus 4.8's dynamic workflows** (§1) and **the Agent SDK metering switchover on June 15 = T-11** (§2). Dynamic workflows give you a *much* bigger lever — *and* a much bigger bill if you turn them on without telemetry. The right move tonight is to **enable + bound** the workflow primitive on one real task, log per-step cost, and turn that into a portfolio artifact before metering flips.

Tags: `#playbook #claude-code #dynamic-workflows #ultracode #cost #orchestration #agents`

---

## 1. Dynamic workflows + the `ultracode` toggle — your tonight playbook {#1-dynamic-workflows}

The single biggest practical change of the last fortnight: **dynamic workflows in Claude Code** ([`01` §2](./01-big-lab-moves.md#2-opus-4-8)). What it actually does, and how to use it without burning your budget:

**What it is.** Claude can **plan a task → spawn tens-to-hundreds of parallel subagents in one session → independently verify each finding → report consolidated results.** This generalizes the [Opus-orchestrator / Sonnet-worker pattern from 2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) into a *built-in* primitive — you no longer hand-wire the team.

**How to enable.** In Claude Code, open the effort menu and set **`ultracode`** (or `/effort xhigh`). That tells Claude it's allowed to fan out subagents and run them in parallel within the session.

**The 45-min playbook for tonight:**

| Step | What to do | Why |
|---|---|---|
| 1 | Pick **one** public repo you know well (≤30K LOC) | Bounded enough to inspect each finding |
| 2 | `cd` into it; `/effort ultracode`; run **one** prompt: *"Audit this codebase for: (a) untested edge-cases, (b) likely-stale TODOs, (c) any silent error-swallowing. For each finding, independently verify and produce a short evidence block."* | Three different task-shapes in one run — exercises the fan-out + verify primitive |
| 3 | **Log per-step token use** with the Claude Code session export | Per-step cost is your portfolio-artifact deliverable |
| 4 | Save: (a) the full transcript, (b) the per-step cost table, (c) a **15-line README** framing this as *"how I'd run a safety-relevant audit at predictable cost"* | This is the artifact |
| 5 | Push to GitHub under a repo named e.g. `dynamic-workflow-audit-demo` | Public, link-able, screenshots in 10 sec |

**Why this is the right artifact this weekend:** it pulls in all four of this week's threads — **Opus 4.8** ([`01` §2](./01-big-lab-moves.md#2-opus-4-8)) as the engine, **MCP-AgentBench** ([`04` §1](./04-research-progress.md#1-mcp-benchmark-wave)) as the methodology, **OpenRouter's multi-model thesis** ([`02` §1](./02-new-emerging.md#1-openrouter)) as the framing, and **the Apple Extensions distribution surface** ([`01` §3](./01-big-lab-moves.md#3-wwdc)) as the future use case. One artifact, four interview answers.

**Other Opus 4.8 levers worth flipping:**

- **Effort controls** on claude.ai (effort = low / medium / high / xhigh / ultracode) — useful for routing tasks by *importance*, not just by *model*.
- **Fast mode = 3× cheaper** than Opus 4.7 fast — your cost floor for routine tasks dropped materially; revisit any "I only run that on Sonnet for cost" decisions.
- **The "~4× less silent-bug" alignment delta** — means you can lower (not eliminate) your downstream-review overhead on Opus-generated code; quantify it on your real workflow and *that's* the metric you cite.

**Sources:**
- [Claude blog — Introducing dynamic workflows in Claude Code](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) `[primary]`
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Anthropic — Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [The New Stack — Claude Opus 4.8 is here: effort controls, dynamic workflows, cheaper fast mode](https://thenewstack.io/claude-opus-48-release/) `[secondary]`
- [Build Fast with AI — Claude Opus 4.8 Review: Benchmarks, Dynamic Workflows, Price](https://www.buildfastwithai.com/blogs/claude-opus-4-8-review-benchmarks-dynamic-workflows-2026) `[analysis]`
- [MindStudio — Code with Claude 2026: 5 New Agent Features Anthropic Just Shipped](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features) `[analysis]`

### Why it matters to you

- **Job lens:** "I shipped a dynamic-workflow audit artifact with per-step cost and verified findings, on Opus 4.8" is a single-paragraph **interview prompt** that proves three Solutions/FDE/AI-Integration skills at once: orchestration, cost awareness, and verification. Drop it in the first paragraph of the cover-letter you send to Anthropic Solutions ([`05` §3](./05-career-and-startup.md#3-apply-window)).
- **Startup lens:** The dynamic-workflow primitive is the **fastest path** to a vertical-Claude-for-X MVP — you no longer need an orchestration framework for the first version. Spend the saved engineering time on the *eval harness* and the *cost model* (those are your moats), not the orchestrator.
- **Insight:** Dynamic workflows + the upcoming **June 15 SDK metering** ([§2](#2-sdk-metering)) are designed *together*. Anthropic shipped a much higher-leverage primitive **and** put a meter on it in the same month. The product story they're telling: *"agentic work is now powerful enough to be paid for line-by-line."* Treat your spend like a P&L from June 15 onward.

---

## 2. June 15 Agent SDK metering — T-minus 11 days {#2-sdk-metering}

The change that's been on the watchlist since [2026-05-16](../2026-05-16/01-big-lab-moves.md): **on June 15, Anthropic moves Claude Agent SDK, `claude -p`, GitHub Actions, and third-party agents onto a *separate* monthly credit pool**, billed at **full API rates**, **no rollover**. Plan-tier credit caps:

| Tier | Agent credit |
|---|---|
| Claude Pro $20 | a fixed monthly credit, separate from chat usage |
| Claude Max 5x $100 | larger fixed credit |
| Claude Max 20x $200 | largest fixed credit |

What to do **this week**, before T-0:

1. **Audit your last 30 days** of programmatic Claude usage — what % of your bill was Agent SDK / `claude -p` / GitHub Actions vs interactive Claude Code? That % is what's about to be metered separately.
2. **Toggle the credit-pool activation manually** in your account settings — it's **not auto-on** (carried from [2026-05-18 §2](../2026-05-18/01-big-lab-moves.md)). Silent-failure mode if you skip.
3. **Enable prompt caching** on any agent prompts that repeat the same system prompt or context across calls — **60–90% input-cost savings** ([2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)).
4. **Add the Opus-orchestrator + Sonnet-worker split** ([2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) to any long-running agent — same job, ~40% cheaper.
5. **Decide which workflows graduate to `ultracode`** and which stay bounded — `ultracode` magnifies parallel spend; only point it at high-value tasks.

**Sources:**
- [Codersera — Anthropic's June 15 Billing Change: What Every Claude Code & Agent SDK User Must Do](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/) `[analysis]`
- [Releasebot — Claude Code Updates by Anthropic, June 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Releasebot — Anthropic Release Notes, June 2026](https://releasebot.io/updates/anthropic) `[aggregator]`
- [Claude Platform — Release notes overview](https://platform.claude.com/docs/en/release-notes/overview) `[primary]`

### Why it matters to you

- **Job lens:** Knowing **exactly** what the June 15 change does, **and** showing you set up your own credit / caching / routing **before** the flip, is a one-line story that ranks above most "I built an agent" claims. Cite this in interview prep.
- **Startup lens:** If you're building on the Agent SDK, your COGS **changed last month** — anything you priced in May at the chat-tier-bundled rate needs a re-quote in June. **Outcome pricing** ([2026-05-10/05](../2026-05-10/05-career-and-startup.md)) gets *more* attractive as the meter becomes legible — you're insulating your customer from raw-token cost variance.
- **Insight:** Metered agent credits + dynamic workflows on the same product surface is the **clearest possible signal** that Anthropic is preparing the books for the S-1 ([`01` §1](./01-big-lab-moves.md#1-anthropic-s1)). Public-market-quality unit economics need **legible** per-customer revenue, and that's what metering delivers. Read it as: *the way to make money on Claude going forward is to build agents whose value-per-dollar you can prove.*

---

## 3. Multi-model routing as a skill — a 60-min OpenRouter sandbox {#3-routing-sandbox}

OpenRouter's $113M Series B ([`02` §1](./02-new-emerging.md#1-openrouter)) made **multi-model routing** an interview-grade skill. A bounded weekend exercise to build it cheaply:

1. Sign up for OpenRouter (a small balance is enough — single-digit dollars for the exercise).
2. Pick **one** real task you do weekly (suggestion: summarizing a paper, generating release notes, refactoring a small function).
3. Run it across **three** models — **Claude Opus 4.8 (or Sonnet 4.6) · Gemini 3.5 Pro (when GA) or Flash · GPT-5.5** — via OpenRouter's unified API.
4. Score each output on **two** dimensions only — *quality* (your own 1–5) and *cost* (token spend).
5. Write a 200-word note: *"On task X, model Y is 60% the cost of model Z for 90% of the quality."* Generalize cautiously — but **the act of measuring** is what you're selling.

**Why this is a job artifact:** every Solutions / FDE / AI-Integration role this year wants someone who can **defend a model choice with numbers, not vibes**. This is the smallest unit of that defense.

**Sources:**
- [OpenRouter docs](https://openrouter.ai/docs) `[primary]`
- [Artificial Analysis — Model pricing and benchmarks](https://artificialanalysis.ai/) `[analysis]`
- [Inc — OpenRouter Helps Companies Pick the Best AI for the Job](https://www.inc.com/ben-sherry/openrouter-helps-companies-pick-the-best-ai-for-the-job-and-could-be-worth-1-3-billion/91325983) `[secondary]`

### Why it matters to you

- **Job lens:** A short *"I benchmarked X / Y / Z on task T and routed cost-aware"* writeup beats most generic "AI experience" lines on a resume. **Especially** if you ship it to GitHub by Monday.
- **Startup lens:** If your startup idea touches LLM cost at all, you need this muscle — and **the eval harness you build for this exercise becomes a reusable internal tool** for any product decision later.
- **Insight:** The next 12 months of LLM cost will be defined by *routing*, not by *one model winning*. People who quantify routing decisions will be paid as a category — *before* the title catches up.

→ Cross-link: [`02` §1 OpenRouter $113M](./02-new-emerging.md#1-openrouter) · [2026-05-22/03 §1 Opus-orchestrator / Sonnet-worker](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`04` §1 MCP-benchmark wave (verification half)](./04-research-progress.md#1-mcp-benchmark-wave).
