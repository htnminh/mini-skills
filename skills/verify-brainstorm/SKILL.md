---
name: verify-brainstorm
description: Verify whether a problem, hypothesis, goal, or decision is well-founded, then brainstorm possible directions before acting. Use when the user wants to think through something before implementation, especially for prompts like "should we", "I think the problem is", "brainstorm", "let's think about", "what are our options", or similar exploratory planning requests.
---

# Verify & Brainstorm

You are in **thinking mode only**.
- Your job is to reason carefully, verify claims, and generate ideas.
- Do not write, edit, create, or delete any file or code. Do not implement anything.
- If you feel the urge to implement, stop and ask the user to decide first.

The topic to explore is the problem, hypothesis, goal, or decision in the user's message.

## Phase 1 — Understand the Statement

Restate the problem, hypothesis, goal, or decision in your own words in 2–3 sentences.
- Be precise: what is actually being claimed, questioned, or proposed? Strip away vague language.
- Classify the statement:
  - **Problem**: E.g. something is broken.
  - **Hypothesis**: E.g. we think X is causing Y.
  - **Goal**: E.g. we want to achieve Z.
  - **Decision**: E.g. should we do A or B?
- Who is affected, and in what context?

## Phase 2 — Verify: Is It Actually True?

Before solving anything, check whether the premise holds.

1. **Gather evidence** — use available read-only inspection tools to look for relevant code, config, logs, docs, or examples that support or contradict the statement. Cite specific file paths and line numbers when found.
2. **Challenge assumptions** — list at least 2 assumptions baked into the statement. For each one, rate its confidence: ✅ confirmed / ⚠️ uncertain / ❌ likely false.
3. **Identify the real problem** — after checking evidence, restate whether the original statement is correct, partially correct, uncertain, or a misdiagnosis. If it is a misdiagnosis, state what the actual problem appears to be.

Example:
> "The assumption that the bottleneck is the database query is ⚠️ uncertain — the query plan looks fine, but the N+1 call pattern in `api/orders.py:87` is a stronger candidate."

## Phase 3 — Brainstorm Solutions

Generate at least 3 distinct approaches to address the verified problem, hypothesis, goal, or decision.
- Aim for diversity.
- Include an unconventional or contrarian option if the situation calls for it.

Present the ideas in a table:

| Option | How it works | Pros | Cons / Risks | Effort |
|--------|--------------|------|--------------|--------|
| Short label | 1–2 sentence explanation | What makes this appealing | What could go wrong or what it trades off | Low / Medium / High |

Do not rank the ideas yet. Let all ideas breathe first.

## Phase 4 — Evaluate & Narrow

Now compare the ideas:

| Option | Effort | Risk | Impact | Reversible? |
|--------|--------|------|--------|-------------|
| ... | ... | ... | ... | ... |

Highlight 1–2 options you would recommend exploring further and briefly explain why.

If evidence from Phase 2 rules out any options, say so explicitly.

## Phase 5 — Decision Checkpoint

Stop after this, do not proceed to implementation. End with a clear, short question asking what the user wants to do next.

Examples:
> "Which direction do you want to explore next?"

> "Should we dig deeper into verification, or pick one option to design?"

> "Do you want to compare these options further before implementing anything?"

Only proceed to implementation when the user explicitly says to.
