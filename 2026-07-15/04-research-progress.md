# Research Progress — 2026-07-15

Three threads to know. **First: agentic negotiation gets its first published benchmark** — AgenticPay, 110+ tasks that put buyer + seller LLM agents on opposite sides of a real payment protocol, measuring "does the agent recognize when to walk away." **Second: the eval-as-a-first-class-skill wave continues to widen** — Terminal-bench + MCP-Atlas / MCP-Bench + real-tool discovery + the July arXiv survey (2507.21504) now catalogs 44 agent benchmarks, and the collective take is that **cost-per-successful-completion is the fifth eval axis** industry is standardizing on. **Third: long-horizon agent survival** — governed-context (Self-GC) + anytime-valid certificates continue to gain traction as the primitive for keeping an agent alive across sessions without either forgetting or hallucinating. If you have 45 minutes to read one thing today, read AgenticPay's task design + the 2507.21504 survey's Table 2.

Tags: `#arxiv #agents #benchmarks #negotiation #eval #multi-agent #long-horizon #cost`

---

## 1. AgenticPay — the first real buyer↔seller negotiation benchmark {#1-agenticpay}

**What:** **AgenticPay** introduces a **110+ task benchmark** to evaluate how multi-agent LLM systems handle buyer-seller negotiation over an actual payment protocol. Two agents (buyer + seller) are given asymmetric information + budgets + policies; the environment forces them to negotiate price, terms, cancellation, refunds — and, critically, **to recognize when the other side is offering below-cost dumping, or when to walk away entirely**.

- **Why it's different from prior negotiation benchmarks:** those measured "did the two agents agree?" AgenticPay measures **did they agree at a *rational* price given their policies?** Walking away is a valid strategy and is rewarded.
- **Baseline results (early paper):** frontier models score **higher on cooperation than on cost discipline** — they hit "yes to a deal" much more often than they hit "the deal should not have happened at all."
- **Adjacent work in the same cluster:** ROMA (recursive open meta-agent, breaks long-horizon tasks into subtree parallel work), MAS-Orchestra (RL-tuned function-call orchestration), Terminal-bench (CLI real-tool eval).

**Sources:**
- [VoltAgent — awesome-ai-agent-papers 2026 catalog (AgenticPay listed)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv 2507.21504 — Evaluation and Benchmarking of LLM Agents: A Survey (44 benchmarks)](https://arxiv.org/pdf/2507.21504) `[primary]`

### Why it matters to you

- **Job lens:** Any Applied Solutions / FDE role touching **procurement, contract-negotiation, supply-chain, or CX** now has a legible benchmark to reference in interviews: *"we would evaluate an agent's negotiation quality against AgenticPay before deploying against real customers."* That single sentence signals **eval-first practitioner** — an increasingly hard-to-fake trait.
- **Startup lens:** The "walk-away is a valid strategy" formulation is the same eval frame you should adopt for **any agent that has budget authority** (procurement, ad-buying, spend-approvals, refunds). If your agent can't accurately recognize when *not* to act, its unit economics will collapse as soon as it hits an adversary. Bake this into your eval harness *before* first customer.
- **Insight:** The industry's eval bar keeps moving from "does the agent complete a task" to "does the agent complete the *right* tasks." AgenticPay is the latest turn of that ratchet. Expect the same reframing to hit fraud-review agents, code-review agents, and clinical-decision-support agents within 6 months.

---

## 2. The eval-benchmark survey (arXiv 2507.21504) — 44 benchmarks, one shared taxonomy {#2-eval-survey}

**What:** *Evaluation and Benchmarking of LLM Agents: A Survey* (arXiv **2507.21504**, July 2026) catalogues **44 published agent benchmarks** across four families and proposes a shared taxonomy that lines up neatly with what practitioners are already de facto standardizing on.

- **Four families:**
  1. **General-agent capability** (SWE-Bench, GAIA, WebArena, τ-Bench, HAL).
  2. **Real-tool discovery + use** (MCP-Atlas, MCP-Bench, Toolathlon, ComplexMCP, Terminal-bench).
  3. **Long-horizon + memory** (AgentSims, MemGPT bench, LongJudgeBench).
  4. **Domain-specific** (SciAgentArena, LemmaBench, AgenticPay, biomedical/legal/finance).
- **The fifth axis emerging across all four families:** **cost per successful completion**. Not "did it succeed" but "how many tokens / how many tool calls / how many wall-clock minutes."
- **Pairs with:** [Efficient Benchmarking of AI Agents (arXiv 2603.23749)](https://arxiv.org/abs/2603.23749) — cuts eval cost 44–70% by filtering to mid-difficulty tasks.

**Sources:**
- [arXiv 2507.21504 — Evaluation and Benchmarking of LLM Agents: A Survey](https://arxiv.org/pdf/2507.21504) `[primary]`
- [arXiv 2603.23749 — Efficient Benchmarking of AI Agents](https://arxiv.org/abs/2603.23749) `[primary]`
- [arXiv 2506.11102 — Evolutionary Perspectives on Evaluation of LLM-Based Agents](https://arxiv.org/pdf/2506.11102) `[primary]`
- [arXiv 2506.10402 — Harnessing the Collective Intelligence of AI Agents in the Wild](https://arxiv.org/pdf/2606.10402) `[primary]`

### Why it matters to you

- **Job lens:** The 44-benchmark table is the **single best interview-prep artifact of Q3 2026** for any eval-adjacent role. You do not need to memorize 44 benchmarks; you need to know the **four families**, the **fifth axis**, and **one benchmark in each family cold** (SWE-Bench + MCP-Atlas + LongJudgeBench + AgenticPay is a defensible quartet). Interviewer asks "how would you evaluate this agent?" → answer maps to family + axis in 45 seconds.
- **Startup lens:** If you're building any agent product, **the survey's family taxonomy is your eval scorecard.** Pick two benchmarks from each family + track cost-per-success as the KPI. You'll ship faster because you'll catch regressions earlier and be able to *demonstrate* them to buyers with a common vocabulary.
- **Insight:** The **cost-per-success** axis is the eval world catching up to what the [Uber/Lindy/Karp token-billing revolt (2026-07-02 §5)](../2026-07-02/01-big-lab-moves.md#5-token-attack) taught the market: quality alone isn't enough — quality per dollar is. Expect model leaderboards to start publishing "$/pass@1" alongside pass@1 by year-end.

---

## 3. Long-horizon agent survival — governed context + anytime-valid certificates {#3-long-horizon}

**What:** The **Self-Governed Context (Self-GC) + Anytime-Valid Certificates** cluster from late Q2 is now the emerging default primitive for keeping an agent alive across long sessions without collapsing into either amnesia or hallucination.

- **Self-GC:** the agent maintains a *policy* over its own context window — what to keep, what to summarize, what to evict, what to move into long-term memory. Formalizes the "context-window custodian" role that many practitioner-scale agents (Cursor, Claude Code, ChatGPT Work) have been ad-hoc implementing.
- **Anytime-valid certificates:** a running proof (in the CS-theory sense) that the agent's outputs stay consistent with its stated policies + evidence base at every step. Enables **early rollback** if a claim's certificate weakens — the *provable* version of the TrajAD rollback primitive [2026-05-19/04 §3](../2026-05-19/04-research-progress.md).
- **Pairs with:** [MemReread (2026-05-18)](../2026-05-18/04-research-progress.md) memory-guided rereading, [Storage Is Not Memory (2026-05-18)](../2026-05-18/04-research-progress.md), [SENTINEL failure-driven RL (2026-07-06)](../2026-07-06/04-research-progress.md).

**Sources:**
- [VoltAgent — awesome-ai-agent-papers 2026 catalog](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`
- [arXiv 2506.11102 — Evolutionary Perspectives](https://arxiv.org/pdf/2506.11102) `[primary]`
- [arXiv 2602.05073 — Uncertainty Quantification in LLM Agents](https://arxiv.org/pdf/2602.05073) `[primary]`

### Why it matters to you

- **Job lens:** Anthropic's [Claude Cowork mobile push (2026-07-11)](../2026-07-11/) is a Self-GC problem in production ("keep the agent alive across a laptop-closed / phone-off boundary"). Reference *Self-GC* by name in any Anthropic Applied / Cowork / Claude Code interview and you signal "I've read the relevant July research, not the May research."
- **Startup lens:** Anytime-valid certificates are the emerging *verifiability* layer of a Self-GC pipeline. If your product involves an agent that persists for hours to days (research assistant, sales SDR, code-migration tool), **the difference between users trusting you and not is whether your agent can produce a certificate the user can eyeball.** Ship it early; it's easier to add certificates now than to retrofit them later.
- **Insight:** The frontier is quietly converging on **"agents that stay alive"** as the highest-leverage research problem. Karpathy → Anthropic pre-training team + Self-GC + AgenticPay-style "walk away when wrong" evals all point at the same shift: **not smarter agents, but agents that behave sensibly over hours and days.** The next 12 months of leaderboards will be won on longevity, not IQ.

---

## Also worth a skim

- **Terminal-bench 2.1** — Grok 4.5 posted **83.3%** at ~15,954 output tokens vs Opus 4.8's ~67,020 on SWE-Bench Pro (a **4.2× token gap**). Cost-per-success as a headline metric, exactly as §2 predicts.
- **QUEST → Fully synthetic → live-transfer research agents** (arXiv 2605.24218) — training on synthetic research tasks that transfer to live benchmarks. Relevant to anyone shipping a research-agent product.
- **AutoResearchBench** — 3M+ arXiv corpus for multi-hop synthesis evaluation. The default eval for Deep Research-style products.
