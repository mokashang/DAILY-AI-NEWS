# Research Progress — 2026-11-12

Two threads worth tracking this month. **(1) November arXiv is dominated by agent-access-control, agent-self-evolution, and training-time-scaffolding** — a complement to Anthropic's own "closing the loop" S-1/A language. **(2) The pre-existing RSI literature (arXiv 2607.07663) is now the obvious citation ladder for anyone trying to understand the Nov 2 disclosure in technical terms.** If you are building a portfolio against frontier-lab Research or Alignment hiring, these two threads are the citation set to internalize this quarter.

Tags: `#arxiv #agents #rsi #access-control #self-evolution`

---

## 1. November arXiv — access-control, self-evolution, planner-free distillation, training-time scaffolding {#1-november-arxiv}

Four papers the Nov 11–12 agent-paper daily digests surfaced.

### (a) "Rethinking Access Control for AI Agents: Recent Advances and Open Challenges" — arXiv 2611.06764 (Nov 4)

Survey paper on **delegation, attenuation, and audit-trail problems** when LLM agents act on behalf of human principals. Why it matters: the Workplace-Suite launch (`01` §3) + the Enterprise security center (`01` §5) both land on the same bottleneck — **how do you prove the agent did exactly what the user authorized, and nothing beyond?** This paper frames the problem rigorously and lists the open sub-problems. For a portfolio engineer: this is the paper to cite when asked "what's the hard problem in agentic enterprise deployment?"

**Source:** [arXiv 2611.06764](https://arxiv.org/abs/2611.06764) `[primary]`

### (b) "AutoScaffold: AI-Guided Scaffolding for Reinforcement Learning of Language Models"

Training-time scaffold generation for RL-tuned LLMs — the "reasoning scaffolds" that used to be hand-designed are now auto-generated. Why it matters: lowers the floor on who can RL-tune a model for a vertical task; the pattern will show up in post-training recipes at labs through Q1 2027.

**Source:** Referenced via [arXiv digest 2026-11-12](https://github.com/duanyytop/agents-radar/issues/4253) `[aggregator]`

### (c) "Falsification-Gated Self-Evolution for LLM Agents"

Agent self-improvement with falsification gates — an agent proposes a change to its own prompt/policy and must falsify it against a test suite before accepting. Why it matters: the *measurable, auditable* analog of RSI at the agent (not model-weights) level. Same question Anthropic raised at the model level, re-asked at the agent-orchestration level. Nice portfolio hook: you can **build** this at the agent level today while the model-weights version is an alignment research problem.

**Source:** Referenced via [arXiv digest 2026-11-12](https://github.com/duanyytop/agents-radar/issues/4253) `[aggregator]`

### (d) "ReTrace: Distilling Tool-Using Agents into Planner-Free Workflows"

Distill a tool-using LLM agent into a **planner-free** execution trace — i.e., take the planner's decisions as training data, bake them into a smaller model, deploy without the planner. Economic translation: **cheap-worker inference wins at scale if you can distill the expensive planner upfront.** Direct implication for your router artifact (see [`03` §1](./03-practical-skills-and-tools.md#1-fable-52-default)) — Haiku 5.5 at `low` effort is the *target* of this distillation, and "distill-then-route" becomes a pattern.

**Source:** Referenced via [arXiv digest 2026-11-11](https://github.com/datnguyenquy94/news-radar/issues/1043) `[aggregator]`

### Why it matters to you

- **Portfolio:** All four papers can be turned into a **90-minute writeup each**. Four writeups → one GitHub repo (`/papers-nov-2026/`) → one Medium / Substack / personal-blog post. **Target: four writeups by end of November.** This is the fastest route to "reads frontier AI research" as a legible interview signal for Research-adjacent roles.
- **Interview talking point:** When asked "what did you read this month?", **(a)** is the right answer for Enterprise Solutions + Policy interviews; **(c)** is the right answer for Research / Alignment interviews; **(d)** is the right answer for Infra / Model-Serving interviews. Memorize one sentence per paper.

→ Cross-link: [`03` §1 router v3](./03-practical-skills-and-tools.md#1-fable-52-default) · [`05` §3 interview rehearsal](./05-career-and-startup.md#3-today-plan).

---

## 2. The recursive-self-improvement research background — arXiv 2607.07663 as the citation anchor for the Nov 2 S-1/A {#2-rsi-paper}

**Paper:** "Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops" ([arXiv 2607.07663](https://arxiv.org/pdf/2607.07663)) `[primary]`

**Why it matters right now:** Anthropic's Nov 2 S-1/A paragraph uses the term "recursive self-improvement" without defining it. If you cite the TechCrunch / DevX secondary coverage in an interview, you'll be answering with a journalist's definition. If you cite this paper, you'll be answering with the technical-community definition that underlies the RSP tripwire itself. The paper establishes:

- A **four-level taxonomy** of self-improvement: (1) bounded self-refinement within a context, (2) training-data curation at scale, (3) fine-tuning its own replacement, (4) autonomous research-loop improvement (model proposes architecture, model trains architecture, model evaluates architecture, repeat).
- **Measurable tripwires** at each level — specifically: doubling rate of codebase contribution; proportion of fine-tune recipes authored by model; eval-score improvement attributable to model-authored changes.
- An argument that **level (3) is where governance should bind** — not level (4), which is too late — because the *detection lag* grows with each level.

Anthropic's "~90% of September 2026 codebase contributions were Claude-authored" disclosure maps directly to this paper's **level (3) tripwire**.

### Why it matters to you

- **Interview-critical:** If you are interviewing at Anthropic Research, Alignment, or Policy in the next 90 days, read this paper's abstract + 4-level taxonomy section tonight. The lens it gives you lets you discuss the S-1/A disclosure in *technical* rather than *political* terms — a meaningful differentiator.
- **Portfolio:** This paper is the natural foundation for a **"mapping the four levels to current frontier labs"** blog post — level 1 is obvious (every assistant does it); level 2 is where OpenAI synthetic-data pipelines live; level 3 is where Anthropic's September disclosure lands; level 4 is the open horizon. 2-hour writeup; outsized interview return.

→ Cross-link: [`01` §2 S-1/A disclosure](./01-big-lab-moves.md#2-rsi-disclosure).

---

## 3. Research threads to watch (longer horizon)

- **Agent-welfare telemetry papers** — expect a late-November / December arXiv paper formalizing the "sustained cruelty" measurement problem introduced by Anthropic's Nov Usage Policy (prior edition).
- **Access-control extensions** — follow-ups to 2611.06764 will likely formalize **delegation chains** (user → agent → sub-agent → tool) with cryptographic attestation. Watch Jay-Yoon Lee, Daniel Fried, and the Berkeley AI Safety group as likely authors.
- **Inference-economics papers** — expect a paper this quarter quantifying the *actual* cost delta from Haiku 5.5 → Fable 5.2 workload substitution. The primary dataset will be the Anthropic post-IPO 10-Q. Write the eval harness to reproduce this *before* the filing drops.
- **Workplace-agent benchmarks** — a Meetings / Sheets / Whiteboards benchmark suite is the natural academic companion to Anthropic's product launch. If one doesn't exist by Jan 2027, propose it. Portfolio hook: author a V0 benchmark called `WORKBENCH-26` — 50 Workplace-Suite tasks with grounded truth — and open-source it.

---

## 4. One-paragraph research TL;DR for the week

Agent research in November has pivoted hard to the orchestration layer: **access control, falsification-gated self-evolution, planner-free distillation, RL scaffold generation**. All four are complements, not alternatives, to Anthropic's Nov 2 S-1/A framing of model-level recursive self-improvement. The 2607.07663 paper is the one technical reference you want next to the TechCrunch article when you discuss the IPO disclosure. Four 90-minute writeups on these papers get you a visible research-literate portfolio by Dec 1 — and they map 1:1 to Anthropic / OpenAI / Google Research hiring surfaces right now.
