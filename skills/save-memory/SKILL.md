---
name: save-memory
description: Save durable knowledge from this conversation into every memory store the harness provides, including instruction files, so a later session does not pay to rediscover it. Use when the user asks to remember something for next time, or when wrapping up work worth carrying forward.
---

Record what a later session would pay to rediscover, and nothing else.

**Write to every store that fits, not only the first one found** — missing one is the usual failure:
- The harness's memory store, if it has one. Its location is named in your own instructions or configuration, so do not invent one.
- Instruction files such as `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.cursor/rules`, or `.github/copilot-instructions.md`, usually one user-level and one committed with the repository.

Route by kind: rules that shape how work is done belong in instruction files, project-level when repository-specific; orientation and pointers belong in the memory store; detail owned by a design, plan, or ticket stays there and is only referenced.

Save decisions with their non-obvious reasons, constraints, dead ends, facts that contradict the obvious assumption, and pointers to what no search would reveal. Skip whatever the repository, git history, or documentation already states, whatever one command re-derives, and conversation narrative. Never record a secret value; record which credential is needed and where to obtain it.

When writing: follow the structure and conventions the store already uses; update an existing entry instead of adding a near-duplicate; delete what proved wrong; update the index if there is one; use absolute dates; reference sources by path, URL, or commit and stay brief when the source is easy to open; confirm a claim about code still holds before recording it.

Report what you wrote, updated, or skipped, and where each landed.
