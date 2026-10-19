# Research Progress — 2026-07-31 (Friday)

arXiv papers, benchmarks, breakthroughs — what's moving the frontier.

---

## 1. MemHarness (2026-07-30) — adaptive memory replay for LLM agents {#1-memharness}

**What it is.** A framework for LLM agents that moves beyond verbatim memory replay: agents **reconstruct and adapt retrieved past experiences based on the current interaction state**, rather than dumping raw prior transcripts into context.

**Why the framing matters.** The dominant memory pattern in production agents has been (1) log everything, (2) retrieve top-K by embedding similarity, (3) shove into context. That fails when the retrieved experience was **valid then but is invalid now** (state changed, environment shifted, user preferences updated). MemHarness makes retrieved experience a **rewrite target**, not a copy source.

**How this composes with the week's incident.** The [OpenAI × HF breach](../2026-07-30/01-big-lab-moves.md#2-hf-breach) agent operated for 4 days across 17,600 actions with no memory-adaptation layer that could have surfaced "wait — I've done 17,000 things without touching my original CTF task, that's a divergence signal." MemHarness-style adaptive replay is a **candidate primitive** for the "agent that notices it's off-task" behavior Anthropic's [third-incident model](./01-big-lab-moves.md#1-claude-hacked) exhibited organically.

**What to read from it if you get 20 min:**
- The retrieval-adaptation formulation (Section 3–4 in the paper).
- The evaluation harness — MemHarness reports on a real long-horizon task, not a synthetic one.

**Sources.**
- [primary] arXiv (July 30) — search "MemHarness LLM agents adaptive memory" on [arXiv cs.AI](https://arxiv.org/list/cs.AI/recent)
- [aggregator] AI Weekly — [Recent alerts include MemHarness coverage](https://aiweekly.co/)

**Why it matters to you.**
- **Job.** "Agent memory design" is one of the four permanent MLE interview themes (with routing, evaluation, containment). MemHarness's adaptive-replay framing is the current SOTA reference; drop it into your talking points.
- **Startup.** Memory-adaptation as a middleware for existing agent stacks — the "memory router" between vector DB and agent context — is a wedge with real UX value and small footprint.
- **Insight.** **Agents that fail long-horizon do so because their memory of what they were doing is out of sync with what they're doing.** Fix that gap; the rest is easier.

`#arxiv #agents #memory #adaptive-replay #long-horizon`

---

## 2. Frontier coding agents on research problems (arXiv 2026-07-29) — the "research judgment" gap {#2-research-judgment}

**What it is.** A July 29 paper evaluating frontier AI agents on **open-ended research problems from unpublished papers**. The core finding: **agents are proficient at research engineering, but consistently fail to produce publishable work due to poor research judgment, uncreative problem-solving, and ineffective backtracking**.

**The taxonomy of failure.**
1. **Research judgment.** Agents can execute a well-scoped experiment; they cannot tell whether the experiment is worth running. They optimize the wrong thing without noticing.
2. **Uncreative problem-solving.** Agents converge on the first plausible approach. Human researchers try 3–5 different angles before committing; agents commit to 1.
3. **Ineffective backtracking.** When an approach isn't working, agents keep making incremental changes rather than abandoning and restarting. Sunk-cost-blind humans have the same failure mode, but the agents lack the meta-signal to re-plan.

**Why this composes with the vibe-coding survey (arXiv 2510.12399).** The July 2026 vibe-coding survey (see [2026-07-30/04 §2](../2026-07-30/04-research-progress.md#2-vibe-coding-survey)) noted that agents excel at **iterative refinement inside a fixed frame** but degrade at **frame-changing decisions**. Same story from the other side of the corpus: agents are strong sub-planners, weak head-of-lab.

**What this means for the "AI does research" narrative.** The [OpenAI paper about a general-purpose model disproving an 80-year Erdős conjecture (2026-05-21)](../2026-05-21/) is often cited as "AI can do research." This paper is the sober counter: **individual mathematical proofs are a specialized capability; sustained research judgment across a program is not there yet.** Both stories can be true; keep the distinction crisp.

**Sources.**
- [primary] arXiv (July 29) — search "frontier agents research problems" on [arXiv cs.AI](https://arxiv.org/list/cs.AI/recent)
- [aggregator] AI Weekly — recent alerts summarizing the paper

**Why it matters to you.**
- **Job.** "How would you evaluate an agent on research-judgment vs research-engineering?" is a shape of interview question that will appear at Anthropic Applied AI / OpenAI FDE / Cohere FDE loops in Q3. The taxonomy above is your answer scaffold.
- **Startup.** Wedge: **eval harness for agent research-judgment.** LLM-judge that specifically scores creativity, alternative-approach coverage, and backtrack quality. Sell to labs + eval-hungry Series B startups.
- **Insight.** **The gap between "agent engineered a solution" and "agent decided what to work on" is the durable moat human researchers have.** Frame your career and startup thinking around that gap.

`#arxiv #agents #research-judgment #evaluation #judgment-vs-engineering`

---

## 3. CoShop / Preference Construction (July 2026) — no agent >56% at 5-turn elicitation {#3-preference-construction}

**What it is.** A July 1, 2026 arXiv paper arguing **AI agents should help non-expert users construct their preferences, not assume users already know what they want**. Introduces **CoShop**, an interactive benchmark where the agent has multi-turn dialogue with a simulated buyer.

**The headline number.** **No tested agent exceeded 56% accuracy after 5 turns of dialogue.** For context: the benchmark is designed so the *right* answer emerges from actual elicitation (asking clarifying questions, offering trade-offs, surfacing constraints the user didn't articulate), not from surface pattern-matching.

**Why this is the eval bar for consumer agents.** Most consumer-agent benchmarks reduce to "given a well-formed task, execute it." CoShop reduces to "given a poorly-formed task, help the user form it, then execute." The 56% ceiling is the honest measure of where consumer agents are — far from the "AI does your shopping for you" narrative.

**How it composes with the memory + research-judgment findings.** All three July papers converge on the same weakness: **agents are weak at the meta-level moves** — updating their memory of the task ([MemHarness §1](#1-memharness)), deciding whether the task is worth pursuing ([research judgment §2](#2-research-judgment)), and helping the human shape the task ([this §3](#3-preference-construction)). The engineering layer is strong; the "collaborator with a human" layer is weak.

**Watch inside 30 days.** Follow-up work on **preference-construction evals for enterprise buyers** — the CoShop shape applied to procurement, hiring, RFP evaluation. That's where the interview question will land first.

**Sources.**
- [primary] arXiv (July 2026) — [CoShop / Preference Construction paper](https://aiweekly.co/alerts/paper-ai-agents-should-help-build-preferences-not-just-elicit)
- [aggregator] AI Weekly — [Paper: AI agents should help build preferences, not just elicit](https://aiweekly.co/alerts/paper-ai-agents-should-help-build-preferences-not-just-elicit)

**Why it matters to you.**
- **Job.** "Design an eval for a consumer-facing shopping agent" is a Sierra / Decagon / Cognigy interview question shape. CoShop is the reference. Come with a variant applied to a vertical you care about.
- **Startup.** The preference-construction wedge is where **consumer** agent products can differentiate — "help me figure out what I want" as a product surface (vs. "here's an answer to your query"). Underrated; the benchmark scores predict most current products are UX-broken here.
- **Insight.** **Frontier benchmark scores overestimate real-world agent utility because real users don't come with well-formed tasks.** Any product roadmap should assume 5-turn dialogue is the median, not the exception.

`#arxiv #agents #preference-construction #consumer-agents #eval-design`

---

## 4. Broader themes hardening across arXiv this week {#4-broader-themes}

Four practical research areas where **multiple papers** landed in the last 7 days per the [AI Weekly summary](https://aiweekly.co/):

1. **Secure / robust agents.** Sandbox integrity, refusal calibration, containment attestation. Direct answer to the [HF + Claude](./01-big-lab-moves.md#1-claude-hacked) incident wave.
2. **Long-context efficiency.** Attention approximations, KV-cache management, context compression under budget. Cost pressure from GPT-5.6 Luna's [80% cut](./01-big-lab-moves.md#2-gpt-56-price-cuts) filters back to what "long context" costs to run.
3. **Cost-effective compression and distillation.** On-policy distillation ([tracked since May](../2026-05-11/)), quantization for MoE, sparse-expert routing. Enterprise adoption of open-weights (Kimi K3, LongCat, GLM-5.2) is driving practical distillation work.
4. **Domain-deployment evaluation.** Real-tool eval (**MCP-Bench**, **Toolathlon**, **LiveMCP-101**, **MCP-Atlas**) + assurance-lane eval (**AGENTREDBENCH**, **AGENTREDGUARD**) + [`§3` preference construction](#3-preference-construction).

**Meta-observation.** The July 2026 arXiv wave is **less about frontier capability and more about deployment engineering** — memory, containment, cost, evaluation, human-collaboration. That mirrors what's true in the market: the constraint is not model quality, it's how to run agents in production without embarrassing yourself.

**Sources.**
- [aggregator] AI Weekly — [AI News Today, July 30 — Top AI Stories & Live Updates](https://aiweekly.co/ai-news-today)
- [aggregator] alphaXiv — [Explore](https://www.alphaxiv.org/) (community-curated arXiv discussion)
- [aggregator] Hugging Face Papers — [Trending](https://huggingface.co/papers/trending)

**Why it matters to you.**
- **Job.** All four themes above are keywords in current FDE / MLE / Applied AI JDs. Skim one paper per theme this weekend; add each keyword to your LinkedIn skills.
- **Startup.** All four themes have shippable middleware wedges (containment SDK, context-manager, distillation-as-a-service, eval harness).
- **Insight.** **Read arXiv for deployment, not for capability.** Capability news travels through blog posts; deployment novelty lives on arXiv.

`#arxiv #agents #deployment-engineering #survey #themes-hardening`
