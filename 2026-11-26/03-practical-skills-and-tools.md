# Practical Skills & Tools — 2026-11-26

The three-frontier-labs-at-$8/$40 moment makes **cost-aware routing** suddenly a credible résumé item (with real dollar savings attached). **Claude Ship (Nov 23)** is the single highest-signal portfolio add this long weekend — it puts an agent at the *approval* seat on your own repo and gives you a one-screenshot story. **Claude Code shipped three material updates this month (2.1.319 auto-mode-default on Nov 6, 2.1.326 Code Mode in agent teams, 2.1.327 short-notes subagent summaries on Nov 17)** — detailed in [2026-11-25 §3 §1](../2026-11-25/03-practical-skills-and-tools.md#1-claude-code-nov-cluster); **Fast mode on Opus 4.8 sunsets Nov 30** (4 days away, no fallback). **MCP 2026-07-28's stateless spec + "Predictable Release Cycle" freeze** (see [2026-11-25 §3 §2](../2026-11-25/03-practical-skills-and-tools.md#2-mcp-release-cycle)) means MCP is treating itself as production infrastructure now. This file is five concrete things you can actually ship over the long weekend.

Tags: `#claude-code #mcp #agents #router #evals #fde-portfolio`

---

## 1. Cost-aware routing across Fable 5.2 / GPT-6.2 / Gemini 4 Carbon {#1-cost-aware-router}

**What to build:**
- A **three-provider router** that splits traffic across Claude Fable 5.2 (Anthropic), GPT-6.2 Astra (OpenAI), and Gemini 4 Carbon (Google) using **the exact same price point** at the frontier tier ($8/M in, $40/M out — Carbon lands there after Nov 30 promo).
- For cheap/daily traffic: **Haiku 5.5 vs. Sol vs. Hydrogen** — this is where the real cost deltas live. Sol at $2/$10 vs. Haiku 5.5 vs. Hydrogen is where you can save real money on a vertical workload.
- Wire it with **LiteLLM** (easiest), **OpenRouter** (hosted), or roll a thin FastAPI shim yourself.
- **Hard eval gate:** before promoting any routing decision to production, you must have an **eval set of ≥20 prompts** with a scoring rubric. This is the piece most routers skip and the piece that makes it credible.

**Weekend milestone:** publish a ~500-word writeup with a cost-per-task chart + eval parity numbers + the router repo link. **This is a résumé-ready artifact** for FDE/MLE applications this cycle.

**Sources:**
- [OpenAI — Introducing GPT-6.2 Astra & Sol pricing](https://openai.com/index/introducing-gpt-6-2-astra-sol) `[primary]`
- [Let's Data Science — Gemini 4 Carbon pricing $4/$20 post Nov 30](https://letsdatascience.com/news/google-rolls-out-gemini-4-carbon-to-general-public-9b41bcb4) `[secondary]`
- [Decrypt — Astra pricing challenges Anthropic](https://decrypt.co/383488/openai-gpt-6-2-astra-challenges-anthropic-price-but-not-every-benchmark) `[secondary]`

### Why it matters to you
- **Job lens:** FDE interview loops routinely ask **"show me where you saved a customer money"** — a router with a real eval harness + a chart is the quickest answer. Target bands: **Glean Founding FDE $160–270K; Distyl $150–250K; Anthropic FDE $200–300K base + RSU.**
- **Startup lens:** If you're pricing a product above 2× API cost, the router is both a margin-recovery tool and a credible "we've done the infra work" signal for enterprise buyers.
- **Insight:** **Routing is the new fine-tuning in terms of résumé value.** It's a project you can realistically finish in a weekend, demonstrates systems thinking, and lets you discuss cost/quality tradeoffs on-script in interviews.

---

## 2. Claude Ship — set it up on your own repo this weekend {#2-claude-ship-setup}

**What it does:**
- Claude Ship (launched Nov 23, Team + Enterprise) sends an agent team to GitHub PRs that **reviews, proposes fixes, applies them to a branch, and auto-approves** when configured eval gates pass. Expected cost $15–25 per PR at launch.
- This extends what Code Review (March 2026) did — it previously commented; now it closes the loop end-to-end.

**Ship this weekend (steps):**
1. **Install Claude Code GitHub app** on a public repo you control (a toy project is fine — the artifact is what matters).
2. Add a `.claude-ship.yml` at the repo root with: (a) trigger (on-PR by default), (b) eval gate (tie to your existing CI test suite — if green, agent may approve), (c) label-based scoping (only PRs labeled `agent-reviewable` get Ship).
3. Open one PR, let Ship review → fix → approve. **Screenshot the approval event.**
4. Write a short post-mortem: what the agent caught, what it missed, what eval you'd add next.
5. Pin the PR link + screenshot to your portfolio / LinkedIn / GitHub profile README.

**Risk hygiene:**
- **Never let Ship auto-approve against a `main` branch with no required-review bypass** in a repo that matters — use feature branches.
- Pair it with required status checks that **include a human-eyes step** for any PR touching auth, billing, or infra.

**Sources:**
- [TechCrunch — Anthropic launches Claude Ship](https://techcrunch.com/2026/11/23/anthropic-launches-claude-ship-letting-ai-agents-review-fix-and-approve-code-changes/) `[secondary]`
- [Anthropic — Bringing Code Review to Claude Code](https://claude.com/blog/code-review) `[primary]`
- [Claude Code docs — Code Review](https://code.claude.com/docs/en/code-review) `[primary]`
- [Help Net Security — AI agents find bugs in PRs](https://www.helpnetsecurity.com/2026/03/10/anthropic-claude-code-review/) `[secondary]`

### Why it matters to you
- **Job lens:** **Claude Ship is the single most discussable Anthropic surface for FDE/Solutions interview loops this fortnight.** You will be asked about agent-approval loops; walking in with a screenshot answer is a shortcut past most of the technical screen.
- **Startup lens:** If you pitch anything PR-review adjacent, you now compete with Anthropic directly. Pivot to verticals (SOC2-regulated, Rust, Solidity, SQL migrations) or orchestration (multi-repo policy-as-code).
- **Insight:** **Auto-approve by an agent is a compliance event waiting to happen.** Build the **audit trail + revocation + eval-coverage tooling** around Claude Ship before the first regulated-industry incident forces it.

---

## 3. MCP 2026-07-28 — 5-tool server as a ship-this-weekend portfolio artifact {#3-mcp-fastmcp}

**What to build:**
- A **5-tool MCP server** that solves one specific workflow problem you actually have (e.g., "search my Gmail + draft reply + attach relevant Drive file"; or "search my notes + generate an interview-prep card + save to Notion").
- Use **FastMCP** (the de-facto server framework) or write it in TypeScript against the official SDK.
- **The MCP 2026-07-28 spec is stateless-core + extension-based** — your server runs on Vercel / Cloudflare Workers / Lambda with no persistent connections. This is the publishable version.

**Ship criteria:**
1. 5 real tools (not 5 wrappers of the same CRUD).
2. **Eval set of 10 cases** — use `mcp-inspect` or a hand-rolled runner. Include 2 adversarial cases (prompt injection, tool-chaining misuse).
3. README with install-in-one-command instructions.
4. A short demo GIF embedded in the README.
5. Public GitHub repo; add to the [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) list for distribution.

**Sources:**
- [Anthropic — Bringing MCP 2026-07-28 to Claude](https://claude.com/blog/bringing-mcp-2026-07-28-to-claude) `[primary]`
- [MCP blog — 2026-07-28 release](https://blog.modelcontextprotocol.io/posts/2026-07-28/) `[primary]`
- [SiliconANGLE — Biggest MCP update brings metadata + cybersecurity enhancements](https://siliconangle.com/2026/07/28/biggest-ever-mcp-update-brings-metadata-cybersecurity-enhancements/) `[secondary]`
- [SD Times — MCP spec updates](https://sdtimes.com/ai/several-new-updates-make-their-way-into-the-mcp-specification/) `[secondary]`

### Why it matters to you
- **Job lens:** **MCP server authoring remains the #1 portfolio item for FDE / Integration Engineer applications.** From the 2026-11-14 edition forward, this has been the consistent recommendation and it has only strengthened.
- **Startup lens:** If your product has an MCP server, you're credibly in the "AI-native workflow" story for enterprise buyers. If it doesn't, you look like a 2024 SaaS.
- **Insight:** **The stateless-core shift means MCP servers are now deployable on the same serverless infra as your main product** — no sidecar process, no long-running daemon. Build the server *inside* your main app, not alongside.

---

## 4. The "tests-as-spec + eval gate" vibe-coding loop {#4-tests-as-spec}

**What the pattern is:**
- Write a **failing test first** that captures the acceptance criterion. Let the agent iterate until the test passes.
- Add an **eval gate** on top (not just test pass, but **output-quality** check — e.g., response matches a rubric, stays under a token budget, cites sources).
- CI runs both; merges blocked if either fails.
- This is the pattern **Claude Ship implicitly requires** — the eval gate is what Ship uses to decide whether to auto-approve.

**Minimum viable implementation:**
```yaml
# .github/workflows/eval-gate.yml
on: pull_request
jobs:
  eval:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: pip install -e . && pytest -xvs tests/
      - run: python eval/run_eval.py --min-score 0.85
```

Where `eval/run_eval.py` is a thin harness over your actual LLM calls that scores outputs against a rubric (keyword presence, length bounds, LLM-as-judge with a different model).

### Why it matters to you
- **Job lens:** Being able to describe the eval harness you designed in one minute is the clearest signal of **real agent experience** vs. prompt-engineering cosplay. Every FDE interview loop this fortnight asks for it.
- **Startup lens:** **Enterprise buyers now ask for eval-gate CI** as part of vendor diligence. Having this in your repo makes your SOC2 / vendor-security review 10× faster.
- **Insight:** **LLM-as-judge is still the fastest-to-implement rubric** — it's not perfect but it beats "check it manually." Use a *different* model as judge than the one being evaluated (e.g., Fable 5.2 judging GPT-6.2 outputs); it dampens the sycophancy failure mode.

---

## 5. Serving a Chinese open-weight model for a non-US edge deployment {#5-open-weight-serving}

**What to try:**
- Download **Kimi K3 (modified-MIT license)** weights or a distilled variant from Hugging Face.
- Serve with **vLLM** or **SGLang** on a single H100 or 2× L40S (a small adapter variant will fit; the 2.8T full model won't on commodity hardware — look for 72B / 100B K3-derived variants).
- Build a **thin adapter** for your domain (one LoRA epoch on <1K domain examples is enough for a demo).
- Wire it behind the same API shape as your OpenAI / Anthropic SDK call — so you can toggle between frontier and open-weight with one env var.

**Why do this:** this project gives you a **"we can run the frontier offline" story** for any regulated / non-US customer. It's also **a credible on-ramp to an NVIDIA / Baseten / Modal / Replicate / Together applied-ML role.**

**Sources:**
- [The Decoder — Moonshot releases Kimi K3 open weights + infrastructure](https://the-decoder.com/moonshot-ai-releases-kimi-k3-open-weights-and-infrastructure-after-shaking-up-the-frontier-model-race/) `[secondary]`
- [Forkast — Chinese open-weight frontier compresses into two licensing models](https://forkast.news/chinese-open-weight-frontier-compresses-five-labs-thirty-days-two-licensing-models/) `[analysis]`
- [SCMP — Moonshot world's largest open-source model](https://www.scmp.com/tech/tech-trends/article/3360885/moonshot-ai-unveils-worlds-largest-open-source-ai-model-china-narrows-gap-us-rivals) `[secondary]`
- [ai2.work — Chinese open-weight leaderboard](https://ai2.work/blog/chinese-labs-own-the-open-weight-leaderboard-glm-deepseek-qwen) `[analysis]`

### Why it matters to you
- **Job lens:** **Open-weight serving (vLLM / SGLang / TGI) is the single most under-supplied skill in the current AI job market.** Everyone can call an API; far fewer can run inference at throughput on a GPU they don't own. This is the lane for ex-infra engineers and CS grads with distributed-systems chops.
- **Startup lens:** On-prem / offline / sovereign-cloud AI is a growing enterprise RFP line item. If you can credibly deploy a frontier-adjacent model behind a customer's firewall, you have a wedge no API-passthrough competitor can match.
- **Insight:** **The frontier-vs-open gap is now narrow enough that for most vertical workflows, a well-tuned open-weight is good enough and 10–50× cheaper per inference.** The arbitrage window for this will stay open through at least Q2 2027.

---

## Weekend plan: pick two

| If you have... | Build this | Hours |
|---|---|---|
| 4 hours | §2 Claude Ship on a toy repo | 4 |
| 1 day | §1 Router + §4 eval gate | 6–8 |
| 1 weekend | §3 MCP server + §4 eval gate | 12–16 |
| 2 weekends | §3 MCP server + §5 open-weight adapter | 20+ |

Pick two; ship them public; link from your LinkedIn and your GitHub profile README. That's the portfolio advance this fortnight.
