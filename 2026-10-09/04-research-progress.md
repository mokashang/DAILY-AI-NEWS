# Research Progress — 2026-10-09

Two research-adjacent events this week dominate: **OpenAI's 722-manuscript math drop (Oct 6)** opens the "research-lab-as-publisher" debate, and the **agent-memory + multi-agent-memory** paper cluster (Dec 2025 → Mar 2026, now consolidating) has become a measurable eval axis. Add the **ongoing Project Suncatcher orbital TPU prototype (Oct 1 launch, 1-year mission)** as the infrastructure-side frontier. The frame: **the research frontier is now pulling along two parallel tracks — model-driven mathematical discovery (closed) and model-driven agent cognition (increasingly measurable).**

Tags: `#arxiv #math #agents #memory #verification #compute #infrastructure`

---

## 1. The verification stack behind OpenAI's 722 manuscripts {#1-verification-stack}

**What happened:** OpenAI's **Oct 6 math drop** (covered in [`01` §3](./01-big-lab-moves.md#3-openai-math-dump)) is the headline, but the research-process-level story is **what verification tooling it reveals** — and what verification tooling it still *doesn't* publish. The exposed stack:

- **Lean formalizations: 162 of 722 manuscripts.** Lean is the de facto open-source proof assistant for frontier math; OpenAI's team formalized the main result in ~22% of outputs. The rest ship as prose claims.
- **Abridged reasoning summaries** — truncated chain-of-thought style, not the full trace. The IAS advisory group asked for exact prompts and per-problem compute times; OpenAI released averages (~3 hours of Pro-thinking compute per result).
- **No model release.** The IAS group's position: without the model, "claims about one-shotting problems with a single agent" are unverified (Sutherland).

**What this maps to in research-engineering practice:**

- **The reproducibility axis is now "model + prompt + compute + Lean trace."** All four are needed to call a result "reproducible." OpenAI released 1 of 4 (the Lean trace, on 22% of outputs). The gap is enormous.
- **Lean is now a frontier-lab career skill.** Not generically — specifically the ability to take a model-produced reasoning trace and formalize its *main result*. This is a specific sub-skill that Anthropic (per Project Glasswing's human-review patch flow) and Google DeepMind (via its ongoing AlphaProof lineage) are also hiring for.
- **The "triage" layer is unoccupied.** Nobody is yet building the open-source tool that takes 722 model-generated manuscripts, cross-checks them against the Semantic Scholar / arXiv graph for prior-art collisions, scores novelty, and flags the top candidates for Lean formalization. 2-person startup, 3-month MVP.

**Sources:**
- [OpenAI — Math model research post (via Decrypt coverage)](https://decrypt.co/380366/openai-secret-ai-model-cracked-hundreds-math-problems-one-prompt) `[secondary]`
- [Gizmodo — 377 new math results on GitHub](https://gizmodo.com/openai-dumps-377-new-math-results-on-github-publishes-hand-wringing-blog-post-2000822613) `[secondary]`
- [The Next Web — 722 maths papers from an unreleased model](https://thenextweb.com/news/openai-maths-722-papers-unreleased-model-github) `[secondary]`
- [Unite.ai — OpenAI 372 math-result families](https://www.unite.ai/?p=480739) `[secondary]`
- [YourStory — OpenAI puts AI-generated maths to the test with 722 manuscripts](https://yourstory.com/ai-story/openai-ai-open-maths-problems-solved) `[secondary]`
- [arXiv:2511.04898 — Real-Time Reasoning Agents in Evolving Environments (referenced in 2026-09-10)](https://arxiv.org/abs/2511.04898) `[primary]`

### Why it matters to you

- **Job lens:** Three specific skill-paths just got re-priced upward. **(1) Lean/Coq formalization** — rare, measurable, aligned with the "model + proof assistant" research-lab recruiting lane. **(2) Reproducibility pipelines** — DVC, MLflow for *reasoning traces*, prior-art cross-check tools. The GitHub for AI-generated research doesn't exist yet. **(3) Verification SRE** — the ops layer around formal-verification compute (long-running proof searches, distributed Lean workers). All three are rare-skill lanes with 2027-Q1 hiring tailwinds.
- **Startup lens:** The 2-person wedge: **"did it discover anything new"-as-a-service**. Take any model-generated research output, run it against Semantic Scholar + arXiv + the formalization libraries, return a novelty score + top 10 overlaps. Price: $0.05/manuscript, free for academics. Twitter-friendly launch. Would have 10K+ runs the week of the OpenAI drop alone.
- **Insight:** The IAS group's recommendation is **the first on-record normative request from the mathematical establishment to a frontier lab.** Watch how (and whether) ACM/AAAI/NeurIPS respond. If any of those bodies publish an "AI-generated research disclosure norm" by end-Q1 2027, that becomes a hiring filter — labs will suddenly want researchers with public positions on it. Having a blog post on your own view **right now** is cheap optionality.

→ Cross-link: [`01` §3 OpenAI math dump](./01-big-lab-moves.md#3-openai-math-dump).

---

## 2. Agent memory, 10-month review — the eval axis settles {#2-agent-memory-eval}

**What happened:** The paper cluster the Sept 10 edition flagged ([2026-09-10/04 §1](../2026-09-10/04-research-progress.md#1-realtime-memory) via arXiv:2512.13564 "Memory in the Age of AI Agents") now has a stable research shape. The core papers:

- **arXiv:2512.13564 "Memory in the Age of AI Agents"** (Dec 2025, revised Jan 2026) — the survey organizing agent memory by form (episodic/semantic/procedural), function (recall/reasoning/forgetting), and dynamics (consolidation/update/eviction). Lists multi-agent memory as the frontier.
- **arXiv:2603.10062** (Mar 2026) — treats multi-agent memory as a *computer architecture* problem. Three-layer hierarchy; argues **memory consistency across agents is the pressing open challenge**.
- **arXiv:2508.08997 "Intrinsic Memory Agents"** (Aug 2025, revised Jan 2026) — agent-specific memories that update as each agent produces output. Benchmarks: PDDL, FEVER, ALFWorld.
- **arXiv:2603.23234 "MemCollab"** (Mar 2026) — memory shared across different LLM agents. Reports accuracy + efficiency gains on math reasoning + code generation.

**What's settled now:** memory is **the production-grade eval axis**, not a research curiosity. The Oct 2025 wave (`mem-agent`, `MemoryAgentBench`, `MemoryArena`, `Mem2ActBench`) crystallized the measurement framework; the Dec 2025 → Mar 2026 wave gave the architecture + consistency framing. 2026-Q4 agents will be *rated* on memory the same way they're rated on tool-use.

**Sources:**
- [arXiv:2512.13564 — Memory in the Age of AI Agents (abs)](https://arxiv.org/abs/2512.13564v1) `[primary]`
- [arXiv:2512.13564 — PDF](https://arxiv.org/pdf/2512.13564) `[primary]`
- [HuggingFace Papers — Memory in the Age of AI Agents](https://huggingface.co/papers/2512.13564) `[primary]`
- [arXiv:2603.10062 — Multi-agent memory as computer-architecture problem](https://arxiv.org/pdf/2603.10062) `[primary]`
- [arXiv:2508.08997v2 — Intrinsic Memory Agents](https://arxiv.org/abs/2508.08997v2) `[primary]`
- [arXiv:2603.23234 — MemCollab](https://arxiv.org/abs/2603.23234) `[primary]`
- [FuguMT paper check — Memory in the Age of AI Agents JP summary](https://fugumt.com/fugumt/paper_check/2512.13564v1) `[analysis]`

### Why it matters to you

- **Job lens:** Agent-memory engineering is **the specialization slot** inside the "AI Integration Engineer" track (per [2026-05-16/05](../2026-05-16/05-career-and-startup.md#1-integration-engineer) and [ME.md focusing decision](../ME.md)). Three sub-roles that are now hiring: **memory-system designer** (design the eval + persistence strategy — Mem0 / EverMemOS / Letta ecosystems), **memory-eval author** (write test suites that probe consolidation + forgetting + consistency across runs), **memory-infra SRE** (vector-store ops, retrieval, latency). All three are specializations within a role that already exists; add the specialization slot in your title.
- **Startup lens:** The **multi-agent memory consistency** problem is the next 10-month wedge. The analogy: eventual consistency in distributed DBs was a wedge from 2010-2015 that spawned Cassandra, Dynamo, CockroachDB. Multi-agent memory consistency is the same shape — now funded, now ventureable. Three plausible company shapes: **"ACID for agent memory"** (strong-consistency primitives), **"CRDT for agent beliefs"** (eventual-consistency, mergeable updates), **"audit log for agent memory"** (compliance play — "show every change this agent remembered or forgot").
- **Insight:** The arXiv:2603.10062 "memory as architecture" paper is **the paper to cite in interviews this quarter.** Three-layer hierarchy = L1 working, L2 episodic, L3 semantic/long-term. Interview trick: when asked to "design an agent with memory," draw this three-layer hierarchy, then specify consolidation + consistency policy per layer. The answer immediately reads as "has done the reading."

→ Cross-link: [`05` §1 memory-eng career lane](./05-career-and-startup.md#1-hiring-map).

---

## 3. Project Suncatcher — the orbital TPU prototype and what it means {#3-suncatcher-infra}

**What happened:** Google's **Project Suncatcher M1** prototype satellite launched on **SpaceX Transporter-18 (Oct 1, 2026)** from Vandenberg. Specs:

- **Payload:** 4× TPUs on board.
- **Workload:** runs **Gemma** for **15 minutes at a time** (heat-management constraint).
- **Pretending-to-work mission:** 1-year validation of launch vibration + radiation + temperature-swing tolerance.
- **Comms:** laser inter-sat links (demo bench: 800 Gbps per direction, 1.6 Tbps total between one pair).
- **Confirmed telemetry:** satellite operating as expected (per Travis Beals, Suncatcher senior director, post-launch).
- **Follow-on:** two more satellites planned 2027 to test cluster connectivity.

**Why this matters as research:** Suncatcher is **the first large-scale orbital test of an AI accelerator architecture.** The engineering question isn't "will the TPU work in space" — Starcloud already demonstrated an H100 running in orbit last November. The research question is **"can a cluster of orbital accelerators scale as a usable compute mesh"** given (a) solar power density advantage (Google claims up to 8× over Earth), (b) laser-link reliability, (c) orbital-mechanics drag + attitude control. Starcloud + Google + reported SpaceX "orbital AI compute satellites" (expected 2028 deployment per Musk) are now a three-horse race.

**Sources:**
- [GPB — Google launches Project Suncatcher, a step towards AI data centers in space](https://www.gpb.org/news/2026/10/01/google-launches-project-suncatcher-step-towards-ai-data-centers-in-space) `[secondary]`
- [OPB — Project Suncatcher launch coverage](https://www.opb.org/article/2026/10/01/google-launches-project-suncatcher-a-step-towards-ai-data-centers-in-space/) `[secondary]`
- [TechRepublic — Google Aims to Power AI Data Centers from Space](https://www.techrepublic.com/article/news-google-project-suncatcher/) `[secondary]`
- [Free Press Journal — First Prototype Satellite With Four AI Chips](https://www.freepressjournal.in/tech/ai-data-centres-in-space-google-launches-first-prototype-satellite-with-four-ai-chips-into-orbit) `[secondary]`
- [Gizmodo — Google's Project Suncatcher is sending AI chips into space](https://gizmodo.com/googles-project-suncatcher-is-sending-ai-chips-into-space-2000816985) `[secondary]`
- [Gigazine — Google Project Suncatcher proposal](https://gigazine.net/gsc_news/en/20251105-google-project-suncatcher) `[secondary]`
- [MIT Sloan ME — Google Tests Space-Powered AI With Solar Satellites](https://www.mitsloanme.com/?p=9675) `[analysis]`

### Why it matters to you

- **Job lens:** The **AI-infrastructure career lane** (per [ME.md adjacent track](../ME.md) — GridCARE / Crusoe / Sphere AI) now has an *orbital* sub-category. Low-competition because physics-tolerant engineers are not applying to AI startups and AI engineers aren't applying to space companies. **Named orgs to watch:** Starcloud, Google X (Suncatcher), Planet Labs (co-building the Suncatcher satellite), SpaceX "orbital AI compute" team. If you have *any* RF, orbital mechanics, radiation-hardened electronics, or satellite-ops background, the hiring is now active.
- **Startup lens:** The near-term application: **"space-rated TPU/GPU validation-as-a-service"** — a lab that stress-tests off-the-shelf AI accelerators for radiation tolerance, thermal cycling, vacuum compat. Pre-launch validation. $10K per chip. The deeper lane: **"orbital AI compute marketplace"** — if Starcloud + SpaceX + Google each ship clusters, there's a brokerage opportunity similar to Lambda Labs / Vast.ai on Earth.
- **Insight:** The *under-weighted* framing: this is **the first time compute location becomes a research variable.** Latency to orbit (~30ms LEO one-way) is already better than many trans-pacific cloud hops; the solar-power advantage is physical and permanent. The next 24 months of compute-cost competition between Earth and orbit is going to produce *measurable* decisions — "which workloads route to space" becomes a routing axis in 2028. Your router's `location` field is now not just "us-east-1 vs eu-west-1" — it's "ground vs orbit."

→ Cross-link: [`03` §3 the weekend router artifact](./03-practical-skills-and-tools.md#3-weekend-artifact) — add a `location` axis to the router schema for the long view.
