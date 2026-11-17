# 05 — Career & Startup — 2026-07-07

## 1. The class-of-2026 job market — what actually shipped {#1-market-numbers}

Fresh mid-year data:

- **New-grad hiring +5.6% YoY** (employer projections for class of 2026).
- **77.2%** of recent grads landed a role **within 3 months** of graduating.
- **35%** of entry-level jobs now require **AI skills** — up from ~5% two years ago.
- **MLE market:** projected to hit **~$113B in 2026** → **~$503B by 2030**. **Only 6%** of ML Engineer JDs are entry-level.
- **Demand/supply gap:** **~1.6M open AI/ML roles vs. ~518K qualified candidates → 3.2:1**. Average MLE salary reported at **~$133K/year** (broad average; frontier-lab TC is far higher).
- **Top-5 metros:** Silicon Valley, Seattle, NYC, San Francisco, Boston.

**Read for you:**
- The **overall market is up**, but the **entry-level share of MLE roles is still small** (~6%). Your path is not "apply to entry-level MLE" — it's **"apply to AI Engineer / FDE / Integration / Applied AI / Solutions"** roles where the entry-level share is meaningfully higher and the AI skill premium is what you're being paid for.
- The **3.2:1 supply gap is a headline number** — but it's for **the aggregate market**. At the frontier labs and top vertical-AI companies, the ratio is inverted. Which is why lens #2 below matters more than #1.

**Sources.**
- [secondary] [CNBC Select — "By the Numbers: What the class of 2026 job market actually looks like"](https://www.cnbc.com/select/class-of-2026-hiring-stats-and-ai-trends/)
- [analysis] [365 Data Science — "AI Engineer Job Outlook 2026"](https://365datascience.com/career-advice/career-guides/ai-engineer-job-outlook-2025/) · [MLE outlook](https://365datascience.com/career-advice/machine-learning-engineer-job-outlook/) · [MLE top skills & trends](https://365datascience.com/career-advice/career-guides/machine-learning-engineer-job-outlook-2025/)
- [analysis] [daily.dev Recruiter — "How to Recruit AI/ML Engineers in 2026"](https://recruiter.daily.dev/resources/recruit-ai-machine-learning-engineers/) (source of the 3.2:1 ratio)
- [analysis] [Public Insight — AI/ML Job Trends](https://publicinsight.io/ai-and-machine-learning-job-trends/)
- [analysis] [Simplilearn — 2026 AI/ML Job Trends](https://www.simplilearn.com/rise-of-ai-and-machine-learning-job-trends-article)
- [primary] [GitHub — 2027 AI College Jobs (daily-updated)](https://github.com/speedyapply/2027-AI-College-Jobs)
- [primary] [GitHub — 2026 AI College Jobs / NEW_GRAD_USA](https://github.com/speedyapply/2026-AI-College-Jobs/blob/main/NEW_GRAD_USA.md)
- [primary] [ZipRecruiter — MLE New Grad](https://www.ziprecruiter.com/Jobs/Machine-Learning-Engineer-New-Grad)

---

## 2. Skill re-price — multi-vendor cost-aware verification is the 2026 hire signal {#2-skill-reprice}

Three converging pieces of today's news re-price your resume skills.

| Signal | What it means for your resume |
|---|---|
| **Sonnet 5 intro $2/$10 through Aug 31** | Your work-samples should be built **on Sonnet 5** through August. "I shipped X on Sonnet 5" reads as **current** in interviews from Aug through Q4. |
| **GLM 5.2 within 1 pt of Opus 4.8 at ~1/5 cost** | Add **multi-vendor cost benchmarking** to your resume. Include GLM 5.2 alongside GPT-5.5 + Sonnet 5. Very few candidates have this. |
| **Real-tool eval wave (MCP-Bench / LiveMCP-101 / Odysseys)** ([`04` §1](./04-research-progress.md#1-real-tool-eval)) | "Ran N cases on a real MCP server + logged cost + logged failure mode" is a **portable interview claim**. Beats "used LangChain." |

**The skill triad to lead with in every 2026 AI Engineer / FDE / Integration interview:**

1. **Model + vendor routing** — "I pick the right model for the right step and know the cost curve."
2. **Real-tool verification** — "I don't ship a demo; I ship an eval against real tools."
3. **Cost-aware engineering** — "I show you the cost per successful task, not the cost per token."

If your GitHub doesn't have one artifact that visibly demonstrates all three, that's the artifact to build this weekend ([`03` §2](./03-practical-skills-and-tools.md#2-portable-interview-artifact)).

---

## 3. Apply this week — target list, refreshed for today's news {#3-apply-this-week}

**Priority applications (Tue–Fri this week):**

- **Tenex.AI** — Series B just closed at **$250M**; hiring across **AI Security Engineer / SOC Automation / FDE-Security**. Category is thin, well-paid, and pairs with the White House framework's cyber-clearinghouse angle ([`01` §1](./01-big-lab-moves.md#1-openai-govt-stake)).
- **Avoca** — **$125M Series B**; hiring for **AI Engineer / CX Deployment**; General Catalyst + Meritech-backed. Framework CX is a beachhead vertical.
- **Anthropic — Solutions Engineer / FDE / Integration Engineer** — Sonnet 5 launch = **fresh customer-ramp demand**. Target the Solutions org.
- **Taktile** — **$110M Series C**; **AI Integration / Decisioning Engineer** for regulated fintech. Higher signal-to-noise than most fintech AI teams.
- **OpenAI FDE / Solutions** — the govt-equity story will (paradoxically) accelerate enterprise + public-sector hiring while the vehicle is being negotiated.
- **Meta Compute** — brand-new unit ([`01` §3](./01-big-lab-moves.md#3-meta-compute)); **Systems Engineer + AI Infra + Customer Engineering** roles will open within 2–4 weeks. Set alerts now.
- **CoreWeave / Nebius / IREN** — despite the July 1 selloff, these still hire aggressively, and the **defensive-hire signal** post-Meta-Compute makes them attractive for **AI Infra** roles you can grow into.

**Reach lane (worth the shot):**
- **Anthropic AI Safety Fellowship**, **OpenAI Residency 2026**, **Google DeepMind Early Career**, **CAISI pre-deployment eval track** (new lane opening around the framework).

**Weekly application-tempo goal:** 5 targeted applications + 3 warm intros per week. Log outcomes in [`APPLICATIONS.md`](../APPLICATIONS.md).

**Sources.**
- See funding-round sources in [`02` §2](./02-new-emerging.md#2-agentic-vertical-b-wave).
- [primary] [YC AI Companies — hiring list](https://www.ycombinator.com/companies/industry/ai)
- [primary] [startup.jobs — ML](https://startup.jobs/machine-learning-jobs) · [Indeed MLE new grad](https://www.indeed.com/q-machine-learning-engineer-new-grad-jobs.html) · [Glassdoor MLE new grad](https://www.glassdoor.com/Job/machine-learning-new-grad-jobs-SRCH_KO0,25.htm) · [newgrad-jobs.com](https://www.newgrad-jobs.com/)

---

## 4. Startup wedge log — today's inputs {#4-wedges}

Three fresh wedges you can put into [`STARTUPS.md`](../STARTUPS.md):

- **Cost-router-for-mid-market-AI-apps** — combine Sonnet 5 + GLM 5.2 (via OpenRouter) + prompt caching + Tool Search behind one API. Sell **per-successful-task pricing**. TAM: any AI-product team spending $10K+/mo on inference. Anchor comps: [Portkey](https://portkey.ai/), [OpenRouter](https://openrouter.ai/), Judgment Labs (eval side).
- **Sovereign / regulated compliance shim for open-weights** — GLM 5.2 is legally deployable in EU/US regulated verticals *only with the right compliance wrapper*. That wrapper is a product. Anchor comp: Nvidia NeMo Guardrails (adjacent), but no clear pure-play compliance-only vendor.
- **Physical-AI eval harness** — Machina Summit is today ([`02` §3](./02-new-emerging.md#3-machina-summit)). The eval literature caught up on text agents (MCP-Bench, LiveMCP-101, Odysseys). Physical AI is where text-agents were 18 months ago. Build the **MCP-Bench of robotics**.

**Your-fit scoring — a first pass:**

| Wedge | Founder-market fit for you | Time to first artifact | Cap-ex risk |
|---|---|---|---|
| Cost-router | **High** — matches your Anthropic focus + agent stack | 2 weekends | Low |
| Compliance shim | Medium — depends on legal-network access | 4–6 weekends | Low |
| Physical-AI eval | Medium — depends on your sim/robotics comfort | 4–8 weekends | Med |

---

## Job · Startup · Insight — the compact take

- **Job:** Ship the **3-vendor eval + cost artifact** ([`03` §2](./03-practical-skills-and-tools.md#2-portable-interview-artifact)) this weekend. Apply to **Tenex + Avoca + Anthropic Solutions** by Friday.
- **Startup:** Cost-router-for-mid-market is the **highest founder-market fit** on today's board. Two weekends to first artifact.
- **Insight:** The **hiring signal for 2026 = "multi-vendor, real-tool-verified, cost-aware"** — not "prompt-engineering." Every artifact you ship this quarter should visibly show all three.
