# Practical Skills & Tools — 2026-09-12

Two of the three things below are 30–60 minutes tonight. The third is a Sunday rewrite. The framing: **the router artifact from Thursday needs a policy layer before Monday**, and **your MCP-token + `.git`-config hygiene is your Saturday chore because Accomplish's flaws are live right now on unpatched agents you're probably running.**

Tags: `#claude-code #routing #safety #evals #security #mcp #git`

---

## 1. Add a policy-layer route to your router — the "refuse-and-explain" case {#1-router-policy-layer}

**What happened:** The Thursday router artifact ([`03` §3 of 2026-09-10](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)) shipped as a 30-line shim with a 5-case eval suite. In the 48 hours since:

- Anthropic's threat report ([`01` §2](./01-big-lab-moves.md#2-threat-report)) says newer models are **no longer confidently below the bioweapons-assist threshold**.
- The PaperCut agent campaign ([`02` §1](./02-new-emerging.md#1-papercut-campaign)) shows the offensive analogue is *operational, not theoretical*.
- Sam Altman's Thursday town-hall ([`01` §1](./01-big-lab-moves.md#1-pacing-pivot)) makes **refusal-calibration** an executive-level topic.

**Upshot:** the v1 router evaluates on **cost × quality × latency**; the v2 needs a **safety** axis. Concretely, add:

### The 6th route: `refuse-and-explain`

Purpose: **detect prompts that should not be answered by any downstream model, and log the refusal instead of routing.**

- Trigger patterns (start with the seven Anthropic threat-report categories): **cyber-op-uplift, influence-op scripting, surveillance target-enumeration, scam-fraud pretexting, biological-uplift, conventional-weapons enablement, distillation-shape queries**.
- Log to the **same SQLite/CSV** as cost/latency, on a new `refused_reason` column. That way your leaderboard README already has the schema.
- **Do NOT** try to build a state-of-the-art safety classifier. Ship a **regex + keyword** first cut with a **known false-positive rate** documented in the README. The point of the artifact is that you *thought about the axis*, not that you solved it.
- Add a **7th eval case** to the 5-case suite: a genuinely-ambiguous CBRN-adjacent prompt where the right answer is "clarify or refuse." Log which models refused cleanly vs which handed over unsafe content.

### 30-minute build order (tonight)

1. Add `refused_reason TEXT` column to your log DB. (2 min)
2. Write the 7-line classifier — a regex list keyed to the 7 categories. (10 min)
3. Add the 7th eval case + wire it into your CI. (10 min)
4. Update the README with a section: *"How the router handles unsafe prompts."* Link the Anthropic threat report. (5 min)
5. Push. Tweet the diff. (3 min)

### Why this is the artifact for Monday's applications

- **Answers the *new* H2 2026 interview question** — "how does your system handle a prompt it shouldn't answer at all?" — which nobody was asking in July.
- **Costs 30 minutes** to add a defensible answer.
- **Signals: you read threat reports**, not just release notes.

### Sources

- [Anthropic — Countering misuse of AI: September 2026](https://www.anthropic.com/threat-intelligence-report-september-2026) `[primary]`
- [Bloomberg — Sam Altman on slowing AI development](https://www.bloomberg.com/news/articles/2026-09-11/openai-is-open-to-slowing-cutting-edge-ai-ceo-sam-altman-tells-staff) `[secondary]`
- [Anthropic — Claude Fable 5.1 platform docs (dual-use-bio restriction language)](https://platform.claude.com/docs/en/models/mythos-5-1/overview) `[primary]`

→ Cross-link: [`01` §2 threat report](./01-big-lab-moves.md#2-threat-report) · [`05` §1 safety-role re-price](./05-career-and-startup.md#1-safety-lanes).

---

## 2. `.git`-config + MCP-token hygiene — 20 minutes, this Saturday {#2-hygiene}

**What happened:** Accomplish's disclosures ([`02` §2](./02-new-emerging.md#2-accomplish-sandbox)) reveal that **on Claude Code and Hermes Agent, malicious `.git/config` payloads execute before the workspace-trust prompt fires**, and that **a public Sentry MCP key is enough to hijack Claude Code / Cursor / Codex sessions.** **Four flaws remained unpatched at Sept 1 retest** across seven agents. You're likely running at least one of these tools on client repos.

### The hygiene checklist (~20 min)

1. **Fresh-clone rule.** Never open an unknown repo directly in Claude Code / Cursor / Codex from the OS shell. Instead:
   ```bash
   # Clone into a quarantine directory first
   git clone --no-hardlinks --no-local <url> ~/quarantine/repo-name
   cd ~/quarantine/repo-name
   # Inspect these BEFORE opening in any AI coding tool:
   cat .git/config
   find . -name '.envrc' -o -name '.sentryclirc' -o -name '.mcp*'
   ls -la .git/hooks/
   ```
   If anything looks unusual, don't proceed. If clean, `cd` in from your normal shell and open the agent.
2. **Workspace-trust prompt on.** In each tool's settings, verify workspace-trust is required, not "always trust." Cursor / Claude Code / Codex all have the setting; audit yours today.
3. **MCP token rotation.** Any MCP server you've configured — especially **Sentry** (the Accomplish-highlighted one), plus **GitHub, Linear, Notion, Slack** — should have its access token rotated **today**. 15 seconds per server through the respective apps; the token-list is 4–8 tokens for most people.
4. **Pin your agent versions.** Note the exact Claude Code / Codex / Cursor / Gemini CLI version you use in your `.tool-versions` or shell aliases. When Accomplish (or someone else) discloses the next batch of fixes, you'll know which of your machines is behind.

### Publish the hygiene checklist as a README addendum

Add a short **"Agent hygiene"** section to your router repo's README — cite Accomplish, link The Hacker News writeup, and add the checklist. This is a **50-line diff** that turns your router artifact into a *portfolio piece with a security posture*, not just a demo.

### Sources
- [The Hacker News — Malicious .git Configs Can Make Claude, Codex, Cursor, and Other AI Agents Run Attacker Code](https://thehackernews.com/2026/09/malicious-git-configs-can-make-claude.html) `[secondary]`
- [BleepingComputer — Cursor, Codex, Gemini CLI, Antigravity hit by sandbox escapes](https://www.bleepingcomputer.com/news/security/cursor-codex-gemini-cli-antigravity-hit-by-sandbox-escapes/amp/) `[secondary]`
- [The New Stack — A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex](https://thenewstack.io/agentjacking-sentry-mcp-attack/) `[secondary]`

→ Cross-link: [`02` §2 Accomplish](./02-new-emerging.md#2-accomplish-sandbox).

---

## 3. Two tactical shifts for how you *use* Claude Code this week {#3-tactical}

**What happened:** Two adjustments that fall out of this week's news, not next quarter's.

### 3.1 Read the threat report as a Skill

Concrete step: **save the Anthropic Sept-2026 threat report as a Skill file** under `.claude/skills/anthropic-threat-report-2026-09.md`, with a short header telling Claude Code to consult it when the user's prompt smells like the seven categories. Skills load *only when relevant* (per the decision tree in [2026-09-10 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree)), which means:

- Your day-to-day Claude Code sessions **stay context-clean**.
- When you're doing something that touches security/dual-use topics — say, writing a red-team eval — the skill triggers and Claude Code has the framing.
- Your Skill file becomes a **living index into your own knowledge of the threat landscape**; update it when the next threat report drops.

This is a five-line change to your `.claude/skills/` directory. Ship it tonight.

### 3.2 Pin your model version in the router — record fingerprints

The Accomplish "capability-jump-re-prices-old-CVEs" insight ([`02` §2](./02-new-emerging.md#2-accomplish-sandbox)) means **your eval suite's results are only valid against the exact model versions you tested.** Add a `model_versions.json` at the top of the router repo — a table of `{provider, model_id, version_hash, tested_on_date}` — and update on each CI run. Recruiters read this as *"this person understands that model behavior isn't a fixed number."* Interview loops read it as *"this person will avoid the class of bug where our production system silently changes behavior when Anthropic pushes a point release."*

### Sources
- [SmartScope — Claude Code Advanced Best Practices (2026)](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [Anthropic — Countering misuse of AI: September 2026](https://www.anthropic.com/threat-intelligence-report-september-2026) `[primary]`
- [Anthropic — Claude Fable 5 announcement](https://www.anthropic.com/news/claude-fable-5-mythos-5) `[primary]`

---

## 4. One-line habits worth keeping this week {#4-habits}

Carrying most of Thursday's list forward, plus one addition:

- **Prompt caching on** for every long system prompt (Fable 5.1 discount still in effect — [`03` §1 of 2026-09-10](../2026-09-10/03-practical-skills-and-tools.md#1-fable-51-economics)).
- **"Address all notes, don't implement yet"** — plan → annotate → implement.
- **Public repo weekly cadence** — one artifact/week. This week's is the router v2 with the policy layer.
- **Two-gate quality control** — check runs + evidence.
- 🆕 **Weekly threat-report reading slot** — 30 minutes Sunday, log one takeaway you can defend in an interview. This is the H2 2026 differentiator; a portfolio can be faked, "I read the Sept threat report the day it dropped and here's what I did about it" cannot.

### Sources
- [Anthropic — Countering misuse of AI: September 2026](https://www.anthropic.com/threat-intelligence-report-september-2026) `[primary]`
- [The AI Corner — Claude best practices 2026: the complete power user guide](https://www.the-ai-corner.com/p/claude-best-practices-power-user-guide-2026) `[analysis]`
