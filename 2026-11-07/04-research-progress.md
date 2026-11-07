# Research Progress — 2026-11-07

Two threads to track this period. First, **November arXiv on agent reliability** adds a new axis — **verifying that an agent's reasoning is its own**, not borrowed from another agent in the swarm or a cached prompt — and a new mechanism for long-horizon stability (**adversarial speculative reasoning**). Second, **DeepMind's CodeMender-descendant agents broke exploit-material from legacy 1024-bit RSA**, the first at-scale agent-swarm cryptanalysis result; the UK NCSC separately warned of AI-powered ransomware on critical infrastructure within 24 months.

Tags: `#arxiv #agents #speculative-decoding #verification #cryptography #cyber #research`

---

## 1. November arXiv — long-horizon reasoning + verification + multi-agent reliability {#1-nov-arxiv}

### 1a. Adversarial Speculative Reasoning (arXiv 2611.05345, Nov 3)

**Claim:** In long-horizon agents using **speculative decoding**, the **numerical noise from the draft-vs-verifier mismatch grows within verification windows** and starts shifting critical reasoning after roughly **30 steps**. The paper proposes a training objective for the draft model that makes critical reasoning paths **adversarially robust** to the noise, extending durable reasoning length by ~2–3×.

**Why it's interesting:** Speculative decoding is now standard on the serving stack of every major lab (it's a 2–4× throughput gain) but the paper is the first to formalize a **degradation mechanism** tied to it in **agent** workloads specifically. The implication is that **two agents in a multi-agent swarm that look identically prompted can diverge in reasoning just because of inference-stack scheduling** — i.e., the swarm is less deterministic than most eval setups assume.

**Source:** [arXiv 2611.05345 — Adversarial Speculative Reasoning Improves Long Horizon Agents](https://arxiv.org/abs/2611.05345) `[primary]`

### 1b. Verified Dafny Postcondition ≠ Independent Reasoning (arXiv 2611.07073, NeurIPS 2026 Workshop)

**Claim:** When multiple LLM agents are asked to formalize the same problem in Dafny (a verification-friendly language), a **verified postcondition** proves a mathematical property of the final formula — **but does not prove that the agents arrived at the result independently**. In practice, agents tend to converge on near-identical reasoning paths because of shared prompt priors + training data overlap, which means **verification can rubber-stamp group-think**.

**Why it's interesting:** Formal verification is increasingly treated as "the gold-standard safety layer" above LLM reasoning. This paper shows that **verification layered over a multi-agent LLM system does not guarantee what you want it to guarantee** — specifically, it doesn't guarantee reasoning diversity. **The eval design implication**: your multi-agent eval needs an **independence probe** (do agents actually explore different paths?) in addition to a correctness probe.

**Source:** Referenced in the Nov cs.AI arXiv listings — see the [cs.AI new submissions index](https://arxiv.org/list/cs.AI/new).

### 1c. Multi-Agent Software Teams May Not Scale With Agent Count (cs.AI listing, in-period)

**Claim:** A short position paper challenges the assumption that **adding more agents to a software-building team increases reliability**. Empirically, adding agents past 4–5 in a build pipeline is reported to *decrease* end-to-end task completion rates because of coordination overhead + conflicting edit intents.

**Why it's interesting:** This is the first paper to put a **coordination ceiling** on agent counts in a concrete task domain. It's a direct challenge to the "swarm beats individual" narrative that underwrites most 2026 multi-agent-framework pitches (CrewAI, AutoGen, LangGraph).

### 1d. Meta-analysis of 1.6K LLM Reasoning Papers (in-period)

A meta-analysis of the LLM-reasoning literature finds the field **concentrates on easily quantifiable aspects** (step count, accuracy, token efficiency) and **rarely targets self-awareness** (does the model know what it does and doesn't know?). Self-awareness is now an open eval frontier.

### Why it matters to you

- **Portfolio artifact — "independence probe":** You can literally port this November research into a weekend side-artifact: a **multi-agent eval harness** that measures reasoning-path diversity (edit distance between CoTs, prompt-attribution scoring, formal reasoning-isomorphism checks). Nobody has shipped a clean open-source version of this yet. It's a **2-weekend artifact**, novel, and cites a NeurIPS-workshop paper from 2 weeks ago.
- **Job lens — eval-authoring remains the premium skill.** The October theme was "can the agent self-report progress" ([2026-10-14 §1 — October arXiv](../2026-10-14/04-research-progress.md)); November's is "**can we prove the agent's reasoning is independent and durable**". If your interview portfolio has (a) an eval harness, (b) a cost-aware agent design, (c) a model-routing demo — you cover the three premium interview questions for AI Integration Engineer / FDE roles in Q4 2026.
- **Insight — the eval frontier is moving faster than the capability frontier.** Each monthly arXiv-review in this repo shows a **new eval axis**: June (cache-efficient context mgmt), July (tool-use eval), August (long-horizon planning), October (progress self-report), November (reasoning independence + durability). **The research community is explicitly working out what to measure next**; the capability frontier (new models) is mostly recombination of existing abilities with new routing. **The skill that compounds fastest is eval authoring.**

---

## 2. DeepMind agents exposed weaknesses in two legacy 1024-bit RSA schemes {#2-deepmind-rsa}

**What happened (in-period):** Google DeepMind's security-research agents (a CodeMender-descendant line) identified exploitable weaknesses in **two legacy 1024-bit RSA implementations** running in production on non-updated infrastructure. 1024-bit RSA has been **deprecated since 2013** (NIST SP 800-131A), so this is **not a cryptanalysis breakthrough** — it's a **capability milestone**: the first agent-swarm, run at Google scale, to surface real exploitable key material from deployed infra.

Companion warning: **UK NCSC** warned the UK should be prepared for an **AI-powered-ransomware attack on critical infrastructure within 24 months**.

**Sources:**
- [AI Weekly roundup — DeepMind RSA + NCSC warning items](https://aiweekly.co/ai-news-today) `[aggregator]`
- [Google DeepMind Blog](https://deepmind.google/discover/blog/) `[primary]`

### Why it matters to you

- **Job lens — the AI-Security-Engineer lane is accelerating.** Three independent data points in the period: (i) DeepMind's RSA result, (ii) OpenAI's GPT-6 Cyber alpha + GPT-5.6-Cyber's CVE-2026-15903 result (V8 engine), (iii) Anthropic's CIDP + OSS Scanner. **All three labs are hiring AI-Security Engineers**; the lane is less crowded than pure FDE because it requires a security + ML crossover that fewer CS grads have. If you've done a CTF / cryptography / security course, **this is your edge lane**.
- **Startup lens — AI-security defender tooling is a line-of-sight category.** Three concrete wedges: (a) **agent-swarm cyber-defense tooling** for mid-market SOCs that can't run their own Daybreak/Fairwind/CIDP-tier programs; (b) **AI-powered vulnerability triage** for OSS maintainers (clone the Anthropic OSS Scanner pattern); (c) **red-team-as-a-service** for enterprises adopting AI agents in production (every AI deployment now needs a red-team pass).
- **Insight — "agent swarms can find real vulns at scale" is now a load-bearing assumption.** The Sept-10-and-Oct-14 editions treated agent-based cyber capability as prospective; November 2026 is when it became operational at frontier labs. Expect **first big-ticket enterprise AI-security deal** (>$100M ARR customer) inside the next 90 days — watch the Palo Alto Networks + CrowdStrike + Wiz earnings calls for the first explicit AI-defense ARR line.

---

## 3. Watchlist — research threads to re-check next edition

- **Reasoning independence probes** — does an open-source eval harness land?
- **Coordination-ceiling empirical results** — does the "4–5 agent ceiling" replicate in different task domains (data analysis, writing, coding)?
- **Self-awareness evals** — does a frontier lab publish an eval axis for "does the model know what it doesn't know"? (Betting line: Anthropic first, Q1 2027.)
- **Agent-swarm cyber capability** — does a frontier lab disclose a new exploitable vulnerability found at scale?
