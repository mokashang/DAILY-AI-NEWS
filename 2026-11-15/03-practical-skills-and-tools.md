# Practical Skills & Tools — 2026-11-15

**One real Sunday afternoon of focused work can produce three portfolio artifacts this week.** The releases below are all small, actionable, and composable: Claude Code 2.1.295/2.1.304 added **`InstructionsLoaded` hook** + a **32-skill preload cap** + a **1024-hooks-per-source safety ceiling**; the **MCP 2026-07-28 spec** is now stable with **TypeScript SDK 2.4.0** and Ruby 1.2.0 shipping full support; **LangGraph 1.2.20 introduced strict resume** that rejects stale interrupt answers (a nasty HITL race-condition fix); **Simon Willison's `llm` 0.37.2** shipped a security patch — **upgrade today** if you've ever run `llm openai endpoint add`; and **Antigravity 2.0** hardened the "sandboxed agent + reasoning + tools + code exec in one API call" primitive. Pair with a prompt-caching audit on one real project and you have three concrete résumé lines by Sunday 10pm.

Tags: `#claude-code #mcp #langchain #langgraph #llm #antigravity #vibe-coding #cost #caching #security`

---

## 1. Claude Code 2.1.295 / 2.1.304 — new `InstructionsLoaded` hook, 32-skill preload cap, 1024-hooks-per-source ceiling {#1-claude-code}

**What changed:**
- **2.1.295 — Subagent skills preload cap** = 32 skills per `skills:` field (the rest remain invokable via the Skill tool). Fix if your `.claude/skills/` sprawl is >32.
- **2.1.304 — Per-source hook cap** = 1,024 hooks per session per source (one repo, one plugin, one user folder). Prevents a runaway plugin from eating your session.
- **New hook event: `InstructionsLoaded`** — fires when `CLAUDE.md` or `.claude/rules/*.md` loads into context. **The missing hook for repo-wide context injection.**
- **Scheduled tasks + `/loop`** now prompt before running a skill with `allowed-tools` or `hooks` unless you pre-approve via `permissions.allow` → `Skill(name)`. Pre-approve the skills you run on a cron.
- **Subagent truncation fix:** subagents hitting the output limit are re-asked for a shorter complete answer instead of returning a truncated tail.

**Sources:**
- [Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Releasebot — Claude Code updates](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### How to use TODAY

1. **Write one skill with `allowed-tools: [Bash, Grep]`** that scans the repo for TODOs and surfaces the newest 10 to the agent on startup. 15 min.
2. **Write one `InstructionsLoaded` hook** that injects today's `TODAY.md` into every session — classic "today's goals" context injection. 10 min.
3. If you use scheduled tasks or `/loop`, update `.claude/settings.json` → `permissions.allow` → `["Skill(safe-shipper)", "Skill(todo-scan)"]`. 5 min.
4. Audit your `.claude/skills/` directory — if >32, split into plugin-scoped namespaces.

**Résumé line draft:** *"Wrote an `InstructionsLoaded` hook + 3-skill agent config that cut context-setup time for a 40K-LOC repo by ~80%; see <repo link>."*

---

## 2. MCP spec revision 2026-07-28 is stable — TypeScript SDK 2.4.0 ships Skills-over-MCP {#2-mcp-2026-07-28}

**What changed:**
- **Spec revision 2026-07-28** removes protocol-level session tracking — each request carries its own protocol version + client capabilities. Everything ≤2025-11-25 is now "legacy." This is the **biggest change since OAuth**.
- **Nov 11 — "More Predictable Release Cycle for MCP"** post on the MCP blog + published roadmap for the next revision.
- **TypeScript SDK 2.4.0**: **Skills over MCP** (expose Claude Skills as MCP tools) + opt-in OAuth refresh scopes + improved server event forwarding.
- **Ruby mcp gem 1.2.0** completes 2026-07-28 revision support.
- **MCP connectivity for Microsoft 365 Copilot** announced Nov 12 (Arctera governance layer).
- **MCP blog Nov 10:** early extension for file transfer between clients and tools.

**Sources:**
- [MCP blog](https://blog.modelcontextprotocol.io/) `[primary]`
- [Spec version tracker](https://nhimg.org/mcp-spec-version-tracker) `[aggregator]`

### How to use TODAY

1. **Scaffold a fresh MCP server on TS SDK 2.4.0** — one "Skills over MCP" tool, one data-fetch tool, one write tool. 90 min.
2. **Add a 5-case eval harness** (success criteria per tool, red/green in CI). 30 min.
3. **README + demo gif** — the gif is the hireability lever; record with `asciinema` or `vhs`. 30 min.
4. **Publish to GitHub + tweet thread tagging @simonw + the MCP blog**. Free distribution.

**This is still the #1 FDE portfolio artifact.** Yesterday's edition said the same thing — because it's still true, and 2.4.0 just made it 2× faster to ship.

**Résumé line draft:** *"Shipped a production MCP server (3 tools, 5-case eval, demo gif) on TS SDK 2.4.0 — <repo link>; benchmarked at <X> RPS with <Y>ms p95 latency."*

---

## 3. LangGraph 1.2.20 — strict resume mode (rejects stale HITL answers), LangChain 1.5.0 drops Python 3.10 {#3-langchain-langgraph}

**What changed:**
- **LangGraph 1.2.20 (Nov 5):** unique ID per interrupt call + **strict resume mode** that rejects stale answers — closes a real class of HITL race bugs where a late human answer merges into a state that has moved on.
- **LangGraph 1.2.21 (Nov 12):** subgraph namespace fix + security dep bumps.
- **LangGraph 1.2.22 (Nov 14):** on PyPI; release notes not yet surfaced — **pin cautiously until notes land**.
- **LangChain 1.5.0 + langchain-core 1.8.0 (Nov 11):** both **drop Python 3.10 support**. Plan migration if still on 3.10.
- **@langchain/langgraph 1.7.2 on npm** (secondary tracker; verify).

**Sources:**
- [LangGraph GitHub releases](https://github.com/langchain-ai/langgraph/releases) `[primary]`
- [LangChain changelog](https://docs.langchain.com/oss/python/releases/changelog) `[primary]`
- [PyPI langgraph](https://pypi.org/project/langgraph/) `[primary]`

### How to use TODAY

1. If your HITL agent is on **<1.2.20**, upgrade and flip interrupts to **strict resume mode** (one param). Prevents the "stale answer merges into live state" bug — rare but ugly.
2. If you're on **Python 3.10**, pin `langchain-core<1.8` or migrate before Dec 1. Prefer migration — 3.10 reached EOL Oct 2026.
3. Publish a 20-line HITL demo (approvals on writes only) and post it. This is a durable portfolio artifact — the LangChain team will often retweet quality demos.

**Résumé line draft:** *"Migrated a production HITL agent from LangGraph 1.1.x to 1.2.20 strict-resume mode; eliminated a class of race-condition bugs in multi-reviewer workflows; demo at <repo link>."*

---

## 4. Simon Willison's `llm` 0.37.2 — SECURITY FIX, upgrade now {#4-llm-0-37-2}

**What changed:**
- **`llm` 0.37 (Nov 2):** ~2 months of accumulated features; embeddings now handle **different content types** (multimodal embeddings). Fixes from 12 authors — "almost all AI-assisted."
- **`llm` 0.37.1 (Nov 3):** follow-up patch.
- **`llm` 0.37.2 (Nov 11):** **SECURITY FIX** for 2 CVE-class issues — an unknown endpoint could receive a configured OpenAI API key. **Upgrade immediately if you ever ran `llm openai endpoint add`.**
- **`llm-anthropic` 0.31 (Nov 9):** adds Claude Fable 5.2 support. Install: `llm install -U llm-anthropic`.
- **`llm-gemini` 0.36 (Nov 10)**.
- **`datasette-llm` 0.1a11 (Nov 14):** `llm`-powered SQLite queries.

**Sources:**
- [llm 0.37 — Simon Willison](https://simonwillison.net/2026/Nov/2/llm/) `[primary]`
- [llm-anthropic 0.31](https://simonwillison.net/2026/Nov/9/llm-anthropic/) `[primary]`
- [Simon Willison — llm tag](https://simonwillison.net/tags/llm/) `[primary]`

### How to use TODAY (the 5-minute version, then the 90-minute version)

**5-minute:**
```bash
pip install -U 'llm[anthropic]' llm-gemini
llm keys set anthropic
llm -m claude-fable-5.2 "quick check"
```

**90-minute "three pipe-native workflows":**
```bash
git log --since="1 week" | llm "write release notes as bullets, tag breaking changes"
cat errors.log | llm -m claude-fable-5.2 "triage; propose 3 fixes with code"
llm embed-multi resume ~/resume.md ~/jd-folder/*.md  # FDE-fit scoring corpus
```

Writeup that scores: *"3 pipe-native `llm` workflows I use daily (git-log → release notes, errors → triage, embeddings-for-FDE-fit)"* with before/after cost math. Publish, tag @simonw — he often amplifies quality posts.

**Résumé line draft:** *"Built a daily `llm`-based workflow stack (release notes, triage, FDE-fit scoring via embeddings) that replaced ~60 min/day of manual work — <blog link>."*

---

## 5. Prompt caching + cost hygiene — the operator playbook (NVIDIA earnings week is the right moment) {#5-prompt-caching}

**The numbers that matter:**
- **Cache TTL in Claude Code ≈ 5 minutes.** A follow-up prompt costs **~2¢ on cache hit vs ~12¢ on cache miss** after a short idle gap — **6× swing**.
- **Prefix stability is the lever.** System prompt + file context FIRST (cacheable prefix), volatile instructions LAST. Do NOT change reasoning-effort mid-session — it breaks caching.
- **Output tokens cost 2–5× input.** Once caching cuts input, limit output: `"No explanations"`, `max_tokens`, format constraints.
- **Metric that matters:** final $ per accepted work unit (merged commit, shipped feature), **NOT cache hit rate**. 90% hit with 3× retries is worse than 60% with one shot.
- `.cursorignore` / `.claude/.gitignore` hygiene: exclude `node_modules/`, `build/`, `dist/`, `.venv/`.

**Sources:**
- [Flavio Copes — Agent prompt caching](https://flaviocopes.com/agent-prompt-caching/) `[analysis]`
- [AI Cost Estimator — Deep-agent caching 41–80%](https://ai-cost-estimator.com/blog/prompt-caching-deep-agents-cut-token-cost-41-80-percent) `[analysis]`

### How to use TODAY

1. **Pick one real Claude Code project** you actually use (not a toy).
2. Run `/cost` mid-session; screenshot the baseline numbers.
3. **Move system prompt to the top of `CLAUDE.md`**; add 10 `.claude/ignore` rules.
4. Keep agent sessions alive during focused work; start a **new session per *task***, not per *message*.
5. Re-run `/cost` after 60 min of normal work; screenshot and diff.
6. Write a 500-word "I cut Claude Code cost on a real project by X%" post with before/after screenshots.

**Résumé line draft:** *"Audited a 40K-LOC Claude Code project; reduced token spend ~55% via prefix stability + `.claude/ignore` rules; wrote up at <blog link>."* Caption with NVIDIA earnings Monday: *"The $40B/GW Rubin number means every token matters — here's how I squeezed one real project 55%."*

---

## 6. IDE AI — Zed 1.27.0 stable, Antigravity 2.0 hardens the managed-agent primitive {#6-ide-ai}

**What shipped:**
- **Zed 1.27.0 (Nov 4):** current recommended free Rust-native editor.
- **Google Antigravity 2.29.0 / Antigravity 2.0 (Nov 3):** the "sandboxed agent + reasoning + tools + code exec, one API call" bundle hardened from I/O; ADK 2.0 under the hood.
- **Cursor** latest publicly listed = 3.1 (April 2026); Agents Window runs up to 8 parallel agents. **Verify newer builds on cursor.com — many comparison blogs are stale.**
- **Windsurf** → **Devin Desktop** post-Cognition acquisition ($250M). Windsurf Pro $20/mo. Rebranding has muddied feature tracking; if you rely on Windsurf, check feature parity before migrating.

**Sources:**
- [Zed Wikipedia](https://en.wikipedia.org/wiki/Zed_(text_editor)) `[secondary]`
- [Google Antigravity Wikipedia](https://en.wikipedia.org/wiki/Google_Antigravity) `[secondary]`
- [Cursor Wikipedia](https://en.wikipedia.org/wiki/Cursor_(code_editor)) `[secondary]`

### How to use TODAY

1. Run through **Antigravity 2.0's Managed Agents quickstart** — this is the **Google / Vertex analog to Anthropic Managed Agents**. FDE candidates who can compare both get interviews.
2. Run one small feature end-to-end in **Zed 1.27.0** to understand the free native alternative — useful for recommending-vs-Cursor conversations in interviews.
3. Skip Devin Desktop unless you have a specific need; the rebrand is still settling.

**Résumé line draft:** *"Built a Managed Agents proof-of-concept comparing Anthropic (self-hosted option) and Antigravity 2.0 (ADK 2.0); 1-page writeup of trade-offs for enterprise prospects at <blog link>."*

---

## This weekend's ship list (ranked by leverage)

1. **MCP server on TS SDK 2.4.0 with Skills-over-MCP** (§2) — 2–3 hrs, #1 FDE portfolio artifact.
2. **`llm` 0.37 pipe-native workflows writeup** (§4) — 90 min, Simon Willison amplification possible.
3. **Prompt-caching audit of one real project** (§5) — 90 min, directly cite NVIDIA earnings Monday for timeliness.

Optional stretch:
4. **`InstructionsLoaded` hook + skill combo** (§1) — 25 min.
5. **Antigravity 2.0 vs Anthropic Managed Agents comparison memo** (§6) — 60 min.

**Target:** three shippable artifacts by Sunday 10pm, one tweet thread + one blog post + one GitHub repo. That's three distinct FDE/applied-AI résumé lines added in 48 hours.
