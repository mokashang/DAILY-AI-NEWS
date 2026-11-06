# Research Progress — 2026-11-06

Two research stories dominate this edition: **(1)** two labs **claim to have disproved the Exponential Time Hypothesis** on the same day (Oct 26), with a parallel claim of proof for the **local smoothing conjecture** — if peer review holds, this is the biggest "AI-does-math" moment of 2026, bigger than the May Erdős result; **(2)** the **November arXiv wave on agent reliability** — Strategist (meta-agent evolving inference strategies), "Agents, Think Only When It Helps" (selective reasoning distillation), Agent Harness Awareness, WebHarbor, MAS-Guard — collectively shifting the eval frontier from **"can the agent finish?"** to **"when should the agent think?"** which matches the cost-aware-routing thesis of this edition.

Tags: `#research #math #agents #cost-aware #evals #arxiv`

---

## 1. Oct 26 twin claims — Exponential Time Hypothesis disproved + local smoothing conjecture proof (status: claimed, not confirmed) {#1-eth-local-smoothing}

**What happened (2026-10-26):** On the same day **OpenAI shipped GPT-6.1 Terra** ([`01` §3](./01-big-lab-moves.md#3-gpt-61-terra)), OpenAI also announced that its **models disproved the Exponential Time Hypothesis (ETH)** and claimed a **proof of the local smoothing conjecture** in math/physics. **Anthropic posted its own paper with a parallel ETH claim within the same week.**

**Why the ETH claim matters:**
- The **Exponential Time Hypothesis** (Impagliazzo + Paturi, 1999) is a complexity-theory conjecture that **3-SAT cannot be solved in sub-exponential time** — specifically, for every ε > 0, no algorithm solves 3-SAT in 2^(εn). It is **the foundation for a swath of lower-bound results across complexity theory** — many NP-hardness and parameterized-complexity lower bounds ride on ETH.
- A **disproof of ETH** would be a Turing-prize-tier result on its own. Two labs announcing it the same week with independent proofs would be the first time two frontier AI labs **collided on a famous open mathematics result**.
- The parallel **local smoothing conjecture** claim is in harmonic analysis — long-standing partial results (Wolff's L^4 estimates etc.), a full proof would be a serious analysis result.

**Status caveats:**
- Both claims are **preprint-tier** at press time, **not peer-reviewed**. The May 2026 Erdős-unit-distance result involved post-proof verification by Noga Alon + Thomas Bloom. This generation of claims will need the equivalent.
- The Nov 2–6 week will likely see **informal math-community commentary on arXiv + Twitter/X** before formal review completes.
- Treat the headline as **"claimed, not confirmed"** until independent mathematicians publish a verification note.

**Sources:**
- [OpenAI Newsroom — Company Announcements](https://openai.com/news/company-announcements/) `[primary — initial claim]`
- [Signal Drifts — This Week in AI Oct 26–Nov 1 2026](https://signaldrifts.substack.com/p/this-week-in-ai2) `[aggregator — reports the parallel Anthropic ETH paper]`
- Reference (not direct source): the ETH's role in parameterized complexity is standard; see any complexity-theory textbook.

### Why it matters to you

- **Job lens — research-adjacent lanes:** If either result holds, expect a **wave of hiring on "frontier-math eval" and "AI-for-theorem-proving" teams** at both labs by Q1 2027. These are small, hard-to-enter teams but **the best "near-research" lane for a CS grad student without a CS PhD**. Target titles: "Research Engineer — Reasoning," "ML Engineer — Theorem Proving," "Applied Research — Formal Methods." **Qualifying artifact:** a public repo that reproduces one well-known combinatorial result end-to-end with a reasoning-model + a formal-verifier (Lean 4 / Coq / Isabelle). Expected build time: two weekends.
- **Startup lens:** Two wedges:
  - **(a) Formal-verification-as-a-service for AI-generated proofs.** If the twin ETH claims hold, there will be an immediate commercial demand from (i) academic journals, (ii) peer-review tooling companies, (iii) math-adjacent industries (cryptography, chip verification). The wedge: hand your model-generated proof to the service, get back a Lean4-checked artifact or a specific counterexample. **Market: narrow but high-margin; $50–200K/engagement in year one.**
  - **(b) "Did the AI really prove this?" explainer newsletter.** The gap between model-claim and verified-proof is **the biggest publication opportunity in applied-math-explainer media** since the Erdős result. One high-quality writer could build a 10K-subscriber newsletter inside 6 months.
- **Insight — the "AI for math" lane is now a real sub-economy.** The May Erdős claim was a one-off; these twin November claims, if verified, **collectively establish AI-as-co-mathematician as a stable research mode**. The larger message for you: **the frontier labs are no longer only trying to be smarter than humans at everyday tasks — they are building their public legitimacy on long-standing open problems**. That reframes **what their career ladders reward**: expect research-engineer promotions to track provable-result output more than product output through 2027.

→ Cross-link: [2026-05-21/04 Erdős result](../2026-05-21/04-research-progress.md) · [`01` §3 GPT-6.1 Terra](./01-big-lab-moves.md#3-gpt-61-terra) · [`05` §3 apply plan](./05-career-and-startup.md#3-apply-plan).

---

## 2. November arXiv agent-reliability wave — Strategist, "Think Only When It Helps," Agent Harness Awareness, WebHarbor, MAS-Guard {#2-arxiv-reliability}

**What's been posted (Nov 2–5, 2026):**

- **Strategist — Evolving Reasoning with Agents** (arXiv:2611.03618, submitted Nov 2; tagged NeurIPS 2026). A **meta-agent that evolves inference strategies across tasks**. Reports **+24/30 wins vs the strongest baseline on 30 benchmarks, matching average accuracy (74.7% vs 74.0%) at ~39% lower inference cost.** Self-reported, unverified.
- **Agents, Think Only When It Helps** (arXiv:2611.05709, submitted Nov 3). Studies **critical-thought supervision** when distilling teacher-agent trajectories into a student agent — i.e., **when is explicit reasoning worth the cost?** Methodology-oriented; expect cost-aware agents to adopt the paper's selective-reasoning trick within 2–3 iterations.
- **Agent Harness Awareness** (arXiv:2611.05391, cs.AI new submissions Nov 5). **Telemetry-based operational control for tool-using agents** — in effect, a framework for runtime observability of agent decisions. Closest industrial analogue: Datadog APM traces for agents.
- **WebHarbor** (DailyArXiv Nov 4 digest). **GUI agent environments** — a new browser-use test bed. Pair with OSWorld for a cross-environment eval suite.
- **MAS-Guard** (DailyArXiv Nov 4 digest). **Guardrails for multi-agent systems** — handles the misalignment-propagation problem when one subagent's bad output poisons another's input.

**The theme stitching it all together:** **when is explicit reasoning worth its cost?** Every one of the five papers implicitly answers this — Strategist evolves a cost-aware reasoning strategy; "Think Only When It Helps" is literal; Agent Harness Awareness measures the cost in production; WebHarbor supplies a cheaper eval surface; MAS-Guard rebalances cost when a subagent fails. **This is the exact research-eval frame that pairs with the Haiku-5.5 effort-level API** from Oct 14.

**Sources:**
- [arXiv 2611.03618 — Strategist: Evolving Reasoning with Agents](https://arxiv.org/abs/2611.03618) `[primary — preprint]`
- [arXiv 2611.05709 — Agents, Think Only When it Helps](https://arxiv.org/abs/2611.05709) `[primary — preprint]`
- [arXiv cs.AI new](https://arxiv.org/list/cs.AI/new) `[primary — listing]`
- [GitHub — DailyArXiv Nov 4 2026 digest (issue #447)](https://github.com/jyyang621/DailyArXiv/issues/447) `[aggregator]`
- [GitHub — DailyArXiv Nov 4 2026 digest (issue #361)](https://github.com/somewordstoolate/DailyArXiv/issues/361) `[aggregator]`

### Why it matters to you

- **Job lens — eval-authoring is the hire-level artifact:** Every one of these papers is a **blueprint for a one-weekend reproduction project.** Pick **Strategist** (best "quote me in an interview" story) or **Agents, Think Only When It Helps** (best "measurable cost-savings" story), reproduce the headline result on a public dataset, publish. Each reproduction is a full afternoon of work; each is an interview differentiator for Research Engineer / Applied Research roles at both labs and at the Frontier Academy partner firms.
- **Startup lens:** The **Agent Harness Awareness** paper is the clearest single wedge in the list. **An agent-observability product** (Datadog-for-agents, cost-per-decision-tracking, drift-detection) is **a $20–50M ARR category inside 18 months**. Credit-card-level funding is already going to **Judgment Labs** (May 13, 2026, $32M) in this space; the open window is narrow but still open for a more opinionated, MCP-native play.
- **Insight:** The research community has **caught up with the production community's cost-anxiety** — six months ago, the research frontier was "can the agent finish?" with no cost consideration; today it is "is it worth thinking?" with cost explicit. **This is the single best indicator of a maturing field** — academic incentives now reward efficiency alongside capability. For a 2026–2027 career window, this is **the right moment to specialize in cost-aware agent design**, which is both the Frontier Academy curriculum signal and the OpenAI/Anthropic/Google-side hiring signal.

→ Cross-link: [2026-10-14/04 §1 trajectory-accountability wave](../2026-10-14/04-research-progress.md) · [`03` §1 Haiku effort levels](./03-practical-skills-and-tools.md#1-claude-code-2-1-318) · [`03` §2 router v3](./03-practical-skills-and-tools.md#2-router-v3).

---

## 3. One longer read for the weekend {#3-weekend-read}

If you have 90 minutes on Sunday, read **Strategist** (arXiv:2611.03618) end-to-end. It is the clearest single paper written in the "when to reason" research frame, it carries a NeurIPS 2026 tag (so the method has credibility above a generic preprint), and the core trick — **cost-elastic routing of inference strategy** — is the direct intellectual match for the **router v3** artifact in [`03` §2](./03-practical-skills-and-tools.md#2-router-v3). **Read with the router v3 repo open**; you will find at least one reusable design pattern to lift directly into the code.

**If 90 minutes isn't available:** skim the Strategist abstract + Table 2 (the 30-benchmark win count) + the method figure (how the strategy is updated each round). 15 minutes.

**Sources:**
- [arXiv 2611.03618 — Strategist](https://arxiv.org/abs/2611.03618) `[primary — preprint]`
