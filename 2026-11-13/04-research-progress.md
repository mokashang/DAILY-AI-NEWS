# Research Progress — 2026-11-13

**The arXiv thread of the month: agents as a civic / institutional object, not a model property.** Four landmark November papers converge on the same question — once agents are deployed persistently, acting on your behalf and the firm's behalf, **who owns what they did, who grants them access, who governs them?** Plus one benchmark that formalizes the research-lifecycle eval and one that makes "investment research" a point-in-time testbed.

Tags: `#arxiv #agents #governance #access-control #memory #benchmarks`

---

## 1. Four arXiv landmarks (Nov 2-11) — persistent-agent governance crystallizes {#1-november-arxiv}

### (a) **arXiv 2611.03092 — "Avatar Intelligence: Amplifying Human Agency Through Persistent Personal Agents"** (Nov 2)

**The claim:** The field needs a formal paradigm — Avatar Intelligence — for **persistent personal agents** that represent an individual's goals, values, and constraints over time, not just for a session.

**Why it's a landmark:** This is the first paper to **put a stake in the ground naming the long-horizon memory + identity + delegation problem as a single paradigm**. Prior papers (Stanford's Generative Agents 2023, the Memory in the Age of AI Agents 2512.13564 from last edition) describe pieces; this one defines the scope.

**Sources:**
- [arXiv 2611.03092 — Avatar Intelligence: Amplifying Human Agency](https://arxiv.org/abs/2611.03092) `[primary]`

### (b) **arXiv 2611.06764 — "Rethinking Access Control for AI Agents: Recent Advances and Open Challenges"** (Nov 4)

**The claim:** A survey across **policy specification, identity + delegation, action + resource enforcement, and information flow control** for AI agents. Observes that the existing access-control literature (RBAC, ABAC, ReBAC) does not cleanly extend to agents because agents **interpret policies, not just check them**, and because **delegation chains are now LLM-mediated**.

**Why it's a landmark:** Agent access control is the compliance / security surface that **every public frontier lab now has to defend in regulatory filings**. The timing — Anthropic IPO roadshow week — is not accidental; expect this paper's taxonomy to appear verbatim in Q1 2027 10-Qs and audit reports.

**Sources:**
- [arXiv 2611.06764v1 — Rethinking Access Control for AI Agents](https://arxiv.org/abs/2611.06764) `[primary]`

### (c) **arXiv 2611.11645 — "A software infrastructure proposal for mathematical research with AI agents"** (Nov 8)

**The claim:** A self-hosted environment in which **a group of people and agents does daily mathematical research work together** — shared knowledge-base, versioned proof-state, cite-able agent outputs. Not a model; an **infrastructure thesis** for mixed-company (human + agent) research.

**Why it's a landmark:** First serious proposal for **"department-scale" (not just "project-scale") agent deployment** in a knowledge-production context. If adopted by even one math department, it becomes the de-facto template for law firms, policy shops, and R&D orgs.

**Sources:**
- [arXiv 2611.11645 — A software infrastructure proposal for mathematical research with AI agents](https://arxiv.org/abs/2611.11645) `[primary]`

### (d) **arXiv 2611.12941 — Agentic systems governance** (Nov 11; **accepted at NeurIPS 2026**)

**The claim:** Governance of agentic systems is urgent given the deployment speed. Proposes a **tiered governance stack** — per-agent policies, per-deployment audit, per-sector regulatory alignment — and argues the EU AI Act's 2026 timeline is **tracking 18 months behind empirical deployment reality**.

**Why it's a landmark:** First NeurIPS-accepted governance paper to center the frame on **the gap between policy-as-written and deployment-as-done**. Combined with (b) above, this is the two-paper read that gets you interview-ready for any **policy / responsible-AI / T&S** role in Q1 2027.

**Sources:**
- Listed on [arXiv cs.AI — new listing (Nov 11)](https://arxiv.org/list/cs.AI/new) `[primary listing]`

### Theme — the eval frontier moved from "can it finish" to "who owns what it did"

October's arXiv (2609.08589 Unreliable Progress Bar, 2606.07462 Act As a Real Researcher, 2608.13417 Beyond Final Scores, 2606.17016 TokenPilot) was about **trajectory accountability inside a single task**. November's is about **persistent identity, delegation, and governance across tasks and time**. The research surface is widening at exactly the pace the policy surface is — not an accident; the same labs fund both.

### Why it matters to you

- **Job lens:** For an AI-Safety / Trust-&-Safety / Policy-Engineering candidate, this is the **research-literate reading list for the next 12 interviews**. Cite (b) + (d) in any Anthropic Policy or OpenAI Preparedness conversation. Cite (a) if you're applying to the memory / personal-agent teams (Anthropic has one; OpenAI's "Memory" team has been expanding). Cite (c) if you're applying to any **vertical-R&D-agent** startup.
- **Startup lens:** **Access control is a horizontal moat.** A clean implementation of the (b) taxonomy — policy-language-parseable, delegation-chain-logged, resource-boundary-enforced — becomes a **sellable shim between your AI startup and every enterprise's existing IAM**. If your product has agents touching enterprise data, you now have 60 days to pre-empt the Q1 regulatory conversation.
- **Insight:** **"Avatar Intelligence" is a frame worth adopting in your public writing.** Whenever you write about personal AI agents, long-horizon memory, or delegation, use it. The research field tends to converge around the paper that names the paradigm first — and being an early citer buys you SEO + credibility at zero cost.

→ Cross-link: [2026-10-14/04 §1 October arXiv](../2026-10-14/04-research-progress.md#1-october-arxiv) · [2026-09-10/04 Memory in the Age of AI Agents](../2026-09-10/04-research-progress.md).

---

## 2. BuySideFlow (arXiv 2611.12966) — point-in-time investment research as the new agent testbed {#2-buysideflow}

**What it is (Nov 11):** A **point-in-time benchmark for LLM agents in investment research** — agents can only use data that was publicly available at the "ask" time. This blocks look-ahead bias and makes the benchmark replayable against historical market conditions.

**Why it matters:**
- **Point-in-time** is the research-quality fix the benchmark world has been missing. A model that "knows" Lehman collapsed is worthless as an investment-research agent benchmark; one that only knows what was known at a given date is actually a research tool.
- **Investment research** is a high-economic-value testbed with **real scoring metrics** (future returns, Sharpe, drawdown) — not a toy domain like trivia or LeetCode.
- **Expect direct comparisons** between BuySideFlow and the FDE Interviewer Agent benchmarks the Anthropic residency will likely produce. Both are vertical, both are time-bounded; the generalization story between them is a research paper waiting to happen.

**Sources:**
- Listed on [arXiv cs.AI — new listing (Nov 11)](https://arxiv.org/list/cs.AI/new) `[primary listing]`

### Why it matters to you

- **Job:** If you have any hedge-fund-adjacent interest, the **AI-for-finance** lane just got a new benchmark you can cite in applications (Point72 Cubist AI, Jane Street Research Eng, Citadel AI Research, Two Sigma Compass).
- **Startup:** **Point-in-time** as a benchmarking primitive is an **evaluation infrastructure wedge**. Build a SaaS that gives AI startups point-in-time snapshots of their own domain (web, codebase, pharma literature) — becomes the "evals in prod" tooling for every agent company.
- **Insight:** **High-economic-value verticals produce the best benchmarks.** Finance, biology, law, and (increasingly) cyber are where the next generation of eval work will live, because they have **ground-truth metrics**. Generic agent benchmarks have been plateauing for 6 months; vertical ones are where the frontier is moving.

→ Cross-link: [2026-10-14/04 §1 October arXiv — eval shift](../2026-10-14/04-research-progress.md#1-october-arxiv).

---

## 3. Also worth a read — three November sleeper papers {#3-sleepers}

### (a) **Agent security under multimodal social engineering**

Listed in the GitHub digest (Issue #450, Nov 9) — a benchmark for how agents handle adversarial multimodal prompts (image + text, voice + text). Not fully indexed yet; track for the full title. Relevance: **the air-gap-your-eval discipline from the Oct 14 edition ([`04` §2](../2026-10-14/04-research-progress.md#2-eval-airgap)) now has an empirical companion**.

### (b) **Honesty × confidentiality × task-completion trade-off**

Same digest — a study on how agents trade off three competing objectives. Confirms empirically the thesis of 2026-10 that **the eval frontier is tri-dimensional** (correctness + trajectory-honesty + resource-discipline).

### (c) **The AI Agent Index (arXiv 2502.01635)**

From February; keeps updating. Worth rechecking quarterly for the deployed-agent list.

**Sources:**
- [GitHub — DailyArXiv Issue #450 (Nov 9)](https://github.com/jyyang621/DailyArXiv/issues/450) `[aggregator]`
- [arXiv 2502.01635 — The AI Agent Index](https://arxiv.org/pdf/2502.01635) `[primary]`

---

Last updated 2026-11-13. Read the two-paper governance pair (b) + (d) tonight if you have 45 minutes — it's the highest-ROI research reading of Q4.
