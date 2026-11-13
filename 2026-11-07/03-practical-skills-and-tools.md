# Practical Skills & Tools — 2026-11-07

Two shipping events this period are the practical ones to internalize: **Claude Personal Finance (Nov 5)** makes **Plaid-over-MCP** a shipped production pattern you can copy, and **Claude Code 2.1.317 (Nov 3)** adds **MCP tasks in SDK sessions + stricter Agent SDK hook controls + usage-cost reporting** — the first version where the "build an MCP server for the Agent SDK" tutorial paths actually match the SDK's shipping defaults. The Saturday-weekend artifact flows directly from both: **rebuild your MCP-server portfolio artifact against 2.1.317 using the Plaid-sandbox pattern**, publish, send Monday.

Tags: `#claude-code #mcp #agents #sdk #plaid #tooling`

---

## 1. Claude Personal Finance (Nov 5) — Plaid-over-MCP as a production pattern {#1-claude-personal-finance}

**What shipped (2026-11-05):** Anthropic launched **Claude Personal Finance** as an **iOS beta** (expected Android + web roll next). Users connect their bank + credit-card accounts through **Plaid** (same Plaid-Link flow consumers already use for Venmo, Robinhood, etc.) and Claude can then answer questions about spending, build category dashboards, and surface anomalies. Access is **read-only** — Claude cannot initiate transfers, open accounts, invest, or alter balances. Available on Claude's existing consumer tiers (free + Pro).

**Sources:**
- [TechCrunch — Claude can now analyze your spending with its new Personal Finance tool (Nov 5)](https://techcrunch.com/2026/11/05/claude-can-now-analyze-your-spending-with-its-new-personal-finance-tool/) `[secondary]`
- [Yahoo Finance — Anthropic's Claude Can Now Read Your Bank Accounts](https://finance.yahoo.com/technology/ai/articles/anthropic-claude-now-read-bank-202740866.html) `[secondary]`
- [BleepingComputer — Anthropic wants Claude to analyze your bank account and financial data (earlier leak)](https://www.bleepingcomputer.com/news/artificial-intelligence/anthropic-wants-claude-to-analyze-your-bank-account-and-financial-data/) `[secondary]`
- [FourWeekMBA — Anthropic Preps Claude Personal Finance, Linked via Plaid](https://fourweekmba.com/ai-anthropic-preps-claude-personal-finance-linked-via-plaid/) `[analysis]`
- [MindStudio — AI personal finance: ChatGPT Plaid vs Claude agents](https://www.mindstudio.ai/blog/ai-personal-finance-chatgpt-plaid-claude-agents) `[analysis]`

### The pattern to internalize

Claude Personal Finance is not primarily a "personal finance" product — **it is Anthropic's first public example of a Plaid-connected MCP-style tool-use loop** on a regulated-data surface. The architecture, inferred from the integration + public docs:

1. **Plaid Link** inside the iOS app handles consent + credential handoff. User-facing explicit scope: "read-only."
2. **Plaid's API** returns a stable account ID + transaction stream to Anthropic's backend.
3. **Anthropic exposes a bounded tool surface** to Claude at inference time — typically `list_accounts`, `get_transactions(account_id, window)`, and category/anomaly helpers. These are MCP-shaped tools; whether the shipping path routes through the Claude Agent SDK's MCP runtime or an internal shortcut is undocumented, but the surface area is identical to what a third-party MCP server would expose.
4. **Read-only enforcement** happens at the tool-definition layer — no `transfer()`, no `trade()`, no `invest()` tool exists in the tool set. This is the right guardrail design: don't ship the capability.

### Why it matters to you

- **Job lens — this is your MCP-portfolio artifact.** The Nov-5 launch gives you a **named production reference** to cite in your artifact README: "This MCP server implements the same Plaid-connected tool pattern Anthropic shipped in Claude Personal Finance on Nov 5, 2026." A recruiter reading that one sentence has **zero ambiguity** about whether the pattern is real.
- **Startup lens — the pattern generalizes to every vertical with a regulated-data broker.** Replace Plaid with: **Change Healthcare / Particle Health** (patient records), **Finch** (payroll), **Snowflake** (enterprise data), **Carta** (cap tables), **Rippling** (HR). For each, build a **read-only MCP connector** + a bounded tool set + a consumer-facing surface. The barrier to entry per vertical is ~2–4 weeks of eng work once you have the pattern; the first mover in each wins the connector slot that Anthropic/OpenAI/Google will eventually consolidate against.
- **Insight — "capability by tool-definition" is the real safety story.** Every public safety discussion in 2026 has focused on model behavior and training. The Plaid pattern shows that **the shipped-product safety guarantee comes from the tool surface**, not the model. If Claude doesn't have a `transfer()` tool, it can't move money, however the user prompts. **This is the control-plane story to tell in interviews** for any AI-safety-adjacent role.

---

## 2. Claude Code 2.1.317 (Nov 3) — MCP tasks in sessions + stricter hook controls + weekend artifact {#2-claude-code-2-1-317}

**What shipped (2026-11-03):** Claude Code **2.1.317**. Headline additions:

- **Security checks** across the CLI + Agent SDK surface (details in release notes).
- **Stricter Agent SDK hook controls** — hooks now require explicit allowlisting; prior silent failures are now surfaced.
- **MCP tasks support added to SDK sessions.** With `CLAUDE_AUTO_BACKGROUND_TASKS=1` + streaming input, MCP tasks can now run in the background inside the SDK session. Server-side MCP tasks have been available since 2.1.304; **client surfaces still without it**: VS Code extension, desktop app.
- **Better usage + cost reporting** — explicit per-call cost + token counts in session output.
- **Dynamic tool lists** — Claude Code now refreshes only the tool list (not the full server spec) on `list_changed` notifications, cheaper + faster.
- **Wide reliability + session + scheduling + connectivity fixes.**

**Sources:**
- [Anthropic — Claude Code MCP docs](https://code.claude.com/docs/en/mcp) `[primary]`
- [Anthropic — claude-agent-sdk-typescript releases](https://github.com/anthropics/claude-agent-sdk-typescript/releases) `[primary]`
- [Releasebot — Claude Code 2.1.317 (Nov 3)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [DevelopersDigest — Claude Agent SDK in Late 2026: What Is New](https://www.developersdigest.tech/blog/claude-agent-sdk-whats-new-2026) `[analysis]`
- [Blake Crosley — Claude Code CLI: The Complete Guide — Hooks, MCP, Skills](https://blakecrosley.com/guides/claude-code) `[analysis]`

### Weekend artifact: Plaid-sandbox MCP server, built against 2.1.317

**The exact deliverable:**

- A **3-tool MCP server** (Node or Python, your preference) that connects to a **Plaid sandbox account**.
- Tools: `list_accounts()`, `get_transactions(account_id, window_days)`, `budget_check(category, threshold)`.
- **5-case eval**: happy path, empty account, token-expired, rate-limit, malformed category argument.
- **README** that: (a) links the Nov-5 Claude Personal Finance launch as the reference pattern; (b) shows the exact `.mcp.json` + `allowed_tools` configuration; (c) includes a 60-second demo gif using Claude Code 2.1.317 `claude -p` non-interactive mode.
- **Published**: GitHub repo + 1 short blog post tagged `#mcp #plaid #finance #claude`.

**4-hour build plan:**
- **00:00–00:30 (30 min)** — Scaffold with `claude-agent-sdk-typescript` quickstart. Confirm Claude Code `2.1.317` is installed (`claude --version`).
- **00:30–01:30 (60 min)** — Plaid sandbox account creation + Link flow + credential storage (use env vars, never commit; **put `.mcp.json` in git, secrets out of it** — matches the 2.1.317 guidance).
- **01:30–03:00 (90 min)** — Implement the 3 tools with correct `mcp__<server>__<tool>` naming (full name goes in `allowedTools`; bare name won't work — this is the single most common tool-not-called bug in SDK reports). Add 5-case eval with `max_turns` set (always set it for headless/automated runs). Use `permissionMode: "dontAsk"` with the `allowedTools` list to lock the agent down.
- **03:00–04:00 (60 min)** — Build README with named Nov-5 reference + 60-sec demo gif + publish to GitHub.

**Three subtle 2.1.317 gotchas** (all of these will save you from "it works locally but fails in the demo" at the worst moment):

1. **Tool name:** Always the **full** `mcp__<server>__<tool>` in `allowedTools`. A bare tool name and the agent silently can't use it.
2. **Malformed input schema = silent drop.** The server will register the tool but Claude won't see it. Validate your input schema against the SDK types before shipping.
3. **Subagent caps.** With the `claude_code` system prompt preset, the model is instructed NOT to call the Agent tool unless asked. With a custom or empty preset, you need to **add that guidance yourself** or your 3-tool server turns into a runaway swarm.

### Why it matters to you

- **Job lens — this is the artifact.** Your profile ([ME.md](../ME.md)) names this exact artifact as the first active one. Nov 5 just **named a production reference for its README** and Nov 3 just updated the SDK it runs on. **Ship it this weekend.** The 3-cold-emails-to-FDE-recruiters action from [ME.md](../ME.md) becomes "here is a shipped MCP server using the same Plaid-over-MCP pattern Anthropic shipped last week, with a 5-case eval and a 60-second demo." That is the strongest possible cold-email artifact for an FDE recruiter in November 2026.
- **Startup lens:** The artifact doubles as the Minimum Viable Demo for the **"Plaid-over-MCP for vertical X"** startup wedge from [`02` §4](./02-new-emerging.md#4-series-a-barbell).
- **Insight:** The 2.1.317 release pattern — **tighter hooks + explicit cost reporting + MCP tasks in sessions** — telegraphs the SDK's trajectory: **production-grade agent orchestration with per-call accounting.** The 2027 SDK will be an enterprise-grade product; the window to build a visible MCP portfolio is the next 90 days, before the market is saturated with Academy grads shipping the same artifacts.

---

## 3. Minor tools + tips roundup

- **ChatGPT Nov-4 image + GIF update** — GIF creation inside the Chat surface is now live for Plus/Pro. Useful for: README demo gifs without external tooling. Cite: [OpenAI News](https://openai.com/news/).
- **Anthropic Console (Nov 5–6):** beta IP allowlisting for Console access; beta project tags for enterprise orgs (spend-by-cost-code tracking). Useful if you have access to a team workspace through a side project. Cite: [Releasebot — Anthropic updates Nov 2026](https://releasebot.io/updates/anthropic).
- **TypeScript SDK (period roll-up):** MCP task support in SDK sessions, as covered in §2 above. If you're on the Python SDK, the parallel feature is tracked at the same version band but ships one release cadence behind.
- **Rule of thumb from the Nov-3 release notes:** keep `.mcp.json` in git, secrets in env vars, and grant each MCP server only the permissions it needs — mirrors the general least-privilege practice but is now explicitly a shipped SDK recommendation.
