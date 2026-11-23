# Research Progress — 2026-11-23

A quieter research week — the labs are in product-ship mode around the IPO + three-model drop — but **three arXiv papers in or near this window matter**: (1) **SlackBench (arXiv 2611.05512)**, a benchmark for agents on workplace chat + evolving-repo work, (2) **Terminal-Bench 2.1 Audit (arXiv 2611.08417)** showing ~30% of 2.0 tasks had issues, and (3) **Research-agent delivery (arXiv 2611.14364, Nov 10)** arguing standalone-task benchmarks overstate real-world agent reliability. The common thread: **benchmarks that measure single-task, stateless agent performance are now understood to overstate real-world capability**, and **"eval the eval" is becoming a research lane**. Also tracked: the (single-source) OpenAI claim that GPT-6.2 Astra crossed the "High" self-improvement threshold under the Preparedness Framework — the first disclosed capability-threshold crossing, pending confirmation.

Tags: `#arxiv #agents #evals #benchmarks #safety #preparedness`

---

## 1. SlackBench — agents on workplace chat + evolving repos (arXiv 2611.05512) {#1-slackbench}

**What it is:**
- Benchmark for agents operating on a combined **workplace-chat stream + evolving code-repo state** — the two primary surfaces of a real engineering job, together.
- Tested **33 frontier models + harnesses**.
- Best scores **~80%**; most agents **<66%**.

**Source:** [papers.cool — arXiv 2611.05512](https://papers.cool/arxiv/2611.05512) `[aggregator]`

### Why it matters to you

- **Job lens:** SlackBench **is a description of the FDE job**. An FDE literally works across customer Slack + an evolving codebase, and the benchmark shows frontier agents are at 66% on that composite task. **That gap is your job-security buffer** for the next 18 months. On interviews, the answer to "can an agent do your job?" is "on SlackBench, the best agent is at 80% on a simplified version of exactly that workflow — so 20% gap, which is where the FDE's judgment and customer context live."
- **Startup lens:** SlackBench is a **category-defining benchmark** that most AI-agent startups will race to score high on. If you're building agents for enterprise work, (a) run SlackBench, (b) publish your score, (c) name the delta vs frontier baseline. That's a quotable pitch-deck fact.
- **Insight:** **"Workplace chat + repo state" is the correct composite task for 2027-era agents.** Prior benchmarks (HumanEval, SWE-Bench, MMLU) all measure isolated capabilities. The composite is where real work lives; expect more benchmarks of this shape through Q1 2027.

→ Cross-link: [`02` §5 — agent memory as open category](./02-new-emerging.md#5-arms-dealers) · [`03` §4 — harness publish practice](./03-practical-skills-and-tools.md#4-terminal-bench-audit)

---

## 2. Terminal-Bench 2.1 Audit — ~30% of 2.0 tasks had issues (arXiv 2611.08417) {#2-terminal-bench-21}

**What it is:**
- Direct audit of **Terminal-Bench 2.0**, a top-5-cited agent benchmark in 2026.
- Found **issues in ~30% of tasks** (ambiguous specifications, broken graders, environment flakiness, under-specified pass criteria).
- Released **Terminal-Bench 2.1** with repairs.
- Explains the volatile "score moved" chatter whenever a new model is announced — part of the signal was eval error, not capability change.

**Source:** [papers.cool — arXiv 2611.08417](https://papers.cool/arxiv/2611.08417) `[aggregator]`

### Why it matters to you

- **Job lens:** This is **the paper to cite in an interview** when asked about model benchmarks. "I take Terminal-Bench scores with a +/- 30% confidence interval pre-audit; I use 2.1 scores with a tighter CI, and I trust my own 20-case eval above either." That sentence is the single highest-density FDE-credibility signal you can carry into a 2026 interview.
- **Startup lens:** **Eval-as-a-service** now has a data-point for category-size. If 30% of the leading open benchmark is broken, **every enterprise buyer with >$1M/yr in AI spend needs a trustworthy eval partner**. Build a paid service that runs reproducible evals weekly, versions them, and publishes score-vs-time charts — $500K–$2M ARR category.
- **Insight:** **Benchmark authority is up for grabs for ~90 days.** Terminal-Bench 2.1 is the correction; whoever ships the *next* audit (of SWE-Bench, LiveCodeBench, Agents' Last Exam, Vending-Bench 2) in this window gets outsized authority. If you're a researcher, this is the open lane.

→ Cross-link: [`03` §4 — Terminal-Bench 2.1 operational takeaway](./03-practical-skills-and-tools.md#4-terminal-bench-audit) · [`01` §3 — Neon's Terminal-Bench 4.1 performance](./01-big-lab-moves.md#3-gemini-4-neon)

---

## 3. Research-agent delivery — benchmarks overstate real-world reliability (arXiv 2611.14364, Nov 10) {#3-research-agent-delivery}

**What it is:**
- Direct challenge to the "research agent" claim category (Perplexity Deep Research, OpenAI Deep Research, Claude Research mode, Gemini Deep Research).
- Argues **standalone-task benchmark scores overstate real-world reliability** when the agent is embedded in an ongoing research project.
- Degradation modes: **context drift across sessions, source-citation decay, false claim of prior work completion, memory inconsistencies**.
- Confirms SlackBench's finding from a different angle: **agents are good at isolated tasks, not at ongoing work**.

**Source:** [papers.cool — arXiv 2611.14364](https://papers.cool/arxiv/2611.14364) `[aggregator]`

### Why it matters to you

- **Job lens:** This paper is **why "AI PhD student" jobs will stay open for humans through 2028**. Grad student research is explicitly multi-session, cross-context, slow-build work — the exact shape where agents fail hardest. If you're on the fence between finishing your PhD and quitting for a startup, this paper says the PhD is still worth more than it looks.
- **Startup lens:** **Agent-memory + cross-session continuity** is a real, open market category. This is the fourth distinct paper in six months arguing the degradation is real, structural, and not solved by longer context windows. Companies working here (MemGPT descendants, cursor-adjacent "project memory" tools) are under-funded relative to the problem size.
- **Insight:** **Don't trust single-task benchmark wins for your purchasing decisions.** If you're buying a research agent for your workflow, buy the one with the best **cross-session + evolving-project** performance on your own tasks, not the one with the highest Deep Research leaderboard number.

→ Cross-link: [`02` §5 — memory as an open category](./02-new-emerging.md#5-arms-dealers) · [`01` §1 — long-term lockup view](./01-big-lab-moves.md#1-ant-ipo)

---

## 4. GPT-6.2 Astra "High" self-improvement threshold claim (single-source) {#4-safety-threshold}

**What was reported (Nov 17–18, single-source):**
- How2Shout reported that **GPT-6.2 Astra is the first model to reach the "High" AI self-improvement threshold** under OpenAI's **Preparedness Framework**.
- If accurate, it is the **first time any frontier lab has declared a Preparedness capability threshold *crossed*** (vs approached).
- The "High" tier historically triggered **additional deployment controls** in OpenAI's own policy — expect tighter API-access gating or behavioral guardrails, or an explicit statement that the policy has been revised.

**Source:** [How2Shout — 20% cheaper, first "High" self-improvement](https://www.how2shout.com/ai/openai-gpt-6-2-astra-sol-release-pricing-benchmarks.html) `[aggregator, single-source]`

### Why it matters to you

- **Job lens:** **Policy / alignment / red-team hiring is about to pick up.** OpenAI, Anthropic, Google DeepMind safety teams all respond to Preparedness-shaped claims with hiring. If you have *any* safety / policy background (even an undergrad paper), target: OpenAI Preparedness team, Anthropic Alignment Science, DeepMind Frontier Safety, METR, Apollo Research. These teams move on 30–60 day loops when a capability claim like this lands.
- **Startup lens:** **Evaluator-build** (building private evals for Preparedness-shaped capabilities, sold to labs + governments) just got a validating data-point. METR, Apollo Research, and Scale AI's red-team unit are the public comps; a startup founded this week in this lane has ~12–18 months of clear-air.
- **Insight:** **Treat the claim as unverified until a second primary source confirms.** A single-source "we crossed a safety threshold" claim has clear motivated-reasoning risk (OpenAI benefits from the capability-aggression framing). Watch for (a) OpenAI's own Preparedness Framework publication of the assessment, (b) third-party replications (METR, Apollo), (c) Anthropic + Google responses within 30 days.

→ Cross-link: [`01` §2 — GPT-6.2 announcement](./01-big-lab-moves.md#2-gpt-62) · [`05` §4 — safety-lane careers](./05-career-and-startup.md#4-fde-comp)

---

## 5. Also-ran / to-verify this window

- **ServerBench** (benchmark for agents designing LLM serving systems) — reported Nov 4, aggregator-only. Verify at arXiv before citing.
- **TASC** (time-dependent safety in conversational assistants) — reported Nov 4, aggregator-only. Verify before citing.
- **Gemini Robotics 2.5 production data (from prior edition):** no new benchmark publications in window. Apptronik + Mercedes-Benz pilot numbers from Nov 11 remain the latest published.
- **OpenAI Lean-verified proofs (from 2026-11-14 edition, Oct 26):** no peer-review resolution in window. The ETH disproof and Yang–Mills claims remain open; Q1 2027 is the realistic resolution window.
- **Runway Praxis-1 / NVIDIA GR00T 2 (from 2026-11-14 edition):** no new production-deployment data in window.

**Why the thin week:** Lab research teams are in "ship product around the IPO + model drops" mode. Expect research backlog to clear Dec 1 → Dec 20 as product cycles close.
