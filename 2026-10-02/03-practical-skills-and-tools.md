# Practical Skills & Tools — 2026-10-02

Three deliverables you can ship this weekend: (1) **Router v2** that adds Gemini 4 Argon + GPT-6.1 Sol to the routing table and re-runs the 5-case eval; (2) a **Claude Code migration** to deferred tool loading + the 4-primitive decision tree; (3) a **DolphinBench-style memory lane** added to your router's eval suite. All three raise your portfolio ceiling at the exact job-market moment where the market is paying for them.

Tags: `#routing #evals #claude-code #mcp #skills #hooks #subagents #pricing`

---

## 1. Router v2 — add Gemini 4 Argon + GPT-6.1 Sol, re-fit routing weights {#1-router-v2}

**What to ship:** Update the 30-line router artifact from [2026-09-10/03 §3](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact) with this week's model-pricing + benchmark data.

### Updated routing table (Oct 2026)

| Workload | Default model | Fallback | Rationale |
|---|---|---|---|
| **Coding (interactive)** | **Gemini 4 Argon** | Claude Fable 5.1 | Argon #1 on Vals coding slices + $2/$10 promo. Fallback: Fable 5.1 if cache hit-rate >60% (cache reads $0.25/1M). |
| **Long-context Q&A (>200K tokens)** | **Gemini 4 Argon** | Claude Fable 5.1 | 1M-token context + Argon's long-context benchmark lead per Google's own numbers. |
| **Cheap batch summarization** | **GPT-6.1 Sol (standard)** | Gemini 3.8 Flash | Sol is ~1/5 Astra's token price; Flash is the second-cheapest frontier-adjacent at this altitude. |
| **Agentic tool-use (short runs)** | **Claude Fable 5.1** | Gemini 4 Argon | Fable retains the lead on terminal + tool-use benchmarks; Argon as fallback if a cost ceiling binds. |
| **Agentic tool-use (long runs, hours+)** | **Claude Fable 5.1** on Sail Research inference infra | Claude Fable 5.1 on API | Long-horizon-agent infra is a Q4 2026 wedge ([`02` §2](./02-new-emerging.md#2-funding)) — vLLM/SGLang bleed on multi-hour workloads. |
| **Computer-use / Codex-style** | **GPT-6.1 Sol via Agents API (computer-use)** | — | OpenAI DevDay shipped native computer-use in the API; competing offerings aren't comparable in Q4 2026. |
| **Science / research-agent** | **Claude Fable 5.1 (Terminal-Bench-Science 52.6%)** | Gemini 4 Argon | Keep Fable until Argon publishes TB-Science; re-check on each new benchmark release. |

### Updated price-per-1M-token snapshot

| Model | Input | Output | Cache (read) | Note |
|---|---|---|---|---|
| Gemini 4 Argon | **$2.00** (promo) → $4.00 | **$10.00** (promo) → $20.00 | ~$1.90 (5% discount) | Promo-period only; re-check expiry date. |
| Claude Fable 5.1 | $5 | $25 | **$0.25** | 75% cache-read cut from 2026-09-10. |
| Claude Opus 5.5 | $15 | $75 | $3.75 | Premium Anthropic. |
| GPT-6.1 Sol (standard) | ~$3 (1/5 Astra) | ~$12 | — | DevDay Sept 29. |
| GPT-6 Astra | $15 | $60 | — | Reference baseline. |

(Numbers derived from referenced sources below; always confirm with the vendor pricing page before invoicing.)

### The 5-case eval you re-run against this table

1. **CODE-1**: Debug a 300-LOC Python agent-loop with a subtle `asyncio.gather` deadlock. Grade on correctness + explanation quality.
2. **LONG-1**: Summarize a 400K-token legal filing into a 1-page memo with 5 citation footnotes. Grade on faithfulness + citation accuracy.
3. **BATCH-1**: Classify 1000 support tickets into 7 categories. Grade on macro-F1 vs human-labeled gold.
4. **TOOL-1**: Agentic tool-use loop with 4 MCP servers (GitHub + Linear + Slack + Postgres). Grade on 15-step task completion rate.
5. **COST-1**: Across all 4 above, compute total cost + p95 latency per model. Grade on cost-per-correct-answer.

**Ship criteria:** v2 pushed to GitHub with (a) `routing_table.yaml` (b) `eval/` with the 5 cases (c) `README.md` with a scoreboard table (d) `COST.md` with per-model per-case $ figures. 90 min of work tonight.

**Sources:**
- [Vals.ai — Gemini 4 Argon Benchmarks, Cost and Capabilities](https://www.vals.ai/models/google_gemini-4-argon) `[primary benchmark]`
- [NeuralTrust — Gemini 4 Argon: Benchmarks, Pricing & Security](https://neuraltrust.ai/blog/gemini-4-argon) `[analysis]`
- [InfoQ — OpenAI DevDay 2026 Recap for Developers](https://www.infoq.com/news/2026/10/openai-devday-2026/) `[secondary]`
- [benchlm.ai — Frontier AI Models: Live Top 10 Rankings (October 2026)](https://benchlm.ai/frontier-ai-models) `[aggregator]`
- [Anthropic — Claude Fable 5.1 pricing](https://www.anthropic.com/pricing) `[primary]`

### Why it matters to you

- **Job lens:** This single artifact answers 3 of the top-5 FDE/AI-Engineer interview questions in one PR: (a) which model for which workload? (b) prove it. (c) what did it cost? Ship it tonight → tweet it tomorrow → add it to the top of your resume Monday. Replace the single hardest line on your resume ("Experienced with LLM APIs") with a GitHub-starred artifact.
- **Startup lens:** The eval + scoreboard is also the exact MVP for a **"model-router as a service"** product. If the artifact gets any traction (>50 stars in 30 days), that's your signal to iterate it into a hosted dashboard with per-customer workload fingerprinting. Alternatively, sell the eval suite itself as a consulting SKU to AI-adopting enterprises.
- **Insight:** The reason router v2 is high-leverage *this specific week* is that Argon landed 48 hours ago + Dots/Sol landed 72 hours ago + the pacing truce suggests the pace will slow slightly, which means **the current routing table has a 2–4 week useful lifetime** instead of the <7 days we saw in September. That's long enough for a published artifact to accumulate signal before it's stale. **Ship within the lifetime of the data.**

---

## 2. Claude Code 2026 maturity — deferred tool loading + streamable HTTP + OAuth 2.1 (migration tonight) {#2-claude-code-mcp-mature}

**What shipped:** Claude Code has matured three MCP features that materially change how you build with it in Q4 2026.

### A. Deferred Tool Loading

- Claude Code now **loads only tool names at startup** and fetches full JSONSchema on demand via `ToolSearch`.
- Cuts context overhead by **~1 order of magnitude** when running 50+ MCP tools.
- Zero-config for Anthropic-published servers; one-flag opt-in for custom servers.

### B. MCP streamable HTTP transport + OAuth 2.1 with PKCE

- You can now point Claude Code at a **remote MCP server** over HTTP streaming — no local stdio process required.
- **OAuth 2.1 with PKCE** means auth flows that worked in web apps work for MCP servers too.
- Direct consequence: **"Claude Code → my hosted MCP server"** is now a 3-line config, not a weekend of plumbing.

### C. The matured 4-primitive decision tree (one more time, authoritatively)

| Problem | Right primitive |
|---|---|
| **"This rule must be enforced, always"** → block an unsafe command, enforce a format | **Hooks** (pre-tool-use / post-tool-use) |
| **"This workflow is long and context-heavy"** → docs refresh, deployment checklist, one-off migration | **Skills** |
| **"This task should run in isolation from the main thread"** → extended research, parallel builds | **Subagents** |
| **"This project always needs this context"** → repo conventions, team style guide, don't-commit rules | **CLAUDE.md** |

### Weekend migration checklist (90 min)

- [ ] Audit `.mcp.json`: identify any server with >5 tools; those will benefit most from deferred loading.
- [ ] Upgrade Claude Code to the latest release (`claude --version` ≥ Oct 2026 build).
- [ ] For every MCP server you host remotely, enable streamable HTTP + OAuth 2.1 (sample config in the MCP docs).
- [ ] Walk your `CLAUDE.md` + Skills + Hooks + Subagents against the 4-primitive table. **Rule of thumb:** anything you've put in two primitives is one too many; pick the right one and delete the other.
- [ ] Install the official Anthropic skills: **skill-creator, frontend-design, webapp-testing, mcp-builder, Superpowers, gstack** (the H1 2026 shortlist that's held up through Q3).
- [ ] Security hygiene: **pin every MCP server by npm version + container digest.** A server description change on an untrusted upstream is a known attack vector in Q4 2026.

**Sources:**
- [alexop.dev — Claude Code Explained (2026): MCP, Skills, Subagents, Hooks & Plugins](https://alexop.dev/posts/understanding-claude-code-full-stack/) `[analysis]`
- [okhlopkov.com — My Claude Code Setup After 4 Months of Daily Use (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) `[analysis]`
- [codersera — Claude Skills and MCP Servers in 2026: A Practitioner's Guide](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/) `[analysis]`
- [Totalum — Claude Code Skills in 2026: The Complete Guide](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [Taskade — Best Claude Code Skills in 2026 (Tested + How to Build)](https://www.taskade.com/blog/claude-code-skills) `[aggregator]`
- [MorphLLM — Claude Code Skills vs MCP vs Plugins: Complete Guide 2026](https://www.morphllm.com/claude-code-skills-mcp-plugins) `[analysis]`
- [Buildthisnow — The Best Claude Code Skills in 2026](https://www.buildthisnow.com/blog/guide/mechanics/best-claude-code-skills-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Interviewers now ask the 4-primitive question verbatim. Being able to say *"I run 60 MCP tools in Claude Code with deferred loading because otherwise my context budget bleeds, and I enforce the format check with a post-tool-use hook because that's a rule, not a workflow"* **wins the AI-Engineer / FDE interview on this exact topic**. 90 minutes of migration = a repeated-use interview edge for the next 6 months.
- **Startup lens:** OAuth 2.1 + streamable HTTP means **"MCP server with a SaaS subscription"** is now a shippable business model. Previously, hosting your own server required customers to run the stdio bridge; now they can call a hosted endpoint over OAuth. Expect the first **"MCP SaaS marketplace"** to launch in Q1 2027; being an early seller in that marketplace is a wedge worth planning for.
- **Insight:** Deferred tool loading is actually the mechanism that lets Dots, Managed Agents, and Antigravity agents each sanely run **50+ MCP tools in a single agent lifecycle** without blowing the context budget. The three persistent-agent primitives would not be viable products at scale without it. Watch for the equivalent "deferred" idea applied to Skills next (lazy-loaded skill libraries).

---

## 3. Weekend micro-project — add a "memory lane" to router eval (uses DolphinBench) {#3-memory-lane}

**What to ship:** A 6th case in the router eval that specifically grades **multi-session interdependent memory**, borrowing a 2-persona subset from DolphinBench (see [`04` §1](./04-research-progress.md#1-memory-wave)).

### The case

- **MEM-1**: Simulate a 10-session user interaction over a week. Across sessions, user reveals (a) their name is Jamie, (b) they're allergic to peanuts, (c) they have a cat named Whisker, (d) they're writing a novel about a desert planet. In session 11, ask the agent to recommend a dinner recipe + a name for the novel's protagonist that honors the cat. **Grade on**: name recall, allergy avoidance, cat-honoring protagonist name (= 3-recall-dimensions-at-once).

Run this against: **Dots (OpenAI persistent memory)**, **Claude with Anthropic memory tool**, **Gemini 4 Argon with system-prompt-stuffed history**, **a raw stateless Fable 5.1 for baseline**.

**Expected result (per DolphinBench's own findings):** interdependent recall drops to **40–60%** on even near-saturated LoCoMo models. If any configuration exceeds 80%, that's your startup wedge (reproduce it, write it up, ship a demo).

### Why this specific case?

Because **this is the gap** between "the agent demos well" and "the agent stays useful after a week." Every enterprise AI deployment of 2026 has run into it; no one has shipped a definitive answer. The person who credibly demonstrates **"my architecture gets to 85% on MEM-1"** is a $400K+ TC hire in Q4 2026.

**Sources:** see [`04` §1](./04-research-progress.md#1-memory-wave) for the DolphinBench paper + related memory benchmarks (MemoryArena, EverMemBench, HaluMem, AMA-Bench, RealMem, StreamMemBench).

### Why it matters to you

- **Job lens:** This is the **single highest-leverage weekend project in Q4 2026**. It directly answers two interview questions ("how do you build long-horizon agents?" and "how do you evaluate them?") with one artifact.
- **Startup lens:** If you ship it as a public eval + leaderboard, you *are* the de-facto benchmark for persistent-agent memory until a bigger team (Scale, LMSYS, Vals) overbuilds you. 6 months of indie leaderboard = inbound to be acquired or Series A'd.
- **Insight:** Memory benchmarking is the eval frontier because it's **compositional** (depends on retrieval + reasoning + grounding) and **adversarial** (small changes in the prompt break the chain). It's the hardest-to-game eval of 2026 — which is exactly why it's the most-valuable one to author.
