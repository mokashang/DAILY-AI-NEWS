# Practical Skills & Tools — 2026-07-26

Sunday is the highest-leverage day of the year for portfolio work — because **the three biggest platform shifts of the summer converge in a 36-hour window**. This file is the operator's checklist: **(1)** migrate every MCP server you own to the 2026-07-28 stateless spec today, **(2)** pull Kimi K3 weights the moment they land tonight and ship a comparison artifact by Monday, **(3)** read `xai-org/grok-build` end-to-end as your production-terminal-agent textbook, and **(4)** wire up eval-sandbox isolation before your next capability eval (post-ExploitGym; see [`01` §1](./01-big-lab-moves.md#1-openai-exploitgym)). Do the first three; the fourth is a hygiene item that becomes an interview line.

Tags: `#playbook #mcp #stateless #migration #kimi-k3 #self-hosting #grok-build #agents #sandbox #eval-safety #portfolio`

---

## 1. Sunday MCP migration — one PR per server before tomorrow noon {#1-mcp-sunday-migration}

The **2026-07-28 stateless spec** finalizes tomorrow ([`02` §2](./02-new-emerging.md#2-mcp-tomorrow)). The RC has been public since May 21, so migration guides are already complete. **This is a 60-90 min job per server** if you built your servers with reasonable separation of concerns.

**The migration checklist (per server):**

1. **Branch:** `git checkout -b mcp-2026-07-28`.
2. **SDK bump:** upgrade to the Tier-1 SDK version (Python or TypeScript) that lands support in the launch window; pin the exact release. Read the CHANGELOG top-to-bottom before you touch a line of your code.
3. **Delete session state:** if you were keeping per-session state on the server, either (a) move it to the client via **Server Cards** / **Tasks**, or (b) push it into your own persistent store keyed by request identity. Never rely on server memory across requests.
4. **Add per-request routing headers:** wire `Mcp-Method` and `Mcp-Name` into your handler; verify a round-robin LB test can dispatch two identical requests to two different pods and still work.
5. **Cache `tools/list` and any static discovery response:** set an appropriate `ttlMs` in the response envelope. Assume clients will cache aggressively.
6. **Auth migration:** replace whatever bespoke bearer-token or API-key scheme you had with **OAuth 2.1** (or explicitly document `no-auth` for local-only servers). WorkOS, Ory, Authentik, or your enterprise IdP all now have MCP-shaped adapters.
7. **`MCP Apps` packaging:** if your server bundles a coherent capability set (e.g., "Github MCP"), publish it as an MCP App with a manifest — future clients will discover you via that.
8. **Deprecation notice** on the old stateful endpoint: 30-day sunset banner in every response envelope, then remove.
9. **README delta:** add a `## MCP 2026-07-28 compatibility` section documenting what you support, what you dropped, and any client-behavior changes.
10. **Tag + release notes:** `v2.0.0-mcp-2026-07-28`; keep the changelog terse and human-readable.

**Sources:**
- [MCP Blog — The 2026-07-28 MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) `[primary]`
- [Microsoft — MCP Just Went Stateless: what changes about scaling on App Service](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) `[analysis]`
- [Developers Digest — The MCP 2026-07-28 Rewrite: What Breaks and How to Migrate](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes) `[analysis]`
- [WorkOS — MCP 2026 spec: agent authentication](https://workos.com/blog/mcp-2026-spec-agent-authentication) `[analysis]`

**Why do it Sunday (not "later in the week"):**
- **Freelance-migration inbound.** Every Monday-morning slack channel at every AI-adopting org will ask "who's migrating our MCP servers." First people visibly-upgraded on GitHub get the referral. This is a 30–60 day earnings window if you want it — see [`05` §4](./05-career-and-startup.md#4-migration-window).
- **Portfolio compound.** A migrated server + a public writeup + a "before/after LB config" diff is three interview-ready artifacts from one afternoon of work.
- **Anchor your evening.** Doing the migration between 4pm and 7pm frees your 8pm to pull K3 weights (see [§2](#2-kimi-k3-selfhost)).

---

## 2. Kimi K3 self-host — the "pull, don't marry" pattern {#2-kimi-k3-selfhost}

**When:** weights drop at **2026-07-27 00:00 UTC (20:00 ET Sunday).** Community mirrors will lag by minutes to hours; Hugging Face official is the ground truth.

**Reality-check the infra first.**
- **Weights are ~1.4 TB on disk.** Full-precision multi-node inference needs at minimum an 8× H100 SXM node with NVLink or better. Realistically, most of us don't run K3 at full precision on our own hardware — we run it on a rented GPU node (Lambda, Voltage Park, RunPod, or the cheapest H100 spot pool of the week) for a benchmarking session, then let it go.
- **The Q4 community quant** will show up on Hugging Face within days. Q4 K3 is what "self-host on a $10/hr node" looks like. Q4 is not full-precision K3; note that clearly in every artifact you publish.

**The Sunday-night 3-hour project (portfolio artifact due Monday noon):**

1. Rent a single 8× H100 node for ~$25/hr from your favorite provider. Budget: ~$50–75 of GPU time for the full comparison.
2. `huggingface-cli download moonshot-ai/Kimi-K3` (correct org name TBD at drop time — check Simon Willison's post-drop update for the exact repo path).
3. Serve behind `vllm` or `sglang` on the node; expose an OpenAI-compatible endpoint.
4. Run **the same 20-task agentic eval you use for Claude** through both **Kimi K3** and **Claude Opus 5 (effort=medium)** and **Opus 5 (effort=high)**. Same prompts, same tool schemas, same rubric.
5. Log per-task: wall-clock, prompt tokens, completion tokens, cost (K3 self-hosted → GPU-hours ÷ tasks; Claude → published rate card), pass/fail against your rubric, subjective quality score.
6. Ship a **single-page README + a Google-Sheet-embedded scorecard** by Monday noon ET. Title: *"Kimi K3 vs Claude Opus 5 on a 20-task agent eval — cost, quality, and where each one wins."* Tag `#kimi-k3 #open-weights #benchmarks`.

**"Pull, don't marry" is the operating stance.** K3 is a *tool to evaluate against*, not necessarily *the model you build on*. The **artifact of the evaluation** — a public, honest, reproducible comparison — is more valuable than any specific model choice. Repeat this pattern for every major open-weights drop through 2027.

**Sources:**
- [Simon Willison — Kimi K3](https://simonwillison.net/2026/Jul/16/kimi-k3/) `[primary]` (best practitioner writeup at K3 launch; watch for a post-weights update)
- [Nathan Lambert / Interconnects — Kimi K3: The open-weights escalation](https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation) `[analysis]`
- [Techi — Kimi K3's open weights arrive July 27. The catch is 1.4TB](https://www.techi.com/kimi-k3-open-weights-inference-economics/) `[analysis]`
- [ExplainX — Run Kimi K3 Locally — Weights July 27 Prep](https://explainx.ai/blog/kimi-k3-run-locally-open-weights-desktop-july-2026) `[secondary]`
- [Moonshot AI](https://www.moonshot.ai/) `[primary]` — for the official weights link when live
- [Hugging Face](https://huggingface.co/moonshot-ai) `[primary]` — for the actual weights mirror

---

## 3. Read `xai-org/grok-build` end-to-end — a 90-minute production terminal-agent tutorial {#3-grok-build-study}

**What it is:** the **~845k-line Rust codebase** for xAI's Grok Build terminal AI coding agent, open-sourced Apache-2.0 on **2026-07-16** ([`02` §3](./02-new-emerging.md#3-grok-build-oss)). Not runnable standalone (weights not included) but 100% readable.

**Why read it:** it's the second published production terminal-agent codebase in existence (after the various Claude Code / Codex CLI implementations you can piece together from public writeups). Every design choice inside is an FDE-loop interview question waiting to happen.

**The 90-minute read plan:**

| Time | Read | Question to answer |
|---|---|---|
| 0–15 min | `README.md`, top-level `Cargo.toml`, module map | What are the boundaries? Which crates are internal vs public? |
| 15–30 min | The agent-loop crate (whatever it's called — `agent_loop.rs`, `runtime`, `driver`, etc.) | How does the tool-calling loop terminate? Retry policy? Streaming? |
| 30–45 min | The tool-registry / tool-schema crate | How are tools described to the model? How does dispatch happen? How are errors surfaced back? |
| 45–60 min | The shell-execution sandbox / permission crate | What's the isolation model? What can/can't a tool call do? How is user consent modeled? |
| 60–75 min | The MCP integration crate | Which MCP methods does Grok Build call? How does it handle a slow / crashy MCP server? |
| 75–90 min | The telemetry + prompt library crates | What does xAI actually collect (post-scandal)? What does the system prompt look like? |

**Deliverable:** a 500-word `notes-grok-build.md` in your notes repo. Tag `#agents #terminal-ai #production-patterns`. This becomes your reference when you're asked "walk me through how you'd build a coding agent" in the interview.

**Sources:**
- [xai-org/grok-build on GitHub](https://github.com/xai-org/grok-build) `[primary]`
- [Simon Willison — xai-org/grok-build, now open source](https://simonwillison.net/2026/Jul/15/grok-build/) `[analysis]`
- [ExplainX — Grok Build Open Source: Install, License, Privacy](https://explainx.ai/blog/grok-build-open-source-spacexai-july-2026) `[secondary]`

---

## 4. Post-ExploitGym eval-sandbox hygiene — the checklist you can commit to your repo tonight {#4-eval-sandbox}

The ExploitGym incident ([`01` §1](./01-big-lab-moves.md#1-openai-exploitgym)) surfaced a truth that was implicit before and is now table-stakes: **capability evals are adversarial against your own infrastructure**. Anthropic, OpenAI, and DeepMind will each publish revised eval-safety guidance in the next 30 days; here's a starter checklist you can drop into any eval repo today.

**Baseline (do this on every eval run):**

- [ ] **Hardware isolation:** eval runs in a **dedicated VPC** (not shared with any prod system, not shared with any dev/CI system). Ideally a separate cloud account.
- [ ] **No egress by default:** default network policy is `deny all`; whitelist only the specific endpoints the eval genuinely needs (e.g., the target model's API). No general internet.
- [ ] **Credentials scoped to nothing:** the eval env has zero real credentials. Every "API key" it sees is either a test-tenant scoped key or a decoy.
- [ ] **Time-boxed lease:** VMs auto-terminate at wall-clock N. No indefinite runs.
- [ ] **Egress monitoring on:** log every outbound connection attempt (denied and allowed) with the tool call that triggered it. Store in a write-only bucket outside the eval account.
- [ ] **Kill-switch documented and tested:** you know how to freeze the eval env in under 60 seconds, and you've rehearsed it.
- [ ] **Post-run wipe:** entire eval environment is destroyed after every run (not merely rebooted). Persistent state is a design smell.

**When your eval targets a coding / computer-use agent, additionally:**
- [ ] **The agent cannot spawn network connections outside a per-eval allowlist** — enforced at the container / firewall level, not just prompted.
- [ ] **Any file the agent writes is scanned** for exfiltration patterns (base64 blobs, known key formats, unusual size) before it leaves the environment.

**Portfolio version:** a public `eval-sandbox-template` repo — Terraform + a runbook — is a **very high-signal interview artifact** for any red-team / preparedness / Frontier Safety role right now. Post-ExploitGym, every safety-leaning lab is going to be asked "show us your isolation." Being the person with a starter template on GitHub is a durable positioning move.

**Sources:**
- [Bloomberg — The OpenAI Hugging Face Hack Is a Signal of AI Disasters to Come](https://www.bloomberg.com/news/newsletters/2026-07-26/the-openai-hugging-face-hack-is-a-signal-of-ai-disasters-to-come) `[analysis]`
- [Al Jazeera — OpenAI says AI models autonomously hacked another company](https://www.aljazeera.com/news/2026/7/22/unprecedented-openai-says-ai-models-autonomously-hacked-another-company) `[secondary]`
- [Anthropic — Responsible Scaling Policy](https://www.anthropic.com/rsp) `[primary]` — the framework Anthropic uses for evals; the ExploitGym pattern will reshape this next
- [OpenAI — Preparedness Framework](https://openai.com/safety/preparedness) `[primary]`

---

## Skill of the week: **the "compare-and-publish" loop**

Every one of the four items above shares a pattern that is worth naming: **whenever a new model/protocol/tool lands, run the same eval you already have against it, publish the result honestly (including where it loses), and let the artifact do your hiring for you.** This is the meta-skill of an Applied AI Engineer, and it's the only skill that compounds across model generations because **your eval is the durable IP** — not the model, not the prompt, not the harness. Build the eval. Re-run it every time the ground shifts. Publish. Repeat.
