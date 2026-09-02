# New & Emerging — 2026-08-01

New models · startups · tools · funding · paradigm shifts. Everything below the frontier-lab tier that is *repricing* something.

---

## 1. Ai4 Las Vegas 2026 — T-3 to America's largest AI conference (Aug 4-6) {#1-ai4-las-vegas}

**What happened.** **Ai4 2026** opens **Tue 2026-08-04** at The Venetian, running through **Thu 2026-08-06**. Scale: **12,000+ attendees · 1,000+ speakers · 400+ exhibitors · 90+ countries** [primary]. The joint keynote fielding is the deepest single stage of the year: **Geoffrey Hinton + Fei-Fei Li + Andrew Ng** together, plus **Sebastian Thrun**, **Dmitri Dolgov** (Waymo co-CEO), **Tom Gruber** (Siri co-founder), **Timothée Lacroix** (Mistral co-founder). Twenty tracks by vertical (financial services, healthcare, cybersecurity, retail, manufacturing, energy, transportation, national security, insurance, media).

**Sources:**
- [Ai4 official site](https://ai4.io/) [primary]
- [Ai4 2026 Yahoo Finance — agenda live](https://finance.yahoo.com/sectors/technology/articles/ai4-2026-agenda-now-live-131500737.html) [secondary]
- [Ai4 2026 keynote spotlight](https://finance.yahoo.com/news/ai4-2026-spotlight-brilliant-minds-182000601.html) [secondary]
- [zPlatform.ai — Ai4 2026 details](https://zplatform.ai/ai-event/ai4-2026/) [aggregator]

**Why it matters to you.**
- **Job:** even if you're not attending, the **hiring booths ship req-lists two weeks before the event**. Grep the exhibitor list (400+ companies) for "Solutions Engineer / FDE / Applied AI / AI Integration". Every Big-4 consulting firm + top-tier neocloud will have a booth. Cold-DM a booth manager Sunday night — three sentences, one link to a portfolio artifact ([`05` §2](./05-career-and-startup.md#2-ai4-cold-outreach)).
- **Startup:** this is the largest **applied-AI-in-verticals** buyer concentration of the year. If your wedge is a vertical agent (insurance claims triage, retail inventory, manufacturing QA), spend $500 on a general-admission ticket, print one A4 case-study sheet with a QR code to a live demo, and hand it out at four vertical-specific tracks. **Cheapest customer-discovery event in the calendar.**
- **Insight:** the **track list is the buyer-side road-map for the next 12 months**. Every category with a dedicated Ai4 track has enterprise budgets already committed; every category *not* on the track list (agentic coding, dev-tools, foundation-model training) is still labs-and-devs-only. Cross-reference to your wedge scoring in [STARTUPS.md](../STARTUPS.md).

`#events #ai4 #vegas #conference #enterprise-buyers #verticals`

---

## 2. Ramp AI Index next drop — Monday Aug 3 preview {#2-ramp-index-preview}

**What happened.** The Ramp AI Index refreshes Mondays; the **Aug 3 print** lands two days from now with July closing data. Two threads to watch on the Monday chart:
1. Whether **Anthropic's lead over OpenAI in US business adoption** — [34.4% vs 32.3% as of 2026-05-14](../2026-05-14/) — held through July or the [GPT-5.6 Luna 80% price cut](../2026-07-31/01-big-lab-moves.md#2-gpt-56-price-cuts) shifted new-account share.
2. Whether **top-1% firms' AI spend/employee** — $7.5K/mo as of Jul 16 — kept the **+14.1% MoM trajectory** (annualized ~350%).

**Sources:**
- [Ramp AI Index landing (weekly)](https://ramp.com/blog/ai-index) [primary]
- [WATCHLIST.md — Ramp thread](../WATCHLIST.md) [archive]

**Why it matters to you.**
- **Job:** the Monday index is the **single most-cited enterprise-AI-adoption data point in Anthropic Solutions / OpenAI Deployment Co / AWS AgentCore interviews.** Have this Monday's numbers on-hand for any interview Tue–Fri; being one screenshot ahead of the interviewer is the cheapest signal-of-care you can send.
- **Startup:** the top-1% spend line **is the addressable-market chart for the "cost-router / model-picker" wedge.** $7.5K/employee/mo × 10 employees × 12% you can save = $9K/mo of headroom to sell into per customer. That's a defensible $499/mo SaaS at ~5% take-rate.
- **Insight:** if the **Anthropic-share line rolled over in July** despite the Sonnet 5 promotional pricing, that's a **buy-side warning shot** — OpenAI's price cut worked. If it held, Anthropic's [pacing-the-frontier letter](../2026-07-30/01-big-lab-moves.md#1-pacing-the-frontier) + [three-org breach disclosure](../2026-07-31/01-big-lab-moves.md#1-claude-hacked) actually *bought* enterprise trust rather than costing it — a first empirical read on whether transparency is a moat.

`#ramp #adoption #anthropic #openai #pricing #benchmarks`

---

## 3. Neocloud consolidation — Nscale × Anyscale post-mortem, next-move watch {#3-neocloud-nextshoe}

**What happened.** Yesterday's [$1.65B Nscale acquisition of Anyscale (Ray)](../2026-07-31/02-new-emerging.md#1-nscale-anyscale) closed a structural gap in the neocloud stack — bare-metal + Ray-based scheduling under one roof. Weekend-of-Aug-01 the interesting question is *who moves next*: **CoreWeave · Crusoe · Together · Lambda Labs · Groq · Nebius · Nscale** are the seven surviving western-hemisphere neoclouds; **the software layer above the GPU is the only defensible margin left** now that GPU spot pricing tracks Nvidia list.

**Sources:**
- [Yesterday's Nscale × Anyscale write-up](../2026-07-31/02-new-emerging.md#1-nscale-anyscale)
- [Nvidia $250B Rubin roadmap + Nvidia-OpenAI 10GW partnership context](https://www.barchart.com/story/news/34966864/openai-and-nvidia-announce-100-billion-strategic-partnership-to-build-10gw-of-ai-data-centers) [secondary]

**Why it matters to you.**
- **Job:** **Ray-native scheduling** is a scarcer skill than the enterprise SDR pipeline suggests. If you can demonstrate a small Ray Serve deployment (single-node, 2 GPUs, deployed to a Nscale/Crusoe trial account) as a weekend project, that's a real portfolio artifact for CoreWeave Applied / Nscale SE / Together Solutions.
- **Startup:** the *unexploited* neocloud niche is **"managed inference for Chinese open-weights"** — DeepSeek V4-Flash-0731, Kimi K3, GLM-5.2, Qwen — hosted in US / EU with an OpenAI-compatible endpoint. Compliance-shielded managed inference could sell into any Fortune 500 that wants K3 economics without hosting-in-China risk. Founder-fit check: can you get a beta cluster live in 90 days on a Nscale trial?
- **Insight:** every neocloud that survives 2027 will have **either an M&A move (like Nscale) or a software-differentiation moat (like Groq's LPU)**. The middle — commodity H100/H200/GB200 rental — is the tier that gets margin-compressed by Nvidia and hyperscaler pricing wars.

`#neocloud #nscale #anyscale #ray #inference #chinese-open-weights`
