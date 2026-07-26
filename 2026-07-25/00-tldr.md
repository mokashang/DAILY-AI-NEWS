# TL;DR — 2026-07-25 (Saturday)

Sixty-second skim. **The workhorse tier repriced, the frontier consolidated to three labs, and the MCP protocol grew up — all in the same week.** **Claude Opus 5 shipped yesterday at Opus 4.8 pricing** (96% SWE-bench Verified, 1M context, per-request `effort` toggle). **OpenAI raised its 2030 infrastructure budget to ~$750B** and named Project Camellia (Georgia). **Amazon shut down its AGI Lab** — the sustainable frontier is now Anthropic + OpenAI + Google, everyone else pivots to distribution. **MCP 2026-07-28 goes stateless on Monday** — the biggest platform migration of the summer. And the **Anthropic Fellows Nov 2026 cohort is reported to close tomorrow (July 26)** — verify tonight and, if real, submit.

*(Note: last edition in this archive was 2026-05-22. This is a fresh week's read, not a continuation — I've cross-linked back where a thread survives.)*

---

1. **Claude Opus 5 shipped 2026-07-24 at Opus 4.8 pricing.** $5/$25 per MTok, 1M context, `effort=low|medium|high` per request, 96.0% SWE-bench Verified, 70.57% OSWorld 2.0. Two Opus generations without a price hike. The **effort toggle is the story** — cost/quality routing moves from API-tier to compiler-level knob. → [`01` §1](./01-big-lab-moves.md#1-opus-5) · [`03` §1](./03-practical-skills-and-tools.md#1-opus-5-effort) `#anthropic #claude-opus-5 #effort-toggle`

2. **OpenAI raised 2030 capex to ~$750B; Project Camellia is the first self-built campus.** ~$20B / 1,400-acre / 3.2 GW data center in Effingham County, GA. OpenAI is quietly **forking into a software company + a utility**; the S-1 (filed 2026-05-22) targets ~$1T. Anthropic's ~$47B ARR vs. OpenAI's ~$24B is an asymmetric revenue-to-valuation gap. → [`01` §2](./01-big-lab-moves.md#2-openai-750b) `#openai #capex #ipo #project-camellia`

3. **Amazon shut down its AGI Lab (2026-07-22→24), laid off frontier-model staff.** Follows Rohit Prasad (SVP AGI) and David Luan (AGI Lab head) departures. Strategic shift: from frontier research to **enterprise deployment via Bedrock + a $1B "embed AWS engineers with customers" initiative.** The **three-lab market** (Anthropic + OpenAI + Google) is the operating assumption for capital and talent now. → [`01` §3](./01-big-lab-moves.md#3-amazon-agi-lab) · [`05` §3](./05-career-and-startup.md#3-meta-amazon-talent) `#amazon #agi-lab #layoffs #consolidation`

4. **MCP 2026-07-28 stateless spec finalizes Monday.** Sessions removed; OAuth 2.1 for connection; new **MCP Apps / Tasks / Server Cards** primitives; per-request `Mcp-Method` / `Mcp-Name` headers for LB-friendly routing. Servers deploy behind a plain round-robin load balancer. Migration is a **portfolio + freelance-revenue** window. → [`02` §4](./02-new-emerging.md#4-mcp-stateless) · [`03` §2](./03-practical-skills-and-tools.md#2-mcp-migration) · [`05` §4](./05-career-and-startup.md#4-migration-window) `#mcp #stateless #protocol #oauth`

5. **Anthropic Fellows Nov 2026 cohort reported to close 2026-07-26 (tomorrow).** Stipend-supported, 6-month, remote-friendly; ~50% of Anthropic technical staff don't have PhDs. **Verify on alignment.anthropic.com tonight; if real, submit tonight.** Highest-EV single application of the year for a CS grad student. → [`05` §1](./05-career-and-startup.md#1-fellows-deadline) `#anthropic #fellows #ai-safety #deadline`

6. **The FDE market has ~10×'d — Anthropic Applied AI + Deloitte's Anthropic FDE = two funnels to run this week.** Median TC $385K mid / $610K staff; equity 55–70% of TC; **~60% of coding-passing candidates wash out on the customer-conversation round.** Apply to the Deloitte GPS "Anthropic FDE" role by Wednesday; record a 2-minute customer-conversation clip for your portfolio. → [`05` §2](./05-career-and-startup.md#2-fde-market) `#fde #applied-ai #anthropic #careers`

7. **Emerging capital: Etched $10.3B ASIC (Sequoia-led), Cathedral $1.4B (DOGE alumni, defense-cyber), Humanoid $1.35B (Europe's first humanoid unicorn), SAP+Prior Labs = EU frontier lab by acquisition.** The seam under [OpenAI's $750B](./01-big-lab-moves.md#2-openai-750b): capital is splitting between **more scale** (labs own the utility) and **more specialization** (Etched changes the hardware assumption). Pick a side. → [`02` §1–3](./02-new-emerging.md#1-etched) `#funding #chips #defense #robotics #eu-ai`

8. **Research: LHTB is the new hard eval for long-horizon coding agents** (top model ~15.2% pass@1 at 0.95 credit); **two RL-post-training compute-allocation papers** landed with real FLOP-accounting; **Anthropic's Project Pilot / Drone-Bench** isolates *scene reconstruction* as the blocker for embodied autonomy. → [`04` §1](./04-research-progress.md#1-lhtb) · [`04` §2–3](./04-research-progress.md#2-rl-compute-allocation) · [`04` §4](./04-research-progress.md#4-project-pilot) `#arxiv #benchmarks #rl #embodied`

---

## One thing to DO this Saturday

→ **Do the two Anthropic-facing moves tonight, one artifact tomorrow.**
1. **Tonight — verify + submit Fellows.** Open [alignment.anthropic.com — Anthropic Fellows Program 2026](https://alignment.anthropic.com/2025/anthropic-fellows-program-2026/); confirm the July 26 deadline; if real, write the 1-page research direction (an alignment/eval angle you can honestly defend) and submit ([`05` §1](./05-career-and-startup.md#1-fellows-deadline)).
2. **Tonight — start the Deloitte-Anthropic-FDE application** so you can submit by Wednesday ([`05` §2](./05-career-and-startup.md#2-fde-market)).
3. **Sunday afternoon (2–4 hours) — ship the merged weekend artifact:** Opus 5 planner (`effort=high`) + Opus 5 worker (`effort=medium`) + Haiku verifier, evaluated against a **fresh 07-28 stateless MCP server** you migrated, with a per-step cost log. One repo, three interview questions answered — orchestration, real-tool verification, cost predictability ([`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact)).

## Watchlist deltas since the 2026-05-22 edition

*Two months have passed. The threads that survived:*

- 🆕 **Claude Opus 5 (2026-07-24)** — new thread. The workhorse repriced. Effort toggle is the sub-thread to track (per-tool effort, effort-adaptive budgets are the natural next knobs).
- 🆕 **OpenAI $750B 2030 capex + Project Camellia** — extends the S-1 thread from 2026-05-22; the IPO is now landing against a materially larger capital-need story.
- 🆕 **Amazon AGI Lab closure** — new thread. Three-lab consolidation.
- 🆕 **MCP 2026-07-28 stateless spec** — new thread. First real protocol maturation moment for MCP.
- 🆕 **Anthropic Economic Index connector + $200M Economic Futures Research Fund + $20M Public First Action donation.** New thread — Anthropic building the policy environment it wants to inherit.
- ➡️ **Ramp adoption leadership:** Anthropic 34.4% of business AI spend vs. OpenAI 32.3% — first month Anthropic leads. Extends the "Anthropic overtakes OpenAI in business adoption" thread from [2026-05-14](../2026-05-14/).
- ➡️ **FDE / Applied AI Engineer market:** the +800% YoY signal from [2026-05-17](../2026-05-17/) matured to +1,165% YoY, ~1,500 US postings, formal comp reports.
- ⬇️ **Trump AI EO** — still postponed as of last archived signal; keep the vocabulary (pre-deployment eval, model-release governance, AI assurance) but treat the *category* as scheduled-not-staffed.
- ⬇️ **Karpathy at Anthropic pre-training** — no fresh public product from that team yet; wait for the paper drop.
- 🆕 **YC S26 in flight (July–Sept)** — "replace, don't assist" is the explicit RFS filter; 3 cold-DMs to overlap founders this week ([`05` §5](./05-career-and-startup.md#5-yc-s26)).

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Opus 5 in [`01` §1](./01-big-lab-moves.md#1-opus-5) + Fellows deadline in [`05` §1](./05-career-and-startup.md#1-fellows-deadline) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) (Opus 5 + OpenAI $750B + Amazon AGI Lab) + [`03` §1–2](./03-practical-skills-and-tools.md) (effort toggle + MCP migration) — the four signals that changed your near-term plan |
| Tonight | [`05` §1](./05-career-and-startup.md#1-fellows-deadline) — Fellows verify + submit; start Deloitte-FDE app |
| Sunday | [`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact) — ship the merged weekend artifact (Opus 5 team × 07-28 MCP server × cost log) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
