# Research Progress — 2026-11-27

Research signal in this window skews toward **agent behavior** (what "exploration" even means in an LLM) and **production-scale multi-agent output** (DeepMind publishing math with Gemini 4). The arXiv weekly is harder to pin from aggregator summaries — verify each ID before citing in an interview.

Tags: `#arxiv #research #agents #rl #multi-agent #robotics #math`

---

## 1. Gemini-4 multi-agent produces six math papers from Google Research {#1-gemini-4-multi-agent-math}

**What's reported:**
- Google Research reportedly **published six math papers** produced by its multi-agent framework **running on Gemini 4** (per aiweekly.co's Nov 27 roll-up).
- No arXiv IDs or author lineups specified in the aggregator; **treat as directional until the papers surface under DeepMind authorship with explicit "methodology: multi-agent on Gemini 4" sections**.
- Context: this would be the first large-scale instance of a frontier lab publishing *its own research in a math domain, with its own flagship model doing the lifting*. On Oct 26 OpenAI claimed three novel proofs including a Lean-verified ETH disproof (noted in 2026-11-14) — the two labs now run parallel "LLM for math" tracks.

**Sources:**
- [aiweekly.co — AI News Today, Nov 27](https://aiweekly.co/ai-news-today) `[aggregator]`
- [The Information — DeepMind Kavukcuoglu on Gemini 4 (Sep)](https://www.theinformation.com/) `[secondary]`

### Why it matters

- **Research lens:** When a frontier lab uses its own flagship to produce research output, it raises **the internal "publishable" bar** for multi-agent orchestration — latency, cost, tool-use reliability, hallucination control have all been pushed hard enough to clear peer-review-adjacent standards. That makes **"verify any LLM-authored proof via Lean / Coq"** a hireable workflow.
- **Job lens:** DeepMind's research-ops team (the engineers who build the infra that lets scientists run Gemini-4 multi-agent at paper-producing scale) is a quietly hireable function. If your interest is in **experimental infra more than models themselves**, pitch into that lane.
- **Insight:** Expect the equivalent capability drop from Anthropic on their first post-IPO shareholder communication — a public lab has new incentives to disclose research-productivity metrics.

→ Cross-link: [`01` §3 — Gemini 4 math](./01-big-lab-moves.md#3-gemini-4-math)

---

## 2. "LLM agent exploration isn't real exploration" — UCSB / MIT / IDSIA {#2-exploration-critique}

**What's reported:**
- A **Nov 10 LLM Daily digest** (buttondown/agent-k) summarizes a paper by researchers at **UC Santa Barbara, MIT, and IDSIA** arguing that commonly-used LLM agent techniques — **temperature sampling, tree search** — are **not genuine exploration** in the RL sense.
- The claim: these techniques sample from the model's existing policy distribution without acquiring genuinely new information about the environment, and thus cannot support the kind of exploration-exploitation tradeoff that RL theorems require.
- **This is a secondhand summary**; the primary arXiv ID isn't in the digest I found. Flag as unverified until the paper is in hand.

**Sources:**
- [LLM Daily Nov 10, 2026 (buttondown/agent-k)](https://buttondown.com/agent-k/archive/llm-daily-november-10-2026/) `[aggregator]`

### Why it matters

- **Research lens:** If this holds up, **the entire "agent with exploration = tree search + temperature" paradigm is fragile**. The practical replacement looks like: (a) tool-use that genuinely probes unknown state (e.g., web search, file reads) rather than sampling; (b) curiosity-driven rewards that credit new information gain rather than new tokens; (c) hybrid RL+LLM setups with explicit environment interaction.
- **Job lens:** If you are interviewing for RL / RLHF / agent-safety roles, **be able to articulate the distinction between policy-space sampling and environment-space exploration** — this is becoming a basic interview check.
- **Insight:** The harshest version of this critique: **"tree-of-thoughts" demos that look good in a paper figure don't produce agents that generalize**. A sober reading: tree search is still useful when you can define a verifier (Lean, SAT, SQL output); it fails when the "verifier" is the model itself.

---

## 3. WikiSkill — compiling agent experience into persistent skill knowledge {#3-wikiskill}

**What's reported:**
- From Hugging Face Papers August 2026 snapshot (trended into Nov 10 digests): **WikiSkill: Compiling Agent Experience into Persistent Knowledge for Skill Evolution**.
- Thesis: agents accumulate transient experience (traces, failures, successful plans); WikiSkill compiles that into a wiki-structured persistent knowledge store — effectively giving agents a long-term skill memory separate from their working memory.
- Connects to the **Long-Lived Agent Memory benchmark** (noted in 2026-11-14) — memory and skill accretion are now a specific research surface, not just a RAG optimization.

**Sources:**
- [Hugging Face Papers (API)](https://huggingface.co/api/papers) `[primary]`
- [Hugging Face Papers trending](https://huggingface.co/papers/trending) `[primary]`

### Why it matters

- **Research lens:** Agent memory is converging on **three layers**: (1) working memory (context window), (2) episodic memory (past traces), (3) skill memory (compiled, reusable patterns). WikiSkill targets #3 explicitly. Expect the pattern to show up in production agent frameworks (LangGraph, Agno, OpenAI Agents SDK) within two quarters.
- **Job lens:** If you're applying for AI-agent roles, **the question "how does your agent learn across sessions?" is now a standard interview check**. Have one three-layer-memory answer ready.
- **Insight:** **Memory is the next architecture battleground after tools.** 2024 was tools, 2025 was multi-step, 2026 is routing, 2027 is memory.

---

## 4. TTPO (Test-Time Policy Optimization) {#4-ttpo}

**What's reported:**
- Trended via Hugging Face Papers mid-November (67 upvotes in the snapshot I found). **TTPO: Test-Time Policy Optimization.**
- Thesis: instead of freezing a policy at train time, update it during inference using the test-time task's own feedback. In LLM terms: use early tokens' quality signals to update the sampler for later tokens.
- Related to inference-time compute scaling (reasoning-model work from 2025) but more specifically **optimizes the policy, not just the sampling budget**.

**Sources:**
- [Hugging Face Papers (API snapshot)](https://huggingface.co/api/papers) `[primary]`

### Why it matters

- **Research lens:** **"Test-time learning"** has graduated from a niche to a named sub-field. The implications for safety are non-trivial: an agent that updates its policy during a session is harder to red-team ex-ante. Expect labs to adopt formal release-committee review of any model that uses test-time updates.
- **Job lens:** Add "test-time compute" and "test-time optimization" to your résumé keyword set if you have any interest in inference-side research or applied ML.
- **Insight:** This moves the eval question. Instead of "is my model X% accurate?" the question becomes "is my model X% accurate on the Nth task after N-1 adaptations?" **Eval design is the quiet skill shortage of 2026 — and the fastest-rising FDE prerequisite.**

---

## 5. UrbanGround — spatial agency in a real-scale city {#5-urbanground}

**What's reported:**
- Highest-upvoted paper in the HF Papers August snapshot I pulled (70 upvotes): **UrbanGround: From Local Perception to Spatial Agency in a Real-Scale City**.
- Thesis: couple a perception stack (local observations, sensor streams) with an agency layer that plans at city-scale. Likely bridges the robotics-VLA (video+language+action) world with navigation/urban planning.

**Sources:**
- [Hugging Face Papers (API snapshot)](https://huggingface.co/api/papers) `[primary]`

### Why it matters

- **Research lens:** Robotics + urban-scale perception is exactly the wedge the BrightAI thesis (see [`02` §1](./02-new-emerging.md#1-brightai)) sits on. **Research and funding are moving into the same lane.**
- **Job lens:** If you're drawn to physical AI, formal-robotics research with a VLA + planning framing is the hireable research artifact. Figure, 1X, Physical Intelligence, and the NVIDIA GR00T team all hire for this specific profile.
- **Insight:** The "urban agent" framing — not just "robot in a room" — is where the next round of VLA papers will land in 2027.

---

## 6. Open-weight VLA continuation (Praxis-1 / GR00T 2 / Gemini Robotics 2.5 from 2026-11-14) {#6-vla-continuation}

**No new drops this fortnight.** Status:

- **Runway Praxis-1** (27B MoE video+action, Apache 2.0) — benchmark lead on RoboLab-120 (46.2%) holds.
- **NVIDIA GR00T 2** — whitepaper out; code drop still slated for December per NVIDIA statement.
- **Google DeepMind Gemini Robotics 2.5** — Apptronik / Mercedes-Benz partners continue testing.

**Sources:**
- [Runway — Praxis-1](https://runwayml.com/) `[primary]`
- [NVIDIA GR00T 2](https://developer.nvidia.com/groot) `[primary]`
- [Google DeepMind — Gemini Robotics 2.5](https://deepmind.google/discover/blog/) `[primary]`

### Why it matters

- **Research lens:** Robotics is now following the open-weight model: labs ship the weights + publish the method; startups (Figure, 1X, physical-infra players like BrightAI) deploy them. Watch for a **GR00T 2 commit log** in mid-December as the next milestone.

---

## 7. Where to go from here

**If you have 60 minutes, pick one:**
- **Read the WikiSkill abstract** and write two sentences about how it changes your current agent project.
- **Read the TTPO abstract** and sketch one eval you'd need to measure "did test-time optimization help?"
- **Pull the arXiv listing for cs.AI Nov 2026** and bookmark three papers from the last five days to read over the weekend. The [arXiv cs.AI daily listing](https://arxiv.org/list/cs.AI/current) is the right surface; third-party mirrors lag.

**If you have a weekend:** build the three-layer memory agent (working + episodic + skill) with 3 tools, 20 test tasks, and a measured improvement from using the skill layer. Publish the writeup.
