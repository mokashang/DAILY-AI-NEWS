# Practical Skills & Tools — 2026-10-19

The window's three practical takeaways: **(1) your router artifact needs a 4th tier (Gemini 4 Argon)**, **(2) start treating "effective context" as the real number (30–50% of advertised)**, and **(3) voice-agent prototyping just got $0.08/min cheap enough to warrant a weekend experiment.**

Tags: `#practical #routing #context #voice #pricing`

---

## 1. Ship router artifact V2 by Sunday Oct 25 — four tiers now, with Argon default vs high-reasoning A/B {#1-router-v2}

**What changed:** With **Gemini 4 Argon's introductory pricing at $2 in / $10 out through Nov 30**, the practical router comparison grew from 3 tiers to 4:

| Tier | Model | Price / 1M in | Price / 1M out | Context | Best for |
|---|---|---|---|---|---|
| Cheap worker | Claude Haiku 5.5 | $0.10 | $0.50 | 200K | Browser-use, subagent workers, high-volume classification |
| Large-context worker (A) | Gemini 4 Argon (intro, through Nov 30) | $2 | $10 | 1M | Long-doc synthesis, multi-file code analysis |
| Large-context worker (B) | GPT-6.1 Sol (standard) | $2 | $10 | 400K+ | Agentic coding, computer use |
| Latency-premium | GPT-6.1 Sol Ultrafast | $12 | $60 | 400K+ | User-visible first-token |
| Frontier | Claude Opus 5.5 | $15 | $75 | 1M | Hard reasoning, long-horizon agent plans |

**The Argon-specific A/B you need:**
- Argon **default** (what Pro/Ultra Gemini-app users actually get)
- Argon **high-reasoning mode** (what Google's benchmarks were run on)

The TechTimes finding (Oct 15) is that **Google's 13-of-19 benchmark lead was high-reasoning-mode**, not default. Your router needs to A/B both modes on the same tasks so you can route accurately and quote accurate cost/latency numbers.

### The 90-minute ship plan

**0–20 min: scaffold.** Clone your prior router. Add a `MODEL_TIER` enum with 5 entries (the 4 above + Argon-high-reasoning). Add a `.env` with 4 API keys (Anthropic, OpenAI, Google, and whichever OSS provider you use as fallback).

**20–40 min: wire Argon.** Use the Gemini API with model id `gemini-4-argon`. For high-reasoning mode, pass the reasoning-effort parameter at max; for default, omit it. Capture per-call: input tokens, output tokens, latency, dollar cost, and (critically) the output text itself for scoring.

**40–70 min: 10-task benchmark.** Pick 10 representative tasks:
- **3 code:** fix a Python typing bug, port a shell script to Python, read a 400-line file and summarize risks
- **3 agent-tool-use:** call 3 MCP tools in sequence, handle a tool error gracefully, read then write a file
- **3 doc-synthesis:** summarize a 10-page RFC, compare two 2000-word blog posts, extract a decision table from a transcript
- **1 long-context:** read a 300K-token codebase and answer 5 cross-file questions

**70–90 min: README + chart + LinkedIn post.** The chart is the deliverable: *cost per correct answer* across tiers, where "correct" is scored by the Opus-5.5 judge. If Argon default comes in >5pp behind Argon high-reasoning on code or long-context, that's the chart's punchline.

### The portfolio pitch

Post the chart to LinkedIn + X with: "**Shipped: 4-tier router with cost-per-correct-answer across Haiku 5.5 / Argon / GPT-6.1 Sol / Opus 5.5, including Argon default-vs-high-reasoning A/B. Repo link in comments.**" Tag `@AnthropicAI` / `@GoogleDeepMind` / `@OpenAI`. **Target an AI Integration Engineer at one of the FDE partner firms** (McKinsey / Deloitte / Accenture / Bain) in the comments: ask them one specific question about how they'd pick between tiers in their practice.

### Sources

- [Google Blog — Introducing Gemini 4 Argon](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-argon/) `[primary]`
- [SmartScope — Gemini 4 Argon access + introductory pricing](https://smartscope.blog/en/blog/gemini-4-argon-access-introductory-pricing-2026/) `[secondary]`
- [TechTimes — Benchmark scores reflect high mode, not subscriber default](https://www.techtimes.com/articles/329026/20261015/gemini-4-argon-rolls-out-benchmark-scores-reflect-high-mode-not-subscriber-default.htm) `[analysis]`
- [SessionWatcher — GPT-6.1 Sol pricing & Codex integration](https://sessionwatcher.com/news/codex-gpt-6-1-sol-ultrafast-pro-500-enterprise-edu) `[aggregator]`

→ Cross-link: [`01` §1 Argon rollout](./01-big-lab-moves.md#1-argon-rollout) · [`05` §3 apply plan refresh](./05-career-and-startup.md#3-apply-plan-refresh).

---

## 2. Monthly re-costing discipline — the pricing floor has moved twice in 17 days {#2-recost-discipline}

**What changed:** On **Oct 7** Haiku 5.5 cut the cheap-tier floor to $0.10/$0.50. On **Oct 13** Argon's introductory tier matched GPT-6.1 Sol standard at $2/$10 for the large-context worker slot. **That's two pricing floor moves in 17 days.** If GPT-6 Astra's standard tier re-prices by Nov 15, the whole frontier price curve has reset in one quarter.

**The discipline you need:**

- **A monthly re-cost of any production AI workflow you own.** For your personal MCP server portfolio artifact: at the start of each month, re-run the router benchmark and re-pick the per-tool-call defaults. A spreadsheet is enough; it does not need to be automated.
- **A written note of pricing-dependent architectural choices.** Three questions to answer in a short README: (1) what workflow steps would you move to Haiku 5.5 if its pricing stayed flat for 6 months? (2) what frontier-tier spend would you drop to the $2/$10 tier? (3) what would need to be true about Argon's quality for you to switch wholesale to it as the large-context default?
- **The specific signal you're watching for next month:** Opus 5.5 re-prices to ~$5/$25 OR holds at $15/$75 with a capability-depth defense. Set a Nov-13 calendar reminder to check Anthropic's pricing page.

### The interview talking point

Any interviewer at an FDE partner firm or frontier lab will ask you about cost management. The answer frame to practice:

> "I track two things: pricing floor moves and effective-tier drift. In October alone the cheap tier re-floored at $0.10/$0.50 with Haiku 5.5, and the large-context tier re-floored at $2/$10 with Gemini 4 Argon's intro pricing. That's two floor moves in 17 days, so I'm running a monthly re-cost on every production workflow and keeping decisions documented so I can defend them in a cost-review. The adjacent discipline is routing — not every call needs the frontier tier, but routing has to be data-backed, not vibes-based."

**That's the hiring-manager-grade answer.** Memorize it; the specifics will update monthly but the frame is stable.

### Sources

- [Oct 14 edition §3 Haiku 5.5](../2026-10-14/03-practical-skills-and-tools.md) `[internal]`
- [SmartScope — Gemini 4 Argon pricing](https://smartscope.blog/en/blog/gemini-4-argon-access-introductory-pricing-2026/) `[secondary]`
- [SessionWatcher — GPT-6.1 Sol pricing](https://sessionwatcher.com/news/codex-gpt-6-1-sol-ultrafast-pro-500-enterprise-edu) `[aggregator]`

→ Cross-link: [2026-10-14/03 §1 Haiku 5.5](../2026-10-14/03-practical-skills-and-tools.md#1-haiku-55) · [`01` §1 Argon rollout](./01-big-lab-moves.md#1-argon-rollout).

---

## 3. Weekend experiment: voice-agent prototype at $0.08/min using Grok Voice 3.0 {#3-voice-prototype}

**What changed:** Grok Voice 3.0 at **$0.08/min** with **86.9 S2S Index** and **sub-second latency** makes a weekend voice-agent prototype economically trivial. **This is the smallest-cost "new specialty lane" artifact you can add to your portfolio in Q4.**

### The 3-hour weekend build

**Hour 1: wire voice-in / voice-out.** Use xAI's Voice Agent API with a telephony front-end (Twilio Voice, Vapi, or Retell) or a browser WebRTC front-end. Minimum MVP: user speaks, Grok transcribes + responds + synthesizes, user hears.

**Hour 2: wire one real tool.** Add exactly one MCP tool the voice agent can call — a calendar lookup, a Google Drive search, or a database query. The point is to prove the voice agent can take an action in the world, not just chat. Keep latency under 2s round-trip.

**Hour 3: record a 2-minute demo + write a 400-word writeup.** The demo is the deliverable. The writeup covers:
- What you built (voice intake → MCP tool call → voice response)
- Cost math ($0.08/min × avg call length, broken out for the three cost components: STT, LLM, TTS)
- One honest tradeoff (likely: latency floor, or interruption handling, or STT accuracy on domain terms)

### Why this specific artifact

Three reasons:

1. **Voice is the under-crowded specialty lane this quarter** — Grok Voice 3.0 at $0.08/min is new; most CS grads have not built with it yet.
2. **MCP tool integration is already your committed specialty** (from `ME.md`); voice is a surface area that forces the tool integration to actually work (interactive, time-pressured, no re-rolls).
3. **The portfolio reads as "I ship across modalities"** — important when interviewing with Solutions / FDE / Integration teams, which rotate across text, voice, code and vision in a single engagement.

### Caveats

- The 0.81s latency vs V2's 0.70s is a regression; test on your actual network before shipping.
- The S2S Index number is from Artificial Analysis's pre-launch testing; wait for user reports before quoting it in interviews as a defended fact.
- Tesla / Starlink deployment claims come from a single Chinese-language source; **don't quote them until a US outlet corroborates.**

### Sources

- [LLM Gateway — Grok Voice 3.0 model page](https://llmgateway.io/models/grok-voice-3-0) `[aggregator]`
- [TechEnclave — xAI releases Grok Voice 3 and upgrades the latest API alias](https://techenclave.com/news/items/xai-releases-grok-voice-3-and-upgrades-the-latest-api-alias) `[secondary]`
- [BenchLM — Grok Voice 3.0 Benchmark Scores](https://benchlm.ai/md/models/grok-voice-3-0.md) `[analysis]`

→ Cross-link: [`02` §1 Grok Voice 3.0](./02-new-emerging.md#1-grok-voice-3) · [`ME.md` focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly).

---

## 4. Effective context discipline — stop quoting advertised context windows in interviews {#4-effective-context}

**What changed (research-backed, surfaced this week):** Multiple writeups now cite the RULER-style multi-needle finding that **effective context on long-context benchmarks is 30–50% of advertised maximum** for most frontier models. The 2026 October arXiv wave on context management (ContextPilot, FS-Researcher — see [`04` §1-2](./04-research-progress.md#1-contextpilot)) reinforces that **the right frame is "manage context as a resource" not "load everything and hope"**.

**The six techniques that actually work** (synthesized from the Oct explainer wave):

1. **Load less up front** — read only the files/sections you've already decided are relevant; don't pre-fetch.
2. **Clear stale tool results** after they've been consumed by the reasoning that needed them.
3. **Summarize old turns** when the conversation gets long; keep only the key facts, drop the chatter.
4. **Offload facts to files** the agent can re-read on demand — the file system becomes durable external memory.
5. **Isolate noisy work** in subagents so their failed attempts don't pollute the main thread's context.
6. **Filter tool output** before it hits the context — most tools return more than you need.

### The interview talking point

> "The headline context window is marketing. On RULER-style multi-needle benchmarks, effective context is usually 30–50% of advertised. So I design agents to actively manage context — load less up front, clear stale tool results, summarize old turns, offload facts to files, isolate noisy work in subagents, and filter tool output before it hits the context. There's recent research backing each of these — ContextPilot at EMNLP and FS-Researcher at ACL this year."

### Sources

- [Future AGI — Evaluating LLM context window management 2026](https://futureagi.com/blog/evaluating-llm-context-window-management-2026/) `[analysis]`
- [StartDebugging — Context Window and How Agents Stretch It in 2026](https://startdebugging.net/2026/10/what-is-a-context-window-and-how-do-agents-stretch-it-in-2026/) `[analysis]`
- [FS-Researcher — Test-Time Scaling for Long-Horizon Research Tasks with File-System-Based Agents (ACL 2026)](https://preview.aclanthology.org/ingest-acl/2026.acl-long.288/) `[primary]`
- [Toolhalla — Context engineering AI agents 2026](https://toolhalla.ai/blog/context-engineering-ai-agents-2026) `[analysis]`

→ Cross-link: [`04` §1 ContextPilot](./04-research-progress.md#1-contextpilot) · [`04` §2 FS-Researcher](./04-research-progress.md#2-fs-researcher).
