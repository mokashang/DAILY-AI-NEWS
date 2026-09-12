# Practical Skills & Tools — 2026-06-13

Act-on-it-this-Saturday. **Two days to Anthropic Agent SDK metering (Monday June 15).** Tonight is your last unmetered Saturday for Claude Code subagents — and Fable 5's release dropped the *cheapest credible orchestrator* tier into the routing table. Two things to do: **(1) toggle the credit + re-wire the agent team for the new model lineup; (2) ship the Fable-5-aware portfolio artifact**. Both are concrete and doable before midnight.

Tags: `#playbook #claude-code #subagents #cost #orchestration #fable-5 #agents #portfolio #metering`

---

## 1. T-2 to metering — toggle the credit, re-route to the post-Fable-5 lineup {#1-t-2-metering}

**The deadline:** **Monday, June 15** — Anthropic Agent SDK + Claude Code usage moves to a **separate monthly credit pool** (Pro $20, Max-5x $100, Max-20x $200), **billed at full API list rate, no rollover.** The credit pool **does not auto-activate** — you must toggle it manually in account settings ([carried from 2026-05-18 / 2026-05-22 watchlist](../WATCHLIST.md)). Miss the toggle and your Monday agent runs will either be blocked or fall back to your regular API spend with no warning.

**Do this Saturday (15 min):**
1. Open Anthropic console → Settings → Billing → **toggle "Apply credit pool to Agent SDK / Claude Code"** to ON.
2. Set a **per-task budget cap** (Anthropic now exposes this on the Max tiers) — start at $5/task and tune up.
3. Add a **`CLAUDE.md` line** at the repo root: *"Default orchestrator: Fable 5; workers: Sonnet 4.6; verifier: Haiku 4.5; fallback to Opus 4.8 on safety-blocked queries."* — that file is the spec the SDK reads from.

**The updated agent-team routing table (post-Fable-5):**

| Seat | Model | Why |
|---|---|---|
| **Orchestrator / planner** | **Fable 5** | SWE-Bench Pro 80.3% (vs Opus 4.8 at 69.2%) — fewer planner turns per task → fewer metered tokens |
| **Workers** | Sonnet 4.6 | Bounded subtasks; cheaper per token; the well-tuned default |
| **Verifier / guard** | Haiku 4.5 | Always-on safety + cheap eval (cf. [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) |
| **Safety fallback** | Opus 4.8 | What Fable's hard refusals route to automatically — explicitly model this in your traces |

**The new reliability primitive (Fable-aware):** the **plan-first → annotate → "address all notes, don't implement yet"** loop from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) **still applies** — but with Fable 5 as planner you should expect *fewer* annotation cycles (the 22-point SWE-Bench Pro gap shows up as more correct first-draft plans). **Don't skip the annotation step**: the saved Sonnet-worker runs are where the cost win lives.

**New Claude Code features to use tonight (per June release notes):**
- **Nested sub-agents** — sub-agents can now spawn their own sub-agents (with depth caps). Use for fan-out/fan-in patterns (one orchestrator → three review agents → one consolidator).
- **Fallback models** — declare a backup model in the SDK config; ride this for the Fable→Opus safety-fallback pattern.
- **Broader deny-rule glob support** — write tighter sandboxes (e.g., `**/node_modules/**`, `**/.env*`).
- **Fast mode on Opus 4.8** at a lower price — use as your "answer quickly when Fable is overkill" tier.
- **Security-guidance plugin** — catches common security issues in agent-generated code; install it on every Claude Code project from this week forward.

**Sources:**
- [andrew.ooo — Anthropic June 15 Billing Change: Claude Code Decision Guide](https://andrew.ooo/answers/anthropic-claude-code-june-15-billing-change-may-2026/) `[analysis]`
- [Releasebot — Claude Code Updates (June 2026)](https://releasebot.io/updates/anthropic/claude-code) `[primary]`
- [Releasebot — Anthropic Release Notes (June 2026)](https://releasebot.io/updates/anthropic) `[primary]`
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [StartupHub — Claude AI in 2026: Models, Pricing, Code, Free Access](https://www.startuphub.ai/ai-news/reviews/2026/claude-ai-complete-guide-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Your interview line just got two sentences sharper: *"After June 15 metering, I re-architected my agent team to put Fable 5 in the planner seat — the SWE-Bench Pro delta paid for itself in fewer planner cycles, and I traced cost per step per model so I could prove the routing decision to a client."* That single line is the FDE/Integration job described from the inside.
- **Startup lens:** Metering hits *your COGS*, not just your dev environment. **Build your wedge with per-task budget caps as a first-class user setting** — Anthropic just normalized it as a UX expectation. Pricing model: *charge for outcomes, not minutes; pass through model-tier cost as a line item so customers see the routing decision.*
- **Insight:** Metering is not an inconvenience — it is the **forcing function that makes "which model in which seat" a real engineering decision** rather than a stylistic one. Builders who treat it as a constraint write better-architected agents than builders who treat it as a deferred bill. **Be the former by Monday morning.**

---

## 2. This weekend's artifact: the Fable-5-aware sanitiser, with a per-step cost ledger {#2-artifact}

You already have the **dual-model "sanitiser" / cost-aware agent** queued from [2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project) and refined in [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact). The Fable 5 release gives you the *concrete* model lineup that converts the artifact from "thoughtful prototype" into "thing you can demo to a Solutions / FDE interviewer with real numbers." **Do not start over. Upgrade.**

**The Saturday rewrite (3-4 hours, total):**
1. **Swap the orchestrator to Fable 5.** Cite the SWE-Bench Pro number in the README — *"Chose Fable 5 over Opus 4.8 because the 11-point coding-benchmark delta translates to ~1 fewer planner turn per task on a 5-task evaluation harness."*
2. **Keep Sonnet 4.6 workers + Haiku 4.5 verifier.** The cost story from [2026-05-22](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) stays intact — Fable just makes the planner cheaper *per correct plan* (not per token).
3. **Verify against one real MCP server** — per [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks). The new [Terminal-Bench 2.0](./04-research-progress.md#1-terminal-bench-2) leaderboard gives you the public comparison harness; pick one of its 89 tasks and run your team against it as the README's worked example.
4. **Add the per-step token-cost ledger** — table with: step, model, prompt tokens, completion tokens, cost at metered rate, cost if you'd routed to Opus instead. **That table is the artifact.** It's what a Solutions/FDE interviewer asks for and 95% of candidates can't show.
5. **Add a Fable→Opus safety-fallback trace.** Write a test case that triggers Fable's hard refusal (a benign cyber-adjacent prompt — *"explain how X log injection works conceptually"* will do); show the trace falling back to Opus 4.8 transparently. That's the new safety-architecture primitive ([`01` §1](./01-big-lab-moves.md#1-fable-5)) made concrete.

**The README single sentence — your FDE interview in one line:** *"I architected a Fable 5 planner / Sonnet 4.6 worker / Haiku 4.5 verifier team with an Opus 4.8 safety fallback, verified it against a real MCP server in a Terminal-Bench 2.0 scenario, and produced a per-step cost ledger that survives the June 15 metering change."* — orchestration, verification, safety, and cost answered together.

→ Cross-link: [2026-05-22/03 §2 prior framing](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [`04` §1 Terminal-Bench 2.0](./04-research-progress.md#1-terminal-bench-2) · [`ACTIONS.md`](../ACTIONS.md).

---

## 3. Quick tip — read the Releasebot Claude Code feed weekly {#3-releasebot}

**The discipline:** Subscribe to (or bookmark) **Releasebot's Claude Code feed** and read it once a week — Saturday morning is the natural slot. It mirrors Anthropic's release notes without the marketing layer. The single biggest reason candidates fall behind on Claude Code interviews is **they're 4–8 weeks late on knowing which subagent/permission feature shipped most recently**; this fixes that for 5 minutes per week.

- [Releasebot — Claude Code](https://releasebot.io/updates/anthropic/claude-code) `[primary]`
- [Releasebot — Claude](https://releasebot.io/updates/anthropic/claude) `[primary]`
- [Releasebot — Anthropic Release Notes (umbrella)](https://releasebot.io/updates/anthropic) `[primary]`

**Why it matters:** Two of this week's three Claude Code features (nested sub-agents, fallback models) **did not get blog coverage** — they only appear in release notes. Be the candidate who knows the SDK by its release notes, not its press releases.
