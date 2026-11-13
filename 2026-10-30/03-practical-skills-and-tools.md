# 03 — Practical Skills & Tools — 2026-10-30 (Friday)

Two concrete, actionable upgrades for your toolbelt this week. Each: what · how to use it · what to ship.

---

## 1. `sandbox-runtime` — Claude Code's OS-level sandbox is open-source (Apache-2); read it before you ship an agent that `exec`s {#1-sandbox-runtime}

**What.** Anthropic's **`sandbox-runtime` (srt)** — the OS-level sandbox that backs Claude Code — is published as an npm package under Apache-2.0 as an *open-source research preview*. It uses the right primitive on each OS:

- **macOS:** `sandbox-exec` with Seatbelt profiles.
- **Linux:** `bubblewrap`.
- **Windows:** alpha-stage build (treat as unstable).

Anthropic's engineering writeup frames it as the containment layer behind "Claude Code can run commands on your laptop without eating your laptop."

**Why this is the practical move of the week.** Every "agent that runs code" startup, side project, or Claude Code plugin reinvents some sloppy version of this layer. **A published, inspectable sandbox is a hiring + startup moat tool at once** — because now the question "what's your containment story?" has a non-handwavy answer: "we started from `sandbox-runtime`, here's our Seatbelt profile diff + our bubblewrap tweaks."

**How to use it (90-minute path).**

1. **Install + inspect.** `npm i @anthropic-experimental/sandbox-runtime` in a scratch dir. Read `src/profiles/*` for Seatbelt / bubblewrap defaults.
2. **Run the demo.** Spin up a two-tool agent (one that reads `~/notes.md`, one that writes `~/notes.md`), confirm the sandbox denies access outside `~/notes.md`'s parent.
3. **Audit for the "lethal trifecta."** Simon Willison's framing (private data in, untrusted content, external communication possible) — write a 5-line README section listing which trifecta edges your sandbox profile blocks and which it doesn't.
4. **Diff against your current agent.** Open your most-public agent repo. For every `exec`, `spawn`, `shelljs`, `child_process.spawn` call, add a one-line comment: `// sandbox-runtime equivalent: X`. If any call has no equivalent, open a GitHub issue titled `containment-gap: <path>:<line>`.
5. **Publish the diff.** One tweet-length writeup + one GitHub commit = a legible, interviewable artifact.

**What to ship this weekend (artifact-grade).** A **GitHub repo + 400-word blog post** titled *"What `sandbox-runtime` does, in 300 lines of code and 1 Seatbelt profile."* Walk through: (a) which Seatbelt deny-rules it ships; (b) which syscalls on Linux it blocks via bubblewrap; (c) what breaks on Windows alpha; (d) one real example of a Claude agent you re-wrote on top of it. This is a **cold-email-worthy artifact** for any FDE / Integration-Engineer screen — directly answers the "how do you contain AI tool-use?" question.

**Caveats to flag.** The Windows build is alpha — don't ship Windows users to it; the "research preview" tag means the API can and will change; publish your version pin. The sandbox is OS-level, so **it does not protect against logic bugs *inside* the sandbox** (an agent that writes to its one allowed path, writes a destructive command *into* that path, then another agent runs it) — the lethal trifecta analysis matters more than the sandbox alone.

**Sources.**
- [primary] [Anthropic Engineering — Claude Code sandboxing](https://anthropic.com/engineering/claude-code-sandboxing)
- [secondary] [InfoQ — Anthropic Claude Code Sandbox](https://www.infoq.com/news/2025/11/anthropic-claude-code-sandbox)
- [secondary] [Simon Willison — Claude Code for Web (covers sandbox-runtime)](https://simonw.substack.com/p/claude-code-for-web-a-new-asynchronous)
- [aggregator] [aiweekly — Anthropic Open-Sources Claude Code Sandbox](https://aiweekly.co/alerts/anthropic-open-sources-claude-code-sandbox-under-apache-20)
- [analysis] [joshuaberkowitz — Secure Code Execution with Sandboxing](https://joshuaberkowitz.us/blog/news-1/anthropic-s-claude-code-is-transforming-secure-code-execution-with-sandboxing-1521)

`#claude-code #sandbox #security #open-source #trifecta #containment`

---

## 2. The Oct-30 router rebuild — four price points, three specialties, one artifact {#2-router-rebuild}

**What.** The month's pricing-floor moves give you a new reference router. The prior router (see [2026-10-14/03](../2026-10-14/03-practical-skills-and-tools.md#2-router-haiku-rebuild)) was two-tier (Haiku 5.5 worker, Opus 5 planner). The Oct-30 router is **four-tier with explicit specialty routing**:

| Tier | Model | Price in/out per 1M | Specialty |
|---|---|---|---|
| Worker | Haiku 5.5 | $0.10 / $0.50 | Short-horizon, cheap sub-agent, text-only |
| Browser / computer-use | GPT-6.1 Terra | $1 / $5 | Visual reasoning + action trajectories; `gpt-6.1-terra` |
| Long-output | Gemini 4 Argon | $2 / $10 (intro, through Nov 30; standard $4/$20) | 1M-token output ceiling, single-call long docs / codebases |
| Planner / high-stakes reasoning | Claude Opus 5.5 | $4 / $20 | Always-on thinking; 1M context; 128K output; FAST mode preview |

**The three routing rules you should encode (literally — in code, with a decision table).**

1. **"Is this a single-step tool call under 1K output tokens?" → Haiku 5.5.** Most of your agent's turns qualify. Don't let Opus 5.5 do grep / list / summarize-one-page work.
2. **"Does this step need to click, scroll, type into a GUI, or read a visual-first screen?" → GPT-6.1 Terra.** The specialty premium ($1/$5 vs Haiku's $0.10/$0.50) is justified only here. **Guard with explicit approval wrapper for any send/pay/sign/delete** (ape the Claude Duet approval primitive from [`02` §1](./02-new-emerging.md#1-duet)).
3. **"Does this step need a single call to emit 50K+ output tokens of consistent long-form text?" → Argon.** Else don't — Opus 5.5 is the planner for everything else that needs real reasoning. Argon's independent-eval score lags Opus 5.5 on reasoning (52.6 vs 57.6 on Artificial Analysis Intelligence Index), so it's a specialty tool, not a drop-in replacement.

**What to ship this weekend (artifact-grade — this is THE weekend artifact).** Repository: `cost-aware-agent-router-2026-10`. Content:

- `README.md` with the pricing table above + three decision rules + one benchmark result table.
- `router.ts` (or `.py`) implementing the four-tier routing with explicit cost logging per call.
- `evals/` with the 5-case eval you used on the Oct-14 router: (1) extract fields from a PDF, (2) book a calendar event via connector, (3) summarize a long thread, (4) code a one-file fix in a repo, (5) answer a multi-step research question. Report **cost / latency / correctness** for each case under three routers: Opus-5-only (baseline), Opus-5.5-only, and the four-tier Oct-30 router.
- `WRITEUP.md`: one-screen table + 300-word narrative — "I moved my eval from the Oct-14 two-tier to the Oct-30 four-tier router. Cost dropped X%. Correctness changed by Y pp. Here's the specialty-routing decision table I'd defend in an FDE interview."
- Publish on GitHub + cross-post one Twitter thread + one LinkedIn long-form post.

**Three one-line pitfalls to avoid.**
- *Don't* run Opus 5.5 at `effort: high` by default. The 2.5× fast mode is a different lever; benchmark both.
- *Don't* route to Terra for text-only work "because it's cheap." $1/$5 vs Haiku's $0.10/$0.50 is 10× — the specialty gap only pays back on visual trajectories.
- *Don't* trust Argon's 1M-output ceiling for free-form fiction / creative long-form. The benchmark is DeepSWE / code / structured output — your mileage will vary on narrative text.

**Sources (pricing anchors to cite in your writeup).**
- [primary] [Anthropic — Haiku 5.5 announcement (Oct 7)](https://www.anthropic.com/news) · $0.10 / $0.50 per 1M.
- [primary] [Anthropic — Opus 5.5 announcement (Oct 18)](https://www.anthropic.com/news) · $4 / $20 per 1M.
- [primary] [OpenAI — Introducing GPT-6.1 Terra (Oct 26)](https://openai.com/index/introducing-gpt-6-1-terra/) · $1 / $5 per 1M.
- [primary] [Google DeepMind — Gemini 4 Argon model card (Oct 13)](https://deepmind.google/models/model-cards/) · $2 / $10 intro, $4 / $20 standard.
- [analysis] [Artificial Analysis — Intelligence Index comparison (Argon 52.6, Opus 5.5 57.6, GPT-6 Astra 52.7)](https://artificialanalysis.ai/)

`#router #cost-aware #agents #haiku #terra #argon #opus-5-5 #effort-levels #portfolio`

---

**End of §03.** Next: [`04` — Research progress](./04-research-progress.md).
