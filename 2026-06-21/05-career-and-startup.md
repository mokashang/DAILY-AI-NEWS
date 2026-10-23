# Career &amp; Startup — 2026-06-21

The big career-relevant moves this week: **Anthropic's FDE / Applied AI requisition is live on Greenhouse with a clean JD**, **Deloitte is hiring "Anthropic Forward Deployed Engineers" via its GPS practice**, and **compensation data confirms the pre-IPO equity premium** at both labs. Underneath: **AI-cited layoffs are running at ~1,093/day with 56% of events naming AI as driver** — the SDE entry-level squeeze is real, and the *specialty lanes* (FDE, MCP authorship, agent verification, defense-AI, agentic-SRE) are now where the durable hiring is. **Sunday's right move: ship the MCP-RC server, post it, and queue three cold emails for Monday-AM send.**

Tags: `#jobs #fde #mle #ai-engineer #anthropic #openai #salary #pre-ipo #startup #wedge`

---

## 1. Talent + protocol shift: read it as a career re-pricing {#1-talent-and-protocol}

**What happened:** Three independent signals this week resolve to the same re-pricing of AI engineering as a skill:

- **Talent** — **Karpathy at Anthropic pre-training** (announced May 19) + **Shazeer at OpenAI architecture** (June 18) plant opposite flags at the two largest labs.
- **Protocol** — **MCP `2026-07-28` RC** ([`02` §1](./02-new-emerging.md#1-mcp-rc)) ships Tasks, MCP Apps, OAuth RS hardening; **35.5M weekly SDK downloads** (more than `openai` + `@anthropic-ai/sdk` combined).
- **Benchmark methodology** — **Artificial Analysis re-weights to Agents 34%** ([`04` §2](./04-research-progress.md#2-aa-reweight)); **DeepSWE program-verified, Fable 5 at #1** ([`04` §1](./04-research-progress.md#1-deepswe)).

The composite read: **the AI-engineering skill that's gaining the most career torque in 2026 is not "fine-tune an LLM" and not "prompt engineer" — it's "ship MCP servers, design agent verifiers, and own per-step cost."** Each of the three signals points there.

### Why it matters to you

- **Job lens:** Your **LinkedIn skills row** should look like this by tonight:
  - `Anthropic Claude (Opus 4.8 / Sonnet 4.6 / Haiku 4.5)` · `MCP Tasks` · `MCP Apps` · `.mcpb packaging` · `OAuth Resource Server / Resource Indicators` · `Agent verification (verifier-pair pattern)` · `Cost-aware agent orchestration` · `Claude Code 2.1.183` · `Devin Desktop / ACP (cross-protocol)` · `Prompt caching (base-camp pattern)`
  - **Crucial deletions:** anything that says "Cursor power user" without the portability counterweight; anything that says generic "ChatGPT / LLM prompting."
- **Startup lens:** **The protocol layer is the most under-priced founder bet of June 2026.** Vertical MCP catalogs, agent-verifier-as-a-service, `.mcpb` packagers, MCP authorization / observability tools — each is a single-engineer-can-validate, $10K-MRR-in-90-days wedge.
- **Insight:** **Lab-name-on-resume is depreciating; protocol-citation-on-resume is appreciating.** When Karpathy and Shazeer flip labs in opposite directions, the labs themselves become less differentiating. The candidate who can recite the MCP-RC spec's Tasks lifecycle and the verifier-pair primitive will out-interview the candidate whose only flex is "I used Claude Pro for 6 months." Optimize accordingly.

---

## 2. Anthropic Forward Deployed Engineer — live on Greenhouse + Deloitte GPS partner postings {#2-anthropic-fde-live}

**What happened:** The Anthropic FDE (Forward Deployed Engineer, Applied AI) requisition is **live on Anthropic's Greenhouse board**. Key spec:

- **Job:** Forward Deployed Engineer, Applied AI
- **Function:** white-glove enterprise deployment of Claude — customer integration, prompt + agent engineering, evals at deployment scale, escalation engineering.
- **Requirements:** **3+ years** in a customer-facing technical role; production LLM work; prompt engineering; agent development; evaluation frameworks; deployment at scale.
- **Travel:** ~25%.
- **Partner-channel parallel:** **Deloitte's GPS practice** is hiring **embedded "Anthropic Forward Deployed Engineer" roles** — same pattern as the Palantir/Anthropic Partner Network arrangement.

**Sources:**
- [Greenhouse — Forward Deployed Engineer, Applied AI at Anthropic](https://job-boards.greenhouse.io/anthropic/jobs/4985877008) `[primary]`
- [Deloitte — Anthropic Forward Deployed Engineer (GPS)](https://apply.deloitte.com/en_US/careers/JobDetail/Anthropic-Forward-Deployed-Engineer-GPS/329283) `[primary]`
- [Anthropic Careers](https://www.anthropic.com/careers) `[primary]`

### Why it matters to you

- **Job lens:** This is your **highest-fit, highest-target role this Sunday.** The single best application narrative right now braids three things from this week: (a) **the Seoul enterprise rollout pattern** ([2026-06-20/01 §1](../2026-06-20/01-big-lab-moves.md#1-seoul)); (b) **the Fable 5 outage incident handling** ([`01` §2](./01-big-lab-moves.md#2-fable-restored)); (c) **a portfolio MCP server built to the `2026-07-28` RC** ([`03` §2](./03-practical-skills-and-tools.md#2-mcpb-bundles)). The cover letter is *"I shipped an MCP server to the RC spec last weekend; here's how I'd have routed Hanwha through the Fable 5 outage; here are the three NAVER-rollout patterns I'd run with on day 30."*
- **Startup lens:** The Deloitte parallel posting is a **signal of demand depth** — Anthropic's first-party hires aren't enough to staff demand, so partner channels are billing for Anthropic FDE work. Founder implication: **"Anthropic-specialist boutique consultancy"** is an under-built category (PwC, Deloitte, and EY are pursuing it at scale, but the $1M–$5M ARR independent shops are wide open). Two-person bootstrap is plausible.
- **Insight:** **3+ years of *customer-facing technical*, not 3+ years of *general engineering*.** That's the trap most CS grad students miss when reading the JD. Translate any past role — internship, TA, open-source maintainer who answered issues — into a customer-facing framing. If you ran a CS course's office hours, you have customer-facing technical experience. Name it that way on the resume.

→ Cross-link: [2026-06-20/01 §1 Seoul partner roster](../2026-06-20/01-big-lab-moves.md#1-seoul) · [`01` §2 Fable 5 restoration as interview material](./01-big-lab-moves.md#2-fable-restored).

---

## 3. Sunday distribution playbook — ship, post, queue 3 cold emails {#3-distribution}

**What happened (the meta-pattern):** Sunday is your *distribution* day, per the discipline you've been running. This week the artifact-to-distribution pipeline writes itself:

### The artifact (today, 4–6 hours)

Ship a public MCP server **to the `2026-07-28` RC spec**, per [`03` §2](./03-practical-skills-and-tools.md#2-mcpb-bundles):

- **Implement at least one Task** (long-running, resumable; e.g., a memory-consolidation job — see [`04` §4](./04-research-progress.md#4-memory-wave)).
- **Wire OAuth 2.1 Resource Server auth** with **resource indicators** (RFC 8707).
- **Ship as a `.mcpb` bundle** with a signed manifest declaring minimal scopes.
- **Include a 5-case eval** that cites the **MCP-Atlas methodology** ([`04` §3](./04-research-progress.md#3-mcp-atlas)) — multi-server, doesn't name your tools in the prompt, claims-based scoring.
- **Add a `cost.md`** with per-step token + dollar cost on Opus-orchestrator + Sonnet-worker split ([2026-06-16/03 §1](../2026-06-16/03-practical-skills-and-tools.md#1-meter-aware-starter)).

### The post (45 minutes, end-of-day)

- **LinkedIn headline (verbatim):** *"I shipped an MCP server to the `2026-07-28` Release Candidate this weekend — Tasks + OAuth Resource Server + `.mcpb` bundle. Here's what the RC's three new primitives change."* (Followed by 3 numbered points + the repo link.)
- **Hacker News** — submit with title *"Show HN: MCP server built to the `2026-07-28` RC (Tasks, MCP Apps, OAuth RS)"*. Match HN's syntax precisely.
- **X (optional)** — one short thread, tagged `@AnthropicAI` + `@modelcontextp` (or the canonical MCP handle).

### The 3 cold emails (queue tonight; send Monday 8:00 AM PT)

- **Anthropic Solutions / FDE recruiter** — link the bundle; one paragraph mapping the Seoul rollout pattern to a 30-day plan ([`§2`](#2-anthropic-fde-live)).
- **OpenAI FDE recruiter** — link the bundle; one paragraph on multi-protocol portability (you ship to MCP and ACP).
- **An engineer at NAVER, Samsung SDS, or Channel Corp** — link the bundle; one paragraph on the in-region Bedrock data-controls pattern ([2026-06-20/01 §1](../2026-06-20/01-big-lab-moves.md#1-seoul)). Korean-language fluency not required; "I built to your data-controls deployment shape" is the point.

### Why it matters to you

- **Job lens:** Three interview rounds answered by one weekend artifact (MCP authorship, real-tool eval, cost discipline) — *plus* an active recruiter-search keyword (`MCP Tasks`) that nobody else has at scale yet. **Expected value of the weekend = 1 callback in 14 days, conservatively.**
- **Startup lens:** Your `.mcpb` bundle is *also* a customer-discovery instrument. Watch which 5 industries open issues / file PRs / install it. Whichever has the most concentrated interest is your **vertical wedge candidate** — and you discovered it for free.
- **Insight:** **Distribution + artifact are the same loop.** Don't decouple them by shipping the artifact and "deciding about the post later." The post is part of the artifact's value. Ship them as one unit.

→ Cross-link: [`03` §2 `.mcpb` ship recipe](./03-practical-skills-and-tools.md#2-mcpb-bundles) · [2026-06-20/00 weekend artifact one-thing](../2026-06-20/00-tldr.md).

---

## 4. Under-applied lanes — defense-AI · agentic-SRE · world-models {#4-under-applied}

**What happened:** [`02` §3](./02-new-emerging.md#3-funding-week) names four rounds from this week, three of which are in lanes with **lower applicant density than frontier-lab FDE roles**:

- **Twenty Technologies $100M Series B at $1B (defense-AI)** — joins the Anduril / Palantir / Scout AI cohort. **Clearance-eligible US citizens preferred**, which is a small fraction of the AI-engineer applicant pool — applicant density is dramatically lower than at Anthropic / OpenAI. Comp is competitive (Palantir-style).
- **Elastic → Deductive AI $85M acqui-hire (agentic-SRE)** — confirmation that the agentic-SRE space is an *acquirer pool*; Datadog, Splunk-Cisco, NewRelic, and Honeycomb are the likely next buyers. Senior SRE + agent-fluency = rare combo.
- **Odyssey $310M / World-models cohort** — small, very selective. PyTorch + graphics/simulation background is the gate.
- **Hydra Host $100M (GPU marketplace)** — adjacent infra lane; one of the two "pick-and-shovel" categories quietly hiring through 2026 (the other is **agent-identity**).

### Why it matters to you

- **Job lens:** Add **one** of these lanes to your application list this week as a hedge against the frontier-lab queue depth. If you have **a US passport with clearance eligibility**, defense-AI is the highest-EV add. If not, **agentic-SRE** is the next-best — your MCP-server portfolio artifact is directly relevant (the Elastic ↔ Deductive deal proves the category is acquirer-ready).
- **Startup lens:** Two-person bootstrap candidates by lane:
  - **Defense-AI:** *agent-eval harness specialized for adversarial-robustness on tool-call outputs* — Anduril / Palantir / Twenty would all buy it.
  - **Agentic-SRE:** *MCP server that wraps PagerDuty + Datadog + Sentry + Jira into one verifier-paired diagnostic loop* — observability incumbents would acqui-hire (see §3 above; 11× ARR for the comparable).
  - **World-models:** *eval harness for sim-to-real handoff* — the cohort is small enough that even an early `arxiv.org`-credible artifact gets noticed.
- **Insight:** **Applicant density is the most under-priced filter for a job search in 2026.** The Anthropic FDE queue is deep; the Twenty Technologies queue is shallow. Comp at the deep queue is higher *per offer*, but **expected offers per hour invested** are higher at the shallow queues. Run a portfolio strategy: 1 deep-queue / 2 shallow-queue applications per week.

→ Cross-link: [`02` §3 funding week](./02-new-emerging.md#3-funding-week) · [2026-06-16/05 §4 SOC + GPU lanes original framing](../2026-06-16/05-career-and-startup.md#4-soc-and-gpu-lanes).

---

## 5. Comp snapshot — Anthropic vs. OpenAI engineers, the pre-IPO premium is real {#5-comp-snapshot}

**What happened:** Latest Levels.fyi data (cited as of June 2026):

| Lab | Range | Median TC | Equity structure |
|---|---|---|---|
| **OpenAI SWE** | L2 $249K → L6 $1.23M | **$805K** | **PPUs** (Profit Participation Units) |
| **Anthropic SWE** | $300K–$759K | **$443K** | RSUs (private); senior $550K–$759K |
| Frontier-lab SWE (cross-lab median) | — | **$600K–$795K** | varies |
| AI engineer (general market) | $145K–$310K | — | varies |

Cash splits at Anthropic: **base $250K–$400K**, **bonus 10–15%**, equity carries the bag.

**Forward Deployed Engineer comp** (Perspective AI 2026 survey, 1,200 FDEs): direct negotiation reference for the [`§2`](#2-anthropic-fde-live) Anthropic FDE role and its parallels.

**Sources:**
- [Levels.fyi — Anthropic Salaries](https://www.levels.fyi/companies/anthropic/salaries) `[primary]`
- [Levels.fyi — OpenAI Software Engineer Salary](https://www.levels.fyi/companies/openai/salaries/software-engineer) `[primary]`
- [JobsByCulture — Anthropic Salary 2026 breakdown](https://jobsbyculture.com/blog/anthropic-compensation-2026) `[secondary]`
- [Perspective AI — 2026 Forward Deployed Engineering Compensation Report (1,200 FDEs)](https://getperspective.ai/blog/2026-forward-deployed-engineering-compensation-report-1200-fdes) `[analysis]`

### Why it matters to you

- **Job lens:** **Pre-IPO grants from either lab are still the largest expected-value comp lever available to a 2026 entry hire.** OpenAI's PPU structure differs from Anthropic's RSUs (settlement, vesting, taxation all different) — read both carefully before optimizing one over the other. **Use the Perspective AI FDE report as a hard floor in negotiations** — bringing benchmark data to the table is a 5–15% comp improvement on average.
- **Startup lens:** A founding-engineer offer at a YC AI startup will typically land at **$180K–$240K base + 0.5–2% equity** in mid-2026 — meaningfully below the OpenAI / Anthropic median TC, but with a 10–100× equity asymmetry on a hit. The decision criterion isn't "more cash" — it's *"which path has higher probability of being the one I look back on as the formative four years?"* That's a personal question, but be honest about both numbers.
- **Insight:** **The TC gap between OpenAI median ($805K) and Anthropic median ($443K) is *not* an apples-to-apples comparison** — it reflects (a) different equity structures (PPU vs RSU), (b) different post-IPO outcome distributions, (c) Anthropic's stated bias toward salary-cap discipline. The right comparison is **expected-value of total comp over 4-year vesting**, not headline TC. Run the math; the headline numbers will mislead.

---

## 6. YC W26 retro + S26 application read (carries forward) {#6-yc-watch}

**What happened (recap context):** **YC W26 Demo Day (March 24, 2026)** was the strongest batch on record: **196 companies, 14 hit $1M ARR at Demo Day**, top performer at $27M ARR. Rebel Fund's analysis: **35% of W26 scored in the historical top-20%.** S26 applications closed; **Demo Day September 2026.**

**Sources:**
- [TechCrunch — 16 most interesting startups from YC W26 Demo Day](https://techcrunch.com/2026/03/26/16-of-the-most-interesting-startups-from-yc-w26-demo-day/) `[secondary]`
- [Jared Heyman / Rebel Fund — On the freakishly strong YC W26 batch](https://jaredheyman.medium.com/on-the-freakishly-strong-yc-w26-batch-056ccb666076) `[analysis]`
- [YC Events — Startup School 2026](https://events.ycombinator.com/startup-school-2026) `[primary]`

### Why it matters to you

- **Job lens:** The W26 batch members who *didn't* break out are quietly hiring **first-engineer #1-5 roles** through Q3. Comp is below frontier-lab TC, but equity asymmetry (0.5–2% at YC-stage) is the trade. Filter the **YC AI companies hiring page** for "founding engineer" or "early engineer" roles in MCP / agent / vertical-AI startups.
- **Startup lens:** **S26 Demo Day is your single most concentrated investor-attention window of H2 2026.** If you're building a wedge, the runway timing is: **portfolio MCP artifact this weekend → customer discovery in July → cofounder lock-in / YC S26 application validation in August → Demo-Day-derivative warm intros in September.** The artifact you ship today is the start of that runway.
- **Insight:** A *"freakishly strong"* batch is a leading indicator for the *next* batch being even more competitive — strong batches recruit strong applicants. **Apply early** (Aug/Sep for the next cycle), and **apply with traction** (5+ paying users beats 5+ stars on GitHub).

---

## This week's action list (deltas)

(For the full task tracker, see [ACTIONS.md](../ACTIONS.md). New / updated items from today:)

- ⚪ **SUN — Ship public MCP server to the `2026-07-28` RC spec + post LinkedIn / HN + queue 3 cold emails for Mon 8 AM PT.** ([`§3`](#3-distribution))
- ⚪ **SUN — Update LinkedIn skills row to the new vocabulary** (`MCP Tasks`, `MCP Apps`, `.mcpb`, `OAuth Resource Server`, `Agent verification (verifier-pair)`). ([`§1`](#1-talent-and-protocol))
- ⚪ **SUN — Upgrade Claude Code to 2.1.183** + re-baseline `cost.md` post-upgrade. ([`03` §1](./03-practical-skills-and-tools.md#1-cc-2-1-183))
- ⚪ **MON — Apply to Anthropic FDE (Greenhouse)** with the new MCP-RC artifact attached. ([`§2`](#2-anthropic-fde-live))
- ⚪ **MON — Apply to Deloitte GPS "Anthropic FDE" partner role.** ([`§2`](#2-anthropic-fde-live))
- ⚪ **THIS WEEK — Add Twenty Technologies or Hydra Host (under-applied lanes)** as a hedge application. ([`§4`](#4-under-applied))
- ⚪ **THIS WEEK — Read one agentic-memory paper end-to-end + sketch an MCP server around it.** ([`04` §4](./04-research-progress.md#4-memory-wave))
- ⚪ **THIS WEEK — Memorize the verifier-pair interview answer** (same tools, no CoT access, policy-grounded). ([`04` §5](./04-research-progress.md#5-verifier-stack))
