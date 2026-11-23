# Practical Skills & Tools — 2026-11-22

Four practical items to internalize this week: **(1) Claude Code 2.1.328 ships `onFailure: block` for mcp_tool hooks and new skill-hook limits — building a `.claude/hooks/` template repo is now the #1 portfolio artifact for FDE applications**; **(2) The $8/$40 flagship pricing floor across Fable 5.2 / GPT-6.2 Astra / Gemini 4 flagship means routing is the whole game — learn Not Diamond / Martian / OpenRouter cost patterns**; **(3) ChatGPT Wallet proves agent payments want biometric-per-transaction, not session auth — this is a UX pattern to copy for any agent you ship**; **(4) MedChemBench being released alongside the Accounting plugin shows "benchmark + vertical plugin" is OpenAI's new shipping shape — expect labs to publish task-specific evals alongside every vertical they target.**

Tags: `#claude-code #mcp #skills #hooks #routing #agent-payments #evals #vibe-coding`

---

## 1. Claude Code 2.1.328 — mcp_tool `onFailure: block` hooks + skill-hook limits + SessionStart rescanSkills {#1-claude-code-2-1-328}

**What changed (Nov 3 and Nov 19, 2026 entries):**
- **`onFailure: "block"` added to mcp_tool hooks** (parity with command and HTTP hooks). When a hook attached to an MCP tool fails, it blocks the call instead of logging a warning. This is **the production-grade primitive for enforcing guardrails on third-party MCP servers you don't control**.
- **Skill-hook limits:** the skills of a single source (a repo, your own folder, or a plugin) can now register **at most 1,024 hooks and 16,384 matcher characters** per session. Prevents hook-bomb attacks from a malicious skills repo.
- **SessionStart `rescanSkills` flag:** a SessionStart hook can now return a flag that triggers Claude Code to **re-scan skill directories mid-session**, so hook-installed skills become available in the **same session** that installed them. Also: SessionStart hooks can now **set the session title**.
- **Skills Claude runs with a model setting other than `context: fork`:** subagents, forks, compaction, and `/recap` now stay on the session's model instead of falling through to a default.
- **Compaction now resends the skill list;** `/reload-skills` sends only new or changed skills (faster, smaller round-trips).
- **Current version as of Nov 19: 2.1.328.**
- **Fixes:** skill hooks firing twice per event; plugin WorktreeCreate / WorktreeRemove hooks being ignored.

**Sources:**
- [Claude Code changelog (code.claude.com)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gradually.ai — Claude Code Changelog November 2026](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Releasebot — Claude Code Updates by Anthropic, November 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [Medium — What Changed for Claude Code Skills This Week](https://medium.com/@abhinav.dobhal/what-changed-for-claude-code-skills-this-week-and-what-two-trending-skill-libraries-get-right-819535ba5b93) `[analysis]`

### How to use it this weekend

**Build and publish a `.claude/hooks/` template repo.** Target: **~4 hooks**, each one 10–30 lines, all working together.

1. **`preToolUse.sh`** — gates any `Bash` call that touches production (looks at `$HOOK_INPUT.toolInput.command` for `rm -rf`, `DROP TABLE`, `kubectl delete`).
2. **`mcp_tool.onFailure=block` config** — attach to a public MCP server (Stripe, Linear, GitHub); fail-closed if the response schema doesn't validate.
3. **`sessionStart.sh`** with `rescanSkills: true` — installs one in-repo skill at session start (e.g., a `/ship-safely` skill).
4. **`sessionEnd.sh`** — writes a 3-line summary of what the session changed to a git note.

**README has:** 60-second install, a 5-case eval (did the hook catch the bad command? did it allow a good one?), and a 90-second GIF demo. **Tag it `#claude-code #hooks #fde-portfolio` and link from your résumé.** Hiring managers at Glean, Distyl, Decagon, and Sierra read Claude Code README files directly — this is the single highest-conversion portfolio artifact for FDE applications right now.

### Why it matters to you

- **Job lens:** **Hooks are the new MCP-server-equivalent portfolio artifact.** 90% of applicants submit prompts and chat screenshots; the ones who get the first call submit a public `.claude/hooks/` repo with a 5-case eval. Zero FDE job description mentions "hooks" explicitly yet, but every interviewer knows what `onFailure: block` means — using the primitive signals you can ship production-grade agents.
- **Startup lens:** If you're building an agent platform, **your pricing page needs a "hooks + guardrails" tier** — enterprise customers won't buy an agent they can't block. Price the guardrail tier at **2–3× the base agent SKU** (that's where the margin is).
- **Insight:** **`onFailure: block` is the moment hooks became production-grade.** Before this, hooks were lint-level warnings; now they're first-class control-plane primitives. Expect LangChain / CrewAI / AutoGen to copy the pattern within 90 days.

→ Cross-link: [`05` §2 — FDE portfolio artifacts](./05-career-and-startup.md#2-fde-comp)

---

## 2. Routing is the whole game — $8/$40 flagship pricing is now the market {#2-rubin-kernels}

**What changed (Nov 10–17, 2026):** Three flagships converged at the same price in 10 days.
- **Claude Fable 5.2:** $8/M input, $40/M output (Nov 10).
- **GPT-6.2 Astra:** $8/M input, $40/M output (Nov 17, per secondary coverage).
- **Gemini 4 flagship tier** (Argon/Carbon): at or near the same band based on Google Cloud pricing pages.

**Implication:** **model pricing is no longer a differentiator at the frontier**. Margins live at two layers:
1. **Routing:** picking the cheapest model that can solve each sub-task.
2. **Infrastructure cost:** what you pay the inference provider (fal, Baseten, Together, Fireworks) vs. list API pricing.

### How to use it this weekend

**Write a one-afternoon routing shim** and benchmark it on your own workflow.

1. Instrument your current agent loop: for every LLM call, log `{task_type, input_tokens, output_tokens, model, cost}`.
2. Classify calls into 3–5 buckets: `reasoning / coding / summary / extraction / tool-call`.
3. For each bucket, pick two candidate models — one flagship ($8/$40) and one workhorse ($1–2 / $5–10).
4. Route each bucket to its cheaper model; fall back to flagship on structured-output validation failure.
5. **Target: 40–70% cost reduction with <5% quality regression** on your own task distribution.

Tools that make this 10 lines, not 100:
- **Not Diamond** — hosted router API.
- **Martian** — hosted router with per-task pricing optimization.
- **OpenRouter** — unified API, you pick the router policy.
- **LiteLLM** — self-hosted proxy with routing configs.

Publish your benchmark (anonymize the workflow) as a blog post. **This specific artifact — "I cut my agent cost 60% with a 10-line router" — gets hiring-manager attention at every inference-cost-conscious AI startup** (which is now all of them).

### Why it matters to you

- **Job lens:** Add **"wrote a production router that cut X workflow cost by Y% with Z% quality maintained"** to your résumé top-3 bullets. This is **the single highest-leverage résumé bullet for inference-economics-literate roles** at Baseten, Together, Fireworks, Not Diamond, Martian, LangChain, and every FDE team at a lab or applied-AI startup.
- **Startup lens:** If you're building any agent product, **budget 15–25% of eng time on routing and cost telemetry**, permanently. Companies that don't have per-task cost dashboards by Q1 2027 will be out-priced by companies that do.
- **Insight:** **The model-pricing floor is the first convergence event in frontier AI.** Compare to cloud compute pricing converging on EC2 ~2010 — at that moment, the moats moved from raw compute to developer experience, services, and vertical integration. **The same transition is happening to model APIs right now.**

→ Cross-link: [`02` §2 — Model ML data platform](./02-new-emerging.md#2-model-ml)

---

## 3. ChatGPT Wallet's biometric-per-transaction UX is the agent-payment pattern to copy {#3-router-patterns}

**What changed (Nov 13, 2026):** OpenAI's **ChatGPT Wallet** went live for US Pro subscribers.
- Agents can make purchases using **card-network tokens** (Visa/Mastercard tokenized card primitives, not raw PANs).
- **Biometric approval required for every purchase** (Face ID / Touch ID / platform biometric), not session-level auth.
- Agents never see the card number; they see a one-time tokenized reference.

**Implication:** OpenAI has publicly committed to the UX pattern that **every agent-payment product should copy**. Anyone shipping agent payments without per-transaction biometric is going to look dangerous by comparison within 90 days.

### How to use it this weekend

**If you're building any agent that spends money, structure the payment surface like this:**

1. **Never store raw payment credentials** inside the agent. Use a tokenization layer (Stripe Connect, Marqeta, Lithic, Privacy.com for test cases).
2. **Per-transaction authorization step** — explicitly re-prompt the user with the amount, the merchant, and a biometric check. Session auth is insufficient.
3. **Per-category spending limits** — stored in the user profile, enforced at the token-issuance layer, not at the agent layer.
4. **Audit log every token exchange** so the user can replay what the agent spent, by whom, at what prompt.

The UX pattern is more important than the specific tokenization provider. **Take screenshots and build this flow into a demo video; add to your portfolio.**

### Why it matters to you

- **Job lens:** **Agent-payment UX is a brand-new specialty** — fintech + security + ML + UX. The companies hiring: Stripe (Agent Toolkit), Marqeta, Lithic, Privacy.com, every AI agent startup that does commerce. **This is a new hiring lane that didn't exist 60 days ago.**
- **Startup lens:** Three durable wedges — **B2B agent invoicing** (OpenAI Wallet is consumer-only), **multi-party escrow** (agents negotiating on behalf of enterprises), **international / cross-border agent payments** (OpenAI Wallet is US-only for now). All three have 12–18 months before OpenAI is likely to cover them.
- **Insight:** **Biometric-per-transaction is the first real agent-safety UX primitive to ship at consumer scale.** It's easy to criticize OpenAI, hard to build this. Watch whether Anthropic ships a Claude-side equivalent within 90 days (likely tied to Claude Meetings for enterprise commerce).

→ Cross-link: [`01` §3 — ChatGPT Wallet in the Nov cluster](./01-big-lab-moves.md#3-openai-gpt-6-2)

---

## 4. "Benchmark + vertical plugin, released together" is OpenAI's new shipping shape {#4-vertical-bench-plugins}

**What changed (Nov 18–20, 2026):** OpenAI shipped **the Accounting plugin (Nov 18) + MedChemBench (Nov 20)** in the same week.
- Accounting plugin = vertical productized workflow for invoicing, reconciliation, month-end.
- MedChemBench = public benchmark for medicinal chemistry tasks (released alongside expanded academic research program).

**Implication:** OpenAI's new pattern is **ship a vertical plugin + publish the benchmark the plugin was built against**. This gives (a) product validation, (b) enterprise sales ammunition, and (c) a defensive-moat talking point against competitors who ship the same vertical later without the benchmark.

### How to use it this weekend

**If you're building a vertical AI product, the new release shape is:**

1. **Pick one vertical workflow.** Not three. One.
2. **Define a 20–50-task benchmark** that measures *whether the workflow is solved*, not just *whether the model can answer trivia*. Example: for an accounting workflow, each task is a real messy ledger with known correct reconciliation.
3. **Publish both together:** the product + the benchmark. Make the benchmark public and reproducible (a GitHub repo + a Hugging Face dataset).
4. **Include your model's score alongside 3–5 competitors.** This is the credibility step.

This is a **weekend-size project for a small team** and a **highest-signal portfolio artifact** for anyone applying to FDE or applied-ML roles at a lab or a vertical AI startup.

### Why it matters to you

- **Job lens:** Add **"designed and published a public vertical benchmark"** to your résumé. Public benchmarks are rare, labs read them, and the person who built one has a direct line to a hiring manager at OpenAI / Anthropic / Google. **This is one of the few portfolio artifacts with a response rate above 20% to cold applications.**
- **Startup lens:** **Shipping a benchmark with your product is a free distribution channel** — researchers test your benchmark, cite it in papers, and your product name shows up alongside GPT / Claude / Gemini. The marginal cost is one weekend. The marginal upside is an order of magnitude of top-funnel.
- **Insight:** **OpenAI publishing MedChemBench next to a product plug-in signals a new era of eval-driven vertical shipping.** Expect every lab to publish 10–20 vertical benchmarks over the next 12 months (healthcare, finance, legal, engineering). If you want to work at the eval team at a lab, **your audition is a public vertical benchmark on your GitHub**.

→ Cross-link: [`04` §1 — Research benchmarks landed this week](./04-research-progress.md#1-compass)

---

## 5. Pipe-native agents: `git log | llm` + `jq` + routers is the vibe-coding default {#5-pipe-native-agents}

**What's holding (ongoing):** Simon Willison's `llm` + the router shim + Unix pipe discipline continue to be the fastest way to prototype a one-off agent.

**Recipe to internalize:**
```bash
# 1. Audit a repo's recent commit quality
git log --oneline -50 | llm -m claude-fable-5.2 "which of these commits touch auth logic?"

# 2. Route cheaply for dumb tasks
git log --oneline -50 | llm -m gpt-6.2-sol "classify each commit as feature/fix/chore"

# 3. Chain
git log --oneline -500 | \
  llm -m claude-fable-5.2 "list the 10 most risky commits with 1-line reasons" | \
  jq -r '.[] | .sha' | \
  xargs -n1 git show | \
  llm -m claude-fable-5.2 "which of these would you want a code review on?"
```

**Why it still matters:** The $8/$40 flagship floor + `llm` CLI + one afternoon = a working audit tool. **This is the vibe-coding pattern that actually ships**; batch it against your own workflows this weekend before you start a bigger project.

### Why it matters to you

- **Job lens:** **"I pipe `git log` into `llm` to triage code reviews"** is a sentence that demonstrates practitioner literacy. Use it in an FDE interview — it signals that you've internalized the tool.
- **Startup lens:** If your product has a CLI-shaped surface area (anything that's batch, scheduled, or git-native), **support `llm`-style piping by default**. It's a near-zero-cost feature that wins practitioner mindshare.
- **Insight:** **Unix pipes are back as a first-class AI interface** — not notebooks, not chat UIs. Watch for `llm`-style CLIs from Anthropic (already exists), OpenAI (coming), and Google (lagging).

→ Cross-link: [`03` §2 — Routing is the whole game](#2-rubin-kernels)
