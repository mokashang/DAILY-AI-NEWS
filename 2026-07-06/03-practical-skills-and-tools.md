# Practical Skills & Tools — 2026-07-06

Hands-on this week: **Fable 5 is back with a new severity + bounty stack you should learn to speak fluently**, and the **model routing table just got a Terra tier + a Gemini 3.5 Flash tier that beats last-gen Pro on real-tool benchmarks** — rebuild your router this week. Voice-agent building drops to a no-code lane at xAI, and Deep Research Max at Google gives you a new autonomous-research primitive worth stress-testing.

Tags: `#practical #claude-code #model-routing #safety #voice-agents #deep-research #mcp #cost-optimization`

---

## 1. Use the returned Fable 5 well — Cybersecurity Classifier, HackerOne, and severity {#1-fable-5-usage}

**What happened:** Fable 5 came back on **July 1** with new safety infrastructure ([`01` §1](./01-big-lab-moves.md#1-fable-5-return)). The practical stack:

- **Cybersecurity Classifier** — invisible pre/post-inference layer that blocks the vulnerability-generation patterns identified in the Amazon research. You don't call it directly; it just runs.
- **HackerOne bug-bounty program** — public, paid channel for reporting cyber jailbreaks. If you find one, submit it.
- **Draft AI Jailbreak Severity Framework** — Anthropic's proposed severity taxonomy. Read the draft, adopt the vocabulary.
- **Usage window:** Fable 5 included up to **50% of weekly usage limits through July 7**, then usage credits after — plan your intensive work *this week*.

### What to actually do

1. **Read Anthropic's [Redeploying Fable 5](https://www.anthropic.com/news/redeploying-fable-5) post as primary source.** Ten minutes.
2. **Enable Fable 5 in Claude Code + Claude.ai** and run one non-trivial cyber-adjacent task (a secure-code review of your own repo, or a threat-model discussion). Note whether the Cybersecurity Classifier changes any responses vs. what you'd have gotten from Sonnet 5.
3. **If you find a cyber jailbreak** — even a small one — **submit to the HackerOne program**. Even a paid $250 finding is a *signal* on your résumé that recruits well at Anthropic (Trust & Safety) and at every AI-security startup.
4. **Draft one page on the AI Jailbreak Severity Framework** as a public artifact — LinkedIn, blog, or repo README. This is the fastest cheap way to demonstrate you understand the new safety stack.

### Why it matters to you

- **Job lens:** Anyone who can articulate the severity framework + classifier layering + bounty operations in interview vocabulary jumps the queue for AI-safety / trust-and-safety / assurance roles. This is the highest-ROI vocabulary shift of Q3.
- **Startup lens:** The bounty + severity framework are calls for tooling. Build a **submission-flow / triage / severity-scoring** SaaS for AI bounties. Adjacent: **cross-lab severity normalization** — OpenAI + Google will need equivalents soon.
- **Insight:** Anthropic's willingness to ship a *draft* severity framework in production shows they view it as a **collaborative standard**, not proprietary. If you contribute a well-considered addition (e.g., an under-covered attack class), you can be part of the standard by August.

---

## 2. The July 2026 model routing table — rebuild your router tonight {#2-model-routing}

**What happened:** Three big shifts landed inside 96 hours: **Fable 5 back**, **GPT-5.6 Sol / Terra / Luna preview**, **Gemini 3.5 Flash GA beating last-gen Pro**. Refresh the router.

### Suggested routing table (July 2026)

| Task | Primary | Backup | Notes |
|---|---|---|---|
| **Deep research / long-horizon coding** | **Claude Opus 4.7 (1M ctx)** | GPT-5.6 Sol / Gemini 3.5 Pro | Opus stays first for multi-file reasoning; Sol contests Terminal-Bench 2.1 |
| **Everyday coding / most agent workers** | **Claude Sonnet 5** (promo $2/$10 through Aug 31) | GPT-5.6 Terra / Gemini 3.5 Flash | Sonnet 5 is the promo-price sweet spot; Terra & Flash trade in per benchmark |
| **Cost-critical / high-QPS / short reasoning** | **Gemini 3.5 Flash** | GPT-5.6 Luna / Claude Haiku 4.5 | Flash beats Gemini 3.1 Pro on Terminal-Bench 2.1 — routing default for volume |
| **Voice agents** | **xAI Voice Agent Builder** (Grok Voice) | GPT-Realtime-2 / Gemini Live | Grok Voice adds MCP native, telephony bundle, voice cloning — best turnkey option |
| **Cyber / security-adjacent** | **Claude Fable 5** (through July 7 promo) | Sonnet 5 with prompt-caching | Cybersecurity Classifier is on for Fable 5; use it while free |
| **Scientific / pharma workflows** | **Claude Science** | Sonnet 5 + custom MCP tools | Science ships with 60+ tools; skip the manual assembly for research work |
| **Autonomous research report** | **Gemini Deep Research Max** | Claude Sonnet 5 + web tools | New Max tier is the step change; benchmark it against Sonnet 5 |

### What to actually do

1. **Refactor your project's model-selector** to use this table. Even a 20-line dispatch function that maps task-type → model + provider is enough. Commit it.
2. **Re-price your top three prompts** at the new mid-tier prices. Terra at ~½ of GPT-5.5 cost is the biggest lever — expect 20–40% total-cost reduction.
3. **Add per-call cost logs.** You should be able to answer "what did this feature cost per user last week?" by Friday.
4. **Ship a fallback + latency guardrail** — if Sol is over 8s or 5xx, route to Sonnet 5. Fable 5 goes to Sonnet 5 after the July 7 promo window.

### Why it matters to you

- **Job lens:** "Which model do you use for what, and why?" is the single most common technical question in AI-Engineer / FDE / Solutions interviews in July. Have the table ready in your head, with two numbers per entry.
- **Startup lens:** The Terra tier is the year's biggest cost lever for production apps. Rerun your unit economics — a lot of "not yet unit-economical" AI startups just crossed the line.
- **Insight:** The mid-tier of every provider is now good enough for 80% of production workloads. **The routing skill is now more valuable than the flagship-prompting skill.** Own the router, not the prompt.

→ Cross-link: [`01` §4 the GPT-5.6 preview details](./01-big-lab-moves.md#4-gpt-56) · [`01` §6 the Gemini 3.5 Flash benchmarks](./01-big-lab-moves.md#6-gemini-flash).

---

## 3. MCP-Bench as the new eval baseline — build one this weekend {#3-mcp-bench-eval}

**What happened:** **MCP-Bench** ([ICLR 2026](https://openreview.net/pdf?id=fe8mzHwMxN)) landed as the standardized benchmark for **MCP-enabled agents on complex real-world tasks**. It follows **Tool Decathlon / Toolathlon (32 apps, 604 tools)** and pairs with **LiveMCP-101** for stress-testing. Combined, they set the eval bar: **your agent should be measured on real MCP servers, discovering tools, doing multi-goal orchestration** — not on canned single-tool tests.

### What to actually do

**Weekend project (4–6 hours):** build a **MCP-Bench-graded eval** for your own agent, even a small one.

1. Pick 3 MCP servers you use (e.g., filesystem + git + a custom one).
2. Write **10 tasks** that require tool *discovery* (agent has to figure out which tool to call) + **10 tasks** that require **multi-goal orchestration** (two tools, chained).
3. Run each task against Sonnet 5 + GPT-5.6 Terra + Gemini 3.5 Flash. Record: **success rate**, **cost per success**, **latency per success**, **wrong-tool-called rate**.
4. Publish as a repo (`mcp-eval-YOUR-DOMAIN`) with the results in a `README.md` table.

### Why it matters to you

- **Job lens:** Publishing a MCP-graded eval is the fastest way to land an interview at Anthropic Solutions or any FDE role. It shows: you speak the vocabulary, you can operate MCP, you can measure agents against real tools, you produced a decision artifact. This is the highest-ROI weekend project of Q3.
- **Startup lens:** The eval-as-a-service wedge is wide open. Judgment Labs raised $32M for eval in May ([2026-05-13](../2026-05-13/02-new-emerging.md)); MCP-Bench + Toolathlon give you a shared vocabulary the market will pay to plug into.
- **Insight:** "Evals are the moat" is now conventional wisdom. Don't just build them; **publish them**. The best evals are cited more than the best models.

→ Cross-link: [`04` §1 the research trend](./04-research-progress.md#1-mcp-bench).

---

## 4. xAI Voice Agent Builder — pilot it this week {#4-voice-agent-builder}

**What happened:** **xAI launched Voice Agent Builder in beta** — no-code platform for production voice agents on Grok Voice, bundling:

- **Telephony** (inbound / outbound / SIP).
- **Knowledge retrieval** (RAG over your docs).
- **Tool calling + MCPs** (native MCP support).
- **Guardrails** (business logic + refusal).
- **Voice cloning** (custom voice from small samples).
- **Observability + call review** (session logs, playback, correction).

### What to actually do

1. **Pilot one flow**: build a voice-agent that answers a real question you've been getting on email (customer FAQ, project intake, availability lookup).
2. **Wire it to one MCP server** — even a trivial one (a filesystem or a Google Calendar via community MCP). That gives you a working demo of the composability story.
3. **Publish a 90-second Loom** demoing it. Post to X + LinkedIn. Tag @xai.
4. **Cost-baseline**: log per-minute cost + latency. Compare against Retell / Bland / Vapi (the incumbent voice-agent SaaS layer).

### Why it matters to you

- **Job lens:** Voice-agent-at-scale (call centers, dispatch, healthcare intake) is a $50B+ TAM with a real hiring surge. Sierra, Decagon, Cognigy are all hiring. A pilot + Loom demo is a portfolio piece that gets attention.
- **Startup lens:** Voice Agent Builder collapses the "build the plumbing" cost to near-zero. **The wedge is now the domain**: agents for veterinarians, agents for HVAC, agents for local government. Pick a vertical, own the training data + integration patterns.
- **Insight:** No-code voice at a frontier lab is a threat to the SaaS layer above it (Retell, Bland, Vapi). But it's an *accelerant* to voice-agent apps *below* it. Position on the app layer, not the SaaS layer.

→ Cross-link: [`01` §7 the xAI Voice launch details](./01-big-lab-moves.md#7-meta-xai).

---

## 5. Gemini Deep Research Max — the new autonomous-research primitive {#5-deep-research-max}

**What happened:** Google shipped **Deep Research Max** ([blog.google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/next-generation-gemini-deep-research/)) — a **step-change autonomous research agent** for long-horizon multi-source research. Positioned as their answer to Anthropic's Managed Agents / Dreaming primitives + OpenAI Deep Research.

### What to actually do

1. **Run the same research question through three agents**: Claude Sonnet 5 (with web tools), OpenAI Deep Research, and Gemini Deep Research Max. Pick a question you *know the answer to* (from prior work) so you can grade quality.
2. **Score** on: **coverage**, **accuracy**, **hallucination rate**, **citation quality**, **time-to-report**, **cost**.
3. **Publish the comparison** as a blog post. If you're rigorous, this gets shared.
4. **Adopt the winner as your default research agent** for the next month.

### Why it matters to you

- **Job lens:** Comparative benchmarking of the three research agents is the single highest-signal artifact for consulting / analyst / AI-Engineer roles at big firms (PwC / Deloitte / EY are all buying research agents).
- **Startup lens:** The **research-agent-for-X** market is real. Legal research (Harvey), sales research (Clay), finance research (Rogo). Deep Research Max being at parity or better than OpenAI's suggests the *underlying agent quality* is now a commodity; the wedge is domain + workflow.
- **Insight:** Three near-equivalent research agents mean the differentiator has moved from **capability** to **integration + workflow + trust in the output**. Your job as a builder: make the output legible + auditable + acted-on, not just generated.

→ Cross-link: [`01` §6 Gemini 3.5 Flash + Deep Research Max release](./01-big-lab-moves.md#6-gemini-flash).
