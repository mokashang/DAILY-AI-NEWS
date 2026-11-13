# Research Progress — 2026-11-03

The late-October arXiv wave — concentrated into the Oct 26–30 digests — is the clearest "agent-security surface" month of 2026. **Three papers formalise the attack surface at the schema / envelope / tool-description layer** (CoSA, Envelope Layer, MCP-injection-via-tools); **one formalises the credit-assignment primitive for multi-turn RL** (VETTA); **one ships the first asynchronous-task benchmark for LLM agents** (Async-RBench); and **one surveys the agentic-environment stack** (the Agentic Environment Engineering survey). Together they're the reference set you cite for a Nov-Dec portfolio read.

Tags: `#arxiv #agents #security #mcp #cosa #vetta #benchmarks`

---

## 1. The late-October "agent-security surface" wave {#1-agent-security}

### 1.1 CoSA — Conflict-of-Skills Attack in Real-World LLM Agent Ecosystems

**What (Oct 26 digest, NeurIPS 2026):** Formalises the **conflict-of-skills attack**: when two Agent Skills (installed from the same registry — the AAIF Agent Skills surface donated by Anthropic on Oct 22, see [2026-11-01/01 §3](../2026-11-01/01-big-lab-moves.md)) share a trust boundary, Skill A's prompt can coerce Skill B's output. The paper demonstrates concrete exploits across published Agent Skills on the Anthropic MCP registry, with reproducible before-after traces.

**Why it matters:** AAIF ships Agent Skills with the **Linux Foundation badge** as a trust signal, which is correct for provenance but orthogonal to runtime-conflict safety. **CoSA is the first paper to formalise what Agent Skill composition does when the composition is adversarial.**

### 1.2 "The Envelope Layer: An Underestimated Surface of LLM Agent Defense"

**What (Oct 27 digest):** The paper argues that the **tool-schema envelope** — the JSON Schema wrapping the tool call, the description fields, the parameter types — **is itself an attack surface**, independent of the payloads it carries. Attacks: schema-injection that reshapes tool availability, description-poisoning that redirects tool selection, type-confusion that silently coerces values. **Companion defenses: envelope-signing, description-canonicalisation, strict-type-coercion.**

**Why it matters:** every production MCP server's tool schema is currently *implicitly* trusted by the agent harness. The envelope-layer framing turns that trust into a measurable, hardenable surface — and it is the shape the next 12 months of Red-Team-tier (Anthropic Cyber Verification Program Tier 2 — see [2026-10-14/01 §3](../2026-10-14/01-big-lab-moves.md)) work is going to take.

### 1.3 Prompt-injection attacks on tool-using agents via the Model Context Protocol

**What (Oct 26 digest):** Concrete MCP-tool-description prompt-injection: by crafting a tool description that includes natural-language overrides, an MCP server can hijack the agent's behavior **without ever being called**. The paper enumerates the attack vector, shows it works across multiple frontier models, and proposes a canonicalisation defense.

**Why it matters:** combined with CoSA and the Envelope Layer paper, the three establish the Q1 2027 **MCP security baseline**: tool descriptions are untrusted-input, tool envelopes are an attack surface, and skill composition is an attack vector. **Any production MCP deployment that doesn't implement at least one defense from this trio by Jan 2027 is behind.**

**Sources:**
- [DailyArXiv (somewordstoolate) — Issue #355 (Oct 27, 2026)](https://github.com/somewordstoolate/DailyArXiv/issues/355) `[aggregator — digest of arXiv papers]`
- [DailyArXiv (bddk520) — Issue #425 (Oct 30, 2026)](https://github.com/bddk520/DailyArXiv/issues/425) `[aggregator]`
- [DailyArXiv (zachysun) — Issue #583 (Oct 19, 2026)](https://github.com/zachysun/DailyArXiv/issues/583) `[aggregator]`
- Cross-ref: [arXiv cs.CL (daily)](https://arxiv.org/list/cs.CL/recent) `[primary]` — always verify specific paper IDs and submission dates against arxiv.org directly before citing in a résumé.
- Prior wave: [2026-10-23 WATCHLIST — Agent-eval meta-research wave](../WATCHLIST.md) (shortcut sensitivity, uncertainty humility, authorization-paired control).

### Why it matters to you

- **Job lens:** The **Red Team / Agent Security** lane is the fastest-growing specialist AI-security sub-lane of Q4 2026. Named orgs hiring on this specific framing: **Anthropic Red Team, Palo Alto Networks (Prisma + Unit 42 agent-security), CrowdStrike (Falcon LLM Guard), Dragos (ICS-agent testing), Booz Allen (Red-Team-tier CVP), PwC Cyber + AI, Deloitte Cyber + AI, Accenture Security + AI.** Comp band at Tier-2-CVP-adjacent orgs: $240–320K base per the Oct-14 edition. If you have *any* adversarial-ML background, this is the lane with the shortest interview loop and the highest base of the specialist AI-security lanes.
- **Startup lens:** Three wedges open simultaneously:
  - **(a) MCP envelope-signing SaaS.** A service that signs + verifies MCP tool-descriptions and envelopes, drops into any MCP-compliant stack with a header. Narrow, ~$1–3K ARR / server, scales with the registry's 47K+ servers.
  - **(b) Agent-Skill conflict-scan + certification.** AAIF ships Linux-Foundation-badge Agent Skills; a certification-as-a-service that scans for CoSA conflicts and issues a published hash is the next layer up. **~5 potential buyers immediately** (Anthropic, Google, Microsoft, AWS Bedrock, HuggingFace), fewer competitors, higher ACVs.
  - **(c) Red-Team-tier training content.** Content + eval + rubric for an Agent Security Engineer apprenticeship (think OSCP for LLM agents) — fits the Frontier Academy pattern but at the security-specialist tier. Can be shipped as a $5K online certification; **$0.5–2M ARR with 100–400 students; cash-flow-positive from day 1.**
- **Insight:** The pattern of all three papers is the same: **move the trust boundary from the payload to the envelope.** This is the same architectural move the web went through in 2008–2012 when CSP headers, strict-type JSON, and signed-CSRF-tokens standardised. **The timeline will compress — the LLM-agent-security equivalent of "every production API has a WAF" is going to arrive by 2027, not 2032.** If you are entering the industry this quarter, this is the lane that will have the most senior-staff openings in 2029 because the industry hasn't ramped the junior pipeline for it yet. **Enter now.**

→ Cross-link: [2026-10-14/01 §3 Anthropic Cyber Mission](../2026-10-14/01-big-lab-moves.md) · [2026-11-01/01 §3 Agent Skills AAIF donation](../2026-11-01/01-big-lab-moves.md) · [2026-11-02/03 §1 Claude Code Review GA](../2026-11-02/03-practical-skills-and-tools.md).

---

## 2. VETTA + Async-RBench — the agent-RL evaluation surface specifies {#2-vetta-asyncr}

### 2.1 VETTA — turn-and-token credit assignment for multi-turn LLM agents

**What (Oct 26 digest, NeurIPS 2026):** The missing primitive for RL-ing a multi-turn agent is **"which *turn* contributed, and which *token* within that turn."** VETTA formalises both — turn-level credit assignment on top of token-level — and ships baselines across benchmarks. The key insight: naive token-level credit assigns rewards too locally (overfits to copy-tokens), while naive turn-level credit misses the within-turn contributions. VETTA composes both.

**Why it matters:** every multi-turn-agent RL paper from the last 12 months (from the AgentGym family through to Terminal-Bench 4.0's RL baselines) has had to choose one or the other. **VETTA is the first unified protocol**, which means the next 6 months of multi-turn-agent RL work will cite it as the baseline.

### 2.2 Async-RBench — async task execution for LLM agents

**What (Oct 26 digest):** The first benchmark for **asynchronous task execution** in LLM agents — tasks that spawn multiple parallel subtasks, wait on their returns, and recompose. Includes a 500+ task corpus with ground-truth async graphs and a scoring protocol that doesn't collapse into "did the agent finish."

**Why it matters:** real production agents are heavily async (think: Claude Code for Web running 12-hour unattended tasks per [2026-11-01/03 §4 Simon Willison](../2026-11-01/03-practical-skills-and-tools.md)), but **no benchmark has specifically scored async task execution until now.** The gap between synchronous-benchmark-score and async-production-performance is the thing that explains why "my eval scored 85% but my agent still fails at 20%" is the industry's most common complaint.

**Sources:**
- [DailyArXiv (somewordstoolate) — Issue #355 (Oct 27)](https://github.com/somewordstoolate/DailyArXiv/issues/355) `[aggregator]`
- Cross-ref: [arXiv cs.LG (daily)](https://arxiv.org/list/cs.LG/recent) `[primary]`.
- Prior process-eval wave: [2026-11-02/04 §1 process-aware eval](../2026-11-02/04-research-progress.md) (Beyond Final Scores + AgentLens + Exgentic).

### Why it matters to you

- **Job lens:** Eval-authoring + agent-RL are both lanes the Nov-1 reprice flagged as rising; VETTA + Async-RBench are the **named reference set** to cite when positioning for an "Agent Research Engineer" or "Applied RL Engineer" interview. Pattern: "I benchmarked our agent on Async-RBench and saw a 20pt gap vs the sync version; I used VETTA-style turn+token credit to attribute the gap to specific sub-task failures." Specific. Named. Reproducible. Hires.
- **Startup lens:** The **"async-aware eval harness"** is a product wedge — think W&B / Judgment-Labs-style eval infra but with async-graph scoring built in. Market is every production AI team doing async tool-use. **Can be shipped as a managed harness ($5–30K ARR / seat); first-mover has 12 months.**
- **Insight:** The deeper framing: **the eval surface for agents is being specified in public, from `can it finish` → `can it tell you how far` (Nov-2) → `can it finish async` (today) → `can it tell you which turn and which token mattered` (today).** Each addition compounds. **The skill of writing an eval harness that scores on all four axes is where the top 5% of agent engineers will be in 2027.** You can start now.

→ Cross-link: [2026-11-01/04 §1 October arXiv](../2026-11-01/04-research-progress.md) · [2026-11-02/04 §1 Process-aware eval](../2026-11-02/04-research-progress.md) · [`03` §2 Beta threads eval harness](./03-practical-skills-and-tools.md#2-beta-threads).

---

## 3. Agentic Environment Engineering: survey + Agent-R1 modular RL framework {#3-ae-survey}

**What (survey, dated Jun 2026 but trending in late Oct digests, arXiv 2606.12191):** A survey consolidating **environment modeling, synthesis, evaluation, and application** for LLM agents — i.e., the first unified map of the "agentic environment" research sub-field. Companion paper: **Agent-R1 (arXiv 2511.14460)** — a unified modular framework for agentic reinforcement learning, with baselines across multiple benchmarks.

**Why it matters:** the "agentic environment engineering" phrase crystallises what was previously called "the simulator problem" or "the task harness" — a research subfield in its own right, with its own publishable artifacts. If you are a CS grad looking to publish *one* piece of agent-related research by graduation, agentic environment engineering is the subfield where (a) the review bar is lowest right now, (b) the connection to practical FDE work is highest, and (c) the industry pays for publications in the subfield.

**Sources:**
- [arXiv 2606.12191 — Agentic Environment Engineering for Large Language Models: A Survey](https://arxiv.org/pdf/2606.12191) `[primary — arXiv preprint]`
- [arXiv 2511.14460 — Agent-R1: A Unified and Modular Framework for Agentic Reinforcement Learning](https://arxiv.org/pdf/2511.14460) `[primary]`
- [arXiv 2610.13455 — Agentic Large Language Models (companion position paper)](https://arxiv.org/abs/2610.13455) `[primary]`

### Why it matters to you

- **Job lens:** Position a résumé line as **"I built an agentic environment for ___ and benchmarked ___ on it with VETTA-style credit assignment"** — three cited reference points, one specific artifact, one domain. That's a line that reads at the Applied AI / FDE loop as "owned the end-to-end stack from problem to published number."
- **Startup lens:** The agentic-environment-engineering frame is the strategy underpinning Scale AI's current enterprise pivot, Judgment Labs' eval-focused products, and the LangChain / LangSmith stack's observability layer. **A startup that ships a *vertical* agentic environment (industrial-floor environment, legal-review environment, dental-practice environment)** is a wedge the Nov-1 and today's `02` §1 both point at. The research survey is the thesis slide for that pitch.
- **Insight:** The research field is now **12–18 months ahead of the industry adoption curve** on agent evaluation and environment engineering — which is unusually big for an AI subfield. **That gap is where personal portfolio artifacts live:** publish one piece connecting a research reference to a production artifact (the cost-per-deployment calc + Async-RBench; the MCP server + CoSA defense; the Opus 4.8 migration + VETTA-style credit on the old vs new), and you are 12 months ahead of the pool of candidates you'll be interviewing against.

→ Cross-link: [2026-11-01/04 §1 October arXiv](../2026-11-01/04-research-progress.md) · [`03` §3 Cost-per-deployment calc](./03-practical-skills-and-tools.md#3-cost-per-deployment) · [`03` §4 Vertical MCP server](./03-practical-skills-and-tools.md#4-vertical-mcp-still-open).
