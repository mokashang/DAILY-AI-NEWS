# Research Progress — 2026-05-31

A genuinely loaded week — and the three biggest research artifacts of it **all argued the same thing from different angles**: the agent capability you measure (and improve) lives in the **harness** — memory, context, tools, orchestration, verification — not just the weights. **SIA** (Hexo Labs, MIT-licensed) closes the loop by *jointly* updating harness and weights. **"From Model Scaling to System Scaling"** (Berkeley position paper) formalizes the taxonomy. **OpenAI's third-party-evaluations playbook** codifies it as governance norm: "harness choices can determine whether a capability appears at all." Underneath that thread, **research-level math** arrived as the next reasoning frontier (ResearchMath-14K + Soohak together), and **automating interpretability** got its first transferable RL formulation (MechRL).

Tags: `#arxiv #agents #self-improvement #harness #systems #evals #math #benchmarks #interpretability #openai`

---

## 1. SIA: Self-Improving AI with Joint Harness + Weight Updates {#1-sia}

**arXiv:** [2605.27276](https://arxiv.org/abs/2605.27276) (v1 2026-05-26, v2 2026-05-28)
**Authors:** Prannay Hebbar et al. (7 authors) — **Hexo Labs** w/ collaborators at Stanford, Oxford, UCSB
**License:** **MIT** ([github.com/hexo-ai/sia](https://github.com/hexo-ai/sia))

### One-line summary

A meta-agent that closes the self-improvement loop by **simultaneously rewriting a task agent's harness** (tools, prompts, retry logic) **and updating its model weights** via PPO/LoRA, evaluated across three unrelated domains.

### Why it matters (5 bullets)

- **Bridges the two previously disjoint schools** of agent self-improvement — "harness-edit only" (ADAS-style) and "weight-update only" (test-time RL). The combined loop **beats either alone on every domain tested**.
- **Headline numbers:**
  - **+20.1 pp accuracy on LawBench** (Chinese legal charge classification, hitting **70.1%**)
  - **91.9% runtime reduction** on a TriMul CUDA kernel relevant to AlphaFold2's Evoformer (**12,483 → 1,017 µs on H100**)
  - **~5× improvement** on MAGIC-based single-cell RNA denoising
- **Reproducible recipe:** built on `gpt-oss-120b` with **LoRA rank 32**. End-to-end open source, MIT-licensed — one of the few self-improvement papers anyone can actually rerun.
- **Operational counterpart to the week's headline lab move** — Claude Opus 4.8's **dynamic workflows** ([`01` §2](./01-big-lab-moves.md#2-opus-48), [`03` §1](./03-practical-skills-and-tools.md#1-ultracode)) ship the harness as a first-class product surface; SIA ships joint harness + weight optimization as a research artifact. Same direction of travel.
- **Expect copycat frameworks within weeks** — the combination is conceptually obvious in hindsight, the open-source release lowers the activation energy to near zero.

**Sources:**
- [arXiv 2605.27276 — SIA: Self Improving AI](https://arxiv.org/abs/2605.27276) `[primary]`
- [MarkTechPost — Hexo Labs Open Sources SIA](https://www.marktechpost.com/2026/05/29/hexo-labs-open-sources-sia-a-self-improving-agent-that-updates-both-the-harness-and-the-model-weights/) `[analysis]`
- [GitHub — hexo-ai/sia](https://github.com/hexo-ai/sia) `[primary]`

Tags: `#arxiv #agents #self-improvement #RL #LoRA #open-source`

---

## 2. From Model Scaling to System Scaling: Scaling the Harness in Agentic AI {#2-system-scaling}

**arXiv:** [2605.26112](https://arxiv.org/abs/2605.26112) (2026-05-25)
**Author:** Shangding Gu — **UC Berkeley**

### One-line summary

A position paper arguing the next bottleneck in agentic AI is the **harness** — memory substrate, context constructor, skill router, orchestration loop, verification layer — and that current evaluation is **model-centric** in ways that miss most of the actual capability surface.

### Why it matters

- **The *taxonomic* version of the same thesis** SIA proves *constructively*. Together they're the dominant research thread of the week.
- Identifies **six first-class system components**: foundation model · memory substrate · context constructor · skill-routing layer · orchestration loop · verification-and-governance layer. Argues each needs its own scaling laws and benchmarks.
- Aligns with **OpenAI's third-party-evals playbook** ([§3](#3-third-party-evals)) which independently argues that **harness configuration materially determines what capability appears**.
- Provides **shared vocabulary** for eval-pipeline design discussions, currently missing in the agent-eval literature.
- Useful as a *reference* in interviews / blog posts — "I built X with this six-component decomposition in mind" is recruiter-legible language for the AI Integration Engineer / FDE lane in [`05` §2](./05-career-and-startup.md#2-anthropic-fde).
- Caveat: position paper, not empirical. Adoption is the story to track over Q3.

**Sources:**
- [arXiv 2605.26112 — From Model Scaling to System Scaling](https://arxiv.org/abs/2605.26112) `[primary]`

Tags: `#arxiv #agents #systems #evals #position-paper`

---

## 3. OpenAI — A Shared Playbook for Trustworthy Third-Party Evaluations {#3-third-party-evals}

**Published:** 2026-05-29 (OpenAI Safety / Frontier Governance team blog)

### One-line summary

Industry-facing guidance for how third-party evaluators should assess frontier models when chatbot-style assessments are no longer adequate — with the central argument that **the evaluation harness itself materially determines what capability shows up.**

### Why it matters

- **First major-lab publication explicitly arguing** that "harness choices can change observed performance and even determine whether a capability appears at all." Codifies what practitioners suspected but didn't have authoritative backing for.
- Calls for **transparency in tools, compute budgets, and configurations** used in any third-party eval. Implication: **"we ran benchmark X" without harness disclosure is no longer credible.** Expect this norm to harden fast across the rest of 2026.
- **Three-way convergence with the academic thread** (SIA + System Scaling). When Anthropic's product surface (dynamic workflows), an open-source agent paper (SIA), an academic position paper (Berkeley), and a frontier-lab governance doc all argue the same thing inside a single week — that's a thread, not a coincidence.
- Part of a broader May 2026 OpenAI safety cluster: **Frontier Governance Framework** (May 28), Content Provenance work (May 19), GPT-5.5 Bio Bug Bounty, **Rosalind Biodefense** ([`01` §3](./01-big-lab-moves.md#3-rosalind)). The third-party-evals doc is the most consequential for the research and hiring community.
- **For job-hunters:** "third-party evaluation, harness disclosure, frontier governance" is now a *concrete* skills vocabulary you can put on a resume targeting AI assurance / pre-deployment eval / safety roles at OpenAI, Anthropic, METR, Apollo, AISI-equivalents.

**Sources:**
- [OpenAI — A Shared Playbook for Trustworthy Third-Party Evaluations](https://openai.com/index/trustworthy-third-party-evaluations-foundations/) `[primary]`
- [Blockchain.news — OpenAI playbook third-party evaluations](https://blockchain.news/news/openai-playbook-third-party-evaluations) `[analysis]`
- [StartupHub — OpenAI's Playbook for AI Evaluation](https://www.startuphub.ai/ai-news/artificial-intelligence/2026/openai-s-playbook-for-ai-evaluation) `[analysis]`

Tags: `#openai #evals #safety #governance #harness`

---

## 4. ResearchMath-14K: Scaling Research-Level Mathematics via Agents {#4-researchmath}

**arXiv:** [2605.28003](https://arxiv.org/abs/2605.28003) (2026-05-27)
**Authors:** ResearchMath team (multi-agent academic pipeline; institutions to be confirmed at v2)

### One-line summary

The **largest research-level math dataset to date** — **14,056 problems** curated from academic sources by a multi-agent pipeline — plus **220K teacher trajectories** and a fine-tuning recipe that improves Qwen3 (4B–30B) by **+9.2 pts on average over the base**.

### Why it matters

- **Natural training-data complement to Soohak** (the 439-problem mathematician-curated eval published earlier in May, where Gemini-3-Pro scored 30.4%, Claude-Opus-4.5 only 10.4%, and most frontier models scored <50% on recognizing ill-posed problems). The community now has **both a hard eval and a scalable training set in the same month.**
- Demonstrates **agentic filtering matters more than raw scraping** — raw teacher trajectories contained "recurring avoidance behaviors — non-attempts and fabricated references" (exactly the Soohak refusal failure mode). Filtering them out is what yields the +9.2 pt gain.
- **Reproducible pipeline:** scrape → 220K teacher traces with 2 open models → agent-filter → fine-tune Qwen3 4B/14B/30B.
- **IMO is effectively saturated** at the frontier; research-level math is the next reasoning measurement frontier. Expect a wave of methods papers training against ResearchMath-14K in June.
- The companion **Soohak refusal-subset finding** — "more compute makes models better at *solving* but not better at *admitting a problem has no answer*" — is the more durable insight; it suggests a fundamental calibration gap that scaling alone won't close.

**Sources:**
- [arXiv 2605.28003 — ResearchMath-14K](https://arxiv.org/abs/2605.28003) `[primary]`
- [arXiv 2605.09063 — Soohak (companion eval)](https://arxiv.org/abs/2605.09063) `[primary]`
- [The Decoder — New math benchmark reveals AI models confidently solve problems that have no solution](https://the-decoder.com/new-math-benchmark-reveals-ai-models-confidently-solve-problems-that-have-no-solution/) `[analysis]`

Tags: `#arxiv #benchmarks #math #datasets #reasoning #calibration`

---

## 5. MechRL: Reinforcement Learning Agents Perform Circuit Discovery for Mechanistic Interpretability {#5-mechrl}

**arXiv:** [2605.26343](https://arxiv.org/abs/2605.26343) (2026-05-25)
**Author:** Barsat Khadka — University of Southern Mississippi (single-author)

### One-line summary

Recasts mech-interp circuit discovery as an **RL problem** — a PPO agent acts over GPT-2 small's 144 attention heads as a discrete action space, each action triggers a zero-ablation with contrastive reward, and learns to recover known circuits **and generalize to held-out tasks**.

### Why it matters

- **First demonstration that a single PPO policy**, trained jointly on Induction and IOI, attains per-episode oracle performance **and** transfers to a held-out third task (docstring completion). Suggests circuit discovery has **shared structure that's learnable, not just hand-craftable.**
- Replaces the current **bespoke pipeline-per-task** workflow (ACDC, EAP, etc.) with a **single generalizable agent**. If it scales beyond GPT-2 small, it changes the economics of interp work substantially.
- **Pairs interestingly** with the same-week companion paper [arXiv 2605.21303 — "From Circuit Evidence to Mechanistic Theory: An Inductive Logic Approach"](https://arxiv.org/abs/2605.21303) (Aljaafari/Carvalho/Freitas, Manchester/Idiap), which formalizes circuits with Causal Functional Signatures and ILP-learned architectural signatures. **Discovery layer + theory layer landing in the same week.**
- **Single-author from a non-frontier-lab institution** — useful counter-evidence to the "only frontier labs can do interp" narrative.
- **Caveat:** only GPT-2 small. The real test is whether the discrete-action approach scales to GPT-2 XL or modern frontier-scale architectures (hundreds of thousands of heads).

**Sources:**
- [arXiv 2605.26343 — MechRL](https://arxiv.org/abs/2605.26343) `[primary]`
- [arXiv 2605.21303 — From Circuit Evidence to Mechanistic Theory (companion)](https://arxiv.org/abs/2605.21303) `[primary]`

Tags: `#arxiv #interpretability #RL #safety #mech-interp`

---

## Research thread of the week

**The harness is the model now.** Three independent publications in five days — **SIA's joint scaffold-and-weight updates**, **Gu's "System Scaling" position paper**, and **OpenAI's third-party evaluations playbook** — all argue from different angles that capability lives in the agent system, not just the weights, and that treating model-only evals or model-only training as the primary lever is increasingly the wrong abstraction. Running parallel underneath: **research-level math arriving as the next reasoning frontier** (Soohak's eval set + ResearchMath-14K's 14K-problem training corpus, both published in May, with frontier models still <31% on the hard subset and <50% on recognizing ill-posed problems), and **automating interpretability** taking its first transferable RL formulation (MechRL + the companion ILP-theory paper).

For the Anthropic-stack focusing decision: **the research literature is now agreeing with the bet you already placed.** Build skills around the harness — verification, orchestration, eval design, harness disclosure — not around prompt-craft for any specific model.

## Beats with thin returns this week

- **Anthropic safety publications** — main May items ("Teaching Claude Why", NLA interpretability) landed earlier in the month (May 7–8); nothing major in the May 23–31 window.
- **DeepMind research** — quiet for the window; main I/O cluster preceded it.
- **Robotics / VLA** — several survey-style papers, no headline new VLA model or capability demo in the window worth elevating.
- **Biology / AlphaFold** — a Nature piece (May 29) on expanded AlphaFold catalogues, but no clear arXiv-side breakthrough in our window.
