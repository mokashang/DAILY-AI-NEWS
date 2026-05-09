# Practical Skills & Tools — 2026-05-09

Hands-on stuff you can act on today. Tools, workflows, prompting, and productivity for builders.

---

## 1. The "Vibe Coding → Agentic Engineering" Discipline (Karpathy at AI Ascent 2026)

**What's new:** On the **one-year anniversary of coining "vibe coding,"** Andrej Karpathy proposed retiring it in favor of **"agentic engineering"** during Sequoia's AI Ascent 2026 keynote. This isn't a rebrand — it's a workflow upgrade.

The Karpathy distinction:
- **Vibe coding** = describe what you want, accept what comes back
- **Agentic engineering** = design the system, specify constraints, set checkpoints, let AI execute the implementation you've already reasoned through

Karpathy's tells about how serious this shift is:
- He says **80% of his own code is now AI-generated**
- He has *"never felt more behind as a programmer"*
- December 2025 was, in his framing, the tipping point where agentic tools moved from "helpful but messy" to consistently producing correct code: *"I can't remember the last time I corrected it."*

**The actual workflow that 2026 senior engineers are running:**
```
1. Architecture pass (human, no AI)
   - sketch the system on paper or tldraw
   - identify the seams, the data flow, the failure modes

2. Spec pass (human + AI conversation)
   - turn the sketch into a written spec the agent can refer back to
   - explicitly list what NOT to do

3. Test scaffolding (AI writes, human reviews)
   - tests come BEFORE code, both for TDD reasons and as guardrails

4. Implementation (AI agent in a loop)
   - agent runs tests, iterates, commits diffs
   - human reviews each diff, never auto-merge

5. Architecture review (human + AI parallel critique)
   - run a separate model session as a critic
   - "what's wrong with this PR" produces different output than the writing model
```

**Sources:**
- [Karpathy — Sequoia Ascent 2026 summary](https://karpathy.bearblog.dev/sequoia-ascent-2026/)
- [YouTube — From Vibe Coding to Agentic Engineering](https://www.youtube.com/watch?v=96jN2OCOfLs)
- [SD Times — Karpathy renames vibe coding](https://sdtimes.com/ai/andrej-karpathy-has-renamed-vibe-coding-heres-what-engineering-leaders-need-to-do-about-it/)
- [Frank's World of Data Science — Karpathy on vibe coding to agentic engineering](https://www.franksworld.com/2026/05/01/andrej-karpathy-on-the-evolution-from-vibe-coding-to-agentic-engineering/)
- [Simon Willison — Vibe coding and agentic engineering](https://simonw.substack.com/) (May 6 post)
- [Heavybit — High Leverage podcast Ep. 9 with Simon Willison](https://www.heavybit.com/library/podcasts/high-leverage/ep-9-the-ai-coding-paradigm-shift-with-simon-willison)

**Insight:** The senior-vs-junior gap in AI productivity (40–50% vs 15–25%) is closing fastest for engineers who treat the LLM **like an over-confident intern with infinite energy** — not like a search engine, not like a peer. The job becomes: write better specs, write better tests, **read every diff**.

---

## 2. Claude Code 2026 Update — What Actually Changed This Week

**What's new (May 5–8):** Anthropic's Code w/ Claude conference plus a quiet point release. The shipped changes that affect daily workflows:

| Feature | What it does | Why you should care |
|---|---|---|
| **Doubled 5-hour limits** (Pro/Max/Team/Enterprise) | Effective immediately for new sessions | Long agentic runs that used to hit the wall now finish |
| **`/resume` ~67% faster on 40MB+ sessions** | Long transcripts load fast again | You can keep one project session running for weeks |
| **Memory leak fixes** | `/usage` no longer leaks ~2GB on big histories | Long sessions stop crashing |
| **SDK fork subagent in non-interactive sessions** | `CLAUDE_CODE_FORK_SUBAGENT=1` | Build CI-grade agent harnesses, run unattended |
| **MCP auto-retry (×3)** on transient startup errors | Less babysitting | Deploy MCP servers without watching logs |
| **Skill folder write protection** | `--dangerously-skip-permissions` no longer prompts on `.claude/{skills,agents,commands}/` | Skills/agents can self-update during long runs |
| **iTerm2 clipboard auto-config** | `/terminal-setup` enables Apps-can-access-clipboard | `/copy` works from tmux on iTerm2 |
| **Opus 4.7 + `xhigh` effort default** | Best for hard coding tasks | Use this on PRs > 200 LoC, leave low/medium for boilerplate |

Plus the bigger Managed Agents announcements (multi-agent orchestration, Outcomes, Dreaming) covered in `01-big-lab-moves.md`.

**The minimum-effective Claude Code config for a CS grad student (2026 edition):**
```bash
# in ~/.claude/settings.json
{
  "model": "claude-opus-4-7",
  "effort": "xhigh",
  "permissions": {
    "allow": ["Bash(git:*)", "Bash(uv:*)", "Bash(pnpm:*)", "Bash(pytest:*)"],
    "ask": ["Bash(rm:*)", "Bash(curl:*)"],
    "deny": ["Bash(sudo:*)"]
  }
}
```

**Sources:**
- [Claude Code Changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
- [What's new — Claude Code Docs](https://code.claude.com/docs/en/whats-new)
- [Releasebot — Anthropic Updates May 2026](https://releasebot.io/updates/anthropic/claude-code)
- [Claudefa.st — Claude Code Changelog 2026](https://claudefa.st/blog/guide/changelog)

**Insight:** If you spend more than 2 hours/day in Claude Code, the `/resume` speedup and rate-limit doubling alone justify the Pro plan price for the rest of the year. The Pro plan is now competitive with Cursor Pro on capability, not just on price.

---

## 3. Claude Managed Agents "Dreaming" — The Practitioner's Take

**What's new:** Claude Managed Agents now do **post-session reflection**. Between active sessions, an agent inspects its previous transcripts, identifies what it missed, and writes:
- **Plain-text learnings** ("this user expects camelCase responses")
- **Structured playbooks** ("for this task type, run X then Y, validate with Z")

These artifacts persist and are referenced in future sessions. Harvey reported a **~6× improvement in task completion** after enabling.

**How to use it intelligently:**
1. **Start with one agent, one workflow.** Don't enable Dreaming across everything; pick one repetitive workflow with clear success/failure signal.
2. **Treat playbooks as code.** Version-control them, code-review them, roll them back.
3. **Set quality gates.** Don't write to long-term memory without a passing eval. Bad playbooks compound.
4. **Use Outcomes alongside Dreaming.** Outcomes give the agent a definition of success during the session; Dreaming uses that definition to learn between sessions. They're a pair.

**The hidden risk:** A bad playbook learned in week 1 will silently bias every future session. **Audit the dream artifacts weekly, like reviewing a junior dev's PRs.**

**Sources:**
- [Claude Managed Agents docs](https://platform.claude.com/docs/en/managed-agents/overview)
- [VentureBeat — Anthropic introduces "dreaming"](https://venturebeat.com/technology/anthropic-introduces-dreaming-a-system-that-lets-ai-agents-learn-from-their-own-mistakes)
- [SiliconANGLE — Claude agents can dream](https://siliconangle.com/2026/05/06/anthropic-letting-claude-agents-dream-dont-sleep-job/)
- [9to5Mac — Three new Managed Agents features](https://9to5mac.com/2026/05/07/anthropic-updates-claude-managed-agents-with-three-new-features/)

**Insight:** "Agent memory engineer" is a real job title now. Whoever owns the playbook cache effectively shapes the agent's behavior more than whoever wrote the original system prompt. **As a portfolio project: build a small Managed Agent for a workflow you actually do (e.g., "weekly literature review of arXiv cs.LG for my research area"), enable Dreaming, and document the playbook evolution over 4 weeks.** That's a resume-magic project — concrete, falsifiable, demonstrates depth.

---

## 4. GitHub Trending This Week — What Builders Are Actually Adopting

**What's hot:**

| Repo | What it is | Why it's trending |
|---|---|---|
| **OpenClaw** | Open-source agent assistant — browses web, fills forms, runs shell, executes code, controls smart home, writes its own skills | **9k → 210k+ stars** in months — the fastest growth ever for an OSS project |
| **pi-mono** (Mario Zechner) | Coding agent CLI + unified LLM API + TUI/web UI + Slack bot + vLLM pods | All-in-one toolkit, **43.9k stars** |
| **DeepSeek-TUI** | Terminal coding agent specialized for DeepSeek V4, 1M-context support | Open-weights frontier in a clean CLI |
| **jcode** (1jehuang) | Code-agent toolkit / framework for testing agents | Trending throughout May |
| **VoltAgent / awesome-ai-agent-papers** | Curated agent research papers 2026 | Single source for keeping up |

**The pattern:** *talk-to-one-model* tools are out. *Team-of-specialized-agents* tools are in. Every trending repo this week is an **agent fleet harness**, not a single chatbot.

**Sources:**
- [Bytebytego — Top AI GitHub Repositories 2026](https://blog.bytebytego.com/p/top-ai-github-repositories-in-2026)
- [Professor Glitch — Top 5 Trending AI GitHub repos May 2026 W18](https://www.askglitch.com/blog/top-5-trending-ai-github-repos-may-2026)
- [AIToolly — jcode trending](https://aitoolly.com/ai-news/article/2026-05-06-jcode-a-new-programming-agent-framework-emerges-as-a-trending-project-on-github)
- [GitHub — caramaschiHG/awesome-ai-agents-2026](https://github.com/caramaschiHG/awesome-ai-agents-2026)
- [GitHub — VoltAgent/awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers)
- [GitHub Trending](https://github.com/trending)

**Insight:** Adoption is moving toward **"vendor-neutral agent harnesses"** — pi-mono and OpenClaw both let you swap the model behind the agent. **As a job candidate, building a small such harness on GitHub is probably the most demonstrative single project you can do in 2026.** It signals: I understand agents, I've thought about provider lock-in, I can package and ship.

---

## 5. Self-Hosted Frontier Stack — Costs After This Week's Releases

The cost frontier moved this week. Updated stack pricing for builders who want to ship without paying frontier-API rates:

| Tier | Setup | $/1M tokens (approx) | When to use |
|---|---|---|---|
| **Frontier API (Anthropic / OpenAI)** | Claude Opus 4.7 / GPT-5.5 | $15 in / $75 out (Opus); $1.25 / $10 (GPT-5.5) | MVP, exploration, customer-facing reliability |
| **Frontier API (Google / xAI)** | Gemini 3.1 Ultra / Grok 4 | ~$3 / $12 typical | Long context (Gemini 3.1 Ultra has 2M-token window) |
| **Open-weights via OpenRouter / DeepInfra** | DeepSeek V4-Pro / Kimi K2.6 | $0.40 / $0.80 typical | Cost-bound production, high volume |
| **Self-hosted** | DeepSeek V4-Flash on 4×H100 | ~$0.20 end-to-end at saturation | >50M tokens/mo, residency or compliance |

**Decision rule (2026 edition):**
- **<10M tokens/mo** → frontier API. Engineering time costs more than tokens.
- **10–50M tokens/mo** → open-weights via OpenRouter. Zero ops, 80% of the cost benefit.
- **>50M tokens/mo with consistent baseline** → self-host with vLLM/SGLang. The unit-economics math now works in your favor.

**Sources:**
- [Hugging Face — DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash)
- [Hugging Face — DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)
- [Artificial Analysis — model pricing](https://artificialanalysis.ai/)
- [LiteLLM](https://litellm.ai/)
- [vLLM Documentation](https://docs.vllm.ai/)
- [SGLang GitHub](https://github.com/sgl-project/sglang)
- [DeepInfra](https://deepinfra.com/)

**Insight:** The biggest practical mistake of 2026 is **over-engineering self-hosting too early**. The OpenRouter middle tier didn't exist 18 months ago and now covers ~95% of the use cases that "self-host for cost" is supposed to solve, with a fraction of the ops overhead. Default to OpenRouter; self-host only when the math is unambiguous.

---

## 6. Three Weekend Projects (Resume-Buildable in 8–16 Hours)

In rough order of "differentiates a 2026 CS grad resume":

1. **A Managed Agent + Dreaming dashboard for your own research workflow.** Pick a workflow you do every week (literature review, paper summary, dataset triage). Build it as a Claude Managed Agent with Outcomes and Dreaming enabled. Show the playbook evolution over 4 weekly runs. Resume bullet: *"Built a self-improving AI research agent — task completion improved from 40% → 85% over 4 weeks via outcome-based prompting and reflective memory."*

2. **A vendor-neutral agent harness in 200 LoC.** Pick LiteLLM as the routing layer. Implement: tools, retries, structured logging, eval harness. Bonus: drop-in swap between Claude Opus 4.7, GPT-5.5, Gemini 3.1, DeepSeek V4. Open-source it. Resume bullet: *"Authored an open-source agent harness with model-provider abstraction, used in production by N teams."*

3. **A "self-hosted DeepSeek V4-Flash + custom MCP server" stack.** Spin up DeepSeek V4-Flash on rented GPU (4×H100 ≈ $4–8/hr). Wire it to Claude Code via a custom MCP server that exposes one specific workflow you actually use. Document the cost-per-task end-to-end. Resume bullet: *"Self-hosted a 284B-parameter open-weights MoE model and integrated it via custom MCP tooling, reducing per-task inference cost by 95% vs API."*

**The README test:** If a recruiter cannot understand what your project does in 30 seconds — GIF, one-sentence pitch, "try it yourself" section — it doesn't count. Build for the recruiter's attention budget, not the technical depth.
