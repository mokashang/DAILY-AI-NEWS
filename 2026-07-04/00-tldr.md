# TL;DR — 2026-07-04 (Saturday · Independence Day)

Sixty-second skim. **Anthropic's China-loophole crackdown + the Pentagon email dump land two days before the UN Geneva AI Governance Dialogue (July 6–7); OpenAI dangles a 5% US-government stake ahead of its S-1; MCP goes stateless in 24 days; Meituan's LongCat-2.0 open-sources a 1.6T MoE trained entirely on Chinese chips.** Two separate storylines — **[Anthropic vs. transfer-station access from mainland China](./01-big-lab-moves.md#1-china-loopholes)** (Ant, ByteDance, Azure-hosted foreign shells) and the **[Pentagon email release](./01-big-lab-moves.md#2-pentagon-emails)** ("just not workable" vs. autonomous-weapons/domestic-surveillance carve-outs) — collide with **T-2 to Geneva**, where governance rules for exactly these frictions get debated. Meanwhile **[OpenAI is talking about a 5% Public Wealth Fund stake](./01-big-lab-moves.md#3-openai-govt-stake)** (~$42.6B at $852B pre-IPO), **[MCP 2026-07-28 RC is out](./02-new-emerging.md#1-mcp-stateless)** — stateless core, six SEPs, Tasks + Apps extensions, breaking changes for every production MCP server — and **[Meituan open-sourced LongCat-2.0](./02-new-emerging.md#2-longcat)**: 1.6T MoE, MIT license, near-frontier agentic coding, trained on domestic Chinese silicon. **For you: today is the monthly AI-spend audit (July 4), the MCP-stateless migration is a Saturday build with a real deliverable, and the Geneva Dialogue is your governance-lane inflection window.**

---

1. **Anthropic closes the China transfer-station loopholes.** Ant Group ran Claude accounts through a Singapore entity; ByteDance reimbursed personal Claude subs via VPN; other firms proxied via foreign-incorporated shells on Azure. Anthropic is now signature-matching on time-zones, proxy configs, and network names to detect them (and pulled the [controversial steganography check out of Claude Code on July 2](./01-big-lab-moves.md#1-china-loopholes)). The compliance-eval / export-control lane just got a fresh case study. → [`01` §1](./01-big-lab-moves.md#1-china-loopholes) `#anthropic #china #export-controls #compliance`

2. **Pentagon–Anthropic emails released July 2.** Emil Michael to Amodei: "just not workable" (on Anthropic's ban on fully-autonomous weapons + domestic surveillance) → Anthropic dropped from the Pentagon's 8-vendor list ([2026-05-09](../2026-05-09/)). The real fight is **whether a lab can bar its buyer from a use-case** — precedent for every AI acceptable-use-policy at every buyer. → [`01` §2](./01-big-lab-moves.md#2-pentagon-emails) `#anthropic #dod #policy #aup`

3. **OpenAI floats a 5% US-government stake ("Public Wealth Fund").** ~$42.6B at $852B; Altman frames it as "Americans share the AI gains"; would likely require Congressional approval; **proposal explicitly asks other frontier labs to cede the same** (Anthropic / Google / xAI). Precedent for **sovereign-AI equity as governance mechanism.** → [`01` §3](./01-big-lab-moves.md#3-openai-govt-stake) `#openai #ipo #policy #sovereign`

4. **MCP 2026-07-28 stateless RC is out — T-24 days to breaking changes.** Sessions removed (SEP-2567), Mcp-Method + Mcp-Name required headers, ttlMs + cacheScope on list/read results, **Tasks extension** (server returns handle, client polls), **Apps extension** (sandboxed HTML in tools), six OAuth 2.1 / OIDC hardening SEPs. **Every production MCP server needs a migration path.** → [`02` §1](./02-new-emerging.md#1-mcp-stateless) · [`03` §1 recipe](./03-practical-skills-and-tools.md#1-mcp-migration) `#mcp #protocol #agents`

5. **Meituan open-sources LongCat-2.0 — 1.6T MoE, MIT, Chinese chips.** Near-frontier agentic coding; **leading OpenRouter usage** among open models; trained on 30T+ tokens on domestic silicon (no Nvidia). Pairs with the Anthropic-China wall = **the open-source escape valve gets a legitimately good model.** → [`02` §2](./02-new-emerging.md#2-longcat) `#open-source #china #agents #coding`

6. **UN Global Dialogue on AI Governance — Geneva, July 6–7 (T-2 days).** First formal UN convening under the Global Digital Compact; all governments + private sector + academia + civil society; **Anthropic's new constitution** ([2026-07-03/01 §4](../2026-07-03/01-big-lab-moves.md#4-constitution)) was published 3 days ahead of it intentionally. Governance-lane roles get their inflection window. → [`01` §4](./01-big-lab-moves.md#4-geneva) · [`05` §2 governance lane](./05-career-and-startup.md#2-governance-lane) `#un #geneva #governance`

7. **Practical: Saturday's build is the MCP-stateless migration + your July AI-spend audit.** Migrate one production-shape MCP server to the 2026-07-28 RC (drop session store, add `Mcp-Method`, wire `Tasks`), publish a "before/after" writeup — **the FDE / integration-engineer artifact that answers "did you keep up when MCP broke."** Then run the [4th-of-month spend audit](./03-practical-skills-and-tools.md#3-spend-audit) — a personal-rule from [`ME.md`](../ME.md). → [`03` §1](./03-practical-skills-and-tools.md#1-mcp-migration) · [`03` §3](./03-practical-skills-and-tools.md#3-spend-audit) `#mcp #portfolio #spend`

8. **Skill re-price:** the value isn't "I use MCP" — it's **"I ship the migration when the protocol breaks."** Protocol churn = *stack-relevance signal* for FDE hiring. LongCat's arrival + Cloudflare's Sept 15 defaults + MCP's stateless flip = three simultaneous repricing events. Whoever ships the migrations gets the Q3 offer. → [`05` §1](./05-career-and-startup.md#1-migration-skill) `#skills #careers`

---

## One thing to DO this Saturday (July 4)

→ **Two-artifact Saturday: (a) run the July AI-spend audit** ([personal rule](../ME.md), 4th-of-month) — pull Anthropic Console + OpenAI Usage + Cursor + any Bedrock/Vertex + cloud tokens; write to `SPEND-2026-07.md`; identify the 20% of usage = 80% of cost. **(b) Migrate one MCP server to the 2026-07-28 RC** ([`03` §1](./03-practical-skills-and-tools.md#1-mcp-migration)) — remove the session store, add `Mcp-Method` + `Mcp-Name` headers, wire the `Tasks` extension for one long-running tool, publish before/after in a public repo. **One weekend = the "protocol-migration engineer" artifact you attach to Monday's FDE apps.**

## Watchlist deltas

- 🆕 **Anthropic China-loophole crackdown (Ant / ByteDance / Azure-shell)** — carried thread; watch (a) whether OpenAI/Google follow with equivalent transfer-station detection, (b) impact on the CN-open-source-model demand curve (LongCat / DeepSeek V4).
- 🆕 **Pentagon–Anthropic email release** — read alongside [2026-05-09/01](../2026-05-09/01-big-lab-moves.md) 8-vendor decision. Watch for a DoD RFP that explicitly *requires* autonomous-weapons authorization.
- 🆕 **OpenAI 5% Public Wealth Fund proposal** — track whether Anthropic / Google / xAI respond; Congressional-approval path is the pacing item; would reprice the whole IPO wave ([2026-05-22/02 §1](../2026-05-22/02-new-emerging.md#1-ipo-wave)).
- 🆕 **MCP 2026-07-28 stateless RC** — **T-24 days**. Migration deadline for every production MCP server. Weekend action item.
- 🆕 **Meituan LongCat-2.0 (1.6T, MIT, domestic chips)** — watch (a) enterprise-eval scoreboard vs. Sonnet 5 / GPT-5.5-Mini, (b) DeepSeek's response, (c) US-export-control reaction.
- 🆕 **UN Geneva AI Governance Dialogue July 6–7** — **T-2 days**. Watch for a formal "voluntary reporting" framework; carries the governance-lane hire signal.
- ➡️ **Claude apps gateway** — Day 2. Carried from [2026-07-03/01 §1](../2026-07-03/01-big-lab-moves.md#1-gateway). Deploy-this-weekend action still live.
- ➡️ **Claude Science $30K credit grant** — **T-11 days to July 15**. Draft-by-Thursday still on the calendar.
- ➡️ **Cloudflare Search/Agent/Training defaults** — Day 4. T-73 days to Sept 15 flip.
- ➡️ **SB Neo (SoftBank US neocloud)** — Day 2. FY27 first-customer.
- ➡️ **Grok 4.5 private beta (SpaceX/Tesla)** — no independent benchmark yet. Watch for a system card.
- ➡️ **Anthropic new constitution** — one story ahead of Geneva.
- ➡️ **Sonnet 5 promo pricing $2/$10** — T-58 days to standard.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + [`01` §1 China loopholes](./01-big-lab-moves.md#1-china-loopholes) + [`02` §1 MCP stateless](./02-new-emerging.md#1-mcp-stateless) |
| 20 min | [`03` §1 MCP migration recipe](./03-practical-skills-and-tools.md#1-mcp-migration) + [`04` §1 MCP-Atlas/Toolathlon](./04-research-progress.md#1-mcp-atlas) — read together, migrate today |
| Today | [`03` §3 monthly spend audit](./03-practical-skills-and-tools.md#3-spend-audit) — 4th-of-month personal rule |
| Weekend | [`03` §1 MCP migration](./03-practical-skills-and-tools.md#1-mcp-migration) + [`03` §2 LongCat routing slot](./03-practical-skills-and-tools.md#2-longcat-routing) + [carried gateway deploy](../2026-07-03/03-practical-skills-and-tools.md#1-gateway-deploy) |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.

*Gap note: the last edition was 2026-07-03. No gap; daily cadence maintained.*
