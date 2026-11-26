# TL;DR — 2026-11-26 (Thanksgiving Day)

Sixty-second skim. **US markets are closed today (Thanksgiving); half-day Friday.** Yesterday (Nov 25) was the deepest AI selloff since September — **Nasdaq −3.98%, NVIDIA −8.69%, AMD −9.56%, ANT a small bounce to ~$82.79 close (session range $73.85–$85.92) but still below its $83 offer**, 7 trading days after the biggest IPO in history. The pattern from [2026-11-25](../2026-11-25/00-tldr.md) holds — **fundamentals strong, multiples contracting** — and today's holiday pause is a gift: use it to prep for the **Dec 1 reopen**, when (a) Microsoft's 60K buyout acceptance deadline hits, (b) the Monday pipeline queues flush, and (c) Dec 2 YC F26 Demo Day lands (71% AI-tagged per Nov 24 edition). **Three things are genuinely new since yesterday's edition**: (1) **Anthropic launched Claude Ship on Nov 23** — agents that **review, fix, AND approve** PRs on GitHub (TechCrunch broke it; builds on March's Code Review product); (2) **Walmart opened Black Friday to Meta's Muse AI agent with per-agent spending caps and human-approval gates** — the first large-retail commerce surface wired for autonomous agent buying; (3) **ElevenLabs is in early talks for a 2027 round at $33B** (up from $22B) — voice-agent infra re-rated as a top-5 AI category. Research pick of the fortnight: **DiscoveryAgent (arXiv 2611.21950)** showed audit sub-agents help scientists catch **14× more valid errors**, and **a16z launched a Forward-Deployed Engineer Fellowship 2027 with a Dec 31 deadline** — the first VC-run FDE track. **Your action this week**: fire 5–10 FDE applications by Dec 15 (before the MSFT wave swamps Jan 2 pipelines), and ship one Claude Ship-eligible eval gate on a public repo over the long weekend.

---

1. **ANT week-one tape:** Nov 24 close **$81.91** (−6.54% day, −26.5% from debut), Nov 25 session range **$73.85–$85.92** closing near **$82.79 (-1.7%)** with after-hours ticking up to ~$83.3 — **still below the $83 IPO offer 7 trading days in.** Nasdaq broadly **−3.98% on Nov 25** with NVDA **−8.69%** and AMD **−9.56%**. Staggered lockup from the S-1 stands; the first ~May 2027 tranche is the single most-watchable date in AI venture. → [`01` §1](./01-big-lab-moves.md#1-ant-week-one) `#anthropic #ipo #ant`

2. **Anthropic launches Claude Ship (Nov 23) — agents review, fix, AND approve PRs.** Beta for Team + Enterprise plans; GitHub-only. **First mainstream agent surface where the agent is the approver**, not just a commenter. Builds on March's Code Review product and the July `@claude review` behavior update. Expected cost $15–25 per PR. → [`01` §2](./01-big-lab-moves.md#2-claude-ship) `#anthropic #claude-code #agents`

3. **Walmart × Meta Muse: first large-retail Black Friday wired for an autonomous agent (Nov 25).** Walmart opened its Black Friday catalogue to **Meta's Muse AI agent** with per-agent spending caps and human-approval gates. **The first production "AI agent buys from you" surface at retail scale** — Amazon and Meta are separately in talks to end Amazon's Muse-on-Instagram blockade. This is the commerce-side companion to Claude Ship's approve-on-GitHub surface. → [`01` §3](./01-big-lab-moves.md#3-walmart-muse) `#meta #commerce #agents`

4. **ElevenLabs in early talks at $33B for a 2027 round (Nov 25 reporting).** Up from $22B. Voice-agent infra now priced as a top-5 AI category. Context: Claude Meetings had an outage-and-restore cycle through mid-November; Sierra at ~$30B; Mercor at $20B. Voice + customer-service + data-labor rounds are the triangle. → [`02` §1](./02-new-emerging.md#1-elevenlabs) `#funding #voice #agents`

5. **Australia Digital Duty of Care Act — fines up to 5% of global revenue.** Passed through parliament this week. Puts Australia alongside the EU AI Act for scope. For US startups: **if your AI product has Australian users, you need an impact-assessment artifact by the effective-date trigger**. Watch for the UK's equivalent in Q1 2027. → [`02` §2](./02-new-emerging.md#2-australia-ddc) `#policy #regulation`

6. **Tidal to delete ~29M fully AI-generated tracks starting Dec 9.** First major streaming platform to do explicit AI-slop removal. Signal: **platform-level content gating is now a real surface area for AI policy**, and provenance-tagging (C2PA, model-watermarks) starts to matter commercially. → [`02` §3](./02-new-emerging.md#3-tidal-ai-removal) `#policy #content #provenance`

7. **a16z Forward-Deployed Engineer Fellowship 2027 — Dec 31, 2026 deadline.** **Eight-week fellowship** for FDEs and applied-AI leaders. First VC-run FDE track — a16z institutionalizing the lane. Stacks with MSFT Frontier Company (6K FDEs) + Anthropic Frontier Academy ($100M / 10K FDEs by 2027) + EY $1B Assurance FDE practice. → [`05` §2](./05-career-and-startup.md#2-a16z-fde) `#fde #careers #fellowship`

8. **Microsoft 60K voluntary-buyout: Dec 1 deadline, 5 days away.** Industry-baseline 3–5% uptake → **1,800–3,000 engineers hit the market Jan 1**. Nadella (Nov 19 analyst Q&A): *"I wish I could just sit here and say it'll all be the same. I cannot."* Combined with Dec 2 YC F26 Demo Day (71% AI-tagged per the Nov 24 edition), **Jan 2 is the most saturated AI job market of the cycle. Fire your apps by Dec 15.** → [`05` §1](./05-career-and-startup.md#1-microsoft-buyout) `#msft #layoffs #timing`

9. **Research pick: DiscoveryAgent (arXiv 2611.21950, Nov 16).** Audit sub-agents help scientists catch **14× more valid errors** vs. manual review alone. First published concrete human-in-the-loop multiplier. Pairs directly with Claude Ship's auto-approve surface: *the agent proposes; the audit sub-agent verifies; humans sign off on only the exceptions*. → [`04` §1](./04-research-progress.md#1-discoveryagent) `#arxiv #agents #audit`

10. **Secondary research this fortnight:** **"Agents, Think Only When It Helps" (arXiv 2611.05709, Nov 3)** — altering/discarding reasoning traces barely hurts distilled agents; implication: much CoT spend is wasted recipe-replay; **"Rethinking Access Control for AI Agents" (arXiv 2611.06764, Nov 4)** — first systematic survey of agent permissions, catalogues confused-deputy and delegation-chain failure modes; **DiscoveryAgent + Access Control = the compliance stack for agent-approved merges.** → [`04` §2–3](./04-research-progress.md#2-think-only-when-it-helps) `#arxiv #audit #access-control`

11. **Chinese open-weight frontier compresses: Kimi K3.1 Pro / GLM-5.3 / Qwen 3.8.** Five Chinese labs on two licensing models in a 30-day window (modified-MIT and revenue-gated custom). AA Index v5 (Nov 5) rankings now include K3.1 Pro at 46 + GLM-5.3 at 32. **The US open-weight frontier is still not obviously best.** → [`02` §4](./02-new-emerging.md#4-china-open-weight) `#open-source #china`

12. **Three-labs-at-$8/$40 holds — the frontier is a commodity.** Claude Fable 5.2, GPT-6.2 Astra, and Gemini 4 Carbon (post-Nov 30 promo) all land at the identical frontier price point. **Model-name résumé bullets are now zero-signal; routing + eval + MCP surface + Claude Ship compliance are the hireable skills.** See the Nov 25 edition's FDE Tier 1 vs Tier 2 split — **Tier 2 ($120–200K) is the new-grad slot**. → [`05` §3](./05-career-and-startup.md#3-commodity-price) `#reprice #careers`

13. **Practical weekend plan:** **(a) set up Claude Ship on a public repo — one merged agent-approved PR as a screenshot artifact;** **(b)** ship a 5-tool MCP server with a 10-case eval; **(c)** draft the a16z FDE Fellowship application. The MCP recipe from [2026-11-25 §3](../2026-11-25/03-practical-skills-and-tools.md#3-mcp-weekend-artifact) still stands; add Claude Ship as the new fortnight artifact. → [`03`](./03-practical-skills-and-tools.md) `#weekend #portfolio #fde`

14. **Timing playbook for the 25-day sprint (Dec 1 – Dec 31):** This is a **sprint window**. Dec 1 reopen → Dec 15 last high-signal application date → Dec 22 last low-volume day → Dec 31 a16z deadline. Fire 5 apps Dec 1–8, 5 more Dec 8–15, Claude Ship + MCP + router artifacts Dec 1–20, a16z draft Dec 15–30. **Then rest until March 1** — the MSFT wave + Google / Amazon / Meta likely follow-on programs will swamp Jan 2–Mar 1 pipelines. → [`05`](./05-career-and-startup.md) `#timing #applications`

---

## One thing to DO this Thanksgiving

→ **Spend 60 minutes today reading the [2026-11-25 edition](../2026-11-25/00-tldr.md) + this one, then open the a16z FDE Fellowship application tab and jot down three paragraph seeds** (one customer story, one artifact link, one "why I'd ship X at an a16z portfolio company"). Do nothing else today. **Markets are closed; recruiters are off; your competitors are eating turkey. You read, then rest.** The Friday half-day → Monday Dec 1 window is where you file applications. Detailed playbook in [`05` §2](./05-career-and-startup.md#2-a16z-fde).

## Watchlist deltas (new since Nov 25)

- 🆕 **Nov 25 Nasdaq −3.98% AI selloff:** new thread. Track whether Friday's half-day stabilizes or deepens the move; watch NVDA / AMD / Broadcom; ANT finding a floor at/below $80 is the key price level to watch Mon Dec 1.
- 🆕 **Walmart × Meta Muse first retail agent-buying surface:** new thread. Watch Amazon's response (Muse-on-Instagram unblock, own agent integration, or counter-launch) and Target / Best Buy follow-on.
- 🆕 **Australia Digital Duty of Care Act (5% global revenue fine):** new thread. Watch UK + Canada equivalents; US startups with Aus users need a compliance doc.
- 🆕 **Tidal AI-generated track deletion (Dec 9):** new thread. Spotify / Apple Music / YouTube Music follow-on will be the signal.
- 🆕 **ElevenLabs $33B talks:** new thread. Voice infra now a top-5 AI venture category; track whether the round closes above or below the markup.
- 🆕 **Claude Ship auto-approve surface:** new thread (also in `01`). First PR-merge-without-human-signoff product at scale; compliance surface is wide open.
- 🆕 **a16z FDE Fellowship 2027:** new thread. First VC-run FDE track; placement outcomes in June 2027 will tell the story.
- ➡️ **ANT lockup → ~May 2027:** staggered schedule per S-1; this is still the single most-watchable date in AI venture for the next 18 months.
- ➡️ **MSFT 60K buyout, Dec 1 deadline:** **5 days away**. Expect uptake disclosure in the Dec earnings commentary.
- ➡️ **YC F26 Demo Day, Dec 2** (per [2026-11-24 edition](../2026-11-24/00-tldr.md)): 71% of 231 companies AI-tagged. Track the top-5 funded pre-Demo-Day.
- ⬇️ **"Model-name fluency" résumé line:** still deprecated. Three labs at $8/$40.
- ⬇️ **Generic PR-review startups:** Claude Ship closed that category — pivot to vertical / compliance / audit.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1](./01-big-lab-moves.md#1-ant-week-one) (ANT week-one tape + Nov 25 selloff) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) + [`05` §1–2](./05-career-and-startup.md) — ANT + Claude Ship + Walmart/Muse + MSFT-buyout + a16z FDE playbook |
| Today (Thanksgiving) | Read 2026-11-25 + today's edition; three paragraph seeds for a16z. Nothing else. |
| Long weekend | [`03` §2](./03-practical-skills-and-tools.md#2-claude-ship-setup) — ship Claude Ship + one merged agent-approved PR as a portfolio artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
