# Practical Skills & Tools — 2026-07-17

Week's practical arc: **the agent-runtime skill you should be building right now is orchestrator + verifier + cost-instrumentation, not prompting.** Claude Code 2.1.212 splits background from inline delegation (`/fork` vs `/subtask`); the `ultracode` prefix lets you spawn multi-agent JS orchestrators up to 1,000 subagents; MCP `2026-07-28` is 11 days from GA and kills sessions entirely; Cursor 3.11 ships side chats and searchable agent transcripts; Simon Willison shipped four small tools in three days. But the single highest-ROI action this weekend is the **cache-hit engineering play** (ProjectDiscovery: 7% → 84% cache hit rate → 59% cost cut). Cache engineering *is* prompt engineering in 2026.

Tags: `#claude-code #cursor #mcp #ultracode #prompt-caching #subagents #shot-scraper`

---

## 1. Claude Code 2.1.212 — `/fork` is now background; `/subtask` is inline {#1-claude-code}

**What happened:** Anthropic split the old `/fork` behavior in two:

- **`/fork`** now copies your current conversation into a **new background session** (visible in `claude agents`) — the parent keeps going.
- **`/subtask`** is the new command for **inline delegated sub-conversations** (the old `/fork` behavior).

Other new-ish shipping in the same window:

- **Session-wide WebSearch cap** — default 200, tuneable via `CLAUDE_CODE_MAX_WEB_SEARCHES_PER_SESSION`.
- **Subagent-spawn cap** — `CLAUDE_CODE_MAX_SUBAGENTS_PER_SESSION` (default 200) — cheap runaway protection.
- **Auto-backgrounding** of MCP tool calls exceeding 2 min.
- **`/resume` picker** now includes **deleted sessions**.

**Sources:**
- [Claude Code changelog — code.claude.com/docs/en/changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Releasebot — Claude Code updates](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### Try tonight
1. Update Claude Code (`claude update`). On your next long refactor, run `/fork this into a background session and migrate every file under src/routes/ to Zod v4`.
2. Add `CLAUDE_CODE_MAX_SUBAGENTS_PER_SESSION=50` to your shell profile if you tend to over-delegate — cheap runaway protection.
3. Try `/resume` and pick a deleted session to test recovery.

### Why it matters (Job · Startup · Insight)
- **Job:** You can now review one PR while the previous refactor keeps running in another slot — a real productivity multiplier that shows up in interview code-samples.
- **Startup:** The spawn caps kill the $$ blowout that used to hide inside runaway delegation loops — a real ops-cost reduction.
- **Insight:** Anthropic is moving Claude Code from *"one live agent"* toward a **"supervisor over many background jobs"** model. Match your mental model + shell aliases to that shift.

**Tags:** `#claude-code #subagents #background-agents #cost-control`

---

## 2. Cursor 3.11 — side chats + searchable agent transcripts {#2-cursor}

**What happened:** Cursor 3.11 shipped:

- **`/side` and `/btw`** commands (or "+" in chat panel) — open a **parallel side chat carrying context from the main thread**. Durable, revisit-able, `@`-mentionable back into parent.
- **Cmd+K in the Agents Window** — searches every transcript via a **local index**.
- **Cmd+F** — in-conversation search.
- **New hooks:** `beforeSubmitPrompt`, `afterAgentResponse`, `subagentStart`, `stop` — build self-correcting loops around cloud agents.

**Sources:**
- [Cursor changelog — Side Chats and Conversation Search](https://cursor.com/changelog/side-chat) `[primary]`
- [Developers Digest — Cursor 3.11 Side Chats developer guide](https://www.developersdigest.tech/blog/cursor-3-11-side-chats-developer-guide-2026) `[analysis]`

### Try tonight
1. During your next debugging session, `/btw` to spawn a side chat for *"explain why this DI pattern was chosen"* without losing your main train.
2. Cmd+K in Agents Window → search a keyword from last week to prove the local index surfaces old work.
3. Wire an `afterAgentResponse` hook that runs `pytest --lf` and pushes failures back into the chat.

### Why it matters (Job · Startup · Insight)
- **Job:** No more "oh no I lost my thread by asking a tangent." Interview signal: *I use hooks to build feedback loops, not just prompt.*
- **Startup:** Transcript search means junior devs can mine senior sessions as institutional memory — a real onboarding lever.
- **Insight:** **IDEs are converging on the "many parallel agent tabs" workspace** — Anthropic's Claude Code and Cursor are racing to the same shape. Learn one deeply and the other transfers.

**Tags:** `#cursor #agent-orchestration #hooks #side-chat`

---

## 3. `ultracode` — type it and Claude writes a multi-agent JS orchestrator {#3-ultracode}

**What happened:** Prefix a prompt with **`ultracode`** (or set `/effort ultracode`) and Claude writes a **JavaScript script that fans work across up to 16 concurrent subagents (1,000 total per run)**.

- **Intermediate results live in script variables, not context** — so a 200-file audit finishes ~16× faster without token blowup.
- Runs are **resumable, saveable as `.claude/workflows/*.js` commands**.
- Bundled workflow: `/deep-research`.
- **New in v2.1.202:** a **"Dynamic workflow size"** `/config` setting (small/medium/large/unrestricted) that biases how many agents Claude spawns.

**Sources:**
- [Claude Code Docs — Orchestrate subagents at scale with dynamic workflows](https://code.claude.com/docs/en/workflows) `[primary]`
- [ContentBuffer — Dynamic Workflows in Claude Code (1000-subagent tutorial)](https://contentbuffer.com/guides/dynamic-workflows-claude-code-1000-subagent-tutorial) `[analysis]`

### Try tonight
1. `ultracode: audit every route handler under src/routes/ for missing auth checks, and adversarially verify each finding before reporting it`. Then hit `s` in `/workflows` to save the script as `/audit-routes`.
2. Set `Dynamic workflow size = medium` in `/config` if you want the safety rail on by default.
3. Run `/deep-research <question>` to see the pattern before you write your own.

### Why it matters (Job · Startup · Insight)
- **Job:** **One-shot codebase audits that used to be a two-day slog now run in the background while you have lunch.** That's a portfolio piece — literally record the run with `shot-scraper video` ([§6](#6-simon)) and it becomes an interview asset.
- **Startup:** Because agents run isolated and intermediate results never enter the parent context, **cost is linear in fan-out, not quadratic**. This is the *cheap* way to run a 200-item pipeline.
- **Insight:** **Anthropic and LangChain (Deep Agents dynamic subagents) both concluded that "let the model write code that spawns agents" beats "let the model call an agent tool in a loop."** The core skill is now *authoring orchestration harnesses*, not prompting.

**Tags:** `#claude-code #dynamic-workflows #ultracode #subagents`

---

## 4. Cache-hit engineering — the ProjectDiscovery 7% → 84% playbook {#4-cache-hit}

**What happened:** The concrete pattern getting traction across multiple production teams:

> **Order prompt blocks most-to-least stable — tool defs → system prompt → reference docs → conversation history → live user query — because any change to a block invalidates it AND everything after it on Anthropic.**

**ProjectDiscovery reported** raising cache hit rate **7% → 84%** by relocating dynamic working memory *out of the system prompt* and into a trailing user message. **Total LLM cost dropped 59%.** Anthropic's 5-min cache breaks even at **~1.4 reads per write**; below a **~30% hit rate the write premium loses money**.

**Sources:**
- [ProjectDiscovery — How We Cut LLM Costs by 59% With Prompt Caching](https://projectdiscovery.io/blog/how-we-cut-llm-cost-with-prompt-caching) `[analysis]`
- [DigitalApplied — Prompt Caching in 2026: Cut LLM Costs, Keep Quality](https://www.digitalapplied.com/blog/prompt-caching-2026-cut-llm-costs-engineering-guide) `[analysis]`
- [Anthropic — Prompt Caching docs](https://docs.claude.com/en/docs/build-with-claude/prompt-caching) `[primary]`

### Try tonight (30-min play; **HIGHEST-ROI ACTION THIS WEEK**)
1. **Log `cache_creation_input_tokens` vs `cache_read_input_tokens`** on every call for a day. If your hit rate on a "stable prompt" workload is **<60%**, something dynamic is stuck at the top.
2. **Move any per-request scratchpad, retrieved memory, or timestamp OUT of your system prompt** and into a trailing user turn.
3. **Add explicit `cache_control` breakpoints** between stable and dynamic blocks so you don't accidentally invalidate expensive prefixes.

### Why it matters (Job · Startup · Insight)
- **Job:** **One afternoon of prompt reordering typically returns 40–90% off the input bill.** This is the single most legible cost-optimization skill on a resume right now — it's what "AI Integration Engineer" roles actually measure you on. Doubles as artifact material.
- **Startup:** **Instrument first, optimize second** — the teams capturing the pricing table's promised savings are the ones tracking hit rate per layer. If you're pre-revenue, this is the difference between $2K/mo and $500/mo API bills.
- **Insight:** **"Prompt engineering" in 2026 is really "cache engineering."** The 2024-era "context stuffing" reflex is now anti-pattern — every stable byte you put at the *end* of your prompt costs you 10× the money and latency vs the *beginning*.

**Tags:** `#prompt-caching #cost-optimization #anthropic-api #observability`

---

## 5. MCP `2026-07-28` stateless spec — 11-day sprint before GA {#5-mcp-spec}

**What happened:** The **largest MCP revision since launch** (RC live now, **GA July 28**):

- **Sessions and `Mcp-Session-Id` header are gone** — protocol version, client identity, and capabilities now travel in a **`_meta`** object on every request.
- Every Streamable HTTP request must include **`Mcp-Method`** and **`Mcp-Name`** headers → enables gateway routing without payload inspection.
- **Long-lived GET SSE streams replaced by the Multi Round-Trip Request pattern** (`InputRequiredResult` with opaque `requestState`).
- **`Roots`, `Sampling`, and `Logging` are deprecated.**
- Error code **`-32002` → `-32602`** (JSON-RPC standard).
- Net: **your MCP server can drop sticky sessions and run behind a plain round-robin load balancer.**

**Sources:**
- [MCP Blog — The 2026-07-28 MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [mcpmigrate.dev — Every breaking change in the 2026-07-28 MCP spec](https://mcpmigrate.dev/blog/mcp-spec-2026-07-28-migration-guide) `[analysis]`

### Try tonight
1. **Grep any MCP server you maintain for `Mcp-Session-Id` and `session_id`** — those must move to `_meta` fields.
2. Add `Mcp-Method`/`Mcp-Name` headers to every outbound call in your client; set `ttlMs` + `cacheScope` on your `tools/list` responses so clients can cache them.
3. **Test against the RC before July 28** — Tier-1 SDKs ship support inside the 10-week window and your gateway config likely needs a redeploy.

### Why it matters (Job · Startup · Insight)
- **Job:** This is the moment your **MCP server ops story stops requiring Redis** — a nice "I migrated an MCP server to the stateless spec" line for interview stories in the next 60 days.
- **Startup:** The new spec **unblocks selling MCP servers behind commodity load balancers**, cutting infra bills and simplifying enterprise procurement.
- **Insight:** **MCP is transitioning from an experimental protocol to something enterprises can operate with standard OAuth + HTTP tooling.** That's the "protocol crosses the enterprise-readiness chasm" moment — expect a 90-day surge in commercial MCP server startups (already visible: mcpmigrate.dev, Speakeasy MCP tooling).

**Tags:** `#mcp #protocol-migration #infrastructure`

---

## 6. Simon Willison's July tool sprint — `claude-token-counter`, `mermaid-ascii`, `grok-mermaid`, `llm-cliche-highlighter` {#6-simon}

**What happened:** Simon shipped **four small tools in three days** (July 15–17):

- **`llm-cliche-highlighter`** (Jul 17) — flags AI-tell phrases ("delve into", "seamlessly", "harnessing the power") in text.
- **`mermaid-ascii`** (Jul 16) + **`grok-mermaid`** (Jul 15) — round-trip diagrams from text.
- **`claude-token-counter`** (Jul 16) — counts tokens for the Claude tokenizer **locally**, no API.

Related June release still hot: **`shot-scraper video`** (from `shot-scraper 1.10`) — your coding agent can now record a **WebM demo of its own work**. Give it a `storyboard.yml` (setup, viewport, scenes of click/type/wait_for/screenshot actions), Playwright records the routine.

**Sources:**
- [tools.simonwillison.net](https://tools.simonwillison.net/) `[primary]`
- [Simon Willison's Weblog](https://simonwillison.net/) `[primary]`
- [shot-scraper video (June 30 post)](https://simonwillison.net/2026/Jun/30/shot-scraper-video/) `[primary]`

### Try tonight
1. Paste your last AI-drafted email into `llm-cliche-highlighter` and see how much "delve into" / "seamlessly" survives.
2. `pip install shot-scraper` then write a 10-line `storyboard.yml` that logs into your local app and clicks through the happy path — **attach the WebM to your next PR**.
3. Bookmark `claude-token-counter` for moments you need to size a prompt without hitting the API.

### Why it matters (Job · Startup · Insight)
- **Job:** **A 30-second video demo of your feature working closes reviewer questions faster than a screenshot.** Attach a `shot-scraper video` demo to your portfolio project readmes.
- **Startup:** **Simon's toolchain is the reference implementation of "tiny sharp CLI tools that agents can call"** — study it as a design pattern for the tools your MCP server exposes.
- **Insight:** **The AI-writing-style filter is quietly becoming a required step in any content pipeline.** Expect enterprise content-moderation to add "AI-tell removal" as a standard step by Q4.

**Tags:** `#simon-willison #shot-scraper #tokenizer #ai-detection`

---

## 7. Visual Studio + JetBrains Copilot — MCP fingerprint validation + BYOK expansion {#7-copilot}

**What happened:** July 14 GitHub Copilot updates:

- **Visual Studio** now validates **MCP server trust at startup** by comparing the server's **config and asset fingerprint** against a trusted baseline; if anything changed, a trust dialog blocks the connection. (Closes a real supply-chain vector — someone else swaps your MCP server's tool defs.)
- **Refreshed Copilot Usage window** — real-time consumption + proactive alerts approaching quota.
- **Right-click a PR in the Git Repo window** → adds to Copilot Chat as context (descriptions, files, comments). Or `#<PR-id>` inline.
- **JetBrains Copilot expanded BYOK** with **OpenAI-compatible custom endpoints** — bring your own key, route to Groq, Fireworks, Together, or your own vLLM.

**Sources:**
- [GitHub Changelog — Copilot in Visual Studio June update](https://github.blog/changelog/2026-07-14-github-copilot-in-visual-studio-june-update/) `[primary]`
- [GitHub Changelog — Copilot for JetBrains expands BYOK capabilities](https://github.blog/changelog/2026-07-14-github-copilot-for-jetbrains-expands-byok-capabilities/) `[primary]`

### Try tonight
1. Right-click your last merged PR in Visual Studio → add to Copilot Chat → ask *"what regressions are likely?"*.
2. If you're on JetBrains, point Copilot at a **Groq or Fireworks endpoint via BYOK** to slash inference cost on completions.
3. Turn on the Copilot Usage window alerts before you spend your monthly quota accidentally.

### Why it matters (Job · Startup · Insight)
- **Job:** No more *"wait, why is my Copilot bill $400 this month"* surprise.
- **Startup:** **MCP fingerprint validation closes a real supply-chain vector** (someone else swaps your MCP server's tool defs). If you're building MCP servers, publish stable fingerprints alongside your releases so downstream users can pin.
- **Insight:** **The IDE vendors have accepted that developers want provider routing at the completion layer, not just chat.** That's the *cost-router* pattern from the daily editions ([2026-05-10](../2026-05-10/)) landing inside the IDE. Provider abstraction is now a mainstream tooling assumption.

**Tags:** `#github-copilot #mcp-security #byok #cost-monitoring`

---

**Highest-ROI thing to try tonight:** **Instrument `cache_creation_input_tokens` vs `cache_read_input_tokens` on one production endpoint, then move any dynamic content out of your system prompt into a trailing user turn** — this is the [§4](#4-cache-hit) ProjectDiscovery **7% → 84%** cache-hit fix, and it is the single change most likely to cut your Anthropic bill in half by tomorrow morning. Bundle it with a **10-line `shot-scraper video`** recording of the before/after (see [§6](#6-simon)) and you have a portfolio artifact that answers *cost, observability, and orchestration* in one screenshot.
