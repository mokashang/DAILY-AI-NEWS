# Practical Skills & Tools — 2026-06-17

Three things to actually *do* this week. Each compounds: §1 ships an FDE-interview-grade artifact, §2 saves real money under the live June-15 Agent SDK meter, §3 closes the loop on the [2026-05-22 dual-model sanitiser carry-over](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

Tags: `#claude-code #mcp #managed-agents #self-hosted #sandbox #cost #routing #workflows #subagents #orchestration #agent-sdk #june-15`

---

## 1. Set up self-hosted sandboxes + MCP tunnels (public beta) — tonight {#1-self-hosted-sandboxes}

**What's new:** Anthropic's **Claude Managed Agents** now run with a split that's the production-grade pattern enterprises (and your interview reviewers) have been waiting for:

- **Orchestration stays on Anthropic** — you don't have to host the agent loop.
- **Tool execution moves to your infrastructure** — the filesystem the agent reads/writes, the processes it spawns, and the network egress are all under your control. Run on your own host, **or** lean on Cloudflare / Daytona / Modal / Vercel as managed sandbox providers.
- **MCP tunnels** (more limited, research preview, requires request access) let the sandbox reach your *private* MCP servers without exposing them publicly.

The [Fable 5 / Mythos 5 suspension story](./01-big-lab-moves.md#1-fable-suspension) is the live governance motivation: a sandbox boundary you control is the only durable answer to **data residency**, **per-tenant isolation**, and **continuity under regulatory action**. This *is* the production version of MCP for enterprises.

**Sources:**
- [Anthropic — New in Claude Managed Agents: self-hosted sandboxes and MCP tunnels](https://claude.com/blog/claude-managed-agents-updates) `[primary]`
- [Anthropic Platform Docs — Claude Managed Agents overview](https://platform.claude.com/docs/en/managed-agents/overview) `[primary]`
- [Anthropic Platform Docs — Self-hosted sandboxes](https://platform.claude.com/docs/en/managed-agents/self-hosted-sandboxes) `[primary]`
- [The Decoder — Anthropic adds self-hosted sandboxes and MCP tunnels to Claude Managed Agents](https://the-decoder.com/anthropic-adds-self-hosted-sandboxes-and-mcp-tunnels-to-claude-managed-agents/) `[secondary]`
- [StartupHub — Claude Agents Get Private Sandbox](https://www.startuphub.ai/ai-news/startup-news/2026/claude-agents-get-private-sandbox) `[analysis]`
- [Wowhow — Claude Managed Agents Self-Hosted Sandbox + MCP Tunnels Enterprise Guide 2026](https://wowhow.cloud/blogs/claude-managed-agents-self-hosted-sandbox-mcp-tunnels-enterprise-guide-2026) `[analysis]`

### Do this tonight (90-minute build)

A self-contained portfolio artifact:

1. **Stand up a sandbox on Modal or Cloudflare.** (Choose Modal for speed; Cloudflare if you want a globally-routed compelling story.) ~20 min.
2. **Wire one private MCP server** — pick a vertical: GitHub-issue-triager, AWS-cost-auditor, or Postgres-schema-investigator. Whichever you have a real data source for. ~30 min.
3. **Run a 5-case eval**: 3 happy-path tasks, 1 ambiguous task, 1 deliberately-malicious task (prompt-injection probe). Log per-step cost. ~30 min.
4. **Push to GitHub with a README that explains the *governance* story** — name-check the Fable 5 suspension, name-check residency / per-tenant isolation, name-check the EO clearinghouse ([`01` §3](./01-big-lab-moves.md#3-eo-signed)). ~10 min.

You now have **one artifact that answers three interview questions**: managed-agents fluency · MCP server authorship · governance-aware design.

### Why it matters to you

- **Job lens:** This *is* the FDE / AI Integration Engineer audition piece. The job's whole bet is "you can take a model into a customer's environment without their security team killing it" — and a self-hosted sandbox demo with a private-MCP eval is literal evidence of that capability. Anthropic, OpenAI, Sierra, and the Big-4 AI Engineer practices will all read this artifact the same way. (Pair with the [`05` §3](./05-career-and-startup.md#3-fde-validated) hiring data: $130–300K base, 30–50% of FDE listings now ask for LLM-integration experience explicitly.)
- **Startup lens:** The same primitive is the **buy-it core** for any enterprise-AI startup pitching this fall. Build the demo once, fork it into a *product seed* once you see traction. Or sell consulting on it next semester.
- **Insight:** The split — orchestration off-host, tools on-host — is the **deepest architectural read** of where enterprise AI is going. The model provider keeps the model loop (so they can ship safety fixes daily); the customer keeps the data plane (so they can comply with their own boundaries). Build for *this seam*, not for "self-hosted everything" or "fully managed everything."

→ Cross-link: [`01` §1 Fable 5 suspension = compliance motivation](./01-big-lab-moves.md#1-fable-suspension) · [`02` §1 MCP ecosystem at production scale](./02-new-emerging.md#1-mcp-ecosystem) · [`05` §2 the EO clearinghouse hiring window](./05-career-and-startup.md#2-eo-lane-live).

---

## 2. Cost-aware model routing under the live Agent SDK meter {#2-cost-router}

**What's new — actionable as of today:**

The **June 15 Agent SDK meter is now T-0** (carried since [2026-05-16/01](../2026-05-16/01-big-lab-moves.md)). Anything programmatic — Agent SDK, `claude -p`, GitHub Actions, OpenClaw — bills against API list rates from the separate credit pool. Combined with **Fable 5 at $10/$50 (when it comes back)** vs **Opus 4.8 at $5/$25** vs **Sonnet 4.6 / Haiku 4.5** as the bench below, the model-routing skill is the highest-ROI thing you can practice this week.

**The Opus-orchestrator/Sonnet-worker pattern (from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) extended:**

| Step type | Model | Why |
|---|---|---|
| Plan / decompose | Opus 4.8 | Fewer steps, better plan = fewer total tokens downstream |
| Worker / execute | Sonnet 4.6 | ~5× cheaper per token; good enough for tool-call execution |
| Verify / critique | Haiku 4.5 | Cheapest; catches obvious failures pre-rollback |
| Hard-step escalation | Fable 5 (when available) | Only the steps where 95% SWE-Verified earns its 2× price |

**Concrete win:** an Opus-orchestrator + Sonnet-workers team runs **~40% cheaper than all-Opus**; adding the Haiku verifier saves another ~15% on average by failing fast on broken plans before the worker burns tokens.

**Two parallel features to use *now*:**

- **Claude Opus 4.8 Workflows + Dynamic Workflows** (research preview in Claude Code, [released May 28](../2026-05-22/)). Lets Claude Code **spin up parallel subagents** for codebase migrations or batched eval. Combined with the cost router, you get parallel speed *and* per-step cost control.
- **Claude Opus 4.8 Fast mode**: $10 input / $50 output — **~2.5× faster** and reported **~3× cheaper** than prior Opus Fast tiers. The win when latency is the bottleneck, not absolute cost.

**Sources:**
- [Artificial Analysis — Claude Opus 4.8: The new #1 AI model](https://artificialanalysis.ai/articles/claude-opus-4-8-analysis-and-benchmarks) `[analysis]`
- [Simon Willison — Claude Opus 4.8: "a modest but tangible improvement"](https://simonwillison.net/2026/May/28/claude-opus-4-8/) `[analysis]`
- [Magicshot — Claude Opus 4.8 Release: Benchmarks, Pricing, Features](https://magicshot.ai/news/claude-opus-4-8-release-features-benchmarks/) `[analysis]`
- [Pasquale Pillitteri — Opus 4.8: Release Date, Pricing, Benchmarks and What's New](https://pasqualepillitteri.it/en/news/3472/opus-4-8-release-date-anthropic-forecast-2026) `[analysis]`
- [Finout — Claude Fable 5 and Mythos 5: Pricing, API Costs, and Benchmark Comparison vs Opus 4.8 and GPT-5.5](https://www.finout.io/blog/claude-fable-5-mythos-5-pricing-benchmarks) `[analysis]`
- [Enterprise DNA — Two Claude Deadlines Hit June 15: What AI Builders Must Do](https://enterprisedna.co/resources/news/anthropic-claude-june-15-retirements-billing-2026/) `[analysis]`
- [Releasebot — Claude Code Updates by Anthropic — June 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### Do this this week (60-min build)

1. **Run the Opus → Sonnet → Haiku tier through one of your existing agent workflows** with per-step cost logging. ~25 min.
2. **Snapshot the cost curve** as a one-pager: "all-Opus baseline" vs "tiered" vs "tiered + Haiku verifier." ~15 min.
3. **Re-write that pager assuming Fable 5 is back at $10/$50** — when is the 2× price worth it? When isn't it? Decision rule out loud. ~20 min.

That one-pager is your interview-grade artifact for *cost-aware FDE* — the same content as the §1 sandbox demo, viewed through the dollar axis.

### Why it matters to you

- **Job lens:** "Hands-on cost routing" is now an explicit screening line at Anthropic Solutions / Sierra Customer Engineering / OpenAI FDE postings ([`05` §3](./05-career-and-startup.md#3-fde-validated)). The artifact above is direct evidence — and almost no other new-grad candidate will have produced one.
- **Startup lens:** A meaningful share of agent startups will exhaust capital this year ([`02` §2](./02-new-emerging.md#2-funding)) because they didn't internalize this lever. Your competitive advantage as a founder *or* first-5 engineer in 2026 is *being the one in the room who knows how to make the spend curve bend.*
- **Insight:** The frontier just got *more* tiered (Fable above Opus above Sonnet above Haiku, with Fast modes on each), and OpenAI runs the same playbook (5.6 above 5.5 above 5.5 Mini). **Multi-model routing is no longer optional** — it's table stakes. The companies still running all-Opus or all-GPT-5.5 in production are *paying for the model's training run* on every query.

→ Cross-link: [`02` §3 GPT-5.6's "modest single-turn, big multi-hour" framing as evidence that escalation routing is the right pattern across all labs](./02-new-emerging.md#3-gpt-56) · [2026-05-22/03 §1 the original Opus-orchestrator/Sonnet-worker write-up](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 3. Claude Code updates worth turning on tonight {#3-claude-code-updates}

**What shipped in the gap window** (verified via Anthropic's release notes):

- **Stronger permission rules** — finer-grained allow/deny per command and tool. Spend 10 min building your project allowlist; **drops permission prompts substantially.**
- **Nested `.claude` support** — sub-project `.claude/` directories now inherit and override parent. **Big for monorepos** and for layering project rules under a personal `CLAUDE.md` (Karpathy's [4-rule playbook](../2026-05-15/03-practical-skills-and-tools.md) still applies).
- **Safer auto mode** — additional guardrails before auto-applying changes. Default is more conservative; opt in to fewer prompts only where you actually want them.
- **/doctor command improvements** — better env diagnostics for "why is Claude Code behaving weirdly here?"
- **Remote Control improvements** — the laptop-as-remote workflow ([2026-05-17](../2026-05-17/00-tldr.md)) got more reliable; useful if you're moving between machines.
- **/bug command improvements** — more structured bug reports back to Anthropic; use it when something fails, not when you give up.

**Sources:**
- [Releasebot — Claude Code Updates by Anthropic — June 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Releasebot — Claude Updates by Anthropic — June 2026](https://releasebot.io/updates/anthropic/claude) `[aggregator]`
- [ClaudeLog — Claude News](https://claudelog.com/claude-news/) `[aggregator]`
- [Anthropic — Newsroom (rolling)](https://www.anthropic.com/news) `[primary]`

### Why it matters to you

- **Job lens:** Permission rules + nested `.claude` + Workflows + dynamic subagents = the difference between *"I use Claude Code"* and *"I run Claude Code as a managed pipeline."* The second phrasing is what gets through to the technical screen at FDE-track companies. Internalize the vocabulary tonight.
- **Startup lens:** If your product wraps Claude Code (a real and growing category — Cursor, Replit, Vercel, GitHub Copilot all wrap it now), every release-notes drop is an integration surface to update. Subscribe to releasebot's RSS *today*.
- **Insight:** The cadence of Claude Code updates (multiple per week) is itself the signal — **Anthropic is treating Claude Code as a real product, not an open-source toy.** Build muscle around treating updates as alpha tests of the next *enterprise* shape: nested config = multi-tenant projects · stronger permissions = corporate IT readiness · safer auto = compliance auditors' yes vote.

→ Cross-link: [`01` §1 Fable 5 suspension changes what "safer auto" buys you in regulated industries](./01-big-lab-moves.md#1-fable-suspension) · [2026-05-21/03 the Claude Code orchestration stack](../2026-05-21/03-practical-skills-and-tools.md).
