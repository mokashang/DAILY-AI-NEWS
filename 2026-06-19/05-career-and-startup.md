# Career & Startup — 2026-06-19

June rewrote two parts of your job-search strategy in the same month. (1) The **export-control regime** ([`01` §1](./01-big-lab-moves.md#1-fable-export-control)) makes **passport** a first-order variable at every frontier lab — for international students this is the biggest single change of 2026. (2) The **Trump EO** ([`01` §2](./01-big-lab-moves.md#2-trump-eo-signed)) turned the pre-deployment-eval career lane from *predicted* into *real and hiring*, with an Aug-1 deadline that gives you a precise calendar. Underneath both: **Claude Code at ~$1B ARR + DeployCo operational** means the FDE / Solutions / Integration market continues to widen, and Anthropic's **Seoul + Bengaluru** openings give you regional alternatives if SF is blocked. Below: how to turn each into a move this week.

Tags: `#jobs #careers #passport #export-control #ai-assurance #fde #integration #anthropic #openai #regional`

---

## 1. Passport-aware job-search strategy (NEW — read first if you're an international student) {#1-passport-strategy}

**What changed:** The Fable 5 export-control episode ([`01` §1](./01-big-lab-moves.md#1-fable-export-control)) made it explicit that **the US government can require frontier labs to suspend access to specific models for *all foreign nationals* — including the lab's own foreign-national employees.** This is not a one-time event. Expect this regime to expand: more "covered" model variants, more roles affected, more passports in scope.

**What this means for an ambitious CS grad student (you):**

- The roles *most* exposed: **direct work on training, fine-tuning, or weights-level engineering of "covered frontier models"** at OpenAI / Anthropic / Google DeepMind. These will increasingly be labeled "US person required" or require security-clearance-eligibility.
- The roles *least* exposed (still abundant): **AI Integration Engineer, FDE, Solutions Engineer, Applied AI, Customer Engineering, vertical-application work.** These touch the model through APIs, not at the weights layer. **This was already the lane you were targeting** per ME.md — the export-control regime *strengthens* that targeting decision, doesn't weaken it.
- The roles to *re-evaluate*: research-engineer at a frontier lab. Still possible; just more passport-sensitive than 6 months ago. Verify with recent hires before betting your timeline on it.

**The four-quadrant target list (refreshed for June):**

| Quadrant | Examples | Why it's less passport-sensitive |
|---|---|---|
| **AI-application companies (US)** | Sierra, Decagon, Cognigy, Plaid, Intuit, HubSpot, Canva | Use Claude / GPT via API; weights never touched |
| **AI Integration consultancies + DeployCo partners** | PwC, Deloitte, Accenture, EY · OpenAI DeployCo + Tomoro + the 19-firm consortium · TCS, DXC (Anthropic partners) | Implementation work, client-facing, structurally global |
| **Frontier-lab regional offices** | Anthropic Seoul (just opened), Anthropic Bengaluru (announced), Anthropic London, OpenAI London/Tokyo, Google DeepMind London | Hiring thin; geographic optionality is now strategic for the labs themselves |
| **Regulated-industry AI assurance teams** | JPM / GS / Citi / BNY Mellon model-risk teams; PwC AI assurance; the EO-driven pre-deployment-eval lane | Buyer of the eval, not the model — passport profile mirrors finance, not Big Tech |

**Sources:**
- [`01` §1 — the Fable 5 export-control episode](./01-big-lab-moves.md#1-fable-export-control) `[primary, this edition]`
- [Anthropic on X — official statement on the export-control directive](https://x.com/AnthropicAI/status/2065597531644743999) `[primary]`
- [TechCrunch — The US government's Anthropic models ban was never about an AI jailbreak](https://techcrunch.com/2026/06/15/the-us-governments-anthropic-models-ban-was-never-about-an-ai-jailbreak/) `[secondary]`
- [Medium — Fable 5 / Anthropic and US Government: How AI Export Controls Just Sorted Builders by Passport](https://alirezarezvani.medium.com/fable-5-anthropic-and-us-gorvernment-how-ai-export-controls-just-sorted-builders-by-passport-a-37f0c896cce0) `[analysis]`

### Why it matters to you

- **Job lens:** Re-rank your apply list this week against the four-quadrant table above. If you're a US person, this changes nothing strategic for you — just be aware of the language showing up in JDs. If you're a non-US person, **shift center of gravity** toward quadrants 1, 2, and 3, and *keep* quadrant 4 (it's the lane the EO just created); deprioritize "weights-layer engineering at SF-HQ frontier labs" unless you have an immigration story that handles the regime well.
- **Startup lens:** Geographic optionality became a strategic asset at the lab level — *and* at the founder level. If you've been assuming "build US-first," ask whether your wedge actually requires it. Several of the most fundable 2026 patterns (AI-for-regulated-industries; AI-for-localized-language; integrator tooling) are *better* built from a regional foothold first. The passport-sorting that just happened at the labs creates founder talent worldwide that wasn't there a year ago. Network accordingly.
- **Insight:** **National-security regimes don't reverse, they extend.** The 2026 export-control directive is the kind of policy that, once normalized, gets used again. Plan around it as a permanent feature of the landscape, not a one-time disruption.

→ Cross-link: [`01` §1 the Fable 5 episode](./01-big-lab-moves.md#1-fable-export-control) · [`02` §1 Anthropic Seoul + Bengaluru = regional alternatives](./02-new-emerging.md#1-anthropic-global) · [`ME.md`](../ME.md) (Integration Engineer focus is now *more* defensible, not less).

---

## 2. The pre-deployment-eval lane is now REAL and hiring (Aug 1 framework deadline) {#2-eo-lane-real}

**What changed:** The EO got signed ([`01` §2](./01-big-lab-moves.md#2-trump-eo-signed)), and the framework deadline is **August 1**. That means **mid-July is when JDs go up**. The companies that will hire into this function:

1. **Frontier labs themselves** — internal pre-release-eval orgs (OpenAI, Anthropic, Google DeepMind, Microsoft AI). Roles will appear under titles like "Pre-Deployment Evaluation Lead," "Frontier Model Assurance Engineer," "Model Release Governance."
2. **Bank model-risk teams** (JPM, GS, Citi, BNY Mellon) — they've been doing model risk for credit/trading models for a decade; they're absorbing AI risk *into* that function.
3. **Big-4 consultancies** (PwC, Deloitte, EY, KPMG) — they sell assurance; an EO that creates a *voluntary* framework is *exactly* the opportunity their AI practices are designed to monetize.
4. **Specialist eval startups** (Judgment Labs, Apollo Research, METR-shaped companies) — already small but will be the most-aggressive H2 hirers in the lane.
5. **The classified-benchmark vendor pool** — NSA/CISA/NIST will need contractors; clearance-eligible candidates only.

**The vocabulary to embed in your LinkedIn this weekend:**

- *Pre-deployment evaluation*
- *Frontier-model assurance*
- *Model-release governance*
- *Covered-frontier-model classification*
- *Capability-conditioned safety threshold* (cites *When AI Builds Itself*, [`04` §1](./04-research-progress.md#1-self-improvement-paper))
- *Real-tool evaluation harness* (cites MCP-Atlas / Toolathlon, [2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks))
- *Execution-based evaluation*

**The portfolio artifact (do it this weekend):**

The dual-model sanitiser project carried from [2026-05-20/05 §3](../2026-05-20/05-career-and-startup.md#3-safety-project) → refined on [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact) needs **one more reframing edit**: in the README, add a section titled *"Pre-Deployment Evaluation Position Statement"* that names which capability thresholds you tested for, what tools you ran the agent against, what the pass/fail criteria were, and what the report deliverable would look like for a "trusted partner" review. *That single section* is the difference between "a side project" and "an artifact written in the vocabulary the EO requires."

**Sources:**
- [`01` §2 — the EO signed text](./01-big-lab-moves.md#2-trump-eo-signed) `[primary, this edition]`
- [Latham & Watkins — President Trump Signs Executive Order Establishing AI Cybersecurity and Frontier Model Framework](https://www.lw.com/en/insights/president-trump-signs-executive-order-establishing-ai-cybersecurity-and-frontier-model-framework) `[primary]`
- [`04` §1 — "When AI Builds Itself" capability-conditioned framing](./04-research-progress.md#1-self-improvement-paper) `[primary, this edition]`
- [`04` §2 — deep-research-eval benchmark wave for FinDeepResearch financial-services tie-in](./04-research-progress.md#2-deep-research-eval) `[primary, this edition]`

### Why it matters to you

- **Job lens:** **By Aug 1, the JDs will exist.** *You* should be searchable on the vocabulary above by July 1, and have one artifact ready by July 15. This is the most precisely-scheduled hiring lane of 2026.
- **Startup lens:** The fundable wedge is **the open-source eval harness that conceptually aligns with the classified threshold** — labs/enterprises need a *similar-shape* internal eval to predict whether their next model will be "covered." Sketch what that looks like as an OSS project; ship a v0 even if rough. It's the highest-thesis-alignment open-source contribution you can make this quarter.
- **Insight:** Watch which **Big-4 partner letters** mention the EO by name — that's how you'll know which consultancy is prioritizing the lane. They are the loudest hiring channel for pre-deployment-eval *outside* the labs.

→ Cross-link: [`01` §2 EO text](./01-big-lab-moves.md#2-trump-eo-signed) · [2026-05-22/05 §2 the May "delayed lane" prediction](../2026-05-22/05-career-and-startup.md#2-reprice).

---

## 3. This Friday's action: 30-minute pre-deployment-eval position paper {#3-action-pre-deployment-paper}

Sit down for 30 minutes today. Open a doc. Title it **"Pre-Deployment Evaluation: Position Paper."** Answer four questions:

1. **What would I test in a "covered frontier model" 30-day pre-release review?** Be specific — e.g., real-tool tool-use against MCP-Atlas / Toolathlon ([2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)); deep-research-task accuracy on a FinDeepResearch-shape harness ([`04` §2](./04-research-progress.md#2-deep-research-eval)); jailbreak resistance against the multi-agent extraction pattern that triggered the Fable 5 episode ([`01` §1](./01-big-lab-moves.md#1-fable-export-control)).
2. **What evidence would qualify a model as "safe to release to trusted partners"?** Pass thresholds, sampling design, repeat-test protocols.
3. **What does the report deliverable look like?** Length, audience (NSA/CISA/NIST evaluator + frontier-lab safety org), supplementary appendices.
4. **What's the cost trace?** Apply the [`03` §2](./03-practical-skills-and-tools.md#2-cost-routing-live) cost-routing skill — what does running this eval *cost* per release candidate? This is the line that signals you understand operational reality, not just the safety vocabulary.

Save as `apps/pre-deployment-eval-position-paper.md` in your portfolio repo. Three downstream uses:

- **Cover-letter substance** for Anthropic Solutions, OpenAI FDE, JPM/GS AI-assurance, PwC AI-assurance roles.
- **README spine** for the dual-model sanitiser project artifact ([`03` §2](./03-practical-skills-and-tools.md#2-cost-routing-live)).
- **Pitch backbone** if you decide to attempt a startup in the eval-harness lane.

### Why it matters to you

- **Job lens:** Most candidates will react to the Aug-1 deadline by scrambling to *list* the EO in their bullets. The candidates who beat them will have **already-written artifacts** demonstrating they know what the function actually does. Be the second category, by Sunday night.
- **Startup lens:** The act of writing this position paper *is* the customer-discovery exercise for an eval-harness startup. If, while writing, you find yourself wishing a specific tool existed — that's the wedge. Note it; come back to it later this month.
- **Insight:** One hour of focused work converted into one persistent artifact is the highest leverage move available to you this Friday. Don't break the writing into research first — let the gaps in what you write *be* your research list for next week.

---

## 4. Applications to file this week {#4-applications-this-week}

| Action | Why | Due |
|---|---|---|
| Apply to **2 OpenAI DeployCo** roles (now hiring through DeployCo + Tomoro brand) | DeployCo operational ([`02` §3](./02-new-emerging.md#3-deployco-update)) | This week |
| Apply to **1 Anthropic Seoul or Bengaluru role** if any opening matches (thin queues, just opened) | Anthropic global ([`02` §1](./02-new-emerging.md#1-anthropic-global)) | This week |
| Apply to **2 Anthropic Solutions / Integration roles** with cover-letter line citing *"the pre-deployment-eval direction the EO operationalizes"* | EO signed ([`01` §2](./01-big-lab-moves.md#2-trump-eo-signed)) | This week |
| Apply to **1 JPM / GS / BNY Mellon AI-assurance / model-risk role** | Pre-deployment-eval lane is the EO's surviving content ([`05` §2](#2-eo-lane-real)) | This week |
| Add **TCS + DXC AI Practice** roles (Anthropic partner channel) to your watch-list | Partner network ([`02` §1](./02-new-emerging.md#1-anthropic-global)) | Watch |
| Add **PwC / Deloitte / EY AI-assurance / model-risk** to your watch-list | Pre-deployment-eval lane ([`05` §2](#2-eo-lane-real)) | Watch |

Log every application in [`APPLICATIONS.md`](../APPLICATIONS.md). Cross-link to this edition.

### Why it matters to you

- **Job lens:** Five applications, structured. Each lands you in a distinct lane (FDE/Deployment, Regional, Anthropic-direct, AI-Assurance, Partner-Network) — i.e., five independent shots, low correlation.
- **Startup lens:** The act of writing the cover letters surfaces *which lane resonates* — useful customer-discovery for your own founder direction. Note which application's research is hardest; that's where the market is least transparent and most underbuilt.
- **Insight:** Diversification of *lane* matters more than diversification of *company*. Five Anthropic apps is one shot; one app each across five lanes is five.

→ Cross-link: [`ACTIONS.md`](../ACTIONS.md) (today's tasks) · [`APPLICATIONS.md`](../APPLICATIONS.md) (log here) · [`ME.md`](../ME.md) (Integration Engineer focus → now stronger, see [§1](#1-passport-strategy)) · [`STARTUPS.md`](../STARTUPS.md) (re-score wedges by export-control resilience + EO-vocabulary fit).
