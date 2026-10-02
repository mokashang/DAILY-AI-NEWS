# Practical Skills & Tools — 2026-07-08

The cheapest, most portable upgrade you can make this week is a **cost-router artifact** that stacks three levers landing simultaneously: (1) **Claude Sonnet 5** as the new Claude Code default with a **$2/$10-per-Mtok promo price through Aug 31**, (2) **prompt-cache-first prompt structure** to compound the discount, and (3) an optional **Chinese open-weight fallback (GLM 5.2 / Kimi K2.7 Code)** for eval-tier and non-sensitive work — which is legibly cutting bills by ~50% in production (Coinbase). Then two smaller wins: **claude mcp login** (finally) and the **/loop TDD pattern** for tests + refactor.

Tags: `#claude-code #cost #routing #prompt-caching #mcp #skills`

---

## 1. The cost-router stack: Sonnet 5 promo + cache-first prompts + open-weight fallback {#1-cost-router-stack}

**What to do (30-min setup, permanent skill):**

Three levers, one weekend project — all three should live in a single **`cost-router-demo/`** repo you push tonight and put in your portfolio.

**Lever A — Sonnet 5 promo pricing (through Aug 31).**
- **Claude Sonnet 5 is now the default model in Claude Code**, with a **native 1M-token context window** and **promo pricing of $2/$10 per Mtok (input/output) through Aug 31**.
- Default your Claude Code sessions to Sonnet 5 for *worker* tasks (code write, tests, refactors). Reserve Opus for the *orchestrator* (planning, code review) — same pattern as the [May 22 orchestrator/worker split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost), but now with a better price point on the worker.
- Verify the pricing by opening `/config` in Claude Code and reading the active model + billing rate — Anthropic surfaces both explicitly now.

**Lever B — Prompt-cache-first template.**
- Put **static context (system architecture, API docs, CLAUDE.md content, style guides) at the very top of every long-running prompt**; put **the user turn / task at the bottom**. Prompt caching hashes from the top down, so a stable prefix hits the cache; a stable *suffix* doesn't.
- Concretely: your CLAUDE.md, your project's top-level README, your MCP server's tool descriptions, and any large fixture data → **top of the prompt, in that order**. Interactive user input → bottom.
- The Claude Docs surface which portion of the prompt hit the cache in each turn — watch it. On the second call, you should see ~80–95% of input tokens billed at the **cache-read price** (roughly 10% of the base rate). Combined with Lever A, that's **effective input pricing of ~$0.20 / Mtok** for repeated-context work.

**Lever C — Optional Chinese open-weight fallback.**
- For **eval passes, batch summarization, boilerplate refactors, and non-sensitive code translation**, route to **GLM 5.2** (via OpenRouter) or **Kimi K2.7 Code** — you should see roughly **3–6× cheaper input, ~6× cheaper output** vs. Opus 4.8 ([`02` §1](./02-new-emerging.md#1-china-cost)).
- **Do NOT route offshore for**: customer PII, regulated data (HIPAA/PCI/SOX), IP-sensitive proprietary code, or anything under an export-control review. Encode this as a **routing table in code**, not a norm.
- Log the cost delta explicitly — that log becomes the **artifact you show in interviews.**

**How to package it:**

```
cost-router-demo/
├── README.md            # the pitch: "50%+ cost cut, capability held on eval-tier tasks"
├── router.py            # a single dispatch function that reads a task-type tag
├── prompts/
│   ├── prefix.md        # cache-friendly static context
│   └── tasks/           # per-task-type user turns
├── evals/
│   ├── holdout.jsonl    # ~50 tasks, mixed sensitivity levels
│   └── run_eval.py      # runs each router config, reports score + $ cost
├── cost_log.csv         # every call, per-model, per-task, per-cache-status
└── docs/
    ├── governance.md    # when NOT to route offshore (residency/IP/export)
    └── benchmark.md     # cost delta + eval-score parity chart
```

**Sources:**
- [Anthropic Claude Help Center — Release notes (Sonnet 5 default, 1M ctx, promo pricing)](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`
- [Claude Code Docs — What's new](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Releasebot — Claude Code updates by Anthropic, July 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [MarkTechPost — Claude Code Guide 2026: 25 features with examples + demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Techtimes — Coinbase cuts AI spend 50% on Chinese models](https://www.techtimes.com/articles/319248/20260628/coinbase-cuts-ai-spend-50-chinese-models-legal-risk-its-ceo-didnt-lead.htm) `[secondary]`
- [Gradually.ai — Claude Code changelog (July 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`

### Why it matters to you

- **Job lens:** This is the **single strongest portfolio artifact** you can put on a resume for FDE / Integration / AI-Solutions roles this quarter. Interviewers already know the pieces; they want to see someone who has assembled them into a **repeatable, documented, cost-aware, governance-aware system**. Lead the README with a number ("Cut inference cost 51% on a 50-task benchmark while holding eval score within 1.2 points of the all-Opus baseline") and put the governance appendix in front — that's the **enterprise-buyer signal** that separates you from bootcamp portfolios.
- **Startup lens:** This artifact is also **the internal document you'd write on day 1 of a founding role.** Every AI-application startup in 2026 has to answer "what's your inference cost curve, and how do you stay margin-positive when Chinese weights halve pricing again?" — having the router pattern *and* the governance table pre-built means you can ship your MVP with the right cost profile without having to refactor 6 months in.
- **Insight:** The meta-skill on display isn't "you can pick a cheaper model" — it's **"you can measure and manage the tradeoff."** In 2025 the interesting question was *which* model. In 2026 it's *what routing policy, at what per-token cost, at what governance risk, for what task class*. That's a discipline, not a knob. Practice the discipline in one repo; then you can apply it to the next lab's models in October without rewriting a thing.

→ Cross-link: [`02` §1 the China cost pressure this responds to](./02-new-emerging.md#1-china-cost) · [`05` §2 the skill reprice](./05-career-and-startup.md#2-reference-lab) · [2026-05-22/03 §1 the orchestrator/worker precursor](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. `claude mcp login` / `logout` — MCP auth finally moves to the shell {#2-mcp-login}

**What shipped:** `claude mcp login` **authenticates a configured MCP server directly from your shell** — no more running through the interactive `/mcp` menu inside a session to hand off credentials. `claude mcp logout` clears stored credentials.

**Why it matters practically:**
- CI-friendly: you can log into your MCP servers from a Makefile or a GitHub Action step now, not from a live session.
- Deterministic for scripting: `claude -p` (programmatic Claude) sessions that depend on MCP tools can now be launched **fully headlessly**.
- Better MCP hygiene: `logout` gives you a clean rotate-credentials story for shared machines (or shared claude.ai sessions).

**Do this tonight (5 min):**
```bash
# for each MCP server you use
claude mcp login <server-name>
# verify
claude mcp list
```
If you have an MCP server exposing production data, **rotate credentials + re-login** now that the surface exists. That's the equivalent of a "clean install" for your agent stack.

**Sources:**
- [Anthropic Claude Help Center — Release notes](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`
- [Claude Code Docs — What's new](https://code.claude.com/docs/en/whats-new) `[primary]`

### Why it matters to you

- **Job lens:** Shell-auth MCP is a small change but a **big signal** — Anthropic is normalizing MCP inside CI/CD, which means enterprises are, too. Add "**shipped a shell-authenticated MCP server as a step in a GitHub Actions pipeline**" to your resume and you're describing production-grade agentic infrastructure. That single line has read-through to Cursor/Vercel/GitHub Copilot-adjacent roles.
- **Startup lens:** If you're building an MCP server as a product (for sale, not for hire), **your integration story just got dramatically simpler**. Update your docs to include the `claude mcp login <your-server>` one-liner as the install command; that's the shortest path from "user reads about it" to "user is authenticated and using it."
- **Insight:** MCP is where the **agent stack's authentication story is finally converging** to look like the rest of the tooling world (think `gcloud auth`, `aws configure`, `gh auth login`). When agent tooling starts to look like ops tooling, agent developers start getting hired like ops engineers — which is a good comp band.

---

## 3. `/loop` for TDD — turn tests-green into a background task {#3-loop-tests}

**What shipped:** The **`/loop`** command in Claude Code runs a prompt or slash command on a recurring cycle. The pattern that just clicked into place: **use it to run tests, refactor, re-run tests, and iterate until 100% green — without needing manual confirmation each turn.**

**Recipe:**
```
/loop 5m /run-tests-and-refactor
```
Where `/run-tests-and-refactor` is a saved skill that (1) runs the test suite, (2) reads failures, (3) proposes a minimal fix, (4) applies it, (5) commits with a stable message, (6) exits if all green.

- **When it works well:** small, well-tested codebase; the failing tests actually pinpoint bugs; you're OK with the model deciding "minimal fix."
- **When it breaks:** long integration tests, or when the test suite is itself flaky (the loop chases ghosts). Add a **rate-limit + failure-cap guard** (`if failures unchanged across 3 iterations → stop and page me`).

**Sources:**
- [Claude Code Docs — What's new](https://code.claude.com/docs/en/whats-new) `[primary]`
- [EmergingAI Substack — Claude changed: the July 2026 way to use it](https://emergingai.substack.com/p/claude-changed-the-july-2026-way) `[analysis]`
- [Superdev Academy — Claude AI 2026 Guide: 10 hidden features to code 10x faster](https://www.superdevacademy.com/en/blogs/claude-ai-2026-guide-coding-tips-tricks) `[analysis]`

### Why it matters to you

- **Job lens:** "**Autonomous test-repair loop with a guard**" is a great **live-demo interview trick** — set it up on a small toy project, break a test on purpose, run `/loop`, and let it converge while you talk the interviewer through the guard logic. Two things this proves in 90 seconds: (1) you understand agentic coding, (2) you understand where agents fail and how to fence them.
- **Startup lens:** For any *internal-tools* wedge, `/loop`-plus-guards is the primitive that turns "AI helps developers" into "AI keeps the CI dashboard green while developers sleep." If you're building dev-tools, the honest question isn't "does it write code" — it's "**does the loop converge without breaking things**"; that's the eval to run and to sell against.
- **Insight:** The pattern generalizes far beyond tests: **"loop-with-guard"** is the shape of every autonomous workflow that's actually shipping (JADEPUFFER attackers, `/loop` TDD, agentic underwriting at Taktile). The **guard is doing more work than the loop.** Practice writing guards deliberately — max iterations, invariants, cost caps, blast-radius limits — because that's where the real 2026 agentic-engineering skill lives.

→ Cross-link: [`02` §2 Taktile as the industrial-scale version](./02-new-emerging.md#2-taktile) · [`04` §1 formal eval evolution](./04-research-progress.md#1-agent-evals).

---
