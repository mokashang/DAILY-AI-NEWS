# New & Emerging — 2026-05-06

New models, startups, tools, funding rounds, and paradigm shifts that just landed on the radar.

---

## 1. Cursor 3.0 — The IDE Is Now a Multi-Agent Operating System

**What happened:** Cursor shipped version 3.0 on April 2, 2026, fundamentally changing what an IDE is. The headline feature is the **Agents Window** — you can now run many AI agents in **parallel** across different repos and environments: locally, in git worktrees, on remote SSH, and in the cloud.

New in May 2026 updates:
- **Async multitasking**: Background agents run while you work on something else
- **`/best-of-n` command**: Runs the same task in parallel across multiple models in isolated worktrees, then compares outcomes side-by-side
- **Multi-root workspaces**: Cross-repo changes in one session
- **Tiled layout**: Split view to manage multiple live agents simultaneously

Cursor is reportedly at $2B+ annualized revenue, valued at $29.3B (raised November 2025), with rumors of talks at a $50B valuation.

**Sources:**
- [Cursor 3.0 Changelog](https://cursor.com/changelog/3-0)
- [Cursor Blog — Meet the new Cursor](https://cursor.com/blog/cursor-3)
- [InfoQ — Cursor 3 agent-first interface](https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/)
- [DataCamp — What is Cursor 3?](https://www.datacamp.com/blog/cursor-3)
- [Releasebot — Cursor May 2026 updates](https://releasebot.io/updates/cursor)

**Why it matters to you:**
- **Immediately actionable:** If you use Cursor, upgrade now and learn the Agents Window. The `/best-of-n` command is genuinely novel — running the same feature implementation across Claude, GPT, and Gemini and comparing results is a workflow that didn't exist 60 days ago.
- **Startup signal:** A code editor just became one of the most valuable dev tools companies ever built at $29–50B. The lesson: the interface layer on top of commodity AI can capture enormous value. Think "Cursor for X" in your target domain.
- **Interview signal:** Knowing how to orchestrate multiple agents in parallel, manage worktrees, and run comparative agent evals is a differentiating skill for MLE/SDE interviews in 2026.

---

## 2. Google "Remy" — Personal AI Agent Coming to Gemini

**What happened:** Google is dogfooding "Remy" internally — a 24/7 personal AI agent embedded in Gemini that takes autonomous actions across your digital life. Connected to Gmail, Calendar, Docs, Drive, GitHub, Spotify, WhatsApp, Google Home, and Android utilities. Not just answering questions — scheduling meetings, managing tasks, responding to messages.

Remy is Google's direct response to **OpenClaw**, the personal agent that went viral in early 2026, prompting Sam Altman to hire its creator for OpenAI's personal agent team.

Meta is building "Hatch" on the same playbook (internal testing by end of June).

**Sources:**
- [AI News — Remy agent](https://www.artificialintelligence-news.com/news/google-remy-ai-agent-gemini-user-control/)
- [eWeek — Gemini Remy](https://www.eweek.com/news/google-gemini-remy-ai-agent/)
- [IT Pro — Remy vs OpenClaw](https://www.itpro.com/technology/artificial-intelligence/google-is-building-its-own-openclaw-alternative-remy-elevates-the-gemini-app-into-a-true-assistant)
- [The Decoder — Google and Meta race on personal agents](https://the-decoder.com/google-and-meta-race-to-build-personal-ai-agents-as-anthropic-and-openai-pull-further-ahead/)

**Why it matters to you:**
- The personal agent race (Google Remy, OpenAI, Meta Hatch, Apple) is the new mobile OS race. Whoever owns the agent layer owns the relationship above all other apps.
- As a **startup founder**: which domain problems will the general personal agent *not* solve well? Deep vertical expertise (medical, legal, scientific, engineering-specific) will remain your wedge.

---

## 3. Rhoda AI — $450M Series A for Robotic Intelligence via Video Prediction

**What happened:** Rhoda AI publicly launched with **$450 million in Series A funding**, unveiling its **FutureVision** platform — a robotic intelligence system built on video-predictive control. The system predicts future video frames to plan and execute robot actions, rather than relying on traditional state-space models.

**Sources:**
- [Crescendo AI — VC investment deals](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups)
- [AI Funding Tracker — startup news today](https://aifundingtracker.com/ai-startup-funding-news-today/)

**Why it matters to you:**
- Video-predictive control for robotics is a distinct approach from the dominant behavior-cloning paradigm. If it works at scale, it generalizes better to unseen environments without massive labeled data.
- The $450M Series A at *launch* shows that robotics + embodied AI continues to attract capital at extraordinary levels. Physical AI is the next frontier after software agents.

---

## 4. Standard Intelligence — $75M, Model That Controls Software by Watching Video

**What happened:** Standard Intelligence raised **$75 million** for **FDM-1** (Foundation Decision Model), a model that learns to control software by watching demonstration videos — no code, no API calls, just video. It observes, infers intent, and replicates actions across any software interface.

**Sources:**
- [AI Funding Tracker — startup news](https://aifundingtracker.com/ai-startup-funding-news-today/)
- [Blog.mean.ceo — AI startup funding news May 2026](https://blog.mean.ceo/ai-startup-funding-news-may-2026/)

**Why it matters to you:**
- A model that can operate *any* software GUI by watching videos removes the need for API integrations entirely. This is a different architecture than MCP-style tool-calling and could be more generalized.
- Startup angle: if this works, it enables automation of software workflows that were previously "unautomatable" — legacy systems with no API, proprietary enterprise tools, complex UI-only workflows.

---

## 5. Runware — $50M Series A for an AI Model Aggregation API

**What happened:** Runware raised **$50 million** to scale its **Sonic Inference Engine** — a single API that routes requests across hundreds of thousands of AI models. Developers get unified access, automatic fallback, and optimal pricing without managing multiple provider integrations.

**Sources:**
- [AI Funding Tracker](https://aifundingtracker.com/ai-startup-funding-news-today/)
- [Crescendo AI VC deals](https://www.crescendo.ai/news/latest-vc-investment-deals-in-ai-startups)

**Why it matters to you:**
- Model routing and aggregation is a growing category as the number of frontier models multiplies. Similar to Helicone, LiteLLM, or Portkey but with broader ambition.
- For builders: a single API that routes to the best/cheapest model per task is a compelling alternative to managing individual provider SDKs. Worth evaluating for your projects.

---

## 6. Nova Intelligence — $31.5M Series A, AI Agents for SAP Migration

**What happened:** Nova Intelligence secured **$31.5 million** building AI agents that help enterprises migrate legacy systems into SAP S/4HANA using generative automation.

**Sources:**
- [Fundraise Insider — AI startups 2026](https://fundraiseinsider.com/blog/ai-startups/)
- [Blog.mean.ceo — startup funding trends May 2026](https://blog.mean.ceo/startup-funding-trends-may-2026/)

**Why it matters to you:**
- SAP migration is a massive, painful, expensive enterprise problem. Nova is the "Cursor for enterprise IT migration" — an agent that takes a specific, well-defined, highly valuable workflow and automates it end-to-end.
- Pattern to copy: pick the most painful, repetitive enterprise workflow in a domain you know, wrap it in agents, sell the outcome not the technology.

---

## 7. OpenClaw Goes Mainstream — The Personal Agent That Started the Race

**What happened:** OpenClaw (a personal AI agent built by an indie developer) became a viral sensation in early 2026 for its ability to respond to messages, conduct research, and take autonomous actions across web and apps. Sam Altman hired its creator to work on OpenAI's personal agent team. This single viral demo triggered the Google Remy and Meta Hatch development tracks.

**Why it matters to you:**
- A solo developer with a good idea and the right demo timing can change the roadmap of billion-dollar labs. This is the kind of market signal that creates startup opportunities.
- The product surface is clearly valued: every major lab is now trying to be your 24/7 digital agent. The opportunity is in specialization — a personal agent for researchers, for engineers, for doctors, rather than a general one.

---

## 8. The Vertical Agent > Horizontal Platform Pattern Is Now Confirmed

**The pattern:** Across funding data, enterprise sales results, and product launches in Q1–Q2 2026, one theme consistently wins: **vertical agentic AI** — tools that take *autonomous actions* in specific domains — beats general-purpose AI assistants for enterprise adoption.

- Anthropic sells 10 pre-configured financial sector agents → wins 70% of enterprise deals vs OpenAI
- Sierra (customer experience agents, Bret Taylor) → raises ~$1B
- Nova Intelligence (SAP migration agents) → $31.5M at seed/Series A
- Reserv (insurance claims AI) → $125M Series C led by KKR

**Sources:**
- [Blog.mean.ceo — startup funding trends May 2026](https://blog.mean.ceo/startup-funding-trends-may-2026/)
- [Wellows — 85 hottest AI startups 2026](https://wellows.com/blog/ai-startups/)
- [Crescendo AI — agentic AI news](https://www.crescendo.ai/news/latest-ai-news-and-updates)

**The formula that's getting funded:**
1. A specific vertical with measurable, repeatable workflow pain
2. An agent that takes *actions* (not just answers questions)
3. A measurable ROI metric in the first 30 days
4. A founder with deep domain credibility in that vertical
