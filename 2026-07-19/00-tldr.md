# TL;DR — 2026-07-19 (Sunday)

> **Continuity note:** Yesterday ([`2026-07-18`](../2026-07-18/)) called the **open frontier as a US-labs-vs-China-labs bipolar race** (Kimi K3 #1 on Frontend Code Arena, Inkling as the US-open counterweight), flagged **Gemini 3.5 Pro still a no-show at T+1**, and marked **Fable 5 free access as terminal at 11:59 PM PT TONIGHT**. Today is the **execution window** for the artifacts those items point at — a review Sunday, not a fresh-scoop Sunday. Cross-links throughout.

Sixty-second skim. **The last day of Fable-5-free, the last-9-days-before-MCP-2026-07-28, and Gemini 3.5 Pro's third-slip becomes a public silence.** Three clocks tick together. **(1)** Anthropic's **Fable 5 free access expires 11:59 PM PT TONIGHT** (third extension, now terminal — [2026-07-18/02 §2](../2026-07-18/02-new-emerging.md#2-fable-5-sunset)) — every hour you haven't captured your empirical Fable-5 evals is an hour of unrecoverable baseline data. **(2)** **MCP `2026-07-28` release-candidate is T-9 days** ([2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md) has the stateless / MCP Apps / Tasks / MRTR read); the migration writeup shipped *this weekend* is a dated artifact on July 28. **(3)** **Gemini 3.5 Pro is silent 48+ hours past target** — [`01` §1](./01-big-lab-moves.md#1-gemini-slip) — the "Google can't ship" narrative is now the base rate, not the risk case. Underneath: **the [Kimi K3 open-weight drop](../2026-07-18/01-big-lab-moves.md#1-kimi-k3) is T-8 (Mon Jul 27)** and lands *inside* MCP-spec-day (Jul 28), stacking two of the year's biggest open-ecosystem events into 30 hours. For you: **the Sunday-block artifact stack — Fable-5 evals + Sonnet-5 routing rule + stateless-MCP migration — is the highest-leverage 2 hours you'll spend on your portfolio this quarter**, because the *timing hook* on each item expires this week.

---

1. **Gemini 3.5 Pro — third slip becomes public silence (T+2, no primary-source signal).** No `gemini-3.5-pro` in the API listing, no ai.google.dev entry, no model card, no pricing page 48+ hours after the July 17 GA target ([2026-07-17/01 §2](../2026-07-17/01-big-lab-moves.md), [2026-07-18/01 §2](../2026-07-18/01-big-lab-moves.md#2-gemini-no-show)). Pricing rumors *hardened* from **$1.25/$10 → $15/$60 + $250/mo Ultra** over 24 hours (Fri→Sat), which reads as pricing-still-being-argued-internally, not a version of "shipping-imminent." **The narrative flip:** "third slip in three months" is now confirmed; Alphabet's coding + reasoning readiness for Q3 is publicly unresolved. → [`01` §1](./01-big-lab-moves.md#1-gemini-slip) `#google #gemini #release-slip`

2. **Fable-5-free sunset (11:59 PM PT tonight) — the 4-hour urgency window.** Anthropic's **third free-tier extension is now terminal**; every eval you don't capture today, you'll pay for tomorrow. [2026-07-18/03 §1](../2026-07-18/03-practical-skills-and-tools.md#1-fable-5-evals) has the 90-min playbook: **pass-rate + $/completed-task + tool-call fabrication rate**, on your own MCP server, three tasks. **Add tonight:** save the **exact API response JSON** (not just the completion) so a two-months-from-now re-baseline against a paid Fable 5 model has *the raw diff*, not just the summary. → [`03` §1](./03-practical-skills-and-tools.md#1-fable-5-evals) `#fable-5 #anthropic #evals #sunset`

3. **MCP `2026-07-28` RC is T-9 — migration writeup is the dated artifact of the quarter.** The stateless / MCP Apps / Tasks / MRTR / OAuth-OIDC spec ([2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md); [Blog RC post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/); [Beta SDKs Py/TS/Go/C#](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/)) is the biggest MCP revision since launch. **Ship an MCP-server migration + writeup THIS weekend** — the artifact is a resume-line only if it's dated **before July 28**, not after. → [`03` §2](./03-practical-skills-and-tools.md#2-mcp-stateless-execution) `#mcp #stateless #2026-07-28 #agents`

4. **Kimi K3 open-weight drop is T-8 (Mon Jul 27) — lands inside MCP-spec-day.** [Kimi K3 already #1 on Frontend Code Arena as a hosted model](../2026-07-18/01-big-lab-moves.md#1-kimi-k3); when weights drop Monday Jul 27, **the *local-runnable* frontier catches up with the *closed-hosted* frontier for the first time this quarter**. Stack that against the July 28 MCP spec: **an open-weight frontier model + a stateless agent protocol shipping in 30 hours**. Every downstream infra decision — router, host, cost model — is a re-decision inside those 30 hours. → [`02` §1](./02-new-emerging.md#1-open-weights-and-mcp-stack) `#kimi #open-weights #mcp #convergence`

5. **The Sunday 2-hour block converts three clocks into one artifact.** Fable-5-evals-tonight + Sonnet-5-routing-rule + stateless-MCP-migration + Kimi-K3-hosted-3rd-leg = **one weekend, four resume lines** for FDE / Applied / Solutions / Deployment-Co roles ([2026-07-17/05](../2026-07-17/05-career-and-startup.md), [2026-07-18/05](../2026-07-18/05-career-and-startup.md)). This is the operational point of a review Sunday. → [`05` §1](./05-career-and-startup.md#1-sunday-block) `#sunday-action #artifact #fde`

6. **Career carry — Ode with Anthropic Karpathy-effect applicant window is closing.** Anthropic × Blackstone × H&F × Goldman × Apollo × GA × Leonard Green × GIC × Sequoia **$1.5B "Ode with Anthropic" launched Jul 15** ([2026-07-17/01 §1](../2026-07-17/01-big-lab-moves.md), CEO Chris Taylor, ex-Fractional AI team). **Apply this week**, cover-letter close cites the **stateless-MCP migration writeup** and the **Fable-5-vs-Sonnet-5 routing table** you'll produce tonight. Both are dated portfolio artifacts a recruiter can validate. → [`05` §2](./05-career-and-startup.md#2-ode-application) `#ode #anthropic #fde #applications`

7. **Watchlist deltas.** Fable 5 free → terminal by midnight ; MCP RC → T-9 ; Kimi K3 weights → T-8 ; Gemini 3.5 Pro → public silence at T+2 ; DeepSeek migration deadline → T-5 (Jul 24 15:59 UTC — silent capability downgrade if you pick v4-pro instead of v4-flash, per [2026-07-16/00](../2026-07-16/00-tldr.md)) ; Anthropic Oct IPO paperwork → live carry from [2026-07-14/01](../2026-07-14/01-big-lab-moves.md). All eight items above roll up to one calendar of the next 9 days.

8. **Skill read of the week (Sunday version).** Every week in 2026, three or four things become *actionable at a specific date*. The interview-differentiating move is **turning that week's dated things into a single dated artifact your GitHub commit-timeline validates.** Not "I read the news." — "I *shipped against* the July 27/28 clock while it was still running." Do that once, and the recruiter reading your GitHub sees the timing hook, then reads the artifact, then closes the tab warmer than they were. → [`05` §1](./05-career-and-startup.md#1-sunday-block).

---

## One thing to DO this Sunday

→ **Run the 2-hour block from [`05` §1](./05-career-and-startup.md#1-sunday-block)** — Fable-5 eval capture (30 min, before midnight PT) + Sonnet-5-default `CLAUDE.md` update (20 min) + stateless-MCP migration on one server (60 min) + public-writeup gist (10 min). The Sunday block is engineered so that if you only get *one hour*, the Fable-5 eval capture is the piece that becomes uncapturable tomorrow.

## Watchlist deltas

- 🔻 **Fable 5 free access:** terminal 11:59 PM PT tonight. Capture evals *now*.
- 🆕 **MCP 2026-07-28 spec T-9 (Jul 28):** migration window closes when the RC becomes the spec. Ship your artifact before then.
- 🆕 **Kimi K3 weights drop T-8 (Mon Jul 27):** the first day a *local-runnable* model that led Frontend Code Arena becomes downloadable — infra planners rebase.
- ➡️ **Gemini 3.5 Pro:** silent at T+2. Do not update the Gemini row in your comparison table until Google ships a primary-source page (model card, pricing, or a `gemini-3.5-pro` in the API list). Watch [DeepMind Blog](https://deepmind.google/blog/) daily.
- ➡️ **DeepSeek migration T-5 (Jul 24 15:59 UTC):** silent capability downgrade if you route `reasoner`→`v4-pro` instead of `v4-flash`. From [2026-07-16/00](../2026-07-16/00-tldr.md) — 5-min audit if you haven't already.
- ➡️ **Ode with Anthropic — apply this week:** window closes as the Karpathy + Blackstone-attention applicant wave lands.
- ⬇️ **Kimi K3 (hosted) as `Frontend Code Arena #1`:** carried from [2026-07-18](../2026-07-18/); adds the pair-with-Sonnet-5-routing angle in [`03` §3](./03-practical-skills-and-tools.md#3-3-model-routing) below.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Sunday block spec in [`05` §1](./05-career-and-startup.md#1-sunday-block) |
| 20 min | [`03` §2](./03-practical-skills-and-tools.md#2-mcp-stateless-execution) (stateless-MCP execution notes) + the [MCP RC post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) itself |
| Tonight | Capture Fable-5 evals BEFORE 11:59 PM PT — [`03` §1](./03-practical-skills-and-tools.md#1-fable-5-evals) |
| Tomorrow | Apply to Ode + 1 Anthropic FDE + 1 OpenAI Deployment Co with tonight's artifact linked — [`05` §2](./05-career-and-startup.md#2-ode-application) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
