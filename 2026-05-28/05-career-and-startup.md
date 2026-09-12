# Career & Startup — 2026-05-28

The market this week argued with itself on the surface, but the signal underneath is clean. **At the macro:** new-grad CS unemployment is 6.1% (≈2× the national rate), entry-level postings are down ~30% YoY, and 43% of recent CS grads are underemployed — the worst entry-level market in decades. **At the same time:** Cognition raised at $26B on $492M ARR, KPMG bought Claude for 276K seats, OpenRouter raised at $1.3B, and ML/AI postings are up **+85% YoY** with AI skills in **42% of all software job descriptions**. The contradiction *is* the signal: **the median CS grad role is shrinking, and the AI-specialist role is the only growing slice.** That is the entire game.

For you, the practical implications: **(1) Big-4 AI-implementation lanes are the lowest-friction high-fit applications you can make this week** — open ~30–60 day window, salary $200K+ for senior, lower bar for new-grad-with-portfolio. **(2) Your *existing* artifact pipeline (router + cost log, MCP server, billing audit) is on-thesis** — three of this week's biggest checks (Cognition, OpenRouter, KPMG/Anthropic) reward exactly that stack. **(3) Skill-stack reweight: orchestration + routing + verification + cost have all been *repriced up* this week**, while raw prompting / model-fluency continued its slide.

Tags: `#jobs #careers #cs-grad #big4 #fde #integration #startup #market-data`

---

## 1. The Big-4 implementation lane — open now, closing in 30–60 days {#1-big4-lane}

**What's open:** With **KPMG (276K), PwC (364K target), Deloitte (~460K)** all on Claude in 60 days, three of the largest professional-services firms simultaneously need to **staff AI-implementation roles faster than they can hire.** The role title is not "ML Engineer" — it's:

- **AI Engineer — Client Delivery**
- **Solutions Architect, AI**
- **Tax & Legal AI Engineer / Industry AI Engineer**
- **Forward-Deployed Engineer / Solutions Engineer (consulting-firm variants)**
- **AI Solutions Manager** (the manager-track for the same skill stack)

**Why now:** Postings tend to follow announcement waves with a **30–60 day lag** as firms convert headcount, write JDs, and align with global HR. KPMG's May 19 announcement → expect peak posting volume **mid-to-late June.** Apply *before* that peak when the applicant pool is thinner and the firms are most willing to flex on credentials.

**Compensation framing** (US, based on 2026 market data and prior Big-4 AI-eng postings):
- New-grad / 1-yr / portfolio-heavy: $90K–$130K base + bonus
- Senior (2–4 yrs): $160K–$220K base
- Staff / lead: $220K–$300K base
- Plus utilization bonuses + signing for high-demand specialties

**Sources:**
- [Anthropic — KPMG alliance](https://www.anthropic.com/news/anthropic-kpmg) `[primary]`
- [Fortune — Big Four consulting's 2 AI nightmares; KPMG's answer is Claude](https://fortune.com/2026/05/26/kpmg-anthropic-claude-partnership-big-four-ai/) `[secondary]`
- [KPMG/Anthropic alliance page](https://kpmg.com/xx/en/what-we-do/alliances/anthropic.html) `[primary]`
- [GitHub — speedyapply/2026-AI-College-Jobs (daily-updated)](https://github.com/speedyapply/2026-AI-College-Jobs) `[primary]` — set a daily-check reminder
- [Extern — Computer Science Job Market 2026](https://www.extern.com/post/computer-science-job-market-2026-guide) `[analysis]`

### Your action this week

1. **Today (~30 min):** Apply to **one** Big-4 "AI Engineer — Client Delivery" or "Solutions Architect, AI" role at **KPMG, PwC, or Deloitte**. Anchor cover letter on: (a) KPMG's Digital Gateway deployment ([`01` §1](./01-big-lab-moves.md#1-kpmg)) as proof you've read the news; (b) your existing **3-provider router + cost log artifact** ([`03` §3](./03-practical-skills-and-tools.md#3-cost-routing)) as your work sample; (c) interest in **PE-portfolio-company implementation** (the Anthropic-KPMG "preferred partner for PE" angle is *under-applied-to* — most candidates won't know about it).
2. **This week:** Track three roles in [APPLICATIONS.md](../APPLICATIONS.md). Status starts ⚪ open; promote to 🟡 on response, 🟢 on offer.
3. **Saturday:** Take **PwC's free Claude certification** (the 30K-trained → 364K-target program from [2026-05-15/01](../2026-05-15/01-big-lab-moves.md)) if you haven't already. It's the lowest-cost, highest-signal credential for this lane.

### Adjacencies worth one application each

- **Cognition (Devin)** — careers.cognition.ai. Specifically **Forward-Deployed Engineer / Solutions Engineer.** The $1B raise ([`02` §1](./02-new-emerging.md#1-cognition)) means 30+ FDE-equivalent roles will open in 60 days. **Apply now, before the listing wave.**
- **OpenRouter** — they're hiring **routing infra eng + governance eng** post-Series B ([`02` §2](./02-new-emerging.md#2-openrouter)). Your router artifact is **literally their work sample.** Lowest-friction application in your queue.
- **Anthropic Solutions / Integration** — keep the weekly application going. Reference the Karpathy/pre-training direction ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md)) and the Mythos rollout posture ([`01` §3](./01-big-lab-moves.md#3-mythos-toggle)) as signal you read past the headline.

→ Cross-link: [2026-05-19/05 the FDE playbook](../2026-05-19/05-career-and-startup.md) · [2026-05-15 PwC certification](../2026-05-15/) · [ACTIONS.md](../ACTIONS.md).

---

## 2. Skill-stack reweight — what got repriced this week {#2-skill-stack}

The same four checks (KPMG, Cognition, OpenRouter, Claude Code update) **all reward one specific stack**. Compare to where the *median* applicant is investing.

| Skill | Market repricing this week | Your status |
|---|---|---|
| **Cost-aware routing across providers** | 🟢 UP — OpenRouter $113M validation | Artifact in progress ([`03` §3](./03-practical-skills-and-tools.md#3-cost-routing)) — ship this weekend |
| **Agent execution inside enterprise perimeter (MCP tunnels, self-hosted sandboxes)** | 🟢 UP — Claude Code May 26 update + KPMG Digital Gateway | Build sandbox demo ([`03` §1](./03-practical-skills-and-tools.md#1-claude-code-sandbox)) Sat |
| **Verification against real tools (MCP-Atlas, Toolathlon)** | 🟢 UP — pairs with above | Touched via the router's MCP leg |
| **Outcome / KPI-pressured agent eval (constraint-violation benchmarks)** | 🟢 UP — Li et al. [`04` §1](./04-research-progress.md#1-constraint-violations); EO cyber half | Interview talking-point only — not yet an artifact |
| **Interpretability / mechanistic safety** | 🟢 UP (cultural) — Pope/Olah moment, Karpathy team | Reach-lane Anthropic AI Safety Fellowship still open |
| **Plain prompting / "I can use ChatGPT well"** | 🔴 DOWN — commoditized | Not in your portfolio (correct) |
| **Generic Python ML** | 🔴 DOWN — entry-level SWE postings -30% YoY | Don't lead with it |
| **AI agent-research (PaperBench-style reproduction)** | 🟢 UP — Karpathy team is the production case | Weekend portfolio candidate ([`04` §2](./04-research-progress.md#2-paperbench)) |
| **Vertical-AI domain fluency (PE, tax, legal, security)** | 🟢 UP — KPMG embedded; Exaforce; OpenAI tax-agent reference | Pick one: PE-portfolio-AI is the highest-leverage given Anthropic-KPMG partnership |

### Your action this week

- **Update LinkedIn skills row** to: *Claude (Managed Agents, MCP, Self-hosted Sandboxes) · Multi-provider Routing · Cost-Aware Agent Design · Agent Evaluation (constraint-violation, real-tool verification) · MCP Server Development · Vertical AI Integration*. **Remove**: generic "Prompt Engineering", "Python ML", "TensorFlow".
- **Pick ONE vertical** for the next 90 days. Recommendation: **PE-portfolio-company AI** — it's where the Anthropic-KPMG partnership pointed, where the dollar density is highest per-implementation, and where competition is thinnest (most CS grads target labs or tech firms, not PE shops).

→ Cross-link: [ME.md focusing decision](../ME.md) — promote PE-vertical pick to active.

---

## 3. Meta-alumni outreach — Week 2 follow-up {#3-meta-week2}

**Carried from:** [2026-05-21/05 §1](../2026-05-21/05-career-and-startup.md#1-meta-outreach) and [2026-05-22/05 §3](../2026-05-22/05-career-and-startup.md#3-meta-followup).

**Status:** You sent **10 Meta DMs on Thursday May 21** (8 AM PT), split into 3 pools — (a) displaced, (b) redirected-to-AI, (c) spinning-out. Friday May 22 was your 30-min reply window. **Today is Day 7** — the second-touch window.

**Your action today (15 min):**

1. **Bump non-responders** *in pool (a) only* (displaced — they're job-hunting, they appreciate the second touch). For pools (b) and (c), wait the full 14 days.
2. **For any pool (c) repliers** (spinning out) — schedule a 20-min call this week. These are the highest-EV conversations in your network right now (they're founders pre-launch, looking for founding-team signal).
3. **Update `apps/meta-alumni-tracker.md`** — log reply status, set next-touch dates, and **migrate the spinning-out reply rows to STARTUPS.md as candidate co-founder leads.**

### Why it matters

- The Meta 8K-person cut ([2026-05-20](../2026-05-20/)) was 35–40% recruiting/HR — meaning many in your DM pool are technical, available, and *just* started looking. The 14-day post-layoff window is **maximum receptivity** for "let me know what you're up to." Touch once now, again at Day 14, then quarterly.

→ Cross-link: [APPLICATIONS.md](../APPLICATIONS.md) — log all responses · [STARTUPS.md](../STARTUPS.md) — migrate pool-(c) replies.

---

## 4. The contradiction-resolved view of the 2026 CS job market {#4-cs-job-market}

For the archive and to anchor your job-search posture for the rest of the quarter.

**The numbers (May 2026):**
- **Recent CS-grad (ages 22–27) unemployment: 5.7%** (well above the 4.2% all-workers rate).
- **CS-grad-specific unemployment: 6.1%** (≈ 2× philosophy majors).
- **43% of recent CS grads are underemployed** (in roles not requiring a CS degree).
- **Entry-level SWE postings: -65% from Jan 2022 to Jan 2025**, while CS-grad supply rose **+40%** over the same period.
- **Senior postings: 38.8% → 43.1% of IT job mix** YoY; **entry-level: 8.1% → 7.4%.**

**The counter-numbers (same May 2026):**
- **ML engineer openings: +59% over Feb 2020 baseline.**
- **AI/ML engineer postings: +85% YoY.**
- **AI skills appear in 42% of all software job descriptions.**
- **Class of 2026 CS starting salaries: $81,535 average (+~7% YoY)** — meaning the *people who land roles* are getting paid more, even as fewer land roles.

**What works** (per the same data set):
- **78% of CS students who secured jobs within 3 months had:** strong GitHub portfolio **OR** ≥1 internship **OR** a specialized certification. **Only 31% of those who relied on degree alone** landed roles in the same window.
- **Graduates with college work experience: 81.6% hire rate** vs **40.7% without.**

**Sources:**
- [Final Round AI — CS Graduates Face Worst Job Market in Decades](https://www.finalroundai.com/blog/computer-science-graduates-face-worst-job-market-in-decades) `[analysis]`
- [Extern — Computer Science Job Market 2026: Why It's So Hard (+ Fixes)](https://www.extern.com/post/computer-science-job-market-2026-guide) `[analysis]`
- [Stanford Review — The Class of 2026 is struggling to find jobs — and it's not because of AI](https://stanfordreview.org/the-class-of-2026-is-struggling-to-find-jobs-and-its-not-because-of-ai/) `[analysis]`
- [CNBC Select — By the Numbers: What the class of 2026 job market actually looks like](https://www.cnbc.com/select/class-of-2026-hiring-stats-and-ai-trends/) `[secondary]`
- [Metaintro — 5.7% and Climbing: What the 2026 Job Market](https://www.metaintro.com/blog/new-grad-job-market-2026-ai-entry-level) `[analysis]`

### Why it matters to you

- **The reductive lesson:** The median CS-grad outcome in 2026 is **bad**. The 80th-percentile CS-grad outcome — **specialized in AI, portfolio-anchored, with one internship-equivalent or certification** — is **outstanding** ($200K+ TC achievable in first role at frontier-AI-adjacent companies). **There's no middle anymore.** You've already chosen the specialized path; the implication is just to **execute on it harder for the next 90 days**, not to hedge back toward generic SWE.
- **Insight:** This is the most one-sided job market segmentation any tech-grad cohort has faced. Don't read the macro headlines and update toward gloom; **read the conditional probabilities and update toward execution.** The portfolio + certification + internship-equivalent triad is the entire game. You have the first; the artifact pipeline in [`03` §3](./03-practical-skills-and-tools.md#3-cost-routing) is the second; **the PwC Claude certification + a 30-day Big-4 contractor or PE-portfolio-company AI engagement** would be the third. Sequence them in that order.

→ Cross-link: [ME.md](../ME.md) — confirm focusing decision · [APPLICATIONS.md](../APPLICATIONS.md) — track this quarter's pipeline.

---

## 5. STARTUPS.md update note

Two wedges to re-rank up this week (do the actual re-rank in `STARTUPS.md`, not here):

1. **"Managed routing + cost governance" (vertical variant)** — directly validated by OpenRouter $113M. Specifically: **HIPAA-compliant routing-with-audit for healthcare**, or **SOC 2 / FINRA routing-with-attribution for fintech.** Customer-discovery conversation is one phone call.
2. **"PE-portfolio-company AI implementation"** — directly validated by Anthropic naming KPMG **preferred partner for PE.** A 3-person team that does **Claude-implementation engagements for PE-owned mid-market companies** (the underbelly of the KPMG/Anthropic deal — KPMG can't economically serve every $50–500M-revenue portfolio company itself). Customer-discovery is a single PE associate intro.

→ Re-rank these in [STARTUPS.md](../STARTUPS.md) this week.
