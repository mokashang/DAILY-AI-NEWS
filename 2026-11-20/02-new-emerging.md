# New & Emerging — 2026-11-20

The week's non-lab story is **the data/eval economy went vertical**: Mercor **doubled to $20B in 13 months** off training + evaluating frontier models with a 5M-person expert network, and **Cognition productized agent-manager agents** (Devin Bots) one day after GPT-6.2 shipped. In biotech-AI, **Boltz opened a London-led $110M Series A** that puts a non-Isomorphic lab on the map. Underneath: **Meta Muse Spark Open** is still trailing Kimi K3 at coding (Nov 14 thread continues), and **Google Antigravity** quietly became the default IDE funnel for individual Gemini CLI users (as of June 2026, re-surfacing now with the Gemini 4 wave). This section emphasizes **wedge quality** over funding size — some $100M rounds matter more than some $1B rounds.

Tags: `#startups #funding #eval #rlhf #agents #biotech #open-source`

---

## 1. Mercor $750M Series D at $20B — doubled valuation in 13 months on expert-network evaluation and training {#1-mercor}

**What happened (2026-11-10):**
- **Mercor** announced a **$750M Series D** at a **$20B post-money valuation** — **2× its ~$10B mark** from October 2025.
- **Expert network**: reported **>5M people** of domain specialists hired to train and evaluate frontier models.
- **Reported investors**: Benchmark, Felicis, Fundomo, Apollo, **NVIDIA**, Zoom. **Lead undisclosed** (some sources cite Benchmark, Mercor has not confirmed).
- **Use of funds**: evaluation + post-training work, plus **environments where AI agents learn enterprise workflows**.
- **Positioning**: Mercor started as a recruiting marketplace, now serves OpenAI + Anthropic + other labs on eval + RLHF data, and is moving into enterprise AI evaluation — directly competing with **Scale AI** and **Surge AI**.
- **Caveats**: valuation reported by Mercor; not confirmed by participating investors. No revenue disclosed.

**Sources:**
- [TFN — Mercor doubles valuation to $20B with $750M Series D](https://techfundingnews.com/mercor-doubles-valuation-to-20b-with-750m-series-d-to-train-and-test-ai-agents-for-enterprises/) `[secondary]`
- [KuCoin — Mercor $750M Series D at $20B](https://www.kucoin.com/news/flash/ai-data-expert-network-mercor-completes-750m-d-round-funding-valuation-hits-20b) `[aggregator]`
- [VentureBurn — Mercor $750M to train AI on every job](https://ventureburn.com/mercor-raises-750-million-series-d-to-train-ai/) `[secondary]`
- [CASRAI — Mercor $750M Series D: What It Means](https://casrai.org/news/mercor-750-million-series-d-2026) `[aggregator]`

### Why it matters to you

- **Job lens:** **Mercor is now hiring hard for infrastructure + ML + product roles** on the back of this round. Expect postings for **"Evaluation Platform Engineer," "Enterprise Workflow Environments," "Expert Marketplace ML"** — these are **FDE-adjacent** roles with meaningful equity (Series D at $20B = reasonable optionality, not frontier-lab compressed). The **marketplace side** also quietly hires experts: if you have deep domain chops (law, medicine, finance, chemistry, specific engineering disciplines), **Mercor is a legitimate second income stream for a grad student** at $50–$200/hr per project depending on specialization.
- **Startup lens:** **Scale + Surge are now visibly #2 and #3.** If your startup touches eval data, expert networks, RLHF loops, or agent-environment generation, **you now have a $20B public comp to anchor against** — which means it is easier to raise against that thesis and harder to pitch a horizontal "we also do eval data" wedge. Consider: can you be **a specific vertical's Mercor** (medical Mercor, legal Mercor, chemistry Mercor, defense Mercor) with a relationship edge the big player can't buy? That's the realistic founder wedge here.
- **Insight:** **"Enterprise workflow environments"** is the phrase to anchor on. Mercor's use-of-funds deck language implies **they are now selling labs the environments where agents are trained to do real work**, not just the data labels. That shifts the primitive from **label marketplace** to **simulated-workflow marketplace**, which is a real moat (reproducibility, customer-specific environments, legal clearance over training data). **If you're applying to Mercor, read the latest OpenAI / Anthropic environments announcements and bring a one-page "environment I'd build" document to your interview.**

→ Cross-link: [`04` §1 — Agents Are Systems](./04-research-progress.md#1-agents-are-systems) · [`04` §2 — EvalResearchBench](./04-research-progress.md#2-evalresearchbench) · [`05` §4 — Ramp AI Index](./05-career-and-startup.md#4-ramp-ai-index)

---

## 2. Cognition ships Devin Bots (Nov 17) — manager-of-agents pattern productized at ~$48B valuation {#2-devin-bots}

**What happened (2026-11-17):**
- **Cognition** launched **Devin Bots** — a **persistent manager agent** that coordinates **teams of Devin coding agents** on projects running **days to weeks**.
- Reported **~$48B valuation** (up from the September 2026 round).
- Each Devin Bot **splits a large project into pieces and assigns them to individual Devin instances** (described as "manager of agents").
- **Distribution:** **McKinsey alliance** named at launch to sell Devin into large US + EU enterprises. Cognition says it works with **6 of 8 global systemically important banks**.
- **Pricing:** Cognition's pricing page did **not** list Devin Bots at launch — early-access / gated rollout.
- Sources describe **competitors as OpenAI "Dots" and Anthropic "Duet"** (treat those product names as unverified — only reported in secondary coverage so far).

**Sources:**
- [KuCoin — Cognition launches Devin Bots, valued at $48B](https://www.kucoin.com/news/flash/cognition-launches-devin-bots-to-manage-ai-coders-valued-at-48-billion) `[aggregator]`
- [TNW — Cognition × McKinsey sell Devin to big firms](https://thenextweb.com/news/cognition-mckinsey-alliance-devin-ai-software-engineering) `[secondary]`
- [DEV Community — Cognition Just Gave Devin a Manager](https://dev.to/paullovelace/cognition-just-gave-devin-a-manager-devin-bots-run-teams-of-ai-coders-for-weeks-21ch) `[analysis]`
- [CryptoBriefing — Cognition launches Devin Bots](https://cryptobriefing.com/cognition-launches-devin-bots-ai-coding/) `[secondary]`

### Why it matters to you

- **Job lens:** **Manager-of-agents** is the clearest new interview concept of Q4 2026. If you can draw a **one-slide architecture** showing: (1) a planner agent that reads a scope doc, (2) a dispatcher that assigns tasks to worker agents, (3) a verifier/escalator that merges results and escalates ambiguity to the human — **you've just answered the "design an autonomous eng system" question that will dominate FDE / Solutions screens for the next 2 quarters**. Companies to watch for similar openings: Cognition, Factory, Replit (Agent 3), Cursor, GitHub (Copilot Workspace), Sourcegraph Cody, Anthropic (likely Claude Orchestrator ships Q1).
- **Startup lens:** **Devin Bots raises the ceiling on agentic-coding valuations but also closes the "we ship a manager agent" wedge.** Honest reads: (a) if you were building a horizontal "manager over any agent," Cognition just owned that primitive — pivot to **domain-specific orchestration** (claims processing, legal drafting, compliance workflows) where Cognition's engineering-centric brand doesn't carry. (b) If you were building **pure coding agents**, the McKinsey alliance just made your enterprise GTM 10× harder — the Big-4 systems-integrator channel is being locked up. Counter-strategy: **partner with regional SIs** (Infosys, Capgemini, Accenture, PwC — though PwC leans Anthropic) or **direct-to-mid-market** verticals.
- **Insight:** **Manager-of-agents is the pattern, not the product.** The real IP is in **three primitives**: (1) **persistent plan state** that survives long runs, (2) **tool-level HITL interrupts** (see LangChain 1.4.9 from Nov 14 edition), (3) **failure-attribution logs** that let a human replay what went wrong at the manager level, not just the worker. Expect to see these primitives standardized in **MCP 2026-12** spec drafts.

→ Cross-link: [`01` §3 — GPT-6.2 fewer output tokens](./01-big-lab-moves.md#3-gpt-62-astra-sol) · [`03` §1 — Claude Code MCP background](./03-practical-skills-and-tools.md#1-claude-code) · [`04` §1 — Agents Are Systems](./04-research-progress.md#1-agents-are-systems)

---

## 3. Boltz $110M Series A for AI drug discovery (Nov 19) — London lab, Bessemer leads {#3-boltz}

**What happened (2026-11-19):**
- **Boltz**, London-based AI drug discovery startup, closed a **$110M Series A**.
- **Lead: Bessemer Venture Partners.** Existing investors: **a16z, Amplify Partners, Zetta Venture Partners, Obvious Ventures** participated.
- Puts a **non-Isomorphic independent lab** on the map in a category that DeepMind / Isomorphic has been running away with (recall: Isomorphic $2.1B Series B in May, AlphaGenome 2 shipped Nov 10–11).
- No clinical pipeline details disclosed in public coverage yet.

**Sources:**
- [Tech.eu — London-based Boltz raises $110M Series A](https://tech.eu/2026/11/19/london-based-boltz-raises-110m-series-a) `[secondary]`

### Why it matters to you

- **Job lens:** **AI-for-biotech** is quietly re-opening a role class that was "Isomorphic or bust" a quarter ago. Boltz hiring in London means **non-US candidates** (visa-adjacent / relocation-friendly) have a credible second option. Roles to watch: **ML research scientist (protein/structure), platform eng (lab workflows), FDE for pharma customers**. If you're a US grad student and open to London, **the 2027 EU/UK AI-biotech hiring window is as open as it's been** — compare Tessera, Iambic, Recursion, Boltz now.
- **Startup lens:** $110M Series A for an independent drug-discovery lab is **a signal that LPs are backing more than one horse** in a category that looked like it would consolidate to Isomorphic + a few majors. The "AI + regulated-industry" thesis is hardening across verticals (legal → Harvey; finance → Hebbia; healthcare → Abridge + a few; drug discovery → Isomorphic + Boltz).
- **Insight:** Watch **Bessemer's AI thesis arc**: fal ($1.65B at $16B, Nov 3) + Mercor ($750M at $20B, Nov 10) + Boltz ($110M, Nov 19) in **17 days**. That's **~$2.5B deployed** by one firm into three different AI primitives (inference infra, eval data, biotech). **Bessemer has visibly out-paced Sequoia + a16z on AI deal velocity this month** — if you're pitching, they are the warmest check in the market this quarter.

→ Cross-link: [`02` §1 — Mercor same week](#1-mercor) · [prior edition: 2026-05-18 Isomorphic $2.1B](../2026-05-18/02-new-emerging.md)

---

## 4. Meta Muse Spark Open follow-up — still trailing Kimi K3 on coding, leading on MCP-Atlas {#4-muse-spark-open-followup}

**What happened (status update after Nov 14 thread):**
- **No new Meta open-weight release** this week — the picture from Nov 14 is unchanged, but the frontier moved around it.
- **Muse Spark Open benchmarks** (Meta's own card, ran against competitors):
  - **Terminal-Bench 2.1: 76.4** (vs **Kimi K3 85.0, GLM 5.3 83.9**)
  - **Artificial Analysis Intelligence Index: 39** (vs **GLM 5.3 45, Kimi K3 44, Qwen3.8-2.4T 40**)
  - **JobBench: 61.8 (highest in Meta's comparison table)**
  - **MCP-Atlas: 89.2 (highest in Meta's comparison table)**
- **The New Stack framing** ("beats them across the board by 20 points") contradicts the specific Terminal-Bench numbers; read Meta's model card directly, not the headline.
- **Implication:** Muse Spark Open is **best at agentic tool-use in Meta's own benchmarks**, but **the open-weight coding crown is still Kimi K3** (and GLM 5.3 is close). Meta has 6–8 weeks to ship a Spark 2 or 1.4 or concede open-weight coding leadership for Q1 2027.

**Sources:**
- [The New Stack — Meta ships Muse Spark Open](https://thenewstack.io/meta-muse-spark-open/) `[secondary]`
- [Unite.AI — Meta's 816B Muse Spark Open Weights Public](https://www.unite.ai/metas-816b-parameter-muse-spark-open-weights-are-now-public/) `[secondary]`
- [Miraflow — Meta Muse Spark Open Explained](https://miraflow.ai/blog/meta-muse-spark-open-explained-benchmarks-hardware-license-2026) `[analysis]`
- [HeshamSaad — Muse Spark Open benchmarks and license](https://heshamsaad.com/en/meta-muse-spark-open/) `[analysis]`

### Why it matters to you

- **Job lens:** **MCP-Atlas 89.2 is the detail to memorize.** If you're interviewing for any role that touches agent-tool-use (FDE, Solutions, Applied, Platform), being able to say "Muse Spark Open scores 89.2 on MCP-Atlas, vs. Terminal-Bench 2.1 where Kimi K3 leads — so if the workload is tool-use heavy, there's an argument for Spark even though its general-coding is weaker" will mark you as someone who **reads model cards, not headlines**.
- **Startup lens:** **A Chinese open-weight model on your own GPUs is still the serious enterprise-sovereignty play.** If you serve EU, UK, Middle East, or Southeast Asia customers where US-API data-residency is a blocker, **Kimi K3 or GLM 5.3 on an Oracle / OVH / Scaleway tenancy is a legitimate production stack** — not a hack. Expect this thread to get louder through Q1 2027.
- **Insight:** **The US open-weight frontier is non-US, still.** Watch for a Meta response in **Jan 2027** — either a Spark 1.4 (coding-focused) or a surprise architecture bet. If neither ships by then, assume Meta cedes open-weight to China for the cycle.

→ Cross-link: [prior edition: 2026-11-14 Muse Spark Open intro](../2026-11-14/02-new-emerging.md#3-muse-spark-open)

---

## 5. Antigravity IDE refresh — the first-run funnel for Gemini CLI users (quiet update worth noting) {#5-antigravity}

**What happened (quiet but important):**
- **Google Antigravity** (the agent-first IDE launched Nov 2025 with Gemini 3) has been the **default landing for individual Gemini CLI users since June 18, 2026** — surfacing again now with the Gemini 4 wave because the model picker surfaces **Gemini 4 Argon Medium**.
- **Antigravity 2.0** (May 19, 2026) spun out a separate desktop app; the IDE is slated to **drop the Agent Manager UI**, becoming a purely agent-powered IDE (treat as reported timeline, not announced ship date).
- **Pricing model** (per third-party guides): free tier + paid at **~$19.99** for higher limits (verify directly on antigravity.google before relying on this number).

**Sources:**
- [Introducing Google Antigravity — Google blog](https://antigravity.google/blog/introducing-google-antigravity/) `[primary]`
- [Google Antigravity Getting Started docs](https://antigravity.google/docs/getting-started/) `[primary]`
- [Wikipedia — Google Antigravity](https://en.wikipedia.org/wiki/Google_Antigravity) `[aggregator]`
- [Fastero — Google Antigravity (model picker + pricing)](https://fastero.com/blog/google-antigravity) `[analysis]`

### Why it matters to you

- **Job lens:** **"Which AI-native IDE do you use?"** has become a real interview question at frontier labs and AI-first companies, and the right answer is **"Claude Code primary, Antigravity for Gemini-native work, Cursor for legacy repos"** — not a single tool. Spend **30 minutes this weekend** installing Antigravity, running the same task you'd run in Claude Code, and writing a 3-paragraph note about which handled it better. **That note is your talking point.**
- **Startup lens:** **The AI-first IDE market is consolidating into labs' own tools** (Antigravity, OpenAI Codex IDE, Anthropic Claude Code, Cursor-the-independent). If you were planning to build a new IDE, **the window closed** — pivot to **extensions / plugins / review tools / eval harness** that sit *around* the IDEs. Or build the vertical IDE (legal IDE, finance IDE, biotech IDE).
- **Insight:** **IDE funnels are where labs meet developers first.** Antigravity being the default Gemini CLI landing is a quiet but structural distribution win for Google. Watch for **Claude Code getting a graphical "home" surface** (not just the terminal) in Q1 2027 — Anthropic has to match this, or concede the "first-run developer experience" lane to Google.

→ Cross-link: [`03` §1 — Claude Code MCP background](./03-practical-skills-and-tools.md#1-claude-code) · [`03` §2 — Code Mode](./03-practical-skills-and-tools.md#2-code-mode)
