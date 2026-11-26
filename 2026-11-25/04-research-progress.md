# Research Progress — 2026-11-25

Five threads worth your reading-list slot: **Agentic Reasoning Caching** (ARCs) is the first serious attempt to decouple reasoning quality from GPU cost for repeat workloads; **MINTEval** gives us a public benchmark for memory under multi-target interference; **ARIS** keeps the adversarial-multi-agent research-agent line going; and **AlphaGenome 2** signals Alphabet's "AlphaFold playbook" is accelerating, not slowing. One editorial note at the bottom: **primary-source reading of papers is now a hireable career habit**, not optional.

Tags: `#arxiv #efficiency #agents #memory #bio #alphagenome`

---

## 1. Agentic Reasoning Caching (ARCs) — compile LLM reasoning traces into CPU-executable caches {#1-arcs}

**Paper:** arXiv **2611.09891** — *"Agentic Reasoning Caching: Robust CPU-Executable Caches from LLM Reasoning Traces"* (Nov 6, 2026).

**What's new:**
- Traditional approach: an agent queries a frontier LLM for every reasoning step at inference time → cost scales linearly with traffic.
- ARCs approach: **collect reasoning traces** from an initial LLM-powered run, **compile them into a robust decision-cache data structure** that runs on a **CPU without an LLM call** for a bounded family of inputs.
- The authors claim the cache **generalizes** across input variants of the same task class (not just key-value lookup) via a trace-generalization step.
- Target workloads: **customer support, structured extraction, recurring ops queries, policy lookups** — anything where the input distribution is bounded.

**Sources:**
- [arXiv 2611.09891 (papers.cool entry)](https://papers.cool/arxiv/2611.09891) `[primary]`

### Why it matters to you

- **Job lens:** **Cost-aware agent design is now a distinct research + eng lane.** ARCs-style work is exactly the kind of project that reads as a serious portfolio artifact for **MLE roles at inference-first companies (fal, Modal, Baseten, Together)** and **FDE roles where unit economics matter**. If you can replicate even a toy version of this paper on a public benchmark, that's a résumé line.
- **Startup lens:** **If this technique generalizes, it reprices the "every agent needs a frontier model" assumption** and opens a product category: **"agentic workload caches"** that sit in front of model APIs and redirect bounded-input traffic to CPU. First-mover wins the enterprise integrator deal.
- **Insight:** **Watch replication attempts on HumanEval+ / LiveCodeBench / SWE-bench Verified.** If the cache survives cross-dataset evaluation, this is a paper that gets cited into production playbooks within 6 months. If it fails to generalize, it's an interesting negative result on trace generalization.

**Attempt it yourself:** Pick one bounded task (e.g., a compliance-checking workflow or a receipt-extraction pipeline). Run Claude Fable 5.2 on 500 examples. Store full traces. Attempt to compile a 5-rule decision tree from the traces. Measure accuracy loss vs. cost savings. **One weekend experiment** — publishes as a GitHub repo you can point at.

→ Cross-link: [`03` §3 — weekend artifact: the MCP server is the easier shipment](./03-practical-skills-and-tools.md#3-mcp-weekend-artifact)

---

## 2. MINTEval — memory under multi-target interference in long-horizon agent systems {#2-minteval}

**Paper:** *"MINTEval: Evaluating Memory under Multi-Target Interference in Long-Horizon Agent Systems"* (2026). Listed as a top paper on the awesomepapers.io trending page; exact arXiv ID not confirmed via search — verify before citing.

**What's new:**
- Prior memory benchmarks (Long-Lived Agent Memory benchmark from our 2026-11-14 edition, Mem-α) tested **retrieval under single-target drift**.
- MINTEval introduces **multi-target interference**: an agent must retrieve + act on **several concurrent task threads** that **mutually overwrite each other's context** across long horizons.
- First benchmark to **explicitly measure cross-task interference**, not just long-context retention.

**Sources:**
- [awesomepapers.io — LLM topics trending](https://awesomepapers.io/llm-papers/topics/LLMs) `[aggregator]`
- [Hugging Face awesome-ai-agent-papers dataset](https://huggingface.co/datasets/molmohsen/awesome-ai-agent-papers) `[aggregator]`

### Why it matters to you

- **Job lens:** Multi-tenant / multi-task agent systems are **exactly the workloads enterprise FDE roles have to deploy**. A customer runs 3 ChatOps agents simultaneously → they interfere. Knowing the benchmark names the interference problem gives you the vocabulary to ask the right questions in an interview.
- **Startup lens:** **Any agent orchestration product (Sierra, Decagon, Rox, Harvey) will adopt MINTEval-flavored evals internally within two quarters**. Build a product that **ships with a measurable MINTEval score**, not just a demo.
- **Insight:** **Memory benchmarks are the new reasoning benchmarks.** Where 2024 was HumanEval and 2025 was SWE-bench, 2026 is multi-task memory under interference. Track **MINTEval, MemReread, Long-Lived Agent Memory** as the triangulation set.

→ Cross-link: [`02` §2 — Model ML will need this for financial workflow agents](./02-new-emerging.md#2-model-ml)

---

## 3. ARIS — Autonomous Research via Adversarial Multi-Agent Collaboration {#3-aris}

**Paper:** *"ARIS: Autonomous Research via Adversarial Multi-Agent Collaboration"* (2026). Top entry on awesomepapers.io LLM trending.

**What's new:**
- Extends the "multi-agent research assistant" pattern (seen in OpenAI Deep Research, Google Research Pro) with an **adversarial inner loop** where one agent **attempts to falsify** another agent's claims before publication.
- Claims improved factual precision on open-ended research tasks vs. non-adversarial baselines.
- Builds on **ARIS-Bench** from our 2026-05-19 edition (same research group).

**Sources:**
- [awesomepapers.io — LLM topics trending](https://awesomepapers.io/llm-papers/topics/LLMs) `[aggregator]`

### Why it matters to you

- **Job lens:** **Adversarial multi-agent architectures are the "hot code pattern" of 2026Q4–2027Q1**. You'll see them in interview take-home prompts. Build a toy version: a draft-writer agent + a critic agent with explicit "find-a-flaw" prompting. Takes 30 minutes with Claude Fable 5.2.
- **Startup lens:** Any product where **output trust matters** (legal, financial, medical) should have an **adversarial-critic layer baked in**. This is the architecture pattern **Harvey, Hippocratic, and Isomorphic will converge on in 2027**. If you're building in a trust-sensitive vertical, ship this now.
- **Insight:** **The ARIS pattern is a specific application of the general insight that "self-consistency doesn't catch systematic bias; adversarial critique does."** Keep this phrase ready for an interview — it's a hireable framing.

→ Cross-link: [`03` §4 — source-tiering is the same adversarial-critic habit for humans](./03-practical-skills-and-tools.md#4-source-tiering)

---

## 4. AlphaGenome 2 + science-first foundation models {#4-science-first-models}

**Context.** AlphaGenome 2 was introduced in the 2026-11-11 Alphabet / DeepMind cluster (see 2026-11-14 edition). It predicts how **DNA variants affect specific human cell types** for disease / drug-discovery use.

**Why this reappears today:**
- **Isomorphic Labs $5B Series C** closed on Nov 16 (see [`02` §1](./02-new-emerging.md#1-isomorphic-5b)).
- Alphabet's **"AlphaFold playbook" — narrow, domain-specific scientific foundation models with open-ish research access** — now has at least four consecutive successful case studies: AlphaFold → AlphaGenome → AlphaProteo → AlphaGenome 2.
- **No other frontier lab has shipped four consecutive science-first foundation models with this cadence.**

**Sources:**
- [SiliconReport — Google DeepMind Gemini Robotics 2.5 + AlphaGenome 2](https://www.siliconreport.com/google-deepmind-introduces-gemini-robotics-2-5) `[secondary]` (via 2026-11-14 edition)
- [AI Funding Tracker — Isomorphic Labs $5B Series C](https://superpowerdaily.com/signals/funding) `[aggregator]`

### Why it matters to you

- **Job lens:** **Google DeepMind's science track + Isomorphic Labs + Xaira + EvolutionaryScale + Latent Labs** is the **highest research-adjacent hiring density** right now for a CS grad with any biology/chemistry adjacent coursework. Google specifically hires from a **narrower network than Anthropic/OpenAI** here — a published arXiv co-authorship or a Kaggle structural-biology competition record can clear a loop.
- **Startup lens:** The playbook is replicable but not easily. **Narrow domain foundation models that beat specialist baselines → wet-lab validation → enterprise licensing to pharma**. If you're incubating around a domain-specific CS problem (geospatial, climate, materials), the Alphabet model is the one to study.
- **Insight:** **"Science-first foundation models" are the single clearest escape hatch from the ANT-triggered multiples compression.** The capital is pricing them on scientific milestones, not revenue multiples (see [`02` §1](./02-new-emerging.md#1-isomorphic-5b)).

→ Cross-link: [`02` §1 — Isomorphic $5B](./02-new-emerging.md#1-isomorphic-5b)

---

## 5. Primary-source reading as a weekly career habit {#5-primary-source-habit}

**The practice.** Spend **30 minutes every Friday reading one arXiv paper end-to-end** — abstract → intro → method → results. Not twenty abstracts. One paper.

**Why Friday specifically.** You come into Monday having absorbed one real idea, which you then recognize throughout the next week's industry noise. This compounds **enormously** over 6 months — you build a map of research threads that others only see through the *N*-th-hand summary filter.

**What to pick.** One of:
- The paper underneath whatever viral tweet thread showed up this week.
- The paper your dream company's research team published this quarter.
- The paper that an engineer at Anthropic / OpenAI / DeepMind quote-tweeted with "huge if true" or equivalent.
- An ARCs replication (if you want to make it an experiment-plus-read Friday).

**Signal when you interview.** "I read [paper] last week. What I found interesting is [specific claim]. The question I'd ask is [specific gap]." **This literally wins the "are you intellectually curious" screen** every time, because 95% of applicants haven't read a paper end-to-end in 6 months.

**Build a repo for it.** `github.com/<handle>/paper-notes` — one `.md` per paper, three sentences max: (1) claim, (2) method highlight, (3) question. Public. Links to arXiv. **This is a dripping-public-asset that recruiters find when they check your GitHub.**

→ Cross-link: [`03` §4 — source-tiering + `[rumor]` vs `[primary]`](./03-practical-skills-and-tools.md#4-source-tiering) · [`05` §4 — portfolio target update](./05-career-and-startup.md#4-portfolio-target-list)

---

## Lens roll-up for Research Progress

- **Job:** ARCs + MINTEval + ARIS vocabularies all read as hireable depth in interviews. AlphaGenome 2 track opens a specific hiring lane most CS applicants won't target — advantage to you if you have *any* bio adjacency.
- **Startup:** ARCs is a potential startup category by itself (agentic workload caches). MINTEval evals should ship with your agent product. Science-first foundation models are the escape hatch from multiples compression.
- **Insight:** **Papers precede product by ~6–12 months.** Read one a week starting this Friday, and by April 2027 you'll have a 20-paper map that nobody else in your applicant cohort has.
