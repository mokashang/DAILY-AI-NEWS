# Career & Startup — 2026-06-07

The macro signal this Sunday is **a bifurcating job market and a re-priced wedge map.** The labs are getting *more* selective at the top of the market while the *floor* of new-grad SWE has fallen ~50%. The good news: the **paths around the bottleneck are explicit** — production artifacts, public expertise, relationship-building 6–12 months out, and choosing the right lane (MLE, FDE, AI Integration, AI Security, AI Eval/Verification). Today's edition translates the week's lab moves into concrete weekly actions for both the job and the startup track.

Tags: `#jobs #mle #fde #residency #compensation #wedge-map #biotech #security #applications`

---

## 1. The 2026 AI job market is bifurcating — what to do about it {#1-bifurcation}

**What the data shows:**

- **MLE roles +41.8% YoY** (fastest-growing job category).
- **Entry-level programmer employment ‑27.5%** overall; **new-grad SWE hiring at top tech ‑50%+**.
- **Senior MLE at frontier labs: $470–630K median; top tail $1M+.**
- **Enterprise MLE (non-frontier): $170–245K total.**
- **AI-skill wage premium: 25% → 56% in 12 months.**

The market is **two markets**: a small, well-paid, hard-to-enter frontier tier, and a much larger enterprise tier where wages are still strong but not in $1M territory. Crucially: **the path between the two markets is the same path** — public artifacts + production experience + targeted relationship-building. Anthropic explicitly states that **PhD and prior ML experience are NOT required** (≈50% of their technical staff have PhDs, ≈50% don't).

**Sources:**
- [Sundeep Teki — How to get hired at OpenAI, Anthropic & DeepMind in 2026](https://www.sundeepteki.org/advice/how-to-get-hired-at-openai-anthropic-and-google-deepmind-in-2026) `[analysis]`
- [Sundeep Teki — AI Research Engineer interview guide: OpenAI, Anthropic, DeepMind (2026)](https://www.sundeepteki.org/advice/the-ultimate-ai-research-engineer-interview-guide-cracking-openai-anthropic-google-deepmind-top-ai-labs) `[analysis]`
- [Data Exec — Breaking into AI in 2026: what Anthropic, OpenAI, and Meta actually hire for](https://dataexec.io/p/breaking-into-ai-in-2026-what-anthropic-openai-and-meta-actually-hire-for) `[analysis]`
- [Anthropic Careers](https://www.anthropic.com/careers) `[primary]`
- [Pin — AI compensation benchmarks 2026: the AI hiring bubble](https://www.pin.com/blog/ai-compensation-salary-guide/) `[analysis]`
- [OpenAI Residency 2026 — open applications](https://openai.com/careers) `[primary, reference]`

### The five-step path the data actually supports (in execution order)

1. **Pick one lane and commit for 90 days.** Five lanes are realistic for a 2026 CS grad: **MLE** (production ML), **AI Integration Engineer / FDE** (deploy + customize at customer), **AI Engineer** (LLM-app eng), **AI Security / Eval** (the Glasswing-shaped lane), **Robotics / Embodied AI** (Generalist AI, Physical Intelligence cohort). Each has different ramps; rotating between them costs you the most expensive resource (focused months).
2. **Ship one production-grade public artifact per month.** Specifically: a repo with a real benchmark, a real cost log, a real evaluation, and a 5-min demo video. Three of these stacked over a quarter is what the labs actually want to see.
3. **Develop relationships 6–12 months before applying.** Cold applications convert at <1%. Warm intros via mutual GitHub contributors, Twitter/X conversations on the targeted-lab researchers' threads, and conference Q&A convert at 10–20×.
4. **Apply during the *vague-terminology window* for new products.** When a new SDK / API / panel ships (e.g., tomorrow's iOS 27 Extensions), the first 2 weeks of postings use unstandardized vocabulary — fewer applicants, less competition. Search across spelling variants.
5. **Use the OpenAI Residency 2026 or Anthropic Safety Fellowship as a non-traditional entry.** **OpenAI Residency: 6 months, ~$220K, explicitly designed for career-changers from physics/math/neuroscience/SWE with strong fundamentals.** This is the single most under-priced backdoor into the frontier tier for someone with a CS grad-level background plus *one* deep specialty.

### Why it matters to you

- **Job lens:** Internalize: **the bifurcation is not a wall, it's a filter.** What gets you across is *artifacts + relationships*, not credentials. Your CS-grad-student status doesn't disqualify you from $470K+ roles; missing public artifacts does.
- **Startup lens:** The bifurcation creates an underdiscussed founder opportunity: **the enterprise MLE tier ($170–245K) is large, growing, and badly served by tools.** Most AI-eng tooling (LangSmith, Braintrust, etc.) is priced and shaped for the frontier tier. There's a clean wedge for **simpler, cheaper tools shaped for the enterprise MLE workflow** — observability, eval, prompt mgmt, but for $99/mo not $999/mo.
- **Insight:** The bifurcation is itself a *temporary* state. Either the enterprise tier grows up to meet the frontier (likely, as MAI-Code-1-Flash + Gemini 3.5 Flash + cheap inference democratize capability) or the frontier tier compresses as IPOs force operating discipline. Either way, **the bifurcation closes within 18–24 months**. Position now to be in the right slot when it does.

→ Cross-link: [`03` §2 the cost-routing artifact](./03-practical-skills-and-tools.md#2-metering-prep) (one of those public artifacts) · [`05` §4 the OpenAI Residency window](#4-residency).

---

## 2. The Glasswing-shaped security lane is the under-priced specialty {#2-security-lane}

**What changed this week:** Project Glasswing expanded to **150+ partners across 15+ countries** ([`01` §3](./01-big-lab-moves.md#3-glasswing)). The bottleneck Anthropic explicitly admits is **vulnerability triage, disclosure coordination, and patch verification** — not model capability.

That's a **hireable, learnable, non-PhD-gated specialty**. The lane is:

- **AI Security / AI Vuln-disclosure Engineer** — translate Mythos findings into responsible-disclosure tickets, coordinate with partner orgs, drive patch verification, re-run scans to confirm closure.
- **AI Eval Researcher (security tilt)** — design + run the evals that score how well a frontier model finds (or fails to find) vulnerabilities; this is the "metrics that govern the Mythos product" function.
- **Customer Engineer for AI Security products** — Exaforce ([2026-05-22/02 §2](../2026-05-22/02-new-emerging.md#2-exaforce)) and its peers need integration engineers who can deploy agentic SOCs at customers; the role is FDE-shaped with a security vertical.

**Why this lane specifically is right for a CS grad:**

- It's **adjacent to the frontier without competing with the PhD-shaped queue.** You don't need a PhD to be excellent at vulnerability triage; you need software-engineering chops + security curiosity.
- The category is **commercially funded** (Exaforce $125M; Project Glasswing partners number 150+) — meaning hiring is real and growing, not pre-revenue speculation.
- It's a **defensible specialty** — once you've coordinated 5 disclosure tickets through a partner org, the next 50 are easier; reputation compounds inside a small, well-connected community.

### Three weekend actions to claim a foothold

1. **Read one CVE disclosure end-to-end** and write a 1-page postmortem on your blog of *how the disclosure was coordinated* (not the technical detail of the vuln). Tag it `#ai-vuln-disclosure`.
2. **Pick one open-source project from the Project Glasswing partner list** and run a thoughtful CodeQL / Semgrep scan against it. Even if you find nothing, the writeup of *what you scanned and why* is the artifact.
3. **DM one Anthropic / Exaforce / Microsoft security engineer this week.** Reference Glasswing specifically; ask one *good* question about disclosure coordination. (Not "are you hiring?".)

→ Cross-link: [`01` §3 Glasswing details](./01-big-lab-moves.md#3-glasswing) · [2026-05-22/02 §2 Exaforce](../2026-05-22/02-new-emerging.md#2-exaforce).

---

## 3. The biotech-AI hiring wave starts in ~6 weeks — be in queue now {#3-biotech}

**What changed:** **NewLimit's $435M Series C (June 2)** lands at the same time as **Isomorphic Labs' $2.1B Series B** from May. Biotech-AI is no longer an experimental category; it's a **capitalized hiring stream** with a 60–90 day ramp.

The crossover roles that don't require a biology PhD:

- **Software Engineer — Biotech AI Platforms.** ML infrastructure for protein/cell models. Pure software with a biotech customer; no wet-lab work.
- **Applied ML Engineer — Drug Discovery.** Builds the eval harnesses, the training loops, the molecule-generation pipelines.
- **ML Infrastructure / Cluster Engineer — for biotech-AI labs.** GPU-cluster work; same skills as any ML infra role; salary band $200–400K because biotech labs match frontier comp to attract software talent.

**Companies to put on your apply list this week (in queue for the July hiring wave):**

- **NewLimit** (the Series C closer)
- **Isomorphic Labs** (London / Cambridge MA / Lausanne)
- **Generate Biomedicines**
- **Inceptive**
- **EvolutionaryScale**
- **Cradle**
- **Atomic AI**
- **310 AI**

**Sources:** [Tech Startups — VC roundup June 3](https://techstartups.com/2026/06/03/venture-capital-startup-funding-roundup-june-3-2026/) `[aggregator]` · [Isomorphic Labs Series B](https://techcrunch.com) `[secondary]` · [Generalist AI Series](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-autonomy-biotech-anthropic/) `[secondary]`

### Why it matters to you

- **Job lens:** Biotech-AI roles are the **most under-fished lane** for a CS grad student. The labs assume the talent comes from biotech; biotech assumes the talent comes from ML. The gap is exactly where you fit. Apply now (before the post-funding-round hiring queue saturates), and reference your **ML infrastructure / agent-eval experience** explicitly — that's the angle that converts.
- **Startup lens:** The wedge is **biotech-AI developer tooling** (the equivalent of Hugging Face / Weights & Biases / Modal for the protein-design + cell-reprogramming + small-molecule-design pipelines). The market is small but growing, and *very* underserved — Hugging Face doesn't speak this audience well. Build for ML-engineers at biotech labs; sell into the $435M-Series-C class of company. Two-year-clear runway because the customer base just got funded.
- **Insight:** Capital flow lags hiring by ~6–10 weeks (the "round closes → recruiter ramps → first JDs post" cycle). The week a $400M+ round closes is the week to **start the relationship-building, not the application** — because the JD that fits you won't be posted for another 5–8 weeks. Most candidates apply *after* the JD is public, by which time they're competing with 200+ inbound. Be in the queue before the JD is written.

→ Cross-link: [`02` §2 the funding rounds table](./02-new-emerging.md#2-funding) · [WATCHLIST → Isomorphic Labs row](../WATCHLIST.md).

---

## 4. The OpenAI Residency 2026 / Anthropic Safety Fellowship — both are open right now {#4-residency}

**What's open:**

- **OpenAI Residency 2026** — 6 months, **$18,333/month (~$220K annualized)**, **explicitly designed for career-changers from physics, math, neuroscience, or software engineering** who have strong fundamentals but lack formal ML experience. The closest thing to a paid bootcamp into a frontier lab.
- **Anthropic AI Safety Fellowship** — research-track program, comparable comp, narrower ML-research focus than the OpenAI Residency.
- **Google DeepMind Early Career AI/ML SWE (PhD)** — different track, PhD-shaped.

**Why these specifically are right for the user's profile:**

- A CS grad student with **one strong software project + one strong ML or eval project** is *exactly* the OpenAI Residency target. The program is built to convert this profile into a frontier-lab researcher in 6 months.
- The Residency is a **structured path that doesn't require the warm-intro queue**. Cold-applying with a strong portfolio is the *expected* entry mode. That's rare in the frontier-lab pipeline and uniquely valuable.

### Why it matters to you

- **Job lens:** If your project portfolio has two of {[cost-router artifact, `03` §2](./03-practical-skills-and-tools.md#2-metering-prep), [dual-model sanitiser](../2026-05-20/05-career-and-startup.md#3-safety-project), [WebMCP demo](../2026-05-20/03-practical-skills-and-tools.md), an MCP server, an eval harness for an agent task} — **you are residency-applicable**. Plan the application this month; the *cover letter that references three of your own public artifacts by URL* is the single highest-ROI page you can write all year.
- **Startup lens:** Residency-and-fellowship cohorts are also **founder pipelines**. Look at the alumni rolls — fellows from the 2024–25 cohorts are running multiple of this year's $100M+ rounds. If "do a startup" is on your goals list and you're not yet ready to go solo, **a residency cohort is the highest-quality co-founder marketplace in the AI ecosystem.**
- **Insight:** The path most people imagine for breaking into a frontier lab is **PhD → research engineer**. The Residency exists *because* the labs noticed the pipeline misses too many strong CS-grad-shaped candidates. Use the program for what it is: a **structured, non-academic on-ramp**.

---

## 5. This week's concrete applications + actions {#5-actions}

In execution order — copy into your `APPLICATIONS.md` and `ACTIONS.md` files:

### Sunday (today, 2 hours)

- [ ] Pre-stage the WWDC scoring doc ([`03` §3](./03-practical-skills-and-tools.md#3-wwdc-prestage))
- [ ] Update WATCHLIST.md — promote **Anthropic IPO path** to 🟢 + add **Apple-Gemini Siri deal** + **MAI-Code-1-Flash** + **Glasswing 150-partner expansion** rows
- [ ] Skim Agent² RL-Bench abstract + intro ([`04` §1](./04-research-progress.md#1-agent2-rlbench))

### Monday (WWDC day, 2.5 hours)

- [ ] Live-monitor WWDC 10–11:30 AM PT using the pre-staged scoring doc
- [ ] Publish the scored prediction table to LinkedIn within 2 hours of keynote end
- [ ] Apply to **one Apple Intelligence / Apple ML role** within the vague-terminology window
- [ ] Update LinkedIn skills with the actual on-stage terms (NOT pre-keynote guesses)

### Tuesday — Thursday (ship the cost-router artifact)

- [ ] Mon eve: README + class signatures
- [ ] Tue/Wed eve: implementation + benchmark
- [ ] Thu eve: publish writeup + repo + a short LinkedIn post

### Friday (T-minus 3 to metering)

- [ ] Apply to **one Anthropic role** referencing the cost-router project specifically
- [ ] Apply to **one biotech-AI MLE role** (NewLimit / Isomorphic / Generate Biomedicines) — be in queue before the JDs saturate

### Weekend (T-minus 1 to metering)

- [ ] **Final** cost-routing + caching audit on your own Claude usage
- [ ] Sketch the OpenAI Residency application essay (1 page draft)

---

## 6. The single biggest re-prioritization from this week {#6-reprio}

If you can do only **one** thing differently in the next 7 days based on this edition:

> **Treat *verification* as a core skill, not a sub-skill of eng or safety.**

The pattern this week — Glasswing's 90% true-positive rate, Agent² RL-Bench separating planning from execution, the dual-model sanitiser primitive, the cost-router needing per-step verification — all point at **verification as the meta-bottleneck of 2026**. Re-frame your portfolio narrative around **"I build systems where the verifier is as carefully designed as the generator."** That sentence outranks 95% of "I built an agent" framings on cover letters this month.

→ Cross-link: [`04` §3 the verification arc](./04-research-progress.md#3-macro-arc) · [`05` §2 the security lane](#2-security-lane).
