# Research Progress — 2026-06-07

The frontier of *research* this week is **agents doing meta-work on themselves and the field consolidating its own vocabulary.** Two papers worth knowing today: **Agent² RL-Bench** asks whether LLM agents can engineer their own RL post-training (the operational form of the Karpathy-Anthropic mandate), and a **unified review of externalization in LLM agents** (memory + skills + protocols + harness engineering) tries to be the field's textbook for the 2026 design space. The parallel macro trend: **benchmarks moved from mock environments to real MCP servers** ([MCP-Atlas, Tool Decathlon](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)) — which is exactly the eval bar the production crowd needed.

Tags: `#arxiv #benchmarks #agentic-rl #post-training #memory #protocols #harness #verification`

---

## 1. Agent² RL-Bench — can LLM agents engineer agentic RL post-training? {#1-agent2-rlbench}

**The paper:** [arXiv:2604.10547 — Agent² RL-Bench: Can LLM Agents Engineer Agentic RL Post-Training?](https://arxiv.org/abs/2604.10547)

**What it does:** Sets up a benchmark where an LLM agent is asked to **design, run, and iterate on the RL post-training pipeline of *another* agent**. The agent under test acts as a meta-engineer: it has to pick reward shapes, decide curricula, run training jobs, evaluate results, and iterate — all in a single closed loop, with the *quality of the downstream agent* as the score.

**Why this paper is the one to read this week:**

- It's the **research-bench analog of the Karpathy hire**. Anthropic's new pre-training-acceleration team is operationalizing exactly this — using a model to drive the loop that produces the next model. Agent² RL-Bench is the public, comparable measurement that lets you track whether "AI building AI" is actually improving.
- It separates **planning failures** from **execution failures** in a way prior agentic-RL benchmarks didn't. You can score a frontier model on "could it *design* the right post-training run?" separately from "could it *get the cluster job to actually run?*". That distinction is what makes the bench useful as a hiring signal — it tells you where the next year's investment goes (planning is closer to solved than execution).

**Related must-read companion:**

- **[arXiv:2604.08224 — Externalization in LLM Agents: A Unified Review of Memory, Skills, Protocols and Harness Engineering](https://arxiv.org/pdf/2604.08224)** — the closest thing to a 2026 textbook for how to think about agent design. Four named primitives — **memory**, **skills**, **protocols**, **harness** — and the paper argues this is the *complete* taxonomy of what gets externalized from the model itself. It's the academic version of the five-layer Claude Code stack in [`03` §1](./03-practical-skills-and-tools.md#1-five-layer-stack); read the two side-by-side this weekend.

### Why it matters to you

- **Job lens:** **"Agent² RL-Bench"** is going to be a verbal interview pop quiz within 60 days — at Anthropic, OpenAI, and any well-staffed RL team. Knowing **(a)** the planning-vs-execution decomposition, **(b)** what the benchmark actually scores, and **(c)** why it's the operational form of self-improvement is the bar you want to clear for a 90-second response. Spend 45 minutes on the paper tonight; this is the highest-ROI 45 minutes you can spend on research prep this week.
- **Startup lens:** If the *agents-engineering-agents* loop is real, the **picks-and-shovels wedges** are: (1) **eval harnesses** that score post-training runs cheaply enough to use in a loop; (2) **reward-shape libraries** (one of the bench's pain points); (3) **cluster-orchestration MCP servers** that let an agent submit and monitor training jobs. None of these are LLM-frontier work — they're plain software, with a frontier-research customer. Easy founder bet for a CS grad.
- **Insight:** The pattern across all three layers this week is **the same primitive showing up under different names**: in research (Agent² RL-Bench), in benchmarks ([MCP-Atlas](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)), in security ([Glasswing/Mythos verification](./01-big-lab-moves.md#3-glasswing)), in practice ([dual-model sanitiser](../2026-05-20/05-career-and-startup.md#3-safety-project)). The primitive is **verifying an agent's output cheaply enough to use in a loop.** Learn this primitive deeply (cost of verification, false-positive/negative trade-offs, where the verifier needs to be a different model than the generator) — it's the single concept that recurs in every research thread on this list.

→ Cross-link: [2026-05-22/04 §1 real-tool benchmarks (MCP-Atlas, Toolathlon)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) · [2026-05-22/01 §3 Karpathy as the talent face of this thesis](../2026-05-22/01-big-lab-moves.md#3-karpathy) · [`03` §1 five-layer Claude Code stack as the practitioner mirror](./03-practical-skills-and-tools.md#1-five-layer-stack).

---

## 2. Benchmark Test-Time Scaling of General LLM Agents — measuring the right thing {#2-tts}

**The paper:** [arXiv:2602.18998 — Benchmark Test-Time Scaling of General LLM Agents](https://arxiv.org/html/2602.18998v1)

**What it does:** Investigates **how LLM agents scale when given more test-time compute** — specifically a *general* agent (one expected to compose search, code, tool use, MCP APIs across diverse realistic tasks). It surfaces an important new measurement: **"does this agent benefit from doubling its inference budget?"** is not the same question as "**is this agent's underlying model better?**"

**Why it's interesting now:** The agent stacks of 2026 (Claude Code, Antigravity, Codex CLI) all expose **test-time compute knobs** — extended thinking budgets, parallel subagents, retry/refine loops. This paper is the empirical evidence on **which agents actually convert added compute into added accuracy**, vs. which ones plateau or even *degrade* with more steps. That distinction is the most important practical knob you have.

### Why it matters to you

- **Job lens:** "Does more compute help here?" is one of the most-asked design-review questions inside any AI eng org. Be the candidate who can *cite* the paper for the empirical answer (it varies by task class and by harness — there's no one number). Knowing this paper marks you as having read past the headline.
- **Startup lens:** If TTS benefits are task-class-dependent, the **policy router** (cheap or expensive per step?) is exactly what differentiates a $40/customer/month agent product from a $4/customer/month one. Cite this paper in any deck for an agent-product startup.
- **Insight:** The whole field's obsession with "**bigger model**" or "**more thinking**" misses the third axis: **better harness around the same model**. Test-time scaling research is starting to formalize *which knob to turn when*, and it's the empirical answer that converts the five-layer Claude Code stack from a craft into an engineering discipline.

---

## 3. The macro research arc to track for the rest of 2026 {#3-macro-arc}

A one-page mental map for the rest of the quarter — three threads, in order of "most likely to define hiring vocabulary by year-end":

1. **Real-tool / production-grade benchmarks.** MCP-Atlas + Tool Decathlon already moved the bar from mocks to actual systems ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)). Watch for follow-on benchmarks that **cost-weight** the score (i.e., dock points for an expensive solution). The first one of those drops the hammer on "more compute is always better."
2. **AI-improving-AI loops.** Agent² RL-Bench is the publishable surface of what Karpathy's team is staffing inside Anthropic ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)). Watch for the first **paper authored by a model + a researcher pair** that's explicitly attributed at submission time — and for whoever publishes the first **AI-discovered improvement on a transformer-architecture choice** (the public, undeniable proof point).
3. **Verification as the bottleneck.** Across security ([Glasswing](./01-big-lab-moves.md#3-glasswing)), agents ([dual-model sanitisers](../2026-05-20/05-career-and-startup.md#3-safety-project)), and post-training (Agent² RL-Bench), the recurring constraint is **how cheaply can we *check* the output?** The next year's most-valuable research papers will be on **cheap, reliable verifiers** — possibly small specialized models, possibly formal-methods hybrids. Track this thread aggressively; it's the most undervalued specialty for a grad student to lean into.

### Why it matters to you

- **Job lens:** Each of these three arcs maps to a hireable specialty: **(1)** *Eval Engineer* (cost-aware benchmarking), **(2)** *Research Engineer for AI-Accelerated R&D* (Karpathy-team-shaped roles), **(3)** *Verification / Eval Researcher* (the AI-safety adjacent lane that's *also* the commercial-security lane). All three are open at Anthropic; #1 and #3 are also open at OpenAI and DeepMind.
- **Startup lens:** Build for the lane the labs *don't* want to build internally. Cheap verifiers and per-step cost-aware benchmark runners are too narrow for a lab to staff a team on, but exactly the kind of thing that becomes a $20M ARR niche tooling business.
- **Insight:** The three arcs above describe **one underlying shift**: in 2025 the bottleneck was *capability*; in 2026 the bottleneck is *verification, evaluation, and cost-of-iteration*. **Pick the side of the field you want to live on.** Capability is harder to break into, increasingly compute-bound, and already crowded. Verification/eval/cost is *under-staffed*, has clear commercial pull, and accepts grad-student-shaped CVs.

---

## 4. Quick mentions (not deep-dives, but on the radar)

- **OdysseyBench** ([arXiv:2508.09124](https://arxiv.org/pdf/2508.09124)) — evaluating LLM agents on **long-horizon complex office application workflows**. Lurking in the background as the "boring enterprise" benchmark; if it gets adopted by enterprise AI vendors as the reference test, this becomes the equivalent of MMLU for the office-work category. Worth a 10-min skim.
- **A Survey on Evaluation of LLM-based Agents** ([arXiv:2503.16416v2](https://arxiv.org/html/2503.16416v2)) — useful taxonomy of the agent-eval landscape across reasoning, planning, tool-use, multi-agent coordination. Skim only if you're writing a section in your portfolio that needs a citable taxonomy.
- **AgentBench** ([arXiv:2308.03688](https://arxiv.org/pdf/2308.03688)) — older, still cited; useful only as a historical reference now that MCP-Atlas / Tool Decathlon have moved past it.
