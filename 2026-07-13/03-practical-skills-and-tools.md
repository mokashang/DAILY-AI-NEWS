# Practical Skills & Tools — 2026-07-13

Hands-on ships you can do this week. This week's shape: **the three big model families all shipped subagent/orchestration primitives**, which means the *cross-lab* routing skill went from "nice to have" to "the interview signal." Five practical items — all doable in an evening — plus one deadline.

Tags: `#practical #claude-code #mcp #routing #voice #deepseek`

---

## 1. Claude Code + MCP hygiene — the 4-rule setup that scales past the demo {#1-mcp-hygiene}

**What's new:** the **community consensus on MCP-server sanity in Claude Code has hardened** as of July 2026 — and it directly reduces cost, latency, and permission-prompt friction. Also: **Claude Code just shipped auto-mode by default on Bedrock/Vertex/Foundry**, a **built-in browser on desktop**, and **monthly recap + focus settings** ([`support.claude.com` release notes](https://support.claude.com/en/articles/12138966-release-notes)).

**The 4-rule setup:**

1. **Cap at 3–6 MCP servers.** Every server adds tool defs to context and widens the credential surface. **Start with GitHub + one or two project-specific servers**; add **Context7** if you frequently work across unfamiliar stacks. Beyond ~6 servers, routing quality degrades.
2. **Enable on-demand tool search.** Set `ENABLE_TOOL_SEARCH=true` so large tool sets are *searched* instead of *dumped* into context. This is the single biggest context-window save if you use many MCP tools.
3. **Put path-specific rules in `.claude/rules/`.** Files there only load when Claude touches matching paths — keeps global `CLAUDE.md` short while giving hot paths their own guidance.
4. **Prefer CLI over MCP when one command wins.** For `gh`, `gcloud`, `aws`, `kubectl` — the CLI is faster, has better auth semantics, and doesn't consume tool-definition context.

**Two more:** **disable unused MCP servers with `/mcp`** on a per-session basis (they cost you every turn), and **for any Claude Code invocation in CI, set a dollar cap + a fallback model** — silent runaways are the #1 CI-billing incident pattern.

**Sources:**
- [Nimbalyst — Best MCP Servers for Claude Code in 2026 (Ranked and Tested)](https://nimbalyst.com/blog/best-claude-code-mcp-servers/) `[analysis]`
- [Gist (septimlabs) — 5 MCP servers every Claude Code user should know in 2026](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) `[practitioner]`
- [Totalum — Best MCP Servers in 2026: 12 Picks for Claude Code, Cursor, and Codex](https://www.totalum.app/blog/best-mcp-servers-2026) `[analysis]`
- [Clarista — Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) `[analysis]`
- [Computing for Geeks — Claude Code Cheat Sheet 2026](https://computingforgeeks.com/claude-code-cheat-sheet/) `[practitioner]`
- [Claude Help Center — Release notes](https://support.claude.com/en/articles/12138966-release-notes) `[primary]`

### Do this tonight (30 min)
- `pip install -U claude-code` (or `npm i -g @anthropic-ai/claude-code`) and `claude --version` to confirm you're current.
- Audit your **~/.claude/mcp.json**: remove or comment out any server you haven't invoked in the last two weeks.
- Add `ENABLE_TOOL_SEARCH=true` to your shell (`.zshrc` / `.bashrc`).
- Move any path-specific "always X in this dir" rule from CLAUDE.md into `.claude/rules/<glob>.md`.
- Commit a `.claude/README.md` documenting your **6-or-fewer MCP profile** — this becomes a portfolio artifact for FDE interviews ("here's how I keep an agent stack fast at scale").

### Why it matters to you
- **Job lens:** Interviewers at Anthropic/OpenAI/vertical-AI startups now regularly ask "how do you keep an agent stack fast in production?" — this profile *is* the answer. Push it to a public repo.
- **Startup lens:** Every SaaS you'd build on top of Claude Code inherits these constraints; write the setup script as **`init-agent-repo`** and you have a small dev-tool wedge.

---

## 2. Cross-lab model routing — the new resume line, priced in {#2-routing}

**What's new:** with **GPT-5.6 Luna/Terra/Sol**, **Muse Spark 1.1**, **Gemini 3.5-Flash / 3.5-Pro (target Thu)**, **Claude Sonnet-4.6/Opus-4.8/Fable-5** all shipping subagent-capable modes, the practical question is **which model per role, at what cost**. Prices per M tokens (input / output):

| Tier | Model | In | Out | Best for |
|---|---|---|---|---|
| Fast/free | GPT-5.6 Luna | $1 | $6 | High-volume simple tasks, chat |
| Fast/free | Gemini 3.5 Flash | $1.50 | $9 | Long-context batch, multimodal in |
| Fast/paid | Muse Spark 1.1 | $1.25 | $4.25 | **Parallel tool-use subagent** (MCP-Atlas 88.1) |
| Mid | GPT-5.6 Terra | $2.50 | $15 | Cost-controlled reliable workhorse |
| Mid | Claude Sonnet-4.6 | $3 | $15 | Verification / eval loops |
| Frontier | GPT-5.6 Sol | $5 | $30 | Long-horizon coding (54% token-eff.) |
| Frontier | Claude Opus 4.8 | $15 | $75 | Orchestrator / high-stakes reasoning |
| Frontier | Gemini 3.5 Pro (rumored) | $15 | $60 | 2M-ctx tasks (if the leak holds) |

**Two shipping patterns worth building portfolio around:**

1. **Opus-orchestrator + Muse-subagent for tool-heavy work.** Muse Spark 1.1's MCP-Atlas 88.1 substantially beats Opus 4.8 on tool-selection accuracy; Opus wins on plan quality. **Route: Opus plans → Muse-Spark parallel subagents execute → Opus verifies.** Expected saving vs all-Opus: **~50%**.
2. **Sol-orchestrator + Terra-worker for coding.** With Sol's 54% token efficiency, a single-family GPT stack now competes with cross-lab routing on **pure-coding** workflows. **Route: Sol plans + reviews → Terra implements.** Expected saving vs all-Sol: **~40%**.

**Sources:**
- [OpenAI — Previewing GPT-5.6 Sol pricing](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [Meta AI Blog — Muse Spark 1.1 pricing + benchmarks](https://ai.meta.com/blog/introducing-muse-spark-meta-model-api/) `[primary]`
- [MarkTechPost — Muse Spark 1.1 benchmarks (MCP Atlas / JobBench / HLE-tools / Finance Agent v2)](https://www.marktechpost.com/2026/07/09/meta-superintelligence-labs-releases-muse-spark-1-1/) `[secondary]`
- [Artificial Analysis](https://artificialanalysis.ai/) `[analysis]`

### Do this week (2 hrs)
- Add a **`ROUTING.md`** to your public agent-project repo showing model choice per role with the **cost estimate per call**. This is the single most legible artifact for FDE/Solutions interviews right now.
- Instrument one existing agent with **per-step model + cost logging** (see [2026-05-22/03 §1 cost-tracking](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)).
- Publish a screenshot: **"same task, three routing configs, X% cost delta, Y% quality delta."**

### Why it matters to you
- **Job lens:** This is the *exact* skill FDE/Solutions Engineer interviews test now. Portfolio artifact > resume line.
- **Insight:** Model prices will keep drifting; the *skill* is the pattern of **making a routing decision defensible with numbers**. That's transferable across every price change.

---

## 3. GPT-Live — build one full-duplex voice demo this weekend {#3-gpt-live}

**What's new:** **GPT-Live-1** ships full-duplex voice — it **listens while it speaks**, making many decisions per second on whether to talk / pause / interrupt / call a tool. **GPT-Live-1-mini is the free default** across ChatGPT. Nine remastered voices.

**Why this is worth an evening:** voice agents were the underbuilt category of Q2 2026 (see [2026-05-13 Wispr Flow $2B](../2026-05-13/)). GPT-Live drops the barrier to a shipping voice-agent demo from *"multi-week integration"* to *"an afternoon."*

**Build spec (3–4 hours):**
- **App:** live coding-pair — you talk through a problem, GPT-Live listens, offers suggestions, **interrupts itself when you speak**, calls a `run_tests` tool between statements.
- **Stack:** OpenAI Realtime / Live API (GPT-Live-1-mini for cost) + a single MCP tool for test running + a whisper-loop for "was it useful?" feedback capture.
- **Portfolio output:** a **60-second screen recording** posted to LinkedIn + a **repo with the barge-in logic isolated in one file** (`interrupt_policy.py`) that a hiring manager can read in 5 min.

**Sources:**
- [OpenAI — Previewing GPT-5.6 Sol / GPT-Live](https://openai.com/index/previewing-gpt-5-6-sol/) `[primary]`
- [TechCrunch — OpenAI launches its new family of models with GPT-5.6](https://techcrunch.com/2026/07/09/openai-launches-its-new-family-of-models-with-gpt-5-6/) `[secondary]`
- [Axios — OpenAI releases GPT-5.6](https://www.axios.com/2026/07/09/ai-openai-gpt-release) `[secondary]`

### Why it matters to you
- **Job lens:** Voice-agent product managers and eng leads (Sierra, Decagon, Cognigy, PolyAI, Voxjar) are hiring; a real full-duplex demo is a hard-to-fake proof point.
- **Startup lens:** Every vertical CX product built on old TTS + STT + turn-taking now has a **rebuild opportunity** on top of GPT-Live. If you have any customer-service or intake-workflow domain expertise, the wedge is open.

---

## 4. DeepSeek migration — hard cutoff **July 24, 15:59 UTC** (T-11 days) {#4-deepseek}

**What's happening:** DeepSeek is **retiring `deepseek-chat` and `deepseek-reasoner`** on **July 24, 2026, 15:59 UTC**. After that timestamp, both model names return errors. Migration is a **one-line change** — swap `model=deepseek-chat` for `model=deepseek-v4-flash` or `model=deepseek-v4-pro`.

**The trap to avoid:** `deepseek-reasoner` currently **maps to `deepseek-v4-flash` (thinking mode)**, **NOT to `deepseek-v4-pro`**. If your workload is heavy reasoning, the default alias migration silently downgrades you to **Flash-tier reasoning at Flash prices**. Explicitly remap to `deepseek-v4-pro` if you need Pro-tier reasoning.

**Sources:**
- [DEV Community — DeepSeek V4 API Migration Guide: Everything Before the July 24, 2026 Deadline](https://dev.to/agdex_ai/deepseek-v4-api-migration-guide-everything-before-the-july-24-2026-deadline-4m30) `[practitioner]`
- [Developers Digest — DeepSeek Retires deepseek-chat and deepseek-reasoner on July 24](https://www.developersdigest.tech/blog/deepseek-chat-to-v4-migration-guide) `[analysis]`
- [Byteiota — DeepSeek Retires deepseek-chat July 24: Migrate Now](https://byteiota.com/deepseek-api-migration-july-2026/) `[analysis]`
- [DeepSeek — API Docs — V4 Preview](https://api-docs.deepseek.com/news/news260424/) `[primary]`

### Do this today (10 min)
- `grep -r "deepseek-chat\|deepseek-reasoner" .` in your projects.
- If any hit: choose **v4-pro** (heavy reasoning) or **v4-flash** (chat / cost-first).
- Also revisit the geo-routing note in §5 below — the China export-controls thread may make DeepSeek migration academic in 3–6 months.

### Why it matters to you
- **Job lens:** Small item, but silent downgrades in a portfolio project during an interview show is *awful*.

---

## 5. Add a geo-fallback line to your ROUTING.md {#5-routing-geo}

**What's new:** The **China overseas-AI-model export-controls story** ([`02` §2](./02-new-emerging.md#2-china-controls)) makes it worth adding a single line to your routing config: **any Chinese frontier model has a *US/EU-safe fallback* named upfront**.

**Suggested pattern (drop in your ROUTING.md):**

```yaml
# geo-fallback policy (defensive routing under 2026 export-controls uncertainty)
qwen-2.5-max        -> fallback: gpt-5.6-terra
kimi-k2.6           -> fallback: claude-sonnet-4.6
deepseek-v4-pro     -> fallback: gpt-5.6-sol
glm-4.5             -> fallback: gemini-3.5-flash
default policy      -> if region in {us-east, eu-west}, use fallback for any zh-* model
```

This is a **10-minute change** that turns a policy risk into a documented artifact. Enterprise buyers (and hiring managers) read it as maturity.

**Sources:**
- [Yahoo Finance / Reuters — Beijing looking at curbing overseas access](https://finance.yahoo.com/technology/ai/articles/exclusive-beijing-looking-curbing-overseas-101644780.html) `[primary]`
- [Asia Business Outlook — Beijing weighs curbs on overseas access](https://www.asiabusinessoutlook.com/news/beijing-weighs-curbs-on-overseas-access-to-china-s-top-ai-models-nwid-12159.html) `[secondary]`

### Why it matters to you
- **Job lens:** Compliance-aware routing is an under-priced FDE skill in July 2026. First to build a portfolio artifact on it wins the interview signal.
- **Startup lens:** A **routing SDK with geo-policy + fallback + latency-aware failover** is a real wedge that fits between your customers and every model provider. That's a $10M–$50M seed thesis right now.
