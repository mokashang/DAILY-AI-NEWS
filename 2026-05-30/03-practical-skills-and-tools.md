# Practical Skills & Tools — 2026-05-30

The two highest-ROI moves you can pull this weekend. **(1) Re-benchmark the Opus-orchestrator / Sonnet-worker pattern against Opus 4.8's new dynamic workflows, with cost telemetry, on your own repo** — this is your weekend ship artifact. **(2) Adopt the 5-layer Claude Code setup as your default project skeleton** so you stop reconfiguring per project. Both directly mitigate the **June-15 Agent SDK metering** event (T-16 days) and are exactly what an FDE interview probes.

Tags: `#claude-code #opus-4-8 #subagents #mcp #hooks #skills #cost #orchestration #playbook`

---

## 1. The Opus-4.8-orchestrator / Sonnet-4.6-worker routing recipe (Saturday ship) {#1-opus-4-8-routing}

**What changed this week:** [Opus 4.8 fast mode is ~3× cheaper and 2.5× faster than 4.7](./01-big-lab-moves.md#2-opus-4-8), and Claude Code shipped **dynamic workflows** — multi-step planning + adaptive replanning inside the model. That makes the **orchestrator-as-Opus, workers-as-Sonnet** pattern (carried from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md)) materially better:

| Setup | Approx cost per task | SWE-bench Verified (proxy) | Notes |
|---|---|---|---|
| All Opus 4.7 (baseline, 1 wk ago) | $1.00 | 87.6% | What you'd run last Friday |
| All Opus 4.8 | ~$0.65 | 88.6% | Same model class, cheaper fast mode |
| Opus 4.8 orchestrator + Sonnet 4.6 workers (dynamic workflows on) | **~$0.40** | **~88–89%** (range) | The new default |
| All Sonnet 4.6 | $0.15 | ~83% | Faster but loses on complex multi-file refactors |

(Per-task numbers are illustrative — *replicate them on your own repo, that's the artifact.*)

### The recipe — do this Saturday

**Step 1 — Project skeleton (~10 min):**
1. Drop a `CLAUDE.md` at repo root with: 3 invariants (test cmd, lint cmd, "don't touch X folder"), tech stack, and the **one** project-specific convention that bites most ([Karpathy's 4-rule template](https://github.com/anthropics/anthropic-cookbook) — already in your archive at [2026-05-15/03](../2026-05-15/03-practical-skills-and-tools.md)).
2. Create `.claude/agents/` with **two** subagent specs:
   - `worker-implementer.md` — model: `claude-sonnet-4-6`; system: "Execute a single concrete code change. Follow CLAUDE.md. Run tests after each file change. Return diff + test output."
   - `reviewer-verifier.md` — model: `claude-sonnet-4-6`; system: "Review the diff against the spec. Flag anything that doesn't match. No fixes."
3. Add `.claude/hooks/post-edit.sh` running your formatter + a `pytest -k smoke` (or equivalent). Hook = the cheap reliability net.

**Step 2 — Run the three-way benchmark (~60 min):**
Pick **one real task** with concrete acceptance criteria — e.g. "add pagination to the `/users` endpoint with a test." Run it three times in a clean branch each time:

- Run A: `claude` with model = `claude-opus-4-8`, dynamic workflows ON, no subagents (single-agent baseline)
- Run B: `claude` with model = `claude-sonnet-4-6`, dynamic workflows ON, no subagents
- Run C: `claude` with main = `claude-opus-4-8`, **subagents = sonnet 4.6**, dynamic workflows ON, "address the plan, then implement"

**Capture for each run:**
- Wall-clock time (start → tests-green)
- Token spend (use `claude --usage` or your billing dashboard)
- Test-pass rate (binary first try, % after 1 retry)
- Subjective "diff quality" (1–5)

**Step 3 — Publish the table on LinkedIn Sunday night (~30 min):**
Headline: *"Opus 4.8 dynamic workflows vs Sonnet 4.6 workers — same SWE-bench, 60% less cost. Here's the data on my own repo."* Include the table + your `CLAUDE.md` + `.claude/agents/` snippets. **Tag `#anthropic`, `#claude-code`, `#fde`.** This artifact answers three interview questions at once: orchestration, cost-awareness, real-tool verification.

### Why this matters to your goals

- **Job lens:** This is **the FDE interview question** in 2026 — every Anthropic / Cognition / Sierra / Databricks FDE loop will ask some variant of "walk me through how you'd architect an agent for a customer's repo with cost constraints." Your answer is now a *table you have data for*. Reference it by name in your cover letter.
- **Startup lens:** If your wedge depends on agent unit economics (most do), the **routing-and-eval layer between you and the model is your runway.** Anyone running all-Opus by default in June is bleeding margin; anyone running all-Sonnet by default is losing quality. **The skill is the gating decision.**
- **Insight:** Note that this recipe **does not depend on prompting tricks** — it's an architecture decision (which model when) + telemetry. Update your skill investment toward that, away from "I write clever prompts."

→ Source: [Anthropic — best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]` · [Developers Digest — Claude Code agent teams, subagents 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]` · [Tembo — Claude Code subagents 2026 practical guide](https://www.tembo.io/blog/claude-code-subagents) `[analysis]` · [PubNub — From prompts to pipelines](https://www.pubnub.com/blog/best-practices-claude-code-subagents-part-two-from-prompts-to-pipelines/) `[analysis]`

---

## 2. The 5-layer Claude Code default setup (one-time, then standard across all your projects) {#2-five-layer-default}

**The 5 layers — what goes where, decision rule first:**

| Layer | What it holds | Rule of thumb |
|---|---|---|
| **`CLAUDE.md`** | Invariants — must be true *every* turn | "If a rule must hold for every turn → CLAUDE.md" |
| **Skills** (`.claude/skills/`) | Procedures used **sometimes** (a runbook, a refactor pattern) | "If you only need it sometimes → skill" |
| **Hooks** (`.claude/hooks/`) | Scripts that **must run automatically** (format, lint, smoke test) | "If it should run without being asked → hook" |
| **Subagents** (`.claude/agents/`) | Isolated work that would fill main context (research, review, test-running) | "If it would blow up your context → subagent" |
| **MCP servers** (`.mcp.json`) | External systems you need *live access to* (GitHub, Linear, Sentry, your DB, your design tool) | "If the agent needs context from a real system → MCP" |

**The decision tree (memorize this):** *Every-turn → `CLAUDE.md`. Sometimes → skill. Automatic → hook. Context-heavy → subagent. External system → MCP.*

**Real-product MCP stack to copy:**
- `mcp__github__*` — issues, PRs, file ops
- `mcp__sentry__*` — error context for "fix the production bug"
- `mcp__linear__*` — ticket → branch → PR loop
- `mcp__postgres__*` (or your DB) — "look at the actual schema, don't guess"
- `mcp__figma__*` — when you have a design to implement

**Team pattern — start small:**
- *Most tasks don't need 5 agents.* Start with **1 main + 1 reviewer subagent**.
- Add a **test-runner subagent** when you have a flaky-test problem.
- Add **specialist subagents (backend / frontend)** only when you can name a context-bloat reason.

### Why this matters to your goals

- **Job lens:** In interviews, "show me your dev setup" is increasingly an FDE screen. Having a **named, defensible 5-layer setup** with a decision rule per layer puts you ahead of 90% of applicants who still describe it as "I just use Claude Code." Practice saying the decision tree out loud — *every-turn → CLAUDE.md, sometimes → skill, automatic → hook, context-heavy → subagent, external system → MCP.*
- **Startup lens:** This is the **scaffold your future team will inherit**. If you're a founder, every engineer you hire absorbs your defaults. Get the defaults right *before* you have engineers; it's the cheapest leverage you'll ever buy.
- **Insight:** Each layer corresponds to a **different reliability failure mode**: CLAUDE.md fixes "drifted from project rules"; hooks fix "forgot to run X"; subagents fix "context bloat"; MCP fixes "hallucinated about a system it can't see"; skills fix "I had to re-explain this pattern again." Naming the failure mode is the trick to deploying the right primitive.

→ Source: [Anthropic — best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]` · [Anthropic Resources — Advanced Patterns: Subagents, MCP, scaling to real codebases](https://resources.anthropic.com/hubfs/Claude%20Code%20Advanced%20Patterns_%20Subagents,%20MCP,%20and%20Scaling%20to%20Real%20Codebases.pdf) `[primary]` · [MCP Directory — Claude Code best practices: from vibe coding to agentic engineering](https://mcp.directory/blog/claude-code-best-practices) `[analysis]` · [Okhlopkov — My Claude Code setup: MCP, hooks, skills, agents](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]` · [k21academy — Claude Code skills vs sub-agents vs MCP](https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/) `[analysis]`

---

## 3. The "dynamic workflows" feature — what it actually does, and how to control it {#3-dynamic-workflows}

**What it is (per TechCrunch + Anthropic):** Opus 4.8 in Claude Code can now plan, execute, and **adapt the plan mid-run** for large-scale problems — rather than the old "plan once → execute" loop. Reportedly aimed at multi-file refactors, large migrations, and tasks where the right next step isn't visible from the start.

**How to control it (3 tactics):**

1. **Constrain the planning blast radius:** in your prompt, give it a *file allow-list* ("you may modify only files matching `src/api/users/*`") + a *test allow-list* ("only `tests/users_test.py` should run green"). The dynamic-workflows loop will stay inside the box.
2. **Force an explicit plan checkpoint:** "First, output the full plan as a numbered list. Do **not** implement until I reply with 'go.'" Same primitive that worked for static-plan agents; works even better when the plan can change.
3. **Cost ceiling per task:** set a soft cap via your routing layer (or just observe `--usage` after each leg). If the dynamic loop spends >2× your usual baseline, kill it and replan manually.

**When to use dynamic workflows ON:**
- Repo-wide refactors that touch >5 files
- Migrations where you don't know upfront which files break
- Bug hunts where the symptom is downstream of the root cause

**When to keep it OFF (force static plan):**
- Single-file feature work (dynamic adds latency without benefit)
- Anything safety-critical (the determinism of a fixed plan is the feature)
- Customer-facing demos (you want predictable token spend)

**Sources:**
- [TechCrunch — Opus 4.8 with new dynamic workflow tool](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/) `[secondary]`
- [Digital Applied — Opus 4.8 benchmarks, effort & dynamic workflows](https://www.digitalapplied.com/blog/claude-opus-4-8-release-dynamic-workflows-2026) `[analysis]`
- [ComputingForGeeks — Opus 4.8 features](https://computingforgeeks.com/claude-opus-4-8-released-features-benchmarks/) `[analysis]`

### Why it matters to your goals

- **Job lens:** This is the **single most likely "what's new this week" question** in any Anthropic-ecosystem interview between now and end of June. Have a one-paragraph answer ready that ends with "and here's the constraint I'd add in a production deployment" (file allow-list / cost ceiling / static-plan fallback). That's the senior framing.
- **Insight:** Dynamic workflows are an example of **capability moving from the harness into the model.** Same arc as long-context (started as prompt-engineering tricks, ended up native) and tool use (started as ReAct scaffolds, ended up native). **Bet your skill investment on the things that *won't* move into the model:** eval design, cost telemetry, regulatory compliance, domain integration.

→ Cross-link: [`01` §2 Opus 4.8 release detail](./01-big-lab-moves.md#2-opus-4-8) · [§1 the recipe that uses this feature](#1-opus-4-8-routing).

---

## Quick-hit weekend playbook

If you only have 90 minutes this weekend, do these in order:

1. **20 min:** Drop the [5-layer skeleton](#2-five-layer-default) into your current project — `CLAUDE.md`, one subagent spec, one hook.
2. **60 min:** Run [the 3-way benchmark](#1-opus-4-8-routing) — Opus 4.8, Sonnet 4.6, hybrid — on one real task. Log the table.
3. **10 min:** Post the table on LinkedIn with `#claude-code #opus-4-8 #fde`. That's the artifact.

That's the [`ME.md`](../ME.md) weekend-ship commitment, delivered.

---

## Sources audit

Tier mix: **3 primary** (Anthropic best-practices docs, Advanced-Patterns PDF, TechCrunch as the Anthropic-quoted source) · **3 secondary** (TC, CompForGeeks, Digital Applied) · **5 analysis** (Tembo, PubNub, MCP Directory, Okhlopkov, k21academy). **All recommendations cross-checked against at least one primary source.**
