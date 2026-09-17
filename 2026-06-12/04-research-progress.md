# Research Progress — 2026-06-12

`#research #arxiv #benchmarks #agents #tool-use #post-training`

---

## 1. Tool-DC — divide-and-conquer tool selection; training-free +25.10% on BFCL/ACEBench. {#1-tool-dc}

**What it claims.** A framework that turns tool selection into a recursive try-check-retry loop. **Training-free** variant: **+25.10% average gain** on BFCL + ACEBench. **Training-based** variant: Qwen2.5-7B reaches **parity with OpenAI o3 and Claude Haiku 4.5** on the same benchmarks.

**Why this is a big deal.**
- "+25.10% training-free" is the *largest* single-method jump on tool-use benchmarks in 2026 so far.
- A 7B open-weight model matching closed flagships on tool-use specifically is the **frontier-flattening signal** for any agentic system that's primarily a tool-router.
- This becomes the **methodology citation** for any verifier-style architecture you build (see [03 §2](./03-practical-skills-and-tools.md#2-weekend-project)).

**Sources.**
- [Hugging Face Papers — Tool-DC (trending)](https://huggingface.co/papers/trending) `[primary]`
- [VoltAgent — awesome-ai-agent-papers (2026 collection)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

**Why it matters to you.**
- **Job.** Cite Tool-DC in your weekend project README; it's the highest-leverage paper-to-portfolio mapping of the week.
- **Startup.** Validates the **"trajectory verifier API"** wedge in [STARTUPS.md](../STARTUPS.md). A productized Tool-DC at the API layer is a credible Series-A wedge.
- **Insight.** The fact that the training-free version beat o3/Haiku-4.5-class systems suggests **runtime structure now matters more than model scale** for tool-heavy agents. Bookmark for the long-form thesis post.

`#tool-use #benchmarks #qwen #bfcl #acebench #training-free`

---

## 2. AI Co-Mathematician — parallel agentic workbench for open mathematical problems. {#2-ai-co-mathematician}

**What it claims.** An agentic system that **runs parallel agents on open-ended math problems**, plus literature search, theorem proving, and *working papers* (draft outputs). Direct conceptual follow-on to the **OpenAI general-purpose model that disproved an Erdős conjecture** ([2026-05-21/01 §4](../2026-05-21/01-big-lab-moves.md#4-erdos-conjecture)).

**Why it matters.**
- Tools that *organize* mathematician workflow (parallel exploration + provenance + draft synthesis) are the underexplored layer between models and human practitioners.
- Adjacent to **LemmaBench** from May 21 — this is the *workbench*, that was the *eval*.

**Sources.**
- [Hugging Face Papers (trending)](https://huggingface.co/papers/trending) `[primary]`

**Why it matters to you.**
- **Job.** If you have any undergrad math background, mention "agentic mathematician tooling" as an example of an emerging vertical to recruiters at Anthropic / DeepMind / Isomorphic; it shows you're tracking the May 21 Erdős breakthrough not just the headline labs.
- **Startup.** **Vertical-agentic-mathematician workbench** is a defensible wedge for a small team (tight community, technical buyers willing to pay). File at fit-score 3 in [STARTUPS.md](../STARTUPS.md).
- **Insight.** The math-agents thread (Erdős → LemmaBench → AI Co-Mathematician) is **3 datapoints in 4 weeks** — that's a category forming.

`#math-agents #research-agents #workbench #lemmabench`

---

## 3. Hugging Face `ml-intern` — open-source agent that automates LLM post-training. {#3-ml-intern}

**What it claims.** Hugging Face released **`ml-intern`** in late April: an **open-source AI agent that automates the LLM post-training workflow** — data prep, fine-tuning, eval, iteration. Open analogue of what **Karpathy's new Anthropic pre-training team** (announced May 22, [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)) is building inside Anthropic.

**Why it matters.**
- **"Claude uses Claude to train Claude"** (closed, Anthropic) and **`ml-intern`** (open, HF) are the same idea at different altitudes. The open variant is grep-able.
- Read the codebase; it's currently the best primer on what frontier post-training automation looks like in practice.

**Sources.**
- [MarkTechPost, "Hugging Face Releases ml-intern: An Open-Source AI Agent that Automates the LLM Post-Training Workflow" (2026-04-21)](https://www.marktechpost.com/2026/04/21/hugging-face-releases-ml-intern-an-open-source-ai-agent-that-automates-the-llm-post-training-workflow/) `[secondary]`
- [Hugging Face Blog](https://huggingface.co/blog) `[primary]` — search "ml-intern"

**Why it matters to you.**
- **Job.** Reading this codebase end-to-end is **the single highest-ROI weekend study for ML Engineer / Applied Research candidates** — explicitly cite it in interviews referencing Karpathy's Anthropic move.
- **Startup.** "Post-training agent for vertical models" is a wedge if you can find a buyer (regulated industries with proprietary data + no in-house RLHF team). File at fit-score 3 in [STARTUPS.md](../STARTUPS.md).
- **Insight.** The open community is now ~6–10 weeks behind the closed frontier on *post-training automation*. That gap is your window for learning-by-reproducing.

`#post-training #open-source #huggingface #karpathy #recursive-improvement`

---

## 4. Quick arXiv hits — June 2026. {#4-arxiv-quick-hits}

One-line each; deeper writeups follow if they prove durable.

- **BAGEN — "Are LLM Agents Budget-Aware?"** Tests whether agents respect cost ceilings; spoiler: most don't. Direct anchor for cost-aware agent design ([03 §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3)). `[primary]` — [VoltAgent collection](https://github.com/VoltAgent/awesome-ai-agent-papers)
- **AgenticPay** — multi-agent LLM negotiation system for buyer-seller transactions. Wedge signal for **agent-to-agent commerce** infrastructure. `[primary]`
- **CommCP** — multi-agent coordination via LLM communication + conformal prediction. Continuation of the May-20 CommCP thread, now with full paper. `[primary]`
- **AutoNumerics** — autonomous, PDE-agnostic multi-agent pipeline for scientific computing. Open analogue of the Prometheus thesis. `[primary]`
- **RuleSmith** — multi-agent LLMs for automated game balancing (also a clean demonstration of evaluator-as-arbiter design). `[primary]`
- **Tool-DC** — see §1 above.
- **DataFlow** — LLM-driven data preparation framework. Useful primitive if you build any vertical-Claude-for-X workflow library ([ME.md](../ME.md) active portfolio).
- **"Environment engineering"** — a paper on structured agent environments that mitigates reward hacking + human-oversight failure modes. Cite alongside Tool-DC in your sanitiser project.
- **"Externalization in LLM Agents"** — survey of memory, skills, protocols, harness engineering (the agent-systems landscape map). `[primary]` — [arXiv 2604.08224](https://arxiv.org/pdf/2604.08224)
- **"Workload-Router-Pool Architecture for LLM Inference"** — vLLM's semantic-router vision paper. Direct upstream of the "cost-aware multi-provider model router" wedge in [STARTUPS.md](../STARTUPS.md). `[primary]` — [arXiv 2603.21354](https://arxiv.org/pdf/2603.21354)
- **"Rethinking Agentic Reinforcement Learning in LLMs"** — meta-survey of the agentic-RL landscape. `[primary]` — [arXiv 2604.27859](https://arxiv.org/html/2604.27859v1)

**Aggregator sources.**
- [arXiv cs.AI — current](https://arxiv.org/list/cs.AI/current)
- [arXiv cs.LG — current](https://arxiv.org/list/cs.LG/current)
- [Hugging Face Papers — trending](https://huggingface.co/papers/trending)
- [VoltAgent — awesome-ai-agent-papers (curated 2026)](https://github.com/VoltAgent/awesome-ai-agent-papers)
- [Analytics Vidhya, "Top 10 LLM Research Papers of 2026" (May)](https://www.analyticsvidhya.com/blog/2026/05/top-llm-research-papers-2026/) `[aggregator]`

---

## Reading guide

| Time | Read |
|---|---|
| 15 min | §1 (Tool-DC) — directly informs the weekend project |
| 30 min | §3 (`ml-intern` codebase walkthrough) |
| 60 min | §1 + §3 + the *Externalization in LLM Agents* survey for an end-to-end mental model |

---

## Cross-links

- **Weekend artifact:** [`03` §2](./03-practical-skills-and-tools.md#2-weekend-project) — Tool-DC is the methodology cite.
- **Career angle:** [`05` §2](./05-career-and-startup.md#2-reprice) — runtime-structure-over-scale is the skill re-price.
- **Compute that enables this:** [`01` §2](./01-big-lab-moves.md#3-anthropic-broadcom) — 3.5GW TPU underwrites the closed post-training experiments.
