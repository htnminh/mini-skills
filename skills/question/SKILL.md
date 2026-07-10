---
name: question
description: Answer this turn without making persistent changes. Use this for read-only investigation, explanation, debugging analysis, clarification, and exploratory checks where the user wants an answer but not implementation.
---

For this turn, treat the user's message as a question or read-only investigation request.
- Do not make persistent changes. These include, but are not limited to:
  - **Files**: editing, creating, deleting, renaming, moving
  - **Git**: committing, pulling, pushing, staging, stashing
  - **Systems / Operations**: changing configuration, installing dependencies, starting services, modifying external systems
- You may inspect files, search the codebase, read documentation, explain findings, and run temporary exploratory commands or scripts when useful.
- If a check requires a potentially persistent side effect, ask before doing it.
