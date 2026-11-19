# Big Lab Moves — 2026-06-09

The morning after WWDC. Two things stack today: **(1) WWDC graded — Apple Intelligence Extensions framework shipped, Gemini-Siri confirmed**, and the open questions are revenue-share + day-1 partner labs + dev SDK access date. **(2) The 96-hour stack** — Tokyo Wed, SpaceX IPO pricing Thu, Agent SDK metering Sun — bracket your week with four hard deadlines.

Tags: `#labs #apple #wwdc #extensions #siri #gemini #anthropic #tokyo #spacex #ipo #metering`

---

## 1. WWDC GRADED — Extensions framework SHIPPED, ~6/8 on yesterday's grid <a id="1-wwdc-graded"></a>

**Grading yesterday's 8-hypothesis grid** ([2026-06-06/03 §3](../2026-06-06/03-practical-skills-and-tools.md#3-wwdc-discipline) + [2026-06-08/01 §1](../2026-06-08/01-big-lab-moves.md#1-wwdc)):

| # | Hypothesis | Outcome | Notes |
|---|---|---|---|
| 1 | Extensions SDK shipped | ✅ HIT | "Apple Intelligence Extensions"; system-level picker (Claude / Gemini / ChatGPT) |
| 2 | Multi-vendor Setup picker | ✅ HIT | User-level choice, not per-app |
| 3 | Siri 2.0 standalone | ✅ HIT | Rebuilt Siri with deep system-wide context + on-screen awareness |
| 4 | Billing model disclosed | ❌ MISS | Revenue-share % for Extensions NOT announced on-stage |
| 5 | On-device vs cloud API split | ⚠️ PARTIAL | Apple Intelligence "expanded" across Mail / Messages / Calendar / etc., but the cloud/on-device split isn't itemized |
| 6 | Image Playground 3rd-party | ⚠️ PARTIAL | Photo edits via natural-language description shipped; 3rd-party model routing for image gen not explicit |
| 7 | Apple-silicon ML runtime | ✅ HIT | iOS 27 up to 30% faster app launches (proxy signal); macOS Golden Gate refines neural-engine-tuned runtime |
| 8 | Agents-on-other-apps gating | ⚠️ OPEN | Extensions framework permits cross-app intents but the *gating policy* (which intents which agents can call) isn't fully spec'd until the SDK lands |

**Net:** **~6/8 hit, 2 open / partial.** The two biggest open questions are **(a) the revenue-share %** for third-party AI labs that ship Extensions, and **(b) the day-1 partner list** — Apple didn't announce on-stage which labs are shipping Extensions on day-1. Expect [Anthropic news](https://www.anthropic.com/news) + [OpenAI news](https://openai.com/news/) to address this inside 48 hours.

**Sources:**
- [Apple newsroom — Apple unveils next generation of Apple Intelligence, Siri AI, and more](https://www.apple.com/newsroom/2026/06/apple-unveils-next-generation-of-apple-intelligence-siri-ai-and-more/) `[primary]`
- [TechRadar — WWDC 2026 live blog](https://www.techradar.com/news/live/apple-wwdc-2026-live) `[secondary]`
- [Tom's Guide — WWDC 2026 recap: Siri AI, iOS 27, Apple Intelligence](https://www.tomsguide.com/news/news/live/wwdc-2026-live-news-updates) `[secondary]`
- [Engadget — Everything announced at Apple's WWDC 2026 keynote](https://www.engadget.com/2189698/everything-announced-at-apples-wwdc-2026-keynote/) `[secondary]`
- [Storyboard18 — 5 biggest announcements from WWDC 2026](https://www.storyboard18.com/photos/digital/apples-ai-moment-5-biggest-announcements-from-wwdc-2026-100585.htm) `[analysis]`
- [Memeburn — Apple WWDC 2026: Siri AI, iOS 27 & every big announcement](https://memeburn.com/apple-wwdc-2026-siri-ai-ios-27-every-big-announcement/) `[secondary]`

### Why it matters to you

- **Job:** **Update LinkedIn today with the EXACT terms** — `Apple Intelligence Extensions`, not "Apple AI"; `App Intents (iOS 27)`, not "iOS AI integration"; `Gemini-Siri integration`, not "Google AI on iPhone". This is the **keyword-precision lesson from [2026-05-20/01 §1](../2026-05-20/01-big-lab-moves.md#1-io-scorecard)** executed live. The first-mover keyword window before recruiter searches saturate is roughly 10 days. Pair with the **FDE compensation report** from yesterday ([2026-06-08/05 §1](../2026-06-08/05-career-and-startup.md#1-fde-comp)) — Apple Intelligence Extensions credentialing pulls forward into the Anthropic Solutions / OpenAI FDE story.
- **Startup:** The **revenue-share %** question is the single biggest unknown gating Extensions-native startup viability. Until Apple publishes (likely in the iOS 27 developer guide within ~10 days), assume the **Apple App Store standard 15–30% take rate** as the planning anchor. The wedge stays the same: pick a sharp vertical (focus / calendar / notes / fitness / accessibility), ship a thin App-Intent agent. **6-month wedge, not 6-year** — the saturation curve will be fast.
- **Insight:** The **MCP-shape converges with the Extensions-intent shape**. Both are "agent declares what it can do; system routes a user request to the right agent." The MCP standard is now ratified across **(1) consumer browser (WebMCP origin trial in Chrome 149)**, **(2) enterprise cloud (AWS MCP Server GA today, see [`02` §1](./02-new-emerging.md#1-aws-mcp-ga))**, and **(3) OS picker (Apple Extensions speaks an MCP-shaped grammar)**. This is the **"platform layer settling on a single intent / tool-use protocol"** prediction confirmed across all three surfaces inside 4 weeks. Quote in interviews.

→ Cross-link: [2026-06-08/01 §1 — pre-keynote Bloomberg consensus](../2026-06-08/01-big-lab-moves.md#1-wwdc) · [2026-05-07/01 — original iOS 27 multi-AI Extensions leak](../2026-05-07/01-big-lab-moves.md) · [2026-05-20/01 §2 — WebMCP origin trial in Chrome 149](../2026-05-20/01-big-lab-moves.md).

`#apple #wwdc #extensions #siri #gemini #graded`

---

## 2. Tokyo Wed + SpaceX IPO Thu + Agent SDK metering Sun — the 96-hour stack <a id="2-tokyo-and-ipo"></a>

Three hard deadlines bracket the week. Each is a thread already on the WATCHLIST; today they compress.

### 2a. Code w/ Claude Tokyo — Wed Jun 10 (T-1)

**What's coming:** Anthropic's APAC counterpart to the May-19 London event. Customer presenters (subset of Asana / Cursor / GitHub / Replit / Vercel + likely APAC adds — Rakuten / SoftBank / NTT-class) likely. Day-1 livestream from 10 AM JST. Watch for:

1. **Post-WWDC Apple Extensions surface-area mention** — does Anthropic announce "Claude on Apple Extensions" on a Tokyo stage? Likely yes; this is the natural slot.
2. **Agent SDK metering soft-landing messaging** — T-5 to the June-15 cutover. Pricing-router demos likely.
3. **APAC customer announcements** — any Japanese / Korean / Singaporean enterprise customer logo would lift the post-S-1 narrative materially.

**Source:** [Anthropic events](https://www.anthropic.com/events) (Tokyo session schedule) `[primary]`.

### 2b. SpaceX IPO pricing — Thu Jun 11 (T-2)

**What's coming:** SpaceX prices Thursday Jun 11, trades Friday Jun 12 on NASDAQ as **"SPCX"** at **~$1.75T target**. This is the **precedent print** the Anthropic + OpenAI offerings calibrate against — public-market AI is no longer a thought experiment as of 96 hours from now.

Per [2026-06-08/02 §1](../2026-06-08/02-new-emerging.md#1-spacex-ipo): expect first-day pop + first-week trading range to set the multiple frame for the Anthropic roadshow.

### 2c. Anthropic Agent SDK metering — Sun Jun 15 (T-6)

**What's coming:** Programmatic Claude (Agent SDK, `claude -p`, GitHub Actions, OpenClaw) moves to a separate credit pool billed at full API list rates. Per-tier credit pool ($20 / $100 / $200 for Pro / Max-5x / Max-20x). [Originally tracked from 2026-05-16](../2026-05-16/01-big-lab-moves.md).

**Two-step actions before Sunday:**
1. **Verify the Agent SDK credit toggle is active** in account settings (manual, easy to miss — see [2026-05-18/03](../2026-05-18/03-practical-skills-and-tools.md))
2. **Cost-router baseline data** — three weeks of running data lets you set the right Opus-4.8/Sonnet-4.6 split. The [Opus-orchestrator + Sonnet-worker pattern from 2026-06-08/03 §1](../2026-06-08/03-practical-skills-and-tools.md#1-opus-48-baseline) is the direct mitigation.

### Why this 96-hour stack matters to you

- **Job:** Three FDE-shaped questions in *any* interview this week — "What's the impact of metering on agent workflows?" / "What's the IPO-narrative comp set?" / "How do you think about cost-aware multi-vendor routing?" — all map to one or more of these three events. A graded-WWDC + Tokyo-recap + IPO-pricing thread on LinkedIn this week is structurally over-indexed for recruiter signal.
- **Startup:** Two compounding wedges. **(1)** The metering switch on Sunday creates a *real* dollar problem for every Claude Code shop with CI/CD volume — pricing-router middleware has a clean GTM window for the next ~6 weeks. **(2)** Public-market trading on Friday creates **first-time-ever AI-secondary-market-comp data** — the moment a frontier AI company trades on a stock exchange, your pitch comp set changes; price that into any raise this summer.
- **Insight:** The week-shape pattern (consumer keynote Mon → developer event Wed → IPO Thu → SaaS pricing change Sun) is a microcosm of the **2026 AI calendar shape**: every quarter has one of these stacks, and the stack you watch *closest* tells you whether you understand the macro. Watch all three.

→ Cross-link: [2026-06-08/02 §1 — SpaceX IPO](../2026-06-08/02-new-emerging.md#1-spacex-ipo) · [2026-05-16 — Agent SDK metering announcement](../2026-05-16/01-big-lab-moves.md) · [2026-05-19/01 — Code w/ Claude London precedent](../2026-05-19/01-big-lab-moves.md).

`#tokyo #spacex #ipo #metering #stack`

---

## Cross-links

- This edition pairs tightly with [`03` §1](./03-practical-skills-and-tools.md#1-aws-mcp-setup) (AWS MCP install — the practical artifact this week) and [`05` §1](./05-career-and-startup.md#1-partner-network) (Partner Network apply window).
- WATCHLIST.md threads resolved: **Apple Extensions SDK** (was 🟡 from [2026-06-06 SATURDAY SORT](../WATCHLIST.md)).
- Open: revenue-share %, day-1 partner labs, dev SDK access date, Tokyo customer announcements, SpaceX first-day pop.
