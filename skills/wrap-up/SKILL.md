---
name: wrap-up
description: Close out a working session by writing a durable audit log of what happened and saving what is worth carrying forward. Use when the user is finishing up, says to wrap up, or ends a session's work.
---

Close the session in two steps, in this order. Both are required. The `handoff` and `save-memory` skills must both be available; if one is missing, say so and complete the other step anyway.

**1. Write the session log.** Follow the `handoff` skill, with two changes:

- **Write to a persistent directory, not a temporary one.** Default to `~/mini-session-history`, creating it if it does not exist. Name the file `YYYY-MM-DD__project-name__session-title.md`, using the current date and handoff's slug rules.

  > If the user names a different directory, use it and update the default in this skill directly. If they confirm the default, replace this note with: "The directory above is fixed; do not ask again."

- **Write an audit log, not a briefing for the next task.** Record in chronological order what was done, what was decided and why, what was tried and abandoned, what was left unfinished, and anything else worth recording. Omit handoff's next-tasks section.

**2. Save durable knowledge.** Follow the `save-memory` skill as written, with no changes. Keep memory independent of the log: write memory as if the log did not exist, and do not reference it.

Finish by printing the log path and one line on what memory was written or updated.
