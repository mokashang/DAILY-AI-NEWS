# Practical Skills + Tools — 2026-11-18

Five concrete 10–45-minute operations to run this week — cost-model re-pricing, benchmark side-by-sides, Copilot swap-ins, Orchestrator turn-on, and the still-active `.claude/settings.local.json` audit from yesterday. All are reversible, all pay back within one week of use.

Tags: `#practical #tools #claude-code #openai #gemini #microsoft #cost`

---

## 1. Re-price your stack TONIGHT against the 48-hour shift (45 min) {#1-reprice-stack}

**Why:** Three pricing shocks landed in 48 hours — **GPT-6.2 Astra 20% off**, **MAI Code 2 Flash at ~20% of Haiku 5.5 price**, and **Gemini Antigravity Orchestrator saving ~24% quota**. If your pricing model (or your startup's unit economics) was built 7 days ago, it's wrong.

**What to do:**

1. **Open your `pricing.md` / `costs.csv` / wherever you track per-call cost.** If you don't have one, create `/tmp/pricing.md` right now — it's the single highest-leverage spreadsheet an AI engineer owns.
2. **Add/update the Nov 17 prices:**
   ```
   Model                  | Input $/M | Cached $/M | Output $/M | Notes
   -----------------------|-----------|------------|------------|------
   gpt-6.2-astra          | $8.00     | $0.40      | $40.00     | NEW: 20% below prior
   gpt-6.2-sol            | $2.00     | $0.10      | $10.00     | unchanged
   claude-fable-5.2       | $8.00     | ~$0.40     | $40.00     | existing
   claude-mythos-5.2      | $3.00     | ~$0.15     | $15.00     | existing
   claude-haiku-5.5       | ~$1.00    | ~$0.05     | ~$5.00     | existing
   gemini-4-carbon        | $2.00     | —          | $10.00     | intro, doubles Dec 1
   gemini-4-hydrogen      | ~$0.30    | —          | ~$2.50     | NEW, fast worker tier
   mai-code-2             | ~$3.00    | —          | ~$12.00    | est, 40% of GPT-6.1 Sol
   mai-code-2-flash       | ~$0.20    | —          | ~$1.00     | est, 20% of Haiku 5.5
   mai-image-2.7          | $35 per 1K images (max); $10 per 1K (Flash)
   mai-realtime-1         | $0.01 per audio-minute
   ```
   (MAI prices are **Microsoft-estimated and not independently verified** — put an `[est.]` tag next to them in your sheet.)
3. **Swap your default coding call:**
   - Change `gpt-6.1-sol` → `gpt-6.2-sol` in your default integrations (same price, better benchmarks, free upgrade).
   - Keep Astra for explicit escalation only — do not auto-upgrade.
4. **Recompute gross margin at the lowest-cost competitor.** For each product line, re-model GM at (a) your current vendor, (b) MAI Code 2 Flash + Gemini Orchestrator (worst-case competitor stack). If GM at (b) drops below 40%, you have a switching-cost problem to solve in Q1 2027.
5. **Set a cal reminder for Dec 1** — Gemini 4 Carbon intro pricing expires, doubling to $4/$20 per 1M. Any cached work should ship before Dec 1.

**Expected payback:** If your monthly token spend is >$200/month (which is almost any dev running Codex + Claude Code), swapping Sol default alone is a ~$20/mo saving. At scale (startup with $10K/mo API spend), this exercise saves **$1–2K/mo** and prevents a wrong-size fundraise.

→ Cross-link: [`01` §4 — GPT-6.2 Astra + Sol](./01-big-lab-moves.md#4-openai-gpt62-astra-sol) · [`01` §3 — MAI family](./01-big-lab-moves.md#3-microsoft-mai-ignite)

---

## 2. Side-by-side benchmark MAI Code 2 Flash vs Claude Haiku 5.5 on your actual repo (45 min + wait time) {#2-benchmark-mai-code2}

**Why:** Microsoft claims MAI Code 2 Flash matches Haiku 5.5 at 20% of the price. If this holds on *your* code, switching is a 5× unit-economics win. If it doesn't, you have interview-grade empirical data to cite.

**What to do:**

1. **Pick 10 real coding tickets from your repo** — mix of easy bug-fixes, medium refactors, and one agent-style multi-step task.
2. **Save each ticket's prompt** to `/tmp/bench/ticket-NN.md`.
3. **Run each prompt against both models** via API (Claude SDK + MAI Azure endpoint). Capture: (a) first-token latency, (b) total tokens used, (c) whether the diff applied cleanly, (d) whether CI passed, (e) your subjective 1–5 "would I ship this" score.
4. **Tabulate**:
   ```
   Ticket | Haiku 5.5 result | MAI Code 2 Flash result | Winner | Cost ratio
   ```
5. **Publish the result as a public gist or blog post** — this is a near-perfect FDE/MLE portfolio artifact (empirical + near-term + opinion-free). Tag @ (official account) on X for extra reach.

**Caveats:** MAI Azure endpoint may require a limited-access registration. Use Azure Foundry preview if available in your org. If you can't get access, fall back to the best open-weight coding model (Kimi K3 or GLM 5.3) as a comparison.

**Expected payback:** Portfolio-grade empirical write-up in 2 hours. The pattern "I ran 10 tickets through X vs Y and here's the distribution" is a recurring Anthropic Solutions / OpenAI FDE interview talking point.

→ Cross-link: [`01` §3 — MAI family](./01-big-lab-moves.md#3-microsoft-mai-ignite) · [`05` §2 — Jobs from today](./05-career-and-startup.md#2-jobs-from-today)

---

## 3. Swap Office tasks to Copilot (Office in Copilot GA) and benchmark against Claude Whiteboards/Sheets (30 min + 1 week trial) {#3-office-in-copilot-swap}

**Why:** Microsoft shipped **Office in Copilot GA** on Nov 17 — Word, Excel, PowerPoint inside the Copilot chat surface, inheriting tenant labels + permissions. This is the direct competitor to Claude Whiteboards + Sheets + Data (from Nov 10). You should know which one your target enterprise prospects will prefer.

**What to do:**

1. Pick **one workflow you own this week** that lives in Office today — e.g., a recurring status doc, a monthly data refresh in Excel, a slides deck you recycle.
2. **Rebuild it twice**: once in Office in Copilot (via Copilot chat inside Word/Excel), once in Claude Whiteboards + Sheets.
3. **Grade on 5 axes (1–5 each):** (a) prompt-to-first-output latency, (b) permissions/labels inheritance (Microsoft's claimed advantage), (c) edit-in-place fidelity, (d) multi-user collaboration, (e) share link + permissions model.
4. Write up the comparison in 500 words, publish to your blog or LinkedIn.

**Known caveat:** Office Watch flagged that **only 76 of 215 announced Ignite features are actually GA on Nov 17–18** — Office in Copilot GA is one of the 76 that *is* ready, but Copilot Workspaces is Frontier preview only. Verify exact state in your tenant.

**Expected payback:** FDE/Solutions-eng interviews love "I've evaluated both and here's the decision matrix" — this is a reusable artifact for every enterprise-AI job app.

→ Cross-link: [`01` §6 — Office in Copilot](./01-big-lab-moves.md#6-microsoft-copilot-azure)

---

## 4. Turn on Antigravity Orchestrator for multi-step coding workflows (10 min) {#4-turn-on-orchestrator}

**Why:** Google's **Antigravity Orchestrator** (Carbon + Hydrogen pair) saves **~24% quota + 19% time on average** vs. Carbon-only. If you're on Google AI Ultra ($250/mo or equivalent), this is a one-click efficiency win. On paid Pro you get the Argon variant.

**What to do:**

1. Open **Google Antigravity** (your AI-coding IDE if you're on it, or Google AI Studio for the API variant).
2. In settings / model picker, select **Orchestrator (Carbon + Hydrogen)** or **Orchestrator (Argon + Hydrogen)** per tier.
3. For your next 5 multi-step coding tasks, use Orchestrator. Record: did it plan, did it fail-mid, did Carbon repair-the-plan, did it ship?
4. If you're not on AI Ultra, **implement the pattern yourself on any API** — have a planner model (Carbon, Sol, Mythos) emit a plan JSON, then a worker model (Hydrogen, Flash, Haiku) execute each step, and loop back to planner on failure. **This is the single highest-leverage portfolio artifact for a mid-level FDE/MLE résumé right now** — see §2 of the research file for the underlying pattern.

**Caveat:** Google's 24% + 19% numbers are vendor-reported and not independently replicated. Test on your own workloads.

**Expected payback:** If you run ≥2 coding sessions per day through this pattern, you get **~5 hours/month back** and **~20% quota headroom** — enough to run an additional side project per quarter.

→ Cross-link: [`02` §1 — Gemini 4 Hydrogen + Orchestrator](./02-new-emerging.md#1-gemini-4-hydrogen)

---

## 5. If you missed yesterday — audit every public repo for leaked `.claude/settings.local.json` TONIGHT (15 min) {#5-audit-claude-settings}

**Why:** From yesterday's Apiiro disclosure: **Claude Code's "Don't Ask Again" toggle persists the full command (including inline secrets) into `.claude/settings.local.json`**; **104K public GitHub files have been found with 1,122–2,539 real credentials exposed.** The data is being actively scraped. If you have ever typed an API key, SSH command, database URL, or token into a Claude Code command and clicked "Don't Ask Again," **you are in the exposure set**.

**What to do:**

1. **Search your own GitHub**: `gh api -X GET search/code -f q='filename:settings.local.json user:<your-username>'` (or use Grep across your local clones).
2. **For every match**: open the file. If any `allow` entry contains a token-shaped string (`sk-*`, `ghp_*`, `AIza*`, `xoxb-*`, AWS keys), **rotate the credential now**. Deleting the file or git-history rewrite does **not** revoke; only credential rotation does.
3. **Prevent recurrence**: add `.claude/settings.local.json` to your global `.gitignore`:
   ```bash
   echo '.claude/settings.local.json' >> ~/.gitignore_global
   git config --global core.excludesFile ~/.gitignore_global
   ```
4. **Verify**: `git check-ignore -v .claude/settings.local.json` in any repo.

**Expected payback:** Avoids a **public credential breach**. This is a 15-minute insurance policy. **Also a portfolio artifact**: write up "I audited X repos, found Y exposures, rotated Z credentials" as a security-eng case study.

→ Cross-link: back to [2026-11-17/03 §1](../2026-11-17/03-practical-skills-and-tools.md#1-audit-claude-settings)

---

## 6. Quick tool-of-the-day: `llm` + GPT-6.2 Sol + MAI Code 2 Flash pipe

Simon Willison's `llm` CLI already supports the new OpenAI model IDs out of the box. One-liner you can start using today:

```bash
# Set GPT-6.2 Sol as your default (free upgrade)
llm models default gpt-6.2-sol

# Pipe a diff through for review
git diff HEAD~1 | llm "Review this diff for correctness, reuse, and style. Flag anything that would fail code-review at a frontier-lab FDE interview."

# Escalate to Astra on-demand
git diff HEAD~1 | llm -m gpt-6.2-astra "Rewrite this diff as if you were preparing a staff-level code review."

# Compare with MAI Code 2 Flash (requires Azure endpoint config)
git diff HEAD~1 | llm -m mai-code-2-flash "Same prompt"
```

Build a `.bashrc` / `.zshrc` alias for your three favorites so you can pipe + switch models without thinking. This is the single highest-ROI terminal workflow of 2026.

Tags: `#tools-of-the-day #llm-cli #simonw`
