# Big Lab Moves — 2026-07-12

A four-front week for the frontier. **Apple opened a courtroom** — suing OpenAI in federal court in the Northern District of California on Friday, alleging trade-secret theft across the hardware push. **OpenAI opened the retail door** — the GPT-5.6 Sol/Terra/Luna family went from "small trusted-partner group" (US-government-requested) to global GA on Thursday, plus the ChatGPT Work agentic surface. **Anthropic opened its books** — run-rate crossed $30B (roughly 3.3× its end-of-2025 baseline), backed by an SEC-visible 3.5-GW Google+Broadcom TPU deal that comes online in 2027. And **Google is holding one door for next week** — Gemini 3.5 Pro is targeted for GA on Wednesday July 17, a rebuild-from-scratch generation with a 2M-token context and a Deep-Think reasoning tier behind the $250/mo Ultra plan.

Tags: `#labs #apple #openai #anthropic #google #gpt-56 #gemini #tpu #hardware #lawsuit #compute #revenue`

---

## 1. Apple sues OpenAI (NDCA, Jul 10, trade-secret theft) {#1-apple-openai}

**What happened:** Apple filed a **trade-secret-theft complaint against OpenAI** in the **US District Court for the Northern District of California** on **Friday, July 10, 2026**. Selected allegations from public reporting:

- **Structural claim:** OpenAI's alleged conduct was **"at every level"** of its hardware effort — not one incident but a pattern.
- **The hardware chief:** OpenAI's hardware lead **Tang Tan** is a **former Apple vice president** (led AirPods and iPhone product design). Apple alleges Tan directed *Apple-employee interview candidates* to bring **"actual parts" from Apple** for "show and tell" during interviews at OpenAI.
- **Employee migration + laptop theft:** Apple alleges OpenAI **coached departing Apple employees on how to evade Apple's exit-security process**, and separately that ex-Apple employee **Chang Liu stole an Apple laptop** on the way out.
- **Scale:** more than **400 former Apple employees** now work at OpenAI.
- **Backdrop:** OpenAI bought Jony Ive's hardware startup **IO Products for $6.4B** in 2025; the ChatGPT-in-iPhone integration announced in 2024 is now, effectively, over.

**Sources:**
- [CNBC — Apple sues OpenAI alleging trade secret theft, says scheme was 'at every level'](https://www.cnbc.com/2026/07/10/apple-openai-lawsuit-trade-secrets.html) `[secondary]`
- [TechCrunch — Apple sues OpenAI over alleged trade secret theft](https://techcrunch.com/2026/07/10/apple-sues-openai-over-alleged-trade-secret-theft/) `[secondary]`
- [Washington Times — Apple files lawsuit accusing ChatGPT maker OpenAI of stealing trade secrets](https://www.washingtontimes.com/news/2026/jul/11/apple-sues-openai-accused-stealing-trade-secrets/) `[secondary]`
- [Japan Times — Apple sues OpenAI for trade secret theft in pivotal case](https://www.japantimes.co.jp/business/2026/07/11/tech/apple-sues-openai-secret-theft/) `[secondary]`
- [Business Today — Apple sues OpenAI over alleged trade secret theft: what happened and why it matters](https://www.businesstoday.in/technology/news/story/apple-sues-openai-over-alleged-trade-secret-theft-what-happened-and-why-it-matters-542373-2026-07-11) `[secondary]`

### Why it matters to you

- **Job lens:** Two second-order hiring waves. (a) **Apple hardware-AI hiring will get gated tighter** — expect stronger IP-clean-room language in offers and slower cross-lab moves; if you have iOS/Vision/silicon on your resume, the value of that specific skill just went up because Apple can't cheaply refill the seat. (b) **OpenAI hardware — the lawsuit is a *hiring shield*** for candidates without Apple in their background: no exit-scrub problem, no discovery risk. If your resume is "clean" of Apple hardware IP, OpenAI's IO Products org is a rare open lane at a lab where lanes usually close on Monday.
- **Startup lens:** The **hardware frontier just became the AI frontier in public.** When models commoditize, the moat migrates down the stack — silicon (Broadcom/Anthropic §3), form factor (IO Products), on-device inference. For a founder, the meaningful signal is: **the labs believe distribution = device**, not app. This is the strongest possible endorsement of the "AI-hardware wearable / new form factor" wedge (though it also means the $6.4B floor to compete is real).
- **Insight:** This complaint doesn't get filed if Apple thinks it can build the same product internally on the same timeline. Read the *filing* as an admission of Apple's timeline anxiety — Cook's team is losing the internal race and needs discovery to slow OpenAI down. Watch the docket for **the preliminary injunction motion**: if Apple asks for one, the timeline pressure is real; if it doesn't, this is a slower long-tail damages play.

→ Cross-link: [2026-05-22/01 §2 OpenAI S-1](../2026-05-22/01-big-lab-moves.md#2-openai-s1) — the Apple suit is now a material risk-factor the S-1 will have to disclose.

---

## 2. OpenAI ships the GPT-5.6 family globally: Sol · Terra · Luna + ChatGPT Work {#2-gpt56}

**What happened:** After a **~2-week US-government-requested "small trusted-partner group" preview**, **OpenAI publicly released the GPT-5.6 family on Thursday, July 10, 2026.** Three-model naming with distinct positioning:

- **Sol** — flagship. Tuned for **biology, chemistry, cybersecurity**; per Sam Altman, **54% more token-efficient on coding tasks** than the prior generation.
- **Terra** — mid-cost general workhorse.
- **Luna** — fastest, cheapest, latency-optimized.

Simultaneously OpenAI shipped **ChatGPT Work** — an **agentic productivity surface** that merges the Codex coding agent into the ChatGPT desktop app and exposes a **15-integration plugin directory** for creating documents, spreadsheets, presentations, and web apps at length ("hours-long" runs). Marketed as the *"complete a wider range of complex professional tasks for hours at a time"* product.

**Sources:**
- [TechCrunch — OpenAI launches its new family of models with GPT-5.6](https://techcrunch.com/2026/07/09/openai-launches-its-new-family-of-models-with-gpt-5-6/) `[secondary]`
- [Axios — OpenAI releases GPT-5.6 and ChatGPT Work tool](https://www.axios.com/2026/07/09/ai-openai-gpt-release) `[secondary]`
- [CNBC — OpenAI to publicly release GPT-5.6, rolls out conversational AI models](https://www.cnbc.com/2026/07/08/openai-expanding-gpt-5point6-ai-model-release-ending-government-limits.html) `[secondary]`
- [Nextgov/FCW — OpenAI's advanced GPT-5.6 models to be publicly released](https://www.nextgov.com/artificial-intelligence/2026/07/openais-advanced-gpt-56-models-be-available-public/414651/) `[secondary]`
- [Crypto Briefing — OpenAI releases GPT-5.6 models to 20 partners, public launch expected by July 2026](https://cryptobriefing.com/openai-releases-gpt-56-models-to-20-partners-public-launch-expected-by-july-2026/) `[secondary]`
- [Bloomberg — OpenAI to Roll Out Top AI Model Globally After Limited Preview](https://www.bloomberg.com/news/articles/2026-07-08/openai-to-roll-out-top-ai-model-globally-after-limited-preview) `[secondary]`
- [GuruFocus — OpenAI Unveils ChatGPT Work Ahead of Potential IPO](https://www.gurufocus.com/news/8952863/openai-unveils-chatgpt-work-ahead-of-potential-ipo) `[analysis]`

### Why it matters to you

- **Job lens:** The **Sol biology/chemistry/cybersecurity specialization** is a giveaway of where OpenAI wants its next wave of vertical FDE deals — expect the AI Solutions / FDE JD language to shift from "generalist AI product" toward **"applied AI in regulated science / infosec workflows."** Update your resume to speak that vocabulary if biology, chem, or cyber is anywhere in your background. Separately: **ChatGPT Work's plugin directory is the OpenAI equivalent of Anthropic's MCP surface** — a *15-integration launch set* means OpenAI needs Integration Engineers who can build the next 100.
- **Startup lens:** ChatGPT Work is an **explicit Microsoft 365 Copilot / Google Workspace direct attack** — office-productivity moves from an assistive sidebar to a *hours-long agent that owns the doc*. For founders: (a) any "AI wrapper over Google Docs / Sheets" idea just competed with a shipped OpenAI product, so pick a *deeper vertical* (legal-brief drafting, MSSP tier-1 triage, biotech ELN) or a *tighter workflow* (specific compliance-heavy step); (b) 54% token efficiency on Sol means your unit economics on any OpenAI-hosted product just improved ~30–50% — reprice, don't just keep the margin.
- **Insight:** The **government-requested 2-week hold** is the story under the story. Read it as (a) the informal-EO era from May didn't disappear — pre-release access is now a *norm*, not a *rule*; (b) OpenAI *complied willingly* — Sam is optimizing for state trust, not just user growth; (c) Sol is *powerful enough* that CAISI/CISA had a real reason to want a look. Whatever "Sol tuned for biology/chemistry/cybersecurity" means empirically, the government thought it deserved a preview.

→ Cross-link: [`02` §3 ChatGPT Work as agentic productivity surface](./02-new-emerging.md#3-chatgpt-work) · [2026-05-22/01 §1 EO postponed](../2026-05-22/01-big-lab-moves.md#1-eo-postponed) — the *voluntary* pre-release model won by not being written down.

---

## 3. Anthropic run-rate crosses $30B; 3.5-GW Google+Broadcom TPU deal is public {#3-anthropic-30b}

**What happened:** Two data points, one story.

- **Revenue side:** In its own newsroom post, Anthropic reports **run-rate revenue "surpassed $30B"**, up from **~$9B at end-of-2025** — roughly **3.3× in seven months.** More than **1,000 business customers now spend $1M+ on an annualized basis.**
- **Compute side:** Anthropic's expanded partnership with **Google and Broadcom** covers **multiple gigawatts of next-generation TPU capacity**. A **Broadcom SEC filing** puts the number at **3.5 GW**, coming online **starting in 2027**. Compute will be housed in the US and sits inside Anthropic's larger **$50B US-compute commitment.**

Framing in Anthropic's own words: this expansion is to serve "extraordinary demand" from Claude customers.

**Sources:**
- [Anthropic — Anthropic expands partnership with Google and Broadcom for multiple gigawatts of next-generation compute](https://www.anthropic.com/news/google-broadcom-partnership-compute) `[primary]`
- [Yahoo Finance — Anthropic secures access to 3.5 gigawatts of compute capacity in Google and Broadcom partnership](https://finance.yahoo.com/sectors/technology/articles/anthropic-secures-access-3-5-124717374.html) `[secondary]`
- [CNBC — Broadcom agrees to expanded chip deals with Google, Anthropic](https://www.cnbc.com/2026/04/06/broadcom-agrees-to-expanded-chip-deals-with-google-anthropic.html) `[secondary]`
- [Data Center Knowledge — Anthropic Secures Multi-Gigawatt TPU Deal With Google, Broadcom](https://www.datacenterknowledge.com/data-center-chips/anthropic-secures-multi-gigawatt-tpu-deal-with-google-broadcom) `[analysis]`
- [Futurum — Anthropic's Gigawatt-Scale TPU Deal with Broadcom Creates a Structural Advantage](https://futurumgroup.com/insights/anthropics-gigawatt-scale-tpu-deal-with-broadcom-creates-a-structural-advantage/) `[analysis]`
- [TechCrunch — Anthropic ups compute deal with Google and Broadcom amid skyrocketing demand](https://techcrunch.com/2026/04/07/anthropic-compute-deal-google-broadcom-tpus/) `[secondary]`

### Why it matters to you

- **Job lens:** $30B run-rate + >1,000 customers >$1M ARR = **a real, funded, growing revenue-facing org.** The concrete lanes hiring against this number: **Solutions / FDE / Customer Engineering / Deployment / Post-Sales Engineering**. The `>$1M ARR customer` threshold is the Anthropic FDE JD's primary internal customer definition — if your resume says "shipped a customer-facing AI integration that hit revenue," you are speaking their exact language. Cross-link the ME.md focusing decision: this is not a directional signal anymore, it's a compounding one.
- **Startup lens:** The **3.5-GW deal coming online in 2027, not now,** is a *forward guarantee of the supply-side moat.* For a founder building on Anthropic: you can price a 12–24 month product roadmap against a supply promise that is now on a Broadcom SEC filing. For a founder building *against* Anthropic (open-weight, alt-vendor): the same filing is your **timing constraint** — you have to reach product-market fit before the 2027 supply wave, because after it the cost/latency picture shifts against you.
- **Insight:** The **rate of ramp** is the whole story. **~9→30B in seven months** is not typical enterprise-SaaS shape — this is *installation* velocity. Enterprises are wiring Claude into workflows they can't easily unwire, which is why the compute commitment is *forward-loaded* rather than *incremental*. The best mental model: Anthropic is behaving like a public utility scaling to a new demand curve, and the "public listing" thread from May is best re-read as **investors buying access to a utility with agentic-workflow lock-in, not to a chat-model with brand.**

→ Cross-link: [2026-05-21/01 §2 Anthropic Colossus tenancy $1.25B/mo](../2026-05-21/01-big-lab-moves.md#2-anthropic-colossus) — the *near-term* compute (H100/H200/GB200 on Colossus 1) and the *long-term* compute (TPU on Broadcom) are now stitched into a single ~5-year supply plan.

---

## 4. Gemini 3.5 Pro is targeted for GA on Wednesday July 17 {#4-gemini-35-pro}

**What happened:** Widely reported target: **Google DeepMind will release Gemini 3.5 Pro on Wednesday, July 17.** Details reported so far:

- **2-million-token context window** — *double* the current frontier ceiling (Claude Sonnet 5 native 1M; GPT-5.6 has not yet published context).
- **Deep Think** — an extended-reasoning mode described as a distinct "reasoning layer," **gated behind Google's $250/mo AI Ultra subscription** (from the May 20 I/O reveal).
- **Ground-up rebuild** — reportedly *not* a 2.5 point release; a new architecture aimed at math, SVG scene generation, and image quality vs. GPT-5.6 Sol and Claude Fable 5.
- **Caveat:** as of the last confirmed pull (July 7), **no official Google model card, pricing page, or launch post has been published**; July 17 is a *target*, not a *scheduled event.* Treat as `[rumor]` until Wednesday.

**Sources:**
- [Geeky Gadgets — Google Gemini 3.5 Pro Leaks with 2 Million Context Window](https://www.geeky-gadgets.com/google-gemini-3-5-pro-leaks/) `[secondary]`
- [BiggoFinance — Google Delays Gemini 3.5 Pro Launch to July 17 for Full Architectural Rebuild](https://finance.biggo.com/news/6f0c6bb2-795f-4c57-9d09-6db691d7638a) `[analysis]`
- [TechTimes — Gemini 3.5 Pro Targets July 17 as DeepSeek's July 24 Deadline Hits Developers Now](https://www.techtimes.com/articles/319877/20260708/gemini-35-pro-targets-july-17-deepseeks-july-24-deadline-hits-developers-now.htm) `[analysis]`
- [Developers Digest — Gemini 3.5 Pro Developer Guide: 2M Context Window and Deep Think Mode](https://www.developersdigest.tech/blog/gemini-3-5-pro-developer-guide-2026) `[analysis]`
- [Zoom Bangla / iNews — Google's Gemini 3.5 Pro Nears General Availability Release](https://inews.zoombangla.com/googles-gemini-3-5-pro-nears-general-availability-release/) `[rumor]`

### Why it matters to you

- **Job lens:** If 2M native context is real, the **long-context / multi-doc RAG interview question just shifted.** The framing "we chose RAG over long context because of cost / staleness / recall" needs to update — for a $250/mo Ultra tier, **long-context becomes viable at production cost.** Rehearse: *when does RAG still win over 2M-context Gemini?* (Answer: cross-tenant data governance, retrieval-audit trails, per-document access control — all still hard in one giant context call.) That's a defensible, well-informed answer for a 2026 interview.
- **Startup lens:** If Google gates Deep Think behind a $250 consumer tier, the **Deep Think API pricing will land somewhere north of Claude Opus 4.7.** Think about whether your product's *hard-reasoning* dependency is *routine enough* to price against $250 Ultra, or *bursty enough* to route to Deep Think per-call. This is the same "premium-reasoning routing" pattern that made the Opus-orchestrator / Sonnet-worker split matter — the vocabulary generalizes.
- **Insight:** Three architecturally different reasoning surfaces are now on the market inside three weeks: **OpenAI Sol** (biology/chem/cyber tuning) · **Anthropic Sonnet 5** (default-model 1M native context, promo-priced) · **Google Deep Think** (dedicated reasoning tier). The **portfolio play** — being fluent in all three, per-workflow — is more valuable than picking one and going deep. Your ME.md focusing decision (Anthropic-first, multi-vendor as production discipline) is exactly the correct posture for this quarter.

→ Cross-link: [`03` §3 the 3-model comparison table to publish Wed Jul 15 12:30 PM PT](./03-practical-skills-and-tools.md#3-io-day-table).
