# Research Progress — 2026-11-15

**The 2611.xxxxx arXiv wave is forming around three themes: trajectory-level agent reliability, test-time scaling (TTS) as the new cost lever, and VLA interpretability + negative results.** Three papers are directly actionable as portfolio artifacts this weekend: **Dependable Long-Horizon LLM Agents (2611.13254)** motivates a mid-trajectory verifier middleware — a fundable wedge; **Ask2Decide (2611.13015)** gives the clean negative data on clarification-asking (a startup opportunity in planner/question-ranker middleware); **RLiD (2611.02455)** shows 99.3% on ALFWorld via decision-plane RL — a reproducible weekend GPU project. On the safety / alignment side, **Anthropic published "Reliable Safety Evaluations" (Nov 13)** and **Anthropic Alignment Science's "Automated Alignment Researchers (Opus 4.8)"** showed LLM-produced ideas beat 28 human researchers' one-shot output on characterized failures — **strongest signal yet that "LLM-on-alignment-work" is a hireable job family**.

Tags: `#arxiv #agents #reliability #tts #reasoning #vla #robotics #interpretability #alignment #memory #benchmarks`

---

## Agents & reliability

## 1. Dependable Long-Horizon LLM Agents (arXiv 2611.13254, Nov 9) {#1-dependable-agents}

**Claim:** A trajectory-centered empirical study showing that **most failed agent runs already contained evidence against the eventual error** before failure. The signal is there — just not surfaced to the agent's own next step.

**Sources:** [arXiv 2611.13254](https://arxiv.org/abs/2611.13254) `[primary arxiv]`

**Why it matters:**
- **Portfolio wedge:** A **mid-trajectory verifier middleware** that runs a lightweight critic every N steps and halts on red flags is a shippable weekend project — the "runtime agent lint." Combine with LangGraph 1.2.20's strict resume (see [`03` §3](./03-practical-skills-and-tools.md#3-langchain-langgraph)) and you have an interview-grade artifact.
- **Startup signal:** Pairs directly with Tail-risk-aware Agent Safety (§2) as the compliance wedge for enterprise agents.

---

## 2. Tail-risk-aware Agent Safety (TAS) (arXiv 2611.10411) {#2-tail-risk}

**Claim:** Models multi-step agent workflows as dependent safety states with a **shared tail-risk budget** — rather than independent per-step filters.

**Sources:** [arXiv 2611.10411](https://arxiv.org/abs/2611.10411) `[primary arxiv]`

**Why it matters:**
- **Enterprise sales lever:** Most agent-governance pitches still rely on per-step filters. A shared budget framing is the first compliance-ready story for multi-step workflows.
- **Pairs with:** [§1](#1-dependable-agents) (verifier middleware) + Agentic Behavior Engineering (§3).

---

## 3. Agentic Behavior Engineering — Design-by-Contract for agents (arXiv 2611.05454, Nov 3) {#3-agentic-engineering}

**Claim:** Treats **observable agent behavior as the version-controlled artifact**, with design-by-contract style contracts across tool calls.

**Sources:** [arXiv 2611.05454](https://arxiv.org/abs/2611.05454) `[primary arxiv]`

**Why it matters:**
- **Governance substrate:** This is the layer large companies will need before shipping internal agents at scale. Pair with MCP + Claude Skills for a governance-plane product pitch.

---

## 4. Ask2Decide — From Questions to Decisions (arXiv 2611.13015) {#4-ask2decide}

**Claim:** 43-task benchmark showing agents **ask for decision-relevant information only marginally more often than for noise** — i.e., clarification-asking is still broken.

**Sources:** [arXiv 2611.13015](https://arxiv.org/abs/2611.13015) `[primary arxiv]`

**Why it matters:**
- **Clean negative result → startup opportunity** in a planner/question-ranker middleware that sits between user → agent and scores clarification candidates by expected-information-gain.

---

## 5. Detecting Shadow AI on Endpoints (arXiv 2611.12377, Nov 9) {#5-shadow-ai}

**Claim:** Taxonomy + open detector for unsanctioned LLM agents running on Windows endpoints.

**Sources:** [arXiv 2611.12377](https://arxiv.org/abs/2611.12377) `[primary arxiv]`

**Why it matters:**
- **Enterprise IT / security wedge:** Shadow-agent proliferation is the 2027 "shadow SaaS" moment. A small open detector is a fast GTM artifact — any CISO you cold-email will take the meeting.

---

## 6. RLiD — Reinforcement Learning in the Decision Plane (arXiv 2611.02455, Nov 2) {#6-rlid}

**Claim:** **99.3% on ALFWorld** via decision-plane RL — cheap agent RL without full-model fine-tunes.

**Sources:** [arXiv 2611.02455](https://arxiv.org/abs/2611.02455) `[primary arxiv]`

**Why it matters:**
- **Replicable weekend project** on 1–2 GPUs. If you can reproduce 95%+ with your own setup and publish a README + numbers, that's a direct MLE résumé line.

---

## Reasoning / test-time scaling (TTS)

## 7. Test-Time Scaling for Open-Ended Reasoning at Small Model Scale (arXiv 2611.02208, Nov 1) {#7-tts-small-models}

**Claim:** Judge-free semantic clustering of small-model samples; **TTS works on free-form generation too**, not just verifiable math/code.

**Sources:** [arXiv 2611.02208](https://arxiv.org/abs/2611.02208) `[primary arxiv]`

**Why it matters:**
- **Router economics shift:** small-model stacks become competitive for agentic sub-tasks → pricing power concentrates in routing + eval design rather than model capability.

---

## 8. Rethinking LLM Pruning via Test-Time Scaling (arXiv 2611.01133, Oct 31) {#8-tts-pruning}

**Claim:** Pruned models often match originals' sample coverage on math/code once TTS is applied.

**Sources:** [arXiv 2611.01133](https://arxiv.org/abs/2611.01133) `[primary arxiv]`

**Why it matters:**
- **Direct cost lever:** the **"pruned + TTS"** pattern is the new inference-cost arbitrage for startups on fal / Modal / Replicate. If you're building on inference infra, this is a pricing differentiator through 2027.

---

## 9. Test-Time Scaling for Diffusion LMs — Frequency-Aware Remasking (arXiv 2611.10486, Nov 7) {#9-diffusion-tts}

**Claim:** Recovers solutions the base sampler missed even after 100 samples.

**Sources:** [arXiv 2611.10486](https://arxiv.org/abs/2611.10486) `[primary arxiv]`

**Why it matters:**
- **Diffusion LMs entering useful territory:** First evidence TTS works well there. A differentiator for teams building on diffusion-LM stacks (Inception Labs, Mercury) rather than transformer-only.

---

## Memory & long context

## 10. Peer Memory Changes Agent Consultation Patterns, Not Accuracy (arXiv 2611.09990, Nov 2) {#10-peer-memory}

**Claim:** Cross-agent memory changes **routing behavior** but NOT final accuracy. Negative result.

**Sources:** [arXiv 2611.09990](https://arxiv.org/abs/2611.09990) `[primary arxiv]`

**Why it matters:**
- **Kills the "shared memory = smarter swarm" pitch dead.** Forces startups with multi-agent memory to justify ROI with evals, not vibes.

---

## 11. Context as an Environment — programmatic context management (follow-ups) {#11-context-env}

**Claim:** Context management is a first-class agent action (compaction / eviction / sub-indexing).

**Sources:** [arXiv 2608.21690](https://arxiv.org/pdf/2608.21690) `[primary arxiv]` + follow-ups

**Why it matters:**
- **Pattern is already in Claude Code 2.1 subagent context strategy.** If you can articulate it in an interview, you demonstrate reading the frontier of the ecosystem you're applying to.

---

## VLA / robotics

## 12. Localizing and Editing the Goal Representation of a VLA (OpenVLA) (arXiv 2611.08895, Nov 6) {#12-openvla-editing}

**Claim:** OpenVLA executes forbidden tasks in **79% of negated prompts** ("do not pick up the red block"); goal direction is linearly editable.

**Sources:** [arXiv 2611.08895](https://arxiv.org/abs/2611.08895) `[primary arxiv]`

**Why it matters:**
- **First clean VLA interpretability artifact.** A safety-of-robotics research lane just opened — if you've ever wanted a research-engineer role at Figure, Physical Intelligence, Apptronik, or DeepMind Robotics, this paper is your weekend read.

---

## 13. JADE — VLM + diffusion jointly denoise actions (arXiv 2611.01215, Oct 31) {#13-jade}

**Claim:** VLM reads current noisy action + visuals + language and co-denoises with the policy diffusion.

**Sources:** [arXiv 2611.01215](https://arxiv.org/abs/2611.01215) `[primary arxiv]`

**Why it matters:**
- **Matches the Runway Praxis-1 / GR00T 2 convergence** from yesterday's edition. If you're pitching a VLA fine-tune wedge, cite JADE.

---

## 14. Meituan-Robotics-0 (arXiv 2611.08577, Nov 10) {#14-meituan-robotics}

**Claim:** Desktop-manipulation VLA foundation model from Meituan.

**Sources:** [DailyArxiv digest](https://github.com/guoyue0412/DailyArxiv/issues/115) `[secondary summary]`

**Why it matters:**
- **Adds a Chinese entrant to the open-weight VLA ladder** (joining Kimi K3.1 Pro's language lineage). The Chinese open-weight stack is now vertically integrated: language → vision → VLA → robotics.

---

## 15. "Is Your Robot's Memory Just a Clock?" (arXiv 2611.14488) {#15-robot-memory-clock}

**Claim:** Memory-augmented VLA policies often rely on **timing shortcuts, not real memory**.

**Sources:** `[secondary summary — arXiv 2611.14488]`

**Why it matters:**
- **Negative result:** if you're building robot memory benchmarks, start here. Paired with the Peer Memory negative result (§10), **"memory in agents" is 2026's most over-claimed capability**.

---

## Interpretability / safety / alignment

## 16. Anthropic — Reliable Safety Evaluations guidance (Nov 13) {#16-anthropic-safety-evals}

**Claim:** 94–98% harmless rate on single-turn API; recommends **multi-turn evals + automated-grader safeguards**.

**Sources:** [Unite.AI — Anthropic guidance](https://www.unite.ai/anthropic-publishes-guidance-for-more-reliable-ai-safety-evaluations/) `[primary — Anthropic blog]`

**Why it matters:**
- **Direct template for an "eval-authoring" portfolio artifact that labs explicitly cite as a hiring signal.** Pick any eval your organization relies on, apply Anthropic's multi-turn + grader-safeguards method, publish results. This is a 2-hour exercise that produces a résumé line.

---

## 17. Anthropic Alignment Science — Automated Alignment Researchers (Claude Opus 4.8) {#17-automated-alignment}

**Claim:** **Opus-4.8-based automated researchers beat 28 human researchers' one-shot ideas on characterized failures.**

**Sources:** [Anthropic Alignment Science — Automated Alignment Researchers](https://alignment.anthropic.com/2026/automated-alignment-researchers/) `[primary]`

**Why it matters:**
- **Strongest signal yet that "LLM-on-alignment-work" is a hireable job family** — you no longer need a safety PhD to work in alignment. The Anthropic Residency 2026 (Nov 22 deadline, see [`05` §4](./05-career-and-startup.md#4-anthropic-residency)) is explicit about this track.

---

## 18. "Understanding AI from the Inside" — Mech Interp Survey (arXiv 2611.08438, Nov 9) {#18-mech-interp-survey}

**Claim:** Current state of mechanistic interpretability for safety.

**Sources:** [alphaXiv 2611.08438](https://www.alphaxiv.org/abs/2611.08438) `[primary arxiv]`

**Why it matters:**
- **The one-weekend read before applying to Anthropic Residency.** Even if you don't apply, citing the survey in a cold email to Anthropic's safety team or in an interpretability recruiter screen is a strong signal.

---

## Benchmarks / meta

## 19. SWE-bench Verified saturation — and SWE-bench Pro in open conflict {#19-swe-bench}

**Claim:** On SWE-bench Verified: Claude Opus 5 **97.0%**, DeepSeek V4 Pro **96.4%**, GLM-5.3 **95.4%**, Kimi K3 **93.4%**. OpenAI publicly argues Verified no longer measures frontier. SWE-bench **Pro** numbers in open conflict across model owners: 61.5% vs 89.9% vs 51.5% depending on who you ask.

**Sources:** [MorphLLM — SWE-bench Pro leaderboard Nov 2026](https://www.morphllm.com/ai-coding-benchmarks-2026) `[analysis]`

**Why it matters:**
- **Portfolio-ready to publish a "which SWE-bench variant should you cite in 2026?" memo.** This is a free 500-word LinkedIn post that will route you into FDE pipelines because every FDE-recruiter is secretly annoyed at candidates citing stale benchmarks.

---

## 20. SWE-Bench Pro Verified (arXiv 2609.08149) {#20-swe-bench-pro}

**Claim:** Reliability-focused Pro variant; still being normalized across evaluators.

**Sources:** [arXiv 2609.08149](https://arxiv.org/pdf/2609.08149) `[primary arxiv]`

**Why it matters:**
- Cite this when publishing a router-eval artifact. Pair with §19.

---

## Hiring signal

### Anthropic Residency 2026 — applications open, due **Nov 22, 2026** {#residency-note}

- Alignment / interpretability lanes explicit.
- The Mech Interp Survey (§18) + Automated Alignment Researchers (§17) are the two things to cite in your application statement.
- **Sources:** [Opportunities for Youth — Anthropic Residency 2026](https://opportunitiesforyouth.org/2026/11/06/anthropic-residency-2026-paid-ai-safety-research-program-for-established-technical-leaders-applications-open/) `[secondary]`

→ Full application playbook in [`05` §4](./05-career-and-startup.md#4-anthropic-residency).

---

## Top three to act on this weekend

1. **Build a mid-trajectory verifier skill** (cite 2611.13254 + Ask2Decide 2611.13015) → direct FDE portfolio artifact.
2. **Replicate RLiD on a toy ALFWorld-style task** (cite 2611.02455) → MLE résumé line + public GitHub repo.
3. **Publish a ~500-word "which SWE-bench variant should you cite in 2026?" memo** (cite 2609.08149 + MorphLLM leaderboard) → LinkedIn signal that routes into FDE pipelines.

---

## Sources (consolidated)

- [arXiv 2611.13254 — Dependable Long-Horizon LLM Agents](https://arxiv.org/abs/2611.13254)
- [arXiv 2611.10411 — Tail-risk-aware Agent Safety](https://arxiv.org/abs/2611.10411)
- [arXiv 2611.05454 — Agentic Behavior Engineering](https://arxiv.org/abs/2611.05454)
- [arXiv 2611.13015 — Ask2Decide](https://arxiv.org/abs/2611.13015)
- [arXiv 2611.12377 — Detecting Shadow AI](https://arxiv.org/abs/2611.12377)
- [arXiv 2611.02455 — RLiD](https://arxiv.org/abs/2611.02455)
- [arXiv 2611.02208 — TTS Small-Model Open-Ended](https://arxiv.org/abs/2611.02208)
- [arXiv 2611.01133 — Pruning via TTS](https://arxiv.org/abs/2611.01133)
- [arXiv 2611.10486 — Frequency-Aware Remasking (Diffusion TTS)](https://arxiv.org/abs/2611.10486)
- [arXiv 2611.09990 — Peer Memory](https://arxiv.org/abs/2611.09990)
- [arXiv 2611.08895 — Editing VLA Goal Representations](https://arxiv.org/abs/2611.08895)
- [arXiv 2611.01215 — JADE joint denoisers](https://arxiv.org/abs/2611.01215)
- [DailyArxiv Nov 11 digest (Meituan-Robotics-0, 2611.14488)](https://github.com/guoyue0412/DailyArxiv/issues/115)
- [alphaXiv 2611.08438 — Mech Interp Survey](https://www.alphaxiv.org/abs/2611.08438)
- [Anthropic — Reliable Safety Evaluations guidance](https://www.unite.ai/anthropic-publishes-guidance-for-more-reliable-ai-safety-evaluations/)
- [Anthropic Alignment Science — Automated Alignment Researchers](https://alignment.anthropic.com/2026/automated-alignment-researchers/)
- [Anthropic Residency 2026 (Nov 22 deadline)](https://opportunitiesforyouth.org/2026/11/06/anthropic-residency-2026-paid-ai-safety-research-program-for-established-technical-leaders-applications-open/)
- [MorphLLM — SWE-bench Pro leaderboard Nov 2026](https://www.morphllm.com/ai-coding-benchmarks-2026)
