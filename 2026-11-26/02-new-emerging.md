# New & Emerging — 2026-11-26

Three genuinely-new items since yesterday's edition: **ElevenLabs is in early talks at $33B for a 2027 round** (voice-agent infra re-rated as a top-5 AI category), **Australia passed its Digital Duty of Care Act** with fines up to 5% of global revenue (joining the EU AI Act for scope), and **Tidal will delete ~29M fully AI-generated tracks starting Dec 9** (first major streaming platform to do explicit AI-slop removal). The **Chinese open-weight frontier compression** story — Kimi K3.1 Pro / GLM-5.3 / Qwen 3.8 on AA Index v5 — still matters even though the individual releases happened over the prior fortnight. For the week's earlier funding stories (Mercor $750M at $20B, Sierra talks $30B, Isomorphic $5B, Model ML $250M, LINQ $90M, LanceDB $57.5M, Charta Health $55M, fal $1.65B at $16B), see the [2026-11-23](../2026-11-23/02-new-emerging.md) / [2026-11-24](../2026-11-24/02-new-emerging.md) / [2026-11-25](../2026-11-25/02-new-emerging.md) editions — summarized in §5 here, not re-covered.

Tags: `#funding #voice #policy #open-source #china`

---

## 1. ElevenLabs in early talks at $33B for a 2027 round (up from $22B) {#1-elevenlabs}

**What happened (2026-11-25 reporting):**
- **ElevenLabs is in early talks for a 2027 funding round at ~$33B**, up from its $22B mark earlier in 2026.
- No lead confirmed publicly at time of writing; Benchmark, Sequoia, a16z are historical participants.
- Positions voice-agent infra as a **top-5 AI venture category**: ElevenLabs $33B + Sierra ~$30B (talks) + Decagon + Rox + Mercor $20B + fal $16B.
- Context: **Claude Meetings** had an outage-and-restore cycle through mid-November (see [`01` §5](./01-big-lab-moves.md#5-claude-meetings)); voice-agent reliability is a real moat that ElevenLabs owns.

**Sources:**
- [AI Weekly — Nov 25 top stories (ElevenLabs $33B)](https://aiweekly.co/ai-news-today) `[aggregator]`
- [TechCrunch AI — AI news aggregation](https://techcrunch.com/category/artificial-intelligence/) `[secondary]`

### Why it matters to you

- **Job lens:** **Voice-agent engineering is a lane with real headroom and few qualified candidates.** The skillset: realtime audio streaming + voice-activity detection + interruption handling + tool-use at <500ms latency. If you've shipped anything voice-adjacent (even a hobby Discord bot that does STT + LLM + TTS), the elevator pitch writes itself. Target companies: **ElevenLabs, Rime, Cartesia, Deepgram, LiveKit, Pipecat, Vapi, PlayHT**. Current comp bands at Founding Voice Engineer level: **$180–280K + 0.1–0.5% equity**.
- **Startup lens:** **Voice-agent infra is now a $33B anchor.** The implication for app-layer startups: build *on top of* ElevenLabs (or peers), not against them. Wedges that work: (a) **vertical voice agents** (healthcare triage, legal intake, logistics dispatch) where latency + domain language matter more than general TTS quality; (b) **voice-agent eval and observability** (there's no "LangSmith for voice" yet); (c) **voice-first commerce** (the Walmart × Muse story extended to audio).
- **Insight:** **The $33B → $22B markup is the biggest inter-round step for a voice-infra company in the cycle.** It signals that **voice is going to be the breakout AI surface of Q1 2027**, synchronized with the maturation of frontier-model latency (Fable 5.2 streaming + Gemini 4 Hydrogen + GPT-6.2 Sol all now sub-second). Expect the first "voice agent of the year" meme in Feb 2027.

→ Cross-link: [`01` §3 — Walmart × Muse](./01-big-lab-moves.md#3-walmart-muse) · [`05` §2 — voice-agent FDE roles](./05-career-and-startup.md#2-a16z-fde)

---

## 2. Australia Digital Duty of Care Act — fines up to 5% of global revenue {#2-australia-ddc}

**What happened (this week):**
- **Australian parliament passed the Digital Duty of Care Act** with **fines up to 5% of global revenue** for non-compliant platforms.
- Scope covers algorithmic recommendation systems, AI-generated content moderation, child-safety protections, and user-complaint pathways.
- Puts Australia alongside **EU AI Act** for regulatory scope on AI/platform operators. Effective-date triggers vary by provision — compliance-grandfathering schedules are being finalized.

**Sources:**
- [AI Weekly — Nov 25 top stories (Australia DDC)](https://aiweekly.co/ai-news-today) `[aggregator]`

### Why it matters to you

- **Job lens:** **AI policy / Trust & Safety / AI Compliance Engineer** is a growing sub-track. Target companies: Anthropic Policy, OpenAI Global Affairs, Google Trust & Safety, Meta Content Integrity, Palantir Compliance. Roles increasingly technical — "I can run a compliance-adversarial eval against our own model" is the demonstrable skill.
- **Startup lens:** **If your product has Australian users (or any revenue from Aus), you need an impact-assessment artifact by the effective-date trigger.** Startups building the **"Compliance-as-Code for AI"** stack (automated impact assessments, model-card generators, audit-trail infra) have a widening market. Market the product at **US-founded, globally-served** AI companies that don't want to build this in-house.
- **Insight:** **Expect UK + Canada DDC-equivalents in Q1 2027** — the pattern of "one country's major platform law catalyzes aligned laws in parallel jurisdictions" is now standard. The **cross-jurisdiction compliance layer** is a $100M+ TAM wedge for the first startup that nails it. If you're a US-based founder, the differentiated pitch: "we're the EU + UK + Aus + CA compliance stack, one API, one eval."

→ Cross-link: [`04` §3 — Access Control for Agents](./04-research-progress.md#3-access-control)

---

## 3. Tidal to delete ~29M fully AI-generated tracks starting Dec 9 {#3-tidal-ai-removal}

**What happened (2026-11-25):**
- **Tidal announced it will begin deleting fully AI-generated tracks on Dec 9**, removing ~29M songs by year-end.
- **First major streaming platform** to do explicit AI-slop removal (Spotify, Apple Music, YouTube Music have policies but haven't executed at scale).
- Discovery: Tidal detects AI-generated tracks via a combination of **watermark checks, audio-fingerprint analysis, and artist-signal matching**.
- Signal: **platform-level content gating is now a real surface area for AI policy**, and provenance tagging (C2PA, model-watermarks) starts to matter commercially.

**Sources:**
- [AI Weekly — Nov 25 Tidal AI-generated track removal](https://aiweekly.co/ai-news-today) `[aggregator]`

### Why it matters to you

- **Job lens:** **AI content detection / provenance engineering** is a quiet but growing lane. Target companies: C2PA consortium members, Truepic, Reality Defender, Hive AI, Pindrop, Adobe Content Authenticity. Also: every streaming/social platform's trust-and-safety org. Skillset: audio/image/video forensics + ML + metadata standards.
- **Startup lens:** **Provenance-as-a-service for AI content is a startup wedge opening right now.** Watermarking infra, C2PA signing, cross-platform content verification — all under-served. The buyer is every social / streaming / commerce platform that has a "no generated content" policy and no way to enforce it.
- **Insight:** **The Tidal move is the opening salvo of the "AI-generated content provenance decade."** By 2028, every major content platform will have a provenance layer — and startups that get their C2PA signing stacks shipped by Q2 2027 will be the default integrations.

→ Cross-link: [`04` §3 — Access Control for Agents](./04-research-progress.md#3-access-control)

---

## 4. Chinese open-weight frontier compresses: Kimi K3.1 Pro / GLM-5.3 / Qwen 3.8 {#4-china-open-weight}

**What happened (last 30 days):**
- **Five Chinese labs compressed into a 30-day release window on two licensing models** (modified-MIT and revenue-gated custom).
- **Kimi K3.1 Pro (Moonshot AI)** — 2.8T-parameter MoE, 1M-token context, modified-MIT ("Kimi K3 License"). Base K3 released July 27.
- **GLM-5.3 (Zhipu AI)** — 753B total parameters; Prime variant on MIT; custom license with revenue review above $10B for full stack.
- **Qwen 3.8 (Alibaba)** — Qwen3.8-Max as closed cloud, Qwen3.8-2.4T-A95B open-weight (Aug 8); 2.4T previewed with eventual open-weight commit.
- **AA Index v5 (Nov 5) rankings:** K3.1 Pro 46 / GLM-5.3 32 / Qwen 3.8-27B in the mix — note the v5 index version shift means don't compare directly to earlier v4 scores.
- Note: **Gemini 4 Neon ranks #1 on AA Coding Agent Index at 58.64 vs Fable 5.2 at 58.47** (per Nov 24 edition), a different index — Chinese open-weight still trails on coding specifically.

**Sources:**
- [Forkast — Chinese open-weight frontier compresses: five labs, thirty days](https://forkast.news/chinese-open-weight-frontier-compresses-five-labs-thirty-days-two-licensing-models/) `[analysis]`
- [regolo.ai — K3.1 Pro vs DeepSeek 1017 vs GLM-5.3 vs Qwen3.8-27B (AA v5)](https://regolo.ai/kimi-k3-1-pro-vs-deepseek-1017-vs-glm-5-3-qwen3-8-27b-benchmarks.md) `[analysis]`
- [The Decoder — Moonshot releases Kimi K3 open weights](https://the-decoder.com/moonshot-ai-releases-kimi-k3-open-weights-and-infrastructure-after-shaking-up-the-frontier-model-race/) `[secondary]`
- [ai2.work — Chinese labs own the open-weight leaderboard](https://ai2.work/blog/chinese-labs-own-the-open-weight-leaderboard-glm-deepseek-qwen) `[analysis]`
- [SCMP — Moonshot unveils world's largest open-source AI model](https://www.scmp.com/tech/tech-trends/article/3360885/moonshot-ai-unveils-worlds-largest-open-source-ai-model-china-narrows-gap-us-rivals) `[secondary]`

### Why it matters to you

- **Job lens:** The **open-weight-finetuning + inference-infra skillset is where Chinese-model-adjacent US startups will hire in 2027**. Learning **vLLM / SGLang / TGI serving patterns** this quarter is the single highest-signal technical upskill for a CS grad targeting applied-ML lanes.
- **Startup lens:** **The first US B2B startup that credibly ships on a Chinese open model in production is the whole thread.** Risk-adjust for license revenue thresholds (GLM $10B review clause), US export-control derivative-work questions (unresolved), customer-trust narrative. Winning lanes: non-US-regulated customers (LATAM, SEA, EU), on-prem offline inference (regulated industries), adapter-layer tooling.
- **Insight:** **The two-licensing-model split (modified-MIT vs revenue-gated) will set the template for how China open-weight competes long-term.** Watch Alibaba's next Qwen 3.8-2.4T license text — the decisive signal. Also: as [NVIDIA guided $0 China data-center compute for Q4](../2026-11-14/01-big-lab-moves.md#5-nvidia-fy27-q3), the pressure on Chinese labs to serve via Huawei Ascend / Cambricon / domestic silicon rises in parallel.

→ Cross-link: [`03` §5 — serving Chinese open-weight models](./03-practical-skills-and-tools.md#5-open-weight-serving) · [`01` §1 — ANT week-one](./01-big-lab-moves.md#1-ant-week-one)

---

## 5. Prior fortnight's funding — brief refresh {#5-prior-funding-refresh}

**For continuity (full detail in referenced editions):**
- **Mercor $750M Series D at $20B (Nov 10–11)** — NVDA + Salesforce + Zoom on cap table; valuation doubled in a year. See [2026-11-24 §2](../2026-11-24/02-new-emerging.md).
- **Sierra in talks at ~$30B on ~$1.5B round (Nov 18)** — The Information scoop; Lightspeed/Greenoaks/Benchmark as leads; ARR $400M/Oct from $150M/Feb (~75× ARR implied). See [2026-11-24 §3](../2026-11-24/02-new-emerging.md).
- **Isomorphic Labs $5B Series C (Nov 16)** — Alphabet/DeepMind drug-discovery spinout; largest biotech-AI round of 2026. See [2026-11-25 §1](../2026-11-25/02-new-emerging.md).
- **Model ML $250M Series B (Nov 17)** — General Atlantic + QED co-leads; financial-services-first agent platform. See [2026-11-25 §2](../2026-11-25/02-new-emerging.md).
- **LINQ $90M (agent telephony), LanceDB $57.5M (Bessemer), Charta Health $55M (clinical AI)** — see [2026-11-24 §4](../2026-11-24/02-new-emerging.md).
- **OpenAI ~$11B raise (Nov 6)** per aggregator reporting — primary vs. secondary split unclear.
- **fal $1.65B at $16B (Series E+F, Nov 3)** — Bessemer-led; already in [2026-11-14 §1](../2026-11-14/02-new-emerging.md).

**November so far:** 371 rounds, $38.2B raised per [Work Insiders](https://workinsiders.com/funding/2026-11/) `[aggregator]`.

### Why it matters to you

- **Job lens:** **Every one of these companies is hiring now, at founding-engineer or FDE/SE levels.** The companies I'd prioritize for application this week (pre-Thanksgiving): **Sierra (Founding SE), Model ML (Applied AI Engineer), Charta Health (Applied AI + Clinical FDE), LanceDB (Developer Advocate + Applied).** Mercor is hiring aggressively for domain-eval work — set up a profile even if you also apply to full-time roles.
- **Startup lens:** **The $38.2B aggregate November spend across 371 rounds is the aggregate number to quote in your own pitch.** It helps anchor: "this is the biggest AI-funding month of the cycle; we're entering the category when capital is most available." But balance with the ANT below-offer trading tape — **Q1 2027 will compress multiples**. Close rounds that are close; be patient on new raises.
- **Insight:** **The pattern across the five-category November funding map (compute, data labor, voice, enterprise agents, bio-AI) is that infrastructure-adjacent is getting outsized checks vs. application-layer.** For your career: **infra-adjacent roles are compensated higher per unit experience** than application-layer roles right now.

→ Cross-link: [`05` §4 — side income via Mercor](./05-career-and-startup.md#4-side-income)
