# Practical Skills & Tools — 2026-06-18

Act-on-this-today section. Two artifacts to ship this week, one habit to install.

Tags: `#claude-code #skills #hooks #plan-mode #productivity #subagents #cost #orchestration #mcp #practical`

---

## 1. The 2026 Claude Code stack, named and ordered — adopt this tonight {#1-claude-code-stack}

The state-of-practice for Claude Code has converged onto a five-layer discipline. Treat this as the **default project setup** for every new repo you touch.

**The stack (apply top-down):**

1. **`CLAUDE.md` at repo root** — your tech stack, project structure, coding conventions, workflow rules. The single biggest one-time quality lift. (Karpathy's template still works; drop it into every project.)
2. **Plan Mode for any multi-file change** — Claude reads, asks, and **does not write** until you've reviewed the spec. The overhead is real (~5 min on a small change, ~20 min on a meaningful refactor) and **prevents the "20 minutes confidently solving the wrong problem"** failure mode. Required for unfamiliar code or architectural decisions.
3. **Skills** (`SKILL.md` files in `.claude/skills/`) — folder-based, reusable workflows. **Progressive-disclosure architecture:** YAML frontmatter always loaded → SKILL.md body loaded when relevant → referenced files navigated only when needed. Token-efficient by design. **Recent June 2026 update:** skills in nested `.claude/skills` dirs load when working on files in that dir; on a name clash, the nested skill appears as `<dir>:<name>` so both stay available.
4. **Hooks** for anything that must run *every time, zero exceptions* — formatters, linters, security scans, secret detection. Hooks are deterministic; `CLAUDE.md` instructions are advisory. Use the right tool for each.
5. **Tests as external ground truth** — without tests, Claude verifies its work using its own (degrading) judgment as context fills. With tests, each red-to-green cycle is unambiguous feedback. Make `pytest -x` or equivalent the first command in any plan.

**Sources:**
- [Claude Code Best Practices (Anthropic docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Builder.io — 50 Claude Code Tips and Best Practices For Daily Use](https://www.builder.io/blog/claude-code-tips-best-practices) `[secondary]`
- [SmartScope — Claude Code Advanced Best Practices: 11 Practical Techniques for Hooks, Subagents & Context Management [2026]](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [F22 Labs — Claude Code Tips: 10 Real Productivity Workflows for 2026](https://www.f22labs.com/blogs/10-claude-code-productivity-tips-for-every-developer/) `[analysis]`
- [KDnuggets — Anthropic's Complete Guide to Claude Skills Building](https://www.kdnuggets.com/anthropics-complete-guide-to-claude-skills-building) `[secondary]`
- [MarkTechPost — Claude Code Guide 2026: 25 Features with Examples + Demo (June 14)](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[secondary]`
- [InfoQ — Claude Code Adds Dynamic Workflows for Parallel Agent Coordination](https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/) `[secondary]`

### Why it matters to you

- **Job lens:** If you're interviewing for Solutions Engineer / FDE / AI Integration roles at frontier labs or AI-application companies, **the interviewer expects you to use this vocabulary.** "I drop a `CLAUDE.md` in every repo, use Plan Mode for cross-file changes, convert repeating workflows into `SKILL.md` files, gate must-run actions through hooks, and use tests as ground truth." That sentence — said unprompted in a behavioral interview — moves you from *"I use Claude"* to *"I architect with Claude."* It's the same upgrade as "I use Git" → "I use trunk-based development with conventional commits." The vocab is the credential.
- **Startup lens:** The discipline is sellable as a product. **A "Claude Code project starter" template SaaS** — auto-generates `CLAUDE.md` from repo analysis, scaffolds standard skills, installs hook-gated formatters, drops in a baseline test runner — is a wedge for the SMB / vertical-vibe-coder segment. Customer Discovery target: solopreneurs and 2–10 person startups who Want Claude Code But Don't Know How.
- **Insight:** This stack is the **fastest-evolving "best practice"** in software engineering right now — what was canonical in March 2026 (just Plan Mode + CLAUDE.md) is now *insufficient* in June (you also need Skills + hooks). Re-evaluate the stack monthly; **don't lock your portfolio to a stale version.**

→ Cross-link: [`05` §4 the SKILL.md portfolio artifact](./05-career-and-startup.md#4-skill-artifact).

---

## 2. The multi-provider comparison harness — build it this week, publish 24hrs after GPT-5.6 lands {#2-comparison-harness}

GPT-5.6 is the next 2-week-window flagship release ([`02` §3](./02-new-emerging.md#3-gpt-5-6)). If you publish a credible comparison post within 24 hours of launch, the LinkedIn distribution premium is ~5–10× the same post 72 hours later. Don't write the post now; **build the harness** so you can write the post in one evening.

**Harness spec (use this tonight as a 60-min project):**

```text
multi-provider-bench/
├── providers/
│   ├── claude_opus_4_8.py     # $5/$25, 1M ctx, 128K out
│   ├── gpt_5_5.py             # current OpenAI flagship
│   ├── gpt_5_6.py             # stub, fill in on launch day
│   ├── gemini_3_5_pro.py      # June flagship (after Pro GA)
│   └── gemini_3_5_flash.py    # $1.50/$9, the cost leg
├── tasks/
│   ├── 01_codebase_qa.md      # 50k-token codebase, 10 Qs, scored 0/1
│   ├── 02_refactor.md         # 3 files, observable behavior preserved
│   ├── 03_planning.md         # spec → implementation plan, depth-checked
│   ├── 04_tool_call.md        # MCP-server tool-call sequence
│   └── 05_long_context.md     # 800K-token doc, 5 needle-in-haystack
├── harness.py                 # runs all providers × all tasks, logs:
│                              #   - latency, tokens in/out, cost
│                              #   - score (LLM-judge or rule)
│                              #   - failure mode (refusal/hallucination/loop)
└── results/                   # one CSV per run; one chart per task
```

**Hard rules:** (a) **log per-step cost** for every run — this is what makes the harness an interview artifact instead of a benchmark hobby, (b) use a **fixed seed + identical prompts** across providers, (c) include **at least one task that exercises tool use against a real MCP server**, not a mock — this aligns the artifact with the real-tool-eval research thread ([`04` §1](./04-research-progress.md#1-benchmarks) + [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)).

**Inspirational reference architecture:** **Hermes Agent async subagents (Nous Research, shipped June 15)** — the parent agent fires off subagent jobs that return task IDs immediately and complete asynchronously; the parent context never sees the subagent's intermediate reasoning, only the final summary. **Copy this pattern** if you want your harness to run providers in parallel without context-poisoning the orchestrator.

**Sources:**
- [MarkTechPost — Hermes Agent Adds Asynchronous Subagents (June 16)](https://www.marktechpost.com/2026/06/16/hermes-agent-adds-asynchronous-subagents-so-delegated-work-no-longer-blocks-the-parent-chat/) `[secondary]`
- [TechTimes — Hermes Agent Ships Async Subagents](https://www.techtimes.com/articles/318549/20260617/hermes-agent-ships-async-subagents-delegated-work-no-longer-blocks-chat.htm) `[secondary]`
- [MarkTechPost — Hermes Agent Ships Tool Search for MCP: 49% to 74% Accuracy Gain on Opus 4 (May 29)](https://www.marktechpost.com/2026/05/29/hermes-agent-ships-tool-search-for-mcp-anthropic-evals-show-49-to-74-accuracy-gain-on-opus-4/) `[secondary]`
- [Anthropic — What's new in Claude Opus 4.8](https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-8) `[primary]`
- [Simon Willison — Claude Opus 4.8: "a modest but tangible improvement"](https://simonwillison.net/2026/May/28/claude-opus-4-8/) `[analysis]`

### Why it matters to you

- **Job lens:** This single artifact answers **three interview questions in one repo**: (a) "Show me you can evaluate models" (the harness), (b) "Show me you understand cost" (the per-step log), (c) "Show me you can wire up real tools" (the MCP-server task). For Solutions Engineer / FDE / AI-Eval roles, this beats every "I built a chatbot" portfolio piece.
- **Startup lens:** A polished, public version of this harness with a hosted dashboard is **the wedge for an "Artificial Analysis but for your own tasks" SaaS** — Artificial Analysis benchmarks the models on canonical tasks; the gap in the market is *benchmark them on **your** tasks*. Customer Discovery: any enterprise considering a switch from Claude to GPT or vice versa.
- **Insight:** The harness compounds. Once it exists, every flagship release (GPT-5.6, Gemini 3.5 Pro, Opus 4.9, Sonnet 4.7) gives you another publication. **One artifact, six posts over six months** is a credibility loop most CS grads never engineer.

→ Cross-link: [`04` §1 real-tool benchmarks](./04-research-progress.md#1-benchmarks) · [2026-05-22/03 §1 Opus-orchestrator/Sonnet-worker cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 3. Habit to install this week: weekly billing audit (60 minutes, every Friday afternoon)

The June 15 Anthropic Agent SDK metering split is now **3 days old**. If you didn't toggle the credit setting in your account ([carried from 2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md)) — your programmatic Claude calls have been billing at full API list rates since Sunday.

**Audit checklist (use this every Friday until you've banked 8 weeks of data):**

1. Anthropic billing → split by API key → tag each key with what it serves (interactive vs programmatic vs Claude Code).
2. OpenAI billing → same split (Codex vs ChatGPT API vs Realtime).
3. Google Cloud → Gemini API spend (the cost-leg in the router).
4. Compute per task — pick your 3 most-used personal workflows, compute **$/task** for each provider.
5. **Cache-read rate** — for any task using prompt caching, confirm `cache_read_input_tokens > 0` and compute hit rate.
6. **Decide one thing to change** for next week (route a task to Flash, raise temperature, drop a redundant subagent, etc.).

**Why this:** the audit is **simultaneously a personal cost-saver, a portfolio artifact (anonymized writeup → "I cut my agent costs 38% by routing X to Y"), and a customer-discovery proxy for a router/billing-audit startup**. Three uses, 60 minutes.

→ Cross-link: [2026-05-16/01 §1 Anthropic agent metering announcement](../2026-05-16/01-big-lab-moves.md) · [`05` §4 the artifact](./05-career-and-startup.md#4-skill-artifact).
