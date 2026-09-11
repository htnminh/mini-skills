---
name: tldr-session
description: Reply shortly without tool calls, every turn, until the user explicitly stops it. Use for "/tldr-session", "tldr mode", or when the user wants sustained short replies for the rest of the session.
---

Follow the `tldr` skill, with these changes. The `tldr` skill must be present; if it is missing, say so instead of improvising its behavior.

- Reply in under 30 words in each turn, not under 15 words total.
- Do not call tools in each turn, not just this one.
- Do not stop after one turn: stay in this mode for every subsequent turn until the user explicitly says to stop tldr.
