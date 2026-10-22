---
name: run-unattended
description: Run an approved task without user interaction, exhaust safe in-scope work, then wrap up and leave a project-root handoff. Never automatically invoke this skill.
---

# Run Unattended

Assume the user is absent and will not answer until the run is complete. Carry the requested task as far as possible using the current scope, permissions, credentials, tools, and repository instructions.

## Do not ask

- Never ask the user a question or request confirmation.
- Do not call interactive question or clarification tools.
- Do not pause waiting for approval, feedback, credentials, authentication, or manual action.
- Avoid interactive commands. Use a non-interactive equivalent when it does not change the action's meaning or safety.
- If a choice is necessary, choose the safest reversible default that stays within the user's request and established project conventions.
- If a consequential choice cannot be inferred safely, skip only the affected work, record the blocker, and continue with every independent task.

The user's request authorizes ordinary, reversible work clearly required to complete it. It does not authorize expanding the task, bypassing safeguards, granting new permissions, obtaining new credentials, or performing destructive or irreversible actions that were not clearly requested.

## Work autonomously

1. Read the relevant repository instructions, documentation, existing implementation, tests, and current state before making changes.
2. Determine the intended outcome, constraints, and checkable completion criteria from the user's request. Do not ask the user to restate them.
3. Execute all work that is clearly in scope.
4. When an approach fails, inspect the failure and try reasonable in-scope alternatives.
5. Do not stop at the first blocker. Continue any work that does not depend on it.
6. Use only existing permissions and credentials. Never expose secrets or weaken security controls to make progress.
7. Verify the result with the strongest available checks: inspect the final state, run relevant tests, builds, linters, or health checks, and confirm each completion criterion.
8. Do not claim that skipped, blocked, or unverified work succeeded.

## Finish

After completing and verifying everything possible, perform these steps in order:

1. Follow the `wrap-up` skill exactly as written.
2. Follow the `handoff` skill exactly as written, with one change: create the handoff file in the repository or project root instead of the operating system's temporary directory.

Determine the handoff directory without asking:

1. Use the Git worktree root when inside a Git repository.
2. Otherwise, use the nearest identifiable project root.
3. If no project root can be identified confidently, use the current working directory and record that fallback in the handoff.

Keep the handoff's normal filename pattern, its sections, and all of its content, security, and redaction rules. Within those sections, clearly distinguish:

- completed and verified work, under **Current state**;
- attempted but unsuccessful work, under **Dead ends**;
- skipped work and why it was unsafe or out of scope, under **Open questions**;
- blockers caused by missing access, credentials, permissions, or external dependencies, under **Open questions**;
- remaining recommended work, under **Next tasks**.

Print the wrap-up result first. Then print the handoff skill's required final message and say nothing after it.
