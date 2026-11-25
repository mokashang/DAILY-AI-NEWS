# Research Progress — 2026-11-21

A VLA-heavy week on arXiv, two monocular/4D vision papers worth noting (Apple **Depth Pro 2**, Shanghai AI Lab **π⁴**), and a provocative agent-self-improvement paper ("**Do LLM Agents Still Need to Be Told How to Self-Improve?**") that is the natural successor to last week's MRTPO. Two heavy-lift lab-blog reads: OpenAI's **"Research acceleration: the jagged frontier"** (companion to the Sept 6 Research-Intern post) and the **Anthropic Alignment Science** blog's November cluster — three posts on multi-agent resource sharing, red-teaming blocking monitors, and cross-model value trade-offs. One high-profile community claim (**"Riemann Hypothesis proof"** with Claude) is flagged `[rumor]` — do not quote.

Tags: `#arxiv #research #vla #depth #agents #alignment`

---

## 1. Gamer — generalist VLA for long-horizon real-time game agents (arXiv 2611.18397) {#1-gamer-vla}

**What the paper claims:**
- Collected **tens of thousands of hours of keyboard + mouse data** on 3D open-world games.
- Pipeline: **sparse-thinking SFT → multi-turn RL** on top of a VLA base; **cloud-edge inference engine** runs many simulator instances concurrently to parallelize rollout collection.
- Reports **skilled-player parity** on 3D open-world games.
- **146 upvotes on HF Papers**; v1 posted Nov 13, v3 Nov 18; 27 authors.

**Sources:**
- [arXiv 2611.18397 — Gamer](https://arxiv.org/abs/2611.18397) `[primary]`
- [Hugging Face Papers — trending](https://huggingface.co/papers/trending) `[primary]`

### Why it matters to you

- **Job lens:** **"VLA-style long-horizon agent + cloud-edge inference engine"** is a job description shape for mid-career MLE / applied-research roles at Runway, Physical Intelligence, DeepMind, and (quietly) Microsoft Research. If you've done *any* RL coursework, re-implement the inference-engine idea on a local gym environment, publish, cite Gamer. That's a live résumé line through Q1 2027.
- **Startup lens:** **Game-agent → game-automation → enterprise-task-automation** is the migration path a few startups will try in 2027 (a game environment is cheaper RL supervision than a real browser). Open question: can you train on games and deploy on productivity software? If anyone can, the demo-to-revenue arc is 9–12 months.
- **Insight:** **The cloud-edge inference engine abstraction is the real contribution, not the parity claim.** Parallel rollout collection is the bottleneck most RL-training code never solves well; a reusable engine would cut that cost 5–10× for everyone who adopts it. Watch for a GitHub release.

→ Cross-link: [`02` §2 — BrightAI physical AI](./02-new-emerging.md#2-brightai-noeri)

---

## 2. Apple Depth Pro 2 — metric monocular depth, images + video, sharp + temporally consistent (arXiv 2611.26603) {#2-depth-pro-2}

**What the paper claims:**
- Single neural network handles **images AND video at full resolution** with **metric** depth accuracy, **sharpness**, and **temporal consistency** jointly — the three usually come as a 2-of-3 trade-off.
- Authors include **Vladlen Koltun** and **Stephan Richter** (Apple ML Research).
- **Code and weights released.**
- Posted Nov 19.

**Sources:**
- [arXiv 2611.26603 — Depth Pro 2](https://arxiv.org/abs/2611.26603) `[primary]`

### Why it matters to you

- **Job lens:** **Depth Pro 2 is a drop-in dependency for VLA builders**, which means knowing its API and failure modes is interview material for Apple ML, Physical Intelligence, Figure, 1X, DeepMind robotics. Portfolio move: **rebuild a Depth Pro 2 integration into a small SLAM or AR demo**, post a short video, link it on your résumé.
- **Startup lens:** **High-quality monocular metric depth is a quiet "unlock" for consumer AR, drone photogrammetry, and inspection products** — tasks that used to require stereo rigs or LIDAR can be reconsidered. A startup wedge: **per-vertical AR tools that assume phone cameras only** (interior design, insurance claims, medical body-scan, construction progress).
- **Insight:** **Apple's ML Research cadence (Depth Pro → Depth Pro 2 in 18 months with open weights)** is the strongest signal in a while that Apple is serious about on-device-first AI. Expect the next WWDC to showcase Depth Pro 2 integrations in Vision Pro + iPhone — plan around it.

→ Cross-link: [`01` §2 — Rubin fastest ramp](./01-big-lab-moves.md#2-nvidia-huang-out)

---

## 3. π⁴ — foundation model for 4D scene geometry and motion (arXiv 2611.23144) {#3-pi-four}

**What the paper claims:**
- One model → **dense geometry + camera poses + object tracks** from uncalibrated 4D observations.
- From Shanghai AI Lab; continues the "π-series" of robotics-adjacent foundation models.
- Posted Nov 17.

**Sources:**
- [arXiv 2611.23144 — π⁴](https://arxiv.org/abs/2611.23144) `[primary]`

### Why it matters to you

- **Job lens:** Shanghai AI Lab's output is a reliable signal for **what Chinese robotics labs will ship into open weights in the next 90 days**. Track their arXiv cadence; the π-series is becoming a reference stack.
- **Startup lens:** **4D scene understanding from uncalibrated cameras collapses a hardware-dependency that used to gate robotics / AR apps.** Any startup planning deployments with "we need a special camera rig" should reconsider — the π⁴ pattern may let phone cameras do most of the work by late 2027.
- **Insight:** **The gap between US and Chinese robotics-foundation-model open weights is now small enough that US-side builders should routinely cite both sides.** The DeepMind Gemini Robotics 2.5 release (last edition) + π⁴ this week are the same shape of contribution.

→ Cross-link: [`04` §1 — Gamer VLA](#1-gamer-vla)

---

## 4. Jeveration — "System One" models now generate images in parallel, 122× faster (arXiv 2611.24738) {#4-jeveration}

**What the paper claims:**
- **Freezes a VLM** (one of the "System One" Qwen/Gemma/Phi-size models) and **repurposes it for parallel image generation**.
- **512×512 in 78 ms** — **up to 122× faster** than unified (diffusion-head) models at comparable quality.
- Single checkpoint handles **T2I, I2I, and dense-prediction tasks**.
- Addresses the spatial-incoherence failure mode of naive parallel image prediction with a specific attention / masking pattern.
- Posted Nov 18. **148 upvotes on HF Papers.**

**Sources:**
- [arXiv 2611.24738 — Jeveration](https://arxiv.org/abs/2611.24738) `[primary]`
- [hyper.ai mirror of 2611.24738](https://hyper.ai/en/papers/2611.24738) `[secondary]`

### Why it matters to you

- **Job lens:** **"512×512 in 78ms on a VLM-sized backbone"** rewrites the latency budget for any product that renders images on-demand. If you build in this area, re-benchmark your pipeline against the Jeveration numbers — in interviews, this is a credibility check.
- **Startup lens:** **Jeveration-class parallel image gen collapses the cost structure for conversational image products.** If you can render 10 variants per user turn at <$0.001/image, you can actually build "Figma for the rest of us" style products that were uneconomic a quarter ago. **A race is on**: whoever productizes this first in a real app wins the 3-month press cycle.
- **Insight:** **The pattern "freeze a VLM, swap the head"** is now a general template for cheap multimodal extensions — image gen (Jeveration), medical-image Q&A (**MedJev** below, same authors), probably video next. Watch the same lab's arXiv page for the sequel.

→ Cross-link: [`03` §4 — `llm` as router](./03-practical-skills-and-tools.md#4-simon-willison)

---

## 5. WeMM-Video — open-source omni-modal video understanding (arXiv 2611.26409) {#5-wemm-video}

**What the paper claims:**
- **Bilingual (CN-EN)** joint model over **text + image + audio + video**.
- Tencent (Hunyuan group).
- Extends the Chinese open-weight multimodal frontier (following Qwen 3.8 / Kimi K3 / GLM 5.3 earlier this fall).
- Posted Nov 19.

**Sources:**
- [arXiv 2611.26409 — WeMM-Video](https://arxiv.org/abs/2611.26409) `[primary]`

### Why it matters to you

- **Job lens:** **Bilingual CN-EN omni-modal is a hiring signal for US-based Chinese-founded startups** (Scale, Mistral, DeepSeek-US, Kimi-US). If you read / speak Chinese, that's a live employable differentiator in this bucket.
- **Startup lens:** Non-US customers increasingly need **models that handle their language and video content natively**. A production wedge: **vertical video-analytics products (education, surveillance, sports) using WeMM-Video as the backbone** instead of a US frontier model.
- **Insight:** **Western media coverage of Chinese open-weight releases is systematically late by 3–7 days.** Track arXiv directly (cs.CL, cs.CV, cs.MM) for open-weight signals — not The Verge, not TechCrunch.

→ Cross-link: [`02` §5 — HF trending Chinese dominance](./02-new-emerging.md#5-hf-trending)

---

## 6. "Do LLM Agents Still Need to Be Told How to Self-Improve?" (arXiv 2611.23219) {#6-agents-self-improve}

**What the paper claims:**
- Given **fixed primitives** (tool-call surface, memory, a general goal), **agents construct their own context-based self-optimization algorithm** — no researcher-designed RL/DPO loop required.
- Natural successor to last edition's **MRTPO** (per-token multi-reward RL) — same "the agent should run its own improvement loop" direction, less infrastructure.
- Authors: Sundaram, Sancaktar, Isola.
- Posted Nov 17.

**Sources:**
- [arXiv 2611.23219 — Agents self-improve](https://arxiv.org/abs/2611.23219) `[primary]`

### Why it matters to you

- **Job lens:** **"Agent that runs its own improvement loop"** is the most contestable interview topic through 2027 — labs want ICs who can argue **when** this works vs **when** it degrades. Prepare: a 2-paragraph brief of the paper, a 2-paragraph critique, and a concrete deployment caveat (observability, drift detection). Have it ready for the FDE / applied-research conversation.
- **Startup lens:** **This paper undermines a specific startup category:** "we build the RL training stack for your agents." If the agent can bootstrap, the per-customer training contract shrinks. **Reverse: it raises the value of agent-ops** — observability, drift detection, rollback, eval-against-baseline. If you were building training, pivot toward governance.
- **Insight:** **Self-improving agents + Noeri's "living systems" framing (see `02` §2) + Claude Code's blocking hooks (see `03` §1) are the same pattern from three angles** — agents that evolve in production, constrained by eval and policy. **This is the 2027 architecture.**

→ Cross-link: [`02` §2 — Noeri living AI systems](./02-new-emerging.md#2-brightai-noeri) · [`03` §1 — Claude Code blocking hooks](./03-practical-skills-and-tools.md#1-claude-code-2-1-328)

---

## 7. MedJev — "System One" VLM for medical image understanding (arXiv 2611.20992) {#7-medjev}

**What the paper claims:**
- Outputs answers **directly** (no text-gen stage) from medical images → accuracy + latency wins on four clinical benchmarks.
- CUHK (Chinese University of Hong Kong).
- Posted Nov 16.
- Same "freeze a VLM + custom head" pattern as Jeveration (§4).

**Sources:**
- [arXiv 2611.20992 — MedJev](https://arxiv.org/abs/2611.20992) `[primary]`

### Why it matters to you

- **Job lens:** **Clinical/medical AI is an underappreciated job surface for CS grads** — a MedJev-trained eye lets you land Tempus, Hippocratic AI, PathAI, and open roles at Harvey (expanding into medical) and Isomorphic Labs. The résumé artifact: a small reproduction of MedJev on an open medical dataset (e.g., CheXpert) with a short write-up.
- **Startup lens:** **Direct-answer clinical VLMs are the tightest-regulated vertical in AI** — but once you clear FDA or CE-mark, the pricing power is enormous. If you have medical co-founder access, this category rewards the patient. If you don't, don't start here.
- **Insight:** **"VLM + domain-specific output head"** is the pattern for vertical AI through mid-2027 — pick a vertical, find its canonical input shape, train a head. The base model is commoditized; the head and the eval are the moat.

→ Cross-link: [`02` §1 — Model ML vertical template](./02-new-emerging.md#1-model-ml)

---

## 8. Lab research blogs: OpenAI "jagged frontier" + Anthropic Alignment Science November cluster {#8-lab-blogs}

**OpenAI — "Research acceleration: the jagged frontier":**
- Companion to the Sept 6 "Research Intern" post.
- Uplift from internal agentic use is **jagged across domains**; **heaviest-user divergence is widening**.
- **Internal agentic-use (API-equivalent) spend per researcher now ~2× non-equity comp.**
- **Largest absolute uplift area is Safety & Alignment** — not pretraining.
- In-window date not pinned exactly (Nov 2026).

**Anthropic Alignment Science — three Nov posts:**
- (a) **Multi-user, multi-agent resource sharing worsens group outcomes** vs a single shared agent (game-theoretic study on cooperative tasks).
- (b) **Red-teaming blocking monitors in Claude Code and OpenAI Codex** with an adversarial agent → Auto Mode hardened as a result.
- (c) **Cross-model value trade-offs** (ANT / OAI / GDM / xAI) measured on ~300K queries — different models have different implicit value functions on specific question types.

**Sources:**
- [OpenAI — Research acceleration: the jagged frontier](https://openai.com/index/research-acceleration-jagged-frontier/) `[primary]`
- [alignment.anthropic.com](https://alignment.anthropic.com/) `[primary]`

### Why it matters to you

- **Job lens:** **"Red-teaming blocking monitors" is the live research direction behind Claude Code 2.1.328's blocking-hooks feature.** Read the alignment.anthropic.com post before any Anthropic interview this quarter — it's the cleanest window into how Anthropic Safety thinks and the vocabulary they use.
- **Startup lens:** The OpenAI jagged-frontier post **tells you exactly which research tasks are and aren't yet uplifted** — meaning exactly where a startup can still sell "human researcher time" and where it can't. Build on the un-uplifted side.
- **Insight:** **Cross-model value trade-offs (Anthropic post c) is the data pattern that justifies model-routing startups.** If different models answer value-laden questions differently at scale, a router that picks the right model per task has a real product. Expect at least one well-funded "values-aware router" company by Q2 2027.

→ Cross-link: [`03` §1 — Claude Code blocking hooks](./03-practical-skills-and-tools.md#1-claude-code-2-1-328) · [`01` §4 — OpenAI cluster](./01-big-lab-moves.md#4-openai-cluster)

---

### Flagged / unverified (DO NOT quote)

- **Riemann Hypothesis proof** claim on HF Posts (Nov 20, "Levent Alpöge + Claude"): **single community post, no arXiv / lab-blog preprint located**. `[rumor]` — wait for primary.
- Agents-radar GitHub digests list several additional IDs (2611.26007, 2611.25891, 2611.25388, "HabitusMem," "QVal," "HerAgent," "SwarmSafe-Delta"). **Not individually verified**; do not cite without opening the arxiv.org/abs/&lt;id&gt; page first.

### Sourcing caveats

- **"Research acceleration: the jagged frontier"** primary URL confirmed; exact publication date within November not pinned from the search snippet. Safe to quote the numbers (jagged uplift, ~2× comp, Safety & Alignment largest) if you note "Nov 2026."
- **Anthropic Alignment Science posts** are primary and safe to summarize; link each individual post if you quote a specific number.
