# Career & Startup — 2026-06-10

The actionable career-and-startup story this week sits at the **intersection of three things you've been tracking**: the **FDE / Integration Engineer hiring wave is now industry-wide** (Anthropic, OpenAI, Cohere, Scale, Mistral are all explicitly staffing this lane), the **Mythos-class ship** ([`01` §1](./01-big-lab-moves.md#1-fable-mythos)) made the "Anthropic-stack-depth" thesis from your `ME.md` measurably correct, and the **Managed Agents update** ([`03` §1](./03-practical-skills-and-tools.md#1-managed-agents)) gives you a single weekend artifact that demonstrates exactly the skills these roles screen for. The shipping bar moved this week — and it moved in a direction that favors *you specifically*.

Tags: `#careers #startup #fde #integration-engineer #anthropic #residency #portfolio`

---

## 1. The FDE / Integration Engineer wave is now industry-wide {#1-fde-hiring}

**What happened:** Multiple market-mapping pieces this week confirm what's been an Anthropic-led story extends across the frontier-and-near-frontier set:

- **Both OpenAI and Anthropic** (plus **Cohere, Scale, Mistral**) are aggressively staffing **Forward Deployed Engineers (FDEs)** — the customer-facing role that *builds the thing* at the customer site.
- **Anthropic's pitch to candidates:** "If you have done interesting independent research, written an insightful blog post, or made substantial contributions to open-source software, **put that at the TOP of your resume.**" Roughly **50% of technical staff have PhDs** — meaning *half don't*. The bar is artifact-driven.
- **OpenAI Residency 2026:** 6-month program; $18,333/month (~$220k annualized); designed for career-changers from physics, math, neuroscience, or SWE who *don't* have formal ML experience.
- **Broader hiring climate context:** New-grad hiring at top general-tech companies is **down 50%+** vs prior years, but the AI-specialty market still rewards *production skills > credentials, depth > breadth, connections > cold applications*.
- **Open Anthropic role (live this week):** [Forward Deployed Engineer, Applied AI](https://job-boards.greenhouse.io/anthropic/jobs/4985877008).

**Sources:**
- [DataExec — Breaking Into AI in 2026: What Anthropic, OpenAI, and Meta Actually Hire For](https://dataexec.io/p/breaking-into-ai-in-2026-what-anthropic-openai-and-meta-actually-hire-for) `[analysis]`
- [Sundeep Teki — How to Get Hired at OpenAI, Anthropic & DeepMind in 2026](https://www.sundeepteki.org/advice/how-to-get-hired-at-openai-anthropic-and-google-deepmind-in-2026) `[analysis]`
- [Anthropic — Careers](https://www.anthropic.com/careers) `[primary]`
- [Anthropic — Jobs board](https://www.anthropic.com/careers/jobs) `[primary]`
- [Anthropic — Forward Deployed Engineer, Applied AI](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) `[primary]`
- [OpenAI — Careers Search](https://openai.com/careers/search/) `[primary]`
- [MarkTechPost — What is a Forward Deployed Engineer: The AI Role OpenAI, Anthropic, and Google Are Hiring in 2026](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/) `[analysis]`
- [The New Stack — Why OpenAI and Anthropic are hiring forward deployed engineer teams](https://thenewstack.io/forward-deployed-engineers-ai/) `[analysis]`
- [Perspective AI — Anthropic Applied AI Engineer Interview Process](https://getperspective.ai/blog/anthropic-applied-ai-engineer-interview-process-frontier-lab-2026) `[analysis]`

### Why it matters to you

- **Job lens (specific actions):**
  1. **Apply** to the live Anthropic FDE role this week. Yes, it nominally wants 3+ years of "customer-facing" experience — **your weekend artifact replaces that.** Lead the resume with: (a) the Mythos-class-aware routing demo, (b) the Managed-Agents scheduled MCP server, (c) the cost-per-resolved-task ledger.
  2. **Re-write the top of your resume** in Anthropic's pattern: *artifact → outcome → tools used → cost numbers*. Not *role → company → bullets*.
  3. **OpenAI Residency** is your fallback if Anthropic doesn't move — apply in parallel; the residency is *explicitly* for people without formal ML credentialing.
  4. **Cohere / Scale / Mistral** are the *less-crowded* side of the same wave. Apply broadly — your `ME.md` already has these as adjacent targets.
- **Startup lens:** The FDE wave is a tell about *where the frontier labs are still bottlenecked*. They have great models; they don't have enough humans who can sit with an enterprise customer and ship a thing on the model. **Three startup wedges** in that gap: (a) an **agency** that does this work for mid-market customers (lower-cost FDE-as-a-service); (b) a **tooling platform** that makes a single FDE 3× more productive (templated MCP servers, scheduled-agent factory, eval-set generator); (c) **an off-the-shelf vertical product** that *replaces* the FDE engagement entirely (the truly disruptive bet — pick a vertical with clear ROI math).
- **Insight:** FDE is the **most leveraged** non-research career bet in AI right now. You sit between the model's capability and the customer's wallet — both sides have to convince you they're worth the engagement. The work scales the labs faster than retraining the model would. Optimize for it.

→ Cross-link: [`03` §1 the weekend-artifact build path that this lane screens for](./03-practical-skills-and-tools.md#1-managed-agents) · [2026-05-22/05 §3 Meta-alumni reply window (still live)](../2026-05-22/05-career-and-startup.md#3-meta-followup).

---

## 2. The shipping bar just moved — and it favors you {#2-shipping-bar}

**What happened:** Across this week's stories, the *shape* of "what counts as a good portfolio artifact" sharpened materially:

- **Managed Agents** ([`03` §1](./03-practical-skills-and-tools.md#1-managed-agents)) shifted the bar from *"I built a Claude Code session"* to *"I shipped a scheduled, sandboxed, MCP-bound service with cost logs."*
- **Mythos-class routing** ([`01` §1](./01-big-lab-moves.md#1-fable-mythos)) added a *"and I made a non-trivial model-routing choice with cost rationale"* requirement.
- **AlphaEvolve's production-shipping** ([`04` §1](./04-research-progress.md#1-alphaevolve)) raised the implicit standard: *"and I designed both the generator and the evaluator, not just the prompt."*

Put together — the **2026 portfolio template** for an AI-job seeker is roughly:

> *A real (small) workflow, shipped as a scheduled Managed Agent, calling a private MCP server, with explicit model routing across 2–3 tiers, a clean eval set (5+ planted cases), and per-step cost numbers. README explains the routing decision, cites the eval, and shows the cost-per-resolved-task delta vs. the naive single-model approach.*

This is *one* artifact, but it answers **the interview questions for four different roles** (FDE, Integration Engineer, AI Engineer, Customer Eng).

### Why it matters to you

- **Job lens:** Your `ME.md` already has four portfolio bullets queued. **This week's news collapses three of them into a single weekend build** (Public MCP server + Vertical-Claude-for-X workflow + Personal Claude billing audit). One ship beats three half-ships. **Do this Sunday — June 14 — *before* the June 15 SDK metering change** so you can include "first build under the new metering regime" as an additional narrative thread.
- **Startup lens:** The same artifact, with a customer logo on it, is a **founding-engineer pitch**. The artifact-as-pitch flow: build it for yourself → run it on a friend's company's repo → write the case study → use the case study to start three customer conversations. Three conversations is enough to know whether you have a startup.
- **Insight:** **You are now over-qualified-on-paper for the job market you're targeting, *if* you ship one artifact in the next 7 days.** The bar's shape changed in a way that rewards exactly what you already invested in (Anthropic stack, MCP, cost discipline). The remaining risk isn't capability — it's *shipping*. Set the deadline. Ship the artifact.

→ Cross-link: [`03` §1 the build path](./03-practical-skills-and-tools.md#1-managed-agents) · [`01` §1 Fable 5 numbers to cite in the README](./01-big-lab-moves.md#1-fable-mythos).

---

## 3. Startup-thesis pattern-match from this week's funding {#3-startup-pattern-match}

**What happened:** [`02` §3](./02-new-emerging.md#3-funding-megarounds) covered the three big rounds (Suno $400M, Generalist AI $400M, Flourish $500M). The *founder takeaway* is the **pattern-match each round implies**:

| Round | Lead | Implicit pattern that won |
|---|---|---|
| **Suno $400M (Series D)** | Bond | *Vertical distribution* — a consumer-platform fund leading a 4th-round AI company. Bet: AI music becomes a mass-market behavior, and Suno owns the distribution. |
| **Generalist AI $400M** | Radical Ventures | *Deep-tech research bet* — fund pattern is multi-year, science-leaning. Bet: foundation models for robotic embodiment are still 3 years from commodity. |
| **Flourish $500M (seed)** | Bezos + Lux + GV | *Contrarian-architecture founder bet* — strategic angels + deep-tech-leaning VCs together. Bet: transformers aren't the endpoint; brain-inspired wins on data-efficiency. |

### Why it matters to you

- **Job lens:** Each pattern hires very differently. *Suno-shape:* product + safety/IP engineers. *Generalist-shape:* embodied-AI / simulation / robotics MLEs. *Flourish-shape:* research-leaning (PhDs or strong indep research). **Match your application list to a pattern**, don't blast all three.
- **Startup lens:** If you're considering a founder seat, ask yourself **which of these three patterns your idea fits before you take a meeting**. There's no "fourth template" being funded this week. If your idea doesn't pattern-match any of these three, *that's the signal to either reshape it or wait for a different month's data*.
- **Insight:** The application layer is **sorting by founder-investor fit**, not just by traction. Suno's traction would have been illegible to Radical; Generalist's research bet would have been illegible to Bond. **Treat investor selection as a 1:1 fit problem, not a 1:many sales problem.** Pick three target investors that fit your shape, do deep research on each, and write the deck *for those three* — not for "VCs."

→ Cross-link: [`02` §3 the funding details](./02-new-emerging.md#3-funding-megarounds).

---

## Action checklist — Wed 06-10 → Sun 06-14

- [ ] **Tonight:** Read [`03` §1](./03-practical-skills-and-tools.md#1-managed-agents) end-to-end. Confirm Managed Agents access on your Anthropic plan. Sketch the workflow.
- [ ] **Thu 06-11:** Stand up the **private MCP server** (5 tools). Local first; deploy on Fri.
- [ ] **Fri 06-12:** Wire the **Fable-5 / Sonnet-4.6 / Haiku-4.5 routing**. Run the eval set (5 clean + 5 planted). Log per-step cost.
- [ ] **Sat 06-13:** README + cost-delta table + 1-paragraph routing rationale + 1-paragraph eval design.
- [ ] **Sun 06-14:** Publish artifact. Email Anthropic FDE recruiter + 3 cold emails to FDE / Integration Engineer / Customer Eng leads at your target list (your `ME.md` row).
- [ ] **Mon 06-15:** **Anthropic Agent SDK metering goes live.** Take a screenshot of your cost dashboard for the first day under new metering — this is artifact content for week 2.
