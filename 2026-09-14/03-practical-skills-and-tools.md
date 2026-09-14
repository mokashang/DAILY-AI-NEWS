# Practical Skills & Tools — 2026-09-14

Act on these today. Three of the four are one-command upgrades to your existing Claude Code stack; the fourth (plugin eval) is the highest-leverage new engineering pattern of the week. **Theme: Claude Code v2.1.267 through v2.1.269 shipped between Sept 9 and Sept 11 with quiet-but-important changes that reprice the router artifact from [2026-09-10/03](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) — you now get reproducible evals for the router, tunable parallelism for the batch case, and prompt-cache stability for the orchestrator system prompt. If you built the router, upgrade it tonight.**

Tags: `#claude-code #evals #skills #plugins #mcp #cache #subagents #routing #workflow`

---

## 1. `claude plugin eval` — reproducible A/B testing for skills & plugins (Sept 11, v2.1.269) {#1-plugin-eval}

**What happened:** Anthropic shipped a **first-class ablation harness inside Claude Code.** Command shape: `claude plugin eval [suite-path]`. It runs your test cases **with a plugin/skill loaded, then re-runs them without it**, and produces a **scored JSON + HTML diff report** — which cases moved, which regressed, what the delta looks like across the suite.

This is the eval loop that was missing for anyone building custom `.claude/skills/`. Before this, "does my skill actually help?" was vibes-based. Now it's a numeric before/after diff you can commit to Git.

### How to try this tonight (60 minutes)

1. **Pick one skill** — the `.claude/skills/*.md` you've been using most, or a new one you're drafting.
2. **Write 5 golden cases** — real prompts your project actually runs (e.g. "review this PR," "generate a migration from schema A to schema B," "answer this doc-QA question"). Save them as `evals/skill-cases.md`.
3. **Run `claude plugin eval --skill <name> evals/skill-cases.md`** — you'll get the JSON + HTML report.
4. **Commit** the report to your repo under `evals/reports/YYYY-MM-DD-<skill>.md`. This is the "we ship evals, not vibes" artifact.
5. **Iterate** — improve the skill, re-run, watch the delta. This *is* the interview differentiator for FDE roles.

### Why this is Sunday's DO

The [Sept 3 GPT-6 Astra launch](../2026-09-10/01-big-lab-moves.md#1-model-fatigue) and the [pacing accord (Sept 12)](./01-big-lab-moves.md#1-pace-the-frontier) collectively re-priced two skills: **model-routing** and **eval-authoring** (per [`05` §1](./05-career-and-startup.md#1-ramp-cracks)). The router artifact you shipped last week gives you the first; **plugin eval + one commit of before/after reports gives you the second.** This is the smallest possible artifact that visibly demonstrates eval discipline on a public repo — and it takes one afternoon.

### Sources
- [Anthropic Claude Code Changelog — v2.1.269 (plugin eval)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Release Plugin Eval Docs — archive Sept 11 2026](https://github.com/llms-txt-archive/anthropic-claude-code/releases/tag/archive-20260911T211743Z) `[primary]`

---

## 2. Tunable concurrent-subagent cap — `CLAUDE_CODE_WORKFLOW_MAX_CONCURRENT_AGENTS` (Sept 11, v2.1.269) {#2-workflow-cap}

**What happened:** The Workflow tool's per-run fan-out ceiling is now a **user-tunable env var** (range: 1–256) rather than a fixed default. Paired with a new VS Code Focus-view feature — **live progress rows for running subagents under tool-call groups** — you finally get visible parallelism for inference-bound work: batch classification, PR triage, doc chunk grading, multi-file review sweeps.

### How to try this tonight (15 minutes)

```bash
export CLAUDE_CODE_WORKFLOW_MAX_CONCURRENT_AGENTS=32
# then, in your project:
/workflow grade-diffs.md
```

Where `grade-diffs.md` is a workflow that fans out one subagent per file in a PR. On a 200-file PR with `=32`, you finish in ~7× less wall clock vs. the old default `=6`. Just be aware of **your API rate limits + spend** — 32 concurrent Fable 5.1 requests hits budget quickly at burst. Use with **cached system prompt** (see §3) to make it affordable.

### Sources
- [Anthropic Claude Code Changelog — v2.1.269](https://code.claude.com/docs/en/changelog) `[primary]`

---

## 3. Prompt-cache stability fix for `--system-prompt` and subagents (Sept 9, v2.1.267) {#3-cache-fix}

**What happened:** **Subagents and sessions started with `--system-prompt` / `--append-system-prompt` now record the system prompt and tool definitions once** instead of re-rendering them each turn. Translation: your **long orchestrator system prompt actually hits cache-read pricing across the whole run** — nontrivial money on Fable 5.1's [$0.25/1M cache-read rate (Sept 1)](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics).

If you were rolling your own agent loop with the SDK and wondered why your cache-hit ratios were terrible, this was almost certainly the reason. Upgrade to ≥ v2.1.267.

### How to try this tonight (10 minutes)

```bash
claude doctor            # confirm version
# if < 2.1.267:
npm i -g @anthropic-ai/claude-code@latest
# then run one long subagent workflow twice — before/after — and diff:
claude /insights         # check cache-read vs input-token counts
```

**Expected effect:** on a 20k-token system prompt + subagent that runs 30 turns, cache-read share should jump from ~35% to ~80%+. At Fable 5.1's cache-read discount, that's ~$0.60 → ~$0.20 per session — a **~3× cost reduction on the orchestrator itself.** Multiply by your daily session count.

### Sources
- [Anthropic Claude Code Changelog — v2.1.267](https://code.claude.com/docs/en/changelog) `[primary]`
- [Anthropic — Token-Saving Updates](https://claude.com/blog/token-saving-updates) `[primary]`

---

## 4. MCP HTTP+SSE fallback + query-param resilience (Sept 10–11, v2.1.268/269) {#4-mcp-fallback}

**What happened:** Two quiet-but-important MCP fixes in successive releases:

1. **HTTP+SSE fallback per spec.** Servers configured as `http` now fall back to the legacy HTTP+Server-Sent-Events transport when the newer transport is unsupported. **A whole class of half-broken community MCP servers just started working.** If you gave up on an MCP server last month, retry it this week.
2. **Query-param resilience.** Synced plugin MCP servers now reconnect on resume, and re-ordering query params in your MCP URL no longer forces a reconnect storm. Fixes a common failure mode with third-party MCPs mounted behind auth proxies.

### How to try this tonight (10 minutes)

```bash
claude mcp list                # what's currently mounted
claude mcp doctor              # diagnostics on each server
# for any server that failed to connect in the past:
claude mcp add <url> --name <n>
```

Combined effect: **the MCP ecosystem got noticeably more reliable this week without any behavior change on your end** other than upgrading. In light of the [DaVinci Resolve 21.1 + ReleasePad MCP wave (§02 §4)](./02-new-emerging.md#4-mcp-verticalizes), this is the right week to re-audit which MCP servers actually belong in your `.claude/settings.json`.

### Sources
- [Anthropic Claude Code Changelog — v2.1.268 / v2.1.269](https://code.claude.com/docs/en/changelog) `[primary]`

---

## Bonus: the 4-line stack upgrade for tonight

If you have exactly one hour and want the maximum-ROI Sunday-night upgrade:

```bash
# 1) Upgrade Claude Code
npm i -g @anthropic-ai/claude-code@latest && claude doctor

# 2) Set parallelism budget
export CLAUDE_CODE_WORKFLOW_MAX_CONCURRENT_AGENTS=16

# 3) Write 5 golden cases for your most-used skill, then:
claude plugin eval --skill <name> evals/skill-cases.md
git add evals/reports && git commit -m "add plugin eval baseline"

# 4) Retry your shelved MCP servers
claude mcp doctor
```

That's it — you now have **cached orchestrator prompts, tunable parallelism, committed skill evals, and a working MCP surface,** all four re-priced upward in the last five days. This same four-line stack is what a hiring manager wants to see on your `.claude/` when they open your GitHub.

### Bonus sources
- [Simon Willison — Release: llm 0.34](https://simonwillison.net/2026/Sep/2/llm/) `[analysis]` — parallel evolution in the CLI ecosystem; `llm logs` speedup worth grabbing
- [layer3labs — GPT-6 Astra API pricing](https://www.layer3labs.io/guides/gpt-6-astra-api-pricing) `[secondary]` — for the router's cost table
