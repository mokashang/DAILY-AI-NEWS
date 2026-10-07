# Career & Startup — 2026-07-18

Everything mapped to your two goals ([ME.md](../ME.md)): **(1) do a startup** · **(2) find an SDE/MLE/AI Integration / FDE role**.

Tags: `#careers #startup #ode #anthropic #artifact-shipping #saturday`

---

## 1. The Saturday triple-signal — three stories, one hire {#1-triple-signal}

**What today's editions add up to.** Three stories that landed inside 72 hours all point at **the same career question**:

1. **Open-frontier bipolar race** ([`01` §1](./01-big-lab-moves.md#1-kimi-k3), [`02` §1](./02-new-emerging.md#1-open-weights-week)) — Kimi K3 + Inkling means US-lab-only stacks are no longer defensibly the "best answer" for cost-sensitive workloads. Someone has to run the evaluation.
2. **Gemini 3.5 Pro no-show** ([`01` §2](./01-big-lab-moves.md#2-gemini-no-show)) — "vendor announced ≠ available" is now a production concern, not a philosophical one. Someone has to build the probes.
3. **Microsoft Project Perception launches with multi-model bundling** ([`01` §4](./01-big-lab-moves.md#4-project-perception)) — even the hyperscalers now sell "the best mix" rather than "our model." Someone has to defend which model for which task.

**All three point at the same hire.** An engineer who can:
- **Evaluate** across US-open + China-open + US-closed frontier models (Kimi K3, Inkling, Fable 5, GPT-5.6, Grok 4.5)
- **Route** per-task based on cost × quality × availability × jurisdiction
- **Verify** each output against a JSON schema (defeat fabrication)
- **Defend** the routing choice to a client, an auditor, and an investor in three different pitch formats

That is **the AI Integration Engineer** ([ME.md's committed lane](../ME.md)) — and today's news put the *skill-price* on this hire ~15-20% higher than it was on Friday.

**Your action.** Ship [§3](#3-artifact-brief) below (3×3 evaluation matrix). Follow with [§2](#2-ode-followup) (Ode/Anthropic/Together/Ollama applications Sunday). Update [ME.md and STARTUPS.md](#4-wedges) with today's shifts.

Tags: `#triple-signal #integration-engineer #artifact-shipping`

---

## 2. Ode with Anthropic — follow-through window is TODAY through Tuesday {#2-ode-followup}

**Recap.** Yesterday's [`05` §1](../2026-07-17/05-career-and-startup.md#1-ode-fde) added **Ode with Anthropic** ($1.5B, Chris Taylor CEO, Fractional AI base, PE-portfolio mandate) as the **single most important named-employer story of the month** for the FDE career path.

**Where things stand (Sat AM).**
- **[APPLICATIONS.md](../APPLICATIONS.md) status:** Ode + Anthropic + OpenAI Deployment Company applications ⚪ queued from Jul 17. If not submitted, **submit today or tomorrow** — the "before-the-wave" window is 3-5 days from launch.
- **Cover-letter update opportunity:** the 3×3 matrix from [§3](#3-artifact-brief) becomes your **hero artifact**. Reference the Kimi K3 vs Fable 5 numbers as your *specific* evidence of client-workload evaluation skill — this is the *exact* thing an Ode FDE does daily inside a PE-portfolio-company deployment.

**Cover-letter close (paste template — edit).**

> This weekend I shipped a 3×3 evaluation matrix (structured extraction / MCP tool-use / agentic coding × Kimi K3 hosted / Inkling hosted / Fable 5) with per-completed-task cost, schema-conformance rate, and tool-call fabrication rate captured. On my top workload, Kimi K3 hosted came in at ~$X per completed task with Y% schema pass; Fable 5 at ~$11.80 per task with Z% pass — the ~[cost delta] gap is defensible only on the top ~20% of tasks by downside cost. This is the framework I'd bring to a Blackstone-portfolio deployment.

**Then:** log the submissions in [APPLICATIONS.md](../APPLICATIONS.md) with links to the specific job postings + your artifact repo URL.

**Sources / references.**
- [Ode press release (Jul 15)](https://www.businesswire.com/news/home/20260715205134/en/Anthropic-Blackstone-and-Hellman-Friedman-Introduce-Ode-with-Anthropic-an-Enterprise-AI-Services-Firm) `[primary]`
- [Ode careers page](https://www.ode.com/careers) `[primary — check daily for new posts]`
- [Anthropic careers](https://www.anthropic.com/careers) — filter Solutions / FDE / Integration
- [OpenAI Deployment Company careers](https://openai.com/careers) — filter FDE
- Prior context: [2026-07-17/05 §1 Ode as career lever](../2026-07-17/05-career-and-startup.md#1-ode-fde)

Tags: `#ode #anthropic #openai #applications #cover-letter`

---

## 3. Saturday artifact brief — the 3×3 open-vs-closed evaluation matrix {#3-artifact-brief}

**Deliverable.** A **public GitHub repo** with a 3-task × 3-model-family evaluation matrix that answers the exact question Ode / Anthropic / Together / Ollama ask in FDE screens: **"How do you pick which model to deploy for a client workload?"**

**The 3×3 matrix.**

|  | **Structured extraction** (20 tasks) | **MCP tool-use** (20 tasks) | **Agentic coding** (20 tasks) |
|---|---|---|---|
| **Kimi K3 hosted** (OpenRouter) | pass rate · $/task · schema-OK % | pass rate · $/task · fabrication % | pass rate · $/task · pass@3 |
| **Inkling hosted** (Databricks/HF Inference) | pass rate · $/task · schema-OK % | pass rate · $/task · fabrication % | pass rate · $/task · pass@3 |
| **Fable 5** (Anthropic — capture BEFORE Sun midnight, [§1 of `03`](./03-practical-skills-and-tools.md#1-fable-5-evals)) | pass rate · $/task · schema-OK % | pass rate · $/task · fabrication % | pass rate · $/task · pass@3 |

**Repo shape.**

1. **`README.md`** — opens with:
   - **The single most important chart of the week:** Kimi K3 at #1 on Frontend Code Arena vs Fable 5 (screenshot from Arena / [Tom's Hardware writeup](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3))
   - The **3×3 matrix filled in with your empirical numbers**
   - **1-paragraph interpretation** — which model wins which workload and why; where a cost-aware router would fall through vs stay-put
   - **Citations:** [Kimi K3 (Moonshot, Jul 16)](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3), [Inkling (TML, Jul 15)](https://thinkingmachines.ai/news/introducing-inkling/), [Fable 5 baseline (Artificial Analysis)](https://artificialanalysis.ai/), [Willison Jul 4 on tool-call fabrication](https://simonwillison.net/2026/Jul/4/better-models-worse-tools/)
   - **"How I'd extend for production"** — a paragraph naming: **provider-availability probe** ([`03` §3](./03-practical-skills-and-tools.md#3-provider-probe)), **cache-hit-rate audit + reordering** ([`03` §5](./03-practical-skills-and-tools.md#5-cache-hit-followup)), **cost budgets per user**, **circuit-breaker on schema-verify fail rate**

2. **`router.py`** — 150 LOC. Three-model chain with schema-verify at each hop + fall-through cost accounting. Same shape as [2026-05-22 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)'s Opus-orchestrator/Sonnet-worker but with **open + closed frontier legs**. Include the [availability probe from `03` §3](./03-practical-skills-and-tools.md#3-provider-probe) at boot.

3. **`schemas/`** — one JSON schema per workload (invoice-extraction, MCP-tool-call, structured-code-diff).

4. **`eval/`** — 20 tasks per workload × 3 models × 3 runs each = 180 evaluations. Deterministic seed. Save to `logs/results.csv` in the schema: `task_id, model, cost_usd, latency_s, pass, schema_ok, fabrication_flags, run`.

5. **`docs/methodology.md`** — 500 words. Cite [MiroEval two-axis process+outcome scoring](./04-research-progress.md#4-arxiv-breadth). Explain the **80/20 rule for defensible routing** — you route to cheaper models on the 80% of tasks where quality gap doesn't dominate, and to premium models on the 20% where downside cost > cost delta.

6. **`LICENSE`** — MIT. **Demo GIF** at README top (2 min).

**Time budget.** 5-7 hours. Cadence-over-intensity discipline. Don't polish past that. Ship publicly on GitHub *tonight* (Sat), post about it *Sunday morning*.

**Sunday morning follow-up (30 min).**
- **LinkedIn post:** 4 bullets — (1) Kimi K3 landed #1 on Frontend Code Arena, (2) here's the 3×3 matrix on my task suite, (3) empirical Grok routing threshold on my workload was ~[X]%, (4) here's the repo. **Include the Arena chart.**
- **Reference the repo in the Ode + Anthropic + Together + Ollama applications** ([§2](#2-ode-followup) above).
- **Log all outputs in [APPLICATIONS.md](../APPLICATIONS.md).**

**Metric of success.** ≥1 reply from a target-company employee OR ≥1 recruiter contact in the following 7 days. Log outcome in [APPLICATIONS.md](../APPLICATIONS.md) reflection cadence.

Tags: `#artifact #saturday #router #evaluation-matrix #kimi-k3 #inkling #fable-5`

---

## 4. Startup wedges — reprioritization from today's news {#4-wedges}

Updates to [STARTUPS.md](../STARTUPS.md):

**Promote to fit-5:**
- **Cost-aware multi-provider model router (with jurisdiction toggle)** — Kimi K3 open-weights ([`01` §1](./01-big-lab-moves.md#1-kimi-k3)) + Inkling ([`02` §1](./02-new-emerging.md#1-open-weights-week)) + WAICO sovereignty signal ([`01` §3](./01-big-lab-moves.md#3-waic-day-2)) mean this wedge now has **US-closed + US-open + China-open + jurisdiction-aware** — four dimensions instead of two. Artifact for this weekend is the MVP; hosted product is 60-day roadmap.
- **Trajectory-verifier / policy-eval as a Perception+Mythos backend** — [`01` §4](./01-big-lab-moves.md#4-project-perception): Microsoft Project Perception's launch as multi-model control plane creates a *shared* need for OpenTelemetry-style verifier plugins. Buyer: any AI-security vendor.

**Add at fit-4 (new wedges from today):**
- **"Kimi K3 for regulated Global South" hosting + fine-tuning SaaS** — [`02` §5](./02-new-emerging.md#5-kimi-hosting): ~10-40× cost delta vs Fable 5 + no US-lab plausible competitor under WAICO regulation = real buyer. Small ACVs ($5-25K/mo), high volume.
- **Jurisdiction-aware model routing (WAICO-stack vs US-allied-stack)** — [`01` §3](./01-big-lab-moves.md#3-waic-day-2): sovereignty is now a legitimate deployment concern in mid-market deals; no purpose-built product yet.

**Carry (no change):**
- Vertical-CX-agent for regulated industries (fit-4) — Anthropic HIPAA self-serve helps, doesn't kill.
- All May-19 wedges from [STARTUPS.md](../STARTUPS.md) — unchanged.

**Demote / drop:**
- **Stand-alone "AI security control plane"** — do NOT build; second-mover against Microsoft + Anthropic. Pivot the idea to the trajectory-verifier backend above.

Tags: `#startups #wedges #reprioritization`

---

## 5. WAICO-adjacent programs to watch (5-min/week, rolling) {#5-waico-programs}

**Speculative but real, updated from [2026-07-18/01 §3](./01-big-lab-moves.md#3-waic-day-2).** WAICO now has:
- **A named home** — Shanghai HQ.
- **A staffed program** — 5,000 training seats over 5 years.
- **4 named partner blocs** — ASEAN, Arab League, African Union, BRICS.

**Adjacent programs to add to [APPLICATIONS.md](../APPLICATIONS.md) monitoring** (rolling, 5 min/week):
- **UN AI Advisory Body** — fellowships / secondments; watch [UN careers site](https://careers.un.org/).
- **UNCTAD digital economy program** — capacity-building roles.
- **World Meteorological Organization** — the 30-country weather-warning system deployment creates real posted-role opportunity.
- **ASEAN AI Task Force** — regional AI-policy work; watch [asean.org](https://asean.org/).
- **African Union AI Strategy office** — same shape.
- **[LSE / Oxford / MIT MIT-IPRI / Georgetown CSET]** — Western fellowships that would fund WAICO-observer research; check [aideadlin.es](https://aideadlin.es/) monthly.

**Application move to make this month (long game).** Draft a **500-word statement of interest** on "AI capacity-building for the Global South" and keep it ready — the first 100 candidates for the WAICO-related fellowships will win because they applied in the first 2 weeks. Don't build a portfolio artifact specifically for this; the [`03` §3](./03-practical-skills-and-tools.md#3-provider-probe) provider-probe + [`05` §3](#3-artifact-brief) 3×3 matrix cover it well enough for framing.

Tags: `#waico #un #reach-lane #long-game #policy`

---

## Personal-rules check — Saturday cadence

- **Artifact this weekend:** ✅ scoped in [§3](#3-artifact-brief) — 3×3 open-vs-closed evaluation matrix
- **Weekly Anthropic + Ode application:** carry from [Fri](../2026-07-17/05-career-and-startup.md#1-ode-fde) — submit today or Sunday
- **Monthly AI-spend audit:** next Aug 4
- **Monthly SOURCES.md re-read:** next Aug 19 — pre-flag [Sebastian Raschka's blog](https://sebastianraschka.com/blog/2026/inkling-architecture-benchmark-notes.html) as already-included Tier-8 confirmation
- **New tags this edition:** `#kimi-k3`, `#inkling`, `#waico-day-2`, `#project-perception`, `#oracle-stargate`, `#fable-5-sunset`, `#raschka` — added to grep-vocabulary

## Cross-references

- [ME.md](../ME.md) — no change to committed lane (AI Integration Engineer); Job-search targeting stays as [May 25 revision](../ME.md)
- [WATCHLIST.md](../WATCHLIST.md) — 4 new rows per [`00` deltas](./00-tldr.md#watchlist-deltas)
- [APPLICATIONS.md](../APPLICATIONS.md) — Ode + Anthropic + OpenAI Dep Co queued from yesterday; add **Together AI + Ollama** this Sunday
- [STARTUPS.md](../STARTUPS.md) — see [§4](#4-wedges) reprioritization
- [ACTIONS.md](../ACTIONS.md) — this weekend's checklist refreshed
