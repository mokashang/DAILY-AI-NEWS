# Practical Skills & Tools — 2026-05-08

Hands-on stuff you can act on today. Tools, workflows, prompting, and productivity for builders.

---

## 1. GPT-5.5 Codex — How to Actually Use the Browser/File/Desktop Agent

**What's new:** Codex with GPT-5.5 can now interact with the **browser, files, docs, and your computer** as one continuous workflow. 400K context, Fast mode (1.5× speed for 2.5× cost), multi-step planning with self-checking.

**A workflow that didn't exist 3 months ago — "QA agent with screenshots":**
```
Task: "Sign up for our free trial, complete onboarding,
       then verify the dashboard renders correctly.
       Take screenshots at each step."

Codex with browser use will:
1. Open your sign-up page
2. Fill in form fields based on test data
3. Solve any 2FA via the terminal-fed mailbox tool
4. Click through onboarding screens
5. Capture screenshots at each step
6. Compare against your design spec, flag mismatches
```

**The 3 modes you should learn:**
1. **Codex CLI** (terminal) — best for scripted automation, CI integration, file manipulation
2. **Codex Web** (browser) — best for "I have a vague idea, code with me" sessions
3. **Codex IDE** (VS Code/Cursor extension) — best for in-flight editing on existing repos

**When to flip Fast mode on:** Iterating on a known pattern (you know what you want, just need it generated). Don't use Fast mode for novel architecture decisions — the slower, more deliberate response is worth the wait.

**Sources:**
- [OpenAI — Introducing GPT-5.5](https://openai.com/index/introducing-gpt-5-5/)
- [OpenAI Codex Changelog](https://developers.openai.com/codex/changelog)
- [Lushbinary — GPT-5.5 Codex autonomous coding agents guide](https://lushbinary.com/blog/gpt-5-5-codex-autonomous-coding-agents-guide/)
- [MindStudio — How to use GPT-5.5 in Codex for agentic tasks](https://www.mindstudio.ai/blog/how-to-use-gpt-5-5-codex-agentic-tasks)
- [NVIDIA Blog — GPT-5.5 powers Codex](https://blogs.nvidia.com/blog/openai-codex-gpt-5-5-ai-agents/)

**Insight:** Codex with browser use = **automated end-to-end testing without writing a single Playwright/Cypress script**. For a startup, this collapses the QA function to one engineer + an agent. As a job candidate, knowing how to set this up is a portfolio differentiator.

---

## 2. Claude Code MCP — The 2026 Configuration Playbook

**The lesson the community learned the hard way:** A bloated MCP tool list slows the agent down and increases the chance it picks the wrong tool. **5–6 well-chosen servers** beats 20 random ones.

**The minimal-viable starting set for a developer:**

| Server | Why | Scope |
|---|---|---|
| **filesystem** | Local read/write | Project |
| **github** | PR/issue/code search | User |
| **linear/jira** | Tickets and roadmap | User |
| **postgres / sqlite** | DB queries (read-only user) | Project |
| **slack** | Team comms search | User |
| **sentry / datadog** | Error/perf data | Project |

**Configuration scope rule:**
- **User-level scope** for stable, cross-project tools (GitHub, Slack, Linear, filesystem)
- **Project-level scope** for project-specific resources (DB, monitoring, project APIs)

**Security defaults that experienced users actually follow:**
- DB users: **read-only** unless you literally need writes
- API tokens: **fine-grained, minimal scopes**
- File access: **scoped to the project directory**, never the home directory
- Never give an MCP server more access than you'd give a junior contractor

**Debugging when an MCP server breaks:**
```bash
claude mcp list           # see all registered servers
claude mcp test <name>    # verify a single server
# tail Claude Code logs   # check stderr from server processes
```

**Sources:**
- [Claude Code MCP Docs](https://code.claude.com/docs/en/mcp)
- [Nimbalyst — Claude Code MCP setup 2026](https://nimbalyst.com/blog/claude-code-mcp-setup/)
- [Generect — Ultimate guide to Claude MCP servers 2026](https://generect.com/blog/claude-mcp/)
- [Toolradar — Best MCP servers for Claude Code 2026](https://toolradar.com/blog/best-mcp-servers-claude-code)
- [DeployHQ — Best MCP servers for web developers](https://www.deployhq.com/blog/6-must-have-mcp-servers-for-web-developers-in-2025)
- [MindStudio — Using MCP servers with Claude Code](https://www.mindstudio.ai/blog/how-to-use-mcp-servers-with-claude-code)

**Insight:** "Building a custom MCP server for [your job/research workflow]" is one of the highest-signal portfolio projects in 2026. It demonstrates: (1) you understand agent architecture, (2) you can ship infrastructure, (3) you've thought about security and scope. Pick a real workflow you do daily — calendar, scheduling, dataset access, internal tool — and write an MCP server for it.

---

## 3. Multi-Agent Framework Decision Matrix — When to Use What

The three production frameworks dominate 2026. **They are not interchangeable.** Pick wrong and you'll rewrite.

| Framework | Use When | Avoid When |
|---|---|---|
| **LangGraph** | Complex conditional flows, branching workflows, long-running stateful agents that need to pause/resume, full control over execution graph | You want fast prototyping; you don't need explicit graph control |
| **CrewAI** | Role-based teams ("researcher + writer + critic"), 20-line prototypes, agents that mirror real org structures | Complex non-linear workflows, deep state management |
| **AutoGen** | Conversational multi-agent collaboration, human-in-the-loop, Microsoft-stack environments | Pure pipeline automation, single-agent tasks |

**The 30-second test for picking:**
- "I want to ship a prototype this weekend" → **CrewAI** (lowest learning curve, role-based DSL)
- "I have a complex production workflow with conditional branches" → **LangGraph** (graph-based, explicit control)
- "I want agents to collaborate conversationally with a human in the loop" → **AutoGen**

**Production data point:** 86% of copilot spending ($7.2B) goes to agent-based systems; **70%+ of new AI projects in 2026 use orchestration frameworks**. This is no longer a research toy.

**Sources:**
- [DataCamp — CrewAI vs LangGraph vs AutoGen](https://www.datacamp.com/tutorial/crewai-vs-langgraph-vs-autogen)
- [Iterathon — Agent orchestration 2026 guide](https://iterathon.tech/blog/ai-agent-orchestration-frameworks-2026)
- [Dev.to — Multi-agent AI in 2026](https://dev.to/ottoaria/multi-agent-ai-in-2026-build-production-systems-with-crewai-langgraph-autogen-5e40)
- [GitHub — CrewAI](https://github.com/crewaiinc/crewai)
- [Gurusup — Best multi-agent frameworks 2026](https://gurusup.com/blog/best-multi-agent-frameworks-2026)

**Insight:** Most failed agent projects in 2026 picked the wrong framework for the workflow. Spend 2 hours on a paper prototype of the agent topology *before* writing code. Map: agents, their tools, decision points, state. Then choose the framework that maps cleanly to your topology.

---

## 4. The "Self-Hosted Frontier Model" Stack — Cheap Inference for Builders

DeepSeek V4-Flash is the first **frontier-quality, MIT-licensed, multi-GPU-runnable** model. Here's the practical setup if you want to ship without paying frontier-API rates.

**The minimal stack:**
| Layer | Tool | Notes |
|---|---|---|
| Model | DeepSeek-V4-Flash | 284B total / 13B active, MIT license |
| Serving | vLLM or SGLang | Best throughput for MoE models |
| Hardware | 4×H100 or 8×A100 (or Huawei Ascend) | $20–60K capex or $4–8/hr cloud |
| Quantization | FP8 or INT4 (AWQ/GPTQ) | Drops VRAM ~50% with minimal quality loss |
| Frontend | LiteLLM | Drop-in OpenAI-compatible API for your existing code |

**Cost comparison (back-of-envelope, your mileage will vary):**
- GPT-5.5 API: ~$1.25 / 1M input + $10 / 1M output tokens
- Claude Opus 4.7 API: ~$15 / 1M input + $75 / 1M output
- **DeepSeek V4-Flash self-hosted at scale: ~$0.20 / 1M tokens** end-to-end if you saturate the GPU
- **DeepSeek V4-Flash on DeepInfra/Together: ~$0.40 / 1M input + $0.80 / 1M output**

**When self-hosting pays off:** You're processing >50M tokens/month or have data-residency requirements.

**When it doesn't:** You're in MVP/discovery mode, traffic is bursty, or you don't have someone on the team who can debug a CUDA OOM at 3am.

**Sources:**
- [Hugging Face — DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash)
- [DeepInfra — DeepSeek-V4-Pro demo](https://deepinfra.com/deepseek-ai/DeepSeek-V4-Pro)
- [vLLM Documentation](https://docs.vllm.ai/)
- [SGLang GitHub](https://github.com/sgl-project/sglang)
- [LiteLLM](https://litellm.ai/)

**Insight:** The "build defensibly" advice for AI startups in 2026 boils down to: **use frontier APIs to get to product-market fit, then drop down to self-hosted DeepSeek/Llama for unit economics**. Plan the architecture migration on day one — design your code to be model-provider-agnostic via LiteLLM.

---

## 5. The "Vibe Coding" Counter-Discipline — How Senior Engineers Actually Use AI in 2026

**The data nobody tells you:**
- Senior engineers (3+ years) get **40–50% productivity gain** from AI tools
- Junior engineers get **15–25%**
- Some studies show experienced engineers are **slower with AI on novel/complex tasks** (METR study) — they overestimate AI's reliability and waste cycles validating

**What senior engineers do differently:**
1. **Architecture first, agent second** — they decide the structure, then ask the agent to fill it
2. **Read every diff** — never accept code blindly; treat AI output like a junior PR
3. **Give the agent strict tests upfront** — "here's the failing test, make it pass" beats "implement this feature"
4. **Use multiple models in parallel** — `/best-of-n` in Cursor, or run Claude + GPT-5.5 + Gemini 3.1 in three terminals
5. **Specialize agents by task** — Claude for refactoring, GPT-5.5 for new feature scaffolding, DeepSeek for repetitive boilerplate

**The 2026 anti-pattern to avoid:** "Pure vibe coding" on production code. AI co-authored code has **2.74× more security vulnerabilities** and **75% more misconfigurations** than human-written code (CodeRabbit analysis of 470 OSS PRs).

**Concrete practices that close the gap:**
- Always include in your prompt: "validate all inputs, encrypt secrets, parameterize SQL, no eval()"
- Run **CodeQL or Semgrep on every AI PR** automatically — catches the vulnerability classes that AI introduces most often
- Treat AI as a junior engineer: trust verification, not assertion

**Sources:**
- [Simon Willison's Weblog](https://simonwillison.net/) (regular vibe coding analysis)
- [METR — productivity study](https://metr.org/) (AI tools and developer productivity)
- [CodeRabbit](https://www.coderabbit.ai/) (AI-assisted PR review data)
- [ACM Technology Policy Council Vibe Coding Statement](https://www.acm.org/)

**Insight:** "How do you balance speed with code quality when using AI?" is now a standard interview question for SDE/MLE roles. Know your answer. The good answer is *not* "I never use AI." The good answer is "AI for X, manual for Y, here's exactly when I draw the line and why."

---

## 6. Weekend Project Ideas (Resume-Buildable in 8–16 Hours)

Pick one. Ship it. Put a link in your resume. In order of "actually impressive in 2026":

1. **Custom MCP server for a real workflow** — your university's library API, your research-data warehouse, a niche service you use daily. (See section 2.)
2. **Agent that automates a tedious task you actually do weekly** — bonus if you can show before/after time logs. Resume bullet: "Automated [task] reducing weekly time from 4h to 12min."
3. **Self-hosted DeepSeek V4-Flash with a real interface** — fork an open-source ChatGPT clone, point it at your local model, deploy on your own GPU. Demonstrates infra + ML stack.
4. **A `/best-of-n`-style agent harness** — runs the same coding task across 3 models and shows differences. Open-source it on GitHub.
5. **Fine-tuned LoRA on a domain you know** — medical, legal, finance, gaming — pair with a clean RAG eval harness. The eval harness is the resume-magic, not the LoRA.

**The README test:** If a recruiter cannot understand what your project does in 30 seconds from your README, it doesn't count. Add a GIF, a "what it does in one sentence," and a "try it yourself" section.
