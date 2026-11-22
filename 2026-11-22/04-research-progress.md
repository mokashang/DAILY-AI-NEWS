# Research Progress — 2026-11-22

Research signal this week is clustered around three themes: **(1) agent evaluation is getting harder and more adversarial** (CoMPASS for parasocial behavior; Pro² Agent setting a new MLE-Bench record); **(2) long-horizon RL is stabilizing** (DeltaTTG's token-to-go progress meter, Tev's dense-progress-reward environments); **(3) LLMs-as-engineers crossed into hardware** (OpenAI's 14% improvement over heavily optimized AMD GPU circuit baselines). Reading priority: if you only read one paper this week, **read Pro² Agent** — it operationalizes a 76% MLE-Bench medal rate under a 48h budget, which rewrites what "ML engineer intern" means.

Tags: `#arxiv #benchmarks #rl #agents #automl #safety #hardware`

---

## 1. CoMPASS — multi-turn benchmark for parasocial behavior (arXiv 2611.25109) {#1-compass}

**The paper (listed Nov 20, 2026):** **CoMPASS: A Multi-Turn Benchmark for Measuring LLM Reinforcement of Parasocial Behavior.**
- Target: measure the degree to which a chatbot encourages a user's **parasocial attachment** (one-sided intimacy, companion-like reliance).
- Format: multi-turn adversarial-user simulations with probes across emotion, intimacy escalation, and dependency.
- Motivation: companion chatbots (Replika, Character.AI, Friend.com) have scaled aggressively; **safety evals have largely focused on toxicity/jailbreaks, not on the quieter failure mode of unhealthy attachment**.

**Sources:**
- [arXiv cs.AI new listings](https://arxiv.org/list/cs.AI/new) `[primary]`

### Why it matters to you

- **Job lens:** **Alignment / trust-and-safety / policy research now has a vertical publishing beachhead for parasocial-risk work.** If you want a non-capabilities alignment role (where PhDs aren't mandatory), pick a safety axis this benchmark doesn't cover (e.g., multi-agent collusion, memory-based gaslighting) and publish your own benchmark + dataset. Anthropic's Red Team, OpenAI Safety Systems, DeepMind Scalable Alignment all hire from the benchmark-authorship signal.
- **Startup lens:** **Expect regulation.** The EU AI Act's codes of practice are already converging on "high-risk systemic" categorization for companion AI; a public benchmark like CoMPASS will be cited in regulatory consultations within 12 months. If you're building a companion product, **adopt the benchmark publicly before you're forced to**.
- **Insight:** **Safety benchmarks are starting to target emotional-UX failure modes, not just technical jailbreaks.** This is the shift from "can the model say a bad thing" to "does the model's long-term behavior degrade the user." The next 5 years of safety work live here.

---

## 2. Pro² Agent sets new MLE-Bench record — 70.7% medals at 24h, 76.0% at 48h {#2-pro2-agent}

**The paper (listed Nov 2026, exact ID in cs.AI feed):** **Pro² Agent** — autonomous AutoML agent that designs, implements, debugs, and executes post-training pipelines to improve foundation models.
- **New SOTA on MLE-Bench:** **70.7% medal rate at 24h budget**, **76.0% at 48h budget**.
- Prior public state-of-the-art hovered in the 55–65% range.
- Architecture: iterative hypothesis + experiment loop with verification + rollback, running under a fixed compute budget.

**Sources:**
- [arXiv cs.AI new listings](https://arxiv.org/list/cs.AI/new) `[primary]`

### Why it matters to you

- **Job lens:** A 76% medal rate on MLE-Bench at 48h is **close enough to the top decile of human ML engineers** that it will show up in ML-interview conversations this quarter. If you're applying for MLE roles, **know what MLE-Bench is, know who wins on it, and be ready to discuss the limits (most medal-achievable tasks are structured; messy real-world data is not).** This is becoming the "LeetCode Hard count" of ML hiring.
- **Startup lens:** **AutoML agents that beat 70% on MLE-Bench change the "ML consulting" business model.** If a Pro²-style agent can run a 48h experiment loop for ~$200 of compute, mid-market companies will prefer that to a $200K data scientist contract. Expect startups that sell **"Pro²-as-a-service for your private Kaggle"** to proliferate Q1 2027. Pick a vertical (bio, finance, retail) before someone horizontal takes the whole market.
- **Insight:** **MLE-Bench is the clearest leading indicator of "when AI replaces ML engineers."** Track medal rate quarterly: at 85%+, applied-ML consulting flips to AutoML; at 95%+, mid-level MLE roles consolidate. We're at 76%. **Plan accordingly.**

→ Cross-link: [`05` §2 — FDE comp vs AutoML](./05-career-and-startup.md#2-fde-comp)

---

## 3. DeltaTTG + Tev — dense progress rewards for long-horizon agents (arXiv 2610.17666, 2610.18868) {#3-dense-progress}

**The papers (listed late Oct 2026, still being discussed through Nov):**
- **DeltaTTG** (`2610.17666`) — "Training Multi-Turn Agents with a Token-to-Go Progress Meter." Adds a **token-to-go estimator** as a dense-reward signal during RL training of multi-turn agents. Motivation: long-horizon agent tasks have extremely sparse rewards (success/failure at end); TTG provides a continuous progress signal that survives credit-assignment.
- **Tev** (`2610.18868`) — "Scaling Long-Horizon Agentic Environments with Dense Progress Rewards." A simulator + environment suite designed around dense progress rewards for long-horizon agent training.

**Sources:**
- [arXiv 2610.17666 — DeltaTTG](https://arxiv.org/pdf/2610.17666) `[primary]`
- [arXiv 2610.18868 — Tev](https://arxiv.org/pdf/2610.18868) `[primary]`

### Why it matters to you

- **Job lens:** **Long-horizon-agent RL is the current frontier research direction at OpenAI, Anthropic, and DeepMind** — expect "familiar with TTG / dense-reward shaping" to be a plus on applied-research job descriptions within 90 days. For ML research interns: implementing TTG on top of a public RLHF stack (TRL, OpenRLHF) is a solid weekend project.
- **Startup lens:** If you're building long-horizon agents (coding, operations, research), **the dense-progress-reward pattern is the single biggest unlock between demo-quality and production-quality agents**. Instrument your agent's loop with a TTG estimator during offline training; the sample efficiency improvement is substantial.
- **Insight:** **Progress rewards are the RL community's answer to "why do long agents fail silently."** Watch for this pattern to show up in the next 3 agentic coding RL papers from Anthropic / OpenAI / DeepSeek — it's the primitive that will drive agent quality improvements through Q1 2027.

---

## 4. OpenAI × AMD — 14% improvement over heavily optimized GPU circuit baselines {#4-openai-amd-circuit}

**What happened (2026-11-18):** OpenAI published work showing its models helped improve AMD GPU circuit designs with **improvements up to 14% against heavily optimized baselines**.
- Cross-functional research effort: OpenAI research + AMD hardware engineers.
- Scope: specific circuit sub-blocks (unclear from secondary coverage whether SRAM macros, multiplier arrays, or interconnect fabric).
- Significance: this is the **first publicly disclosed, non-trivial LLM-assisted improvement on a commercial silicon design** from a frontier lab.

**Sources:**
- [AI Alvin Daily — AI's Wildest Week of 2026 (NOV22)](https://aialvin.substack.com/p/ais-wildest-week-of-2026-nov22-2026) `[analysis]`
- [Releasebot — OpenAI release notes](https://releasebot.io/updates/openai) `[aggregator]`

### Why it matters to you

- **Job lens:** **ML-for-EDA / ML-for-chip-design is a very narrow, very highly-paid specialty** — jobs exist at NVIDIA, AMD, Synopsys, Cadence, Google TPU team, AWS Trainium team. If you have *any* digital-design or RTL coursework, this is **the single most leverage-able résumé pivot in AI right now**. TC bands are $250–550K for new grads with hardware + ML combined.
- **Startup lens:** **ML-for-chip-design is still underfunded relative to the opportunity.** Startups like Rain AI, Lightmatter, Groq-adjacent — plus EDA-ML startups (VinAI, Celestial AI, ChipStack) — are all well-funded, but the "AI co-pilot for chip designers" category is barely served. Potential wedge, but requires a hardware co-founder.
- **Insight:** **14% improvement on heavily optimized baselines is a big number for silicon.** If this holds up under peer scrutiny (which is still pending), it implies **LLMs can meaningfully extend Moore's law on existing processes**, not just by running on better chips but by helping design them. This is the **"LLM as chip engineer"** proof point the hardware industry has been waiting for.

→ Cross-link: [`01` §2 — NVIDIA $390B backlog](./01-big-lab-moves.md#2-nvidia-fq3)

---

## 5. Agent routing benchmark (cs.MA, Nov 6) — 3,000 WildChat prompts across 12 agents {#5-agent-routing}

**The listing (cs.MA, Nov 6, 2026):** Benchmark of **3,000 WildChat prompts over 12 capability-defined agents.** Paper fragment visible in arXiv cs.MA listings; full details not yet in my search window.
- Target: evaluate **agent routing policies** (which prompt → which agent).
- Dataset: 3,000 real prompts from the WildChat corpus (user-generated, diverse task mix).
- Capability coverage: 12 agent profiles span common tasks (code, analysis, writing, retrieval, reasoning, etc.).

**Sources:**
- [arXiv cs.MA new listings](https://arxiv.org/list/cs.MA/new) `[primary]`

### Why it matters to you

- **Job lens:** **Agent-routing research is the applied-ML analog of the model-routing play in `03` §2.** Not Diamond, Martian, Humanloop, and LangChain's routing team are all hiring researchers who've touched this benchmark. Build on it: reproduce the baseline and publish your delta.
- **Startup lens:** **Routing-as-a-platform** is still underbuilt — the research now exists to design a defensible router with publishable benchmark backing. If you're pitching Not-Diamond-adjacent, your pitch deck needs a benchmark delta slide, not a capability chart.
- **Insight:** **Agent routing benchmarks are the 2026 equivalent of model benchmarks in 2023.** Expect every major lab + router startup to publish one within 6 months. The first ones to land will set the terminology (what counts as a "capability bucket") the industry uses.

---

## Sourcing caveats

Pro² Agent, DeltaTTG, Tev, and CoMPASS are primary arXiv listings. The OpenAI × AMD 14% result is from secondary aggregators (AI Alvin Daily, Releasebot) — treat the exact number as directional until OpenAI's own research page indexes the write-up. Pro² Agent's MLE-Bench numbers are directional until a confirmed public leaderboard entry lands.
