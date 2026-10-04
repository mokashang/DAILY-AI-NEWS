# TL;DR — 2026-09-01 (Tuesday)

Sixty-second skim. **A pricing cliff hits your bill today, the top of Google DeepMind changes hands, and Anthropic quietly ships the browser-agent primitive.** **Sonnet 5's introductory API pricing ended Aug 31; $2/$10 → $3/$15 per MTok takes effect this morning** — every Claude Code / Agent-SDK run you leave on autopilot is now +50% more expensive. **Koray Kavukcuoglu is the new SVP of Google DeepMind; Hassabis moves to chair; Jeff Dean + Sanjay Ghemawat + Oriol Vinyals + Quoc Le all left to co-found Discovery Loop** — the most credentialed AI-founding team of 2026, and the loudest talent signal since Karpathy → Anthropic in May. **Claudeforce launched yesterday (Salesforce in Claude, 37 prebuilt sales skills, open beta this month)** and **Claude in Chrome is GA** — Anthropic's browser-agent surface is now callable from Salesforce and from every tab. **Pentagon opened GenAI.mil to ChatGPT Mil + Grok for Government (3M personnel); Claude remains excluded on supply-chain risk** — the SLED/DoD lane is a Gemini/OpenAI/xAI carve-up for now. **OpenAI paused Astra over cyber risk and retired o3 on Aug 26.** **Fable 5's biology safeguards were retuned: ~85% fewer blocked queries** — a real signal that Anthropic can iterate a classifier's "constitution" fast, and a hint about the "evaluation engineer" lane.

---

1. **Sonnet 5 pricing cliff hits at 00:00 today: $2/$10 → $3/$15 per MTok.** Introductory pricing ended Aug 31. Anthropic's own numbers: **Sonnet 5 = 63.2% SWE-bench Pro** vs. Opus 4.8's 69.2% and Sonnet 4.6's 58.1%; **81.2% OSWorld-Verified, 57.4% HLE.** After today's bump, Sonnet 5 is **60% of Opus 5's per-token cost** ($3/$15 vs. $5/$25) — the "cheap-workhorse" gap narrowed. Audit your default model in Claude Code, Agent SDK, and any MCP-connected agents **today**. → [`01` §1](./01-big-lab-moves.md#1-sonnet-5-price-hike) · [`03` §1](./03-practical-skills-and-tools.md#1-sonnet-5-price-audit) `#anthropic #pricing #sonnet-5 #cost`

2. **Google DeepMind leadership: Hassabis → chair, Kavukcuoglu → SVP, Jeff Dean out.** Announced Aug 5–12. Kavukcuoglu (formerly DeepMind CTO / Google chief AI architect) now owns Gemini, frontier research, and the Gemini app + developer teams; reports directly to Sundar Pichai. Hassabis becomes DeepMind chair + Alphabet chief scientist, keeps Isomorphic Labs. **Alphabet dipped ~5% on the news.** The four-founder exit to Discovery Loop is separate but concurrent — see below. → [`01` §2](./01-big-lab-moves.md#2-deepmind-reshuffle) · [`05` §3](./05-career-and-startup.md#3-founding-team-signal) `#google #deepmind #leadership #kavukcuoglu`

3. **Jeff Dean + Ghemawat + Vinyals + Quoc Le co-found Discovery Loop (Delaware PBC).** Automating the experimental loop of scientific research itself — ML research first, then hardware design, drug discovery, clean energy. **Google is a founding investor + Cloud partner.** This is the highest-density founding team of 2026 — four Google Senior Fellow / VP-tier researchers exiting together, with Google's blessing. Read as: (a) the "AI-for-science" wedge is the most credentialed thesis in the market, (b) Google is willing to spin-out capital rather than lose the talent, (c) the AGI-lab consolidation ([2026-07-25](../2026-07-25/01-big-lab-moves.md#3-amazon-agi-lab)) now has a **spin-out valve**. → [`02` §1](./02-new-emerging.md#1-discovery-loop) · [`05` §3](./05-career-and-startup.md#3-founding-team-signal) `#startup #discovery-loop #ai4science #google-alumni`

4. **Claudeforce launched Aug 31: Salesforce in Claude (37 prebuilt sales skills), open beta this month.** Pilot customers now, open beta Sept 2026. This puts **Claude as the reasoning surface inside the world's largest sales-workflow install base**. Read against Anthropic × Deloitte / PwC / Ramp adoption lead: the "AI Integration Engineer at Salesforce partners" lane just materially expanded. → [`01` §3](./01-big-lab-moves.md#3-claudeforce) · [`05` §2](./05-career-and-startup.md#2-fde-and-integration-lane) `#anthropic #salesforce #claudeforce #integration`

5. **Claude in Chrome is generally available.** Anthropic's browser-operating AI (in beta since spring) is now GA — every tab is a callable surface. Practical shift: agent workflows that used to require a headless browser + a Playwright MCP now compose with the user's *actual* browser session (auth cookies, extensions, tabs). → [`01` §4](./01-big-lab-moves.md#4-claude-in-chrome-ga) · [`03` §2](./03-practical-skills-and-tools.md#2-claude-in-chrome-workflows) `#anthropic #claude-chrome #browser-agents`

6. **Pentagon GenAI.mil expansion Aug 31 — ChatGPT Mil + Grok for Government added, 3M personnel.** Both accredited at DoD Impact Level 5 (CUI). Gemini for Government has been on the platform since Dec 2025. **Claude is not on the platform** — the Trump administration flagged it as a supply-chain risk earlier this year. The federal-AI lane is now a **Gemini + OpenAI + xAI carve-up**; the assurance/eval jobs are non-Anthropic here. → [`01` §5](./01-big-lab-moves.md#5-pentagon-genai) · [`05` §4](./05-career-and-startup.md#4-federal-ai-lane) `#pentagon #openai #xai #google #federal`

7. **OpenAI paused Astra over cyber risk; o3 retired Aug 26; GPT-Live voice launched.** Astra was to be the successor model to GPT-5; paused after a critical cyber-risk finding (echo of the CAISI 90-day pre-release review thread from May). GPT-Live ships as a native voice model — sub-300ms latency, no text pipeline. Wispr-flow / voice-OS thread ([2026-05-13](../2026-05-13/)) just got a frontier-lab bake-off partner. → [`01` §6](./01-big-lab-moves.md#6-openai-astra-live) · [`03` §3](./03-practical-skills-and-tools.md#3-voice-workflows) `#openai #astra #gpt-live #voice`

8. **Fable 5 biology safeguards retuned: ~85% fewer blocked queries, ~67% fewer total Claude.ai fallbacks.** Anthropic rewrote the classifier's "constitution" with expert feedback, then retrained. Dual-use work (virology, toxicology, molecular design) still routes to Opus 5. **The "classifier constitution" itself is the newsworthy artifact** — the eval-engineering job description is starting to look like "write and iterate on classifier constitutions." → [`01` §7](./01-big-lab-moves.md#7-fable-5-safeguards) · [`04` §4](./04-research-progress.md#4-classifier-constitution) · [`05` §5](./05-career-and-startup.md#5-eval-engineer-lane) `#anthropic #fable-5 #safety #eval-engineering`

9. **Research (arXiv 2026, curated): AgentAtlas (21,730 rollouts, 9 systems × 9 benchmarks); AgentSearchBench (agent search as retrieval + reranking); "Reasoning Trap" (better reasoning ↑ tool-hallucination); "Tools Only When Epistemically Necessary."** The tool-use / benchmarking literature is converging on a single lesson: **outcome leaderboards are already gamed; audit the process.** → [`04` §1–3](./04-research-progress.md) `#arxiv #benchmarks #tool-use #agents`

10. **Emerging: Clay at $7B pre-money (up from $5B Jan 2026); Keenable $26M seed (Accel) for AI-agent web search; Aziron / Aziro enterprise agent-execution platform; Optimizely Virtual Teammates; Cashfree Relay GA.** The "agent runtime for X vertical" thesis is still funding at a premium; **agent-native web search** is the newest wedge with a real check behind it. → [`02` §2–5](./02-new-emerging.md) `#funding #clay #keenable #aziro #agents`

---

## One thing to DO today (Tuesday)

→ **Audit the Sonnet 5 price cliff before you write a single new prompt.**
1. **08:00** — Open your Anthropic Console usage dashboard. Sort last 7 days by model. If Sonnet 5 is >30% of your token spend, **decide by default**: (a) drop non-critical Sonnet 5 calls to Haiku 4.5 or (b) promote critical Sonnet 5 calls to Opus 5 with `effort=medium` — the $/quality on Opus 5 is now better than it looks. → [`03` §1](./03-practical-skills-and-tools.md#1-sonnet-5-price-audit).
2. **Lunch** — Ship a 60-line "cost-router" script that reads a per-call `budget` and picks Haiku / Sonnet / Opus (effort=low|med|high). Push to your portfolio repo. Interviewers love this exact artifact right now.
3. **This evening** — Draft one paragraph on **Discovery Loop as founding-team signal** for your public writing rotation. The four-Google-fellow exit is a top-10 startup event of the year; the *analysis* is scarce and the timing is right for a "what this means for CS grads" take.

## Watchlist deltas since the 2026-07-25 edition

*Five weeks have passed. Threads that survived:*

- 🆕 **Sonnet 5 pricing cliff (2026-09-01)** — new thread. Pricing is now the model-lifecycle event to track; expect one every quarter.
- 🆕 **Google DeepMind reshuffle + Discovery Loop spin-out (2026-08-05→12)** — new thread. The AGI-lab consolidation from [2026-07-25](../2026-07-25/01-big-lab-moves.md#3-amazon-agi-lab) grew a *spin-out valve*.
- 🆕 **Claudeforce (2026-08-31)** — new thread. Anthropic now inside Salesforce as a reasoning surface; watch attach rate and skill count.
- 🆕 **Claude in Chrome GA** — extends the "browser as agent surface" thread ([WebMCP, 2026-05-20](../2026-05-20/)); moves from origin-trial protocol to a live product surface.
- 🆕 **Pentagon GenAI.mil expansion (2026-08-31)** — new thread. Federal-AI lane = OpenAI + Google + xAI; Anthropic excluded.
- 🆕 **OpenAI Astra paused; o3 retired 08-26; GPT-Live launched** — extends the CAISI pre-release-review thread from [2026-05-21](../2026-05-21/); this is what a *staffed* pre-release eval finding looks like.
- ➡️ **FDE / Applied AI Engineer market:** still growing; the +1,165% YoY figure from [2026-07-25](../2026-07-25/) has held through Q3; **Anthropic Bengaluru** opens Applied AI Architect / Applied AI Engineer roles under Irina Ghose.
- ➡️ **MCP protocol maturity:** the 07-28 stateless migration ([2026-07-25](../2026-07-25/)) landed; the industry is now writing the *style guides* on top (AGENTS.md, subagent teams, hook enforcement).
- ⬇️ **Anthropic Fellows Nov 2026 cohort** — should be past selection notifications by now; retrospective worth doing if you applied.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + Sonnet 5 pricing in [`01` §1](./01-big-lab-moves.md#1-sonnet-5-price-hike) + Discovery Loop in [`02` §1](./02-new-emerging.md#1-discovery-loop) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) (pricing + DeepMind + Claudeforce) + [`03` §1–2](./03-practical-skills-and-tools.md) (cost-router + Claude in Chrome) — the four signals that changed your near-term plan |
| Tonight | [`03` §1](./03-practical-skills-and-tools.md#1-sonnet-5-price-audit) — audit + build the cost-router artifact |
| This week | [`05` §2–3](./05-career-and-startup.md) — send 2 FDE apps + 2 AI-for-Science / Discovery-Loop-thesis DMs |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
