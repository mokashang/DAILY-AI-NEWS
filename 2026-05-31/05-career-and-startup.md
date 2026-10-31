# Career & Startup — 2026-05-31

The single highest-leverage week of 2026 so far for the artifact-first, Anthropic-stack-committed lane you're on. Anthropic's **$65B / $965B raise** ([`01` §1](./01-big-lab-moves.md#1-anthropic-65b)) → headcount in a ~4×/year regime; **Bloomberg's May 28 profile** of Anthropic recruiting hammers the **artifacts-over-pedigree** message explicitly. **FDE postings industry-wide are up 729% YoY** (643 → 5,330). **OpenRouter's $113M Series B** ([`02` §4](./02-new-emerging.md#4-openrouter)) confirms the gateway/router layer as a fundable category — meaning standalone roles (eval engineer, gateway SRE) at OpenRouter / Portkey / Helicone / LangSmith multiply through Q3. **Meta's May 20 restructure** is now in execution and **~7K headcount redirected into Applied AI Engineering / Agent Transformation** — those reqs reopen in 2–4 weeks. **AI Engineer World's Fair is exactly 4 weeks out (June 29–July 2)** — this is the last realistic week to lock 1:1s.

Tags: `#jobs #fde #anthropic #openai #meta #funding #conference #portfolio #newgrad`

---

## 1. OpenRouter $113M Series B confirms gateway/router as a hiring vector — and a fundable founder thesis {#1-router-category}

**What happened (2026-05-26):** **OpenRouter** raised **$113M Series B led by CapitalG**, with NVentures (Nvidia), ServiceNow, MongoDB, Snowflake, Databricks Ventures + existing a16z and Menlo, at a **$1.3B post-money** (>2× from $547M in June 2025). 25T tokens/week, 8M+ developers across 400+ models. Full deal detail in [`02` §4](./02-new-emerging.md#4-openrouter).

### Implication for you

Model-routing / observability / governance is now a **standalone, fundable category** — meaning standalone titles ("Gateway SRE", "Eval Engineer", "Model Operations PM", "Routing PM") at **OpenRouter, Portkey, Helicone, LangSmith, Braintrust** are about to multiply through Q3. **Build one public artifact this week** that lives in this category:

- An open-source router (Python OK, LiteLLM-style) that picks between Claude 4.8 / Gemini 3.5 Flash / GPT-5.5 / DeepSeek V4 with a documented cost/quality trade-off curve on a real workload.
- OR a public benchmark/dashboard comparing model performance + cost on **your** real workload (Claude Code session logs, your research-coding workflow, an agentic eval pipeline).
- OR a small "router-as-a-service" MCP server (this is the highest-leverage version: it lives in the Anthropic stack, ships as a single artifact, and matches the FDE category in §2 below).

That single repo is more recruiter-legible than another LeetCode grind — and it's *exactly* what an OpenRouter or Portkey hiring manager looks for. Doubles as a founder-thesis demo if you decide to pitch a vertical router startup (healthcare PHI-redaction routing, finance-compliance routing).

**Sources:**
- [OpenRouter — Raises $113M Series B](https://openrouter.ai/announcements/series-b) `[primary]`
- [TechCrunch — OpenRouter doubles valuation to $1.3B](https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/) `[secondary]`

Tags: `#funding #infra #routing #jobs #openrouter`

---

## 2. Anthropic Forward Deployed Engineer — Manager req posted May 15, IC reqs live, $250K+ TC {#2-anthropic-fde}

**What happened:** Anthropic posted a **Manager, Forward Deployed Engineering** req on **May 15** and continues to actively hire FDEs across Applied AI, Federal Civilian, and partner-aligned tracks. Industry-wide:

- **FDE postings: 643 (Apr 2025) → 5,330 (Apr 2026) — +729% YoY**
- Senior FDE base: **$215K–$310K**; frontier-lab TC **routinely clears $500K**
- Anthropic SWE TC band (Levels.fyi, May 29): **$563K–$785K**
- The role embeds engineers with strategic customers to ship **MCP servers, sub-agents, and Agent Skills** — *exactly* the stack you're already committed to per [`ME.md`](../ME.md).

### Implication for you

**This is the cleanest possible match for the AI Integration Engineer lane.** The official bar is "3+ years technical-customer experience OR former technical founder" — but **internships + a public agentic-system portfolio substitute for years**. The funnel-bypass move:

1. Open the [Anthropic FDE Applied AI req on Greenhouse](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) in a tab.
2. Ship a single non-trivial **public MCP server** by Wednesday (pick a tool you actually know — a niche API in your research area, a research-workflow wrapper, your university's course-catalog API).
3. Write a ~1,500-word "what broke, what I learned" blog post.
4. Put the artifact at the **literal top of your resume** (per Anthropic's own careers-page instruction, see §3).
5. Submit the application + a 90-second Loom of you debugging a real Claude Agent SDK integration end-to-end.

**Sources:**
- [Anthropic FDE Applied AI req](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) `[primary]`
- [MarkTechPost — What is a Forward Deployed Engineer](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/) `[analysis]`
- [Levels.fyi — Anthropic SWE](https://www.levels.fyi/companies/anthropic/salaries/software-engineer) `[primary]`
- [The New Stack — Why OpenAI and Anthropic are hiring FDE teams](https://thenewstack.io/forward-deployed-engineers-ai/) `[analysis]`

Tags: `#jobs #fde #anthropic #mcp #compensation`

---

## 3. Bloomberg profiles Anthropic's hiring funnel (May 28): "$250K+ packages, the resume bar isn't what you think" {#3-bloomberg-funnel}

**What happened (2026-05-28):** Bloomberg published a feature on Anthropic's recruiting emphasizing:

- **$250K+ entry-level packages**
- **Explicitly non-traditional backgrounds** — "bringing in diverse careers to build Claude"
- **Anthropic's own careers page reinforces:** *"If you have done interesting independent research, written an insightful blog post, or made substantial contributions to open-source software, put that at the TOP of your resume."*

Headcount trajectory:
- **~1,000–1,100** (most of 2025)
- **~4,585** (Feb 2026)
- **Roughly 4×/year regime**, accelerated by the $65B raise
- OpenAI is targeting **~8,000 employees by end of 2026** (from ~4,500 early 2026)

### Implication for you

PhDs and FAANG pedigree are **not** the gating filter at Anthropic right now. **Legible public artifacts are.** Spend this week shipping one of:

- (a) A substantive technical blog post (~2,000 words) on the Anthropic agentic stack — e.g., "What I learned building 5 Claude Skills in a week"
- (b) A non-trivial open-source MCP server (matches §2 directly — same artifact, two uses)
- (c) An in-depth eval of Claude Code (or Opus 4.8 / dynamic workflows) on a real codebase using Hamel's `eval-audit` Skill ([`03` §3](./03-practical-skills-and-tools.md#3-eval-audit))

Then **put it at the literal top of your resume** — Anthropic's careers page is telling you exactly what to do, in plain English. Most candidates will not do this. Be the one who did.

**Sources:**
- [Bloomberg — Anthropic Job Recruiting Brings In Diverse Careers](https://www.bloomberg.com/news/features/2026-05-28/anthropic-job-recruiting-brings-in-diverse-careers-to-build-claude) `[primary]`
- [Anthropic Careers page](https://www.anthropic.com/careers) `[primary]`
- [Data Exec — Breaking Into AI in 2026: What Anthropic, OpenAI and Meta actually hire for](https://dataexec.io/p/breaking-into-ai-in-2026-what-anthropic-openai-and-meta-actually-hire-for) `[analysis]`

Tags: `#anthropic #jobs #portfolio #newgrad`

---

## 4. Meta's May 20 restructure — 8K cuts + 6K reqs canceled, but 7K *redirected* into Applied AI Engineering / Agent Transformation {#4-meta-restructure}

**What happened (2026-05-20, now in execution):**

- **~8,000 layoffs** (~10% of workforce); **6,000 open reqs canceled** = ~14,000 effective headcount reduction
- **2,212 of the cuts were HQ software engineers**
- **~7,000 workers redirected** into new units: **Applied AI Engineering, Agent Transformation Accelerator XFN, Central Analytics**
- 2026 capex: **$115B–$135B**
- Reported individual elite-AI-hire packages: **up to $1.5B**
- Tech-industry YTD layoffs: **142,000**; TrueUp projects **370,000** by year-end

### Implication for you

The signal isn't "Meta is shrinking" — it's **"Meta is rebuilding the org chart around agent-shaped work, and the new teams have headcount."** Three specific moves:

1. **Watch Meta's careers page** through the next 2–4 weeks for **"Applied AI Engineer"** and **"Agent Transformation"** reqs to reopen — these are the inheritors of the canceled reqs.
2. **Don't apply to old "Machine Learning Engineer" listings** — those are the slots being cut. Filter strictly on titles containing "Agent" or "Applied AI."
3. **Lead with agentic-system artifacts**, not Kaggle competitions. The selection function changed; your application has to acknowledge that.

**Sources:**
- [NPR — Meta slashes 8,000 jobs](https://www.npr.org/2026/05/20/nx-s1-5826917/meta-layoffs-ai-jobs) `[primary]`
- [TNW — Meta cuts 8,000 jobs, cancels 6,000 reqs](https://thenextweb.com/news/meta-layoffs-8000-ai-restructuring-may-2026) `[secondary]`
- [Yahoo Finance — Layoffs accelerate May 2026](https://finance.yahoo.com/sectors/technology/articles/layoffs-accelerate-may-2026-firms-040430218.html) `[secondary]`

Tags: `#layoffs #meta #agents #faang #jobs`

---

## 5. Catena Labs $30M Series A — Circle co-founder's "AI-agent payment rails" startup is hiring humans now {#5-catena}

**What happened (2026-05-20, ongoing):** **Sean Neville (Circle co-founder)** raised a **$30M Series A** for **Catena Labs** from **Acrew Capital + a16z crypto**, with **Breyer, General Catalyst, QED** participating. The company builds **stablecoin payment + identity rails for AI agents** and has applied for a **national trust bank charter (OCC, NY)**. Team: 11 people. Asked how he'd spend the capital: **"We are hiring humans."**

### Implication for you

A Series A startup at 11 people that explicitly raised to hire is the **sweetspot for founding-engineer-with-equity** — and "agent payments / identity / authorization" is one of the few new categories where the work is genuinely net-new (not yet another LLM wrapper).

If you've ever shipped anything with **Stripe + an LLM + an identity primitive** (Passkeys, DIDs, OAuth), you're qualified to email Sean Neville directly with a working demo. **Founder-thesis adjacency:** agent-native finance, identity, and authorization (think OAuth-for-agents) are wide-open building spaces this week. If you don't want to apply to Catena, build your own thing in this lane — the market signal is loud.

**Sources:**
- [Fortune — Circle cofounder raises $30M for Catena Labs](https://fortune.com/2026/05/20/catena-labs-series-a-sean-neville-ai-native-bank/) `[primary]`
- [Blockonomi — Catena Labs $30M Series A + bank charter](https://blockonomi.com/catena-labs-raises-30m-series-a-and-files-for-national-trust-bank-charter-to-power-ai-agent-finance/) `[secondary]`

Tags: `#funding #founding-engineer #agents #fintech #startup`

---

## 6. AI Engineer World's Fair, June 29 – July 2 — book meetings THIS week {#6-aieworldsfair}

**What happened:** The **AI Engineer World's Fair** runs **June 29 – July 2** in San Francisco with **6,000+ attendees**; per the official site, this is "where the top agent and model labs… meet to debut, **hire**, and compete in the largest technical AI Expo ever."

Two compounding signals make this the highest-leverage in-person venue of the year:

1. The **Anthropic + Blackstone + Goldman + H&F $1.5B JV** ([archived 2026-05-04 cluster](../2026-05-06/01-big-lab-moves.md)) needs hundreds of FDE-shaped engineers fast. Parallel OpenAI $10B deployment-company structure has the same need.
2. The World's Fair is the **single most efficient in-person recruiting venue** for that exact archetype.

### Implication for you

The conference is **exactly 4 weeks out** — this is the last realistic week to book meetings before recruiter calendars fill up.

1. **Buy a ticket this week** (prices climb on June 1).
2. **Draft a 2-minute personal pitch** oriented around "I deploy Claude agents inside production workflows" (the same pitch arc as your FDE application in §2).
3. **Pre-schedule 1:1s** with Anthropic, OpenAI, Cognition, Sierra, Palantir, Databricks, Scale, OpenRouter, Portkey, Helicone recruiters via the conference's networking tool.
4. Bring the MCP-server-artifact from §2 + §3 on a phone-ready demo loop. Don't bring a laptop into rooms — bring a Loom.

**Sources:**
- [AI Engineer World's Fair 2026](https://www.ai.engineer/worldsfair/2026) `[primary]`
- [CNBC — Anthropic-Goldman-Blackstone $1.5B AI Venture](https://www.cnbc.com/2026/05/04/anthropic-goldman-blackstone-ai-venture.html) `[primary]`
- [Fortune — Anthropic takes shot at consulting industry](https://fortune.com/2026/05/04/anthropic-claude-consulting-industry-joint-venture-blackstone-goldman-sachs/) `[secondary]`
- [Anthropic — Building a new enterprise AI services company](https://www.anthropic.com/news/enterprise-ai-services-company) `[primary]`

Tags: `#fde #anthropic #enterprise #conference #networking`

---

## Bonus skills repricing (worth knowing, not a full item)

The market value of "**Claude Skills + MCP server authorship**" has clearly inflected. The ecosystem went from a handful of official examples to **10,000+ active public MCP servers** and **1M+ community-contributed Skills** by early 2026. Industry commentary this month frames pre-2026 "Mega-Prompt" marketplaces as "low-leverage fossils." Translation: **a single well-built, well-documented MCP server on your GitHub is now a stronger signal than a generic ML side project.** Aligns precisely with §2, §3, §6 above.

**Sources:** [Stormy AI — The 2026 Skill Economy](https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills) `[analysis]` · [Verdent — Claude Skills vs MCP vs Agents](https://www.verdent.ai/guides/claude-skills-vs-mcp-agents-comparison) `[analysis]`

## Beats with thin returns this week

- **DeepMind new-grad/intern programs** — no major announcements in window; careers page steady-state.
- **YC** — Summer 2026 batch on-time deadline (May 4) passed; late apps still open. No new batch-level news.
- **OpenAI Residency 2026** — closed earlier in year; next intake not yet announced.

---

## This week, prioritize: ship 1 MCP server + apply to Anthropic FDE + buy World's Fair ticket — same day

If you do **exactly one thing** in the next 7 days, **build and publicly ship one non-trivial MCP server** ([`03` §1–4](./03-practical-skills-and-tools.md) gives you the tooling), then **submit the [Anthropic FDE Applied AI req](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) with that artifact at the top of your resume**, and **buy a World's Fair ticket before June 1**. The rationale compounds across every signal this week:

1. Anthropic's hiring funnel explicitly weights **public artifacts over pedigree** (§3).
2. The FDE category grew **+729% YoY** and the **$1.5B Anthropic JV** is filling reqs *now* (§2, §6).
3. **OpenRouter's $113M raise** confirms the AI-integration layer is fundable, so the same artifact doubles as a founder-thesis demo and an in-person conversation prop at the World's Fair in 4 weeks (§1, §6).
4. With **142K tech layoffs YTD** and the new-grad funnel collapsed 50%+, generic resumes are filtered out — **only the legibly-differentiated ones get human review** (§3, §4).

**One MCP server, one application, one ticket. That's the play.**
