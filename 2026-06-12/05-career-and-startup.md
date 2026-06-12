# Career & Startup — 2026-06-12

`#career #jobs #fde #mle #startups #hiring #new-grad`

---

## 1. AI Engineer remains #1 fastest-growing US job title (+143% YoY); but the entry-level rules just changed. {#1-ai-engineer-job-market}

**The headline data.**
- **AI Engineer = #1 fastest-growing US job title** (LinkedIn 2026), **+143% YoY** in postings.
- **35% of *all* entry-level US jobs now require AI skills** (NACE / LinkedIn / Indeed cross-source).
- **Employer projections: +5.6% hiring for class of 2026** — up but modest.
- **But — recent-grad unemployment is 5.7%** (22–27-year-olds), well above 4.2% overall workforce; **~43% of new grads underemployed**.
- **Skills breakdown for entry-level AI roles:** **Python 71% required, Java 22%, AWS 32.9%, Azure 26%.**
- **>75% of postings now prefer domain depth over breadth** — generalist resumes are getting filtered out.

**Sources.**
- [Pragmatic Engineer, "State of the software engineering job market in 2026"](https://newsletter.pragmaticengineer.com/p/state-of-the-job-market-2026) `[analysis]`
- [CNBC Select, "By the Numbers: What the class of 2026 job market actually looks like"](https://www.cnbc.com/select/class-of-2026-hiring-stats-and-ai-trends/) `[secondary]`
- [Hero Hunt, "Fastest Growing AI Roles in 2026: Data and Rankings"](https://www.herohunt.ai/blog/fastest-growing-ai-roles-in-2026-data-and-rankings/) `[analysis]`
- [Metaintro, "5.7% and Climbing — What the 2026 Job Market..."](https://www.metaintro.com/blog/new-grad-job-market-2026-ai-entry-level) `[analysis]`
- [Final Round AI, "Software Engineering Job Market 2026: Full Outlook for Developers"](https://www.finalroundai.com/blog/software-engineering-job-market-2026) `[analysis]`
- [IEEE Spectrum, "How to Stay Ahead of AI as an Early-Career Engineer"](https://spectrum.ieee.org/ai-effect-entry-level-jobs) `[analysis]`

**Why it matters to you.**
- **Job.** The 5.7% / 43% underemployment lines are the bear case. The +143% AI Engineer postings is the bull case. **They co-exist because the filter is now "demonstrably-deployed work."** Your weekend artifact ([03 §2](./03-practical-skills-and-tools.md#2-weekend-project)) is the specific response to this filter.
- **Job — entry-level lane.** Domain-depth-over-breadth (>75% of postings) means **pick one of the 5 AI sub-roles** (Applied / Platform / LLM / Product / Responsible — see [2026-05-16/05](../2026-05-16/05-career-and-startup.md#1-integration-engineer)) **and rewrite your resume headline to match by next Sunday**. Generalist headlines won't pass keyword filters anymore. (This is still open in [ACTIONS.md](../ACTIONS.md).)
- **Startup.** A 43% underemployed new-grad cohort is a *labor market arbitrage opportunity* for early-stage founders. "AI agent that ships 5 portfolio artifacts for a CS new grad in 4 weeks" is a wedge with real customer pain — file at fit-score 2 (consumer monetization is hard) in [STARTUPS.md](../STARTUPS.md).

`#jobs #ai-engineer #new-grad #2026 #hiring #unemployment`

---

## 2. Skill re-price: runtime structure > raw model knowledge. {#2-reprice}

**The shift you should bet on.** Three of this week's deepest signals converge:
1. **Tool-DC's +25.10% training-free gain** ([04 §1](./04-research-progress.md#1-tool-dc)) — **runtime structure** (divide-and-conquer) outperforms more training compute.
2. **`ml-intern` open release** ([04 §3](./04-research-progress.md#3-ml-intern)) — post-training is becoming an **agent-orchestrated process**, not a hand-tuned one.
3. **Microsoft MAI-Code-1-Flash priced under Haiku 4.5** ([01 §5](./01-big-lab-moves.md#5-microsoft-mai-code-1)) — raw model quality is being **commoditized at the price floor**.

**Translation for the resume.** Skills that *appreciated* this week:
- Eval-harness design (Tool-DC / MCP-Atlas / per-claim evals)
- Cost-aware routing (Opus-orchestrator / Sonnet-worker / MAI-cheap-leg)
- Verifier architecture (Haiku-verifier + Opus-agent ratio from [2026-05-19/04 §3](../2026-05-19/04-research-progress.md#3-trajad))
- TPU + GPU fluency (cf. [01 §2](./01-big-lab-moves.md#2-anthropic-broadcom))

**Skills that *depreciated*.**
- "Prompt engineering" as a standalone skill (commoditized; assume the recruiter assumes you can)
- Single-provider proficiency (multi-vendor is now production discipline)
- Model-rote-memorization (the model picker will pick for you; the skill is *evaluating* which one wins)

**Why it matters to you.**
- **Job.** Update LinkedIn skills tomorrow. Specifically delete "prompt engineering" and add **"eval-harness design"**, **"cost-aware agent orchestration"**, **"Tool-DC / MCP-Atlas methodology"**. The keyword filter is the gate.
- **Startup.** Anything that productizes "runtime structure" (verifier APIs, eval harnesses, routers) gets a Q3 2026 valuation lift. Anything that bets on "raw model improvements unlock my moat" gets commoditized.
- **Insight.** **The same skill re-price happened in 2018 with software engineering** (rote-coding → systems thinking). What changes now is the time scale: the re-price compresses into 8–12 weeks instead of 3 years.

`#skills #careers #reprice #portfolio #linkedin`

---

## 3. New career lane: TPU-native infra (Broadcom, Marvell, Google Cloud TPU). {#3-tpu-lane}

**Why it just opened.** [01 §2](./01-big-lab-moves.md#2-anthropic-broadcom) — Anthropic's 3.5 GW TPU deal means Broadcom + Marvell are now structurally NVIDIA's secondary competitors at the AI-accelerator layer. **Mizuho models $42B Broadcom AI revenue from Anthropic alone in 2027.** The hiring follows the dollars.

**Concrete roles to file in [APPLICATIONS.md](../APPLICATIONS.md).**

| Company | Role family | Why apply |
|---|---|---|
| **Google Cloud TPU** | Software Engineer — TPU Platforms (L4-L6) | The mothership; deepest TPU stack experience |
| **Broadcom** | Software Engineer — AI / ML Accelerator Tooling | Front-row to the 3.5 GW build |
| **Marvell** | ML Compiler Engineer | NVIDIA's other secondary; smaller team, faster ramp |
| **Crusoe** | Data Center Software Engineer | Energy + compute; fits with the Anthropic compute thread |
| **OpenAI** | Hardware Software Engineer (Stargate group) | The NVIDIA mirror of this lane |
| **Cerebras / Groq** | Compiler / Systems Engineer | Long-shot but the comp data is interesting |

**Skill prep gaps to close (60–90 min).**
- Read [Google Cloud TPU architecture overview](https://cloud.google.com/tpu/docs/system-architecture-tpu-vm) and one **JAX** tutorial (the JAX/TPU pairing is the hiring filter).
- Read **OpenXLA** intro — the abstraction layer that makes JAX/PyTorch/TensorFlow portable across TPU/GPU.

**Sources.**
- [Yahoo Finance — 3.5 GW TPU deal](https://finance.yahoo.com/sectors/technology/articles/anthropic-secures-access-3-5-124717374.html) `[secondary]`
- [TechCrunch — Anthropic compute deal](https://techcrunch.com/2026/04/07/anthropic-compute-deal-google-broadcom-tpus/) `[secondary]`

**Why it matters to you.**
- **Job.** This is the **non-overlapping lane** with your default Anthropic-Solutions queue. Filing one Broadcom or Marvell app this month *diversifies* your job-market exposure.
- **Startup.** TPU-portability tooling is a wedge in [STARTUPS.md](../STARTUPS.md); doing it from the inside (i.e., as an employee) compounds your customer-discovery.
- **Insight.** The labor-market timing of this lane: **most CS grads don't know Broadcom hires ML engineers in volume.** That ignorance is your edge for the next 60 days.

`#jobs #tpu #broadcom #marvell #ml-systems #infrastructure`

---

## 4. Programs & deadlines — June 2026 windows still open. {#4-programs}

Update [APPLICATIONS.md](../APPLICATIONS.md) with the following deadlines (cross-confirm each before submitting):

| Program | Status | Deadline | Action |
|---|---|---|---|
| OpenAI Residency 2026 | ⚪ open | TBD — confirm via [openai.com/careers](https://openai.com/careers) | Submit this month per [ME.md](../ME.md) |
| Anthropic AI Safety Fellowship | ⚪ open | TBD — confirm via [anthropic.com/careers](https://www.anthropic.com/careers) | Submit this month |
| Google DeepMind Early Career | ⚪ open | TBD — confirm | Submit this month |
| Workday × Anthropic Solopreneurship Accelerator | ⚪ open | Per [2026-05-19/05 §5](../2026-05-19/05-career-and-startup.md#5-workday-solopreneur) — 15 slots | Apply by next Sunday |
| **(NEW)** OpenAI Deployment Engineer (FDE) | ⚪ open | Rolling | Apply alongside Anthropic Solutions weekly |
| **(NEW)** Broadcom AI Compiler Engineer | ⚪ open | Rolling | First non-frontier-lab app this month |

`#programs #residencies #fellowships #deadlines`

---

## 5. Founder lens — Prometheus + NEURA reframe the wedge map. {#5-founder-lens}

After today's [02 §1–2](./02-new-emerging.md#1-prometheus), file these wedge adjustments in [STARTUPS.md](../STARTUPS.md):

| Wedge | Adjustment | Reason |
|---|---|---|
| Industrial / Physical-AI software layer | Add at fit-score 3 | Prometheus + NEURA create a market for upstream tooling |
| CAD-to-LLM tokenization | Add at fit-score 3 | Adjacent to Prometheus; not a competitor |
| Agent-to-agent commerce infra | Promote to fit-score 4 | AgenticPay paper ([04 §4](./04-research-progress.md#4-arxiv-quick-hits)) + Decagon/Sierra-style buyers |
| Cost-aware multi-provider router | Lower urgency (window narrowed) | Microsoft Copilot Desktop entered the same surface ([01 §5](./01-big-lab-moves.md#5-microsoft-mai-code-1)) |
| Pre-deployment eval-as-a-service | Re-activate (was dropped on May 22) | G7 summit ([01 §1](./01-big-lab-moves.md#1-g7-summit)) could re-create the buyer |

`#startups #wedges #wedge-map #physical-ai`

---

## This week's actions (added to [ACTIONS.md](../ACTIONS.md))

1. **Tonight (5 min)** — toggle Agent SDK credit ([03 §1](./03-practical-skills-and-tools.md#1-agent-sdk-t-3))
2. **Tomorrow (15 min)** — LinkedIn skills update: delete "prompt engineering", add "eval-harness design", "cost-aware orchestration", "Tool-DC/MCP-Atlas" (§2)
3. **This week (60 min)** — 1 Anthropic Solutions app + 1 OpenAI FDE app + 1 *Broadcom or Google TPU* app (§3)
4. **Weekend (4 hr)** — reframed sanitiser project ([03 §2](./03-practical-skills-and-tools.md#2-weekend-project))
5. **Sunday (30 min)** — write `weeks/2026-06-08.md` rollup (NEW convention starting this week — see [weeks/README.md](../weeks/README.md))

`#actions #weekly-plan`

---

## Cross-links

- **TLDR:** [`00`](./00-tldr.md)
- **Compute lane (TPU):** [`01` §2](./01-big-lab-moves.md#2-anthropic-broadcom)
- **Microsoft entry (decision tree):** [`03` §3](./03-practical-skills-and-tools.md#3-coding-agent-decision)
- **Skill anchor (Tool-DC):** [`04` §1](./04-research-progress.md#1-tool-dc)
- **Startup wedges:** [STARTUPS.md](../STARTUPS.md)
- **Applications:** [APPLICATIONS.md](../APPLICATIONS.md)
