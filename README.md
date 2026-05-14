# DAILY-AI-NEWS

A personal AI news intelligence system for a CS grad student pursuing startups and SDE/MLE/AI roles.

Every day gets its own folder. Every story has a source and a direct "why it matters to you" section.

---

## Folder Structure

```
YYYY-MM-DD/
├── 00-tldr.md                      # 60-second skim: 5–8 bullets + one action + watchlist deltas
├── 01-big-lab-moves.md             # OpenAI, Anthropic, Google, Meta, xAI, Apple — strategy, products, policy
├── 02-new-emerging.md              # New models, startups, tools, funding rounds, paradigm shifts
├── 03-practical-skills-and-tools.md # Hands-on workflows, tools, prompting, productivity — act on this TODAY
├── 04-research-progress.md         # arXiv papers, benchmarks, breakthroughs — what's moving the frontier
└── 05-career-and-startup.md        # Job market, VC trends, skills to build, startup playbook
```

Every entry has:
- **What happened** — the fact
- **Sources** — verified links, no secondhand summaries without attribution
- **Why it matters to you** — direct implication for startup or job hunt (three lenses: **Job · Startup · Insight**)
- **Tags** — `#anthropic #funding #voice #agents` etc., so you can `grep -r "#voice" .` across the archive

Cross-cutting docs at repo root:
- [`SOURCES.md`](./SOURCES.md) — master tiered source list (8 tiers, ~100 sources)
- [`WATCHLIST.md`](./WATCHLIST.md) — running threads that span multiple days, so nothing drops between editions

---

## Editions

| Date | Highlights |
|---|---|
| [2026-05-14](./2026-05-14/) | **Anthropic overtakes OpenAI in US business adoption for the first time** (Ramp AI Index: 34.4% vs 32.3%; Anthropic ~4×'d adoption in 12 months) · Anthropic raise talks now at up to ~$950B · US + China agree to launch a formal AI safety protocol at the Trump–Xi Beijing summit · Google's "Googlebook" confirmed — Aluminium OS, Gemini as the OS layer · Cisco +15% on $9B AI-infra order guidance while cutting ~4,000 jobs · Claude Code now ~4% of all public GitHub commits · OpenClaw hits 210K+ stars · Appier "Answer, Refuse, or Guess?" — LLMs miscalibrated on risk · Hint (Martha Stewart) $10M seed |
| [2026-05-13](./2026-05-13/) | **Anthropic "Claude for Legal" — 12 practice-area plugins + 20+ MCP connectors (DocuSign, Ironclad, iManage, NetDocuments, LexisNexis, Thomson Reuters, Box, Everlaw); TR CoCounsel Legal now rebuilt on Claude Agent SDK** · Google Threat Intel: first-ever AI-built zero-day caught in active mass-exploitation campaign (2FA bypass) · Meta Avocado/Mango delays + closed-source pivot confirmed at C-suite · Wispr Flow in talks at ~$2B ($260M Menlo Ventures lead) — "Voice OS" rebrand · Judgment Labs $32M Seed + Series A (Lightspeed ×2) for deep-agent eval · arXiv 2602.16666 Agent Reliability — 12 metrics, "reliability decoupling" thesis · Q1 2026 layoffs revised to 78,557 / 47.9% AI-attributed · Meta 8,000-person cut scheduled May 20 |
| [2026-05-12](./2026-05-12/) | **Google "Android Show: I/O Edition" — Aluminium OS desktop platform reveal (HP/Lenovo/Acer/ASUS/Samsung), Android 17 agentic features, Android XR glasses, system-level Gemini** · Anthropic $50B/$900B raise board decision expected this week · EU vs Mythos escalation: Spain Minister Cuerpo publicly cites AI Act Article 51 (Aug enforcement window) · Cognition (Devin) raising at $25B, 80× enterprise growth · xAI Speech-to-Text + TTS + Grok Imagine Quality Mode GA · On-Policy Distillation sweep (Thinking Machines Lab + survey + SDPO + OPSD) · `Constraint Decay` arXiv paper (May 7) — quantifiable failure mode in coding agents · CS new-grad Q1 data: 52,050 layoffs · MLE +41.8% YoY vs SWE -40% |
| [2026-05-11](./2026-05-11/) | **IBM CAIO study: 76% of orgs now have a Chief AI Officer** (up from 26% in 2025) · **Anthropic ARR crosses ~$44B** (May), full monthly progression disclosed · NVIDIA Nemotron 3 Nano Omni open-source (30B-A3B hybrid Mamba-Transformer, 9× throughput) · Apple iOS 27 multi-AI "Extensions" framework · Anthropic blocks Mythos from EU CAISI equivalent · Karpathy `autoresearch` (630 LOC) overnight ML experiments · Mythos 94.6% GPQA Diamond · Q1 2026 venture data ($300B, 80% AI) · Mollick's May 2026 model picks · Air Street State of AI: May 2026 |
| [2026-05-10](./2026-05-10/) | Anthropic targeting **$900B / $50B raise** · GPT-5.5 Instant becomes ChatGPT default (52.5% fewer hallucinations) · GPT-Realtime-2 / Translate / Whisper voice APIs · Sierra $950M at $15B · Moonshot AI $2B at $20B (Kimi K2.6 #2 on OpenRouter) · IBM Sovereign Core · Grok 4.3 on OCI · On-Policy Distillation sweep (Lightning OPD, SDPO) · Mem0 + EverMemOS memory architectures · Air Street State of AI: May 2026 · FDE role playbook · Outcome pricing as 2026 default |
| [2026-05-09](./2026-05-09/) | Anthropic rents **all of Colossus 1** from xAI/SpaceX (220K GPUs) · 80× quarterly growth · OpenAI **GPT-5.5-Cyber** for vetted defenders · Pentagon picks 8 AI vendors (Anthropic excluded) · Code w/ Claude conf — Managed Agents "Dreaming" + finance templates · Sierra **$15.8B** Series E · Moonshot AI **$20B** valuation · Cloudflare cuts **1,100 jobs** at record revenue · EU AI Act delayed to 2027/2028 · Karpathy: vibe coding → agentic engineering · Single-agent beats multi-agent under matched compute (Stanford) |
| [2026-05-08](./2026-05-08/) | Anthropic-Google **$200B compute deal** (1M TPUs) · Anthropic Wall Street + Jamie Dimon · DeepSeek V4 (MIT license, runs on Huawei Ascend) · Pit $16M a16z launch · Parallel Web Systems $2B · GPT-5.5 Codex browser agent · Mem0 graph memory · 2026 resume formula · Wedge of 2026 = "AI product team as a service" |
| [2026-05-07](./2026-05-07/) | **Apple iOS 27 multi-AI Extensions framework** (Gemini + Claude + GPT picker) · Anthropic **$1.5B PE deployment JV** (Blackstone, Goldman, Apollo, H&F, General Atlantic) · OpenAI mirror enterprise JV · Apple **$250M AI marketing settlement** · CAISI pre-deployment review signs MS/Google/xAI · Gemini 3.1 Flash-Lite GA at $0.25/M input (1432 Arena Elo) · Anthropic **"Dreaming"** agent technique · Single-agent vs multi-agent (Stanford recap) |
| [2026-05-06](./2026-05-06/) | Anthropic Claude Mythos (cybersecurity model restricted at launch) · OpenAI $25B ARR + IPO · Google "Remy" personal agent · Cursor 3.0 Agents Window · Vibe coding security risks · CS job market reality check · Vertical agent startup formula |

---

## Master Source List

See [`SOURCES.md`](./SOURCES.md) — organized by type with notes on reliability and signal quality.

---

## Reading Strategy

| Time budget | What to read |
|---|---|
| **60 seconds** | Today's `00-tldr.md` |
| **5 minutes** | `00-tldr.md` + bold headlines of one category file |
| **20 minutes (recommended)** | One full category file, deep — rotate through the 5 across the week |
| **Weekend** | Pick one item from `03-practical-skills-and-tools.md` and **actually do it**. Re-read `WATCHLIST.md` and update personal threads. |

## Tagging Convention

Every entry tags with `#topic`. Search the archive across days:

```bash
grep -rn "#anthropic" .          # all Anthropic stories
grep -rn "#voice" .              # voice-AI thread across days
grep -rn "#funding" .            # every funding round noted
```

Common tags: `#labs #anthropic #openai #google #apple #nvidia #funding #vc #seed #agents #voice #multimodal #open-source #research #policy #eu #jobs #fde #startups #playbook #pricing #benchmarks #memory`
