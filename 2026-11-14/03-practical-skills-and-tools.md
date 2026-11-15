# Practical Skills & Tools — 2026-11-14

Hands-on wins you can run before Friday. The common thread this cycle: **the agent tooling has matured past the demo stage.** Claude Code 2.1's skill-and-hook system is stable enough to ship, Simon Willison just cut a fresh `llm` CLI release with reasoning traces, the MCP spec landed a **stateless redesign** that makes servers actually scalable, LangChain shipped **per-call human-in-the-loop interrupts**, and the community has converged on a **"tests-as-spec"** pattern that keeps vibe coding from eating production. Pick one, run the 5-minute test, keep what works.

Tags: `#practical #tools #claude-code #mcp #llm-cli #langchain #agent-patterns #vibe-coding`

---

## 1. Claude Code 2.1.318 — hot-reload skills + `/plan` shortcut {#1-claude-code-2-1-318}

**Date:** v2.1.318 shipped **Nov 3, 2026** (2.1.308–2.1.318 covers Oct 22 → Nov 3). The 2.1 line launched Jan 7, 2026, but the Oct/Nov patches make skills usable without restart churn.

**What it is:** Claude Code's `~/.claude/skills/` and `.claude/skills/` folders are now **hot-reloaded in-session** — edit a `SKILL.md` and it's live on the next turn. Combined with **`/plan`** (type it inline, no permission prompt needed) and **SubagentStart/SubagentStop** hook events, you can build a repo-scoped assistant that plans before it edits and refuses certain tool calls automatically. v2.1.308+ also adds `ultrathink` at `xhigh`, subagent effort control, and `claude -p` exit codes for CI.

**Try it in 5 minutes:**
```bash
mkdir -p .claude/skills/safe-shipper
cat > .claude/skills/safe-shipper/SKILL.md <<'EOF'
---
name: safe-shipper
description: Enforce plan-before-edit on this repo. Use for any code change.
---
Before editing, state the files you'll touch and the test you'll run.
Refuse to touch migrations or env files without explicit confirmation.
EOF
claude            # start session
> /plan add a /healthz endpoint and a test for it
```
Edit the `SKILL.md` mid-session, send another message — the new instructions take effect immediately, no restart.

**Sources:**
- [Claude-World — What's New in Claude Code: November 2026 (v2.1.308–2.1.318)](https://claude-world.com/articles/claude-code-november-2026-whats-new/) `[tier-2]`
- [paddo.dev — Claude Code 2.1: 109 CLI changes](https://paddo.dev/blog/claude-code-21-pain-points-addressed/) `[tier-2]`
- [VentureBeat — Claude Code 2.1.0 arrives](https://venturebeat.com/orchestration/claude-code-2-1-0-arrives-with-smoother-workflows-and-smarter-agents) `[tier-1]`
- [Official Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`

### Why it matters to you

- **Job lens:** A versioned `.claude/skills/` folder in the repo is the cleanest way to encode **team conventions** (test command, migration policy, review checklist). It shows up in PRs, reviewers can read it, new hires get the same assistant behavior as seniors. **A PR that adds a well-designed skill file to the repo reads as senior engineering** — very interview-worthy.
- **Startup lens:** Skills + hooks let one engineer run **three parallel subagents on distinct features without each going off the rails** — SubagentStop hooks can run `pytest -x` and block a merge-candidate branch from committing on red. This is the leverage that lets a solo founder outship a 5-person team.
- **Insight:** The "prompt in a system prompt" era is ending. **Reusable, file-backed, hot-reloadable instructions are the actual interface to agentic coding** — treat them like code (lint, review, version) not like a chat.

---

## 2. Simon Willison's `llm` 0.37 — reasoning traces + server-side tools {#2-llm-0-37}

**Date:** **Nov 2, 2026** release post on simonwillison.net; ~2 months of accumulated features + fixes.

**What it is:** `llm` is a Python CLI/library that treats every model (OpenAI, Anthropic, Gemini, local Ollama/GGUF) as a uniform shell-pipeable tool. 0.37 adds first-class support for **reasoning traces**, OpenAI Responses API, server-side tools, smarter logging, and (per the Oct 23 companion post) **accurate token accounting** that includes tool calls, system prompts, and reasoning tokens. There's also a plugin ecosystem (`llm install llm-tools-...`) so you **compose** capabilities instead of writing glue.

**Try it in 5 minutes:**
```bash
pipx install llm                          # or: uv tool install llm
llm keys set anthropic                    # paste key
llm -m claude-opus-4-7 "summarize $(cat README.md)"

# log everything with reasoning traces
llm logs                                  # SQLite db of every call

# chain with Unix tools
git diff | llm -m claude-opus-4-7 "write a conventional commit message"

# tool use
llm install llm-tools-datasette
llm -T "datasette:https://my.db" "which 3 users spent most last month?"
```

**Sources:**
- [Simon Willison — LLM 0.37 release post (Nov 2, 2026)](https://simonwillison.net/2026/Nov/2/llm/) `[primary]`
- [Simon Willison — llm-tool-use tag feed](https://simonwillison.net/tags/llm-tool-use/) `[primary]`

### Why it matters to you

- **Job lens:** Interviewers notice candidates who treat the LLM as **a pipe, not a chatbox**. `git log | llm 'draft release notes'` in a cover letter demo beats another LangChain-wrapper repo.
- **Startup lens:** `llm logs` becomes a **zero-cost usage/accuracy dataset**. When a customer complains, you grep the SQLite, replay the exact prompt against a newer model, and diff reasoning traces — **eval infra for free**.
- **Insight:** CLI-native LLM use **composes with everything that already exists** (cron, Make, GitHub Actions). Any workflow you can describe in a pipe, you can deploy today.

---

## 3. MCP 2026-07-28 stateless spec + FastMCP — ship your own server in an afternoon {#3-mcp-fastmcp}

**Date:** Spec version **`2026-07-28`** is the current baseline through Nov 2026; **FastMCP** tutorials remain the lowest-friction path.

**What it is:** The MCP spec was redesigned to be **stateless** — the old session-handshake model that made servers painful to scale is gone, and the four major SDKs ship it out of the box. **FastMCP** (Python) turns a server from hundreds of lines of boilerplate into **a decorator on a function**. Any MCP-capable client (Claude Code, Cursor, Zed, Continue) can plug it in.

**Try it in 5 minutes:**
```bash
pip install fastmcp
cat > server.py <<'EOF'
from fastmcp import FastMCP
import subprocess

mcp = FastMCP("repo-tools")

@mcp.tool()
def git_log(n: int = 10) -> str:
    """Return the last n commits in this repo."""
    return subprocess.check_output(
        ["git", "log", f"-n{n}", "--oneline"], text=True
    )

if __name__ == "__main__":
    mcp.run()          # stdio transport, auto-registers tool schema
EOF
# Register with Claude Code
claude mcp add repo-tools -- python /abs/path/server.py
# In session:
> use repo-tools to show the last 5 commits
```

**Sources:**
- [Tech-Insider — How to Build an MCP Server with Python: FastMCP Tutorial (2026)](https://tech-insider.org/how-to-build-mcp-server-python-fastmcp-tutorial/) `[tier-2]`
- [DEV — Build an MCP Server with TypeScript — 2026 Tutorial](https://dev.to/jangwook_kim_e31e7291ad98/build-an-mcp-server-with-typescript-2026-tutorial-1ipk) `[tier-2]`
- [DEV — Building Your First MCP Server in Python (2026)](https://dev.to/elysiumquill/building-your-first-mcp-server-in-python-a-practical-2026-guide-4dap) `[tier-2]`

### Why it matters to you

- **Job lens:** An MCP server that wraps your company's internal API is the modern "write a script that automates my job" — and because **it plugs into whatever agent the team uses**, the ROI is visible on day one. **This is the #1 portfolio artifact for FDE applications.**
- **Startup lens:** Instead of selling an "AI app," ship an **MCP server**. Users keep their preferred client (Claude Code, Cursor, ChatGPT desktop), your distribution surface quintuples, and the stateless spec means you can scale it like any REST service.
- **Insight:** **MCP is becoming the USB-C of AI tooling.** Writing a server is now cheaper than writing a CLI — don't wrap your API in LangChain tools, wrap it in MCP.

---

## 4. LangChain 1.4.9 — per-call Human-in-the-Loop interrupts {#4-langchain-1-4-9}

**Date:** `langchain 1.4.9` shipped **Nov 4, 2026** (1.4.8 on Nov 2; 1.4.6 on Oct 14 is where **opt-in per-call HITL interrupts** landed in the middleware).

**What it is:** LangGraph/LangChain's `HumanInTheLoopMiddleware` now supports **per-call interrupts** — you can mark specific tool calls (e.g., "send email", "run SQL that writes") to pause the agent and wait for a reviewer, **without routing every call through approval**. 1.4 also bakes in built-in MCP + node timeouts; 1.4.9 adds **standardized model-refusal content blocks** so you can detect and route refusals explicitly. *Heads up: Python 3.10 support drops in `langchain-core` 1.8.0 / `langchain` 1.5.0.*

**Try it in 5 minutes:**
```python
# pip install -U "langchain>=1.4.9" "langgraph>=1.2" langchain-anthropic
from langchain.agents import create_agent
from langchain.agents.middleware import HumanInTheLoopMiddleware
from langchain_core.tools import tool

@tool
def send_email(to: str, body: str) -> str:
    """Send an email."""
    return f"sent to {to}"

@tool
def read_inbox() -> str:
    """Read recent emails."""
    return "..."

agent = create_agent(
    model="anthropic:claude-opus-4-7",
    tools=[send_email, read_inbox],
    middleware=[HumanInTheLoopMiddleware(
        interrupt_on={"send_email": True},   # pauses only on writes
    )],
)
# Resume with human decision:
#   agent.invoke(..., config={"configurable": {"approve": True}})
```

**Sources:**
- [LangChain docs changelog](https://docs.langchain.com/oss/python/releases/changelog/index.html) `[primary]`
- [Developers Digest — LangChain + LangGraph in Late 2026](https://www.developersdigest.tech/blog/langchain-langgraph-whats-new-2026) `[secondary]`
- [LangChain — October 2026 newsletter](https://langchain.com/blog/october-2026-langchain-newsletter) `[primary]`

### Why it matters to you

- **Job lens:** "Approvals on dangerous tool calls only" is the exact **risk-control pattern enterprise buyers ask about**. Demoing it in a 20-line snippet reads as senior.
- **Startup lens:** Per-call HITL is **how you charge enterprise prices** — the guardrails are the product, and they're now one middleware line.
- **Insight:** **Agent reliability stopped being a prompting problem and became a control-plane problem.** Interrupts, timeouts, and typed refusal blocks are where accuracy actually comes from in 2026.

---

## 5. The "tests-as-spec" vibe-coding pattern {#5-tests-as-spec}

**Date:** Pattern crystallized across **Oct–Nov 2026** write-ups; most mature description in the Vonage, SitePoint, and SE-ML "Pattern Language for Agentic Coding" posts.

**What it is:** Instead of prompting the agent to "write feature X," **you (the human) write the failing test**, then hand it to the agent and say "make this green without changing the test." The test is the spec; the agent iterates with `run_tests` in a loop; a **SubagentStop hook or CI gate blocks on red**. This neutralizes the biggest failure mode of vibe coding — **unverifiable agent output** — while preserving the speed.

**Try it in 5 minutes:**
```bash
# 1. Human writes the test
cat > tests/test_slugify.py <<'EOF'
from app.utils import slugify
def test_basic():          assert slugify("Hello World") == "hello-world"
def test_unicode():        assert slugify("Café Noël")   == "cafe-noel"
def test_collapse_dashes():assert slugify("a -- b")      == "a-b"
EOF

# 2. Hand it to the agent with a tight contract
claude <<'EOF'
Implement app/utils.py:slugify so tests/test_slugify.py passes.
Rules: do not modify the test file. Run `pytest tests/test_slugify.py -x` after each edit.
Stop as soon as all tests pass.
EOF
```
Add `.claude/hooks/subagent-stop.sh` that runs `pytest --maxfail=1` and exits non-zero on red — the agent **cannot claim done on a failing suite**.

**Sources:**
- [SE-ML — Towards a Pattern Language for Agentic Coding](https://se-ml.github.io/blog/2026/agentic-patterns/) `[primary]`
- [Vonage — Beyond Vibe Coding: Best Practices 2026](https://developer.vonage.com/en/blog/beyond-vibe-coding-best-practices-2026) `[tier-2]`
- [SitePoint — Vibe Coding in 2026: The Structured Guide](https://www.sitepoint.com/vibe-coding-2026-the-structured-guide-to-aifirst-development/) `[tier-2]`
- [DEV — 5 vibe-coding workflows that ship production code (2026)](https://dev.to/dohkoai/5-vibe-coding-workflows-that-actually-ship-production-code-in-2026-1nmn) `[tier-2]`

### Why it matters to you

- **Job lens:** In code-review and system-design loops, **"I write the tests, the agent writes the code, CI gates the merge"** is a story that signals **judgment, not hype**.
- **Startup lens:** Writing tests first costs 15 minutes and lets a single engineer parallelize three agents on three features overnight **without waking up to a graveyard of broken PRs**.
- **Insight:** The useful definition of "senior engineer" in 2026 is **"the person who can write the test that defines done."** Specs and tests are leverage on agent output — everything else is vibes.
