# Career & Startup — 2026-07-11

The most important career shift this week: **Anthropic's destination gravity strengthened again** (Jumper + Adler + Pritzel arriving one week, on top of Karpathy from May); the **OpenAI IPO slipped to 2027** (retail RSU math changes); the **CS-grad job market data crystallized as bifurcated** (6.1% general CS unemployment vs +59% ML-engineer openings vs 2020, AI-engineer #1 fastest-growing job two years running); and the **funded-startup call sheet for July** now includes six directly interviewable companies. Your Anthropic-stack focusing decision from `ME.md` is holding up in the market — but the market itself is repricing what "prepared for the role" means. Update the artifact, not the resume.

Tags: `#careers #jobs #startups #fde #anthropic #openai #hiring #layoffs`

---

## 1. The Anthropic destination signal — cite it specifically, not generically {#1-anthropic-destination}

**What happened:**

- **Karpathy** (May 19) → Anthropic pre-training + "Claude-accelerates-Claude" team.
- **John Jumper** (Nobel Chemistry 2024, AlphaFold) → Anthropic (this week).
- **Jonas Adler + Alexander Pritzel** (Jumper's AlphaFold co-authors) → Anthropic (same week).
- Product / vertical wave in parallel: **Sonnet 5** (June 30) + **Fable 5 GA** (June 9) + **Fable 5 global redeploy** (July 1) + **Claude Cowork mobile** (July 10) + **Claude Science + drug-discovery beta** (this week).
- Ramp signal from May stays live: Anthropic overtook OpenAI in US business adoption ([2026-05-14/01](../2026-05-14/01-big-lab-moves.md)); one July aggregator now claims **Anthropic overtook OpenAI on revenue** as well (single-source, treat as `[aggregator]` until a primary lands).

**Sources:**
- [The Agent Report — Google Gemini 3.5 Pro delayed / DeepMind talent exodus](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) `[secondary]`
- [Anthropic Newsroom](https://www.anthropic.com/news) `[primary]`
- [AIToolsRecap — AI News July 3 2026: Anthropic overtakes OpenAI on revenue](https://aitoolsrecap.com/Blog/ai-news-july-3-2026) `[aggregator]`
- [Claude timeline (public record)](https://github.com/jqueryscript/anthropic-claude-timeline) `[aggregator]`
- [2026-05-22/01 §3 — Karpathy hire recap](../2026-05-22/01-big-lab-moves.md#3-karpathy)

### Why it matters to you

- **Job lens (concrete):** In your Anthropic Solutions / FDE / Integration Engineer cover letters this month, don't cite "Anthropic's momentum" or "Anthropic is hot" — those are noise. Cite **specifically** the **Jumper move** *and* explain *why*: the **AlphaFold research thread relocating to a frontier lab is a bet on scientific-discovery-as-a-product**, and Claude Science ([`02` §1](./02-new-emerging.md#1-claude-science)) is the launch. That paragraph reads like sector literacy, not enthusiasm.
- **Startup lens:** The most defensible founder wedge for the next 12 months is **whatever sits under Anthropic Solutions when they win a bio / legal / finance / science deployment.** That's the FDE workflow: MCP servers, eval harnesses, cost-routers, compliance certificates. Ship one, sell it into a partner (any of the six §4 companies), skip the "compete with Anthropic" trap.
- **Insight:** The 2026 destination map: **Anthropic (frontier research + verticals) · OpenAI (consumer + super-app + Codex-inside-ChatGPT) · Google/DeepMind (rebuilding, T-6 days to 3.5 Pro) · SpaceXAI (cheap-and-fast tier) · Microsoft (own-model-for-office).** Every offer you take should be evaluated against *which slot on that map* it puts you in — that's your career optionality question.

→ Cross-link: [`01` §3 the exodus itself](./01-big-lab-moves.md#3-deepmind-exodus) · [`02` §1 Claude Science (the product this team is likely staffing)](./02-new-emerging.md#1-claude-science) · [`ME.md` current focusing decision](../ME.md).

---

## 2. The offer-math flip — OpenAI IPO 2027, Sonnet-5 pricing, and how to negotiate this quarter {#2-offer-math}

**What happened:**

- **OpenAI IPO slipped to 2027** (Bloomberg / Reuters late June; [`01` §4](./01-big-lab-moves.md#4-ipo-slip)) — Altman won't list below $1T.
- **Sonnet 5 introductory pricing** ($2 in / $10 out per M tokens, through Aug 31) makes Claude the **cheapest near-frontier per token** if you route right. Anthropic's own token economics improved sharply.
- **CS-grad market data (July):** general CS unemployment **6.1%**; **AI/ML engineer openings +59% vs 2020 baseline; SDE −49%**; AI/ML salaries **$134K–$193K** with a **~43% AI-skill premium**; recruiters spend **<10s on resumes** and **80% more time on GitHub with runnable code / live demos**.
- **Layoffs, real numbers (year-to-date):** 267 layoff events, **185,894 workers**, **56% of events explicitly cite AI**, 150 companies. Recent notable: **Intuit −3,000 (17%)**, **Microsoft −4,800 (2.1%)**.

**Sources:**
- [FinalRoundAI — CS job market 2026: what graduates must know](https://www.finalroundai.com/blog/computer-science-graduates-face-worst-job-market-in-decades) `[analysis]`
- [SQ Magazine — Software engineer layoff statistics 2026](https://sqmagazine.co.uk/software-engineer-layoff-statistics/) `[secondary]`
- [TechCrunch — Every major tech layoff in 2026 that name-checked AI](https://techcrunch.com/2026/07/06/the-running-list-major-tech-layoffs-in-2026-where-employers-cited-ai/) `[secondary]`
- [TechCrunch — AI was supposed to kill engineering jobs, but new data suggests they're the most resilient](https://techcrunch.com/2026/06/24/ai-was-supposed-to-kill-engineering-jobs-but-new-data-suggests-theyre-the-most-resilient/) `[secondary]`
- [Pin — Tech job market 2026: layoffs, AI salaries, hiring data](https://www.pin.com/blog/tech-job-market-report/) `[analysis]`
- [Skillsyncer — 2026 tech layoffs tracker (live)](https://skillsyncer.com/layoffs-tracker) `[aggregator]`

### Why it matters to you

- **Job lens — negotiate this way this quarter:**
  1. **Base + signing** > equity for early-career offers at OpenAI (2027 horizon). At Anthropic, private-round comp is more competitive; you can be more equity-tolerant given the more likely 2026-2027 liquidity window.
  2. **Ask for RSU refresh cycles** on any private-lab offer — the private-market runway just got 12+ months longer, so a single-grant vest is more diluted risk than a year ago.
  3. **When two offers are close on comp, take the one that lands you closer to the [§1](#1-anthropic-destination) destination map.**
- **Startup lens:** The **Sonnet-5 introductory price** is a *time-limited arbitrage* — August 31 is the deadline. Any experiment / MVP you run this month is roughly 60% cheaper than it will be in September. **Batch your MVP builds now**, not in Q4.
- **Insight:** The market is bifurcating cleanly: **general CS jobs are contracting; AI/ML engineering roles are expanding; and the middle ("SDE with some AI on the side") is being repriced downward.** Don't market yourself as the middle. Pick the specialty lane in `ME.md` (AI Integration Engineer / FDE) and lean hard.

→ Cross-link: [`01` §4 IPO slip](./01-big-lab-moves.md#4-ipo-slip) · [2026-05-15/05 §1 AI Engineer #1 fastest-growing](../2026-05-15/05-career-and-startup.md).

---

## 3. Weekend action — refresh the artifact against July, before you touch anything else {#3-weekend}

Given the mobile-agent and MCP-code-execution updates, the artifact you have queued needs one weekend upgrade to be July-current. Don't rebuild — *reframe.*

**Sat morning (2 hours):**
1. Install Claude Cowork on your phone (see [`03` §2 step 1](./03-practical-skills-and-tools.md#2-artifact)).
2. Pick the Routine (arXiv scanner recommended).
3. Wire it as a Routine on Claude Code on the web with one MCP tool (`SCHEMA_VERSION` tagged) + schedule trigger.
4. Screenshot the mobile push. Screenshot `/usage`.

**Sat afternoon (2 hours):**
5. Rewrite the README with the new "orchestration + real-tool verification + cost + **mobile operation**" framing.
6. Add a per-model routing table (Opus 4.7 planner + Sonnet 5 workers + Haiku 4.5 verifier + Grok 4.5 fallback for cheap answers, with a confidence threshold).
7. Screenshot the run's token trace pre/post the code-execution-with-MCP refactor ([`03` §1](./03-practical-skills-and-tools.md#1-code-exec-mcp)).

**Sun (90 minutes):**
8. Push the repo.
9. Write a **one-page LinkedIn post** — *"What I learned building a mobile-first Claude agent this weekend."* Include: the routing table, the token graph, the phone screenshot, one sentence about the Jumper hire as sector context.
10. Update `APPLICATIONS.md` — apply to **1 Anthropic Solutions / FDE**, **1 OpenAI Solutions**, **1 Norm AI or Taktile Solutions Engineer** (both funded this week; both need domain-native FDE-shaped hires).

**Mon:**
11. Send **3 cold emails to frontier-lab engineers** referencing the post + a specific technical question (see the [ME.md](../ME.md) list).

### Why it matters to you

- **Job lens:** The **8-step artifact** above is the single most efficient use of a summer weekend for a CS grad targeting the roles in your ME.md. It produces the resume line, the interview story, the LinkedIn post, and 3 concrete applications from one weekend of work.
- **Startup lens:** Same weekend, you also have the beta of a **"Claude-Routine-per-profession" product** — same code, different Routine per customer. That's the first day of a startup, not a portfolio piece.
- **Insight:** Cadence > intensity. You've had a full artifact plan queued since May 20; this weekend is the reframe that makes it July-current. Ship it. The next edition will move to the next thing.

→ Cross-link: [`03` §2 the step-by-step](./03-practical-skills-and-tools.md#2-artifact) · [`APPLICATIONS.md`](../APPLICATIONS.md) · [`ACTIONS.md`](../ACTIONS.md).

---

## 4. Micro-signals that changed the shape of the week (7 short items) {#4-micro-signals}

- **Together AI $800M / $8.3B, Aramco-led** ([`02` §4](./02-new-emerging.md#4-vc-record)). If you like infra: hire-signal. Cite Together AI as evidence you understand the "open-source infra as public utility" thesis.
- **Norm AI $120M Series C** — agentic compliance for regulated industries; **hiring domain-savvy Solutions Engineers.** Apply if finance / legal / policy background is even tangential.
- **Taktile $110M Series C** — agentic decision platform for banks + insurers; **NYC.** Same Solutions Engineer thesis as Norm AI; also strong for MLE with any credit-risk exposure.
- **Ollama $65M Series B** — local-model runner; developer-native. Portfolio play: ship a "run Sonnet 5 locally with a hybrid-cloud fallback" starter template on top of Ollama; it will get GitHub stars.
- **Prime Intellect $130M Series A** — decentralized training compute. Research-adjacent role opening; interesting for anyone with distributed-systems + ML background.
- **TwelveLabs $100M Series B (video)** — multimodal ML engineering hiring surface.
- **Anthropic reflection dashboard** ([`01` §2](./01-big-lab-moves.md#2-cowork)) — turn it on for a week, learn what you actually use Claude for. Those top-3 repeated prompts are your first 3 **Routines** — see [`03` §2](./03-practical-skills-and-tools.md#2-artifact).

**Sources:** see [`02` §4](./02-new-emerging.md#4-vc-record) for the funding-round citations.

### Why it matters to you

Six actively-hiring funded startups + a Big-Six-scale reshuffle in one week is roughly 3 months' worth of application signal compressed. Update the outreach list, refresh the cover-letter paragraph, and send. Don't overthink it.

→ Cross-link: [`ACTIONS.md`](../ACTIONS.md) · [`APPLICATIONS.md`](../APPLICATIONS.md) · [`STARTUPS.md`](../STARTUPS.md).
