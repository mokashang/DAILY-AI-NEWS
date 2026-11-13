# Practical Skills & Tools — 2026-10-17

Three actionable items this edition. **Claude Code v2.1.299 → 2.1.302 shipped in four days** — three of the four releases change workflows you probably use daily (@file by path, auto-mode defaults, idle compaction, Windows exFAT). **OpenAI Codex CLI 0.163.0** is the second-day-to-day coding agent — if you ship a router, test both. **Weekend action:** add an "Evaluator-ready" overlay to the router v2 artifact you're already planning (air-gapped runtime + trajectory + published-disclosure template) — this is the single piece that converts the router from "a portfolio demo" into "an artifact an actual Tier-1 evaluator org would clone."

Tags: `#claude-code #codex #routing #evaluator-ready #tools`

---

## 1. Claude Code v2.1.299 → v2.1.302 — four releases in four days, three of them change daily workflow {#1-claude-code-updates}

**What shipped (Oct 14–17):**

### v2.1.299 (Oct 14) — `@file` mentions pass **paths** not contents

- New env var: `CLAUDE_FILE_MENTION_PATHS=1`
- When enabled, `@filename` mentions pass **the file path** to Claude instead of injecting the file contents into the context window.
- Claude then reads the file itself via Read.

**Impact:** For large files in long sessions, this is a significant token-overhead reduction. The default behavior still injects contents — you have to opt in.

### v2.1.300 → v2.1.301 (Oct 14 – Oct 15)

- **Unattended retry mode gets a bail-out env var** — stop waiting if the usage-limit reset is far away (prevents unattended agents from idling for hours).
- **OpenTelemetry tracing guidance** added to the `claude-api` skill — the official way to wire Claude Code sessions into your observability stack.
- **Vim mode:** added `%` motion for bracket matching (works alone or with `d` / `c` / `y`).

### v2.1.302 (Oct 17) — the biggest release

- **Client-side auto-mode model selection** — Claude Code can now pick the model locally based on task-type signals rather than every call going through the gateway for model selection. Faster, cheaper, more auditable.
- **Idle compaction controls** — tune when the session's context is auto-compacted when idle.
- **Startup speedup with many plugins** — meaningful for anyone running the new plugin marketplace from [Oct 14 §4](../2026-10-14/03-practical-skills-and-tools.md#4-claude-code-october).
- **Windows exFAT/FAT32 file-write fix** — if you're on a dual-boot machine or USB-mounted workspace, previously-blocked writes now work.
- **General auto-mode improvements** — smoother handoff between planning / execution modes.

**Sources:**
- [Claude Code — Official Changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gradually.ai — Claude Code Changelog (October 2026)](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Releasebot — Claude Code Updates (October 2026)](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`

### What to do this weekend (20 min)

1. **Upgrade** (`claude --upgrade` or equivalent). Confirm v2.1.302+.
2. **Try `CLAUDE_FILE_MENTION_PATHS=1`** on your next long-session project. Measure token-count delta — this is a 10-50% session-cost reduction for file-heavy workflows.
3. **Add OpenTelemetry tracing** to one of your Claude-API-skilled projects. The `claude-api` skill now has the official recipe. **This is also an "evaluator-ready" signal** — observability is a Tier-1 evaluator checklist item.
4. **Set your auto-mode defaults** to prefer Haiku 5.5 at low effort unless the task class requires otherwise. The v2.1.302 client-side selector respects env-var overrides.
5. **(If on Windows)** retry any previously-failing file writes on exFAT/FAT32. The Oct 17 fix should resolve them.

→ Cross-link: [Oct 14 §4 — Claude Code October updates](../2026-10-14/03-practical-skills-and-tools.md#4-claude-code-october) · [`04` §3 air-gap discipline v2](./04-research-progress.md#3-discipline-v2).

---

## 2. OpenAI Codex CLI 0.163.0 — parallel tool use + Windows polish + thread recovery (Oct 16) {#2-codex-cli}

**What shipped (2026-10-16):** Codex CLI 0.163.0.

**Headline changes:**
- **Parallel tool use** — Codex can now call multiple tools in a single response (Claude-equivalent primitive since February).
- **Thread recovery** — if a session crashes mid-stream, the thread can be resumed. Previously, crashed sessions were lost.
- **Network safeguards** — more aggressive timeouts + retry logic on remote tool calls.
- **Windows clipboard support** — Codex can now interact with the Windows clipboard reliably.

**Why this matters (short):** Codex is maturing as the **second day-to-day coding-agent surface**. For most CS grads targeting a 2026–2027 role, having experience shipping on both Claude Code and Codex is more valuable than being an expert in one. **The two tools are reaching feature parity**; the differences are stylistic (Codex integrates tightly with ChatGPT; Claude Code integrates tightly with the Anthropic agent ecosystem).

**Sources:**
- [Releasebot — Codex 0.163.0 release notes](https://releasebot.io/updates/openai) `[aggregator]`
- [Tech-Insider — Codex CLI 0.162 vs Claude Code 2.1.296](https://tech-insider.org/codex-cli-0-162-vs-claude-code-2-1-296-2026/) `[analysis]`

### What to do this weekend (30 min)

1. **Install Codex CLI 0.163.0** alongside Claude Code (both run side-by-side; no conflict).
2. **Run the same 3-task workload through both** (e.g., "refactor this file," "add tests for this function," "generate a README for this repo"). Time + token + cost per task.
3. **Add the comparison to your router v2 artifact's README** — "the router works with both coding-agent surfaces" is a non-obvious + strong portfolio signal.
4. **For your résumé:** add Codex CLI as a specific line, not just "ChatGPT" — recruiters filtering on "Codex" as a keyword are hiring for OpenAI's Agent Platform.

→ Cross-link: [Oct 14 §2 — Router rebuild](../2026-10-14/03-practical-skills-and-tools.md#2-router-haiku-rebuild).

---

## 3. The "Evaluator-ready" overlay — the single highest-leverage weekend task {#3-evaluator-ready}

**The reframe:** The Oct 14 edition framed this weekend as "router v2 artifact + a ChatGPT native app." Oct 15's METR embed changes the priority. **The router v2 artifact is still the right thing to build; but add a 2-page "Evaluator-ready" overlay that pushes it from "demo" to "artifact that an actual Tier-1 evaluator (METR / SecureBio / Apollo / UK AISI) would clone."**

**What to add to the router v2 artifact's README:**

### A. "Air-gapped runtime" section (10 min, cite [Oct 14 §5](../2026-10-14/03-practical-skills-and-tools.md#5-air-gap-evals))

Explicit statement:
```
This router's eval harness runs in an air-gapped runtime by default:
  - No outbound network access.
  - Tool-call allowlist pinned to the exact tools under test.
  - All other tool calls return a static error.
  - Prompt-injection payloads targeting the test harness itself are included
    in the injection corpus.
```

### B. "Trajectory + progress-accuracy logging" section (10 min, cite [Oct 14 §4](../2026-10-14/04-research-progress.md#1-october-arxiv))

Define three log channels per eval run:
1. **Outcome:** pass/fail against golden output.
2. **Trajectory:** step-by-step record (which tools called, which routing decisions made, which model + effort chosen).
3. **Progress-accuracy:** at each timestep, ask the agent to self-estimate % complete; grade against actual timeline. Cite the "Unreliable Progress Bar" paper.

### C. "Published-disclosure template" section (15 min, cite [`01` §1](./01-big-lab-moves.md#1-metr-tier-1))

A 1-page template that mirrors what a Tier-1 evaluator would publish if the router found a capability issue:
- **Finding** (what was observed)
- **Severity** (per Anthropic's framework — critical / high / medium / low)
- **Reproducibility** (steps to reproduce; eval version; model version)
- **Non-equity disclaimer** (the author of the finding has no equity in the lab under test)
- **Suggested remediation** (not required; good signal if present)

### D. "Non-equity ground rules" section (5 min)

Short block mirroring Anthropic's framework language:
```
Author ground rules (copying Anthropic's 2026-10-15 framework):
  - Author holds no equity in the labs under evaluation.
  - Author has no commercial dependency (consulting, employment)
    on the labs under evaluation at the time of running the eval.
  - Author discloses any prior employment or financial relationship.
```

### E. "Reproducibility hash + eval version pin" (5 min)

- Hash the eval harness + the fixture inputs + the model version.
- Commit the hash to the README.
- Any future run that produces a different hash is a different eval. This solves the "did the eval change?" audit question before an evaluator org asks it.

### Why these five additions matter

Each is **under 15 minutes of writing time**, but together they move the artifact from "a nice demo someone built in a weekend" to **"a reference implementation that an actual Tier-1 evaluator could fork and use."** Which is exactly the signal that opens cold emails to METR / SecureBio / Apollo / UK AISI.

**One cold-email template per evaluator org** (also 5 min total):

```
Subject: Reference implementation for your Tier-1 publication framework

Hi [name],

I built a minimal reference implementation of a model router that
adopts your published evaluator framework end-to-end:
  - Air-gapped runtime
  - Trajectory + progress-accuracy logging
  - Published-disclosure template
  - Non-equity ground rules
  - Reproducibility-hash + eval-version pinning

Repo: [link]
Walkthrough (90 sec): [link to a loom/screencast]

Would love 20 min of your time to hear what I missed, and what a
Tier-1 evaluator would want next from an open-source reference.

— [you]
```

The ask is 20 minutes. The yes-rate at this spec level is unusually high.

→ Cross-link: [`01` §1 METR embed](./01-big-lab-moves.md#1-metr-tier-1) · [`05` §3 cold-reach-out plan](./05-career-and-startup.md#3-apply-plan) · [Oct 14 §2 router rebuild](../2026-10-14/03-practical-skills-and-tools.md#2-router-haiku-rebuild).

---

## 4. Which ChatGPT app to pick, revised with NextSlide context {#3-chatgpt-app-pick}

**The Oct 14 ask (ship one ChatGPT native app this weekend) remains valid.** The Oct 15–17 updates sharpen the pick:

- **DON'T** build a slide-generation app — OpenAI just acquired NextSlide and shipped the PowerPoint add-in. You'll be competing with the house.
- **DO** build either:
  - **An eval-adjacent utility** (reads your prior 10 ChatGPT conversations and generates a short "progress report" — alignment to the Oct 15–17 story, cheap to ship, novel enough to post about).
  - **A model-router demo** (a ChatGPT app that lets you call Claude or Gemini-4-Argon from inside ChatGPT and compares outputs). This is directly aligned with the router artifact.
  - **A workflow-automation primitive** that lives on OpenAI's app surface + calls your own Claude backend. Shows you understand the dual-vendor pattern.

**Timebox:** 4 hours Saturday. The scope should be *tiny* — ship a demo, not a product.

→ Cross-link: [Oct 14 §3 — ship a ChatGPT app](../2026-10-14/03-practical-skills-and-tools.md#3-chatgpt-app) · [`02` §3 NextSlide rollout](./02-new-emerging.md#3-nextslide-rollout).

---

## 5. The "which router goes where" default table — updated with Argon {#5-routing-table-v2}

With Argon now in paid-tier GA ([`01` §2](./01-big-lab-moves.md#2-gemini-4-argon)), the recommended default routing table changes:

| Task class | Default model | Why |
|---|---|---|
| Terminal / shell coding, multi-step agent | **Claude Opus 5.5** | Still 10 pts ahead of Argon on Terminal-bench 4.0; Anthropic ecosystem alignment |
| High-volume classification, routing, summarization | **Claude Haiku 5.5 (effort-low)** | 75% cheaper than Haiku 4.5; shipped Oct 7 as new default |
| Browser-use, subagent orchestration | **Claude Haiku 5.5 (effort-medium)** | 72.4% OSWorld 2.1; was the Oct 14 default |
| Long video / audio multimodal | **Gemini 4 Argon** | 91.7% LVBench; Google's video-encoder stack is still best in class |
| Cost-sensitive general reasoning | **Gemini 4 Argon or GPT-6 Astra** | Argon 52.56 II / Astra 52.67 II; near-tie, use whichever has a volume discount |
| High-stakes reasoning + long context | **Claude Opus 5.5** | 57.62 II — 4-5 pts ahead on independent benchmarks |
| Local / sandbox / air-gapped | **Claude Haiku 5.5 (effort-high) via local proxy** | Smallest cheap tier that still clears OSWorld 2.1 bar |

**Caveat:** Numbers above are vendor + independent (Artificial Analysis) blended. Run your 5-case eval before shipping to production.

→ Cross-link: [Oct 14 §2 router rebuild](../2026-10-14/03-practical-skills-and-tools.md#2-router-haiku-rebuild) · [`01` §2 Gemini 4 Argon](./01-big-lab-moves.md#2-gemini-4-argon).
