# Practical Skills & Tools — 2026-06-10

The week's most actionable shift: **Claude Managed Agents now run on schedules, securely use CLI tools, and connect to *your* private MCP server** — *and* yesterday's **AWS MCP Server GA** ([2026-06-09/02 §1](../2026-06-09/02-new-emerging.md#1-aws-mcp-ga)) makes the AWS side of that integration first-party-managed. Paired with the **Mythos-class routing matrix** (Fable 5 at the orchestrator level, Sonnet 4.6 as workers) and a **Tool Search trick that cuts MCP context overhead ~85%**, the practitioner stack is now materially cheaper *and* materially more deployable. Below: the install order, the routing matrix, and the eval pattern — exactly as you'd ship them as a portfolio artifact this weekend.

Tags: `#claude-code #managed-agents #mcp #scheduling #subagents #tool-search #cost #routing #aws-mcp`

---

## 1. Claude Managed Agents — schedules, CLI, private MCP, vault-stored env vars {#1-managed-agents}

**What happened:** Anthropic shipped a meaningful upgrade to **Claude Managed Agents** (the SDK-launched, lab-hosted variant of the agent loop):

- **Schedules:** Cron-based automation. Recurring jobs you don't have to babysit.
- **CLI tools, safely:** Agents can now invoke command-line tools inside a **sandbox you control** — not Anthropic's sandbox, *yours*.
- **Vault-stored environment variables:** Credentials live in a managed vault, not in code or prompts. Agents pull them at invocation, not at definition.
- **Browser-capable integrations:** Authenticated browser sessions for sites without APIs.
- **Private MCP server:** Connect Managed Agents to **your private Model Context Protocol servers** — agents now reach *your* internal tools, not Anthropic-hosted stubs.

This stack is the answer to *every* deployment objection from 2025: scheduling, auth, sandbox, internal-tool access — all primitives, all first-party.

**Sources:**
- [Anthropic — Newsroom (Managed Agents update)](https://www.anthropic.com/news) `[primary]`
- [Claude Code Docs — Best practices](https://code.claude.com/docs/en/best-practices) `[primary]`
- [DevToolPicks — Anthropic Splits Claude Subscriptions: Agent SDK Credit June 2026](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[analysis]`
- [Developers Digest — Claude Code Agent Teams, Subagents, and MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [Duet.so — Claude Code Skills Complete Guide: SKILL.md, MCP, Subagents & Teams (2026)](https://duet.so/guides/claude-code-skills-complete-guide) `[analysis]`
- [AntStack — Claude Agents, Subagents, Agent Teams, Skills & MCP: A Developer's Field Guide](https://www.antstack.com/blog/claude-agents-subagents-agent-teams-skills-and-mcp-a-developer-s-field-guide/) `[analysis]`
- [PubNub — Best practices for Claude Code subagents](https://www.pubnub.com/blog/best-practices-for-claude-code-sub-agents/) `[analysis]`
- [PubNub — Subagents Part II: From Prompts to Pipelines](https://www.pubnub.com/blog/best-practices-claude-code-subagents-part-two-from-prompts-to-pipelines/) `[analysis]`

### The build path — *do this tonight*

A concrete 90-minute build that turns last week's "Opus-orchestrator / Sonnet-worker" team into a **scheduled, sandboxed, AWS-MCP-hosted, private-MCP-connected service**:

1. **Pick the workflow.** Re-cut the dual-model "sanitiser" project (carried from [2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project) → [2026-05-22 lead](../2026-05-22/00-tldr.md)) as a **nightly compliance check** that runs at 02:00, scans yesterday's repo diffs, flags PII/secret patterns, posts results to a Slack channel.
2. **Install AWS MCP Server (yesterday's GA).** This is the **first step** — it gives you IAM-scoped agent permissions and CloudWatch per-call observability for free. The exact install steps are in [2026-06-09/03 §1](../2026-06-09/03-practical-skills-and-tools.md). About 15 minutes.
3. **Routing matrix.** Set the routing as: **Fable 5** at the orchestrator step (it triages which file gets which kind of scan); **Sonnet 4.6** at the worker step (it does the actual scan); **Haiku 4.5** at the "post to Slack with a summary" step. This gives you a *cost story* in three numbers — see Tool Search note below for the 85% MCP-overhead haircut.
4. **Wire the schedule.** Use Managed Agents' cron-based scheduling — daily at 02:00 in your tenant timezone.
5. **Sandbox + vault.** Drop the GitHub token, Slack webhook, and any PII regex configs into Managed Agents' env-var vault. Nothing in code; nothing in prompts.
6. **Private MCP (the *custom* one, on top of AWS MCP).** Stand up a minimal local MCP server (5 tools max: `list_yesterday_diffs`, `read_diff`, `flag_pattern`, `summarize`, `post_to_slack`). Point the Managed Agent at it. **Cap your MCP server count at 4–6** per Anthropic's updated guidance ([2026-06-09/03 §1](../2026-06-09/03-practical-skills-and-tools.md)) — Cursor's 40-tool ceiling fills faster than expected.
7. **Logs + eval.** Log each step's token cost (CloudWatch will do most of this for free via the AWS MCP Server). Run an eval set of 10 historical diffs (5 clean, 5 with planted secrets) once before shipping. **This eval IS the portfolio artifact** — see [`05` §2](./05-career-and-startup.md#2-shipping-bar).

### Why it matters to you

- **Job lens:** This is the **single most direct path** from your `ME.md` "MCP server + cost-aware agent design" focus to **a demonstrable artifact** — and it covers three of your four `ME.md` portfolio bullets in one build (Public MCP server / vertical workflow / cost audit). Lead with it in any FDE/Integration/Customer-Eng interview. The interview pattern: "I shipped X as a *scheduled* MCP-bound Managed Agent, on the Anthropic stack, with per-step cost logged at $Y/run." Three concrete claims in one sentence.
- **Startup lens:** Managed Agents + private MCP is the **fastest existing path to a vertical "Claude for X"** product. Pick a workflow (legal-doc-diff QA, ops-on-call triage, cron-scheduled fraud checks), put a custom MCP server in front of customer data, and you've got an enterprise-deployable service in days, not months. The platform risk is real — see "Microsoft Claude Code retreat" below — but the speed advantage is currently unmatched on the Anthropic stack.
- **Insight:** **The agent stack is sorting into a 3-layer architecture**: (a) **harness** (Managed Agents, Claude Code, Cursor) handles loop, retries, cost, sandbox; (b) **integration** (MCP servers) handles "what can this agent see and do?"; (c) **orchestration** (subagents, skills) handles "who does what step?". Engineers who understand all three layers are the *new* AI Engineer profile — and "all three" is *exactly* what your weekend artifact will demonstrate.

→ Cross-link: [`01` §1 Fable 5 as the orchestrator-tier model](./01-big-lab-moves.md#1-fable-mythos) · [2026-05-22/03 §1 Opus-orchestrator/Sonnet-worker cost pattern](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [`05` §1 the FDE/Integration-Engineer interview pattern](./05-career-and-startup.md#1-fde-hiring).

---

## 2. The MCP context-bloat trick — Tool Search cuts ~85% of context overhead {#2-tool-search}

**What happened:** A practitioner-level finding being repeated across multiple Claude-Code best-practice writeups: **a typical 5-server MCP setup with ~58 tools costs roughly 55,000 tokens *before* you send a single prompt** — because every tool description is in the system prompt. **Anthropic's Tool Search feature** (route the agent through a search-the-tool-catalog step before invocation) **cuts this ~85%**.

- The default behavior — list every tool definition in the system prompt — *was* the easy thing to do at <10 tools; at 58, it's wasteful.
- Tool Search loads only the relevant tools for the current step; reduces fixed overhead from ~55k → ~8k tokens.
- This is the same architectural move as **subagent context-forking** (covered next), just applied to *tools* instead of *work*.

**Sources:**
- [Claude Code Docs — Best practices](https://code.claude.com/docs/en/best-practices) `[primary]`
- [MCP Directory — Claude Code Best Practices (2026)](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [Developers Digest — Claude Code Agent Teams, Subagents, and MCP (2026 Playbook)](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [Antstack — Claude Agents, Subagents, Agent Teams, Skills & MCP: Developer's Field Guide](https://www.antstack.com/blog/claude-agents-subagents-agent-teams-skills-and-mcp-a-developer-s-field-guide/) `[analysis]`

### Why it matters to you

- **Job lens:** This is **exactly** the kind of "cost-aware agent design" claim your `ME.md` calls out as your active focus. Make it a one-paragraph addendum in any artifact README: *"Tool Search reduced our per-invocation overhead by 85% on a 58-tool MCP fleet; here's the before/after token log."* Concrete-number claims like this win FDE interviews.
- **Startup lens:** A startup that *automates* the "what to put in tool-search index" decision (or makes MCP tool definitions automatically tiered by usage frequency) is *exactly* the kind of picks-and-shovels play that compounds as MCP usage compounds. Low-glamour, high-utility.
- **Insight:** **Context is the new RAM.** Every "make the agent better" lever in 2026 is, underneath, *a context-management trick*: Tool Search (load only the tools you need), subagent forking (do messy work in a forked context), Skills (load only the right "how to" doc). The mental model for the next year of agent-skill development: think like an OS engineer managing limited memory.

---

## 3. Subagents — context-forking is now the default Claude Code pattern {#3-subagents}

**What happened:** Across multiple practitioner writeups from the last week, the dominant Claude Code pattern is settling on **subagents as a context-forking primitive** — not as a "multi-agent system" architecture choice. Implementer and QA agents run in a **forked context** doing the messy work (npm test, large diffs, iterative debugging), then return a **clean summary** to the orchestrator.

The decision framework crystallized:

- **Skills** = how to do something (load only the relevant docs).
- **MCP** = access to external systems (with Tool Search to control overhead — §2).
- **Subagents** = delegate work to a specialist *with its own context window* (return a summary).
- Most tasks don't need 5 agents. Start with one main agent + add specialists only when context separation provides clear value (typical team for a refactor: main + 1–2 implementers + test + review).

**Sources:**
- [Developers Digest — Agent Teams, Subagents, and MCP: 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) `[analysis]`
- [PubNub — Best practices for Claude Code subagents](https://www.pubnub.com/blog/best-practices-for-claude-code-sub-agents/) `[analysis]`
- [PubNub — Subagents Part II: From Prompts to Pipelines](https://www.pubnub.com/blog/best-practices-claude-code-subagents-part-two-from-prompts-to-pipelines/) `[analysis]`
- [Ofox — Claude Code: Hooks, Subagents & Skills Complete Guide (2026)](https://ofox.ai/blog/claude-code-hooks-subagents-skills-complete-guide-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** "When did you reach for a subagent vs a skill vs an MCP tool?" is now a *real* Claude-stack interview question. The answer you want ready: *"Skill for stable how-to knowledge; MCP for system access; subagent when the work would pollute the orchestrator's context — usually iterative testing or large-diff review."* That's two sentences of legible competence.
- **Startup lens:** A *templating* tool that generates a starter subagent topology for common workflows (refactor, code review, ops on-call, data-cleanup) is a tiny-team, fast-MVP play. Low TAM but high product-market fit with anyone building on Claude Code.
- **Insight:** The Claude Code stack now has the same three-layer shape Linux has: **harness (kernel) / MCP (drivers) / subagents (processes)**. Once you start thinking about it that way, *all* the recent best-practice writeups become a single, coherent narrative — and you stop being surprised when a new feature drops.

→ Cross-link: [`01` §1 Fable 5 / Mythos 5 fits as the "orchestrator-tier" model in this pattern](./01-big-lab-moves.md#1-fable-mythos).

---

## 4. The competitor map — Microsoft, Google, MiniMax now have coding contenders {#4-competitors}

**What happened:** While Anthropic owns the headline this week, the **coding-agent model market** has more entries than it did a month ago:

- **Microsoft MAI-Code-1-Flash** (June 2): beat **Claude Haiku 4.5** on SWE-Verified using **up to 60% fewer tokens** — the new "budget pick" for cost-sensitive workflows.
- **MiniMax M3** (June 1): frontier-level coding + **1M-token context window** — the new open-weight frontier pick.
- **NVIDIA Nemotron 3 Ultra** (June 4): another general-purpose contender.
- **Google Antigravity 2.0**: doubled down on agentic orchestration ("one agent codes a website while another generates brand assets").

The story underneath: **Anthropic still has the SWE-Verified lead at the top end** (Opus 4.8 + Fable 5), but the *cost tier* is now genuinely contested.

**Sources:**
- [CNBC — Microsoft and Google take on Anthropic and OpenAI in AI coding models](https://www.cnbc.com/2026/06/01/microsoft-and-google-take-on-anthropic-and-openai-in-ai-coding-models.html) `[secondary]`
- [The New Stack — Microsoft's quiet Claude Code retreat and the real cost of enterprise AI](https://thenextweb.com/news/microsoft-claude-code-retreat-ai-cost) `[secondary]`
- [Lushbinary — AI Coding Agents 2026 Comparison](https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/) `[analysis]`
- [The New Stack — Claude Code vs. Cursor vs. Codex vs. Antigravity — six months in](https://thenewstack.io/claude-code-vs-cursor-vs-codex-vs-antigravity-2026/) `[analysis]`
- [Felloai — Best AI Models in June 2026: ChatGPT, Claude, Gemini & Grok](https://felloai.com/best-ai-models/) `[aggregator]`
- [LLM Stats — AI Updates Today (June 2026): Latest AI Model Releases](https://llm-stats.com/llm-updates) `[aggregator]`

### Why it matters to you

- **Job lens:** Multi-vendor literacy is now table-stakes for Integration / FDE / Customer-Eng roles. Be able to say *which* model goes in *which* slot of a workflow and *why* — not "I'm an Anthropic person." Your `ME.md` already calls this out: *"Multi-vendor as production discipline; Anthropic-first for depth."* That framing now has live evidence.
- **Startup lens:** "Microsoft's quiet Claude Code retreat" is a *real* piece of market signal — large enterprises are stress-testing the unit economics of AI coding agents at scale, and not everyone is happy with the per-developer-per-month bill. Founder opportunity: **a router that ships every code-edit through the cheapest model that can complete it**, with quality gates at each tier. Defensibility: *the routing logic itself* (which model wins which task class) becomes proprietary IP within months.
- **Insight:** The interesting question isn't "is Claude still the best?" — it's **"which tier of coding work is now *commoditized* by a smaller, cheaper model?"** Right now: simple refactors and small-context fixes are commoditized (Haiku-class). What stays at the top: long-context, multi-file, agentic-loop coding. That's the work you should be building artifacts in.

→ Cross-link: [`01` §1 Fable 5 as the "stays at the top" tier](./01-big-lab-moves.md#1-fable-mythos) · [`05` §1 the routing-skill as an interview narrative](./05-career-and-startup.md#1-fde-hiring).
