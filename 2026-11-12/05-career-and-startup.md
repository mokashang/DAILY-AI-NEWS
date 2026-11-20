# Career & Startup — 2026-11-12

Three things changed for you in the last week. **(1) FDE pay bands crystallized into three distinct tiers** — frontier-lab direct ($350-550K TC, vendor-reported), enterprise-platform ($200-310K base), public-sector ($143-195K base) — so your application plan now routes by tier, not by firm. **(2) Anthropic's workplace-suite launch creates a new interview question — "how would you build on Claude Meetings / Sheets / Whiteboards?"** — that pre-empts half the generic FDE panel. **(3) The IPO quiet period (Nov 10–19) is historically the easiest hiring window at a late-stage tech IPO** — reqs stay open, reviews happen, external comms is throttled, so the application surface is less contested.

Tags: `#careers #fde #hiring #ipo #startups #interview-prep`

---

## 1. The FDE pay-band map just crystallized — route your applications by tier {#1-fde-bands}

### Three bands that now exist publicly

| Band | Comp band | Example postings | Fit criteria |
|---|---|---|---|
| **Tier A — Frontier-lab direct** | $350-550K total comp (vendor-reported, verify) | Anthropic Solutions / FDE, OpenAI FDE, OpenAI Public Sector FDE | Strong systems + model fluency; MCP / Claude Code / API portfolio; eval authoring |
| **Tier B — Enterprise-platform FDE** | $150-310K base ($200K median for AI Engineer per [Fast AI Jobs](https://www.fastaijobs.com/)) | Databricks AI FDE London (Nov 4) · Raydar FDE $150-240K (Nov 4) · Ampersand FDE · Wellfound AI/ML FDE · Frontier Academy partner firms | Integration + customer-facing; vertical workflow experience; cost-aware agent design |
| **Tier C — Public-sector FDE** | $143.7-194.4K base | AWS Public Sector FDE Arlington VA · OpenAI Public Sector (emerging) · Palantir Forward Deployed (emerging) | US citizenship / clearance; govtech experience; slower sales cycle tolerance |

**Sources:**
- [ChoppingBlock — Raydar FDE $150-240K](https://www.choppingblock.ai/jobs/forward-deployed-engineer-at-raydar-2621575) `[primary]`
- [Fast AI Jobs — Databricks AI FDE](https://www.fastaijobs.com/job/greenhouse--8546367002) `[secondary]`
- [Paraform blog — What Is a Forward Deployed AI Engineer?](https://www.paraform.com/blog/forward-deployed-ai-engineer) `[analysis]`
- [Uvik blog — FDE Index](https://uvik.net/blog/forward-deployed-engineer-index/) `[analysis]`
- [Kore1 — Hire AI FDE Engineers 2026](https://www.kore1.com/hire-ai-forward-deployed-engineers-2026/) `[analysis, marketing-adjacent]`

### Your application plan — route by tier, not by firm

**Tier A (apply in the next 10 days — IPO quiet-period window):**
- Anthropic: Solutions Engineer (Enterprise), Forward Deployed Engineer (San Francisco, London, Singapore), Integration Engineer, Research Engineer (Alignment / Model Welfare), Policy Engineer
- OpenAI: Forward Deployed Engineer, Federal Deployed Engineer (DoD lane), Codex DX Engineer (post-Pierre acquisition)
- xAI / Google DeepMind / Meta GenAI: one app each, rounded out

**Tier B (apply by Nov 25):**
- The eight Frontier Academy partner firms: Accenture GenAI Studio · Bain Vector · Capgemini AI · Deloitte AI Institute · McKinsey QuantumBlack · Morgan Stanley AI/Tech Division · Commonwealth Bank of Australia · Novo Nordisk Data Science
- AI platform players: Databricks · Snowflake · MongoDB · DataRobot · Hugging Face · Scale AI
- Vertical AI apps hiring FDEs: Sierra · Decagon · Cognigy · Harvey · EvenUp · Hebbia

**Tier C (one app only, unless you want the clearance path):**
- AWS Public Sector FDE (if US + clearance-eligible)
- OpenAI Public Sector (emerging team — watch Driscoll's org chart)

### Why it matters to you

- **This is the first month the FDE pay-bands are *publicly comparable* across tiers.** Keep a spreadsheet of each req, listed comp, closing date. Track your pipeline against the three bands — not "which firms did I apply to" but "did I run three parallel funnels into A, B, C?" The portfolio shape (MCP server, router v3, Workplace Suite artifact, voice migration demo) satisfies all three tiers.
- **Cold-email play:** The 3 cold emails to frontier-lab engineers this week (from [ME.md](../ME.md)) should go to **the first-cohort Frontier Academy residents** if any have been named publicly, **plus** any Anthropic Enterprise Solutions engineers who have posted on LinkedIn about the Workplace Suite launch this week. Topic: "I'm building a Claude Sheet artifact that mimics the FDE residency deliverable shape — mind if I share for a 5-minute read?"

---

## 2. The re-price of the week: workplace-suite distribution is an Anthropic asset {#2-workplace-reprice}

**Last month's re-price:** Frontier Academy productized the FDE path. Your plan became two-track (direct vs. partner).

**This month's re-price:** The Workplace Suite converts "Anthropic Enterprise seat" from *a chat subscription* into *the surface where the artifacts happen*. Meetings · Sheets · Whiteboards · Data · Adobe/Atlassian/HubSpot full-app plugins. This is the horizontal-office-suite play many predicted Google or Microsoft would make, except Anthropic went first — and with a reasoning-tier that Claude Fable 5.2 delivers at 1M context.

### What this changes for your plan

#### (a) Interview question that will appear in 70%+ of panels inside 30 days

**"How would you design a Claude [Meetings / Sheets / Whiteboards] agent extension?"**

Rehearsed answer frame:
1. **Name the primitive** — Meetings is a live-transcript + action-item stream; Sheets is a tabular datastore + formula engine; Whiteboards is a canvas + object graph.
2. **Name one high-leverage integration point** per primitive — Meetings: a "silent interviewer" that whispers the next question to the facilitator; Sheets: a "formula-authoring agent" that converts natural-language intent into Sheets formulas; Whiteboards: a "spec-to-code" agent that turns a sketched flow into a working prototype.
3. **Name one non-obvious failure mode** — Meetings: hallucinated action items attributed to the wrong participant; Sheets: cross-tab formula cascades that make lineage unreadable; Whiteboards: whiteboard-driven workflows that drift from the actual code after 3 days.
4. **Name one measurement** — per-feature: ratio of accepted agent outputs / total agent outputs over 14 days. This is the metric the FDE panel will react to.

#### (b) Portfolio piece to add this weekend

**One Claude Sheet artifact + one Claude Data dashboard**, both built on the beta surface, both linked from your portfolio. Topic: a **"model router cost dashboard"** — Fable 5.2 vs Haiku 5.5 vs Opus side-by-side, with per-task cost and effort-level recommendation. Cross-links the router v3 work from [`03` §1](./03-practical-skills-and-tools.md#1-fable-52-default).

#### (c) Startup wedges that just repriced

- **Workplace-vertical template packs** (finance ops, HR, RevOps) — 60-day revenue cycle, no API moat, immediate.
- **Meetings-adjacent agents** — live-call agents running *inside* Claude Meetings. Compete with Otter + Fireflies + Gong on their home turf.
- **Workplace-suite migration consulting** — $100K-$500K engagements decommissioning Otter / Fireflies / Excel macros for enterprises moving to Claude.
- **Attested-human-in-the-loop tooling** (new, driven by RSI disclosure) — a durable product category because Anthropic's own S-1/A commits to keeping humans in frontier R&D. Platform that *measurably documents* human review becomes safety-attested vendor of record.

→ Cross-link: [`01` §3 Workplace Suite](./01-big-lab-moves.md#3-workplace-suite) · [`03` §3 beta patterns](./03-practical-skills-and-tools.md#3-workplace-beta).

---

## 3. One Thing To Do This Thursday — the two-artifact + 90-sec-answer plan {#3-today-plan}

**Time budget: 2 hours total. Ship by EOD today (Thursday Nov 12).**

### Artifact 1 — Workplace Suite distribution diagram (45 minutes)

**Goal:** A 1-page diagram showing where Claude Meetings / Sheets / Whiteboards / Data sit relative to Google Meet · Otter · Fireflies · Microsoft Copilot · Excel · Google Sheets · Notion · Figma · Miro.

**Format:** Mermaid or hand-draw-then-scan is fine. Don't over-design — this is a *conceptual* map, not a pixel-perfect deck slide.

**Outcome:** One PNG + one caption paragraph (3 sentences max) saying what the diagram shows. Post to LinkedIn today with "I built a map of where the new Claude Workplace Suite sits. Thoughts?" This is a legible "I pay attention to distribution" signal that recruiters at Enterprise-focused firms read.

### Artifact 2 — "What did you make of Anthropic's RSI disclosure?" 90-sec verbal answer (30 minutes)

**Goal:** A rehearsed-out-loud 90-second answer to the interview question that will dominate Research / Alignment / Policy panels for the next quarter.

**Answer frame (your version — modify to your voice):**

> *"The Nov 2 S-1/A paragraph is a Securities Act §11 disclosure — meaning it is subject to investor-suit liability, so the estimate is likely conservative. Operationally, Anthropic disclosed that over 90% of its own September 2026 codebase contributions were Claude-authored — the 'closing the loop' they describe is already half-closed in a measurable way. For my career, the most important implication is that alignment, Trust & Safety, Policy, and Model Welfare are now line items in a public-company risk register — which converts alignment from a research-only problem into a corporate-governance problem. It's why I'm applying into Research Alignment and Policy tracks, not just Solutions and FDE — that hiring surface just doubled."*

**Practice:** Say it out loud 3 times. Record yourself the third time. Listen back. Trim anything that stretches past 90 seconds. Upload the audio as a private note.

### Interview rehearsal (45 minutes)

**Four questions to rehearse to 60-second answers each:**
1. "What did you make of Anthropic's RSI disclosure?" (the big one — above)
2. "What's your default Claude model and why?" (Fable 5.2 at medium effort, routing to Opus at xhigh for hard reasoning — see [`03` §1](./03-practical-skills-and-tools.md#1-fable-52-default))
3. "How would you design a Claude Sheets / Meetings / Whiteboards agent extension?" (see §2 above)
4. "If Anthropic IPOs at $1.3T — is that a buy or a sell?" (Your framing: the RSI disclosure creates a real §11-liability floor on the capability estimate; if you believe their estimate is conservative, the floor is understated and the IPO is underpriced on capability — but the lock-up overhang + enterprise-RFP shifting to Gemini 4 as incumbent creates a 180-day drift risk. Three-part answer, no yes/no.)

### Cold-email play (10 minutes)

**One cold email today** to an Anthropic Enterprise Solutions engineer who has posted on LinkedIn about the Workplace Suite launch this week. Topic: "I built a distribution map of where Claude Meetings sits vs. Otter/Fireflies — mind taking a 5-minute look?" Attach Artifact 1. This is a **sub-200-character email + one attachment**; the response rate to that shape is ~5-15% at labs this quarter, which is 10x generic "I'd love to chat" cold emails.

---

## 4. Actions tracker — this week (Nov 12–18)

| Status | Action | Due | Source |
|---|---|---|---|
| ⚪ | **Ship Artifact 1 (Workplace Suite distribution diagram)** + LinkedIn post | Thu Nov 12 | [`05` §3](#3-today-plan) |
| ⚪ | **Rehearse Artifact 2 (RSI 90-sec answer)** — 3 reps, 1 recording | Thu Nov 12 | [`05` §3](#3-today-plan) |
| ⚪ | **1 cold email to Anthropic Workplace-Suite engineer** | Thu Nov 12 | [`05` §3](#3-today-plan) |
| ⚪ | **Apply to 3 Tier A roles** (Anthropic Solutions + OpenAI FDE + Research-Alignment) | Fri Nov 13 | [`05` §1](#1-fde-bands) |
| ⚪ | **Apply to 3 Tier B roles** (Frontier Academy partner firms) | Mon Nov 17 | [`05` §1](#1-fde-bands) |
| ⚪ | **Rebuild router artifact v3 (Fable 5.2 default)** — publish to GitHub | Sun Nov 15 | [`03` §1](./03-practical-skills-and-tools.md#1-fable-52-default) |
| ⚪ | **Build 1 Claude Sheet + 1 Claude Data dashboard** — model-router cost dashboard | Sun Nov 15 | [`05` §2](#2-workplace-reprice) |
| ⚪ | **Migrate 1 voice-agent demo to GPT-Live** | Mon Nov 17 | [`03` §2](./03-practical-skills-and-tools.md#2-gpt-live-migration) |
| ⚪ | **Monitor Anthropic IPO pricing Nov 18 → first trade Nov 19** — 15-min check only | Tue-Wed Nov 18-19 | [`01` §1](./01-big-lab-moves.md#1-ipo-roadshow) |
| ⚪ | **Read arXiv 2611.06764 + 2607.07663** — write one paragraph on each | Wed Nov 18 | [`04` §1-2](./04-research-progress.md) |

---

## 5. Startup/founder ambient items (if you're on that track)

- The **quiet-period hiring advantage** at Anthropic is also a **secondary-market pricing anomaly window.** If you have any secondary exposure to Anthropic shares or options and the lock-up allows a transaction, consider repricing now — the Nov 10 roadshow range (~$70-78 → $1.1-1.4T) might be your best public anchor until post-first-trade.
- **If you're deciding founder vs. first-5-hire at a startup this quarter:** the application-layer margin compression (from Fable 5.2 + Haiku 5.5 pricing) suggests that *infra* and *security* and *vertical workplace* are stronger first-5 bets than *horizontal application* right now. First-5 at an enterprise-security or workplace-vertical startup would compound harder through 2027 than first-5 at a horizontal app.
- **Sovereign-capital awareness:** If you take a founding role at a company that has (or is raising from) Prosperity7 / Mubadala / PIF / G42, understand what strategic asks accompany the capital before signing (deployment-in-country, data-center placement, etc.). See [`02` §2](./02-new-emerging.md#2-rox-funding) for the pattern.

---

## 6. One-paragraph TL;DR for the week

Your week has two shapes: **(a) a 72-hour sprint** — Workplace Suite diagram + RSI 90-sec answer + 1 cold email today, apply to 3 Tier A roles Friday, build router v3 + Claude Sheet + Claude Data dashboard this weekend; and **(b) a monthly thesis** — Anthropic just converted itself from "chat seat" to "artifact surface," which creates a specialization lane called "workplace-agent FDE" that did not exist 7 days ago. Target that lane at the Frontier Academy partner firms during the IPO quiet period. If you land one direct interview in the next 30 days, the RSI answer and Workplace-Suite diagram are the two pieces that separate you from the stock Enterprise FDE candidate.
