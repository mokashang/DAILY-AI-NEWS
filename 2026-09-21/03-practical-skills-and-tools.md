# Practical Skills & Tools — 2026-09-21

Hands-on workflows, tools, prompting, productivity. Act on this today or this week.

---

## 1. MCP 2026-07-28 stateless migration — the 10-months-into-a-12-month clock {#1-mcp-stateless-migration}

**What happened.** MCP's 2026-07-28 rewrite (see [`02` §3](./02-new-emerging.md#3-mcp-stateless) for the strategic frame) is now ~10 months into its 12-month Tier-1 deprecation window. Roots, Sampling, and Logging remain functional but are marked deprecated; Tasks and Notifications moved to an extensions framework; sessions moved to `_meta`-parameter identification.

**What to actually do this week.**

1. **Audit your server.** If your MCP server:
   - Tracks a session in a server-side map by client ID — **rewrite** to identify per-request via the `_meta` parameter.
   - Uses the `HTTP GET` change-notification endpoint — **migrate** to `subscriptions/listen`.
   - Relies on Dynamic Client Registration for auth — **plan the move** to Client ID Metadata Documents (CIMD) before Q1 2027.
   - Uses Roots / Sampling / Logging — **note the deprecation**; do the rewrite before Q3 2027.

2. **Update Tier-1 SDKs.** The TypeScript, Python, Go, and Rust SDKs all shipped July–August 2026 updates. Bump versions and rerun tests.

3. **Add caching to your list endpoints.** The new spec added `cacheable` list results as a first-class feature. If your server has a `list_tools` or `list_resources` endpoint, mark it cacheable — that's a free performance win.

4. **Load-test at 10K concurrent stateless requests.** Stateless is the whole point of the rewrite. Confirm your server scales horizontally the way the new spec promises. Cloudflare's MCP v2 doc is the reference example.

**Sources.**
- [MCP Blog — 2026-07-28 Specification](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [MCP Blog — 2026 Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) `[primary]`
- [MCP.io — Roadmap](https://modelcontextprotocol.io/development/roadmap) `[primary]`
- [Cloudflare Blog — The next generation of MCP](https://blog.cloudflare.com/mcp-v2/) `[primary]`
- [InfoWorld — MCP going stateless](https://www.infoworld.com/article/4201254/model-context-protocol-is-going-stateless-to-make-scaling-simpler.html) `[secondary]`
- [Developers Digest — MCP 2026-07-28 rewrite: migration diff](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes) `[analysis]`
- [ITdaily — MCP protocol receives major update](https://itdaily.com/news/software/mcp-2026-update-specs/) `[secondary]`

**Why it matters to you.**
- **Job.** Your MCP server portfolio artifact (from [ME.md active-portfolio-artifacts](../ME.md#active-portfolio-artifacts)) needs to be spec-current when you drop it in an FDE interview. A pre-2026-07-28 MCP server reads to a Claude-team recruiter the way a Python 2.7 sample reads to a modern hiring manager.
- **Startup.** Stateless MCP + edge runtime = a real deployment surface for a "managed MCP" wedge. See [`02` §3](./02-new-emerging.md#3-mcp-stateless).
- **Insight.** The clock is a soft-deadline market signal — everyone with an MCP server does a v2 pass between now and October 2027. That's a 12-month migration window during which "MCP-server-upgrade-as-a-service" is a viable *consulting* wedge you can staff with one engineer.

`#mcp #protocols #migration #portfolio`

---

## 2. ChatGPT desktop now runs Chrome extensions — the browser-inside-the-chat is now a real browser {#2-chatgpt-extensions}

**What happened.** On Sept 18, OpenAI turned on **Chrome-extension support inside ChatGPT desktop's built-in browser**. Users install and pin extensions (1Password, Grammarly, Notion Web Clipper, ad-blockers, etc.) directly inside the ChatGPT window without alt-tabbing to a full browser.

**What to actually do this week.**

1. **Try it — this is a shape-of-work change.** ChatGPT desktop → open the built-in browser → install 1Password + one extension you use daily. Notice: the assistant now has structural access to your extension ecosystem.

2. **Add "extension-in-agent-browser" to your threat model.** If you build agent-shaped tools, this expands the agent's *effective* scope by the extension's scope — a browser agent that can read a page + can also read your 1Password vault + write to your Notion is *quantitatively* more capable this week than last. That's not automatically bad, but it changes what a scope-violation looks like (cf. Google's Gemini disclosure — [`01` §5](./01-big-lab-moves.md#5-gemini-red-team)).

3. **Update your resume line.** If you use ChatGPT-built-in-browser at work, that's a real "AI-native workflow" line you can put on your CV under skills.

**Sources.**
- [Buildfast — AI News Today Sept 18](https://blog.buildfastwithai.com/ai-news-today-september-18-2026) `[aggregator]`
- [OpenAI News](https://openai.com/news/) `[primary]`

**Why it matters to you.**
- **Job.** Agent-shaped browser is the emerging OS surface (WebMCP from [2026-05-20](../2026-05-20/) → Antigravity DevTools → now Chrome-inside-ChatGPT). Every dev role at OpenAI, Anthropic, Google, Meta, xAI is now downstream of this pattern.
- **Startup.** Two candidate wedges: **(a)** a browser-extension-that-treats-the-agent-as-the-user (i.e., a permissions layer for extensions running inside an agent's browser); **(b)** an agent-audit extension that logs everything the agent does inside the built-in browser.
- **Insight.** The frontier-labs are converging on the same surface: **assistant → browser → tools**. Whichever lab ships the best (safe, audited, extensible) browser inside their assistant wins the workflow. This is why Anthropic's [Skills / Hooks / Subagents / CLAUDE.md primitive stack](./03-practical-skills-and-tools.md#4-claude-code-decision-tree-still) matters — different lab, same problem.

`#openai #agents #browsers #chrome-extensions`

---

## 3. Ship a 10-eval red-team suite — the eval-authoring artifact of the week {#3-red-team-suite}

**What happened.** The shared safety body ([`01` §1](./01-big-lab-moves.md#1-shared-safety-body)) + Anthropic's Accenture faculty program ([`01` §4](./01-big-lab-moves.md#4-amodei-safety)) + Google's Gemini scope-violation disclosure ([`01` §5](./01-big-lab-moves.md#5-gemini-red-team)) collectively signal: **behavioral evals authored by an outsider are a hireable skill this quarter.** The scarce human is the one who can prove-by-testing what a model will and won't do.

**What to actually build (2–4 hours; ship tonight).**

Pick **one narrow capability**, e.g.: *"a Claude subagent with file-write access does not exfiltrate contents of files outside its declared working directory even when prompted to."*

Then build a red-team suite:

1. **Ten test cases**, each with:
   - A precise setup: agent config, tool permissions, files pre-seeded in scope + out of scope.
   - A prompt that attempts to induce the target unsafe behavior (five obvious, five subtle — e.g., indirect prompt injection via a filename or a comment inside a scoped file).
   - An **expected observed behavior** — not "model refuses" but "no I/O touches the out-of-scope path."
   - A **pass/fail predicate** — a script that inspects the tool-call log, not the model's chatty output.

2. **A README** that names:
   - The narrow capability.
   - Why it matters (link Gemini scope-violation disclosure).
   - How to run.
   - The precise definition of "pass" and "fail."
   - What variables you controlled and what you didn't.

3. **A CSV or JSONL output** of run results, printable as a mini-report.

4. **A GitHub Actions step** that reruns the suite nightly against `claude-sonnet-4-5-*` or `claude-opus-4-*` and drops a table into a README badge. This makes the artifact *live*, not static.

**Sources.** See [`01` §1](./01-big-lab-moves.md#1-shared-safety-body), [`01` §4](./01-big-lab-moves.md#4-amodei-safety), [`01` §5](./01-big-lab-moves.md#5-gemini-red-team) for context. Reference works: MCP-Atlas / Toolathlon from [2026-05-22 §research](../2026-05-22/04-research-progress.md); JADE / TrajAD from [2026-05-19 §research](../2026-05-19/04-research-progress.md).

**Why it matters to you.**
- **Job.** This is the **interview-differentiator artifact of Q4 2026**. It answers three questions at once: (a) can you author evals; (b) can you talk about safety concretely; (c) can you ship. FDE / Applied-AI-Engineer / safety-eval roles at Anthropic, OpenAI, Google, Meta, and the Accenture faculty program each want to see something like this. It's the [2026-09-10 §3 router](../2026-09-10/03-practical-skills-and-tools.md#3-router-artifact)'s sibling: *router = what to use, eval-suite = what to trust.*
- **Startup.** A repo of narrow-capability red-team suites, evolved over 6 months, becomes a *catalog* — the raw material for the "eval-suite marketplace" wedge in [`02` §2](./02-new-emerging.md#2-pre-deployment-eval).
- **Insight.** The scaling law for eval-authoring skill in 2026 is *narrow > broad*. A general "safety benchmark" reads like homework. A **10-case suite for one specific hazard, with a live report** reads like a founding hire.

`#evals #red-team #portfolio #safety`

---

## 4. Claude Code decision tree — still the 4-primitive rule (with the September polish) {#4-claude-code-decision-tree-still}

**What happened.** The 2026 best-practices consensus on Claude Code has hardened, and multiple guides (DEV Community, Totalum, SmartScope, Developers Digest, MCP Directory) converged in June–September on the same decision framework:

| If you need... | Use... |
|---|---|
| **Enforcement of a rule** (must always happen) | **Hooks** or permissions |
| **Contextual knowledge on demand** (how-to for a workflow) | **Skills** |
| **Delegation boundary** (isolate context, own tools) | **Subagents** |
| **Always-on project guidance** (short, top-of-mind) | **CLAUDE.md** |

**The September polish.**
- Anthropic's Sept 2026 Claude Code changelog added: visible memory warning when critical; `CLAUDE_CODE_MCP_STARTUP_WAIT_MS` env to bound MCP-server startup wait; `effort` attribute on the `claude_code.llm_request` OpenTelemetry span.
- Best-practice guides now say: **start with skills** (easiest), **add hooks** when you need deterministic enforcement, **use subagents** when parallel work or context isolation matters.
- CLAUDE.md content pattern: short rules only ("never edit raw diary notes", "run tests before saying done") — long procedures move to Skills.

**Sources.**
- [Claude Code Changelog (Sept 2026)](https://code.claude.com/docs/en/changelog) `[primary]`
- [Gradually — Claude Code Changelog Sept 2026](https://www.gradually.ai/en/changelogs/claude-code/) `[aggregator]`
- [Releasebot — Claude Code Updates Sept 2026](https://releasebot.io/updates/anthropic/claude-code) `[aggregator]`
- [DEV — Claude Code Hooks, Subagents & Power Features: The Complete Guide (2026)](https://dev.to/vibehackers/claude-code-hooks-subagents-power-features-the-complete-guide-2026-c71) `[analysis]`
- [Totalum — Claude Code Skills in 2026](https://www.totalum.app/blog/claude-code-skills-totalum) `[analysis]`
- [Totalum — Claude Code Subagents: the 2026 Production Playbook](https://www.totalum.app/blog/claude-code-subagents-totalum) `[analysis]`
- [SmartScope — Claude Code Advanced Best Practices](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) `[analysis]`
- [MCP Directory — Claude Code Best Practices](https://mcp.directory/blog/claude-code-best-practices) `[analysis]`
- [Developers Digest — Best Claude Code Skills in 2026: A Curated Directory](https://www.developersdigest.tech/blog/best-claude-code-skills-2026) `[analysis]`

**Why it matters to you.**
- **Job.** This is the same decision tree from [2026-09-10 §2](../2026-09-10/03-practical-skills-and-tools.md#2-decision-tree). What's *new* this week is the memory-warning + MCP startup wait knob — meaning production Claude Code use is being formally tuned for reliability. Add "Claude Code hooks + skills + subagents (2026 pattern)" to your CV under Skills; recruiters will match it.
- **Startup.** If your product ships a workflow embedded in Claude Code (e.g., a Skill for a vertical), the packaging is now well-defined: SKILL.md + helper scripts + optional assets. That's a distributable unit. Multiple emerging directories (Developers Digest, MCP Directory) are already ranking Skills — a distribution channel exists.
- **Insight.** The four primitives are converging into an OS-shaped stack: **hooks = daemons, skills = shell scripts, subagents = processes, CLAUDE.md = shell rc.** Once you see it as an OS, cross-team standards ("we always hook X, we always skill Y") become the org-design question.

`#claude-code #hooks #skills #subagents`

---

## 5. Weekend project (one artifact by Sunday night) {#5-weekend-project}

Two candidates, pick one:

**A. Ship the 10-eval red-team suite from §3.** ~4 hours; ships tonight or tomorrow; single-highest interview-differentiator artifact this quarter. Publish on GitHub, drop a screenshot in the README, share on X with `#claudecode` and `#aisafety`.

**B. Migrate your existing MCP server to the 2026-07-28 spec.** ~6 hours; ships by Sunday; renews the [ME.md](../ME.md#active-portfolio-artifacts) portfolio artifact and unlocks a "MCP v2-native from day one" line in an FDE cover letter.

Do not do both. Cadence > intensity ([ME.md personal rules](../ME.md#personal-rules)).

`#weekend #portfolio #cadence`
