# Practical Skills & Tools — 2026-07-02

Four things you can actually do tonight. Ranked by ROI. If you only do one, do §1 — it's the direct counter to the Uber/Lindy/Karp story in [`01` §5](./01-big-lab-moves.md#5-token-attack), and it takes ~15 minutes.

Tags: `#practical #claude-code #cost #agents #mcp #hooks #skills`

---

## 1. Rewrite your prompt-caching for the 5-minute TTL — or lose 30–60% to the meter {#1-prompt-cache}

**What / how:** Anthropic quietly cut the **default prompt-cache TTL from 60 min → 5 min** earlier this year. If you built around the old behavior, your **cache-write costs (1.25× base)** are being paid over and over while **cache reads (~10% of base)** rarely land. Three fixes worth trying tonight:

1. **Pass `cache_control: {"type": "ephemeral", "ttl": "1h"}`** on your **largest stable block** (system prompt, tool definitions, long RAG context). The 1h TTL is available but priced higher, so **only use it when you get >2 hits/hour.**
2. **Lightweight "keep-alive" ping every 4 min** for hot sessions — cheapest way to keep the 5-min default warm.
3. **Stack Batch API (50% off) + Haiku routing + caching** → **~$0.05/1M cached tokens**, roughly 100× cheaper than raw Opus input.

Cache the **system prompt + tool defs first** — usually the biggest, most stable block.

**Sources:**
- [Anthropic — Prompt caching docs](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [Dev.to — Claude prompt caching in 2026: the 5-min TTL change](https://dev.to/whoffagents/claude-prompt-caching-in-2026-the-5-minute-ttl-change-thats-costing-you-money-4363) `[secondary]`
- [PE Collective — Cost optimization: batch + cache stacking](https://pecollective.com/tools/claude-pricing-guide/) `[analysis]`

Tags: `#claude #cost #api #caching`

**Why-it-matters:** A one-parameter change that can cut a research/agent bill 60–90%. This is the exact "I saved us $X/mo by re-reading the docs" story that lands FDE/Solutions interviews right now — and the direct counter to enterprise-side skepticism ([`01` §5](./01-big-lab-moves.md#5-token-attack)).

---

## 2. Split your long-running agent into an *initializer* + a per-session coding agent that writes to `claude-progress.txt` {#2-long-running}

**What / how:** Anthropic's engineering post on "**effective harnesses for long-running agents**" (which underpinned the SWE-bench-multi-session record) prescribes a two-agent pattern you can copy on top of the Agent SDK:

- **Initializer agent** — runs once, generates `init.sh`, an empty `claude-progress.txt`, and an initial git commit. This *is* the environment the coding agent will resume into.
- **Coding agent** — invoked every session with the rule: "make incremental progress on **one feature**, then commit with a descriptive message and append a summary to `claude-progress.txt`."

When the next session starts with a fresh context, it reads the progress file + git log to reconstruct state. This **beats naïve `--resume`** for anything running > 1 context window, and lets you `git revert` bad steps as a safety net.

**Sources:**
- [Anthropic Engineering — Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) `[primary]`
- [Anthropic Engineering — Harness design for long-running application development](https://www.anthropic.com/engineering/harness-design-long-running-apps) `[primary]`
- [VentureBeat — Anthropic multi-session Claude SDK](https://venturebeat.com/ai/anthropic-says-it-solved-the-long-running-ai-agent-problem-with-a-new-multi) `[secondary]`

Tags: `#agents #agent-sdk #claude-code #workflow`

**Why-it-matters:** This is the current SOTA pattern for autonomous coding agents. Implement it once on a portfolio project (e.g., a nightly "refactor a package" agent that runs while you sleep) and you have a concrete **context-engineering** interview talking point — separate from "I know how to prompt."

---

## 3. Save Claude Code tokens with a `PreToolUse` hook that filters test output — and move `CLAUDE.md` rules into on-demand Skills {#3-hooks}

**What / how:** Two under-used levers straight from Claude Code's official cost docs.

**(a) `PreToolUse` hook for test-output filtering.** Add a hook matching `Bash` that rewrites `npm test` / `pytest` / `go test` to pipe through:

```bash
grep -A 5 -E '(FAIL|ERROR|error:)' | head -100
```

Turns a 10K-line log into a few hundred tokens without changing the workflow. Script lives in `~/.claude/hooks/filter-test-output.sh`, wired via `settings.json`.

**(b) Trim `CLAUDE.md` to < 200 lines and push per-workflow instructions** (PR reviews, migrations, style guides) into `.claude/skills/*/SKILL.md`. Skills load **only when invoked**, so you stop paying for the PR-review playbook on every unrelated message.

Also: **prefer the `gh`, `aws`, `gcloud` CLIs over their MCP equivalents** — the MCP tool list itself costs tokens; CLI calls cost nothing until used.

**Sources:**
- [Claude Code — Manage costs effectively](https://code.claude.com/docs/en/costs) `[primary]` (includes exact hook JSON + shell script)
- [Anthropic Support — Claude Code power-user tips](https://support.claude.com/en/articles/14554000-claude-code-power-user-tips) `[primary]`
- [Anthropic — Steering Claude Code: skills, hooks, rules, subagents](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) `[primary]`

Tags: `#claude-code #cost #hooks #skills`

**Why-it-matters:** Real engineering muscle — hooks + skills are the "settings.json diff that shaves 40% off token spend" you can put in a README and show off in interviews. Directly relevant to any FDE role at Anthropic.

---

## 4. Install `ykdojo/claude-code-tips` for a context-aware status line + `/handoff` in one command {#4-plugin}

**What / how:** A single install adds a **status bar** showing model, cwd, git branch, uncommitted count, and **live token usage** (10 color themes), plus the `dx` plugin's `/handoff` skill that writes a `HANDOFF.md` **before you `/clear`** — much cleaner than trusting auto-compact. Also ships:

- `/dx:gha` — analyze failing GitHub Actions runs
- `/dx:clone` and `/dx:half-clone` — branch or trim a conversation
- a reddit-fetch skill

Run once:

```bash
claude plugin marketplace add ykdojo/claude-code-tips
claude plugin install dx@ykdojo
# or bootstrap everything (aliases + settings + status line):
bash <(curl -s https://raw.githubusercontent.com/ykdojo/claude-code-tips/main/scripts/setup.sh)
```

Pair with `/config` → **disable auto-compact** so `/handoff` is authoritative.

**Sources:**
- [GitHub — ykdojo/claude-code-tips](https://github.com/ykdojo/claude-code-tips) `[secondary]` (40+ tips + code)
- [Claude Code — Plugin marketplaces docs](https://code.claude.com/docs/en/plugin-marketplaces) `[primary]`
- [Security Boulevard — 7 Claude Code plugins worth your time (June 2026)](https://securityboulevard.com/2026/06/7-claude-code-plugins-from-the-marketplace-worth-your-time/) `[analysis]`

Tags: `#claude-code #plugins #dx #workflow`

**Why-it-matters:** Instant DX upgrade — a visible status line + explicit handoffs prevents the classic "I lost 3 hours of context to `/compact`" story. Easy demo when someone asks "so how do you actually use Claude Code?"

---

## Thursday-night recipe (60 minutes, all four together)

1. `pip install`-nothing: open `~/.claude/settings.json`, add the `PreToolUse` hook from §3.
2. `claude plugin marketplace add ykdojo/claude-code-tips && claude plugin install dx@ykdojo` (§4).
3. Trim your `CLAUDE.md` to <200 lines; move one big rules block to `.claude/skills/pr-review/SKILL.md` (§3).
4. Edit your one agent-SDK script to pass `cache_control` with `ttl: "1h"` on the system prompt (§1).
5. Log a per-session `cost` before and after, commit the diff, push to a public gist. **This is the artifact `00-tldr` "one thing to do" is asking for.**
