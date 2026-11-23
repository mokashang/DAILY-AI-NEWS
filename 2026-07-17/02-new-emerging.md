# Emerging — 2026-07-17

The enterprise agent-stack funding week: **$2.5B+ in disclosed rounds across identity, voice, coding, inference, video, robotics, and back-office**. The category getting the loudest capital vote isn't a specific vertical — it's **the plumbing layer under agents**: Fireworks ($1.5B for customizable inference), Oak ($60M for AI-agent identity/IAM), Rime ($24M for speech-to-speech foundation), Thira ($21M for agentic back-office). Add Thinking Machines' first shipped model (**Inkling**, 975B / 41B-active MoE, Apache-2.0) and NetApp's DataPelago acquisition, and the shape of the emerging tier is clear: **as the frontier labs commoditize models and go vertical, the picks-and-shovels layer around them is the next $10B+ opportunity set.**

Tags: `#funding #agents #inference #voice #open-source #video #humanoids #identity #back-office`

---

## 1. Fireworks AI closes $1.5B Series D at $17.5B — customizable inference becomes a tier {#1-fireworks}

**What happened:** **Fireworks** — the open-source model fine-tuning + inference platform founded in 2022 by ex-Meta PyTorch engineer **Lin Qiao** — raised **$1.505B Series D at $17.5B post**.

- **Round:** Co-led by **Atreides Management, Index Ventures, and TCV**. Follow-ons: **Lightspeed, NVIDIA, Bessemer, Menlo, Insight, Lone Pine**.
- **Traction:** **ARR past $1B (~5× YoY)**; daily token volume **jumped from 15T to 40T** in the past year.
- **Use of funds:** More compute + deeper **Microsoft and NVIDIA integrations** — the "customizable inference on top of open frontier models" thesis at hyperscaler scale.

**Sources:**
- [Fireworks — Series D Announcement](https://fireworks.ai/blog/series-d-announcement) `[primary]`
- [SiliconANGLE — AI infrastructure startup Fireworks closes $1.5B round at $17.5B valuation](https://siliconangle.com/2026/07/16/ai-infrastructure-startup-fireworks-closes-1-5b-round-17-5b-valuation/) `[secondary]`
- [Quartz — Fireworks AI raises $1.5 billion Series D at $17.5 billion valuation](https://qz.com/fireworks-ai-series-d-fundraise-valuation-open-source-071626) `[secondary]`

### Why it matters to you

- **Job:** Fireworks is now a top-tier destination for **inference / systems / distillation engineers** — competing directly with Anthropic, Together, Databricks, and Baseten on comp. If you're MLE-inclined with GPU experience, this is a live-hiring org.
- **Startup:** The **"specialized intelligence"** thesis (customer-fine-tuned open models beating frontier general models on niche tasks) just got its biggest capital vote yet. That's structural cover for any "vertical open-model" wedge in [STARTUPS.md](../STARTUPS.md).
- **Insight:** **Post-training + inference infra**, not base-model training, is where the next durable margin pool sits. Fireworks + Runware ([2026-05-19/02 §4](../2026-05-19/02-new-emerging.md#4-runware)) + Together + Modal + Baseten are collectively pricing the *between-labs-and-app* layer at multi-billion-dollar TAM.

**Tags:** `#funding #series-d #inference #open-source #infrastructure #unicorn`

---

## 2. Thinking Machines Lab ships Inkling — 975B MoE, Apache-2.0, plus Tinker fine-tuning {#2-inkling}

**What happened:** **Mira Murati's Thinking Machines Lab** released its first product: **Inkling**, a **975B-total / 41B-active MoE** with:

- **1M-token context**, native **text + image + audio** multimodality.
- **Pretrained on 45T multimodal tokens**.
- Released **Apache 2.0 on Hugging Face** in **BF16** and **NVFP4** variants, plus **speculative MTP (multi-token prediction) layers**.
- Companion release: **"Inkling-Small"** 276B preview + the **Tinker fine-tuning platform** for training custom variants.

**Sources:**
- [Thinking Machines Lab — Introducing Inkling](https://thinkingmachines.ai/news/introducing-inkling/) `[primary]`
- [TechCrunch — Thinking Machines amps up its bet against one-size-fits-all AI with its first open model, Inkling](https://techcrunch.com/2026/07/15/thinking-machines-amps-up-its-bet-against-one-size-fits-all-ai-with-its-first-open-model-inkling/) `[secondary]`
- [VentureBeat — Thinking Machines open sources first multimodal language model Inkling](https://venturebeat.com/technology/thinking-machines-open-sources-first-multimodal-language-model-inkling-focused-on-low-cost-and-resistance-to-censorship) `[secondary]`

### Why it matters to you

- **Job:** **TML is now a live "5th lab" hiring destination** — smaller than Anthropic/OpenAI, likely higher equity leverage for early joiners. Important context: **Meta poached 5 TML co-founders** in the past 90 days (including Andrew Tulloch on a reported **$1.5B** package), so TML is **actively backfilling** senior IC and research roles.
- **Startup:** **You can now build a defensible vertical product on a customizable near-trillion-param open model** without begging OpenAI/Anthropic for access. Tinker is Meta-Llama-Stack scale of ambition, from a US-native lab, under Apache-2.0. Every "vertical-Claude-for-X" wedge in [STARTUPS.md](../STARTUPS.md) now has a *bring-your-own-model* alternative worth pricing out.
- **Insight:** The **open frontier is now genuinely competitive** — GLM-6, DeepSeek-V4, Kimi K3, MiniMax M-2, and now a US-native Apache-2.0 model at 1T scale. The "closed frontier only" thesis is officially back in question — plan for a world where the price of a fine-tunable near-frontier model is ~$0.

**Tags:** `#open-source #foundation-model #multimodal #moe #huggingface #tinker`

---

## 3. Emergent hits $1.5B on $130M Series C — India's 13-month AI-coding unicorn {#3-emergent}

**What happened:** **Emergent** — Bangalore-based, founded June 2025 by brothers **Mukund and Madhav Jha** — raised **$130M Series C at $1.5B post** (5× jump in six months).

- **Round:** Led by **PE firm Creaegis**; follow-ons: **Khosla, SoftBank Vision Fund 2, Lightspeed, Y Combinator**. **Total raised: $230M**.
- **Traction:** **$120M ARR** and **200K+ paying customers** building "full-stack production-ready apps" via autonomous agents.

**Sources:**
- [TechCrunch — Indian AI coding startup Emergent becomes a unicorn just over a year after launch](https://techcrunch.com/2026/07/15/indian-ai-coding-startup-emergent-becomes-a-unicorn-just-over-a-year-after-launch/) `[secondary]`
- [SiliconANGLE — Emergent emerges as latest AI unicorn](https://siliconangle.com/2026/07/15/emergent-emerges-latest-ai-unicorn-raising-130m-funding/) `[secondary]`
- [Bloomberg — Indian AI Startup Emergent Valued at $1.5B](https://www.bloomberg.com/news/articles/2026-07-15/indian-ai-startup-emergent-valued-at-1-5-billion-in-fundraising) `[primary journalism]`

### Why it matters to you

- **Job:** **AI-coding hiring is now global, not just SF**. India-based ML / agent-engineering roles are a real path — especially for anyone with OPT/H-1B uncertainty or open to remote-first geos.
- **Startup:** The **"vibe-coding for non-devs"** category (Lovable, Bolt, Emergent, Replit Agent, Cursor Web) has multiple unicorns now — differentiation is now **go-to-market and reliability**, not model access. The **13-month unicorn template** is legit: narrow wedge, aggressive velocity, ride the incumbent tailwind.
- **Insight:** A **one-year, $70M → $1.5B valuation swing** shows the AI-coding market is *still expanding faster than it's saturating* — but the tell is that Emergent won on **customer count (200K)**, not on model quality. Distribution beats model choice in this category.

**Tags:** `#funding #series-c #coding-agents #unicorn #india`

---

## 4. Neko Health $700M Series C at ~$7B — AI + hardware + owned clinics {#4-neko}

**What happened:** **Daniel Ek's (Spotify)** preventive-health clinic chain **Neko Health** closed a **$700M Series C at ~$7B post** (4× jump from Jan 2025).

- **Round:** Led by **Lightspeed** and **O.G. Venture Partners**. New backers: **Mark Zuckerberg & Priscilla Chan, Tim Ferriss, will.i.am, and OpenAI** (yes, OpenAI as a strategic investor into consumer preventive health).
- **Model:** Vertically integrated — **proprietary imaging hardware + clinical software + owned clinics**. **350K-person waitlist**. Manhattan flagship opening later this year.

**Sources:**
- [AI News — Neko Health raises $700M to expand AI body scans in the US](https://www.artificialintelligence-news.com/news/neko-health-700m-ai-body-scans-us/) `[secondary]`
- [HITConsultant — Daniel Ek's Neko Health Secures $700M](https://hitconsultant.net/2026/07/15/neko-health-raises-700-million-series-c/) `[secondary]`
- [Tech.eu — Neko Health raises $700M as demand grows for preventive health scans](https://tech.eu/2026/07/15/neko-health-raises-700m-as-demand-grows-for-preventive-health-scans/) `[secondary]`

### Why it matters to you

- **Job:** A rare **vertically integrated AI + hardware + clinical operation** hiring across **ML, computer vision, clinical infrastructure, and site ops**. Reachable if you have CV/imaging depth.
- **Startup:** Signals that **"AI + physical footprint" health plays can command frontier-lab-tier valuations**, not just SaaS multiples. The wedge is **consumer-pay preventive medicine** — a departure from US insurance-reimbursement gates.
- **Insight:** **OpenAI as a strategic investor in Neko** is a data point about OpenAI's evolving thesis: **consumer health + AI** is a market they want distribution rights into, not just a research problem.

**Tags:** `#funding #series-c #health-ai #vertical-ai #computer-vision`

---

## 5. PixVerse / AIsphere hits $439M Series C — Alibaba enters AI video, "R1 world model" {#5-pixverse}

**What happened:** **PixVerse (parent: AIsphere)**, founded April 2023 by ex-MSRA / ByteDance exec **Wang Changhu**, closed a Series C extension bringing the round to **2.98B yuan (~$439M) at >$2B valuation**.

- **Round:** **Alibaba led**, with **Lollapalooza Capital, Mirae Asset**, and others.
- **Traction:** Claims **150M+ registered users in 177 countries**.
- **Product:** New "R1" pitched as the **first real-time world model** — environments generated on-the-fly in response to player actions.

**Sources:**
- [Caixin — Alibaba Leads $439M Funding Round for AI Video Startup AIsphere](https://www.caixinglobal.com/2026-07-15/alibaba-leads-439-million-funding-round-for-ai-video-startup-aisphere-102464241.html) `[secondary]`
- [DealStreetAsia — PixVerse's Series C reaches $439m as Alibaba joins extension round](https://www.dealstreetasia.com/stories/pixverse-series-c-funding-extension-488982) `[secondary]`
- [TFN — Video generation startup PixVerse lands $439M](https://techfundingnews.com/video-generation-startup-pixverse-lands-439m-from-alibaba-and-others-to-reshape-entertainment/) `[secondary]`

### Why it matters to you

- **Job:** **World-model / real-time interactive-video engineering** is a fresh subfield hiring across CV, RL, and rendering. Odyssey / Runway / Kling / PixVerse are all live-hiring in H2 2026.
- **Startup:** With OpenAI Sora reportedly **retracting from the market**, this is a **global consolidation moment** — Runway, Kling, PixVerse, Odyssey are the survivors. If you're founding, pick a specific *use case* (gaming, ads, education), not a horizontal video generator.
- **Insight:** **The Chinese AI ecosystem is quietly building the world-model foundations** that could power the next wave of gaming / simulation. Xi's WAIC framing ([`01` §2](./01-big-lab-moves.md#2-gemini-3-5-pro)) makes more sense in that light.

**Tags:** `#funding #series-c #video-ai #world-models #china`

---

## 6. Oak exits stealth with $60M seed — identity for AI agents {#6-oak}

**What happened:** **Oak** — Israeli AI-native IAM startup, co-founded by **Shai Morag** (whose prior startup Ermetic sold to Tenable for $265M in 2023) — exited stealth with a **$60M seed** co-led by **Accel, CRV, and Greylock**, plus **AlphaDrive, Hetz, and angels**.

- **Product:** A **live identity graph** across **humans + service accounts + AI agents**, built from raw evidence, with real-time risk decisions and root-cause remediation.
- **Traction:** Already **GA with 50 employees** and enterprise customers.

**Sources:**
- [TechCrunch — Oak steps out of stealth to fix the identity mess that AI agents are making worse](https://techcrunch.com/2026/07/15/backed-by-60m-in-funding-oak-steps-out-of-stealth-to-fix-the-identity-mess-that-ai-agents-are-making-worse/) `[secondary]`
- [PR Newswire — Oak Raises $60M in Seed Funding](https://www.prnewswire.com/news-releases/oak-raises-60m-in-seed-funding-to-build-the-ai-native-identity-operating-system-302826349.html) `[primary]`
- [SecurityWeek — Oak Emerges From Stealth Mode With $60 Million](https://www.securityweek.com/oak-emerges-from-stealth-mode-with-60-million-in-funding/) `[secondary]`

### Why it matters to you

- **Job:** **"Non-human identity" and agent-security** is a brand-new hiring lane — **Accel + CRV + Greylock triple-leading a seed** is a rare signal. If you're security-inclined with agent-stack knowledge, this is a high-optionality early join.
- **Startup:** A textbook example of the **emerging "agentic governance" category** — you can't ship agents in enterprises without answering *"what can this agent access, and why."* This is the **agent-identity/KYC wedge** I've been tracking in [STARTUPS.md](../STARTUPS.md) — now anchored by a $60M seed, so promote it to `researching` status or move on to a more open lane.
- **Insight:** **The security perimeter is being rebuilt around identity, not networks.** Every AI-agent product will now need an IAM plan. Oak, Astrix, Entro, Silverfort — this category is going to consolidate fast.

**Tags:** `#funding #seed #agents #security #iam #stealth-exit`

---

## 7. Rime $24M Series A — speech-to-speech foundation model, 100M calls/mo {#7-rime}

**What happened:** **Rime** — founded by **Lily Clifford** (Stanford linguistics PhD), **Brooke Larson** (ex-Amazon Alexa), and **Ares Geovanis** — raised **$24M Series A** led by **M13**, with **Twilio Ventures, Corazon, Unusual, Cadenza**.

- **Team:** **Rafael Valle** (ex-Meta Superintelligence Labs / NVIDIA audio) joined as **Chief Scientist**.
- **Traction:** Serving **100M+ calls/month** across enterprise clients incl. **Mayo Clinic, Dialpad, Upstart, Asurion**.
- **Product:** Building the **"first enterprise-ready speech-to-speech foundation model."**

**Sources:**
- [TechCrunch — Rime picks up $24M Series A to help enterprises field customer calls](https://techcrunch.com/2026/07/15/rime-picks-up-24m-series-a-to-help-enterprises-field-customer-calls/) `[secondary]`
- [Business Wire — Rime Raises $24 Million Series A](https://www.morningstar.com/news/business-wire/20260715773471/rime-raises-24-million-series-a-to-build-the-worlds-first-enterprise-ready-speech-to-speech-model) `[primary]`

### Why it matters to you

- **Job:** **Voice AI hiring is heating up on the model side, not just app side** — speech-to-speech researchers are the new NLP hires. Rime, ElevenLabs, Cartesia, Wispr, PolyAI are all senior-IC hunting.
- **Startup:** **Vapi, Bland, Retell, PolyAI, Rime** — voice-agent infra is fragmenting; the winner will be whoever nails **proprietary training data + enterprise reliability**, not the largest model.
- **Insight:** **Voice is the interface layer for the coming wave of enterprise agent deployments** — customer support alone is a >$100B TAM. Note the *Mayo Clinic* customer — healthcare voice is a real wedge, not a demo.

**Tags:** `#funding #series-a #voice-ai #speech-to-speech #agents`

---

## 8. Also this week — the emerging enterprise-plumbing tier {#8-plumbing-tier}

Rapid-fire, one line each — each independently significant, together the strongest week for enterprise-plumbing rounds in Q3 2026.

- **Thira** — **$21M seed** led by **Madrona**, with **FUSE**. Bellevue-based, from **Apptio co-founders Sunny Gupta and Kurt Shintaffer**. Building an **"agentic system of execution" for enterprise back-office IT** (onboarding, access provisioning, software-purchase approvals). 10 design-partner enterprises; broader launch this fall. Serial-founder-backed → likely the safest agent-startup early join right now. → [GeekWire](https://www.geekwire.com/2026/apptio-co-founders-reunite-to-launch-enterprise-ai-startup-thira-with-21m-in-funding-led-by-madrona/) `#seed #agents #back-office`

- **microagi** — **$55M seed** led by **Hummingbird**, with **Northzone, LocalGlobe, Village Global, Redalpine**. Munich-based, from ex-Red Bull Racing F1 engineer **Bercan Kilic (CEO)** and CTO **Nico Nussbaum**. Captures factory + household data (incl. 20K people filmed doing chores), scales in simulation, fine-tunes plant-specific humanoid robotics models. **Germany's largest seed round ever.** → [Sifted](https://sifted.eu/articles/munich-robotics-startup-microagi-raises-55m-germanys-largest-ever-seed-round) `#seed #robotics #humanoids #europe`

- **NetApp acquires DataPelago** — terms undisclosed. DataPelago's **"Nucleus" engine** does CPU+GPU-accelerated data processing at the storage layer — up to **80% infra cost reduction, 10× perf** vs conventional. NetApp becomes the **"zero-copy activation of enterprise data for AI"** vendor. → [NetApp](https://www.netapp.com/newsroom/press-releases/news-rel-20260716-210092/) `#acquisition #data-ai #enterprise`

- **Ramp launches Token Spend Management** (July 16) — a product-level signal. Ramp finance-team tooling now **tracks token spend across providers**. Underlying data: **top 1% of firms spend $7,500 per employee per month on AI (up 14.1% MoM); median $11.38.** Ramp Economics Lab finding: **"companies investing heavily in AI hire more"** — flipping the layoff narrative. → [SiliconANGLE](https://siliconangle.com/2026/07/16/ramp-targets-ais-fastest-growing-cost-expanded-token-spend-tracking/) · [Ramp AI Index](https://ramp.com/data/ai-index) `#finops #ramp #hiring-signal`

### Why the *set* matters

Every one of these is **infrastructure between the model and the app**, not a model or an app. Read as a portfolio, the week's message is: **the frontier is being commoditized by open weights (Inkling), by customizable inference (Fireworks), and by cross-lab tenancy (Google-SpaceX, Anthropic-Colossus)** — and the money is flowing into the *middleware*. Any "vertical-AI-for-X" wedge in [STARTUPS.md](../STARTUPS.md) is now competing against an increasingly commodified stack; **the durable startups this week are all middleware** (Ramp for cost, Oak for identity, Rime for voice, Thira for back-office, Fireworks for inference).

**Category that got hot this week:** **enterprise-agent middleware** — identity, voice, back-office, inference, FinOps — with Fireworks providing the customizable-inference backbone and Thinking Machines' Inkling providing the open-weights alternative to close out a **$2.5B+ week** for the agent stack.
