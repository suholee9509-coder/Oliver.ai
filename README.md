# Oliver

> **Keeping humans thinking in the age of AI.**
> Open-source UI building blocks from Oliver — an interaction layer that answers first, then hands the thinking back to you.

This repository is the open-source part of **Oliver**, a project exploring AI that *strengthens* human thinking instead of replacing it. The full product keeps its core decision engine private, but the interaction pieces that other developers can reuse are open here.

---

## Why Oliver exists

When you ask an AI something, it produces a plausible answer **even when your intent is incomplete**. So you skip the step of clarifying what you actually want — the AI fills that gap silently. Over time, you stop doing the thinking that getting an answer used to require.

Oliver calls this **the outsourcing of intent**. Its bet: don't withhold the answer (people just leave) — give the answer, then make the user's intent visible and reusable, so the thinking comes back to the person.

This repo open-sources two pieces that carry that idea, in a form any AI app can adopt.

---

## What's in this repo

### 1. Intent Note
A lightweight note where the user captures their **own intent** — what they're really trying to do — and the AI **references it** when answering. Instead of re-explaining context every turn, your intent lives in a note the model reads from. It turns "thinking out loud once" into persistent context that keeps your answers aligned with what *you* meant, not what the model guessed.

- Capture intent as short, editable notes
- Notes are passed as context the model references on each turn
- The thinking you do stays with you instead of scrolling away

### 2. Intent Toggle (UI)
A collapsible toggle that sits under an AI answer and surfaces the **choices and assumptions** that answer was built on — so you can catch where the model guessed your intent wrong.

- Renders only when there's something worth surfacing (a settled fact gets no toggle)
- Calm, companion-style copy — reveals, doesn't lecture
- Drop-in React component; bring your own extraction source

> **Note:** This repo ships the interaction layer (the Intent Note and the Toggle UI). Oliver's core decision engine — when to ask back, how intent is scored and extracted — stays in the private product.

---

## Tech

- React components
- Model-agnostic: works with any chat completion API (OpenAI / Anthropic / others)

## Roadmap

- Adapters for popular chat UIs
- Shared intent notes across a session
- Hooks for wiring the Toggle to your own intent-extraction backend

---

## About

Oliver is built and maintained by a solo developer working in an AI-native workflow — designing, speccing, and shipping with AI agents end to end. It grows out of a simple conviction:

> What makes us human is the ability to think for ourselves. AI offers to do that for us. Oliver is built to protect it.

