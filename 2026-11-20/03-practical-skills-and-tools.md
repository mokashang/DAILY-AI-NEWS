# Practical Skills & Tools — 2026-11-20

The practitioner week was dominated by **Claude Code's MCP maturation** (background tasks, `mcp add-json` stdin, Code Mode) and **Simon Willison's `llm` ecosystem keeping up with the model wave** (llm-gemini 0.38 for Neon, llm-anthropic 0.31, llm 0.37.3 for the SQLite upgrade). The **GPT-6.2 Astra at $8/$40** also means **every router built on "Claude is more expensive than GPT" is now wrong** — refresh yours this weekend. One reality-check: **the Devin Bots launch pushes the "manager-of-agents" pattern into production — but it does not mean every workload needs one**; the discipline this week is picking the right shape of agency for your actual task. Ship-today-worthy entries are marked **↯**.

Tags: `#claude-code #mcp #llm #routing #gpt62 #gemini4 #agents #vibe-coding`

---

## 1. Claude Code 2.1.319 → 2.1.327 — MCP background, `add-json` stdin, Code Mode experimental {#1-claude-code}

↯ **Ship-today item.**

**What changed (across ~9 point releases in 14 days):**
- **2.1.318 (Nov 4):** MCP stdio servers now receive `CLAUDE_PROJECT_DIR` env var. MCP reconnects no longer re-announce the full tool-name list (silent re-establish = less log noise).
- **2.1.319 (Nov 6):**
  - **MCP tool calls now background by default.** Claude Code spawns the MCP task, keeps working, and reports back when the task finishes. **Old behavior restored by env var `CLAUDE_CODE_DISABLE_MCP_TASK_BACKGROUND=1`**.
  - New setting: `permissions.denyInsteadOfPrompting` (silently denies a tool instead of asking the user — useful for CI).
- **2.1.323:** **Code Mode** — experimental opt-in. Claude **writes JavaScript that calls its own tools**, executed in a single pass. **One call, many tool invocations, no reasoning-loop overhead.** (Your mileage will vary for complex tasks; good for "scrape + filter + summarize" shapes.)
- **2.1.327:** **`claude mcp add-json <name> -`** reads the server JSON config **from stdin** — **secrets stay out of shell history and process-listing arguments**. Also: several MCP stability fixes.

**Sources:**
- [Claude Code Changelog (November 2026) — Gradually](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Releasebot — Claude Code Updates November 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Claudexia — Claude Code 2.1.317–2.1.326 changelog](https://claudexia.tech/blog/claude-code-novoe-v-noyabre-2026) `[analysis]`
- [This week in Claude Code / Codex / Gemini CLI (Nov 8)](https://dev.to/aicoding-guide/this-week-in-claude-code-codex-and-gemini-cli-week-of-november-8-2026-485k) `[analysis]`
- [getAIDrops — AI Drops for Claude Code](https://getaidrops.com/claude/changelog) `[aggregator]`

### Why it matters to you

- **Job lens:** **MCP-background-by-default** is the kind of version-level change interviewers ask about implicitly. If asked "how have you been using Claude Code lately?", the correct 2026-11 answer is **"I background MCP tool calls so the main thread stays responsive while long jobs finish, and I'm testing Code Mode for jobs where I'd otherwise write a one-off script"** — that's 2 bullet points of recent-release fluency.
- **Startup lens:** **If your startup exposes an MCP server to developers**, (a) make sure it's **idempotent across reconnects** (2.1.318 fix means Claude Code no longer re-advertises), (b) emit **progress events** that look sane in Claude Code's new backgrounded task UI, (c) consider whether your server becomes a **"backgroundable long task" offering** (data refresh, index build, scrape) — that's the new sweet spot for MCP servers specifically.
- **Insight:** **Code Mode is this quarter's "watch it mature" feature.** It's an experimental toggle, so don't ship customer-facing anything on it yet, but **the pattern of "LLM writes glue code in one pass instead of looping"** is the same pattern that OpenAI shipped with "Responses API agentic shortcuts" and that Gemini 4 Hydrogen optimizes for. **This is a cross-lab convergence, not a Claude quirk.**

**Action this weekend (30 min):**
1. Upgrade Claude Code to latest (`claude update` or reinstall).
2. Try backgrounded MCP: start any long MCP task, keep chatting, wait for the callback.
3. Opt into Code Mode in `.claude/settings` and run one "scrape + summarize" task through it — compare latency + output to the default flow.
4. Switch any Claude MCP server configs to **`claude mcp add-json ... -`** with stdin JSON so your secrets never hit shell history.

---

## 2. Code Mode (experimental) — one-pass JS-glue is the next vibe-coding pattern {#2-code-mode}

**Longer take on Code Mode because it's a pattern, not just a feature.**

**What it is:** Claude Code writes a **JavaScript program that calls its tools** (file I/O, bash, MCP servers), runs the whole program in one pass, and returns the result. No multi-turn reasoning loop. Think of it as **"Claude writes `curl + jq + python + ffmpeg` glue code for you, then runs it, in one step"** — but with Claude's toolset instead of a shell.

**When it wins:** bulk file transforms, scrape-and-summarize jobs, batch log analysis, API fan-out with aggregation, data pipeline stubs. Tasks where you'd write a 30-line script by hand.

**When it loses:** debugging an unknown system (where the reasoning loop needs to probe + adapt), any task with user-approval gates, anything where you'd normally interact mid-flight.

**Not a replacement for:** the main reasoning-agent loop. It's a **second tool shape**, like how `make` + a one-shot script coexist with an interactive terminal.

**Why it matters:**
- **Latency**: one pass beats 10 reasoning rounds for simple fan-outs by ~5–10×.
- **Cost**: fewer input-token repeats because the state doesn't go in prompts.
- **Verifiability**: the generated JS is readable, review-able, savable as a file — **you can PR-commit the script Claude wrote**, which gives you auditability for free.

**Cross-lab convergence to watch:**
- OpenAI Responses API has similar one-pass-with-tool-calls behavior.
- Gemini 4 Hydrogen's per-task latency targets imply Google is heading the same place.
- **If you can show you understand "when to one-pass vs. when to loop," that's a Q4 2026 interview edge.**

**Weekend artifact idea:** build a `.claude/skills/one-pass-scraper.md` skill that triggers Code Mode for any scrape-and-summarize request, with a 5-case eval set. Publish the skill. **That is a week-7 FDE résumé artifact**, especially if you include eval results per URL class (SPA vs. SSR vs. API-only).

---

## 3. Router refresh: GPT-6.2 Astra at $8/$40 kills the "cost router" wedge, forces behavior-based routing {#3-router-refresh}

↯ **Ship-today item.**

**The change:** GPT-6.2 Astra (Nov 17) is **$8/$40 per M = exact parity with Claude Fable 5.2**. Cheap-vs-expensive routing is **structurally dead** at the frontier tier as of this week.

**What the new router looks like (recipe):**

```
# Pseudocode for a 2026-11 router
#
# TASK_CLASS → preferred model (ranked)
# All frontier models are $8/$40 per M input/output; weight on behavior, not cost.
#
# Task class:
# - long_code_refactor   : Claude Fable 5.2 (prompt caching + output efficiency wins)
# - novel_reasoning      : GPT-6.2 Astra  (fewer output tokens, same accuracy on hard reasoning)
# - agentic_tool_use     : Muse Spark Open on your own GPUs (MCP-Atlas 89.2) if cost-sensitive
#                          else Claude Fable 5.2 (MCP-native tooling)
# - web_browse_or_scrape : Gemini 4 Neon  (built for Flash-speed browsing)
# - meeting_summary      : Claude Meetings beta (if Team/Enterprise tenant)
# - cheap_classify       : GPT-6.2 Sol ($2/$10) or Claude Haiku 5.5 ($0.10/$0.50) if latency-sensitive
```

**Eval set to build (5 cases per task class):**
1. **long_code_refactor** → PR you already merged; replay through each model, grade ground-truth diff distance.
2. **novel_reasoning** → 5 ARC-AGI-style tasks or 5 live Project Euler.
3. **agentic_tool_use** → 5 MCP tool chains with known expected call-sequence.
4. **web_browse_or_scrape** → 5 news-aggregator queries with ground-truth facts.
5. **cheap_classify** → 50 pre-labeled customer support tickets.

**Scoring:**
- **Primary**: accuracy or diff-distance (per class).
- **Secondary**: output token count (lower = better at same accuracy, after the GPT-6.2 "fewer output tokens" trend).
- **Tertiary**: latency p50 + p95.

**Publish it.** The router + eval set is still the **#1 portfolio artifact for FDE applications** (per Nov 14 edition). **You just gained a reason to publish v2 this week** — the prior router was priced on an assumption that no longer holds.

**Sources:**
- [FinanceFeeds — GPT-6.2 pricing analysis](https://financefeeds.com/openai-gpt-6-2-astra-and-sol-shake-up-api-pricing/) `[secondary]`
- [MLQ.ai — Astra 20% price cut](https://mlq.ai/news/openai-launches-gpt-62-astra-and-sol-cutting-astras-api-price-by-20/) `[secondary]`

---

## 4. Simon Willison's `llm` ecosystem — 0.37.3, llm-anthropic 0.31, llm-gemini 0.38 {#4-llm-ecosystem}

↯ **Ship-today item.**

**What shipped (Nov 2–18):**
- **llm 0.37** (Nov 2): added OpenAI-compatible endpoint support via `llm openai endpoint add`; default model changed to `gpt-6-luna`; 12 contributors, almost all AI-assisted.
- **llm 0.37.3** (Nov 16): bug fix. Homebrew now ships SQLite 3.54.1, which includes a fix for a bug that broke `llm` logging. **Upgrade blocker on macOS.**
- **llm-anthropic 0.31** (Nov 9): adds the new Anthropic models (Fable 5.2, Mythos 5.2). Willison reports they **ranked #1 on Artificial Analysis at launch**.
- **llm-gemini 0.36** (Nov 10, Carbon), **0.37** (Nov 12, Hydrogen), **0.38** (Nov 18, Neon). Willison called the Gemini 4 pricing confusing — **fair warning: expect to see weird bills if you're not careful with per-SKU rate routing**.
- **datasette-llm 0.1a11** (Nov 14): OpenAI-compatible endpoint support, so local models (LM Studio, Ollama, llama.cpp) can power Datasette queries.

**Why it matters:**
- `llm` is the fastest-moving open CLI for cross-lab experimentation. **`git log | llm -m gpt-6.2-astra 'summarize this changelog as release notes'`** works today — pipe-native workflows are the practitioner edge.
- **The datasette-llm update is underweighted:** it means **you can run Datasette with a 100% local backend** (LM Studio + Ollama) for private corporate data — zero API cost, zero data egress. **This is the first serious "local-first business-data chat" pattern to land in open tooling.**

**Sources:**
- [Simon Willison — Release: llm 0.37](https://simonwillison.net/2026/Nov/2/llm/) `[primary]`
- [Simon Willison — Release: llm 0.37.3](https://simonwillison.net/2026/Nov/16/llm/) `[primary]`
- [Simon Willison — Release: llm-anthropic 0.31](https://simonwillison.net/2026/Nov/9/llm-anthropic/) `[primary]`
- [Simon Willison — Release: llm-gemini 0.38](https://simonwillison.net/2026/Nov/18/llm-gemini/) `[primary]`
- [Simon Willison — Release: datasette-llm 0.1a11](https://simonwillison.net/2026/Nov/14/datasette-llm/) `[primary]`

**Action (10 min):**
```bash
# Upgrade + add the new plugins + run a one-liner across three models
uv tool install --upgrade llm
llm install llm-anthropic llm-gemini  # if not already
git log --since='1 week ago' | llm -m gpt-6.2-astra 'Summarize as a 5-bullet release-notes digest.'
```

---

## 5. The "manager-of-agents" pattern — when to use it, when not to {#5-manager-of-agents}

**Context from `02` §2:** Cognition shipped Devin Bots on Nov 17, productizing a persistent manager that splits week-long projects across teams of Devin coding agents.

**The pattern:**
- **Manager agent**: reads a scope doc, builds a plan graph, assigns subtasks to worker agents, tracks progress.
- **Worker agents**: do the actual work (code, call tools, write tests, submit PRs).
- **Verifier/escalator**: merges results, runs tests, escalates ambiguities to the human.

**When to reach for it:**
- Projects that span **>24 hours** of agent runtime.
- Work that is **parallelizable across files / services / data partitions**.
- Teams that already have **strong test coverage** (verifier has a signal).
- Tasks with **clear acceptance criteria** written up front.

**When to NOT reach for it (yet):**
- Tasks under 4 hours of agent runtime — overhead > speedup.
- Novel-system exploration — reasoning loop beats static plan graph.
- Any task where errors silently produce plausible-looking outputs (verifier loses).
- Any task over sensitive data without clear HITL interrupts on tool calls.

**The three primitives you need before building one yourself:**
1. **Persistent plan state** (file-backed or DB-backed; not in-prompt — see Nov 14 "Long-Lived Agent Memory benchmark").
2. **Tool-level HITL interrupts** (LangChain 1.4.9's `interrupt()` middleware is the reference impl).
3. **Failure-attribution logs** at the manager level, not just the worker.

**DIY vs. buy:**
- If you need it today and your workload fits coding → use Devin Bots (McKinsey-channel pricing applies).
- If you want to learn the primitives → build one with **Claude Code + Managed Agents + a Postgres-backed plan state**. Weekend project.
- **The learning version is the stronger portfolio artifact** — Devin Bots usage is not a differentiator in interviews.

---

## 6. Quick hits worth 60 seconds each {#6-quick-hits}

- **Claude Desktop update channels** (Stable / Latest, Nov 17): switch to Latest if you want new features ~1 week early; stay on Stable for production work. **Mix per-machine, not per-user.**
- **Claude watermarking on text** (Nov 16): if you ship Claude-generated text into regulated workflows (news, compliance, legal), **non-default sampling settings can disable the watermark** — know this before you ship. Disabling it may put you on the wrong side of future AI-content-provenance regulations.
- **Linked Billing** (Nov 17): if you are a third-party Claude app vendor, let customers pay through their own Claude org — simpler enterprise procurement, faster deal close. **Rebuild your billing page around this** if you haven't.
- **Antigravity + Gemini 4 Argon Medium**: Google's model picker surfaces a "Medium" variant not listed on DeepMind's main model page. **Possible first tiering hint of SKU-within-SKU**; worth watching.
- **Claude Code Code Mode**: experimental — opt-in via `.claude/settings`. Don't ship customer-facing code paths through it until the next stable cut.
- **llm-gemini pricing confusion**: Willison's own note. Cache your own cost sheet per SKU before letting llm-gemini auto-select.

---

## Weekend action stack (if you have 4 hours)

1. **(45 min)** Upgrade Claude Code, enable MCP backgrounding, try Code Mode on one scrape task.
2. **(60 min)** Rebuild router v2 with GPT-6.2 Astra added + a 5-case eval set per task class. Save evals to a public Gist.
3. **(60 min)** Build or clone one MCP server (data-source of your choice), use `mcp add-json ... -` stdin install.
4. **(45 min)** Draft and push a "Router v2 for the GPT-6.2 era" post on LinkedIn or a short Substack — include the eval table. **This is the highest-leverage practitioner artifact you can publish this month.**
5. **(30 min)** Optional: install Antigravity, run one task, compare to Claude Code, write 3 paragraphs for your interview notes.
