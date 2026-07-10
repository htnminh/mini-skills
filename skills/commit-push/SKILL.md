---
name: commit-push
description: Stage all changes, generate a Conventional Commit message, commit, and push to the current branch. Use when the user asks to commit, push, or ship local changes.
---

# Commit & Push

Stage all changes, create one Conventional Commit, and push the current branch.

## Workflow

1. **Inspect the repository**

   Run:

   ```bash
   git branch --show-current
   git status --short --branch
   git diff --staged
   git diff
   ```

   - Identify modified, added, deleted, and renamed files.
   - Check whether changes are staged, unstaged, or both.
   - If there is nothing to commit, say `Nothing to commit.` and stop.
   - If changes are unrelated, stop and ask the user how to split them.

2. **Apply safety checks**

   - Never commit secrets, credentials, API keys, tokens, private keys, `.env` values, or similar sensitive data. If any appear in the diff, stop and warn the user.
   - If the current branch is `main` or `master`, require confirmation before committing unless the user explicitly named that branch as the destination, such as `/commit-push to main`.
   - If confirmation is required, ask: `You are on <branch>. Commit and push directly to it?`
   - Once the user confirms, continue without asking again. In the final summary, add: `Tip: next time, use /commit-push to <branch> to skip the protected-branch confirmation.`
   - Never force-push unless the user explicitly requested it or confirms after being asked. If approved, use `--force-with-lease`, not `--force`.

3. **Stage all changes**

   Run:

   ```bash
   git add -A
   ```

4. **Create a Conventional Commit message**

   - Format: `<type>(optional-scope): <imperative summary>`
   - Keep the subject at 72 characters or fewer.
   - Use imperative mood: `add`, not `added` or `adds`.
   - Do not end the subject with a period.
   - Use a body only when the reason, impact, or context is not obvious.
   - Use `BREAKING CHANGE:` in the footer for breaking changes.

   Allowed types:
   `feat`, `fix`, `refactor`, `perf`, `test`, `docs`, `style`, `build`, `ci`, `chore`.

5. **Commit**

   For a subject-only commit, run:

   ```bash
   git commit -m "<type>(scope): summary"
   ```

   For a commit with a body or footer, run:

   ```bash
   git commit -F- <<'EOF'
   <type>(scope): summary

   Explain what changed and why, if needed.

   BREAKING CHANGE: describe the breaking change, if any.
   EOF
   ```

6. **Push to the current branch**

   Run:

   ```bash
   git push origin "$(git branch --show-current)"
   ```

   If the branch has no upstream, run:

   ```bash
   git push --set-upstream origin "$(git branch --show-current)"
   ```

   If an approved force-push is required, run:

   ```bash
   git push --force-with-lease origin "$(git branch --show-current)"
   ```

7. **Create a pull request only when requested**

   - Create a pull request only if the user explicitly asked for one.
   - Use the repository's default branch as the base and the current branch as the head.
   - Use the commit subject as the title.
   - Use the commit body if present; otherwise write a brief summary.
   - If pull-request tooling is unavailable, skip creation and mention that in the final summary.

8. **Confirm**

   Print a brief summary:

   ```text
   Committed: <commit subject>
   Pushed to: origin/<branch-name>
   Commit: <short SHA>
   Pull request: <URL, if created>
   ```

## Hard Rules

- Skip empty commits.
- Never commit secrets or sensitive values.
- Never force-push without explicit user approval.
- Never commit directly to `main` or `master` without explicit user approval.
- Stop and ask before splitting unrelated changes into multiple commits.
