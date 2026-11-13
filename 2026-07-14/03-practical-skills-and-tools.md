# Practical Skills & Tools — 2026-07-14

Act-on-it-today. The June-15 Anthropic Agent-SDK metering has been live for a month — you've now got real data on what your agents cost. The **two levers that reset that number this week** are: (1) **Claude Sonnet 5** (June 30) — Anthropic launched it *explicitly* as "cheaper way to run agents," which lets you rebuild the [May-22 Opus/Sonnet split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) at meaningfully lower unit cost; and (2) **GPT-5.6 prompt-cache breakpoints** (July 9) — explicit cache control + 30-min minimum cache life, meaning cross-provider cost engineering just got *symmetric*. Both are doable tonight.

Tags: `#playbook #claude-code #sonnet-5 #gpt-5-6 #subagents #cost #prompt-caching #mcp #portfolio`

---

## 1. Rebuild your agent team on Sonnet 5 — and standardize on prompt-cache breakpoints across providers {#1-model-routing}

The May-22 primitive was **Opus 4.7 orchestrator + Sonnet 4.6 workers ≈ 40% cheaper than all-Opus**. Two July updates change the math:

**A. Sonnet 5 (Anthropic, June 30).** Launched with the explicit tagline: "*a cheaper way to run agents.*" The right read is not "swap Sonnet 4.6 for Sonnet 5 everywhere," it's:

- **Worker seats** (bounded, well-scoped subtasks — review / test / codegen / QA) → **Sonnet 5**. Direct drop-in for Sonnet 4.6 workers; if quality holds, keep it.
- **Orchestrator seat** → **still Opus 4.7 (or Opus 4.8 if you can access it)**. Planner reasoning still pays for itself; do *not* downgrade this.
- **Guard / verifier seat** → **Haiku 4.5 remains correct** for always-on checks.

**Rule of thumb for the swap:** run the same eval task **twice** — once on your existing team, once with Sonnet 5 in the worker seats — and compare **(quality-metric, tokens, wall-clock)**. If quality doesn't drop >3% and cost falls ≥20%, cut over. Log this in your portfolio README as a numeric before/after.

**B. GPT-5.6 explicit cache breakpoints (July 9).** OpenAI shipped **explicit prompt-cache breakpoints + a 30-minute minimum cache life** as part of GPT-5.6 (Sol/Terra/Luna). This closes a real gap vs. Anthropic's prompt-caching primitives and means:

- If you were only using prompt caching on the Claude side, **turn it on on the OpenAI side too** — the ROI (60–90% input-cost savings on repeated context) is now available symmetrically.
- **Standardize your prompt scaffolding** so the *same cacheable prefix* lands identically on both providers — same tool schemas, same system prompt, same few-shot ordering. Then you can A/B on quality without cost variance getting in the way.

**Pricing to internalize (per 1M tokens):**

| Model | Input | Output | Best fit |
|---|---|---|---|
| GPT-5.6 **Sol** | $5 | $30 | Hardest orchestrator/verifier work; frontier reasoning |
| GPT-5.6 **Terra** | $2.50 | $15 | Balanced worker; general everyday work |
| GPT-5.6 **Luna** | $1 | $6 | Fast/cheap worker; parallelizable subtasks |
| Claude **Sonnet 5** | (Anthropic list) | (Anthropic list) | Cheaper worker for agent teams; the drop-in |
| Claude **Haiku 4.5** | (Anthropic list) | (Anthropic list) | Always-on guard / verifier |
| Claude **Opus 4.7/4.8** | (Anthropic list) | (Anthropic list) | Orchestrator / plan-first / hard judgment calls |

*(Confirm exact Anthropic list prices via [Anthropic pricing docs](https://docs.anthropic.com/en/docs/about-claude/pricing) before publishing anything with numbers.)*

**The reliability primitive from May-22 still applies verbatim:** *plan-first with the orchestrator (no implementation) → annotate in your editor → return with "address all notes, don't implement yet" → only then let cheaper workers execute.* The cheaper your workers, the more the plan has to be right.

**Sources:**
- [TechCrunch — Anthropic launches Claude Sonnet 5 as a cheaper way to run agents](https://techcrunch.com/2026/06/30/anthropic-launches-claude-sonnet-5-as-a-cheaper-way-to-run-agents/) `[secondary]`
- [OpenAI — Previewing GPT-5.6 Sol (announcement + prompt-cache changes)](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [OpenAI Help — A preview of GPT-5.6 Sol, Terra, and Luna](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) `[primary]`
- [Simon Willison — The new GPT-5.6 family: Luna, Terra, Sol](https://simonwillison.net/2026/Jul/9/gpt-5-6/) `[analysis]`
- [DataCamp — GPT-5.6 Sol, Terra, and Luna: OpenAI's Next-Gen Model Family](https://www.datacamp.com/blog/gpt-5-6-sol-luna-terra) `[analysis]`

### Why it matters to you

- **Job lens:** *"After June-15 metering, I rebuilt our agent team on Sonnet 5 workers + Opus orchestrator + Haiku guard, standardized prompt-cache breakpoints across Anthropic and OpenAI, and cut per-task cost ~X% at flat quality"* is a **single interview-answer sentence** that lands three different questions at once — orchestration, cost engineering, and cross-provider fluency. This is the FDE/Integration story ([`02` §1](./02-new-emerging.md#1-msft-frontier)) as a portfolio artifact.
- **Startup lens:** Your COGS is tokens, and the two levers you *actually* control are **(a) which model in which seat** and **(b) how much of your input is cacheable**. Sonnet 5 shifts (a); GPT-5.6 breakpoints unlock (b) on the other side. Both were priced in this month — build the muscle now while it still looks like discipline, not table stakes.
- **Insight:** Prompt caching becoming symmetric between Anthropic and OpenAI is a **quiet convergence signal**: the frontier providers are now optimizing the *same* efficiency levers, in the *same* shapes, in public. That's actually good for you — a cost-engineering skill built on one now transfers cleanly to the other, and the marginal reward for "Claude-only" vs "OpenAI-only" specialization has dropped.

---

## 2. Claude Code July 2026 refresh — the two things worth doing tonight {#2-claude-code-refresh}

The wider **Claude Code 2026 playbook** (subagents / MCP / agent teams / dashboard) is well-established. Two specific July additions that reward action tonight:

**A. Wire one real MCP server — don't just read about them.** The 2026 practitioner consensus (across Anthropic's docs and the top playbook write-ups) is that **one connected MCP server beats reading a hundred MCP articles**. The cheapest, highest-ROI first server is *whichever tool you copy-paste from most already*: Postgres, Linear/Jira, Figma, GitHub, or your monitoring stack. Do that one tonight; measure how many copy-paste round trips it eliminates in a week.

**B. Move your subagents from ad-hoc prompts to YAML with scoped tools.** The 2026 subagent guides converge on this: **description quality is everything** (vague descriptions cause the wrong subagent to fire or none at all), and **each subagent should have its own scoped tool set** so it can't reach outside its lane. Convert your 2–3 most-used subagents from inline prompts to YAML definitions with (i) a specific, unambiguous description, (ii) a scoped tool list, (iii) an independent model choice (this is where §1 lands — the sub-agent's YAML is where you write "worker → Sonnet 5").

**Sources:**
- [Anthropic — Claude Code best practices (official docs)](https://code.claude.com/docs/en/best-practices) `[primary]`
- [Developers Digest — Claude Code agent teams, subagents, and MCP: the 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [Fastio — Claude Code Subagents: a Practical Guide for 2026](https://fast.io/resources/claude-code-subagents-guide/) `[analysis]`
- [PubNub — Best Practices with Claude Code Subagents Part II: From Prompts to Pipelines](https://www.pubnub.com/blog/best-practices-claude-code-subagents-part-two-from-prompts-to-pipelines/) `[analysis]`
- [MarkTechPost — Claude Code Guide 2026: 25 features with examples + demo](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`
- [Claude Directory — Best Claude Code setups for AI & agent development (July 2026)](https://www.claudedirectory.org/for/ai-agent-development) `[aggregator]`

### Why it matters to you

- **Job lens:** *"I run a live subagent stack — YAML-defined, scoped-tool, per-agent model choice — against one production MCP server"* is a **hire-me line** in itself. Screenshot the dashboard for your README.
- **Startup lens:** If any part of your wedge involves *deploying* AI in another company's environment (FDE-adjacent — everything is FDE-adjacent this month), the ability to wire a *specific* MCP server + hand off a scoped subagent to a client team is the deliverable. Practice on your own stack first.
- **Insight:** Every Claude-Code update this year has quietly rewarded the same thing: **explicit structure over free-form prompting**. YAML subagents, MCP tools, dashboards, hooks, orchestrator/worker teams — all four are the same shift. If you keep using Claude Code as a chat window, you'll get chat-window productivity; if you invest in the *structured* interface, you get an *engineered* system. Bias every hour toward the second.

---

## 3. This week's artifact: publish the "cost + eval + real-tool" agent case study {#3-artifact}

You already have the **dual-model sanitiser artifact** from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact). The July upgrade is *numeric*:

1. Run it **before June-15 metering (pull from your bills)** and **now, with the Sonnet 5 worker swap** — table it out: `tokens_in`, `tokens_out`, `cache_hit_%`, `cost_by_model_seat`, `wall_clock_p50`, `quality_score`.
2. Run **one real MCP server integration** (§2A) and log: `tool_calls`, `refusals`, `injections_caught` (feed it one prompt-injection test case from the [Google Threat Report / IPI trend](../2026-05-20/README.md) or a simple hidden-instruction HTML page).
3. Write the README section **"How I'd wire this for an FDE client"** — one paragraph on **on-site deployment** (§ [`02` §1](./02-new-emerging.md#1-msft-frontier)), one paragraph on **per-step cost telemetry**, one paragraph on **real-tool verification** with the MCP result.

Publish it. Link it from your LinkedIn "Featured" — this is the single most on-thesis artifact you can ship in the current market week.

→ Cross-link: [`05` §1 FDE application action](./05-career-and-startup.md#1-fde-quintupled) · [2026-05-22/03 §2 the artifact frame](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) · [`ACTIONS.md`](../ACTIONS.md).
