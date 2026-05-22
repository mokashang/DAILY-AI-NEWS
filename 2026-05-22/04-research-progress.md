# Research Progress — 2026-05-22

The through-line continues from yesterday's live-benchmark wave, but the frontier of *measurement* took a sharp, practical turn: from "can the model reason on paper?" to **"can the agent do real work, against real tools, with real errors?"** Two benchmarks define it — **MCP-Atlas** and **Tool Decathlon (Toolathlon)** — and a major **agentic-reasoning survey** gives the field its vocabulary. If you read one thing this week to sound credible in an FDE/AI-engineer interview, read these; they describe the exact gap between "demo works" and "deploys."

Tags: `#research #benchmarks #mcp #agents #tool-use #evaluation #arxiv`

---

## 1. Real-tool agent benchmarks — MCP-Atlas + Tool Decathlon {#1-real-tool-benchmarks}

The defining shift: agent evals stopped using **simplified mocks** and started running against **real tools, real schemas, real errors.**

- **MCP-Atlas (Scale)** — a large-scale benchmark for **tool-use competency with *real* MCP servers.** Tasks run against actual MCP implementations (real schemas, real errors, real API behavior). Crucially, **prompts describe the goal in plain language and never name the tool or server** — so the agent must **discover** what to use, not follow a recipe. This is the closest public proxy yet for "can this agent operate a stack it wasn't told about?" `[arXiv 2602.00933]`
- **Tool Decathlon / Toolathlon (ICLR 2026)** — a **diverse, long-horizon** benchmark spanning **32 applications and 604 tools**, from everyday platforms (Google Calendar, Notion) to professional systems (**Kubernetes, BigQuery, WooCommerce**). Realistic environment setup + **execution-based evaluation** (the environment checks whether the task actually got done), most tools built on revised/implemented **MCP servers**. `[arXiv 2510.25726]`

Together they answer the question every deployment team actually has: not "is the model smart?" but **"will the agent complete a multi-step job across my real tools without me hand-holding it?"**

**Sources:**
- [arXiv 2602.00933 — MCP-Atlas: a large-scale benchmark for tool-use competency with real MCP servers](https://arxiv.org/html/2602.00933) `[primary]`
- [Scale — Open-sourcing MCP-Atlas: a benchmark for real tool use](https://scale.com/blog/open-sourcing-mcp-atlas) `[primary]`
- [arXiv 2510.25726 — The Tool Decathlon: benchmarking language agents for diverse, realistic, long-horizon task execution](https://arxiv.org/pdf/2510.25726) `[primary]`
- [GitHub — hkust-nlp/Toolathlon (ICLR 2026)](https://github.com/hkust-nlp/Toolathlon) `[primary]`

### Why it matters to you

- **Job lens:** This is the **technical core of the FDE/Integration job**, made into a benchmark. "I evaluated my agent against real MCP servers (à la MCP-Atlas) and reported tool-discovery + execution success" is a sentence that says *"I know the difference between a demo and a deployment."* Use the [`03` §2](./03-practical-skills-and-tools.md#2-artifact) artifact to make it true, not just say-able.
- **Startup lens:** **Real-tool, execution-based eval is a recurring-revenue wedge** (the labs and enterprises both need it — cf. Judgment Labs, [2026-05-13](../2026-05-13/04-research-progress.md)). The defensible product isn't "a benchmark"; it's a harness that runs *a customer's own tools* and tells them whether their agent is production-ready. Toolathlon's "execution-based evaluation against 604 real tools" is the open-source proof that this is buildable.
- **Insight:** Capability and its measurement keep co-evolving, but the measurement just got *more expensive and more valuable*: mocking tools is cheap; standing up 604 real ones is hard. **The harder a benchmark is to build, the more durable the skill of building it.** Eval-against-reality is the rare competency that gets *more* scarce as models improve — exactly the bet to make.

→ Cross-link: [2026-05-21/04 §2 the live-benchmark wave](../2026-05-21/04-research-progress.md#2-benchmarks) · [`03` §1 the agent-team you'll test this way](./03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. The vocabulary layer: "Agentic Reasoning for Large Language Models" (survey) {#2-agentic-reasoning-survey}

**What it is:** A comprehensive survey that reframes LLMs from "text predictors" to **autonomous agents that plan, act, and learn through continual interaction** — and, usefully, gives the field a clean **three-layer taxonomy**:

1. **Foundational agentic reasoning** — planning, tool use, search.
2. **Self-evolving agentic reasoning** — feedback, adaptation, learning from outcomes.
3. **Collective multi-agent reasoning** — coordination and knowledge sharing across agents.

It's the connective tissue under everything else this week: layer 1 is what **MCP-Atlas/Toolathlon** measure; layer 2 is what **Karpathy's pre-training-automation team** ([`01` §3](./01-big-lab-moves.md#3-karpathy)) is industrializing; layer 3 is the multi-agent thread the archive has tracked since CHAL/DyTopo.

**Sources:**
- [arXiv 2601.12538 — Agentic Reasoning for Large Language Models (survey)](https://arxiv.org/abs/2601.12538) `[primary]`
- [Hugging Face — paper page for 2601.12538](https://huggingface.co/papers/2601.12538) `[aggregator]`
- [GitHub — Awesome-Agentic-Reasoning (companion list)](https://github.com/weitianxin/Awesome-Agentic-Reasoning) `[primary]`

### Why it matters to you

- **Job lens:** Surveys are the **highest ROI-per-hour reading** for interviews — one paper gives you the *map* (the three layers) so you can place any specific paper or product correctly. Drop the taxonomy in conversation ("that's a layer-2 self-evolving technique") and you sound like you've read the field, not a blog post.
- **Startup lens:** The taxonomy is a **wedge-finder**: most shipped products are stuck at layer 1 (plan/tool/search). The unbuilt value is in layer 2 (agents that *improve from their own outcomes* — durable, data-compounding) and layer 3 (coordination infra). Score your wedge by which layer it lives in; layer-1-only wrappers are the "feature, not a company" filter from [2026-05-21/02 §2](../2026-05-21/02-new-emerging.md#2-defense-and-climate).
- **Insight:** Note the synchrony again — a *taxonomy* survey, *real-tool* benchmarks, and a *talent* move toward self-improving systems all in one week. When the survey, the benchmark, and the hiring all point at "self-evolving, multi-agent, real-tool" simultaneously, that's not noise — that's the field telling you where the next two years go. Read with it, build toward it.

→ Cross-link: [`01` §3 layer-2 industrialized (Karpathy)](./01-big-lab-moves.md#3-karpathy) · [2026-05-21/04 §2 single→multi-agent eval](../2026-05-21/04-research-progress.md#2-benchmarks).
