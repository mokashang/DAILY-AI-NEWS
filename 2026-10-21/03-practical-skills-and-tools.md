# Practical Skills & Tools — 2026-10-21

Hands-on. **Read this one with a terminal open.** The two artifacts here (router v3 + eval harness) land you a résumé line, a portfolio GitHub repo, and a shippable demo by Sunday.

Theme: **routing + eval are the Q4 2026 interview differentiators.** Everyone can call one model. The person who can prove a choice between three is the hire.

---

## 1. Claude Code v2.1.304 (Oct 19) — upgrade and configure {#1-claude-code-21304}

**The shortest actionable list.** The last 10 days of Claude Code releases introduced auto mode as default, mods, code review levels, and the Haiku-5.5-as-default-small-model shift. If you set up Claude Code before Oct 7, your config is out of date. [[Classmethod](https://dev.classmethod.jp/en/articles/20261020-cc-updates-v2-1-304/)] [[DEV cheat sheet](https://dev.to/anglo_lima/claude-code-cheat-sheet-october-2026-the-complete-state-of-play-1j26)] [[Releasebot](https://releasebot.io/updates/anthropic/claude-code)]

**Do this today (10 minutes):**

```bash
# 1. Upgrade
claude --version                     # should be ≥ 2.1.304
# if older:
curl -fsSL https://claude.com/install.sh | bash

# 2. Opt into auto mode for this project
claude /auto-mode-setup              # walks through per-project config
                                     # choose task-dispatch model + telemetry

# 3. Set your code-review level (Owner only; applies org-wide)
claude /config set code_review.level standard
                                     # options: quick | standard | deep
                                     # standard is the default; deep for prod PRs

# 4. Verify Haiku 5.5 is the default worker
claude /config get models.default_haiku
                                     # expect: claude-haiku-5-5

# 5. (Optional) Install an auto-fix mod
claude /mods browse                  # browse community mods
# or write your own; mods can hook on tool calls
```

**New primitives worth building a hook into:**

| Primitive | Added | Why it matters |
|---|---|---|
| **Auto mode** | v2.1.287+ (default v2.1.302) | Subagents run in background; you keep flow; the default dispatch model is picked by the harness, not you |
| **Mods** | v2.1.287 | Change Claude Code's own behavior from the inside; the mod is your product surface |
| **Code Review levels** | v2.1.304 (Oct 19) | 3-tier policy you can enforce org-wide; Deep + Haiku 5.5 is approximately free |
| **Haiku 5.5 default (1M ctx)** | Oct 7 | Subagent-worker tier is now a 1M-context model; re-architect your subagent flow |
| **`claude --worktree`** | v2.1.304 fix | No longer deletes without confirm; use for safe parallel branches |
| **OpenTelemetry tracing** | v2.1.301 | Auto-mode decisions are now distinguishable in traces |

**Sources:**
- [primary] Claude Code changelog [[Changelog](https://code.claude.com/docs/en/changelog)]
- [secondary] Classmethod — v2.1.303 → v2.1.304 release notes [[CM](https://dev.classmethod.jp/en/articles/20261020-cc-updates-v2-1-304/)]
- [secondary] Classmethod — v2.1.301 OpenTelemetry [[CM](https://dev.classmethod.jp/en/articles/20261016-cc-updates-v2-1-301/)]
- [secondary] DEV cheat sheet [[DEV](https://dev.to/anglo_lima/claude-code-cheat-sheet-october-2026-the-complete-state-of-play-1j26)]
- [aggregator] Releasebot [[RB](https://releasebot.io/updates/anthropic/claude-code)]

**Why it matters to you**
- **Job**: "Configured auto mode + mods for team Claude Code deployment" is a real engineering line, not vibes. If you set this up for a side project and screenshot the trace, you have an interview-ready artifact.
- **Startup**: Mods are a **free distribution channel** for a developer-tool startup. If your wedge is "better X for Claude Code," ship it as a mod first — zero install friction.
- **Insight**: Anthropic is building Claude Code into **a platform for third-party plugins (mods)**, not just a CLI. Compare to Cursor + Windsurf's extension stories. The platform that wins is the one with the strongest base-tool pull.

`#claude-code #auto-mode #mods #code-review #haiku`

---

## 2. MCP: use the stateless spec, drop the SSE one {#2-mcp-stateless}

**What changed.** The MCP spec moved to a **stateless design in the July 2026 revision** under the Agentic AI Foundation / Linux Foundation. Earlier server implementations are not forward-compatible on some endpoints. [[WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026)] [[Towards AI](https://pub.towardsai.net/mcp-in-2026-it-stopped-being-a-tool-connector-c16f246f96aa)] [[SerpAPI](https://serpapi.com/blog/the-state-of-mcp-everything-that-changed-in-h1-2026/)]

**Current SDKs** (as of this writing): TypeScript v1.27.1, Python v1.26. Native in Google ADK, OpenAI Agents SDK, Cursor, Windsurf, Replit, Claude Code.

**What to use:**

```python
# Minimal stateless MCP server (Python SDK ≥ 1.26)
from mcp.server import Server
from mcp.transport.http_stateless import StatelessHttpTransport

server = Server("my-tool")

@server.tool()
async def search_docs(query: str) -> list[dict]:
    """Search internal docs."""
    return [{"title": "...", "url": "..."}]

if __name__ == "__main__":
    transport = StatelessHttpTransport(host="0.0.0.0", port=8080)
    server.run(transport)
```

**Open problems to NOT solve yourself** (they're moving):
- Server-side authN / authZ (OAuth 2.1 is the current direction; wait on the official spec)
- Multi-server tool-name collision (will be solved at protocol level, not application level)
- Session identity across stateless requests (viable with signed tokens; not a general solution)

**Sources:**
- [analysis] WorkOS — "Everything your team needs to know about MCP in 2026" [[WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026)]
- [analysis] Towards AI — "MCP in 2026: It Stopped Being a Tool Connector" [[TAI](https://pub.towardsai.net/mcp-in-2026-it-stopped-being-a-tool-connector-c16f246f96aa)]
- [analysis] SerpAPI — state of MCP H1 2026 [[SA](https://serpapi.com/blog/the-state-of-mcp-everything-that-changed-in-h1-2026/)]
- [primary] MCP official specification (modelcontextprotocol.io)

**Why it matters to you**
- **Job**: Your public MCP server portfolio artifact (from `ME.md`) needs to target the stateless spec. If it still runs on the SSE-era design, update it this weekend before showing it in any interview.
- **Startup**: MCP as infra = **the authentication / policy / registry layer** is the open problem. If you want to build around MCP, build in the open-problem corners, not the "yet another MCP server" corner.
- **Insight**: Protocols reach stability only after the first big breaking change. MCP is past that threshold — invest in it as if it's HTTP/2.

`#mcp #protocol #stateless #sdk #agents`

---

## 3. THIS WEEKEND'S SHIP — 3-model router + 10-case eval harness {#3-this-weekend}

**The artifact.** A public GitHub repo (`claude-vs-argon-vs-gpt6-router`) that:

1. Accepts a prompt + a "capability profile" tag
2. Routes to **Opus 5.5 / Argon / GPT-6 Sol-or-Luna** based on a 20-line policy
3. Logs cost, latency, output
4. Runs a **10-case eval suite** (3 Terminal-Bench-style, 3 agentic-tool-use, 2 long-context, 2 reasoning) with Opus-as-judge
5. Produces a **3-column comparison CSV** in `evals/results.csv`

**Why this is the right ship:**
- Three flagship models within 2× of each other on price AND capability + Argon's 40-day $2/$10 window = **the one week where cost arbitrage is a story worth telling**.
- Everyone will have "called Opus 5.5" on their résumé by Dec 1. **Almost no one will have run eval traffic on all three yet.**

**Minimal file layout (one weekend, 300 LOC):**

```
claude-vs-argon-vs-gpt6-router/
├── README.md                 # 1-page: wedge, methodology, results snapshot
├── router.py                 # 20-line policy; log everything
├── providers/
│   ├── anthropic.py          # Opus 5.5 — effort="high"
│   ├── google.py             # Gemini 4 Argon
│   └── openai.py             # GPT-6 Sol (default) + Luna fallback
├── evals/
│   ├── cases/                # 10 .yaml case files
│   ├── run.py                # dispatches each case to all 3 vendors
│   ├── judge.py              # Opus-as-judge
│   └── results.csv           # <-- the deliverable
├── costs.py                  # price-per-1M lookup (Argon intro expires 2026-11-30!)
└── demo.gif                  # 10-second asciinema of a routed call
```

**Router policy (literally 20 lines):**

```python
# router.py — pseudocode
def route(prompt, tag, budget_cents_max=5):
    # cost-aware: cheap-flagship-first until the task gets hard
    if tag == "agentic-coding":        return "claude-opus-5-5"
    if tag == "long-context":           return "gemini-4-argon"  # 1M + cheap
    if tag == "tool-use":               return "gpt-6-sol"
    if tag == "reasoning-heavy":        return "claude-opus-5-5-xhigh"
    if tag == "cost-floor":             return "gemini-4-argon"
    if estimate_cost(prompt, "gemini-4-argon") < budget_cents_max:
        return "gemini-4-argon"
    return "claude-opus-5-5"
```

**Argon API quick-start** (so you can run it before Dec 1):

```bash
pip install google-genai
export GOOGLE_API_KEY=...
```

```python
from google import genai

client = genai.Client()
resp = client.models.generate_content(
    model="gemini-4-argon",
    contents="Explain MCP's stateless spec in 3 bullets.",
)
print(resp.text)
```

**Opus 5.5 with effort levels:**

```python
import anthropic
c = anthropic.Anthropic()
msg = c.messages.create(
    model="claude-opus-5-5",
    max_tokens=4096,
    thinking={"type": "enabled", "effort": "xhigh"},  # low|medium|high|xhigh|max
    messages=[{"role": "user", "content": "..."}],
)
```

**GPT-6 Sol:**

```python
from openai import OpenAI
c = OpenAI()
r = c.responses.create(
    model="gpt-6-sol",
    input="..."
)
```

**Eval cases (10 is enough for a signal, 30 is overkill):**
1. **Agentic coding** × 3: fix a failing test; refactor a module; implement a feature from a spec
2. **Tool use** × 3: web search + synthesize; file I/O + SQL; MCP server call chain
3. **Long context** × 2: QA over a 100K-token repo; summarize a book
4. **Reasoning** × 2: a Humanity's Last Exam-style question; an ARC-AGI-adjacent puzzle

**Shipping checklist (Sunday 10 PM):**
- [ ] Repo pushed public with README that answers "why this matters now"
- [ ] `results.csv` with 10 rows × (model, cost_usd, latency_ms, score)
- [ ] One screenshot of the 3-column comparison in the README
- [ ] One asciinema `demo.gif` of a routed call
- [ ] Posted on LinkedIn + X with the 40-day Argon-window framing
- [ ] Linked from `ME.md` → portfolio artifacts

**Why it matters to you**
- **Job**: This single artifact answers 4 common interview questions: "How do you pick a model?" / "How do you build an eval?" / "How do you reason about cost?" / "What's a project you shipped this quarter?" You wouldn't believe how few applicants have this.
- **Startup**: If you ever build a product, cost-routing is the **highest-ROI engineering primitive you own**. The router you build this weekend is the kernel of your future production system.
- **Insight**: Three parity-ish flagships + 40-day cost-arb window = **shipping speed matters more than shipping quality this week**. The person who publishes a mid-quality 3-model eval on Oct 25 is more differentiated than the person who publishes a perfect one on Nov 25.

`#router #eval #argon #opus #gpt6 #portfolio #this-weekend`

---

## 4. Router v3 — the "effort level × model" matrix (next sprint, ~2 weeks) {#4-router-v3}

**After this weekend's v1 ships**, the natural extension is the **25-cell matrix router**: 5 Claude effort levels × 5 vendors (Haiku-5.5 / Sonnet / Opus-5.5 / Fable-5.1 / Mythos) + Argon + GPT-6 Sol/Luna/Astra. [[Opus 5.5 effort docs — The Batch](https://www.deeplearning.ai/the-batch/claude-opus-5-5-leaps-forward)]

**Core idea.** The 2026 cost-aware agent config is:
1. **Model family** (big = Opus, mid = Sonnet, small = Haiku)
2. **Effort level** (low → max; always-on reasoning)
3. **Cross-vendor fallback** (Argon when Opus is overloaded)
4. **Cache strategy** (95% off on Argon; 90% off on Opus/Sonnet)

**Portfolio pitch** (interview script):
> "I built a cost-aware router that selects across 25 Claude cells, Argon, and GPT-6. For a benchmark workload, it hit **42% cost reduction at 97% quality retention** vs. always-max-Opus."

Even if you only hit 20% / 95%, the artifact is still interview-ready.

**Why it matters to you**
- **Job**: FDE / Integration Engineer loops ask about cost reasoning in every stage. Have numbers.
- **Startup**: Router v3 is literally the heart of a cost-ops-for-AI startup (cf. North $60M Series B). You're not building a side project; you're building the kernel.
- **Insight**: **Effort level × model is a 2D search space.** 2026's AI engineering is becoming operations research with LLM-sized decision variables.

`#router #effort-levels #routing #cost #portfolio`

---

## 5. Weekly tool-of-the-week — the `openrouter` eval dashboard pattern {#5-tool-of-week}

**Pattern.** Instead of building an eval dashboard from scratch, pipe your router's `results.csv` into **Hugging Face Datasets + Spaces** and get a free hosted leaderboard:

```bash
# push dataset
hf dataset upload my-router-results-20261021 ./evals/results.csv

# publish a space (Gradio) that reads the dataset and renders a 3-way chart
hf spaces create router-leaderboard --sdk gradio
```

**Why it matters to you**
- **Job**: A HF Space is a one-click public demo. Link from your résumé.
- **Startup**: HF Spaces + Datasets = **free content-marketing infra** for a dev-tool startup.
- **Insight**: In 2026, "shipped it" means "someone else can click it in 5 seconds." Not "pushed to GitHub."

`#huggingface #spaces #eval #leaderboard`

---

## Reading cross-reference

- Why the router + eval ship *this* week specifically: [`01` §1](./01-big-lab-moves.md#1-gemini-4-argon)
- Benchmark saturation = your-own-eval premium: [`02` §4](./02-new-emerging.md#4-benchmark-saturation)
- The job market for routing / eval skills: [`05` §3](./05-career-and-startup.md#3-skill-reprice)
