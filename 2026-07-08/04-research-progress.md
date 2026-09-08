# Research Progress — 2026-07-08

Two threads move together this week: **real-tool + production-workflow evaluation** is where the interesting benchmark work is landing (AgenticDataBench, BuilderBench, AgenticPay, Terminal-Bench, CLAWSBench), and **agentic reasoning as a taxonomy** is now stable enough that surveys and awesome-lists have taken over — a signal the field is transitioning from "invent new agents" to "measure and compose the ones we have." Also two smaller items to note: **DeepAgent** (scalable tool-set reasoning) and **Skill Reuse as Compression** (agentic RL memory pattern).

Tags: `#research #arxiv #benchmarks #agents #reasoning #evaluation`

---

## 1. The July agent-eval wave: AgenticDataBench, BuilderBench, AgenticPay, Terminal-Bench, CLAWSBench {#1-agent-evals}

**Why these five together:** they extend the **"real-tool evaluation"** thread from the [May 22 MCP-Atlas + Toolathlon story](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) into **specific production contexts**. The bar is no longer "can the agent call a mock tool" — it's "can the agent do the *actual* job."

**AgenticDataBench** — arXiv **2607.01647** (submitted **Jul 2, 2026**).
- Benchmark for **LLM-based data agents** across **15 domains** with **5 real B2B fintech workflows** (loan underwriting, KYC, claims triage, fraud triage, AML alert investigation — same shape as the Taktile customer workload in [`02` §2](./02-new-emerging.md#2-taktile)).
- Fine-grained labels + a **GitHub testbed + Hugging Face dataset** (Apache-2.0) — designed to be **reproducible and inspectable**, unlike the closed / black-box evals dominating vendor marketing.
- Practical takeaway: this is the benchmark **you can literally re-run this weekend** and post scores to. Publishing "I got X% on AgenticDataBench with a Sonnet-5-plus-GLM-5.2 router" is exactly the kind of quantified artifact recruiters at Anthropic Solutions / OpenAI FDE / Sierra CX-agent look for.

**BuilderBench** — HTML rev at arXiv **2510.06288v4**, revised early July.
- Benchmark for **agents that learn through interaction** in an open-ended exploration setting — the *training-benchmark* half of the eval story, complementary to inference-eval benchmarks like AgenticDataBench.
- Frame: how do you measure an agent's ability to *acquire* skills, not just apply them? Critical primitive for the recursive-self-improvement thread from [Karpathy's Anthropic hire](../2026-05-22/01-big-lab-moves.md#3-karpathy).

**AgenticPay** — multi-agent negotiation benchmark (110+ tasks).
- Buyer-seller natural-language negotiation — a **safety + capability crossover benchmark** (multi-agent adversarial reasoning under commercial incentives). Directly relevant to the **agentic-fintech buyer decisions** at Taktile-class companies.

**Terminal-Bench** — CLI-agent tasks.
- Hard, realistic **command-line** tasks — an eval bar much closer to what an actual dev or SRE would do than a code-only benchmark. Aligns closely with Claude Code's own product loop.

**CLAWSBench** — capability + safety of **productivity agents** in simulated workspaces.
- Explicitly pairs capability and safety in one framework — this is the *shape* of eval frameworks that Anthropic-style deployment reviews will formalize inside enterprises this year.

**Sources:**
- [Let's Data Science — Researchers Release AgenticDataBench for LLM Data Agents](https://letsdatascience.com/news/researchers-release-agenticdatabench-for-llm-data-agents-f3a2fd61) `[secondary]`
- [arXiv — BuilderBench: The Building Blocks of Intelligent Agents](https://arxiv.org/html/2510.06288v4) `[primary]`
- [Awesome AI Agent Papers (VoltAgent) — curated agentic-research index](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [Awesome Agentic Reasoning (weitianxin) — survey + resources](https://github.com/weitianxin/Awesome-Agentic-Reasoning) `[aggregator]`
- [arXiv — Agentic Reasoning for Large Language Models (survey, 2601.12538)](https://huggingface.co/papers/2601.12538) `[primary]`

### Why it matters to you

- **Job lens:** Pick **AgenticDataBench** and reproduce one workflow (loan underwriting is the easiest wire-up). Publish the notebook + a short blog. On Anthropic Solutions / Cursor / Sierra interviews, you can then walk the interviewer through: (a) the eval, (b) your router config, (c) the cost trace, (d) where it breaks — that's a **complete interview conversation, tied to a benchmark they already know about**, in one artifact. This is more valuable than one more toy MCP server.
- **Startup lens:** The AgenticDataBench workflows *are* the Taktile customer workflows. If you're building in agentic-fintech and can publish **benchmark-anchored eval numbers on your platform**, you cut your enterprise sales cycle materially — buyers finally have a shared vocabulary. The reverse is also true: if a competitor publishes AgenticDataBench numbers first, they win the vocabulary; move.
- **Insight:** Zoom out — the whole **eval world is bifurcating**. On one side: **capability benchmarks that match production workflows** (AgenticDataBench, Terminal-Bench, Toolathlon). On the other: **safety/behavior benchmarks that measure downside** (CLAWSBench, AgenticPay's negotiation-under-incentive). Serious enterprise buyers now demand *both* score sets before onboarding. The skill that has quietly become highest-leverage is **eval design** — the ability to translate a business workflow into a scorecard the buyer trusts. That's the same skill Karpathy's team at Anthropic ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) is scaling internally for pre-training.

→ Cross-link: [`03` §1 the router artifact you can run these on](./03-practical-skills-and-tools.md#1-cost-router-stack) · [2026-05-22/04 §1 the MCP-Atlas/Toolathlon precursor](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).

---

## 2. Two smaller research notes worth filing

**DeepAgent** — *"A General Reasoning Agent with Scalable Toolsets"* (arXiv **2510.21618**, updated recently).
- Framing: an agent architecture optimized for **operating over very large toolsets** — the pain point everyone hits the moment their MCP server exposes more than ~30 tools and the agent starts making bad tool-selection calls.
- Worth reading if you're building an MCP server as a portfolio artifact — most of the recent "why does the agent pick the wrong tool" pain has a paper trail here.

**Skill Reuse as Compression in Agentic RL** — arXiv **2605.31509**.
- Pattern: treat *learned skills* as **compression primitives** for future planning; an agent that has seen a pattern before short-circuits it as a single skill call.
- Practical read-through: this is why **fine-grained skill memory** (per-task "recipes" cached across sessions) is starting to feel like the next unlock for agentic products — a research analog to the [/loop TDD pattern](./03-practical-skills-and-tools.md#3-loop-tests).

**Sources:**
- [arXiv — DeepAgent (2510.21618)](https://arxiv.org/pdf/2510.21618) `[primary]`
- [arXiv — Skill Reuse as Compression in Agentic RL (2605.31509)](https://arxiv.org/pdf/2605.31509) `[primary]`

### Why it matters to you

- **Job lens:** In an interview, saying "**tool-selection over large toolsets is a known pain point — DeepAgent is the paper I'd start from**" is far above the median candidate's read on the field. Two-sentence citations of active research (not textbook stuff) are one of the most under-priced ways to signal seriousness.
- **Startup lens:** "**Skill memory / recipe caching**" is a plausible wedge for a horizontal agent-runtime startup. Nobody has fully productized this yet — a lightweight service that watches agent sessions and extracts reusable recipes, with pricing tied to the compute-cost savings it produces, is a viable positioning.
- **Insight:** The pattern across both notes is the same: **agents get more useful as their action space gets larger, but only if you help them compress it.** Whether that compression is architectural (DeepAgent), memory-based (skill reuse), or product-level (well-scoped MCP servers), the design taste that's about to matter is **compressing the action space intelligently** — not just adding more tools.

---
