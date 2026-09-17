# Practical Skills & Tools — 2026-06-14 (Sunday)

`#claude-code #mcp #agent-sdk #cost-routing #portfolio`

Hands-on workflows you can ship **today** and **tomorrow morning**. Two of the three items below are time-boxed to specific clock-times (8 AM PT Monday for the metering toggle; tonight for the dependency audit). Don't postpone these.

---

## 1. T-MINUS 18 HOURS: the Agent SDK metering split goes live tomorrow {#1-jun15-setup}

**What's happening.** At **00:01 PT Monday June 15**, Anthropic moves programmatic Claude (Agent SDK, `claude -p`, GitHub Actions, third-party agents that auth through the Agent SDK) **out of your standard Pro/Max subscription bucket** and into a **separate dollar-denominated credit pool** billed at **full Anthropic API list prices**. Interactive Claude (chat, Claude Code in the terminal, Claude Cowork) is **unaffected**.

**The credit pool by tier.**
| Subscription | Monthly credit allocation | Effective break-even |
|---|---|---|
| **Pro ($20/mo)** | $20 | ~2M Opus 4.8 input tokens / month |
| **Max-5x ($100/mo)** | $100 | ~10M Opus 4.8 input tokens / month |
| **Max-20x ($200/mo)** | $200 | ~20M Opus 4.8 input tokens / month |

Credits expire end of billing cycle. **Unused credits do NOT carry over.**

**The setup checklist (do this Monday 8 AM PT, ~10 min total).**

1. **Open Anthropic Console → Settings → Billing → Agent SDK Credits.** Toggle "Claim my monthly Agent SDK credit" ON. *(The credit does not auto-activate. Silent failure if skipped — your `claude -p` calls will fail at 00:01 PT instead of falling back gracefully.)*
2. **Enable overflow billing.** Same panel → "Allow API-rate billing when credits exhausted." Without this, automation **stops** when credits run out — and on June 15 nobody knows exactly how fast their credits drain.
3. **Tag your agents.** In your Agent SDK calls, add the `metadata.user_id` field with a tag like `"portfolio-mcp-server-v1"` per project — this is the only way to see post-hoc which portfolio artifact ate which percentage of the credit.
4. **Set a daily cost log.** Cron job: `claude api cost --since=24h --format=json >> ~/anthropic_cost_log.jsonl`. Eyeball it daily for two weeks; you'll learn exactly how the meter ticks before deciding to upgrade tier.

**Sources.**
- `[secondary]` [TechTimes — Anthropic Ends Subscription Subsidy for Agents June 15: Credit Pool Replaces Flat-Rate Access](https://www.techtimes.com/articles/317625/20260602/anthropic-ends-subscription-subsidy-agents-june-15-credit-pool-replaces-flat-rate-access.htm)
- `[secondary]` [The New Stack — Anthropic splits billing again: Agent SDK gets separate credit pools](https://thenewstack.io/anthropic-agent-sdk-credits/)
- `[analysis]` [Coders Era — Anthropic's June 15 Billing Change: What Every Claude Code & Agent SDK User Must Do](https://codersera.com/blog/anthropic-june-2026-billing-change-claude-code/)
- `[analysis]` [Context Studios — Anthropic's June 15 Billing Split: Your Break-Even Decision](https://www.contextstudios.ai/blog/anthropics-june-15-billing-split-your-break-even-decision)
- `[aggregator]` [Canonical reference gist — Anthropic May 13 Agent SDK $200 credit policy change](https://gist.github.com/MagnaCapax/d9177e35b355853f03c730dfcaa693ef)

**Why it matters to you.**

- **Job ·** Interviewers in any Anthropic-stack role will ask you "how do you control agent cost." Having a 2-week cost log + a "I orchestrate with Opus 4.8 and worker on Sonnet 4.6 because…" answer is now table stakes.
- **Startup ·** If your wedge involves running agents on customer credit, the metering split is **the single biggest gross-margin variable in your model**. Re-do the unit economics tomorrow.
- **Insight ·** This is Anthropic's first step toward **per-agent billing** at the enterprise level. The Pro tier will become the consumer / hobbyist line; Max-20x becomes the indie-developer line; enterprise contracts get bespoke. Plan your spend tier accordingly.

`#claude-code #agent-sdk #billing #cost-routing #ops`

---

## 2. TONIGHT: the Fable 5 dependency audit + multi-vendor router shim {#2-anthropic-stack-hedge}

**Why.** The shutdown in [`01` §1](./01-big-lab-moves.md#1-fable-shutdown) means **any project, demo, or portfolio artifact that pinned to `claude-fable-5` is broken until further notice.** Anthropic's automatic fallback is Opus 4.8 — but only if your code reads the API's model-substitution header. Most demo code does not.

**The 60-minute artifact.** A single commit with a small router shim and a top-level README note. Ships an **artifact** (resume-quality), not just a fix.

### Step 1 — Audit (5 min)

```bash
# In each portfolio repo:
grep -rn "claude-fable-5\|fable-5\|claude-mythos-5\|mythos-5" . \
  --exclude-dir=node_modules --exclude-dir=.git
```

Expect hits in: model picker dropdowns, prompt-engineering harnesses, CI configs, MCP server configs, README examples.

### Step 2 — Router shim (15 min)

Drop a single `models.py` (or `models.ts`) into each repo:

```python
# models.py — multi-vendor router with auto-fallback (2026-06-14 post-shutdown edition)
from anthropic import Anthropic
from openai import OpenAI
from google import genai

DEFAULT_VENDOR = "anthropic"
DEFAULT_MODEL  = "claude-opus-4-8"  # Fable 5 unavailable as of 2026-06-12

FALLBACK_CHAIN = [
    ("anthropic", "claude-opus-4-8"),
    ("anthropic", "claude-sonnet-4-6"),
    ("openai",    "gpt-5.5"),
    ("google",    "gemini-3.5-flash"),
]

def chat(prompt: str, vendor: str = DEFAULT_VENDOR, model: str = DEFAULT_MODEL):
    for v, m in [(vendor, model)] + FALLBACK_CHAIN:
        try:
            return _call(v, m, prompt)
        except Exception as e:
            print(f"[router] {v}/{m} failed: {e}; trying next…")
    raise RuntimeError("All vendors exhausted")

def _call(vendor, model, prompt):
    if vendor == "anthropic":
        return Anthropic().messages.create(
            model=model, max_tokens=1024,
            messages=[{"role":"user","content":prompt}])
    if vendor == "openai":
        return OpenAI().chat.completions.create(
            model=model, messages=[{"role":"user","content":prompt}])
    if vendor == "google":
        return genai.Client().models.generate_content(
            model=model, contents=prompt)
```

The 4-line subset that goes into `README.md`:

> **2026-06-14 post-shutdown policy:** all model references route through `models.py`. Default `claude-opus-4-8`; auto-fallback chain Opus → Sonnet 4.6 → GPT-5.5 → Gemini 3.5 Flash. Re-pin to Fable 5 after the BIS directive is lifted (see [tracking issue](#)).

### Step 3 — Commit + tweet (40 min)

```
git commit -m "shutdown-safe: multi-vendor router (2026-06-12 BIS directive)"
git push
```

Then post one paragraph on X or LinkedIn — link the repo + explain the chain — title `"Shipping a multi-vendor model router 48 hours after the US directive on Claude Fable 5."` This is the **highest-signal resume artifact you can ship this weekend** because: (a) it's grounded in a real, dated event; (b) it demonstrates a production discipline (multi-vendor) that 90 % of demo repos lack; (c) it's a 60-minute commit, so it lands while the news is still hot.

**Sources.**
- `[primary]` [Anthropic — Statement on directive to suspend Fable 5 / Mythos 5](https://www.anthropic.com/news/fable-mythos-access)
- `[secondary]` [VentureBeat — Anthropic blocks all public access to Fable 5, Mythos 5 — what enterprises should do](https://venturebeat.com/technology/anthropic-blocks-all-public-access-to-claude-fable-5-mythos-5-following-us-government-order-what-enterprises-should-do)
- `[analysis]` [Simon Willison / past on multi-vendor LLM routing](https://simonwillison.net/) (the conceptual baseline; substitute the post-shutdown model list)

**Why it matters to you.**

- **Job ·** Every FDE / Solutions / Customer Engineering screener for the next 90 days will ask "describe a time you handled a vendor outage." You'll have a concrete one.
- **Startup ·** If your wedge is in [STARTUPS.md](../STARTUPS.md), audit it: does it pin to a single vendor? If yes, your investor pitch just got a pre-determined hard question — get the router shim in before any new VC conversation this week.
- **Insight ·** The "Anthropic-first, multi-vendor as production discipline" line in [ME.md](../ME.md) is now operationalized. Update ME.md to reference this artifact as the proof.

`#anthropic #router #fallback #multi-vendor #portfolio-artifact`

---

## 3. The "Series A bar" buildable: routing engine + security gate {#3-routing-gate-recipe}

**Why.** The funding-bubble analysis in [`02` §4](./02-new-emerging.md#4-funding-cool) calls out two specific features as the **Series A gate** for agentic startups: a proprietary multi-agent routing engine + a security gate. Most candidates / founders don't have working reference implementations. Here's a starter playbook to convert these from concept to two-day buildable artifacts.

**Routing engine (Day 1, 4–6 hours).**

- **Inputs:** prompt + a tagged context object (e.g. `{"sensitivity": "PII", "cost_cap": "$0.05", "max_latency_ms": 3000, "needs_tools": ["web", "filesystem"]}`).
- **Outputs:** chosen `(vendor, model, params)`, plus a fallback chain.
- **Implementation:** a 30-line classifier (rule-based first, replace with a tiny model later) → produces a `RoutingDecision` → consumed by the `models.py` shim from §2.
- **Eval surface:** 30 representative prompts manually labelled with the "right" routing decision; track precision/recall + cost / latency vs all-Opus baseline. *Reuse the [τ²-Bench dual-control framing](./04-research-progress.md#1-tau2-erl) for any conversational routing decisions.*

**Security gate (Day 2, 4–6 hours).**

- **Pre-prompt validator:** a Sonnet 4.6 mini-LLM that takes the user prompt + tagged context and emits `{ allow: bool, reason: str, redacted: str }`. Block obvious prompt-injection patterns (`"ignore previous instructions"`, suspicious base64, Unicode-tag attacks à la Pliny); pass otherwise.
- **Post-response auditor:** same model, post-generation: `{ harm_score: 0-1, leaked_secrets: list, escalate: bool }`. Implements the cheap dual-model sanitiser pattern from [2026-05-20/03 §3](../2026-05-20/03-practical-skills-and-tools.md).
- **Integration:** wraps every `chat()` call in `models.py`.
- **Eval surface:** Pliny's published jailbreak patterns + the OpenAI red-team test set; precision = "blocked malicious only" / "all blocked."

**Sources.**
- `[primary]` [Anthropic — Claude Code best practices](https://code.claude.com/docs/en/best-practices)
- `[analysis]` [pubnub — Best practices for Claude Code subagents](https://www.pubnub.com/blog/best-practices-for-claude-code-sub-agents/)
- `[analysis]` [okhlopkov — My Claude Code Setup: MCP Servers, Hooks, Skills and Agents (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/)
- `[analysis]` [Developers Digest — Claude Code Agent Teams, Subagents, and MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026)
- `[analysis]` [MCP Directory — Claude Code Best Practices: From Vibe Coding to Agentic Engineering (2026)](https://mcp.directory/blog/claude-code-best-practices)

**Why it matters to you.**

- **Job ·** This is **the single artifact that closes the gap between "I used an agent" and "I designed agent infrastructure."** Add it to ME.md as a 3rd active portfolio artifact (alongside the MCP server and the billing audit).
- **Startup ·** This is also **the Series A bar from the VC analysis**. Showing a working routing engine + security gate in a 10-minute demo gets you past the door that most Series A pitches die at.
- **Insight ·** Pliny's published jailbreak patterns are the best available **adversarial training set** as of June 14 — the world's free red team. Use them shamelessly.

`#routing #security #agent-architecture #portfolio-artifact #series-a`

---

## 4. Claude Code subagent + MCP best practices (Jun 2026 stack baseline) {#4-cc-mcp-baseline}

**Quick reference for new repos / project setup tonight or this week.**

- **MCP servers worth starting with:** **Playwright** (browser + UI verification), **PostgreSQL/MySQL** (direct schema), **Slack** (read bug-report threads), **Figma** (design-to-code).
- **CLAUDE.md** = stable rules. **Skills** = repeated workflows. **Hooks** = automation + logging. Don't mix these in one file.
- **Subagent rule of thumb:** **feature-specific beats general "qa" or "backend engineer".** Specificity buys better tool selection + tighter context.
- **Tool whitelisting:** **omitting `tools:` in a subagent inherits all available tools (including MCP).** Whitelist explicitly to prevent surprise blast radius.
- **Token amortization:** subagent file reads + greps stay in the subagent; only the final report bubbles to the main session. **Highest-leverage move for keeping main contexts small.** Crucial for the per-step cost lever post-Jun-15 metering.

**Sources.** Same as §3 above.

**Why it matters to you.** This is the **default skeleton** every new project should start with after this weekend. Build it into your `~/dotfiles/claude/` templates so you never re-debate the choices.

`#claude-code #mcp #subagents #project-setup`

---

## Cross-page

- See [`02` §1–2](./02-new-emerging.md) for the funding category alignment + Gemini 3.5 Pro launch window that informs §2's fallback list ordering.
- See [`04` §1](./04-research-progress.md#1-tau2-erl) for **τ²-Bench** — the right eval framework to plug into §3's routing-engine + security-gate evaluation surface.
- See [`05` §1](./05-career-and-startup.md#1-focusing-reeval) for the focusing-decision re-evaluation that the §2 dependency audit operationally implements.
