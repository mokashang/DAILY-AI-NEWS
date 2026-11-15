# Practical Skills & Tools — 2026-05-30

Saturday is **ship day**. Friday's plan ([2026-05-29/03 §1 Dynamic Workflows demo](../2026-05-29/03-practical-skills-and-tools.md#1-dynamic-workflows)) is still the right artifact — but the [Opus 4.8 day-2 failure-mode sort](./01-big-lab-moves.md#1-opus-4-8-day-2) means you now ship it with **three Opus-4.8-specific patches** that *also* answer three additional interview questions. One artifact, six interview answers. Sunday 7–9 PM PT LinkedIn post timing.

Tags: `#claude-code #opus-4-8 #dynamic-workflows #subagents #cost #orchestration #fde-portfolio`

---

## 1. The weekend ship — Dynamic Workflows demo with 3 Opus-4.8 patches {#1-weekend-ship}

**The base artifact (carried from Friday):** A **Dynamic Workflows migration demo** on one repo you own — Claude Code writes a JS orchestration script that spawns sub-agent trees (cap: 1,000 agents / 16 concurrent) to execute a real codebase migration against the test suite. See [2026-05-29/03 §1](../2026-05-29/03-practical-skills-and-tools.md#1-dynamic-workflows) for the spec.

**Three patches you add today, because the day-2 sort surfaced specific failure modes:**

### Patch A — Sonnet-4.6 fallback subagent for refused security steps

**Why:** Day-2 HN reports flag **Opus 4.8 over-refusing on legitimate security code** (red-team scripts, fuzzers, hardening code) — "malware reminder" patterns. If your migration touches *any* security-adjacent surface (auth, crypto, input validation, parsing), the orchestrator will hit refusals.

**How:**
```
# .claude/agents/security-fallback.md
model: claude-sonnet-4-6
system: |
  You handle steps the Opus orchestrator refused on safety/security grounds.
  Verify the task is legitimate (not actual malware). If so, execute.
  If genuinely unsafe, return "REFUSE_ESCALATE" for human review.
```

In your orchestrator script, catch the refusal pattern (`"I can't help with"` + `"security"` heuristic) → route the step to `security-fallback` subagent → log the routing decision.

### Patch B — Turn-by-turn fallback for one-shot tasks

**Why:** Multiple day-2 reports of **Opus 4.8 underperforming 4.7 on simple one-shot prompts** (UI generation, missed-obvious-instructions). Migrations have a long-tail of small one-shot prompts mixed in with multi-step planning steps; you don't want either failure mode.

**How:** In your orchestrator script, add a step-classifier (rough heuristic: word-count + tool-count on the planned subtask):
- **Multi-step / >5 tools / >200 words:** route to Opus 4.8 (the bigger-task strength)
- **One-shot / ≤2 tools / <100 words:** route to **Claude Sonnet 4.6** (faster, cheaper, no regression risk)
- **Anything in between:** Opus 4.7 as the conservative-middle (still cheaper than 4.8 fast mode is for single-shots)

This is **the model-routing skill in production form** — exactly what an FDE interview probes.

### Patch C — Per-step token + cost log (the June-15-metering mitigation)

**Why:** Anthropic's Agent SDK metering goes live **June 15 — T-16 days**. The post-metering bill = sum of per-step costs. **You can't optimize what you don't measure.**

**How:** After each subagent run, append to `costs.jsonl`:
```jsonl
{"step_id": "...", "agent": "implementer-1", "model": "claude-sonnet-4-6", "input_tokens": 4521, "output_tokens": 892, "wall_ms": 12380, "test_passed": true, "cost_usd": 0.0223}
```

After the full migration: a summary table of **cost-per-agent-step by model**, plus the **total run cost**. This *is* the data the FDE interviewer wants to see, and almost no applicant brings it.

---

### The 90-minute Saturday plan (revised)

| Block | Minutes | What you do |
|---|---|---|
| **1. Setup** | 15 | Pick the repo + migration target (1 page README). Add `.claude/agents/security-fallback.md`. |
| **2. Orchestrator** | 30 | Have Opus 4.8 generate the Dynamic Workflows JS script with step-classifier + cost log baked in. |
| **3. Run** | 30 | Execute bounded at 16 concurrent / ≤100 total subagents. Watch the cost log scroll. |
| **4. Write-up** | 15 | One README block + the cost-summary table + the routing decisions. Commit. |

**Sources:**
- [Anthropic — Introducing Claude Opus 4.8 (dynamic workflows)](https://www.anthropic.com/news/claude-opus-4-8) `[primary]`
- [The New Stack — Opus 4.8: dynamic workflows + effort controls](https://thenewstack.io/claude-opus-48-release/) `[secondary]`
- [Anthropic — best practices for Claude Code](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Anthropic Resources — Advanced Patterns: Subagents, MCP, scaling to real codebases (PDF)](https://resources.anthropic.com/hubfs/Claude%20Code%20Advanced%20Patterns_%20Subagents,%20MCP,%20and%20Scaling%20to%20Real%20Codebases.pdf) `[primary]`
- [Simon Willison — Opus 4.8 "modest but tangible improvement"](https://simonwillison.net/2026/May/28/claude-opus-4-8/) `[analysis]` (the day-2 read motivating the patches)
- [2026-05-29/03 §1 Friday Dynamic Workflows spec](../2026-05-29/03-practical-skills-and-tools.md#1-dynamic-workflows) `[archive]`

### Why it matters to your goals

- **Job lens:** **One artifact, six interview answers:** (1) parallel subagent orchestration, (2) verification against real tests, (3) cost-aware routing, (4) failure-mode mapping (the day-2 patches), (5) graceful degradation (security-fallback + one-shot fallback), (6) multi-vendor judgment (you chose to mix Opus 4.8 / Opus 4.7 / Sonnet 4.6 with reasons). Almost no new-grad applicant brings this depth. **The cost-log alone puts you in the top 1% of FDE applicants this week.**
- **Startup lens:** **Each of the three patches is a productizable wedge:**
  - Patch A → "security-aware AI dev environment" (intercept refusals, route safely)
  - Patch B → "cost-and-quality router for AI dev tools" (the OpenRouter pattern inside an IDE)
  - Patch C → "AI dev observability" (cost / token / quality per agent step)
  - Don't pursue all three. Pick the one that grates *you* most when you run the migration tonight. That's the wedge.
- **Insight:** **Failure-mode mapping is the new senior-engineer signal.** A junior engineer demos a feature. A senior engineer demos a feature *plus* the named failure modes *plus* the graceful-degradation path. The day-2 sort gives you the failure modes for free; you just have to wire them in. Make this your habit for every model release in 2026.

→ Cross-link: [`01` §1 day-2 sort that motivates the patches](./01-big-lab-moves.md#1-opus-4-8-day-2) · [2026-05-29/03 §1 base Dynamic Workflows spec](../2026-05-29/03-practical-skills-and-tools.md#1-dynamic-workflows) · [2026-05-22/03 the orchestrator/worker cost lever](../2026-05-22/03-practical-skills-and-tools.md).

---

## 2. The Sunday 7–9 PM PT LinkedIn post — exact template {#2-sunday-post}

**Why timing:** Sunday evening is when hiring managers + senior engineers scroll LinkedIn before Monday. Lowest feed competition; recruiters re-check Monday morning. **Don't post Monday — you'll be buried under everyone else's "weekly AI roundup."**

**Headline pattern (copy-edit to taste):**
> *"Opus 4.8 dynamic workflows — what worked, what didn't, and the routing fallback I added (with cost data)."*

**Structure (3 short blocks + 1 table + closing line):**

1. **One-sentence frame:** "Shipped a 4-file migration with Claude Code's new Dynamic Workflows + Opus 4.8 over the weekend — here's the data plus the day-2 failure modes I had to route around."

2. **The cost table (the only "image" — paste as code-block markdown table for native rendering):**

| Step type | Routed to | Avg cost/step | Test-pass first try |
|---|---|---|---|
| Multi-step refactor | Opus 4.8 (dyn workflows) | $0.041 | 92% |
| One-shot UI tweak | Sonnet 4.6 | $0.004 | 95% |
| Security-adjacent (Opus refused) | Sonnet 4.6 fallback | $0.005 | 88% |
| **Total run** | | **$N.NN** | **N migrations completed** |

(*Fill in with your actual numbers. The numbers don't need to be impressive — they need to be **real**.*)

3. **The 3-failure-mode block** (verbatim from your README):
   > *Two failure modes the day-2 Opus 4.8 sort flagged, and how I routed around them: (a) over-cautious refusals on legitimate security code → Sonnet 4.6 security-fallback subagent. (b) Turn-by-turn regressions on one-shot prompts → step-classifier routes one-shots to Sonnet 4.6 by default.*

4. **The closing line / comment-bait:**
   > *"Curious if anyone else is seeing the security-refusal pattern — share the prompt that triggered it for you."*

**Tags:** `#claude #claudecode #anthropic #opus48 #fde #forwarddeployedengineer #aiengineer #dynamicworkflows`

**Sources:**
- [Pragmatic Engineer — state of the SWE job market 2026 (LinkedIn timing rationale)](https://newsletter.pragmaticengineer.com/p/state-of-the-job-market-2026) `[analysis]`

### Why it matters to your goals

- **Job lens:** **By Monday 10 AM PT, that post is the artifact you link in 2 FDE applications.** Don't apply with "I'm interested in AI" — apply with a link to the post and a one-line in the cover letter: "*Built and posted a 4.8 vs Sonnet 4.6 vs Opus 4.7 routing table on a real repo this weekend; here's the link.*" That's the differentiator.
- **Insight:** **Sunday-night posts compound.** Same post on Sunday 8 PM PT vs Tuesday 11 AM PT typically gets 3–5× the impressions for a technical-engineering audience because the feed is empty and the audience is browsing-with-intent. **Use the window.**

→ Cross-link: [`05` §3 the Saturday-artifact career angle](./05-career-and-startup.md#3-assurance-lane) · [§1 the artifact](#1-weekend-ship).

---

## 3. Quick "did I do everything?" weekend checklist {#3-checklist}

If you only check four boxes this weekend, check these:

- [ ] **Saturday afternoon (90 min):** ship the artifact in [§1](#1-weekend-ship). Cost log + 3 patches.
- [ ] **Saturday evening (25 min):** skim the [OpenAI Frontier Governance Framework](https://openai.com/index/openai-frontier-governance-framework/) end-to-end. Vocabulary for 12 months.
- [ ] **Sunday 7–9 PM PT (15 min):** post per [§2](#2-sunday-post). Tagged right. Comment-bait closing line.
- [ ] **Sunday 10–11 PM PT (15 min):** file 2 FDE / Solutions / Customer-Eng applications via [`05` §1](./05-career-and-startup.md#1-jobs-apocalypse) list. Link the post in cover letters.

Optional fifth box: **30 min on [`STARTUPS.md`](../STARTUPS.md) re-pricing** after the Cognition $26B / 53× ARR comp and the post-Series-H Anthropic supply lock-in. Friday's [2026-05-29 watchlist](../2026-05-29/00-tldr.md) is the prompt.

---

## Sources audit

Tier mix: **3 primary** (Anthropic Opus 4.8 announcement, best-practices docs, Advanced Patterns PDF) · **2 secondary** (The New Stack, Pragmatic Engineer) · **1 analysis** (Simon Willison) · **3 archive cross-links**. **Two of three patches are directly motivated by named day-2 community findings (HN security-refusal pattern, Bridgewater + Vibe Check one-shot reports) — not speculation.** Patch C (cost log) is structural prep for the [2026-05-16 metering announcement](../2026-05-16/), not a day-2 finding.
