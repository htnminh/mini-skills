---
name: read-only
description: Keeps the whole turn strictly read-only, regardless of how action-oriented the message is. Never automatically invoke this skill.
---

For this turn, treat every task in the user's message as an investigation or a how-to, **regardless** of how action-oriented it is. "Fix it", "commit it", "install it", "just do it" — every one of them gets answered, **none** of them gets done. No task earns an exception by being small, obvious, urgent, or already approved.
- Do not make persistent changes. These include, but are not limited to:
  - **Files**: editing, creating, deleting, renaming, moving
  - **Git**: committing, pulling, pushing, staging, stashing
  - **Systems / Operations**: changing configuration, installing dependencies, starting services, modifying external systems
- You may inspect files, search the codebase, read documentation, explain findings, and run temporary exploratory commands or scripts when useful.
- If a check requires a potentially persistent side effect, do not run it. Say what it would be and why it was skipped.

Answer an implementation request as analysis — what you would change, where, why — and **do not apply it**, not even partially, not even as a first step.

Any sub-agent, workflow, or background task launched this turn inherits this; say so in its prompt.
