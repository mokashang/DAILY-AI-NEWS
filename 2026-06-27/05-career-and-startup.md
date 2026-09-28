# Career & Startup — 2026-06-27

Three Friday-actionable signals, ordered by urgency for your profile (CS grad → startup OR SDE/MLE/AI/FDE role at frontier-adjacent company):

1. **AI-for-science talent wave is the highest-leverage door opening this quarter** — apply if your background includes ML + bio/chem/physics.
2. **Inference-infra hiring is the cleanest non-frontier-lab MLE lane** — Baseten + 5 peers are all hiring with $1.5B+ war chests.
3. **FDE postings are mainstream + paying $500K–$1M+ TC at senior** — apply this weekend.

---

## <a id="1-jumper-signal"></a>1. The Jumper signal — AI-for-science is a real career lane now

**Date:** 2026-06-19 (move announced) → 2026-06-30 (Anthropic SF science event) · **Tier:** `[secondary]`

**What.** John Jumper (AlphaFold, 2024 Chemistry Nobel) **left Google DeepMind for Anthropic** to lead AI-for-science. Two days earlier, Noam Shazeer (Gemini co-lead, "Attention" co-author) left Google for OpenAI. See [`01` §4](./01-big-lab-moves.md#4-talent) for the full story.

**Why this is your move:**

If you have **ML + biology / chemistry / physics / materials**, the door is now visible. Anthropic specifically has been quietly building wet-lab + biological-agent infrastructure with the **Allen Institute** and **HHMI** — that's the playbook Jumper inherited.

**Concrete actions this week:**

| Action | Effort | When |
|---|---|---|
| **RSVP Anthropic's June 30 SF science event** | 5 min | Today |
| Filter Anthropic careers page for "Frontiers" / "Science" / "Research" roles | 15 min | Today |
| Search Allen Institute (alleninstitute.org/careers) + HHMI Janelia (janelia.org/careers) for ML/computational roles | 30 min | This weekend |
| Restructure your resume to **lead with bio/chem/physics if you have it** (don't bury it in the second column) | 1 hr | Sunday |
| Find 3 papers Jumper cites in his recent work; read them; cold-DM 2 of the authors with one sharp question | 2 hr | Next week |

**Companies expanding the AI-for-science talent market (next 90 days probable):**
- **Anthropic** (Jumper's new home)
- **Allen Institute, HHMI Janelia** (partners)
- **Isomorphic Labs** (DeepMind's drug discovery spinout — their hiring may *accelerate* in response to losing Jumper as a magnet)
- **OpenAI** (their bio team needs to respond)
- **Recursion, insitro, Verge Genomics, Generate Biomedicines, Inceptive** (next-tier bio-AI)
- **Lila Sciences, Nabla Bio, EvolutionaryScale, Future House** (newer wave)

**Why it matters to you.**
- **Job:** Highest-leverage door opening in 2026 for ML + science combos. The bar is genuinely high; the comp is genuinely strong.
- **Startup:** Pick one Nature-family domain Jumper *won't* be solving inside Anthropic (e.g. structural materials, ecology, plant biology, geology). Build the data+eval+agent harness. Pitch as "the NatureBench winner for X." See [`04` §1a](./04-research-progress.md#1-real-work-benchmarks).
- **Insight:** Anthropic now has a **recursive-Claude team (Karpathy) + a Claude-for-science team (Jumper)** running in parallel. Both bet that the next leverage isn't a bigger model, but **Claude applied to the bottlenecks of pre-training and of science.** Mirror the bet at your own scale.

**Tags:** `#hiring #ai-for-science #anthropic #talent #jumper`

---

## <a id="2-baseten"></a>2. Inference-infra hiring — Baseten + 5 peers with $$ to deploy

**Date:** 2026-06-22 (Baseten Series F) · **Tier:** `[primary]` + `[secondary]`

**What.** Baseten raised **$1.5B Series F at $13B** (Altimeter / Conviction / Spark lead). Capital is explicitly **"earmarked for workforce expansion + enterprise GTM."** See [`02` §3](./02-new-emerging.md#3-baseten).

**Why this is your move:**

Inference-infra is the **cleanest non-frontier-lab MLE lane right now** — same skills compound (kernels, batching, quantization, serving) across all employers in the category. You can ship one portfolio artifact (e.g. a vLLM-vs-TensorRT benchmark on your model of choice) and it qualifies you at all six companies below.

**The cohort (all hiring aggressively):**

| Company | What they do | Recent capital | Title to target |
|---|---|---|---|
| **Baseten** | Model serving + GPU orchestration | $1.5B Series F (June 22) | Inference Platform Engineer / Model Performance Engineer |
| **Fireworks AI** | Custom serving + speculative decoding | $552M Series C (Feb '26) | Inference Engineer / ML Infra |
| **Together AI** | OS-model serving + fine-tuning | $305M Series B (March '26) | Systems Engineer / Inference Optimization |
| **Modal Labs** | Serverless GPU infra | $80M Series A (~ '25) | Platform Engineer / Distributed Systems |
| **Replicate** | Model deployment SaaS | Series C (~ '25) | ML Infra / Reliability Engineer |
| **Anyscale** | Ray-based serving | $99M Series D (~ '24) | Distributed ML Engineer |

**Concrete this weekend (4 hours):**

1. Pick a 3–8B open model (Mistral, Llama 3, GLM-5.2 small variant).
2. Benchmark inference latency + throughput + cost across **vLLM, TensorRT-LLM, and TGI** on a single H100 (rent for $2/hr).
3. Publish results in a GitHub README with charts.
4. Apply to all six companies above this weekend; **link the README in cover letter line 1.**

**Why it matters to you.**
- **Job:** This artifact directly answers "what would you actually do day one" for every company in the cohort. It's also a credible resume bullet for FDE / Solutions Engineering at the frontier labs.
- **Startup:** **Inference SaaS** is wedge-able if you pick a vertical (legal / medical / finance). Your differentiator is compliance + cost transparency, not raw throughput.
- **Insight:** Capital is repricing the inference layer ([`02` §1](./02-new-emerging.md#1-inference-week)). The macro signal is loud; the micro action is straightforward: ship one inference-benchmark project.

**Tags:** `#hiring #inference #mle #baseten #portfolio`

---

## <a id="3-fde-apply"></a>3. FDE is mainstream — apply this weekend (live reqs)

**Date:** This week · **Tier:** `[secondary]` + [primary job postings]

**What.** Forward Deployed Engineer is now a **standard role across hyperscalers, frontier labs, and enterprise AI**. Live indicators this week:
- **Google Cloud has a live "Forward Deployed Engineer II, Generative AI" req** (job ID 96964929679958726)
- **Salesforce** has FDE postings in SF + Seattle live this week
- **OpenAI, Anthropic, Palantir** all hiring multi-level FDE
- **LinkedIn shows 136K+ relevant postings; 6,386 new this week**

**Comp range** (frontier / senior):
- Base $200K–$300K
- Total comp $500K–$1M+ at senior
- Equity component meaningful at frontier labs (especially given Anthropic Oct '26 IPO trajectory)

**Why this is your move:**

FDE is the **highest-paying door that values shipping + customer-empathy over pure research credentials**. It's the right shape for a CS grad with strong engineering + decent communication who isn't going to out-publish a PhD.

**Concrete tonight (90 min):**

1. **Browse and bookmark 8–10 reqs** across Google FDE, Salesforce FDE, Anthropic Solutions, OpenAI Forward Deployed, Palantir FDE, PwC AI Engineer, Deloitte AI Engineer, EY AI, Accenture AI, Cohere Solutions.
2. **Build one customer-style end-to-end demo** for your portfolio:
   - Dataset: pick a real enterprise public dataset (SEC filings, FDA AERS reports, customer support logs)
   - Pipeline: RAG + agent + eval harness (use Claude Code w/ subagents — see [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-week26))
   - Eval: 20-case test set with expected outputs
   - Writeup: README + 2-min Loom
3. **Submit 3 applications this weekend**, each cover letter line-1 linking the demo.

**Why it matters to you.**
- **Job:** This is the most efficient effort → comp ratio in the market right now. **One artifact, three applications, $500K+ TC achievable.**
- **Startup:** FDE experience is *the* training for founding engineer or solo founder — you've already learned to listen to customers and ship to their constraints.
- **Insight:** FDE postings +800% YoY (tracked since 2026-05-17). This is no longer a niche; it's a **default career on-ramp** at every company shipping AI to enterprise. Plan accordingly.

**Tags:** `#hiring #fde #salary #portfolio #apply-this-week`

---

## <a id="4-market-signals"></a>4. Market signal grab-bag (read in 2 min)

| Signal | Source | What it means for you |
|---|---|---|
| **Ramp June Index — Anthropic 41% > OpenAI 39.5% business adoption** (+2.5pp Anthropic, OpenAI flat) | [Ramp AI Index](https://ramp.com/data/ai-index) | List Claude/Claude Code experience explicitly on your resume — majority enterprise stack now |
| **DeepSeek topped Ramp's trending vendor list** | Same | Open-weights are eating the price-sensitive tier; mention DeepSeek/GLM/MiniMax on resume if you've used them |
| **Top 1% of companies spend $7,500/employee/month on AI; median $11.38 — 680× gap** | Same | Target the top-1% AI-pilled cohort for internships/jobs (heavy Brex/Ramp spend on Anthropic + coding agents) |
| **Tech layoffs 185,894 YTD (~1,050/day); 56% cite AI** | TrueUp via TechTimes (June 16) | Within "shrinking" enterprises, AI-platform sub-orgs are net-hiring — target ServiceNow Now Assist, GitLab Duo, Salesforce Agentforce job pages directly |
| **ServiceNow cut mid-June while net-hiring on Now Assist / AI Control Tower / Action Fabric** | Salesforce Ben | "AI redundancy washing" — don't be filtered out by headline cuts; sub-orgs are hiring |
| **GitLab cut 350 (~14%) June 3 to fund AI infra** | TrueUp | GitLab Duo team is hiring; same applies |

---

## <a id="5-thread-status"></a>5. Status of tracked career threads

| Thread (from prior editions) | Status this week |
|---|---|
| **Anthropic Solopreneurship Accelerator (15 slots)** | No update; assume closed. Watch for next cohort announcement. |
| **AI Engineer #1 fastest-growing US job title (+143% YoY)** | Holds — Ramp data + Codex usage paper [`04` §3](./04-research-progress.md#3-shift-to-agentic) both reinforce. |
| **FDE postings +800% YoY** | Holds; Google live reqs this week (§3 above). |
| **Meta 14K cuts (~7K redirected to AI)** | No fresh news. |
| **Anthropic–Stainless $300M+ M&A** | No update; assume closed or quiet. |
| **PwC trains 30K on Claude Code** | No fresh update; PwC AI Engineer postings remain live. |
| **OpenAI Deployment Company $4B** | No fresh update. |

---

## <a id="6-weekly-checklist"></a>6. This week's checklist (do these)

- [ ] **RSVP Anthropic SF science event (June 30)** if you have ML + science background
- [ ] **Apply to 1 FDE req tonight** (Google, Salesforce, OpenAI, Anthropic, Palantir) — see §3
- [ ] **Ship the inference-benchmark artifact** this weekend (§2) OR the browser-port artifact ([`03` §2](./03-practical-skills-and-tools.md#2-portfolio-port)) — pick one
- [ ] **Update LinkedIn keywords:** add Claude Code, MCP, subagents, inference, RAG, eval — drop "ChatGPT," "OpenAI API" if they're stale
- [ ] **Set up `claude mcp login` + `/usage`** logging this evening ([`03` §1](./03-practical-skills-and-tools.md#1-claude-code-week26))
- [ ] **Read NatureBench abstract** ([`04` §1a](./04-research-progress.md#1-real-work-benchmarks)) — it's the citation everyone in AI-for-science will use this fall
- [ ] **Log entries in `APPLICATIONS.md`** for every req you apply to this weekend

---

**Cross-reference threads:**
- The macro reason for the inference-infra hiring spike: [`02` §1](./02-new-emerging.md#1-inference-week)
- The macro reason for the AI-for-science talent wave: [`01` §4](./01-big-lab-moves.md#4-talent)
- The macro reason for "ship one artifact": this week's research [`04` §1c](./04-research-progress.md#1-real-work-benchmarks) (RigorBench) literally measures whether you can finish what you start
