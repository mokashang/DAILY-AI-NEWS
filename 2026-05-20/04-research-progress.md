# Research Progress — 2026-05-20

The most important "paper" this week isn't on arXiv — it's **Google's empirical threat report on indirect prompt injection (IPI) in the wild**, which both (a) quantifies a real, growing attack surface and (b) lands on the *same* defensive architecture as last week's TrajAD verifier work. The field's three hot lanes — evaluation, verification, and now **safety-under-autonomy** — are converging on one primitive: **a small cheap model supervising a large privileged one.**

Tags: `#research #prompt-injection #ipi #agent-safety #dual-model #multi-agent #dytopo #arxiv #convergence`

---

## 1. Indirect Prompt Injection in the Wild — Google's Empirical Report {#1-ipi-wild}

**What it is:** Google published a measurement study of **indirect prompt injection (IPI)** — hidden instructions embedded in ordinary web content that an AI agent ingests and then executes. This is the first large-scale *empirical* (not theoretical) characterization of the attack as it actually appears on the live web.

**Key findings:**
- **+32% relative increase** in the "malicious" category between **November 2025 and February 2026** — the attack is industrializing, not hypothetical
- **Real payloads found in the wild include fully-specified PayPal transaction instructions** hidden invisibly in standard HTML, targeting agents with payment capability
- Sophistication is still *low* (per SecurityWeek) — meaning the window to harden defenses *before* attackers get good is open right now
- Threat actors are themselves **automating with agentic AI**, driving the cost of attack down

**The recommended defense — and why it matters for research framing:** Google recommends **dual-model verification**: a small, isolated "sanitiser" model fetches the page, strips hidden formatting, isolates executable commands, and passes only plain text to the capable reasoning agent. (Implementation in [`03` §3](./03-practical-skills-and-tools.md#3-dual-model).)

**Sources:**
- [Google Security blog — AI threats in the wild: prompt injections on the web](https://blog.google/security/prompt-injections-web/) `[primary]`
- [Artificial Intelligence News — Google warns malicious web pages poisoning AI agents](https://www.artificialintelligence-news.com/news/google-warns-malicious-web-pages-poisoning-ai-agents/) `[secondary]`
- [SecurityWeek — attacks increasing, sophistication still low](https://www.securityweek.com/malicious-ai-prompt-injection-attacks-increasing-but-sophistication-still-low-google/) `[secondary]`
- [Decrypt — malicious pages hijacking agents, going after PayPal](https://decrypt.co/365677/google-prompt-injection-ai-agents-paypal-enterprise) `[secondary]`
- [Unit 42 (Palo Alto) — web-based IPI observed in the wild](https://unit42.paloaltonetworks.com/ai-agent-prompt-injection/) `[secondary]`
- [Help Net Security — indirect prompt injection taking hold in the wild](https://www.helpnetsecurity.com/2026/04/24/indirect-prompt-injection-in-the-wild/) `[secondary]`

### Why it matters to you

- **Research lens:** This is the empirical anchor that turns "agent safety" from a values-conversation into a **measurable engineering problem** (32% relative growth, dated, with real payloads). When you cite agent-safety work in interviews, lead with *this measurement*, not abstractions — concrete numbers signal you read the primary report.
- **Career lens:** "Agent safety / IPI defense" is moving from research to **table-stakes production requirement** the same week Google + Anthropic both ship autonomous web-browsing agents. Every FDE deploying a customer-facing agent now has to answer "how do you stop indirect prompt injection?" **If you can implement and explain the dual-model sanitiser, you can answer the single most likely 2026 agent-deployment objection.** That's a direct hireability multiplier for Solutions/FDE roles.
- **Insight:** The attack is industrializing *because* agents are gaining real-world privileges (payments, email, calendars). The IPI growth curve is a **leading indicator of agent capability deployment** — it only grows when agents are worth attacking. Track the next quarter's number: if it keeps climbing, autonomous agents are being deployed faster than the press suggests.

---

## 2. The Convergence Thesis — One Primitive, Three Research Lanes {#2-convergence}

The week's signal isn't any single paper; it's that **three independent research/industry threads landed on the same architecture**:

| Thread | Source | The shared primitive |
|---|---|---|
| **Trajectory verification** | TrajAD ([2026-05-19/04 §3](../2026-05-19/04-research-progress.md#3-trajad)) | Haiku-size verifier monitors Opus-size agent, rolls back on error |
| **Per-claim evaluation** | JADE ([2026-05-19/04 §2](../2026-05-19/04-research-progress.md#2-jade)) | decompose + check each claim against a ground-truth source |
| **Safety under autonomy** | Google IPI report (§1) | small isolated sanitiser guards the privileged reasoning agent |

**The unifying sentence to remember:** *"A cheap, narrow, low-privilege model supervising an expensive, broad, high-privilege one is becoming the default safety/reliability primitive of 2026."* Verification, evaluation, and injection-defense are three faces of the same shape. Use this in an interview — it demonstrates you've synthesized 3 weeks of reading into one principle, which is what senior engineers do.

**Why it's now economically obvious:** the supervisory leg was always architecturally attractive; what changed is **price**. Gemini 3.5 Flash at $1.50/1M (and Haiku) makes running a guard model in front of every privileged action cost ~nothing. **The architecture was waiting on the inference price to drop — and yesterday it did.**

---

## 3. New arXiv this week — multi-agent coordination & adversarial robustness {#3-arxiv}

Refreshed from Hugging Face trending + the VoltAgent curated set:

- **DyTopo** — dynamically *rewires* agent-to-agent connections each reasoning round via semantic matching, instead of a fixed communication topology. (Carried from 5/17; still trending — the topology-is-dynamic thesis is hardening.)
- **RuleSmith** — automated game balancing via multi-agent LLM self-play + Bayesian optimization. Interesting beyond games: a template for **self-play + optimization loops** in any rule-governed environment (pricing, scheduling, allocation).
- **CommCP** — uses **conformal prediction** to filter noisy inter-agent messages for multi-robot coordination. Notable because it brings a *statistically principled* uncertainty bound to message-passing — the kind of rigor multi-agent work has lacked.
- **Low-latency adversarial-interaction / fraud-detection layers for LLM agents** — an emerging applied lane: real-time detection of adversarial interaction patterns against agents (the runtime-defense complement to Google's IPI study).

**Sources:**
- [Hugging Face — Trending Papers](https://huggingface.co/papers/trending) `[primary]`
- [VoltAgent — awesome-ai-agent-papers (2026)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[curated]`
- [arXiv cs.AI — current](https://arxiv.org/list/cs.AI/current) `[primary]`

### Why it matters to you

- **Research lens:** The center of gravity is **multi-agent robustness** — DyTopo (topology), CommCP (message filtering), and the fraud-detection layer all attack the same problem: *multi-agent systems are fragile to noise and adversaries*. This is the natural next frontier after the eval/verification stack from last week.
- **Career lens:** Pick **one** of these to reproduce as a weekend artifact. CommCP (conformal prediction over agent messages) is the highest-signal for an MLE-track resume because conformal prediction is a genuine statistical skill that screens well. RuleSmith (self-play + Bayesian opt) is the most fun and most demo-able.
- **Insight:** Conformal prediction showing up in agent coordination (CommCP) is an early sign that **classical statistical-ML rigor is being re-imported into the LLM-agent stack**. The 2023–2025 "just prompt it" era is giving way to "bound it, verify it, supervise it." That's good news if your background includes real ML/stats — those skills are becoming *more* relevant in agent work, not less.

---

## 4. This week's combined research thesis {#4-thesis}

```
        2026 agent stack — the supervisory layer hardens
        ──────────────────────────────────────────────
   [evaluation]     [verification]    [safety/injection]
      JADE             TrajAD          Google IPI report
        │                │                   │
        └──────── same primitive ────────────┘
        cheap narrow guard model  ⟶  expensive broad agent
                         │
        enabled by ⟶  Gemini 3.5 Flash @ $1.50/1M (5/19)
                         │
        multi-agent robustness ⟶ DyTopo · CommCP · fraud-layer
```

**One sentence:** *"In 2026, you don't trust an agent — you supervise it with a cheaper one, and the supervisor finally got cheap enough to always be on."*

→ Cross-link: [`03` §3 build the dual-model sanitiser](./03-practical-skills-and-tools.md#3-dual-model) · [`05` §3 the agent-safety portfolio project](./05-career-and-startup.md#3-safety-project).
