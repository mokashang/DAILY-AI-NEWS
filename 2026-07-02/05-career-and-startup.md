# Career + Startup — 2026-07-02

Five signals shape the week: **Baseten $1.5B/$13B tripling headcount** on the inference-margin thesis; **Anthropic $30B run-rate + statewide California deal + explicit FDE hiring**; **YC S26 batch skewing ~60% AI** and pointing right at agent-infra; **tech layoffs at 1,115/day with 56% citing AI** — but AI teams are the exception; and the brutal reality that **only 2.5% of US AI/ML job postings target 0–2 years**, so the tactic is *bypass*, not queue.

Tags: `#career #startup #hiring #fde #ycombinator #newgrad #compensation`

---

## 1. Baseten raises $1.5B Series F at $13B — tripling headcount to serve 1B+ daily inferences {#1-baseten}

**What happened:** On **June 22, 2026**, AI inference platform **Baseten** announced a **$1.5B Series F** led by **Altimeter, Conviction, and Spark**, split across tranches at **$11B and $13B post-money** — a **160% valuation jump in five months** (prior round was $300M Series E at $5B). Baseten reported **~20× YoY revenue growth**, **~1B+ daily inference requests across 87 clusters on 18 clouds**, and said the capital will fund **"tripling headcount this year"** across engineering, research, and GTM.

**Sources:**
- [Businesswire — Official Series F release](https://www.businesswire.com/news/home/20260622645563/en/Baseten-Raises-%241.5-Billion-to-Power-the-Next-Era-of-AI-Inference) `[primary]`
- [Baseten blog — Announcing our Series F](https://www.baseten.co/blog/announcing-our-series-f/) `[primary]`
- [TechCrunch](https://techcrunch.com/2026/06/18/ai-inference-startup-baseten-reportedly-raising-1-5b-months-after-its-last-mega-role/) `[secondary]`
- [The Next Web](https://thenextweb.com/news/baseten-13-billion-valuation-blackbird) `[secondary]`

Tags: `#funding #infra #hiring #inference #series-f`

### Why it matters to you

- **Job:** Inference-infra is one of the few segments still hiring aggressively at all levels — **"tripling headcount"** reads as "we will interview you." Baseten runs the Anthropic stack (Claude is among its top-served models); its **FDE/solutions and platform-eng ladders** are a realistic target for a grad who has shipped anything with vLLM, TGI, or Modal. Look at the [current careers page](https://www.baseten.co/careers) this week.
- **Insight:** The tranche structure (11 → 13) and **5-month re-up** signal that **inference margin is the single most defensible wedge in 2026 infra.** More Basetens will exist by Q4. Aim your resume at the *category*, not just the company.

---

## 2. Anthropic hits ~$30B run-rate + California statewide deal + aggressive FDE hiring {#2-anthropic-fde}

**What happened:** Anthropic's run-rate revenue crossed **~$30B in April 2026** (up from ~$9B end-2025); **>1,000 customers now spend $1M+/yr**, doubling in under two months. Late June: **California signed a statewide deal** giving all state agencies, cities, and counties Claude at a **50% discount** — Claude's largest US public-sector deployment. Anthropic is actively hiring **FDE** roles including:

- "**Forward Deployed Engineer, Applied AI**" (3+ yrs)
- "**Forward Deployed Engineer, Federal Civilian**" (4+ yrs)
- Expanded **partner-network FDEs via Deloitte**.

(Note: [big-lab-moves §5 (Palantir Karp attacking token billing)](./01-big-lab-moves.md#5-token-attack) suggests the near-term run-rate print is under enterprise-CFO scrutiny — but the FDE hire wave is orthogonal, and if anything intensifies as customers push for outcome-priced engagements.)

**Sources:**
- [Anthropic — FDE Applied AI job](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) `[primary]`
- [Anthropic Careers](https://www.anthropic.com/careers/jobs) `[primary]`
- [California Claude statewide deal](https://awesomeagents.ai/news/anthropic-california-claude-half-price-newsom/) `[secondary]`
- [The New Stack — FDE hiring](https://thenewstack.io/forward-deployed-engineers-ai/) `[analysis]`

Tags: `#anthropic #fde #hiring #enterprise #govtech`

### Why it matters to you

- **Job:** This is **your most direct target.** FDE is the fastest-growing role at frontier labs and the one where CS-grad polymath skills (prompt/agent + integration code + client-facing) beat a pure-ML-PhD pedigree. **Ship a public MCP server + eval harness on GitHub *before* you apply** — see [`03` §3](./03-practical-skills-and-tools.md#3-hooks) and [`04` §1 SciAgentArena's stepwise-validator pattern](./04-research-progress.md#1-sciagent).
- **Insight:** A **$30B run-rate customer base with 1,000 seven-figure accounts** is the mechanical reason FDE demand is exploding — each of those accounts wants an embedded Anthropic engineer. Even if the token model gets repriced ([`01` §5](./01-big-lab-moves.md#5-token-attack)), *the seat count doesn't drop.*

---

## 3. YC S26 batch: ~60% AI companies, $500K checks, RFS = "AI becomes the foundation, not a feature" {#3-yc-s26}

**What happened:** YC's Summer 2026 batch (running July–Sept in SF) has already launched **55 companies with ~60% AI-focused** (up from 40% in 2024). YC is investing **$500K per company** on standard terms. **YC's Summer 2026 RFS explicitly names 15 categories** — the S26 batch skews heavily to **agent-infrastructure**:

- **Sazabi** — AI-native observability with auto RCA
- **"Evidence before act"** retrieval for agents
- **Real-time web context** for agents
- **AI-run consumer brands** (e.g., Light Anchor)

**Sources:**
- [YC S26 companies page](https://www.ycombinator.com/companies?batch=Summer+2026) `[primary]`
- [Extruct — S26 batch list](https://www.extruct.ai/data-room/ycombinator-companies-s26/) `[secondary]`
- [Urban Geekz — YC S26 RFS coverage](https://urbangeekz.com/2026/05/y-combinator-reveals-15-startup-ideas-it-wants-founders-to-build-in-summer-2026/) `[secondary]`
- [Forbes — YC batch analysis](https://www.forbes.com/sites/dariashunina/2026/06/04/what-y-combinators-latest-batch-reveals-about-the-future/) `[secondary]`

Tags: `#ycombinator #s26 #startups #agents #rfs`

### Why it matters to you

- **Startup:** The wedge signal for a founding CS grad is clear — **agent tooling that assumes the model is a given** (evals, observability, memory, retrieval provenance, browser context) is where YC is writing checks right now. **Skip the "we trained our own model" pitch.**
- **Job:** These 55+ companies will each hire 2–4 engineers in the next 6 months; **batch demo day is a hiring event, not just a fundraising one.** The S26 launch pages are the **highest-signal early-stage job board on the internet.** Bookmark it and check weekly.

---

## 4. Tech layoffs hit 1,115/day; 156K workers cut with AI cited — but AI teams are the exception {#4-layoffs-bifurcation}

**What happened:** Through mid-June 2026, **247 layoff events displaced 183,966 workers** (~1,115/day, nearly **2× the 2025 pace**). **56% of events explicitly cite AI/automation** — 156,270 workers across 150 companies. June cuts include:

- **GitLab** (~350, 14% of staff, June 3)
- **Oracle** (500 in Romania, June 25)
- **Cisco** (471 in California)

**Microsoft, Google, and Amazon hired ~40% fewer new grads for technical roles vs. 2024** — but continue to **recruit aggressively in AI product teams** (Copilot, Gemini, applied research). This is the **bifurcation** — not a market-wide freeze.

**Sources:**
- [TechCrunch — Running list of AI-cited layoffs 2026](https://techcrunch.com/2026/06/22/the-running-list-major-tech-layoffs-in-2026-where-employers-cited-ai/) `[secondary]`
- [Forbes — 123K tech jobs lost, AI most-cited](https://www.forbes.com/sites/maryroeloffs/2026/06/04/tech-industry-loses-123000-jobs-this-year-ai-is-the-most-cited-reason-for-layoffs/) `[secondary]`
- [TechTimes — 1,115/day pace](https://www.techtimes.com/articles/318466/20260616/tech-layoffs-hit-1115-day-2026-companies-cite-ai-cuts-fail-boost-returns.htm) `[secondary]`
- [Allwork — Microsoft freeze spares AI teams](https://allwork.space/2026/03/microsofts-new-hiring-freeze-spares-ai-teams-as-tech-giants-reshape-workforce-strategies/) `[analysis]`

Tags: `#layoffs #hiring #newgrad #bigtech #bifurcation`

### Why it matters to you

- **Job:** The market is **not "bad" — it is bifurcated.** The generalist SDE lane is closing (postings −65% since Jan 2022) while the AI-adjacent lane (MLE, applied research, FDE, AI Solutions Engineer) is at near-full employment. **Stop optimizing a Leetcode-only pipeline; start optimizing a "shipped an agent + eval harness" pipeline** — the same artifact answers both interview loops.
- **Insight:** Big Tech's freeze is why **YC S26 will have its strongest hiring pool ever** — the top-decile new grads who would have taken the Google offer are now open to Series A cos. If you're a founder, this is your recruiting tailwind; if you're a candidate, [`05` §3](#3-yc-s26) is where to look.

---

## 5. New-grad AI-engineer comp: $134K–$193K base at mainstream, $300K retention at frontier labs — but only 2.5% of postings target 0–2 yrs {#5-newgrad}

**What happened:** Robert Half's 2026 Salary Guide puts **new-grad AI/ML eng base at $134K start / $170,750 midpoint / $193,250 top.** Average AI engineer TC hit **~$206K in 2026, up $51K YoY**. **OpenAI added $300K retention bonuses (2-yr vest)** for new-grad technical hires (announced Aug 2025, in force through 2026). Frontier labs pay **10–20% above mainstream on base** and ship equity-heavy packages **1.5–2.5× base**.

Sharp catch: **only ~2.5% of US AI/ML postings target 0–2 years of experience**; the modal ask is **4–6 years for a discipline barely 4 years old** in its current form.

**Sources:**
- [Robert Half — 2026 AI/ML salary](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[primary]`
- [KORE1 — AI engineer offer data](https://www.kore1.com/ai-engineer-salary-guide/) `[secondary]`
- [Pin AI — 2026 compensation benchmarks](https://www.pin.com/blog/ai-compensation-salary-guide/) `[secondary]`
- [Medium — Anthropic-cited 2.5% entry-level data](https://medium.com/@reactjsbd/ai-engineer-is-the-fastest-growing-job-in-america-9bdfaa6a328b) `[aggregator]`

Tags: `#compensation #newgrad #frontierlabs #hiring #openai`

### Why it matters to you

- **Job:** The **2.5% number is the whole game.** You're competing not against 4-yr-experience candidates but against **everyone else trying to fit into a nearly-nonexistent entry slot.** Two proven bypasses:
  - **(a) Apply as SWE-with-AI-projects** to New Grad SWE reqs at AI-heavy companies, pivot internally after 6–12 months.
  - **(b) Target FDE / Solutions Engineer / AI Integration Engineer** titles where "**customer-facing + can code + can prompt + can eval**" beats "4 yrs of MLE." This aligns with the [ME.md focusing decision](../ME.md#current-focusing-decision-re-evaluate-monthly).
- **Insight:** The **$300K OpenAI retention bonus** and Anthropic's revenue ramp mean **frontier-lab TC packages will likely push $600K–$1M for the strongest new grads by end of 2026** — the ceiling is still moving up faster than the floor. Optimize for the strongest single artifact you can ship this month, not for volume.

---

## Actions to schedule this week

- **Tonight (Thu):** [`03` §1](./03-practical-skills-and-tools.md#1-prompt-cache) prompt-cache fix + `PreToolUse` hook — commit to your public gist.
- **Fri:** Apply to Anthropic **FDE, Applied AI** (job link above) — attach the gist + a 1-page write-up citing the [`01` §5 token-billing revolt](./01-big-lab-moves.md#5-token-attack).
- **Sat:** Draft the [Anthropic AI-for-Science credit-grant application](./01-big-lab-moves.md#6-anthropic-science) — deadline **July 15**. Use [`04` §1 SciAgentArena](./04-research-progress.md#1-sciagent) stepwise-validator framing.
- **Sun:** Browse YC S26 launch pages ([`05` §3](#3-yc-s26)); pick 2 to cold-email as **founding-engineer** candidates.
