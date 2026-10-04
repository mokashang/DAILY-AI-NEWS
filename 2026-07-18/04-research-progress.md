# Research Progress — 2026-07-18

Four items, two of them fresh this week (Inkling + Kimi K3 architecture), two carry-forward context.

Tags: `#research #arxiv #inkling #kimi-k3 #architecture #benchmarks`

---

## 1. Sebastian Raschka's Inkling architecture writeup — the practitioner-grade read of the week {#1-inkling-arch}

**What.** [Sebastian Raschka's blog post "Inkling Architecture and Benchmark Notes"](https://sebastianraschka.com/blog/2026/inkling-architecture-benchmark-notes.html) — the reference architectural teardown of **Thinking Machines Lab's Inkling** (released Tue Jul 15). Raschka is the single most-cited practitioner writer on **ML fundamentals** through 2025-2026; his writeups are what people copy into their interview prep.

**Key architectural notes from Raschka's post (paraphrased — read the original):**
- **975B total / 41B active** MoE with an unusually deep routing tree — TML pushed **expert count high, expert size low** to maximize the sparsity-per-forward-pass ratio.
- **Multi-Token Prediction (MTP) layers** (speculative-decoding-adjacent) shipped as **separate downloadable weight variants** — a first for a US open-frontier release.
- **BF16 + NVFP4 variants both released day-1** — NVFP4 is Nvidia's newest low-precision format; releasing it day-1 signals TML has deep Nvidia partnership access and is optimizing for on-B200/GB200 inference from the start.
- **45T-token pretrain across text + image + audio + video** — the multimodal-from-scratch decision (not adapter-stack) is the same call Moonshot made for Kimi K3.
- **Tinker fine-tuning platform** shipped simultaneously — enables SFT + reward-model + DPO/KTO out of the box. Raschka's read: **this is TML's revenue play, not the model itself**.

**Why Raschka's take is worth the 15 minutes.** Three reasons:
- **He calibrates hype.** Raschka is famously restrained; when he says "this is notable," you can trust it as a signal, not a marketing echo.
- **He surfaces architectural tradeoffs by naming them explicitly** — "TML chose X over Y because Z" is exactly what interviewers ask about when they say "walk me through Inkling's architecture."
- **He includes runnable notebook examples** for MTP layer inference — 30 more minutes of your Saturday if you want to *feel* the primitive.

**Sources.**
- [Sebastian Raschka — Inkling Architecture and Benchmark Notes](https://sebastianraschka.com/blog/2026/inkling-architecture-benchmark-notes.html) `[primary practitioner]`
- [Thinking Machines Lab — Introducing Inkling](https://thinkingmachines.ai/news/introducing-inkling/) `[primary]`
- [Unite.AI — Thinking Machines Lab Unveils Inkling, Its First Open-Weights Multimodal AI Model](https://www.unite.ai/thinking-machines-lab-unveils-inkling-its-first-open-weights-multimodal-ai-model/) `[secondary]`

### Why it matters to you

- **Job lens:** **"Walk me through Inkling's architecture"** is now on the MLE interview-question shortlist for Q3. **The Raschka post is your prep** — read it once today, take three notes: (a) sparse-MoE tradeoff (why 975B/41B not 700B/60B), (b) MTP-layer purpose (speculative decoding, latency win), (c) NVFP4 vs BF16 choice (Nvidia-partnership signal + on-device economics).
- **Startup lens:** **Tinker (TML's fine-tuning platform) is the revenue play, not the weights.** If your startup depends on fine-tuning open-weight models, evaluate Tinker vs Databricks Mosaic vs Together AI training vs self-hosted — Tinker's day-1-with-Inkling posture may give it a native-integration edge for the next 6 months.
- **Insight:** **US open-frontier is a two-team race, and TML is the one team.** DeepMind and Meta are absent from the open-weights leaderboard now. If TML sustains this pace, they become the **default fine-tuning target for US-jurisdiction customers**, similar to what Kimi K3 will be for WAICO-jurisdiction customers ([2026-07-18/02 §5](./02-new-emerging.md#5-kimi-hosting)).

Tags: `#inkling #tml #architecture #raschka #open-source`

---

## 2. Kimi K3 architecture — the 2.8T MoE built around US export controls {#2-kimi-k3-arch}

**What.** Kimi K3's architectural notes (Moonshot's own release + community teardowns via [Codersera](https://codersera.com/blog/kimi-k3-complete-guide-2026/) + [Simon Willison](https://simonwillison.net/2026/Jul/16/kimi-k3/)):

- **2.8T total parameters** with estimated **150-200B active** at max-reasoning — the largest open-weight model release in history.
- **Trained on Huawei Ascend 910C + domestic H100-substitute stacks** (reported), not on export-controlled Nvidia H100/H200/B200. This is **strategically significant** — Moonshot demonstrates a **frontier-class model can be trained without US-controlled compute**. It undercuts a major pillar of US export-control policy.
- **Native multimodal from the ground up** — text + image + audio + video in a single pretraining loop, matching Inkling's decision.
- **1M-token context window** with **"max reasoning" toggle** (parallel test-time compute).
- **Open weights promised by Jul 27** — the licensing details are still TBD, but Moonshot's K2.6 shipped Apache-2.0-adjacent so expect similar for K3.

**Two architectural lessons.**

1. **"Sovereign compute" is now a shippable posture.** A trillion-parameter-plus model trained on non-Nvidia hardware is a **product proof**, not a research bet. Expect **Chinese frontier releases through Q4 to be advertised with hardware provenance** — "trained on Ascend / Huawei / domestic infrastructure" is now a WAICO-aligned marketing feature.
2. **Scale + sparsity is not enough alone** — Kimi K3 loses to Fable 5 Max on GDPval-AA v2 (1,687 vs 1,815) *despite* being ~3× larger by parameter count. The quality gap on the top ~20% of tasks is real and appears to be about **post-training quality**, not scale. Post-training (RLHF, DPO, expert-mix routing) is where the frontier gap now sits.

**Sources.**
- [Codersera — Kimi K3: Moonshot AI's 2.8T Open-Weight Model — Release, Specs & Pricing](https://codersera.com/blog/kimi-k3-complete-guide-2026/) `[analysis]`
- [Tom's Hardware — Moonshot AI delivers largest open-weight AI model ever](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3) `[primary journalism]`
- [Bloomberg — Moonshot Unveils Kimi K3 AI Model, Narrowing Gap With US Rivals](https://www.bloomberg.com/news/articles/2026-07-17/china-s-powerful-new-moonshot-ai-model-closes-gap-with-us-rivals) `[primary journalism]`
- [Simon Willison — Kimi K3, and what we can still learn from the pelican benchmark](https://simonwillison.net/2026/Jul/16/kimi-k3/) `[practitioner]`
- [Trending Topics — Kimi K3 Is the China Shocker That Lifts Open-Weight Models to Frontier Level](https://www.trendingtopics.eu/kimi-k3-china-shocker/) `[secondary]`

### Why it matters to you

- **Job lens:** **"Walk me through Kimi K3 and where it sits vs Fable 5"** is now a stock MLE interview question. Two-minute answer: (a) 2.8T MoE at 150-200B active, native multimodal, 1M ctx, max-reasoning toggle; (b) trained on Chinese domestic compute (Ascend 910C etc.), which is a *product proof* against export controls; (c) beats every open model on Frontend Code Arena but trails Fable 5 Max on GDPval-AA v2 by ~130 Elo — the gap is **post-training**, not scale.
- **Startup lens:** **The post-training moat matters more than the pretraining moat** now — a small team with strong RLHF pipelines can turn Kimi K3 open weights into a domain-specific model that beats Fable 5 on **that** domain. This is a legitimate **wedge in vertical-AI**, especially in verticals where Fable 5's generality isn't paid for.
- **Insight:** **US export controls are now an incentive to skip Nvidia, not a barrier to frontier work** — Kimi K3 proves it can be done. The response the Nvidia + hyperscaler ecosystem takes to this in Q4 will define **whether the "trained on sovereign compute" flag becomes a global feature or stays a China-only marketing angle**.

Tags: `#kimi-k3 #moonshot #architecture #export-controls #post-training`

---

## 3. Carry-forward — Ring-Zero + AI2 harness-evolution + Long-Horizon Terminal-Bench {#3-carry-forward}

From yesterday's edition ([2026-07-17/04 §1-4](../2026-07-17/04-research-progress.md)) — still relevant this weekend:

- **Ring-Zero (Ant Group, 1T MoE, "Zero RL")** — documented five emergent behaviors at trillion-scale RLVR, including "context anxiety" (self-budgeting compute). **Ring-1T open weights** match GPT-5 on Codeforces at ~50B active. **Weekend project candidate** — see [`05` §3](./05-career-and-startup.md#3-artifact-brief) alternative artifact.
- **AI2's harness-evolution paper** — shows most "self-improving agent" gains vanish under matched-compute + held-out eval. **Interview citation** for the "is agent-self-improvement real?" question.
- **Long-Horizon Terminal-Bench** — replaces pass/fail with dense-reward grading for multi-hour tasks. Complements the [MCP-Atlas / Toolathlon real-tool bench thread from 2026-05-22](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).
- **Anthropic's J-lens** — global-workspace-like subspace found inside Claude. **Interpretability read** for the weekend if you have extra time.

Tags: `#ring-zero #harness-evolution #terminal-bench #j-lens #interpretability`

---

## 4. Breadth pass — arXiv agent-papers from the last 10 days {#4-arxiv-breadth}

Quick log for [SOURCES.md](../SOURCES.md) awareness. Skim titles + abstracts; deep-read only what maps to your active portfolio direction.

From [VoltAgent's awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers) (curated arXiv 2026 list):

- **QUEST — training frontier deep-research agents with fully synthetic tasks** (arXiv 2605.24218): task-synthesis pipeline that produces "genuine research question + citable answer" pairs at scale, enabling deep-research training without human-authored data. **Relevant if you're building a research-agent side project.**
- **MiroEval — benchmarking multimodal deep research agents in process AND outcome** (arXiv 2603.28407): two-axis evaluation (process + outcome) instead of final-answer-only scoring. **The evaluation framing you cite in your portfolio README** — see [`05` §3](./05-career-and-startup.md#3-artifact-brief).
- **HAS-Bench — evaluating LLM-based human-agent systems with configurable human participation** (arXiv 2607.04329): benchmark for hybrid human-in-the-loop agent workflows. **Relevant for the Ode-style FDE-deployed-inside-a-client workflow.**
- **Act As a Real Researcher** (arXiv 2606.07462): benchmark suite for frontier LLM performance in the research lifecycle. **Adjacent to QUEST but with real-researcher-workflow authenticity.**
- **RL Foundations for Deep Research Systems: A Survey** (arXiv 2509.06733): if you want to onboard fast to the RL side of agent training. Save for a weekend when you have 3 hours.

Tags: `#arxiv #breadth #agent-papers #interview-prep`

---

## Cross-references

- [ACTIONS.md](../ACTIONS.md) — Raschka read added to Saturday afternoon
- [SOURCES.md](../SOURCES.md) — [Sebastian Raschka's blog](https://sebastianraschka.com/blog/2026/inkling-architecture-benchmark-notes.html) is Tier-8; already on the list (see Tier 8 "Ahead of AI (Sebastian Raschka)")
- Prior research: [2026-07-17/04](../2026-07-17/04-research-progress.md) (Ring-Zero, AI2 harness evolution, Long-Horizon Terminal-Bench, J-lens)
