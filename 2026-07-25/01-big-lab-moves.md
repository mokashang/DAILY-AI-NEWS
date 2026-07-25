# Big Lab Moves — 2026-07-25

The week the workhorse tier repriced and the "everyone is a frontier lab" era officially ended. **Anthropic shipped Claude Opus 5 yesterday at Opus 4.8 pricing** — a 96% SWE-bench Verified, 1M-token, effort-toggled workhorse for $5/$25 per MTok. **OpenAI raised its 2030 infra budget to ~$750B** and named its next flagship data-center campus (Project Camellia, Georgia). And **Amazon shut down its AGI Lab and laid off frontier-model staff** — the clearest concession yet that the sustainable frontier is a three-lab market (Anthropic + OpenAI + Google), with everyone else pivoting to distribution and integration. Frame: *the frontier consolidated, and the workhorse-tier bar moved.*

Tags: `#labs #anthropic #claude-opus-5 #openai #ipo #capex #amazon #agi-lab #google #gemini #sap #frontier`

---

## 1. Claude Opus 5 ships — 1M context, effort toggle, Opus 4.8 pricing held flat {#1-opus-5}

**What happened:** Anthropic released **Claude Opus 5** on **2026-07-24** as the new flagship in the Opus tier — the workhorse below Fable 5. Model ID `claude-opus-5`. Concrete deltas:

- **Native 1M-token context window** in the API (all tiers), matching what Sonnet 5 got at GA on 2026-06-30.
- **Per-request effort toggle** — `low` / `medium` / `high` — trades reasoning depth for latency and cost inside a single API call. The knob a cost-aware agent team can actually pull per subtask.
- **Benchmarks (Anthropic's own, worth taking with a grain of salt but directionally):** **96.0% SWE-bench Verified**, 79.2% SWE-bench Pro, 43.3% Frontier-Bench (reported to edge GPT-5.6 Sol and Anthropic's own Fable 5), **70.57% OSWorld 2.0**, 30.2% ARC-AGI 3 (roughly 4× GPT-5.6 Sol).
- **Pricing held at $5 in / $25 out per MTok — identical to Opus 4.8** and **half of Fable 5**. Two Opus generations in a row without a price hike.
- **Same-day surface expansion:** Amazon Bedrock, Google Cloud Vertex, Microsoft Foundry, claude.ai, Claude Code, and Cowork all get Opus 5 at launch; default model on Claude Max.
- **Developer platform bump the same week:** `agent-memory-2026-07-22` beta header (stable memory-list ordering), Python SDK 0.116.0, TS 0.110.0, Go 1.56.0, Java 2.48.0; Claude Code got subagent text streaming and background-agent reliability fixes.

**Sources:**
- [Anthropic — Introducing Claude Opus 5](https://www.anthropic.com/news/claude-opus-5) `[primary]`
- [MarkTechPost — Meet the New Claude Opus 5: Frontier-Class Agentic Coding and Computer Use at Unchanged Opus Pricing](https://www.marktechpost.com/2026/07/24/meet-the-new-claude-opus-5-frontier-class-agentic-coding-and-computer-use-at-unchanged-opus-pricing/) `[secondary]`
- [9to5Mac — Anthropic upgrades Claude with new Opus 5 model](https://9to5mac.com/2026/07/24/anthropic-upgrades-claude-with-new-opus-5-model-details-here/) `[secondary]`
- [Vellum — Claude Opus 5 Benchmarks Explained](https://www.vellum.ai/blog/claude-opus-5-benchmarks-explained) `[analysis]`
- [Releasebot — Claude Developer Platform Updates](https://releasebot.io/updates/anthropic/claude-developer-platform) `[secondary]`

### Why it matters to you

- **Job lens:** The single most on-thesis line to add to your resume/portfolio this week: *"Rebuilt the [demo] on Opus 5 with per-subtask `effort` routing — X% latency reduction, Y% cost reduction, same SWE-eval pass rate."* This is exactly the FDE/Applied AI Engineer skill Anthropic hires on ([`05` §2](./05-career-and-startup.md#2-fde-market)) — and it's now doable in an afternoon on the API you already have. Screenshot the per-effort cost log.
- **Startup lens:** Opus-tier pricing held two generations in a row while benchmarks jumped is a **gross-margin gift** for any "Claude-for-X" product — your COGS on the same workflow is roughly flat vs. Opus 4.8 with materially better quality. Founders who repriced in April on 4.8 economics should re-run their unit economics this weekend.
- **Insight:** The **effort toggle is the story**, not the benchmark bar. It shifts model routing from "which SKU do I call" to "which effort setting for which subtask, on the same SKU" — closer to compiler-level control than API-level. The teams that build cost logs *per effort level per subtask* over the next 60 days will out-margin teams that don't; this is a stealth commoditization of the model-router category that just launched a wave of startups.

→ Cross-link: [`03` §1 how to wire per-effort routing tonight](./03-practical-skills-and-tools.md#1-opus-5-effort) · [`05` §2 the FDE market that hires for exactly this](./05-career-and-startup.md#2-fde-market).

---

## 2. OpenAI: 2030 capex ballooned to $750B; Project Camellia is the first self-built campus {#2-openai-750b}

**What happened:** OpenAI **raised its 2030 infrastructure budget from ~$600B to ~$750B (+25%)** and named its anchor build:

- **Project Camellia:** ~$20B data-center campus, **1,400 acres**, Effingham County, GA (north of Savannah). Requires **3.2 GW** from Georgia Power between 2028–2032. Land acquired; build/operate partner in selection.
- **Model shift:** from leasing compute (Oracle / AWS / CoreWeave) to being the **"principal designer and developer"** of its own facilities — closer to a hyperscaler than a lab.
- **Financial backdrop:** the previously reported confidential S-1 (filed 2026-05-22) targets up to ~$1T at IPO. Enterprise now **>40% of revenue**; ~$2B/month run-rate; Goldman + Morgan Stanley on the deal.

**Sources:**
- [TechCrunch — OpenAI's AI spending spree has ballooned to $750B](https://techcrunch.com/2026/07/22/openais-ai-spending-spree-has-ballooned-to-750b/) `[secondary]`
- [Quartz — OpenAI plans $20B data center campus near Savannah](https://qz.com/openai-data-center-georgia-savannah-project-camellia-072226) `[secondary]`
- [Yahoo Finance — OpenAI raises planned AI infrastructure spending to $750B](https://finance.yahoo.com/technology/ai/articles/openai-raises-planned-ai-infrastructure-134830365.html) `[secondary]`
- [Business Model Analyst — OpenAI Now Spends Like a Utility. It's Valued Like Software](https://businessmodelanalyst.com/openai-750-billion-infrastructure-spending/) `[analysis]`

### Why it matters to you

- **Job lens:** OpenAI's org chart is quietly forking into a **software company + a utility**. The two hiring surfaces are diverging: (a) the classic FDE / research / product roles, and (b) an emerging **capacity planning · datacenter engineering · power procurement** cluster that's genuinely under-supplied. If you have any distributed-systems / infra flavor to your background, an OpenAI Infrastructure req in 2026–2027 is a less-crowded queue than research.
- **Startup lens:** "Spends like a utility, valued like software" is the crisp frame for the coming IPO risk story. For founders: any wedge that reduces frontier-lab compute demand (efficient inference, better caching, targeted small models, on-prem edge) has a $750B TAM tailwind — but so does anything that supplies the utility (power, cooling, interconnect, chip packaging). Pick a side of the seam explicitly.
- **Insight:** Anthropic's ~$47B ARR / ~$965B post-money vs. OpenAI's ~$24B ARR / ~$1T IPO target is an **asymmetric revenue-to-valuation gap**. Public markets will price this within months. Your equity-comp math (RSUs vs. private-co options) at either lab is about to become a real spreadsheet exercise — start it before the roadshow window closes visibility.

→ Cross-link: [`02` §1 the $10B Etched ASIC round is the counter-move](./02-new-emerging.md#1-etched) · [2026-05-22/01 §2 the S-1 filing itself](../2026-05-22/01-big-lab-moves.md#2-openai-s1).

---

## 3. Amazon shuts the AGI Lab — the frontier consolidates to three labs {#3-amazon-agi-lab}

**What happened:** **Amazon closed its AGI Lab** (stood up December 2024, "several dozen" researchers) as part of a broader RIF inside the AGI org on **2026-07-22 → 2026-07-24**.

- Cuts include **model customization and post-training** roles; VPs **Adeeb Shanaa** (AGI data services) and **Vishal Sharma** (AGI info) had reports impacted (per The Information).
- Follows two senior departures: **Rohit Prasad** (SVP over AGI) left end of 2025; **David Luan** (AGI Lab head) left February 2026.
- Part of ~**16,000 corporate cuts** announced earlier in 2026 (~30,000 total since October 2025).
- Strategic shift: away from frontier research toward **enterprise deployment** — pairs with the announced **$1B "embed AWS engineers with customers"** agentic-AI initiative.

**Sources:**
- [CNBC — Amazon lays off some employees in its AGI unit](https://www.cnbc.com/2026/07/22/amazon-lays-off-some-employees-in-its-agi-unit.html) `[secondary]`
- [The Information — Amazon Shuts AI Agent Research Lab In AGI Layoffs](https://www.theinformation.com/briefings/amazon-shuts-ai-agent-research-lab-agi-layoffs) `[secondary]`
- [The Next Web — Amazon shuts its AGI Lab in fresh AI layoffs](https://thenextweb.com/news/amazon-shuts-agi-lab-frontier-model-retreat-layoffs) `[secondary]`
- [GeekWire — Amazon cuts jobs in AGI group as it puts more focus on customer-facing AI](https://www.geekwire.com/2026/amazon-cuts-jobs-in-agi-group-as-it-puts-more-focus-on-customer-facing-ai/) `[secondary]`

### Why it matters to you

- **Job lens:** Two direct effects. (a) A wave of **experienced frontier-model researchers hits the market this week** — Anthropic, OpenAI, and DeepMind will absorb the strongest; smaller labs (xAI, Mistral, Cohere) will absorb the rest. Watch your LinkedIn for ex-AGI-Lab first-degree connections and reach out for coffee. (b) AWS is doubling down on **Bedrock-plus-integration-services** — meaning **Claude-on-Bedrock Solutions Architect** and **AWS Applied AI Engineer** roles get *more* leverage, not less, because Amazon is now betting the org on distribution rather than models. This is a friendly hire for your Anthropic-stack focus.
- **Startup lens:** "**Post-training-as-a-service**" got a lot harder as a startup wedge this week — an incumbent just conceded the market to Anthropic/OpenAI. Two safer post-training-adjacent plays remain: (a) **verified-reward domain fine-tunes** (see the [SLAI T-Rex pattern](./04-research-progress.md#5-slai-t-rex) for the recipe) with a symbolic verifier, and (b) **evals-as-a-service** aimed at the labs that survived.
- **Insight:** The **three-lab market** is now the operating assumption for capital allocation. Amazon's retreat + Meta's admission that its AI reorg "hasn't come to fruition" ([2026-05-22 tangent](../2026-05-22/01-big-lab-moves.md) context) + SAP's move to build Europe's frontier lab from an *acquisition* ([§4](#4-sap-prior-labs)), not from scratch, all say the same thing: **the barrier to entry became insurmountable somewhere in 2026**, and the sensible strategy for everyone outside the top three is to buy or partner. Price your career and founder bets accordingly.

→ Cross-link: [`05` §3 the ex-Amazon-AGI talent wave](./05-career-and-startup.md#3-meta-amazon-talent) · [`02` §1 Etched thesis on the other side of the same seam](./02-new-emerging.md#1-etched).

---

## 4. Google DeepMind: Gemini 3.6 Flash + 3.5 Flash-Lite + Cyber — but no 3.5 Pro {#4-gemini-flash}

**What happened:** On **2026-07-21**, Google DeepMind released three new Gemini models — none of them the flagship Pro:

- **Gemini 3.6 Flash** — the new workhorse; Google claims **~17% fewer tokens** for the same task vs. 3.5 Flash.
- **Gemini 3.5 Flash-Lite** — cheapest tier, aimed at high-volume/low-margin inference.
- **Gemini 3.5 Flash Cyber** — **fine-tuned for cyber-vulnerability finding and remediation**; limited-access pilot, government and trusted partners only.
- Product lead **Logan Kilpatrick** said **3.5 Pro is testing with partners** and "hopes to land soon"; the team has started **its "most ambitious pre-training run yet"** for Gemini 4.
- Ambient context: the Gemini app crossed ~**900M MAU** at I/O 2026; Apple picked a custom **1.2T-parameter Gemini** to power the rebuilt Siri in iOS 27 (~$1B/yr deal).

**Sources:**
- [TechCrunch — Google releases three new Gemini models — but no 3.5 Pro](https://techcrunch.com/2026/07/21/google-releases-three-new-gemini-models-but-no-3-5-pro/) `[secondary]`
- [TUN — Google DeepMind Launches Gemini 3.6 Flash and Two New Models](https://www.tun.com/home/google-deepmind-launches-gemini-3-6-flash-and-two-new-models/) `[secondary]`
- [Stan Ventures — The State Of Google Gemini July 2026](https://www.stanventures.com/news/state-of-google-gemini-july-2026-7431/) `[analysis]`
- [Google DeepMind Blog](https://deepmind.google/blog/) `[primary]`

### Why it matters to you

- **Job lens:** A **cyber-specialty frontier variant** shipping to governments is a hiring signal — expect Google DeepMind's **security / red-team / trust & safety** roles to expand in Q3–Q4 2026, and expect similar variants (legal, medical, industrial) to spawn adjacent teams at Anthropic and OpenAI. If security-adjacent AI work interests you at all, this is the moment to add "vertical fine-tune · gov-fit eval · abuse-model design" to your vocabulary.
- **Startup lens:** **Vertical LLM as a distribution channel** just got a lab-endorsed template. The wedge isn't "our model beats GPT" — it's "our model + our eval + our vertical distribution beats a general model for this narrow task, at a price the enterprise buyer can defend." SAP's Prior Labs bet ([§4](#4-sap-prior-labs)) applies the same thesis to tabular data.
- **Insight:** No new Pro + already pre-training Gemini 4 says Google is **in the trough between generations**. Anthropic's Opus 5 launch this week and OpenAI's GPT-5.6 GA earlier in July land against a soft Google Q3 — which is why Google is leaning into **product surface** (Cyber, Flash-Lite, the Apple deal) rather than a headline benchmark. Read the Flash-Lite pricing when it lands; it will set the floor for anyone else's cheap-inference SKU.

---

## 5. SAP × Prior Labs — Europe builds a frontier lab by acquisition, not from scratch {#4-sap-prior-labs}

**What happened:** Week of **2026-07-20**, **SAP closed its acquisition of Prior Labs** — the German research group behind the **TabPFN** family of tabular foundation models — and committed **>€1B over four years** to build Prior Labs into a European frontier lab.

- Thesis: the largest untapped enterprise AI opportunity is **structured / tabular data in business databases**, not more general-purpose LLMs.
- Positioning: Europe's answer to the three-lab US market — SAP + Mistral + Prior Labs stack.
- Caveat: could not fully verify the €1B number from a first-party SAP press release in this pass; two secondary trackers report it consistently. Treat spend figures as `[secondary]` pending IR confirmation.

**Sources:**
- [BuildFastWithAI — AI News Today July 20 2026: 16 Biggest Stories](https://www.buildfastwithai.com/blogs/ai-news-today-july-20-2026-16-biggest-stories) `[secondary]`
- [Cheatsheets — Frontier AI Labs List: Companies, Models & Strategy (2026)](https://cheatsheets.davidveksler.com/ai-frontier.html) `[analysis]`

### Why it matters to you

- **Job lens:** Berlin / Munich / Walldorf becomes a real destination for research-adjacent work. If you're open to Europe, this is the newest hiring surface (and one with less applicant density than the US labs). Prior Labs' TabPFN direction rewards ML backgrounds heavier on statistics than on transformer scaling.
- **Startup lens:** **Tabular foundation models on enterprise databases** is an unclaimed adjacent wedge — most enterprise data is structured, and Claude-on-Bedrock isn't optimized for it. A "MCP server + TabPFN-style small model" packaging for a vertical (financial ops, supply chain, HR analytics) is a defensible founder bet the incumbents are unlikely to attack head-on.
- **Insight:** Every incumbent that "builds" a frontier lab in 2026 is doing it by **acquisition** (SAP → Prior Labs) or **carve-out** (see Amazon's retreat in §3). Organic frontier lab creation is closed. Founders working near frontier capability should optimize for **acquirable at ≤$500M** as a plausible exit alongside IPO.

→ Cross-link: [`02` §5 SLAI T-Rex is a Chinese-stack echo of the same pattern](./02-new-emerging.md).
