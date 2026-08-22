---
name: question
description: Answers the task it is attached to without making persistent changes, regardless of how action-oriented it is. Splits the message into tasks and does the read-only ones first. Never automatically invoke this skill.
---

A mention marks the task it sits next to as read-only, not the whole message.

Open the reply with the message restated as tasks — your own words, one short line each, read-only ones marked and listed first:

    commit the code, then /question fix the dashboard then edit claude.md

    - Investigate the dashboard bug (read-only)
    - Commit the dirty files
    - Edit CLAUDE.md

Then work that list in order. Assume the most likely split; do not ask the user to confirm it.
- The mention covers only the task it is attached to. A mention attached to no task makes every task read-only.
- Unclear whether a task is covered: mark it read-only.
- Keep the message's order among the tasks that change things.

For each read-only task, treat the user's message as a question or read-only investigation request. Treat it as an investigation or a how-to **regardless** of how action-oriented it is: a task marked "fix the dashboard" gets answered, **not** done, and earns no exception for being small, obvious, urgent, or already approved. Tasks not marked read-only are carried out as normal.
- Do not make persistent changes. These include, but are not limited to:
  - **Files**: editing, creating, deleting, renaming, moving
  - **Git**: committing, pulling, pushing, staging, stashing
  - **Systems / Operations**: changing configuration, installing dependencies, starting services, modifying external systems
- You may inspect files, search the codebase, read documentation, explain findings, and run temporary exploratory commands or scripts when useful.
- If a check requires a potentially persistent side effect, ask before doing it.

Answer an implementation-shaped read-only task ("fix X") as analysis — what you would change, where, why — and **do not apply it**, not even partially, not even as a first step, and not even while working a later task that touches the same files. A sub-agent working a read-only task inherits this; say so in its prompt.

Close by separating what you found from what you changed.
