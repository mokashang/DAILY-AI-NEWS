# Career & Startup — 2026-11-20

The Anthropic IPO **re-prices the entire AI career market overnight**. For the first time, a CS grad can model TC against a frontier lab with a real public ticker, not a guessed last-round mark. Simultaneously, **FDE moved up from "emerging job" to #2 on Pave's hot-jobs index** (AI Engineer is #1 at 97.4; FDE 97.0), with **1,143 live FDE postings across 462 companies** and **Databricks leading at 83 open reqs**. MSFT's 60K-person buyout window **closes Dec 1**, with company guidance now **"<5% uptake"** — materially softer than the Nov 14 edition expected, which means the Jan 1 job-market swamp will be ~2,000 ex-MSFT engineers, not 5,000. The **Ramp AI Index shows Anthropic now at 58.7% of business token spend** in the week ending Nov 15 — the highest provider concentration ever recorded, which is both a tailwind for Anthropic-ecosystem job hunting and a quiet antitrust risk through Q1 2027.

Tags: `#careers #fde #ai-eng #ipo #anthropic #msft #ramp #comp`

---

## 1. FDE boom continues — Pave #2 hot job, 1,143 live postings, comp refresh needed post-IPO {#1-fde-boom-continues}

**What happened (Nov 13–17):**
- **Pave's Nov 17 hot-jobs report**: **AI Engineer at 97.4 (#1), Forward Deployed Engineer at 97.0 (#2).** FDE moved up from Pave's Q2 "emerging jobs" watchlist.
- **Volume** (several counts, each snapshot-dependent):
  - **joinplank census (Nov 13):** 1,143 live FDE postings across 462 companies.
  - **dev.to tally (Nov 16, "forward deployed" title filter):** 184 roles. Leaders: **Databricks 83, OpenAI 36, Scale AI 12, Cohere 10.**
  - **getperspective (Nov 4):** 297 postings across 19 company job boards with "Forward Deployed" or "FDE" in the title.
- **Growth**: Lightcast (cited by third-party analysis) says US FDE postings went from **~200 in 2024** to **>5,200 in H1 2026** — ~26× in two years.
- **Comp** (Levels.fyi + posted ranges):
  - Levels.fyi US median: **$225K TC** (range $170–300K).
  - Frontier labs: **$300–550K TC** at senior FDE / Solutions Engineer level.
  - Glean Founding FDE: **$160–270K base** (per Nov 14 edition).
  - Distyl: **$150–250K base**.
- **Title fragmentation warning**: one analysis notes that filtering on the literal string "forward deployed engineer" **misses roughly a third of the live market** hiding under adjacent titles (Solutions Engineer, Deployment Engineer, Applied Engineer, Customer Engineer, Partner Engineer).

**Sources:**
- [Pave Hot Jobs Report (Nov 17) via Boston 25 News](https://www.boston25news.com/news/rise-specialized/22RBK7S7R4YLBPNHYF2Y5UYRCY/) `[secondary]`
- [joinplank — FDE Job Market: 1,143 roles across 462 companies](https://joinplank.com/fde-job-market) `[aggregator]`
- [DEV Community — AI startup hiring snapshot Nov 16, 6,481 open roles](https://dev.to/cleanrows/ai-startup-hiring-snapshot-16-november-2026-6481-open-roles-half-at-four-companies-4a7e) `[analysis]`
- [getperspective — 2026 FDE Hiring Trends](https://getperspective.ai/blog/2026-fde-hiring-trends-what-1000-job-posts-reveal) `[analysis]`
- [prepare.sh — Forward Deployed Engineer 2026](https://prepare.sh/articles/forward-deployed-engineer-2026) `[analysis]`
- [aiengineerinsights — FDE: What the Role Is, Salary, How to Get Hired](https://aiengineerinsights.com/blog/forward-deployed-ai-engineer/) `[analysis]`
- [Mobilunity — FDE Hiring Trends 2026](https://mobilunity.com/blog/forward-deployed-engineering-hiring-trends/) `[analysis]`
- [startup.jobs — Forward Deployed Engineer jobs](https://startup.jobs/roles/forward-deployed-engineer) `[aggregator]`

### Why it matters to you

- **Job lens:** **Three specific moves this weekend:**
  1. **Expand your FDE search string** — include "Solutions Engineer," "Deployment Engineer," "Customer Engineer," "Applied Engineer," "Partner Engineer." You've been missing a third of the market.
  2. **Apply to 5 Databricks FDE reqs** — they have the single-largest FDE opening in the category (83 reqs) and pay in the $200–350K TC band. Databricks is **post-IPO** so comp is RSU-legible — compare to ANT.
  3. **Rewrite the top of your résumé** with the **three-line FDE top-section** from the Nov 14 edition: one line **customer-facing work**, one line **prototype velocity**, one line **vertical you understand**.
- **Startup lens:** **FDE roles at Series A/B startups are founder-adjacent.** Glean Founding FDE ($160–270K) + the Nov 14 note that ~40% of 2025–26 vertical-AI YC founders came from FDE roles means **this is the single best path from "employed" to "founding engineer / spinout CEO" in the 2026 AI cycle.**
- **Insight:** **The Anthropic IPO just rebased FDE comp expectations.** Every candidate interviewing for FDE / Solutions at a private AI lab from now through Q2 2027 should ask: **"How does your RSU strike/valuation compare to ANT at current public price?"** Pre-IPO labs will respond either with a legible answer (good — negotiate from there) or with ambiguity (which tells you the lab is bracing for a down-round and you should re-price your offer).

→ Cross-link: [`01` §1 — ANT IPO Day 1](./01-big-lab-moves.md#1-ant-ipo-day) · [`05` §5 — Angel-check supply](#5-angel-check-supply) · [prior editions: 2026-11-14 FDE boom, 2026-10-14 Frontier Academy](../2026-11-14/05-career-and-startup.md#2-fde-boom)

---

## 2. The AI-infra lane after Jensen — second-tier infra roles got more interesting this week {#2-ai-infra-lane}

**Context:** Jensen Huang resigned Nov 12. NVIDIA still printed $115.8B. Rubin ramped at $20B first quarter. The **uncertainty is management, not demand.**

**What's actually re-priced:**
- **NVIDIA internal mobility** will slow for ~6 months. If you were planning to internal-transfer at NVIDIA, defer.
- **AMD / Broadcom / Marvell / Cerebras / Groq / Tenstorrent** just got a credible pitch window for hiring. Some open headcount:
  - **AMD MI400 / Instinct**: ML infra, perf engineering.
  - **Broadcom custom accelerators** (OpenAI deal): networking + chip design + co-development.
  - **Cerebras**: scaling engineers, inference-first.
  - **Groq**: LPU inference.
  - **Tenstorrent**: open-source RISC-V AI silicon (Jim Keller).
- **GPU-aware SRE / MLE at hyperscalers** (CoreWeave, Crusoe, Lambda, Together, Modal, Baseten, fal) — all growing, all hiring. **fal** just raised $1.65B at $16B two weeks ago and has been rate-limiting paying customers — they need infra talent *yesterday*.
- **Regulated-infra plays**: GridCARE (power), Sphere AI, Crusoe (campus-scale power + compute), the whole "AI-data-center power" sub-category still has tailwinds despite the Jensen noise.

**Comp**:
- Senior infra MLE at hyperscalers: **$250–400K TC**.
- GPU-aware SRE: **$200–350K TC**.
- Alt-silicon perf engineer: **$280–450K TC** (frontier labs pay more for MLPerf wins).

### Why it matters to you

- **Job lens:** If you've been eyeing NVIDIA or an NVIDIA-adjacent role for 2027, **don't withdraw — but widen your funnel to AMD + alt-silicon + hyperscaler-infra for a week**. Apply to **1 NVIDIA + 2 alt-silicon + 2 hyperscaler-infra roles** before Thanksgiving to get interviews lined up for January.
- **Startup lens:** **The alt-silicon story just got a legitimately open window.** If your startup is building anything in the inference / routing / cost-optimization / cross-silicon abstraction space, **the next 6 weeks are the warmest fundraising environment for it in 18 months** — investors are looking for a hedge against NVIDIA concentration, and the Jensen exit gives them cover to write the check.
- **Insight:** **Watch Broadcom.** The OpenAI × Broadcom 10 GW Ethernet deployment (from the Nov 14 edition) is the clearest multi-year threat to NVIDIA's rack-scale lock-in. If Broadcom shipments hit the roadmap on time (H2 2026 → 2029), **the 2028 compute-vendor map is very different from the 2026 one**. Broadcom's own hiring will spike through Q1 2027.

→ Cross-link: [`01` §2 — Jensen exit + Q3 earnings](./01-big-lab-moves.md#2-jensen-exit-and-earnings) · [prior edition: 2026-11-14 OpenAI × Broadcom Ethernet](../2026-11-14/01-big-lab-moves.md#4-nvidia-vera-rubin)

---

## 3. Microsoft 60K-employee buyout — decision Dec 1, likely <5% uptake, less swamp than feared {#3-microsoft-buyout}

**What's new since the Nov 14 edition:**
- **Microsoft spokesperson confirmed guidance "under 5% uptake"** — materially lower than the ~30% that accepted the April 2026 voluntary retirement program.
- **Decision deadline: early December** (specifically **Dec 1** per most coverage).
- **Exit date: Dec 31.**
- **Scope**: ~60K employees (level 70 and below) in US, UK, Canada, India.
- **Framing**: Microsoft says the program is about "the right talent in the right places" — **not framed as a cost cut**, not framed as AI-driven. Spokesperson explicitly denied AI was driving the buyout decision.
- **Comparison**: April 2026's voluntary retirement program (different scope) hit ~30% uptake. This one is wider and younger, which lowers expected uptake per the spokesperson.

**Sources:**
- [CNBC — Microsoft voluntary buyouts](https://www.cnbc.com/2026/10/26/microsoft-msft-voluntary-buyouts.html) `[secondary]`
- [Fortune — Microsoft 60K buyout analysis](https://fortune.com/2026/10/30/microsoft-voluntary-exit-offer-buyout-60000-employees/) `[analysis]`
- [BigGo Finance — Microsoft offers buyouts to 27% of workforce](https://finance.biggo.com/news/520e14ef-7f6a-4e20-a092-d671406e5b66) `[aggregator]`
- [KUOW — Microsoft offers voluntary buyouts to a quarter of workforce](https://www.kuow.org/technology/2026-10-26/microsoft-offers-voluntary-buyouts-to-a-quarter-of-its-workforce) `[secondary]`

### Why it matters to you

- **Job lens:** **The January market swamp is smaller than the Nov 14 edition expected.** If uptake is 3–5%, that's **1,800–3,000 ex-MSFT engineers** on the market Jan 1, not 5,000. **Your race is still real, but the stakes are lower.** You still want applications out before Thanksgiving (interview slots get booked up in early January once the ex-MSFT cohort hits).
- **Startup lens:** **The ex-MSFT hiring pool is smaller and more AI-adjacent than feared.** Microsoft is specifically **retaining AI + Azure + Copilot teams** per the "right talent in the right places" framing — so the buyout-takers are likely from more traditional product + Office + legacy Windows + support orgs. **Seed-stage talent sourcing from this cohort is still real, but it's not an AI-researcher firehose.** Calibrate accordingly.
- **Insight:** **This is the third voluntary-separation program at MSFT in 2026.** The pattern — **pay-to-leave > RIF** — is now the Big Tech default. Expect **Amazon / Google / Meta / Oracle to run similar programs in 2027** as the AI-reorg cycle continues. If you work at Big Tech and the Q4 financial reports mention "capital allocation," assume your business unit is in scope.

→ Cross-link: [prior edition: 2026-11-14 Microsoft 60K buyout intro](../2026-11-14/05-career-and-startup.md#1-microsoft-buyout)

---

## 4. Ramp AI Index (Nov 11 release, October data) — record adoption, slow spend growth, Anthropic 58.7% token share {#4-ramp-ai-index}

**Headline numbers from the November 2026 Ramp AI Index:**
- **US business AI adoption: 56.8%** — all-time high.
- **Spending growth: +1.65% M/M** — record spend but slow growth. **$16.32/employee median** (from $15.38 in September).
- **Top 1% concentration**: **$10.2K/employee/month** — top 1% drives ~**80% of OpenAI + Anthropic spend**.
- **Engineering = 72% of all classified AI spend** (dropping from summer highs, but still dominant).
- **Price trend**: average **$/M tokens fell 21% M/M**. Volume rising faster than spend = textbook deflationary dynamic.
- **Provider share (week ending Nov 15)**: **Anthropic 58.7%** of business token spend (highest ever recorded provider share).

**Sources:**
- [Ramp AI Index — November 2026 (official)](https://ramp.com/data/ai-index-nov-2026) `[primary]`
- [Ramp AI Index landing page](https://ramp.com/data/ai-index) `[primary]`
- [TechCrunch — Ramp data shows AI spending stalling just as Anthropic nears IPO](https://techcrunch.com/2026/11/06/ramp-data-shows-ai-spending-stalling-just-as-anthropic-nears-its-ipo/) `[secondary]`
- [DEV Community — Ramp AI Index: token volume +37.1%, spending +8.9%](https://dev.to/delimitter/ramp-ai-index-business-ai-token-volume-grew-371-while-spending-grew-89-36fc) `[analysis]`
- [FourWeekMBA — Top 1% spend $10.2K, 625× median](https://fourweekmba.com/ai-ramp-openai-anthropics-top-1-spend-10-2k-625x-median/) `[analysis]`
- [MLQ.ai — US business AI spending record in October](https://mlq.ai/news/us-business-ai-spending-hit-a-record-in-october-but-grew-less-than-2-ramp-data-shows/) `[secondary]`

### Why it matters to you

- **Job lens:** **"Anthropic has 58.7% of business token spend"** is the single highest-signal data point for your Anthropic-ecosystem focusing decision ([`ME.md`](../ME.md)). Your bet is *working*. Interview framing: **"I chose the Anthropic agentic stack as my portfolio focus because the Ramp AI Index shows Anthropic at 58.7% of business token spend as of mid-November, which means Anthropic-ecosystem experience is the single most-transferable AI skill in enterprise hiring."** That is a **provable positioning claim**, not an aspiration.
- **Startup lens:** **Spend growing +1.65% M/M while token volume grew +37.1% is the single clearest "the API margin is collapsing" signal in the market.** If your wrapper startup priced per-token or per-call, **re-model your unit economics** this weekend. Any startup that was <2× API cost is probably burning per-call now.
- **Insight:** **Watch for Q1 2027 antitrust chatter about Anthropic's concentration.** 58.7% of enterprise token spend from a single provider in an infrastructure category will attract DC attention within a quarter, especially post-IPO when the lab is visible to politicians. The **Anthropic ad-free policy pledge** (May 2026) is a defensive positioning move — expect more.

---

## 5. The angel-check supply thread — what happens between Dec 2026 and Q2 2027 {#5-angel-check-supply}

**Timeline of equity-into-liquidity moments this cycle:**

| Event | Date | Equity unlocked |
|---|---|---|
| Anthropic IPO (ANT) | **2026-11-18** (priced) | Primary + secondary; employees locked ~180d |
| ANT Lock-up expiry | **~2027-05-17 (Q2 2027)** | **Largest employee liquidity event of the AI cycle** |
| OpenAI IPO (if Q1–Q2 2027) | Rumored | Second-largest AI lock-up window of 2027 |
| MSFT buyout completions | **2026-12-31** (exits) | Cash-out; ex-MSFT engs flush with severance |
| Mercor Series D (last mark) | **2026-11-10** | Secondary market unlock — expect tender offers in H1 2027 |

**What this means for you:**

1. **Dec 2026 – Mar 2027**: Quiet period. Angel checks come from pre-existing senior people (VPs, early employees) who still had unlocked prior stock. Demand for founders will exceed supply of checks. **Lean into founder-in-residence programs, accelerators (YC W27 batch), and angel syndicates** during this window.

2. **Apr 2027 – Jun 2027 (Q2 2027)**: **The flood.** ANT lock-up expires ~May 17. Anthropic employees who IPO'd at $83 and ride to $150+ (a realistic 1-year range for a frontier AI lab) will have **meaningful liquid wealth** and will write angel checks and seed into AI startups. **This is the single hottest founder environment of the decade so far.**

3. **Jul 2027 onward**: The ex-Anthropic researcher seed class starts raising their own Series A / Bs. That compounds through Q3–Q4 2027.

**What to do now:**
- **Build the "I want to be in your pipeline" relationship** with 5 current Anthropic engineers you admire. Not pitching, just learning. **They are the Q2 2027 angel checks.**
- **If you are planning a founding move**, time your incorporation / YC application / seed round to **land in Q2 2027** when the market deepens.
- **If you want a job**, apply **now** — before the Q2 2027 founder flight depletes the senior-FDE pool and salaries jump again.

### Why it matters to you

- **Job lens:** **Timing your 2027 moves against the ANT lock-up calendar is a real planning advantage.** Interviewing with Anthropic right now gets you RSUs priced at $97; interviewing in April 2027 gets you RSUs priced at wherever the stock is. Interviewing in June 2027 means you're competing against Anthropic engineers who just cashed out and want your seat.
- **Startup lens:** **Plan backwards from Q2 2027.** If the plan is "seed round from ex-Anthropic angels," you need: incorporation Q4 2026, MVP Q1 2027, warm intros to ANT people Q1–Q2 2027, raise closes Q2 2027. **The calendar is tight — start the incorporation this month if that's the plan.**
- **Insight:** **IPO lock-ups are the single most under-discussed macro variable in AI hiring + startup fundraising.** Everyone talks about the IPO day pop; almost no one talks about the lock-up expiry. **Be the person in the room who does.**

→ Cross-link: [`01` §1 — ANT Day 1 close + lock-up](./01-big-lab-moves.md#1-ant-ipo-day) · [`ACTIONS.md`](../ACTIONS.md) — add "Q2 2027 relationships: 5 Anthropic eng intros before EOY"

---

## Weekend action stack (Friday → Sunday)

**Friday night (90 min):**
- Rewrite résumé with FDE three-line top section.
- Build the four-column "Role · Pre-IPO · Post-IPO · Lock-up" table.
- Post one 300-word LinkedIn note: "ANT is public — here's what it means for AI-eng comp."

**Saturday (3 hr):**
- 5 FDE applications (Databricks ×2, OpenAI ×1, Scale ×1, Cohere ×1).
- 2 Solutions Engineering applications (Anthropic, Glean).
- 1 AI-infra application (fal or AMD or Groq).

**Sunday (2 hr):**
- Router v2 shipped with GPT-6.2 added ([`03` §3](./03-practical-skills-and-tools.md#3-router-refresh)).
- Weekend write-up: "ANT IPO + Jensen out + GPT-6.2 — my re-priced model of the AI job market."
- Reach out to 2 Anthropic engineers you've been meaning to talk to.

**Total**: ~10 focused hours = **the single highest-leverage weekend of your Q4 2026.**
