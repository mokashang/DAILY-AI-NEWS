# Practical Skills & Tools — 2026-11-02

Three things to actually *do* this week: **(1)** build a Claude-Code-Review clone on open weights before Nov 15, **(2)** rewrite your Oct-14 router to use GPT-6.1 Terra + Kimi K3.1 Pro + Haiku 5.5 as tiered workers, and **(3)** reroute every multi-step agent you touch through a cheap-tier model with explicit effort-level and provider-swap flags.

Tags: `#claude-code #router #open-weights #agents #effort-levels #evals`

---

## 1. Build a Claude-Code-Review clone on open weights — weekend artifact {#1-claude-code-review}

**Why this is the one artifact to ship this month:** Claude Code Review hit GA Oct 15 on Claude Team + Enterprise ([`01` §5](./01-big-lab-moves.md#5-claude-code-review)). It is **the single most direct FDE-portfolio artifact** you can clone because it exercises the exact Anthropic-deployment-engineer skill chain: code-model handling, commit-review workflow, enterprise-security awareness, MCP fluency.

**Stack to clone it on:**
- **Model:** Mistral Large 4 (FP8, from Hugging Face, served on your own GPU box or a rented H100/A100 for a weekend) **or** Kimi K3.1 Pro API ($2/$10 per 1M, no self-host) **or** Haiku 5.5 ($0.10/$0.50 per 1M, cheapest for a demo).
- **Git integration:** MCP server pointed at GitHub / GitLab PR events, running locally via Claude Code's own MCP support.
- **Review rubric:** one-page JSON spec covering (a) correctness bugs, (b) security concerns, (c) performance regressions, (d) style/lint. Grep the Oct 14 edition's eval-authoring points for the trajectory-reporting pattern.
- **Output:** inline PR comments + a review summary comment. Add a cost dashboard that logs tokens per PR.

**60-minute version — tonight:**
- **10 min:** `git clone` a mid-size open-source repo you understand. Create a working branch with a deliberate bug + a style issue + an unused import.
- **15 min:** Spin up Haiku 5.5 via Anthropic API (cheapest). Write a 150-line Python script that reads the PR diff and generates a markdown review against your JSON rubric.
- **20 min:** Wire it to a GitHub webhook using the GitHub MCP server (open-source, documented in the Oct 14 edition cross-reference). The MCP server pushes PR events → your script → inline review comment.
- **15 min:** Add a `--provider` flag that swaps between `haiku-5-5`, `gpt-6.1-terra`, and `kimi-k3.1-pro`. Log tokens + latency + cost per PR.

**Weekend version:**
- Add Mistral Large 4 as a self-hosted fourth provider.
- Add a trajectory report (per-file reasoning trace, cost per step).
- Publish it as `claude-code-review-oss` on your GitHub. Record a 2-minute Loom. Pin to top of résumé + LinkedIn.

**Why this is credential-grade:** The Oct 14 edition's "FDE training is now productized" thesis assumed the artifact-set that signals FDE-readiness is now explicitly: **MCP server, cost-aware agent, eval harness, routing layer, trajectory report.** Claude-Code-Review-clone exercises all five in one weekend.

**Sources (reference material):**
- [Buttondown — Claude Code v2.1.91: MCP goes big, plugins go native](https://buttondown.com/claudecode/archive/claude-code-v2191-mcp-goes-big-plugins-go-native) `[secondary]`
- [DEV Community — Claude Code 2.1.118 adds Vim mode, theme, and hook/MCP](https://dev.to/raxxostudios/claude-code-21118-adds-vim-mode-theme-and-hook-mcp-43m5) `[secondary]`
- [C-SharpCorner — Anthropic Launches Remote MCP Server Integration in Claude Code](https://c-sharpcorner.com/news/anthropic-launches-remote-mcp-server-integration-in-claude-code) `[secondary]`

→ Cross-link: [`01` §5 Claude Code Review GA](./01-big-lab-moves.md#5-claude-code-review) · [`05` §1 apply plan](./05-career-and-startup.md#1-apply-plan-nov).

---

## 2. Router v3 — rebuild for Terra + Kimi K3.1 Pro + Haiku 5.5 + optional self-host {#2-router-v3}

**Why:** The Oct 14 edition flagged Router v2 (Haiku-5.5-as-worker + effort levels). Since then **GPT-6.1 Terra at $1/$5** and **Kimi K3.1 Pro at $2/$10** both shipped — the router has to triple-dispatch to be credible in Q4 2026.

**v3 architecture (one-page spec):**

| Tier | Model | Price (in/out per 1M) | Use when |
|---|---|---|---|
| **Cheap-worker** | Claude Haiku 5.5 (`effort: low`) | $0.10 / $0.50 | Subagent lookups, deterministic extraction, "pre-filter" classification. |
| **Mid-worker** | GPT-6.1 Terra (`effort: medium`) | $1 / $5 | Tool-use chains, codex-style small refactors, structured extraction with reasoning. |
| **Open-weight-worker** | Kimi K3.1 Pro (self-host or API) | $2 / $10 (API) · $0 variable self-host | 1M-token-context ingestion, batch jobs, compliance-sensitive paths. |
| **Flagship** | Claude Opus 5.5 **or** GPT-6 Astra **or** Gemini 4 Argon | $15 / $75 approximate ceiling | Only when the task fails the cheap/mid tiers OR when latency ≤ 2 sec at full capability is required. |
| **Policy-gated** | Gemini 4 Carbon (Fairwind-only) | n/a | Cyber-defense workflows only. Fence off at the application layer. |

**Routing policy (opinion):**
- **80% of your traffic should land on Cheap-worker + Mid-worker.** If you're hitting flagship for anything other than a known failure case, your router is misconfigured.
- **Explicit "degrade on cost spike" rule:** monitor $/day; auto-downgrade to K3.1 Pro self-host above a daily cost cap. The cap itself is a résumé-line artifact.
- **Trajectory logging:** every router decision writes a trace. These traces are **the artifact a hiring manager actually asks to see**, more than the router code itself.

**Expected numbers (as of Nov 2, 2026):**
- GPT-6.1 Terra: Terminal-Bench 4.0 at 50.3% max-effort; >3× faster than Astra per OpenAI self-timing.
- Haiku 5.5: 72.4% on offline OSWorld 2.1 subset (vs 15.7% for 4.5) per Oct 14 edition.
- Kimi K3.1 Pro: ~3 points off frontier on self-reported benches (open weights expected Nov 4).
- Mistral Large 4 OSS: Vals Index 48.05% (32 of 44 overall; higher among open-weight-only).

**Sources (reference pricing + benchmarks):**
- [AI Weekly — OpenAI Ships GPT-6.1 Terra at $1/$5 Per Million](https://aiweekly.co/alerts/openai-ships-gpt-61-terra-at-15-per-million-half-of-sol) `[aggregator]`
- [Vals.ai — GPT-6.1 Terra](https://vals.ai/models/openai_gpt-6.1-terra) `[primary]`
- [Vals.ai — Kimi K3.1 Pro](https://www.vals.ai/models/kimi_kimi-k3.1-pro) `[primary]`
- [Vals.ai — Mistral Large 4 OSS](https://www.vals.ai/models/mistralai_mistral-large-4-oss) `[primary]`
- [FourWeekMBA — Moonshot prices Kimi K3.1 Pro at half of Claude Opus 5.5](https://fourweekmba.com/ai-moonshot-prices-kimi-k3-1-pro-at-half-of-claude-opus-5-5/) `[analysis]`

→ Cross-link: [2026-10-14/03 §1 Haiku 5.5](../2026-10-14/03-practical-skills-and-tools.md#1-haiku-55) · [`05` §2 open-weight wedge](./05-career-and-startup.md#2-open-weight-wedge).

---

## 3. The "cheap-tier year" — reroute every multi-step agent you touch {#3-cheap-tier-year}

**The thesis:** Haiku 5.5 (Oct 7), GPT-6.1 Terra (Oct 26), Kimi K3.1 Pro (Oct 23), Mistral Large 4 OSS (Oct 29). **Four distinct cheap-tier shipments in 30 days.** The Oct 14 edition called this the "cheap-tier replaces the small-tier" shift; Nov 2 updates it: **the cheap-tier is now good enough to do agent-worker duties across all four major families.**

**Operational rule for the next 30 days:**
- **Every multi-step agent you touch** — personal projects, interview take-homes, startup prototypes — **must route its subtasks to a cheap-tier model** by default, with an explicit allow-list of task types that escalate to flagship.
- The allow-list itself is the artifact. **Someone who can tell you why their agent escalates on 11% of tasks and names the 11% is more hireable than someone with a flagship-only agent that costs 10× to run.**

**Three concrete action items:**
1. **Pick one multi-step agent you've built in the last 90 days.** Fork it. Rebuild the router with v3 ([`03` §2](./03-practical-skills-and-tools.md#2-router-v3)). Compare cost + quality traces on the same task set.
2. **Publish the comparison as a one-page write-up.** Title: "Rerouting [your agent] through Haiku 5.5 + Terra + K3.1 Pro — cost down X%, quality within Y%." LinkedIn + GitHub + personal site. Cold-reach-out hook for Nov 10–20.
3. **Add the write-up link to the top of your résumé.** Replace "Experience with Claude 5.5 / GPT-6 / Gemini 4" bullet.

### Supporting signal (Simon Willison / Nathan Lambert direction)

- Simon Willison's cadence has moved from "which model is best" to "which routing policy earns its cost" over the last 60 days. Watch his substack / blog for the explicit v3-shaped posts.
- Nathan Lambert's Interconnects has repeatedly made the case for open-weight-as-worker, closed-as-arbiter. The Mistral Large 4 + Kimi K3.1 Pro landing probably triggers a long-form post inside the next two weeks.

**Sources (direction + practitioner):**
- [Simon Willison's Weblog](https://simonwillison.net/) `[primary — practitioner]`
- [Interconnects — Nathan Lambert](https://www.interconnects.ai/) `[analysis]`
- [Latent Space — swyx + Alessio](https://www.latent.space/) `[practitioner]`

→ Cross-link: [`04` §1 process-aware eval](./04-research-progress.md#1-process-eval) · [`05` §2 open-weight wedge](./05-career-and-startup.md#2-open-weight-wedge).

---

## 4. Tool-tip of the week — the `--channels` flag on Claude Code {#4-tool-tip}

Claude Code gained a **`--channels` flag** at some point in the 2.1.x line; one third-party source describes it as *"with --channels, MCP servers can push messages directly into your Claude Code session"* (no official release date confirmed in these results). Treat as experimental.

**Why it's useful:** It inverts the model from "Claude polls MCP server" to "MCP server pushes to Claude session." For a code-review agent (see [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-review)), this means your agent reacts to a webhook-triggered MCP push rather than polling PR state — the latency and token-cost profile improves substantially.

**Caveat:** The flag's docs are not well-covered in primary sources yet. Confirm against your installed Claude Code's `--help` output before building anything production-shaped around it.

**Sources:**
- [corsummit — Claude Code effort channels MCP forms](https://corsummit.netlify.app/news/claude-code-effort-channels-mcp-forms) `[aggregator — unverified]`
- [Buttondown — Claude Code v2.1.91: MCP goes big](https://buttondown.com/claudecode/archive/claude-code-v2191-mcp-goes-big-plugins-go-native) `[secondary]`

---

**Edition cross-links**
- [`01` §2 — GPT-6.1 Terra pricing + benchmarks](./01-big-lab-moves.md#2-gpt61-terra)
- [`02` §1 — Open-weight pincer](./02-new-emerging.md#1-open-weight-pincer)
- [`04` §1 — Process-aware eval](./04-research-progress.md#1-process-eval)
- [`05` §1 — Apply plan refresh](./05-career-and-startup.md#1-apply-plan-nov)
