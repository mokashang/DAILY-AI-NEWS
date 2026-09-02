# Practical Skills & Tools — 2026-05-29

This is the **hands-on** file. Pick **one** item below and *do it* this weekend. If you only have an hour, do §1 (Dynamic Workflows). If you have 20 minutes after that, do §2 (mid-conversation system messages). Both pay back for months.

Tags: `#claude-code #orchestration #dynamic-workflows #subagents #prompt-cache #cost #verification`

---

## 1. Dynamic Workflows — the orchestration primitive you should ship this weekend {#1-dynamic-workflows}

**What it is:** A **Claude Opus 4.8 feature in research preview**: given a task description, **Claude writes a JavaScript script that orchestrates a tree of subagents** to do the work. A separate **runtime executes the script in the background**, spawning subagents that themselves use Claude.

- **Concurrency cap:** **16 concurrent subagents per run.**
- **Total cap:** **1,000 subagents per workflow.**
- **Surfaces:** Claude Code (CLI), Claude Desktop, the VS Code extension.
- **Plans:** Max, Team, Enterprise.
- **Headline use case Anthropic ships with:** *end-to-end codebase migrations across hundreds of thousands of lines of code, from kickoff to merge, against the existing test suite as the success criterion.*

**Why it matters more than the "Opus 4.8 benchmarks" headline:** Until this week, **multi-agent orchestration was a *you-build-it-yourself* pattern** (the LangGraph / CrewAI / hand-rolled fan-out). Anthropic moving the *script generator* into Claude itself, with a hosted runtime, **collapses the orchestration layer** that ~30+ open-source projects existed to provide. It's the same compression move Managed Agents made for agent-runtime ([2026-05-09](../2026-05-09/01-big-lab-moves.md)) and that the Agent SDK made for tool-loops ([2026-05-16](../2026-05-16/01-big-lab-moves.md)).

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8 (Dynamic Workflows section)](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [TechCrunch — Anthropic releases Opus 4.8 with new dynamic workflow tool](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/) `[secondary]`
- [MarkTechPost — Dynamic Workflows, fast mode, 1000-subagent cap](https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/) `[analysis]`
- [Winbuzzer — Dynamic Workflows for Claude Code](https://winbuzzer.com/2026/05/29/anthropic-ships-opus-48-with-dynamic-workflows-xcxwbn/) `[secondary]`

### The 90-minute hands-on (do this Saturday)

1. **Pick the repo.** Any Python or JS repo of yours, ≥1,000 LOC, with **a working test suite**. The test suite is the verifier.
2. **Define the migration.** One short, mechanical change that touches **dozens-to-hundreds** of files. Examples (pick whichever is most-real for your code):
   - `requests` → `httpx`
   - `print` → `logging.info`
   - class-based React components → hooks
   - `os.path` → `pathlib`
   - `unittest` → `pytest`
   - JS callbacks → `async/await`
3. **Bound the run.**
   - `MAX_CONCURRENT_AGENTS=8` (half the cap).
   - `MAX_TOTAL_AGENTS=100` (10% of cap; gives you a margin of safety on cost).
   - **Set a hard cost budget** in your runtime config (whatever your tolerance is — say $25).
4. **Prompt Claude Code to author the workflow.** Skeleton:
   > "Write a Dynamic Workflow that, for the migration described above, (a) enumerates all files touched, (b) per-file: drafts a patch, runs the test suite scoped to the affected module, retries if red, (c) commits per-file once tests pass, (d) writes a per-file structured log of token counts and seconds-elapsed."
5. **Run it. Log per-step.** The output you want is two things:
   - **Wall-clock and dollars spent per subagent.**
   - **Test-suite green / red ratio per subagent retry.**
6. **Write up the readme** (≤500 words). Include:
   - The **diff size** (files changed, LOC).
   - The **cost / hour breakdown** (you can plot it).
   - The **failure modes** — every flaky test, every "Claude misunderstood the spec" instance. *Honest* writeups are the ones that get hiring-manager DMs.
7. **Cross-reference [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)** — the **Opus-4.8 orchestrator + Sonnet-4.6 worker** split is now even more relevant because **Opus 4.8 Fast Mode is 3× cheaper**, so the orchestrator side itself gets cheaper. Re-do the cost math vs. the all-Opus baseline you measured last week.

### Why it matters to you

- **Job lens:** This is **one artifact that answers three interview questions simultaneously**: *agent orchestration*, *cost-aware routing*, *verification against real outputs*. Most candidates do not have *any* of these on their portfolio; you can have all three by Sunday night.
- **Startup lens:** Dynamic Workflows make the **"migrations as a service"** wedge real. Pricing: charge per migration (say, "$10K to migrate your test suite from `unittest` to `pytest`, guaranteed-green") and the unit economics work because the agent runtime can be capped. Find one mid-sized SaaS, do it pro-bono once, and you have a case study.
- **Insight:** Anthropic's framing ("hundreds of thousands of LOC, kickoff to merge, against the test suite") is **the canonical evaluation metric for a coding agent in 2026.** Internalize this metric: **lines-of-code-migrated per dollar, conditional on test-suite-green** is the unit of "how good is your coding agent" — not LMSYS Elo, not HumanEval. The market will move to this metric within ~6 months.

→ Cross-link: [`01` §2 Opus 4.8 detail](./01-big-lab-moves.md#2-opus-48) · [2026-05-22/03 §1 the orchestrator/worker cost lever](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-22/04 §1 MCP-Atlas / Toolathlon real-tool eval](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).

---

## 2. Mid-conversation system messages — the prompt-cache lever {#2-mid-convo-system-messages}

**What changed:** Opus 4.8's API now accepts **a `system` turn appended *after* user turns** in the `messages` array. Pre-4.8, system instructions had to live at the top of the array — meaning to *update* the instructions mid-conversation you either restated the entire system prompt (cache miss on subsequent turns) or wrote workarounds (e.g., embedding new instructions as fake `user` turns).

**Why it matters:** **Prompt cache hits survive** an updated steer. Translation: in an agent loop that runs many turns, you can **swap or extend instructions at step N without invalidating the cache prefix from steps 1…N-1.**

Simon Willison's review flags this as the under-priced feature of the release. (His framing: *"being able to steer the system prompt mid-conversation sounds really powerful."*)

**Sources:**
- [Simon Willison — Claude Opus 4.8 notes](https://simonwillison.net/2026/May/28/claude-opus-4-8/) `[analysis]` — independent practitioner review; this is the source for the mid-conversation system-messages feature being highlighted
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`

### The 20-minute hands-on (do this Sunday morning)

1. **Pick an agent loop you already have** — anything that runs ≥5 turns with a non-trivial system prompt (your MCP server's host, a Claude Code session you can replay, a research-summarizer, whatever).
2. **Add one mid-conversation `system` turn** at turn 3 or 4 that **extends** the instructions (e.g., "from now on, output JSON only" or "from now on, you are restricted to read-only tools").
3. **Verify two things:**
   - The new behavior takes effect from the next turn.
   - **Prompt cache hits continue** — check via the Anthropic billing dashboard or the `usage` field on the API response (`cache_read_input_tokens` should be non-zero on subsequent turns).
4. **Write the one-liner takeaway** ("we updated steering rules at turn N and preserved $X of prompt-cache spend").

### Why it matters to you

- **Job lens:** Tiny, deep, specific. *"In the interview I asked the candidate how they cut their agent-loop cost — they said 'prompt caching plus mid-conversation system messages.' Hired."* You want to be that candidate.
- **Startup lens:** Any product whose unit economics are constrained by the cost of long-running agent loops just got better. Reprice your runway.
- **Insight:** This is a **cache-aware API design** decision — Anthropic is *prioritizing prompt-cache efficiency as a first-class API feature*, not an optimization detail. Expect more such moves; treat **prompt-cache hit rate** as a *production metric* you monitor, not an occasional optimization.

→ Cross-link: [2026-05-17 prompt caching as 60–90% input-cost saver](../2026-05-17/03-practical-skills-and-tools.md).

---

## 3. The "effort" selector — when to use `low / medium / high` {#3-effort-selector}

Opus 4.8 (in claude.ai and Cowork; soon API) exposes an **effort selector**: `low / medium / high`. **Opus 4.8 defaults to high.**

**When to drop to `medium`:**
- Pure transformation tasks (translate, summarize, format-shift) where you do **not** need extended reasoning.
- Inner-loop subagent calls inside a Dynamic Workflow (the orchestrator is high; the workers are medium).
- Batch jobs.

**When to drop to `low`:**
- Generation of short structured outputs (one-line classifications, tag extraction).
- Routing decisions.

**Stay at `high`:**
- Architecture/design questions.
- Code review (especially security-adjacent).
- Anything where the failure mode is *plausible-looking-wrong-answer*.

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Simon Willison — Opus 4.8 notes (effort selector usage)](https://simonwillison.net/2026/May/28/claude-opus-4-8/) `[analysis]`

### Why it matters to you

- **Job lens:** "When I should drop from `high` to `medium`" is a **15-second interview answer** you should rehearse. It demonstrates you have actually **operated** Claude, not just used it.
- **Insight:** The effort selector is a **continuation of the Fast/Slow / thinking-budget / reasoning-effort move** every frontier model has converged on in 2026. **Expect cross-vendor portability of the concept** — be ready to think of "effort" as a first-class dimension of every model call, like temperature in the 2024 era.

→ Cross-link: [`01` §2 Opus 4.8 deltas](./01-big-lab-moves.md#2-opus-48).

---

## 4. The Friday cost lever — re-audit your Claude bill {#4-bill-audit}

With three changes landing this week — **Fast Mode 3× cheaper, mid-conversation system messages, effort selector** — **your existing bill is structurally over-priced.** Do a **15-minute audit today**:

1. Pull last 7 days of Claude usage from the billing dashboard.
2. Identify the **top 3 cost drivers** (you want >70% of spend isolated).
3. For each driver, answer:
   - Is it on **Fast Mode**? If not and the task tolerates Fast, switch — 3× cheaper.
   - Is it a **multi-turn loop** with a stable system prompt? If yes, are you using prompt caching? If no, add it ([2026-05-17](../2026-05-17/03-practical-skills-and-tools.md)).
   - Could the **effort** drop? If yes, drop it.
4. Tag the change. **Re-pull billing in 48 hours** and screenshot the delta.

That's your **personal billing audit + writeup artifact** from [ME.md portfolio](../ME.md#active-portfolio-artifacts) — half-done.

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [2026-05-16/01 Agent SDK metering — T-17 days reminder](../2026-05-16/01-big-lab-moves.md) — context for why this matters more now than next month
