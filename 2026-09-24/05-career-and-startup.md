# Career & Startup — 2026-09-24

Hiring holds, salary bands split by tier, and the domain-expert / eval-authoring / router-designing lanes get repriced up. Bio-AI adjacent roles just widened. Safety/eval work — post-UN — is now a legitimate career lane. **Frame: the market is asking for depth in one vertical + fluency across the model tiers + one shipped artifact. Have all three by Sunday.**

Tags: `#careers #salary #startups #jobs #fde #safety #eval`

---

## 1. Hiring map — the state of the AI-engineering job market {#1-hiring-map}

**Headline numbers (source: KORE1, Axial Search, Robert Half — Sept 2026):**
- **~49,200 open AI-engineer positions** in the US, with a **3.2:1 demand/supply gap** (3.2 open roles per qualified candidate).
- **AI-engineer demand up 143% YoY.**
- **Median AI-eng salary: $176K.** Average total comp (including equity + bonus): **$242,507.**
- **Mid-level (3–5 yrs) base: $160–210K + 15–25% bonus → real loaded cost $185–265K/yr.**
- **ML-engineer median: $197K.**
- **70% of AI/ML roles are mid-level or senior IC**; only **2% are Director+.** This is a **mid-to-senior IC market** — new grads compete for the ~28% remaining band, which is narrower than it looks.
- **>75% of AI job listings now seek domain experts** — pick a vertical (bio, finance, security, legal, education, gaming) and cluster your applications.
- **Entry-level AI premium over general SWE: ~6%** (modest); **senior AI premium: ~30–40%** (large). Career math favours getting the first role fast (any AI-adjacent SWE role) then verticalising into AI depth.

**Where the 49,200 openings concentrate (rough distribution):**
- **~30% Big Tech + frontier labs** (Anthropic, OpenAI, Google, Meta, Microsoft, NVIDIA, Amazon) — high bar, high pay.
- **~35% AI-application startups** (post-Series-A, $50M–$5B valuations) — most volume, moderate bar, equity-heavy.
- **~20% Traditional enterprise integration** (Fortune 500 AI teams, consulting firms) — steady, less-glamorous, 6-month cycles.
- **~15% Government + defense** (Anduril, Scale, Palantir, defence primes, GovAI) — clearance often required.

**Which roles are up-priced in Q3–Q4 2026 specifically:**
1. **AI Integration Engineer / FDE / Solutions Engineer** — the most-mentioned specific title across your ME.md targets. Anthropic, OpenAI, Sierra, Cognigy, PwC, EY all hiring aggressively.
2. **Applied AI Engineer (agent workflows)** — pattern-matched to the Claude-Code / MCP stack; every 2026 grad who can talk hooks/skills/subagents wins.
3. **ML Engineer (LLM specialist)** — $220–280K base at frontier labs; median TC $300K+.
4. **AI Safety / Eval Engineer** — freshly-repriced by [`01` §4 UN Security Council](./01-big-lab-moves.md#4-un-security-council).
5. **Bio-AI Engineer** — freshly-repriced by [`01` §3 ART discovery](./01-big-lab-moves.md#3-anthropic-biolab).
6. **Cost / observability / router-designer** — every AI startup needs one; hardly anyone titles the role explicitly; opportunity to write your own title in the interview.

**Sources:**
- [KORE1 — AI Engineer Salary 2026: $145K–$310K (Real Offer Data)](https://www.kore1.com/ai-engineer-salary-guide/) `[analysis]`
- [Axial Search — Inside the AI Engineering Job Market: 43,500 Postings Analyzed](https://axialsearch.com/insights/ai-engineering-jobs) `[analysis]`
- [Axial Search — The State of the ML Engineering Job Market in 2026](https://axialsearch.com/insights/ml-engineering-jobs) `[analysis]`
- [Robert Half — AI/ML Engineer Salary (Updated for 2026)](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[secondary]`
- [FutureProofing — AI Engineer Demand 2026: Job Market, Roles & Pay](https://www.futureproofing.dev/resources/ai-talent-gap/ai-engineer-demand-2026) `[analysis]`

### Why it matters to you

- **Job lens:** Two applications to prioritise **this week** given the market + your ME.md targets:
  1. **Anthropic Solutions / FDE / AI Integration** — refresh your resume with the routing-artifact bullet + a "Claude Code four-primitive" narration + one specific line about the ART method as inspiration for an eval-orchestration project. Apply.
  2. **A funded startup from your ME.md list (Sierra / Decagon / Cognigy) or a Twelve Labs / Instinct-scale team** — same resume, different tone, emphasise ship-cadence + full-stack range. Apply.
- **Startup lens:** The hiring map is your **customer-discovery inversion**: any startup you build for "AI Integration Engineers as buyers" (dev-tools, evaluation, observability, routing) has ~14,000 named-buyer accounts to sell to. This is a *narrow, high-ARPU* motion — B2B SaaS with ACV $30–150K, ~1000 accounts to $30M ARR.
- **Insight:** The **3.2:1 demand/supply gap** at the aggregate level hides **massive tier-specific dispersion**. Frontier-lab roles: probably 10:1 supply/demand (thousands apply). Vertical-startup + integration-engineer roles: probably 1:1 or lower. Route your applications to the *softer* end of the market first; use the wins to build the resume that gets the harder ones.

→ Cross-link: [ME.md targeting](../ME.md#job-search-targeting-as-of-latest-edition) · [`§2` skill re-price](#2-safety-eval-repriced) · [APPLICATIONS.md](../APPLICATIONS.md).

---

## 2. Skill re-price — safety/eval + bio-adjacency go up, "prompt engineering" continues to drop {#2-safety-eval-repriced}

**What went UP this week:**
- **AI safety / eval / red-team infra work** — post-UN, this is now an internationally-visible career lane rather than a niche interest. Watch Anthropic + OpenAI + NIST AISI + UK AISI + CAISI job pages weekly.
- **Bio-AI adjacency** — ART discovery repriced the entire subsector; even a bio-minor or a bioinformatics course on your transcript is a differentiator.
- **Multi-tier model routing** — Sept 22 price cuts made this the highest-ROI single-skill upgrade of Q3.
- **Eval-authoring** — every serious 2026 engineering role asks how you'd evaluate an agent; the answer is domain-specific eval-suite design.
- **Deprecation-migration engineering** — Sora shutdown is a forcing function; the *skill* of migrating between providers is now hiring-manager-obvious.

**What stayed FLAT:**
- **Vector-DB + RAG operational skills** — table stakes but not differentiating anymore.
- **Fine-tuning small models** — still valued for local-inference tier, less differentiating than 2024.
- **Front-end / product engineering** — steady demand; not the differentiator.

**What went DOWN:**
- **"Latest model" fluency** — three-tier × four-lab matrix = nobody can memorise; routers memorise for you.
- **"Prompt engineering" as a standalone skill** — subsumed into Skills / Hooks / Subagents discipline.
- **"Chatbot builder" job titles** — repriced downward as agent-eng titles up-price.
- **Any AI job whose scope is "wrap the API in a UI"** — commoditised by no-code stacks + Anthropic Skills marketplace.

**Sources:**
- Extends [2026-09-10/05 §2](../2026-09-10/05-career-and-startup.md#2-reprice) — the earlier skill re-price of Q3.
- Cited throughout above and in [`01` §4](./01-big-lab-moves.md#4-un-security-council), [`01` §3](./01-big-lab-moves.md#3-anthropic-biolab), [`03` §1](./03-practical-skills-and-tools.md#1-three-tier-routing).

### Why it matters to you

- **Job lens:** **Update LinkedIn skills** this week — add "AI-eval design," "cost-aware model routing," "agent orchestration," "MCP." Remove anything that reads "prompt engineering" as a standalone or "chatbot development." Small change; big search-visibility impact for recruiters running LinkedIn Recruiter searches.
- **Startup lens:** The three most-re-priced skills (safety/eval, bio-AI, multi-tier routing) map to three founder wedges you could pursue *even without leaving school*: (a) eval-as-a-service for the AI-safety org buying pattern; (b) bio-adjacent agent-orchestration for the biology-AI subsector; (c) routing/observability layer for the AI-app market. Pick one; commit.
- **Insight:** **Skill re-pricing is faster than credential re-pricing.** A course transcript with "AI Safety" or "Multimodal ML" or "Computational Biology" line-items takes a semester to build; a re-priced skill on your LinkedIn takes 30 seconds. In a fast market, prefer the fast update — and use the semester for the *deeper* work (a research project, a startup MVP, a shipped artifact).

→ Cross-link: [ME.md active portfolio](../ME.md#active-portfolio-artifacts) · [`§1` hiring map](#1-hiring-map).

---

## 3. Startup wedges revealed this week — a running founder log {#3-startup-wedges}

**Six wedges the last 48 hours specifically opened or sharpened:**

1. **Model-router-as-a-service, tier-aware** (from [`01` §1](./01-big-lab-moves.md#1-opus-5-5), [`01` §2](./01-big-lab-moves.md#2-gpt-6-sol-luna), [`03` §1](./03-practical-skills-and-tools.md#1-three-tier-routing)) — public leaderboard tied to customer traffic; auto-migrate on new model releases; per-tier cost budgets. **ARR path:** $5–15M in 18 months. **Buyer:** every AI-app startup with >$10K/mo inference bill. **Moat:** eval-data + routing-decision logs.
2. **Video-gen abstraction layer** (from [`02` §1](./02-new-emerging.md#1-sora-api-shutdown), [`03` §4](./03-practical-skills-and-tools.md#4-sora-migration)) — LiteLLM-for-video; Runway/Kling/Veo/Luma/Pika unified. **ARR path:** $2–8M bootstrapped, $10–30M with sales team. **Buyer:** every media/marketing/gaming/edtech company with video-gen dependencies. **Moat:** provider-relationship depth + eval-suite.
3. **Rights-clearance-as-a-service for AI training data** (from [`02` §2](./02-new-emerging.md#2-funding-round)) — Stability's music-label deal signals the shape; you sell the compliance + provenance + royalty-attribution layer. **ARR path:** $10–40M in 3 years. **Buyer:** every generative-media startup going to Series A. **Moat:** first-mover legal precedent + label relationships.
4. **Agent-orchestration for scientific discovery** (from [`01` §3](./01-big-lab-moves.md#3-anthropic-biolab), [`04` §2](./04-research-progress.md#2-art-method)) — productise the ART method for pharma / materials / energy / defence research shops. **ARR path:** $50–200M in 5 years. **Buyer:** enterprise R&D labs. **Moat:** vertical eval-suite + wet-lab partnerships.
5. **AI-incident notification protocol + eval infra for international bio-weapons ban** (from [`01` §4](./01-big-lab-moves.md#4-un-security-council)) — analogous to CVE/CISA for AI. **ARR path:** slow start ($1–3M in year 1), then rapid scale if UN protocol lands ($10–50M in years 3–5). **Buyer:** governments + frontier labs + biosecurity firms. **Moat:** first-mover + regulatory-body relationships.
6. **Memory-as-a-service, Pareto-aware** (from [`04` §1](./04-research-progress.md#1-dolphinbench)) — hybrid memory-graph + full-context + RAG-summary, routed per-query. **ARR path:** $10–30M in 2 years. **Buyer:** agent-builder startups + enterprise agent teams. **Moat:** memory-strategy eval-suite tied to customer usage.

**Wedge ranking (for a CS grad student solo-or-cofounder starting today):**

| Wedge | Time-to-MVP | Fundraising odds | Your-fit | Composite |
|---|---|---|---|---|
| Model-router-as-a-service | 2 weeks | High (VC pattern-matches) | High (CS + your artifact) | **★★★★★** |
| Video-gen abstraction | 3 weeks | Moderate | Moderate | ★★★★ |
| Memory-as-a-service | 4 weeks | Moderate | High | ★★★★ |
| Agent-orchestration for science | 6 weeks | High (if bio-adjacency) | Moderate (needs bio partner) | ★★★★ |
| Rights-clearance | 8 weeks | Moderate (legal moat) | Low (needs legal cofounder) | ★★ |
| AI-incident notification | 12 weeks | Slow build | Low (gov-adjacent) | ★★ |

**Sources:**
- Extends [STARTUPS.md](../STARTUPS.md) — running wedge log.
- Individual wedges cited above.

### Why it matters to you

- **Job lens:** Even if you don't found any of these, the *narration* of them is a differentiator in FDE / Solutions interviews — hiring managers are looking for "founder-mindset" candidates.
- **Startup lens:** **Pick one wedge, this week, and commit to a 4-week timeboxed MVP.** The model-router wedge is the star-ranked one because it composes with your existing artifact ([`03` §3](./03-practical-skills-and-tools.md#3-router-extension)) — the artifact is *literally* the MVP v0.1.
- **Insight:** **Wedge-clarity beats vision-grandeur** in Q4 2026 fundraising. VCs are pattern-matching on "founder who can articulate a specific $X ARR path with a specific buyer + moat" — the six-row table above is exactly that shape. Practice the pitch out loud.

→ Cross-link: [STARTUPS.md running wedge log](../STARTUPS.md) · [`03` §3 router extension](./03-practical-skills-and-tools.md#3-router-extension).

---

## 4. This Thursday's action list (60 min tonight) {#4-thursday-action}

**60 minutes tonight, before Friday:**

1. **10 min — LinkedIn skill refresh.** Add: `AI evaluation design`, `cost-aware model routing`, `agent orchestration`, `MCP`, `Claude Code`. Remove: standalone `prompt engineering`.
2. **10 min — Router-artifact scaffolding.** Create the GitHub repo (empty except for README skeleton per [`03` §3](./03-practical-skills-and-tools.md#3-router-extension)). Public, MIT license. Commit-1 today.
3. **15 min — 3 Anthropic applications.** FDE / Solutions / Applied AI. Use the resume with the router-artifact bullet even if the artifact is v0.1 — link to the empty README + say "publishing this weekend, follow the repo."
4. **15 min — 2 funded-startup applications.** Sierra / Decagon / Twelve Labs / Instinct / any of the 160+ funded AI startups from the [Vinit Shahdeo tracker](https://github.com/speedyapply/2026-AI-College-Jobs).
5. **10 min — Update [APPLICATIONS.md](../APPLICATIONS.md)** with today's 5 applications; note company + role + resume version + date.

**This weekend:**
- **Saturday** — Ship the router artifact v0.1 (Opus 5.5 + Sol + Luna + Gemini 3.8 Flash + Muse Spark 1.3, five eval cases per [`03` §3](./03-practical-skills-and-tools.md#3-router-extension)). Publish. Post on LinkedIn.
- **Sunday** — Sora migration weekend project (if applicable) or **read one DolphinBench-cited paper** and write a 500-word summary.

**Sources:**
- Composed from this edition's cross-links.

### Why it matters to you

- **Job lens:** The action list is calibrated to the specific hiring surface open *this week*, not the generic year. Timing matters more than volume in AI hiring — 5 applications sent tonight beat 20 sent in October.
- **Startup lens:** The router artifact doubles as MVP-day-one for the wedge #1 startup path. **You are not choosing between job + startup — you are choosing the artifact that unlocks both.**
- **Insight:** **Cadence is the moat**. Nobody who reads this edition will out-strategise you; a few will out-execute you if you don't ship the router this weekend. The scarce resource in your career right now is not information — it's the willingness to publish a v0.1 before it's ready.

→ Cross-link: [ACTIONS.md](../ACTIONS.md) · [APPLICATIONS.md](../APPLICATIONS.md) · [`03` §3 router extension](./03-practical-skills-and-tools.md#3-router-extension).
