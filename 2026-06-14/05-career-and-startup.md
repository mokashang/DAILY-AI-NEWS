# Career & Startup — 2026-06-14 (Sunday)

`#career #startup #focusing-decision #fde #ai-engineer #policy`

The page where today's news lands on your goals from [ME.md](../ME.md). Two of the three sections below are time-sensitive — section 1 is the 90-day re-evaluation that's now overdue; section 3 is the application list for the week starting tomorrow.

---

## 1. The Anthropic-stack focusing decision — 90-day re-evaluation, on schedule {#1-focusing-reeval}

**What changed.** Your [ME.md](../ME.md) commits you to "**Anthropic agentic stack** for portfolio + skill investment. Multi-vendor as production discipline; Anthropic-first for depth." That decision was made when the production-discipline half was theoretical. **As of Friday June 12** it's empirical. The federal government took Anthropic's flagship offline for an indeterminate period; the multi-vendor discipline became mandatory, not aspirational. The "Anthropic-first for depth" half remains correct on capability — but the implicit safety margin disappeared.

**The 90-day re-evaluation matrix.**

| Dimension | Status as of 2026-06-14 | Implication for the focusing decision |
|---|---|---|
| **Capability depth** | Opus 4.8 still live; Sonnet 4.6 live; **Mythos 5 + Fable 5 unavailable until further notice.** Karpathy team has not yet shipped. | Anthropic-first remains valid on depth. The frontier-with-no-replacement still tilts Anthropic. |
| **Career signal** | Anthropic hires more aggressively than OpenAI in Solutions / FDE / Customer Engineering. Bengaluru office (see [`01` §4](./01-big-lab-moves.md#4-india-office)) opens new geographic path. | Strengthens, not weakens, the lane choice. |
| **Stack reliability** | First-ever 72-hour-after-launch federal shutdown of a flagship model. Multi-vendor discipline now mandatory. | **Multi-vendor router shim is now a portfolio requirement, not an option.** Built tonight in [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge). |
| **IPO / equity** | Confidential S-1 filed June 1; Oct 2026 target. Bullish but **Fable 5 shutdown will appear in the public S-1 as a regulatory-risk disclosure** — public market debut may be choppier than the Sept OpenAI debut. | Equity timing tilts toward "later is better" if joining post-IPO; "join pre-IPO if you can lock in pre-S-1-amendment" if joining pre. |
| **Geographic optionality** | Bengaluru office formally opens. India = #2 market. London FDE concentration via the OpenAI-Tomoro acquisition lens. | APAC + UK lanes meaningfully more open than 30 days ago. |
| **Wedge defensibility (startup track)** | Multi-vendor routing + security gate is the [Series A bar](./02-new-emerging.md#4-funding-cool). Anthropic-stack-only wedges are now riskier; multi-vendor-as-feature wedges are stronger. | **Re-spec your wedge with multi-vendor as a first-class feature**, not a hedge. |

**The recommendation.**

- **Keep:** Anthropic-stack as the depth investment. The capability and career-signal arguments stand.
- **Add:** the **multi-vendor router shim** (from [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge)) as the **third active portfolio artifact** in ME.md (alongside MCP server + billing audit).
- **Reframe:** specialty lane is no longer just "AI Integration Engineer" — it's "**AI Integration Engineer with policy / export-control fluency**." That extra qualifier is now a hiring differentiator at every CAISI-adjacent customer.
- **Re-time:** the 90-day re-evaluation cadence stays on schedule; next checkpoint is **2026-09-14** (post-Anthropic-IPO; assess based on public S-1 + post-IPO hiring patterns).

**Sources.** All threading through this edition's `01` and `02` files; the source list there is the citation set for this section.

**Why it matters to you.**

- **Job ·** The "policy fluency" overlay opens two new sub-lanes within the FDE umbrella: **export-control-aware FDE** (Anthropic, OpenAI, GCP Public Sector) and **AI-assurance engineer** (Big-4, banks, Treasury contractors). Add both to your search.
- **Startup ·** Wedge must include multi-vendor as a feature. Re-write your 1-pager.
- **Insight ·** A 90-day re-evaluation cadence that you actually *do* is rare. Most candidates lock a focusing decision once and don't revisit until it fails them. You revisit on schedule; the multi-vendor router shim is the receipt that this cadence works.

`#focusing #anthropic #portfolio #policy #careers`

---

## 2. Interview prep — the post-shutdown vocabulary upgrade for the next 60 days {#2-interview-prep}

**The new things you can credibly mention in any AI-stack interview this quarter.** Use these instead of generic 2025-era talking points; they signal "I read what shipped this month."

| Topic | Talking point | Source / depth |
|---|---|---|
| **Policy** | "The June 2 EO created a 'covered frontier model' designation; June 12 was its first live invocation against Fable 5." | [`01` §2](./01-big-lab-moves.md#2-eo-signed-and-invoked) |
| **Multi-vendor discipline** | "I shipped a router shim on June 14 with a four-stage fallback chain. Here's the repo." | [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) |
| **Cost-aware orchestration** | "I orchestrate with Opus 4.8 and worker with Sonnet 4.6 because the per-step economics broke in favor of routing on June 15 with the Agent SDK metering split." | [`03` §1](./03-practical-skills-and-tools.md#1-jun15-setup) |
| **Eval design** | "I'd plug τ²-Bench for dual-control conversational evals and Agent-Diff for state-diff API-task grading." | [`04` §1–2](./04-research-progress.md) |
| **Self-improvement loop** | "ERL is the cheapest deploy-this-week version of Karpathy's Anthropic team mission — heuristics distilled from trajectories + retrieved at test time." | [`04` §1](./04-research-progress.md#1-tau2-erl) |
| **Security / red-team posture** | "Pliny's published Fable 5 jailbreaks are the free adversarial training set I'd plug into the pre-prompt validator." | [`03` §3](./03-practical-skills-and-tools.md#3-routing-gate-recipe) |
| **Geographic optionality** | "Anthropic's Bengaluru opening + India as #2 market means I'd take a Solutions or FDE role there with no comp gap to perceived prestige." | [`01` §4](./01-big-lab-moves.md#4-india-office) |
| **IPO / public-market context** | "Both labs filed confidential S-1s in the last two weeks; the Fable 5 shutdown becomes a real regulatory-risk disclosure in Anthropic's public S-1." | [`01` §3](./01-big-lab-moves.md#3-ipo-wave-vs-shutdown) |

**Why it matters to you.**

- **Job ·** Each row is one talking point. Eight talking points × four interview rounds = enough material to never repeat yourself. (And each one is specific to events <14 days old, which signals attention.)
- **Insight ·** The 2025-era "I've used Claude Code for X" line is dead. The 2026-Q3 vocabulary is "I've shipped Y artifact in response to Z dated event." Today gave you four dated events.

`#interview #vocab #fde #ai-engineer`

---

## 3. This-week application list (week of Jun 15) {#3-application-prep}

**Five targeted applications + three outreach DMs for the week.** Calibrated for the post-shutdown market.

**Applications (ship by Friday June 19):**

1. **Anthropic — Solutions Engineer, India (Bengaluru)** *[new sub-lane this week]*. The office is hiring; comp band will be locally calibrated, but pipeline + visibility access is top-tier global.
2. **Anthropic — Forward Deployed Engineer, US (Regulated Industries focus)** *[reframed]*. Lead with "policy fluency" — reference the EO + Fable 5 invocation in the cover letter.
3. **OpenAI — Forward Deployed Engineer (Tomoro acquisition cohort)** *[carryover from 2026-05-22]*. Tomoro's London / Edinburgh / Manchester / Singapore / Sydney / Melbourne posts will start opening over the next 30 days; pre-stage your application now.
4. **Sierra — Customer Engineering / Solutions Engineer** *[new line of attack]*. **Lead with τ²-Bench fluency in the cover letter** — it's their own benchmark. Demonstrates technical literacy of their stack.
5. **A US bank's AI assurance / model risk function** *[net-new lane]*. JPMC, Goldman, MS, BofA all staffing model-risk groups that absorb the new "covered frontier model" framework. Search "model risk AI," "AI governance engineer," "responsible AI" titles.

**Outreach DMs (send Monday or Tuesday morning):**

1. **A Meta-alumni → Anthropic Solutions Engineer** (the [2026-05-22 reply window](../2026-05-22/05-career-and-startup.md#3-meta-followup) target, deferred to today). Subject: "On the Fable 5 shutdown — and a router I shipped over the weekend." Attach the [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) repo link.
2. **A Sierra Customer Engineering hire from H2 2025**. Subject: "Reading τ²-Bench this weekend; one question on the dual-control framing." Reference [`04` §1](./04-research-progress.md#1-tau2-erl) specifically.
3. **A founder in the agentic-security category** (Pi Security / Exaforce / similar — pick the closest match to your portfolio). Subject: "How are you handling the Pliny jailbreak corpus as a training input?" Reference [`03` §3](./03-practical-skills-and-tools.md#3-routing-gate-recipe).

**Why it matters to you.**

- **Job ·** Five applications + three DMs = an over-the-bar weekly outreach volume. Time-boxed; no perfectionism. The DM angles are 100 % news-grounded — none of the recipients will have seen those exact framings from anyone else this week.
- **Startup ·** The agentic-security founder DM doubles as a wedge-discovery conversation. Ask three questions, listen, take notes for [STARTUPS.md](../STARTUPS.md).
- **Insight ·** Cadence > intensity. Five + three this week. Five + three next week. Track in [APPLICATIONS.md](../APPLICATIONS.md). Don't deviate.

`#applications #outreach #fde #solutions-engineer #weekly`

---

## Cross-page

- [`00`](./00-tldr.md) — the 60-sec skim of the day.
- [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) — the event that drove every recommendation here.
- [`03` §2](./03-practical-skills-and-tools.md#2-anthropic-stack-hedge) — the artifact this page assumes you ship tonight.
- [ME.md](../ME.md) — update with the third active portfolio artifact reference + the "policy fluency" specialty-lane qualifier.
- [WATCHLIST.md](../WATCHLIST.md) — convert the Fable 5 shutdown thread to the top-priority row when you update tomorrow morning.
- [APPLICATIONS.md](../APPLICATIONS.md) — log the five + three from §3 above.
