# Practical Skills & Tools — 2026-11-01

Four artifacts to ship this week. The dominant practical shift is **the API `2026-10-21` cutover** — the first new Anthropic API version since `2023-06-01` (three-plus years). Paired with it: **Python SDK 2.0.0, TypeScript SDK 1.0.0**, a `/claude-api api-version` migration command in Claude Code `v2.1.307`, and a **27-release Claude Code train** (`v2.1.287 → v2.1.314` across 30 days) that shipped **Claude Mods** (your plugin lane), **Linux namespace sandbox** (run against untrusted repos safely), **native binary**, **skill hot-reload**, **Setup hook**, and platform-wide **Monitor**. Also in-window: **monthly API credits now bundled with Max/Ultra/Team seats** (collapse the two-wallet problem), **Simon Willison's "headless-MCP-first products"** quote (Oct 29), and **the prompt-caching discipline crystallizing as an SRE metric**.

Tags: `#api #sdk #claude-code #claude-mods #sandbox #mcp #prompt-caching #portfolio`

---

## 1. API `2026-10-21` — first new API version in 3+ years; Python SDK 2.0.0, TypeScript SDK 1.0.0; migrate pinned projects this week {#1-api-cutover}

**What shipped (2026-10-21):** Anthropic cut over to a new API version string **`2026-10-21`**, the first since **`2023-06-01`**. The cut-over carries breaking changes to request/response shapes and bumps **Python SDK to 2.0.0** and **TypeScript SDK to 1.0.0** as major releases. Claude Code `v2.1.307` added a **`/claude-api api-version`** command to move project code to the new version.

**What breaks (common cases):**
- Pinned API-version strings in production configs (anything hardcoded to `2023-06-01`)
- Request-shape changes (SDK migration docs enumerate; the migration command handles most)
- Legacy MCP server configs that assumed older response shapes

**What stays:**
- Model IDs (Haiku 5.5, Sonnet 4.5, Opus 5.5, etc.)
- MCP tool-call protocol itself
- Prompt-caching semantics (though pricing/TTL math unchanged, see [`§7`](#7-prompt-caching))

**Sources:**
- [DEV Community — "Claude API 2026-10-21: What breaks and how to upgrade"](https://dev.to/tokely/claude-api-2026-10-21-what-breaks-and-how-to-upgrade-1954) `[analysis]`
- [Claude Code changelog — v2.1.307 adds `/claude-api api-version`](https://code.claude.com/docs/en/changelog) `[primary]`
- [Releasebot — Anthropic Oct 2026 releases](https://releasebot.io/updates/anthropic) `[aggregator]`
- [github.com/anthropics/claude-agent-sdk-python — releases](https://github.com/anthropics/claude-agent-sdk-python/releases) `[primary]`

### What to do this week (90-minute block)

1. **Audit (15 min):** list every project that imports the Anthropic SDK or hardcodes the API version string.
2. **Migrate (45 min):** in each repo, run `claude /claude-api api-version` (Claude Code `v2.1.307+`). If a repo isn't a Claude Code workspace, follow the DEV writeup linked above — it's a mechanical SDK bump plus 2–3 breaking-change edits.
3. **Pin the new version (10 min):** add `anthropic-version: "2026-10-21"` headers in production configs; update `requirements.txt` / `package.json` to the new SDK majors.
4. **Write a 500-word migration post (20 min):** publish to your blog + LinkedIn with the exact diffs you shipped, titled "What breaks on the Anthropic API `2026-10-21` cutover (and the five minutes it takes to fix each one)." **This is a free portfolio artifact** — the recruiter reading your résumé next week has not written it.

→ Cross-link: [`§2`](#2-claude-code-releases) Claude Code `v2.1.307`.

---

## 2. Claude Code `v2.1.287 → v2.1.314` — 27 releases in 30 days; Claude Mods, Linux namespace sandbox, native binary, skill hot-reload {#2-claude-code-releases}

**What shipped (dates in-window):**
- **`v2.1.287` (Oct 1):** **Claude Mods** introduced — plugins that modify deeper interface behavior (panels, status lines, slash commands, hooks on tool calls); opt-in continuous review
- **`v2.1.288` (Oct 2):** one-keystroke recovery of lost work; per-finding control in code-review
- **`v2.1.300` (Oct 14):** prompt handling rework + agent-view customization
- **`v2.1.305` (late Oct):** **Linux namespace sandbox** support
- **`v2.1.307`:** **`/claude-api api-version`** migration command (see [`§1`](#1-api-cutover))
- **`v2.1.310`:** **Monitor** tool extended to Linux + macOS + Windows
- **`v2.1.314` (Oct 30):** auto-mode blocked-call messages now name the specific command + point to `/permissions`
- **Also in-window (undated in official log):** **Setup hook**, **skill hot-reload**, **switch to a native binary**

**Sources:**
- [Claude Code changelog — official (code.claude.com)](https://code.claude.com/docs/en/changelog) `[primary]`
- [claudelog — Claude Code changelog](https://claudelog.com/claude-code-changelog/) `[aggregator]`
- [Gradually — Claude Code Changelog (Oct 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [claudefa.st — Claude Code release notes 2026](https://claudefa.st/blog/guide/changelog) `[aggregator]`

### Three things to ship against this week

**(a) A Claude Mod — your 1-weekend portfolio artifact (6 hours).**
- Pick a visible-value Mod: **live model-cost meter during a session**, **MCP tool-call latency panel**, **cache hit-rate side pane**, or **S-1 reader panel** (reads SEC EDGAR as you code, surfaces the Anthropic S-1 risk-factor section).
- Scaffold with the `plugin-authoring` skill in this session.
- Publish to GitHub + submit to the Claude Code plugin registry.
- Why it reads strong: Mods are **brand-new as of Oct 1**. Very few candidates have shipped one. A shipped Mod on your résumé is a signal flare to a Solutions Engineer interviewer; it's "I ship on new primitives inside 30 days."

**(b) A Setup hook + hot-reloaded skill — the eval-authoring loop you've been deferring (90 min).**
- Setup hook triggers on `claude start`; preload your eval harness skill.
- Skill hot-reload means you iterate the skill in-place while a dev loop runs — **~10× faster iteration cycle** vs. prior "edit → restart" dance.
- Pair with the migration-post from [`§1`](#1-api-cutover) — the hot-reloaded skill is the "test the API-version migration diff on a 20-prompt eval suite" skill.

**(c) Namespace sandbox for untrusted-repo review (30 min to try).**
- You can now run Claude Code against candidate code, OSS forks you don't trust, scraped repos, without worrying about `.bashrc` writes or env-var reads.
- Specific use: **the Agent Skills AAIF registry** (see [`01` §3](./01-big-lab-moves.md#3-agent-skills-donation)) will have thousands of community-contributed skills; the sandbox lets you audit them locally without exposing credentials.

→ Cross-link: [`§1`](#1-api-cutover) API cutover · [`05` §3 portfolio](./05-career-and-startup.md#3-portfolio).

---

## 3. Monthly API credits bundled into Claude Max/Ultra/Team plans — API, Managed Agents, Agent SDK, `claude -p` {#3-api-credits}

**What shipped (rolled live mid-to-late Oct 2026):** **Claude Max, Ultra, and Team** plans now include **monthly API credits** usable against: (a) the Claude API, (b) Claude Managed Agents, (c) the Claude Agent SDK, and (d) `claude -p` (headless-mode Claude Code) when the API key is linked to the plan's Claude Console organization.

**Sources:**
- [Anthropic Support — Use the Claude Agent SDK with your Claude plan](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [Releasebot — Anthropic Oct 2026](https://releasebot.io/updates/anthropic) `[aggregator]`

### Why it matters

- **Immediate use:** The CI-driven eval runs you keep deferring are now **inside your seat quota**, not metered separate. Plan a weekend's worth of `claude -p` runs — one eval harness run per MCP server you build this month ([`§5`](#5-aws-labs-mcp)).
- **Portfolio implication:** When you publish an eval, publish the **cost per full run** too (now easy to compute from one wallet). "67% policy-adherence at $0.42/run on Haiku 5.5" is a far stronger résumé line than "67% policy-adherence."

→ Cross-link: [`§7`](#7-prompt-caching) prompt-caching discipline · [`04` §2 behavioral adequacy](./04-research-progress.md#2-eval-authoring-tier).

---

## 4. Simon Willison on headless-MCP-first products + 12-hour unattended Claude Code task {#4-headless-mcp-first}

**What happened (Oct 16, 22, 23, 29):** Four signals in-window from the single highest-signal practitioner blog in your SOURCES.md:

- **Oct 16 — continuous review as default + 12-hour Claude Code task:** "Review runs continuously, more like spellcheck while you write. Most changes get reviewed and fixed by Claude at least once before a human looks." Reports a Claude Code for Web task that ran **>12 hours** unsupervised.
- **Oct 22 — `datasette-mcp`:** Lets Claude search Simon's blog archive. Template for personal-knowledge MCP servers.
- **Oct 23 — single-prompt "Tool Quick Study" (canvas paintbrush sim):** Built with **one prompt to Claude Opus 5.5 High**.
- **Oct 29 — the thesis quote:** "**I want every product to be a headless MCP server that feeds an agent, so the user never has to think about the layers underneath.**"

**Sources:**
- [Simon Willison's Weblog — homepage](https://simonwillison.net/) `[primary]`
- [Simon Willison on claude-code (tag)](https://simonwillison.net/tags/claude-code/) `[primary]`
- [Simon Willison on sub-agents (tag)](https://simonwillison.net/tags/sub-agents/) `[primary]`

### Three deployable patterns

**(a) "MCP-first product design"** — now a stated design philosophy from the most-read practitioner. **Invert any tool-call-shaped startup feature from GUI-first to MCP-first.** If your startup backlog has one, ship MCP first, GUI second.

**(b) The 12-hour overnight Claude Code task** — pick one long-running codebase task this weekend and ship a public gist of the single-prompt + task-log. Candidates:
- Full type-annotation of a 10K-LOC JS project
- Exhaustive dead-code elimination on a 20K-LOC Python repo
- OSS repo porting from Python 3.8 → 3.13
- Full test-coverage pass on an untested OSS lib
- API migration from `2023-06-01` → `2026-10-21` on a 50-file codebase (meta — see [`§1`](#1-api-cutover))

**(c) The continuous-review question** — "**how do you *measure* the quality of continuous review?**" is the FDE interview question of Q4 2026, because the obvious failure mode is review-fatigue noise. Have an answer anchored in [`04` §2](./04-research-progress.md#2-eval-authoring-tier) (behavioral adequacy, 82.8% pass / 33.8% adequate).

→ Cross-link: [`01` §3 Agent Skills donation](./01-big-lab-moves.md#3-agent-skills-donation) · [`§5`](#5-aws-labs-mcp) AWS Labs MCP.

---

## 5. AWS Labs MCP mono-repo — three October releases; the gold reference corpus for MCP server authorship {#5-aws-labs-mcp}

**What shipped:**
- **Oct 12** (`2026.10.20261002180809`): added **Oracle Database@AWS**, multi-tenant **RDS Oracle**, and ODB Autonomous support in the Postgres/Oracle MCP server.
- **Oct 16** (`2026.10.20261015170211`): **Redshift** MCP server gained opt-in read-write mode + named transactions (previously read-only).
- **Oct 30** (`2026.10.20261030201955`): ~11 commits since previous release; fixes to **billing cost-management**, **MySQL**, and **AWS-documentation** servers.

**Repo scale:** ~70 open-source MCP servers maintained in `awslabs/mcp` — the single highest-signal reference corpus for MCP server authorship.

**Sources:**
- [awslabs/mcp — Releases (2026.10.*)](https://github.com/awslabs/mcp/releases) `[primary]`
- [awslabs/mcp — tag 2026.10.20261030201955](https://github.com/awslabs/mcp/releases/tag/2026.10.20261030201955) `[primary]`
- [awslabs/mcp — tag 2026.10.20261015170211](https://github.com/awslabs/mcp/releases/tag/2026.10.20261015170211) `[primary]`

### Weekend MCP-server plan (4 hours end-to-end)

**Don't reinvent what AWS already ships.** Instead:

1. **Pick a vertical SaaS without an MCP server** (per [`02` §3](./02-new-emerging.md#3-mcp-ecosystem)): legal practice management (Clio, PracticePanther, MyCase), dental (Dentrix, Open Dental), logistics TMS, real-estate CRM (Follow Up Boss, kvCORE, Chime), municipal/court records. (Financial Cents already shipped the accounting one Oct 20.)
2. **Fork `awslabs/mcp`'s `postgres` or `redshift` server as a scaffold** (90 min). You get battle-tested connection management, auth patterns, tool-schema templates for free.
3. **Ship 3 tools:** `search_<entity>`, `get_<entity>`, `create_<entity>_or_action` (or `update_*`). Keep scope tight — a shipped 3-tool server beats an unfinished 15-tool one.
4. **Write a 5-case eval using the BizAgentBench policy-vs-goal split** (see [`04` §1 B2](./04-research-progress.md#1-october-arxiv)). Report goal-pass + policy-adherence as two numbers.
5. **README:** 30-second demo gif, pricing-with-Haiku-5.5 estimate, link to the eval and the full task log.
6. **Publish:** GitHub + submit to the MCP Registry + wrap as an **Agent Skill** and submit to AAIF ([`01` §3](./01-big-lab-moves.md#3-agent-skills-donation)).

### Why this specific artifact is the single highest-signal Q4 2026 deliverable

- Hits **five rising categories at once:** MCP authorship, vertical SaaS, Agent Skills OSS contribution, eval authoring, policy-aware tool design.
- For a **Deloitte Associate GenAI, Accenture Senior GenAI, Anthropic Applied AI Engineer** loop — this is the artifact that bypasses the recruiter-screen filter and lands you at the hiring-manager read.
- 100+ open slots in non-dev-tool verticals; Financial Cents took one on Oct 20 — the ~50 others will land Q4. **Be one of them.**

→ Cross-link: [`§4`](#4-headless-mcp-first) Simon Willison headless-MCP · [`02` §3 ecosystem](./02-new-emerging.md#3-mcp-ecosystem) · [`04` §1 BizAgentBench corpus](./04-research-progress.md#1-october-arxiv) · [`05` §3 portfolio](./05-career-and-startup.md#3-portfolio).

---

## 6. OpenAI Codex CLI — rust-v0.161.0 (Oct 7) defaults to GPT-6.1 Sol; voice-control; Codex cloud-tasks start metering (Oct 20) {#6-codex-cli}

**What shipped:**
- **`rust-v0.160.0` (Oct 1):** fullscreen-terminal paste, easier task-history browsing
- **`rust-v0.160.1` (Oct 5):** fixed a Windows env-settings regression on remote servers
- **`rust-v0.161.0` (Oct 7):** **default model changed to GPT-6.1 Sol** (faster, cheaper than GPT-6); microphone + speaker config for voice conversations
- **Oct 20:** Codex *cloud* tasks start counting against plan usage limits (local Codex CLI stays outside quota)

**Sources:**
- [OpenAI Codex changelog (type=codex-cli)](https://developers.openai.com/codex/changelog?type=codex-cli) `[primary]`
- [Havoptic — Codex October 2026 releases](https://www.havoptic.com/releases/openai-codex/2026/10) `[aggregator]`
- [Scalevise — DevDay 2026 Developer Event (Codex rollout coverage)](https://scalevise.com/resources/openai-devday-2026-developer-event/) `[aggregator]`
- [Agentpedia — OpenAI DevDay 2026 Everything Announced](https://agentpedia.codes/blog/openai-devday-2026-everything-announced) `[aggregator]`

### Why it matters

- **Pattern-match the "cheap tier is now the agent-worker tier" thesis across labs:** Haiku 5.5 became Claude Code default (Oct 7); GPT-6.1 Sol became Codex CLI default (Oct 7). **Keep your router artifact's per-provider worker-model config dynamic** — these defaults will shift again before year-end.
- **Codex cloud metering (Oct 20):** any portfolio artifact you built on Codex cloud-executed tasks (not local CLI) needs to be re-costed. **Migrate to local Codex CLI** when possible, or move Codex workloads to Claude Code's `claude -p` (which is now covered by your Max/Ultra/Team API credits — see [`§3`](#3-api-credits)).

---

## 7. Prompt-caching discipline — cache hit-rate as the agent SRE metric {#7-prompt-caching}

**What's new:** The combination of (a) new agents built on long shared tool-definition blocks and (b) the API `2026-10-21` cutover (which changed some response shapes and invalidated some prior caches) has made **"cache hit-rate as an SRE metric"** the current cost-engineering frontier.

**Pricing math (Anthropic):**
- **Cache read:** ~0.1× input price (~90% discount)
- **5-minute TTL cache write:** 1.25× input
- **1-hour TTL cache write:** 2.0× input
- **Haiku 5.5 min cache size:** 1,024 tokens
- **Target hit rate:** ≥70% on an agent's intermediate steps; sub-70% signals prompt bloat or broken prefixes (reordered tool defs, dynamic timestamps in system prompts)

**Sources:**
- [OpenRouter — The Cheapest Token Is a Cached One: Prompt Caching + Sticky Routing](https://openrouter.ai/blog/tutorials/prompt-caching-sticky-routing/) `[analysis]`
- [Baytech Consulting — Prompt caching cuts agentic AI costs by up to 80% but only if you design for it](https://www.baytechconsulting.com/blog/prompt-caching-cuts-agentic-ai-costs-by-up-to-80-but-only-if-you-design-for-it.md) `[analysis]`
- [Fast.io — AI Agent Prompt Caching](https://fast.io/resources/ai-agent-prompt-caching) `[analysis]`
- [Morph — Prompt Caching: Anthropic / OpenAI / Google](https://www.morphllm.com/prompt-caching) `[analysis]`

### Weekend artifact — the personal Claude billing audit

The **"Personal Claude billing audit"** on your `ME.md` checklist is now the most tractable artifact in the queue. 1-weekend project:

1. **Pull your Console billing CSV** (last 90 days).
2. **Compute effective cache hit-rate** per agent / project.
3. **Compute per-session cost** and per-token effective price (accounting for cache reads).
4. **Identify the three cost-leaks** (sub-70% hit-rate sessions = where to focus).
5. **Publish a one-pager titled "Three mistakes that cost me $47 this month"** (or whatever your real number is).

This reads to every integration-engineer interviewer as proof you understand **the layer below the demos.** No one at the recruiter screen has written it. First-mover artifact for Q4 2026.

→ Cross-link: [`§3`](#3-api-credits) API credits in plans · [`05` §3 portfolio](./05-career-and-startup.md#3-portfolio).

---

## 8. Zed `1.24.2` (Oct 14) — ACP matures; Claude Code / Codex / Gemini CLI run natively inside Zed {#8-zed-acp}

**What shipped (2026-10-14):** Zed's `1.24.2` stable release matured the **Agent Client Protocol (ACP)** integration — a shared protocol that lets external coding agents (Claude Code, Codex CLI, Gemini CLI, OpenCode) run as a first-class pane inside Zed with the editor's file-tree + buffer context piped through. Reviewers rate Zed's built-in Agent Panel behind Cursor 3's Agents Window and the newly rebranded **Devin Desktop (formerly Windsurf)** for fully-autonomous multi-step work — but ACP makes the editor-vs-agent choice orthogonal.

**Numbers:**
- **ACP spec version:** `v0.56.0`
- **Windsurf → Devin Desktop:** rebranded in-window (`windsurf.com` → `devin.ai`)
- **Cursor:** `3.1` remains latest stable (April 2026)
- **Zed:** `1.24.2` released 2026-10-14

**Sources:**
- [Zed changelog / release notes](https://zed.dev/releases) `[primary]`
- [Agent Client Protocol — v0.56.0 release](https://github.com/agentclientprotocol/claude-agent-acp/releases/tag/v0.56.0) `[primary]`
- [Octave HQ — Windsurf vs Cursor vs Zed (2026)](https://www.octavehq.com/post/windsurf-vs-cursor-vs-zed-which-ai-ide-which-ai-ide-in-2026) `[analysis]`

### Why it matters

- **Startup lens:** ACP is the "USB-C of coding agents." If a thesis in your backlog is "the editor is the AI-first surface for devs," **ACP is the protocol to build *on*** — pulls model choice out of the IDE and makes "editor + agent" a mix-and-match market.
- **Job lens:** Learning the ACP spec is **under-the-radar depth** on an FDE résumé next to "I know MCP." Two of three practical patterns from Simon Willison ([`§4`](#4-headless-mcp-first)) + MCP + ACP = you can speak to the full agent-plumbing stack. **Expected on the Anthropic Applied AI Engineer loop within 1 year.**

→ Cross-link: [`01` §3 Agent Skills](./01-big-lab-moves.md#3-agent-skills-donation) · [`§5`](#5-aws-labs-mcp) MCP mono-repo.
