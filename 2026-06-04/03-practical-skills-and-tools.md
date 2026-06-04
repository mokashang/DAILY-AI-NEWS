# Practical Skills & Tools — 2026-06-04

Three things you can do tonight or this weekend, each ≤2 hours and each producing a portfolio-grade artifact. **The unifying skill this week: orchestration that knows what it costs.** Dynamic workflows in Claude Code, a re-priced routing matrix, and a 100-line multi-vendor fallback are three faces of the same job: *control the bill while the model does the work.*

Tags: `#claude-code #dynamic-workflows #routing #cost #fallback #plugins`

---

## 1. Try Claude Code dynamic workflows tonight — and log the spawned-agent bill {#1-dynamic-workflows}

**What it is:** A feature shipped with Opus 4.8 (May 28) that lets you ask Claude to *create a workflow* and orchestrate **tens to hundreds of background agents in parallel** inside a single Claude Code session. Practically: you describe a big task, Claude plans the topology, dispatches sub-agents, aggregates results.

**The 90-minute drill:**
1. Pick a real codebase you're working on (your own — not a toy repo).
2. Update Claude Code to latest (auto-loads `.claude/skills` plugins now).
3. Prompt: *"Use a dynamic workflow to audit this repo for (a) outdated dependencies, (b) test coverage gaps in the highest-churn 10% of files, (c) missing error-handling at function boundaries. Plan the workflow first; show me the agent topology; then execute and aggregate."*
4. **Log per-sub-agent input/output tokens** to a CSV (Opus 4.8 supports this via the standard tracing endpoints).
5. Compare the dynamic-workflow run to a single-agent run of the same task. Note: time, total tokens, % of useful output.

**The artifact:** a short README — *"What dynamic workflows actually cost on my repo"* — with the CSV embedded. **Three sentences of takeaway is enough.** Push to GitHub by Sunday.

**Sources / docs:**
- [Anthropic — Introducing Claude Opus 4.8 (dynamic workflows)](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Releasebot — Claude Code Updates June 2026](https://releasebot.io/updates/anthropic/claude-code) `[secondary]`
- [Claude Code Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [MindStudio — Code with Claude 2026: 5 New Agent Features Anthropic Just Shipped](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features) `[analysis]`

### Why it matters to you

- **Job lens:** This is the single most likely thing an Anthropic Solutions interview will ask you about for the next 60 days. "Have you used dynamic workflows? On what kind of task? What was the spawn cost?" An honest answer with a CSV beats a polished answer without one — *every* time.
- **Startup lens:** Dynamic workflows commoditize "multi-agent orchestration" as a feature, which means **multi-agent observability** ("which sub-agent burned the most tokens, on what subtask, with what success rate?") becomes the open product. That's a real wedge — Langfuse, LangSmith, Arize all have partial answers; nobody has the *dynamic-workflow-native* answer yet.
- **Insight:** Anthropic shipped the orchestration *primitive* and skipped the orchestration *framework* layer entirely. They expect the layer above to be built by partners and customers — i.e., you.

→ Cross-link: [`01` §4](./01-big-lab-moves.md#4-opus-48) · [`04` §1](./04-research-progress.md#1-orchestration-cost) (the research backing this).

---

## 2. Re-price your routing matrix this week (the GA-pricing reset is real) {#2-routing-matrix}

**What it is:** A one-page table that maps **task type → chosen model → why** for your own workflows. The model lineup just shifted (Opus 4.8, Opus 4.8 Fast, GPT-5.5 GA, GPT-5.5 Pro, Gemini 3.5 Flash GA). The table you wrote in May is now wrong.

**The 30-minute drill — minimum viable matrix:**

| Task | Pick | Rationale (1 sentence) | Fallback |
|---|---|---|---|
| Multi-step planning / agent orchestrator | **Opus 4.8 (standard)** | Best on SWE-Pro / Terminal-Bench; alignment matters when it's deciding what to do next | GPT-5.5 Pro |
| Bulk code generation in a known pattern | **Opus 4.8 Fast** | $10/$50, 2.5× speed, recently 3× cheaper — fits the worker-pool role | Sonnet 4.5 |
| Computer-use / browser agent | **Opus 4.8** | 84% on Online-Mind2Web; Anthropic-best | GPT-5.5 (computer-use improved) |
| Bulk classification / extraction | **Gemini 3.5 Flash** | $1.50/$9, GA, 1M ctx — cheapest workhorse on long inputs | Haiku 4.5 |
| Long-context document QA | **Gemini 3.5 Pro** *(when GA, ~mid-June)* | 2M ctx + Deep Think; otherwise Opus 4.8 | Opus 4.8 |
| Cheap sanity-checker / verifier in front of expensive call | **Haiku 4.5 / Gemini Flash** | Pennies per call; catches 70%+ of obvious failures | — |

- **Cached-input savings** (Flash $0.15, GPT-5.5 $0.50, Anthropic prompt caching from [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)) is the largest single cost lever — apply *first* before re-tiering.
- The **June 15 Agent SDK metering** change (T-11 days) means programmatic Claude use bills at API list rates against a separate credit pool. Re-run your matrix *with that pricing in effect* on the 16th.

**Sources:**
- [Artificial Analysis — Pricing & benchmarks rollup](https://artificialanalysis.ai/) `[analysis]`
- [Vellum — Opus 4.8 Benchmarks Explained](https://www.vellum.ai/blog/claude-opus-4-8-benchmarks-explained) `[analysis]`
- [llm-stats — AI Updates Today (current pricing)](https://llm-stats.com/llm-updates) `[aggregator]`

### Why it matters to you

- **Job lens:** Bring this matrix to a screen interview. It demonstrates: read the changelog, understand pricing, build a defensible routing policy. That's three signals in one artifact.
- **Startup lens:** A *good* routing matrix is the kernel of a *routing product.* Companies are paying for this as a service ([Portkey, Helicone, OpenRouter](https://openrouter.ai)). If yours is better-tuned for your vertical than theirs, that's your wedge — package it.
- **Insight:** The skill is not "I know all the models." The skill is "I can defend this *exact* matrix against a CFO." Anyone can list the models; few can justify the routing policy.

→ Cross-link: [2026-05-20/03 §4](../2026-05-20/03-practical-skills-and-tools.md#4-cost-routing) (prior version, now superseded).

---

## 3. Ship a 100-line multi-vendor fallback router this weekend {#3-fallback-router}

**What it is:** A small Python (or TS) module that exposes a single `complete(messages, **kwargs)` function, routes by your matrix, and **automatically falls back** across providers on errors / timeouts / rate-limits / content-policy refusals. The June 2 Claude outage made this concrete.

**Spec (keep it 100 lines):**
- One function in, structured response out.
- Provider order (configurable): `anthropic → openai → google → openai-azure`.
- Circuit breaker: after N consecutive errors per provider, skip for M minutes.
- Per-call logging: `{provider_used, latency_ms, input_tokens, output_tokens, retries, fallbacks_used}` written to a JSONL file.
- One CLI flag: `--vendor=auto|anthropic|openai|google` for forcing.

**Don't include:** prompt caching (use the SDKs' built-in), streaming (skip for v1), batching, auth-vault integrations. Resist the urge.

**Sources / examples:**
- [LiteLLM](https://github.com/BerriAI/litellm) `[secondary]` — reference implementation of the same idea at scale; read for design ideas.
- [Simon Willison — LLM CLI](https://github.com/simonw/llm) `[secondary]` — minimal multi-provider abstraction.
- [Anthropic Python SDK](https://github.com/anthropics/anthropic-sdk-python) `[primary]` · [OpenAI Python SDK](https://github.com/openai/openai-python) `[primary]` · [Google GenAI SDK](https://github.com/googleapis/python-genai) `[primary]`

### Why it matters to you

- **Job lens:** The interview question *"what would you do if Claude went down for 2 hours during peak business?"* is now a *current event*. Demoing this artifact answers it cleanly: code, log file, fail-open vs fail-closed defaults, and a sentence on what each vendor's SLA actually says.
- **Startup lens:** Procurement loves "multi-vendor by design." Even if you run on Anthropic for 95% of traffic, having the fallback hot-wired removes the "single-point-of-failure" objection from your sales cycle.
- **Insight:** This is the *opposite* of the dynamic-workflows artifact (§1) — that one is **maximum orchestration sophistication on one vendor**; this one is **maximum vendor resilience with minimum sophistication**. Both belong on the same résumé.

→ Cross-link: [`02` §4](./02-new-emerging.md#4-outage) (the outage that made this concrete).

---

## 4. Bonus: turn `.claude/skills` plugins on this week {#4-plugins}

**What it is:** Claude Code now **auto-loads plugins from any `.claude/skills/` directory**, no marketplace registration required. `claude plugin init` scaffolds one.

- One plugin = a `SKILL.md` (instructions) + optional `bin/` (executables) + optional MCP server.
- Use case: a `gitops` skill that runs your team's standard branch-create + commit-message + PR-open flow with your repo's conventions baked in.
- Add the **`security-guidance` plugin** (Anthropic-shipped) — it reviews Claude's own code changes for vulnerabilities and fixes them in the same session.

**Sources:**
- [Releasebot — Claude Code Updates June 2026](https://releasebot.io/updates/anthropic/claude-code) `[secondary]`
- [Claude Code Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Anthropic GitHub — claude-code releases](https://github.com/anthropics/claude-code/releases) `[primary]`

### Why it matters to you

- **Job lens:** A single well-crafted skill in your `dotfiles` repo is the most direct way to show *daily, hands-on Claude Code usage* to a hiring manager. Two skills + a SKILL.md README explaining your workflow = the lightest possible "experience using Claude Code" portfolio entry.
- **Startup lens:** **Distributable skills are the missing link** between Claude Code and the broader Plugin economy. The first SkillHub-equivalent (hosted skill registry with reviews, install metrics, paid skills) is a real venture-scale wedge. Anthropic shipped the loader; nobody has shipped the marketplace.
- **Insight:** Plugins-by-convention (drop file in directory) is a *much stronger* developer-experience choice than plugins-by-registration. Anthropic understands that the bottleneck on agent adoption is workflow standardization, not capability — and they're betting that file-conventions beat APIs for that job.

→ Cross-link: [2026-05-17/03 §3](../2026-05-17/03-practical-skills-and-tools.md) (Karpathy `CLAUDE.md` — same conventions-over-config pattern).
