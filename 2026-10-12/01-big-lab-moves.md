# Big Lab Moves — 2026-10-12

Two Anthropic model releases six days apart (Opus 5.5 Sept 22 + Sonnet 5.5 Sept 28), an OpenAI DevDay that quietly ceded the pure-model race and bet the distribution surface instead (Sept 29), an **explicit "not 2026" from Altman** on an OpenAI IPO (Fortune, Sept 12) while Anthropic's confidential S-1 keeps pointing at a fall listing, and the **EU AI Act's GPAI enforcement powers went live Aug 2** with no first enforcement action yet. **The frame:** last month's "four frontier models in one week" shock resolved into a *structural* re-ordering — Anthropic flagship + Anthropic workhorse + OpenAI platform, each with a distinct market job to do.

Tags: `#labs #anthropic #openai #google #ipo #claude #opus-5-5 #sonnet-5-5 #gpt-6 #devday #dots #computer-use #eu`

---

## 1. Claude Opus 5.5 — Anthropic cuts the flagship price while releasing it {#1-opus-55}

**What happened:** On **Sept 22, 2026** (exactly two months after Opus 5), Anthropic released **Claude Opus 5.5**, the first model in a new 5.5 family. Third-party coverage reports:

- **Terminal-Bench 4.0:** **66.4%** (xhigh effort) — vs Fable 5.1 55.8%, Opus 5 52.3%. Max-effort: 64.8%.
- **GDPval-AA v2.1:** **1846 Elo** — ahead of Fable 5.1 (1735), Opus 5 (1708), OpenAI GPT-6 Astra (1542).
- **FrontierCode v1.1:** **54.4%** — vs GPT-6 Astra 53.3%, Fable 5.1 50.3%, Opus 5 48.0%.
- **OSWorld 2.0:** **81.8%** partial-task completion.
- **Artificial Analysis Intelligence Index:** 58 — reported as the best measured as of launch.
- **Context:** 1M input / 128K output.
- **Pricing:** **$4 per 1M input / $20 per 1M output** — a **20% cut on both legs vs Opus 5** ($5 / $25).

Anthropic said Sonnet 5.5 and Haiku 5.5 would follow "in the coming weeks" (Sonnet shipped six days later; see §2). Some scores were obtained at max effort; safety systems redirected certain biology/cybersecurity prompts to earlier models. Opus 5.5 reportedly trails GPT-6 Astra in multi-step business-workflow execution — a crack OpenAI's DevDay turn (§3) widens on purpose.

**Sources:**
- [computingforgeeks — Claude Opus 5.5 released: features and benchmarks](https://computingforgeeks.com/claude-opus-5-5-released-features-benchmarks/) `[secondary]`
- [Layer3 Labs — Claude Opus 5.5 Benchmarks (reviewed Sept 22, 2026)](https://www.layer3labs.io/guides/claude-opus-5-5-benchmarks) `[secondary]`
- [tosea.ai — How to use Claude Opus 5.5: complete guide](https://tosea.ai/blog/claude-opus-5-5-complete-guide) `[secondary]`
- [metricnexus — Claude Opus 5.5: benchmarks, pricing, real costs](https://metricnexus.ai/blog/claude-opus-5-5-benchmarks-pricing) `[secondary]`
- [claudefa.st — Claude Opus 5.5](https://claudefa.st/blog/models/claude-opus-5-5) `[secondary]`

### Why it matters to you

- **Job lens:** A **flagship price cut delivered *with* the release** is a leading indicator, not a lagging one — it tells you (a) margin on Opus 5 was more than enough, (b) Opus 6 is already in training, (c) Anthropic is confident enough in paid-conversion to trade list-price for seat-count. Translation for your job search: **Anthropic is in growth-hire posture**, not margin-defense posture. Weight Anthropic Solutions / FDE / Integration applications **above** your OpenAI applications for the next 90 days. Use the Opus-5.5 price cut as the specific line in your cover letter ("the pricing says you're hiring for scale, so here's what I'd bring to that curve").
- **Startup lens:** The $4/$20 flagship resets the economics for **two whole startup categories**. (a) Agent workflows that were previously "too expensive to run on Opus" are now **20% cheaper by default** — anything you built last quarter that used Sonnet 5 for cost reasons should be re-benchmarked on Opus-5.5 this week (you may be surprised). (b) **Agent-cost-observability tooling** gets a durable TAM — every founder re-tuning their router this month is a customer. The dual Opus-5.5 + Sonnet-5.5 release gives you a two-datapoint price curve to pitch VCs with.
- **Insight:** The *order* of the three Anthropic releases this cycle — Fable 5.1 (Sept 1) → Opus 5.5 (Sept 22) → Sonnet 5.5 (Sept 28) — is itself the news. Anthropic shipped **a specialty model (code/finance), then its flagship, then its workhorse** in a 27-day window. That's a frontier lab iterating a *family*, not a single model. OpenAI's three-SKU strategy (Astra, Sol, Luna) is similar but staggered differently — the race in Q4 is **families, not flagships**, which means your resume talking point should be "I route across a family" rather than "I know the latest model."

→ Cross-link: [`03` §1 Router update](./03-practical-skills-and-tools.md#1-router-update) · [`05` §2 Anthropic hiring posture](./05-career-and-startup.md#2-anthropic-hiring).

---

## 2. Claude Sonnet 5.5 — the workhorse re-prices under the flagship {#2-sonnet-55}

**What happened:** **Sept 28, 2026** — Anthropic released **Claude Sonnet 5.5**. Available on the Anthropic API, Claude app, and OpenRouter at launch.

- **Pricing:** **$2 input / $10 output per 1M** — same list price as Sonnet 5, but Anthropic claims up to **30% cheaper per task** and **>30% faster** on real agentic workloads (the delta comes from fewer tokens-per-task + lower per-token latency, not price).
- **Context:** 1M input tokens.
- **Positioning:** The workhorse under the Opus 5.5 flagship, built for agentic workflows with heavy tool-use and multi-turn planning.
- **Haiku 5.5:** announced; one Japanese outlet reports it launched with ~75% cost reduction vs Haiku 4.5, but the Anthropic model-card page still lists Haiku 5.5 as announced/preview, so treat the Haiku release status as unresolved pending the official announcement.

**Sources:**
- [AI Indigo — Claude Sonnet 5.5 release](https://aiindigo.com/blog/ai-arena-claude-sonnet-5-5-release) `[secondary]`
- [DataLearner — Claude Haiku 5.5 model profile](https://www.datalearner.com/ai-models/pretrained-models/claude-haiku-5-5) `[secondary]`
- [Gradually.ai — Claude Haiku 5.5 model profile](https://www.gradually.ai/en/ai-models/claude-haiku-5-5/) `[secondary]`
- [gori.me — Claude Haiku 5.5 launch, ~75% cheaper than Haiku 4.5](https://gori.me/?p=171039) `[secondary]`

### Why it matters to you

- **Job lens:** The workhorse-tier model is the one your interview questions will target. Every FDE/AI-Engineer loop in Q4 will have a system-design question of the form "design an agent that runs at X QPS at Y cost." **The cheapest correct answer is now Sonnet 5.5, not Sonnet 5**, and the answer that gets you promoted is "Sonnet 5.5 as the default, Opus 5.5 for the hard planner nodes only, Haiku 5.5 for the ultra-cheap verifier." Memorize the three price points: Opus-5.5 $4/$20, Sonnet-5.5 $2/$10, Haiku-5.5 (TBD, but ~$0.25/$1.25 expected).
- **Startup lens:** The **~30% cheaper-per-task** claim is the first time Anthropic has advertised a *behavioral* price cut (tokens-per-task) rather than a *listed* price cut. If it holds under third-party eval, **~30% is the kind of economics that re-opens vertical-SaaS wrappers** — a Legal-AI or Finance-AI vertical that penciled at 20% gross margin suddenly pencils at 45%. Re-visit the vertical-Claude-for-X workflow library in your portfolio ([`ME.md`](../ME.md#active-portfolio-artifacts)) with Sonnet-5.5 as the backbone and recompute the unit economics on your pitch deck.
- **Insight:** Anthropic's 2026 release pattern — flagship first, workhorse ~1 week later, Haiku ~2–4 weeks after — matches a **"revenue cascade"**, not a technical cascade. The Opus launch drives press and enterprise RFPs; the Sonnet launch drives per-seat revenue; the Haiku launch drives developer-tier adoption. Learn the cascade; it's the pattern every lab is converging to. (Watch whether OpenAI's "Astra / Sol / Luna / Ultrafast" rollout matches this shape over the next 60 days.)

→ Cross-link: [`03` §1 Router update](./03-practical-skills-and-tools.md#1-router-update) · [`05` §3 Routing-skill re-price](./05-career-and-startup.md#3-reprice).

---

## 3. OpenAI DevDay 2026 — the platform turn {#3-openai-devday}

**What happened:** **Sept 29, 2026, Fort Mason, San Francisco.** OpenAI's official recap frames it as "20+ announcements across ChatGPT, Codex, our models, and entirely new forms of working with AI." The structural shift inside those bullets: **OpenAI is no longer competing on pure model quality in Q4; it is competing on the distribution surface.**

Key announcements (OpenAI recap + secondary tracking):

- **Dots** — persistent, always-on agents powered by GPT-6 Astra. Designed to take on *ongoing* responsibilities (not just task-shaped requests).
- **Agents API with Computer Use** — the full computer-use primitive productized, with a developer SDK and sandboxed execution. Direct response to Anthropic Managed Agents + Claude Code's agent primitive from May.
- **Decisions API** — a declarative API for complex decision workflows (reported detail is light; watch for the formal docs).
- **ChatGPT as a shared humans+agents workspace** — developers can now ship **native experiences inside ChatGPT**, reaching OpenAI's **~1.2B weekly users** without their own distribution motion. This is the single most consequential platform move of the year.
- **GPT-6.1 Sol + Ultrafast** — model refresh + a premium inference tier.
- **Pro 500** — a **$500/mo tier** matching Anthropic Max-20× pricing.
- **Codex Security Cloud** — hardened Codex execution for regulated enterprises; broader plugin platform.

**Hardware:** No hardware announcement reported in the recap or secondary coverage.

**Sources:**
- [OpenAI — DevDay 2026 recap (official)](https://openai.com/index/devday-2026-recap/) `[primary]`
- [aitoolly — DevDay 2026 recap, 20+ announcements](https://aitoolly.com/de/ai-news/article/2026-09-30-openai-devday-2026-recap-over-20-major-announcements-highlighted-by-gpt-6-astra-and-new-developer-to) `[aggregator]`
- [agentpedia — OpenAI DevDay 2026, everything announced](https://agentpedia.codes/blog/openai-devday-2026-everything-announced) `[aggregator]`
- [SmartScope — DevDay 2026 features plan](https://smartscope.blog/en/blog/was-announced-openai-devday-2026-features-plan-developer-2026/) `[analysis]`
- [MacObserver — DevDay 2026 keynote preview](https://macobserver.com/news/openai-devday-2026-keynote-time-schedule-and-what-developers-should-expect) `[secondary]`

### Why it matters to you

- **Job lens:** The platform turn re-prices OpenAI's hiring in two directions. **UP:** Applied-AI / FDE / Platform-Engineer roles that build native experiences inside ChatGPT get bigger (new TAM = 1.2B weekly users for every integration). **DOWN:** Pure model-research roles — because the near-term product moat is distribution, not frontier gain. For a CS grad targeting OpenAI, this means **shift your pitch from "I understand model internals" to "I can ship a native ChatGPT experience in a week."** Build one this week (see [`03` §2](./03-practical-skills-and-tools.md#2-dots-computer-use)) and lead your application with the demo link, not the resume.
- **Startup lens:** The ChatGPT-as-workspace move is **a classic platform risk/opportunity**. Risk: any wrapper you were building on top of ChatGPT may now be redundant. Opportunity: **the "native experience" slot is a unit of distribution** — if yours is first in a category inside ChatGPT, you get OpenAI's reach for free. The two founder wedges this opens: (a) **native-experience accelerators** (SDK + templates to publish into ChatGPT in <24 hours); (b) **cross-platform-agent neutrality layers** so you don't lock in to ChatGPT's distribution (hedge against future rev-share surprise). Pick one; add it to [STARTUPS.md](../STARTUPS.md).
- **Insight:** DevDay 2026 is the moment OpenAI **chose distribution over flagship**. Anthropic has the better flagship (Opus 5.5 numbers above), but OpenAI has 1.2B weekly users and a workspace primitive. **In 2027, the lab that wins is the one whose users don't have to leave to use the agent.** This re-draws your startup thesis: *distribution via ChatGPT* and *vertical depth via Claude* are now the two defensible slots. Everything in between is a feature.

→ Cross-link: [`03` §2 Dots + Computer-Use demo](./03-practical-skills-and-tools.md#2-dots-computer-use) · [`05` §4 OpenAI vs Anthropic hiring split](./05-career-and-startup.md#4-split).

---

## 4. Altman: "not 2026" — the IPO lead widens to ~24 months {#4-ipo-divergence}

**What happened:** In a Fortune interview published **Sept 12, 2026**, Sam Altman explicitly ruled out an OpenAI IPO in 2026 ("I would say not 2026"), citing AI safety and the "ill-advised moment" to list. He did *not* commit to 2027. Bloomberg reads the remarks as pushing an OpenAI listing into 2027 or later.

Meanwhile, **Anthropic's confidential S-1** — filed **June 1, 2026** after a $65B Series H at a **$965B post-money** — continues to point at a fall 2026 listing per NYT and secondary tracking. The crowded IPO window (SpaceX in parallel) remains the external risk.

**Sources:**
- [Fortune via Free Press Journal — Sam Altman rules out OpenAI IPO in 2026](https://www.freepressjournal.in/tech/sam-altman-rules-out-openai-ipo-in-2026-cites-ai-safety-as-the-reason) `[secondary]`
- [Virginia Business — Altman delays IPO, extinction risk](https://virginiabusiness.com/openai-sam-altman-delays-ipo-ai-extinction-risk/) `[secondary]`
- [Canberra Times — OpenAI won't do 2026 IPO](https://www.canberratimes.com.au/story/9349026/openai-wont-do-2026-ipo-extinction-risk-unacceptable/) `[secondary]`
- [Pulse2 — OpenAI rules out 2026 IPO](https://pulse2.com/openai-rules-out-2026-ipo-as-sam-altman-prioritizes-ai-safety-work/) `[secondary]`
- [Yahoo/Reuters — Anthropic files to go public](https://finance.yahoo.com/markets/stocks/articles/anthropic-files-public-163655473.html) `[primary]`
- [TechCrunch — Anthropic files to go public](https://techcrunch.com/2026/06/01/anthropic-files-to-go-public/) `[secondary]`
- [DataCenterDynamics — Anthropic confidentially files S-1](https://www.datacenterdynamics.com/en/news/anthropic-confidentially-files-for-ipo-with-the-us-sec/) `[secondary]`
- [richnerds substack — Anthropic $965B IPO filing analysis](https://richnerds.substack.com/p/anthropic-ipo-filing-2026) `[analysis]`

### Why it matters to you

- **Job lens:** The IPO calendar flips the near-term liquidity-and-grant comparison hard. **Anthropic**, listing this fall, is already resetting its RSU/grant pricing to the public-equivalent price band — meaning **new-hire grants are being written at IPO-anchor valuations**, which is historically the single best moment to join a lab. **OpenAI**, with a 2027+ horizon, has **more private-stage upside but less liquidity transparency** — your grant price depends on their next tender offer, not a public print. Translation: if you're risk-averse or want a clean comp conversation, Anthropic has a 12–18-month hiring window with better price discovery. If you believe OpenAI will outperform the public tape, OpenAI's grants are longer-dated. Weight your applications by *your own* risk preference, not by brand.
- **Startup lens:** **Anthropic's IPO becomes the first public-market comp for frontier AI.** Every founder pitching an AI startup through Q4 will be benchmarked, implicitly, against Anthropic's revenue multiple on opening day. If Anthropic prints at a **discipline-driven multiple** (growth + margin, not pure growth), your SaaS startup gets re-priced down; if it prints at a **narrative multiple** (comp to NVIDIA / SpaceX), you get re-priced up. Watch the opening-day pop closely; set your fundraise cadence around it. Also: **Anthropic alumni-founder flywheel starts post-lockup** (~Q2 2027). If your founder-hunt list doesn't have Anthropic alumni on it yet, add them now while they're still inside.
- **Insight:** The *why* of Altman's "not 2026" is more interesting than the *what*. Framing it as **AI safety** (not markets) is a signal to the policy/eval ecosystem — it tells Washington and Brussels that OpenAI is willing to accept delayed liquidity to preserve pre-deployment-review latitude. That reads as a soft concession on the Trump-EO / EU AI Act fronts, and it quietly **re-prices the pre-deployment-eval career lane upward** — safety / evals / assurance teams at labs just got a longer runway and a more publicly-committed executive sponsor.

→ Cross-link: [`05` §4 split hiring posture](./05-career-and-startup.md#4-split) · [2026-09-10/01 §2 Anthropic IPO thread](../2026-09-10/01-big-lab-moves.md#2-anthropic-ipo).

---

## 5. EU AI Act GPAI enforcement went live Aug 2, 2026 {#5-eu-enforcement}

**What happened:** The European Commission's AI Office formally gained enforcement powers over general-purpose AI (GPAI) providers under Articles 51–56 of the AI Act on **Aug 2, 2026**, with no first enforcement action yet named. Powers include:

- Demand documentation from GPAI providers.
- Order model evaluations.
- Require corrective measures up to and including market withdrawal.
- **Fine up to €15M or 3% of worldwide turnover (whichever is higher).**

GPAI enforcement is **centralized at the Commission** (unlike high-risk systems, which national market-surveillance authorities police). The Digital Omnibus package (Council approval June 29, 2026) pushed *Annex III high-risk* deadlines to Dec 2, 2027 but **left GPAI enforcement untouched**. Separately, systems placed on the market before Aug 2, 2026 have until Dec 2, 2026 to meet the Article 50(2) machine-readable marking requirement.

**Sources:**
- [CSA — EU AI Act GPAI Enforcement research note](https://labs.cloudsecurityalliance.org/research/csa-research-note-eu-ai-act-gpai-enforcement-20260803-csa-st/) `[analysis]`
- [sota.io — EU AI Act GPAI Enforcement August 2026](https://sota.io/blog/eu-ai-act-gpai-enforcement-august-2026-commission-powers-ai-office-developer-guide) `[analysis]`
- [Let's Data Science — EU activates AI Act powers](https://letsdatascience.com/news/eu-activates-ai-act-powers-over-model-providers-1db889b5) `[secondary]`
- [WSGR — EU AI Act enforcement phase begins](https://www.wsgrdataadvisor.com/2026/08/eu-ai-act-enforcement-phase-begins/) `[analysis]`

### Why it matters to you

- **Job lens:** The pre-deployment-eval / AI-assurance career lane the May Trump-EO thread kept pointing at **has actually arrived — just in Brussels, not Washington.** This is a legitimately open lane with no entrenched incumbents: **Commission AI Office** (public sector, policy-adjacent), **big-four assurance practices** (Deloitte / EY / KPMG / PwC — all building GPAI compliance teams right now), and **"compliance-as-code" startups**. Add `AI assurance`, `GPAI compliance`, and `model documentation (Article 53)` to your LinkedIn keywords tonight. The CSA note is the right length (~2000 words) to reference in a cover letter.
- **Startup lens:** The **€15M / 3%-of-turnover penalty** creates an immediate, non-optional buyer for **compliance infrastructure** — every GPAI provider serving EU customers now has to produce documentation on demand and show evaluation protocols on request. Two concrete wedges: (a) **model-documentation automation** (every doc the Commission can ask for, generated from your training logs); (b) **evaluation-protocol-as-a-service** (so you can hand the Commission a reproducible eval run). The TAM is every GPAI provider × every EU jurisdiction × every audit cycle. 18-month play.
- **Insight:** Watch the **first enforcement action**. The pattern in similar regulatory debuts (GDPR, DMA) is that the first case is deliberately *small enough to win*, chosen to establish precedent rather than maximize fine. Which provider gets picked first — a US frontier lab, a EU player (Mistral), or a Chinese open-weights distributor — tells you how the Commission is framing its mandate. Set a 60-day calendar reminder.

→ Cross-link: [`05` §1 hiring map](./05-career-and-startup.md#1-hiring) · [2026-05-22/01 §1 Trump EO postponed](../2026-05-22/01-big-lab-moves.md#1-eo-postponed).

---

## 6. Google Gemini 4 — in post-training, "before year-end" {#6-gemini-4}

**What happened:** At a late-September event, Google DeepMind head Koray Kavukcuoglu confirmed **Gemini 4 is in post-training** and that Google wants to ship **a first version before year-end 2026**, with iterative updates after that rather than waiting for a fully-polished release.

- No official date set. Some observers speculate October.
- No disclosed architecture, parameter count, context window, modality details, benchmarks, or pricing.
- Gemini 3.5 Pro reportedly delayed to accommodate the Gemini 4 timeline.

**Sources:**
- [InfoWorld — Google plans Gemini 4 release before year-end](https://www.infoworld.com/article/4226642/google-plans-gemini-4-release-before-year-end-2.html) `[secondary]`
- [LetsDataScience — Google DeepMind Nears Gemini 4 Release](https://letsdatascience.com/news/google-deepmind-nears-gemini-4-release-bee31f0a) `[secondary]`
- [MindStudio — Gemini 4 release date rumors](https://www.mindstudio.ai/blog/gemini-4-release-date-rumors/) `[rumor]`
- [TechNews.tw — Gemini 4 in post-training (Chinese)](https://technews.tw/?p=1620904) `[secondary]`

### Why it matters to you

- **Job lens:** Google is **the third slot** on every "which lab should I apply to" list right now — behind Anthropic (growth posture + IPO) and OpenAI (platform turn + 1.2B users). A Gemini 4 ship-before-year-end **doesn't change the slot order**, but it does open **Vertex-AI / Antigravity / Google Cloud Agent Platform** hiring once the model goes GA. Watch the Gemini 4 launch date; set your Google application window to +14 days after launch (that's when Vertex teams staff up on launch-adjacent work).
- **Startup lens:** The "release the first post-training version, iterate publicly" approach is **a release-pattern bet** — Google is betting that a less-polished model shipping fast beats a polished model shipping late. If this works for Google, every lab adopts it, and **the primary-source-tracking skill drops in value further** (the "latest model" is less latest than yesterday's). If it doesn't work (quality complaints, retraction, hallucination incident), it's a flag for the "release-cadence as risk" thread opened by the Sept 1–3 four-model week.
- **Insight:** Gemini 4 in post-training in late September + ship before year-end + Gemini 3.5 Pro delayed = **Google has effectively conceded the Q4 2026 model-quality race.** Opus 5.5 holds the Elo lead, GPT-6 Astra holds the Computer-Use lead, and Gemini 4 is the one that would unseat either — but not until Q1 2027. Factor this into your startup competitive map: for the next 90 days, "built on Gemini 4" is not a credible marketing line.

→ Cross-link: [`03` §1 Router update](./03-practical-skills-and-tools.md#1-router-update).

---

## 7. Nvidia + Hugging Face — $12.93B acquisition reported Sept 3 {#7-nvidia-hf}

**What happened:** Multiple outlets reported on **Sept 3, 2026** that NVIDIA announced an acquisition of **Hugging Face** at a sticker price of **~$12.93B**. (Several sources call it a "deal," which can also indicate a strategic investment / partnership — treat the specific transaction structure as unconfirmed pending the official NVIDIA / HF announcement text.) The reporting is thin but consistent on the figure.

**Sources:**
- [privsource — AI/ML Acquisitions in 2026](https://www.privsource.com/acquisitions/ai-machine-learning/2026) `[aggregator]`

### Why it matters to you

- **Job lens:** If the transaction is a **full acquisition**, Hugging Face becomes NVIDIA's open-source distribution arm — and **every HF team role gets reclassified as an NVIDIA role**, which likely means better pay bands + more enterprise exposure. If it's a **strategic investment**, less changes immediately, but NVIDIA GPU allocation to HF users (Spaces, Inference Endpoints) likely tilts favorably. Either way: HF roles become more interesting, not less.
- **Startup lens:** NVIDIA-controlled HF means **the open-weights distribution path has a single gatekeeper** for inference economics. If your startup depends on cheap long-tail open-weights serving (Runware thesis), you now have NVIDIA pricing power sitting upstream. Alternative stacks (Together, Replicate, Modal, Fireworks) matter more; multi-cloud / multi-provider abstraction matters more.
- **Insight:** Watch for the **antitrust angle**. NVIDIA + HF + the SpaceX/xAI Colossus deal + the ~$40B in NVIDIA equity bets through 2026 = a story the FTC and the European Commission will not ignore. If an antitrust review opens, the deal may become a **conditional close** with structural remedies, which would re-open the "neutral open-weights distribution" slot for a new startup.

→ Cross-link: [`02` §4 the open-weights infra thread](./02-new-emerging.md#4-open-weights-infra).

---

Thread continuity: this file's §1–§4 updates `WATCHLIST.md` under *Funding & Valuations* (OpenAI IPO path, Anthropic IPO path) and *Models & Capability* (Opus 5.5, Sonnet 5.5, GPT-6 family, Dots, Gemini 4). §5 updates *Policy & Geopolitics* (EU AI Act). §7 is a new row under *Compute & Infrastructure*.
