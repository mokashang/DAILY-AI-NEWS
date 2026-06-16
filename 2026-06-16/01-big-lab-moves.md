# Big Lab Moves — 2026-06-16

A 25-day re-baseline. The metering deadline this archive has tracked since May 16 went live yesterday — **the Anthropic Agent SDK now meters at full API list rate against a separate credit pool**, and on the same morning the **original Claude 4 Sonnet/Opus models retired from the API**. In the background, **both frontier labs are now S-1-confidential** (Anthropic June 1 at ~$965B → $1.75–1.8T target; OpenAI June 8 at ~$852B → $1T+ Sept window) and **Anthropic shipped its first public Mythos-class model — Fable 5** — at Code w/ Claude Tokyo (June 9–10), GA on all three hyperscalers day-one. **Apple, in Tim Cook's last keynote as CEO**, opened iOS 27 to a **third-party AI Extensions marketplace** (Claude / Gemini / ChatGPT / Grok as default Siri). The state-vs-market dynamic from [2026-05-22](../2026-05-22/01-big-lab-moves.md) settled into the same answer as before: **the market is setting the velocity, and the velocity is rising.**

Tags: `#labs #anthropic #openai #apple #google #pricing #agent-sdk #ipo #public-markets #fable-5 #mythos #ios27 #extensions`

---

## 1. Anthropic Agent SDK metering goes live — Day 1 {#1-metering-day-1}

**What happened:** As of **00:00 UTC June 15, 2026** (yesterday), Anthropic split agentic workloads onto a separate metered credit pool. This was the deadline tracked since [2026-05-16/01](../2026-05-16/01-big-lab-moves.md#1-meter) and refined through [2026-05-18/03 (manual toggle warning)](../2026-05-18/03-practical-skills-and-tools.md#1-agent-sdk-toggle).

- **Scope:** Claude Agent SDK · `claude -p` headless CLI · Claude Code GitHub Actions · third-party agents (Zed, Cursor, Cline, Aider, …) authenticating with Claude subscription credentials.
- **Credit pool:** **$20 / $100 / $200 monthly credit** on Pro / Max-5x / Max-20x respectively, **billed at full Claude API list rates**, **no rollover**, no overage subscription (overage goes to the API account at list rate).
- **What stayed on subscription:** **Interactive Claude Code TUI** in the terminal + **claude.ai web/desktop chat**. These continue to draw from the existing subscription pool unchanged.
- **Same-morning second hit:** **The original Claude 4 model IDs retired from the API** — specifically `claude-sonnet-4-20250514` and `claude-opus-4-20250514`. Any production system that pinned these IDs broke silently at the same UTC midnight.
- **Effective price impact:** for the highest-volume programmatic users, **~12×–175× effective price increase** by workload type per the canonical reference; light/interactive users essentially unaffected.

**Sources:**
- [DEV Community — Your Claude automation starts metering today (June 15)](https://dev.to/aws-builders/your-claude-automation-starts-metering-today-june-15-a-quick-checklist-to-avoid-surprise-charges-3c3k) `[secondary]`
- [Codersera — Anthropic's June 15 Billing Change: What Every Claude Code & Agent SDK User Must Do](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/) `[secondary]`
- [DigitalApplied — Claude Credit Overhaul 2026: What Changes on June 15](https://www.digitalapplied.com/blog/anthropic-claude-credit-overhaul-june-15-2026) `[secondary]`
- [UsageBox — Anthropic's June 15 Double Hit: Agent SDK Leaves Your Subscription, Claude 4 Retires](https://usagebox.com/articles/anthropic-june-15-agent-sdk-credit-split-claude-4-retirement) `[analysis]`
- [Enterprise DNA — Two Claude Deadlines Hit June 15](https://enterprisedna.co/resources/news/anthropic-claude-june-15-retirements-billing-2026/) `[analysis]`
- [Make Help Center — Anthropic Claude model deprecations on June 15, 2026](https://help.make.com/anthropic-claude-model-deprecations-on-june-15-2026) `[primary-adjacent]`
- [Canonical reference gist — May 13, 2026 Agent SDK $200 credit policy change](https://gist.github.com/MagnaCapax/d9177e35b355853f03c730dfcaa693ef) `[analysis]`
- [DevToolPicks — Anthropic Splits Claude Subscriptions: What Changes for Indie Hackers on June 15](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026) `[secondary]`

### Why it matters to you

- **Job lens:** This is the moment the **"AI Integration Engineer / Solutions / FDE"** lane stops being theoretical and becomes a budget-line conversation in every Anthropic customer. The interview prompt that lands tomorrow is some version of *"a customer is panicking because their Claude bill 5×'d overnight; what do you triage first?"* You should be able to answer that in 90 seconds with the meter-aware starter ([`03` §1](./03-practical-skills-and-tools.md#1-meter-aware-starter)) — prompt caching, model routing (Opus orchestrator / Sonnet worker), per-step trace cost, model-ID audit (the retirement caught real prod systems silently). Ship the "what I changed June 15" LinkedIn post (see [`00` "One thing to DO"](./00-tldr.md)) — that's the artifact.
- **Startup lens:** The metering shock prices a *category* — **cost-routing / model-routing / agent-budget guardrails** is now a hair-on-fire pain for every team running programmatic Claude, which (per [2026-05-14/01](../2026-05-14/01-big-lab-moves.md)) is now the #1 US business-adopted lab. The thinnest wedge is **a 1-week-installable per-step cost router** that takes your three-provider keys and a budget envelope and **routes by cost-per-task-class**. The 2026-05-22 dual-model sanitiser reframed around cost + real-tool verification is one quarter of the same wedge.
- **Insight:** Read the structure, not the price. **"Programmatic agent compute is separately metered"** is now the canonical posture of the most-adopted lab in the US; OpenAI's separately-priced agent surfaces (Operator, ChatGPT Agent) point at the same equilibrium. **The flat-rate-subscription / unlimited-agent era ended yesterday.** Your professional value going forward is denominated less in "I built an agent" and more in **"I built an agent that knows what it cost."** Make the trace-cost a first-class artifact in every project you ship from now on.

→ Cross-link: [`03` §1 meter-aware starter](./03-practical-skills-and-tools.md#1-meter-aware-starter) · [2026-05-16 metering announcement origin](../2026-05-16/01-big-lab-moves.md#1-meter) · [2026-05-18 manual-toggle warning](../2026-05-18/03-practical-skills-and-tools.md#1-agent-sdk-toggle).

---

## 2. Both Anthropic and OpenAI filed confidential S-1s — the frontier is going public in parallel {#2-both-s1}

**What happened:** Inside three weeks, **both labs have draft registration statements at the SEC** — the first time in the history of the modern AI cycle that both frontier labs have an S-1 confidential at the same time.

- **Anthropic, June 1, 2026:** confidential S-1 filed. Backed by a recent **Series H closed at ~$965B post**, ARR trajectory through **~$47B annualized**; reporting names a **$1.75–1.8T listing valuation** target and **up to $75B raise** — which would be the **largest IPO in history**.
- **OpenAI, June 8, 2026:** confidential S-1 confirmed. Underwriters **Goldman Sachs + Morgan Stanley + JPMorgan**. Last private mark **~$852B** (March 2026 round); listing window **as early as September 2026**, with analysts at CNBC and Enterprise DNA expecting **>$1T at IPO**. OpenAI explicitly said it "hasn't decided on timing" and a listing "may be a while" — read this as confidentiality discipline, not signal of delay.
- **Order is the story:** Anthropic moved **first**. Given Anthropic's lead in US business adoption ([2026-05-14/01](../2026-05-14/01-big-lab-moves.md)) and projected first profitable quarter ([2026-05-21/01 §2](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus)), this isn't a coincidence — **profitability + adoption lead means Anthropic is the harder comp** for OpenAI's roadshow.

**Sources:**
- [TechCrunch — Anthropic files to go public](https://techcrunch.com/2026/06/01/anthropic-files-to-go-public/) `[secondary]`
- [Fortune — Anthropic confidentially files for IPO after raising $65 billion at $965 billion valuation](https://fortune.com/2026/06/01/anthropic-confidentially-files-ipo-965-billion-valuation/) `[secondary]`
- [Yahoo Finance — Anthropic Files Confidential S-1: Joins $3 Trillion AI IPO Race](https://finance.yahoo.com/markets/stocks/articles/anthropic-files-confidential-1-joins-161008569.html) `[secondary]`
- [Enterprise DNA — Anthropic Files Confidential S-1 for Near-$1 Trillion IPO](https://enterprisedna.co/resources/news/anthropic-s1-ipo-filing-june-2026/) `[analysis]`
- [TechStackIPO — Anthropic IPO 2026: $965B Valuation, S-1 Filed June 1 — Full Investor Guide](https://www.techstackipo.com/ipo/anthropic) `[analysis]`
- [AI Weekly — OpenAI Files Confidential IPO Targeting $850B Valuation](https://aiweekly.co/alerts/openai-files-confidential-ipo-targeting-850b-valuation) `[aggregator]`
- [Crypto Briefing — OpenAI files for IPO with potential $1 trillion valuation, late 2026 listing](https://cryptobriefing.com/openai-ipo-filing-trillion-valuation/) `[secondary]`
- [IND Money — Inside OpenAI's Confidential SEC IPO Filing: Valuation, Financials and Risks](https://www.indmoney.com/blog/us-stocks/openai-ipo-valuation-financials-risks) `[analysis]`
- [Investing.com — The Trillion-Dollar IPO Test: SpaceX and OpenAI Face Public Markets](https://www.investing.com/analysis/the-trilliondollar-ipo-test-spacex-and-openai-face-public-markets-200680688) `[analysis]`

### Why it matters to you

- **Job lens:** Two compounding effects you should price in this week. (1) **Pre-IPO equity windows close fast** — if you've been waitlisting an Anthropic Solutions / FDE / Integration application, the window to be hired *before* the equity refresh-grant policy resets post-S-1 is narrowing; senior FDE TC at frontier labs is already $665K–$750K with 55–70% equity ([`05` §1](./05-career-and-startup.md#1-fde-tc)), and that equity component is **about to mark to a public price.** (2) **Post-S-1 quiet periods + SOX discipline = more structured headcount-planned hiring**, which is *good for new-grads* (clearer ladders, real comp bands, public org charts via the S-1 itself). Bookmark *both* labs' eventual public S-1s — you're about to get the cleanest revenue-by-org maps that have ever existed for either company.
- **Startup lens:** A simultaneous frontier-lab IPO wave is **liquidity rocket fuel for the rest of the stack.** Three downstream effects: (a) **founder-recycling** — large alumni cohorts cash out and angel-invest into the next wave (the classic Stripe/Square pattern, but at a 5× scale); (b) **enterprise budget legitimization** — CIOs find it easier to defend a 7-figure Claude/OpenAI commit when the vendor has a public market cap and quarterly disclosures; (c) **public market pressure tilts both labs toward monetization** — OpenAI toward ads ([2026-05-21/02 §1](../2026-05-21/02-new-emerging.md#1-ads-surface)), Anthropic toward enterprise margin and vertical Claude products (which is *good for your Integration Engineer lane*).
- **Insight:** **Both labs filing inside 8 days is itself the signal.** Anthropic moved first because its books are cleaner (the profitable-quarter projection). OpenAI followed because it could not be perceived as second. **The competitive equilibrium is now: whichever lab lists first sets the comp for the other.** Watch which prices first; that's the lab the public market believes is more durable.

→ Cross-link: [2026-05-22/01 §2 the OpenAI confidential-S-1 first read](../2026-05-22/01-big-lab-moves.md#2-openai-s1) · [`02` §1 IPO-wave as emerging asset class](./02-new-emerging.md#1-asset-class).

---

## 3. Fable 5 + Mythos 5 — Anthropic's first publicly-available Mythos-class model {#3-fable-5}

**What happened:** At **Code w/ Claude Tokyo (June 9–10)**, Anthropic announced **Claude Fable 5** + **Claude Mythos 5** — the rumored 5.x generation, shipped in two SKUs that resolve the EU access standoff this archive has tracked since [2026-05-06](../2026-05-06/01-big-lab-moves.md).

- **Fable 5 = the public, guardrailed sibling of Mythos.** Same generation, new safeguards that **block responses in specific high-risk domains** (cybersecurity, biology), making it the first Mythos-class model Anthropic ships to anyone with a paid plan.
- **Performance:** **+10% over Opus 4.8** on several benchmarks ([Opus 4.8 itself launched May 28 as a "modest but tangible improvement"](https://simonwillison.net/2026/May/28/claude-opus-4-8/) per Simon Willison); first model to clearly establish a meaningful **"gap widens as task length grows"** property in the early reports from Tokyo.
- **Day-1 distribution:** GA on **Claude API + Claude Platform + Claude Code + consumption-based Enterprise plans**, and on **AWS, Google Cloud, Microsoft Foundry simultaneously.** GitHub Copilot pushed Fable 5 to GA the same day.
- **Mythos 5** — the unguardrailed sibling — ships to **vetted defenders** (the established pattern from GPT-5.5-Cyber / Mythos-original).
- **Anthropic temporarily suspended Fable 5** within 48 hours after a controversy on terms-of-use surfaced and was re-enabled with revised terms — the InfoQ / BleepingComputer reporting is the cleanest record of this micro-incident; treat it as a reminder that **public-availability + guardrails is now its own product surface, not just a marketing question.**

**Sources:**
- [Anthropic News — Claude Fable 5 and Claude Mythos 5](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`
- [CNBC — Anthropic releases Mythos-like AI model to the public, Claude Fable 5](https://www.cnbc.com/2026/06/09/anthropic-mythos-claude-fable-5.html) `[secondary]`
- [GitHub Changelog — Claude Fable 5 is generally available for GitHub Copilot](https://github.blog/changelog/2026-06-09-claude-fable-5-is-generally-available-for-github-copilot/) `[primary]`
- [Latent Space (AINews) — Anthropic Claude Fable 5 — Mythos but Safe, with Controversial Terms](https://www.latent.space/p/ainews-anthropic-claude-fable-5-mythos) `[analysis]`
- [BleepingComputer — Anthropic rolls out Claude Fable 5, but it's available for a limited time](https://www.bleepingcomputer.com/news/artificial-intelligence/anthropic-rolls-out-claude-fable-5-but-its-available-for-a-limited-time/) `[secondary]`
- [InfoQ — Anthropic Releases and Temporarily Suspends Claude Fable 5](https://www.infoq.com/news/2026/06/claude-5-release/) `[secondary]`
- [Claude.com — Code with Claude Tokyo](https://claude.com/code-with-claude/tokyo) `[primary]`
- [note.com — Code w/ Claude Tokyo Day 1 First Half Report (山本 健太)](https://note.com/pn_yamaken/n/nd828717251bd?hl=en) `[secondary]`
- [pasqualepillitteri — Claude Fable 5 Is Here: First Public Mythos-Class Model](https://pasqualepillitteri.it/en/news/4523/claude-fable-5-fruitcake-eap-mythos-public-release) `[analysis]`

### Why it matters to you

- **Job lens:** This is the **third public validation in three weeks** of the Anthropic-stack focusing decision in [ME.md](../ME.md): (1) Karpathy joined Anthropic ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)), (2) S-1 confidential at $965B → $1.75T target (§2 above), (3) **Fable 5 lands the highest-benchmark model in the industry, day-one GA on every hyperscaler**. Update your portfolio repos to **explicitly target Fable 5** (model ID + the new task-length-scaling property). Anyone interviewing you for an Anthropic-adjacent role this week wants to see you operating on the *current* model, not Opus 4.7/4.8.
- **Startup lens:** The **guardrails-as-product** pattern is now the SKU split. Fable 5 (public, restricted) vs Mythos 5 (vetted, full). For founders, this opens **two distinct dependency surfaces**: build on Fable 5 if you need consumer/SMB reach with predictable refusal patterns; pursue Mythos 5 vetted access if you're building in defensible/dual-use lanes (cybersecurity, biosecurity, defense). The **vetting pipeline itself** ([Sundeep Teki on FDE / partner-program access](https://www.sundeepteki.org/advice/how-to-get-hired-at-openai-anthropic-and-google-deepmind-in-2026)) is increasingly a moat for early-stage cyber+bio AI startups.
- **Insight:** Watch the **gap-widens-on-long-tasks** property carefully. The earliest Tokyo reports emphasize that Fable 5's lead over peers **grows with task length and complexity** — this is exactly the regime that matters for *agents*. If it holds across more benchmarks over the next 30 days, agentic workloads are about to consolidate hard around Claude 5.x, which then makes the metering economics from §1 even more strategic. The whole edition rhymes: **the cheap-task layer commoditizes (Gemini 3.5 Flash), the long-horizon layer pulls away (Fable 5), and the bill in the middle is metered (June 15).**

→ Cross-link: [2026-05-06/01 §1 Mythos restricted launch origin](../2026-05-06/01-big-lab-moves.md) · [`02` §1 Fable 5 distribution implications](./02-new-emerging.md#1-fable-5-distribution).

---

## 4. Apple WWDC opens iOS 27 to third-party AI Extensions {#4-apple-extensions}

**What happened:** At **WWDC June 8, 2026** — **Tim Cook's last keynote as Apple CEO** — Apple announced **iOS 27 Extensions**, a framework + dedicated App Store marketplace that lets users set **Claude, ChatGPT, Gemini, or Grok** as the **default AI provider** across Siri, Writing Tools, and Image Playground.

- **Mechanics:** the framework exposes a system-level integration point; user picks default AI in Settings; the chosen model handles Siri intents, in-app writing assistance, and image-generation Playground prompts.
- **Distribution surface:** **>1.5 billion active Apple devices** (the framework is iOS 27 + macOS 27 + iPadOS 27 + watchOS).
- **Timing:** **Beta now (developer + public), production ship Fall 2026** with the iOS 27 consumer release.
- **Stagecraft footnote:** the marquee Extensions UX was **conspicuously absent from the WWDC keynote slides themselves** — present in the SDK + beta, scheduled to be the Sept iPhone-event headline — a deliberate split designed to keep the iPhone keynote charged. This archive has tracked this rollout since [2026-05-07/01](../2026-05-07/01-big-lab-moves.md) and [2026-05-11/01](../2026-05-11/01-big-lab-moves.md).

**Sources:**
- [AI Weekly — Apple iOS 27 Extensions Opens Third-Party AI Marketplace at WWDC 2026](https://aiweekly.co/node/2611) `[aggregator]`
- [Tom's Guide — Apple WWDC 2026 recap: Siri AI, iOS 27, Apple Intelligence](https://www.tomsguide.com/news/live/wwdc-2026-live-news-updates) `[secondary]`
- [Tom's Guide — WWDC 2026 was Apple's AI renaissance — but there's one feature still missing](https://www.tomsguide.com/phones/iphones/wwdc-2026-was-apples-ai-renaissance-but-theres-one-very-important-feature-still-missing-from-ios-27) `[analysis]`
- [TheNextWeb — Why Apple built a third-party AI system for Siri and then refused to show it at WWDC](https://thenextweb.com/news/apple-siri-extensions-third-party-ai-missing-wwdc) `[analysis]`
- [MacRumors — What to Expect From WWDC 2026: Gemini-Powered Siri, iOS 27, macOS 27](https://www.macrumors.com/guide/wwdc-2026-what-to-expect/) `[secondary]`
- [Redshark — WWDC 2026: new Siri, Gemini deal and iOS 27](https://www.redsharknews.com/apple-wwdc-2026-siri-gemini-ios-27) `[secondary]`
- [iTechPost — 3 Hidden Major iOS 27 Features Reportedly Coming This Fall](https://www.itechpost.com/articles/236318/20260614/3-hidden-major-ios-27-features-are-reportedly-coming-this-fallheres-what-expect.htm) `[secondary]`
- [BuildFastWithAI — AI News Today June 8, 2026 (Tim Cook last keynote framing)](https://www.buildfastwithai.com/blogs/ai-news-today-june-8-2026) `[aggregator]`

### Why it matters to you

- **Job lens:** Apple Extensions creates a new lane on top of the Anthropic-stack focusing decision: **iOS Extension SDK engineering on the AI side**. Anthropic and Google both need engineers who can ship an Extension that handles Siri intents *well* in fall — that's a 90-day shovel-ready window. If you have one weekend free, **build a "Claude-as-Siri-default" Extension sample app** (against the iOS 27 beta SDK) and post it. It's a near-zero-competition portfolio piece for the next 4 weeks before the iOS 27 GA wave drives applicant supply up.
- **Startup lens:** This is **the biggest distribution-channel shift of 2026**. A founder who builds a *vertical* Extension (e.g., "Claude-for-Legal as Siri default for solo-practitioner attorneys", anchored to [2026-05-13/01](../2026-05-13/01-big-lab-moves.md)) gets **default-AI surface on every iPhone in their target demographic**. Two of your STARTUPS.md wedges (vertical-Claude-for-X and agent-identity) gain a new go-to-market by becoming the *default AI in their vertical*'s iPhone. Move "Build Extension SDK demo" into STARTUPS.md.
- **Insight:** Read the **Tim Cook signal**. A CEO's final keynote is reserved for moves the CEO wants on their tape. Cook chose **opening Apple's AI distribution to competitors** — explicitly admitting Apple can't win the model layer alone, and pricing that admission as a *strategic* not *defeated* move. The takeaway: **the distribution layer (Apple, browser, OS) and the model layer (Anthropic/OpenAI/Google) just decoupled in public**. For your career bets, this validates that distribution-side roles (Apple Intelligence Extension integration, Chrome WebMCP — [2026-05-19](../2026-05-19/01-big-lab-moves.md)) are now durable, not transitional.

→ Cross-link: [2026-05-07/01 Apple Extensions framework origin](../2026-05-07/01-big-lab-moves.md) · [2026-05-11/01 Apple multi-AI Extensions confirm](../2026-05-11/01-big-lab-moves.md) · [`05` §3 Apple Extensions as a portfolio shovel](./05-career-and-startup.md#3-portfolio).

---

## 5. Google Gemini 3.5 Pro still pending — the cheap-tier price war held, the high-end didn't ship {#5-gemini-pending}

**What happened:** **Gemini 3.5 Pro has not shipped as of June 16**, despite Sundar Pichai naming a **"within a month"** window at I/O on May 19. The model remains in internal use and limited preview.

- **Promised specs:** **2-million-token context window**, **"Deep Think"** reasoning mode, frontier multimodal understanding. In Google's reorg, Pro absorbs the use cases previously routed to the deprecated "Ultra" tier.
- **Expected pricing (unconfirmed):** ~10× the Flash rate, i.e., ~**$15/$60 per 1M tokens** — would still undercut Anthropic/OpenAI flagships by a wide margin.
- **Gemini 3.5 Flash held the price line:** **$1.50/$9 per 1M (input/output)**, $0.15 cached input, 1M ctx, multimodal — shipping since I/O day, has held its position as the cheap-tier price floor of the industry.

**Sources:**
- [TechTimes — Google Gemini 3.5 Pro Nears June Launch With 2 Million Token Context And Deep Think Reasoning](https://www.techtimes.com/articles/317919/20260606/google-gemini-35-pro-nears-june-launch-2-million-token-context-deep-think-reasoning.htm) `[secondary]`
- [Codersera — Gemini 3.5 Pro: The June 2026 Launch Guide](https://codersera.com/blog/gemini-3-5-pro-launch-guide-2026/) `[analysis]`
- [WaveSpeed — Gemini 3.5 Pro Is Coming Next Month — What the Flash Release Already Tells Us](https://wavespeed.ai/blog/posts/gemini-3-5-pro-coming-next-month/) `[analysis]`
- [ofox.ai — Gemini 3.5 Pro: Release Date, Expected Specs, and What Flash Already Tells Us](https://ofox.ai/blog/gemini-3-5-pro-release-date-expected-specs-2026/) `[analysis]`
- [Google AI for Developers — Gemini API release notes (changelog)](https://ai.google.dev/gemini-api/docs/changelog) `[primary]`

### Why it matters to you

- **Job lens:** **The "build now while the high-end is still single-vendor" window is open another 2–4 weeks.** Until Gemini 3.5 Pro ships, the long-task agentic frontier is **Fable 5 alone** (with Opus 4.8 as the Anthropic-stack baseline). If you've been delaying portfolio work waiting to triangulate three providers — start with two (Claude + GPT-5.5), commit code, and add Gemini 3.5 Pro as a leg post-launch. **Shipping beats hedging.**
- **Startup lens:** **Cheap-tier price war is fully won by Flash at $1.50/1M.** Anyone building "the cheapest inference" as a moat is racing a Google-margin curve, which is unwinnable. Move the wedge from *price* to **task-class routing** (cheap-when-it-works, premium-when-it-matters) — that's where the Personal Billing Audit ([ME.md](../ME.md)) doubles as customer-discovery.
- **Insight:** Watch the Anthropic counter-pricing carefully when Gemini 3.5 Pro lands. Anthropic has so far refused to chase Flash on price — confident in Fable 5's long-task lead. If Anthropic *does* drop price on Sonnet to defend the cheap tier, that's a signal the gap-widens-on-length property isn't holding under independent eval. If pricing stays sticky, it's a vote of confidence in the moat.

→ Cross-link: [2026-05-19/01 Gemini 3.5 Flash launch](../2026-05-19/01-big-lab-moves.md) · [2026-05-20/01 §1 I/O scorecard](../2026-05-20/01-big-lab-moves.md#1-io-scorecard).
