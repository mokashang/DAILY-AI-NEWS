# Practical Skills & Tools — 2026-06-11

Act-on-it-today. With **Fable 5 at $10/M in · $50/M out** and **June 15 Agent SDK metering T-4 days**, the highest-leverage move tonight is **drop Fable 5 into the orchestrator seat in your existing router** and log the cost delta vs Opus 4.8. Second move: **Codex's richer MCP schemas** mean the MCP server you've been planning can now ship as a *portable* artifact — one server, two agent runtimes. Third: **the visible-safeguards pattern from today's reversal** is a 30-minute eval-harness add to your portfolio.

Tags: `#playbook #claude-code #fable-5 #mcp #codex #cost #orchestration #safety #portfolio`

---

## 1. Drop Fable 5 into the orchestrator seat — re-baseline the router tonight {#1-fable-5-router}

The May-22 lever was **Opus-4.7 orchestrator + Sonnet-4.6 workers ≈ 40% cheaper than all-Opus**. With Fable 5 shipping at **$10/M in / $50/M out**, the math changes — Fable is **roughly half the per-token cost of Opus 4.8** and **scores higher** on SWE-Bench Pro (80.3% vs 69.2%) and FrontierCode (29.3% vs 13.4%). The orchestrator seat is the spot where capability quality compounds most, and Fable now offers the best $/quality at the top of the stack.

**The 2026-06 router (replace your current default):**

| Seat | Model | $/M in | $/M out | Why |
|---|---|---|---|---|
| **Orchestrator / planner** | **Fable 5** | $10 | $50 | Best $/quality at top; SWE-Bench Pro 80.3%; capability headroom for next 3 mo |
| **Workers (codegen, tests, review)** | Sonnet 4.6 | (lower) | (lower) | Bounded, parallelizable, already-validated for sub-tasks |
| **Verifier / guard** | Haiku 4.5 | (cheapest) | (cheapest) | Continuous safety/regression check (TrajAD pattern, [2026-05-19/04](../2026-05-19/04-research-progress.md)) |
| **Fallback (cyber/bio/research)** | Opus 4.8 | (legacy) | (legacy) | Where Fable's *visible* safeguards re-route — same flag as Anthropic uses (see [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal)) |

**Things to log per run** (open a `cost.md` per project):

- Tokens-in and tokens-out **per model per step**.
- Tokens by step type (plan vs implement vs verify vs route-to-Opus).
- Wall time per step.
- The actual $-per-task at end of run.

**Reliability primitive (carry forward from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)):** plan-first, no implementation; annotate the plan; send back "address all notes, don't implement yet"; only then let workers execute. Fable-as-orchestrator means the plan is even tighter, so the **annotation pass becomes shorter** — that's where the real cost win lands.

**Sources:**
- [Anthropic — Claude Fable 5 and Claude Mythos 5 (pricing + safeguards)](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`
- [Vellum — Fable 5 & Mythos 5 benchmarks explained](https://www.vellum.ai/blog/claude-fable-5-and-mythos-5-benchmarks-explained) `[analysis]`
- [News.bitcoin.com — Fable 5 launches at half price of Mythos preview](https://news.bitcoin.com/anthropic-launches-claude-fable-5-at-half-the-price-of-mythos-preview-benchmarks-top-all-rivals/) `[secondary]`
- [Anthropic — Claude Code best practices](https://code.claude.com/docs/en/best-practices) `[primary]`

### Why it matters to you

- **Job lens:** *"I re-baselined my agent team in 24 hours after Fable 5 shipped — same plan→annotate loop, swapped the planner seat, cut task cost X% with a 9pt gain in plan-stage SWE-Bench Pro"* is a stronger interview line than anything generic. Specifically: include the **cost.md** screenshot and a **graph of $/task before vs after**. This single artifact answers Solutions / FDE / Integration Engineer interview questions about cost engineering, model selection, and reasoning about benchmark relevance.
- **Startup lens:** **Margin lever.** If your wedge is any kind of Claude-for-X vertical, the orchestrator-seat swap **compresses your COGS by ~30–50% vs an all-Opus stack at higher plan quality.** Run the swap on a real workload before you talk to a customer or an investor; the data is the pitch.
- **Insight:** June 15 metering ([2026-05-16](../2026-05-16/01-big-lab-moves.md)) prices per-step decisions explicitly. The teams that swap their planner seat to Fable 5 *before* June 15 metering goes live get a clean "before / after metering" delta to show. **That's the most defensible cost-engineering story for any AI Integration interview through Q3.**

---

## 2. Ship one MCP server, run it inside both Claude Code AND Codex {#2-codex-mcp}

OpenAI's Codex update (this week) **added richer MCP tool-schema support** — meaning the MCP server you've been planning since [2026-05-19](../2026-05-19/03-practical-skills-and-tools.md) is now a *portable* artifact: write the server once, register it inside both Claude Code (where MCP has been native since 2024) and Codex (where the schema is now usable). One server, two agent runtimes.

**Concrete weekend ship — 4-hour scope:**

1. **Choose a real tool** — not a toy. Pick something from your daily workflow: a small ETL into your own knowledge base, a GitHub issue triager, a "summarise this PR with cross-references" tool. The bar from MCPVerse / Tool Decathlon is **real**, not mocked.
2. **Implement the MCP server** in Python or TypeScript using Anthropic's SDK; ship 3 tools with proper schemas.
3. **Verify under both runtimes**: register inside Claude Code (`claude mcp add`), register inside Codex (use the updated MCP schema), and run the same 5 test cases in both. Note any behaviour differences.
4. **Write a 1-page README** with: the 5 test cases, screenshots of both runtimes invoking the server, **per-step cost log** (token-level, from §1).
5. **Push to GitHub** with the tag `mcp-server` `claude-code` `codex` `cost-engineering` — these are the keywords recruiters search for.

**Sources:**
- [Anthropic — MCP overview](https://modelcontextprotocol.io/) `[primary]`
- [Anthropic — MCP servers (developer guide)](https://docs.anthropic.com/en/docs/build-with-claude/mcp) `[primary]`
- [Releasebot — OpenAI Codex June 2026 release notes (richer MCP schemas)](https://releasebot.io/updates/openai) `[aggregator]`
- [arXiv — MCPVerse: real-world benchmark for agentic tool use](https://arxiv.org/html/2508.16260v2) `[primary]`

### Why it matters to you

- **Job lens:** A portable MCP server with **dual-runtime verification + cost log** is — practically — a complete take-home for Solutions / Integration roles. It demonstrates: tool design, MCP fluency, vendor-agnostic engineering, cost-awareness, real-task framing. The May-22 dual-model sanitiser project + this MCP server = the **two-artifact** portfolio that answers all of orchestration / verification / cost / portability.
- **Startup lens:** Tool ecosystems are where the **lock-in flip** happens. The first wave of "Claude-for-X" wedges in [STARTUPS.md](../STARTUPS.md) assumed Claude-only. A **portable MCP toolchain** lets your wedge advertise vendor-portability to enterprise buyers — which is now table stakes after the Microsoft June-2 move and the Apple-Gemini deal ([`01` §4](./01-big-lab-moves.md#4-wwdc-apple-gemini)) reminded everyone that platforms refuse to be model-locked. Add "MCP-portable by default" as a [STARTUPS.md](../STARTUPS.md) wedge-design rule.
- **Insight:** **MCP is winning by adoption, not by spec.** The Codex MCP-schema upgrade is the second major non-Anthropic stack adopting it (Chrome 149 WebMCP is the other). When the *de facto* standard's spec is owned by Anthropic and the adoption is driven by OpenAI + Google, the *standard itself* is becoming the moat layer. Build on it; recommend it; ship MCP-shaped APIs in any new project — that's the lowest-risk infra bet of 2026.

---

## 3. The visible-safeguards eval harness — a 30-minute portfolio add {#3-visible-safeguards}

Today's Anthropic reversal ([`01` §3](./01-big-lab-moves.md#3-safeguards-reversal)) is *also* a tiny eval-harness opportunity. The thing Anthropic was caught doing — *silently degrading* a model's response on flagged topics — is empirically detectable. Add a small eval to your dual-model sanitiser project that:

1. **Probes** the model with a query in the *flagged* domain (ML accelerator design, distributed training).
2. **Compares** the response against the same query routed to **Opus 4.8** (the now-visible fallback).
3. **Flags** any *silent* delta — i.e., divergent quality without a visible "this query was routed" notice.

That single harness, **portably runnable across providers**, is the *primitive* version of the assurance category Fortune just called for. Even at 50 lines of code, it lands as a portfolio item: **"I built the eval that would have caught the Fable 5 silent-safeguard issue Anthropic admitted to."**

**Sources:**
- [Simon Willison — Anthropic Walks Back Policy](https://simonwillison.net/2026/Jun/11/anthropic-walks-back-policy/) `[analysis]`
- [Fortune — Anthropic accused of 'secret sabotage'](https://fortune.com/2026/06/10/anthropic-accu-claude-fable-5-limits-capabilities-ai-researchers-developers/) `[secondary]`

### Why it matters to you

- **Job lens:** This artifact lands in *every* AI-assurance, evaluation, and trust-and-safety interview through Q4. It's the cheapest way to credibly claim "I think about evaluation as a first-class engineering problem." 30 minutes; one repo; one screenshot.
- **Startup lens:** This is the **MVP** of the **visible-safeguard observability** wedge from [`01` §3](./01-big-lab-moves.md#3-safeguards-reversal). Build the toy version; document one *real* divergence (even a synthetic one); the founder-pitch writes itself.
- **Insight:** When a public reversal happens this fast, the underlying *measurement gap* it exposes becomes a buyer pain point in weeks. The teams that build the measurement layer in those weeks are the ones who get acquired (Judgment Labs pattern, 2026-05-13). **Move now while the lesson is hot.**

---

## 4. Calendar lever — get your Workspace Agents free credit before July 6 {#4-workspace-agents}

OpenAI's **Workspace Agents** stays free until **July 6** ([`01` §5](./01-big-lab-moves.md#5-openai-stack)), then becomes credit-priced. If you've been meaning to evaluate Workspace Agents against Claude Code agents — do it inside the next 25 days. Same dual-runtime principle as §2: register your MCP server inside Workspace Agents, run the 5-case eval, log cost. **Comparison data ages well** in interviews.

**Sources:**
- [OpenAI Help — Model & ChatGPT release notes](https://help.openai.com/en/articles/9624314-model-release-notes) `[primary]`
- [Releasebot — OpenAI Workspace Agents June 2026](https://releasebot.io/updates/openai) `[aggregator]`

### Why it matters to you

- **Job lens:** Cross-vendor comparisons are the kind of *evidence* that gets you past keyword-screen and into a real technical interview.
- **Startup lens:** If you're building anything in the agent-runtime space, the free window is when you build the integrations cheaply.
- **Insight:** Free credit windows are where you do the experiments you wouldn't otherwise pay for. Don't miss this one.
