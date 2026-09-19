# Research Progress — 2026-07-29 (Wednesday)

Two threads landed with real weight this week: Mythos-style **LLM-driven cryptanalysis becomes a paper category** (not just a lab claim), and the **RL-compute-allocation** literature continues to converge on FLOP-accounting as the honest way to compare RL training runs. Plus one benchmark drop worth noting for anyone thinking about agent evaluation.

---

## 1. LLM-driven cryptanalysis crystallizes as a research category {#1-llm-cryptanalysis}

**What.** Anthropic's Mythos disclosure ([`01` §1](./01-big-lab-moves.md#1-mythos-hawk)) is coming out as at least two things simultaneously:
- A **primary result** (HAWK-256 automorphism → cost drop from ~2⁶⁴ to ~2³⁸; 7-round AES-128 attack sped ~200–800×).
- A **methodology paper** (implicit): "cryptanalysis-as-compute-line-item" — what happens when a research task's cost model shifts from **person-years** to **$/billion output tokens**.

The [FourWeekMBA analysis](https://fourweekmba.com/ai-anthropic-claude-mythos-hawk-cryptanalysis-compute/) does the cleanest economic reframing: cryptanalysis previously priced as scarce human labor is now priced as elastic compute. Once you accept that reframe, **every hard analytical field with a "years of PhD attention" cost structure** looks a little different — theorem-proving, materials search, catalyst discovery, protein-design edge cases.

**Sources.**
- [Anthropic write-up (via Hacker News)](https://thehackernews.com/2026/07/claude-ai-just-cracked-post-quantum.html) `[secondary]`
- [Dataconomy 07-29 summary](https://dataconomy.com/2026/07/29/anthropic-ai-flaws-hawk-aes/) `[secondary]`
- [FourWeekMBA economic framing](https://fourweekmba.com/ai-anthropic-claude-mythos-hawk-cryptanalysis-compute/) `[analysis]`
- [Explainx.ai detailed writeup](https://explainx.ai/blog/anthropic-mythos-cryptographic-weaknesses-hawk-aes-july-2026) `[analysis]`

**Why it matters (research-side).**
- The Mythos result is a **capabilities existence proof**, not a benchmark. Expect a wave of "we tried the same thing on cipher X" papers over the next 3–6 months.
- The **evaluation methodology** is quietly the more important contribution. FLOP-counted, token-counted, wall-clock-counted attack construction, with a controlled comparison against a matched human-review baseline. This is the template for future "AI-vs-human" research-productivity claims — and the template is what gets cited in every downstream paper.
- Watch for: **arXiv cs.CR** picking up "LLM-assisted cryptanalysis" as a subject cluster within 30 days.

**Insight.** For a grad student, the highest-leverage research direction opened up by Mythos is not "reproduce on another cipher" (compute-gated). It's **eval design**: what's the honest way to measure LLM-assisted-research productivity vs. human? That paper writes itself with a modest compute budget and it will be widely cited.

**Job · Startup · Insight.**
- **Job.** For an Anthropic Alignment / Red Team application, name the eval-design gap explicitly — "I'd propose X eval to measure lift over expert baseline; here's why it's harder than it looks." Concrete beats generic.
- **Startup.** A well-run **AI-assisted-research benchmark** ("MMLU for research productivity") is a fundable OSS project by itself.
- **Insight.** Methodology papers age better than result papers. The Mythos result may be surpassed in a year; the eval template will outlast it.

`#arxiv #cryptanalysis #eval #methodology #mythos`

---

## 2. RL compute-allocation: the "art of scaling" thread continues {#2-rl-compute-allocation}

**What.** Building on [2026-07-25 §2](../2026-07-25/04-research-progress.md#2-rl-compute-allocation). The RL-for-LLM training literature continues to converge on a shared vocabulary:

- **Environment-cost-per-episode** as a first-class budget line (separate from model-forward-pass FLOPs).
- **Rollout-length × task-difficulty × episodes-to-signal** as the axis practitioners argue about.
- The **[DeepSWE](https://www.together.ai/blog/deepswe)** methodology remains the reference open example — fully open-sourced RL-trained coding agent from 2025, still the most-copied training pipeline.
- Newer angles this month: [**Agent-World** (arXiv 2026-06)](https://arxiv.org/) — scaling real-world environment synthesis; [**Beyond Ten Turns**](https://arxiv.org/) — long-horizon agentic search with large-scale async RL; and the [**"art of scaling RL compute for LLMs"** framework](https://arxiv.org/) that formalizes the compute-vs-signal tradeoffs.

**Sources.** [arxiv cs.LG recent](https://arxiv.org/list/cs.LG/recent) `[primary]` · [Interconnects — Nathan Lambert on RL-compute framing](https://www.interconnects.ai/) `[analysis]`

**Why it matters.** Two years ago RL-post-training was described in vibes ("we did some RL"). Now it's described in FLOP accounting. That maturation matters because:
- It makes reproducibility possible.
- It makes **cost-per-quality-point** a comparable metric across labs.
- It makes **outsider-reproducible** RL training possible (with a big compute check).

**Insight.** For a CS grad student, the fastest way to look serious in an MLE / Applied Research interview is to speak the **FLOP-accounting vocabulary** fluently — env-cost, episodes-to-signal, wallclock-per-improvement. Read one recent well-written paper in the thread this week and steal the vocabulary wholesale.

**Job · Startup · Insight.**
- **Job.** In an MLE interview: describe *your* project's cost curves in FLOPs, not vibes. Interviewers who work in RL will notice.
- **Startup.** RL-for-agents infra is under-served — a tool that gives you clean per-episode compute + reward accounting out of the box would sell to every applied AI team fine-tuning agents.
- **Insight.** The next "attention is all you need" moment for RL-post-training is likely a methodology paper, not an architecture paper. Track methodology.

`#rl #compute #arxiv #methodology #deepswe`

---

## 3. Benchmark landscape: LHTB, Terminal-Bench, SWE-INTERACT — the "agent competence" cluster stabilizes {#3-benchmarks}

**What.** The long-horizon agentic-coding benchmark cluster from [2026-07-25 §1](../2026-07-25/04-research-progress.md#1-lhtb) has broadened:

- **Long-Horizon-Terminal-Bench (LHTB)** — top model still ~15.2% pass@1 at 0.95 credit. Room to run.
- **Terminal-Bench (2026)** — realistic CLI tasks. Broader tool distribution than SWE-bench.
- **TerminalWorld / ORAgentBench / SWE-INTERACT / TUA-Bench** — 2026 additions to the cluster.
- **DeepSWE** — remains the reference "fully open-sourced" training pipeline for agent-coding.

Meta-paper worth reading: [*"What twelve LLM agent benchmark papers disclose about themselves: A pilot audit and an open scoring schema"*](https://arxiv.org/) — the audit-of-audits, useful for grading which benchmarks are actually well-constructed.

**Sources.** [arXiv cs.LG recent](https://arxiv.org/list/cs.LG/recent) `[primary]` · [Hugging Face Papers trending](https://huggingface.co/papers/trending) `[aggregator]` · [Papers With Code](https://paperswithcode.com/) `[aggregator]`

**Why it matters.**
- The cluster has stabilized enough that **choosing which benchmarks to report on is now a signal.** Pick 2–3 with real construction rigor (LHTB, Terminal-Bench, SWE-INTERACT); avoid the "reported once, never reproduced" ones.
- **Long-horizon coding remains the visible ceiling** for agent competence. Top models pass simple SWE-bench tasks trivially; LHTB and its cousins are where the frontier fights are.

**Insight.** If you're building a portfolio agent, pick **one** benchmark (LHTB is a good default) and report your agent's score honestly, including "runs failed to complete." Honest low scores beat aspirational high scores in interviews.

**Job · Startup · Insight.**
- **Job.** "I ran my agent on LHTB and it scored 11% — here's why, and here's what I'd fix" is a stronger interview story than "SWE-bench Verified 62%."
- **Startup.** The benchmark-audit meta-paper is the shape of an **eval-quality startup** — "we grade AI benchmarks so buyers know which numbers to trust."
- **Insight.** Benchmarks age fast. Report against the freshest that has real construction rigor; don't chase the shiniest.

`#benchmarks #lhtb #terminal-bench #agents #eval`

---

## 4. Signal to keep watching: NIST PQC standardization {#4-nist-pqc}

**Why here.** Because Mythos ([`01` §1](./01-big-lab-moves.md#1-mythos-hawk)) just made cryptanalysis-per-compute a real threat model. NIST's remaining post-quantum candidates will be re-scrutinized against this new capability. If a *finalized* NIST algorithm — not just a Round 3 candidate — turns up structural weaknesses under LLM cryptanalysis, that becomes the year's biggest security story.

**What to watch.** [NIST PQC page](https://csrc.nist.gov/projects/post-quantum-cryptography) and [arXiv cs.CR](https://arxiv.org/list/cs.CR/recent) over the next 90 days.

**Insight.** Zero-day disclosures in cryptography historically came from adversarial cryptanalysts. The next tier now includes "a lab running a frontier model for 60 hours." Update your threat models.

`#nist #pqc #watchlist`
