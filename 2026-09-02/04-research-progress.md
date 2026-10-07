# Research Progress — 2026-09-02

Fewer big-paper landings than the July fortnight, but the **structural stories are louder**: **Astra's Preparedness-tier trigger** ([`01` §4](./01-big-lab-moves.md#4-astra)) is a research event as much as a product one; **Berkeley RDI's benchmark-gaming audit** casts a shadow over every SWE-bench/TB2.1 number in this edition; **DeepSeek V4-Pro-0813 + Qwen3.8-Max** landed with a level of engineering polish that argues the open-weights side is now doing genuinely useful post-training research in public; and **Jeff Dean's Discovery Loop** ([`01` §5](./01-big-lab-moves.md#5-google-reorg)) is the highest-profile bet on **autonomous scientific-discovery agents** as a research direction of its own.

Tags: `#arxiv #benchmarks #agents #cyber #preparedness #open-weights #interpretability #discovery-agents`

---

## 1. OpenAI Astra: first "Critical" cyber tier — what it means as a research event {#1-astra-research}

**Release:** [OpenAI — Path to Astra](https://openai.com/index/path-to-astra/) and [Responding to next-frontier critical cyber capabilities](https://openai.com/index/responding-next-frontier-critical-cyber-capabilities/) (both 2026-08 → 09-01).

**Claim in one sentence:** Astra is the first frontier model that **discovers new zero-day vulnerabilities in the wild during eval**, resolves **10 open problems in math + TCS**, and hits **100% on ExploitBench** — tripping the Preparedness Framework's "Critical" cyber tier and forcing OpenAI's first real gated-alpha release (Daybreak Blue).

**The delta:**
- **Concrete threshold** — Preparedness-tier language now attaches to a real model, not a hypothetical. Enterprise procurement will demand tier labels within one quarter.
- **Dual-use pattern** — the model is **capable of discovering vulnerabilities** but *trained* to refuse to build exploits. Mirrors the Anthropic Fable/Mythos 5.1 split; **capability isn't restricted, use is**.
- **Solved-problem list** as the real signal — 10 open problems in math + TCS in one internal deployment is *not* a benchmark; it's a research-productivity claim that will drive competitor product roadmaps.

### Why it matters to a builder
- **The vocabulary of gated-alpha ("Critical tier," "Daybreak Blue")** is now the *canonical* way procurement discusses risk with a frontier lab. Know the tiers before your competitors do.
- **"Refuse to build exploits"** is the fine-grained-usage-policy pattern of 2026 — expect Anthropic Mythos-track to publish an equivalent taxonomy this quarter.
- **Solved-open-problems** as an eval — expect a wave of "science leaderboards" (MathBench, TCS-Open, and Anthropic's Frontier Math Bench) to sharpen the *actual* frontier signal. Watch for one from Google DeepMind + Kavukcuoglu's reorged team.

---

## 2. Anthropic's ~$71B compute commitment as a research-capacity signal {#2-anthropic-compute-research}

**Release:** Announced/aggregated pre-TechCrunch Disrupt 2026, week of 2026-08-27. See [`02` §6](./02-new-emerging.md#6-anthropic-compute).

**Claim in one sentence:** Anthropic has locked in roughly **$71B** of multi-year compute — one of the largest disclosed compute books in the industry — implying training-run and post-training capacity through **2028**.

**The delta:**
- Puts Anthropic's Colossus rental ([2026-05-21](../2026-05-21/)) + Google TPU deal ([2026-05-08](../2026-05-08/)) in a **single balance-sheet frame**.
- On a rough mass-production basis, that supports **multiple Opus-6-class training runs plus post-training + evals + Frontier Red Team + Applied Research infra** over the horizon.
- Signal for pre-IPO investors: **capacity certainty into 2028**, not just capital raise size.

**Sources:**
- [TechCrunch Disrupt 2026 announce](https://techcrunch.com/2026/08/27/anthropic-and-openai-are-joining-the-ai-stage-at-techcrunch-disrupt-2026/) `[secondary]`
- Aggregator: [note.com — Anthropic compute commitment](https://note.com/kuro_ai_note/n/nacf98c6bf435?hl=en) `[aggregator]` — treat the $71B as `[secondary]` pending Anthropic IR confirmation.

### Why it matters to a builder
- Multi-year compute at that scale is the biggest **on-ramp expansion for Fellows / Applied Research** hires in Anthropic's history. Cohort sizes for Fellows Nov / Jan / Aug 2027 will likely grow; timing your app against that is real signal.
- **Post-training capacity as a moat** — the [SLAI T-Rex](../2026-07-25/04-research-progress.md#5-slai-t-rex) MFU numbers already argued mid-team domain fine-tunes can beat general frontier models on their turf. Anthropic buying more compute doesn't invalidate that thesis — it says **the lab expects to spend more on RL post-training + specialized runs**, not just base pretraining.

---

## 3. DeepSeek V4-Pro-0813 + Qwen3.8-Max as post-training research {#3-open-weights-research}

**Release:** [`02` §2](./02-new-emerging.md#2-open-weights).

**Research-relevant claims (as reported):**
- **DeepSeek V4-Pro:** 1.6T MoE / 49B active, 1M ctx, MIT-licensed. **80.6% SWE-bench Verified**, **87.9 Terminal-Bench 2.1**, **62.7 DeepSWE**. Uses a **verifier-guided RL post-training** stack (per model card) — the strongest public replication of the "verifier-in-the-loop" RL pattern from the [chess-scaling paper](../2026-07-25/04-research-progress.md#3-chess-scaling).
- **Qwen3.8-Max:** 2.4T sparse MoE. Vendor-reported **86.6 TB2.1**, **92.6 GPQA-Diamond**. Alibaba's public post highlights "reasoning-effort routing" as a new inference-time knob — mirror of Anthropic's `effort` API.

**Sources:**
- [Morph — DeepSeek V4 technical write-up](https://www.morphllm.com/deepseek-v4) `[secondary]`
- [StartupHub — Qwen3.8-Max analysis](https://www.startuphub.ai/ai-news/artificial-intelligence/2026/qwen3-8-27b-challenges-gpt-5-6-and-deepseek-v4-in-benchmarks) `[aggregator]`
- [LLMGateway model timeline](https://llmgateway.io/timeline) `[aggregator]`

### Why it matters to a builder
- **Verifier-guided post-training is portable engineering knowledge now.** If you have a symbolic verifier for your domain (SQL, LEAN, TLA+, SMT, SVG-DSL, JSON-schema-satisfaction), you can bootstrap a domain-expert small model from a strong open-weights base for **thousands of dollars, not millions**. Real startup wedge — see the [SLAI T-Rex OR-tasks recipe](../2026-07-25/04-research-progress.md#5-slai-t-rex) for the playbook.
- **Inference-time effort routing appearing in a Chinese open-weights model** confirms the [Opus 5 effort toggle](../2026-07-25/03-practical-skills-and-tools.md#1-opus-5-effort) is becoming an **industry pattern**, not an Anthropic-only design choice. Build your telemetry columns for effort now — you'll want to reuse them across providers.

---

## 4. Discovery Loop and the "autonomous scientific-discovery agent" thesis {#4-discovery-loop}

**Release:** Jeff Dean's announced departure ([`01` §5](./01-big-lab-moves.md#5-google-reorg)) — Discovery Loop targets autonomous scientific discovery as its core product.

**Research context:** Threads pointing at Discovery Loop's likely direction:
- **Anthropic's "Dreaming" internal research technique** (May–Sep 2026) — long-horizon self-play + hypothesis generation for open scientific problems.
- **Anthropic Frontier Red Team + Andon Labs Project Pilot** (July) — established the "sim + real experiment" evaluation shape for embodied agents.
- **The [chess-scaling paper](../2026-07-25/04-research-progress.md#3-chess-scaling)** — showed **pretraining-loss-as-a-predictor** for downstream RL gains in a fully verifiable environment.
- **[SLAI T-Rex OR-tasks recipe](../2026-07-25/04-research-progress.md#5-slai-t-rex)** — the exact template for **solver-verified synthetic SFT + verifier-guided RL** on a specialized domain.

### Why it matters to a builder
- **The unstated bet** — Dean is betting **autonomous scientific-discovery agents** will be a durable category, not a Google-integrated feature. Watch for the first funded competitors within 60 days.
- **The plausible wedges** — literature-agent tooling, experiment-planning agents, scientific-verifier chains, domain-specific solver harnesses. All of them **compose with MCP + verifier-guided post-training** — the exact stack you're already investing in.
- **Public "solved open problem" tracking** — as more labs publish "we solved this open problem autonomously" claims (Astra, Discovery Loop, Anthropic pilots), the community will need a **verified list**, akin to the AI-conjecture archive. Owning that archive is a founder-shaped play.

---

## 5. Berkeley RDI: eight major agent benchmarks are gameable {#5-benchmarks-gameable}

**Paper / audit:** UC Berkeley's Center for Responsible Decentralized Intelligence, 2026 report (surfaced via commentary from Morph, Automation Anywhere). The audit shows **SWE-bench Verified, Terminal-Bench, WebArena, OSWorld, GAIA, FieldWorkArena** and two others can be **pushed to near-perfect scores without solving tasks** via:
- Leaked reference answers.
- Unsanitized `eval()` in scoring functions.
- Prompt-injectable LLM judges.
- Scoring functions that skip correctness.

**Sources:**
- [Morph — Best AI Coding Agents 2026 (benchmark critique)](https://www.morphllm.com/best-ai-coding-agents-2026) `[analysis]`
- [Automation Anywhere — AI agent benchmarks primer](https://www.automationanywhere.com/company/blog/ai-agent-benchmarks) `[analysis]`

### Why it matters to a builder
- **"Agent + model" is the unit, not "model."** DeepSeek V4-Pro's 87.9 TB2.1 and Qwen3.8's 86.6 TB2.1 should be read as claims about the *harness* as much as the model; the same is true for Claude Opus 5's 96% SWE-bench Verified when reported by Anthropic. Ask "which harness, which prompt, which judge" before quoting the number in an interview.
- **This is the single most defensible line to have in your portfolio README:** *"I ran evals X and Y with harness details disclosed and the LLM judge audited for prompt injectability."* If your writeup can point to Berkeley's audit and say **"here's how I avoided each failure mode"**, you dominate every candidate who just quotes the vendor number.
- **The wedge** — verified, uncheatable evaluation harness-as-a-service is a legitimate startup category. Expect at least one YC S26/W27 company to occupy it explicitly.

→ Cross-link: [`03` §5 how the weekend artifact bakes in the audit's mitigations](./03-practical-skills-and-tools.md#5-weekend-artifact) · [`02` §2 vendor-reported number caveat](./02-new-emerging.md#2-open-weights).

---

## 6. Also worth knowing (adjacent, cited for context)

- **Simon Willison — "Confused environment" attacks (2026-08-30).** A new class of prompt injection where a system prompt from context A leaks its authority into a hostile context B. Read before shipping any agent that touches customer data. → [simonwillison.net](https://simonwillison.net/2026/Aug/6/) `[primary]`
- **EU AI Act GPAI transparency rules live (2026-08-02).** GPAI providers must publish a training-data summary and transparency reports; first real filing cycle Q4 2026. → [EU Commission — AI Act GPAI](https://digital-strategy.ec.europa.eu/en/policies/ai-act) `[primary]`
- **[LHTB (2026-07-11)](../2026-07-25/04-research-progress.md#1-lhtb) is still the eval floor for hours-long agent tasks** — no new competitor benchmark landed in the six-week gap. Frontier agents remain **low-teens pass@1** at 0.95 credit. Continue to point to LHTB in every "solves real work?" conversation.
- **Anthropic Fable 5.1 "vulnerability discovery, no exploit build"** ([`01` §2](./01-big-lab-moves.md#2-fable-5-1)) mirrors the Astra dual-use pattern — expect a formal Anthropic Responsible Scaling Policy update in the next 30 days.

→ Cross-link: [`03` §1 the effort-matrix as a compiler-level primitive](./03-practical-skills-and-tools.md#1-fable-matrix) · [`05` §1 the Fellows track that hires on exactly this vocabulary](./05-career-and-startup.md#1-fellows-hackathons).
