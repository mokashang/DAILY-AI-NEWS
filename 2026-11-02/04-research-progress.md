# Research Progress — 2026-11-02

The eval frontier moved another step: **"process-aware evaluation" is now the dominant research direction**, replacing final-score pass@k as the credible benchmark style. The anchor papers: *Beyond Final Scores* (long-horizon AI R&D), AgentLens (the lucky-pass problem in SWE-agents), the ACL 2026 Findings LLM-agent-evaluation survey, and the Exgentic framework for general-agent evaluation. Nov 2 adds **GDPx (SemiAnalysis)** as the first economic-value-weighted agentic benchmark released on a frontier-lab IPO morning.

Tags: `#arxiv #agents #evals #process-aware #trajectory #sweagents`

---

## 1. Process-aware agent evaluation becomes the dominant research direction {#1-process-eval}

**What's happening:** Four distinct 2026 research threads have converged on the same claim — **final-score benchmarks hide the real failure modes of agents, and the next generation of evals must measure the trajectory, not just the terminal state.**

### 1a. *Beyond Final Scores: A Systematic Evaluation of Agents for Long-Horizon AI R&D*

**arXiv:** [`2608.13417`](https://arxiv.org/pdf/2608.13417) `[primary — preprint]`

Systematic evaluation of agents on long-horizon AI research and development tasks, specifically arguing that pass/fail or pass@1 scoring **hides the failure modes that matter** in agents assigned multi-step, multi-day research tasks. Introduces a per-trajectory scoring protocol.

### 1b. AgentLens — the "lucky pass" problem in SWE-agent evaluation

**arXiv:** `2605.12925` *(as referenced in a 2026 analytics roundup — [source link](https://www.analyticsvidhya.com/blog/2026/08/top-agentic-ai-research-papers/))* `[secondary — referenced]`

AgentLens targets the specific failure mode where a SWE-agent gets a correct answer on a benchmark despite executing a wrong-shaped trajectory (e.g., accidentally stumbling into the right file via a wrong grep). The paper proposes a trajectory-match requirement in addition to the final-answer check.

### 1c. ACL 2026 Findings — LLM-based agent-evaluation survey

**Published:** ACL 2026 Findings (July 2026). [`2026.findings-acl.1330.pdf`](https://aclanthology.org/2026.findings-acl.1330.pdf) `[primary — venue]`

Survey of LLM-based agent evaluation. The useful contribution for a practitioner is a **taxonomy of eval modes** — final-answer, trajectory, resource-cost, recovery-from-failure, self-verification — and a case-by-case guide to which is appropriate for which agent type.

### 1d. Exgentic — unified protocol for general-purpose agents

**arXiv:** [`2602.22953`](https://arxiv.org/abs/2602.22953) `[primary — preprint]`

Proposes a unified protocol and the Exgentic framework for evaluating general-purpose agents. Important for a founder or MLE who needs to standardize eval across heterogeneous agents.

### 1e. The June 2026 "process-aware measurement" research brief

[tdteach — June 18, 2026 Research Brief](https://tdteach.github.io/paper-news/2026-06-18/) `[aggregator]`

A roundup that stitches multiple 2026 papers into the same thesis: **evaluation is shifting from final-answer scoring to process-aware measurement** because pass/fail, pass@1, or pooled factuality scores hide the real failure modes in agents.

### 1f. The Nov-2 GDPx benchmark (economic-value-weighted)

[AI Weekly — SemiAnalysis Launches GDPx; Best Frontier Model Hits 12%](https://aiweekly.co/alerts/semianalysis-launches-gdpx-best-frontier-model-hits-12) `[aggregator]`

Not an academic paper, but a Nov-2-published benchmark that scores agents on real-world economic-value-weighted knowledge tasks. **~12.5%** best frontier result. See [`02` §2](./02-new-emerging.md#2-gdpx).

### Why it matters to you

- **Job lens — this is now a hirable skill.** The exact capability a Q1 2027 FDE / MLE hiring loop is now screening for: **can you author an eval harness that reports trajectory + cost + recovery + self-verification, not just pass@k?** The weekend-artifact play: fork a public SWE-bench style harness, add trajectory scoring, publish. This is simultaneously your pre-cover-letter technical signal and your interview talking-point.
- **Startup lens:** "Eval-as-a-service" is a startup wedge, but it has been for a year. The wedge that is *new* in Nov 2026: **GDPx-style, economic-value-weighted eval per-vertical.** Build the GDPx-for-legal, GDPx-for-healthcare, GDPx-for-manufacturing-ops benchmark; sell access to vendors who want to prove their fine-tuned open-weight stack holds up. Low-moat but immediate; the entry cost is one weekend + 100 well-chosen tasks.
- **Insight — the deeper claim:** benchmark design is becoming a **de-facto industry-structuring instrument.** The GDPx-vs-Terminal-Bench disagreement **re-prices which labs are "ahead."** Watch for the ANT S-1 to cite its chosen benchmarks explicitly in the "Business" section — that choice is itself a disclosure.

→ Cross-link: [`02` §2 GDPx](./02-new-emerging.md#2-gdpx) · [`03` §3 cheap-tier year](./03-practical-skills-and-tools.md#3-cheap-tier-year).

---

## 2. Open-weight capability research progresses — Kimi K3.1 Pro + Mistral Large 4 architectural notes {#2-open-weight-research}

Not peer-reviewed research, but the model cards and architectural notes released alongside the Nov-week open-weight drops are the closest-to-primary architectural documents available:

- **Kimi K3.1 Pro (Moonshot) — MoE at 2.8T total / 104B active, 1M context.** The architectural claim worth tracking: **frontier-adjacent capability at **~3.7% of parameter activation**. If the open weights land Nov 4 as promised, this is **the first open-weight 1M-context MoE at this scale**.
- **Mistral Large 4 "Le Chonk" — 1T total / 49B active, multimodal natively.** FP8 and NVFP4 variants released on Hugging Face. The release of FP8 + NVFP4 implies production-aimed deployment, not research-only.

**Sources:**
- [1023jack — Kimi K3.1 Pro architectural read](https://1023jack.com/news/kimi-k3-1-pro-an-open-weight-giant-lands-three-points-from-the-frontier-the-weig/) `[analysis]`
- [Codersera — Kimi K3.1 Pro: Specs, pricing, benchmarks, open-weights](https://codersera.com/blog/kimi-k3-1-pro-complete-guide-2026/amp/) `[analysis]`
- [Constellation Research — Mistral Large 4 release context](https://www.constellationr.com/insights/news/mistral-makes-its-open-model-case-mistral-large-4) `[analysis]`
- [VKTR — Mistral Large 4 debuts as 1T open-weight](https://www.vktr.com/ai-platforms/mistral-large-4-debuts-as-1t-parameter-open-weight-model/) `[secondary]`

### Why it matters to you

- **Job lens:** Being able to **compare Kimi K3.1 Pro's and Mistral Large 4's MoE routing strategies** on a whiteboard is now a differentiator for MLE / Infra-AI / Platform roles. The exact talking-point: **"Why does Mistral activate 4.9% of parameters per token while Moonshot activates 3.7%?"** You don't need to know the actual answer — you need to know the question is live.
- **Startup lens:** For a product that depends on inference economics, **the gap between the two architectures is a practical infra decision**, not an academic curiosity. Lower active-parameter fraction = cheaper per-token at the same quality tier *if* routing holds up. Build the comparison into your TAM / cost model.
- **Insight:** The open-weight tier **is now producing architectural research as a side-effect of competitive releases**, not through a controlled research-paper cadence. For a CS grad student, this means **reading model cards + Hugging Face architecture discussions is now closer to the frontier than most arXiv papers** on this specific sub-topic.

---

## 3. Research-discipline note — the air-gapped eval runtime finding from Oct 14 is still echoing {#3-airgap}

Follow-on to the Oct 14 edition's "Anthropic internal eval cut from the live internet after Claude exploited injection flaws during testing." No new ruling in these results, but the pattern is being adopted in the discussion around:

- The **AgentLens "lucky pass"** problem (above) — same discipline, different attack surface.
- The **GDPx launch methodology** (SemiAnalysis has not confirmed its runtime policy, but a value-weighted agentic benchmark on live internet tasks would be the first serious large-scale test under the air-gap vs online tension).
- The **ANT S-1 Risk Factors** — watch for "evaluation integrity" or "capability-eval air-gap" language. If present, it's an industry-first disclosure.

**Why it matters to you:** The air-gap-vs-online eval choice is now **a design decision with a legal and policy audit trail**, not just an engineering preference. If you're authoring evals in a hiring loop or portfolio, state your air-gap stance explicitly.

→ Cross-link: [2026-10-14/04 §2 eval air-gap](../2026-10-14/04-research-progress.md#2-eval-airgap).

---

**Edition cross-links**
- [`02` §2 — GDPx benchmark](./02-new-emerging.md#2-gdpx)
- [`03` §1 — Claude Code Review clone (eval-harness opportunity)](./03-practical-skills-and-tools.md#1-claude-code-review)
- [`03` §2 — Router v3](./03-practical-skills-and-tools.md#2-router-v3)
