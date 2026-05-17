# Practical Skills & Tools — 2026-05-17

Sunday is the **ship day** of the AI-news week. Today: five hands-on plays you can complete tonight, ordered by ROI per minute. Total time-cap: 4 hours. If you do only one, do #1.

Tags: `#claude-api #cost-optimization #caching #claude-md #karpathy #mcp #io2026 #playbook`

---

## 1. Prompt Caching: The 60–90% Cost Cut You're Probably Not Using {#1-prompt-caching}

**Why now:** Anthropic Agent SDK metering goes live **June 15** (T-minus 29 days). On that day, every programmatic call (`claude -p`, Agent SDK, GitHub Actions, Cowork, third-party SDK wrappers) gets billed at **full API list rates** from a separate monthly credit pool that mirrors your subscription tier ($20 / $100 / $200). Prompt caching is the **single most reversible, lowest-risk optimization** that compounds with every cached read for the rest of 2026.

### The pricing math (Claude API as of May 2026)
- **Cache write** (first call that stores cached block): **1.25× standard input price** (5-min TTL) or **2× standard input price** (1-hour TTL).
- **Cache read** (every subsequent call that hits the cache): **10% of standard input price.**
- **Break-even** for the 5-min cache: 3+ reads within 5 minutes of the write. For the 1-hour cache: 5+ reads within an hour.
- **Minimum block size**: 2,048 tokens for Sonnet 4.6 · 4,096 tokens for Opus 4.7. Smaller than that → no cache created (silent fail; check the response headers).

### The 30-minute recipe (do this tonight)
1. **Pick your highest-volume project.** Open the file that builds the prompt sent to Claude.
2. **Find the longest *stable* prefix** — system prompt, tool spec, RAG-retrieved context that doesn't change between calls within a conversation. This is your cache target. Goal: ≥2,048 tokens for Sonnet, ≥4,096 for Opus.
3. **Add `cache_control: {"type": "ephemeral"}`** to that block:
   ```python
   messages = [{
     "role": "system",
     "content": [{
       "type": "text",
       "text": LONG_STABLE_SYSTEM_PROMPT,
       "cache_control": {"type": "ephemeral"}  # 5-min default; add ttl="1h" for 1-hour cache
     }]
   }]
   ```
4. **Run one call.** Check the response — the `usage` block should now report `cache_creation_input_tokens` (~ size of the cached block).
5. **Run a second call within 5 minutes.** The `usage` should report `cache_read_input_tokens` (same size, billed at 10%).
6. **Verify in your Anthropic billing dashboard** within 24 hours that the cache-read line is appearing.

### Stacking with two more optimizations (the compounding move)
- **Model routing (Haiku 4.5 for classification / Sonnet 4.6 for complex / Opus 4.7 only when needed).** Haiku is **$0.25/M input** vs Sonnet $3/M vs Opus $15/M. For any pipeline with multiple steps, route the *first* step to Haiku and only call Sonnet/Opus when the answer is genuinely complex. Typical impact: 4–10× cost reduction on routing-eligible workloads.
- **Batch API (50% off everything, non-realtime).** Anything you can wait 24h for — overnight evals, bulk content gen, historical-data backfills — goes through the Batch API at 50% off all token classes.
- **Combined:** Caching (10% of input) + Model routing (Haiku for 70% of calls) + Batch API (50% off the remainder) → typical workload runs **80–90% cheaper than naive Opus calls.** Numbers verified across multiple Sunday tutorials.

### Common gotchas
- **TTL default dropped from 1 hour to 5 minutes in early 2026** (Anthropic quietly changed it). If you wrote your code in 2025, your cache is silently invalidating every 5 minutes. Re-test.
- **Adding `cache_control` to a short prompt creates no cache** but charges you nothing extra. Silent fail; no error. Check the response header.
- **Cache is per-API-key**, not per-account. If you have multiple workers, share the key (or accept duplicate writes).
- **Cache writes count against your daily ratelimit** at *full* input rate; reads do not. Heavy initial-write loads (eg morning startup) can blow ratelimit before the savings kick in.

**Sources:**
- [Anthropic — Prompt caching (API docs)](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) `[primary]`
- [Anthropic — Pricing (API docs)](https://platform.claude.com/docs/en/about-claude/pricing) `[primary]`
- [Anthropic — Manage costs effectively (Claude Code docs)](https://code.claude.com/docs/en/costs) `[primary]`
- [TokenMix — Claude API Cache Pricing 2026: 90% Input Savings Explained](https://tokenmix.ai/blog/claude-api-cache-pricing) `[analysis]`
- [AI Magicx — Prompt Caching for Claude: Cut Your API Bill 60% in Production](https://www.aimagicx.com/blog/prompt-caching-claude-api-cost-optimization-2026) `[analysis]`
- [SitePoint — Claude API Cost Optimization: Reduce Costs 60%](https://www.sitepoint.com/claude-api-token-optimization/) `[analysis]`
- [DEV.to / Whoffagents — Claude API Cost Optimization: Caching, Batching, and 60% Token Reduction in Production](https://dev.to/whoffagents/claude-api-cost-optimization-caching-batching-and-60-token-reduction-in-production-3n49) `[analysis]`
- [Jangwook — Claude Prompt Caching: Cut LLM API Costs 70% With 4 Patterns](https://jangwook.net/en/blog/en/claude-api-prompt-caching-cost-optimization-guide/) `[analysis]`
- [PE Collective — Claude API Pricing 2026 Reference](https://pecollective.com/tools/anthropic-api-pricing/) `[reference]`

→ **Pair with:** [yesterday's billing-audit recipe](../2026-05-16/03-practical-skills-and-tools.md#1-billing-audit). The audit told you *where* you're bleeding; caching is *how* you stop the bleed.

---

## 2. Drop `CLAUDE.md` Into Every Project Tonight — Karpathy's 4 Principles {#2-claude-md}

**Why now:** Karpathy's `CLAUDE.md` skills file (~65 lines) is at **~109K GitHub stars** and has been **#1 on Weekly Trending for 28 consecutive weeks** as of May 17. It is the single highest-ROI piece of agentic-coding hygiene that exists, and you can install it in 5 minutes per project.

### What it does
Claude Code (and the Agent SDK) reads any `CLAUDE.md` in the project root *and* the user-home root before every session, treating it as system-prompt-grade behavioral guidance. The file encodes Karpathy's four principles, derived from weeks of intensive Claude Code usage where he tracked the agent's recurring failure modes.

### The four principles
1. **Think Before Coding** — verify assumptions before writing code; ask for missing context rather than guessing.
2. **Simplicity First** — three similar lines is better than a premature abstraction; don't add layers / factories / helpers without an explicit reason.
3. **Surgical Changes** — change only what the task requires; no "while I was here" cleanups; no opportunistic refactors.
4. **Goal-Driven Execution** — every change must have a verifiable success criterion (passing test, type-check, behavior match) before claiming done.

### The four failure patterns it addresses
- Silent assumptions never verified ("I'll assume the API returns a list" — and it doesn't)
- Hypertrophy of code and abstractions (one-off becomes a class hierarchy)
- Collateral changes to code that was never requested ("while I was in this file, I also fixed…")
- Absence of verifiable success criteria ("done!" without running anything)

### The 5-minute install
```bash
# In every active project root
curl -L https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md > CLAUDE.md
# Then open it and customize 3 lines for your stack:
#   - Replace "Python" / "TypeScript" with your primary language
#   - Add your test command (e.g., `pytest -xvs` or `npm test`)
#   - Add your lint/typecheck command (e.g., `ruff check` or `tsc --noEmit`)
git add CLAUDE.md && git commit -m "Add CLAUDE.md (Karpathy template)"
```

For non-Claude users: **the same file works as a system prompt for Cursor, Cline, Aider, and Sweep** (rename to `.cursorrules` or paste into custom instructions).

### Adoption signal
- ~109K stars on `forrestchang/andrej-karpathy-skills` (single-file repo)
- 28 weeks #1 on GitHub Weekly Trending — longest run of any 2026 repo
- Karpathy himself reported shifting from "80% manual + 20% agent" coding in Nov 2025 to "80% agent + 20% touchups" by Jan 2026 using this file

**Sources:**
- [forrestchang/andrej-karpathy-skills (GitHub, ~109K stars)](https://github.com/forrestchang/andrej-karpathy-skills) `[primary]`
- [Agentpedia — Karpathy's CLAUDE.md Skills File: The Complete Guide](https://agentpedia.codes/blog/karpathy-claude-code-skills-guide) `[analysis]`
- [AIToolly — Andrej Karpathy Inspired Guidelines for Claude Code](https://aitoolly.com/ai-news/article/2026-04-16-andrej-karpathy-inspired-guidelines-for-claude-code-optimizing-llm-performance-via-claudemd) `[analysis]`
- [Miraflow — The 65-Line File With 100K GitHub Stars That Changed How Developers Use AI Coding Agents in 2026](https://miraflow.ai/blog/karpathy-claude-md-100k-github-stars-ai-coding-2026) `[analysis]`
- [Pasquale Pillitteri — The #1 GitHub Trending File That Fixes LLMs Worst Coding Habits](https://pasqualepillitteri.it/en/news/1872/karpathy-claude-md-trending-github-llm-coding) `[analysis]`
- [AlphaSignal — Karpathy-Inspired CLAUDE.md: How to Add It to Any Project in 30 Seconds](https://alphasignalai.substack.com/p/karpathy-inspired-claudemd-how-to) `[analysis]`
- [Knightli — Karpathy's 65-Line CLAUDE.md: Helping AI Coding Avoid Three Common Mistakes](https://www.knightli.com/en/2026/04/19/karpathy-claude-md-ai-coding-rules/) `[analysis]`
- [Andrej Karpathy — Original CLAUDE.md X thread (Jan 26, 2026)](https://x.com/karpathy) `[primary]`

---

## 3. Ship an MCP Server in a Weekend — The 2026 Stack {#3-mcp-weekend}

**Why now:** MCP servers are the **portable skill artifact** of 2026 — the same MCP server runs across Claude Desktop, Claude Code, Cursor, VS Code Copilot, Cline, and most IDE-side AI agents. **As of early 2026 there are >8,600 community-built MCP servers.** Building one is the highest-signal proof of agent-fluency you can put on a resume (per yesterday's [`05` career section](../2026-05-16/05-career-and-startup.md)).

### The minimum-viable MCP server (90 minutes)
- **Python (FastMCP):** `pip install mcp==1.27.0` → `from mcp.server.fastmcp import FastMCP` → 30 lines for a working tool. The official `mcp` SDK ships with FastMCP. Tutorial: [tech-insider.org 12-step Python guide](https://tech-insider.org/mcp-server-tutorial-python-fastmcp-claude-2026/).
- **TypeScript:** `npm i @modelcontextprotocol/sdk` → 5 imports, one server, one tool registration, you're live. Tutorial: [DEV.to TypeScript 2026 tutorial](https://dev.to/jangwook_kim_e31e7291ad98/build-an-mcp-server-with-typescript-2026-tutorial-1ipk).

### The four production patterns (per BuildToLaunch's 5-patterns piece — the canonical reference)
1. **Read-only API wrapper** (the safest first server) — wraps an API you use daily (e.g., GitHub, Notion, your todo app). 1 tool, 2 hours.
2. **Auth-protected DB query tool** — wraps a Postgres/Supabase read-only with row-level security. 2 tools, 4 hours.
3. **Workflow orchestrator** — chains 3–5 API calls into a single tool (e.g., "create issue, link branch, notify Slack"). 4 tools, weekend.
4. **Stateful agent tool** — server holds session memory across calls (warning: stdio transport doesn't persist; use HTTP transport for state). Weekend+.

### Pick the right transport
- **stdio** (default) — Claude opens the server like a local app. Best for personal-machine tools. No network exposure.
- **HTTP** — server runs as a network service. Best for: multi-user, server-side, cross-device, or anywhere state needs to persist. **Use this if you want the server to be a hire-able portfolio piece** that someone can `pip install`-and-run remotely.

### What to actually build (this weekend, for portfolio leverage)
Pick one tool you personally use every day that has a public API and **does not yet** have a published MCP server. Recommended targets as of May 2026 (verified gap on [the awesome-mcp-servers list](https://github.com/modelcontextprotocol/servers)):
- **Garmin Connect** (running/health data → agent that summarizes the week)
- **Bear / Notion-Calendar / Granola** (notes/calendar tools without official MCP yet)
- **A vertical CRM** (Pipedrive, Close.com) — pairs perfectly with the Avoca-style vertical-agent thesis in [`02`](./02-new-emerging.md#2-avoca)
- **A regional bank or credit-union API** (Plaid-adjacent but specifically *non-US* — see the [`01-big-lab-moves OpenAI Codex Mobile`](./01-big-lab-moves.md#3-codex-mobile) and [yesterday's ChatGPT Personal Finance](../2026-05-16/01-big-lab-moves.md#3-chatgpt-finance) sections for why non-US fintech-MCP is a wedge)

### Ship target
- **Publish to GitHub by Sunday night.**
- **README has:** 30-second video demo · `pip install` / `npm install` one-liner · 3 example prompts that exercise the tool · 5-case eval-table (input → expected behavior → pass/fail).
- **Pin above your other repos.** Tweet it Monday morning with a single short demo gif. Tag `@AnthropicAI`, `@simonw`, `@karpathy`.

**Sources:**
- [Model Context Protocol — Build an MCP server (official)](https://modelcontextprotocol.io/docs/develop/build-server) `[primary]`
- [VS Code — Add and manage MCP servers](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) `[primary]`
- [Tech Insider — MCP Server Tutorial: 12 Steps Python FastMCP (2026)](https://tech-insider.org/mcp-server-tutorial-python-fastmcp-claude-2026/) `[analysis]`
- [DEV.to / Jangwook — Build an MCP Server with TypeScript: 2026 Tutorial](https://dev.to/jangwook_kim_e31e7291ad98/build-an-mcp-server-with-typescript-2026-tutorial-1ipk) `[analysis]`
- [DEV.to / Chuck M — Building a Javascript "Hello,World" MCP server in 2026](https://dev.to/chuckm/building-a-javascript-helloworld-mcp-server-in-2026-2lbc) `[analysis]`
- [BuildToLaunch — How to Build an MCP Server in 2026: 5 Patterns I Actually Shipped](https://buildtolaunch.substack.com/p/how-to-build-mcp-server-complete-guide) `[analysis]`
- [Arif Dewi (Medium) — Building Your First Production-Ready MCP Server: A Weekend Project That Actually Shipped](https://medium.com/@arifdewi/building-your-first-production-ready-mcp-server-a-weekend-project-that-actually-shipped-131305c69d54) `[analysis]`
- [DevTk.AI — Build Your First MCP Server: Step-by-Step TypeScript Tutorial (2026)](https://devtk.ai/en/blog/build-mcp-server-tutorial-2026/) `[analysis]`
- [Innovatrix Infotech — How to Build an MCP Server: Step-by-Step Guide 2026](https://www.innovatrixinfotech.com/blog/how-to-build-mcp-server) `[analysis]`

→ Cross-link: the [2026-05-16 weekend-project plan](../2026-05-16/03-practical-skills-and-tools.md) committed you to one MCP server by Sunday night. **This is that night.**

---

## 4. Google I/O Tuesday — Viewing Playbook {#4-io-viewing-playbook}

**Why now:** I/O 2026 keynote is **Tuesday May 19, 10 AM PT / 1 PM ET.** You should watch it live. But "watching" is not the same as "extracting value." This is the structured note-template that turns 3 hours of keynote into a Monday-morning interview-grade brief.

### Pre-keynote checklist (Monday night)
- [ ] Re-read [today's `01` I/O preview](./01-big-lab-moves.md#1-io-tminus-2) so the leak map is fresh
- [ ] Open the [Android Authority preview](https://www.androidauthority.com/what-to-expect-from-google-io-2026-3664979/) in tab 1, [Android Central preview](https://www.androidcentral.com/phones/google-pixel/google-io-2026-what-to-expect) in tab 2 (these are the consensus-leak baselines)
- [ ] Open [the Gemini Omni leak post](https://wavespeed.ai/blog/posts/google-omni-video-model-leak-i-o-2026/) in tab 3 — this is the only one with screenshot evidence
- [ ] Set up a markdown note-taking buffer with the section headers below
- [ ] Clear your calendar 10 AM–1:30 PM PT

### Live note-taking template (use during keynote)
```
## Keynote Notes — Google I/O 2026 — 2026-05-19

### Section 1: What did Sundar lead with?
- Opener: ______________
  - Read: enterprise-first / consumer-first / developer-first?

### Section 2: Gemini 4 (or 3.5)
- Name shipped: ______________
- Modalities: text / image / video / audio / code / 3D
- Context window: ______________
- Pricing vs Claude Opus 4.7 / GPT-5.5: ______________
- New benchmarks announced: ______________
- Available today / preview / waitlist: ______________

### Section 3: "Omni" (or whatever it's branded)
- Confirmed name: ______________
- Video / image / audio unified? ______________
- Max clip length: ______________
- NL editing demos shown: list the 3 most impressive
- Pricing: ______________
- Compared to Sora 2 / Veo 3.1 / Runway / Pika: ______________

### Section 4: Aluminium OS
- Shipped as preview / GA / dev preview / nothing
- First-party apps shown:
- OEM ship dates:
- Developer SDK link:

### Section 5: Android XR Gen 2
- Hardware partners confirmed: Samsung / Gentle Monster / others
- Price points:
- Developer SDK link:

### Section 6: Vertex Agent SDK
- Did it ship? Y/N — if Y, link to the SDK page
- Comparison with Anthropic Agent SDK / OpenAI Assistants:
- Pricing:
- Featured agents:

### Section 7: Anything totally unexpected?
- ______________

### Section 8: Hiring signals
- "We're hiring X engineers for Y" mentions:
- Job-page links shown on screen:
```

### Post-keynote action plan (Tuesday afternoon)
- [ ] **Within 4 hours of keynote end** — write your **1-page Gemini 4 vs Claude Opus 4.7 vs GPT-5.5 comparison**. Pricing per million tokens, context window, multimodal support, agent SDK availability, current benchmark scores. **Pin to your LinkedIn and X by 5 PM PT.** This is the [`ME.md` artifact](../ME.md) you committed to last week.
- [ ] **Within 24 hours** — pick ONE new Google API/SDK announced and build a 30-line demo against it. Push to GitHub. Tweet it tagged `@sundarpichai`, `@Google`, `@GoogleDeepMind`. (Historical: every I/O 2024 and 2025 produced 3 individual demos that became their authors' next employer.)
- [ ] **Within 48 hours** — apply to one Google Cloud FDE role using your `CLAUDE.md` repo + your Tuesday I/O demo as proof points. (Filter: [Google Cloud FDE listings](https://careers.google.com/jobs/results/120977245454901958-forward-deployed-engineer/)).

**Sources:**
- [Android Authority — What to Expect from Google I/O 2026](https://www.androidauthority.com/what-to-expect-from-google-io-2026-3664979/) `[secondary]`
- [Android Central — Google I/O 2026 confirmed for May 19](https://www.androidcentral.com/phones/google-pixel/google-io-2026-what-to-expect) `[secondary]`
- [WaveSpeed — Google's Mysterious 'Omni' Video Model: What the Gemini UI Leak Tells Us Ahead of I/O 2026](https://wavespeed.ai/blog/posts/google-omni-video-model-leak-i-o-2026/) `[analysis]`
- [Nokia Power User — Google I/O 2026 Starts May 19: Gemini Spark, Omni Video AI, Veo Upgrades & Smarter AI Agents Expected](https://nokiapoweruser.com/google-io-2026-gemini-spark-omni-gemini-3-5-rumors/) `[analysis]`
- [Simon Willison — Code w/ Claude live blog (May 6 — relevant for pre-I/O context)](https://simonwillison.net/2026/May/6/code-w-claude-2026/) `[primary]` (referenced as a *live-blog template* you can mimic for your I/O note-taking)

---

## 5. Sunday Action — Three 30-Minute Tasks Before Bed {#5-sunday-action}

In priority order. Stop after whichever your time runs out at.

1. **Drop `CLAUDE.md` into all active projects (15 min × N projects).** Copy [Karpathy's template](https://github.com/forrestchang/andrej-karpathy-skills), customize 3 lines for your stack. `git add CLAUDE.md && git commit`. → §2 above.
2. **Enable prompt caching on your hottest project (30 min).** Add `cache_control: {"type": "ephemeral"}` to the longest stable prefix. Run one call to verify `cache_creation_input_tokens` shows in the response. → §1 above.
3. **Apply to one Google Cloud FDE role and one Anthropic FDE role (30 min).** Use your existing MCP server + `CLAUDE.md` install + (if you did yesterday's task) the billing-audit write-up as the three artifacts in your cover note. → §4 above + [`05`](./05-career-and-startup.md#1-fde-800-percent).

**You'll wake up Monday with three commits, two cached agent pipelines, and two FDE applications in-flight.** The compound on each compounds across 2026.

---
