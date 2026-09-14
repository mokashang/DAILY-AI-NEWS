# Practical Skills & Tools — 2026-07-20

Three things to actually *do* this week. **First**, if you haven't yet — set up **3–5 parallel Claude Code sessions in git worktrees** and put every session behind a **plan-mode gate**. This is the single largest productivity delta of 2026, and Claude Code now has **native worktree support** so there's no excuse. **Second**, if you have a GPT budget — build a **tier picker** for Sol / Terra / Luna and route by task class; the cost gap between the three tiers is enough that a 30-line router pays for itself in a week. **Third — and most urgently** — **audit your Claude Code bill against Opus 4.7's new tokenizer.** Same $/M, ~30% more tokens per prompt. If you don't measure the delta this week you are silently overpaying.

Tags: `#claude-code #workflow #verification #plan-mode #worktree #tokenizer #cost #router`

---

## 1. The Claude Code productivity playbook that actually held up {#1-claude-code-playbook}

**What to install this week (in order):**

1. **`CLAUDE.md` at every project root.** Karpathy's 4-rule template (originally flagged on [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)) remains the single highest-leverage one-time install. If you already have one, re-read it and prune anything Claude Code has since made obsolete (e.g. explicit "always read this file first" — the harness now does that natively).

2. **3–5 parallel sessions, each in its own git worktree.** Claude Code now ships **native worktree support** — you no longer have to hand-roll the `git worktree add` + directory-switching dance. The pattern that works: **1 planning session (Opus 4.7, plan mode)** + **2–3 implementation sessions (Sonnet 4.6, edit mode)** + **1 verification session (Opus 4.7, read-only, evaluates the others' output).** You are now capable of shipping the work of a small team.

3. **Plan mode (`Shift+Tab`) before every non-trivial edit.** This is *not* optional. In plan mode Claude reads files and proposes a written plan but makes **no edits** — the write tools are physically unavailable, enforced at the tool level. Review the plan; only exit and approve when the approach is right. **This one habit removes the vast majority of "Claude did the wrong thing" incidents.**

4. **Verification is the #1 tip. If you adopt one thing this week, adopt this one.** After every non-trivial task, ask Claude to **verify its own output** — run the tests, load the resulting UI, grep for stale imports, whatever the domain-appropriate check is. The `verify` skill / `/verify` slash command captures the pattern; if your project doesn't have one, bootstrap it with a two-sentence prompt: *"Before you report done, exercise the change end-to-end. Run the tests. If it's UI, load it. If it's a script, run it. Then report what you observed, not what the diff says."*

5. **Start a fresh conversation for each big task.** Many practitioners report this alone cuts down on silly mistakes — a stale conversation drags obsolete context into every new prompt.

6. **`/loop` for recurring housekeeping.** `/loop 5m /babysit` for auto-addressing review comments and rebasing; `/loop 1h /pr-pruner` for closing stale PRs. Runs locally for up to 3 days at a time.

**The 2026-vs-2025 shift, in one sentence:** the developer's role has moved from **context management** (clearing conversations, maintaining artifact directories, manually simulating workflow structure) to **outcome specification** (defining what "done" means precisely enough that a verification loop can check it). Design your habits around *the new job*, not the old one.

**Sources:**
- [Anthropic Support — Claude Code power user tips](https://support.claude.com/en/articles/14554000-claude-code-power-user-tips) `[primary]`
- [Blake Crosley — Claude Code CLI: The Complete Guide — Hooks, MCP, Skills](https://blakecrosley.com/guides/claude-code) `[analysis]`
- [Iwosz Zapar — Claude Code Best Practices: 8 Rules I Learned the Hard Way](https://www.iwoszapar.com/p/claude-code-best-practices) `[analysis]`
- [DZone — 50 Claude Code Tips That 10x My Coding Workflow](https://dzone.com/articles/claude-code-tips-boost-coding-productivity) `[analysis]`
- [F22 Labs — 10 Real Productivity Workflows for 2026](https://www.f22labs.com/blogs/10-claude-code-productivity-tips-for-every-developer/) `[analysis]`
- [Data Science Collective — Effective Claude Code Workflows in 2026: What Changed and What Works Now](https://medium.com/data-science-collective/effective-claude-code-workflows-in-2026-what-changed-and-what-works-now-c93ebc6f8f50) `[analysis]`
- [White Prompt Blog — The Claude Code Playbook: 5 Tips Worth $1000s in Productivity](https://blog.whiteprompt.com/the-claude-code-playbook-5-tips-worth-1000s-in-productivity-22489d67dd89) `[analysis]`

### Why it matters to you

- **Job lens:** In an interview, **"I run 3–5 parallel Claude Code sessions in worktrees behind plan-mode gates with a verification pass"** is a specific, testable answer to "how do you actually use AI in your workflow?" Most candidates will hand-wave; this answer is falsifiable and demonstrably productive. Pair it with a metric — e.g. "cut my median PR turnaround from 2 days to 4 hours" — and you have the strongest single interview answer for an AI-forward SWE / SDE role.
- **Startup lens:** The **plan → verify** loop is the same primitive that a customer buys from you when they buy an "AI product" — you are selling a *system that specifies an outcome and confirms the outcome*, not "raw model access." Product-market fit is where your verifier is credible to the buyer.
- **Insight:** Note how much of this playbook is **negative space** — plan mode *removes* the write tool, fresh conversations *drop* stale context, verification *rejects* the diff-report-only output. **The AI-workflow skill of 2026 is not "make the model do more"; it's "constrain the model's action space so its output can be trusted at speed."**

---

## 2. Build a Sol / Terra / Luna tier picker this week {#2-provider-router}

**What to build:** A **30-line request-time router** that picks the GPT-5.6 tier per task class. The rough allocation that works:

| Task class | Tier | Rationale |
|---|---|---|
| Multi-file refactors, hard math, agent orchestration | **Sol** ($5/$30) | Only tier that reliably survives long tool chains |
| Standard coding, doc drafting, summarization, extraction at medium volume | **Terra** (~½ of GPT-5.5 price) | Best cost-per-quality point |
| Bulk classification, high-volume triage, first-pass filtering | **Luna** (cheapest) | ~10× cheaper; quality is fine for the filter/triage lane |

Then wire an **eval harness** in front of it: for each task class, run the *same 20 prompts* through all three tiers, score against a rubric (correctness / latency / cost), and let the numbers pick the tier automatically. **This is a portfolio artifact and a real cost saver in one build.**

**Extension:** run the same 20 prompts through **Opus 4.7 Sonnet 4.6 / Haiku 4.5** and you have the **3-provider (× multiple tiers) comparison table** carried on [ACTIONS.md](../ACTIONS.md) since May.

**Sources:**
- [OpenAI Help Center — A preview of GPT-5.6 Sol, Terra and Luna](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) `[primary]`
- [FelloAI — GPT-5.6 Sol, Terra, Luna: What OpenAI Just Shipped](https://felloai.com/gpt-5-6/) `[analysis]`
- [Tech Journal — GPT-5.6 Explained: Sol, Terra & Luna (July 2026)](https://techjournal.org/openai-gpt-5-6-sol-terra-luna) `[analysis]`

### Why it matters to you

- **Job lens:** This is one of the highest-signal *shippable* portfolio artifacts you can build in a weekend. Public repo + README + `benchmark_results.md` showing the tier-routing decisions with numbers. **The exact skill a Solutions Engineer / FDE demonstrates during a customer POC.**
- **Startup lens:** The router *is* the product for a class of B2B tooling (spend-mgmt / cost-observability / dev-platform). Even if you don't build a standalone company, **your own product benefits from the router immediately** — same output quality at ~40–60% of the cost.
- **Insight:** **Tier picking used to be a research exercise; it's now table stakes.** As frontier labs ship 3–4 tiers per model family, the *skill that scales with model progress* is not "prompt Sol better" — it's "know when Terra is enough."

---

## 3. Audit your Claude Code bill against the Opus 4.7 tokenizer — TODAY {#3-tokenizer-cost}

**What changed:** **Opus 4.7's new tokenizer produces ~30% more tokens per identical text** vs Opus 4.6. **Pricing stayed at $5/M input / $25/M output.** Nothing was announced loudly — it lives in the model card footnotes.

**The audit (one hour):**

1. Pull your last 7 days of Claude Code usage from `~/.claude/usage.jsonl` (or the equivalent for your setup — the Anthropic web console has the same view).
2. Sum input + output tokens per day. Multiply by list price.
3. **Divide the token count by 1.30** to estimate what the same week would have cost on Opus 4.6.
4. Compute the delta as a % of your total monthly Claude budget.
5. If delta > 15% of budget, mitigate this week: (a) push more subagent work to **Sonnet 4.6** (the Opus-orchestrator/Sonnet-worker pattern — [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)); (b) turn on **prompt caching** on your longest system-prompt path (60–90% input-cost cut — [2026-05-17/03 §2](../2026-05-17/03-practical-skills-and-tools.md#2-prompt-caching)); (c) tighten context — drop stale files from `CLAUDE.md` and shrink system prompts.
6. **Ship the audit script as a public gist by Friday.** That's your customer-discovery artifact for the cost-router startup wedge *and* the portfolio artifact for AI-Integration-Engineer interviews.

**Draft prompt for a Sonnet-4.6-worker audit script (copy-paste):**

> *Read the last 7 days of Claude usage logs from `~/.claude/usage.jsonl`. For each day, sum input_tokens and output_tokens per model. Compute: (a) actual daily spend at list price; (b) implied Opus 4.6 spend (input_tokens / 1.30 for Opus 4.7 rows only, at same $/M); (c) the delta and delta as % of a `$MONTHLY_BUDGET` env var (default $500). Print a markdown table sorted by delta descending. Then output a one-line recommendation: "route N tasks/day to Sonnet 4.6 to close the delta." Then run `pytest -q` on any tests you write, and only report done after verification.*

**Sources:**
- [Anthropic — Introducing Claude Opus 4.7](https://www.anthropic.com/news/claude-opus-4-7) `[primary]`
- [BoringBot — Claude Opus 4.7 results: early benchmarks, real-world feedback, and is it worth upgrading?](https://boringbot.substack.com/p/claude-opus-47-results-early-benchmarks) `[analysis]`
- [Vellum — Claude Opus 4.7 Benchmarks Explained](https://www.vellum.ai/blog/claude-opus-4-7-benchmarks-explained) `[analysis]`

### Why it matters to you

- **Job lens:** *Nobody* is talking about this cost bump publicly. Being the first person in your network to publish a real audit — with numbers — is worth more than any generic "here are Claude Code tips" post. **Concrete, measured, published within 5 days of the underlying change** is the pattern that gets you retweeted by frontier-lab engineers, and that gets you a Solutions/FDE recruiter DM.
- **Startup lens:** This audit is the **first sales call** for the model-router wedge on your STARTUPS.md. You call three Claude-Code-heavy friends, run the script on their bill, hand them a number, and ask *"would you pay $X/mo for this to run automatically and cap you at $Y?"* That is customer discovery in the truest sense.
- **Insight:** Tokenizer changes are the **model-vendor equivalent of a stealth price hike** — same list price, more tokens. Watch for this pattern on every future model release: **any time a new tokenizer ships alongside a "capability upgrade," assume the effective price went up until you measure otherwise.**

---

## 4. Anthropic Claude Code stability update: three new safety primitives worth knowing {#4-claude-code-stability}

**What shipped:** As part of Anthropic's July Claude Code update ([Anthropic News](https://www.anthropic.com/news) `[primary]`):

- **Tighter permission checks** on file/shell tools. Fewer "silent shell escapes."
- **Safer Bash and PowerShell handling.** Specifically better handling of long-running commands and shell-escape edge cases.
- **Improved background-session cleanup.** Long-lived agents no longer leak orphaned processes.
- **Stronger telemetry.** More visibility into what tools an agent invoked and why.
- **Better remote and plugin reliability.**
- **New `EndConversation` tool.** Lets Claude — or you — cleanly terminate a session mid-run, preserving state.
- **Progress heartbeats for long-running tasks.** No more "is it stuck or just thinking?"

**Sources:** (rolled up from Anthropic release notes and the Claude Code changelog)
- [Anthropic News](https://www.anthropic.com/news) `[primary]`
- [Anthropic Support — Release notes](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`

### Why it matters to you

- **Job lens:** The `EndConversation` tool + progress heartbeats + telemetry are all **production-primitives**, not dev-preview toys. That's Anthropic signaling that Claude Code is intended to run on *your team's servers*, not just your laptop. In an interview, **"we run Claude Code in a hook-guarded, telemetry-instrumented subagent tree with `EndConversation` on timeout"** is a differentiated answer.
- **Startup lens:** These same primitives are what make a Claude-Code-based product *sellable to enterprise*. If your startup wedge involves running long agents on customer data, this stability update is what unblocks the enterprise SKU. **Re-read your product spec against this list; anywhere you had a manual heartbeat / manual cleanup / manual terminate, you can now delete code.**
- **Insight:** The **shape of the update — heartbeats, cleanup, telemetry, safer shell** — is the shape of every mature agent-runtime story. This is the third such update this year. **Agent runtimes are becoming the new "web frameworks"** — comfort with 2–3 (Claude Code, OpenAI's Managed Agents, Google's Antigravity/ADK) will be table stakes for platform-eng-adjacent roles by end of Q4.

→ Cross-link: [`01` §4 Opus 4.7 + the wider Anthropic launch bundle](./01-big-lab-moves.md#4-opus-47-default) · [2026-05-21/03 §2 hook-guarded MCP mini-agent](../2026-05-21/03-practical-skills-and-tools.md#2-artifact)
