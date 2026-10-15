# Research Progress — 2026-07-14

The May-22 arc — *evals moved from mock tools to real production stacks (MCP-Atlas, Tool Decathlon)* — extended in July into two directions: **(1) recursive multi-agent orchestration is now trainable**, not just designable — with ROMA formalizing subtask-tree decomposition and MAS-Orchestra training orchestration as function-calling RL; and **(2) the eval bar keeps expanding** — Terminal-bench brings realistic CLI-agent evaluation, HAS-Bench brings *configurable human participation* into the human-AI-system evaluation loop, and a new survey shipped a 44-benchmark map of the whole LLM-agent-benchmark landscape (Feb-2023 → Feb-2026). The **ICML 2026 (Seoul, July 6–11)** cycle punctuated all of it.

Tags: `#arxiv #agents #multi-agent #orchestration #benchmarks #rl #interpretability #icml`

---

## 1. ROMA — Recursive Open Meta-Agent for long-horizon multi-agent {#1-roma}

**What's advancing:** **ROMA (Recursive Open Meta-Agent)** proposes that long-horizon multi-agent tasks be decomposed into **subtask trees** that run in **parallel across specialized agents**, avoiding the context-window ceilings that flatten most current agent teams. Rather than one big loop, ROMA builds a hierarchy: a meta-agent produces a tree, subtasks fan out, results roll up. The framing directly addresses the "context is the constraint" pattern that the Claude Code 2026 subagent guides also converge on ([`03` §2](./03-practical-skills-and-tools.md#2-claude-code-refresh)).

**Companion at ICML 2026 (Seoul, Jul 6–11): AOrchestra** — studies how agent systems can **dynamically create specialized sub-agents** during execution, rather than relying on fixed pre-defined roles. Same lineage, different lever.

**Sources:**
- [VoltAgent — Awesome AI Agent Papers 2026 (GitHub, curated arXiv list incl. ROMA)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [Atoms.dev — ICML 2026 Review: five accepted papers on building better agents (AOrchestra)](https://atoms.dev/blog/icml-2026-papers-ai-agents) `[analysis]`

### Why it matters to you

- **Job lens:** ROMA is the *research vocabulary* for the FDE artifact you're building ([`03` §3](./03-practical-skills-and-tools.md#3-artifact)) — cite it in your README as the frame for "why we decompose the task before dispatching workers." Being fluent in the *paper name* differentiates you from candidates who only know Claude Code marketing copy.
- **Startup lens:** The **AOrchestra insight** — *dynamically spawn subagents from the task, not from a fixed roster* — is the wedge under "adaptive agent teams for X vertical." Cheaper and more general than a hand-designed stack, but only useful if you *own the eval* proving it works. Which brings us to §2 & §3.
- **Insight:** The whole shift can be stated in one line: **the agent isn't the atom — the *plan* is.** Once the plan is a tree instead of a linear chain, everything downstream (worker choice, cost, verification, fault isolation) becomes a *graph* problem. Build your mental models on that basis.

---

## 2. MAS-Orchestra + orchestration-trace RL — training multi-agent as function-calling RL {#2-mas-orchestra}

**What's advancing:** **MAS-Orchestra** formalizes multi-agent orchestration as **function-calling reinforcement learning with holistic system-level reasoning**, and releases **MASBENCH** for controlled evaluation. A related line ("**RL for LLM-based Multi-Agent Systems through Orchestration Traces**") identifies **reward-design families** covering orchestration rewards for parallelism speedup, split correctness, and aggregation quality — decomposing orchestration learning into **five sub-decisions**: *when to spawn, whom to delegate to, how to communicate, how to aggregate, and when to stop.*

That five-decision decomposition is the **cleanest engineering vocabulary** we've seen for what an orchestrator actually does. Every agent-team question you'll ever face maps onto one of those five.

**Companion research:** **OPID (On-Policy Skill Distillation for Agentic RL)** on arXiv is the compression side — teaching a cheaper policy the skills of a stronger one, which pairs cleanly with the [Sonnet 5 worker swap](./03-practical-skills-and-tools.md#1-model-routing) in production.

**Sources:**
- [Hugging Face Papers — RL for LLM-based Multi-Agent Systems through Orchestration Traces (2605.02801)](https://huggingface.co/papers/2605.02801) `[primary]`
- [arXiv — RL for LLM-based Multi-Agent Systems through Orchestration Traces (HTML)](https://arxiv.org/html/2605.02801v1) `[primary]`
- [arXiv — OPID: On-Policy Skill Distillation for Agentic Reinforcement Learning (2606.26790)](https://arxiv.org/pdf/2606.26790) `[primary]`
- [VoltAgent — Awesome AI Agent Papers 2026 (MAS-Orchestra entry)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

### Why it matters to you

- **Job lens:** The **five-sub-decision decomposition** is a rock-solid interview vocabulary — *"our orchestrator's five decisions are: when to spawn, whom to delegate to, how to communicate, how to aggregate, when to stop; we picked our model per seat by asking which of these each seat owns."* Rehearse it once, use it forever.
- **Startup lens:** If you can *train* orchestration (not just prompt it), you own a durable competitive advantage over a competitor who's using a stock frontier model with prompt tricks. This is the same shift as the SFT→RL wave in code models. Watch for MASBENCH-style benchmark leaderboards to become the qualification for enterprise procurement.
- **Insight:** OPID + MAS-Orchestra together = **the plausibility of *cheap* trained agent teams** (small models, trained by distillation from a stronger one, orchestrated by an RL-trained coordinator). Two years out, the "team of small models" thesis probably eats the "one big model doing everything" story on cost.

---

## 3. Terminal-bench + HAS-Bench + LLM-agent-benchmark survey — eval-as-skill keeps re-pricing {#3-eval-wave}

**What's advancing:** The eval bar keeps rising, on multiple axes.

- **Terminal-bench** — benchmarks agents on *hard, realistic* tasks in **command-line interfaces**. This closes a real gap: MCP-Atlas / Toolathlon (May-22) benchmark against real production tools with GUIs and APIs, but the *terminal* is where a huge fraction of engineering happens. Now on the eval bar.
- **HAS-Bench (Human-Agent Systems)** — evaluates LLM-based **human-agent systems** under **configurable human participation** — how the system holds up as you dial the human loop from "always" to "occasional" to "supervisor only." Directly addresses the FDE reality where a human is *sometimes* in the loop.
- **A comprehensive LLM-agent-benchmark survey** compiled the field's benchmarks from **Feb 2023 → Feb 2026** — *44 benchmarks*, mostly designed for pure LLM agents, some multimodal. **A "map of the maps."** Read the abstract/table of contents at minimum; cite in a portfolio README.
- **AgenticPay** — a 110+ task multi-agent negotiation benchmark for buyer-seller transactions. Narrow but real; the *commerce* eval didn't exist a year ago.
- **DeepResearch Bench** — dedicated benchmark for deep-research agents; complements HAS-Bench and Terminal-bench.

**Sources:**
- [arXiv — Terminal-bench (search / awesome-ai-agent-papers entry)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv — HAS-Bench: Evaluating LLM-Based Human-Agent Systems under Configurable Human Participation (2607.04329)](https://arxiv.org/pdf/2607.04329) `[primary]`
- [arXiv — Evaluation and Benchmarking of LLM Agents: A Survey (2507.21504)](https://arxiv.org/pdf/2507.21504) `[primary]`
- [arXiv — DeepResearch Bench (2506.11763)](https://arxiv.org/pdf/2506.11763) `[primary]`
- [arXiv — Act As a Real Researcher: benchmarks for frontier LLMs in the research lifecycle (2606.07462)](https://arxiv.org/pdf/2606.07462) `[primary]`

### Why it matters to you

- **Job lens:** *"I evaluate my agents against **{MCP-Atlas, Toolathlon, Terminal-bench}** for tool use, **HAS-Bench** for the human loop, and log per-decision cost"* is now a **cover-letter-ready sentence**. Half the FDE / evaluation openings will be filled by people who cite three real benchmark names; use them.
- **Startup lens:** The 44-benchmark survey tells you the *market for evaluation itself* has hardened — Bespoke Labs, Patronus AI, Judgment Labs, and the coming wave are all selling into a space that has real vocabulary now. Any wedge that produces *auditable evidence* of agent behavior against these benchmarks is fundable.
- **Insight:** Eval is where **product-market fit meets model quality**. In 2024 nobody cared about your eval methodology; in 2026 the *first* enterprise question is "*how do I know it works?*" — and the answer is either a benchmark name or vibes. Own the benchmark vocabulary and you own the sale.

---

## 4. Anthropic mechanistic interpretability + emotion vectors — the internal-state lens matures {#4-interpretability}

**What's advancing:** Anthropic's interpretability line — from the **circuit tracing work on Claude 3.5 Haiku (now succeeded by Haiku 4.5)** demonstrating that multi-step reasoning, hallucination, and jailbreak-resistance mechanisms can be surfaced — extended into the **emotion vectors paper (April 2026)** identifying **171 emotion concept vectors in Claude Sonnet 4.5** that **causally shift** the model's behavior in the emotion's predicted direction.

Adjacent: **MIT Technology Review named mechanistic interpretability a 2026 Breakthrough Technology**, reflecting both maturity and urgency. And on arXiv the current interpretability edge is *stability* — **"Certified Circuits" (arXiv 2602.22968)** offers formal stability guarantees for mechanistic circuits, and **"Mechanistic Circuit-Based Knowledge Editing"** targets edit-in-place model surgery.

**Sources:**
- [Medium / Lee Fischman — Anthropic drops an amazing report on LLM interpretability](https://medium.com/@lee.fischman/anthropic-drops-an-amazing-report-on-llm-interpretability-d3fbcd5ba762) `[analysis]`
- [Anthropic Newsroom](https://www.anthropic.com/news) `[primary]`
- [The Consciousness AI — Mechanistic Interpretability Named MIT's 2026 Breakthrough](https://theconsciousness.ai/posts/mechanistic-interpretability-breakthrough-2026/) `[analysis]`
- [arXiv — Certified Circuits: Stability Guarantees for Mechanistic Circuits (2602.22968)](https://arxiv.org/pdf/2602.22968) `[primary]`
- [arXiv — Mechanistic Circuit-Based Knowledge Editing in Large Language Models (2604.05876)](https://arxiv.org/pdf/2604.05876) `[primary]`
- [arXiv — Mechanistic Interpretability for AI Safety: A Review (2404.14082)](https://arxiv.org/pdf/2404.14082) `[primary]`

### Why it matters to you

- **Job lens:** Interpretability is *the* rising Anthropic hiring lane besides the FDE track — and it selects for a **specific research aesthetic** (math + careful experimentation + patience). If your background has *any* signal-processing, dynamical systems, or theoretical CS component, an interpretability spec is a real path in. The Anthropic AI Safety Fellowship remains the credentialed door.
- **Startup lens:** **Certified circuits + knowledge editing** together = the beginning of a **model-surgery** market. "Edit *this* misbehavior out without retraining" is a real B2B service if you can prove stability. High technical bar; small competitor set.
- **Insight:** The subtext of mechanistic interpretability winning MIT's 2026 Breakthrough is that **"the model as a black box" is officially over as a research posture**. Every serious downstream product story now leans on some *legibility* of what the model is doing — auditing, safety, editability, cost prediction. Bias your career and portfolio investments toward whichever legibility layer suits your skills.

→ Cross-link: [`01` §2 Anthropic revenue engine funding the research](./01-big-lab-moves.md#2-anthropic-ipo) · [`02` §3 Bespoke Labs & Patronus as the eval-market anchors](./02-new-emerging.md#3-agent-funding).
