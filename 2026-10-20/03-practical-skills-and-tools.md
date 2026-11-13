# Practical Skills & Tools — 2026-10-20

Two things to do with your hands this week. **(1) Pick a Scion good-first-issue and ship a PR before Scion crosses 1K stars** — the "early contributor" window on an Anthropic-authored infra tool is 30 days, decays fast; Scion is **new today** so the window is wide open. **(2) Extend the router V2 you were going to ship by Sunday Oct 25 (per Monday's edition) to a cache-aware five-vendor version that bakes in the Nov 30 Argon pricing cliff** — the artifact answers "do you know what shipped this week," "can you build cost-aware agents," AND "do you track the Nov 30 cliff" in one résumé line.

Tags: `#scion #router #claude-code #gemini-api #openai-api #anthropic-api #eval #open-source #portfolio`

---

## 1. Pick a Scion good-first-issue and ship a PR this week {#1-scion}

**What:** Anthropic released **Scion**, an open-source Git replacement, this week (see [`01` §6](./01-big-lab-moves.md#6-scion)). The repo is new, which means issues are open, maintainers are responsive, and PRs are small-scope.

**Why this specifically:**
- A merged PR on `anthropic/*` has a different weight at Anthropic recruiting than a merged PR on, say, `langchain-ai/*`. "First 50 contributors" is a durable résumé claim.
- Scion is **brand new today** (released this week per [`01` §5](./01-big-lab-moves.md#5-scion)) — issues are open, maintainers are responsive, PRs are small-scope. The window won't be this wide again.
- The "early contributor" window on Anthropic infra tooling has a durable premium — see the Karpathy `CLAUDE.md` arc (109K stars, #1 trending for 28 weeks) and the Mythos / OpenClaw / autoresearch pattern.

**Steps (90–120 min):**
1. `git clone` the repo. Read the README + CONTRIBUTING in full.
2. Browse `good-first-issue` and `help-wanted` labels. Pick one with a clear acceptance criterion.
3. Reproduce the bug / implement the small feature on a branch.
4. Add a test (or follow repo convention — some early-stage infra repos use integration tests only).
5. Open the PR with a clean commit message and a 2–3 sentence description.
6. Add a line to your LinkedIn / portfolio referencing the merged PR by number.

**Fallback if nothing on good-first-issue fits:** a **doc PR** (fix a typo, clarify an install step, add a missing error-message explanation) is still worth filing. Doc PRs on infra tools from a vendor like Anthropic read as "pays attention to detail, operates in open source" at the recruiter stage.

### Why it matters to you

- **Job:** "Early contributor to Anthropic Scion (PR #<xx>)" is a one-line résumé entry that lands harder than three unrelated side projects.
- **Startup:** Reading Scion end-to-end tells you Anthropic's current taste on the "AI-native coder stack" — provenance, large-diff merging, agent-concurrency. If you're building adjacent tooling, Scion is the shape to design against.

---

## 2. Extend the router V2 (Monday's edition) to a cache-aware five-vendor V3 — ship by Sunday Oct 25 {#2-router-v3}

**What:** Build on the router V2 that Monday's edition ([2026-10-19/03 §1](../2026-10-19/03-practical-skills-and-tools.md#1-router-v2)) specced out — Haiku 5.5 / Argon intro / GPT-6.1 Sol / Opus 5.5 — and extend it to **a five-vendor cache-aware harness**: add **Muse Spark Open** (local Mac Studio, from the Oct 18 edition) and **cache-aware routing policy** so the Argon −95% cached-input dial actually shows up in the cost ledger. Keep the Nov 30 Argon pricing-cliff baked into the cost projection.

**Why this specifically:**
- The "which-model" question has moved from a two-vendor choice (May) → three-vendor (last week) → **four- or five-vendor cache-aware routing problem** this weekend. Each new vendor adds one SDK + one cost schedule + one effort-level dial.
- Argon's **−95% cached-input discount** + Haiku 5.5's **effort levels** + GPT-6 Sol/Luna's **−50% API price cut** + Muse Spark Open's **$0 self-hosted inference** mean every production agent has a legitimate reason to call all five in the same hour on different workloads.
- **This exact spec is being asked at FDE / AI Integration Engineer interviews right now.** The 2026-09-10 version of this router (one-vendor, Claude-only) was already a credible portfolio piece. The five-vendor cache-aware version is table stakes for the Oct–Dec hiring season.

**Minimum scope (ship by midnight):**

| Piece | Content | Time |
|---|---|---|
| `router.py` | 50-line class with `.route(prompt, policy)` method; wraps `anthropic`, `google-genai`, `openai` clients | 25 min |
| `evals/cases.jsonl` | 10 prompts: 5 "cheap-tier appropriate" (classification, extraction, format conversion) + 5 "top-tier required" (multi-step reasoning, long-context synthesis, agentic planning) | 15 min |
| `evals/run.py` | Loop over cases × 3 providers × 2 tiers (cheap, top). Log cost, latency, success. Output `results.md` | 25 min |
| `README.md` | Setup, usage, "what this proves" (3 bullets) | 10 min |
| `routing_policy.py` | 20-line policy: cheap-tier default, escalate to top-tier if prompt length > N tokens OR previous attempt failed | 15 min |

**Stretch (this weekend):**
- Add **effort-level routing** for Haiku 5.5 (3 effort levels × 2 model tiers = 6 Anthropic configs).
- Add **cache-aware routing** that pre-populates Argon's cache for repeat-context workloads.
- Publish a blog post + a Twitter/X thread with the results table.

**One-liner version of the eval harness** (if you want to prototype in 10 minutes before building the full repo):

```python
# evals/quick.py — not the final artifact, just a smoke test
import time, anthropic, google.genai as genai, openai
providers = {
    "haiku-5.5":   lambda p: anthropic.Anthropic().messages.create(model="claude-haiku-5-5", max_tokens=200, messages=[{"role":"user","content":p}]).content[0].text,
    "argon":       lambda p: genai.Client().models.generate_content(model="gemini-4-argon", contents=p).text,
    "gpt-6-luna":  lambda p: openai.OpenAI().responses.create(model="gpt-6-luna", input=p).output_text,
}
cases = ["Classify: 'This stock is going to zero' as [bullish, bearish, neutral]",
         "In 3 steps, plan a user-interview recruiting flow for a B2B SaaS beta."]
for name, call in providers.items():
    for c in cases:
        t = time.time(); out = call(c); print(f"{name:12s} {time.time()-t:5.2f}s  {out[:80]}")
```

(**Verify SDK method names before running** — these providers change SDK surface area frequently. Treat the snippet as a scaffold, not production code.)

### Why it matters to you

- **Job:** The router repo is **the single most interview-relevant portfolio artifact** in Q4 2026. It demonstrates (a) you know which models shipped this week, (b) you can wire multi-vendor SDKs, (c) you can design an eval + cost ledger, (d) you can write a routing policy. That is **four of the five FDE job-description bullets** in one weekend's work.
- **Startup:** The same code is the **demo repo for a cache-aware routing SaaS**. Pitch: "we're the Twilio of model routing — one API, three vendors, cost-aware by default, cache-aware optional." Credible seed story for a two-person team shipping in Q1 2027.
- **Insight:** A router with a published eval table is the single clearest signal that you understand the *economics* of agent systems, not just the API surface. Every founder and every hiring manager is noticing who posts one this quarter.

→ Cross-link: [`05` §2 the apply plan uses this artifact](./05-career-and-startup.md#2-apply-plan).

---

## 3. Monitor the Fable 5.5 ship window — set a Claude Code eval-ready today {#3-fable-55-prep}

**What:** [`01` §4](./01-big-lab-moves.md#4-fable-55) reports Fable 5.5 in Azure's East US 2 catalog marked GA. Public ship could happen any day this week.

**Prep today (30 min):**
1. Pin your current Claude Code to a known version — `claude --version` and note it. (**Why:** so if the Fable 5.5 ship changes default behavior, you have a before-snapshot.)
2. Save an existing eval run with Haiku 5.5 + current Sonnet as the "before" baseline. 3 prompts, 3 runs each, JSON output. Store in `evals/baseline-2026-10-20.json`.
3. Set a repo-watch: subscribe to anthropic.com/news RSS or the GitHub repo `anthropics/anthropic-sdk-python` releases.
4. On ship day: re-run the eval, diff cost/latency/quality, publish a blog post titled "Fable 5.5 vs {baseline} on {your use case}" within 24h of release.

### Why it matters to you

Fastest-to-publish eval results on a brand-new model release are an **evergreen attention beat**. The pattern has worked for Mythos (May), Fable 5.1 (Sept), Haiku 5.5 (Oct). The window closes within 72 hours of release as a dozen other posts land. Beat the dozen.

---

## 4. Audit your current spend against Argon's −95% cached-input dial {#4-cache-audit}

**What:** Argon's cached-input pricing is a **step change** for workloads with high context-reuse. If your production or portfolio agents call the same long system prompt or RAG-fetched context repeatedly, Argon's cache will **cut your bill by 90%+** without changing your code structure.

**60-minute audit:**
1. For each agent / endpoint you own, estimate **what % of each call's token budget is unchanged across calls** (system prompt, retrieval docs that get re-fetched, few-shot examples).
2. For workloads at >50% context-reuse, estimate the Argon cached-input price: `(unchanged_tokens × $0.10/1M) + (new_tokens × $2/1M) + output_tokens × $10/1M`.
3. Compare to current spend on Haiku 5.5 / Sonnet / GPT-6 Luna.
4. If Argon is a 50%+ saving, migrate the top-cost workload and log the before/after.

### Why it matters to you

- **Job:** "Cut agent inference cost 60% via Argon cache migration" is a **tangible, numbered résumé bullet**. Every FDE / AI Platform Engineer interview will ask for a story like this.
- **Startup:** For any seed-stage agent product, Argon's cache dial is often the difference between burning $8K/mo on inference and burning $800/mo. That's a 10× runway extension on a Series A clock.

---

## 5. One-pager: the three-vendor routing cheat sheet (reference) {#5-cheat-sheet}

Keep this one-page reference next to the router repo. All prices are per 1M tokens, as of 2026-10-20.

| Vendor | Model | In | Out | Notes |
|---|---|---|---|---|
| Anthropic | Claude Opus 5.5 | — | — | Top tier; still wins Terminal-bench 4.0 |
| Anthropic | Claude Sonnet 5.x | ~$3 | ~$15 | Current workhorse; Fable 5.5 pending — expect reprice |
| Anthropic | Claude Haiku 5.5 | **$0.10** | **$0.50** | Default worker; configurable effort levels; 72.4% OSWorld 2.1 (offline subset) |
| Google | Gemini 4 Argon | **$2 → $4** (Dec 1) | **$10 → $20** (Dec 1) | **Cached in −95%**; leads 13/19 Google-reported benches |
| Google | Gemini 3.5 Flash | $1.50 | $9 | Cheap tier; GA since May 2026 |
| OpenAI | GPT-6 Sol / Luna | — | — | **−50% vs GPT-5.6 promo** (exact dollar price not fully disclosed on all SKUs); Codex Composer predictions beta |
| OpenAI | GPT-6 Pro — Parallel Agents | — | — | Multi-agent split; ChatGPT Pro tier |
| Meta | Muse Wonder (closed) | $4 | $20 | Closed frontier; parity claim with Fable 5.1 / GPT-6 Astra (unverified) |
| Meta | Muse Spark Open | 0 (self-host) | 0 (self-host) | Open weights; local on 2× Mac Studio |

**Rules of thumb:**
- **Default to Haiku 5.5 for classification / extraction / short-context tasks.**
- **Route to Argon when context-reuse > 50% (cache dial).**
- **Reserve top-tier (Opus 5.5 / GPT-6 Astra) for multi-step reasoning + long-context synthesis + agentic planning.**
- **Pin provider per workflow for 7-day eval windows** — avoid floating assignments that make attribution impossible.

### Why it matters to you

A pinned cheat sheet of this shape is **the one artifact that converts "I follow the field" into "I make the call."** Carry it into every interview.

---

Session cross-links: [`01` Big lab moves](./01-big-lab-moves.md) · [`02` New & emerging](./02-new-emerging.md) · [`04` Research progress](./04-research-progress.md) · [`05` Career & startup](./05-career-and-startup.md) · [`00` TL;DR](./00-tldr.md)
