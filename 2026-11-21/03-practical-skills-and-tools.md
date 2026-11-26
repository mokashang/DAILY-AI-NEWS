# Practical Skills & Tools — 2026-11-21

A hands-on week. Claude Code shipped two point releases that **make Auto Mode the default** and **let hooks actually block actions** (the piece that makes "tests-as-spec" an enforceable workflow, not a convention). llama.cpp hit **v1.0.0** — the headline is a stability contract, not a speed jump — and SGLang held its **first Summit**, launching **v1.0**, a 9-member **Consortium**, and the **Miles v0.2** RL/trainer stack. ⚠️ **OpenAI Evals full shutdown lands Nov 30**; if you have evals there, migrate this week. Simon Willison keeps the pattern going with **`llm openai endpoint add`** (0.37 ergonomics) and a Nov 17 blogmark on **external sandboxes for coding agents** — the natural companion to Claude Code's new blocking hooks. On the AGENTS.md front, OpenAI's Codex best-practices page now treats `AGENTS.md` as **layered, nearest-wins**.

Tags: `#tools #claude-code #mcp #evals #inference #oss`

---

## 1. Claude Code 2.1.327 → 2.1.328: Auto Mode default + hook failures can BLOCK actions {#1-claude-code-2-1-328}

**What happened (2026-11-17 → 2026-11-19):**
- **2.1.327 (Nov 17):**
  - `claude mcp add-json` **reads JSON from stdin** → secret tokens never land in your shell history.
  - **Shell start-up files run before the first Bash approval** (so your `~/.zshrc` env is live before Claude sees your first command). Opt-out: `CLAUDE_CODE_DISABLE_SHELL_HEAD_START=1`.
  - `/status` surfaces **broken files and hooks** in a single pane.
  - `/tui classic` restores the pre-redesign TUI for anyone who preferred it.
  - **VS Code "Add to Chat"** right-click menu.
- **2.1.328 (Nov 19), 140+ changes:**
  - **Auto Mode now DEFAULT** for interactive sessions on **Opus 4.6 / Sonnet 4.6** across Bedrock/Vertex/Foundry.
  - **Hook failures can BLOCK actions.** This is the gate that makes **"tests-as-spec" enforceable, not aspirational** — a `PreToolUse` hook that runs your test suite and exits non-zero will now actually stop Claude from taking the tool call.
  - `CLAUDE_CODE_FORK_SUBAGENT=0` → subagents wait for their subagents instead of forking.
  - Effort-level regression fixed on subagent models over Bedrock/Vertex/Foundry.

**Sources:**
- [Claude Code changelog (primary)](https://code.claude.com/docs/en/changelog) `[primary]`
- [claudekit.io — 2.1.327](https://claudekit.io/en/updates/claude-code-2-1-327/) `[aggregator]`
- [claudekit.io — 2.1.328](https://claudekit.io/en/updates/claude-code-2-1-328/) `[aggregator]`
- [havoptic.com — 2.1.328 breakdown](https://www.havoptic.com/r/claude-code-2.1.328) `[aggregator]`

### Why it matters to you

- **Job lens:** **Hooks that block actions are the FDE-interview material of the quarter.** Build this weekend: a `.claude/hooks/pre-tool-use/` script that runs `pytest` on the current project before any `edit_file` or `shell` tool call, blocks on red, and logs the block to a JSONL you can grep. Commit it. Put the repo link on your résumé. In an FDE interview, the question "how do you keep the agent safe in production" now has a one-line answer: **"I ship blocking pre-tool-use hooks + an audit log."**
- **Startup lens:** Auto Mode default on Opus/Sonnet 4.6 means **the median Claude Code user is now running agent-mode by default**. Any dev-tool startup whose UX assumes "manual-approve every tool call" is already behind. If your product sits in the Claude Code path, two things need to ship in the next 30 days: (a) a **telemetry channel** for Auto Mode runs (what tools fired, with what inputs, with what outcomes), (b) a **budget guard** that interrupts when Auto Mode burns past a configured spend.
- **Insight:** **Blocking hooks are the "pre-commit for agents" primitive.** Just like `.pre-commit-config.yaml` is now universal in Python repos, `.claude/hooks/pre-tool-use/` will be universal in agent-enabled repos by mid-2027. Ship a hook template repo this weekend — the first three well-documented templates in each category (test-runner, secret-scanner, typecheck, cost-guard) will become de facto standards.

→ Cross-link: [`01` §3 — Microsoft Agent Discovery Store](./01-big-lab-moves.md#3-microsoft-ignite) · [`05` §3 — FDE lane](./05-career-and-startup.md#3-fde-still-boom)

---

## 2. llama.cpp v1.0.0 (Nov 13) + SGLang Summit v1.0 + Consortium (Nov 12–13) {#2-llamacpp-sglang}

**What happened:**

**llama.cpp v1.0.0 (Nov 13):**
- First `1.0` tag in the project's history. **The headline is a stability contract, not a throughput jump** — breaking C-API changes will now bump the major version (semver proper).
- Downstream consumers (**Ollama, LM Studio, Jan, LocalAI, KoboldCpp**) get a legitimate procurement signal: enterprise buyers can finally cite semver compliance in due diligence.
- Nightly builds still ship daily; v1.0.0 is the compatibility promise, not a feature freeze.

**SGLang Summit (SF, Nov 12–13):**
- **SGLang v1.0 cutover announced** (tracker open; tag landed a few days post-summit).
- **SGLang Consortium** launched with **9 founding members** — governance layer over the OSS inference stack, similar to the Linux Foundation / CNCF model.
- **Miles v0.2** released — SGLang's RL/trainer-stack companion, now production-usable for RLHF / RLAIF / RL-with-tools pipelines.

**Sources:**
- [llama.cpp — GitHub Releases](https://github.com/ggerganov/llama.cpp/releases) `[primary]`
- [buttondown — llama.cpp hits 1.0, here's what breaks](https://buttondown.com/insiderllm/archive/llamacpp-hits-10-heres-what-breaks/) `[analysis]`
- [eesel.ai — llama.cpp overview post-1.0](https://www.eesel.ai/de/blog/llama-cpp) `[secondary]`
- [LMSYS — SGLang Summit Recap 2026-11-17](https://www.lmsys.org/blog/2026-11-17-sglang-summit-recap) `[primary]`

### Why it matters to you

- **Job lens:** **vLLM vs SGLang vs TensorRT-LLM is a real question in MLE interviews now, and the right answer sounds different after this week.** Say: "vLLM for simple serving + `continuous batching`; **SGLang when RadixAttention + structured decoding + agent-heavy workloads matter**; TensorRT-LLM when you've already committed to NVIDIA + production-grade perf tuning." llama.cpp is the **local / CPU-GPU-mixed path**. Knowing which to pick is table-stakes for inference-infra roles at Together, Fireworks, Baseten, Modal, Anyscale, and any Rubin-era GPU-aware startup.
- **Startup lens:** **The SGLang Consortium is a governance-layer wedge.** Any inference startup can now join or build around the Consortium to earn an "OSS-governed" badge in enterprise procurement — a real differentiator against closed stacks. If your startup serves models today, publish a 1-page compatibility statement ("we pin SGLang v1.0, our fine-tune training uses Miles v0.2, our inference runtime complies with the Consortium's API surface") and send it to your top 20 enterprise prospects within 60 days.
- **Insight:** **Local inference is finally a legitimately procurement-ready option.** llama.cpp 1.0 + Ollama GA + Apple Silicon memory bandwidth means **a $5K Mac Studio can serve an 70B model at useful latency** — which means **a startup can prototype on local hardware without API dependency**. For solo founders and students, this cuts your "burn rate before PMF" by 60–80%.

→ Cross-link: [`02` §4 — Muse Ember open-weight routing tier](./02-new-emerging.md#4-muse-ember)

---

## 3. ⚠️ OpenAI Evals: read-only since Oct 31, full shutdown Nov 30 — migrate this week {#3-openai-evals-shutdown}

**What happened:**
- **OpenAI Evals dashboard** moved to **read-only on 2026-10-31**; **full shutdown lands 2026-11-30**.
- If you have evals in the OpenAI dashboard, **export this week**. The replacement options:
  - **Braintrust** (~$800M valuation after Feb 2026 $80M Series B; commercial SaaS; "LLM observability + eval" positioning)
  - **Langfuse** (ClickHouse-acquired Jan 2026; OSS, self-hostable, production-grade for prompt + trace storage)
  - **promptfoo** (OpenAI-acquired March 2026; still MIT-licensed; CLI-first, YAML-driven, great for CI pipelines)
- **Caveat:** The shutdown date surfaced via a third-party summary; **verify against openai.com/products/release-notes before Friday**.

**Sources:**
- [andrew.ooo — OpenAI Evals alternatives 2026](https://andrew.ooo/answers/openai-evals-alternatives-promptfoo-braintrust-langfuse-2026/) `[secondary]`
- (Primary verification needed: OpenAI release notes)

### Why it matters to you

- **Job lens:** **"I migrated our team off OpenAI Evals before the Nov 30 shutdown"** is a 60-second interview story worth preparing. If you shepherd this migration (even for a single project), you'll touch all three replacement tools — which means you can speak to their trade-offs in any FDE / applied-ML / solutions interview this winter. It's a rare "I did the thing, here's what I'd pick" story that actually shows judgment.
- **Startup lens:** **The OpenAI Evals shutdown is a direct demand pull for one of the three alternatives — probably Langfuse or promptfoo for cost-sensitive teams, Braintrust for well-funded ones.** If you're building eval tooling, this week's moves: (a) ship a one-command **"OpenAI Evals → Langfuse / promptfoo"** importer, (b) publish a comparison table that doesn't oversell your side, (c) offer paid migration consulting to 5 target customers before Nov 30.
- **Insight:** **An eval harness that survives tool migrations is a career asset.** Write yours in a tool-agnostic way — define evals as a YAML + a prompt-template + an `assertEval()` contract, with adapters for each backend. That pattern survives the next three tool shifts in this category.

→ Cross-link: [`04` §6 — Agents construct their own self-improve algorithm](./04-research-progress.md#6-agents-self-improve)

---

## 4. Simon Willison: `llm openai endpoint add` + Nov 17 blogmark on external sandboxes {#4-simon-willison}

**What happened (2026-11-11 → 2026-11-17):**
- **Simon Willison** kept building the `llm` CLI into the pattern-defining tool for individual-developer LLM use.
- **Nov 11:** The 0.37-era command **`llm openai endpoint add`** replaces the old `extra-openai-models.yaml` pattern. Point `llm` at any OpenAI-compatible endpoint — **Together, Fireworks, Groq, DeepInfra, Anyscale, OpenRouter, any self-hosted vLLM/SGLang/llama.cpp** — as a one-liner. **Pattern: `llm` is now your cost-arbitraged router front-end from the terminal.**
- **Nov 17 blogmark:** External sandboxes for coding agents (tagged `sandboxing + webassembly + claude-code`) — notes on how to run Claude Code tools in a sandbox that isn't your actual filesystem.

**Sources:**
- [simonwillison.net — November 2026 posts](https://simonwillison.net/2026/Nov/?page=2) `[primary]`
- [llm docs — 0.37 release notes](https://llm.datasette.io/en/stable/changelog.html) `[primary]`

### Why it matters to you

- **Job lens:** **Set up `llm` on every machine you code on, with endpoints for at least 3 providers.** In an interview, "I keep a 5-provider router in my shell and route by task" is a credibility signal at the exact right abstraction level — technical enough to be real, practical enough to be useful.
- **Startup lens:** Simon's pattern is a **standing demo of what "cost-arbitraged, provider-agnostic" looks like from a user's perspective**. If your product requires lock-in to a single provider, it looks worse than `llm` does. Ship a provider-agnostic path as soon as you have one.
- **Insight:** **The sandboxing blogmark is the natural companion to Claude Code's blocking hooks.** Blocking hooks say "stop if it fails"; sandboxes say "let it fail safely." **The pair is the production pattern.** Build a project this weekend: a WebAssembly-sandboxed shell exposed as an MCP tool, with a pre-tool-use hook that logs every invocation.

→ Cross-link: [`01` §4 — OpenAI jagged-frontier post](./01-big-lab-moves.md#4-openai-cluster)

---

## 5. OpenAI's AGENTS.md pattern formalized; Codex Agents SDK runs Codex as MCP server {#5-agents-md}

**What happened:**
- OpenAI's **Codex best-practices page** now formalizes **`AGENTS.md`** as **layered, nearest-wins** — exactly parallel to `CLAUDE.md`'s loading semantics.
- **Codex Agents SDK** runs Codex as an **MCP server** with `start_conversation` and `continue_conversation` as tools — letting any MCP client treat a Codex session as a tool call.
- For a user already running `CLAUDE.md` + `.claude/skills/`, the clean path is **one canonical rules source that emits both file layouts** (e.g., a `scripts/sync-agent-rules.py` that reads a YAML spec and writes `CLAUDE.md`, `AGENTS.md`, and a Cursor `.cursor/rules/`).

**Sources:**
- [developers.openai.com — Codex best practices](https://developers.openai.com/codex/learn/best-practices.md) `[primary]`
- [developers.openai.com — Codex Agents SDK](https://developers.openai.com/codex/guides/agents-sdk) `[primary]`

### Why it matters to you

- **Job lens:** **Shipping a single-source agent-rules file that cross-compiles to CLAUDE.md + AGENTS.md + Cursor rules is a 2-hour portfolio artifact.** It shows you understand the shape of the ecosystem and you ship the plumbing nobody else does. Put it in your `dotfiles` repo and the interview conversation writes itself.
- **Startup lens:** If your product exposes a tool surface, make sure **it works as an MCP server under both Claude Code and Codex Agents SDK, same day**. OpenAI running Codex as an MCP server validates the entire pattern — treat MCP as the universal integration target, not a Claude-specific one.
- **Insight:** **Agent rules files are the next `.editorconfig` / `.gitignore` / `.pre-commit-config.yaml` layer.** Projects that don't have one will be visibly behind within 6 months. Ship yours as a weekend rule and make it part of the culture of every repo you own.

→ Cross-link: [`01` §1 — ANT IPO comp signal](./01-big-lab-moves.md#1-anthropic-ipo-priced)

---

## 6. Show HN agent-tool pattern this week — confirms the MCP wedge is competitive {#6-show-hn}

**What happened:**
- Multiple **Show HN** posts this week built directly on the MCP-as-portfolio-artifact pattern:
  - **AG2B** — browser-side agent loop via WebMCP (run MCP tools in the browser, not the terminal).
  - **Vet** — coding-agent guard (runs policy checks over agent-proposed diffs before merge).
  - **Sandbox Agent SDK** — generic sandbox-as-MCP-tool with a Python / Node API.
  - **Xalgorix** — open-source AI pentester (agent with structured recon + exploit-suggestion tools).
- All fit the same thesis: **wrap an existing surface as an MCP tool, publish, let the agent ecosystem discover you.**
- Confirmation of the 2026-11-14 edition's claim that **"MCP servers are the #1 portfolio artifact for FDE applications"** — the category is **competitive now, not theoretical**.

**Sources:**
- [Hacker News — Show HN](https://news.ycombinator.com/shownew) `[primary]`

### Why it matters to you

- **Job lens:** **Ship your MCP server THIS WEEKEND, not next.** The category is still rewarding early movers but saturating fast. Target shape: **3 tools, 5 evals, one GIF demo, 50 README lines, publish to npm or PyPI, submit to the MCP registry.** Put the link above the fold on your résumé. Expect at least one recruiter message per week from publishing it.
- **Startup lens:** **"MCP server for X" is now a legitimate seed-stage wedge** if X is (a) a non-trivial data source, (b) a regulated vertical, (c) an existing SaaS with no MCP surface yet. Pick one of the top 100 SaaS tools without an MCP server; build the MCP wrapper + a small eval suite; cold-email their CTO about a partnership. First-mover advantage compounds for the 3–6 months before the SaaS vendor ships their own.
- **Insight:** **The Show HN tempo is the single best market-cadence indicator for AI dev tools.** If two different Show HN posts in a week address the same wedge, the category is open. If five do, it's saturated.

→ Cross-link: [`02` §1 — Model ML template](./02-new-emerging.md#1-model-ml)

---

### Sourcing caveats

- **OpenAI Evals shutdown date (Nov 30):** sourced from a third-party summary. Verify at openai.com/products/release-notes before quoting a hard date to a customer.
- **SGLang v1.0 tag:** announced at the Summit Nov 12–13; the GitHub tag may have landed a few days post-recap. Check the repo releases page before pinning.
- **Simon Willison items:** sourced from simonwillison.net directly; the `llm openai endpoint add` flag name is from his Nov 11 post. Primary and reliable.
