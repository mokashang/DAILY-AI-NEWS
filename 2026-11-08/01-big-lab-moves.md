# Big Lab Moves — 2026-11-08

The 24 hours between Nov 7 and this edition were mostly roadshow-eve housekeeping: no new Anthropic S-1 amendment filed on EDGAR as of Nov 6, investor-side valuation talk walking down from ~$2T to $1.2–1.3T, a fresh federal antitrust complaint (Nov 6) that the amended S-1 will have to acknowledge, Google's $17B Wyoming campus (Nov 5) hardening into the first US reference architecture for "gas-with-CCS as clean compute," and no new Gemini-4-variant announcement. The frame for the week: **the first frontier-lab roadshow begins tomorrow against a backdrop of (a) walked-down valuation, (b) material antitrust disclosure, (c) a lab-governance redaction visible in a METR report.** Each of the three is independently manageable; stacked, they will set the pricing anchor.

Tags: `#labs #anthropic #ipo #antitrust #google #datacenter #ccs`

---

## 1. Roadshow eve — Mon Nov 9 kickoff, pricing the following week, price range STILL unfiled, valuation range walked down ~40% in ~30 days {#1-roadshow-eve}

**Where we are (as of Nov 8 AM):**
- **IFR:** Anthropic plans to begin the IPO roadshow Monday Nov 9 and price the deal "the next week."
- **Bloomberg:** Possible roadshow start "week of Nov 9."
- **FinanceFeeds (Nov 6 EDGAR check):** No amended S-1 has filled in **share count, price range, or the underwriters' option to purchase additional shares.** The Nov 2 S-1/A filled in financials only.
- **Seeking Alpha:** Investor-side chatter now in a **$1.25–1.75T range**; raise target **$80–100B**.
- **Investor pushback (secondary reporting):** Four people familiar with the process reportedly question whether a Nov 9 start is realistic; some buyers have cited **$1.1T** as a floor.
- **Prediction market:** Kalshi "ANT prices before Dec 1" contract last reported ~**82¢**.
- **Underwriters:** Goldman Sachs + Morgan Stanley lead (confirmed in the Oct 26 public S-1).
- **Ticker:** ANT on Nasdaq.

**What is missing and matters most to watch:**
1. The **amended S-1 with price range and share count** (sometimes called the "red herring price" filing). Highest-variance event of the week; expect it within the next **24–48 hours** or the roadshow slips.
2. **Risk-factor updates** — specifically whether the **Nov 6 antitrust complaint** (see §2) is now referenced, and whether the **METR redaction** (see `04 §1`) is referenced in the governance / research-risk section.
3. **Insider-selling / lockup structure** — Amazon's stake (confirmed in the Oct 26 filing) is already a public comp for AMZN itself; watch for any pre-deal secondary.

**Sources:**
- [FinanceFeeds — Anthropic IPO roadshow looms with no price range in sight (Nov 6)](https://financefeeds.com/anthropic-ipo-roadshow-looms-with-no-price-range/) `[secondary]`
- [FourWeekMBA — Anthropic Said to Start IPO Roadshow Next Week; No Price Yet](https://fourweekmba.com/ai-anthropic-said-to-start-ipo-roadshow-next-week-no-price-yet/) `[aggregator]`
- [Leverage Shares — Anthropic IPO Tracker (date, valuation, S-1 status)](https://leverageshares.com/us/anthropic-ipo-tracker/) `[analysis]`
- [Seeking Alpha — Wall Street Brunch: Anthropic IPO Goes On The Road (ANT)](https://seekingalpha.com/article/4964841-wall-street-brunch-anthropic-ipo-goes-on-the-road) `[analysis]`
- [Motley Fool — Anthropic's IPO Could Come Within Weeks (Nov 7)](https://www.fool.com/investing/2026/11/07/anthropic-s-ipo-could-come-within-weeks-amazon-already-owns-a-piece-of-it/) `[secondary]`
- [BigGo Finance — Anthropic IPO Hits Headwinds: Investors Question $2 Trillion Valuation](https://finance.biggo.com/news/a6711738-b7dd-4df0-a209-2bbf48ac0189) `[aggregator]`
- [SEC EDGAR — Anthropic, PBC Form S-1 FY2026](https://www.sec.gov/Archives/edgar/data/0002130357/000162828026067168/exhibit45-sx1.htm) `[primary]`

### Why it matters to you

- **Job lens:** The specific interview-prep delta is **the "ANT day-one trading thesis."** Every FDE / Solutions / Policy recruiter at Anthropic this week is personally refreshing EDGAR every 2 hours; walking into a Monday interview *without* an opinion on "what the amended S-1 price range should look like, and why" is a tell. Your 2-paragraph thesis: (a) pick a price band, (b) justify from **H1 2026 revenue ($16.3B), run-rate burn (strip the non-cash GPU-contract remeasurement from the $80.7B loss), NRR (~900% from the Oct 29 edition), and the antitrust disclosure**; (c) say which of the three Monday events (S-1 amendment / antitrust response / METR commentary) is the biggest risk, and why. Draft it tonight. Full prompt sketch: [`05` §4](./05-career-and-startup.md#4-ant-interview-thesis).
- **Startup lens:** The biggest structural read is that the walk-down from $2T to $1.2T is almost entirely *demand-side* (investor pushback), not *supply-side* (business-model deterioration). The lab's P&L is unchanged from Oct 29. **What this tells founders:** even when the underlying business is arguably the fastest-compounding ARR curve in SaaS history, the public market will underwrite a frontier AI lab at roughly **40% below the last private-market mark** before it opens a position. Your fundraising decks should assume a comparable public-vs-private discount when you forecast exit multiples.
- **Insight:** The single cleanest **reflexivity signal** in the week is between the **amended S-1 price range (not yet filed)** and the **antitrust complaint (filed Nov 6)**. If the amended S-1 drops Mon AM with a price range *above* $1.3T and discloses the complaint as "not material," that's a lab-and-underwriter statement that Sherman §1 on "safety coordination" is not a legally plausible theory. If the complaint moves to a prominent risk factor instead, the band will land in the $1.1–$1.2T zone. Watch the band first, the complaint-disclosure language second — those together reveal Goldman + Morgan Stanley's internal house view on this suit's survivability.

→ Cross-link: [2026-11-07/01 §1 Anthropic S-1 (Oct 26)](../2026-11-07/01-big-lab-moves.md) · [`04` §1 METR redaction](./04-research-progress.md#1-metr) · [`05` §4 ANT interview thesis](./05-career-and-startup.md#4-ant-interview-thesis).

---

## 2. Antitrust lawsuit filed Nov 6 — four consumer plaintiffs vs. Anthropic + OpenAI + SpaceXAI + Google, Sherman §1, NDCA {#2-antitrust}

**What happened (2026-11-06):** Four consumer plaintiffs filed a federal antitrust complaint in the **U.S. District Court for the Northern District of California** against **Anthropic, OpenAI, SpaceXAI, and Google**, alleging a violation of **Section 1 of the Sherman Antitrust Act** — i.e., an unlawful horizontal agreement to **slow AI development** under the banner of "industry-wide coordination."

**Core theory (as described in Bloomberg Law / CBS / PBS / ABC / Hill coverage):**
- Anchor: **Dario Amodei's "industry-wide coordination" essay** (Anthropic CEO) calling for cross-lab pacing on frontier capability releases.
- Endorsements cited in the complaint: **Elon Musk (xAI/SpaceXAI), Sam Altman (OpenAI), Demis Hassabis (Google DeepMind)** are each quoted as agreeing with the call.
- Plaintiffs: four consumers; plan to seek **class certification, injunctive relief, declaratory judgment.**
- Lead attorney Nick Rowley reportedly argues AI safeguards should be set by **government**, not by private agreements among competitors.

**Lab responses captured so far:**
- **Altman (OpenAI):** OpenAI "does not believe it needs to wait for an antitrust exemption or legislation" to proceed with its work.
- **Anthropic / Google / SpaceXAI:** no on-record response in the coverage I captured as of Nov 8 AM.
- **Senate:** **Senator Josh Hawley** has publicly stated he would not grant the companies an antitrust exemption; Amodei's essay reportedly floated such a waiver as a path.

**Sources:**
- [Bloomberg Law — OpenAI, Anthropic, Google, SpaceXAI Hit With Antitrust Lawsuit](https://news.bloomberglaw.com/litigation/openai-anthropic-google-spacexai-hit-with-antitrust-lawsuit) `[primary]`
- [Yahoo Finance — Anthropic, OpenAI, Google, SpaceXAI Accused of Collusion](https://finance.yahoo.com/technology/ai/articles/anthropic-openai-google-spacexai-accused-141632331.html) `[aggregator]`
- [CBS News — Lawsuit says Anthropic, OpenAI, SpaceXAI and Google made illegal deal on AI slowdown](https://www.cbsnews.com/news/ai-slowdown-lawsuit-openai-anthropic-google/) `[secondary]`
- [PBS NewsHour — Lawsuit says Anthropic, OpenAI, SpaceXAI and Google made illegal agreement on AI slowdown](https://www.pbs.org/newshour/nation/lawsuit-says-anthropic-openai-spacexai-and-google-made-illegal-agreement-on-ai-slowdown) `[secondary]`
- [The Hill — Lawsuit accuses Anthropic, OpenAI, SpaceXAI, Google of AI pacing 'collusion'](https://thehill.com/policy/technology/6099571-lawsuit-accuses-anthropic-openai-spacexai-google-of-ai-pacing-collusion/) `[secondary]`
- [NewsNation — Lawsuit accuses Anthropic, OpenAI, SpaceXAI, Google of AI pacing 'collusion'](https://www.newsnationnow.com/business/tech/ai/lawsuit-anthropic-openai-spacexai-google-ai-pacing-collusion/) `[secondary]`
- [Open The Magazine — US Antitrust Lawsuit Targets Anthropic, OpenAI, Google, Elon Musk Over Alleged AI Safety Collusion](https://openthemagazine.com/technology/ai-safety-or-collusion-anthropic-openai-google-face-us-antitrust-lawsuit) `[aggregator]`

### Why it matters to you

- **Job lens:** **AI-policy and T&S legal-counsel adjacent roles just got concrete.** The complaint cites Amodei's essay — a written artifact — as the horizontal-agreement anchor. Every lab's Policy, Communications, and Trust & Safety teams will spend the next two quarters building what "public coordination without Sherman §1 exposure" looks like as a workflow: who can publish what essay, what language avoids "we have agreed to…," what disclosure templates work for Congressional testimony. If you have any humanities / philosophy / law background, this is the single clearest hiring pulse of Q4; watch Anthropic Policy + OpenAI Global Affairs + Google Policy for new reqs within 30 days.
- **Startup lens:** A narrow but real wedge is **"antitrust-safe safety-coordination tooling"** — a hosted service that labs can use to publish capability-pause commitments through a legally-safe mediation layer (independent nonprofit, government-adjacent, or a court-tested voluntary-disclosure template). Market: ~5 potential customers (the frontier labs). Comp parallel: **Trusted Information Sharing Analysis Centers (ISACs)** in cyber — small market, high per-customer ACV, meaningful policy moat. If your founder-fit profile is law-adjacent engineering, this is the pitch-this-month wedge.
- **Insight:** The legal theory itself is **novel but not fringe** — Sherman §1 has reached farther than this complaint goes (see the publishing-consortium and LIBOR cases) — and the fact that it reached a docket 48 hours before an IPO roadshow is a timing note, not a coincidence. The **forum-shopping read** (NDCA is one of the most plaintiff-friendly federal courts for tech antitrust, from the Epic-Apple pattern) makes this a credible-enough theory to extract settlement pressure, even if the merits lose on summary judgment. **Every founder pitching a safety-first wedge now needs to be able to answer "what's your coordination-theory risk?" on the first VC call.**

→ Cross-link: [`01` §1 roadshow eve](./01-big-lab-moves.md#1-roadshow-eve) · [2026-10-14/01 §6 Anthropic Usage Policy update](../2026-10-14/01-big-lab-moves.md#6-usage-policy).

---

## 3. (reserved) {#3-reserved}

*No new big-lab move landed in the 24h cycle that isn't already covered under §1–2 or §4; the Nov 8 slot that would normally host a third lab story is intentionally empty so the reader's time budget rolls into [`04` §1 METR](./04-research-progress.md#1-metr).*

---

## 4. Google announces $17B Wyoming AI data center with a 702MW fuel-cell + CCS reference architecture (Nov 5) {#4-wyoming}

**What happened (2026-11-05):** Google announced a **$17B data center in Laramie County, Wyoming** — its **first in the state** — with a power stack unlike any prior lab-scale US build:

- **702MW commercial-scale fuel-cell development with carbon capture and storage**, contracted with **AEP**. Google calls it "the largest planned development of its kind to date."
- **Fuel cells manufactured in-US by Bloom Energy.**
- **20-year power-purchase agreement**; **full operations by end-2028** (per POWER Magazine / TNW).
- **Captured carbon stored underground at Tallgrass Energy's Eastern Wyoming Sequestration Hub.**
- Additional natural-gas supply from **Tallgrass + Black Hills Energy**; CCS retrofits of Tallgrass turbines under study.
- **Related Digital** is the named campus developer partner.
- **Google pays 100% of the data center's power use** and covers infrastructure needs directly driven by its growth.

**What's not disclosed in Google's blog:** total MW of the campus itself (vs. the 702MW fuel-cell line), construction timeline, in-service milestones, and whether the $17B includes AEP / Bloom / Tallgrass / Black Hills spend.

**Sources:**
- [Google Blog — Investing in Wyoming's infrastructure, energy and workforce](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/wyoming-data-center/) `[primary]`
- [TNW — Google's first Wyoming data centre will run on gas with carbon capture](https://thenextweb.com/news/google-wyoming-data-centre-17b-fuel-cells-carbon-capture) `[secondary]`
- [FourWeekMBA — Google Confirms $17B Wyoming Data Center, Pays 100% of Power](https://fourweekmba.com/ai-google-confirms-17b-wyoming-data-center-pays-100-of-power/) `[aggregator]`
- [Roic.ai — Google's $17B Wyoming data center bets on gas + carbon capture (11-05-2026)](https://www.roic.ai/news/googles-17-billion-wyoming-data-center-bets-on-gas-carbon-capture-11-05-2026) `[analysis]`
- [AI Weekly — Google backs $17B Wyoming data center with 702MW fuel-cell CCS](https://aiweekly.co/alerts/google-backs-17b-wyoming-data-center-with-702mw-fuel-cell-ccs) `[aggregator]`

### Why it matters to you

- **Job lens:** This creates **5 new counterparty hiring surfaces** for AI-adjacent infrastructure roles that largely didn't exist 6 months ago as discrete pipelines: **Bloom Energy (fuel-cell manufacturing + grid integration), Related Digital (campus developer + ops), AEP (utility-side AI load engineering), Tallgrass Energy (CCS pipeline + sequestration), Black Hills Energy (regulated utility + AI-load dispatch).** Deep lane: "AI-infrastructure Solutions Engineer" roles at any of these are **significantly less contested** than the Anthropic/OpenAI FDE funnel, pay competitively ($180–240K base per levels.fyi / fullstack market data), and build a résumé that's valued on both the lab side and the hyperscaler side. If your fallback is "I can't break into the top FDE funnel this cycle," this is the lane to add. Full plan: [`05` §2](./05-career-and-startup.md#2-infra-lane).
- **Startup lens:** Three wedges open the day a hyperscaler publishes a reference-grade "gas-with-CCS as clean compute" architecture:
  - **(a) PPA-structuring-as-a-service** for mid-size enterprise AI builds (sub-100MW) — templating what Google / AEP / Related Digital did at 702MW so a mid-market build can replicate it on $100M of capex rather than $17B.
  - **(b) Sequestration-as-a-service accounting** — the regulatory + accounting workflow for carbon-captured from a datacenter-owned fuel-cell to a third-party sequestration hub is underspecified for the mid-market. Build the ledger.
  - **(c) Fuel-cell-ops dispatch software** — matching load to fuel-cell output at scale is still largely a utility-engineer job; a software product that automates the dispatch envelope for a 50–700MW fuel-cell farm is niche but credible.
- **Insight:** The strategic read is that Google has **moved first on "gas + CCS as the LPAC** (Lowest Publicly Acceptable Carbon) **compute pattern"** — ahead of nuclear (still regulatory-blocked for new builds under 2030), ahead of long-duration-storage renewables (still not bankable at 1GW scale), ahead of Microsoft's Three Mile Island restart (one-off). The pattern will be copied because the alternatives aren't deployable on frontier-lab timelines. **Watch for OpenAI / Meta / Anthropic to announce a similar structure within 180 days; the Nov 5 blog is the template.**

→ Cross-link: [2026-05-21/01 SpaceX Colossus contract](../2026-05-21/01-big-lab-moves.md) · [`05` §2 infra lane](./05-career-and-startup.md#2-infra-lane).
