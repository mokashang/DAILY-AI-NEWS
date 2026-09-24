# New & Emerging — 2026-09-24

Sora API dies today. Twelve Labs + Stability announce Series B rounds anchored by unusual strategic-investor cap tables (music labels + AAA gaming + chipmakers). The biology-AI subsector just got repriced upward by Anthropic's ART discovery. **Frame: rights-cleared data + vertical-domain wet-lab access + real video understanding are the three emerging moats where a Series A now anchors.**

Tags: `#video #startups #funding #video #rights #bio #api-deprecation #openai`

---

## 1. Sora API sunset — TODAY (Sept 24) {#1-sora-api-shutdown}

**What happened:** **OpenAI shuts down all Sora API endpoints (sora-2, sora-2-pro, all snapshots) today, September 24, 2026.** The consumer app + web experience were already discontinued on **April 26, 2026** — the API had a ~5-month grace period. Any videos you've already generated + downloaded remain yours; **content stored only on Sora's servers will be permanently deleted.**

**Why now (analyst read):** OpenAI is consolidating video-generation resources into the **Astra multimodal line** and the **hardware / agent products** shaped by the Jony Ive / io Products acquisition. The Sora shutdown is the first "official" retirement of a flagship generative-media product by a frontier lab — an important precedent for developer trust.

**Migration options for anyone with Sora-dependent code:**
- **Runway Gen-4** — most feature-parity, strongest editorial workflow
- **Kling 2.0** — best price/quality for short-form, Chinese lab
- **Google Veo 3** — deepest integration with Vertex + Gemini prompt-chain
- **Luma Dream Machine v3** — best for creative direction, weakest for tool-calling from an agent
- **Pika 2.5** — best low-cost per-second, weakest quality

**Sources:**
- [OpenAI Help Center — What to know about the Sora discontinuation](https://help.openai.com/en/articles/20001152-what-to-know-about-the-sora-discontinuation) `[primary]`
- [NewsBytes — Sora API shuts down September 24: What users should do](https://www.newsbytesapp.com/news/science/sora-api-shuts-down-september-24-what-users-should-do/story) `[secondary]`
- [Medium — OpenAI Is Shutting Down Sora. That Says More Than Most Product Launches](https://medium.com/codetodeploy/openai-is-shutting-down-sora-that-says-more-than-most-product-launches-05db8b07c136) `[analysis]`

### Why it matters to you

- **Job lens:** **"Model deprecation migration"** is a resume line hiring managers pattern-match on positively — because it signals you've maintained something in production long enough to see it break. If you have *any* Sora-adjacent project, write the migration up (even if you don't own production code — do the migration hypothetically as a weekend exercise and publish a "what I would have done" post). File under: portfolio artifact for AI Integration / FDE roles.
- **Startup lens:** **Video-gen developer surface just fragmented.** The wedge: **"video-gen abstraction layer"** that lets a developer switch providers with a config change (analogous to LiteLLM for text). Runway + Kling + Veo + Luma + Pika all have different APIs, price models, and quality trade-offs — an SDK that unifies them and adds a cost-router + eval-suite is a $2–8M ARR opportunity for a bootstrapped founder over 12 months.
- **Insight:** **Consumer + API sunsetting of a flagship product** is a shape we haven't seen before at a frontier lab. It signals **OpenAI's willingness to abandon a product with brand equity to reallocate compute** — a *behaviour*, not a strategy statement. Watch whether other labs follow: DeepMind's Imagen 4? Meta's Emu? A discontinuation cascade would compress the video-gen provider list from ~15 to ~5 by Q1 2027.

→ Cross-link: [`03` §1 three-tier routing rubric](./03-practical-skills-and-tools.md#1-three-tier-routing) (same pattern applies to video-gen providers).

---

## 2. Funding — Twelve Labs $100M Series B + Stability AI $76M with unusual anchors {#2-funding-round}

**What happened:**

**Twelve Labs — $100M Series B**, co-led by **New Enterprise Associates (NEA) + Naver Ventures.** San Francisco-based; builds AI systems trained on **video archives** — the "search / understand / index" primitive underneath every "search my video corpus" agent workflow. **This is the *video-understanding* wedge**, distinct from *video-generation* (Runway, Kling, Sora-successors). With Sora's API dying today, Twelve Labs' timing is impeccable — every video-workflow team now needs a stack, and Twelve Labs sits at the *inference-time indexing* layer.

**Stability AI — $76M Series B**, bringing total funding to **$232M**. Unusual cap-table anchors:
- **Universal Music Group** + **Sony Music Group** + **Warner Music Group** — the **big-three music labels**, historically Stability's litigation adversaries.
- **Electronic Arts** — AAA gaming publisher.
- **AMD Ventures** — chip vendor.
- **Pacific Alliance Ventures** — Asia-Pacific bridge capital.

**The music-label investment is the story.** Two years ago the labels sued open-source image / audio models over unlicensed training data; today they're on the cap table. Read: **rights-cleared training data is now the moat**, and the labels are choosing to own equity in the model layer rather than just license or sue.

**Sources:**
- [TechCrunch — Stability AI, maker of image generator Stable Diffusion, raises $76 million in fresh funding](https://techcrunch.com/2026/08/25/stability-ai-maker-of-image-generator-stable-diffusion-raises-76-million-in-fresh-funding/) `[secondary]`
- [Crunchbase News — The Week's 10 Biggest Funding Rounds: AI, Energy And Biotech Lead The Way](https://news.crunchbase.com/venture/biggest-funding-rounds-ai-energy-biotech-joulent/) `[secondary]`
- [AlleyWatch — The 15 Largest US Funding Rounds of August 2026](https://alleywatch.com/2026/09/us-startup-funding-top-largest-august-2026-vc/) `[aggregator]`

### Why it matters to you

- **Job lens:** **Video-understanding is a hot lane; Twelve Labs is hiring.** Roles that pattern-match: **Applied ML for video, Multimodal Model Engineer, Solutions Engineer — Video Workflows**. Compensation likely $180–250K base for mid-level (per broader AI-eng market — see [`05` §1](./05-career-and-startup.md#1-hiring-map)). Adjacent hires: **any music-label AI team** now staffing up post-Stability investment — Universal, Sony, Warner all have small ML groups that will double in size.
- **Startup lens:** Two founder-specific reads:
  - **The Twelve Labs $100M B validates *video-search-as-primitive*** — if you're building an agent workflow that touches video (education, healthcare imaging, security cameras, corporate archives, creator tools), the *right* infra decision now is "build on Twelve Labs, don't reinvent." Wedge: **verticalise Twelve Labs** — pick a domain (legal depositions, medical imaging, security investigation, real estate walkthroughs) and build the *domain-specific eval + workflow layer* on top of Twelve Labs' primitive. This is a $3–8M ARR wedge inside 18 months.
  - **The Stability music-label deal is the *rights-cleared data moat* thesis crystallising** — every generative-media startup now needs to answer "who owns your training data?" before Series A. Wedge: **rights-clearance-as-a-service for AI training data** — a compliance + provenance + royalty-attribution platform aimed at the next 100 generative-media startups. Adjacent: **licensing-marketplace for creators' opt-in data** (Getty already tried this; opportunity for a well-executed 2.0).
- **Insight:** **The labels + EA + AMD combination is a genuinely novel cap-table shape.** It says (a) generative-media requires rights-cleared data (labels), (b) *and* interactive-media distribution (games/EA), (c) *and* first-party compute access (AMD). This is a **three-way distribution moat**, not a valuation-multiple round — an increasingly common shape in 2026 (see the Isomorphic four-corner template from [2026-05-19](../2026-05-19/02-new-emerging.md)). Watch for other AI companies pursuing the same shape — a music-focused AI startup with Spotify + Universal + Nvidia on the cap table would be an obvious next.

→ Cross-link: [`05` §1 hiring map](./05-career-and-startup.md#1-hiring-map).

---

## 3. Biology-AI subsector repriced upward by the ART discovery {#3-bio-ai-repriced}

**What happened (second-order effect of [`01` §3](./01-big-lab-moves.md#3-anthropic-biolab)):** Anthropic's autonomous ART discovery is a **capability demonstration** that reprices the biology-AI subsector — because it demonstrates that a *general* model + agent orchestration can produce *original* biological discoveries, not just refinements of known space.

**Companies whose valuation model / recruiting posture should tighten this week:**

- **Isomorphic Labs** — Alphabet subsidiary, drug design. Already at $2.6B [total capital](../2026-05-18/02-new-emerging.md#3-isomorphic). ART result validates the "AI can find *new* things in biology" thesis on which Isomorphic's next round will be priced. Watch for a Q4 up-round.
- **Xaira Therapeutics** — Stephen Quake / ARCH Venture Partners, ~$1B seed round in 2024. Similar profile. **Highest chance of a "we did our own ART" moment in Q4 or Q1.**
- **Insitro** — Daphne Koller. Longer track record; slower cadence. Probably a beneficiary of the *hiring* wave, not the *valuation* one.
- **Chai Discovery** — YC S24, structure prediction. Newer; expect a Series A pull-forward.
- **Cradle Bio** — protein-design startup. TechCrunch profile in Aug named them as a founding-team-to-watch; ART result probably accelerates their fundraise.
- **University spinouts** — Broad / Whitehead / Salk / Scripps all have ~5 stealth AI-biology teams. Faculty founders' phones started ringing yesterday.

**What Anthropic's move signals about staffing:** if Anthropic productises the ART method (agent-orchestration for scientific discovery, offered as a Claude-adjacent product to biology customers), a **"Life Sciences Solutions" org** at Anthropic staffs up in Q4 — analogous to Anthropic's May 2026 Legal + Financial-services solutions expansions.

**Sources:**
- Extends [`01` §3 anthropic biolab discovery](./01-big-lab-moves.md#3-anthropic-biolab) — see sources there.
- [TechCrunch — Anthropic says its biology lab has already found something big](https://techcrunch.com/2026/09/23/anthropic-says-its-biology-lab-has-already-found-something-big/) `[secondary]`

### Why it matters to you

- **Job lens:** If you have *any* biology adjacency (undergrad bio, bioinformatics coursework, wet-lab TA experience, a computational-biology internship), **surface it on your resume immediately** — even one line makes you the "CS-with-bio-context" applicant, which is the exact shape Anthropic + Isomorphic + Xaira will over-hire for in Q4. If you don't have bio background: the *agent-orchestration* half of the ART method is 100% CS work — build a portfolio artifact that mimics it (see [`03` §3 router extension](./03-practical-skills-and-tools.md#3-router-extension)).
- **Startup lens:** **The bio-AI subsector's TAM just got mentally re-priced by every VC in the market.** Concrete: (a) Series-A bio-AI rounds will price 20–40% higher over the next 60 days; (b) three-person biology-AI teams with a defensible dataset will get inbound they didn't ask for; (c) *non-*biology AI founders should consider whether their agent-orchestration infra has a biology-adjacent application worth publishing.
- **Insight:** The ART result **narrows the gap between "AI-assisted research" and "AI-driven research"** — a distinction VCs and academic hiring committees have been arguing about for 3 years. It doesn't close the gap (the humans still verify + pick + write the paper), but it moves the boundary. Watch which biology-AI startups start publishing "AI-driven" instead of "AI-assisted" in their next press cycle — that's the leading edge of a re-branding wave.

→ Cross-link: [`01` §3 anthropic biolab](./01-big-lab-moves.md#3-anthropic-biolab) · [`05` §1 hiring map](./05-career-and-startup.md#1-hiring-map).

---

## 4. Instinct (Series B continues; total now $325M) — the viral-consumer-AI wedge holds {#4-instinct}

**What happened:** **Instinct**, the SF-based viral AI startup ([`02` §1 from 2026-09-10](../2026-09-10/02-new-emerging.md#1-funding-barbell)), extended its Series B. **Total equity funding: $325M.** Backed by **Index Ventures, Benchmark, Kleiner Perkins, Scott Belsky, Neil Mehta.**

**Framing:** the $325M cumulative + the top-tier VC lineup positions Instinct as **the reference "consumer AI" bet of 2026** — the round every other consumer-AI Seed / Series A will benchmark against.

**Sources:**
- Extends [2026-09-10/02 §1](../2026-09-10/02-new-emerging.md#1-funding-barbell) — original coverage there.
- [AlleyWatch — The 15 Largest US Funding Rounds of August 2026](https://alleywatch.com/2026/09/us-startup-funding-top-largest-august-2026-vc/) `[aggregator]`

### Why it matters to you

- **Job lens:** Instinct's headcount + burn scale means they hire opportunistically — **watch their careers page monthly.** Concrete role types to expect: **Consumer Product Engineer (React Native / Swift), Growth ML Engineer, LLM Applications Engineer, Applied Research (recsys / personalisation).**
- **Startup lens:** The **consumer-AI valuation floor** is now $2.5B for a viral product with credible retention. If you're building consumer AI, the pitch has to include: (a) a defensible **retention curve** (not just DAUs); (b) a **model + data flywheel** (each user's interactions improve the product for others); (c) a plausible path to **>50M MAU** (Instinct-scale). Anything without those three lines will get benchmarked-away by a VC to Instinct.
- **Insight:** The **consumer-AI barbell** — one $2.5B viral leader + a long tail of $10–30M seed rounds — is the shape most likely to hold through Q4. Middle-of-the-market ($100–500M valuation, non-viral consumer AI) is the *hardest* place to fundraise right now.

→ Cross-link: [`05` §1 hiring map](./05-career-and-startup.md#1-hiring-map).
