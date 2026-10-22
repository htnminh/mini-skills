---
name: wrap-up
description: Close out a working session by writing a durable audit log of what happened and saving what is worth carrying forward. Use when the user is finishing up, says to wrap up, or ends a session's work.
---

Close the session in two steps, in this order. Both are required. The `handoff` and `save-memory` skills must both be available; if one is missing, say so and complete the other step anyway.

**1. Write the session log.** Follow the `handoff` skill, with three changes:

- **Write to a persistent directory, not a temporary one.** Use the user's preferred directory if one is known; otherwise use `~/mini-session-history`, creating it if it does not exist. Name the file `YYYY-MM-DD__project-name__session-title.md`, using the current date and handoff's slug rules.

- **Write an audit log, not a briefing for the next task.** Use handoff's sections, with these swaps:
  - **Goal** becomes **Requests**: each user request as a short quote in the user's own words, one line each.
  - Add **Chronology** after Requests: numbered steps in the order they happened, each naming the files it touched and the check that proved it worked.
  - **Current state** becomes **Final state**, and also lists each commit with its hash and subject.
  - **Next tasks** becomes **Open items**: unfinished work and known defects, each with where it lives.
- **Skip handoff's closing message.** Do not print "Conversation successfully handed off"; the closing line at the end of this skill replaces it.

**2. Save durable knowledge.** Follow the `save-memory` skill as written, with no changes. Keep memory independent of the log: write memory as if the log did not exist, and do not reference it.

Finish by printing the log path and one line on what memory was written or updated.
