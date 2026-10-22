---
name: handoff
description: Create a secure handoff file that preserves the context another agent or coding harness needs to continue without costly rediscovery. Use when the user wants to move ongoing work to another session, conversation, agent, or harness.
---

Write a handoff document summarizing the current conversation so a fresh agent or coding harness can continue the work.

Start with this command pattern:
- Unix-like shell: `mktemp -t 'handoff__project-name__handoff-title__XXXXXXXX.md'`
- Windows PowerShell: `$handoff = Join-Path $env:TEMP ("handoff__project-name__handoff-title__{0}.md" -f ([System.IO.Path]::GetRandomFileName().Split('.')[0])); New-Item -ItemType File -Path $handoff -ErrorAction Stop | Out-Null; $handoff`

Where:
- `project-name` identifies the project, usually the repository name.
- `handoff-title` is a short, filesystem-safe slug that descriptively identifies the purpose of the handoff.

After creating the file, read it first if the harness requires a file to be read before it can be edited. Then write the handoff document to that file.
- **The handoff must preserve enough context from the whole conversation for the next agent to continue without losing the thread.**
- Use these sections, in this order. Write "None." under an empty section, so every handoff has the same shape and a reader always finds a fact in the same place:
  1. **Header**: project, branch, date, and the session identifier if the harness exposes one.
  2. **Goal**: the current goal and its constraints. Quote the user's own words wherever the next agent must not reinterpret them.
  3. **Decisions**: what was chosen, what it was chosen over, and why.
  4. **Dead ends**: what was tried and why it failed, so no one tries it again.
  5. **Current state**: branch, last commit, uncommitted changes, processes or services left running, and files created outside the repository.
  6. **Open questions**: unresolved questions and assumptions not yet confirmed.
  7. **Next tasks**: what the next agent should do, following the rule for unclear next tasks below.
  8. **Notes**: anything else worth keeping that fits no section above.
- Keep one fact per bullet. Include anything expensive or risky to rediscover; point to files, commits, and diffs instead of copying them.
- If the user specified what the next session should focus on, emphasize that focus without omitting broader context needed for continuity.
- When relevant, suggest under **Next tasks** the skills the next session is likely to need. Mention only skills that fit its expected work.
- Do not duplicate content already captured in other artifacts, such as PRDs, plans, ADRs, issues, commits, or diffs. Reference those artifacts by path, URL, commit hash, identifier, or any other durable pointer that lets the next agent find the original source.
- **Handle sensitive information carefully.** Do not include raw API keys, passwords, tokens, private credentials, or secrets in the handoff. Instead, describe what secret is needed, where it should be configured, and how the next agent should reference it, such as an existing environment variable name, project `.env` file entry, secret manager key, or setup step. Redact PII unless it is necessary for continuing the work.
- If the next tasks are not clear, help the receiving agent suggest useful next steps because you have the most comprehensive context. Under **Next tasks**, write them in this format:
  > Next tasks unclear. Ask the user what they want to do next. Suggestions:
  > - {Suggested next task 1}
- After writing the handoff, print the final path in this format and say nothing else:
  > Conversation successfully handed off, paste this prompt into another agent or conversation:
  >
  > Pick up and continue from this handoff: {absolute path to handoff file}
