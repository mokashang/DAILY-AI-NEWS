# Practical Skills & Tools — 2026-05-07

Hands-on workflows, tools, prompting, productivity. Act on this TODAY.

Tags: `#tools #workflows #voice #ios #prompting`

---

## ⭐ One Thing to DO This Week

**Build a 3-provider router using LiteLLM + OpenRouter on a real task you care about.**

- Pick a task you actually do (e.g., summarizing arxiv abstracts, generating SQL from natural language, writing code review comments)
- Run **GPT-5.5, Claude Opus 4.7, and Gemini 3.1 Pro** on 20 examples of that task
- Score each output yourself (or with a 4th model as judge)
- Push the project to GitHub with a results table

Why: it's the cheapest, highest-signal portfolio item you can produce this month. It demonstrates: multi-provider thinking, eval design, cost awareness, taste, and shipping.

---

## 1. Workflow: Real-time Voice Agent in a Weekend

With OpenAI's GPT-Realtime-2 + Translate + Whisper-2 released this week, you can build a real-time voice agent (interpreter, customer support, voice-controlled tool) in a single weekend. Skeleton:

```python
# requirements: pip install openai
from openai import OpenAI
import asyncio

client = OpenAI()

async def voice_agent():
    async with client.beta.realtime.connect(model="gpt-realtime-2") as conn:
        await conn.session.update(session={
            "instructions": "You are a real-time meeting interpreter. Translate the user's speech.",
            "modalities": ["text", "audio"],
            "input_audio_format": "pcm16",
            "output_audio_format": "pcm16",
            "voice": "alloy",
        })
        # Stream mic → conn.input_audio
        # Stream conn.output_audio → speakers
        # (Full stream loop omitted for brevity — see OpenAI Cookbook)

asyncio.run(voice_agent())
```

For translation specifically, swap `model="gpt-realtime-translate"` and pass source / target language. Pricing: **$0.034/min** for translate, $0.017/min for Whisper-2. A 5-hour meeting costs $10 to interpret end-to-end.

**Sources:**
- [OpenAI Cookbook — Realtime API patterns](https://github.com/openai/openai-cookbook)
- [Latent Space — GPT-Realtime-2 review](https://www.latent.space/p/ainews-gpt-realtime-2-translate-and)
- [OpenAI — Realtime models in API](https://openai.com/index/advancing-voice-intelligence-with-new-models-in-the-api/)

**Why it matters to you:**
- **Job lens:** Real-time voice + LLM streaming is a *thin labor market*. If you ship a working voice demo (push the video to X), the volume of inbound DMs from voice-AI startups will surprise you. Try Vapi, Hume, Sesame, ElevenLabs, Pickle as targets.
- **Startup lens:** Vertical voice agents are now buildable for under $5K in API costs to prove value. Pick one hostile workflow (insurance claims call, medical triage call, multilingual support) and prototype an agent that handles 80% of it. Outcome-priced contracts follow.

---

## 2. Practitioner Tip: Stress-Test Models Before Committing to One

Use this minimal eval harness to compare providers on your own data:

```python
from litellm import completion
from concurrent.futures import ThreadPoolExecutor
import json

MODELS = ["openai/gpt-5.5", "anthropic/claude-opus-4-7", "gemini/gemini-3.1-pro"]
TASKS = json.load(open("my_eval_set.json"))  # list of {prompt, expected}

def run(model, task):
    out = completion(model=model, messages=[{"role":"user","content":task["prompt"]}])
    return {
        "model": model,
        "task": task["id"],
        "output": out.choices[0].message.content,
        "expected": task["expected"],
    }

with ThreadPoolExecutor(8) as ex:
    futures = [ex.submit(run, m, t) for m in MODELS for t in TASKS]
    results = [f.result() for f in futures]

# Then run a 4th model as a judge, or grade yourself
```

This is *the* habit that separates AI builders from AI tinkerers. Get the eval discipline in your hands now.

---

## 3. Tool Stack — May 7 Edition

| Layer | Tool | Why |
|---|---|---|
| **Routing** | [LiteLLM](https://docs.litellm.ai/) | Multi-provider in one SDK |
| **Inference** | [OpenRouter](https://openrouter.ai/) · [Together AI](https://together.ai/) · [Fireworks](https://fireworks.ai/) | Cheap unified endpoints |
| **Voice** | OpenAI Realtime · Gemini TTS · [Vapi](https://vapi.ai/) | Real-time pipelines |
| **Observability** | [LangFuse](https://langfuse.com/) · [LangSmith](https://www.langchain.com/langsmith) | Traces and evals |
| **Agent runtime** | [Claude Code](https://www.anthropic.com/claude-code) · [OpenAI Codex](https://openai.com/codex/) | File-system + tool-use loops |
| **Browser agent** | [Parallel Web](https://parallel.ai/) · [Browser Use](https://browser-use.com/) | Programmable browser control |
| **Eval harness** | [Promptfoo](https://promptfoo.dev/) · [Inspect](https://inspect.ai-safety-institute.org.uk/) | Quick eval scripts |
