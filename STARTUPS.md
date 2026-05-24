# Startup Wedges — Running Log

Every "vertical-AI-for-X" wedge that surfaces across the daily editions gets logged here, tagged with market signals, your-fit score, and a status. **Closes the loop** between "interesting idea in Tuesday's edition" and "Saturday refinement / decision."

Status legend: 💡 noted · 🔍 researching · 🟡 prototyping · 🟢 active project · 🔴 closed (won't pursue) · 🏁 shipped

Fit score (1–5): 5 = your strengths + market wide-open; 1 = poor fit or market closed

Last updated: **2026-05-24**

---

## Open wedges — sorted by fit

| Status | Wedge | Buyer | Contract size | Anchor competitor(s) | Fit | Notes / Source |
|---|---|---|---|---|---|---|
| 💡 | **Claude + multi-jurisdiction 1099/contractor tax-classification** | Small accounting firms (5–25 staff) | $750/mo per advisor | None at SMB tier (Intuit too generic) | 5 | Workday Solopreneur Accelerator candidate. [2026-05-19/05 §5](./2026-05-19/05-career-and-startup.md#5-workday-solopreneur) |
| 💡 | **Claude + small-firm M&A due-diligence checklists** | Boutique investment-bank associates | $1,500/mo per seat | iManage / NetDocuments (enterprise-only) | 5 | Workday Solopreneur Accelerator candidate. [2026-05-19/05 §5](./2026-05-19/05-career-and-startup.md#5-workday-solopreneur) |
| 💡 | **SaaS → agent migration-as-a-service** (rip-and-replace a department off Salesforce/ServiceNow seats onto a governed Claude/OpenAI workflow) | Mid-market ops/IT leaders cutting SaaS spend | $15–60K/project + retainer | None vertical-specific (Big-4 too broad) | 5 | The SaaSpocalypse *is* the demand curve; the migration Skill doubles as the demo. [2026-05-24/02 §1](./2026-05-24/02-new-emerging.md#1-saaspocalypse) |
| 💡 | **Per-action billing / attribution control plane** (the missing layer as enterprises move per-seat → per-action) | Companies replacing SaaS licenses with API credits | $0.0005/action or $500–5K/mo | New Relic/Datadog (none agent-billing-native) | 4 | Adjacent to migration wedge; the SaaSpocalypse's missing infra. [2026-05-24/02 §1](./2026-05-24/02-new-emerging.md#1-saaspocalypse) |
| 💡 | **Verifiable / audit-grade / poison-resistant agent memory** (precondition for replacing a system of record) | Vertical-AI vendors + migration buyers | $500–5K/mo | Mem0 / EverMemOS / Cognee (not verification-first) | 4 | Build on PolarMem + 2604.16548 threat model. [2026-05-24/04 §1](./2026-05-24/04-research-progress.md#1-memory-synthesis) |
| 💡 | **Tabular-FM analytics/forecasting agent** (TabPFN-powered, beats AutoML at a fraction of setup) | SMB/mid-market ops + finance teams | $300–3K/mo | SAP Joule (enterprise), classic AutoML | 3 | Non-LLM frontier just got €1B validation. [2026-05-24/02 §2](./2026-05-24/02-new-emerging.md#2-sap-prior-labs) |
| 💡 | **Vertical-CX agent for regulated FS / healthcare / legal** | Mid-market FS / healthcare / legal | $5–25K/mo | Sierra ($15B) — enterprise only | 4 | Vertical wedge under Sierra's price floor. [2026-05-19/02 §2](./2026-05-19/02-new-emerging.md#2-sierra) |
| 💡 | **Agent identity / KYC / auth layer** | Agent-platform vendors | $0.001 per request | None — green-field | 4 | Adjacent to Parallel Web Systems. [2026-05-19/02 §3](./2026-05-19/02-new-emerging.md#3-parallel-web) |
| 💡 | **Agent observability / per-agent endpoint analytics** | Production agent teams | $200–2000/mo | New Relic / Datadog (none agent-native) | 4 | Adjacent to Parallel Web + TrajAD research |
| 💡 | **JADE-style per-claim eval API** | Vertical-AI vendors (Claude for X) | $500–5K/mo | Judgment Labs ($32M Lightspeed) | 4 | Build on JADE methodology. [2026-05-19/04 §2](./2026-05-19/04-research-progress.md#2-jade) |
| 💡 | **Trajectory verifier API (TrajAD-style)** | Production agent teams | $0.001–0.01 per check | None published yet | 4 | First-mover advantage; Haiku verifier + Opus main agent ratio. [2026-05-19/04 §3](./2026-05-19/04-research-progress.md#3-trajad) |
| 💡 | **Cost-aware multi-provider model router** | Any team running 3+ providers | $0.0001 per routed token | OpenRouter (consumer-first), early-stage commercial | 4 | Doubles as audit-tool. [2026-05-10](./2026-05-10/) and your personal billing audit |
| 💡 | **Public MCP server + connector marketplace** | Solo devs + small AI teams | $99/mo per connector | None yet (Anthropic owns spec, not marketplace) | 3 | High visibility, low contract size; pure portfolio play |
| 💡 | **Fine-tuning-as-a-service for non-LLM modalities (audio / video / time-series)** | ML teams without infra | $1–10K/mo per model | Runware (LLM-focused) | 3 | Adjacent to Runware. [2026-05-19/02 §4](./2026-05-19/02-new-emerging.md#4-runware) |
| 💡 | **B2B onboarding / compliance auto-course generator** | SMB HR + compliance | $300–1500/mo | Workday Learning (enterprise) | 3 | Adjacent to Oboe. [2026-05-19/02 §5](./2026-05-19/02-new-emerging.md#5-oboe) |
| 💡 | **Vertical-PM-agent for mid-market PMs** | Mid-market product managers | $50–200/mo per user | Linear AI features (enterprise-built-in) | 3 | Suleyman 4-verticals lane (PM was the most under-built). [2026-05-18/05 §5](./2026-05-18/05-career-and-startup.md) |
| 💡 | **AI-tooling for FDEs (Cursor-for-FDE workflows)** | OpenAI / Anthropic / Palantir FDEs | $50–200/mo per FDE | None | 3 | Niche but high-fit-with-trends. [2026-05-19/05 §2](./2026-05-19/05-career-and-startup.md#2-openai-deployment-co) |
| 💡 | **AI-skills wage-premium calculator + career-tracker** | CS students + early-career engs | Free + premium $20/mo | Levels.fyi (not AI-skill-specific) | 2 | Consumer; harder to monetize |
| 💡 | **On-device inference orchestration (Apple Extensions / Aluminium OS)** | Mobile app devs | Per-device licensing | None | 2 | Requires deep mobile + on-device ML expertise |
| 💡 | **AI-drug-discovery startup** | Big Pharma | $multi-million pilots | Isomorphic ($2.6B) + Recursion + Insilico | 1 | Too capital-intensive without bio co-founder. Apply to Isomorphic *roles* instead. [2026-05-19/02 §1](./2026-05-19/02-new-emerging.md#1-isomorphic) |
| 💡 | **Generic customer-experience agent** | Mid-market enterprise | $5–50K/mo | Sierra ($15B) + Decagon + Cognigy + Ada | 1 | Category closed |
| 💡 | **Generic FDE-as-a-service** | Mid-market enterprise | $10–100K/mo | OpenAI Deployment Co + Anthropic Solutions + Palantir + Big-4 | 1 | Category closed; only vertical-FDE specialists remain open |
| 💡 | **Generic agent-search infrastructure** | Agent-platform vendors | TBD | Parallel Web ($230M) + 1-2 stealth | 1 | Anchored |

---

## Wedges to revisit when relevant news lands

| Wedge | What needs to happen first |
|---|---|
| **EU-sovereignty AI vertical** | Mistral capital event > $5B or formal EU CAISI mirror launches |
| **Defense AI tooling** | Anduril / Helsing publish public-tooling spec |
| **Climate / carbon AI vertical** | First $200M+ four-corner round in carbon space |

---

## Decision matrix — top 3 to refine this Saturday

By Saturday May 23, pick **one of the top-3-fit wedges** above and produce a 1-pager covering:

1. Problem statement (3 sentences)
2. Buyer + budget (1 sentence)
3. Wedge product (3 sentences)
4. First 5 customers to call (list)
5. What you would build in 4 weeks to validate

The 1-pager is the input to the Workday Solopreneurship Accelerator application + becomes a permanent artifact in your interview portfolio regardless of outcome.

---

## Notes

- **Update cadence:** every Tuesday after the daily edition + every Saturday at refinement time
- **Demotion rule:** if a wedge sits 💡 for 30 days without being researched, demote to a `parking-lot/` section or close
- **Promotion rule:** any wedge that hits 🟡 prototyping for 14+ days should either advance to 🟢 with a named first customer, or drop back to 💡 with a one-line "why I'm pausing"
