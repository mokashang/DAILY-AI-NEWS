# Big Lab Moves — 2026-05-06

Strategy, products, policy, and power moves from the labs and companies shaping AI.

---

## 1. Anthropic's Claude Mythos — The Most Dangerous Model Ever Restricted at Launch

**What happened:** Anthropic released Claude Mythos Preview — a general-purpose model that is, in their words, "far ahead of other models in cybersecurity." Before giving anyone access, Anthropic used it internally to identify **thousands of zero-day vulnerabilities** across every major OS and browser, including a 17-year-old RCE vulnerability in FreeBSD (CVE-2026-4747) that allows root access on any machine running NFS.

Because of how capable it is offensively, Anthropic restricted access to a small group of approved organizations via **Project Glasswing** — AWS, Apple, Cisco, CrowdStrike, Google, JPMorgan Chase, Linux Foundation, Microsoft, NVIDIA, and Palo Alto Networks. The goal: let defenders harden critical systems *before* an attacker-equivalent model becomes broadly available.

**Sources:**
- [Anthropic — Claude Mythos Preview](https://red.anthropic.com/2026/mythos-preview/)
- [Anthropic — Project Glasswing](https://www.anthropic.com/glasswing)
- [Fortune — Anthropic restricting Claude Mythos to security researchers](https://fortune.com/2026/04/07/anthropic-claude-mythos-model-project-glasswing-cybersecurity/)
- [Simon Willison — Project Glasswing analysis](https://simonwillison.net/2026/Apr/7/project-glasswing/)
- [Schneier on Security — Mythos & Glasswing](https://www.schneier.com/blog/archives/2026/04/on-anthropics-mythos-preview-and-project-glasswing.html)
- [Foreign Policy — Claude Mythos changes cyber calculus](https://foreignpolicy.com/2026/04/20/claude-mythos-preview-anthropic-project-glasswing-cybersecurity-ai-hacking-danger/)

**Why it matters to you:**
- **For the job search:** AI security / red-teaming is now a billable, hireable specialty. Companies in the Glasswing consortium are actively hiring people who can evaluate AI models for adversarial capabilities. If you have any interest in security + AI, this is a uniquely hot intersection.
- **For the startup:** AI-assisted vulnerability discovery is entering the mainstream. Startups building AI-native security tools (automated pentesting, patch prioritization, CVE triage) are in the exact market that Glasswing is creating awareness for.
- **Insight:** The fact that Anthropic *chose* to gate this rather than release it shows that the dual-use problem for AI models is now real and acute — not hypothetical. This is the first major case of a frontier model being restricted pre-release for capability reasons, not safety-theater reasons.

---

## 2. OpenAI Hits $25B Annualized Revenue — IPO on the Horizon

**What happened:** OpenAI crossed **$25 billion in annualized revenue** in February 2026, up from $20B at year-end 2025. The company has surpassed **900 million users**. It's now actively preparing for a public listing — potentially filing in H2 2026 for a 2027 IPO at a target valuation of up to **$1 trillion**, which would be the largest IPO in history.

To put the growth in context: Salesforce took 18 years to reach $25B revenue. Google took 17 years. Facebook took 12. OpenAI did it in ~39 months.

The catch: OpenAI is projecting ~$14 billion in *losses* on that $25B revenue — the cost of compute to train and serve frontier models is staggering.

**Sources:**
- [The Information — OpenAI tops $25B annualized revenue](https://www.theinformation.com/articles/openai-tops-25-billion-annualized-revenue-anthropic-narrows-gap)
- [Yahoo Finance — OpenAI $25B revenue](https://finance.yahoo.com/news/openai-tops-25-billion-annualized-033836274.html)
- [Humai Blog — What the numbers actually mean](https://www.humai.blog/openai-makes-25-billion-a-year-and-is-preparing-for-an-ipo-here-is-what-the-numbers-actually-mean/)
- [techi.com — OpenAI IPO timeline](https://www.techi.com/openai-ipo/)

**Why it matters to you:**
- **Startup lens:** OpenAI going public sets a valuation benchmark for the entire AI sector. Expect secondary markets for AI startup equity to heat up significantly. Watch for LP re-allocations into AI VC funds.
- **Job lens:** A pre-IPO OpenAI is aggressively hiring to build toward the listing narrative. RSUs at OpenAI are worth watching if you're evaluating offers — but understand the lockup risk.
- **Insight:** $14B in losses on $25B revenue is not a profitable business. The bet is on the future — AGI + monopolistic compute leverage. OpenAI is essentially the largest "research project disguised as a company" in history. This is either the best startup ever or the most expensive science experiment.

---

## 3. US Government Gets Pre-Deployment Model Testing Rights — Anthropic Left Out

**What happened:** The Center for AI Standards and Innovation (CAISI) announced agreements with **Google DeepMind, Microsoft, and xAI** giving the US government the right to evaluate their AI models *before public release*. This is the Trump administration's primary AI oversight mechanism, replacing the Biden-era Executive Order framework.

Notably: **Anthropic was excluded** from this initial group — despite the Pentagon separately striking a deal with Anthropic for defense use. Eight big tech companies got Pentagon AI service agreements; Anthropic was initially bypassed, then confirmed separately.

**Sources:**
- [CNN Business — Microsoft, Google, xAI pre-deployment testing](https://www.cnn.com/2026/05/05/tech/microsoft-google-xai-government-test-ai-models)
- [CNBC — Trump admin AI oversight](https://www.cnbc.com/2026/05/05/ai-oversight-trump-google-microsoft-xai.html)
- [Claims Journal — Google, Microsoft early access](https://www.claimsjournal.com/news/national/2026/05/05/337371.htm)
- [CNN Business — Pentagon AI deals](https://www.cnn.com/2026/05/01/tech/pentagon-ai-anthropic)

**Why it matters to you:**
- **Startup lens:** Companies with "cleared" status for government pre-deployment evaluation will have a structural moat for government and enterprise contracts. This is infrastructure-level gatekeeping forming right now.
- **Insight:** The US government is now using pre-deployment evaluation as the carrot — labs that cooperate get access to procurement pipelines. Labs that don't cooperate risk being locked out. Anthropic's separate Pentagon deal suggests they're playing a different political strategy than Google/Microsoft.

---

## 4. Google's "Remy" — A 24/7 Personal AI Agent Inside Gemini

**What happened:** Google is internally testing a personal AI agent codenamed **"Remy"** inside an employee-only version of the Gemini app. Remy is described as a 24/7 personal agent for work, school, and daily life. It connects to Gmail, Calendar, Docs, Drive, GitHub, Spotify, WhatsApp, Google Home, and Android utilities to take *actions* on behalf of users — not just answer questions.

Google also discontinued its experimental Mariner browser agent on May 4, folding its technology into Gemini Agent. Remy is expected to debut publicly at **Google I/O**.

This is widely seen as Google's response to OpenClaw, the personal AI agent that went viral in early 2026 — prompting Sam Altman to hire its creator for OpenAI's personal agent team.

**Sources:**
- [AI News — Google Remy AI agent Gemini](https://www.artificialintelligence-news.com/news/google-remy-ai-agent-gemini-user-control/)
- [Storyboard18 — Remy 24/7 agent](https://www.storyboard18.com/digital/google-developing-remy-a-24-7-ai-agent-to-manage-users-digital-lives-ws-l-97337.htm)
- [IT Pro — Google Remy vs OpenClaw](https://www.itpro.com/technology/artificial-intelligence/google-is-building-its-own-openclaw-alternative-remy-elevates-the-gemini-app-into-a-true-assistant)
- [eWeek — Gemini Remy 24/7 agent](https://www.eweek.com/news/google-gemini-remy-ai-agent/)

**Why it matters to you:**
- **Startup lens:** Every major lab is racing to own the "personal OS layer" — the agent that knows your calendar, email, tasks, and digital life. If they succeed, they own the relationship layer above all other apps. As a founder, think about which user problems will *not* be solved by a general personal agent (highly domain-specific, professional, or sensitive workflows).
- **Insight:** The personal agent race is the new mobile OS race. Google (Remy), OpenAI (OpenClaw-acquired team), Meta (Hatch, testing end of June), and Apple are all building versions of this. The winner controls what apps people actually interact with.

---

## 5. Meta Unveils Muse Spark + $115–135B Capex — Alexandr Wang's Superintelligence Lab

**What happened:** Meta unveiled **Muse Spark**, the first flagship LLM from its newly formed Superintelligence Labs (led by Chief AI Officer Alexandr Wang, ex-Scale AI founder). Muse Spark targets multimodal perception, reasoning, health applications, and agentic tasks — at significantly lower compute cost than comparable Western frontier models.

Meta also committed **$115–135 billion in AI capex for 2026**, nearly double last year. Meta is internally building agent "Hatch" for personal use, planning to switch from Anthropic's Claude models to Muse Spark at launch (internal testing expected by end of June).

**Sources:**
- [The Decoder — Google and Meta race to build personal AI agents](https://the-decoder.com/google-and-meta-race-to-build-personal-ai-agents-as-anthropic-and-openai-pull-further-ahead/)
- [TLDL — AI news updates 2026](https://www.tldl.io/blog/ai-news-updates-2026)
- [LLM Stats — AI news](https://llm-stats.com/ai-news)

**Why it matters to you:**
- **Startup lens:** Meta going from "open Llama releases" to "Superintelligence Labs + $130B capex" is a massive gear-shift. The key question: will Muse Spark have an open-weight version? If Meta continues its open-source strategy with a frontier-competitive model, it dramatically lowers the cost of building AI products.
- **Insight:** Alexandr Wang being poached as CAO signals Meta is done being the "open-source underdog." Wang built Scale AI on the insight that data quality is the real moat — expect Meta to use that philosophy to close the gap with OpenAI and Anthropic.

---

## Quick Scorecard: Where Each Lab Stands (May 2026)

| Lab | Strongest At | Key Move This Week | Watch For |
|---|---|---|---|
| **Anthropic** | Cybersecurity (Mythos), coding (Claude Opus 4.7), enterprise | Project Glasswing restricted release | When Mythos gets broader access |
| **OpenAI** | Revenue ($25B ARR), users (900M), omnimodal (GPT-5.5) | IPO groundwork, personal agent (OpenClaw) | H2 2026 IPO filing |
| **Google** | Cost/token (Gemini 3.1 Flash-Lite), multimodal, search | Remy personal agent, Google I/O upcoming | Remy public debut at Google I/O |
| **Meta** | Open-source ecosystem, capex ($130B), data | Muse Spark + Hatch personal agent | Open-weight Muse Spark release |
| **xAI** | Grok speed, real-time data | Pre-deployment government testing agreement | Next Grok release |
