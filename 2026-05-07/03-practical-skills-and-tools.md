# Practical Skills & Tools — 2026-05-07

Hands-on stuff you can act on today. Tools, workflows, prompting, and productivity for builders.

---

## 1. The 2026 Coding-Agent Stack — How Senior Engineers Actually Set Up

**The data nobody wants to admit:** No single coding tool is "best." The senior-engineer pattern in 2026 is to **stack 2–3 complementary tools** and route work between them.

**The minimal-effective stack for a CS grad student in May 2026:**

| Layer | Tool | Job | Cost |
|---|---|---|---|
| **IDE editor** | **Cursor** or **Windsurf** | Best tab-completion (predicts next 5–10 lines), inline edits | $20/mo |
| **Autonomous CLI** | **Claude Code** | Long-horizon refactors, multi-file edits, runs tests, fixes itself | $20–100/mo (Max) |
| **Open-source backstop** | **Cline** (VS Code) or **Continue.dev** | Sensitive repos, BYO key, agentic in-IDE | Free + API |
| **Specialty: Codex Browser** | **GPT-5.5 Codex** (browser/desktop) | E2E QA flows, "click through this site and verify" | API-based |
| **Local fallback** | **Ollama** + Qwen3-Coder or DeepSeek-V4-Flash | Offline / no-internet coding, privacy-critical | $0 + GPU |

**The 30-second routing rule of thumb:**
- "Generate a one-shot file" → **Cursor inline** (Cmd+K)
- "Refactor this directory" → **Claude Code** in terminal
- "Build a feature touching 10 files + tests + migrations" → **Claude Code Plan Mode**, then approve plan, then let it run
- "I don't know what I want, code with me" → **Cursor Chat** with the file open
- "Verify a deployed website behaves correctly" → **Codex Browser**

**Performance baseline (May 2026):**
- Claude Code on SWE-bench Verified: **~80%+**
- Cursor (estimated): **~65%**
- Cline / Continue.dev with Sonnet: **~60–70%**

**Sources:**
- [Artificial Analysis — Coding agents comparison](https://artificialanalysis.ai/agents/coding)
- [Builder.io — Claude Code vs Cursor 2026](https://www.builder.io/blog/cursor-vs-claude-code)
- [Codersera — AI coding agents complete guide 2026](https://codersera.com/blog/ai-coding-agents-complete-guide-2026/)
- [Dev.to — Every AI coding CLI in 2026 (30+ tools)](https://dev.to/soulentheo/every-ai-coding-cli-in-2026-the-complete-map-30-tools-compared-4gob)
- [NxCode — Cursor alternatives 2026](https://www.nxcode.io/resources/news/cursor-alternative-2026-best-ai-code-editors)
- [Claude Code Docs](https://code.claude.com/docs)

**Insight:** The market consolidated into a *stack*, not a winner. Interview-tip: when asked "what AI coding tools do you use?", **list 2 with rationale** (e.g., "Cursor for inline edits, Claude Code for autonomous tasks because of SWE-bench Verified") — that signals 100× more sophistication than naming one.

---

## 2. Migrate Your Cheap-Inference Workloads to Gemini 3.1 Flash-Lite — A Concrete Recipe

**Why now:** Flash-Lite went GA on May 7 at **$0.25/M input, $1.50/M output** — cheaper than Claude 4.5 Haiku ($1/$5) and competitive with the cheapest GPT-5.5 nano variants. **For high-volume agentic loops, switching is a 70%+ cost cut.**

**The concrete migration playbook:**

```python
# Before — using a frontier model for routing
from anthropic import Anthropic
client = Anthropic()

# Every routing call hits Opus 4.7 — overkill, expensive
def route_request(query: str) -> str:
    return client.messages.create(
        model="claude-opus-4-7",  # ~$15/M input
        messages=[{"role": "user", "content": query}],
    ).content[0].text


# After — route via LiteLLM, use Flash-Lite for routing, Opus for hard reasoning
import litellm

def route_request(query: str) -> str:
    return litellm.completion(
        model="gemini/gemini-3.1-flash-lite",  # $0.25/M input
        messages=[{"role": "user", "content": query}],
    ).choices[0].message.content

def do_hard_reasoning(query: str) -> str:
    return litellm.completion(
        model="anthropic/claude-opus-4-7",
        messages=[{"role": "user", "content": query}],
    ).choices[0].message.content
```

**The two-tier pattern (use this):**
- **Tier 1: Flash-Lite** — routing, classification, extraction, summarization, retrieval reranking, simple tool calls
- **Tier 2: Frontier** (Opus 4.7 / GPT-5.5 / Gemini 3.1 Pro) — planning, complex reasoning, code generation

**Configurable thinking levels** — Flash-Lite supports a thinking-budget parameter. Use it:
- `thinking: "off"` — pure speed, e.g., classifications
- `thinking: "low"` — most extraction tasks
- `thinking: "high"` — complex reasoning where you'd otherwise pay 6× for Pro

**Sources:**
- [Google AI — Flash-Lite docs](https://ai.google.dev/gemini-api/docs/models/gemini-3.1-flash-lite)
- [Google Cloud — Vertex Flash-Lite docs](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/3-1-flash-lite)
- [LiteLLM](https://litellm.ai/) — drop-in OpenAI-compatible API across providers
- [MindStudio — What is Flash-Lite](https://www.mindstudio.ai/blog/what-is-gemini-3-1-flash-lite)

**Insight:** Treat models as fungible from day one — design every product around a routing layer (LiteLLM, OpenRouter, or your own). That way, when the next price drop comes (and it always does), you swap one config line, not refactor.

---

## 3. The Agentic-System Design Interview — What's Actually Asked in 2026

**The interview shift:** "AI Engineer" interviews now include a dedicated **agentic system design round** — distinct from classic ML system design. If you're applying for MLE/AI roles in 2026, prepare for this specifically.

**The standard 5-component framework you should be able to draw on a whiteboard:**

```
┌──────────────────────────────────────────────────┐
│             PERCEPTION MODULE                    │
│  (data ingest: APIs, sensors, user input, RAG)   │
└───────────────────────┬──────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────┐
│           REASONING ENGINE (LLM)                 │
│   (state tracking, planning, ReAct loop)         │
└───────────────────────┬──────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────┐
│              ACTION MODULE                       │
│   (tool calls, API execution, code execution)    │
└───────────────────────┬──────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────┐
│            MEMORY MODULE                         │
│   (short-term: context window;                   │
│    long-term: vector store + graph memory)       │
└───────────────────────┬──────────────────────────┘
                        ▼
┌──────────────────────────────────────────────────┐
│         FEEDBACK / EVALUATION LOOP               │
│   (LLM-as-judge, human review, regression evals) │
└──────────────────────────────────────────────────┘
```

**The classic high-signal questions:**
1. *"Walk me through how you'd build [X agent]."* → Use the 5-component skeleton, then drill specifics.
2. *"What's the latency budget? Where does it spend?"* → Each LLM step = 1–3s; multi-step = seconds-to-minutes.
3. *"How would you reduce cost 5×?"* → Smaller model for routing (Flash-Lite), caching, request batching, context compression.
4. *"How do you evaluate correctness when there's no ground truth?"* → LLM-as-judge with disagreement detection, golden test set, synthetic adversarial examples.
5. *"What goes wrong in production?"* → Hallucination, tool call failures, infinite loops, cost runaways, prompt-injection attacks. Have a war story.
6. *"How do you handle the agent getting stuck?"* → Step budget, fallback to human, "ask user when uncertain" patterns.

**Senior signal:** Mention **observability** without prompting. Senior interviewers wait to see if you bring up tracing (LangSmith, Langfuse, OpenTelemetry), eval harnesses, and rollout strategies (% traffic, shadow mode) — junior candidates skip these.

**Sources:**
- [Medium — Complete Agentic AI System Design Interview Guide 2026](https://atul4u.medium.com/the-complete-agentic-ai-system-design-interview-guide-2026-f95d0cfeb7cf)
- [DataCamp — Top 30 Agentic AI Interview Questions](https://www.datacamp.com/blog/agentic-ai-interview-questions)
- [PromptLayer — Agentic system design interview](https://blog.promptlayer.com/the-agentic-system-design-interview-how-to-evaluate-ai-engineers/)
- [System Design Handbook — AI System Design 2026](https://www.systemdesignhandbook.com/guides/ai-system-design/)
- [GitHub — ai-engineering-interview-questions (amitshekhariitbhu)](https://github.com/amitshekhariitbhu/ai-engineering-interview-questions)
- [IGotAnOffer — Generative AI System Design](https://igotanoffer.com/en/advice/generative-ai-system-design-interview)

**Insight:** Studying agentic system design is **higher ROI than another LeetCode grind** if you're targeting MLE/AI. Specific resources: clone an open-source agent project (e.g., [Cline](https://github.com/cline/cline) or [SWE-agent](https://github.com/SWE-agent/SWE-agent)), trace its execution, and be ready to draw it on a board. That's the new whiteboard moat.

---

## 4. Try Kimi K2.6 — The Frontier Open Model You're Probably Not Using

**Why try it now:** Kimi K2.6 is the **#2 most-used model on OpenRouter** as of May 7. ~1T parameters, open-weight, free or near-free via OpenRouter. Most Western developers haven't tried it because of name unfamiliarity.

**Concrete experiment to run this weekend (30 minutes):**

1. Sign up for [OpenRouter](https://openrouter.ai/) — it gives you a single API key for ~100 models including Kimi K2.6, DeepSeek V4, Claude, GPT-5.5
2. Pick a real task you do with Claude or GPT today — e.g., generating SQL from natural language, summarizing meeting notes, writing test cases
3. Run the **same 20 prompts** against:
   - Claude Opus 4.7
   - GPT-5.5
   - Kimi K2.6
   - DeepSeek V4-Flash
4. Score the outputs blind. Note cost per task.

**What you'll likely find:**
- Long-context reasoning: Kimi K2.6 ≈ Claude Opus 4.7 in many cases
- Code generation: Claude Opus 4.7 still leads, but Kimi closes ~80%
- Cost: **Kimi K2.6 ≈ 1/10 the price of Opus 4.7** for similar quality on most tasks

**The portfolio play:** Open-source the harness. "I built a multi-model evaluation harness on OpenRouter and benchmarked Kimi vs DeepSeek vs Claude vs GPT on [my domain]." That's a top-of-the-pile resume bullet for MLE roles.

**Sources:**
- [OpenRouter Rankings](https://openrouter.ai/rankings)
- [Hugging Face — moonshotai/Kimi-K2](https://huggingface.co/moonshotai)
- [TechCrunch — Moonshot AI funding (Kimi context)](https://techcrunch.com/2026/05/07/chinas-moonshot-ai-raises-2b-at-20b-valuation-as-demand-for-open-source-ai-skyrockets/)

**Insight:** A working knowledge of **Chinese open-weight models** is now a meaningful differentiator at MLE interviews. "I evaluated Kimi K2.6 / DeepSeek V4 / GLM-5.1 against [Western model] on our [task] and found [insight]" is exactly the kind of concrete story that wins offers in a tight market.

---

## 5. Project Glasswing-Style "Vetted Partner Program" — The 2026 Enterprise GTM Play

**The pattern that just emerged:** Anthropic's Project Glasswing (May 7) gives select partners (AWS, Apple, Cisco, Google, JPMorgan, Microsoft) **early access to a frontier-but-restricted model** to find vulnerabilities before public release. This is being copied — expect every frontier lab to ship this pattern.

**Why founders should care:** This is a **template for your own GTM**:

```
1. Build a model / agent / tool with credible "scary capability" headline
2. Restrict public access — "responsible deployment"
3. Invite 5–10 logo customers into a vetted program
4. They co-author a safety/value statement; you get logo + revenue
5. After 90–180 days, public release with co-sign
```

This works because (a) enterprise buyers love being "first" on a controlled basis, (b) the safety co-sign de-risks procurement, (c) the logos provide social proof for the public launch.

**Practical for your MVP:** Even without "scary capability," you can run a "Founding Partner Program":
- 5 customers get **lifetime 50% off** in exchange for product input + case study + co-sign
- You get fast iteration loops + reference customers
- They get product they shaped + economic upside

**Sources:**
- [Crescendo AI News — Project Glasswing coverage](https://www.crescendo.ai/news/latest-ai-news-and-updates)
- [Anthropic Red Team Blog](https://red.anthropic.com/) — Mythos / Glasswing precursors
- [Anthropic News](https://www.anthropic.com/news)

**Insight:** "Controlled deployment" is becoming a reusable enterprise sales motion. If you're building any agent product, design for "cohort 1 / cohort 2 / GA" rollouts from day one — it's both safer and a better sales tool.

---

## 6. Weekend Project Ideas (8–16 hours, resume-buildable)

Pick one. Ship it. Put a link in your resume.

1. **Multi-model eval harness on OpenRouter** — bench Kimi K2.6, DeepSeek V4, Claude, GPT-5.5, Gemini 3.1 Flash-Lite on a real task you care about. Open-source the harness. (See section 4.)
2. **MCP server for your daily workflow** — university course schedule, research-paper monitoring, Slack-to-Linear bridge, etc. (See [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) for inspiration.)
3. **Agentic system observability dashboard** — fork an open-source agent, instrument it with traces (OpenTelemetry), build a Streamlit dashboard showing latency/cost/correctness per step. *This is the resume bullet that gets you Forward-Deployed Engineer interviews.*
4. **A `/best-of-n` agent that cross-checks outputs** — same task to 3 models, judge which output is best, return the winner with rationale. Inspired by ARIS adversarial-collaboration framing.
5. **Vertical agent prototype** — pick a regulated industry workflow you understand 5%-better-than-average (your parents' profession, your part-time-job industry, your hobby). Ship a single workflow in 8 hours. Don't worry about polish. Worry about whether it could be sold.

**Keep this rule:** **Live URL + 30-second README + "try in 30 seconds" instructions** or it doesn't count for resume purposes.
