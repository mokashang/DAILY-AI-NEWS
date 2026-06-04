# Research Progress — 2026-06-04

The research sweep this week converges on a single thesis: **multi-agent orchestration is real, but it's only a win when you bake in cost.** Three arXiv papers (AgentOrchestra, the orchestration-survey from January, and "When Should We Orchestrate Multiple Agents?") plus the **Efficient Benchmarking of AI Agents** paper are the four citations that should land in your next 10 cover letters. They map exactly onto the practitioner story (Opus 4.8 dynamic workflows, [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows)).

Tags: `#arxiv #research #orchestration #cost #benchmarks #multi-agent`

---

## 1. Cost-aware multi-agent orchestration — three papers, one thesis {#1-orchestration-cost}

**What's moved:**

### a. AgentOrchestra — TEA protocol, 89.04% on GAIA Test (v6 updated May 28, 2026)
- [arXiv:2506.12508](https://arxiv.org/abs/2506.12508) — *"AgentOrchestra: Orchestrating Multi-Agent Intelligence with the Tool-Environment-Agent (TEA) Protocol"* `[primary]`
- **The contribution:** a **protocol** (not just a framework) for *how* a planner agent describes a sub-task to a worker agent, and *how* a worker reports back. Tool, Environment, and Agent are the three explicit types.
- **The number:** **89.04% on the GAIA Test set** — high enough to be a credible new SOTA on a respected agent benchmark.
- **Why this is interesting:** protocols compose where frameworks don't. The TEA decomposition is small enough to copy into a custom system; the paper is essentially a reference implementation guide.

### b. When Should We Orchestrate Multiple Agents? (March 2026 with active discussion)
- [arXiv:2503.13577](https://arxiv.org/abs/2503.13577) — *"When Should We Orchestrate Multiple Agents?"* `[primary]`
- **The contribution:** a formal cost-aware framework — explicitly accounts for **inference compute cost, carbon, and per-agent capability differentials.** Shows that *naive* multi-agent gains are systematically over-estimated when cost is omitted from the comparison.
- **The killer plot:** for many task families, the **single best model at a higher per-call price** dominates a multi-agent ensemble of cheaper models on cost-adjusted performance. This is the cleanest evidence-based pushback against multi-agent maximalism.

### c. Benchmarking Multi-Agent LLM Architectures for Financial Document Processing (March 2026)
- [arXiv:2603.22651](https://arxiv.org/abs/2603.22651v1) — *"Benchmarking Multi-Agent LLM Architectures for Financial Document Processing: A Comparative Study of Orchestration Patterns, Cost-Accuracy Tradeoffs and Production Scaling Strategies"* `[primary]`
- **The number:** reflexive architecture hits **0.943 F1**, but at **2.3×** the cost of the sequential baseline. The 2.3× multiplier is the new "rule of thumb" to cite in interviews.

### d. The Orchestration of Multi-Agent Systems (January 2026 — the survey)
- [arXiv:2601.13671](https://arxiv.org/abs/2601.13671) — *"The Orchestration of Multi-Agent Systems: Architectures, Protocols, and Enterprise Adoption"* `[primary]`
- **What to take from it:** the taxonomy (centralized vs decentralized vs hybrid orchestration; sync vs async messaging; agent-discovery patterns). Use it as the *map* before you read the other three.

### Why it matters to you

- **Job lens:** These four papers + one sentence of synthesis = a 60-second answer to *"how do you think about multi-agent design?"* The synthesis: **"the question isn't whether to use multiple agents, it's whether the per-task cost-adjusted improvement justifies the orchestration overhead — and there's published methodology to answer that case-by-case."** Memorize that sentence.
- **Startup lens:** **Cost-adjusted multi-agent benchmarking** is an unowned analyst category. Whoever publishes the "Artificial Analysis for multi-agent topologies" gets the eyeballs of every CTO trying to size an AI team's compute budget.
- **Insight:** The research community has converged on cost-aware evaluation a full year ahead of the typical lag. That's because **the buyer of frontier models — enterprise CFOs — already converged on it.** Academic and commercial incentives are pointed the same way for the first time in this cycle.

→ Cross-link: [`01` §4](./01-big-lab-moves.md#4-opus-48) (the production face) · [`03` §1](./03-practical-skills-and-tools.md#1-dynamic-workflows) (your assignment).

---

## 2. Efficient Benchmarking of AI Agents — cut eval cost 44–70% {#2-efficient-benchmarking}

**What's moved:** Franck Ndzomga's *"Efficient Benchmarking of AI Agents"* ([arXiv:2603.23749](https://arxiv.org/abs/2603.23749), submitted March 24, 2026; v1) shows that for a new agent scaffold, you only need to evaluate on **tasks with intermediate historical pass rates (30–70%)** to preserve rank-order against full evaluation — at **44–70% lower task count.**

- Empirical base: **8 benchmarks × 33 agent scaffolds × 70+ model configurations.**
- The intuition: trivially-easy tasks (everyone passes) and impossibly-hard tasks (nobody passes) contribute zero discrimination — middling tasks are where rank-order is determined.
- Practical implication: **you can build a small, fast eval suite that ranks agents *correctly* for an order of magnitude less compute.**

**Sources:**
- [arXiv:2603.23749 — Efficient Benchmarking of AI Agents (PDF)](https://arxiv.org/pdf/2603.23749) `[primary]`
- [arXiv abstract page](https://arxiv.org/abs/2603.23749) `[primary]`

### Why it matters to you

- **Job lens:** Eval-design is the under-priced skill in the agentic-AI hiring market ([2026-05-21/05](../2026-05-21/05-career-and-startup.md)). A portfolio artifact that **(a) picks a benchmark, (b) sub-samples to the 30–70% pass-rate window, (c) shows rank-order is preserved on your scaffold** is a hireable demonstration of the skill. 4 hours of work, evergreen on a résumé.
- **Startup lens:** Eval-as-a-service plays (Judgment Labs, Patronus, others) can adopt this paper directly to cut their own infra cost. If you're building one, this is a "free 50% margin" technique sitting in the open literature.
- **Insight:** The bottleneck on agent progress is increasingly *evaluation throughput*, not *model capability*. Anything that compresses the eval loop compounds — and this paper compresses it by half.

→ Cross-link: [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) (real-tool eval thread) · [`05` §4](./05-career-and-startup.md#4-finops-lane).

---

## 3. Adjacent threads worth scanning {#3-adjacent}

Two more papers, one-line takeaways each. Read on the weekend if at all.

- **MLR-Bench** ([arXiv:2505.19955](https://arxiv.org/pdf/2505.19955)) — *"Evaluating AI Agents on Open-Ended Machine Learning Research"*; 201 open-ended ML research tasks + human-aligned MLR-Judge. **Take:** the eval bar for "AI doing ML research" is now public and quantitative. Karpathy's new Anthropic team has a benchmark to be judged against. `[primary]`
- **PaperBench** ([arXiv:2504.01848](https://arxiv.org/pdf/2504.01848)) — *"Evaluating AI's Ability to Replicate AI Research."* **Take:** replication, not generation, is the harder test — and the right one for the "AI improves AI" thesis ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)). `[primary]`
- **From Reproduction to Replication** ([arXiv:2506.19724](https://arxiv.org/pdf/2506.19724)) — *"Evaluating Research Agents with Progressive Code Masking"*; a graduated-difficulty research-agent benchmark. **Take:** the right way to evaluate research agents is to **incrementally hide context** and watch where they break. `[primary]`

### Why it matters to you

- **Job lens:** Reference one of these papers (by title + 1-line takeaway) in a cover letter to an Anthropic pre-training role. Differentiates you from the bulk of candidates who cite generic agent benchmarks.
- **Startup lens:** Research-agent evaluation is a niche but defensible product area — and the public benchmarks above are the starter kit.
- **Insight:** The shape of agent evaluation is moving toward **graduated difficulty + cost-adjusted ranking**, away from binary pass/fail on fixed tasks. Plan your eval skills around that direction.

→ Cross-link: [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy) (the team this benchmarks).
