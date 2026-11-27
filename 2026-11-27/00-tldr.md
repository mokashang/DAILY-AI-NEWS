# TL;DR — 2026-11-27 (Black Friday, Friday after Thanksgiving)

Sixty-second skim. **The two weeks since 2026-11-14 resolved the IPO story and opened a new one: Anthropic went public, the stock broke below its offer price within a week, and a nonprofit coalition filed a California lawsuit asking a judge to freeze further frontier-model releases — all in the same window.** On **Nov 18 Anthropic priced the largest IPO on record at $83/share** (above the $70–78 range, ~$81.3B offering, 980M shares, ~20% retail allocation). On **Nov 19** ANT opened **+34% at $111.50**, closed debut at **$97.17**. By **Nov 24** it closed at **$81.91 — below the $83 IPO price** (down ~26.5% from the debut intraday peak). Premarket today: **+3.6%**, not the +10% circulating on X. Alongside: **Dario and Daniela Amodei each sold 3.37M shares to IPO underwriters on Nov 20** (disclosed in 424B filings). On **Nov 12** four nonprofits (Public Citizen, Heat Initiative, Irreplaceable Education Fund, Alliance for Secure AI) **sued Anthropic, Google, Meta, OpenAI, and SpaceX SI in SF Superior Court under CA Unfair Competition Law**, asking the court to bar new model releases. Also hot: **OpenAI frontier models + Codex live in Google Cloud Model Garden** (private preview, Oct 21 → scaling now), **Gemini 4 in multi-agent production** (six math papers reportedly produced by a DeepMind multi-agent system on Gemini 4), **BrightAI $97M at $750M** for physical AI, and **Claude Code 2.1.317 → 2.1.327** shipped three builder-grade upgrades in three weeks. The re-price for your goals: **the public-lab era just began; the ex-Anthropic liquidity wave starts May 2027 (~6-month lockup); the MSFT buyout deadline is Monday**.

---

1. **Anthropic IPO: priced $83, opened $111.50, closed Nov 24 at $81.91 — below IPO.** Nov 18 pricing above the $70–78 range; **~$81.3B offering** (980M shares, largest IPO on record, topping SpaceX's June 2026 $85.7B); ~20% retail allocation. Nov 19 open +34% at $111.50, debut close $97.17. By Nov 24 slid 6.54% to **$81.91 (below $83 IPO)**. Premarket Nov 27: +3.6%. Dario + Daniela Amodei each sold 3.37M shares to underwriters on Nov 20. **Lockup expiry ≈ May 2027 — mark the calendar.** → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-debut) `#anthropic #ipo #ant`

2. **Nov 12 Public Citizen + 3 lawsuit asks CA court to freeze frontier AI.** Plaintiffs: Public Citizen, Heat Initiative, Irreplaceable Education Fund, Alliance for Secure AI. Defendants: Anthropic, Google, Meta, OpenAI, SpaceX SI. Filed in SF Superior Court under CA Unfair Competition Law. **First serious US judicial attempt to halt frontier model releases** — overhang risk now a real line item on every private-market round and every hire-side comp offer with large equity grants. → [`01` §4](./01-big-lab-moves.md#4-public-citizen-lawsuit) `#policy #legal #overhang`

3. **OpenAI frontier models + Codex live in Google Cloud Model Garden.** Oct 21 announcement, private preview with GPT-6 Astra / GPT-6.1 Sol / GPT-6 Luna. Customers can connect Codex CLI/Desktop directly to Gemini platform for inference, buy OpenAI models through GCP Marketplace, apply existing GCP commits. **The "competitor on your cloud" model is now normal** — multi-model routing is the engineering default. → [`01` §2](./01-big-lab-moves.md#2-openai-gcp) `#openai #google #multi-cloud`

4. **Gemini 4 is in production enough to publish math.** Google Research reportedly published **six math papers** produced by its multi-agent framework **running on Gemini 4** (per aiweekly.co). Signals Gemini 4 is out of post-training and inside DeepMind's own research loop, even if no consumer GA yet. Three-way frontier race just compressed again. → [`01` §3](./01-big-lab-moves.md#3-gemini-4-math) `#google #gemini #research`

5. **BrightAI $97M Series B at $750M for physical AI (Nov 18).** Smith Point Capital led; **GE Vernova** strategic (energy-vertical lock-in); Khosla, Inspired, Upfront returned. Platform: sensors + robots + field software for energy, water, waste, heavy industry. Total raised: $184M. Expanding into Europe + Asia. **"Physical AI for essential services" is now a backable category** — the first vertical adjacent to the GridCARE/Crusoe lane you've been tracking. → [`02` §1](./02-new-emerging.md#1-brightai) `#funding #physical-ai #infra`

6. **Anthropic "30K AI agents on R&D, Claude writes 26% of our code" claim circulates.** MindStudio aggregator reports Anthropic says ~30K Claude agents run internal research+engineering tasks with Claude credited for ~26% of Anthropic's R&D work. Figure is unconfirmed by Anthropic directly but — if even roughly true — it validates the **"AI firms will have fewer people per $B revenue than any prior software firm"** thesis and reshapes new-grad expectations. Verify via Anthropic's next shareholder letter (first one due as a public company). → [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-debut) `#anthropic #productivity #hiring`

7. **Anthropic Rust-rewrote the Messages API with Claude agents — reported 70% lower CPU, 80% lower memory.** Aggregator report (aiweekly.co) describes a Python → Rust rewrite driven by Claude agents. Unconfirmed, but matches the industry pattern: **"vibe-rewrite your performance-critical path in Rust"** is now a documented production playbook. → [`03` §4](./03-practical-skills-and-tools.md#4-rust-rewrite) `#performance #rust #vibe-coding`

8. **Claude Code 2.1.317 → 2.1.327 in three weeks.** 2.1.317 (Nov 2): **cost reports for gateway admins**, **Agent SDK hooks that can block on failure**. 2.1.326 (Nov 16): **Code Mode + agent teams coexist**, **/status row explains why features are off**, **Remote Control replies stream to phones/browsers as they're written**. 2.1.327 (Nov 17): **first Bash command runs faster** (startup files pre-approved), **Windows + PowerShell speedups**. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-cadence) `#claude-code #tooling`

9. **Funding snapshot Nov 14–27:** BrightAI $97M/$750M (Nov 18); 7 rounds >$2M in 24h to Nov 18 (~$179.5M total). Thinking Machines Lab **$5B Seed** on Nov 6 (per one aggregator — cross-check). OpenAI reportedly raising **$15B at $1.25T** (CNBC Nov 12; OpenAI has not confirmed). Nov 9–13 weekly: 40 USD-denominated rounds, $6.0B. **~2.5% of deals took ~65% of dollars** (unverified but directionally matches prior-month pattern). → [`02`](./02-new-emerging.md) `#funding`

10. **Microsoft 60K voluntary buyout: Dec 1 deadline = Monday.** Program opened Nov 10; **~27% of global workforce** eligible (includes VP). Industry baseline 3–5% uptake → **1,800–3,000 ex-MSFT engineers hit market Jan 1**. Third voluntary-separation program at MSFT in 2026 — pay-to-leave is the Big Tech preferred playbook over RIFs. **Beat the January wave: fire 5 applications this weekend.** → [`05` §2](./05-career-and-startup.md#2-msft-buyout-deadline) `#msft #timing #jobs`

11. **Research surface Nov 14–27:** UCSB/MIT/IDSIA paper argues **LLM "exploration" via temperature sampling + tree search is not genuine exploration** — big implication for RL-on-LLM pipelines (secondary summary; find the arXiv ID). **WikiSkill** (compile agent experience into persistent skill memory), **TTPO** (test-time policy optimization), **UrbanGround** (local perception → spatial agency) trended on Hugging Face Papers. **Six Gemini-4 math papers** from DeepMind's multi-agent system. → [`04`](./04-research-progress.md) `#arxiv #rl #agents`

12. **FDE lane, Nov 2026 update:** LinkedIn's January 2026 report crystallized — **FDE roles grew 42× between 2023 and 2025**, vs. 13× for "AI engineer." OpenAI's June 2026 **$1B dedicated FDE org** investment is now the industry comp anchor. Mid-level pay bands: **$200–280K base / $300–450K TC**. Candidates searching only the literal title miss ~1/3 of the live market — **search "Deployed Engineer", "Solutions Engineer", "Customer Eng", "AI Integration" in parallel**. → [`05` §3](./05-career-and-startup.md#3-fde-crystallized) `#fde #careers #comp`

13. **The re-price of this edition: public-lab era reframes employee equity.** With ANT trading (even below IPO), **base salary vs. RSU math becomes legible for the first time in frontier-lab hiring**. For CS grads: a **$220K base + $150K ANT RSU** at a small lab is now worth *more* than before (public, liquid, taxable at known marks), but RSUs at a pre-IPO lab are worth *less* per face-value dollar (no comparable). **Ask recruiters for ANT-equivalent trading comp, not just "last-round valuation × shares".** → [`05` §1](./05-career-and-startup.md#1-ant-reprices-equity) `#comp #equity #hiring`

14. **One-shot thread from Thanksgiving week:** the OpenAI × Google Cloud deal + Anthropic IPO + Nov 12 lawsuit in one 20-day window = **"the frontier is a public, regulated, multi-cloud market now"**. The old mental model ("pick your lab, specialize") still works for careers. The new model that unlocks ("route across all three") is the *skill* that gets you an FDE offer at any of them. → [`03` §5](./03-practical-skills-and-tools.md#5-multi-model-router) `#frontier #multi-model #skills`

---

## One thing to DO this Black Friday weekend

→ **Use the 4-day gap (Thu Nov 26 → Sun Nov 29) to ship one portfolio artifact.** Pick ONE: (a) a **multi-model router** (OpenAI via GCP + Anthropic ANT-period API + Gemini 4 preview) with `/route` CLI + 5 example tasks + eval table — the single most interview-ready skill of this quarter; (b) an **MCP server** that wraps a real workflow you use (gmail triage, calendar prep, invoice reconciliation) — the #1 portfolio artifact for FDE applications; (c) **5 FDE applications + 1 Anthropic Solutions application** before Sunday night — the MSFT Dec 1 wave hits Monday. **Do not do all three — one shipped artifact beats three half-done.** Details in [`03` §5](./03-practical-skills-and-tools.md#5-multi-model-router) and [`05` §2](./05-career-and-startup.md#2-msft-buyout-deadline).

## Watchlist deltas

- 🆕 **ANT ticker price watch:** new thread. Track whether ANT stays below $83 through Dec 1 (first analyst initiations due), the ~May 2027 lockup expiry (employee liquidity + angel-check wave), and whether short interest climbs after the Public Citizen lawsuit is docketed.
- 🆕 **Public Citizen et al. v. Anthropic/Google/Meta/OpenAI/SpaceX SI:** new thread. Watch for motion-to-dismiss timing (typically 30–60 days), judge assignment, and whether a preliminary-injunction hearing gets scheduled before year-end.
- 🆕 **OpenAI in Google Cloud GA window:** new thread. Private preview Oct 21 → "general availability in coming weeks" per OpenAI. Watch pricing disclosure (will Model Garden match OpenAI API list?) and whether Anthropic follows on AWS Bedrock terms.
- 🆕 **Gemini 4 math papers:** new thread. Watch which arXiv IDs land under Google DeepMind authorship between now and mid-Dec, and whether the "multi-agent on Gemini 4" setup gets documented in a methods paper.
- 🆕 **BrightAI + GE Vernova physical-AI stack:** new thread. First large strategic from a utility-grade partner. Watch next vertical-infra round (water utilities? pipeline?) and whether Crusoe/GridCARE announce comparable partnerships.
- 🆕 **"30K Claude agents on R&D" / 26% of Anthropic R&D:** new thread. Treat as unverified until Anthropic's first public filing (10-Q due ~Feb 2027). If confirmed, resets new-grad hiring math at every lab.
- 🆕 **Python → Rust vibe-rewrite pattern:** new thread. Watch which teams publish their rewrite writeup first (cloudflare? vercel? datadog?) — this is the 2026 equivalent of the "we rewrote the hot path in Go" blog wave.
- ➡️ **MSFT 60K voluntary buyout (from 2026-11-14):** Dec 1 deadline = Monday. Resolve this weekend by firing applications before the wave hits Jan 1.
- ➡️ **Claude Fable 5.2 + Whiteboards/Sheets/Data (from 2026-11-14):** no major product moves this fortnight — the IPO sucked all the air. Watch for Dec–Jan post-IPO roadmap drops.
- ➡️ **FDE lane (from 2026-11-14 and 2026-10-14):** LinkedIn 42× datapoint crystallized the trend. Comp bands held at $200–280K base / $300–450K TC.
- ⬇️ **"Latest model" fluency:** further deprecated. Three-way frontier race + cross-cloud availability means **routing is the skill**, raw fluency is a commodity that halves every quarter.
- ⬇️ **Generic "AI-SaaS wrapper" pitch for late-stage rounds:** Public Citizen lawsuit + Ramp AI Index spend-stalling + token price compression means pure wrappers are stuck between a regulatory ceiling and a margin floor.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-anthropic-ipo-debut) (the ANT debut + pullback) |
| 20 min | [`01` §1–4](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — IPO + lawsuit + MSFT deadline + equity reframe |
| Today | [`05` §2](./05-career-and-startup.md#2-msft-buyout-deadline) — 5 FDE apps before Sunday night |
| This weekend | [`03` §5](./03-practical-skills-and-tools.md#5-multi-model-router) — ship one multi-model-router artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
