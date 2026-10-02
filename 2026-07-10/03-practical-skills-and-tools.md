# Practical Skills & Tools — 2026-07-10

Six things landed this week that materially change what you should be doing tonight. **First**, **Claude Sonnet 5 is now the default in Claude Code with a 1M-token context window and a $2/$10 per-Mtok promo through Aug 31** — free upgrade if you update. **Second**, **Simon Willison** codified the subagent model-routing pattern he's been shipping (Sonnet writes, Haiku edits, main loop reviews) and published a **Jul 2 DSPy write-up** for tuning agent system prompts empirically — 3-line frontmatter change, measurable savings. **Third**, the **MCP 2026-07-28 Release Candidate** is out: **MCP goes stateless** (kill the last exotic infra requirement), adds a **Tasks extension**, **MCP Apps** for server-rendered UI, and formal Extensions. **Fourth**, **Cowork went cloud-native** on web and mobile. **Fifth**, **Ethan Mollick's "specs, not tricks"** — the era of prompt tricks is over. **Sixth**, a **GitHub trending trio** (gstack + orca + agent-skills) plus **Gemini CLI v0.50** — the practical toolbelt for the week.

Tags: `#claudecode #sonnet5 #subagents #mcp #cowork #dspy #agentskills #geminicli #costoptimization`

---

## 1. Claude Sonnet 5 is now the Claude Code default — 1M ctx + $2/$10 through Aug 31 {#1-sonnet5-default}

**What it is:** Anthropic promoted **Sonnet 5** to the **default model in Claude Code** (CLI, IDE, desktop). Two things you get for free by updating:

- **Native 1M-token context window** — long-context workflows that used to fail (repo-wide refactors, massive log traces, big design docs) now work.
- **Promo pricing: $2 input / $10 output per Mtok** through **Aug 31**.

The same July release adds transcript protection, a full **`/doctor`** setup check, smarter PR-linking, and lower-memory auto-updates.

**Do tonight (10 min):**

```bash
npm install -g @anthropic-ai/claude-code@latest    # or brew upgrade claude-code
claude /doctor                                     # verify setup
claude                                             # confirm default = Sonnet 5
```

Then re-run one long-context workflow you'd shelved (large-repo audit, multi-file refactor, one-shot codebase Q&A).

**Sources:**
- [Claude Code — What's New](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Claude Code Releases (GitHub)](https://github.com/anthropics/claude-code/releases) `[primary]`
- [Gradually — Claude Code changelog July 2026](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`

### Why it matters to you

- **Job lens:** Interview problems will *assume you use the current default*. "Show me a workflow you built on Sonnet 5 that leverages 1M context" is a question you'll be asked in Q3 FDE loops; be ready. Bonus: cite the promo pricing in a cost-analysis interview question — it demonstrates production-cost awareness.
- **Startup lens:** The **Aug 31 promo end date** is your ratchet. Any cost model you build over the next 7 weeks should either **(a) capture the discount now and lock in usage patterns** so you're default-cheap when list price returns, or **(b) build a router that automatically fails over to Haiku / Grok 4.5 / GPT-5.6 Terra when Sonnet-5 goes off promo**.
- **Insight:** A **default-model bump + a 5× context window + a 2-month discount** is the single easiest way to get better output from a tool you already run. It's also the cleanest possible A/B: if your workflow was tuned to Sonnet 4.6 last quarter, run *the exact same prompt* against Sonnet 5 today and log the token/quality delta — that data point is what a "before/after" post gets you 2K impressions on LinkedIn.

→ Cross-link: [`01` §3 Anthropic Cowork cloud](./01-big-lab-moves.md#3-anthropic-cowork-cloud) · [`03` §2 Willison model-routing](#2-willison-routing).

---

## 2. Simon Willison — subagent model-routing pattern + DSPy for agent prompts (Jul 2–3) {#2-willison-routing}

**What it is:** In a **Jul 3** post, Willison codified a pattern he's now shipping across Claude Code / Agent SDK setups:

> *In Claude Code / Agent SDK setups, spawn a subagent with an explicit lower-power model override (Sonnet for real implementation, Haiku for mechanical edits), keep judgment/review/synthesis in the main loop.*

Pair with his **Jul 2** post: he used **DSPy with GPT-4.1-mini/nano** to **auto-tune the Datasette Agent's SQL system prompts** — and found several concrete wins the human-authored prompts had missed. DSPy compiles prompts empirically instead of by intuition.

**Do tonight (15 min):**

```yaml
# .claude/agents/rename-files.md — a mechanical subagent
---
name: rename-files
description: Bulk-rename files following a naming convention
model: haiku          # <-- add this line
tools: [Bash, Glob]
---
Use the current shell to rename the listed files. Preserve extensions.
```

Then run your typical daily workflow for one day and log token/cost delta. Second stage: fork DSPy, feed it 5–10 traces of your best subagent prompt, and let it tune.

**Sources:**
- [Simon Willison — Research: DSPy for Datasette Agent SQL prompts (Jul 2)](https://simonwillison.net/2026/Jul/2/dspy-datasette-agent-prompts/) `[practitioner]`
- [Simon Willison — parallel-agents tag](https://simonwillison.net/tags/parallel-agents/) `[practitioner]`
- [Simon Willison — datasette-agent tag](https://simonwillison.net/tags/datasette-agent/) `[practitioner]`

### Why it matters to you

- **Job lens:** **"I moved my mechanical subagents to Haiku with `model:` frontmatter and cut token spend N%"** is the strongest interview answer you can give about cost-aware AI engineering — it's small, measurable, and demonstrates you *ran real workloads on real bills*. Do it this weekend; put the numbers in your GitHub README.
- **Startup lens:** Willison's pattern + DSPy is a **repeatable moat**: every agent product you build can be tuned instead of hand-prompted. If you're doing an accelerator app (YC S26, `RFS` explicitly names AI supply-chain / hardware / agriculture — [`05` §2](./05-career-and-startup.md#2-compounding)), demonstrate DSPy-tuned prompts in the demo — most seed-stage founders still write prompts by intuition.
- **Insight:** The **compounding move** is now: (a) Sonnet 5 default + 1M ctx (§1) + (b) Haiku subagent routing (§2, this section) + (c) MCP server built to the stateless RC (§3). Those three primitives together = what a well-run Anthropic-stack production system looks like in mid-2026. Master them in that order; interviews will assume all three.

→ Cross-link: [`01` §1–2 GPT-5.6 + Grok 4.5 pricing](./01-big-lab-moves.md#1-gpt56) · [`04` §3 MIPU inference-time policy](./04-research-progress.md#3-mipu).

---

## 3. MCP 2026-07-28 Release Candidate — stateless, Tasks, MCP Apps, Extensions (Jul 2026) {#3-mcp-rc}

**What it is:** The next MCP spec is now an **RC** (final on **Jul 28**). Practical changes worth reading before you ship anything:

- **Stateless MCP** — a remote MCP server can now sit behind a plain **round-robin load balancer** (no sticky sessions, no shared session store). Routes on an `Mcp-Method` header. **The single biggest infra simplification of the year.**
- **Extensions framework** — formal capability negotiation between clients and servers.
- **Tasks extension** — long-running work first-class in the protocol.
- **MCP Apps** — server-rendered UIs (agent-callable + interactive).
- **OAuth/OIDC-aligned auth hardening + a deprecation policy.**

**Do this weekend:** clone the RC repo, port your best existing MCP server prototype to stateless, deploy behind a boring HTTP load balancer, ship it as the "before-the-final-spec" reference implementation.

**Sources:**
- [Model Context Protocol Blog — 2026-07-28 Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [Stacktree — MCP 2026-07-28 spec: what changed, what breaks](https://stacktr.ee/blog/mcp-2026-spec-changes) `[analysis]`
- [MCP Playground — MCP goes stateless: what the 2026 RC means](https://mcpplaygroundonline.com/blog/mcp-stateless-2026-release-candidate) `[analysis]`

### Why it matters to you

- **Job lens:** Anthropic Solutions / OpenAI Deployment Company job posts will ask for **"MCP 2026-07-28 spec exposure"** by August. Ship your MCP server *now*, get one blog post + one demo gif on your GitHub before September, and you're in the top 5% of applicants by that credential alone.
- **Startup lens:** **Stateless MCP kills the last piece of exotic infra** needed to run an MCP server at scale — you can host one on the same boring HTTP stack as any REST API. That collapses the infrastructure barrier to "vertical SaaS as MCP server" from "specialist" to "any competent backend team." Which means: **the derivative wedges under [`02` §4](./02-new-emerging.md#4-mcp-distribution) unlock in the next 6 months.** Bet accordingly.
- **Insight:** Read the RC in one sitting. This is the last MCP spec that will be simple enough to read cover-to-cover; every subsequent version will accrete real complexity. **The 2 hours you spend now are the highest-ROI protocol reading of your career.**

→ Cross-link: [`02` §4 MCP distribution channel](./02-new-emerging.md#4-mcp-distribution) · [`05` §2 compounding artifacts](./05-career-and-startup.md#2-compounding).

---

## 4. Claude Cowork on web & mobile — device-independent agent runs (Jul 7) {#4-cowork-webmobile}

**What it is:** Cowork (Anthropic's remote agent runner) now runs on **web and mobile** in addition to desktop, with sessions and files tied to your Claude account rather than a machine. **Close the laptop, keep working; check progress from a phone; scheduled tasks run with no device online.** Chat + Cowork share a single home tab, and Cowork usage limits are **doubled through Aug 5**. Rollout starts on Max, expanding through the month.

**Do this week:** move one long-running background task (nightly research, weekly report, ongoing repo audit) from "run on my laptop with a shell open" to Cowork. Then check it from your phone tomorrow morning — a workflow change that *shows up in your habits* is the point.

**Sources:**
- [Anthropic (Claude blog) — Cowork on web and mobile: hand off work anywhere](https://claude.com/blog/cowork-web-mobile) `[primary]`
- [9to5Mac — Anthropic expanding Claude Cowork to mobile and web](https://9to5mac.com/2026/07/07/anthropic-expanding-claude-cowork-to-mobile-and-web-details-here/) `[secondary]`
- [TechCrunch — The coding-agent wars are spilling into the rest of the office](https://techcrunch.com/2026/07/07/the-coding-agent-wars-are-spilling-into-the-rest-of-the-office-claude-cowork/) `[secondary]`

### Why it matters to you

- **Job lens:** "Ran a Cowork session across three devices to accomplish task X" is a *specific* project-story you can cite in an FDE / Applied AI interview — everyone else will still be running local `claude` sessions. Concreteness wins.
- **Startup lens:** Device-independent agent runs = **you can be an operator of many agents at once**. This is the "one founder + a fleet of Coworks" pattern that YC has now been referencing publicly for months. Practice it now so the workflow is native by the time you actually need to run one.
- **Insight:** Once agent runs are device-independent, the productivity question flips from *"what can I run while I watch?"* to **"what long tasks can I kick off before dinner?"** The **weekend project** discipline in your ME.md becomes a *background* discipline, not a foreground one. Redesign your week around it.

→ Cross-link: [`01` §3 Anthropic Cowork cloud](./01-big-lab-moves.md#3-anthropic-cowork-cloud).

---

## 5. Ethan Mollick — "Twilight of the Chatbots" / specs, not tricks (Jul 7 + preceding week) {#5-mollick-specs}

**What it is:** In two early-July **One Useful Thing** posts, Mollick argues the era of clever prompt tricks is over: **treat modern LLMs as literal, capable executors that need managerial specs** — goals, output definitions, quality bars, test cases — not incantations. Anchoring example: **Opus 4.7 worked autonomously for 14 hours to ship software estimated at 2–17 weeks of human engineering, at ~$251 in tokens.** Practical takeaway: **rewrite one of your prompt templates as a one-page spec** (task, deliverable format, acceptance tests, budget).

**Do tonight (20 min):** pick your most-used prompt template. Rewrite as a 1-page spec:

```markdown
## Task
[Concrete objective, one paragraph]

## Deliverable
[Exact format, structure, length]

## Acceptance tests
- [checkable criterion 1]
- [checkable criterion 2]
- [checkable criterion 3]

## Budget
- Max tokens: N
- Max wall-clock: M
- Fail-safe: [what to do if criteria not met]
```

Diff the output. Almost always: faster, tighter, closer to what you actually wanted.

**Sources:**
- [Ethan Mollick — One Useful Thing](https://www.oneusefulthing.org/) `[practitioner]`
- [ExplainX — Ethan Mollick / Wharton: prompting = specs, not tricks](https://explainx.ai/blog/ethan-mollick-wharton-prompting-science-specs-not-tricks-2026) `[analysis]`
- [AI Weekly — Ethan Mollick: agents are replacing chatbots for real work](https://aiweekly.co/alerts/ethan-mollick-agents-are-replacing-chatbots-for-real-work) `[aggregator]`

### Why it matters to you

- **Job lens:** **"Show me a prompt spec you wrote"** is a rising interview question at labs and applied-AI shops. Bring three specs to your next loop.
- **Startup lens:** If your product ships prompts that anyone can see, they should look like specs, not tricks. It's a *credibility* signal to enterprise buyers, who reject "trust me, this prompt works" but accept "here's the spec, here's the acceptance test, here's the log."
- **Insight:** If your prompt library is still full of role-play openers and "think step by step," you're **paying for autonomy you're not using**. The $251-for-2-to-17-weeks-of-work number is real. Specs unlock that budget-to-outcome ratio. Tricks don't.

→ Cross-link: [`04` §1 Anthropic Global Workspace](./04-research-progress.md#1-j-lens) (concept-legibility ↔ spec-writability).

---

## 6. GitHub trending trio + Gemini CLI v0.50 (week of Jul 6–10) {#6-github-trending}

**What it is:** Three practical repos surged in early July:

- **`garrytan/gstack`** — a **Claude Code setup with 23 opinionated roles** (CEO, Designer, Eng Manager, Release Manager, QA, etc.) you can clone into a project overnight to get a "team-shaped" agent stack.
- **`stablyai/orca`** — a **desktop/mobile agent development environment** for running fleets of parallel coding agents.
- **`addyosmani/agent-skills`** — **production-grade Agent Skills** (SKILL.md packages) covering common engineering tasks.

Plus: **Gemini CLI v0.50.0** (Jul 8) shipped **Tool Registry Discovery** so extensions auto-register — a genuine ergonomic improvement if you use Gemini CLI as a second-opinion tool.

**Do this weekend (30 min):** clone one — probably `agent-skills` — and use it to speed up **one recurring task you already do this week**.

**Sources:**
- [OSSInsight — Trending AI repositories on GitHub](https://ossinsight.io/trending/ai) `[aggregator]`
- [OrangeBot — GitHub trending today](https://orangebot.ai/github-trending-today) `[aggregator]`
- [Gemini CLI v0.50.0 release notes](https://geminicli.com/docs/changelogs/latest/) `[primary]`
- [Anthropic Engineering — Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) `[primary]`

### Why it matters to you

- **Job lens:** Contributing one Agent Skill (SKILL.md) to `addyosmani/agent-skills` is the fastest way to get an **AI-engineering-relevant open-source contribution** on your GitHub with real audience.
- **Startup lens:** Skill packs and role scaffolds are becoming the fastest way to turn a generic coding agent into a team member that knows how *your* shop ships. If you're founding, `gstack` shape (23 opinionated roles) is a template for your future company's internal agent scaffolding — copy it before you scale.
- **Insight:** GitHub trending in the AI category is the **cheapest signal you can get for what your peers are actually running**. Read it weekly (Sunday, 10 minutes) and clone one repo per week. Your skill compounding curve for 2026 is directly a function of this discipline.

→ Cross-link: [`03` §1 Sonnet 5 default](#1-sonnet5-default) · [`02` §4 MCP distribution](./02-new-emerging.md#4-mcp-distribution).

---

## Bottom line — one-hour Friday checklist

1. **10 min** — update Claude Code, confirm Sonnet 5 default, run one long-ctx workflow. ([§1](#1-sonnet5-default))
2. **15 min** — add `model: haiku` frontmatter to one mechanical subagent, log token savings. ([§2](#2-willison-routing))
3. **20 min** — rewrite your most-used prompt template as a 1-page spec. ([§5](#5-mollick-specs))
4. **This weekend** — read the MCP 2026-07-28 RC end-to-end, port your MCP-server prototype to stateless. ([§3](#3-mcp-rc))
5. **This week** — move one long-running background task to Cowork, monitor from your phone. ([§4](#4-cowork-webmobile))
6. **Sunday, 10 min** — scan GitHub Trending AI, clone one repo. ([§6](#6-github-trending))
