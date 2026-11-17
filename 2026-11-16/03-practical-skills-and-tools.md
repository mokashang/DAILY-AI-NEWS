# Practical Skills & Tools — 2026-11-16

Three concrete upgrades to make this week, in order of pay-off per minute spent: **(a) bump to Claude Code 2.1.319** — the new MCP-tasks-in-terminal, deny-not-prompt permission, and Apps Gateway controls materially change the auto-mode workflow and are mandatory for anyone using `/loop`-style agents in CI; **(b) update `llm` 0.37 and point it at `gpt-6.1-sol` / `gpt-6.1-terra`** — Simon Willison's release covers two months of fixes and adds an easier OpenAI-compatible endpoint command (critical for pipe-native workflows against Together/Fireworks); **(c) ship one MCP server on the 2026-07-28 stateless spec** — this is the single highest-leverage portfolio artifact for an FDE application in the ANT-pricing week. The thread beneath all three: as model prices fall and token volume grows, the leverage is in **control-plane skills (routing, sandboxing, hooks, permissions)**, not model fluency.

Tags: `#claude-code #mcp #llm #tooling #vibe-coding #sandbox #skills`

---

## 1. Claude Code 2.1.319 — MCP tasks in terminal, "deny instead of prompt" permission, Apps Gateway controls {#1-claude-code-2-1-319}

**What happened (2026-11-06 headline; 2.1.317 Nov 2, 2.1.318 Nov 3):**
- **MCP tasks in terminal (new, 2.1.319):** Long-running MCP tool calls move to the background so the conversation doesn't stall on a slow tool. A new env var toggles this off for scripted/non-interactive runs.
- **New permission setting: "deny instead of prompt."** Important for CI and auto-mode runs — the agent fails closed instead of waiting on an interactive approval that never comes.
- **Claude Apps Gateway controls** for admins: centralized model / skill / MCP routing with cost and rate-limit policy at the org level.
- **2.1.317 (Nov 2):** Gateway cost reporting for admins, stricter Agent SDK hooks, safety prompts; fixed first-turn disconnect for project+local MCP servers.
- **2.1.318 (Nov 3):** earlier warnings before `claude.ai` sign-in expires.
- **Bash-sandbox + skills nuance:** when the Bash sandbox is on, `.claude/skills/` loads **only** when CC starts in that folder or moves there via `/cd` — easy to miss and a common cause of "my skill isn't loading."

**Sources:**
- [Claudekit — Claude Code 2.1.319 update](https://claudekit.io/en/updates/claude-code-2-1-319/) `[aggregator]`
- [LabMemo — CC 2.1.319 Auto Mode + Gateway + MCP Task (JP)](https://labmemo.com/claude-code-v2-1-319-auto-mode-gateway-mcp-task-2026-11/) `[aggregator]`
- [Havoptic — November 2026 Claude Code releases](https://www.havoptic.com/releases/claude-code/2026/11) `[aggregator]`
- [Claude Code official changelog](https://code.claude.com/docs/en/changelog) `[primary]`

### Why it matters to you

- **Job lens:** **"Deny instead of prompt"** is exactly the control-plane primitive FDE interviews probe for. If you can explain in 30 seconds **when you'd use deny vs prompt vs allow** (hint: CI → deny, interactive debugging → prompt, trusted auto-mode → allow) with a concrete example from your own `.claude/settings.json`, you have an interview-ready story that signals real operational depth. For MLE interviews, **MCP tasks in terminal** is the practical version of "how do you orchestrate long-running tool calls without blocking the agent loop" — a distributed-systems question, dressed up.
- **Startup lens:** **Apps Gateway** is Anthropic's quiet admission that **cost + skill routing is now an enterprise-table-stakes feature, not a differentiator**. If your startup was selling "cost-aware routing" or "central skill registry" as the wedge, you need to pivot *above* that layer: per-vertical skills, eval harnesses, compliance audit trails, data-governance for MCP connectors. Build on top of the Gateway, not against it.
- **Insight:** The **`.claude/skills/` + `.claude/hooks/` + `.claude/settings.json`** triplet is the **2027 version of `.editorconfig`** — a per-repo, version-controlled, team-shared operational contract for coding agents. Repos that ship these files in `main` will out-recruit repos that don't, because they advertise "we take agent-ops seriously." **Make yours this week.**

### Action this Monday (15 min)
1. `npm update -g @anthropic-ai/claude-code` (or your install method). Verify 2.1.319+.
2. Add `"permissions.default": "deny_if_unattended"` to `.claude/settings.json` on your main project.
3. Add a `MCP_TASKS_IN_TERMINAL=true` env toggle to your `.envrc`.
4. Commit all three in one PR titled `agent-ops: adopt CC 2.1.319 controls`. That PR is a portfolio artifact.

→ Cross-link: [`02` §3 — Devin multi-repo](./02-new-emerging.md#3-devin-multi-repo) · [`03` §3 — MCP 2026-07-28 default](#3-mcp-2026-07-28)

---

## 2. Simon Willison's `llm` 0.37 — 2 months of fixes, new models, easier OpenAI-compatible endpoint config {#2-llm-0-37}

**What happened (2026-11-02):**
- **`llm` 0.37** released, covering ~2 months of accumulated features and fixes since 0.36.
- **New models registered:** `gpt-6.1-sol`, `gpt-6.1-terra` (per third-party coverage; Simon's own release post is brief).
- **New command:** easier configuration of OpenAI-compatible endpoints — directly relevant to piping `llm` against **Together / Fireworks / Groq / vLLM-self-hosted** without manually editing `~/.config/io.datasette.llm/extra-openai-models.yaml`.
- Release-note says "cheaper default", details unspecified in Simon's post body.
- **Caveat:** Simon's naming has shifted model-family labels between 0.36 and 0.37; double-check `llm models list` after upgrade and confirm the version in `github.com/simonw/llm/releases` before quoting model names in a doc or interview.

**Sources:**
- [Simon Willison — Release llm 0.37 (Nov 2)](https://simonwillison.net/2026/Nov/2/llm/) `[primary]`
- [LetsDataScience — Willison releases llm 0.37 w/ GPT-6.1 + cheaper default](https://letsdatascience.com/news/simon-willison-releases-llm-037-with-new-gpt-61-models-and-c-82383ed8) `[aggregator]`

### Why it matters to you

- **Job lens:** `llm` is the **"Unix pipe for LLMs"** — a tool interview panels love because it signals you work in the terminal, not in a chat window. The one-liner to have memorized: `git log --since="7 days" | llm -s "What shipped this week? Summarize for a non-technical stakeholder."` That is a defensible answer to "how do you use LLMs day-to-day?" in any MLE/FDE loop.
- **Startup lens:** **Simon's work is the leading indicator for what will be in `pip install langchain-cli` 6 months from now.** Watching his blog is free market research. In particular, **OpenAI-compatible-endpoint easing** is the signal that **self-hosted + Together + Fireworks are now first-class citizens** for Python-centric teams — if your startup built on OpenAI SDK lock-in as a soft moat, the moat is gone by Q1 2027.
- **Insight:** **CLI-native LLM tooling is the practitioner signal** of 2027. Anyone who can hold forth on Simon's `llm` + `files-to-prompt` + `shot-scraper` + `strip-tags` + `datasette-llm` stack is operating three levels above a prompt-engineer. Learn one of these every weekend.

### Action this Monday (5 min)
```
pipx upgrade llm       # or: uv tool upgrade llm
llm models list        # confirm gpt-6.1-sol, gpt-6.1-terra
git log --since="1 week" | llm "Summarize what shipped this week in <50 words."
```

→ Cross-link: [`03` §3 — MCP 2026-07-28](#3-mcp-2026-07-28) · [`04` §1 — Memory-in-agents resurface](./04-research-progress.md#1-memory-in-agents)

---

## 3. MCP 2026-07-28 is now the default — stateless handshake, hardened auth, graduated extensions {#3-mcp-2026-07-28}

**What happened (rolled out progressively; now the default on Claude.ai and in CC):**
- **Stateless core:** The initial handshake has been removed; sessions are optional. Simpler to deploy on edge / serverless platforms.
- **Hardened authorization** across the OAuth flow and transport layer.
- **Graduated official extensions** — resources, prompts, sampling, elicitation — stabilized out of "experimental."
- **GitHub MCP Server** already supports it; **Claude.ai connectors negotiate 2026-07-28 by default**, with a legacy opt-out for pre-July 2026 servers.
- **Practical implication:** A working MCP server is still the **#1 portfolio artifact** for FDE applications — but it must speak the stateless handshake. **Any example MCP server older than July 2026 needs the shim or a rewrite** before you demo it to an Anthropic recruiter.

**Sources:**
- [MCP Blog — 2026-07-28 release](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [Claude — Bringing MCP 2026-07-28 to Claude](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) `[primary]`
- [HackerNoon — What the 2026 spec actually changes for your servers](https://hackernoon.com/mcp-just-went-stateless-what-the-2026-spec-actually-changes-for-your-servers) `[secondary]`

### Why it matters to you

- **Job lens:** **One MCP server + one eval + one `README` with a 30-second Loom = a credible FDE portfolio** at Anthropic, Glean, Distyl, Sierra, Harvey, and every applied-AI shop in the Ramp top-10. Pick a mundane-but-real tool connection (your bank CSV, your Google Calendar via a read-only token, your `git log`), ship it with 3 tools + 5 eval cases, host it on `smithery.ai` or your own URL, link it from your résumé. **This is ~1 weekend of work and clears 80% of applicant filtering.**
- **Startup lens:** **Stateless + edge-deployable MCP collapses the "AI agent middleware" cost basis.** You can serve an MCP connector from a Cloudflare Worker for pennies per 1000 calls, which means **"AI connector marketplace"** is a viable startup wedge *again* — specifically if you own distribution (vertical community, enterprise procurement relationships, niche SaaS integrations your target customers already use). Smithery, mcp.so, and Puppeteer-Modal-wrappers are the early movers; the gap is in **vertical catalogs with real eval harnesses**.
- **Insight:** The MCP spec cadence (now quarterly) is the **single clearest leading indicator of where the agent stack is headed**. Read every release note on the day it ships. The `July 2026` spec made MCP cheap enough for every SaaS to publish a connector; the next spec (expected Q1 2027) will probably standardize **long-running / streaming / multimodal** — which is where "Meetings-style join-and-act" agents and voice-first SaaS will land.

### Action this weekend (1 afternoon)
1. `uvx create-mcp-app` (or `npm create mcp-app`) scaffolds a 2026-07-28-compliant server.
2. Add 3 tools that touch a real dataset you care about (bank CSV, GitHub issues, Google Calendar).
3. Write 5 eval cases (`good_input → expected_output`) using Anthropic's `evals` SDK.
4. Host on Smithery or a Cloudflare Worker. Put the URL on your résumé.
5. Record a 60-second Loom. Link from your résumé's top section.

→ Cross-link: [`02` §4 — Execution bottleneck](./02-new-emerging.md#4-execution-bottleneck) · [`05` §2 — FDE comp bands](./05-career-and-startup.md#2-fde-comp-bands)

---

## 4. Tactical pattern of the week: pick a sandbox and ship {#4-execution-pattern}

**What's circulating (Nov 10–16 on HN, X, GitHub trending):**
- The crystallizing reframe: **"models are commoditizing faster than expected (Ramp Nov 2026 confirms prices falling faster than usage), so the differentiator is where your agent runs — not what model it calls."**
- **Tier-1 execution sandboxes to know by name:** **E2B**, **Daytona**, **Modal Sandboxes**, **Cloudflare Browser Rendering**, **Vercel Sandbox**, **AWS Bedrock Sessions**.
- Vercel Labs' `agent-desktop` repo is climbing GitHub trending in November — a signal that **"agent UI + sandboxed execution"** is a real product surface, not just internal tooling.

**Sources:**
- [CoddyKit — November 2026 trending AI repos](https://www.coddykit.com/pages/blog-detail?id=5130015) `[aggregator]`
- [OSS Insight — AI trending (live)](https://ossinsight.io/trending/ai) `[aggregator]`

### Why it matters to you

- **Job lens:** **"I built a browser-using agent that executes inside E2B / Vercel Sandbox, with Claude Code as the orchestrator and an MCP server for the vertical-specific tools"** is a **single-sentence résumé line that beats 80% of applicants**. The underlying project is ~3 weekends. The hiring signal it sends — you understand MCP, sandboxes, orchestration, and have an opinion about agent control-plane — is worth more than any single "I fine-tuned X" line.
- **Startup lens:** **Cheapest moat in 2027: vertical workflow + sandbox + MCP server, no training.** Pick a boring vertical (real-estate comp-pulls, SaaS migration audits, procurement RFP analysis, legal discovery triage), build the workflow on top of an off-the-shelf sandbox, charge flat-rate per month, let token prices fall underneath you — margin expands on a flat price.
- **Insight:** **The "execution bottleneck" claim will be a cliché by Q1 2027.** Being the person who adopts it in November 2026 is a 60-day head start on the market narrative. Use the lead time to ship, not to opine.

### Action this weekend
Pick **one** sandbox from the list above, build **one** workflow that touches **one** real dataset, connect **one** MCP server you wrote, publish a 2-minute demo. Call it done by Sunday. Iterate next weekend.

→ Cross-link: [`02` §4 — Execution bottleneck](./02-new-emerging.md#4-execution-bottleneck) · [`01` §5 — Apple Siri AI preview](./01-big-lab-moves.md#5-apple-siri-ai-dev-preview)

---

## 5. The 60-second cheat sheet for this week {#5-weekly-cheatsheet}

| What | Where | Time | Why |
|---|---|---|---|
| Upgrade Claude Code to 2.1.319 | `npm update -g @anthropic-ai/claude-code` | 2 min | Deny-not-prompt + MCP tasks in terminal = `/loop`-safe CI |
| Upgrade `llm` to 0.37 | `pipx upgrade llm` | 2 min | New GPT-6.1 models + easier OpenAI-compatible endpoints |
| Ship one MCP server (2026-07-28 spec) | `uvx create-mcp-app` | 1 afternoon | #1 FDE portfolio artifact, works by Sunday |
| Pick & use one sandbox | E2B / Vercel Sandbox / Daytona | 1 weekend | "Execution layer" résumé line |
| Read NVDA FY27Q3 call transcript | Tue Nov 17 after close | 20 min | Rubin CPX SKU detail = 2027 inference pricing floor |
| Watch ANT Day 1 trading | Thu Nov 19 open | 15 min | Public comp print for every AI-adjacent counter-offer |

---

### Sourcing caveats

Claude Code changelog aggregators are reliable but **version-number drift** (2.1.317 → 319 in 4 days) means the specific features listed above may land, rename, or move between minor releases — verify against `code.claude.com/docs/en/changelog` before you cite exact release numbers in a résumé. Simon Willison's 0.37 release post is primary but brief; the GPT-6.1 model names (`-sol`, `-terra`) come from third-party coverage and should be re-verified via `llm models list` locally. MCP 2026-07-28 is confirmed primary. The "execution bottleneck" thesis is thesis-level synthesis — the sandbox list is my recommendation, not a published ranking.
