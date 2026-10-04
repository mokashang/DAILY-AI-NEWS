# Practical Skills & Tools — 2026-05-31

Five things shipped this week you can install or try **tonight**. The headline is **Opus 4.8 + dynamic workflows + `/effort ultracode`**, but the sneakier wins are: a **free Anthropic security plugin** that hardens every diff Claude writes, **Hamel Husain's `eval-audit` Skill** that diagnoses your eval setup in 10 minutes, **Semble MCP** for sub-second semantic code search at ~98% token savings, and **Karpathy's "render as HTML" prompt suffix** that changes how you read long AI output. Each is reversible, each is doable in <30 minutes, and each is on-thesis for the Anthropic-stack focusing decision in [`ME.md`](../ME.md).

Tags: `#claude-code #opus-4-8 #subagents #mcp #plugins #security #evals #prompting #cost-optimization`

---

## 1. Dynamic Workflows + `/effort ultracode` in Claude Code (Opus 4.8) {#1-ultracode}

**What it is:** Claude Code now writes its own orchestration scripts and **spawns tens-to-hundreds of parallel sub-agents in a single session**, then verifies each output before reporting back. Bundled with Opus 4.8 and a new `xhigh` effort tier.

**The actual recipe — tonight:**

```bash
# 1. Update Claude Code CLI (you need Opus 4.8 access — Max/Team/Enterprise/API)
claude --version  # verify ≥ 2.1.144

# 2. Inside a session, flip the new effort flag:
/effort ultracode

# 3. Or ask in natural language — Claude will emit the orchestration script:
"Create a dynamic workflow to audit this repo for SSRF vectors,
 verify each finding independently, and produce a one-page report."

# 4. Watch progress in the new Agent view; check spend with:
/usage
```

**Best for tonight:** codebase-wide bug hunts, profiler-guided optimization audits, security audits, large refactors — anything **embarrassingly parallel** where you want **independent verification on every finding**.

**Why it works:** Parallel sub-agents avoid context pollution (each verifies in a clean window). The orchestration script is **inspectable and reusable** — you can re-run a failed branch without re-doing the whole job. This is the operational version of the "harness is the model" research thread in [`04`](./04-research-progress.md).

**Cost note:** `ultracode` burns tokens. Pair with **`Opus-orchestrator + Sonnet-worker` model split** ([2026-05-22 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) and the **Semble MCP** below ([§4](#4-semble)) to claw back ~50–70% of the spend before the **June 15 Agent SDK metering** kicks in (T-15 days).

**Sources:**
- [Anthropic — Introducing dynamic workflows in Claude Code](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) `[primary]`
- [TechCrunch — Anthropic releases Opus 4.8 with new "dynamic workflow" tool](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/) `[secondary]`
- [Claude Code docs — Orchestrate subagents at scale](https://code.claude.com/docs/en/workflows) `[primary]`

Tags: `#claude-code #opus-4-8 #subagents #parallel #verification #ultracode`

---

## 2. `security-guidance` Plugin — free inline vuln review for every Claude Code edit {#2-security-guidance}

**What it is:** A free, all-plans Anthropic plugin that runs a **three-layer security review** on every file edit, model output, and commit/push Claude Code makes. Anthropic's internal testing cut **security-related PR comments by 30–40%**.

**The actual recipe — tonight (5 minutes):**

```bash
# 1. Make sure you're on Claude Code CLI ≥ 2.1.144, Python ≥ 3.8 on PATH

# 2. Inside any Claude Code session:
/plugin install security-guidance@claude-plugins-official
/reload-plugins
```

That's it. No flags. It now runs:

- **Layer 1 (every edit):** deterministic pattern match for `eval()`, `new Function()`, `os.system()`, `child_process.exec()`, `pickle.loads`, DOM injection, hardcoded secrets, etc.
- **Layer 2 (every model output):** Claude self-reviews the proposed diff against ~25 high-risk vuln classes.
- **Layer 3 (commit/push):** deeper agentic pass reads callers + sanitizers + related files before the change leaves your machine.

When it flags something, Claude **tries to fix it in the same turn** — you get a corrected diff, not a passive comment.

**Why it works:** The deterministic prefilter is cheap and catches the obvious wins; the agentic pass uses surrounding-code context that linters can't reason about. Three checkpoints means a single missed issue gets two more chances.

**Sources:**
- [Cybersecurity News — Anthropic Releases Free Security Plugin for Claude Code](https://cybersecuritynews.com/free-security-plugin-for-claude-code/) `[secondary]`
- [Help Net Security — Claude now reviews and fixes vulnerabilities as you write code](https://www.helpnetsecurity.com/2026/05/27/anthropic-claude-code-security-guidance-plugin/) `[secondary]`
- [Claude Code Docs — Catch security issues as Claude writes code](https://code.claude.com/docs/en/security-guidance) `[primary]`
- [Anthropic Plugins — Security Guidance](https://claude.com/plugins/security-guidance) `[primary]`

Tags: `#claude-code #security #plugins #appsec #free`

---

## 3. Hamel Husain's `eval-audit` Skill — diagnose your eval setup in 10 minutes {#3-eval-audit}

**What it is:** A Claude Code Skill that inspects whatever eval pipeline (or lack of one) you have and runs diagnostic checks across **six areas**: error analysis, evaluator design, judge validation, human review, labeled data, pipeline hygiene. Outputs a **prioritized punch-list**.

**The actual recipe — tonight (10 minutes):**

```bash
# Inside a Claude Code session in the repo you want to evaluate:
/plugin marketplace add hamelsmu/evals-skills
/plugin install evals-skills@hamelsmu-evals-skills

# Restart Claude Code, then run:
/evals-skills:eval-audit
```

You get back a **ranked list** of issues. Fix the top 3 before you touch your judge prompt or write a new eval. (Hamel's repeated finding: most teams have evaluator bugs that dwarf the model-quality differences they're trying to measure.)

Follow-up skills in the same plugin walk you through fixing each area: `/evals-skills:error-analysis`, `/evals-skills:judge-validation`, etc.

**Why it works:** The unsexy floor-raising work in agent evals is *error analysis* and *judge-human agreement*, not benchmark design. This Skill operationalizes the boring-but-load-bearing stuff almost nobody does properly.

**Why it matters to your portfolio:** A blog post titled **"I ran Hamel's eval-audit on a 5-week-old side project and here's what I found"** is exactly the kind of artifact OpenAI / Anthropic / Cognition recruiters now weight above pedigree (see [`05` §3 Bloomberg on hiring funnel](./05-career-and-startup.md#3-bloomberg-funnel)).

**Sources:**
- [Hamel's Blog — Evals Skills for Coding Agents](https://hamel.dev/blog/posts/evals-skills/) `[primary]`
- [GitHub — hamelsmu/evals-skills](https://github.com/hamelsmu/evals-skills) `[primary]`
- [Hamel on X — announcement](https://x.com/HamelHusain/status/2028894099483578872) `[primary]`

Tags: `#evals #claude-code #skills #hamel-husain #portfolio`

---

## 4. Semble MCP — sub-second semantic code search, ~98% fewer tokens than grep+read {#4-semble}

**What it is:** An MCP server (and CLI) that gives any coding agent — Claude Code, Cursor, Codex, OpenCode, VS Code — **semantic search over your whole codebase** using static **Model2Vec** embeddings + **BM25** + **Reciprocal Rank Fusion**. Indexes and queries a full repo in **<1 second**.

**The actual recipe — tonight (10 minutes):**

```bash
# 1. Install (no compile, no GPU needed):
pip install "semble[mcp]"
# or, no install at all:
uvx --from "semble[mcp]" semble

# 2. Register as an MCP server in Claude Code:
/mcp add semble "uvx --from 'semble[mcp]' semble" --arg <path-to-repo>

# 3. **The step most people skip**: add a Semble snippet to AGENTS.md or CLAUDE.md
#    so dynamic-workflow sub-agents (which can't call MCP directly) can shell out to it.
#    Example block to drop in:
#
#    ## Code search
#    Use `semble search "<query>"` for semantic code lookup before grep.
#    Use `semble savings` to see token reduction vs. grep+read.

# 4. After a session:
semble savings  # actual token reduction vs grep+read baseline
```

**Why it works:** Static embeddings (Model2Vec) are **~200× faster to index and ~10× faster to query** than transformer-based code embedders, at ~99% retrieval quality. Fused with BM25 to catch literal symbol matches you'd otherwise miss. Drops a ~98% token tax that grep+read currently puts on every "find me where X happens" turn.

**Pair with:** Dynamic workflows ([§1](#1-ultracode)) — every parallel sub-agent doing code lookup gets the savings, compounding fast.

**Sources:**
- [GitHub — MinishLab/semble](https://github.com/MinishLab/semble) `[primary]`
- [askGlitch — Top 5 Trending AI GitHub Repos May 2026](https://www.askglitch.com/blog/top-5-trending-ai-github-repos-may-2026) `[analysis]`
- [PyPI — semble](https://pypi.org/project/semble/) `[primary]`

Tags: `#mcp #code-search #cost-optimization #agents-md`

---

## 5. Karpathy's "Render as HTML" prompt suffix {#5-html-output}

**What it is:** A prompt suffix that makes long-form AI responses dramatically more scannable. Instead of fighting walls of Markdown, you let the model design its own UI.

**The actual recipe — tonight (1 minute):**

Append to any prompt where the answer would otherwise be a wall of text:

```
Format your entire response as a complete, self-contained HTML document with
inline CSS. Use proper headings, color-coded sections, collapsible <details>
elements for deep dives, tables for any comparisons, and a clean modern
layout with dark/light mode support.
```

Then:

```bash
claude -p "<your prompt + the suffix above>" > response.html && open response.html
```

**Best for:** research summaries, codebase walkthroughs, PR review writeups, architecture comparisons, anything with 5+ sections.

**Automate it** as a Skill — drop the suffix into `~/.claude/skills/html-output/SKILL.md` and invoke with `/html-output`.

**Why it works:** Plain Markdown collapses spatial/visual structure your brain processes for free. HTML lets the model encode hierarchy, color, and **progressive disclosure** (`<details>` collapsibles) that match how you actually read. The model can already do this — we were just asking it to whisper in monotone.

**Sources:**
- [Quasa — Enough with the Walls of Text: Karpathy's Simple Lifehack](https://quasa.io/media/enough-with-the-walls-of-text-andrej-karpathy-s-simple-lifehack-just-ask-ai-for-html) `[analysis]`
- [dsebastien.net — HTML as the New AI Output Format](https://www.dsebastien.net/2026-05-12-html-as-the-new-ai-output-format/) `[analysis]`
- [Skills Playground — karpathy-guidelines Skill (community port)](https://skillsplayground.com/skills/forrestchang-andrej-karpathy-skills-karpathy-guidelines/) `[secondary]`

Tags: `#prompting #karpathy #productivity #output-format`

---

## Honorable mentions (bookmark, not a tonight project)

- **Codex CLI Goal Mode is GA** ([OpenAI changelog](https://developers.openai.com/codex/changelog)) — multi-day autonomous coding sessions inside the Codex app / IDE extension / CLI. Closest direct analogue to Claude's dynamic workflows. `codex goal "<objective>"` with a precise completion condition.
- **AWS MCP Server is GA** ([AWS announcement, May 6](https://aws.amazon.com/about-aws/whats-new/2026/05/aws-mcp-server/)) — single MCP tool calls any AWS API + sandboxed Python execution against AWS services. Drop into Claude Code if you live in AWS.
- **Simon Willison shipped `llm-anthropic` 0.25.1** ([May 28 post](https://simonwillison.net/2026/May/28/llm-anthropic/)) — `pip install -U llm-anthropic`; supports Opus 4.7/4.8 with `thinking_effort: xhigh` and new `thinking_display` / `thinking_adaptive` knobs. Great for quick CLI experiments outside Claude Code.
- **SQLite added an AGENTS.md** ([Simon's writeup, May 27](https://simonwillison.net/2026/May/27/sqlite-agents/)) — notable because the message is "we do **not** accept agentic code, but we *do* accept agent-generated bug reports with reproducible test cases." Useful template for your own OSS contribution policy.

---

## Skill of the week

**Install `security-guidance` ([§2](#2-security-guidance)) tonight, then run `/evals-skills:eval-audit` ([§3](#3-eval-audit)) on whatever side project you're shipping.** The first hardens every diff Claude writes for free with zero workflow change; the second tells you in ten minutes whether your evals are actually measuring what you think they are. Both are reversible, both are free, and both pay for themselves the first time you'd otherwise have shipped a vuln or trusted a broken judge. Together they cover the two highest-leverage practices for an Anthropic-stack portfolio in 2026: **secure-by-default code generation** and **eval-driven iteration**.
