# Big Lab Moves — 2026-07-11

The week the mobile super-app war went live, and the talent map re-drew *toward Anthropic*. **OpenAI merged Codex + ChatGPT into a single "super app"** (with GPT-5.6 landing in three sizes — Sol / Terra / Luna), **Anthropic shipped Claude Cowork for iOS + Android** (mobile agentic sessions, finally decoupled from a desktop), **four senior DeepMind researchers left in one week** (three of them to Anthropic — including Nobel laureate John Jumper), and **the OpenAI IPO slipped to 2027** while Altman holds his $1T floor. The frame: *the frontier moved onto your phone; the talent moved into Anthropic; and the public-market path just got longer.*

Tags: `#labs #openai #anthropic #google #deepmind #ipo #talent #mobile #superapp #cowork`

---

## 1. OpenAI ships the "super app" — Codex + ChatGPT merged, GPT-5.6 (Sol / Terra / Luna) rolling out {#1-openai-superapp}

**What happened (July 9–10):**

- **OpenAI officially rolled out GPT-5.6** on July 9 — three sizes: **Sol** (flagship), **Terra** (balanced), **Luna** (budget). Launch followed a completed U.S. government review (the surviving voluntary review from the postponed EO thread — see [2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)).
- **Codex and ChatGPT merged into a single "super app."** OpenAI is now shipping **ChatGPT Work** (web + mobile), a new **ChatGPT desktop app**, and a **hosted-websites feature** — you build and share a site directly through ChatGPT Work.
- Roll-out sequence: **Pro / Enterprise / Edu first (July 9); Plus / Business over the next few days.**
- Positioning line from OpenAI: 5.6 is *"competitive with models that are far, far more expensive at twice the speed and much, much cheaper."*
- Companion launch: **OpenAI Bio Bug Bounty** — a security-vulnerability program specifically for the biology / life-sciences model surface (paired with §2 of Anthropic's own Claude Science drug-discovery push, [`02` §1](./02-new-emerging.md#1-claude-science)).

**Sources:**
- [OpenAI News (index) — GPT-5.6 launch + ChatGPT Work + Bio Bug Bounty](https://openai.com/news/) `[primary]`
- [CGTN — OpenAI unveils long-awaited "super app" as rivalry with Anthropic intensifies](https://news.cgtn.com/news/2026-07-10/OpenAI-unveils-super-app-as-rivalry-with-Anthropic-intensifies-1OF7nrvaglG/p.html) `[secondary]`
- [BuildFastWithAI — AI News Today July 10 2026 (biggest stories)](https://www.buildfastwithai.com/blogs/ai-news-today-july-10-2026) `[aggregator]`
- [LLM-Stats — Latest AI model releases (GPT-5.6 Sol/Terra/Luna)](https://llm-stats.com/llm-updates) `[analysis]`
- [Releasebot — Anthropic + OpenAI release notes, July 2026 (roll-up view)](https://releasebot.io/updates/anthropic) `[aggregator]`

### Why it matters to you

- **Job lens:** Whichever role you take next, the interviewer is on the receiving end of a **model-family fragmenting into tiers.** The right sentence in a cover letter this month is *"I designed for the flagship / balanced / budget size split (Sol/Terra/Luna, Opus/Sonnet/Haiku, Grok 4.5 vs Grok 4-mini) and can defend the routing decision by task."* That's the FDE/Integration-Engineer job in one line. Concrete task: pick one repo you already have, add a **`ROUTING.md`** at the root describing which model handles which subtask + why + observed cost — and reference it in interviews.
- **Startup lens:** The "super app" pattern **removes a distribution moat** — ChatGPT's *"you can host your website inside ChatGPT Work"* directly targets the surface that Cursor, Replit, and Vercel own today. That's both a threat (if your startup is a thin wrapper) and an opening (if your wedge is verticalized: a legal super-workspace, a physician-super-workspace, a founder-super-workspace). The pattern to bet on now: **"a super app for one profession, on the Claude Cowork mobile surface" ([§2](#2-cowork))**, not "a general chat wrapper."
- **Insight:** Sol / Terra / Luna is **product marketing catching up to what pricing already forced.** Anthropic did it with Opus/Sonnet/Haiku a year ago; OpenAI is finalizing the same tier language. From here forward, **assume every frontier lab ships three sizes at three prices**, and treat *routing* as a first-class engineering skill.

→ Cross-link: [`03` §1 code-execution-with-MCP + federated orchestration](./03-practical-skills-and-tools.md#1-code-exec-mcp) · [2026-05-22/03 §1 the Opus-orchestrator / Sonnet-worker split](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost).

---

## 2. Anthropic Claude Cowork for iOS + Android — mobile agentic sessions go live {#2-cowork}

**What happened (July 10, same 24-hour window as §1):**

- **Anthropic launched Claude Cowork for mobile** on **iOS + Android** — the single largest surface change since Claude Code shipped. The blocking constraint it removes: previously, **agentic sessions required a desktop client to remain active** (close the laptop → the agent stops). With Cowork mobile, **you delegate a long-running agent, close the laptop, and monitor from your phone.**
- Pairs with the wider July 6–10 Anthropic release wave (Week 28):
  - **Claude Opus 4.7 is now the default on Max and Team Premium**, with a new **`xhigh` effort level** as the recommended coding setting and an interactive **`/effort` slider** (dial reasoning intensity mid-session).
  - **Routines on Claude Code on the web** — fire templated cloud agents from a **schedule, GitHub event, or API call.** Mobile push notifications ping your phone when a long task finishes or the agent needs you.
  - **`/usage`** shows what's driving your plan limits (the metering audit tool the June 15 change forced everyone to want).
  - **CLI moves to native binaries** — no more Node runtime dependency; the developer surface just got a lot slimmer.
  - **In-app browser on Desktop** — Claude Code can pull up docs, designs, or any site and interact with pages the way it does with a local dev-server preview.
- Beta **reflection dashboard** on Claude web + desktop: usage patterns, quiet hours, "use AI more intentionally" prompts — Free/Pro/Max with Memory on. Positioned against the ChatGPT ads-first monetization surface — quiet ideology piece as much as feature.
- **API key expirations** (preset / custom / Never) — an infra pattern that finally shows up on the console.

**Sources:**
- [BuildFastWithAI — AI News Today July 10 2026 (Claude Cowork mobile launch)](https://www.buildfastwithai.com/blogs/ai-news-today-july-10-2026) `[aggregator]`
- [Claude Code — What's new (official changelog)](https://code.claude.com/docs/en/whats-new) `[primary]`
- [Anthropic — Enabling Claude Code to work more autonomously](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously) `[primary]`
- [Releasebot — Claude Code Updates July 2026 (Week 28 rollup)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Anthropic — Use the Claude Agent SDK with your Claude plan (help center)](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [MarkTechPost — Claude Code Guide 2026: 25 features with examples](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) `[analysis]`

### Why it matters to you

- **Job lens:** *"I built and operate a mobile-first autonomous knowledge-work agent, fired by schedule, monitored via push notification, with a documented failure-recovery loop"* is a **directly hire-able sentence** for FDE / Solutions / Integration Engineer roles this quarter. **Ship one before Monday** — the [`03` §2](./03-practical-skills-and-tools.md#2-artifact) walk-through is the artifact.
- **Startup lens:** Cowork on mobile is the **wedge into non-desktop workflows** the Claude platform previously couldn't touch: field-services, healthcare rounds, sales prep in the car, on-call triage. The startup lane is *not* "build the app" — it's **build the domain-specific Routine library** that runs on top: 10–20 vertical Routines packaged as a template pack + light CLI setup, sold to a specific occupation. Cheap to prototype (a `.md` file + an MCP server), hard to displace (it lives inside the customer's tools).
- **Insight:** The **mobile agent surface has arrived**, on both sides of the frontier, in the same week — and it inverts an assumption most 2025 tooling was built on ("the developer is at a laptop"). The next 12 months of AI product design will re-run the 2010 desktop-to-mobile transition, compressed: **anything that assumes an always-open terminal is now legacy.** Update your mental model accordingly — and design your artifacts to be *observed*, not just *run*.

→ Cross-link: [`03` §2 the Routine artifact](./03-practical-skills-and-tools.md#2-artifact) · [2026-05-22/01 §3 Karpathy → Anthropic pre-training (the destination signal these tools now serve)](../2026-05-22/01-big-lab-moves.md#3-karpathy).

---

## 3. DeepMind talent exodus — Nobel laureate + two co-authors to Anthropic, Gemini co-lead to OpenAI {#3-deepmind-exodus}

**What happened (early-to-mid July):**

- **Four senior DeepMind researchers departed in a single week**:
  - **Noam Shazeer** (Gemini co-lead; co-inventor of the Transformer's key attention innovations and Google's Character.AI acquihire) → **OpenAI**.
  - **John Jumper** (**2024 Nobel Prize in Chemistry** for AlphaFold) → **Anthropic**.
  - **Jonas Adler** → **Anthropic**.
  - **Alexander Pritzel** → **Anthropic**.
- The two Anthropic-bound co-authors (Adler + Pritzel) sit inside Jumper's structural-biology / AlphaFold research lineage — this isn't three unrelated hires; it's *the AlphaFold research thread* moving labs.
- **Markets reacted violently**: **~$225B off Alphabet's market cap** was attributed to the exodus + the Gemini 3.5 Pro delay (see §5) in reporting.
- Backdrop: Anthropic just released **Claude Sonnet 5 (June 30)** at near-Opus-4.8 quality, **Claude Fable 5 GA (June 9)** with 1M-token context + always-on adaptive thinking + safety fallback to Opus 4.8 for cyber/bio-flagged requests, and **Fable 5 was globally redeployed on July 1** after the US lifted export controls. The team-arrival timing is not a coincidence.

**Sources:**
- [The Agent Report — Google Gemini 3.5 Pro delayed to July 2026; $225B wiped off Alphabet as DeepMind talent exodus deepens](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) `[secondary]`
- [BigGo Finance — Google delays Gemini 3.5 Pro launch to July 17 for full architectural rebuild](https://finance.biggo.com/news/6f0c6bb2-795f-4c57-9d09-6db691d7638a) `[secondary]`
- [Anthropic Newsroom — Claude Sonnet 5 launch (June 30)](https://www.anthropic.com/news/claude-sonnet-5) `[primary]`
- [MacRumors — Anthropic launches Claude Sonnet 5 with near-Opus performance at a lower price](https://www.macrumors.com/2026/06/30/anthropic-claude-sonnet-5/) `[secondary]`
- [gHacks — Claude Sonnet 5, Fable 5 & Mythos 5 redeployed after US lifts export controls](https://www.ghacks.net/2026/07/01/anthropic-releases-claude-sonnet-5-with-near-opus-performance-restores-fable-5-and-mythos-5-after-us-lifts-export-controls/) `[secondary]`
- [Claude timeline (community-maintained public record)](https://github.com/jqueryscript/anthropic-claude-timeline) `[aggregator]`

### Why it matters to you

- **Job lens:** This is the **strongest possible market signal** for your ME.md focusing decision ([`ME.md` #Current focusing decision](../ME.md)). The **Jumper + AlphaFold-lineage → Anthropic** move rhymes exactly with **Karpathy → Anthropic** on 2026-05-19 ([2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)): pre-training + fundamental research talent is voting with its feet, and the destination is one place. Cite this in interviews — *specifically the Jumper move* — as evidence you read the sector, not just the news feed.
- **Startup lens:** Where Jumper/Adler/Pritzel land inside Anthropic tells you where **Claude Science drug-discovery** ([`02` §1](./02-new-emerging.md#1-claude-science)) is heading. If you're founding, the wedge that pays off in 12 months is not "compete with them on models" — it's **the operator layer**: eval harnesses for molecular-property agents, MCP servers over lab-inventory systems, integration into the wet-lab tooling stack. Build against the *product* that this team is going to ship, not the model.
- **Insight:** The clean read is **"Anthropic beat Google in the July talent market, and the public markets priced it."** But the deeper signal is that the frontier is now optimizing for a **specific research profile — automation of scientific discovery + long-horizon-agent reliability** — and each of Karpathy / Jumper / Adler / Pritzel sits inside that profile. Skill-invest for that shape (verification, memory, tool routing), not for "raw LLM engineering" in the abstract.

→ Cross-link: [`05` §1 Anthropic as career destination](./05-career-and-startup.md#1-anthropic-destination) · [2026-05-22/01 §3 the Karpathy move](../2026-05-22/01-big-lab-moves.md#3-karpathy).

---

## 4. OpenAI IPO slipped to 2027 — Altman's $1T floor holds {#4-ipo-slip}

**What happened (late June, still current):**

- **Reuters (late June)** and **Bloomberg (June 26)** reported that OpenAI is now **leaning toward a 2027 IPO**, not the September/October 2026 date that [2026-05-22/01 §2](../2026-05-22/01-big-lab-moves.md#2-openai-s1) led with.
- The primary reason cited: **CEO Sam Altman's hard floor at a $1 trillion listing** — combined with **market volatility** through Q2/Q3.
- The confidential S-1 filed May 22 is still in place; the **valuation band remains $852B → >$1T**; **Goldman Sachs + Morgan Stanley** still lead the deal.
- New financial data surfaced in the reporting: OpenAI is pulling **~$2B/month** in revenue, hit **~$25B annualized run-rate by March**, has **50M consumer subscribers + 9M business users**, and **loses $1.22 for every $1 of revenue**.

**Sources:**
- [AIToolsRecap — OpenAI IPO 2026: confidential S-1 filed, $1T valuation target, timeline](https://aitoolsrecap.com/Blog/openai-ipo-2026-s1-filing-valuation-timeline) `[analysis]`
- [BingX Learn — OpenAI Pre-IPO Outlook 2026 (Reuters + Bloomberg July follow-up)](https://bingx.com/en/learn/article/openai-pre-ipo-global-outlook-trillion-dollar-artificial-intelligence-race-enters-final-stretch) `[analysis]`
- [Polymarket — OpenAI IPO by...? (live prediction market)](https://polymarket.com/event/openai-ipo-by) `[analysis]`
- [DecodeTheFuture — OpenAI IPO explained: S-1 filing, date & valuation](https://decodethefuture.org/en/openai-ipo-explained/) `[analysis]`
- [Indmoney — Anthropic vs OpenAI IPO date: who will list first?](https://www.indmoney.com/blog/us-stocks/anthropic-openai-ipo-date-valuation-risks) `[analysis]`

### Why it matters to you

- **Job lens:** For 2026 offers: **stop pricing OpenAI equity as "months-away liquidity."** RSU vs option math flips when the IPO horizon lengthens by 12+ months. If you get an OpenAI offer, **assume a 2027 listing at best**, and negotiate for cash/base + a signing bonus rather than optimizing for equity. Same discipline applies to any lab where the IPO thread just moved.
- **Startup lens:** **Loses $1.22 per $1 of revenue** is the number to hold onto. That's a company **structurally dependent on continued capital access + platform take-rate expansion** — meaning enterprise price rises, ad-surface build-out, and OS-level integration deals will all accelerate. If your startup rides on OpenAI infra, price in ~20–30% higher API cost by year-end and treat it as a *known*, not a risk.
- **Insight:** The most important detail is Altman's **$1T floor** — a **behavioral commitment**, not a market fact. Founders and lab leaders now use IPO date as a signaling device, not a plan. Read every "we might list in Q2" statement through that filter: it's positioning, not calendar.

→ Cross-link: [2026-05-22/01 §2 the original S-1 filing story](../2026-05-22/01-big-lab-moves.md#2-openai-s1) · [`05` §2 how the slip reshuffles your offer math](./05-career-and-startup.md#2-offer-math).

---

## 5. Gemini 3.5 Pro delayed to July 17 — full architectural rebuild, DeepMind talent bleed context {#5-gemini-delay}

**What happened:**

- **Google DeepMind delayed Gemini 3.5 Pro to July 17, 2026** — six days from today. Sundar Pichai had promised a June ship at Google I/O 2026 ([2026-05-19](../2026-05-19/), [2026-05-20](../2026-05-20/)). The June date slipped, then July, then this specific date.
- **Full architectural rebuild**: Google scrapped the existing Gemini 2.5 Pro architecture, citing enterprise-tester feedback that the model was **consuming excessive tokens during extended agentic tasks** — the exact failure mode the [Toolathlon / MCP-Atlas](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks) benchmarks were built to catch.
- **New capabilities claimed:** 2M-token context window, **Deep Think Reasoning Layer**, autonomous workflow support, improvements in mathematical reasoning, SVG generation, image quality.
- **Positioning:** Google is explicitly targeting parity with **GPT-5.6 and Claude Fable 5**.
- **Context:** the delay + §3 exodus together drove **~$225B off Alphabet's market cap**.

**Sources:**
- [BigGo Finance — Google delays Gemini 3.5 Pro launch to July 17 for full architectural rebuild](https://finance.biggo.com/news/6f0c6bb2-795f-4c57-9d09-6db691d7638a) `[secondary]`
- [The Agent Report — Google Gemini 3.5 Pro delayed to July 2026: $225B wiped off Alphabet](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) `[secondary]`
- [Google Blog — Latest AI news announced in June 2026 (context)](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-june-2026/) `[primary]`
- [Releasebot — Gemini updates by Google, July 2026](https://releasebot.io/updates/google/gemini) `[aggregator]`
- [DeepMind — News blog](https://deepmind.google/blog/) `[primary]`

### Why it matters to you

- **Job lens:** If you had "learn Vertex AI Agent Platform" on your priority list from the [2026-05-20/03](../2026-05-20/03-practical-skills-and-tools.md) I/O sweep, **hold the investment shallow** until 3.5 Pro actually ships and is measurable. The token-consumption failure means Google's agentic story is **not production-ready for extended tasks** as of today — building a portfolio piece on top of an unstable primitive burns credibility.
- **Startup lens:** Google's excessive-token failure is a **direct opening for cost-side wedges** — any startup that offers *routed multi-vendor agentic execution + token-usage monitoring* now has the case study handed to it. "We saw Google delay a flagship for this failure mode; here's how we prevent it in your stack."
- **Insight:** **Rebuilds ship late.** Read the delay + the talent exodus together and the takeaway is: **the incumbent Google-scale advantage did not translate cleanly into the agentic paradigm.** Assume the same could be true for other 2020-era incumbents (Microsoft in-house MAI, Meta AI, Apple Intelligence) in 2026–2027. Skill-invest for the *reorg* wave that follows, not the current org-chart.

→ Cross-link: [2026-05-20/01 §2 Antigravity / Managed Agents (the runtime primitive)](../2026-05-20/01-big-lab-moves.md) · [2026-05-22/04 §1 real-tool benchmarks (the failure mode this delay confirms)](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks).
