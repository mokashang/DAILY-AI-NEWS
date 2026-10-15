# Big Lab Moves — 2026-07-20

The frame this week: **talent is what re-priced.** Anthropic captured a Nobel laureate + 3 senior DeepMinders (Jumper, Adler, Pritzel); OpenAI captured Noam Shazeer; **Google took the loss and ≈$225–270B off Alphabet's market cap** across two sessions. In the same window Google **missed its widely-reported July 17 GA target for Gemini 3.5 Pro** — Vertex enterprise preview only, August window now the assumption. OpenAI is 11 days into **GPT-5.6 (Sol / Terra / Luna) general availability** — the first US frontier release cleared by the federal CAISI pre-deployment-review process. Anthropic's **Opus 4.7** is the new enterprise default, with a **10.9-pt SWE-bench Pro jump** and — quietly — a **new tokenizer that produces ~30% more tokens per identical prompt**, re-pricing every Claude Code bill in the wild. **Read this all as one story: the frontier's leverage is talent, and the talent market moved.**

Tags: `#labs #anthropic #openai #google #deepmind #meta #talent #opus #gpt-5-6 #gemini #pricing`

---

## 1. DeepMind talent exodus: Nobel laureate + 3 more to Anthropic; Shazeer to OpenAI {#1-deepmind-exodus}

**What happened:** In a single stretch of trading sessions, Google DeepMind lost:

- **John Jumper** → **Anthropic**. Jumper shared the **2024 Nobel Prize in Chemistry** with Demis Hassabis for AlphaFold; his hire is the single loudest scientific-agent talent signal of 2026.
- **Jonas Adler** → **Anthropic**. Reportedly worked on **Google's AI coding efforts** — a direct competitive transfer.
- **Alexander Pritzel** → **Anthropic**. Involved in **pretraining** — pairs with the **Karpathy pretraining hire** flagged on [2026-05-22/01 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy). The recursive-self-improvement bench is now materially deeper.
- **Noam Shazeer** → **OpenAI**. Co-author of **"Attention Is All You Need"** (2017 transformer paper); Google had paid **~$2B** to acquire him via the Character.ai team.

Market reaction: Alphabet's market cap swung roughly **$225–270B across two trading sessions** — the most concentrated talent-driven repricing of a Big-Tech name in 2026.

Employees at DeepMind, on background, describe the environment as **"bureaucratic, sometimes bordering on sclerotic, and highly risk-averse."** A specific trigger reportedly cited: **Google reassigned compute capacity from one of Shazeer's projects to another team**, and resource allocation became a source of tension as teams competed for limited advanced chips.

**Sources:**
- [Fortune — As top talent leaves Google DeepMind, some question if the lab can remain at the forefront of AI development](https://fortune.com/2026/06/23/google-deepmind-ai-researcher-departures-raise-doubts-about-ability-to-win-the-ai-race-shazeer-jumper-eye-on-ai/) `[secondary]`
- [Axios — Google takes the hit in AI's talent war](https://www.axios.com/2026/06/23/ai-lab-agi-google-deepmind-departures) `[secondary]`
- [The Rundown AI — Google's Nobel winner jumps to Anthropic](https://www.therundown.ai/p/google-s-nobel-winner-jumps-to-anthropic) `[aggregator]`
- [Crypto Briefing — Anthropic recruits two more key Gemini researchers from Google](https://cryptobriefing.com/google-ai-researchers-anthropic-talent-exodus/) `[secondary]`
- [Search Engine Journal — Google Loses Two Top AI Researchers To OpenAI & Anthropic](https://www.searchenginejournal.com/google-loses-two-top-ai-researchers-to-openai-anthropic/580201/) `[secondary]`
- [Taipei Times — Nobel Prize AI researcher leaves Google to Anthropic](https://www.taipeitimes.com/News/biz/archives/2026/06/22/2003859496) `[secondary]`
- [The Agent Report — Google Gemini 3.5 Pro Delayed to July 2026: $225B Wiped Off Alphabet as DeepMind Talent Exodus Deepens](https://the-agent-report.com/2026/07/google-gemini-3-5-pro-delayed-july-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** This is the **loudest possible validation** of the [ME.md](../ME.md) Anthropic-focusing decision. When a Nobel laureate + the co-inventor of the training loop underlying every LLM you use both leave Google in the same week — one to Anthropic, one to OpenAI — the talent market is telling you where the *interesting work* is priced. Anchor cover letters and interviews to the **specific Anthropic hire that maps to your target role**: Solutions / Integration / FDE (cite Karpathy's *use Claude to accelerate Claude* mandate + Jumper's *scientific-agent* implication as evidence that the platform is deepening, not commoditizing). Do NOT write "Anthropic is hot right now" — write "the pretraining-automation team Karpathy joined now shares a hallway with Jumper's protein-structure lineage; that's an *agent-for-science* stack forming in real time."
- **Startup lens:** Three of the four hires are **research-adjacent, not product-adjacent** — this points at a **scientific-agent** wave (protein/materials/biotech) as Anthropic's next distribution surface, on top of the Isomorphic-Labs template ([2026-05-19/02](../2026-05-19/02-new-emerging.md)). The picks-and-shovels wedge: **domain-specific eval harnesses + verifiers for scientific workflows** (protein, chemistry, materials, drug-discovery). If you're building on Claude, the *scientific-agent* readme story now signals real understanding of Anthropic's roadmap.
- **Insight:** The **compute-allocation-fight backstory** is the enduring lesson. Frontier talent is now mobile because **compute is the constraint**, and whichever lab makes researchers feel they can *run the experiment they want* wins the recruiting fight. This is why Anthropic's **$1.25B/month Colossus contract** ([2026-05-21/01 §2](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus)) and Meta's **Prometheus 3GW build** ([§4](#4-meta-prometheus)) matter *for hiring*, not just for training runs.

→ Cross-link: [`05` §1 talent-exodus as a career signal](./05-career-and-startup.md#1-ai-engineer-market) · [2026-05-22/01 §3 Karpathy → Anthropic pretraining](../2026-05-22/01-big-lab-moves.md#3-karpathy)

---

## 2. Gemini 3.5 Pro missed the July 17 GA target — August window now the assumption {#2-gemini-35-pro-slip}

**What happened:** Google DeepMind was widely reported to be targeting **July 17, 2026 for Gemini 3.5 Pro general availability**, following a **complete architectural rebuild** — engineers reportedly scrapped the original 2.5 Pro path after finding **structural failures in recursive tool-calling and SVG generation.** July 17 came and went with **no public release**, no model card, no pricing post. As of today, Pro sits in **limited Vertex AI enterprise preview**, and downstream reporting has shifted the assumed window to **August**.

Reported (but **unconfirmed**) specifications circulating in third-party coverage:

- **2M-token context window** — would be the largest in a production frontier model, ~2× Claude Opus 4.7 (1M — see [§4](#4-opus-47-default)).
- **Deep Think reasoning layer** — extended, deliberate reasoning path for the hardest problems (Google's answer to Anthropic's `xhigh` effort setting).
- Companion models: **Nano Banana Pro** (image gen) and **Gemini 4 Flash** (speed tier).

**Gemini Flash** (the previously-shipped tier) *did* land benchmark numbers Google itself confirmed: **76.2% on Terminal-Bench 2** — solid, but priced against a Sol/Opus-4.7 pair that has moved.

**Sources:**
- [TechTimes — Gemini 3.5 Pro Targets July 17 After Full Rebuild: Every Spec Remains Unconfirmed](https://www.techtimes.com/articles/320308/20260713/gemini-35-pro-targets-july-17-after-full-rebuild-every-spec-remains-unconfirmed.htm) `[secondary]`
- [BigGo Finance — Google Delays Gemini 3.5 Pro Launch to July 17 for Full Architectural Rebuild](https://finance.biggo.com/news/6f0c6bb2-795f-4c57-9d09-6db691d7638a) `[secondary]`
- [Enterprise DNA — Gemini 3.5 Pro: July 17 Launch After Google's Full Rebuild](https://enterprisedna.co/resources/news/gemini-35-pro-july-17-rebuild-vs-deepseek-v4-2026/) `[analysis]`
- [Memeburn — Gemini 3.5 Pro Targets July 17 With 2M Token Context](https://memeburn.com/gemini-3-5-pro-targets-july-17-with-2m-token-context/) `[secondary]`
- [Central Jersey — Google Gemini 3.5 Pro: What to Expect From Today's Big AI Launch (July 17)](https://centraljersey.com/2026/07/17/google-gemini-3-5-pro-launch-what-to-expect/) `[secondary]`

### Why it matters to you

- **Job lens:** Do not put "Vertex AI 3.5 Pro" on your résumé until Google ships a model card. This is the second Google slip of 2026 (see also the [Gemini 4 rename → 3.5 correction on 2026-05-19](../2026-05-19/01-big-lab-moves.md)) — the pattern is real, and hiring managers know it. **Reallocate the "Gemini bring-up" hours you had budgeted this week into a GPT-5.6 tier comparison** ([§3](#3-gpt-56-ga)) or into **Opus 4.7 telemetry against the new tokenizer** ([§4](#4-opus-47-default)) — both ship interview material *this week*.
- **Startup lens:** A missed frontier-model launch pushes **enterprise buying decisions to the two shipped incumbents** (OpenAI + Anthropic). If you're building on top of Gemini, the switching-cost math just got worse; if you're a Claude-first or GPT-first shop, this is a **customer-conversion window** — pitch "we run on the two GA'd frontiers" as a reliability differentiator.
- **Insight:** Talent exodus + missed launch is not coincidence — the *same compute-allocation dysfunction* [§1](#1-deepmind-exodus) surfaces at ship time. The durable read: **frontier velocity in 2026 is a function of talent × decision-making speed, not raw compute.** Google has the compute; it's losing on both other axes.

→ Cross-link: [`03` §2 the 3-provider router](./03-practical-skills-and-tools.md#2-provider-router) · [2026-05-20/03 §1 the I/O comparison table format](../2026-05-20/03-practical-skills-and-tools.md#1-comparison-table)

---

## 3. OpenAI GPT-5.6 (Sol / Terra / Luna) at day 11 of general availability {#3-gpt-56-ga}

**What happened:** **GPT-5.6 became broadly available on July 9, 2026**, after a **June 26 limited preview** to ~20 government-approved partner organizations. Three tiers:

- **GPT-5.6 Sol** — top-tier for complex reasoning, extended coding sessions, agent-driven workflows, security-focused applications. **$5.00 / $30.00 per 1M input/output.**
- **GPT-5.6 Terra** — "competitive performance to GPT-5.5 while being **2× cheaper**." The middle-of-the-market cost/quality point.
- **GPT-5.6 Luna** — speed / cost floor. The tier you route to for high-volume classification, extraction, first-pass triage.

**Companion product:** **ChatGPT Work** — an agent (built on Sol) that "carries out whole jobs rather than merely answering questions." Turns scattered notes and drafts into finished work; positioned directly at the FDE/Integration-Engineer buyer.

**The policy backdrop is the news.** The staggered rollout followed **Trump's executive order of June 2, 2026**, which directed federal agencies to build a **capability-benchmarking process** for new frontier models. The **US Commerce Department's Center for AI Standards and Innovation (CAISI)** completed its review and cleared wider access before the July 9 broad launch. **GPT-5.6 is the first US frontier model release cleared by federal pre-deployment review** — the process I flagged on [2026-05-21/01 §1](../2026-05-21/01-big-lab-moves.md#1-trump-eo) as "the pre-deployment-eval career lane" is now shipping.

**Sources:**
- [VentureBeat — OpenAI unveils GPT-5.6 Sol, Terra and Luna models — but only accessible to limited preview partners for now, per US Gov](https://venturebeat.com/technology/openai-unveils-gpt-5-6-sol-terra-and-luna-models-but-only-accessible-to-limited-preview-partners-for-now-per-us-gov) `[secondary]`
- [OpenAI — Previewing GPT-5.6 Sol: a next-generation model](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [OpenAI Help Center — A preview of GPT-5.6 Sol, Terra and Luna](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) `[primary]`
- [SpaceDaily — On July 9, 2026, OpenAI opened its most powerful system yet to the public — GPT-5.6 in three tiers named Sol, Terra and Luna — alongside an agent it calls ChatGPT Work](https://spacedaily.com/m-on-july-9-2026-openai-opened-its-most-powerful-system-yet-to-the-public-gpt-5-6-in-three-tiers-named-sol-terra-and-luna-alongside-an-agent-it-calls-chatgpt-work-built-to-carry/) `[secondary]`
- [Axios — OpenAI releases GPT-5.6 and ChatGPT Work tool](https://www.axios.com/2026/07/09/ai-openai-gpt-release) `[secondary]`
- [ExplainX — GPT-5.6 Sol, Terra, Luna rolling out in ChatGPT, Codex, and API](https://www.explainx.ai/blog/when-will-gpt-5-6-sol-terra-luna-be-available-everyone-2026) `[analysis]`

### Why it matters to you

- **Job lens:** **ChatGPT Work is a direct FDE / Integration-Engineer buyer signal.** OpenAI is not selling API tokens with this product — it's selling *finished work*. Anthropic's Solutions/FDE roles ([2026-05-19/05 §2](../2026-05-19/05-career-and-startup.md#2-openai-deployment-co)) and OpenAI's own Deployment Company + Tomoro ([same]) are the counter-hires. **The specific skill to lead with in interviews now: "I can define, price, and instrument a finished-work-unit outcome"** — that's what Sol + ChatGPT Work makes teachable in production.
- **Startup lens:** The **Terra tier (~2× cheaper than GPT-5.5 at competitive quality)** is the new default for any GPT-first product's *high-volume* path. Re-price your COGS this week. Also: with Sol at **$30/M output**, the **cost gap vs. Opus 4.7 at $25/M output narrowed sharply** — pick your model by *coding depth* (Opus 4.7 SWE-bench Pro 64.3, [§4](#4-opus-47-default)) or *tool orchestration* (Sol + ChatGPT Work), not by list price.
- **Insight:** **The CAISI-cleared release is the more important story.** In 8 weeks the "pre-deployment-eval / AI-assurance" lane went from *drafted-but-postponed* ([2026-05-22/01 §1](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)) to *the process a shipped model just went through*. Add **"CAISI pre-deployment review"** and **"capability-benchmarking pack"** to your skills vocabulary; add **bank AI-risk, insurance AI-risk, and government AI-assurance teams** to your apply list (the hiring wave is now real, not projected).

→ Cross-link: [`05` §2 the AI-assurance lane, live version](./05-career-and-startup.md#2-caisi-lane) · [2026-05-22/01 §1 EO as originally drafted](../2026-05-22/01-big-lab-moves.md#1-eo-postponed)

---

## 4. Anthropic Opus 4.7 is the new enterprise default — with a 30% tokenizer surprise {#4-opus-47-default}

**What happened:** **Claude Opus 4.7** — released **April 16, 2026** — is now the enterprise-default Opus tier across GitHub Copilot, Vertex Model Garden, Bedrock, and Anthropic's own API. The July usage picture:

**Benchmarks (vs prior Opus 4.6):**
- **SWE-bench Pro: 53.4 → 64.3** (+10.9 pts, single version bump)
- **SWE-bench Verified: 80.8 → 87.6** (+6.8 pts)
- **GDPVal-AA (knowledge-work Elo): 1,753** — vs GPT-5.4 **1,674**, Gemini 3.1 Pro **1,314**
- **Regression: BrowseComp dropped 4.4 pts** (worth logging if you have a browser-agent path)

**New capabilities:**
- **`xhigh` effort setting** — deeper reasoning path; peers with GPT-5.6 Sol's hardest-problems mode
- **Task budgets** — control agent spending at the prompt level (the primitive the June-15 Agent SDK metering forced)
- **Improved instruction-following** — executes prompts more literally; the "address all notes, don't implement yet" loop from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) works better
- **Vision to 2,576 px** on the long edge (~3.75 MP; 3× prior Claude resolution)

**Pricing — unchanged at $5/$25 per 1M input/output. But:** Opus 4.7's **new tokenizer produces ~30% more tokens per identical text** vs Opus 4.6. **A prompt that cost $0.50 on 4.6 now costs ~$0.65.** This has not been widely surfaced in coverage — it's the single most important line to catch in this edition.

**Sources:**
- [Anthropic — Introducing Claude Opus 4.7](https://www.anthropic.com/news/claude-opus-4-7) `[primary]`
- [Vellum — Claude Opus 4.7 Benchmarks Explained](https://www.vellum.ai/blog/claude-opus-4-7-benchmarks-explained) `[analysis]`
- [BuildFastWithAI — Claude Opus 4.7: Full Review, Benchmarks & Features (2026)](https://www.buildfastwithai.com/blogs/claude-opus-4-7-review-benchmarks-2026) `[analysis]`
- [GitHub Changelog — Claude Opus 4.7 is generally available](https://github.blog/changelog/2026-04-16-claude-opus-4-7-is-generally-available/) `[primary]`
- [BoringBot — Claude Opus 4.7 results: early benchmarks, real-world feedback, and is it worth upgrading?](https://boringbot.substack.com/p/claude-opus-47-results-early-benchmarks) `[analysis]`
- [AI/ML API Blog — Opus 4.7 Review: Features, Performance & How to Use It (2026 Guide)](https://aimlapi.com/blog/opus-4-7-review-features-performance-how-to-use-it-2026-guide) `[analysis]`

Adjacent product launches from Anthropic this month (see [Anthropic News](https://www.anthropic.com/news) `[primary]`):
- **Claude Design** (Anthropic Labs) — collaborate to produce visual outputs (designs, prototypes, slides, one-pagers). Direct competitor to Figma AI + Canva Magic Studio.
- **Claude for Teachers** — free premium access for verified US K-12 educators; curriculum standards for all 50 states. **The 6th distinct distribution channel Anthropic has stood up in 90 days.**
- **Claude Reflect** — monthly recap, focus/break settings, quiet hours, work insights.
- **Memory updates** — individual categorized entries replace daily-summary memory model; richer conversation context.
- **Claude Code stability update** — tighter permission checks, safer Bash/PowerShell handling, `EndConversation` tool, progress heartbeats for long-running tasks. **This is the tell that Anthropic is treating Claude Code as production infrastructure**, not a dev-preview toy.
- **Enterprise Admin API (beta)** — list members, change roles, remove, manage groups.

### Why it matters to you

- **Job lens:** **The SWE-bench Pro number is what you cite in interviews.** "Opus 4.7 hit 64.3 on SWE-bench Pro; the +10.9 jump in one bump is the largest single-version SWE-bench delta Anthropic has posted" — pairs perfectly with "I orchestrate an Opus-4.7-planner + Sonnet-4.6-worker team to cut cost 40%" ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)). The GDPVal-AA lead (1,753 vs GPT-5.4 1,674) is the sharper *knowledge-work* pitch for FDE / Solutions roles.
- **Startup lens:** **Task budgets are the primitive to build on.** Any Claude-first product now has a *first-class* way to cap per-user or per-tenant spend — the "outcome-priced product on a token-priced model" gap just narrowed. Also: **the 6th distribution channel (Teachers) tells you Anthropic's playbook — pick a vertical, ship a bundle, use free/heavily-subsidized access as the wedge, monetize on the API tail.** If you're building for K-12, the on-ramp just got competitive.
- **Insight:** The **tokenizer change is the sleeper story.** Every Claude Code user is now paying more per prompt without being told. **This is the customer-discovery opening for a cost-audit / model-router startup** (see [STARTUPS.md](../STARTUPS.md)) — build a 20-line audit script, run it against your own bill, publish the delta, DM 5 Claude-Code-heavy engineers you know. The pain is real, the fix is small, and the artifact answers "can you find and explain a real production issue?" in a way that no résumé bullet can.

→ Cross-link: [`03` §3 the tokenizer audit playbook](./03-practical-skills-and-tools.md#3-tokenizer-cost) · [2026-05-16/01 §1 the Agent SDK metering change](../2026-05-16/01-big-lab-moves.md)

---

## 5. Meta Superintelligence Labs — Prometheus 1GW → 3GW, ~3,000 engineers on RL {#5-meta-prometheus}

**What happened:** SemiAnalysis and Meta's own AI blog have surfaced the **Meta Superintelligence Labs (MSL) 12-month progress picture**, and the two numbers you should hold in your head:

- **Prometheus** — Meta's flagship AI cluster, partially operational already — is on a path from an initial **~1 GW to >3 GW within two years**, using a **"scrappy tent datacenter design"** (Meta's answer to the timeline math of conventional builds). The 2026 tokenomics model projects **Meta will have more AI compute than OpenAI and Anthropic combined by year-end.**
- **The "applied AI engineering org"** (announced late May) now has **~3,000 engineers full-time on RL tasks and environments** — including **70% of new grads plus a significant number of seniors**. This is the *personnel* side of the reallocation flagged in [2026-05-20/01 §5](../2026-05-20/01-big-lab-moves.md#5-meta-cut) (the 8K-person cut with ~7K redirects).

Combined with the **~$14.3B Scale AI acqui-hire** for Alexandr Wang + the SEAL team and multi-hundred-million-dollar packages for top researchers, MSL's spend line is the biggest single AI-infrastructure bet outside of the sovereign programs.

**Sources:**
- [SemiAnalysis — The Future of Meta Superintelligence: A 1-Year Progress Update](https://newsletter.semianalysis.com/p/the-future-of-meta-superintelligence) `[analysis]`
- [Wikipedia — Meta Superintelligence Labs](https://en.wikipedia.org/wiki/Meta_Superintelligence_Labs) `[secondary]`
- [Built In — Meta Superintelligence Labs: What We Know So Far](https://builtin.com/artificial-intelligence/meta-superintelligence-labs) `[analysis]`
- [Constellation Research — Meta Superintelligence Labs: A look of the challenges ahead](https://www.constellationr.com/insights/news/meta-superintelligence-labs-look-challenges-ahead) `[analysis]`
- [AI at Meta Blog](https://ai.meta.com/blog/) `[primary]`

### Why it matters to you

- **Job lens:** **The ~3,000-engineer "RL tasks/environments" org is the largest single AI-engineering hiring target open to new grads right now** — 70% of that headcount is new-grad by Meta's own disclosure. The lane isn't "research"; it's **RL-environment engineering** (task design, reward specification, evaluator wiring, distributed rollouts). Rewrite your resume to highlight any coursework or side project touching **environment design, reward shaping, rollout collection, or evaluator scoring** — that's the exact vocabulary of the posted JDs.
- **Startup lens:** Meta's tent-design gambit tells you **energy-adjacent AI infra remains under-priced**. The **GridCARE thread** ([2026-05-16/02](../2026-05-16/02-new-emerging.md)) and the *data-center-siting / permitting / power-broker* wedge only got hotter. The Meta signal is that even the biggest incumbents can't buy their way out of the multi-year power-and-permitting bottleneck; picks-and-shovels vendors that shorten that path have compounding TAM.
- **Insight:** Read Meta and Anthropic side by side. **Anthropic won this week's talent war; Meta is winning this year's compute war.** These are not the same race — they're two different bets on *what the binding constraint on model progress actually is.* Your read: **short-term (12 months), talent > compute** (recursive-self-improvement, agent design, verifier engineering). **Long-term (3+ years), compute > talent** (frontier scaling laws still bite). Plan your career for the *short-term* leverage (Anthropic-stack skill investment) and your investing/founding for the *long-term* infrastructure (energy, cooling, power-broker).

→ Cross-link: [`05` §3 the RL-environment engineer job spec](./05-career-and-startup.md#3-rl-env-engineer) · [2026-05-20/01 §5 Meta cut executing](../2026-05-20/01-big-lab-moves.md#5-meta-cut)
