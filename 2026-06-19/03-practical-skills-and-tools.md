# Practical Skills & Tools — 2026-06-19

This is a **plan-the-weekend** edition. Three things land Monday: **GPT-5.6 launch** ([`01` §2](./01-big-lab-moves.md#2-gpt56-imminent)), **second-week metering bill** ([`02` §2](./02-new-emerging.md#2-metering-day5)), and the **June 22 Fable 5 pricing cliff** ([`01` §1](./01-big-lab-moves.md#1-fable-day8)). You have 60 hours to make sure your stack is ready for all three. The single artifact that solves it: a **4-line multi-vendor router shim with `fallbackModel` configured + 30-prompt eval harness + cost trace**, pushed Sunday 10 PM PT.

Tags: `#playbook #weekend-artifact #router #cost #orchestration #portfolio`

---

## 1. The weekend-sprint plan: 4-line multi-vendor router shim {#1-router-shim}

**The artifact (build Saturday, refine Sunday):**

A small repo — `multi-vendor-claude-router` or similar — that demonstrates a **production-shaped agent team**, robust to a Fable-5-style outage, with predictable per-step cost, and verified against a 30-prompt eval harness. One repo, three FDE-interview answers (orchestration · cost · verification), one demo gif.

**The routing config (the literal 4 lines):**

```yaml
# router.yaml
orchestrator:    Opus-4.8         # planner + integration; high-judgment turns only
worker:          Sonnet-4.6       # bounded, well-scoped subtasks; parallelizable
verifier:        Haiku-4.5        # always-on guard (TrajAD pattern; cheap enough to keep on)
fallbackModel:   [Sonnet-4.6, Haiku-4.5, GPT-5.5, Gemini-3.5-Flash]  # degrade gracefully
```

**The 6-step weekend recipe:**

1. **Fri night, 30 min** — set up the empty repo + `README.md` skeleton + plan the file structure.
2. **Sat morning, 2 hr** — copy the cost-routing playbook from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) into actual working code; wire the Opus / Sonnet / Haiku team against the Anthropic API.
3. **Sat afternoon, 2 hr** — add the non-Anthropic leg (GPT-5.5 + Gemini 3.5 Flash) with the fallback chain. Test that a forced Opus rate-limit fails over correctly.
4. **Sun morning, 2 hr** — build the 30-prompt eval harness. Use the **τ²-Bench / MCP-Atlas / Toolathlon** patterns ([2026-06-14/04](../2026-06-14/04-research-progress.md) · [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)). At least one real MCP server in the eval (not a mock).
5. **Sun afternoon, 1 hr** — record the cost trace; build the comparison table (model × tokens × dollars × pass-rate); generate the demo gif.
6. **Sun 10 PM PT** — push, write a 6-line README.md preface that **specifically references the June 15 metering / June 22 Fable cliff / GPT-5.6 launch context** so the artifact is timestamped to the moment.

**Sources (the doc trail you'll cite in the README):**
- [Claude Code Docs — fallbackModel configuration](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Anthropic — Claude Code best practices (official)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [2026-05-22/03 §1 — Opus/Sonnet/Haiku cost split (~40% cheaper)](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) `[primary, archive]`
- [2026-06-14/01 §1 — Fable 5 export-control shutdown context (why robustness matters)](../2026-06-14/01-big-lab-moves.md) `[primary, archive]`
- [2026-05-22/04 §1 — MCP-Atlas / Toolathlon real-tool eval patterns](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) `[primary, archive]`
- [2026-06-14/04 — τ²-Bench dual-control Dec-POMDP pattern](../2026-06-14/04-research-progress.md) `[primary, archive]`

### Why it matters to you

- **Job lens:** This single repo is **literally** the FDE / AI Integration Engineer interview rubric. *"I built and ran a multi-vendor agent team during a real frontier-model regulatory outage, with predictable per-step cost and execution-based eval against real MCP servers."* Every clause of that sentence maps to a question you'll be asked in 3 separate interview loops.
- **Startup lens:** The repo *is* a v0 of a fundable thesis (cost-aware multi-vendor agent runtime as a service). If during Sunday you find the harness is shaped enough to point a customer at, note that as your wedge candidate and come back to it next week.
- **Insight:** Every time the labs ship the next leverage (subagents, `fallbackModel`, Artifacts) the *configuration discipline* gets more valuable, not less. Tools commoditize fast; *configurations that survive a real outage with cost in band* don't. Your portfolio's job is to show you can hold the latter — that's what hiring managers will pay up for in H2 2026.

→ Cross-link: [`05` §3 the weekend sprint as career artifact](./05-career-and-startup.md#3-weekend-sprint) · [2026-05-22/03 §1 the cost-routing recipe](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. Pre-stage the GPT-5.6 comparison table — publish within 48h of GA {#2-pre-stage-comparison}

**Why pre-stage:** Per consensus, GPT-5.6 GA likely lands week of June 22. The [2026-05-19/03 §1](../2026-05-19/03-practical-skills-and-tools.md#1-io-live-discipline) discipline applies: **the value of a comparison post is in the *48-hour window* after launch.** Pre-staging the skeleton makes that publication-window achievable as a part-time effort.

**The skeleton (write Sunday, fill Monday post-launch):**

| Capability | Claude Opus 4.8 (current Anthropic flagship) | Claude Fable 5 ([restored if/when]) | GPT-5.5 | **GPT-5.6** (fill Monday) | Gemini 3.5 Pro |
|---|---|---|---|---|---|
| SWE-bench Verified | (look up) | 95.0% (set the bar; currently dark) | 82.3% | **TBD** | (look up) |
| Terminal-Bench 2.0 | (look up) | (last available) | 82.7% | **TBD** | 76.2% |
| FrontierMath T4 | (look up) | (last available) | 35.4% | **TBD** | (look up) |
| Context window | 1M ctx | 1M ctx | 1M | **TBD** | 1M ctx |
| Input price / 1M | $5 | $10 (post-cliff) | (look up) | **TBD** | $1.50 |
| Output price / 1M | $25 | $50 (post-cliff) | (look up) | **TBD** | $9 |
| Agentic features | Claude Code, fallbackModel, subagents | (same) | computer-use, code interpreter | **TBD** | Antigravity, Managed Agents |

**The publish flow:**

- **Pre-stage Sunday:** populate every Claude / GPT-5.5 / Gemini column.
- **Monday launch + 4h:** fill the GPT-5.6 column from OpenAI's announcement post.
- **Monday launch + 24h:** add a single-paragraph "what changed for builders" take.
- **Monday launch + 48h:** post on LinkedIn + your portfolio site.

### Why it matters to you

- **Job lens:** Recruiters' Monday search feeds will be saturated with GPT-5.6 keyword posts; the artifacts that win the search rankings are the ones up *fast* with *real numbers and a clear take*. Be in the index Monday by sundown.
- **Startup lens:** Your customer / would-be-customer reads the same comparison; if your product is on Claude, you need a written answer to "should I switch?" within 48 hours of every flagship launch. Pre-staging is the only way that's not painful.
- **Insight:** The discipline of **pre-stage the publish, fill at launch** beats post-hoc analysis for both job-market and customer-conversation purposes. Apply this pattern to *every* major launch in 2026 — Anthropic, OpenAI, Google, Meta, Mistral.

---

## 3. Three small workflow upgrades to install this weekend {#3-workflow-upgrades}

Quick reps while you're configuring the router:

- **`/cd` mid-session.** Stop killing sessions to switch repos. Use `/cd <path>` to keep your plan + cache intact when an orchestrator dispatches into a different worktree. (Shipped in the June Claude Code drop — [2026-06-18/03](../2026-06-18/03-practical-skills-and-tools.md).)
- **One `SKILL.md` per recurring workflow.** Carries from yesterday's action — pick the next-most-common recurring workflow you didn't get to Thursday, write a `SKILL.md`, commit. By month's end you have 4 skills checked in; the public skills repo is a 5-second proof for a Solutions Engineer hiring manager.
- **`--safe-mode` as your first debugging step.** Whenever Claude Code feels off, that's the first command. Establishes whether the issue is your config or upstream — saves 30+ minutes per false debugging path.

**Sources:**
- [Claude Code Docs — Best Practices (official)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [2026-06-18/03 §1 — the 5-layer Claude Code stack](../2026-06-18/03-practical-skills-and-tools.md#1-claude-code-stack) `[primary, archive]`

### Why it matters to you

- **Job lens:** Three small daily markers that signal "I run this stack at production discipline." Cumulative over a month they're the difference between "uses Claude" and "operates Claude."
- **Startup lens:** Each is a tool-shaped wedge if you go deep on it. The **skills marketplace** is the under-built thing in the ecosystem; first-mover advantage is wide-open.
- **Insight:** Workflow superpowers compound *daily*. The 5-minute habit that saves 15 minutes a day is the cheapest leverage you'll buy — and the only thing standing between you and shipping the next portfolio artifact one week sooner.
