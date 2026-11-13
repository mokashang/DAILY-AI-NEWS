# Research Progress — 2026-09-27

Sunday research read. One thread this week: **the agent-memory-eval canon consolidated** into 4 papers over 30 days. Read one closely, skim three, ship 500 words. Two secondary threads worth logging: **live real-tool benchmarks** as the dominant Q3 leaderboard shape, and **the RSI (recursive self-improvement) research wave** — the operational counterpart to Anthropic's "26% of R&D is Claude" number.

Tags: `#arxiv #agents #memory #benchmarks #rsi #weekend`

---

## 1. Memory-eval synthesis — DolphinBench + Jev-Mem + MemCalib + EverMemBench {#1-memory-eval-synthesis}

**What happened:** four papers over ~30 days, converging on **"agent memory has a joint accuracy × cost × latency budget; measure all three"**:

- **arXiv 2609.24971 — DolphinBench** (Sept 21). 200 tasks/persona, verified retention over long horizons. **The first Pareto-frontier memory benchmark** (per [2026-09-26/04 §1](../2026-09-26/04-research-progress.md#1-dolphinbench)).
- **arXiv 2609.23986 — Jev-Mem.** System-One / System-Two agent memory. +11.0% on LoCoMo with lower query latency (per [2026-09-25/04](../2026-09-25/04-research-progress.md)). The **memory-as-routing** frame — memory is a decision, not a substrate.
- **arXiv 2609.24259 — MemCalib.** Calibration of memory-retrieval confidence.
- **arXiv 2602.01313 — EverMemBench.** Everlasting-memory benchmark; long-horizon evaluation over months of simulated agent history.

**The unifying idea:** if you're building an agent product, **the memory decision is a routing decision.** Hot store (in-context) is cheap latency but expensive tokens; warm store (session cache) is cheap tokens but expensive setup; cold store (vector DB + retrieval) is cheap storage but expensive latency. Route by task, log per-tier cost + latency + hit-rate; publish the numbers. The Sept 26 4-paper canon gives you the vocabulary + benchmarks to defend the routing decisions.

**Sunday assignment:** read DolphinBench closely (~45 min); skim the other three (~10 min each). Ship a **500-word `NOTES-dolphinbench.md`** in your router repo (see [`03` §2](./03-practical-skills-and-tools.md#2-notes-dolphinbench)).

**Sources:**
- [arXiv 2609.24971 — DolphinBench](https://arxiv.org/abs/2609.24971) `[primary]`
- [arXiv 2609.23986 — Jev-Mem](https://arxiv.org/abs/2609.23986) `[primary]`
- [arXiv 2609.24259 — MemCalib](https://arxiv.org/abs/2609.24259) `[primary]`
- [arXiv 2602.01313 — EverMemBench](https://arxiv.org/abs/2602.01313) `[primary]`
- [2026-09-26/04 §1 DolphinBench](../2026-09-26/04-research-progress.md#1-dolphinbench) `[primary — this repo]`
- [2026-09-25/04 Jev-Mem](../2026-09-25/04-research-progress.md) `[primary — this repo]`
- [Hugging Face Papers — Trending](https://huggingface.co/papers/trending) `[aggregator]`

### Why it matters to you

- **Job lens:** In senior interviews: "**Memory in an agent isn't a substrate; it's a routing decision measured on a Pareto frontier of accuracy × cost × latency.**" Cite DolphinBench. That single sentence differentiates a senior-agent-eng candidate from a mid-level one.
- **Startup lens:** The unfilled wedge is **audit-logged, per-tenant memory-as-a-service** with DolphinBench-shape metrics — memory + the [`03` §1 governance primitives](./03-practical-skills-and-tools.md#1-publish-router). Seed-fundable Q1 2027.
- **Insight:** The **rate of arXiv-paper-to-production-primitive is now ~60 days for agent-adjacent research.** Reading the top-3 trending papers each week for 90 minutes = a 60-day lead on tools that will become table stakes. Cadence over intensity.

→ Cross-link: [`03` §2 publish NOTES](./03-practical-skills-and-tools.md#2-notes-dolphinbench) · [2026-09-26/04 §1 memory canon](../2026-09-26/04-research-progress.md#1-dolphinbench).

---

## 2. Live real-tool leaderboards — the Q3 benchmark shape {#2-live-benchmarks}

**Consolidated state (as of Sunday):**

- **Terminal-Bench 4.0** — Claude Code + Codex tied at #1 (57.9% / 58.2% per [2026-09-22](../2026-09-22/00-tldr.md#5-terminal-bench-4)).
- **Terminal-Bench-Science** — Fable 5.1: 52.6% (per [2026-09-10](../2026-09-10/01-big-lab-moves.md#1-model-fatigue)); Opus 5.5 improves on this on the agentic-coding subset (per Anthropic).
- **MCP-Atlas** — real MCP servers; agent must discover tools rather than being handed them.
- **Toolathlon** — 32 apps, 604 tools, real integrations.
- **Artificial Analysis Intelligence Index** — Opus 5.5 currently #1 (per [2026-09-23/01 §1](../2026-09-23/01-big-lab-moves.md#1-opus-55)).
- **SWE-Bench Pro** — Opus 5.5: 89.9% (per [2026-09-25/01 §2](../2026-09-25/01-big-lab-moves.md#2-opus-55)).

**Interpretation:** the whole class of agent leaderboards is now **live, live-updating, and real-tool**. Marketing-benchmark cycles (single-shot benchmarks in each launch post) are still with us, but the industry citation-graph runs on the live boards. When you defend a model pick, cite a live board + a specific score; when you build an eval suite, seed it with tasks lifted from the top-3 relevant boards.

**Sources:**
- [Artificial Analysis](https://artificialanalysis.ai/) `[analysis]`
- [Terminal-Bench (live leaderboard)](https://tbench.ai/) `[primary]`
- [arXiv 2601.11868 — Terminal-Bench baseline paper](https://arxiv.org/pdf/2601.11868) `[primary]`
- [Papers With Code — Agent Benchmarks](https://paperswithcode.com/) `[aggregator]`
- [Hugging Face Papers — Trending](https://huggingface.co/papers/trending) `[aggregator]`

### Why it matters to you

- **Job lens:** Cite live scores by name. "Opus 5.5 is #1 on the Artificial Analysis Intelligence Index and 89.9% on SWE-Bench Pro; that's why my router defaults to it for agent-coding tasks." That's the concrete, dated evidence hiring managers want.
- **Insight:** **Live-leaderboard companies** — Artificial Analysis, Terminal-Bench, Papers With Code — will each have a real Series A moment in Q1 2027. Watch which one gets funded first; that anchors the category.

→ Cross-link: [`03` §1 publish the router](./03-practical-skills-and-tools.md#1-publish-router).

---

## 3. RSI (recursive self-improvement) research wave — operational, not speculative {#3-rsi-wave}

**The context:** Anthropic disclosed [26% of its own R&D is Claude-led](../2026-09-21/00-tldr.md) (per Sept 17–18 disclosure). That number turned RSI from a philosophy-department topic into an operational research area. The arXiv wave that immediately followed:

- **arXiv 2609.15802 — Economics of RSI.** How the cost structure of RSI changes when the improver *is* the model.
- **arXiv 2609.14858 — Dream-RSI.** Offline "dream-time" self-improvement loops (RL variant).
- **arXiv 2609.19526 — Fast-Tree-Search Self-Improvement.** Tree-search-based improver over a code base.
- **arXiv 2609.11873 — The Last AI Built by Humans.** Position paper; frames the pattern.
- **arXiv 2609.15818 — Atria Dawn: The Dawn of Agentic Superintelligence.** Also a position paper; the more speculative counterpart.

**Interpretation:** RSI research is now an *operational* category — measured, ablated, benchmarked — not a thought experiment. That means every senior agent-eng interview in Q4 will touch it. Read Economics of RSI + Fast-Tree-Search Self-Improvement; skim the two position papers; you'll be able to speak to it fluently in 60 minutes.

**Sources:**
- [arXiv 2609.15802 — Economics of RSI](https://arxiv.org/abs/2609.15802) `[primary]`
- [arXiv 2609.14858 — Dream-RSI](https://arxiv.org/abs/2609.14858) `[primary]`
- [arXiv 2609.19526 — Fast-Tree-Search Self-Improvement](https://arxiv.org/abs/2609.19526) `[primary]`
- [arXiv 2609.11873 — The Last AI Built by Humans](https://arxiv.org/abs/2609.11873) `[primary]`
- [arXiv 2609.15818 — Atria Dawn](https://arxiv.org/pdf/2609.15818) `[primary]`
- [2026-09-22 pacing week edition](../2026-09-22/00-tldr.md) `[primary — this repo]`
- [2026-09-21 self-regulation edition](../2026-09-21/00-tldr.md) `[primary — this repo]`

### Why it matters to you

- **Job lens:** RSI is the topic where a candidate can most easily *sound smart* by name-dropping — but the interviewer will follow up. Read 2 papers deeply; don't fake it.
- **Startup lens:** The **RSI-observability wedge** (tools for measuring recursive-improvement loops in agent stacks) is small but real — [Anthropic's own 1-in-47,000-blocked ratio](../2026-09-21/00-tldr.md#2-claude-builds-claude) is a metric type that will become industry-standard within 12 months. Adjacent-fundable.
- **Insight:** The RSI wave is the *most under-priced adjacency* between research and production in Q4 2026. Public artifacts (a paper reading list + a 3-metric evaluation harness) publish for near-zero cost and land as senior-signalling for a year.
