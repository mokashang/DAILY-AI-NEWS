# Practical Skills & Tools — 2026-09-02

Three things ship *this week* on your Anthropic stack that directly change what belongs on [`ME.md`](../ME.md). **(1) Fable 5.1 re-anchors the effort × model matrix** — the July [Opus-5-effort recipe](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort) needs an updated column. **(2) Claude Code v2.1.239–v2.1.251 shipped a batch of production-grade knobs** — Sonnet 5 default, 1M context, restricted-mode sandbox, per-loop token breakdowns, subagent live-execution mirror. **(3) A one-script open/closed A/B** (Claude vs. DeepSeek V4-Pro) is now cheap enough to be a weekend portfolio project. Karpathy's `nanochat` + `autoresearch` are the credential to attach.

Tags: `#playbook #claude-code #fable-5-1 #effort-toggle #deepseek #open-weights #nanochat #portfolio #cost`

---

## 1. The updated Fable × Opus × effort matrix — where each SKU actually belongs {#1-fable-matrix}

The July recipe was Opus-5-planner-high + Opus-5-worker-medium + Haiku verifier ([2026-07-25/03 §1](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort)). Fable 5.1's **~25–45% price cut** and Claude Code's Sonnet-5-default reshuffles the deck:

| Seat | Model + effort (Sept-2026) | Rationale |
|---|---|---|
| **Orchestrator (rare, expensive) planner** | **Fable 5.1, `effort=high`** | Fable's smarter frontier reasoning is now cheap enough to spend on the plan; the plan cascades. Cache the persona + system prompt. |
| **Worker (bulk, well-scoped)** | **Opus 5, `effort=medium`** | Still the workhorse. Cheaper than Fable 5.1 for volume; medium is the sweet spot on bounded subtasks. |
| **Adversarial verifier** | **Opus 5, `effort=high`** OR **Fable 5.1, `effort=medium`** | You want it *sharper* than the worker; keep verifier persona cached across a whole run. |
| **Formatter / summarizer / labeler** | **Sonnet 5, `effort=low`** | Now the default in Claude Code with 1M ctx. Cheap, deterministic, keeps volume off the pricier tiers. |

**One-hour project you can ship tonight:**
1. Pick a real repo you have.
2. Have Claude Code build an orchestration script that runs the same "add a feature + tests" task three times — once each on **(a) all-Opus-5-medium**, **(b) Fable-5.1-planner + Opus-5-medium-worker + Sonnet-5-low-formatter**, **(c) all-Fable-5.1-medium**.
3. Log: **wall-clock, in/out tokens, cache-read tokens, subagent count, tests-passing-on-first-run**.
4. Publish a two-page README: *"Fable 5.1 cost/quality frontier vs. Opus-only, September 2026 edition."*
5. Tag it `#claude-fable-5-1 #effort-routing`; screenshot the table for interviews.

**Sources:**
- [Anthropic — Claude Fable product page](https://www.anthropic.com/claude/fable) `[primary]`
- [Anthropic — Prompt caching docs](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [llm-stats — Fable 5.1 pricing](https://llm-stats.com/models/claude-fable-5-1) `[aggregator]`

### Why it matters to you
- **Job lens:** *"Per-subtask model + effort routing on Claude Fable 5.1 with a documented cost curve"* is the strongest resume line you can add this week. It's exactly the customer-conversation payload for an [FDE loop at Anthropic](./05-career-and-startup.md#2-fde-market).
- **Startup lens:** If your product has fanout ≥ 3 subtasks per run, the Fable-5.1-planner + Opus-worker mix is a **real gross-margin lever** vs. all-Opus. Re-cost this week; the annual savings on a modestly-scaled product are meaningful pre-Series-A runway.
- **Insight:** The **model × effort matrix is the new API decision** — expect more per-tool / per-turn granularity in the next Anthropic release. Build telemetry that logs *which cell of the matrix* every subagent used, so when Anthropic adds effort-adaptive budgets you just add columns.

---

## 2. Claude Code v2.1.239 → v2.1.251 — production-grade knobs shipped {#2-claude-code}

Skim the changelog; adopt the four that change how you build.

- **Sonnet 5 is the default with 1M-token context**, replacing Sonnet 4.6. That single change doubles the useful headroom for long-repo tasks; move any context-truncation workarounds out of your CLAUDE.md now.
- **Restricted-mode sandbox** blocks risky filesystem/network ops by default; opt-in per-run. Use it whenever you're running Claude Code on customer data or fresh repos of unknown provenance — the new baseline for "won't-nuke-my-git" assurance.
- **Per-loop token breakdown + hook events for model switches** — you can now instrument cost telemetry *inside a single session* without wrapping the CLI. This is the missing piece for making the §1 matrix production-legible.
- **Subagent live-execution mirroring to Remote Control** — background subagents stream their output to a companion session/UI. Combined with the July nested-subagents-to-depth-3, you can build **planner → workers → verifier** hierarchies you can actually watch.

**Sources:**
- [Claude Code Changelog — 2.1.239 → 2.1.251](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gradually — Claude Code changelog mirror](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Simon Willison — Aug 30 confused-environment attack post](https://simonwillison.net/2026/Aug/6/) `[primary]`

### Why it matters to you
- **Job lens:** *"Instrumented Claude Code per-loop cost telemetry and shipped an artifact using restricted-mode sandbox on a fresh customer repo"* is a specific, verifiable, current portfolio bullet. Anthropic Solutions/FDE loops score exactly this kind of production discipline.
- **Startup lens:** Restricted-mode sandbox is the **wedge for shipping Claude-inside-customer-repos as a product**. If your idea depends on running an agent inside a customer's codebase, the "we can guarantee no rogue writes" promise now has a first-class primitive to build on.
- **Insight:** Two months of Claude Code releases went from *"we're adding features"* to *"we're adding **guarantees**"* — sandbox, per-loop cost breakdowns, hook events. That trajectory says Anthropic is racing to make Claude Code the **default IDE for production agent work**, not a research tool. Which means your CLAUDE.md discipline is now a *portable skill*, not tool-specific hackery.

**Also:** Simon Willison's Aug 30 post flags **"confused environment" attacks** — a new class where a system prompt from context A leaks its authority into a hostile context B. Read before shipping any agent that touches customer data.

---

## 3. Open/closed A/B — Claude Fable 5.1 vs. DeepSeek V4-Pro-0813 in one script {#3-open-closed-ab}

The [DeepSeek V4-Pro-0813 release](./02-new-emerging.md#2-open-weights) makes an open/closed comparison legitimately cheap for the first time. A weekend script that does the following is a strong portfolio artifact:

1. **Pick an eval you already have** — SWE-bench Lite subset (20 tasks) or your own 20-task agent eval.
2. **Wire two providers** in the same script: Anthropic API (Fable 5.1, effort=medium) and DeepSeek API (V4-Pro-0813) using OpenAI-compatible SDK. Same system prompt, same tool set.
3. **Log per-task:** wall-clock, in/out tokens, agent turns, pass/fail, and total $ at published pricing.
4. **Report the frontier:** where DeepSeek is materially cheaper, where Claude wins on quality, where both fail. Compute *pass-rate per dollar*.
5. **Publish the writeup** with the numbers. Title it *"Open-weights caught up on the number — here's what actually changes for a builder"* — hits the discourse pocket that Simon Willison and Karpathy have both been writing into.

**Sources:**
- [Morph — DeepSeek V4 overview + benchmarks](https://www.morphllm.com/deepseek-v4) `[secondary]`
- [Anthropic API — Fable 5.1 docs](https://www.anthropic.com/claude/fable) `[primary]`
- [Simon Willison — recent open-weights coverage](https://simonwillison.net/) `[primary]`

### Why it matters to you
- **Job lens:** *Being the person on the team who ran the open/closed number* is a real signal — hiring managers now assume every Applied-AI candidate has *opinions* on open vs. closed and can't defend them with data. You'll be able to.
- **Startup lens:** The report doubles as **founder due diligence** for anyone considering an open-weights fallback path. If your unit economics get materially better in cell (X, Y) of the matrix, that's a wedge — not to *replace* your Claude backend, but to *arbitrage* against future price changes.
- **Insight:** Open-weights matching *benchmark* numbers doesn't mean matching *product experience*. The gap in tool-calling reliability, streaming quality, context management, and MCP ecosystem is where you should expect Claude/GPT to stay ahead through 2027. Measure that in your writeup — it's the honest answer.

---

## 4. Karpathy: nanochat + autoresearch as the fresh credential {#4-nanochat}

**What's live:** Karpathy's Sequoia Ascent 2026 talk reframed the frontier engineer's job as *"outsource thinking, not understanding."* His personal write-to-delegate ratio flipped **80:20 → 20:80** over 2026.

Practical takeaways:
- **`nanochat`** (github.com/karpathy/nanochat) — the "I trained an LLM end-to-end" credential now costs **~$100 and ~4 hours** on a rented single-node GPU. Run it once; the pipeline experience is worth every dollar.
- **`autoresearch`** (github.com/karpathy/autoresearch, ~630 LOC, from Nov 2025) — an overnight-ML-experiment agent. Fork it, run it against your MCP-server evals, add one custom tool. Ship the writeup as an artifact for the [`ACTIONS.md`](../ACTIONS.md) queue.
- **Framing:** LLMs automate what you can **verify**, not just specify. Every subagent in your CLAUDE.md should have an explicit verification hook — otherwise you're paying tokens for latency, not confidence.

**Sources:**
- [Karpathy — Sequoia Ascent 2026 notes](https://karpathy.bearblog.dev/sequoia-ascent-2026/) `[primary]`
- [GitHub — karpathy/nanochat](https://github.com/karpathy/nanochat) `[primary]`
- [GitHub — karpathy/autoresearch](https://github.com/karpathy/autoresearch) `[primary]`
- [The AI Opportunities — Sequoia Ascent 2026 writeup](https://www.theaiopportunities.com/p/sequoia-ai-ascent-2026-andrej-karpathy) `[secondary]`

### Why it matters to you
- **Job lens:** *"Trained a small LM end-to-end on nanochat + wrote up X finding"* is the fastest way to move your resume from "used LLMs" to "understands LLMs." One weekend, ~$100, materially different signal.
- **Startup lens:** "Outsource thinking, not understanding" is the founder posture that survives the *"can't your customer do this with Cursor and Claude Code alone"* interview. Your wedge is where **verification is hard** — pick that seam.
- **Insight:** Karpathy is now the **default operator vocabulary** for how a modern IC works. If you can't quote back the write/delegate ratio and the verification-vs-specification frame, you're behind on the taste level of the market.

---

## 5. This weekend's artifact: the one repo answering four interview questions {#5-weekend-artifact}

Fold September's news into the July recipe. This weekend, ship a **single repo** demonstrating:

- **Orchestration:** Fable 5.1 planner (`effort=high`) + Opus 5 worker (`effort=medium`) + Sonnet 5 formatter (`effort=low`) — §1.
- **Verification:** Runs against your **migrated 07-28 stateless MCP server** — same one from [2026-07-25/03 §4](../2026-07-25/03-practical-skills-and-tools.md#4-this-weekends-artifact). Show discovery via Server Card, OAuth 2.1 connect, malicious-prompt refusal.
- **Cost telemetry:** Per-loop token breakdown from Claude Code v2.1.251 hooks; compute per-run $ at Sept 2026 API prices.
- **Open/closed A/B:** Same eval also run against DeepSeek V4-Pro-0813 on rented compute; frontier table with pass-rate-per-dollar (§3).

Write the README so a hiring manager reads it in 90 seconds and sees: *(a) you orchestrate in 2026-shape (effort + model + verifier), (b) you build against the real MCP spec, not a mock, (c) you can talk about margin + quality in the same paragraph, (d) you have opinions on open vs. closed and defend them with data.* That's the Anthropic Applied AI Engineer interview in a repo — with September's specific news baked in.

→ Cross-link: [`04` §5 the benchmark-gaming caveat you must address](./04-research-progress.md#5-benchmarks-gameable) · [`05` §2 the FDE market that hires on exactly this](./05-career-and-startup.md#2-fde-market) · [`ACTIONS.md`](../ACTIONS.md) · [`ME.md`](../ME.md).

---

## Bonus tips worth adopting this week

- **Register the Alpaca AI Trading Agents Hackathon (Aug 28 → Sep 4)** — $6K pool, closes this Thursday. If you have any interest in financial-agent territory, this is a legitimate portfolio artifact for a weekend of work. → [lablab.ai/ai-hackathons](https://lablab.ai/ai-hackathons) `[aggregator]`
- **YC S26 Demo Day is 2026-09-10** — block the livestream. Best free market map of what's actually getting funded in agents/infra. → [`05` §4](./05-career-and-startup.md#4-yc-s26-demo).
- **AI Builders Hackathon (students-only) submissions due 2026-09-15.** → [ai-builders-hackathon-2026.devpost.com](https://ai-builders-hackathon-2026.devpost.com/) `[primary]`
- **iOS 27 previews start rolling out with the 2026-09-09 Apple event.** If you're serious about the Anthropic-stack focusing decision, spend one weekend porting a small workflow to a Claude-backed iOS 27 extension. → [`01` §1](./01-big-lab-moves.md#1-apple-ceo) {#2-ios-27}
