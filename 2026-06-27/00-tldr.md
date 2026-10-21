# TL;DR — 2026-06-27 (Friday)

Sixty-second skim. **The week the federal whitelist became the product.** Yesterday's two simultaneous announcements made the new release paradigm legible: **OpenAI shipped GPT-5.6 Sol/Terra/Luna under explicit US government partner-gating** (~20 pre-cleared customers for Sol) and **Anthropic's Mythos 5 was re-authorized for ~100 cleared US institutions** after 14 days dark. The Trump AI executive order — which our 2026-05-22 edition tracked as "postponed" — was in fact **signed and is now operative** (correction logged in `WATCHLIST.md`). Underneath the policy news, an **inference-economics week**: **OpenAI + Broadcom unveiled "Jalapeño,"** OpenAI's first custom inference ASIC; **Qualcomm closed its $3.9B acquisition of Modular** (Mojo + MAX) for the CUDA-alt stack; **Baseten raised $1.5B Series F at $13B**. And the talent map kept redrawing: **John Jumper (AlphaFold, 2024 Nobel) left DeepMind for Anthropic**, two days after **Noam Shazeer left Google for OpenAI**. For you: the **government-gated tier reshapes which startups can build on which frontier models**, and **inference-infra megarounds are the cleanest non-frontier-lab MLE lane**.

---

1. **GPT-5.6 Sol/Terra/Luna shipped under partner-gating.** OpenAI's strongest model to date (Sol) plus efficient tier (Terra) and cheap cousin (Luna), with new "max reasoning effort" + "ultra mode" (parallel subagents). **Sol is limited to ~20 US-government-pre-cleared partners**; GA "in coming weeks." First major model release under the Trump EO. → [`01` §1](./01-big-lab-moves.md#1-gpt56) `#openai #gpt56 #regulation #agents`

2. **Anthropic Mythos 5 cleared for ~100 US institutions** — Commerce Sec. Lutnick green-lit re-enablement after ~2 weeks dark (June 12 → June 26). **Fable 5 remains offline** as of writing. Federal-cleared customer lists are now an actual moat. → [`01` §2](./01-big-lab-moves.md#2-mythos5) `#anthropic #mythos5 #exportcontrols`

3. **OpenAI + Broadcom unveil "Jalapeño"** — OpenAI's first custom inference ASIC, reticle-sized, nine-month design-to-tape-out (reportedly accelerated by OpenAI's own models). Targeted EOY 2026 deployment; claimed ~50% cheaper than Nvidia GPUs for inference. → [`01` §3](./01-big-lab-moves.md#3-jalapeno) · [`02` §1](./02-new-emerging.md#1-inference-week) `#openai #broadcom #chips #inference`

4. **Qualcomm closes $3.9B all-stock acquisition of Modular** (Chris Lattner; Mojo language + MAX runtime). Direct shot at CUDA lock-in; write-once-run-on-any-accelerator. Pair with **Qualcomm × Hugging Face expanded partnership (June 26)** = Qualcomm is now the most aggressive non-Nvidia/AMD player on the open-source inference stack. → [`02` §2](./02-new-emerging.md#2-qualcomm-modular) `#qualcomm #modular #cuda-alt #M&A`

5. **Baseten raises $1.5B Series F at $13B** — largest US venture round of the week. Altimeter / Conviction / Spark lead; **~20× YoY revenue**, **1B+ daily inference requests across 87 clusters**. Capital earmarked for workforce expansion + enterprise GTM. → [`02` §3](./02-new-emerging.md#3-baseten) · [`05` §2](./05-career-and-startup.md#2-baseten) `#funding #seriesF #inference #hiring`

6. **John Jumper (AlphaFold, 2024 Nobel) leaves DeepMind for Anthropic** to lead AI-for-science (built on Anthropic's earlier wet-lab + biological-agent work with Allen Institute and HHMI). **Noam Shazeer left Google for OpenAI 48 hrs earlier**. Bio/science is the new talent-war front. → [`01` §4](./01-big-lab-moves.md#4-talent) · [`05` §1](./05-career-and-startup.md#1-jumper-signal) `#anthropic #talent #ai-for-science`

7. **Real-work agent benchmark wave (arXiv this week):** **NatureBench** (frontier agents beat published-SOTA on only 17.8% of 90 Nature-family tasks, web-search disabled), **EnterpriseClawBench** (852 tasks distilled from real enterprise sessions — data not released, but recipe is), **RigorBench** (scores agents on engineering *discipline*: plan, verify, recover, abstain, atomic commits — not just test-pass), **CoffeeBench** (90-day economy sim with multi-agent trading). The eval bar moved from real-tool to **real-work outcomes + process discipline**. → [`04` §1](./04-research-progress.md#1-real-work-benchmarks) `#benchmarks #agents #arxiv #science`

8. **Practical: this week's act-tonight stack.** Claude Code Week 26 ships **`claude mcp login` + cross-repo subagents (GA) + `/usage` per-agent cost attribution**; **GLM-5.2 (MIT, 753B MoE, 1M ctx, 62.1 SWE-Bench Pro) at $1.40/$4.40 per Mtok** is a credible Claude-Opus fallback for ⅙ the cost; **Simon Willison's Moebius-0.2B browser-port walkthrough** doubles as a portfolio recipe. → [`03` §1](./03-practical-skills-and-tools.md#1-claude-code-week26) `#claude-code #mcp #cost #portfolio`

---

## One thing to DO this Friday

→ **Apply to ONE Google Cloud / Salesforce / Anthropic / OpenAI / Palantir FDE req tonight** (live reqs surfaced this week — see [`05` §3](./05-career-and-startup.md#3-fde-apply)). Pair the application with a **3-hour Simon-Willison-style portfolio artifact**: pick one HuggingFace 0.2–1B model, port it to the browser via ONNX + WASM/Pyodide using Claude Code, ship on your personal site by Sunday ([`03` §2](./03-practical-skills-and-tools.md#2-portfolio-port)). One artifact answers three interview questions: shipping, model deployment, and end-to-end ownership.

## Watchlist deltas

- 🔄 **CORRECTION → Trump AI executive order:** was tracked as "POSTPONED" in 2026-05-22 edition. **Actually signed and operative.** It is the legal basis for GPT-5.6 Sol's ~20-partner restriction AND Anthropic Mythos 5's ~100-org whitelist. Status flips 🟡-stalled → 🔴-active.
- 🆕 **Federal whitelisting as release paradigm:** new thread — track which startups appear on (or get cut from) the cleared lists; this is the "pre-deployment-eval" career lane materializing as enterprise procurement law.
- 🔻 **OpenAI IPO Sept 2026:** **reportedly slipping to 2027** [rumor, Reuters/Bloomberg Tech June 26]. OpenAI says "may be a while." Anthropic still tracking Oct 2026. If true, Anthropic beats OpenAI to public markets — material for equity-comp expectations at both.
- 🆕 **Inference economics as megaround category:** new thread — Baseten $1.5B/Series F at $13B + Jalapeño chip + Qualcomm-Modular $3.9B + CNBC "tokenmaxxing→efficiency" framing. The MLE/infra hiring signal of the cycle.
- 🆕 **AI-for-science talent war:** new thread — Jumper → Anthropic + Shazeer → OpenAI in the same 48 hours. Anthropic hosting science-focused event June 30 (RSVP if possible).
- 🆕 **Real-work benchmark wave (Jun 21–25 arXiv):** NatureBench / EnterpriseClawBench / RigorBench / CoffeeBench. Reframes evaluation from "can the agent use a tool" → "can the agent finish the job with engineering discipline."
- ➡️ **Karpathy → Anthropic (recursive Claude-trains-Claude team):** still live from 2026-05-22, no new shipping signal in this window.
- ➡️ **Anthropic Agent SDK metering (June 15):** in effect for 12 days; no fresh data, but Baseten's $13B Series F and Jalapeño underline why per-step cost-engineering became the skill of the year.

---

## How to read this edition

| Time budget | Path |
|---|---|
| 60 sec | This file. Done. |
| 5 min | This file + GPT-5.6 partner-gating + Mythos 5 clearance in [`01` §1–2](./01-big-lab-moves.md) |
| 20 min | [`04` §1](./04-research-progress.md#1-real-work-benchmarks) (real-work benchmarks) + [`02` §1–3](./02-new-emerging.md) (inference-economics week) — the two deepest signals |
| Today | [`05` §3](./05-career-and-startup.md#3-fde-apply) — FDE application this evening |
| Weekend | [`03` §2](./03-practical-skills-and-tools.md#2-portfolio-port) — ship the browser-port portfolio artifact |

Source-confidence legend: `[primary]` first-party · `[secondary]` reputable journalism · `[aggregator]` curated digest · `[analysis]` analyst writeup · `[rumor]` leaked / unconfirmed.
