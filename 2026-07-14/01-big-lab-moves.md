# Big Lab Moves — 2026-07-14

Three moves that are actually one story: **Anthropic is diversifying its silicon (Samsung), pricing itself for the public markets (IPO paperwork filed at ~$965B on ~$47B ARR), and — as of Friday — OpenAI is being sued by Apple over the hardware it needs to matter in consumer.** The May-22 frame ("the regulator paused, the bankers stepped up, the talent voted with its feet") sharpened this month into: **the frontier is reorganizing its dependencies — on foundries, on the public markets, and on a device story.** Anthropic is winning the reorganization; OpenAI just got a legal drag on its.

Tags: `#labs #anthropic #openai #apple #samsung #chips #ipo #hardware #litigation`

---

## 1. Anthropic × Samsung — preliminary talks on a custom 2nm chip {#1-anthropic-samsung}

**What happened:** Anthropic entered **preliminary, exploratory** discussions with **Samsung Electronics** to manufacture a **custom AI chip** on Samsung Foundry's **2-nanometer process (SF2)** with advanced packaging. Reported first by *The Information* (July 2), quickly corroborated across CNBC, Bloomberg, TechCrunch, TrendForce, and Korean-market outlets.

- **What SF2 buys you:** Samsung's 2nm node uses **Gate-All-Around (GAA) nanosheet transistors**, an architectural jump from the FinFET generation — the same class of node TSMC is qualifying for Apple/Nvidia. GAA improves performance-per-watt and leakage vs. FinFET; the *packaging* piece (2.5D / advanced) matters as much as the node for AI accelerators.
- **What's undecided:** what the chip will be optimized for, how powerful it will be, or how it slots into a server rack. This is a **scoping conversation**, not a tape-out.
- **Anthropic's official framing:** AWS Trainium, Google TPUs, and Nvidia GPUs remain **central** to compute strategy — a custom chip would **add a layer** to the stack, not replace one.
- **The hire that tells you it's serious:** **Clive Chan**, formerly on **OpenAI's chip design team**, joined Anthropic to build internal hardware expertise. You don't hire that person for a rumor.

**Sources:**
- [Bloomberg — Anthropic in Talks With Samsung for Custom AI Chip](https://www.bloomberg.com/news/articles/2026-07-02/anthropic-in-talks-with-samsung-for-custom-ai-chip-information-mr3l34t4) `[secondary]`
- [TechCrunch — Anthropic is discussing a new custom chip with Samsung](https://techcrunch.com/2026/07/02/anthropic-is-discussing-a-new-custom-chip-with-samsung/) `[secondary]`
- [TrendForce — Anthropic reportedly eyes custom AI chip; in talks with Samsung for 2nm foundry and advanced packaging](https://www.trendforce.com/news/2026/07/03/news-anthropic-reportedly-eyes-custom-ai-chip-in-talks-with-samsung-for-2nm-foundry-and-advanced-packaging/) `[analysis]`
- [TheStreet — Anthropic quietly joins the race to build its own chips](https://www.thestreet.com/technology/anthropic-samsung-custom-chip-talks) `[secondary]`
- [Korea JoongAng Daily — Anthropic weighing Samsung partnership](https://www.koreajoongangdaily.com/business/anthropic-weighing-samsung-partnership-to-develop-custom-ai-chips-us-media/12754518) `[secondary]`
- [UPI — Anthropic eyes South Korea's Samsung for custom AI chip](https://www.upi.com/Top_News/World-News/2026/07/03/Anthropic-Samsung-Electronics/7811783128641/) `[secondary]`

### Why it matters to you

- **Job lens:** *Silicon* is now an explicit Anthropic hiring lane, and it's a scarce one — **hardware-adjacent MLE / systems / kernel-engineering** roles at frontier labs pay a premium precisely because the talent pool is thin. If you have any low-level, kernel, compiler, HBM/interconnect, or systems background — even coursework — get an application in *now* (the Clive Chan hire is a leading indicator, not a lagging one). For the non-hardware track, the story tells you Anthropic is *deepening its stack* — meaning platform/infra/tooling roles have more scope over the next 24 months.
- **Startup lens:** The frontier is building a **portfolio of compute suppliers**, not a monopoly. Nvidia is no longer the only game — **AWS Trainium, Google TPUs, Anthropic-custom-on-Samsung, Meta MTIA** are converging. The startup implication: **compiler / kernel / cross-backend performance-portability** (make one model run efficiently across five silicon backends) is a real wedge — same shape as *the* MLIR / OpenXLA story, but now with real enterprise buyers. Score any wedges you have against "does the four-way silicon fragmentation help or hurt me?"
- **Insight:** Read this **paired with §2**: a lab about to go public *always* diversifies its supply chain first (analysts and short-sellers hate single-vendor risk on your top-line COGS). The Samsung talks aren't a chip story, they're an *IPO-prep* story. The same logic will drive more announcements — SK Hynix HBM deals, alternate cloud commitments, foundry pre-payments — before the roadshow.

→ Cross-link: [§2 Anthropic IPO filed](#2-anthropic-ipo) · [2026-05-21/01 §2 Colossus contractual burn](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus).

---

## 2. Anthropic files IPO paperwork at ~$965B on ~$47B ARR — passes OpenAI on both {#2-anthropic-ipo}

**What happened:** **Anthropic confidentially submitted draft IPO paperwork** at a target valuation of **~$965B**, on the back of a **~$47B annualized revenue run-rate** (up from ~$30B earlier in 2026 and ~$10B in 2025). The May-22 thread ("Anthropic eyeing October") is now a **filed** document, not a rumor — and both the valuation and the revenue number now **exceed OpenAI's** ($852B March round; run-rate roughly in the mid-$30Bs). GPT-5.6's July 9 GA is OpenAI's counter-punch on the product side, but the *financial* leadership crossed this quarter.

Concrete pieces:
- **Revenue trajectory (Anthropic):** ~$10B (2025 year-end) → ~$30B (Q1 2026) → **~$47B ARR (May–June 2026)**. Growth is driven by **Claude Code + enterprise adoption**, with Anthropic's May "first profitable quarter" narrative ([2026-05-21/01 §2](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus)) as the underwriter's headline.
- **IPO structure:** confidential S-1 (draft registration), enabling private iteration with the SEC and financials released ~15 days before roadshow. **Anthropic is now on a track to print *ahead of* OpenAI's Sept target.**
- **OpenAI counter-punch:** **GPT-5.6 (Sol / Terra / Luna) GA on July 9** — Sol $5/$30, Terra $2.50/$15, Luna $1/$6 per 1M tokens; new **explicit prompt-cache breakpoints + 30-min minimum cache life**; **UK AISI reports universal jailbreaks in Sol's cyber safeguards**, which is the safety story to watch.

**Sources:**
- [Fortune — Anthropic confidentially files for IPO after raising at $965B valuation](https://fortune.com/2026/06/01/anthropic-confidentially-files-ipo-965-billion-valuation/) `[secondary]`
- [CNBC — Anthropic tops OpenAI as most valuable AI startup, nears $1T valuation](https://www.cnbc.com/2026/05/28/anthropic-open-ai-startup-value.html) `[secondary]`
- [Futurum Group — Anthropic Files For IPO, Looking to Beat OpenAI to the Punch](https://futurumgroup.com/insights/anthropic-files-for-ipo-looking-to-beat-openai-to-the-punch/) `[analysis]`
- [CNBC (Tech Download) — Anthropic's IPO sets up first big test of AI boom valuations](https://www.cnbc.com/2026/06/05/tech-download-anthropic-ipo-ai-valuations.html) `[analysis]`
- [OpenAI — Previewing GPT-5.6 Sol](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [Simon Willison — The new GPT-5.6 family: Luna, Terra, Sol](https://simonwillison.net/2026/Jul/9/gpt-5-6/) `[analysis]`
- [VentureBeat — OpenAI unveils GPT-5.6 Sol, Terra, Luna, but only accessible to limited preview partners](https://venturebeat.com/technology/openai-unveils-gpt-5-6-sol-terra-and-luna-models-but-only-accessible-to-limited-preview-partners-for-now-per-us-gov) `[secondary]`
- [Forbes Investor Hub — OpenAI vs Anthropic IPO comparison](https://www.forbes.com/sites/investor-hub/article/openai-vs-anthropic-ipo-comparison/) `[analysis]`

### Why it matters to you

- **Job lens:** The **filed** IPO is the strongest possible ratification of your ME.md focusing decision. Two concrete moves: (1) When Anthropic's S-1 goes public (~15 days pre-roadshow), **read the revenue-mix disclosure as an internal org chart** — the fastest-growing segment (Claude Code? Enterprise API? Solutions/FDE?) tells you where the headcount will be added next. (2) Anthropic offers under an *approaching-IPO* comp structure have a **defined liquidity path**: RSUs are about to become priceable, not paper. Update your offer-comparison spreadsheet accordingly.
- **Startup lens:** A public Anthropic (probably first) and public OpenAI (soon after) reprices the *entire* AI startup market. Expect (a) a **secondary-market unlock** for pre-IPO shares at both companies → next founder wave; (b) **quarterly monetization pressure** on both platforms → more pricing changes and packaging shifts (Anthropic's June-15 Agent SDK metering was a preview); (c) **buy-side coverage** finally producing legitimate revenue-segment analysis → your competitive intel gets much better, cheaply.
- **Insight:** The interesting question isn't "who prints first?" — it's **which one Wall Street *treats* as the primary "buy AI" ticker.** Historically first-mover doesn't win that (see Facebook vs LinkedIn, Snowflake vs Cloudera). Anthropic will argue *revenue leadership + margin*; OpenAI will argue *consumer distribution + brand + optionality on the device*. Watch the sell-side notes when both are public — the framing sets the sector's multiple for years.

→ Cross-link: [§1 Anthropic Samsung chip](#1-anthropic-samsung) · [§3 Apple v. OpenAI](#3-apple-openai) · [2026-05-22/01 §2 OpenAI S-1 filing](../2026-05-22/01-big-lab-moves.md#2-openai-s1).

---

## 3. Apple sues OpenAI for trade-secret theft over the coming AI device (July 10) {#3-apple-openai}

**What happened:** On **Friday, July 10, 2026**, **Apple filed suit against OpenAI in the U.S. District Court for the Northern District of California**, alleging **trade-secret misappropriation and breach of contract** in the development of OpenAI's coming Jony-Ive-designed AI hardware device.

- **Named defendants (personnel):** **Chang Liu**, former Apple engineer now at OpenAI — accused of **"accessing and downloading dozens of Apple's confidential hardware-related files"** including unreleased-product info, engineering presentations, technical specs, and proprietary project data. **Tang Tan**, OpenAI's hardware chief and former iPhone/Apple-Watch product design lead — accused of **using Apple confidential info while recruiting**, of instructing candidates to **bring Apple parts to interviews**, and of **coaching Apple employees on how to leave the company**.
- **The scheme framing:** Apple's complaint says the misappropriation was **"at every level"** — not one bad actor, but a systematic personnel + information transfer.
- **OpenAI response (Drew Pusateri, spokesperson):** *"We have no interest in other companies' trade secrets. We remain focused on building innovative technology that empowers people everywhere."*
- **What's on the line:** The **Jony Ive-designed device** — expected to unveil later this year — is OpenAI's answer to Apple in consumer AI. And per Bloomberg's read of the docket, the suit could **complicate OpenAI's coming IPO**, both by extending the disclosure risk window and by putting device-strategy details on the litigation record.

**Sources:**
- [CNN Business — Apple accuses OpenAI of using stolen trade secrets to create its upcoming AI gadgets](https://www.cnn.com/2026/07/10/tech/apple-openai-devices-lawsuit) `[secondary]`
- [Bloomberg — Apple Sues OpenAI for Trade Secret Theft Over AI Hardware Designs](https://www.bloomberg.com/news/articles/2026-07-10/apple-sues-openai-for-trade-secret-theft-in-blockbuster-case) `[secondary]`
- [Bloomberg — How Apple's Lawsuit Threatens to Disrupt OpenAI's Bid to Rival the iPhone](https://www.bloomberg.com/news/articles/2026-07-13/how-apple-s-lawsuit-threatens-to-disrupt-openai-s-bid-to-rival-the-iphone) `[analysis]`
- [Washington Post — Apple sues OpenAI, alleging the AI company stole trade secrets](https://www.washingtonpost.com/technology/2026/07/10/apple-sues-openai-alleging-ai-company-stole-trade-secrets/) `[secondary]`
- [Axios — Apple sues OpenAI for trade secret theft](https://www.axios.com/2026/07/10/apple-sues-openai-trade-secret-theft) `[secondary]`
- [CNBC — Apple sues OpenAI alleging trade secret theft, says scheme was 'at every level'](https://www.cnbc.com/2026/07/10/apple-openai-lawsuit-trade-secrets.html) `[secondary]`
- [TechCrunch — Apple sues OpenAI over alleged trade secret theft](https://techcrunch.com/2026/07/10/apple-sues-openai-over-alleged-trade-secret-theft/) `[secondary]`

### Why it matters to you

- **Job lens:** Two hiring signals. **(1) OpenAI hardware is now under discovery** — hiring won't stop but the pace of the device group may. If OpenAI hardware is on your target list, put it *later* in the outreach queue this quarter and prioritize *software / FDE / Deployment Company* first ([`02` §1](./02-new-emerging.md#1-msft-frontier)). **(2) The rest of AI hardware just went "up for grabs"** — Anthropic (§1), Google/DeepMind, and Meta will read this as a moment to poach the exact people the suit names. If you have hardware ambitions, note the *volume* of the market for those skills is higher this week, not lower.
- **Startup lens:** The **"AI wearable / AI hardware"** category is more legally contested than it looked in 2025. Any founder in this space needs (a) **clean-room engineering hygiene** — documented provenance for schematics, firmware, and packaging know-how; (b) **hiring hygiene** — clear "you may not bring or reference prior employer materials" onboarding, with sign-off; (c) **cap-table hygiene** — Apple's suit will make LPs skittish about founders with recent Big Tech tenure in the same product area, so document your differentiation up front. This is a *category-shaping* case, not just a two-party one.
- **Insight:** The suit is really about **who owns the design language of the "post-phone" era.** Apple is preemptively defending the *category* — glass slabs, wearables, ambient devices — before OpenAI can define an alternative aesthetic and hardware stack. The court fight is a proxy for a **platform war**: whoever ships the consumer AI device with mindshare gets the next decade of application distribution. Discount everything you read about the technical merits and read the litigation as **market positioning by other means**.

→ Cross-link: [§2 Anthropic IPO](#2-anthropic-ipo) (OpenAI's counter-timing pressure) · [2026-05-07/01 Apple iOS 27 multi-AI Extensions](../2026-05-07/01-big-lab-moves.md).
