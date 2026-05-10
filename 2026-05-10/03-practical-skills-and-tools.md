# Practical Skills & Tools — 2026-05-10

Hands-on workflows, tools, prompting, productivity. **Pick one item from this file and act on it today.**

---

## 1. The 2026 MCP Server Setup That Actually Holds Up in Real Work

**The problem:** Most MCP setups break in production because people install 30 MCP servers, the agent's context fills up with tool descriptions, and capability degrades. The well-tested 2026 pattern is **5–6 servers max, with strict scoping**.

**The reference setup for a CS grad doing real work:**

```jsonc
// ~/.claude/settings.json (user scope — applies to every project)
{
  "mcpServers": {
    "filesystem":    { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-filesystem", "/home/user/projects"] },
    "github":        { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-github"] },
    "memory":        { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-memory"] }
  }
}

// ./.claude/settings.json (project scope — overrides for this codebase only)
{
  "mcpServers": {
    "postgres":      { "command": "uvx", "args": ["mcp-server-postgres", "postgres://localhost/dev"] },
    "playwright":    { "command": "npx", "args": ["-y", "@playwright/mcp"] }
  }
}
```

**What changes in 2026:**
- **Claude Code's MCP Tool Search** lazy-loads tool definitions, reducing context usage by ~95%. This means you can have 5+ servers configured without the "tool description bloat" that killed early MCP setups.
- **Cursor still loads all configured MCP tools at session start** — so on Cursor, keep your list shorter (3–4 max).
- Both honor the same MCP wire protocol — **server configs are interchangeable**.

**Sources:**
- [Nimbalyst — Claude Code MCP Setup: Practical 2026 Guide](https://nimbalyst.com/blog/claude-code-mcp-setup/)
- [DeployHQ — Best MCP Servers for Web Devs in 2026](https://www.deployhq.com/blog/best-mcp-servers-for-web-developers)
- [ClaudeFast — Cursor MCP Servers 2026 Setup Guide](https://claudefast.io/blog/tools/mcp-extensions/cursor-mcp-setup)
- [Steve Kinney — Popular MCP Servers for Claude Code and Cursor](https://stevekinney.com/courses/ai-development/mcp-for-claude-code-and-cursor)

**Why it matters to you:**
- **Job lens:** "I built and deployed an MCP server for [domain]" is a 2026 resume bullet that gets callbacks. Build one for your specific niche (your university course catalog, your internship's internal API, an open dataset you care about) and put it on GitHub.
- **Action this week:** Build *one* MCP server for a workflow in your life. Open-source it. Add it to your portfolio. Total time: 4 hours if you've never done it before.

---

## 2. The "Cursor as PM, Claude Code as Worker" Workflow — The Best 2026 Coding Setup

**The pattern that's now consensus among power users:**

| Role | Tool | What it does |
|---|---|---|
| **Project Manager** | Cursor (or Windsurf) | Reads the spec, breaks it into tasks, reviews diffs, tracks state |
| **Worker** | Claude Code (or Codex) | Executes one task at a time end-to-end, pushes back when blocked |

**Why this works:**
- The PM tool has the IDE context (file tree, open buffers, debugger) but limited autonomy.
- The Worker tool has full autonomy (filesystem write, command execution) but works best on focused, well-scoped tasks.
- Hand-offs happen at task boundaries — PM creates a precise prompt + acceptance criteria, Worker takes it from there.

**The "3-strike rule" for CI:** If Claude Code's PR fails CI three times in a row, **the agent stops and asks for human input**. This prevents infinite-loop debugging that wastes tokens and produces worse code.

**Practical config:**
- Use Cursor's **Composer (Agents Window)** to plan and break tasks down.
- Hand each subtask to Claude Code with `claude code --task "..."` and an acceptance test.
- Accept Claude's PR only after CI passes and the diff matches the spec.

**Sources:**
- [MCP Market — Cursor & Claude Code Workflow Guide](https://mcpmarket.com/tools/skills/cursor-claude-code-workflow-guide)
- [Composio — Cursor MCP Integration with Claude Code](https://composio.dev/toolkits/cursor/framework/claude-code)
- [KSRed — Claude Code as MCP Server Setup](https://www.ksred.com/claude-code-as-an-mcp-server-an-interesting-capability-worth-understanding/)

**Why it matters to you:**
- **Job lens:** You will be asked at every senior interview in 2026 *"how do you use AI agents in your daily workflow?"* The wrong answer: "I copy-paste into ChatGPT." The right answer: "PM/Worker handoff with Cursor and Claude Code, with a 3-strike CI rule and a `.cursorrules` file that encodes our coding standards."
- **Action this weekend:** Set up the PM/Worker split for one of your existing personal projects. Track how much human-time you save vs. solo coding. Bring those numbers to interviews.

---

## 3. The Hallucination-Eval Habit — From Vibe Code to Production Code

**The headline:** GPT-5.5 Instant cut hallucinations 52.5% on high-stakes prompts vs. GPT-5.3 Instant. **Why does that matter to you specifically?** Because hallucination measurement just became the #1 differentiator between *amateur* and *professional* AI builders.

**The minimum-viable hallucination eval pipeline (you can build this in a weekend):**

```python
# pseudo-code outline — adapt to your stack
import json

# 1. Build a "gold" Q&A set for your domain (50-200 items)
gold = json.load(open("gold.json"))

# 2. Run your AI pipeline against the gold set
results = [run_pipeline(q["question"]) for q in gold]

# 3. Score against ground truth using:
#    - Exact match for factual extraction
#    - LLM-as-judge with rubric for open-ended answers
#    - Faithfulness check: is every claim in the answer in the source?
scores = [score(r, q) for r, q in zip(results, gold)]

# 4. Track three metrics
hallucination_rate   = sum(s["hallucinated"] for s in scores) / len(scores)
faithfulness         = sum(s["faithful"]    for s in scores) / len(scores)
answer_precision     = sum(s["precise"]     for s in scores) / len(scores)
```

**Recommended free tools:**
- **`llm-eval`** (Simon Willison's) — quick CLI evals against any model
- **`promptfoo`** — YAML-based evals with cost tracking
- **`Inspect AI`** (UK AISI) — production-grade safety evals
- **`langsmith`** — if you're already in LangChain land

**Sources:**
- [OpenAI — GPT-5.5 Instant hallucination metrics](https://openai.com/index/gpt-5-5-instant/)
- [Simon Willison — llm tool releases May 2026](https://simonwillison.net/2026/May/)
- [HuggingFace — Trending Papers on Eval](https://huggingface.co/papers/trending)

**Why it matters to you:**
- **Job lens:** "I built an evaluation pipeline that caught X% of factual drift in production" is a senior-IC-level resume bullet from a new grad. It signals you understand that **shipping AI is not vibes — it's measurement**. Add this to one project before your next interview cycle.
- **Startup lens:** Your customers are starting to ask "what's your hallucination rate?" If you can show them a measured number, you win the deal. If you say "trust us," you don't.
- **Insight:** The bar for "professional AI engineer" has moved from "can call APIs" → "can build agents" → "can measure agents." Each shift takes ~12 months. We're 6 months into the third shift.

---

## 4. The "Personal Agent" Stack You Should Be Running by End of Q2

**The thesis:** A CS grad in 2026 should have **at least one personal agent running 24/7** that automates a chunk of their life. Not because the tooling demands it, but because it's the fastest way to develop intuition for what agents can/can't do — and that intuition is the highest-paid skill in the field.

**The reference stack:**

```
┌─────────────────────────────────────────────────┐
│  Trigger:  cron / webhook / email / GitHub     │
├─────────────────────────────────────────────────┤
│  Orchestrator: LangGraph or n8n with MCP        │
├─────────────────────────────────────────────────┤
│  LLM Router:  LiteLLM → {Claude / GPT / Kimi}   │
├─────────────────────────────────────────────────┤
│  Memory:    Mem0 graph memory + sqlite          │
├─────────────────────────────────────────────────┤
│  Tools:     fs, github, email, calendar, web    │
├─────────────────────────────────────────────────┤
│  Logging:   Langfuse or Helicone                │
└─────────────────────────────────────────────────┘
```

**Concrete starter projects (pick one, ship by next weekend):**
1. **Job-hunt agent** — every day, read [speedyapply/2026-AI-College-Jobs](https://github.com/speedyapply/2026-AI-College-Jobs), filter to your criteria, draft tailored cover letters, post a Slack/Telegram notification. ~6 hours to build.
2. **arXiv reading agent** — every morning, scan arXiv cs.AI/cs.LG/cs.CL new papers, score for relevance, summarize the top 3 in your inbox. ~4 hours.
3. **Repo health agent** — runs hourly on your projects, identifies stale dependencies, drafts PRs that update them, notifies you. ~5 hours.
4. **Internship recruiter agent** — monitors recruiter LinkedIn DMs, drafts a contextual reply for you to approve, schedules calendly slots. ~8 hours, but high impact.

**Sources:**
- [LangGraph documentation](https://langchain-ai.github.io/langgraph/)
- [Mem0 paper](https://arxiv.org/abs/2504.19413)
- [LiteLLM documentation](https://docs.litellm.ai/)
- [n8n-MCP integration](https://aitoolly.com/ai-news/article/2026-05-06-n8n-mcp-a-new-model-context-protocol-tool-for-building-n8n-workflows-via-claude-desktop-and-cursor)

**Why it matters to you:**
- **Job lens:** Walking into an interview and saying "I have an agent that's been running for 3 months and has [done X, saved me Y hours]" is the single most underrated answer to "tell me about a project." It demonstrates: agentic intuition, ops literacy, persistence, and judgment about *what's worth automating*.
- **Startup lens:** Your first product idea will probably come from running personal agents. Half of the YC W26 batch's vertical-agent startups started as personal automations the founders kept extending. **Build for yourself first.**
- **Insight:** The compounding effect of having a personal agent stack is *exponential*. Month 1: it saves 1hr/week. Month 6: it saves 10hr/week. Month 12: you don't remember life before it. Start now.

---

## 5. Prompting in 2026 — The Six Things That Still Move the Needle

Most "prompt engineering" advice is now obsolete, but these six techniques *do* still measurably improve output quality on Claude Opus 4.7, GPT-5.5, and Gemini 3.1 Pro:

1. **Role + audience + format upfront.** "You are an expert X writing for Y in format Z." Still works in 2026 — recent Anthropic eval shows 8–15% accuracy lift.
2. **Force a thinking step.** For Claude: prepend `<thinking>` block. For GPT-5.5: use the `reasoning` parameter or just say "Think step by step before answering." Reasoning models do this internally, but for non-reasoning calls (which are most of your high-volume use cases), it still matters.
3. **Few-shot examples for format.** When you need a specific JSON shape or tone, give 2–3 examples. Beats any system-prompt instruction.
4. **Explicit failure modes.** "If you don't know, say 'I don't know'. If the answer requires data you don't have, say what data you'd need." Cuts hallucination measurably.
5. **Self-critique pass.** "Now review your answer. Identify any errors or ungrounded claims. Provide a corrected final version." Adds latency but reliably improves accuracy on hard tasks.
6. **Tool over prompt.** If you find yourself writing a 2,000-word system prompt, you probably need a tool (function calling, MCP server, retrieval) instead. Prompts handle *style*. Tools handle *facts*.

**Sources:**
- [Ethan Mollick — One Useful Thing: An Opinionated Guide to Using AI Right Now](https://www.oneusefulthing.org/p/an-opinionated-guide-to-using-ai)
- [Ethan Mollick — 15 times to use AI, 5 not to](https://www.oneusefulthing.org/p/15-times-to-use-ai-and-5-not-to)
- [Simon Willison — How I use LLMs to help me write code](https://simonw.substack.com/p/how-i-use-llms-to-help-me-write-code)
- [Anthropic — Claude prompting docs](https://docs.anthropic.com/)
- [OpenAI — prompting guide for GPT-5 family](https://platform.openai.com/docs/guides/prompt-engineering)

**Why it matters to you:**
- **Action this week:** Take any prompt you currently use regularly. Add **#4 (explicit failure modes)** and **#5 (self-critique pass)**. Measure the difference. You'll see 10–20% fewer mistakes immediately.
- **Insight:** The "prompt engineering" hype was always overblown — what matters is **how you compose prompts with tools, retrieval, and evals**. That stack is the actual skill, and it's what 2026 employers test for in interviews.

---

## ACTION TODAY (pick exactly one)

- [ ] Set up the 5-server MCP config above and test it on one workflow.
- [ ] Pair Cursor (PM) + Claude Code (Worker) for one feature on a personal project.
- [ ] Build a 50-item gold-set evaluation pipeline for one of your existing AI projects.
- [ ] Ship the smallest possible "personal agent" — even just an arXiv summary in your inbox.
- [ ] Take one of your existing prompts and add explicit-failure-mode + self-critique. Measure the delta.
