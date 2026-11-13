# 04 — Research Progress — 2026-07-07

## 1. Real-tool eval is the frontier of measurement — the June/July arXiv wave {#1-real-tool-eval}

The eval literature has now hard-pivoted from **mocked tools + synthetic tasks** → **real tools, real MCP servers, real workspaces, long horizons**. Six papers from the last ~6 weeks anchor the shift:

### MCP-Bench — real MCP servers, complex tasks
- Agents evaluated against **actual MCP servers** on multi-tool tasks where **tool discovery is part of the challenge** (not pre-listed). Complements Scale's MCP-Atlas (2026-05-22) as the second-generation "your production stack, not a mock" bench.

### LiveMCP-101 — stress test + diagnostic for MCP-enabled agents
- Adversarial + edge-case tasks; the diagnostic dimension is new — agents get graded on **failure mode**, not just pass/fail. Turns eval into a **skills gap map**.

### Odysseys — long-horizon web-agent benchmark
- Realistic **long-horizon** browsing/task tasks (multi-step, multi-page, requires memory + planning). The web-agent counterpart to Scale/Toolathlon on the API/tool side.

### Workspace-Bench 1.0 — file-dependency workspace tasks at scale
- Benchmarks agents on **workspace tasks with large-scale file dependencies** — the "coding-agent that has to understand the repo, not just this file" benchmark that the field needed.

### OfficeQA Pro — enterprise end-to-end grounded reasoning
- Enterprise benchmark for **end-to-end grounded reasoning** — the SQL-to-answer arc, but stitched together with documents, dashboards, and email context.

### WebWorld — large-scale world model for web-agent training
- Not a bench but a **training-data / world-model** primitive: a large-scale simulated web environment for training web agents at data scales previously reserved for language models. Complements Odysseys on the eval side.

### The joint thesis (why the pivot matters)

Two years ago the eval story was "can this LLM answer MMLU?". One year ago it was "can this agent use a fake calendar tool?". This quarter it's **"can your agent survive Kubernetes + BigQuery + Notion + Chrome DevTools + a 40-file monorepo across 30 turns?"** — and both **the ceiling and the discriminating power** of these benches are much higher than the previous generation.

**Why it matters — three lenses.**
- **Job:** hiring managers now ask for a **specific bench number** on a **specific tool stack**. Pick one bench (MCP-Bench is easiest to reproduce end-to-end), run it, publish the score with your config. That's a resume line.
- **Startup:** **eval-as-a-product** is a live category — Judgment Labs ($32M, 2026-05-13) will not be the last. If your wedge involves reliability, ship a *diagnostic* eval (LiveMCP-101 style), not a leaderboard.
- **Insight:** the **eval bar moving to real tools** puts a floor under the value of Verification-focused engineering work (see [`03` §2](./03-practical-skills-and-tools.md)). Any product without a real-tool eval story is one bench cycle from being commoditized.

**Sources.**
- [primary] [arXiv cs.AI current listings](https://arxiv.org/list/cs.AI/current)
- [primary] [Odysseys — Benchmarking web agents on realistic long horizon tasks (arXiv 2026)](https://arxiv.org/list/cs.AI/current)
- [primary] [OfficeQA Pro — enterprise end-to-end grounded reasoning (arXiv 2026)](https://arxiv.org/list/cs.AI/current)
- [primary] [WebWorld — large-scale world model for web agent training (arXiv 2026)](https://arxiv.org/list/cs.AI/current)
- [primary] [MCP-Bench — benchmarking tool-using LLM agents via MCP servers](https://arxiv.org/list/cs.AI/current)
- [primary] [LiveMCP-101 — stress testing MCP-enabled agents](https://arxiv.org/list/cs.AI/current)
- [primary] [Workspace-Bench 1.0](https://arxiv.org/html/2605.03596v1)
- [analysis] [alphaXiv](https://www.alphaxiv.org/) · [Papers With Code — benchmarks](https://paperswithcode.com/)

---

## 2. Adjacent research signals to track this month

- **Agent-reasoning failure modes.** Multiple June/July papers (across arXiv cs.AI and cs.CL) probe **why long-horizon planning breaks** — a live thread that couples with Odysseys/Workspace-Bench numbers. Watch for the follow-up to "Beyond Individual Intelligence" (survey on collaboration/failure attribution/self-evolution in LLM MAS) which frames the taxonomy for the next round.
- **Uncertainty propagation in agent decision chains** — UProp-style work is starting to give you **confidence intervals** on multi-step agent outputs, which pairs directly with the **cost-per-successful-task** metric from [`03`](./03-practical-skills-and-tools.md).
- **Tool-call structure is linearly decodable in residual streams** — one of the more interesting mechanistic-interpretability findings from the last quarter; suggests **tool-use is a first-class computation**, not a shallow finetune artifact. Implications for eval design and safety.

**Why it matters — three lenses.**
- **Job:** if you're targeting **research-engineer** roles, being conversant on **failure-mode + uncertainty + interpretability** as a *linked triad* is what separates candidates. Read one paper from each, connect them in your cover letter.
- **Startup:** a wedge that combines **agent uncertainty + real-tool eval + cost budget** into a runtime governor is a novel product surface — nobody has integrated all three yet.
- **Insight:** the **research → benchmark → product** loop is compressed to about **6–8 weeks** in agent land right now. Papers that land this month will be product features by Sept.

**Sources.**
- [primary] [arXiv 2506.17419 — UProp: Uncertainty Propagation in Multi-Step Agentic Decision-Making](https://arxiv.org/pdf/2506.17419)
- [primary] [arXiv 2605.25310 — Tool-Call Dependency Structure is Linearly Decodable in LLM Agent Residual Streams](https://arxiv.org/pdf/2605.25310)
- [primary] [arXiv 2605.14892 — Beyond Individual Intelligence (LLM MAS survey)](https://arxiv.org/pdf/2605.14892)
- [primary] [arXiv 2503.02682 — MPO: Boosting LLM Agents with Meta Plan Optimization](https://arxiv.org/pdf/2503.02682)
- [primary] [arXiv 2503.23037 — Agentic Large Language Models, a survey](https://arxiv.org/pdf/2503.23037)
- [primary] [arXiv 2606.12780 — ProPlay: Procedural World Models for Self-Evolving LLM Agents](https://arxiv.org/pdf/2606.12780)
- [primary] [arXiv 2604.10866 — OccuBench: Evaluating AI Agents on Real-World Professional Tasks](https://arxiv.org/pdf/2604.10866)
- [primary] [arXiv 2604.12162 — AlphaEval: Evaluating Agents in Production](https://arxiv.org/pdf/2604.12162)
- [analysis] [Hugging Face Papers — trending](https://huggingface.co/papers/trending)
