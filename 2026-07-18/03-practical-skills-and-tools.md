# Practical Skills & Tools — 2026-07-18

Saturday operator patterns — every one is deployable in ≤2 hours.

Tags: `#practical #evaluation #routing #cache #cost #verification`

---

## 1. Capture your Fable-5-free evals TODAY — 90-minute play {#1-fable-5-evals}

**Why.** Fable 5 free access **expires Sun Jul 19 at 11:59 PM PT** ([`02` §2](./02-new-emerging.md#2-fable-5-sunset)). No fourth extension announced. Rate-limits will saturate on Sunday from the last-day rush — **run today**.

**The 90-minute play.** Pick your **top 3 workloads** (structured extraction, agentic coding, tool-use — whichever you actually run). For each:

**(a) Pass-rate baseline (30 min).**
- Assemble **20 tasks** representative of the workload (real prompts, not synthetic).
- Run each through Fable 5 free-tier + your current default model (probably Sonnet 5, GPT-5.6 Terra, or Grok 4.5).
- Log two columns: **task pass/fail** and **JSON-schema conformance** separately (per [Willison Jul 4](https://simonwillison.net/2026/Jul/4/better-models-worse-tools/) — a task can "pass" logically but fabricate schema fields, and both matter).

**(b) Cost per completed task (20 min).**
- Divide total tokens billed (or would-be-billed, since it's free) by number of *accepted* outputs.
- Compare against [Artificial Analysis' Fable 5 cost baseline of $11.80/task](https://artificialanalysis.ai/) — see how your workload sits vs the AA number.

**(c) Tool-call fabrication rate (20 min).**
- For workloads that use tools: count how many outputs include **extra fields not in the schema** or **missing required fields**. Divide by total tool-call outputs.
- **>10% fabrication rate = you need Layer-A schema enforcement** ([§4 below](#4-schema-verify-layer)).

**(d) Save + commit to your evals repo (20 min).**
- One CSV per workload: `task_id, model, cost, tokens, pass, schema_ok, fabrication_flags`.
- Commit with a timestamp — this becomes your Sunday-post evidence and your Ode/Anthropic cover-letter reference.

**Why this matters (for you).** These three numbers **are** the substrate for [`05` §3](./05-career-and-startup.md#3-artifact-brief)'s 3×3 matrix. Without them, the artifact is hand-wave; with them, it's screener-clearing.

Tags: `#anthropic #fable-5 #evaluation #urgency #90-min-play`

---

## 2. Evaluating Kimi K3 hosted — the 30-minute setup {#2-kimi-k3-eval}

**Why.** [`01` §1](./01-big-lab-moves.md#1-kimi-k3) landed Kimi K3 at #1 on Arena Frontend Code Arena, past Fable 5. To defend a routing decision including Kimi K3, you need **your own** numbers on **your** tasks, not Arena's numbers on Arena's tasks.

**Hosted access options (Sat Jul 18).**
- **Moonshot Platform** (native, mainland China): `platform.moonshot.cn` — needs a Chinese payment method, VPN-friendly. Fastest access to Kimi K3 Max.
- **OpenRouter** (US-friendly proxy): `openrouter.ai/moonshotai/kimi-k3` — pay per token in USD via Stripe. Slightly higher price, no VPN needed.
- **Databricks** (Inkling only, not K3 yet): [Databricks Blog Jul 15](https://www.databricks.com/blog/inkling-thinking-machines-lab-now-databricks) — enterprise access if your org has a Databricks account.

**Recommended setup (US-based, US-payment).**
1. Sign up for OpenRouter (5 min, free).
2. Add $10 credit — enough for ~2000 Kimi K3 requests at reasonable output length.
3. Point your existing eval harness at the OpenRouter endpoint (change base URL + model name; API is OpenAI-compatible).
4. Run the same 20-task-per-workload eval you ran for Fable 5 in [§1](#1-fable-5-evals) above.

**Reference API shape (OpenRouter, OpenAI-compatible):**
```python
from openai import OpenAI
client = OpenAI(base_url="https://openrouter.ai/api/v1",
                api_key=OPENROUTER_KEY)
resp = client.chat.completions.create(
    model="moonshotai/kimi-k3",
    messages=[{"role": "system", "content": SYSTEM},
              {"role": "user", "content": PROMPT}],
    max_tokens=2048,
    # Note: Kimi K3's "max reasoning" toggle is an extra_body param:
    extra_body={"reasoning_effort": "high"}
)
```

**Post-open-weights-drop plan (Jul 27).** Once Kimi K3 weights hit HF, decide: (a) keep using hosted for speed of iteration, (b) self-host on a rented H200/B200 for cost, or (c) fine-tune. **For your artifact deadline (this weekend), (a) is the right choice.**

**Sources.**
- [Tom's Hardware — Kimi K3 release notes](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3) `[primary journalism]`
- [Simon Willison — Kimi K3, and what we can still learn from the pelican benchmark](https://simonwillison.net/2026/Jul/16/kimi-k3/) `[practitioner]`
- [Codersera — Kimi K3: Moonshot AI's 2.8T Open-Weight Model — Release, Specs & Pricing](https://codersera.com/blog/kimi-k3-complete-guide-2026/) `[analysis]`

Tags: `#kimi-k3 #openrouter #evaluation #30-min-play`

---

## 3. Provider-availability probe — the primitive Gemini's no-show validates {#3-provider-probe}

**Why.** [`01` §2](./01-big-lab-moves.md#2-gemini-no-show): Gemini 3.5 Pro is 24+ hours past its own target with no model card. If your router assumes `gemini-3.5-pro` is available and it isn't, you either **hang, retry-storm, or crash**.

**The 30-line pattern (put in your router startup, once).**

```python
# probe.py — on-boot verification that declared models actually exist
from typing import Iterable

def probe_availability(models: Iterable[str], clients: dict) -> dict[str, bool]:
    """
    Sends a 5-token no-op to each declared model. Returns {model_id: True/False}.
    Call once at router startup; log to structured JSON so ops can see which
    providers dropped out today.
    """
    results = {}
    for model_id in models:
        provider = model_id.split("/")[0]  # e.g. "google", "anthropic"
        try:
            _ = clients[provider].chat.completions.create(
                model=model_id, max_tokens=5,
                messages=[{"role": "user", "content": "ping"}],
                timeout=8,  # tighter than default; a slow provider counts as unavailable
            )
            results[model_id] = True
        except Exception as e:
            results[model_id] = False
            log_provider_unavailable(model_id, str(e))
    return results

# in router bootstrap:
DECLARED = ["anthropic/claude-fable-5", "openai/gpt-5.6-terra",
            "xai/grok-4.5", "google/gemini-3.5-pro",
            "moonshotai/kimi-k3", "thinkingmachines/inkling"]
AVAILABLE = probe_availability(DECLARED, PROVIDER_CLIENTS)
ROUTER_CHAIN = [m for m in ROUTER_CHAIN if AVAILABLE.get(m, False)]
```

**Interview-ready framing.** *"After the Gemini 3.5 Pro target-date slip on Jul 17-18, I added an on-boot availability probe to my router. It sends a 5-token ping to each declared model, prunes the chain, and logs any provider unavailability to structured JSON. Costs about $0.001 per boot and prevents the classic retry-storm-on-missing-model failure mode."* — that's a 60-second interview answer worth ~15 IQ points of screener-clearing.

**Why this matters (for you).** The pattern generalizes: **anywhere your product depends on an announced-but-unshipped vendor capability, you need a probe**. Applies to: MCP server presence, tool-registry existence, LLM feature flags (extended-thinking, structured output, etc.), and jurisdiction-restricted models (Kimi K3 hosted may not be accessible from some IPs; probe on boot).

Tags: `#router #probe #reliability #production #interview-prep`

---

## 4. Schema-verify layer — Layer A + Layer B, still the killer for tool-call fabrication {#4-schema-verify-layer}

**Why.** [`01` §1](./01-big-lab-moves.md#1-kimi-k3): Kimi K3 is the new #1 on Arena Frontend Code Arena, but **it's untested on your task suite for the tool-call fabrication pattern Willison documented on Jul 4** ([Better Models: Worse Tools](https://simonwillison.net/2026/Jul/4/better-models-worse-tools/)). Assume Kimi K3 will have some non-zero fabrication rate until you measure it.

**The two-layer defense (unchanged from Willison; carried into every model you route to):**

**Layer A — strict JSON-schema validation at the tool boundary.** Use `jsonschema.Draft202012Validator` (Python) or `Ajv` with `strict: true` (Node). Reject any output that has:
- Extra keys not in the schema
- Missing required keys
- Type mismatches
- Enum values outside the declared enum

On rejection, return a **structured error** to the model so it can self-correct: `{"error": "invalid_output", "extra_keys": [...], "missing_required": [...]}`. **Do not** silently drop extra fields — the model will "learn" the fabrication is fine and keep doing it.

**Layer B — explicit schema echo in the system prompt.** Add a section:
```
When you produce structured output, use EXACTLY these fields, no others:
<JSON schema goes here, formatted>

Do not invent additional fields. If you want to communicate additional
information, use only the fields declared above. Extra fields will cause
your output to be rejected.
```

**Both layers required.** Layer B reduces the fabrication rate; Layer A catches what slips through. Neither is sufficient alone.

**For Kimi K3 specifically:** Kimi's `reasoning_effort: "high"` mode consumes more test-time compute — expect **more** verbose outputs, therefore **more** opportunity for schema drift. Test at `"low"`, `"medium"`, `"high"` and pick the setting where **quality gain vs schema-drift rate** is best.

**Why this matters (for you).** Ships as part of [`05` §3](./05-career-and-startup.md#3-artifact-brief)'s router artifact. Test your Kimi K3 evals ([§2](#2-kimi-k3-eval) above) against both **schema-pass rate** and **task-correctness** — these can diverge sharply on the reasoning-effort dial.

Tags: `#schema-verify #tool-use #kimi-k3 #reliability`

---

## 5. Cache-hit follow-up (from 2026-07-17 §3): update your cache-hit numbers with Fable-5-free-tier data {#5-cache-hit-followup}

**Why.** Yesterday's edition ([2026-07-17/03 §4](../2026-07-17/03-practical-skills-and-tools.md)) surfaced **ProjectDiscovery's 7% → 84% cache-hit-rate playbook** (relocate volatile state out of the system prompt for a **59% total cost cut**). **Do the audit today** on your Fable 5 usage — the free-tier billing dashboard makes the before/after visible without touching your credit card, and this is your **only unmetered window** to run the audit properly.

**30-minute play.**
1. Open Anthropic Console → **Usage → Prompt Caching** dashboard.
2. Note your current **cache-read tokens as % of total input tokens**. Below 30% = big win available; below 10% = 4-6× cost cut sitting on the table.
3. Identify the **volatile state** in your system prompt: current-user-context, current-timestamp, session-state, recent-tool-results. **Move these to the user message**, keep the system prompt **stable**.
4. Rerun a canonical eval sequence (same tasks as [§1](#1-fable-5-evals) above), compare cache-hit-rate before and after.
5. Extrapolate to your Fable 5 (paid, post-Sun) or Sonnet 5 or Kimi K3 monthly budget. **If you don't hit at least 50% cache-hit-rate on high-volume workloads, you're leaving money on the table.**

**Sources.**
- [Anthropic — Prompt Caching docs](https://docs.claude.com/en/docs/build-with-claude/prompt-caching) `[primary]`
- [Anthropic — Prompt Caching Best Practices Cookbook](https://github.com/anthropics/claude-cookbooks/blob/main/misc/prompt_caching.ipynb) `[primary]`
- Yesterday's cache-hit playbook: [2026-07-17/03 §4](../2026-07-17/03-practical-skills-and-tools.md)

**Why this matters (for you).** The audit + the 3×3 matrix ([`05` §3](./05-career-and-startup.md#3-artifact-brief)) + the availability probe ([§3](#3-provider-probe) above) together form **one interview answer** that clears 3 questions in ~90 seconds: cost engineering, cross-vendor evaluation, production robustness.

Tags: `#cache-hit #anthropic #cost-engineering #audit`

---

## Cross-references

- [ACTIONS.md](../ACTIONS.md) — this weekend's actions refreshed
- Prior practical stack: [2026-07-17/03](../2026-07-17/03-practical-skills-and-tools.md) (Claude Code 2.1.212 fork/subtask + ultracode multi-agent JS + MCP 2026-07-28 stateless RC)
- [Simon Willison archive July 2026](https://simonwillison.net/2026/Jul/) — read the pelican-benchmark + Kimi-K3 posts today
