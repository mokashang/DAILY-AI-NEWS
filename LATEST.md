# LATEST — pointer to the most recent edition

> **2026-06-27** — see [`2026-06-27/00-tldr.md`](./2026-06-27/00-tldr.md)

This file is auto-updated every edition so a one-click read of the latest TL;DR is always at the repo root.

---

## Today's headline

**Friday — the week the federal whitelist became the product.** **OpenAI ships GPT-5.6 Sol/Terra/Luna** — Sol limited to **~20 US-government-pre-cleared partners** under the (operative) Trump AI executive order; new "ultra mode" parallelizes work via subagents. Same day, **Anthropic Mythos 5 is re-authorized for ~100 cleared US institutions** after 14 days dark (Fable 5 still offline). Underneath the gating news: **OpenAI + Broadcom unveil "Jalapeño"** (OpenAI's first custom inference ASIC, 9-month design-to-tape-out, claims ~50% Nvidia cost reduction), **Qualcomm closes $3.9B Modular acquisition** (Mojo + MAX), **Baseten raises $1.5B Series F at $13B**. **John Jumper (AlphaFold, 2024 Nobel) → Anthropic** for AI-for-science (two days after **Shazeer → OpenAI**); Anthropic hosting science event **June 30 SF**. Research wave: **NatureBench / EnterpriseClawBench / RigorBench / CoffeeBench** all in 5 days = eval bar moves from real-tool to **real-work + engineering discipline**. **OpenAI IPO reportedly slipping to 2027** [rumor]; **Anthropic still Oct 2026** = Anthropic would beat OpenAI to public markets. For you (Anthropic-stack, AI-Integration-Engineer lane): **RSVP the Anthropic June 30 SF science event** + **apply to 1 FDE req tonight** (Google/Salesforce/Anthropic/OpenAI/Palantir all live) + **ship the browser-port OR inference-benchmark portfolio artifact this weekend**.

Full edition → [`2026-06-27/`](./2026-06-27/)

---

## One-thing-to-do (Friday)

→ **Apply to ONE FDE req tonight** — Google Cloud "Forward Deployed Engineer II, Generative AI" (job ID 96964929679958726), Salesforce FDE (SF + Seattle live), Anthropic Solutions, OpenAI Forward Deployed, Palantir FDE. Comp range $200–300K base, $500K–$1M+ TC at senior. Pair the application with a **3-hour portfolio artifact** — pick one HF 0.2–1B model, port to browser via ONNX + WASM/Pyodide using Claude Code; ship to your site by Sunday. Recipe in [`2026-06-27/03 §2`](./2026-06-27/03-practical-skills-and-tools.md#2-portfolio-port).

→ **RSVP Anthropic's June 30 SF science event** if you have ML + bio/chem/physics — Jumper-led AI-for-science is the highest-leverage door of the quarter ([`2026-06-27/05 §1`](./2026-06-27/05-career-and-startup.md#1-jumper-signal)).

→ **Upgrade Claude Code to ≥ v2.1.185** for `claude mcp login` + cross-repo subagents GA + `/usage` per-agent cost attribution — the act-tonight stack ([`2026-06-27/03 §1`](./2026-06-27/03-practical-skills-and-tools.md#1-claude-code-week26)). Screenshot `/usage` output after one orchestration run — that's your interview answer to "how do you control AI costs at scale."

→ **Read [`2026-06-27/04 §1`](./2026-06-27/04-research-progress.md#1-real-work-benchmarks)** — the four-paper "real-work benchmarks" cluster (NatureBench / EnterpriseClawBench / RigorBench / CoffeeBench). NatureBench will be cited in every AI-for-science interview this fall; RigorBench reframes coding-agent evaluation from capability → discipline. Talking-point ammunition for both startup pitches and job interviews.

→ **CORRECTION logged in [WATCHLIST.md](./WATCHLIST.md):** the 2026-05-22 entry tracked the Trump AI EO as "POSTPONED" — it was actually signed (2026-06-02 confirmed). The June-26 Mythos 5 clearance + GPT-5.6 Sol gating are the *operational* consequences. Update mental model accordingly.
