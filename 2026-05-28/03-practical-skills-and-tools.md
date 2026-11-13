# Practical Skills & Tools — 2026-05-28

Two install-this-week things and one workflow upgrade. **(1) Claude Code's May 26 update** is the biggest *enterprise-perimeter* improvement since MCP itself — **self-hosted sandboxes + MCP tunnels + a security plugin** that you can install with one `/plugins` command. **(2) OpenAI Codex's May 27 update** ships **Appshots** (one-shot context from any frontmost app on macOS), expanded Goal mode, and the productionized **self-improving tax-agent** reference. **(3) The workflow upgrade**: now that Cognition / OpenRouter / Anthropic's perimeter posture all converge, **the high-leverage skill of June is "agents that run in your customer's environment, route across models, and prove their own cost"** — three artifacts you can ship over the next two weekends.

Tags: `#claude-code #managed-agents #mcp #self-hosted #codex #appshots #routing #cost`

---

## 1. Claude Code 2026-05-26 update — self-hosted sandboxes, MCP tunnels, security plugin {#1-claude-code-sandbox}

**What shipped (May 26, 2026):** Anthropic released a Claude Code update centered on **enterprise-perimeter execution** and **safer-by-default agentic edits**.

**The three big additions:**

1. **Self-hosted sandboxes for Managed Agents (public beta).** Tool-execution moves to **infrastructure you configure** — your own VPC, Kubernetes cluster, on-prem, or a managed provider (**Cloudflare**, **Daytona**, **Modal**, **Vercel**). The **agent loop** (orchestration, context management, error recovery) **stays on Anthropic's infrastructure**, so you don't have to host the model. This is the long-promised "your data never leaves" + "we still run the smart part" split.
2. **Private MCP servers via tunnel.** Managed Agents can now reach **MCP servers that live inside your network** — i.e., Postgres / Snowflake / Jira / OpsGenie / internal-API MCP servers — without exposing them publicly. (`Enterprise setting for Claude.ai cloud MCP connectors` enables this org-wide.)
3. **Security guidance plugin** (`/plugins` marketplace, all users) — monitors **edits, diffs, and commits in real time**, flagging dangerous patterns (e.g., secrets, unsafe shell, prompt-injection-prone file reads) **before they reach production.** This is Anthropic's first first-party "guardrails" plugin.

**Smaller wins in the same release:**
- **Usage insights** — richer per-session token / cost / step breakdowns. Stop hand-computing these.
- **Keyboard-friendly diff scrolling** + improved Markdown task-list rendering — quality-of-life, but real.
- **Permissions, transcripts, history, feedback** — long list of fixes.

**Sources:**
- [Anthropic — Claude Code changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Releasebot — Claude Code Updates by Anthropic, May 2026](https://releasebot.io/updates/anthropic/claude-code) `[secondary]`
- [Cybersecurity News — Anthropic Updates Claude Code With Security Plugin and Faster Performance](https://cybersecuritynews.com/anthropic-updates-claude-code/) `[secondary]`
- [Anthropic — news](https://www.anthropic.com/news) `[primary]`

### Why it matters to you

- **Tonight (5–10 min):** Open Claude Code → `/plugins` → install the **security guidance plugin**. It's free, it ships, and it shows up in your `.claude/` config. Now every diff Claude Code stages goes through guardrails by default. You'll catch your own secrets-in-config mistakes before commit.
- **Saturday project (2–3 hrs):** Stand up a **self-hosted sandbox on Modal or Daytona** (whichever you already have an account on) and connect it to a Managed Agent. Cost: pennies. Outcome: a portfolio artifact titled **"Managed Agents inside my perimeter — orchestration on Anthropic, execution on Modal, MCP to local Postgres"** with a 90-second screencast. This *directly* maps to KPMG / PE / regulated-enterprise FDE interview questions. Pair it with the cost-tracing artifact in §3 and you have one repo answering three FDE/Solutions interview questions.
- **Why now:** The May 26 update is the **operational backbone** of the KPMG-style deals ([`01` §1](./01-big-lab-moves.md#1-kpmg)) — Digital Gateway *needed* private-MCP + perimeter-execution to deploy at all. You now have the same primitives KPMG is using. **Build with them while every applicant pool still thinks Managed Agents = Anthropic's cloud only.**

→ Cross-link: [2026-05-22/03 §1 the Opus/Sonnet orchestration loop](../2026-05-22/03-practical-skills-and-tools.md) — this update is what lets that loop run inside an enterprise · [`05` §1 the Big-4 lane](./05-career-and-startup.md#1-big4-lane).

---

## 2. OpenAI Codex 2026-05-27 update — Appshots, Goal mode, tax agents {#2-codex-updates}

**What shipped (May 27, 2026):**

1. **Codex Appshots (macOS)** — keybinding sends **the frontmost app's window** as a **screenshot + text payload** into Codex. Use case: you're debugging a Figma layout, or a SQL workbench, or a Linear ticket — one keystroke, the visual context is in. Frees you from "describe what you're looking at" prompting overhead.
2. **Goal mode expanded** — across the **app, IDE extension, CLI, and Chrome**. Goal mode = state the outcome, Codex iterates with tools (browser, repl, file edits) until success or budget exhaustion. Comparable to Claude Code's plan→annotate→execute loop, with a stronger browser-tool emphasis.
3. **Browser annotations + remote computer use** reliability improvements — fewer phantom clicks, better recovery from layout changes.
4. **ChatGPT Enterprise / EDU Skills governance**: dedicated admin page, workspace permissions, **upload scanning with risk review and blocking**, expanded Compliance Logs Platform support. This is the enterprise-IT side of Skills closing.
5. **Reference build published: "Building self-improving tax agents with Codex"** — the first OpenAI-authored reference for **agents that update themselves** against changing rules. Production-quality template; read it even if you don't work in tax (the patterns generalize to legal, compliance, eligibility, anywhere with frequent rule churn).

**Sources:**
- [OpenAI — Release notes (May 2026)](https://releasebot.io/updates/openai) `[aggregator]`
- [OpenAI — News](https://openai.com/news/) `[primary]`
- [OpenAI — Research index/release](https://openai.com/research/index/release/) `[primary]`
- [OpenAI — "Building self-improving tax agents with Codex"](https://openai.com/research/) (linked from the OpenAI news index, May 27 entry) `[primary]`

### Why it matters to you

- **Tonight (5 min):** If you're on macOS, set up Codex Appshots — even if you primarily use Claude Code for coding, **the visual-debug workflow is faster in Codex** for non-code tasks (Figma critique, SQL plan diagrams, design docs). Two-tool day: Claude Code for code, Codex Appshots for visual debugging.
- **Read this week:** the **self-improving-tax-agents** reference. The *meta-pattern* — "agents that monitor a rules source, regenerate their own prompts/tool definitions, and gate the change on eval" — is the **strongest generalizable agent template I've seen ship in months.** Apply it to any rule-driven domain in your portfolio (e.g., a Claude agent that updates itself when the AWS pricing page changes, with cost-impact alerts). One read, one portfolio artifact.
- **Compete-the-stack lens:** Notice that Codex Goal mode + Anthropic's Managed Agents + Google's Antigravity ADK 2.0 are **converging on the same primitives**: one API call, sandboxed execution, tool use, code execution, plan/iterate/verify. The skill the market is repricing is *not* "which agent stack" — it's **"orchestrate agents portably across stacks."** Maintain at least two stacks fluently. The Anthropic-stack focusing decision in [ME.md](../ME.md) still holds *for depth*; OpenAI Codex is the necessary breadth.

→ Cross-link: [2026-05-22/03 §1 the orchestration loop](../2026-05-22/03-practical-skills-and-tools.md) · [2026-05-20/01 §1 Antigravity / Managed Agents parity](../2026-05-20/01-big-lab-moves.md).

---

## 3. The cost-routing artifact, updated for this week's news {#3-cost-routing}

**What:** You've been carrying a "3-provider router + per-step cost log" project across [2026-05-10](../2026-05-10/) → [2026-05-20/03](../2026-05-20/03-practical-skills-and-tools.md) → [2026-05-22/03](../2026-05-22/03-practical-skills-and-tools.md). With **OpenRouter at $1.3B** ([`02` §2](./02-new-emerging.md#2-openrouter)) and **Gemini 3.5 Flash at $1.50/1M in** still the cheap-frontier anchor, **now is the right week to ship it.**

**Updated scope (final cut, ship by Sunday):**

1. **Three legs:** Claude (Opus-4.7 + Sonnet-4.6 split — orchestration + workers); GPT-5.5 Instant; Gemini 3.5 Flash.
2. **One MCP tool** the router can call (e.g., a local Postgres or a Notion-search MCP) so the **real-tool-verification** thread ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md)) is touched.
3. **Per-step cost log** in CSV → simple Streamlit dashboard. Columns: step, model, in-tokens, out-tokens, $cost, latency, success/fail.
4. **Reproduce one OpenRouter-style "route by cheapest-good-enough"** rule: cheap model first, escalate to expensive if confidence < threshold or eval-task fails. **This is a 30-line wrapper, not a startup.**
5. **README anchored to today's news:** 2 sentences on OpenRouter's $113M raise, 2 sentences on Gemini 3.5 Flash pricing, 1 sentence on Anthropic Managed Agents (Anthropic-stack depth signal). Make the artifact *visibly current.*

**Why this combination:** It answers the **four highest-frequency interview/portfolio questions** in one repo:
- **Orchestration:** Opus/Sonnet split + escalation rule
- **Real-tool verification:** the MCP leg, with one eval case
- **Cost awareness:** the dashboard
- **Multi-vendor judgment:** three legs, with one written 2-line "when to use which"

**Time budget:** ~6 hours if you reuse the existing 3-provider router code from [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md). Don't make this a clean-room rewrite.

**Sources (for the README):**
- [TechCrunch — OpenRouter $1.3B](https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/) `[secondary]`
- [VentureBeat — Gemini 3.5 Flash $1.50/1M analysis](https://venturebeat.com/) `[secondary]` (cite the specific May 19 piece you used on [2026-05-20](../2026-05-20/))
- [Anthropic — Managed Agents docs](https://docs.anthropic.com/) `[primary]`

### Why it matters to you

- **Job lens:** This is the **one artifact** that interview loops for FDE/Solutions/Integration roles at **Anthropic, OpenAI, Sierra, Cognition, OpenRouter (yes, they're hiring), Big-4 implementation lanes, GridCARE, and bank AI-risk teams** all map onto. One repo → many applications. **Ship by Sunday so it's on your resume before the Cognition-driven applicant flood hits next week.**
- **Startup lens:** This is *also* customer-discovery material. A real working router + cost log lets you walk into a 30-min conversation with any mid-market eng leader and ask: *"What does your per-eng AI spend look like, and where do you wish you had per-step attribution?"* That's a **5-minute validation conversation** for the "managed routing + governance" wedge ([`02` §2 startup lens](./02-new-emerging.md#2-openrouter)).
- **Insight:** Routing/cost is now a *priced* skill, not a *future* one. **CapitalG just paid $113M for the thesis.** The marginal hour you spend on this is worth more this week than a marginal hour on any of the other in-flight projects in [ME.md](../ME.md). Defer the others by 7 days; ship this.

→ Cross-link: [2026-05-22/03 §1 Opus/Sonnet orchestration](../2026-05-22/03-practical-skills-and-tools.md) · [`02` §2 OpenRouter](./02-new-emerging.md#2-openrouter) · [ACTIONS.md](../ACTIONS.md) — promote this artifact to the Saturday slot.
