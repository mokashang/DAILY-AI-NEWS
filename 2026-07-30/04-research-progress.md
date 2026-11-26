# Research Progress — 2026-07-30

The RSI thought-experiment moved to arXiv formalism, "vibe coding" got its first canonical survey (1,000+ papers reviewed), and Terminal-Bench + MLGym + CORE are the new agent-eval trio to know. Frame: **research is catching up to what practitioners already do — memorize the taxonomies now while there's still a small window of citation-arbitrage in interviews.**

Tags: `#arxiv #research #rsi #vibe-coding #benchmarks #agents #evals`

---

## 1. Recursive Self-Improvement moves from proposal to formal characterization {#1-rsi-paper}

**What happened:** Two connected artifacts anchor this week's RSI thread.

**(A) Anthropic — "When AI Builds Itself: Our Progress Toward Recursive Self-Improvement and Its Implications"** (published 2026-06-04). Key claims cited by Anthropic's endorsement of [Pacing the Frontier](./01-big-lab-moves.md#1-pacing-the-frontier):
- **>80% of Anthropic's merged code (as of May 2026) is written by Claude.**
- Survey of 130 Anthropic research employees (March 2026): **median self-reported productivity multiplier from AI = ~4×.**
- Framework proposes **three futures — plateau, human-guided acceleration, full RSI** — with observables that would let you tell them apart in retrospect. Explicit position: they are NOT at RSI yet, but the runway is shorter than expected.

**(B) arXiv 2607.07663 — "Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops."** Formalizes the boundary between (a) inference-time self-refinement (in-scope for current systems) and (b) autonomous research loops (out-of-scope until compute-and-tool primitives cross a specified threshold). Provides a **taxonomy of research-loop primitives** — hypothesis generation, experiment design, code execution, result interpretation, decision-to-continue — and marks which are demonstrated in the wild.

**Sources:**
- [Anthropic — When AI Builds Itself (research post)](https://www.anthropic.com/research/rsi) `[primary]`
- [arXiv 2607.07663 — Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/pdf/2607.07663) `[primary]`
- [Forbes (Lance Eliot) — Anthropic Declares That The Next Big Step For Humans And AI Is AI That Builds Itself Via Recursive Self-Improvement](https://www.forbes.com/sites/lanceeliot/2026/06/07/anthropic-recursive-self-improvement-ai/) `[analysis]`
- [Kingy AI — Inside the Recursive Self-Improvement Race](https://kingy.ai/news/anthropic-says-ai-is-now-building-ai-inside-the-recursive-self-improvement-race/) `[analysis]`
- [Menon Lab — Anthropic's Bombshell: Claude Writes 80% of Its Own Code](https://themenonlab.blog/blog/anthropic-recursive-self-improvement-ai-builds-itself-june-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** The RSI taxonomy is the conceptual glue between (a) the [Pacing the Frontier letter](./01-big-lab-moves.md#1-pacing-the-frontier), (b) the [Hugging Face agent breach](./01-big-lab-moves.md#2-hf-breach), and (c) the [agent-safety checklist](./03-practical-skills-and-tools.md#3-agent-safety-checklist). Know the "three futures + five research-loop primitives" so you can situate any agent-safety question you get.
- **Startup lens:** The taxonomy is also a **product taxonomy** — every research-loop primitive is a candidate product surface (hypothesis-generation UX, experiment-scaffolding, verification / halting, etc.). The Karpathy `autoresearch` weekend project from [2026-05-11](../2026-05-11/) sits inside this taxonomy; the next 6 months will produce funded companies here.
- **Insight:** "80% of Anthropic's code written by Claude" is a *productivity* metric, not an RSI metric — it measures adoption, not autonomy. The gap between those two, formalized in the arXiv paper, is where the interesting technical debate is right now.

→ Cross-link: [`01` §1 the pacing letter cites this paper](./01-big-lab-moves.md#1-pacing-the-frontier).

---

## 2. Vibe Coding gets its canonical survey — 1,000+ papers, formal taxonomy {#2-vibe-coding-survey}

**What landed:** **arXiv 2510.12399 — "A Survey of Vibe Coding with Large Language Models"** — the first systematic review of the practice Karpathy named. Draws from **>1,000 research papers** to formalize:

- **Definition:** vibe coding = a development methodology where developers validate AI-generated implementations through **outcome observation** rather than line-by-line code comprehension.
- **Critical infrastructure components** identified: LLMs for coding · LLM-based coding agents · development environments · feedback mechanisms.
- Companion empirical work: **arXiv 2604.12311 "Is Vibe Coding the Future?"** — 450 vibe-coded Python scripts across Claude 3.5 Haiku, GPT-4o-Mini, and Gemini 2.5 Flash on construction safety tasks; **arXiv 2602.18492 "Vibe Coding on Trial: Operating Characteristics of Unanimous LLM Juries"** — a unanimous-jury evaluation protocol as a defense against silent-failure vibe-coded code.

**Sources:**
- [arXiv 2510.12399 — A Survey of Vibe Coding with Large Language Models](https://arxiv.org/abs/2510.12399) `[primary]`
- [HuggingFace Papers — Survey of Vibe Coding](https://huggingface.co/papers/2510.12399) `[primary]`
- [arXiv 2604.12311 — Is Vibe Coding the Future? Empirical Assessment on Construction Safety](https://arxiv.org/abs/2604.12311) `[primary]`
- [arXiv 2602.18492 — Vibe Coding on Trial: Operating Characteristics of Unanimous LLM Juries](https://arxiv.org/abs/2602.18492) `[primary]`

### Why it matters to you

- **Job lens:** "**Outcome-observation as validation**" is a concrete phrase to know when talking about your own development practice in interviews. The taxonomy also names the **verification-gap** (validated-by-outcome vs. validated-by-understanding) — you can position your own testing / eval discipline as filling this gap, which is exactly what a lot of new-eng ambient hiring anxiety centers on.
- **Startup lens:** The **"unanimous LLM jury"** pattern is a shippable verification primitive — one Opus 5 + one Fable 5 + one Gemini 3.5 Pro, all must agree the code passes, before merge. Cheap now that Kimi K3 exists as the majority-vote-tiebreaker on non-sensitive checks. There is a product here for the sub-10-eng dev-tools stack.
- **Insight:** The 1,000+ paper baseline means the field has enough surface for the next round of methods papers to specialize. Watch for **domain-specific vibe-coding evals** (finance, legal, medical, industrial) in Q3–Q4 — the pattern that hit LLM benchmarking in 2023 replays here.

→ Cross-link: [`03` §2 the router uses a similar tier-hierarchy logic](./03-practical-skills-and-tools.md#2-cost-routing).

---

## 3. Agent-eval trio worth knowing — Terminal-Bench, MLGym, CORE {#3-agent-eval-trio}

**What landed:** Three benchmarks / eval frameworks that have gained enough adoption in Q2–Q3 2026 to warrant knowing by name.

- **Terminal-Bench.** Benchmarks agents on **hard, realistic tasks in command-line interfaces** — real shells, real scripts, real failure modes. Distinct from the LHTB / SWE-bench class; the fastest way to sanity-check an agent framework's ability to survive an unstructured environment.
- **MLGym.** A framework + benchmark for **advancing AI research agents** — specifically for agents that run experiments, interpret results, iterate. Direct arXiv cousin of the [RSI paper](#1-rsi-paper); MLGym is where the primitives get measured.
- **CORE.** Benchmarks LLMs' **code-reasoning capabilities through static-analysis tasks** — trace-through, invariant reasoning, dead-code detection. The eval that measures whether the LLM "understands" the code, complementing the vibe-coding "outcome-observation" work.

Adjacent to these: **General AgentBench** — a unified framework studying **test-time scaling behaviors** under sequential (iterative interaction) and parallel (multi-trajectory) scaling.

**Sources:**
- [VoltAgent — Awesome AI Agent Papers (2026 curated list)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv 2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/abs/2602.18998) `[primary]`
- [arXiv 2605.18747 — Code as Agent Harness](https://arxiv.org/pdf/2605.18747) `[primary]`
- [arXiv 2606.17799 — Position: Coding Benchmarks Are Misaligned with Agentic Software Engineering](https://arxiv.org/pdf/2606.17799) `[primary]`

### Why it matters to you

- **Job lens:** Frontier lab interviews (Anthropic Applied AI, OpenAI FDE, Google Gemini App Eng) increasingly ask **"which agent benchmark would you use to validate that?"** — Terminal-Bench + MLGym + CORE cover most reasonable answers. Add one 3-line summary of each to your interview cheat-sheet.
- **Startup lens:** The **"eval-first agent tooling"** wedge is more real than it was in May — the [Hugging Face breach](./01-big-lab-moves.md#2-hf-breach) is the tailwind, MLGym gives you the reference eval structure to build against. Judgment Labs ([May seed](../2026-05-13/)) is the anchor competitor; the wedge under it is domain-specific evals for regulated industries (health, finance, legal).
- **Insight:** The June 2026 position paper **"Coding Benchmarks Are Misaligned with Agentic Software Engineering"** (arXiv 2606.17799) is worth reading straight — it argues that SWE-bench-style benchmarks measure the wrong thing for agents. Frontier labs are already internalizing this critique in the design of Opus 5 evals; expect a broad reset of "the eval you cite" narratives in Q4.

---

## 4. Also worth a bookmark

- **arXiv 2605.18747 — "Code as Agent Harness"** — argues code as the primary agent interface (vs. structured JSON tool-call APIs). Aligns with Anthropic's Managed Agents / Sonnet 5 code-execution primitive from June.
- **arXiv 2504.19678 — "From LLM Reasoning to Autonomous AI Agents: A Comprehensive Review"** — for the panorama read; skim for the taxonomy figure.
- **arXiv 2512.10971 — "AI-Trader: Benchmarking Autonomous Agents in Real-Time Financial Markets"** — the domain-specific extension of the eval discipline, useful shape.

**Sources:**
- [VoltAgent — Awesome AI Agent Papers list](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv 2504.19678 — From LLM Reasoning to Autonomous AI Agents](https://arxiv.org/pdf/2504.19678) `[primary]`
- [arXiv 2512.10971 — AI-Trader](https://arxiv.org/pdf/2512.10971) `[primary]`
