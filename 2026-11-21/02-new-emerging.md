# New & Emerging — 2026-11-21

Three themes dominate the funding tape this week. **(1) Vertical AI agents at $1–1.5B Series B is now the dominant shape** — Model ML's $250M at $1.5B after 18 months is the template. **(2) Physical AI is raising on revenue multiples, not hype** — BrightAI at $750M is a $80M-rev bootstrapped company taking in strategic money. **(3) Consumer AI search & customer-support agents keep marking up** — Perplexity crosses $1B ARR; Decagon in talks at $4–5B. Underneath, **the Chinese open-weight stack dominates Hugging Face trending** (Qwen family = 7 of top 20); Meta's **Muse Ember** fills the lightweight/routing tier; no major Western open-weight frontier drop this week.

Tags: `#startups #funding #agents #physical-ai #open-source`

---

## 1. Model ML raises $250M Series B at $1.5B — vertical-agent template, 18 months out of stealth {#1-model-ml}

**What happened (2026-11-17):**
- **General Atlantic + QED** co-lead a **$250M Series B at a $1.5B valuation**.
- Target users: **investment bankers, management consultants, institutional investors**. Agents handle model-building, pitch-deck drafting, and portfolio screening — the kind of 20-hr/week manual work that already has a budget line.
- **ARR 12× YoY** (specific ARR undisclosed; implied $40–80M range per usual multiples in the segment).
- Only **18 months out of stealth**; total raised **~$350M**. Headquartered in London.

**Sources:**
- [FinTech Futures — Model ML $250M at $1.5B](https://www.fintechfutures.com/venture-capital-funding/model-ml-250m-series-b-funding-round-1-5bn-valuation) `[secondary]`
- [tech.eu — Model ML hits $1.5B valuation](https://tech.eu/2026/11/17/model-ml-hits-15b-valuation-with-250m-raise-just-18-months-after-emerging-from-stealth/) `[secondary]`

### Why it matters to you

- **Job lens:** Model ML's hiring page will open 10–20 senior FDE / forward-deployed solutions reqs in the next 60 days — this is the standard post-$250M-raise pattern. The role profile they'll pay a premium for: **"ex-banker or consultant who can code"** (SQL + Python + deck fluency + reading an income statement). If you're a CS grad who can **read a 10-K and script up a comparable-companies screen**, you are the target — apply directly to the CEO's inbox with a two-screenshot portfolio artifact (one data query, one deck slide) instead of the careers page.
- **Startup lens:** $1.5B Series B after 18 months at **~20× ARR** is the clean comp pattern for 2026 Q4 vertical agents. **For context, a16z's "Avoiding Death on the Yellow Brick Road" thesis is explicitly against general-connector wrapper startups** — Model ML works because the agents read bank-grade data and emit bank-grade output (regulatory audit-trail, data lineage, review workflow). That's the narrow moat replacement for "we built a chatbot." Pitch: **"vertical expertise in the eval loop, not just the prompt."**
- **Insight:** **The Series B at $1–1.5B is now the dominant AI shape — and it's also the sweet spot for founding-engineer joins.** You get comp close to frontier labs ($250–350K TC), an equity package that's still meaningful if the company doubles, and the kind of problem shape that teaches you how to ship. The next 3–6 Series B-sized rounds in this category will likely be: Decagon (talks $4–5B), Harvey (next up), Glean (Founding FDE reqs live), Sierra (same), Dust (EU equivalent).

→ Cross-link: [`05` §3 — FDE lane, Anthropic Head of FDE posting](./05-career-and-startup.md#3-fde-still-boom)

---

## 2. Physical AI pops: BrightAI $97M at $750M (Nov 18); Noeri launches with $110M (Nov 16) {#2-brightai-noeri}

**What happened (2026-11-16 → 2026-11-18):**
- **BrightAI** raised **$97M at $750M** (Smith Point Capital leads; **GE Vernova strategic**). Physical AI on critical infrastructure — pipelines, power lines, offshore rigs — with sensors, drones, and inspection bots that train and ship models on edge GPUs. **Bootstrapped to ~$80M in revenue** before this round. Total raised to date ~$184M. 1.9× step-up from the $51M Series A.
- **Noeri** launched Nov 16 with a **$110M seed/Series A**. Founders: **Yejin Choi (Stanford)** and **Carlos Guestrin (Stanford/formerly Apple VP ML)**. **Menlo Ventures leads**; NVIDIA, Madrona, NEA, Snowflake, Cisco in. Positioning: **"living AI systems" — agents that continue improving in production from user traces and feedback**, with a model-weight layer, memory layer, and self-eval layer that are versioned together. Valuation undisclosed.

**Sources:**
- [TheNextWeb — BrightAI $97M physical-AI infrastructure](https://thenextweb.com/news/brightai-97m-physical-ai-infrastructure-ge-vernova) `[secondary]`
- [AI Weekly — BrightAI $97M at $750M, Smith Point](https://aiweekly.co/alerts/brightai-raises-97m-at-750m-led-by-smith-point-capital) `[aggregator]`
- [SiliconANGLE — Noeri raises $110M for living AI systems](https://siliconangle.com/2026/11/16/noeri-raises-110m-to-help-companies-build-living-ai-systems-that-self-improve-over-time/) `[secondary]`
- [TheNextWeb — Noeri $110M Stanford Choi/Guestrin](https://thenextweb.com/news/noeri-110m-stanford-yejin-choi-carlos-guestrin-menlo-nvidia) `[secondary]`

### Why it matters to you

- **Job lens:** **BrightAI is the physical-AI FDE opportunity right now.** Imagine an FDE role where "customer" means a utility operator and the artifact you ship isn't a Figma mockup but a drone flight path + an edge-inference binary. Comp will anchor to **Anthropic/OpenAI FDE bands ($250–320K base) because it has to compete for the same talent pool**. If you have *any* embedded systems, controls, or field-robotics coursework, you have a route in that few CS grads can match. Apply directly, and pair the application with a 2-paragraph "day in the life" story of how you'd scope the first week of a utility deployment.
- **Startup lens:** **Noeri's "living systems" wedge is the sharpest new-category framing in weeks.** The pitch — that agents in production *should* be versioned together with their memory and their eval set, as a single evolving artifact — is a credible attack on today's "pick a model + prompt template" setup. **If you're pre-seed in agent-ops, your pitch deck now needs a one-slide answer to "how does Noeri eat us."** Expect VCs to ask that question in every meeting through December.
- **Insight:** **Physical AI is raising at 20–30× revenue, not 100–200× — that's the signal.** BrightAI's $750M / $80M = ~9× TTM, closer to a growth-software multiple than an "AI premium." Translation: **investors are now underwriting physical-AI startups on economic output, not narrative**. For founders: ship revenue first (even bootstrapped), raise less, retain more. For job seekers: companies in this category have real work and real money — and are less exposed to the Ramp-measured "spend-flat, volume-up" wrapper squeeze.

→ Cross-link: [`04` §1 — Gamer VLA](./04-research-progress.md#1-gamer-vla) · [`01` §2 — NVIDIA Rubin production](./01-big-lab-moves.md#2-nvidia-huang-out)

---

## 3. Perplexity crosses $1B ARR; Decagon in talks at $4–5B {#3-perplexity-decagon}

**What happened (2026-11-13 → 2026-11-19):**
- **Perplexity** crossed **$1B ARR** per the **Latent Space weekly** (Nov 16 recap). **4× YoY growth.** Nvidia–Perplexity $30B+ partnership talks from August still **unresolved**.
- **Decagon** reportedly **in talks to raise at a $4–5B valuation** (The Information, mid-Nov). Round **not closed**; terms, lead investor, and new-money amount not yet public.
- Context: Rox (AI sales agents) closed $100M at $1.3B on Nov 11; Sierra, Decagon, and Nooks have been collectively eating the "customer-support agent + sales-agent" category. The $4–5B mark would **re-anchor the whole category** upward.

**Sources:**
- [Latent Space — Perplexity hits $1B revenue run rate, up 4× in 2026](https://latent.space/p/ainews-perplexity-hits-a-1b-revenue-run-rate-up-4x-in-2026/) `[aggregator]`
- [The Information — Decagon talks $4B valuation](https://feature.theinformation.com/articles/customer-support-ai-startup-decagon-talks-raise-4-billion-valuation) `[paywall]`

### Why it matters to you

- **Job lens:** **Consumer AI search isn't dead** — Perplexity at $1B ARR is a hiring surface not every CS grad will aim at and most will overlook. Target team: **search ranking + answer quality + source citation**, which is a nicely interviewable surface (LLM-as-judge, factual-verification eval, ranking metrics). Decagon's roles will skew FDE — if the raise closes at $4–5B, expect comp bands to open ~10–15% versus Sierra/Rox posted ranges. The window is **apply in the ~3 weeks between round announcement and req-posting**, before the pipeline fills.
- **Startup lens:** **Decagon at $4–5B marks the "post-Sierra customer-support-agent" ceiling.** If you're building in this category, your two valid pivots are (a) **go down-market with SMB pricing and an AppSumo-style motion**, (b) **go sideways into a sibling vertical** — healthcare intake, legal client-intake, academic advising. The direct-attack strategy is closed; the flanking attacks are wide open.
- **Insight:** **Perplexity's 4× YoY growth at $1B ARR is a shot across Google's bow** that will provoke a response — likely in the form of Gemini's search integration going further than most expect in Q1 2027 (deeper SGE, per-query agents, more aggressive citation surfaces). **Prepare for the Gemini response the same way you'd prepare for a new compiler release**: check your prompts, your evals, and your ranking-dependent features against a Gemini-backed Perplexity-equivalent pattern.

→ Cross-link: [`01` §3 — Microsoft Agent Store](./01-big-lab-moves.md#3-microsoft-ignite) · [`05` §1 — Ramp Anthropic 49.3% share](./05-career-and-startup.md#1-ramp-nov)

---

## 4. Meta Muse Ember (Nov 9): the open-weight routing/tool-call tier gets a model {#4-muse-ember}

**What happened (2026-11-09):**
- Meta released **Muse Ember** — a **lightweight, open-weight model in the Muse family** targeting routing, tool-call dispatch, and short coding subtasks. Position: the "Claude Haiku / Fable-lite / Gemini Flash" tier.
- Pairs with the earlier **Muse Spark Open** (816B MoE / 42B active) frontier release.
- Still unconfirmed: **Muse Spark 1.2 weights** (promised but not published).
- **The Batch's reading:** Meta's Muse family now covers **frontier (Spark Open) + routing/tool tier (Ember)** — the first US open-weight family to formalize the two-tier pattern Anthropic/OpenAI/Google already ship in closed form.

**Sources:**
- [DeepLearning.AI The Batch — With Muse Spark, Meta pivots from open-weights Llama](https://www.deeplearning.ai/the-batch/with-muse-spark-meta-pivots-away-from-its-open-weights-llama-strategy) `[secondary]`

### Why it matters to you

- **Job lens:** **Muse Ember is the first open-weight model worth putting in a "I built a router" portfolio piece against Fable 5.2 + GPT-6.2.** Build: a 150-LoC router that dispatches between (a) Ember for simple tool calls, (b) Spark Open for long reasoning, (c) a frontier API for the hard tail — with a public eval showing cost vs accuracy. This is the **highest-leverage weekend artifact** you can ship right now; it reads as "FDE-ready" and "cost-aware MLE" simultaneously.
- **Startup lens:** **A credible US open-weight routing tier matters for any startup trying to avoid per-token API dependency.** If your margin is squeezed (and the Ramp Nov Index suggests it is), Ember + Spark Open on your own GPUs becomes the escape hatch. Pair it with fal/Baseten/Modal/Together inference and a careful eval harness — you can cut variable cost 60–80% on a majority of traffic.
- **Insight:** **Two-tier open-weight is the new standard.** Expect the next Kimi / GLM / Qwen family releases to formalize the same pattern (frontier + routing tier), and watch for whichever DeepSeek variant does it first.

→ Cross-link: [`03` §4 — SGLang 1.0 / inference stack](./03-practical-skills-and-tools.md#2-llamacpp-sglang)

---

## 5. Hugging Face trending snapshot (Nov 13): Chinese open-weight dominance holds {#5-hf-trending}

**What happened (week of 2026-11-13):**
- Hugging Face trending top 20 (Nov 13): **Qwen family = 7 slots** (variants of Qwen 3.8 Instruct, Qwen 3.8 Coder, Qwen VLM, Qwen-A3B, Qwen-Image).
- #1 trending: **DeepSeek-V4-Pro-Qwen3.5-9B-UNCENSORED-heretic** (community fine-tune pipeline — DeepSeek-V4-Pro as teacher, Qwen 3.5-9B as student, uncensoring protocol applied).
- No major new Chinese open-weight frontier drop confirmed in the Nov 17–20 window. **Kimi K3.1 Pro weights** were promised Nov 4 (prior edition) — **still not posted** as of this edition.
- **Western open-weight event** of the week was Meta Muse Ember (above); **Western frontier open-weight** gap vs Kimi K3 / GLM 5.3 / Qwen 3.8 continues.

**Sources:**
- [presenc.ai — Hugging Face trending snapshot Nov 2026](https://presenc.ai/research/huggingface-trending-models-november-2026) `[aggregator]`
- [Hugging Face Papers / Trending](https://huggingface.co/papers/trending) `[primary]`

### Why it matters to you

- **Job lens:** **"I distill a frontier model into a smaller one and publish the recipe"** is the current highest-signal open-source résumé artifact. The trending #1 is literally that. Pick a non-political task (code, math, scientific QA, SQL) and ship a **distillation + eval + README** in one weekend — then put the HF link at the top of your résumé. That reads as "MLE who ships" better than any coursework line.
- **Startup lens:** **Chinese open-weight dominance + visible community fine-tune activity = a stable alternative supply chain for non-US customers.** Any startup serving EU/APAC/LatAm can now credibly say "we don't depend on US API access" in enterprise sales. Build the on-prem deployment story around Qwen 3.8 Instruct + vLLM/SGLang, not around Llama.
- **Insight:** **The gap between "trending open fine-tunes" and "trending research papers" is widening.** The HF trending list is now its own genre — a community coding cadence that trains, fine-tunes, and re-mixes faster than labs can publish base models. If you want to be part of it, watch the top 50 weekly and contribute one fine-tune or eval repo per month for 3 months.

→ Cross-link: [`04` §5 — WeMM-Video omni-modal](./04-research-progress.md#5-wemm-video)

---

## 6. Weekly funding totals and gaps {#6-funding-totals}

**What happened (week of 2026-11-14 → 2026-11-21):**
- **Nov 18** funding slice: **~$180M across 7 rounds**; BrightAI largest ($97M).
- **Nov 9–13** week: **~$6.0B across ~40 rounds** (AI Funding tracker).
- **Nov MTD**: **~$15.5B across 62 rounds**; largest single item is Thinking Machines Lab's reported **~$5B seed** (unconfirmed; see caveat).
- **Unconfirmed mega-raise:** CNBC Nov 12 cited **OpenAI $15B at $1.25T** — OpenAI itself has not announced. Treat as **[rumor]**.
- **No confirmed Nov 17 / Nov 19 / Nov 20 day-level rollups** surfaced in search (only Nov 18 had a dated slice this week).

**Sources:**
- [StartupHub — Startup funding roundup Nov 18 2026](https://www.startuphub.ai/ai-news/funding-roundup/2026/startup-funding-roundup-november-18-2026) `[aggregator]`
- [AI Funding — Weekly roundup Nov 9–13 2026](https://aifunding.me/insights/weekly-roundup-nov-9-13-2026) `[aggregator]`
- [AI Funding — November 2026 roundup](https://aifunding.me/roundups/november-2026) `[aggregator]`

### Why it matters to you

- **Job lens:** **The pace of new AI Series A/B rounds is the single best proxy for near-term hiring.** ~$15.5B in a month ≈ 150–250 companies with fresh runway hiring in the next 90 days. The highest-leverage move: **track AI Funding's weekly rollup every Sunday**, cold-email the CEOs of 3 companies that closed that week, offer a 2-hour paid audit of their agent stack or eval harness.
- **Startup lens:** **The absence of day-level rollups for Nov 17 / 19 / 20 doesn't mean no deals closed** — it means Thanksgiving-week discipline. Expect a Nov 24–26 and a Dec 1–5 cluster of rounds as deals postponed from this week clear.
- **Insight:** **Unconfirmed OpenAI $15B at $1.25T is a market thermometer — if it's real, it anchors every late-stage AI private comp above the ANT pricing.** Watch for either an OpenAI press release or an S-1-for-direct-listing filing in Q1 2027.

→ Cross-link: [`05` §4 — Comp bands and new-grad premium](./05-career-and-startup.md#4-comp-bands)
