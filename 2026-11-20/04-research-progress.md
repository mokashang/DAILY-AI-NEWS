# Research Progress — 2026-11-20

Three themes dominate this week's arXiv activity: **(1) "agents are systems, not models"** — the frame flip from model-level benchmarks to system-level trajectories, (2) **agents designing their own evals** (recursive evaluation is a serious live research question, not a sci-fi idea), (3) **theoretical limits on agent safety** — a strong impossibility-style result arguing that the tool-goal coupling makes certain safety properties undecidable. Supporting these: a new **Agent² RL-Bench** on cs.AI's Nov 20 listing for compact diagnostic benchmarking of agentic RL post-training, and a **graph-mediated agent systems survey** (Nov 4) that will shape taxonomy for 2027. Verify each paper's arXiv ID + submission date at the source before citing — the ID conventions can be noisy in secondary coverage.

Tags: `#arxiv #agents #eval #safety #rlhf #benchmarks`

---

## 1. "Agents Are Systems, Not Models" (arXiv 2610.01618) — the eval frame flip, with 18K+ trajectories released {#1-agents-are-systems}

**What it argues:** Agent evaluation should move from **"which model wins this benchmark"** to **"which system configuration — model + task info + reasoning scaffold + self-verification + time budget + backbone — wins this trajectory class."** The paper studies how each of these dimensions changes results, decoupling agent outcome from model choice.

**What they released:** The paper releases the benchmark and **more than 18,000 agent trajectories**, which is itself a significant open artifact for the eval research community.

**Why it's a bigger deal than it looks:**
- **Benchmark leaderboards for agents have been unreliable for 18 months** — different scaffolds give different numbers for the same model. This paper is the cleanest attempt yet to say so, and to **propose a trajectory-level metric** that generalizes.
- **It aligns with Mercor's $20B thesis** (eval + expert environments, [`02` §1](./02-new-emerging.md#1-mercor)) and with Cognition's Devin Bots product framing ([`02` §2](./02-new-emerging.md#2-devin-bots)): **systems are the unit, not models**.
- **Hiring implication:** anyone who writes "I benchmarked GPT-4 vs Claude-3" on a résumé now looks a generation behind "I benchmarked **system configurations** across 3 model backbones with a trajectory-level eval."

**Source:**
- [arXiv 2610.01618 — Agents Are Systems, Not Models: Rethinking Agentic Evaluation](https://arxiv.org/abs/2610.01618) `[primary]`

### Why it matters to you

- **Job lens:** Read the full paper this weekend if you have any eval / platform / applied-AI aspirations. **Pull one quote, one figure, and one methodological critique into your interview prep** — this is the eval paper that will come up in Anthropic / OpenAI / DeepMind screens in Q1 2027.
- **Startup lens:** **The trajectory-level eval** is the primitive to build around. Judgment Labs ($32M, May 13 edition), Promptfoo, Langfuse — the first one to productize **"system configuration search" as a service with a SOC2-compliant eval platform** wins the enterprise AI-eval category.
- **Insight:** This paper is the academic framing for what Google Orchestrator (Nov 18) just productized. **Academic → product lag was 6 months** on this one, which is faster than the usual 12–18. The next theoretically-interesting paper usually becomes a product in 2026-H2–2027-H1. Read fast, ship faster.

---

## 2. "EvalResearchBench" (arXiv 2610.04184) — can agents design their own evaluations? {#2-evalresearchbench}

**What it tests:** Whether agents (specifically Codex and Claude Code harness configurations) can **design evaluations** for other agents across **14 target benchmarks**.

**Why it matters:** The agentic-eval loop is the obvious next step after agentic coding — you want a system that can **look at your task, produce a test suite, and run it before letting a worker agent touch production**. EvalResearchBench is the first serious benchmark for that recursive capability.

**Headline finding (as framed in the paper):** Current agents can **partially** design their own evals — they succeed at structured benchmarks (coding tests with clear pass/fail) and **fail at open-ended tasks** (anything requiring judgment about what the eval should measure).

**What it implies:** The **human-eval authoring role is not automated yet**. Your eval-authoring skills (which are already high-signal per the Nov 14 edition) remain scarce for at least another 6–12 months.

**Source:**
- [arXiv 2610.04184 — EvalResearchBench: Can AI Agents Design Their Own Evaluations?](https://arxiv.org/html/2610.04184v1) `[primary]`

### Why it matters to you

- **Job lens:** **Learn to write evals.** This paper is implicit evidence that eval authoring is the **hardest-to-automate agent-adjacent skill** of 2026–2027. A résumé artifact that says "I wrote 50 evals for a coding agent across 10 task classes, with diff-distance scoring, and the agent-written evals had 23% lower agreement with ground truth than mine" is **directly interview-ready**.
- **Startup lens:** The gap between "agent designs test" and "agent designs good test" is where **eval-ops startups live**. If your product helps engineers write, validate, or compose evals, this paper is your citation footing.
- **Insight:** Watch for a **"self-improving agent via self-generated evals"** paper in Q1 2027 that closes this loop on structured tasks. That would be the nearest-term RSI-style result (recursive self-improvement) in a safe-to-ship domain.

---

## 3. "Pandora's Toolbox: Why Agent Safety Cannot Be Verified" (arXiv 2611.25325) — an impossibility-style theoretical result {#3-pandora-safety}

**What it argues:** Coupling **tools + goals + persistent state** in a single agent makes certain safety properties **undecidable** — i.e., there is no algorithm that can, in general, prove an agent will not reach an unsafe state via some tool composition.

**Why it matters:** This is a **theoretical ceiling** on what you can guarantee about agent systems — not an empirical result about today's models. If the proof holds, then **"we formally verified the agent is safe"** is **provably false as a claim for the general case**. You can still verify specific properties under specific tool sets, which is the practical fallback.

**Why it is not doom:** The proof constrains **general verification**, not **targeted verification**. Engineering responses are: **narrow the tool surface**, **compose agents with trusted-boundary wrappers**, **gate-call anything that touches the real world through HITL** (which is what LangChain 1.4.9 shipped from the Nov 14 edition).

**Why it is interview-relevant:** The question **"how would you make an agent safe to deploy?"** now has a **principled wrong answer** ("formal verification") and a **principled right answer** ("boundary design + HITL + narrow tool surface + observability on side-effects"). If asked in a frontier-lab or defense-adjacent interview, cite the boundary framing.

**Source:**
- [arXiv 2611.25325 — Pandora's Toolbox Or Why Agent Safety Cannot Be Verified](https://arxiv.org/abs/2611.25325) `[primary]` (verify ID at arXiv listing)

### Why it matters to you

- **Job lens:** **This is the single most-likely-to-come-up safety-paper citation of Q4 2026.** Expect it at Anthropic Alignment / RSP, OpenAI Preparedness, Google DeepMind Safety, every defense-adjacent role. Have a one-sentence summary ready: **"Pandora's Toolbox shows general agent-safety verification is undecidable when tools + goals + state couple — so engineering has to be boundary-first, not proof-first."**
- **Startup lens:** If your startup is in agent safety / observability / HITL tooling (Andromeda, Patronus, Credo, Arize), **this paper is your thesis** — ground your pitch in it. If you're pitching to defense / regulated verticals, pair it with a **"what we verify + what we gate"** matrix per customer.
- **Insight:** Impossibility results are **calibration tools, not excuses**. The engineering response is to **shrink the tool surface** until local verification works. **Expect MCP spec contributors to start carving "safe-subset" and "sensitive-subset" tool categories** in 2026-12 or Q1 2027 drafts.

---

## 4. Agent² RL-Bench (cs.AI Nov 20 listing) — compact diagnostic for agentic RL post-training {#4-agent2-rlbench}

**What it is:** A **compact diagnostic benchmark** for evaluating agentic RL post-training — the kind of thing you'd run to check whether an RLHF / RLAIF loop actually improved agent behavior at a trajectory level, not just at a next-token level.

**Why it's useful:** Agentic RL has been running mostly blind. Labs train against reward models and hope the trajectory-level outcomes track. **Agent² RL-Bench is a diagnostic — not a championship leaderboard — meant to catch regressions early in a training run.**

**Where it fits:** Combine with **"Agents Are Systems"** ([`04` §1](#1-agents-are-systems)) and **MRTPO per-token multi-reward RL** from the Nov 14 edition — you now have a stack of **(trajectory-level eval) + (per-token RL) + (compact diagnostic)** that is a credible modern agentic RL methodology.

**Source:**
- [arXiv cs.AI new listings — Nov 20, 2026](https://arxiv.org/list/cs.AI/new) `[primary]` (verify ID)

### Why it matters to you

- **Job lens:** MLE / Applied Research roles touching RL will cite benchmarks like this at onboarding. **Read the abstract this weekend, note the task mix, and have one concrete opinion on what's missing** (likely: tool-use-heavy trajectories are under-represented).
- **Startup lens:** If your startup does any post-training or fine-tuning, **run your pipelines on a diagnostic bench like this before each release**. Advertising "regression-caught by Agent² RL-Bench" in a changelog is a trust signal to technical customers.
- **Insight:** Expect **a whole subgenre of compact diagnostic benchmarks** to emerge over Q1 2027 — the eval-crowd is explicitly moving away from mega-benchmarks (SWE-bench style) toward **fast, focused, catch-the-regression** suites. This is the right shape of eval for internal CI, and the wrong shape for marketing announcements.

---

## 5. Graph-Mediated LLM Systems in the Agentic Era (arXiv 2611.05953, Nov 4) — a taxonomy survey worth 20 minutes {#5-graph-mediated-survey}

**What it is:** A **survey-style paper** covering **reasoning, knowledge, retrieval, execution, and coordination** in agent systems where **graphs are the mediator** (knowledge graphs, task graphs, agent-interaction graphs).

**Why read a survey:** Because the **vocabulary** that emerges from a survey becomes the shorthand of the field for the next 12 months. Graph-mediated patterns are the **natural follow-on to RAG → GraphRAG → graph-mediated multi-agent**, and the terminology from this paper will leak into product-marketing and job-postings within a quarter.

**What to pull from it:**
- **The five-axis taxonomy** (reasoning, knowledge, retrieval, execution, coordination).
- **The specific graph primitives** cited for each axis (worth skimming to recognize when you see them in a product pitch).
- **Open problems section** — if you want a dissertation topic or a founder wedge, this is a well-cited starting point.

**Source:**
- [arXiv 2611.05953 — Graph-Mediated LLM Systems in the Agentic Era](https://arxiv.org/abs/2611.05953) `[primary]`

### Why it matters to you

- **Job lens:** **Vocabulary = signal.** If you can say "my eval harness is graph-mediated across the coordination and retrieval axes, with a knowledge-graph verifier at the boundary" in an interview, you have **just demonstrated a quarter of literature fluency** that most candidates won't.
- **Startup lens:** **GraphRAG + graph-mediated multi-agent is a real wedge** that has not yet consolidated. Candidates: Memgraph, Neo4j, LlamaIndex GraphRAG, Microsoft GraphRAG. If you were building a multi-agent system and chose "flat message log" for state, read this and consider the alternative.
- **Insight:** **Graphs are the serialization format that bridges agent memory + knowledge + plans.** Expect "long-lived agent memory" products from Anthropic / OpenAI / Google in 2027 to be **graph-backed under the hood**, whatever the UX calls them.

---

## Reading plan if you only have 30 minutes

1. **(10 min)** `01-agents-are-systems` abstract + §3 methodology. This is the frame flip.
2. **(10 min)** `03-pandora-safety` abstract + one worked example in §4. This is your interview quote.
3. **(10 min)** Skim `05-graph-mediated-survey` taxonomy table. Save it as a bookmark.

If you have **60 minutes**, add `02-evalresearchbench` §5 (failure modes).

If you have **a weekend**, replay Anthropic's released Fable 5.2 trajectories through your own eval harness and compare your system-level metric to Anthropic's reported model-level metric. **That delta is your first blog post of 2027.**
