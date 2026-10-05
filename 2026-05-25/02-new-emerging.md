# New & Emerging — 2026-05-25

The emerging model story going into June: **Gemini 3.5 Pro is confirmed but unshipped**, and the *gap* between it and the already-shipped Flash is the interesting part. Flash GA'd at I/O with strong **coding and agentic** scores but a **regression on hard reasoning** — which tells you exactly what Pro is for, and tells you how Google is now *segmenting* its lineup: cheap-and-fast for agents, reasoning-tier for the hard problems. Around it sits the rest of the I/O agent stack — **Spark** (a 24/7 proactive agent) and **Omni** (a world model) — now consolidating into a coherent platform.

Tags: `#google #gemini #models #agents #spark #omni`

---

## 1. Gemini 3.5 Pro lands in June — and the Flash/Pro split tells the strategy {#1-gemini-pro}

**What's emerging:** **Gemini 3.5 Pro is confirmed for June** (no exact date), positioned as the **reasoning tier** above the already-GA **Gemini 3.5 Flash.** The detail that matters:

- **Flash beats the *previous* flagship (Gemini 3.1 Pro) on coding and agentic benchmarks** — reported ~**76% on Terminal-Bench 2.1** and ~**84% on MCP-Atlas** — at a fraction of the cost.
- But **Flash *regressed* on hard reasoning** relative to top reasoning models — a deliberate trade. Google shipped the cheap, fast, agent-optimized tier first and is holding the **reasoning-heavy Pro tier for June.**
- Around the models: **Gemini Spark** (a 24/7 proactive agent on the Antigravity harness, MCP-integrated with third-party apps like Canva/Instacart/OpenTable "within weeks") and **Gemini Omni** (a world model generating outputs across modalities, starting with video). The Gemini app reportedly crossed **~900M MAU.**

**Sources:**
- [Google Blog — Gemini 3.5 models and research](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-5/) `[primary]`
- [MarkTechPost — Google introduces Gemini 3.5 Flash at I/O 2026](https://www.marktechpost.com/2026/05/20/google-introduces-gemini-3-5-flash-at-i-o-2026-a-faster-and-cheaper-model-for-ai-agents-and-coding/) `[secondary]`
- [WaveSpeed — Gemini 3.5 Pro coming next month](https://wavespeed.ai/blog/posts/gemini-3-5-pro-coming-next-month/) `[analysis]`

### Why it matters to you

- **Job lens:** The Flash/Pro split is a **routing lesson you can put in a portfolio.** "Use Flash for the agentic/coding legs (where it now beats last-gen Pro), route to a reasoning-tier model only for the hard-reasoning steps" is exactly the cost-aware design FDE/AI-engineer interviews probe. Your 3-provider router ([ACTIONS.md](../ACTIONS.md)) should now encode this as an explicit rule, with a per-step cost chart showing where Flash saves and where you escalate.
- **Startup lens:** Flash's coding/agentic scores at low cost **compress margins for any agent product** — your competitors can now run cheap-and-good for most steps. Your differentiation can't be "we use a good model"; it has to be the **verification, the vertical data, or the deployment** ([2026-05-24/02 §3](../2026-05-24/02-new-emerging.md#3-board) made the same point about the model board commoditizing). Build where the model is a swappable backend.
- **Insight:** Google segmenting Flash (agents) from Pro (reasoning) confirms the **2026 lineup pattern across all labs**: a cheap-fast agentic tier + an expensive reasoning tier, and you're expected to *route between them.* The skill the whole industry is converging on isn't "pick the best model" — it's "**put the right model in each seat.**" That's the same thesis as the Opus-planner/Sonnet-worker split ([2026-05-22/03 §1](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost)) — now true *within* Google's lineup too.

→ Cross-link: [2026-05-20/01 the I/O scorecard (Flash GA)](../2026-05-20/01-big-lab-moves.md) · [2026-05-22/03 §1 model-routing as the skill](../2026-05-22/03-practical-skills-and-tools.md#1-agent-team-cost) · [2026-05-24/02 §3 the model board commoditizing](../2026-05-24/02-new-emerging.md#3-board).
