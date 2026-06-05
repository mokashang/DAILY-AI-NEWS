# Practical Skills & Tools — 2026-06-05

The 14-day gap delivered a *single* practical lever that dwarfs everything else: **Claude Opus 4.8 dynamic workflows**. Plus the **T-10 reminder** for the June 15 Agent SDK metering split, and an updated **4-provider cost-routing** stack now that **MAI** is real and **Gemini 3.5 Flash** is the new cheap-frontier baseline.

Tags: `#claude-code #claude #anthropic #agents #cost #routing #mcp #practical`

---

## 1. Claude Opus 4.8 dynamic workflows — the playbook {#1-dynamic-workflows}

**What it is:** Opus 4.8's **dynamic workflows** let Claude **write a JavaScript orchestration script** from your plain-language request; a **separate runtime** executes that script in the background, **spawning dozens to hundreds (up to 1,000) of parallel subagents**, each verifying its own output before returning. This is qualitatively different from manually spawning subagents — Claude designs the work *and* the verification, then runs the plan.

**How to trigger:**

```
# Explicit (recommended starting out)
> include the word "workflow" anywhere in your prompt
> Claude detects → writes a script → hands to runtime → runs

# Automatic
> /effort ultracode
> Claude decides when a task is big enough to justify a workflow
```

**Available on:** Claude Code in **Max / Team / Enterprise** plans, plus **API**.

**Best use cases (where the per-token spend pays back as reviewer time saved):**

| Use case | Why it fits |
|---|---|
| **Framework migration** (Vue 2 → Vue 3, React class → hooks, etc.) | Independent file changes + shared verification (test suite passes) |
| **Security audit** | Embarrassingly parallel per route / per file / per endpoint |
| **Flaky-test investigation** | Many independent reproductions; rollup verifier |
| **Multi-package dependency upgrade** | Parallel updates with cross-package integration tests |
| **Repo-wide perf review** | Per-module hot-spot scan + rolled-up report |

**When NOT to use a dynamic workflow:**

- Tiny edits (one file, < 50 LOC) — workflow overhead exceeds benefit
- Tasks where a single narrow prompt is easier to *review*
- Anything where you can't articulate the verification step

**Best practices (synthesized across the linked guides):**

1. **Define the verification step before the work step.** *"How will I know each subagent's output is good?"* must be answerable before you fire the workflow. The verifier is the most important code in a workflow.
2. **Track cost per *successful task*, not per token.** A workflow that costs 3× more but saves 2 hours of review is still a bargain — calculate it that way.
3. **Cache the repo context.** Don't pay to re-explain the codebase to each subagent — prompt-caching the repo digest is the single biggest cost lever inside a dynamic workflow.
4. **Route models per step.** Opus 4.8 for planning + final review; **Sonnet 4.6 or Gemini 3.5 Flash for the parallel subagent work**. The 40% savings number from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) gets stronger when the cheap leg is Flash.
5. **Start tightly scoped.** A 200-LOC dead-code sweep is a great calibration run. *Then* scale to a 200K-LOC migration.
6. **Save the workflow scripts.** They're reusable artifacts — refine them like prompt templates. Build a workflow library.

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [Apidog — Claude Code Dynamic Workflows: Running Hundreds of Parallel Subagents with Opus 4.8](https://apidog.com/blog/claude-code-dynamic-workflows-opus-4-8/) `[analysis]`
- [Sagnik Bhattacharya — Claude Opus 4.8 Dynamic Workflows Tutorial for Claude Code](https://sagnikbhattacharya.com/blog/claude-opus-4-8-dynamic-workflows) `[analysis]`
- [Geeky Gadgets — A Complete Guide to New Claude Code Dynamic Workflows](https://www.geeky-gadgets.com/claude-opus-dynamic-workflows-guide/) `[analysis]`
- [MindStudio — Claude Opus 4.8 Dynamic Workflows: How to Run Hundreds of Parallel Sub-Agents](https://www.mindstudio.ai/blog/claude-opus-4-8-dynamic-workflows-parallel-sub-agents) `[analysis]`
- [allthings.how — Claude Opus 4.8 dynamic workflows in Claude Code, explained](https://allthings.how/claude-opus-4-8-dynamic-workflows-in-claude-code-explained/) `[analysis]`
- [Agentpedia — Claude Code Dynamic Workflows: Official Step-by-Step Guide](https://agentpedia.codes/blog/claude-opus-4-8-claude-code-workflows) `[analysis]`

### Why it matters to you

- **Job lens:** Interview answer for *"how do you scale a coding agent without losing reliability?"* is now: **"design the verifier first, write the workflow second, route the work to cheap models, route the review to Opus, cache the repo context, and instrument per-step cost."** That sentence + a one-page demo will set you apart from any candidate whose only agent experience is single-prompt Claude.
- **Startup lens:** This is the *first time* the orchestration script is **a first-class shipping artifact** instead of internal-tooling cruft. Founder wedge: **the GitHub of workflow scripts** — a community library of tested, cost-instrumented dynamic-workflow scripts that anyone can clone-and-run. Anthropic owns the runtime; the *library* is open.
- **Insight:** Two weeks ago the answer to "what's the next career-defining skill?" was *prompt engineering* or *agent design*. Today the answer is **workflow design** — the discipline of declaring intent, verification, model-routing, and cost as one artifact. This is the closest the AI field has come to a real software-engineering discipline since the original LangChain wave. Get good at it now.

---

## 2. T-minus 10 days — June 15 Agent SDK metering checklist {#2-june-15-checklist}

**Reminder:** On **June 15, 2026** Anthropic moves **Claude Agent SDK, `claude -p`, Claude Code GitHub Actions, and third-party agents** off your normal subscription into a **separate monthly credit pool** billed at **full API rates**. Pro $20 / Max-5x $100 / Max-20x $200. **No rollover.**

**Interactive Claude Code in the terminal + Claude.ai web/desktop/mobile chat are NOT affected.** Only **programmatic** usage moves.

**Friday-night 30-min checklist:**

```
[ ] (1) Toggle: open Claude account settings → enable the new Agent SDK credit pool.
        Silent failure mode if skipped — agents will start failing on June 15.

[ ] (2) Decide on "usage credits" overflow: enable it = overflow bills at API rates;
        disable = jobs fail at zero remaining credit. For CI, enable. For local
        experiments, disable (a forcing function).

[ ] (3) Audit your last 30 days of Agent SDK usage. Tools: Anthropic billing portal
        + your own token logs. Goal: find your steady-state monthly token spend so
        you can project against $20/$100/$200.

[ ] (4) Enable prompt caching on your highest-volume codebase. cache_read_input_tokens
        > 0 should appear in your logs within one session. 60–90% input-cost savings.

[ ] (5) Switch programmatic CI runs to a cheaper model where the verifier still passes.
        Sonnet 4.6 or Flash for parallel; reserve Opus 4.8 for plan + review.

[ ] (6) Set up a daily cost alert ($10/day threshold to start). Tools: Anthropic API
        usage webhook or a simple cron + curl on /v1/usage.
```

**A single coding agent session can burn 100K–200K tokens in one pass; a moderately active CI repo can exhaust $20 in days.** Treat this as a forcing function to instrument cost properly — the discipline is reusable career capital.

**Sources:**
- [InfoWorld — Anthropic puts Claude agents on a meter across its subscriptions](https://www.infoworld.com/article/4171274/anthropic-puts-claude-agents-on-a-meter-across-its-subscriptions.html) `[secondary]`
- [Codersera — Anthropic's June 15 Billing Change: What Every Claude Code & Agent SDK User Must Do](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/) `[analysis]`
- [DevToolPicks — Anthropic Splits Claude Subscriptions: What Changes for Indie Hackers on June 15](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[analysis]`
- [ChatForest — Anthropic's June 15 Billing Split: What Every Claude Agent Developer Needs to Know](https://chatforest.com/reviews/anthropic-claude-agent-sdk-billing-split-june-15-2026-credit-pool-developer-guide/) `[analysis]`
- [The New Stack — Anthropic splits billing again: Agent SDK gets separate credit pools](https://thenewstack.io/anthropic-agent-sdk-credits/) `[secondary]`
- [Digital Applied — Claude Credit Overhaul 2026: What Changes on June 15](https://www.digitalapplied.com/blog/anthropic-claude-credit-overhaul-june-15-2026) `[analysis]`

### Why it matters to you

- **Job lens:** "How do you stay under a fixed AI budget while shipping agentic code at scale?" is suddenly a *real* interview question. Having a writeup of *your own* June 15 audit (with numbers) is a 10-minute case study you can drop into any interview about cost-aware engineering.
- **Startup lens:** Validates the **cost-router / model-budget-guard** startup thesis (running for 6 weeks in this archive). The June 15 deadline creates a *forcing function* for thousands of independent users to look at their AI bill for the first time. That's a user-acquisition wedge.
- **Insight:** Every metering event in this industry has produced a *real* market for cost tooling 30–60 days later. **Bookmark June 15 → mid-July as your launch window** if you ship anything in this lane.

---

## 3. 4-provider cost routing — the updated stack {#3-cost-routing}

With Gemini 3.5 Flash GA, Opus 4.8 shipped, Microsoft MAI launched, and OpenAI GPT-5.5 Instant now default, the **production-grade router** has 4 legs and a cleaner per-task split:

| Task pattern | Recommended primary | Why |
|---|---|---|
| **Planning + final review** (high-stakes, must be right) | **Opus 4.8** | 4× honesty improvement on coding flaw detection |
| **Parallel subagent work** in a dynamic workflow | **Sonnet 4.6** or **Gemini 3.5 Flash** | <½ cost of Opus, sufficient for narrow scoped subtasks |
| **Long-context retrieval / synthesis** | **Gemini 3.5 Flash** (1M+ ctx) | Cheapest-good-enough long-context |
| **Voice / translate / real-time** | **OpenAI GPT-5.5 + new realtime audio** | GA voice stack, easiest integration |
| **Privacy-locked-in / Azure-tenant** | **Microsoft MAI-Code-1-Flash** | Native to Foundry, commercially-licensed training data |
| **Open-weights / on-prem** | **Mistral / Nemotron / DeepSeek V4** | Per [Air Street State of AI May 2026](https://press.airstreet.com/p/state-of-ai-may-2026) |

**Implementation skeleton:**

```python
# Each provider's SDK; one router decides per request
def route(task: Task) -> Provider:
    if task.requires_planning_or_review:
        return Provider.ANTHROPIC_OPUS
    if task.is_parallel_subtask and task.context < 200_000:
        return Provider.ANTHROPIC_SONNET   # or GEMINI_FLASH
    if task.context > 500_000:
        return Provider.GEMINI_FLASH
    if task.modality == "voice":
        return Provider.OPENAI_REALTIME
    if task.tenant_requires_azure:
        return Provider.MICROSOFT_MAI_CODE
    return Provider.ANTHROPIC_SONNET  # default
```

Log **`{provider, task_id, tokens_in, tokens_out, latency_ms, cost_usd}`** per request — that's the data both your June 15 audit and any future interview answer about "model routing" needs.

**Sources:**
- [Air Street Press — State of AI: May 2026](https://press.airstreet.com/p/state-of-ai-may-2026) `[analysis]`
- [Releasebot — Anthropic Release Notes June 2026](https://releasebot.io/updates/anthropic) `[aggregator]`
- [TechCrunch — With Gemini 3.5 Flash, Google bets its next AI wave on agents](https://techcrunch.com/2026/05/19/with-gemini-3-5-flash-google-bets-its-next-ai-wave-on-agents-not-chatbots/) `[secondary]`

### Why it matters to you

- **Job lens:** The router-with-logging is now a 1-day artifact (the SDKs are all stable). Push it to a public GitHub repo, write a 500-word README, and you have something to *show* during any interview about cost-aware AI engineering.
- **Startup lens:** The router is also the **simplest possible MVP** of a cost-control product — your own usage log becomes the proof point.
- **Insight:** The *list of providers* changes monthly; the *shape of the routing decision* (task → cost-utility tradeoff → provider) does not. **Build the shape; swap the providers.**

---

## 4. MCP Atlas + MCPAgentBench as your verification stack {#4-mcp-verification}

A practical follow-on to last week's mention of **MCP-Atlas** ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)): the new **MCPAgentBench** (arXiv 2512.24565) is now available and offers a **dynamic sandbox + distractor-tool evaluation** against 20,000+ real MCP tools. This is the *exact* skill the Opus 4.8 dynamic-workflow demo can show off — wire your workflow to one MCP server, run it against MCPAgentBench-style distractors, log the pass-rate.

**Sources:**
- [arXiv 2512.24565 — MCPAgentBench: A Real-world Task Benchmark for Evaluating LLM Agent MCP Tool Use](https://arxiv.org/abs/2512.24565) `[primary]`

### Why it matters to you

- **Job lens:** *"How do you evaluate an agent's tool use?"* — answer with **MCPAgentBench's dynamic-sandbox-with-distractors framing**, citing the paper. Most candidates will still be citing AgentBench from 2023.
- **Startup lens:** A SaaS that runs MCPAgentBench-style continuous evaluation against a customer's agent + their own MCP servers is an unbuilt category. (Judgment Labs is closest; not the same.)
- **Insight:** Real-tool eval just professionalized. Don't get caught citing mock-tool benchmarks in mid-2026.

→ Cross-link: [`04` §1 MCPAgentBench + ETOM + MSB triple](./04-research-progress.md#1-mcpagentbench).
