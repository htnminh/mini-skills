---
name: orchestrate-lite
description: orchestrate a coding task in one tight loop — explore the code, plan, delegate the implementation to a single sub-agent, then verify and fix the result yourself. use only when the user explicitly invokes this skill or explicitly accepts a recommendation to use it; never apply automatically.
---

# Orchestrate Lite

You are the orchestrator. Do the thinking and the verification yourself; hand only the implementation to a sub-agent.

This is the light version of `orchestrate`: one implementer instead of a role hierarchy, no separate reviewer, and no model-routing table. Reach for `orchestrate` instead when you need independent review or parallel specialists.

## The loop

Work these five steps in order. Do not skip verification, and do not delegate the planning.

1. **Explore.** Read the relevant code yourself — the files you will touch, their callers, and any tests around them. You cannot write a plan or judge a result you have not read.

   *Done when:* you can name every file the change touches and say what each one does today.

2. **Plan.** Write a short plan before delegating: the change in one or two lines, the files and scope, the acceptance criteria, and anything that must not break. Keep it to a handful of lines — this is the sub-agent's brief, not a design document.

   *Done when:* each acceptance criterion is checkable and the file scope is explicit.

3. **Delegate.** Spawn exactly one sub-agent to implement the plan. Do not ask it to spawn its own sub-agents, and do not hand it the conversation history. Pass the plan, the file scope, and the acceptance criteria; tell it the workspace may be shared and it must preserve unrelated changes. Do not over-specify the implementation — say what must be true, not line by line how to get there.

   *Done when:* the sub-agent returns with the work claimed complete.

4. **Verify.** Treat the sub-agent's summary as a claim, not a fact. Read the actual diff, run the tests, build, and linter, and check each acceptance criterion against what you see. Fix trivial problems (under ten lines) yourself.

   *Done when:* every acceptance criterion is checked and you have a verdict — clean, or a list of concrete failures.

5. **Fix.** For anything substantial, route the failures back to the sub-agent with the exact error output and re-verify after it returns. Repeat until the result is clean or the user explicitly accepts the remaining risk.

   *Done when:* the work is verified clean, or you are blocked and have asked the user.

## Delegation prompts

Keep them concise, like a Jira task. Include:

- the goal and intended design;
- the file scope and owner;
- the acceptance criteria;
- the requirement to preserve unrelated changes and not revert another agent's work.

Do not include past conversation unless there is a specific reason.

## Rules

- Explore and plan yourself; never delegate them.
- One implementer. If you need review by a different agent or parallel workstreams, use `orchestrate` instead.
- Verify from the artefact, never from the sub-agent's prose.
- Do not declare completion until verification is clean or the user accepts the remaining risk.
