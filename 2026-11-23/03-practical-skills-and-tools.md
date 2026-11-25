# Practical Skills & Tools — 2026-11-23

Five concrete things to do this week, roughly by return-on-time. **(1) Patch Claude Code to ≥2.1.326** — 2.1.319 was mostly a security fix for a Bash permission bypass + worktree sandbox escape, 2.1.326 wires Code Mode into agent teams. **(2) Publish a `router.md` to your portfolio repo tonight** — three frontier models now sit at overlapping price points, so a routing policy + 20-case eval is the single most legible 2026 portfolio artifact. **(3) Add a Gemini 4 Neon case to your evals** — its Vending-Bench 2 + SEC-bench Pro lead means it will show up in production as the default for business-ops agents. **(4) Internalize the Terminal-Bench 2.1 audit lesson** — publish your eval harness, not just your scores. **(5) MCP spec reminder** — 2026-07-28 remains current; the window is stable, keep shipping servers.

Tags: `#claude-code #routing #evals #mcp #portfolio #vibe-coding`

---

## 1. Claude Code 2.1.319 → 2.1.326 — security fixes + Code Mode in agent teams {#1-claude-code}

**What shipped (2026-11-06 → 2026-11-16):**
- **v2.1.319 (Nov 6):** **>50% of release is security fixes.** Patches a **Bash permission bypass** (tool call could execute without permission check) and a **worktree sandbox escape** (operations could leak outside the sandboxed worktree). If you haven't updated since late October, **upgrade today** — this is not an incremental version.
- **v2.1.325 (Nov 13):** Incremental polish.
- **v2.1.326 (Nov 16):**
  - **Code Mode now works with agent teams** — a `Code` subagent can be invoked from a team definition, so `/plan` + `Code` + a verifier can be composed as an SDK pattern.
  - **Startup warnings catch malformed tool rules** before the session begins.
  - **Tighter default permissions** on first launch.
  - `/rewind` restored; **background sessions** more stable.

**Sources:**
- [code.claude.com/docs/en/changelog](https://code.claude.com/docs/en/changelog) `[primary]`
- [claudekit — Claude Code 2.1.319 release notes](https://claudekit.io/en/updates/claude-code-2-1-319/) `[aggregator]`
- [Havoptic — Claude Code v2.1.326](https://www.havoptic.com/r/claude-code-2.1.326) `[aggregator]`
- [Claude World — What's New Nov 2026](https://claude-world.com/articles/claude-code-november-2026-whats-new/) `[aggregator]`

### Why it matters to you

- **Job lens:** The security-fix cadence (and the fact that >50% of 2.1.319 was CVE-adjacent) is the **single most visible signal that Claude Code is an "enterprise tool"** now, not a developer toy. On an Anthropic FDE interview, the right way to talk about Claude Code is **operationally**: version pinning, permission scopes, sandbox boundaries — not features. Ship a `.claude-code-version` file in your portfolio repo this week.
- **Startup lens:** **Code Mode + agent teams** is the pattern to study. Anthropic is publicly productizing the "plan → write → verify" multi-agent loop that most agent startups built as proprietary scaffolding. If your startup is a Claude-Code wrapper, this news deprecates ~30% of your backend code; if your startup is downstream of Claude Code (eval, observability, CI), you just got a cleaner primitive to hook into.
- **Insight:** **Upgrade cadence is itself a signal.** Anthropic shipped 7 Claude Code versions in the Nov 6–16 window. That ship rate is only sustainable if the team is big — which says Anthropic is still hiring Claude Code engineers hard despite the IPO. If you want to work on Claude Code itself, the team is in a hiring posture; file the application.

**To do (30 min):**
```bash
# Pin the version in your portfolio repo
echo "2.1.326" > .claude-code-version
# Sanity-check installed version
claude-code --version
# Patch if stale
claude-code upgrade
```
Then add `.claude-code-version` to your `.gitignore` *exception* list so it stays tracked.

---

## 2. Ship a `router.md` + 20-case eval to your portfolio tonight {#2-routing-policy}

**The 2026 FDE portfolio piece.** Three $8–$3 frontier models from three labs with overlapping capabilities = **routing is the most legible applied-AI skill**. Here is the template:

### `router.md` skeleton

```markdown
# Model Routing Policy — [your name], v1 — 2026-11-23

## Defaults
- **General text, cost-weighted:** Gemini 4 Neon ($3/$15, Vending-Bench 2 #1)
- **Agents' tool use, latency-weighted:** GPT-6.2 Astra ($8/$40, Agents' Last Exam #1 cost-adjusted)
- **Coding (shell, SWE-Bench, multi-file refactor):** Claude Fable 5.2 or Opus 5.5 ($8/$40,
  Terminal-Bench 4.1 + FrontierCode 2.0 #1)

## Escalation
- First call: Default by task class above
- On failure signal (parser error, eval-grader fail, user "regenerate"): escalate to Fable 5.2
- Hard budget cap: $X per session; refuse > cap with a canned "retry with smaller prompt"

## Degraded-mode fallbacks
- If Anthropic 5xx: GPT-6.2 Astra as coding replacement; Neon as general replacement
- If budget blown: GPT-6.2 Sol ($2/$10) as emergency cheap-mode

## Eval (see /eval)
- 20 cases across 4 task classes (5 each): coding, agent-tool-use, long-context, general
- Graded by rubric + a judge model (Gemini 4 Neon acts as cheap judge)
- Run on CI weekly; commit scores to `eval/scores/YYYY-MM-DD.json`
```

### The 20-case eval

Pick **5 cases per class** × **4 classes** = **20 cases**. Each case has: input, expected outputs (acceptable set), grader rubric (3–5 bullets). Commit the whole thing to a public repo. Keep cases small — 1–3K tokens each — so you can rerun on every model release without a cost blowout.

### Why it matters to you

- **Job lens:** This is the **#1 artifact for a 2026 FDE application**. It demonstrates: (a) you know every model's price in your head, (b) you know how to measure, (c) you've thought about degraded-mode operation, (d) you've got CI for AI. No other single artifact lets you show all four in a weekend.
- **Startup lens:** This is **also the first MVP for a routing/observability SaaS** (see §5 arms-dealers). Charge $X/call for: routing based on policy + eval-backed fallback + budget caps. If your 20-case eval shows an obvious win (e.g., "Neon-first routing saves 62% vs GPT-only on general tasks"), that's the opening slide of a pre-seed deck.
- **Insight:** The eval is the moat, not the policy. **Anyone can write a `router.md`; a 20-case eval that reruns on every model release is the actual IP.** Make the eval harness a separate repo so you can license it later.

**To do (tonight, 45 min):**
1. `mkdir -p portfolio/routing/eval/cases`
2. Write `router.md` from the template above, edit for your own task mix
3. Write 5 coding-task cases (take real GitHub issues you've fixed, strip to ≤3K tokens)
4. Write a trivial grader (text match or small-model judge); commit; push to GitHub
5. Add the URL to your résumé under "Projects" with the one-liner **"Routing policy over Fable 5.2, GPT-6.2 Astra, Gemini 4 Neon; 20-case eval + CI"**

---

## 3. Add Gemini 4 Neon to your evals this week — it will be production-default by January {#3-neon-vending-bench}

**Why:** Neon's **#1 on Vending-Bench 2 ($16,843)** and **SEC-bench Pro (90.5%)** make it the default back-office business-agent model at Ramp's top-1% spenders. If your interview pipeline includes **fintech / regulated-SaaS** companies, you will be asked specifically about Neon by January.

**What to do:**
- **Case 1 (coding):** a Terminal-Bench 4.1 task — Neon should **lose** (expected). Note it.
- **Case 2 (agents):** a Vending-Bench 2–style task (negotiate inventory and prices across a multi-step sim) — Neon should **win** on both score and cost.
- **Case 3 (long context):** a 500K-token document Q&A (edges toward 272K+ threshold where OpenAI surcharges). Neon's $3/$15 at 1M ctx is the best-value long-context today.
- **Case 4 (agent business ops):** generate a quarterly ops plan from CSV data (SEC-bench-style). Neon should win on cost-per-correct.

**The interview-ready one-liner from your eval:** *"Gemini 4 Neon beats Fable 5.2 on cost-per-correct for long-context business-ops tasks by ~3×; loses on code-in-shell by ~8%. Route accordingly."*

### Why it matters to you

- **Job lens:** Vertical-AI companies (Ramp, Brex, Mercury, Rippling, Carta, Alloy, Unit) all live in the "business-ops agent" space where Neon just took the lead. If you want FDE at any of them, name Neon by its benchmark win in your cover letter.
- **Startup lens:** Opportunity to **productize the Neon-for-finance-ops routing** before incumbents notice. First-mover wedge: "Finance agents on Neon — 60% cheaper than Fable, better on SEC-bench." Be careful on the moat; it's volatile.
- **Insight:** "Model-name fluency" is still dead as a résumé line — but **"model-benchmark-specific fluency"** (e.g., "I pick Neon for Vending-Bench-shaped tasks") is a 2026 skill.

---

## 4. Terminal-Bench 2.1 audit — publish your eval harness, not just your scores {#4-terminal-bench-audit}

**What happened (arXiv 2611.08417, Nov 5):**
- Researchers audited **Terminal-Bench 2.0** (one of the most-cited agent benchmarks in 2026) and found **issues in ~30% of tasks**.
- Released **Terminal-Bench 2.1** with repairs.
- Explains why "my Terminal-Bench score moved" conversations between model announcements have been noisy — part of the signal was eval error, not model change.

**Source:** [papers.cool — arXiv 2611.08417](https://papers.cool/arxiv/2611.08417) `[aggregator]`

### Why it matters to you

- **Job lens:** The practical takeaway is operational: **in interviews, never quote a benchmark score without naming the version and the harness**. "Opus 5.5 scored X on Terminal-Bench" is the amateur answer; **"Opus 5.5 scored X on Terminal-Bench 2.1 (post-audit) under default harness settings, verified against the 2.1 repro script"** is the FDE answer. Practice this phrasing.
- **Startup lens:** **Eval-as-a-service** is a category that just got a market-size proof point. ~30% error rate on the leading open benchmark means every serious AI buyer needs a trusted eval partner. Opportunity: a "Terminal-Bench but reproducible-by-default" harness-as-service with weekly benchmark runs for a subscription price.
- **Insight:** **Post-audit, benchmark authority is up for grabs for ~90 days.** Anyone who ships a credible, well-run, community-trusted benchmark in that window gets outsized distribution. If you have a benchmark idea you've been sitting on, **ship it in the next 90 days**.

---

## 5. MCP spec is stable — keep shipping servers; the window is still wide open {#5-mcp}

**Status as of 2026-11-23:**
- **Current spec:** **2026-07-28 (stateless)** — no new revision in this window.
- **All four Tier-1 SDKs** (Python, TypeScript, Go, Rust) speak the current spec.
- The **12-month deprecation window** for pre-stateless servers is underway (deprecate by Jul 2027).

**Source:** [modelcontextprotocol.io — 2026-07-28 changelog](https://modelcontextprotocol.io/specification/2026-07-28/changelog) `[primary]`

### Why it matters to you

- **Job lens:** MCP-server authorship remains the **#1 portfolio artifact for FDE applications** (reconfirmed from prior editions). The stability is a feature: a server you ship this week will still be current on your January interviews. **Three-server threshold** stays unchanged: 1 server = "tried it", 3 servers = "understand the protocol".
- **Startup lens:** A stable spec + growing ecosystem = this is the **safest surface in AI infra to build on right now**. "MCP server for X vertical" is a legitimate wedge if X has non-obvious data access (CRM, EHR, trading data). Don't build "MCP server for GitHub" — it's been done; build "MCP server for [the one data source your prior job had unusual access to]".
- **Insight:** The absence of a new spec is itself news. **The protocol is in "grow the ecosystem" phase, not "chase the spec" phase.** Ship servers, not spec commentary.

---

## 6. The vibe-coding pattern of the week: Code Mode in team mode {#6-vibe-coding}

**The pattern (new in Claude Code 2.1.326):**
```
agent-team:
  members:
    - name: planner
      role: writes the failing test (tests-as-spec)
    - name: coder
      role: Code Mode — iterates until the failing test passes
    - name: verifier
      role: reviews diff; blocks merge if CI red or if diff > N lines
```

**Why it ships things:** The "tests-as-spec" pattern from last edition is now **composable with Code Mode in an agent-team definition** — meaning you can run the whole loop (plan → code → verify) as one SDK call instead of orchestrating it yourself. **Velocity gain is ~2–3× for medium-complexity tasks**, per practitioner reports on Latent Space.

**To do (weekend):**
1. Take your portfolio's biggest half-finished issue
2. Write a failing test (the "spec")
3. Define the 3-member agent team in `.claude/agents.yml`
4. Run `claude-code run --team my-team "fix issue-12"`
5. Watch the planner → coder → verifier loop; when it merges green, the artifact is done
6. Commit the `.claude/agents.yml` to the portfolio repo; add a README section "How this repo uses agent teams" — that's the interview-ready writeup

### Why it matters to you

- **Job lens:** This is the **concrete evidence that goes under "vibe-coding"** on your résumé. Not "I used an AI coding tool" but "I compose planner/coder/verifier agents in Claude Code with tests-as-spec, shipping ~2× faster on medium tasks."
- **Startup lens:** The agent-team YAML is a **lock-in surface** — once your team's workflows are encoded as YAML, you're switching costs away from Claude Code for 6+ months. This is why Anthropic shipped the feature; it's why you should build on it. Churn-management is the next startup wedge *around* this surface (re-export to Cursor/Zed, configuration version-control, team audit logs).

---

## 7. Quick hits this week

- **`llm` by Simon Willison:** no new release this window; **0.37 from prior edition is still current** — keep using `git log | llm` as your pipe-native workflow.
- **LangChain / LangGraph:** no new in-window releases; **1.4.9 + 1.2** from prior editions still current — the HITL-interrupt middleware remains the enterprise-friendly guardrail.
- **Cursor / Zed / Windsurf:** no new in-window updates surfaced. If you use Cursor, keep it pinned at your current version; the quiet period is typical post-funding.
- **GitHub trending (AI):** no new standout in-window project rose to top — standard Nov pre-holiday pattern. Expect Dec 1–15 to spike (Hacktoberfest aftermath + Dec hobbyist surge).
