# Big Lab Moves — 2026-11-24

OpenAI · Anthropic · Google · Meta · Apple · xAI · Microsoft · NVIDIA.

---

## 1. Anthropic IPO: ANT trades on Nasdaq, largest IPO in history

**What happened.** On **Wed Nov 18**, Anthropic priced its IPO at **$83 per share, above the marketed $70–$78 range**, and **upsized the offering to ~980M shares, raising ~$81.3B — the largest IPO on record, topping SpaceX's listing**. **$19.7B TTM revenue** was disclosed in the S-1. Ticker **ANT**, Nasdaq Global Select Market. Goldman + JPM + MS lead. Dual-class structure preserves founder control.

**Day 1 (Nov 19).** Opened **$111.50 (+34%)**, traded a **$92.72–$115.10** range, **closed $97.17 (+17.07% vs. IPO)** on **~840M shares**. Fully-diluted Day-1 market cap landed at **~$1.27–1.5T** across different counting conventions (Yahoo Finance: $1.27T; CNBC + Fox + Wikipedia: ~$1.5T) vs. **last private mark $965B** at the Series H in May.

**Day 3 (Nov 23).** ANT **−5% after-hours** on a report that **Apple is hiring for a competing on-device AI-agent effort** (see §2).

**Sources.**
- [primary] [Anthropic S-1 (Oct 26, 2026)](https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=anthropic) (via EDGAR)
- [secondary] [CNBC: Anthropic IPO raises over $81 billion in largest offering on record, topping SpaceX (Nov 18)](https://www.cnbc.com/2026/11/18/anthropic-ipo-ai-offering-price.html)
- [secondary] [Fox News: Anthropic soars 34% past IPO price in Nasdaq debut](https://www.foxnews.com/live-news/anthropic-claude-ai-ipo-nasdaq-11-19-26)
- [aggregator] [Wolf Financial: ANT live blog (Day 1 range + close)](https://wolf.financial/blog/anthropic-ipo-live)
- [secondary] [Yahoo Finance: How to buy a company's stock when it IPOs — Anthropic](https://finance.yahoo.com/personal-finance/investing/article/anthropic-ipo-how-to-buy-a-companys-stock-when-it-ipos-201237173.html)

**Why it matters to you.**
- **Job.** Every Anthropic req from today is a **public-market comp conversation**: a Senior FDE at $300–550K TC is readable in actual ANT shares. You can price the offer against your job boards in seconds. Negotiate on **restricted stock units at current ANT price + a lockup-expiry multiplier**, not on "potential upside."
- **Startup.** The **~6-month lockup (expiry ~May 2027)** is now the single most important date on your 2027 calendar. Ex-Anthropic researchers who want to found hit the market with **liquid personal capital for the first time**. Q2 2027 is going to be the hottest **"ex-Anthropic researcher pre-seed"** window of the decade. If you want to be at the first dinner, **start sending cold emails to Anthropic researchers NOW** (the ones who will sell in Q2 and raise in Q3).
- **Insight.** Frontier AI is now a **public-market asset class**. Anthropic + OpenAI + SpaceX going public inside ~12 months means their hiring plans become **legibly structured** (public-quarter SBC targets, quarterly engineering-headcount disclosures in 10-Qs), and the "secret lab" narrative premium collapses. The market just priced **$1.27–1.5T on $19.7B of TTM revenue = ~65–75× sales** — a number that only closes if the agent-commerce platform (Claude Meetings, Businesses in ChatGPT–equivalent) actually attaches.

`#anthropic #ipo #ant #comp #public-markets`

---

## 2. Apple's competing on-device AI agent appears in job listings (Nov 23)

**What happened.** On **Mon Nov 23**, a round of Apple job listings — primarily in Cupertino and Zurich — surfaced describing engineering work on **"on-device foundation-model agents with iOS Extensions integration"** and **"system-level agentic policy enforcement"**. ANT closed Monday down ~1% and then fell **~5% in after-hours** on the news. This confirms the long-running thread that Apple's **May 2026 iOS 27 multi-AI Extensions framework** was always the scaffolding for Apple's own in-house agent, not just a Switzerland for Anthropic / OpenAI / Google.

**Sources.** [aggregator] AI Weekly Alerts top story Nov 23 ("Anthropic Shares Fall ~5% After-Hours on Debut as Apple Job Listings Reveal Rival AI-Agent Push"); [primary] [Apple Jobs — "AI/ML — Agent Platform" and "Software Engineering — Agentic System Services"](https://jobs.apple.com/) (search terms, filters: AI/ML, Platform Architecture).

**Why it matters to you.**
- **Job.** Apple just added a job family that **pays at FAANG L5/L6 bands, sits outside the frontier-lab pipeline, and has a known 3–9 month interview loop**. For CS grads who want AI-adjacent SWE/MLE roles at the top comp band without betting on a startup, this is a **new #2 target behind OpenAI/Anthropic FDE**. Expect reqs to surface publicly within 2–4 weeks.
- **Startup.** If Apple does ship a first-party on-device agent at WWDC 2027, the **"anyone-but-Apple" distribution wedge** reopens: any third-party agent that runs on non-Apple hardware (Windows, Chromebook, Android, Meta Ray-Ban, humanoid) gets a tailwind. The **Aluminium OS / Googlebook (from May I/O)** is suddenly a more interesting build-target than it looked in June.
- **Insight.** This is the **first serious crack in a lab's post-IPO narrative** — a reminder that **public-market caps re-price daily** on things that would have been a one-day rumor at a private lab. The "secret lab" hiring pitch dies; the "quarterly earnings risk" hiring pitch is born.

`#apple #agents #distribution #ios #on-device`

---

## 3. Gemini 4 wave: Carbon (Nov 10), Hydrogen (Nov 12), Neon (Nov 18)

**What happened.** Google DeepMind shipped **three Gemini 4 variants in nine days**:

- **Gemini 4 Carbon (Nov 10)** — the flagship, now available on the models page.
- **Gemini 4 Hydrogen (Nov 12)** — **the new free-tier model AND the model powering Google Search's AI features**. This is the free-tier moat Google has that Anthropic + OpenAI structurally cannot match.
- **Gemini 4 Neon (Nov 18)** — the agentic-coding / long-form-knowledge tier. Rolling out on the Google DeepMind X account post. "Equal to or better than Carbon at ~3× the speed and ~60% the cost" (DeepMind internal evals).

**Benchmarks.** Neon took **#1 on the Artificial Analysis Coding Agent Index at 58.64, vs. Claude Fable 5.2 at 58.47** (a razor-thin lead). Vendor-reported SWE-Atlas-QnA has Neon at 67.7 vs. GPT-6.2 Astra at 55.1. **Harness matters**: Neon scores 12.8% on SWE-sweep with the mini-SWE agent but **39.0% in Google Antigravity** — a >25pp swing on the agent-container, not the model.

**Sources.**
- [primary] [Google DeepMind on X: "Gemini 4 Neon is rolling out now…" (Nov 18)](https://x.com/GoogleDeepMind/status/2123167884411077030)
- [primary] [Google DeepMind Models page](https://deepmind.google/models/)
- [analysis] [Artificial Analysis Coding Agent Index — gemini-4-neon-high leaderboard entry](https://arena.ai/leaderboard/agent/code/models/gemini-4-neon-high-m0ck)
- [secondary] [Winbuzzer: Google Gemini 4 Neon Beats Claude Opus 5.5 on Benchmarks (Nov 19)](https://winbuzzer.com/2026/11/19/gemini-4-neon-carbon-estimated-benchmark-task-time-xcxwbn/)
- [secondary] [officechai: Gemini 4 Neon Beats Claude Opus 5.5, GPT 6.2 Sol On Most Benchmarks](https://officechai.com/ai/gemini-4-neon-benchmarks/)
- [analysis] [Simon Willison: Gemini Hydrogen as Google Search's new free-tier model (Nov 12)](https://simonwillison.net/tags/llms+ai/)

**Why it matters to you.**
- **Job.** If you're interviewing for FDE/MLE and you have one `gemini-4-neon` vs. `claude-fable-5-2` comparison on your own task **with a measured agent-harness choice**, you beat every candidate who said "I prompted X well." The Antigravity vs. mini-SWE 25pp swing is the single most interviewable example of **harness-aware eval design** on the market right now.
- **Startup.** Hydrogen is **free**, high-capability, and **inside Google Search**. Any consumer-facing AI product that competed with the search bar for the "quick answer" lane just got its ground torched. **Route around it**: pick wedges where (a) the answer must have audit trail (Claude for Legal), (b) the data lives inside a closed enterprise (Palantir territory), or (c) there's latency/privacy that free-tier Google can't serve (on-device).
- **Insight.** Three Gemini 4 variants in nine days vs. one Claude Fable 5.2 in the same window is **release-cadence as marketing**. Google now has the ad-platform discipline at the model layer — **ship small, ship often, let the market name winners**. The "big named model release" era (GPT-5, Claude Opus, Gemini 2.5 Pro) is giving way to **continuous-fractional-upgrade cadence** at every lab.

`#google #gemini #carbon #hydrogen #neon #coding #routing`

---

## 4. Claude Fable 5.2 / Mythos 5.2 recap (Nov 9) — context for the week

**What happened (if you missed it in 2026-11-14).** Anthropic shipped **Claude Fable 5.2 and Mythos 5.2 on Nov 9** at **$8/M input · $40/M output** standard, **2× for fast mode**; **outputs up to 30% faster than Fable/Mythos 5.1**. Mythos 5.2 reported **10.2% more vulnerabilities found than Opus 5.5 and 14.4% more than Mythos 5.1** on Anthropic's internal cyber bench. **Fable 5.2 took #1 on Artificial Analysis Intelligence Index v5 at 65** (dethroned by Gemini 4 Neon on the *coding sub-index* nine days later, but still #1 overall). Pro subscribers and standard Team seats could use Fable without credits until Nov 16. The **Developer Platform** also got a **self-hosted Managed Agents** option.

**Sources.**
- [primary] [Anthropic Release Notes (Releasebot — Anthropic)](https://releasebot.io/updates/anthropic)
- [secondary] [Constellation Research: Anthropic releases Mythos 5.2, Fable 5.2](https://www.constellationr.com/insights/news/anthropic-releases-mythos-52-fable-52)
- [secondary] [AI Weekly: Anthropic ships Claude Fable 5.2 and vetted-tier Mythos 5.2](https://aiweekly.co/alerts/anthropic-ships-claude-fable-52-and-vetted-tier-mythos-52)
- [secondary] [TestingCatalog: Anthropic launches Claude Fable 5.2 and Mythos 5.2](https://www.testingcatalog.com/anthropic-launches-claude-fable-5-2-and-mythos-5-2/)
- [analysis] [Shelly Palmer: Anthropic's Fable and Mythos Upgrade](https://shellypalmer.com/2026/11/anthropics-fable-and-mythos-upgrade/)

**Why it matters to you.**
- **Job.** Fable 5.2 pricing is now the comp-line for routing arguments: a well-designed router that uses **Haiku 5.5 for 70% of calls + Fable 5.2 for 30%** vs. all-Fable is the single highest-leverage one-week project you can show at an FDE interview.
- **Startup.** **Mythos 5.2's +10.2% vuln delta over Opus 5.5** is the single strongest signal that **agentic-cybersecurity is the top vertical AI-application category for 2027**. See the Rox/Nooks/Decagon comp wave in [`02`](./02-new-emerging.md) — security is next.
- **Insight.** The **"one model for everything"** era is done. Vertical Claudes (Finance, Legal, Manufacturing, Cyber) now ship as **Mythos-tier gated access**, while Fable owns the general tier. Expect **"Claude for Research"** or **"Claude for Education"** next — track Anthropic's `claude-*-5-3` codenames.

`#anthropic #fable #mythos #cyber #routing`

---

## 5. OpenAI November cluster: GPT-5.6 GA + ChatGPT Wallet + verticals + mobile redesign

**What happened.** OpenAI shipped a full November product cadence:

- **GPT-5.6 Sol / Terra / Luna (GA, early November)** — the three-tier family: **Sol** (flagship, new high on **Agents' Last Exam**), **Terra** (everyday), **Luna** (low-cost). Available in ChatGPT, Codex, and API.
- **ChatGPT Images 2.6 (Nov 4)** — faster generation, GIF support, API editing controls.
- **Businesses in ChatGPT beta + Business Hub (Nov 10)** — SMB workspace; verified businesses can set up a customer-question agent.
- **Advanced + Standard Voice retirement announcement (Nov 10)** — both retire **Dec 11**, replaced by **GPT-Live**.
- **ChatGPT Wallet (Nov 13)** — **biometric purchase approval** for US Pro, agent-initiated purchases.
- **ChatGPT for Healthcare & Clinicians (Nov 16)** — medical evidence search + inline citations.
- **ChatGPT for Sales (Nov 17)**.
- **Redesigned mobile app (Nov 19)**.
- **ChatGPT Space (Nov 20)** — rolling out to Plus users 18+.

**Sources.**
- [primary] [OpenAI — GPT-5.6](https://openai.com/index/gpt-5-6/)
- [aggregator] [Releasebot: ChatGPT Updates by OpenAI — November 2026](https://releasebot.io/updates/openai/chatgpt)
- [aggregator] [Releasebot: OpenAI Release Notes — November 2026](https://releasebot.io/updates/openai)
- [analysis] [ScriptByAI: OpenAI & ChatGPT Timeline — GPT Release Dates to GPT-6.2 (2026)](https://www.scriptbyai.com/timeline-of-chatgpt/)

**Why it matters to you.**
- **Job.** ChatGPT Wallet = **agent-commerce job family**. Any team shipping payments + chat + policy enforcement at the chat layer now has budget for engineers who know **Stripe/Plaid/Adyen + biometric auth + agent-policy enforcement**. If you have one working demo (even a hobby project), lead your résumé with it.
- **Startup.** **ChatGPT for Healthcare + Sales + Wallet** is OpenAI running the **AWS-2010s playbook at warp speed**: horizontal platform (ChatGPT) + vertical services (Healthcare, Sales, Business Hub) + per-task premium pricing. Every vertical ChatGPT ships **forecloses a vertical wrapper startup**. Pick wedges OpenAI *will not* ship (regulated data residency, union-labor, physical hardware integration, non-English-first markets).
- **Insight.** **Voice goes from Advanced → GPT-Live in one month**. This is the pattern of the rest of 2026: **feature-named products → model-native capabilities**. The 2026 "voice agent" wrapper startups just got repriced to a thin margin.

`#openai #gpt-5-6 #chatgpt-wallet #verticals #voice`

---

## 6. Microsoft 60K-employee buyout: Dec 1 window closes

**What happened.** On **Oct 26**, Microsoft opened a **Voluntary Exit Offer** to **up to 60,000 employees (~27% of global workforce)**, L70-and-below in US/Canada/UK/India. Participating orgs: **Copilot, Windows + Devices, AI experiences, Xbox, finance, HR**. Excluded: commercial, marketing, security. Window closes **Dec 1**; exits **Dec 31**. April's narrower 7%-of-US program had **30%+ uptake**.

**Sources.**
- [secondary] [Fortune: Microsoft's voluntary exit offer / buyout — 60,000 employees (Oct 30)](https://fortune.com/2026/10/30/microsoft-voluntary-exit-offer-buyout-60000-employees)
- [secondary] [TechRepublic: Microsoft Offers Buyouts to 60,000 Staff in Windows, Copilot](https://www.techrepublic.com/article/news-microsoft-buyouts-60000-employees-copilot-windows/)
- [secondary] [TechSpot: Microsoft offers voluntary buyouts as AI spending takes priority](https://www.techspot.com/news/112174-microsoft-offers-voluntary-buyouts-thousands-us-workers-ai.html)
- [secondary] [Fortune: Microsoft offers buyouts to nearly 30% of workforce in ongoing AI shift (Oct 26)](https://fortune.com/2026/10/26/microsoft-offers-buyouts-to-nearly-30-of-workforce-in-ongoing-ai-shift/)

**Why it matters to you.**
- **Job.** **Apply in December, interview before Jan 15.** If you're at Microsoft, the Dec 1 math is yours; if you're applying anywhere else, **the window to get an offer from Glean/Distyl/Decagon/Sierra/Harvey/OpenAI/Anthropic before the ex-MSFT wave swamps intake is this week and next.** Recruiters will triage ex-MSFT PRINCIPAL / L65 engineers above new-grad résumés in January.
- **Startup.** 1,800–5,000 ex-MSFT engineers hit the market Jan 1, and April's pattern says ~30% had L65+ experience. **Pre-seed hiring in Jan–Mar 2027 is going to be the easiest "first-10-engineer" market in two years**, IF you're a founder with a seed check. Watch for ex-Copilot founders on the Oct-26-plus-6-month timeline.
- **Insight.** **Pay-to-leave is now the preferred Big Tech restructuring playbook**. Third voluntary-separation program at MSFT in 2026, no public layoff. Expect Google, Amazon, Meta to follow this pattern — because it preserves the relationship, the alumni-network, and the hiring option.

`#msft #layoffs #timing #careers`

---

## Cross-references

- [`00-tldr`](./00-tldr.md) · all the above in 60 seconds.
- [`02-new-emerging`](./02-new-emerging.md) · funding + Tesla Optimus + the vertical-agent comp pattern.
- [`04-research-progress`](./04-research-progress.md) · agent-memory wave (BioMem / Prospective / MemFail / Evidence-Linked / Peer).
- [`05-career-and-startup`](./05-career-and-startup.md) · MSFT Jan 1 wave · FDE still #1 · YC F26 Demo Day Dec 2.
