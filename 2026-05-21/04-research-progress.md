# Research Progress — 2026-05-21

The frontier item this week is not a benchmark — it's a **proof**. A general-purpose model produced **net-new mathematics**, disproving an 80-year-old conjecture. Underneath it, a wave of arXiv work is building the measurement apparatus for exactly this capability: **live, contamination-resistant math benchmarks** and **repository-level / multi-agent reasoning evals**. The throughline: as models start doing real discovery, the research community is racing to build benchmarks that can't be memorized.

Tags: `#research #math #benchmarks #agents #reasoning #arxiv #evaluation`

---

## 1. An OpenAI model disproved a central conjecture in discrete geometry {#1-erdos}

**What happened:** OpenAI reported that one of its **general-purpose reasoning models** (not a math-specialized system) addressed the **planar unit-distance problem** — Erdős, 1946: place *n* points in the plane; how many pairs can be *exactly* distance 1 apart? For ~80 years, **square-grid constructions were believed optimal.** The model found an **infinite family of constructions giving a polynomial improvement**, and — the striking part — built the proof by **connecting the geometry problem to algebraic number theory**, importing machinery from a different subfield. Independent verification by mathematicians including **Noga Alon (Princeton)** and **Thomas Bloom**.

**Why it's a milestone (and the honest caveats):**
- **First time a prominent open problem central to a math subfield was solved/advanced autonomously by AI** — and by a *general-purpose* model, not AlphaProof-style specialized tooling.
- Caveat 1: it **disproved/improved a conjectured bound** (found better constructions) — enormously valuable, but read precisely, not as "AI closed the problem."
- Caveat 2: this is a single high-profile result with expert verification; the open scientific question is **reproducibility and generality** — can the same model do this across problems, or was this a needle found in a very large haystack of attempts?

**Sources:**
- [OpenAI — An OpenAI model has disproved a central conjecture in discrete geometry](https://openai.com/index/model-disproves-discrete-geometry-conjecture/) `[primary]`
- [TechCrunch — OpenAI claims it solved an 80-year-old math problem — for real this time](https://techcrunch.com/2026/05/20/openai-claims-it-solved-an-80-year-old-math-problem-for-real-this-time/) `[secondary]`
- [AIToolly — OpenAI reasoning model disproves longstanding Erdős conjecture](https://aitoolly.com/ai-news/article/2026-05-21-openai-reasoning-model-disproves-longstanding-erds-conjecture-in-discrete-geometry) `[analysis]`
- [YourStory — Mathematicians verify the proof](https://yourstory.com/ai-story/openai-ai-cracks-80-year-old-geometry-problem) `[secondary]`

### Why it matters to you

- **Job lens:** This is the answer to the rising interview question *"what's the hardest problem you'd point a frontier model at, and how would you verify the output?"* Note the **verification** half — the result mattered *because* Alon and Bloom checked it. "I can get a novel answer **and** design the check that makes it trustworthy" is the AI-Engineer skill that just got more valuable, and it's the same muscle as eval design (below) and the regulatory pre-release review ([`01` §1](./01-big-lab-moves.md#1-trump-eo)).
- **Startup lens:** "General-purpose model + expert-in-the-loop verification" is a **services-and-tooling pattern for any field with hard, checkable problems** — math-adjacent engineering, chip design, materials, comp-bio (cf. Isomorphic Labs). The wedge isn't "the model"; it's **the verification + workflow harness** that lets a domain expert trust and ship model-generated discovery.
- **Insight:** Capability has crossed from *automation* (do the task humans do) into *discovery* (produce knowledge humans didn't have). That's precisely the capability that makes governments want pre-release review — **§1 and this section are the same story.** Track the reproducibility follow-ups closely; if independent groups replicate "general model → novel proof" across problems, the AI-research labor market reprices again.

→ Cross-link: [`01` §3 lab framing](./01-big-lab-moves.md#3-openai) · §2 below (the benchmarks built to measure exactly this).

---

## 2. The measurement apparatus racing to keep up — live math + agentic-reasoning benchmarks {#2-benchmarks}

A coherent recent arXiv cluster, all answering "how do we *measure* models that might be doing real reasoning, without contamination?"

- **LemmaBench** — a **live, research-level math benchmark** (continuously refreshed so it can't be memorized). The natural companion to the Erdős result: the field's response to "did it generalize or memorize?" is **benchmarks that update faster than training sets.** `[arXiv 2602.24173]`
- **RepoReason** — a **white-box, repository-level reasoning** benchmark using an execution-driven mutation framework (the environment as a semantic oracle to regenerate ground truth). Targets logical consistency across large, interdependent codebases — the agentic-coding analogue of "real reasoning." `[arXiv 2601.03731]`
- **A Comprehensive Evaluation of LLM Reasoning: single-model → multi-agent** — unifies direct generation, CoT, and multi-agent workflows under one lens; introduces **MIMeBench** (semantic abstraction + contrastive discrimination). Useful for the recurring "is multi-agent actually worth the cost?" question. `[arXiv 2601.13243]`
- **Benchmark Test-Time Scaling of General LLM Agents** — how much does extra inference-time compute actually buy a general agent? Directly relevant to your cost-aware-routing thesis. `[arXiv 2602.18998]`
- **PostTrainBench — can LLM agents automate LLM post-training?** A benchmark for agents doing the meta-task of improving models. Watch this lane: agents-improving-models is the recursive loop everyone's circling. `[arXiv 2603.08640]`

**Sources:**
- [arXiv 2602.24173 — LemmaBench: a live, research-level math benchmark](https://arxiv.org/pdf/2602.24173) `[primary]`
- [arXiv 2601.03731 — Benchmarking Agentic Code Reasoning at the Repository Level (RepoReason)](https://arxiv.org/abs/2601.03731) `[primary]`
- [arXiv 2601.13243 — A Comprehensive Evaluation of LLM Reasoning: single-model to multi-agent](https://www.arxiv.org/abs/2601.13243) `[primary]`
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1) `[primary]`
- [arXiv 2603.08640 — PostTrainBench: Can LLM Agents Automate LLM Post-Training?](https://arxiv.org/abs/2603.08640) `[primary]`

### Why it matters to you

- **Job lens:** Read **LemmaBench + RepoReason** end-to-end and you can speak fluently to "**contamination-resistant evaluation**" — the exact competency the §1 verification story and the §[`01`](./01-big-lab-moves.md#1-trump-eo) pre-release-review framework both demand. Eval design is the rare AI skill that's *more* valuable as raw model capability rises, because trust becomes the bottleneck.
- **Startup lens:** "Live / contamination-resistant eval-as-a-service" is a real, recurring-revenue wedge (cf. Judgment Labs, 2026-05-13). The tell that it's a market: the *labs themselves* and now *the government* need it. A vertical eval harness for one domain (legal, finance, code) is a buildable, defensible v1.
- **Insight:** Note the synchrony — the discovery result (§1) and the live-benchmark wave (§2) appeared the same week. **Capability and its measurement co-evolve.** When you see a flashy capability headline, look immediately for the benchmark being built to falsify it; that benchmark is usually the more durable thing to learn and build on.

→ Cross-link: [2026-05-19 §AIRS-Bench/JADE/TrajAD](../2026-05-19/04-research-progress.md) (the eval/verifier thread this continues) · [`03` §2 ship your own tiny eval trace](./03-practical-skills-and-tools.md#2-artifact).
