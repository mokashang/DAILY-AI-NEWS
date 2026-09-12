# Practical Skills & Tools — 2026-06-07

Sunday is the right day to consolidate. Three things to act on **before Monday**: (1) the **consensus 2026 Claude Code stack** crystallized this week into a clean five-layer mental model — adopt it; (2) **the Agent SDK metering flip is T-minus 8 days** — this is your last full weekend to audit and route; (3) a **30-minute WWDC pre-stage doc** prevents tomorrow from being noise.

Tags: `#claude-code #mcp #subagents #hooks #skills #cost #orchestration #routing #wwdc`

---

## 1. The consensus 2026 Claude Code stack — five layers, one decision rule {#1-five-layer-stack}

**What's settled:** Multiple high-signal practitioner writeups landed this week (PubNub, SmartScope, Crio, Developers Digest, mcp.directory) and they **converge on the same five-layer architecture**. Adopt it as your baseline tonight.

| Layer | What it is | What it's for | Decision criterion |
|---|---|---|---|
| **`CLAUDE.md`** | Plain-Markdown project rules at repo root | Things that must be true *every* turn | "If skipping it would break behavior anywhere → put it here" |
| **MCP servers** | External tools/data exposed via MCP protocol | Connecting Claude to GitHub, Linear, Sentry, Postgres, Figma, internal APIs | "If it lives outside the repo and needs read/write → MCP" |
| **Skills** | Reusable workflows ("how to do X") loaded on demand | Procedures you need *sometimes*, not every turn | "If it's a recipe with steps, not a rule → skill" |
| **Hooks** | Automation + safety scripts on lifecycle events | Auto-format on Stop, secret-scan on PreToolUse, etc. | "If it should run *automatically*, no decision required → hook" |
| **Subagents** | Isolated workers spawned with their own context | Research, review, or any task that would pollute main ctx | "If it would do 20 file reads / 12 greps → subagent" |

The single most-quoted line across writeups this week:

> *"If an instruction must be true for every turn, it belongs in `CLAUDE.md`. If it's a procedure you only need sometimes, make it a skill. If it's a script that should run automatically, make it a hook. If it would fill the main context, delegate it to a subagent."*

**Sources:**
- [Claude Code docs — Best practices](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Anthropic — Building agents with the Claude Agent SDK](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk) `[primary]`
- [okhlopkov — My Claude Code setup: MCP servers, hooks, skills and agents (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[practitioner]`
- [Developers Digest — Claude Code agent teams, subagents, and MCP: the 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[practitioner]`
- [SmartScope — Claude Code advanced best practices: 11 practical techniques](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[practitioner]`
- [PubNub — Best practices for Claude Code subagents](https://www.pubnub.com/blog/best-practices-for-claude-code-sub-agents/) `[practitioner]`
- [mcp.directory — Claude Code best practices: from vibe coding to agentic engineering (2026)](https://mcp.directory/blog/claude-code-best-practices) `[practitioner]`

### How to operationalize tonight (90 minutes)

1. **`CLAUDE.md` (15 min).** Pin: language/version, build command, test command, lint command, the four files an agent must read before writing code, what NOT to touch. Reference [Karpathy's CLAUDE.md template](https://github.com/karpathy/CLAUDE.md) for shape (the 4-rule playbook from [2026-05-15](../2026-05-15/03-practical-skills-and-tools.md)).
2. **MCP (30 min).** Install **filesystem + git + GitHub + one project-specific server** (Postgres, Linear, Sentry — whichever applies). Stop there. **Don't install seven MCP servers on day 1**; each one is context cost.
3. **One skill (20 min).** Write your single most-repeated workflow as a skill (the `code-review` pattern from [Anthropic's skills examples](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk) is the canonical demo).
4. **One hook (15 min).** Add **PreToolUse hook for `Bash`** that blocks destructive commands (`rm -rf`, `git push --force`, `git reset --hard`). This single hook prevents the most common agentic accident.
5. **One subagent (10 min).** Define a **"Explore"-style research subagent** with one clear input/output contract — spawn it whenever you need to grep across a large repo without polluting main context.

### Why it matters to you

- **Job lens:** Every line item above is now expected fluency in interviews for **AI Engineer**, **AI Integration Engineer**, and **FDE** roles at the labs. The interview signal isn't "you used Claude Code" — it's "**you can name the five layers and choose between them by decision criterion**." A 30-second answer using the decision rule above instantly outranks 90% of candidates.
- **Startup lens:** The five-layer stack is also the **service blueprint** for any AI-consulting or FDE-as-a-service business. When you sell a customer on Claude integration, your delivery is literally these five layers customized to their stack. Productize each layer (templates for `CLAUDE.md` per industry, library of MCP servers per ERP, library of skills per workflow, library of hooks for compliance) and you have a repeatable consulting wedge.
- **Insight:** The shift in 2026 isn't *what Claude can do* — it's that **the surface area of how you configure Claude has standardized**. Five layers, one decision rule. When a system reaches the "five composable primitives" stage, the **practitioner skill premium falls** (anyone can copy the template) and the **judgment premium rises** (which layer is the *right* place for this concern?). Train the judgment, not the syntax.

→ Cross-link: [Karpathy's CLAUDE.md, 2026-05-15](../2026-05-15/03-practical-skills-and-tools.md) · [`04` §1 the research thread underneath these layers](./04-research-progress.md#1-agent2-rlbench).

---

## 2. T-minus 8 days to Agent SDK metering — the cost-routing artifact to ship this week {#2-metering-prep}

**What's the deadline:** **Monday June 15, 2026** — Anthropic's Agent SDK / `claude -p` / GitHub Actions / OpenClaw traffic moves to a **separate credit pool billed at API list rates** (Pro $20 / Max-5x $100 / Max-20x $200), per the [2026-05-16 announcement](../2026-05-16/01-big-lab-moves.md). This week is **the last full work-week before that flip**.

The mitigation playbook (in order of ROI per hour):

1. **Prompt caching (1 hour).** 60–90% input-cost savings on repeated context. Reference [2026-05-17 prompt-caching writeup](../2026-05-17/03-practical-skills-and-tools.md).
2. **Opus-orchestrator + Sonnet-worker split (2 hours).** ~40% cheaper than all-Opus per the [2026-05-22/03 §1 numbers](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost). Set up tonight if not done.
3. **Cost-aware routing across 5 providers (3 hours).** Build a thin router that picks among {Opus 4.7, Sonnet 4.6, Gemini 3.5 Flash @ $1.50/M, GPT-5.5, MAI-Code-1-Flash} by **task class × cost-floor × accuracy-target**. This is the artifact below.
4. **Token audit on your last 14 days of usage (30 min).** Anthropic exposes a usage dashboard — pull it, classify spend by job-shape, find your top-3 spend drivers, redirect those specifically.

### The artifact to ship this week (the one with the highest career ROI)

**Project:** `cost-aware-agent-router-2026.md` — a **public** writeup + minimal code repo that documents:

- The **June 15 metering change** (what's billed where, with primary citation).
- A **single Python class** (`Router`) that takes a task description and routes among 5 providers based on three policies: *cheapest-good-enough*, *quality-first*, *latency-first*.
- A **per-step cost log** (tokens × $/M-token by model per task; sums per session).
- **One real benchmark**: run the same 20 tasks through each policy, log accuracy + total cost, publish the table.
- **One real MCP server**: do the benchmark *with tool calls* against an actual MCP server (filesystem or git) so it's not a chat-only artifact. Cite [MCP-Atlas](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) as inspiration.

That single repo answers **three interview questions** in one artifact: orchestration, real-tool verification, and cost-aware routing. It's the highest-leverage thing you can ship before the June 15 deadline.

**Sources:** *(carried forward from prior editions; primary cites)*
- [Anthropic Agent SDK metering announcement, 2026-05-16](../2026-05-16/01-big-lab-moves.md) `[primary]`
- [Gemini 3.5 Flash pricing $1.50/M in · $9/M out, 2026-05-19](../2026-05-19/01-big-lab-moves.md) `[primary]`
- [Opus-orchestrator/Sonnet-worker cost math, 2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) `[analysis]`

### Why it matters to you

- **Job lens:** *Cost-aware routing* shifted from "nice-to-have" to "required" at every AI Integration / FDE / Solutions Engineer role in 2026. The single most-asked interview question I've seen reported this month: **"You're running an agent in production. How do you decide which model to use for each step, and how do you measure it?"** The artifact above is the literal answer.
- **Startup lens:** The same primitive is a **product**. Every series-A AI startup runs a model bill they can't fully explain — sell them a per-step cost dashboard + auto-router and you're invoicing within 30 days. The defensible version is **per-customer routing policies** (each customer's tradeoff curve becomes a moat).
- **Insight:** What's changed in 8 months: **the cheap path is no longer "just use the smallest model."** It's "**use the right model for each step, with the right caching, with a verifier on the cheap output.**" That's a fundamentally different skill — and the skill that survives the next price/perf shift, because it's about composition, not vendor choice.

→ Cross-link: [2026-05-22/03 §1 the orchestrator/worker split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`05` §1 the bifurcation this skill protects you from](./05-career-and-startup.md#1-bifurcation).

---

## 3. The 30-minute WWDC pre-stage doc (do this Sunday afternoon) {#3-wwdc-prestage}

**Why:** Tomorrow's keynote (Mon June 8, 10 AM PT) will hit you with **6–9 announcements in ~90 minutes**, most of them speculative right up to the moment of shipping. The difference between **noise** and **signal** is whether you have a **scoring rubric ready before the keynote**. Build it now.

### The template (copy-paste into a new note)

```
# WWDC 2026 — Live Scoring (T+0 at 10 AM PT, Mon Jun 8)

| # | Prediction (pre-keynote) | Source | What actually shipped | Implication for me |
|---|---|---|---|---|
| 1 | Siri rebuilt on 1.2T-param custom Gemini, ~$1B/yr license | Tech Times / Technobezz | ___ | ___ |
| 2 | "Search or Ask" multi-AI panel (Siri / ChatGPT / Gemini) | Newsweek / FourWeekMBA | ___ | ___ |
| 3 | App Intents / agentic OS hooks in iOS 27 | Multiple | ___ | ___ |
| 4 | Foldable iPhone preview | Crypto Briefing | ___ | ___ |
| 5 | macOS / iPadOS / watchOS / visionOS branding refresh | TechRadar | ___ | ___ |
| 6 | Apple Intelligence developer SDK formal release | Multiple | ___ | ___ |
| 7 | Tim Cook farewell framing + Ternus appearance | TechRadar | ___ | ___ |
| 8 | (open slot for surprise) | — | ___ | ___ |
| 9 | (open slot for surprise) | — | ___ | ___ |

## Action checklist (decide *before* the keynote)
- [ ] If Gemini-Siri deal confirmed → update WATCHLIST + apply to one Apple Intelligence / Apple ML role today
- [ ] If "Search or Ask" panel confirmed → update LinkedIn skills with "Apple Intelligence Extensions"
- [ ] If App Intents = MCP-shaped → start the MCP↔App Intents bridge demo this week
- [ ] If SDK ships day-of → install + screen-record a 60-sec demo before bed Monday
- [ ] Publish the scored table on LinkedIn within 2 hours of keynote end
```

### Why it matters to you

- **Job lens:** A **2-hour-post-keynote LinkedIn post** with a **scored prediction table** is one of the highest-ROI personal-brand actions you can take all year. Recruiters at Apple, Google, and Anthropic are all monitoring WWDC chatter — your post lands in the window where attention is highest and competing content is lowest.
- **Startup lens:** Whichever of the 6+ announcements actually ships becomes a **30-day startup wedge.** Decide *before* the keynote which 2 you'd be willing to build against if confirmed; that pre-commitment is what separates founders from observers.
- **Insight:** The most underrated keynote-watching skill is **pre-committing to your scoring rubric.** Watching live without it, you'll over-weight whatever was emphasized on stage. With it, you'll catch the *under-emphasized* announcement that turns out to matter most (e.g., the way Anthropic's MCP was under-emphasized at first reveal, then turned into a year-defining standard).

→ Cross-link: [`01` §2 the keynote preview](./01-big-lab-moves.md#2-wwdc).

---

## 4. Three small tips that compounded this week {#4-small-tips}

Quick hits, no deep dive — each is a 5-minute upgrade:

- **Spawn the subagent *the moment* a task would pollute main context.** The classic mistake (across every writeup this week): doing 20 file reads + 12 greps in main, then trying to plan with all that noise loaded. Spawn an Explore subagent, get a report back, plan clean. → [SmartScope writeup](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/)
- **Feature-specific subagents beat role-named ones.** A subagent called `migrate-from-rest-to-graphql` beats one called `backend engineer`. Specificity buys better tool selection and tighter context. → [PubNub writeup](https://www.pubnub.com/blog/best-practices-for-claude-code-sub-agents/)
- **Plan → annotate → "address all notes, don't implement yet"** loop (carried from [2026-05-22](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)). The middle step is the reliability primitive — it forces the model to *think about the diff* before producing it.

---

## 5. The Sunday-evening action stack

In execution order, 2 hours total:

1. **(45 min)** Write the 5-layer setup into your top-2 active repos — `CLAUDE.md`, one MCP, one hook, one skill, one subagent definition.
2. **(30 min)** Pre-stage the WWDC scoring table from §3 above.
3. **(45 min)** Sketch the cost-router repo structure from §2 (just the README + the empty `Router` class with method signatures + the benchmark plan) — finish the implementation Mon/Tue evenings.

If you only have 45 minutes: **do step 1.** Everything else compounds off that base.
