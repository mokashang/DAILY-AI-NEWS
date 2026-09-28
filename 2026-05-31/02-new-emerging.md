# New & Emerging — 2026-05-31

A capital-heavy week dominated by mega-rounds at the coding-agent layer (Cognition $1B), the gateway/router layer (OpenRouter $113M), and the infra layer (Groq $650M neocloud). Two M&A signals — **Asana acquiring StackAI** and **Mistral acquiring Emmi** — confirm that horizontal SaaS is *buying* the agent layer, and that European labs are pivoting from pure model R&D into vertical industrial AI. Innovation signal continues to migrate to non-Big-6 actors: **OpenBMB's MiniCPM5-1B** quietly took the sub-2B open-weights crown from a Tsinghua-affiliated lab. **The market is bifurcating into a US capital story and a rest-of-world capability story.**

Tags: `#funding #m-and-a #cognition #groq #asana #stackai #mistral #emmi #openrouter #china #open-source #infra #saas-consolidation`

---

## 1. Cognition $1B at $26B post-money — Devin ARR $492M, 6 straight months of 50% MoM enterprise growth {#1-cognition}

**What happened (2026-05-27):** Devin-maker **Cognition** closed a **$1B+ late-stage round at $25B pre-money / $26B post-money**, co-led by **Lux Capital, General Catalyst, and 8VC**, with **Ribbit, Atreides, Layer Global, Founders Fund, and Elad Gil** participating.

- **ARR run-rate:** **$492M**
- **Enterprise usage growth:** **50% MoM for six straight months**
- **Customers:** Mercedes-Benz, NASA, Goldman Sachs, Santander
- **Internal stat (CEO Scott Wu):** **>90% of Cognition's own code is now written by Devin**
- **Valuation history:** ~2.5× from $10.2B in September 2025 → $26B now (~8 months)

**Sources:**
- [TechCrunch — AI coding startup Cognition raises $1B at $25B pre-money valuation](https://techcrunch.com/2026/05/27/ai-coding-startup-cognition-raises-1b-at-25b-pre-money-valuation/) `[primary]`
- [Bloomberg — Cognition Raises $1 Billion at $26 Billion Value](https://www.bloomberg.com/news/articles/2026-05-27/ai-coding-startup-cognition-raises-1-billion-at-26-billion-value) `[primary]`
- [TNW — Cognition raised $1B at $26B and 90% of its own code is written by its AI](https://thenextweb.com/news/cognition-just-raised-1-billion-at-a-26-billion-valuation-and-90-of-its-own-code-is-written-by-its-ai) `[secondary]`

### Why it matters to you

- **Job lens:** Coding-agent is now a mega-category — Cognition + Cursor + Replit + GitHub Copilot + Codex + Claude Code are all hiring engineers who *use* coding agents to ship product, not just maintain the agents themselves. The "I shipped X with Devin / Claude Code in Y days" portfolio is now recruiter-legible at every one of these companies. Also: Cognition's enterprise customer list (Mercedes/NASA/GS/Santander) means **enterprise-deployment / FDE-style roles at Cognition** are now a credible adjacency to the Anthropic FDE path in [`05` §2](./05-career-and-startup.md#2-anthropic-fde).
- **Startup lens:** The 6-consecutive-months 50% MoM growth is the most interesting datapoint — it means enterprise demand for *autonomous-coding* agents is real and durable, not a Q1 spike. But it also means the wedge is closing fast: a horizontal "another coding agent" startup is now table-stakes-hard. The open wedge is **vertical coding agents** (compliance-aware code generation for finance/healthcare/aerospace; embedded-systems coding agents; SQL/BI coding agents) — categories where domain-specific verification matters more than raw capability.
- **Insight:** The "90% of our own code is written by Devin" claim is the **recursive-self-improvement signal** in the wild — paired with Karpathy's "Claude accelerates Claude's training" team at Anthropic ([2026-05-22 §3](../2026-05-22/01-big-lab-moves.md#3-karpathy)), the pattern of *AI labs using their own products to accelerate themselves* is now the operating norm at the frontier. Internalize this: if you're not using Claude Code / Cursor / Codex to write 50%+ of your own code, you're competing with people who are.

→ Cross-link: [2026-05-22 §3 Karpathy to Anthropic / Claude-accelerates-Claude](../2026-05-22/01-big-lab-moves.md#3-karpathy) · [`03` §1 dynamic workflows](./03-practical-skills-and-tools.md#1-ultracode).

---

## 2. Asana acquires StackAI ($75M) + Groq raising $650M as a neocloud — two faces of agent-economy M&A {#2-groq-asana}

**Asana acquires StackAI (2026-05-28, $75M):** Asana acquired YC-bred no-code AI workflow platform **StackAI** for **$75M** alongside its earnings call. StackAI lets enterprises design, test, and deploy custom AI agents that operate across Salesforce, Slack, and Google Workspace. Founders Tony Rosinol and Bernard Aceituno (both ex-MIT robotics) join Asana; StackAI continues as its own brand. CEO Dan Rogers framed the combination as building **"the operating system for human-agent teams."**

**Groq raising $650M (2026-05-28 Axios scoop → 2026-05-29 broader coverage):** Following December 2025's $20B Nvidia "not-acqui-hire" (which absorbed Groq's LPU IP plus founder Jonathan Ross and most senior engineers), the **remaining Groq entity — now "Groq2" under CEO Adam Winter and CFO Matt Eng** — is raising up to **$650M from existing investors** (Disruptive and Infinitum backstopping pro rata) to pivot fully into **AI inference cloud services**. Crucially, the new entity competes with CoreWeave/Lambda as a neocloud but sits **on top of Nvidia hardware**, not its own silicon — a striking inversion of Groq's original challenger thesis.

**Sources:**
- [TechCrunch — Asana acquires no-code agent-builder StackAI](https://techcrunch.com/2026/05/28/asana-acquires-no-code-agent-builder-stack-ai/) `[primary]`
- [Reworked — Asana Buys StackAI for $75M](https://www.reworked.co/digital-workplace/asana-buys-stackai-to-power-agent-orchestration/) `[secondary]`
- [Axios — Scoop: Groq raising $650 million for its second act](https://www.axios.com/2026/05/28/groq-650-million-nvidia) `[primary]`
- [TechCrunch — After Nvidia's $20B not-acqui-hire, Groq reportedly raising $650M](https://techcrunch.com/2026/05/29/after-nvidias-20b-not-acqui-hire-ai-chip-startup-groq-reportedly-raising-650m/) `[secondary]`
- [Crypto.news — Groq lines up $650M for neocloud spin-out](https://crypto.news/groq-lines-up-650m-for-neocloud-spin-out-after-20b-nvidia-deal/) `[aggregator]`

### Why it matters to you

- **Job lens:** Asana's StackAI buy is the clearest signal yet that **horizontal SaaS incumbents are buying — not building — the agent layer.** That means the next 12 months of "Agent Engineer at $SaaS_Co" job postings come from acquired-team-leads inside Notion, Monday, ClickUp, Atlassian, etc. — same pattern Salesforce ran with Tableau/Slack. **The play: skill up on Anthropic Agent SDK + MCP + a horizontal-SaaS API stack (Salesforce, Slack, Workspace, M365)** and you have the exact CV the acquiring incumbents will look for. Groq's neocloud pivot also opens an "AI inference SRE / capacity-planning engineer" lane that didn't exist 6 months ago.
- **Startup lens:** Two M&A pricing comps. **StackAI at $75M after a YC-bred 2–3-year arc** sets a floor for no-code agent platforms — credible exit target for any founder building in that lane. **Groq's $650M neocloud pivot** is the cautionary tale: even an ostensibly successful "Nvidia-killer" chip company ended up reincarnated as a Nvidia-hosted services co. Don't pitch "competing with Nvidia on silicon" unless you have unreasonable capital and patience; pitch *services and workflows on top of* the GPU oligopoly instead.
- **Insight:** Together these two deals say the AI economy is **stratifying fast**: capital flows to frontier labs and to the SaaS layer that distributes their output, while the *middle* (chip startups, agent-platform startups) gets either absorbed (Groq → Nvidia) or rolled into incumbents (StackAI → Asana). For a founder, the safest 2026 positions are at the *edges* — frontier capability or last-mile vertical workflow — not in the middle.

→ Cross-link: [`05` §2 Anthropic FDE / horizontal-SaaS adjacency](./05-career-and-startup.md#2-anthropic-fde).

---

## 3. Mistral acquires Vienna's Emmi AI — Europe makes its physics-AI play {#3-mistral-emmi}

**What happened (2026-05-25):** Mistral acquired Austrian physics-simulation startup **Emmi AI** in a cash-and-stock deal sources peg near **€300M** (officially undisclosed). Emmi was founded in 2024, raised **€15M last year** (Austria's largest 2025 seed), and builds **neural surrogate models that compress physics simulations** (airflow, heat transfer, material stress) from **hours to seconds**.

- **Emmi's 30+ engineers** join Mistral's Science and Applied AI teams.
- **Target markets named:** aerospace, automotive, semiconductor manufacturers.
- **Mistral's 2nd acquisition in 3 months** (after French cloud-deployment platform Koyeb in Feb).
- Part of a **4-lab / 4-acquisition cluster in 5 days** (Anthropic/Stainless, Google DeepMind/Contextual AI, Mistral/Emmi, Meta/undisclosed).

**Sources:**
- [The AI Insider — Mistral AI Acquires Physics Simulation Startup Emmi AI](https://theaiinsider.tech/2026/05/25/mistral-ai-acquires-physics-simulation-startup-emmi-ai-to-deepen-industrial-ai-push/) `[secondary]`
- [Sifted — Mistral strikes second M&A deal in months with Emmi](https://sifted.eu/articles/mistral-strikes-second-ma-deal-in-months-with-austrian-ai-startup-emmi) `[primary]`
- [HPCwire — Mistral AI Acquires Emmi AI](https://www.hpcwire.com/aiwire/2026/05/26/mistral-ai-acquires-emmi-ai-to-expand-physics-ai-and-engineering-models/) `[secondary]`
- [StartupHub — Four labs, four acquisitions in five days](https://www.startuphub.ai/ai-news/ai-news/2026/four-labs-four-acquisitions-ai-consolidation-may-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Physics-AI / engineering-surrogate-models is one of the **least crowded** sub-disciplines of applied ML in 2026. If you have ANY background in mechanical engineering, aerospace, fluid dynamics, materials, or semiconductors, **Mistral's Science and Applied AI teams + Emmi's Vienna office are an asymmetric application**. Pair that with the Airbus partnership ([§4 on `01`](./01-big-lab-moves.md#4-mistral)) and there's a credible 3-year path from "join as an applied scientist" → "lead a vertical industrial agent product."
- **Startup lens:** **Industrial / engineering AI** just had its acquisition comp set near €300M for a 30-person team. That's a strong signal for any solo founder or small team building surrogate-model tooling for a specific industrial vertical (battery design, chip lithography, fluid simulation, CAD-integrated optimization). The buyers are now identified (Mistral, Airbus, the EU sovereign funds), and the exit path is real.
- **Insight:** The reason this matters more than another consumer-AI acquisition: **physics-AI is one of the few categories where Chinese open-source models can't yet compete on parity** because the training data is proprietary, regulated, and often classified (aerospace, semiconductors). That makes industrial AI a structurally defensible Western moat in a year when most other AI moats are getting commoditized fast.

→ Cross-link: [`01` §4 Mistral AI Now Summit / Airbus deal](./01-big-lab-moves.md#4-mistral).

---

## 4. OpenRouter $113M Series B at $1.3B — the gateway/router layer is a category, not a feature {#4-openrouter}

**What happened (2026-05-26):** **OpenRouter** raised a **$113M Series B led by CapitalG** (Alphabet's growth fund), with **NVentures (Nvidia), ServiceNow, MongoDB, Snowflake, Databricks Ventures**, plus existing investors a16z and Menlo Ventures, at a **$1.3B post-money** (>2× from $547M in June 2025).

- **Weekly volume:** 5T → **25T tokens in 6 months**
- **Developer base:** **8M+** building across **400+ models**
- **Use of proceeds:** routing, governance, optimization for enterprise AI workflows

**Sources:**
- [OpenRouter — Raises $113M Series B](https://openrouter.ai/announcements/series-b) `[primary]`
- [TechCrunch — OpenRouter more than doubles valuation to $1.3B in a year](https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/) `[secondary]`

### Why it matters to you

- **Job lens:** Model-routing / observability / governance is **now a fundable standalone category**, not a feature on top of someone else's platform. That means standalone titles ("Gateway SRE," "Eval Engineer," "Model Operations PM," "Routing PM") at **OpenRouter, Portkey, Helicone, LangSmith, Braintrust** are about to multiply through Q3. Build one public artifact this week: a small open-source router (Python OK; LiteLLM-style), or a benchmark comparing Claude 4.8 vs Gemini 3.5 vs GPT-5.5 on a real workload with cost/quality plotted. That single repo is more recruiter-legible than another LeetCode grind, and it's *exactly* what an OpenRouter or Portkey hiring manager looks for.
- **Startup lens:** OpenRouter's strategic-investor list (CapitalG / Nvidia / ServiceNow / MongoDB / Snowflake / Databricks) tells you who the **eventual acquirers** of this category will be. Snowflake/Databricks especially — they need an AI gateway as a first-class product surface and don't yet have one. The wedge for a *new* gateway/router startup is now **vertical** (e.g., a router specialized for healthcare PHI redaction, or for financial-compliance routing), not horizontal.
- **Insight:** 25T tokens/week through one router is the most interesting datapoint. It means a non-trivial share of AI consumption is **already mediated by an intermediary** — the multi-model future isn't speculative, it's the current state. Cost-aware routing is a top-2 interview-worthy skill for the next 12 months.

→ Cross-link: [`05` §1 router category as hiring vector](./05-career-and-startup.md#1-router-category) · [`03` §4 Semble MCP for code search](./03-practical-skills-and-tools.md#4-semble).

---

## 5. OpenBMB ships MiniCPM5-1B — sub-2B open-weights frontier is a Chinese story now {#5-minicpm}

**What happened (2026-05-28):** Beijing's **OpenBMB** (Tsinghua-affiliated) released **MiniCPM5-1B** under **Apache-2.0**, shipping weights, the pre-training corpus, deployment code, and **Apple Silicon (MLX) + GGUF builds on Hugging Face simultaneously**.

- **Artificial Analysis Intelligence Index: 17.9** — **7.4 points above the next-best ≤1B open model**
- **Aggregate score: 42.57** across reasoning/code/math/agentic benchmarks (vs. 35.61 prior best in size class)
- **Built-in hybrid reasoning** via a `<think>` chat template
- **128K context**, fits in smartphone memory
- **Same release wave (last ~6 weeks):** Kimi K2.6, GLM-5.1, DeepSeek V4, MiniMax M2.7, Qwen 3.6 — all landing at roughly Western frontier capability at ~⅓ inference cost

**Sources:**
- [Artificial Analysis — MiniCPM5-1B: The leading 1B open weights model](https://artificialanalysis.ai/articles/minicpm5-1b-the-leading-1b-open-weights-model) `[analysis]`
- [Hugging Face — openbmb/MiniCPM5-1B](https://huggingface.co/openbmb/MiniCPM5-1B) `[primary]`
- [GitHub — OpenBMB/MiniCPM](https://github.com/openbmb/minicpm) `[primary]`

### Why it matters to you

- **Job lens:** **On-device / edge AI** is the underrated 2026 hiring lane — every consumer-AI product company (Apple, Samsung, Meta Ray-Ban, OpenAI's rumored hardware) needs engineers who can deploy and tune sub-2B models on actual hardware. The skill: take MiniCPM5-1B, deploy it on your laptop with MLX, build something useful, write up the latency/quality/memory profile. That writeup is interview-ready for any company building on-device AI.
- **Startup lens:** A genuinely capable 1B model running on a phone changes the **B2C unit economics** for consumer AI — you can ship an app that runs the model client-side, paying zero inference cost, while still delivering "looks like GPT-4o" quality on most consumer tasks. Wedges: privacy-first journaling/therapy apps, kid-safe AI tutors (on-device, no data leaves), creator-economy tools where latency and offline-availability matter.
- **Insight:** The frontier of *small* models is now squarely Chinese open-source. Western labs (Meta, Mistral, Google's Gemma) are still strong but no longer obviously leading at <2B. Read together with DeepSeek's permanent 75% cut ([`01` §5](./01-big-lab-moves.md#5-deepseek)): **the *cheap and small* half of the model market is structurally tilted east now.** The Western answer (so far) is to win on the *expensive and large* half — which is exactly what Anthropic's $965B + Opus 4.8 narrative is selling.

→ Cross-link: [`01` §5 DeepSeek permanent price cut](./01-big-lab-moves.md#5-deepseek).

---

## Capital concentration this week (one-line read)

Coding agents and customer-facing agents absorbed the largest checks (**Anthropic $65B, Cognition $1B, Asana/StackAI $75M**); the rest of the dollars flowed to infrastructure plays repositioning around the Nvidia-centric stack (**Groq $650M neocloud, Anthropic adding Samsung/SK Hynix/Micron**); and the *innovation* signal migrated to non-US, non-Big-6 actors (**Mistral/Emmi, OpenBMB MiniCPM5-1B, DeepSeek on Ascend**) — collectively suggesting the market is bifurcating into a **US capital story** and a **rest-of-world capability story**.
