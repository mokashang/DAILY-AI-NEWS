# New & Emerging — 2026-09-09

The **Cognition-Devin round** is this week's single biggest signal in the emerging tier: ~2× valuation in ~4 months, revenue almost doubled ($492M → $900M), and a syndicate that reads like a "who's who" of AI-tier VCs plus NVIDIA. Beneath it, physical AI took real money (Algomatic Dynamics), the AI-hardware seam continues to attract nine-figure rounds, and a set of vertical-AI checks landed in health, travel, and legal. **The market split named in the July 25 edition is now sharper**: frontier gets bigger checks (Cognition, Anthropic pre-IPO facility), verticals need proof and defensible data, and physical AI is graduating from thesis to prototype capital.

Tags: `#funding #cognition #devin #coding-agents #robotics #physical-ai #vertical-ai #hardware #travel #health`

---

## 1. Cognition raises $2B Series E at $48B — Devin's price tag nearly doubled in four months {#1-cognition-2b}

**What happened:** On **2026-09-08**, Cognition (the Devin autonomous-coding-agent company) closed a **$2B Series E at ~$48B post-money valuation** — up from the ~$26B Series D in May. Concrete:

- **Lead:** Andreessen Horowitz and Accel co-lead.
- **Follow-on / existing:** Founders Fund, General Catalyst, Avenir.
- **New / syndicate:** Benchmark, Bessemer, Kleiner Perkins, Greylock, Lightspeed, Altimeter, Bond Capital, Meritech, Atreides, Valor, T. Rowe Price, Lux, 8VC, D1, 137 Ventures, DST, Positive Sum, HOF, Soma, BoxGroup, Battery, Ribbit, Swish, Stripes, Definition, Hanabi, Journey, Bain Capital Ventures, Layer Global, A* Capital, Alpha Wave, Alkeon, Diffusion, and **NVIDIA**.
- **Revenue growth:** run-rate ~**$492M → ~$900M** (May → early Sept). That's ~2× in a Series-D-to-E gap; SaaS peers historically took 4–6 quarters for the same jump.
- **Product framing:** Devin as the **reference autonomous engineer** — plans, writes, tests, ships PRs in supervised loops; positioned against Cursor's IDE-native flow and Claude Code's CLI-native flow.

**Sources:**
- [Unite.AI — Cognition Raises Over $2B Series E at $48B Valuation to Scale Devin Agents](https://www.unite.ai/cognition-raises-over-2b-series-e-at-48b-valuation-to-scale-devin-agents/) `[secondary]`
- [Tech Startups — Cognition AI raises $2B at $48B valuation, nearly doubling its value in just four months](https://techstartups.com/2026/09/09/cognition-ai-raises-2b-at-48b-valuation-nearly-doubling-its-value-in-just-four-months/) `[secondary]`
- [Dealroom — Cognition raises $2B Series E at $48B valuation to scale Devin](https://dealroom.co/news/149496-cognition-raises-2b-series-e-at-48b-valuation-to-scale-devin/) `[secondary]`
- [Techzine Global — Cognition raises $2 billion and nearly doubles in value](https://www.techzine.eu/news/devops/144173/cognition-raises-2-billion-and-nearly-doubles-in-value/) `[secondary]`
- [Vantage Markets — Cognition AI Hits $48B Valuation: What's Driving the Surge?](https://www.vantagemarkets.com/market-news/cognition-ai-funding-round-september-9-2026/) `[analysis]`

### Why it matters to you

- **Job lens:** Cognition's Series E hires typically go public 4–8 weeks after close. Watch [cognition.ai/careers](https://cognition.ai) between **Sept 22 and Oct 20** for a wave of eng, applied-AI, FDE, and go-to-market roles. **The specific role that mints senior comp** in a company like this is **Applied Engineer (customer-facing) with a coding-agent portfolio artifact** — one repo showing a supervised-loop workflow you designed. Ship that this weekend ([`03` §4](./03-practical-skills-and-tools.md#4-weekend-artifact)); apply within the day of first posting.
- **Startup lens:** Cognition's $48B — with $900M ARR — implies a **~53× revenue multiple**, which is at the *high end even for AI-tier* and above any comparable coding-tool SaaS multiple in history. Two interpretations: (a) the market is pricing in *seat replacement* not *seat augmentation* (a Devin literally replaces $250K/yr in engineering seats when running well), or (b) it's a bubble beta. Either way, the **wedge below Cognition** is now: **any vertical where Devin's generalist coding pipeline can't work** — hardware-adjacent firmware, safety-critical embedded, healthcare-audit-trail code, regulated-industry SDLC. Pick one; build the *supervised-agent-for-X* thin layer.
- **Insight:** The most interesting name on the syndicate is **NVIDIA** — a strategic that has also joined the OpenAI, Anthropic, and Cohere cap tables. When Nvidia is on every leading coding-agent cap table simultaneously, that is a **hedge against any one lab winning the developer surface**. Read Nvidia's position as: they are *long developer productivity, agnostic to which agent wins* — because the tokens flow to them either way.

→ Cross-link: [`05` §3 the Cognition-Devin lens on the coding-agent job market](./05-career-and-startup.md#3-cognition-lens).

---

## 2. Physical AI graduates: Algomatic Dynamics + Gimlet Labs {#2-physical-ai}

**What happened:** Two notable physical-AI rounds landed in the last week:

- **Algomatic Dynamics** (Tokyo) — raised **¥5B (~$34M USD)** from DMM.com in a first financing after spinning out of the DMM/Algomatic restructuring. Working on **motion-data collection, AI-driven multi-finger robotic hands, and bipedal-system control**. Plans to release an **AI multi-finger hand platform in Japan in 2026**.
- **Gimlet Labs** — raised **$300M in an AI-hardware round** (largest early-stage AI-hardware check of the season, per Tech Startups' summary; specific hardware target undisclosed at press time).
- **Framing:** both rounds sit in the **"physical AI" seam** — motion, manipulation, and world-modeling for embodied systems — that opened when Anthropic's Project Pilot / Drone-Bench ([2026-07-25 §04](../2026-07-25/04-research-progress.md)) identified scene-reconstruction as the embodied-autonomy blocker.

**Sources:**
- [Tech Startups — Startup Funding News Today, September 9, 2026: Cognition AI, Algomatic Dynamics, QNu Labs, VideoGen & More](https://techstartups.com/2026/09/09/startup-funding-news-today-september-9-2026-cognition-ai-algomatic-dynamics-qnu-labs-more/) `[secondary]`
- [mean.ceo — AI Startup Funding News | September, 2026](https://blog.mean.ceo/ai-startup-funding-news-september-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** Physical AI hiring has a **very different profile** from the LLM-app market: robotics + controls + real-time systems + Sim2Real ML. If you did *any* robotics coursework (CS 6xx robotics, mechanical design, simulation labs), get one Sim2Real project on your GitHub this quarter. The **supply of "LLM-app engineers" is now over-served**; the supply of "LLM-plus-robotics" is deeply under-served — pivoting one line of your background there is a high-EV career hedge.
- **Startup lens:** Physical AI's US market has a **compliance moat** (FDA, DOT, safety certifications) that pure-software AI does not. That is a founder's *positive* — it means a domain-experienced founder still matters more than a big model. If you know any hardware-adjacent founder-market-fit (biomedical device, industrial automation, warehouse logistics), start the founder-conversation loop now — the *AI + hardware + regulated market* triple is the least-crowded three-way seam in Q4.
- **Insight:** Physical AI + language-agent research are converging fast. The next major research direction (see [`04` §2](./04-research-progress.md#2-agents-multimodal)) is **agents that plan in language and act in the physical world** — the papers to read this fall are about **grounding language plans in continuous control**. If you can pattern-match between "agentic engineering" and "robotic planning," you become genuinely rare on the hiring market.

---

## 3. Vertical-AI rounds keeping the market split real {#3-vertical-ai}

**What happened:** Beneath the frontier-lab and coding-agent headlines, a set of vertical / applied checks landed in the past week:

- **WeRoad — $58M travel AI raise.** Travel-planning agents + operator dashboards; Italy-based, expanding to US.
- **Scan.com — $90M Series C.** Diagnostic imaging + AI-assisted radiology triage.
- **QNu Labs — quantum-safe encryption for AI infra** (round size undisclosed at press).
- **VideoGen — pre-Series-B AI video generation** for enterprise marketing.
- **Sequence:** Q3 2026 continues the "compute + robotics + regulated verticals" thesis, with generalist AI-consumer startups getting notably less love than in H1.

**Sources:**
- [Tech Startups — Startup Funding News Today, September 9, 2026](https://techstartups.com/2026/09/09/startup-funding-news-today-september-9-2026-cognition-ai-algomatic-dynamics-qnu-labs-more/) `[secondary]`
- [mean.ceo — Startup Funding Announcements News | September, 2026](https://blog.mean.ceo/startup-funding-announcements-news-september-2026/) `[aggregator]`

### Why it matters to you

- **Job lens:** Vertical AI companies at Series B–C are the **sweet spot for a CS grad student's first full-time role**: real revenue, small enough that ownership scope is broad, mature enough that they've fixed the worst founding-team bugs. Set a Google Alert on 4–5 vertical categories that align with your interest; apply to the strongest one **within 2 weeks of their round announcement** (the founders are actively evangelizing and hiring at that window).
- **Startup lens:** The **market split is now formal**: frontier tier = mega-checks (Cognition, Anthropic), applied tier = "must have proof + defensible data + measurable results" (per [mean.ceo](https://blog.mean.ceo/ai-startup-funding-news-september-2026/)). The founder-fit test to run on yourself: **what verifiable evidence can you generate in 90 days that a technical wedge exists?** If you can't, keep learning; if you can, start shipping.
- **Insight:** The vertical AI market is **implicitly a bet against generalist agents** (Cognition-Devin, ChatGPT Agent, Anthropic Cowork). Every vertical raise is a wager that a specialized workflow outperforms a general model even after the general model gets 2× smarter. Watch which verticals have raises **after** a Cognition Series F next spring — those are the ones investors think are *safe from generalist encroachment*.

---

## 4. Second-order: NVIDIA's cap-table strategy is now visible {#4-nvidia-strategy}

**What happened:** NVIDIA appears in the Cognition Series E syndicate. Cross-reference: NVIDIA is also invested (directly, via NVentures, or indirectly) in **OpenAI, Anthropic, Cohere, Mistral, xAI, and a growing list of applied-AI startups**. Framing: NVIDIA is **hedging across every leading AI vendor at the venture level while selling GPUs to all of them**.

**Sources:**
- [Unite.AI — Cognition Raises Over $2B Series E at $48B Valuation to Scale Devin Agents](https://www.unite.ai/cognition-raises-over-2b-series-e-at-48b-valuation-to-scale-devin-agents/) `[secondary]`

### Why it matters to you

- **Job lens:** NVIDIA is a **legitimate applied-AI career play** now, not just a hardware company. Roles like **AI Software Engineer at NVIDIA** (working on CUDA-Python integration, TensorRT-LLM, or NIM microservices) get you close to every frontier lab as customer without picking a lab. Broadly applicable; equity has been outstanding.
- **Startup lens:** If NVIDIA joins your Series B/C cap table, you get **preferred allocation on next-gen GPU sales**. That is *materially* valuable — think of it as a strategic-supply moat, not just capital. If you are raising a compute-intensive round in 2026–2027, put NVIDIA on your investor list even if you don't need the money.
- **Insight:** NVIDIA's **"long-every-vendor"** posture works only as long as GPUs remain the training substrate. Anthropic's move to TPUs (see [`01` §2](./01-big-lab-moves.md#2-anthropic-tpu)) is the first real crack. Watch whether NVIDIA responds by (a) launching NVLink-native chips for training on custom silicon, or (b) accelerating its investments in TPU/Trainium-adjacent startups. The former is 18 months out; the latter is happening quietly.

---

*Compiled from: Tech Startups · Unite.AI · Dealroom · Techzine · Vantage Markets · mean.ceo · Gravity Fast. All rounds cross-checked to at least two sources where possible; single-source rounds (Algomatic, QNu, VideoGen) flagged as such.*
