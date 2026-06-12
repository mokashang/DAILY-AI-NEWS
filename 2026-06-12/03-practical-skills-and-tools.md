# Practical Skills & Tools — 2026-06-12

`#practical #claude-code #agents #cost #coding-agents #mcp`

Act on at least one of these today.

---

## 1. T-3 to Claude Agent SDK metering — toggle credits TONIGHT. {#1-agent-sdk-t-3}

**The 5-minute fix.** On **Monday June 15**, Claude Agent SDK + `claude -p` + Claude Code GitHub Actions + third-party harnesses (**OpenClaw, Conductor, Jean, Hermes, Zed ACP**) move to a *separate* credit pool, metered at API rates. **If you don't toggle the credit setting, your weekend agent runs will silently fail Monday morning.**

**What stays unchanged.** `claude` interactive terminal sessions, claude.ai web/desktop/mobile, and Cowork stay on existing subscription limits.

**Credits by plan.**
- Pro: **$20/month** Agent SDK credit
- Max 20x: **$200/month**
- Team Premium: **$100/month**

**Tonight's checklist (5 minutes).**
1. Open Claude account → Settings → **Plans & Billing → Agent SDK Usage** → enable "Use included Agent SDK credit." (Otherwise programmatic Claude breaks at 00:00 Pacific Monday.)
2. Add a **monthly budget alert** to prevent overflow from silently billing.
3. Stop optimizing for the subsidy. **Optimize per-token from now on.** Three lever-pulls in order:
   - **Prompt caching** (60–90% input-cost cut; confirm via `cache_read_input_tokens > 0` in your trace) — carries from [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md)
   - **Opus orchestrator + Sonnet worker** team (~40% cheaper than all-Opus) — carries from [2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)
   - **Sonnet 4.6 as default for ≥80% of agent steps**; reserve Opus 4.7 for plan + verify, not execute

**Sources.**
- [Anthropic Support, "Use the Claude Agent SDK with your Claude plan"](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) `[primary]`
- [Claude Code Docs, "Agent SDK overview"](https://code.claude.com/docs/en/agent-sdk/overview) `[primary]`
- [Vantage Point, "Claude Agent SDK Billing Splits June 15: What Teams Must Do"](https://vantagepoint.io/blog/ai/claude-agent-sdk-billing-change-june-15) `[analysis]`
- [Enterprise DNA, "Two Claude Deadlines Hit June 15: What AI Builders Must Do"](https://enterprisedna.co/resources/news/anthropic-claude-june-15-retirements-billing-2026/) `[analysis]`
- [The Planet Tools, "Claude Agent SDK Changes June 15 2026: What Devs..."](https://theplanettools.ai/blog/claude-agent-sdk-billing-model-deprecation-june-15-2026-migration-playbook) `[analysis]`
- [Alex Cloud Star, "Claude June 15 2026 Pricing Changes: Indie Dev Survival Guide"](https://www.alexcloudstar.com/blog/claude-june-2026-pricing-survival-guide/) `[analysis]`

**Why it matters to you.**
- **Job.** A 5-minute audit you can demo on a recruiter call ("here's what I changed when the Agent SDK metering hit"). Cost-awareness is now the *differentiator* among AI Engineer applicants. See [`05` §2](./05-career-and-startup.md#2-reprice).
- **Startup.** Personal billing audit doubles as customer-discovery for the **cost-aware multi-provider router** wedge in [STARTUPS.md](../STARTUPS.md).
- **Insight.** Anthropic's metering migration is the first time a major lab has explicitly separated *interactive* from *agentic* billing. Pattern to expect on OpenAI (Codex) and Google (Gemini API) within 90 days.

`#claude-code #agent-sdk #pricing #cost`

---

## 2. Weekend project (60 min) — reframe the dual-model sanitiser around Tool-DC. {#2-weekend-project}

**Carries from** [2026-05-22/03 §2](../2026-05-22/03-practical-skills-and-tools.md#2-artifact). The sanitiser project keeps the same wire-format but the *interview-pitch* changes after this week.

**Old framing (May 22):** Opus-planner / Sonnet-worker + verify against one real MCP server + per-step cost.

**New framing (today):** add a head-to-head row for **MAI-Code-1-Flash** vs Sonnet 4.6 vs GPT-5.5 Codex at the *same task*, citing **Tool-DC's +25.10% training-free gain on BFCL/ACEBench** ([`04` §1](./04-research-progress.md#1-tool-dc)) as the methodology your verifier follows. **One artifact answers four interview questions:**
1. Orchestration (planner/worker split)
2. Verification (Tool-DC divide-and-conquer + MCP-Atlas grounding)
3. Model selection (4-way head-to-head with measured cost-per-step)
4. Cost-awareness (per-step token-by-model table, after Agent SDK metering)

**Deliverable shape (Sat–Sun).**
- `README.md` — the framing above + a 3-sentence "why" + 4 measured comparison cells
- `evals/` — 5 cases, each on a real MCP server (pick from MCP-Atlas's catalog)
- `cost-trace.csv` — per-task, per-model, per-step token & dollar
- `LICENSE` (MIT) + `demo.gif`

Then **post the README screenshot on X + LinkedIn with a 2-sentence take.** This is the artifact you cite in every Anthropic / Sierra / Decagon application from now through July.

**Sources.**
- [Tool-DC trending paper (Hugging Face Papers)](https://huggingface.co/papers/trending) `[primary]`
- [MCP-Atlas (Scale) reference — see 2026-05-22/04 §1](../2026-05-22/04-research-progress.md#1-real-tool-benchmarks)
- [VoltAgent — awesome-ai-agent-papers (2026 collection)](https://github.com/VoltAgent/awesome-ai-agent-papers) `[aggregator]`

**Why it matters to you.**
- **Job.** Production-grade artifact > resume copy. The Anthropic / OpenAI Solutions / FDE bar in mid-2026 is "show me your eval harness."
- **Startup.** The harness *is* the wedge: "trajectory verifier API (TrajAD-style)" in [STARTUPS.md](../STARTUPS.md) gets one more validation data point from this build.
- **Insight.** The week's deepest practical pattern: **research benchmarks (Tool-DC, MCP-Atlas) and production tooling (Agent SDK, MCP) finally rhyme.** Build at that intersection.

`#weekend-project #portfolio #claude-code #agents #mcp #tool-dc`

---

## 3. Coding-agent decision tree — update for MAI-Code-1 + Copilot Desktop. {#3-coding-agent-decision}

**Decision matrix after Microsoft Build:**

| Use case | Pick | Why |
|---|---|---|
| Day-to-day in VS Code, want max model variety in one IDE | **GitHub Copilot Desktop (preview)** | Picker carries OpenAI + Anthropic + Google models; MAI-Code-1-Flash is sub-Haiku-priced |
| Long-running terminal agents, MCP-native, CLAUDE.md guardrails | **Claude Code** | Still the deepest agent-SDK + sub-agent + hooks story; Anthropic-stack focusing decision |
| OpenAI-shop, async coding via phone, GPT-5.5-codex agents | **OpenAI Codex (mobile + browser)** | Best when the rest of your team is OpenAI-stack |
| Pure speed for `simple_edit`, lowest cost-per-line | **MAI-Code-1-Flash via Copilot picker** | Microsoft is currently price-leader; reassess Q3 |
| Inside JetBrains | **Cursor 3.0 + Codex** | Cursor still owns the JetBrains ergonomics |

**Quick recommendation for *you*.** Stay **Claude Code primary** (per [ME.md](../ME.md) focusing decision — Anthropic agentic stack). Add **Copilot Desktop as the model-picker reference rig** so you can demo the comparison in interviews. Don't switch IDEs.

**Sources.**
- [CNBC, "Microsoft and Google take on Anthropic and OpenAI in AI coding models"](https://www.cnbc.com/2026/06/01/microsoft-and-google-take-on-anthropic-and-openai-in-ai-coding-models.html) `[secondary]`
- [Testing Catalog, "Microsoft Build 2026 recap"](https://www.testingcatalog.com/microsoft-build-2026-recap-from-windows-to-copilot-all-ai/) `[secondary]`

`#coding-agents #claude-code #copilot #cursor #codex #decision-tree`

---

## 4. Prompt-caching reminder — re-confirm before Monday. {#4-prompt-caching}

After tonight's Agent SDK toggle, prompt caching becomes a **direct dollar lever** rather than a marginal optimization. Five-minute confirmation:

```bash
# In your last agent run's trace, grep for:
cache_read_input_tokens
# Should be > 0 on second+ runs of the same context window.
```

If it's zero, your caching isn't hitting. Two common causes:
1. Cache breakpoint not declared (Anthropic requires explicit cache-control headers on the prompt block you want cached).
2. Context drift (a single dynamic value in the cached block invalidates the cache).

**Reference.** Carries from [2026-05-17/03](../2026-05-17/03-practical-skills-and-tools.md).

`#prompt-caching #cost #claude-code`

---

## 5. CLAUDE.md sweep across every active repo. {#5-claude-md}

If you haven't already (per the still-open thread in [ACTIONS.md](../ACTIONS.md) carried from 2026-05-17/03), drop the Karpathy 4-rule `CLAUDE.md` template into every active project root tonight. Three immediate effects under the new metering regime:
1. Cuts token use 20–40% by routing context discipline at the project level.
2. Makes every Claude Code session reproducible on a different machine (interview demo gold).
3. Doubles as documentation when you publish the weekend project's repo.

`#claude-md #karpathy #claude-code #weekend`

---

## Cross-links

- **Cost arithmetic:** [`01` §3](./01-big-lab-moves.md#3-anthropic-revenue) explains *why* Anthropic is metering now.
- **Research that anchors the verifier framing:** [`04` §1](./04-research-progress.md#1-tool-dc)
- **Career angle of cost-awareness:** [`05` §2](./05-career-and-startup.md#2-reprice)
