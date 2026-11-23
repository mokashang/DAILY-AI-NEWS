# 03 — Practical Skills & Tools · 2026-10-11

Act on this today. The three things with the highest ROI-per-hour this week: **the Haiku-5.5 orchestrator math**, **the Intelligent-UI wedge**, and **a 20-minute CLAUDE.md audit against the Oct 7 pricing changes**.

---

## 1. The Haiku-5.5 "orchestrator + swarm" cost math — rebuild your router this week {#1-haiku-swarm}

**The setup.** With Haiku 5.5 at **$0.10 / $0.50** per 1M tokens (short prompts) and Sonnet 5.5 cache reads **cut in half**, the pre-Oct-7 Claude-Code cost assumptions in your project are now wrong. A representative task that cost **$0.08 on Sonnet-only** likely costs **~$0.025** on Sonnet-planner + Haiku-5.5-workers before caching, and roughly **$0.015** with cache reads on the plan prompt.

### The architecture (minimum viable version)

```
                            ┌────────────────────────────┐
                            │ Sonnet 5.5 (planner)       │
   user prompt ───────────► │ · reads CLAUDE.md          │ ──┐
                            │ · writes a 3–10 step plan  │   │
                            │ · emits N parallel tasks   │   │
                            └────────────────────────────┘   │ fan-out
                                                             │
                            ┌────────────────────┐           │
                            │ Haiku 5.5 worker 1 │ ◄─────────┤
                            │  effort="low"      │           │
                            └────────────────────┘           │
                            ┌────────────────────┐           │
                            │ Haiku 5.5 worker 2 │ ◄─────────┤
                            └────────────────────┘           │
                                     ...                     │
                            ┌────────────────────┐           │
                            │ Haiku 5.5 worker N │ ◄─────────┘
                            └────────────────────┘
                                     │
                                     ▼  per-worker results
                            ┌────────────────────┐
                            │ Sonnet 5.5 merge   │  → final answer + cost + wall-clock
                            └────────────────────┘
```

### Why Haiku-5.5 specifically (not Haiku 4.5, not Sonnet-only)

1. **Effort levels (new on Haiku 5.5)** — you can run most workers at `effort="low"` and only escalate the ones whose first draft fails a cheap verifier. Haiku 4.5 didn't let you do this.
2. **1M-token context** — large documents / codebases can fan out to Haiku workers without a separate chunker.
3. **~75-90% cheaper than Haiku 4.5** — the orchestrator-worker split that was uneconomic in Aug 2026 is in-the-money today.
4. **Sonnet 5.5 cache-read price cut** — the planner's shared system prompt + CLAUDE.md are now ~free on repeat calls.

### What to ship this weekend (90-min build, 90-sec demo)

A **public repo** called `haiku-swarm` (or similar) containing:

- `orchestrator.py` — ~50 lines, Sonnet-5.5 planner + N parallel Haiku-5.5 workers via `anthropic` Python SDK with `asyncio.gather` for fan-out.
- `eval/` — a 5-case eval suite with expected outputs; prints wall-clock + per-task cost against:
  - Sonnet-5.5-only
  - Haiku-5.5-only
  - **Sonnet-5.5 planner + Haiku-5.5 swarm (the thesis)**
- `README.md` — the table of {cost, wall-clock, quality} for each strategy on your 5 cases.
- A 90-second **asciinema** or screen recording of the orchestrator running.

**Three migration gotchas** (do NOT skip):
- Remove assistant-prefill from any Haiku 4.5 calls — **returns errors on Haiku 5.5** (per VKTR coverage).
- Validate token-counts on short prompts — the tokenizer change inflates them for some workloads; measure real-world savings on *your* traffic, not the headline 75%.
- When passing results between Sonnet-planner and Haiku-workers, use **structured outputs** (JSON schema), not free-form text. Haiku-5.5 at `effort="low"` is cheap enough that parse errors become the dominant failure mode.

**Sources.**
- [Anthropic Haiku 5.5 launch via AIWeekly](https://aiweekly.co/alerts/introducing-claude-haiku-55) `[aggregator]`
- [VKTR — pricing + migration notes](https://www.vktr.com/ai-platforms/anthropic-cuts-smallmodel-pricing-90-with-claude-haiku-55/) `[analysis]`
- [LetsDataScience — effort controls + Sonnet cache cut](https://letsdatascience.com/news/anthropic-releases-claude-haiku-55-with-lower-prices-and-eff-f698c663) `[aggregator]`

**Why it matters to you.** The router + eval-suite was the "interview-differentiator of Q4 2026" called out in [`2026-09-10/03`](../2026-09-10/03-practical-skills-and-tools.md). Oct 7 added **a reason to rebuild it**: Haiku 5.5 changes the shape of the router tree. Rebuild it this weekend and you have **a fresh timestamp on the artifact** every recruiter screen will ask about.

`#claude-code #routing #cost #haiku #sonnet`

---

## 2. Intelligent UI = a 72-hour startup wedge via generative UI + MCP {#2-ui-wedge}

**The thesis.** OpenAI shipping **Intelligent UI** (Oct 7) legitimizes **"an answer is a tool / component, not a paragraph"** as a mainstream product interaction. For your startup lane: pick ONE vertical where **the ideal answer to a user question is literally a calculator / form / table / chart**, and ship an MCP-backed assistant that returns it.

### What generative UI actually looks like

```
User: "If I max out my Roth IRA this year and next, what's the balance in 2050?"
                      │
                      ▼
Assistant (Sonnet 5.5 + MCP tool: `retirement.compound`)
                      │
                      ▼
Tool returns NOT a sentence. It returns an interactive component:

  ┌────────────────────────────────────────────────────────┐
  │ Starting balance: [ $12,500      ]                     │
  │ Annual contribution: [ $7,000 ]                        │
  │ Years: [ 25 ]                                          │
  │ Expected return (%): [ 7.5 ]                           │
  │                                                        │
  │ Projected balance in 2050: $647,281                    │
  │ [chart.svg: growth curve 2026→2050]                    │
  │                                                        │
  │ ↻ recalculate   📧 email me   ⚙ scenarios              │
  └────────────────────────────────────────────────────────┘
```

**That's the wedge.** Pick one high-stakes question type where this beats a paragraph:
- **Fintech**: loan amortization, refi break-even, tax what-ifs.
- **Health**: dosage calculators, drug-interaction tables, insurance-plan comparers.
- **Education**: concept visualizers, practice problem generators (returned as a component, not text).
- **Operations**: SLA calculators, cost-model what-ifs, hiring-plan sliders.
- **Research**: "give me the comparison table of X vs Y" → returned as a sortable, filterable table component, not a markdown list.

### The build

1. Pick vertical. 48-hour cutoff on the decision.
2. Draft the top-10 user questions and classify each: "paragraph" vs "component". Target: 7+ in the "component" bucket.
3. Build 2-3 MCP tools that each return a **structured UI spec** (JSON) rather than text — e.g. `{type: "calculator", inputs: [...], output_formula: "..."}`.
4. Render the UI spec client-side in whatever your frontend is (React/Next.js + a thin `UISpecRenderer` component). The LLM does **tool choice + argument assembly**; the client does the rendering.
5. Record a 2-minute demo. Publish.

**Why this specifically.** It aligns the "AI Integration Engineer" portfolio focusing decision in [`ME.md`](../ME.md) with the fresh news hook. **Every recruiter screen in October will mention Intelligent UI.** Having a working prototype built against the primitive — not just a reaction post — is the differentiator.

**Sources.**
- [Digit — GPT-6 + Intelligent UI user features](https://www.digit.in/news/general/openai-rolls-out-gpt-6-for-all-users-introduces-intelligent-ui-for-more-interactive-chatgpt-responses.html) `[secondary]`
- [YourStory — GPT-6 arrives with Intelligent UI](https://yourstory.com/ai-story/gpt-6-intelligent-ui-chatgpt-answers) `[secondary]`
- Related primitive: [MCP spec](https://modelcontextprotocol.io) and the WebMCP origin trial covered in [`2026-05-20/01`](../2026-05-20/01-big-lab-moves.md)

`#startups #ui #mcp #skills #generative-ui`

---

## 3. The 20-minute CLAUDE.md audit against Oct 7 changes {#3-claude-md-audit}

**Context.** [`2026-09-10/03`](../2026-09-10/03-practical-skills-and-tools.md) locked in the 2026 Claude Code 4-primitive stack: **Hooks (enforcement) · Skills (contextual knowledge) · Subagents (delegation) · CLAUDE.md (always-on project guidance)**. Oct 7 didn't change the primitives — but it changed **what belongs in each**.

### What to add to your CLAUDE.md this Sunday

```markdown
## Model routing (updated 2026-10-11)

- **Default planner**: `claude-sonnet-5-5` with effort="medium"
- **Default worker (fan-out tasks)**: `claude-haiku-5-5` with effort="low"
- **Escalate to Sonnet** when: structured-output parse fails, verifier flags
  a hallucinated identifier, or wall-clock > N s per worker
- **Never use Opus for**: pure classification, retrieval re-ranking, format
  translation, structured extraction — Haiku 5.5 effort="low" wins on
  $/correct-answer

## Caching

- Keep system prompt + CLAUDE.md + stable context in cacheable prefix.
- Sonnet 5.5 cache reads cut 50% on 2026-10-07 — the ROI on prefix
  stability is now higher than it was in September.
```

### What to add to one of your Skills

Create (or update) a Skill called `ui-component` or similar, whose instructions say: **"when the user's question is answered better by a component than by text, call this skill; return a JSON spec, not prose."** This is the Skill-level reflection of the Intelligent UI primitive. Even if you don't ship it to prod, it structures your thinking next time you're asked.

### What to add to your Hooks

A **pre-tool-use hook** that logs model + token-count + estimated cost per request. (If you're already paying for Claude Pro / Max, this is still worth it to compare against the API bill.) Required reading if you expect the Haiku-5.5 pricing to actually move your bill: without a hook capturing real $-per-task, you'll never know whether the swarm architecture paid off.

**Sources.**
- 2026 Claude Code 4-primitive stack: [`2026-09-10/03`](../2026-09-10/03-practical-skills-and-tools.md)
- [Vonage — Beyond Vibe Coding, Best Practices 2026](https://developer.vonage.com/en/blog/beyond-vibe-coding-best-practices-2026) `[secondary]`
- [Zencoder — 6 Best Practices for Coding with AI Agent Platforms 2026](https://zencoder.ai/blog/best-practices-for-coding-with-ai-agent-platforms) `[secondary]`

`#claude-code #claude-md #skills #hooks #routing #cost`

---

## 4. Quick wins — things to do in 10 minutes {#4-quick-wins}

- **Update your Claude SDK** to the version that supports `claude-haiku-5-5`. Re-run your eval suite. If any assertions break, it's the prefill / sampling-param migration — fix in-place.
- **Add a `#haiku-5-5` tag** to your sources archive (`grep -r "#haiku-5-5" .` across this repo will become a career-ready search).
- **Draft one LinkedIn post** on the Haiku-5.5 cost math + your orchestrator architecture. 150 words max. The window on being "early" to the Oct 7 news is ~5 days.
- **Review your APPLICATIONS.md** — add 1-2 Armadin / Instinct / EliseAI roles (they have the fresh capital, they're hiring).
- **Open [`WATCHLIST.md`](../WATCHLIST.md) and update** the "Haiku 5.5 effort levels" thread with a datestamp.

`#weekly-checklist #applied`

---

## See also

- [`01-big-lab-moves.md`](./01-big-lab-moves.md) — the full Haiku 5.5 + GPT-6 + accord picture
- [`04-research-progress.md`](./04-research-progress.md) — the agentic-eval papers you can cite in interviews
- [`05-career-and-startup.md`](./05-career-and-startup.md) — hiring map + applications queue
- Prior editions: [`2026-09-10/03`](../2026-09-10/03-practical-skills-and-tools.md) (2026 Claude Code 4-primitive stack + router artifact) · [`2026-05-21/03`](../2026-05-21/03-practical-skills-and-tools.md) (orchestration stack)
