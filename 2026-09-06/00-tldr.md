# TL;DR — 2026-09-06 (Sunday)

Sixty-second skim. **The frontier moved on all three labs inside one week, and the enterprise-safety plumbing got redrawn.** **OpenAI shipped GPT-6 Astra (Sept 3)** with Greg Brockman on record calling it "the start of the AGI era" — 1M context, 72.6% OSWorld 2.0, saturates FrontierMath T4 and ARC-AGI-3, priced at $10/$50 per MTok. **Anthropic released Claude Fable 5.1 + Mythos 5.1 (Sept 1)** — same model, two safeguard tiers; cybersecurity false-positive rate cut ~60%, biology fallback ~85%; **Enterprise Frontier Safeguards (EFS)** moves monitoring into the customer's cloud. **Google DeepMind shipped Gemini 3.8 Flash + Flash Cyber (Sept 2).** **Sonnet 5 promo pricing ended Aug 31** — every prod bill re-prices tomorrow if it hasn't already. And the **FDE market crossed 982 live postings / 462 companies**, with OpenAI opening **Healthcare + Legal FDE tracks**. **OpenAI DevDay Sept 29** is the next scheduled inflection point.

*(This is the first edition after a long gap in the archive — treat it as a fresh week's read. Cross-references back to the [2026-07-25 edition](../2026-07-25/) where a thread survives.)*

---

1. **OpenAI GPT-6 Astra ships (Sept 3) — first model marketed as "AGI-adjacent" by an OpenAI officer on the record.** 1M context; **72.6% OSWorld 2.0** (edges Claude Opus 5 at 70.2%); **97.6% FrontierMath T4** (saturation); **99.9% ARC-AGI-3**; **100% ExploitBench**; average computer-use task 75 min → 40 min. **$10 / $50 per MTok** (Fast mode 2×; cached $1; batch half); rollout starts with Daybreak enterprise, ChatGPT + Azure + Bedrock. → [`01` §1](./01-big-lab-moves.md#1-gpt6-astra) · [`03` §1](./03-practical-skills-and-tools.md#1-astra-vs-opus5) `#openai #gpt-6 #astra #agi #benchmarks`

2. **Claude Fable 5.1 + Mythos 5.1 (Sept 1) — same weights, two safeguard tiers, quieter guardrails.** Fable 5.1 is GA; Mythos 5.1 is restricted-access (cyber + life sciences). **Cyber safeguards fire ~60% less often on benign requests; biology fallback ~85% less.** New **Enterprise Frontier Safeguards (EFS)** ships monitoring telemetry to the *customer's* cloud — zero-retention + misuse detection stop being mutually exclusive. → [`01` §2](./01-big-lab-moves.md#2-fable-mythos-5-1) · [`02` §3](./02-new-emerging.md#3-efs-primitive) `#anthropic #fable-5-1 #mythos-5-1 #efs #safeguards`

3. **Sonnet 5 promotional pricing ended Aug 31 → $3 / $15 per MTok from Sept 1.** If your team was quietly running Sonnet 5 as the workhorse under the promo, this is a **50% input / 50% output cost jump on the same code path.** Audit today; the reroute (Fable 5.1 for hard subtasks, Sonnet 5 for medium, Haiku 4.5 for cheap) usually beats a straight price-through. → [`03` §3](./03-practical-skills-and-tools.md#3-sonnet-repricing) `#anthropic #sonnet-5 #pricing #cost-audit`

4. **Google DeepMind: Gemini 3.8 Flash + 3.8 Flash Cyber (Sept 2) — third Flash in six weeks, still no new Pro.** Priced at 3.7 Flash levels with better coding/reasoning; on DeepSWE v1.1 it beats "most larger frontier models at a fraction of the cost." Flash Cyber echoes Anthropic's Mythos-tier pattern (restricted, cyber-focused). Google is winning on **workhorse cadence** while Anthropic and OpenAI absorb the flagship air. → [`01` §3](./01-big-lab-moves.md#3-gemini-38-flash) `#google #gemini-3-8 #flash #cyber`

5. **Claude Code Sept updates — enterprise MCP + headless permission + smaller binary.** New `managedMcpServers` setting lets orgs push HTTP/SSE MCP servers to every user (one config, N seats). `--permission-prompts none` unblocks CI / unattended hosts (default-deny anything prompt-worthy). Native binary re-compressed with **zstd — 340 MB → ~75 MB on Linux x64.** → [`03` §2](./03-practical-skills-and-tools.md#2-claude-code-updates) `#claude-code #mcp #devex #enterprise`

6. **The FDE surface is now measurable: 982 live postings across 462 companies (as of Sept 4).** Palantir + OpenAI + Databricks + Mistral + Cohere + Cresta + Scale still lead. **OpenAI opened Healthcare + Legal FDE tracks** this week — first time verticalization inside a lab's FDE org is public. Mid $300–450K TC · Senior $450–550K · Staff $600K+. This is the highest-leverage single lane for the ME.md target set. → [`05` §1](./05-career-and-startup.md#1-fde-market) `#fde #applied-ai #openai #healthcare #legal #careers`

7. **Emerging capital: vague AI can't raise anymore; vertical + regulated + revenue-adjacent can.** Week's stand-outs: **AusperBio Therapeutics $120M Series C**, **Elucid $55M Series D** (health tech), **InstaAstro $12M Series A** (consumer vertical). Compute + chips + robotics + legal + healthcare vertical tools continue to concentrate capital. **Seed → Series B has re-priced** for horizontal wrappers. → [`02` §1](./02-new-emerging.md#1-funding-week) · [`05` §2](./05-career-and-startup.md#2-startup-lens) `#funding #vertical-ai #biotech #healthtech`

8. **OpenAI DevDay Sept 29 (San Francisco) — the next dated inflection point.** Historically the Codex / GPT SDK / Managed Agents surfaces get updated here; with Astra now out, expect a **realtime + computer-use + agents SDK** wave. Pre-stage a one-page comparison table and calendar the keynote. → [`02` §2](./02-new-emerging.md#2-devday-preview) `#openai #devday #calendar`

9. **Research: multi-agent adversarial-attack surface + long-horizon coding evals hardened.** GLOBECOM 2026 accepted *Adversarial Attacks in Multi-Agent LLM Pipelines* (structural vulnerabilities in agentic architectures — this is now a design constraint, not a bug class); the **VoltAgent awesome-ai-agent-papers** list crossed a threshold of usable curated papers (memory, RAG, tooling, eval, observability, security). → [`04` §1](./04-research-progress.md#1-adversarial-multiagent) · [`04` §2](./04-research-progress.md#2-agent-papers-curated) `#arxiv #agents #security #survey`

---

## One thing to DO this Sunday

→ **Ship a 3-model comparison artifact by tonight.** Take one real task from your portfolio (an MCP server exercise or the dual-model sanitiser you scoped in the [May 20 edition](../2026-05-20/03-practical-skills-and-tools.md)), and run it three ways: **GPT-6 Astra (`Fast` off) · Claude Fable 5.1 · Gemini 3.8 Flash**. Log per-call latency, cost, and one-shot correctness. Publish it as a public gist by Monday morning. This is **the exact artifact** the ME.md portfolio lists as "1-page Gemini-vs-Claude-vs-OpenAI comparison" and it's cheaper to build this week than any other: all three flagships are 1M context, and Astra + Fable both just moved. Cross-link: [`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact).

## Watchlist deltas since the 2026-07-25 edition

- 🆕 **GPT-6 Astra** — new thread. The AGI-framing hits the record; also normalizes $10/$50 as the new flagship price band (2× Opus 5).
- 🆕 **Claude Fable 5.1 / Mythos 5.1 + EFS** — extends the [Opus 5 thread from 2026-07-25](../2026-07-25/01-big-lab-moves.md#1-opus-5); safeguard-tiering + customer-cloud telemetry is a new product primitive.
- ➡️ **MCP as protocol** — the [2026-07-28 stateless spec](../2026-07-25/02-new-emerging.md#4-mcp-stateless) is in the wild; enterprise-managed MCP servers (Claude Code `managedMcpServers`) is the first *deployment* primitive after the protocol matured.
- ➡️ **FDE market** — extends the [+1,165% YoY thread from 2026-07-25](../2026-07-25/05-career-and-startup.md#2-fde-market); now measured at 982 live postings, and **OpenAI just opened Healthcare + Legal FDE tracks** — first public verticalization of a lab FDE org.
- ⬇️ **Gemini 3.5 Pro** — still no ship, three Flash releases into the trough; keep watching, don't wait.
- 🆕 **DevDay 2026 (Sept 29)** — new calendar item. Every serious portfolio should have a live comparison artifact by then.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + GPT-6 Astra in [`01` §1](./01-big-lab-moves.md#1-gpt6-astra) + Sonnet 5 repricing in [`03` §3](./03-practical-skills-and-tools.md#3-sonnet-repricing) |
| 20 min | [`01` §1–3](./01-big-lab-moves.md) (Astra + Fable 5.1 + Gemini 3.8 Flash) + [`05` §1](./05-career-and-startup.md#1-fde-market) (FDE market snapshot) |
| Tonight | [`03` §4](./03-practical-skills-and-tools.md#4-this-weekends-artifact) — build and publish the 3-model comparison |
| Before Sept 29 | [`02` §2](./02-new-emerging.md#2-devday-preview) — pre-stage the DevDay watch plan |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
