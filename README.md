# Oliver

> **Keeping humans thinking in the age of AI.**
> An interaction layer that answers first — then hands the thinking back to you.

Oliver is an open-source experiment in building AI that *strengthens* human thinking instead of replacing it. Most AI tools compete on giving faster answers. Oliver takes the opposite bet: it gives you the answer, then surfaces the intent and assumptions that answer was built on — so you stay the one who decides what you actually meant.

---

## The Problem

When you ask an AI something, it produces a plausible answer **even when your intent is incomplete**. So you skip the step of clarifying what you actually want — the AI fills that gap for you, silently. Over time, you stop doing the thinking that used to be required just to get an answer.

This is **the outsourcing of intent** — and it's measurable. It's not that AI gives bad answers. It's that smooth answers let us hand over the part of thinking where understanding is actually built.

## The Bet

Oliver doesn't withhold answers to force you to think (people just leave). Instead, it adds a thin layer **on top of** the answer:

- **Answer first.** Oliver never holds the answer hostage.
- **Ask only when it matters.** A judge evaluates whether the answer was genuinely weakened by missing intent. Silence is the default — it speaks only when a real gap would change the result.
- **Show the intent behind the answer.** Oliver reveals the choices and assumptions it made to fill your unstated intent, so you can catch where it guessed wrong.
- **Steer, don't restart.** You comment on any piece of the surfaced intent and send all your corrections back at once.

The goal: you come for a sharper answer; sharper thinking comes as a byproduct.

---

## What's Implemented

This repository contains a working prototype of Oliver's core interaction loop:

- **Trigger pipeline (3-gate)** — decides *when* to ask back, with silence as the default:
  1. **Code gate** — cheaply blocks obvious cases (user asked for a quick answer; we just asked last turn).
  2. **Judge (LLM)** — scores whether the answer was weakened by missing user intent (0–1).
  3. **Threshold gate** — a single tunable knob controls how often Oliver speaks.
- **Intent Toggle** — after answering, Oliver shows the choices / assumptions / counterfactuals behind that answer. Shown *only when there's something worth surfacing* (a settled fact gets no toggle).
- **Intent Steering** — each surfaced intent becomes a block you can comment on; comments stack as badges and are sent back as one combined re-request.
- **Live reasoning (CoT)** — while generating, Oliver shows the *actual* pipeline step it's running, not a fake "thinking…" label.
- **Knowledge graph** — the intent, concepts, and decisions surfaced across a conversation are structured into a connected graph, so the thinking you do with Oliver accumulates instead of scrolling away.

## Tech

- React (prototype UI)
- Anthropic / OpenAI chat completion API for the answer, judge, and intent-extraction calls (up to 3 LLM calls per turn, run in parallel)

## Roadmap

- **Clarify mode** — opt-in upfront questions before the first answer (the one case where asking-before-answering is by user choice).
- **Intent profile** — persistent user context so Oliver stops re-asking what it already knows.
- **Production hardening** — structured outputs instead of prompt-enforced JSON, lighter models for the judge, and a trigger-data loop that learns *which interventions actually provoke thinking*.

---

## About

Oliver is built and maintained by a solo developer working in an AI-native workflow — designing, speccing, and shipping with AI agents end to end. It grows out of a simple conviction:

> What makes us human is the ability to think for ourselves. AI offers to do that for us. Oliver is built to protect it.

## License

MIT
