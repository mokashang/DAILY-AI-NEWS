# LATEST — pointer to the most recent edition

> **2026-07-04** — see [`2026-07-04/00-tldr.md`](./2026-07-04/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Saturday (Independence Day) — the state, the protocol, and the escape valve all move inside 24 hours ahead of the UN Geneva Dialogue.** **[Anthropic closes the China transfer-station loopholes](./2026-07-04/01-big-lab-moves.md#1-china-loopholes)** (Ant Group Singapore-shell, ByteDance VPN reimbursements, Azure-hosted foreign shells — detected via time-zone + proxy + network-name signatures; steganography check in Claude Code removed July 2). **[Pentagon–Anthropic emails released July 2](./2026-07-04/01-big-lab-moves.md#2-pentagon-emails)** — Emil Michael to Amodei: **"just not workable"** on Anthropic's ban on autonomous weapons + domestic surveillance; the AUP-vs-procurement precedent. **[OpenAI floats a 5% US-government stake ("Public Wealth Fund")](./2026-07-04/01-big-lab-moves.md#3-openai-govt-stake)** — ~$42.6B at $852B pre-IPO, asks Anthropic / Google / xAI to cede the same, IPO timing may slip to 2027. **[MCP 2026-07-28 stateless RC is out — T-24 days to breaking changes](./2026-07-04/02-new-emerging.md#1-mcp-stateless)**: sessions removed, required routing headers, `ttlMs`/`cacheScope`, Tasks + Apps extensions, six OAuth 2.1 SEPs. **[Meituan open-sources LongCat-2.0](./2026-07-04/02-new-emerging.md#2-longcat)** — 1.6T MoE, MIT license, trained entirely on Chinese chips, leading OpenRouter usage. **[UN Global Dialogue on AI Governance — Geneva, July 6–7 (T-2 days)](./2026-07-04/01-big-lab-moves.md#4-geneva)** — first UN convening under Global Digital Compact.

**For you:** today is the July AI-spend audit (`ME.md` 4th-of-month rule), the MCP migration is Saturday's high-leverage build, and Geneva is the governance-lane inflection window.

Full edition → [`2026-07-04/`](./2026-07-04/)

---

## One-thing-to-do (Saturday July 4 → Sunday July 5)

→ **Migrate one MCP server to the 2026-07-28 stateless RC.** [`2026-07-04/03 §1`](./2026-07-04/03-practical-skills-and-tools.md#1-mcp-migration). 2–3 hours. Sessions removed, `Mcp-Method`/`Mcp-Name` headers, `ttlMs`/`cacheScope`, one long-running tool moved to the Tasks extension. Publish before/after wire trace + 3-min outage-drill Loom. **This is the FDE / integration-engineer artifact of Q3** — every production MCP server needs it before July 28.

→ **Run the July AI-spend audit** (`ME.md` 4th-of-month personal rule). [`2026-07-04/03 §3`](./2026-07-04/03-practical-skills-and-tools.md#3-spend-audit). 30 min. Pull Anthropic Console + OpenAI Usage + Cursor + cloud tokens; write `SPEND-2026-07.md`; identify the 20% of usage = 80% of cost.

→ **Add LongCat-2.0 as a 5th routing slot.** [`2026-07-04/03 §2`](./2026-07-04/03-practical-skills-and-tools.md#2-longcat-routing). 20 min via Together AI or Baseten. Route bulk-refactor + test-generation workloads there; compare against Opus 4.7 on cost / time / pass-rate.

→ **Read the Anthropic constitution + one TechPolicy piece before Monday.** [`2026-07-04/03 §4`](./2026-07-04/03-practical-skills-and-tools.md#4-constitution-read). 20 min. Sets up your Geneva Dialogue coverage Mon–Tue and gives you a 1-page LinkedIn note for Tuesday.

→ **Also live from 2026-07-03**: draft the Claude Science credit-grant proposal by Thu **July 9** (deadline Wed **July 15**, $30K × up to 50 projects). Carried from [`2026-07-03/05 §3`](./2026-07-03/05-career-and-startup.md#3-grant-deadline). Frame around a stepwise-verifiable science-agent workflow; cite [Self-Evolving Agents w/ Anytime-Valid Certificates](./2026-07-04/04-research-progress.md#2-long-horizon) + [AutoNumerics](./2026-07-04/04-research-progress.md#4-auto-research).

→ **Monday: apply to Anthropic FDE / Applied AI + 1 governance-adjacent role** with the migration repo attached + a 1-page cover-letter one-liner ("shipped MCP-stateless-RC migration this weekend, T-24 to July 28 spec lock").
