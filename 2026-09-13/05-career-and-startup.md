# Career & Startup — 2026-09-13

The Sunday summary of the 2026 market for a CS grad targeting SDE / MLE / AI-Engineer or founder tracks: **AI Engineer is officially LinkedIn's #1 fastest-growing role, salaries stretched further at the top ($145K–$310K real-offer band), and the agentic-enterprise packaging (Salesforce Agentforce) just created a fourth job family — agent orchestration engineer — while the sandbox-CVE class opened a fifth: agent security engineer.** The compounding move is unchanged from last edition: ship one artifact/week. The artifact this week evolved shape — it now maps to the six Trusted Enterprise AI Harness pillars.

Tags: `#careers #salary #startups #fde #ai-engineer #mle #hiring #anthropic #openai #salesforce`

---

## 1. The hiring map — where the reqs actually are (Sept 13 update) {#1-hiring-map}

**What happened:** The [2026-09-10/05](../2026-09-10/05-career-and-startup.md) hiring map holds — with three additions from this week:

### Salary anchors (Sept 2026 real-offer data)

- **AI Engineer:** **$145K–$310K** real-offer band; median $200–225K base; LLM specialists $220–280K base alone.
- **MLE:** **$128K–$186K** base by city + YOE; median new-grad $128,769 (Jul 10, 2026 data).
- **Remote premium:** remote ML roles average $195K base — **+21% above national average.**
- **F500 employers to target:** Google, Microsoft, Amazon, Meta, Apple, NVIDIA, IBM, Adobe, Salesforce, Uber, JPMorgan Chase, American Express, Walmart (from 2026 early-career research).

### LinkedIn 2026 Jobs on the Rise
- **AI Engineer = #1** on the fastest-growing-role list.
- **7 of 10 fastest-growing tech roles are AI-related.**
- Adjacent lanes still hot: AI Solutions Engineer, AI Integration Engineer, ML Platform Engineer, AI Product Manager.

### Three new job families that emerged this week

| Job family | Where the reqs are appearing | Why the demand exists |
|---|---|---|
| **Agent orchestration engineer** | Salesforce (Agentforce), F500 in-house teams | The Salesforce Sept-11 named-agent launch [`01` §1](./01-big-lab-moves.md#1-agentforce-seven) created immediate demand for per-customer configuration + cross-vendor routing |
| **Agent security engineer** | Anthropic, OpenAI, Cursor, Cognition, agent-trust-infra startups | The sandbox-CVE class [`03` §1](./03-practical-skills-and-tools.md#1-sandbox-escapes) made this a named line-item on 2027 security budgets |
| **International FDE / Solutions (APAC + EU)** | Anthropic (Bengaluru, Seoul, Paris, Munich); OpenAI (London, Tokyo); Google DeepMind (Paris) | Anthropic's global expansion [`01` §2](./01-big-lab-moves.md#2-anthropic-global) is the highest-signal international-hiring trace of 2026 |

**Sources:**
- [Robert Half — AI/ML Engineer Salary (Updated for 2026)](https://www.roberthalf.com/us/en/job-details/aiml-engineer) `[analysis]`
- [Kore1 — AI Engineer Salary 2026: $145K–$310K (Real Offer Data)](https://www.kore1.com/ai-engineer-salary-guide/) `[analysis]`
- [Kore1 — ML Engineer Salary 2026: $128K–$186K Base by City & YOE](https://www.kore1.com/ml-engineer-salary-guide/) `[analysis]`
- [Interview Kickstart — Machine Learning Engineer Salary 2026: Full Salary Breakdown](https://interviewkickstart.com/blogs/articles/machine-learning-engineer-salary) `[analysis]`
- [Skillcrush — AI Engineering Jobs in 2026](https://skillcrush.com/blog/artificial-intelligence-engineering-jobs/) `[analysis]`
- [Simplify Jobs — New Grad Data Science & AI/ML Jobs (2026–2027)](https://simplify.jobs/l/New-Grad-Data-Science-AI-ML) `[aggregator]`
- [Indeed — Machine Learning Engineer New Grad 2026](https://www.indeed.com/q-machine-learning-engineer-new-grad-2026-jobs.html) `[aggregator]`
- [ZipRecruiter — Machine Learning Engineer New Grad Jobs](https://www.ziprecruiter.com/Jobs/Machine-Learning-Engineer-New-Grad) `[aggregator]`

### Why it matters to you

- **Job lens (updated targeting):** Your target list this quarter now has *three tiers of urgency*:
  1. **Apply this week (the seven-day tier):** Salesforce Agentforce team + Anthropic Bengaluru/Seoul/Paris/Munich openings + any agent-trust-infra startup on the [`02` §2](./02-new-emerging.md#2-agent-trust-funding) $435M list. These are net-new reqs; the field is small; you have a real shot.
  2. **Apply this month (the four-week tier):** Anthropic Solutions/FDE/DX (US), OpenAI FDE, Cognition (Devin), Cursor, any Claude-Code-adjacent role at PwC / Deloitte / Accenture / EY.
  3. **Apply this quarter (the market-hedge tier):** F500 in-house AI-Engineer roles (JPMorgan, American Express, Walmart, etc.). Slower cadence, more stable comp, better for MLE positioning.
- **Insight:** Read *AI Engineer #1 on Jobs on the Rise* + *7 of 10 tech roles are AI-related* together. This is the single most important labor-market data point for a CS grad in 2026: **you are entering a labor market where 70% of the growth is in your field.** The specific title matters less than the specialty. Optimize the résumé for "AI + a real artifact" — not for a specific title.

→ Cross-link: [`03` §3 the trusted-agent starter is the artifact for the seven-day tier](./03-practical-skills-and-tools.md#3-hardening-checklist) · [`01` §2 international hiring surfaces](./01-big-lab-moves.md#2-anthropic-global).

---

## 2. The skill re-price of the week — orchestration + governance + memory join the top-value list {#2-reprice}

**What happened:** Last edition's re-price ([2026-09-10/05 §2](../2026-09-10/05-career-and-startup.md#2-reprice)) put model-routing and eval-authoring at the top. This week, three more skills gained value simultaneously:

| Skill | Gain trigger | How to acquire (this weekend) |
|---|---|---|
| **Agent orchestration** | Sakana Fugu ([`04` §1](./04-research-progress.md#1-fugu-orchestration)) + Salesforce Agentforce ([`01` §1](./01-big-lab-moves.md#1-agentforce-seven)) | Read the Fugu paper; extend your router with an orchestration eval ([`04` §3](./04-research-progress.md#3-eval-suite-template)) |
| **Agent governance** | Salesforce Trusted Enterprise AI Harness ([`03` §2](./03-practical-skills-and-tools.md#2-trusted-harness)) | Map your artifact to the six pillars in `PILLAR_MAP.md` |
| **Agent security** | Sandbox-CVE class ([`03` §1](./03-practical-skills-and-tools.md#1-sandbox-escapes)) | Ship a hardening checklist as `sandbox/HARDENING.md` |

**Deprecated further this week:**

- "Which model is best" fluency — Sakana's orchestrator now decides for you.
- "Building a chatbot" — Cursor + Windsurf + Devin have consumed that category (see [`02` §3](./02-new-emerging.md#3-coding-agent-consolidation)).

### The updated four-week compounding move

| Week | Artifact | Why it lands |
|---|---|---|
| **This week (Sept 13)** | Trusted-agent starter (router + evals + policy + audit + hardening + pillar-map) | Answers "how would you deploy agents at an enterprise" in code |
| Next week (Sept 20) | Memory eval suite ([`04` §3](./04-research-progress.md#3-eval-suite-template) M1–M4) | Answers "how do you know your agent remembers correctly" |
| Week 3 (Sept 27) | Orchestration eval suite ([`04` §3](./04-research-progress.md#3-eval-suite-template) O1–O3) + a 500-word Fugu paper summary post | Answers "have you read this month's most-important paper" |
| Week 4 (Oct 4) | An MCP server for one real workflow + a public cost dashboard for the router | Answers "you've built agent infrastructure people use" |

**Same shape as last edition (four artifacts by mid-Oct); the shape shifted from "chatbot-plus-evals" to "governed-agent-plus-evals."** That reflects the market's shift over the past three days.

### Sources
- [`03` §3 the current artifact spec](./03-practical-skills-and-tools.md#3-hardening-checklist)
- [`04` §3 the eval suite template](./04-research-progress.md#3-eval-suite-template)
- [2026-09-10/05 §2 the prior re-price](../2026-09-10/05-career-and-startup.md#2-reprice) (for cross-comparison)

### Why it matters to you

- **Job lens:** The four-artifact plan gets you to a **portfolio that reads as "this candidate thinks about the whole agent lifecycle, not one part."** That's the frame recruiters at Anthropic (Solutions), OpenAI (FDE), Salesforce (Agentforce), Cognition, Cursor, and any well-funded agent-trust-infra startup are searching for. Ship them all and by Oct 8 you're differentiated from 90%+ of the applicant pool.
- **Startup lens:** The four artifacts *are also* the technical scaffolding for the founder path in [`05` §3](#3-startup-wedges). Do them for portfolio, and if you go founder the code is ~80% reusable as the OSS layer for either an orchestrator startup or an agent-trust-infra startup.
- **Insight:** The re-price direction is stable: **the frontier keeps moving to systems around the model.** Router → memory → orchestration → governance → observability. If you keep shipping one system-around-the-model artifact per week, you compound faster than the model release cadence can invalidate your work — which is the whole game.

---

## 3. Startup path check-in — three wedges to prototype this month {#3-startup-wedges}

The founder-shortlist evolved this week. Two carry over, one is new:

### Wedge A (unchanged) — model-fatigue tooling
Router / migration engine / cost-observability. See [2026-09-10/02 §3](../2026-09-10/02-new-emerging.md#3-model-fatigue-tooling). Still open; first-check target $500K–$1M pre-seed on a working demo.

### Wedge B (unchanged) — agent-native primitives
Re-imagine one human protocol for agent-to-agent use (identity, comm, authorization, reputation, dispute, storage). See [2026-09-10/02 §2](../2026-09-10/02-new-emerging.md#2-natural-agent-payments). Still open; Natural raised on this thesis for payments; others fundable.

### Wedge C (NEW) — agent trust infrastructure
The [`02` §2](./02-new-emerging.md#2-agent-trust-funding) $435M / 12-round pole. Three concrete sub-wedges:

1. **Cross-vendor policy engine** — declare a policy once (in the shape of the Salesforce Trusted Harness pillars), enforce across Anthropic / OpenAI / Gemini / Agentforce / custom.
2. **Agent audit-log-as-a-service** — append-only log of every agent action + tool call + prompt; queryable for compliance replay; SOC 2 / ISO 27001 / EU AI Act ready.
3. **Agent identity + delegation infra** — the OAuth-for-agents primitive; who is this agent, on behalf of whom, with which permissions, for how long.

**First-check target:** $500K–$2M pre-seed with (a) an OSS reference implementation, (b) one design-partner logo, (c) a memo mapping your product to at least 2 of the six Trusted Harness pillars *by name*.

### Do this weekend (4 hours)

Pick one of A / B / C. Write a **one-page memo:**
- 3 real payloads that fail today (real agent × real customer × real task).
- The minimal primitive (5 endpoints or fewer) that unblocks them.
- The 500-line reference impl you'll ship next weekend.

Post to your GitHub + LinkedIn. This memo is your seed-round warm-intro currency.

### Why it matters to you

- **Startup lens:** Wedge C is the most under-supplied of the three right now. 12 rounds in 5 months = ~2.4 checks per month; ~30 companies visible; category still has room for 20+ more. And unlike model orchestration (Fugu OSS'd — some of the wedge got compressed), agent trust infra requires deep vertical + compliance expertise that AI grads can *acquire* over a weekend + a month of reading. Very good founder-market fit for a CS grad.
- **Job lens:** *Even if you don't start*, publishing the memo signals founder-shaped thinking. The specific memo topic (Wedge A / B / C) also tells you which employer to prioritize:
  - Wedge A memo → Anthropic Solutions, OpenAI FDE, any router-focused startup
  - Wedge B memo → Natural, any agent-native-primitive startup, Anthropic Applied AI
  - Wedge C memo → Euno, any agent-trust-infra startup, Salesforce Agentforce security
- **Insight:** Wedges A + B were "the layer above the model." Wedge C is "the layer *around* the agent." Both stack — Wedges A+B are the *product*, Wedge C is the *guardrails around the product*. A founder or an engineer who understands both stacks is roughly 20% of the current AI talent pool and 80% of the AI opportunity through 2027.

→ Cross-link: [`02` §2 agent trust funding pole](./02-new-emerging.md#2-agent-trust-funding) · [`01` §1 the Salesforce Trusted Harness (customer-visible artifact for wedge C)](./01-big-lab-moves.md#1-agentforce-seven).

---

## 4. This week's concrete moves

- **Today (30 min):** Update LinkedIn skills line → add "agent orchestration", "agent governance", "Agentforce", "Trusted Enterprise AI Harness", "MCP", "AI agent security". Update headline → "AI Engineer" if not already.
- **Today (4 h):** Ship the trusted-agent starter repo ([`03` §3](./03-practical-skills-and-tools.md#3-hardening-checklist)). Public.
- **Tonight (60 min):** Read the Fugu paper intro + method ([`04` §1](./04-research-progress.md#1-fugu-orchestration)) so you can talk about it competently.
- **Applications this week:** 3 to Anthropic (Solutions / FDE / DX — target Bengaluru / Seoul / Paris / Munich also, not just US), 2 to Salesforce Agentforce team, 2 to well-funded agent-trust-infra startups from the [`02` §2](./02-new-emerging.md#2-agent-trust-funding) list.
- **Weekend memo (4 h):** One founder-wedge memo (Wedge C if forced to pick — most under-supplied).
- **Reading:** the two arXiv papers in [`04` §1](./04-research-progress.md#1-fugu-orchestration) + [`04` §2](./04-research-progress.md#2-memory-benchmarks) so you can name-drop them in interviews next week.

**End-of-week checkpoint:** 1 major artifact shipped, 7 apps out, 2 papers read, LinkedIn updated. If you hit this, you're already ahead of ~90% of the 2026 AI-hire applicant pool.
