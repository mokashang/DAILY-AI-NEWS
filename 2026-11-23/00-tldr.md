# TL;DR — 2026-11-23 (Monday)

Sixty-second skim. **The nine days since the last edition compressed a quarter of normal news into one week: Anthropic actually went public (ANT priced Nov 18 at $83, popped 34% intraday to $111.50 on Nov 19, closed the week at ~$90), and OpenAI + Google answered with GPT-6.2 Astra + Sol (Nov 17) and Gemini 4 Neon (Nov 18) — three frontier models shipped inside 48 hours of the IPO.** Anthropic raised **~$81.3B** — the largest IPO on record — on **$19.7B TTM revenue** disclosed in the S-1; the stock is now trading **below Day-1 close but well above the $83 offer price**, with the **~6-month lockup expiry landing in late May 2027** as the single most-watchable date on the AI calendar. OpenAI's **GPT-6.2 Astra ($8/$40 per M, ~20% cheaper than GPT-6)** is **#2 on Artificial Analysis Intelligence Index behind Claude Fable 5.2**; Google's **Gemini 4 Neon ($3/$15 per M)** is **#3 overall, #1 on Vending-Bench 2 ($16,843) and SEC-bench Pro (90.5%)** but **trails Opus 5.5 on Terminal-Bench 4.1 and FrontierCode 2.0** — coding is still the Claude moat. Underneath: **Sierra reportedly in talks to raise ~$1.5B at ~$30B (2× May mark)**, the **Ramp AI Index flipped to a regime change on token spend (+10.5% MoM, Anthropic 49.3% share)**, **Microsoft's 60K-employee buyout deadline hits Dec 1 (8 days away)**, and **Claude Code 2.1.326 wired Code Mode into agent teams**. Research-side: **Terminal-Bench 2.1 audit (arXiv 2611.08417)** found ~30% of 2.0 tasks broken — explains half the "my coding score moved" chatter you'll hear this week.

---

1. **Anthropic (ANT) is public.** Priced **980M Class A shares at $83 on Nov 18** (above $70–78 range, upsized from 825M), **~$81.3B raise — largest IPO ever**. Day 1 (Nov 19): opened **$111.50 (+34.3%)**, intraday $115.10 high / $92.72 low, closed **$97.17 (+17%)**. Market cap at close widely cited **~$1.5T fully diluted**. Today (Nov 23): **~$89.77, below Day-1 close** but comfortably above offer. **Lockup expiry = ~May 2027** — the hottest "ex-Anthropic researcher seed" window of the cycle. → [`01` §1](./01-big-lab-moves.md#1-ant-ipo) `#anthropic #ipo #comp`

2. **OpenAI GPT-6.2 Astra + Sol launched Nov 17.** Astra **$8/M in · $40/M out** (cache $0.40), **20% cheaper than GPT-6 Astra** and matches Fable 5.2 pricing exactly. Sol is **$2/$10** with 2×/1.5× surcharge above 272K ctx. Astra **+5.2 pts on Agents' Last Exam at <1/3 the cost**, reportedly **first model to hit "High" AI self-improvement threshold** under OpenAI Preparedness Framework (single source — verify). Astra lands **#2 behind Fable 5.2** on Artificial Analysis Intelligence Index. → [`01` §2](./01-big-lab-moves.md#2-gpt-62) `#openai #pricing #models`

3. **Google Gemini 4 Neon — the 4th Gemini 4 model in 7 weeks (Nov 18).** Sequence: Argon (Oct 13 GA) → Carbon (Nov 10) → Hydrogen (Nov 12) → **Neon (Nov 18)**. Pricing **$3/$15 per M, 1M ctx**. Intelligence Index **61 @ highest effort, #3 overall**; **#1 on Vending-Bench 2 ($16,843)** and **SEC-bench Pro (90.5% vs Sol 88.3%)**; **trails Opus 5.5 on Terminal-Bench 4.1 and FrontierCode 2.0**. Coding is explicitly its weakest axis. → [`01` §3](./01-big-lab-moves.md#3-gemini-4-neon) `#google #gemini #models`

4. **The three-model week structure.** Fable 5.2 + GPT-6.2 Astra + Gemini 4 Neon now sit at the same $8–$3 input price band, with **Fable #1, Astra #2, Neon #3** on the public intelligence index. Price-per-intelligence-point has fallen **~30% in 10 weeks**. The coding axis is still a Claude single-vendor game (Terminal-Bench 4.1, FrontierCode 2.0); the math/reasoning axis is tightest (<5 pts between the three). → [`02` §3](./02-new-emerging.md#3-three-model-week) `#market-structure #pricing`

5. **Sierra reportedly in talks to raise ~$1.5B at ~$30B (Nov 18, per The Information).** ~**2× May's $15–15.8B mark** when they raised $950M. Report-of-talks, not a closed round — verify before wiring into pitch math. Confirms the "AI customer-service agent" category is still the dominant enterprise agents' logo. → [`02` §1](./02-new-emerging.md#1-sierra) `#funding #agents #revaluation`

6. **NVIDIA supply-chain expansion (Nov 18).** Commitments with **Amkor, Foxconn, Kinsus, Samsung Electro-Mechanics, SPIL, TSMC** for substrates/advanced packaging/wafers. **Vera Rubin NVL72 + Vera CPUs now in volume shipment Q3 2026 on TSMC 5nm/3nm + CoWoS**. No dollar figures disclosed. Signal: NVIDIA pricing in 2027 demand explicitly, not just 2026. → [`01` §4](./01-big-lab-moves.md#4-nvidia-supply) `#nvidia #infra`

7. **Ramp AI Index Nov 11 — token-spend regime change.** US AI adoption **56.8% (+1 pp MoM, +13.3 pp YoY)**. Vendor share: **Anthropic 44.8% / OpenAI 40.6%**. **Total token spend +10.5% MoM** (prior months were ~flat — this is the break). **Anthropic token share 49.3%**. Top-1% "AI-pilled" firms now spend **$10,199/employee/month** (up from the $7,500 last cited); median **$16.32**. Engineering is **~72% of classified AI spend** (via secondary; verify). → [`05` §3](./05-career-and-startup.md#3-ramp-index) `#ramp #spend #anthropic`

8. **Microsoft 60K buyout — Dec 1 deadline is 8 days out.** Industry baseline 3–5% uptake → **1,800–3,000 engineers hit market Jan 1**. Third voluntary-separation in 2026. **Apply to AI startups this week** before the Q1 2027 applicant flood. → [`05` §2](./05-career-and-startup.md#2-msft-buyout-deadline) `#msft #layoffs #timing`

9. **Research: Terminal-Bench 2.1 Audit (arXiv 2611.08417).** ~**30% of Terminal-Bench 2.0 tasks had issues**; authors released 2.1 with repairs. **This explains why Terminal-Bench 2.1 vs 4.1 scores move between model announcements** — the harness itself was in flux. Lesson for your FDE portfolio: **publish YOUR benchmark harness, not just scores**. → [`04` §2](./04-research-progress.md#2-terminal-bench-21) `#arxiv #evals #benchmarks`

10. **Research: Research-agent delivery (arXiv 2611.14364, Nov 10).** Argues **benchmark scores overstate real-world agent reliability** in ongoing projects — the standalone-task framing hides degradation across multi-session work. **SlackBench (arXiv 2611.05512)** confirms: across 33 frontier models, best score ~80%; most agents <66% on workplace chat + evolving repo tasks. → [`04` §3](./04-research-progress.md#3-research-agent-delivery) `#arxiv #agents #evals`

11. **Claude Code 2.1.319 → 2.1.326 (Nov 6 → 16).** 2.1.319 was **>50% security fixes** (Bash permission bypass + worktree sandbox escape — patch if you haven't). 2.1.326 **wires Code Mode into agent teams**, catches malformed tool rules at startup, tightens default permissions. **Code Mode + agent teams is the pattern to add to your portfolio MCP this week.** → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code) `#claude-code #security #agents`

12. **FDE compensation refresh.** Per Paraform: **Anthropic FDE comp $300K–$1.2M** depending on level (ceiling is outlier, not base). Landscape unchanged from mid-fall: OpenAI ~26 reqs, Palantir ~48, Anthropic 6. With ANT now public, **RSU math becomes legible for the first time** — negotiate on grant *shares*, not grant dollars. → [`05` §4](./05-career-and-startup.md#4-fde-comp) `#fde #comp #negotiation`

13. **The re-price of the week: the lockup clock is now running.** ANT public + $81.3B raised + ~6-month lockup → **late May 2027 is the single most-watchable date** in AI venture. Expect: (a) ex-Anthropic researcher seed wave Q2 2027, (b) Anthropic internal attrition Q3 2027, (c) backfill req surge Q3 2027 — the **Aug–Oct 2027 window is when "I worked at public-era Anthropic" becomes a hiring premium**. Plan 18 months out. → [`05` §1](./05-career-and-startup.md#1-ant-comp-aftermath) `#anthropic #timing #careers`

---

## One thing to DO this Monday

→ **Spend 45 minutes auditing your three-model routing policy this evening.** With Fable 5.2 (#1 intelligence, #1 coding, $8/$40), GPT-6.2 Astra (#2 intelligence, $8/$40), and Gemini 4 Neon (#3 intelligence, #1 Vending-Bench + SEC-bench, $3/$15) all live at overlapping price points, **anyone shipping agent code without an explicit routing policy is overpaying 2–5×**. In your portfolio repo, add a `router.md` that names: (1) default model, (2) escalation model, (3) which task classes each wins (coding → Opus/Fable, cost-floor general → Neon/Sol, agent-tool-heavy → Astra), (4) the eval you used to decide. **Ship it tonight, push to GitHub, link from your résumé.** This is the single most legible "I understand the 2026 market" portfolio artifact for any FDE/Solutions application. Details in [`03` §2](./03-practical-skills-and-tools.md#2-routing-policy).

## Watchlist deltas

- 🆕 **ANT trading + lockup (May 2027):** new thread. Track price vs. $83 offer and $97.17 Day-1 close weekly; mark the lockup-expiry date on your calendar.
- 🆕 **GPT-6.2 Astra "High" self-improvement claim:** new thread. Single-source today. Watch for Anthropic / Google responses; this is the first time a Preparedness threshold has been declared crossed.
- 🆕 **Gemini 4 Neon Vending-Bench + SEC-bench lead:** new thread. Watch which vertical-AI startups adopt Neon as their default backend for finance/regulated-ops workflows.
- 🆕 **Sierra ~$30B revaluation (talks):** new thread. If it closes, enterprise-agents category comp resets; watch Decagon/Harvey/Rox next-round marks.
- 🆕 **Ramp token-share regime change:** new thread. +10.5% MoM is the first break from flat; watch Dec/Jan prints for continuation.
- 🆕 **Terminal-Bench 2.1 audit:** new thread. Watch which benchmarks get the same treatment (SWE-Bench, LiveCodeBench) — the "audit the eval" lane is emerging as a research niche.
- ➡️ **Anthropic IPO window (from 2026-11-14):** closed as a question — ANT is public. Advanced to **lockup watch**.
- ➡️ **FDE lane (from 2026-11-14):** comp bands now include Anthropic $300K–$1.2M. Apply this week.
- ➡️ **MSFT 60K buyout (from 2026-11-14):** Dec 1 deadline in 8 days; Jan 1 is the applicant-flood date.
- ⬇️ **"Latest model" fluency:** further deprecated. Three #1-class models at ~same price = **routing**, not fluency, is the FDE skill.
- ⬇️ **Benchmark number-dropping on résumés:** down. Post-Terminal-Bench 2.1 audit, you need **your harness**, not just numbers.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-ant-ipo) (the ANT IPO day) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–3](./05-career-and-startup.md) — IPO + three models + comp aftermath |
| Tonight | [`03` §2](./03-practical-skills-and-tools.md#2-routing-policy) — publish a `router.md` |
| This weekend | [`03` §1](./03-practical-skills-and-tools.md#1-claude-code) — upgrade Code Mode + agent teams in your portfolio MCP |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
