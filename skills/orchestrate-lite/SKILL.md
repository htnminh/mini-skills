---
name: orchestrate-lite
description: orchestrate a coding task in one tight loop — explore the code, plan, delegate the implementation to a single sub-agent, then verify and fix the result yourself. use only when the user explicitly invokes this skill or explicitly accepts a recommendation to use it; never apply automatically.
---

# Orchestrate Lite

You are the orchestrator. Do the thinking and the verification yourself; hand only the implementation to a sub-agent.

This is the light version of `orchestrate`: one implementer instead of a role hierarchy, no separate reviewer, and no model-routing table. Reach for `orchestrate` instead when you need independent review or parallel specialists.

## The loop

Work these five steps in order. Never delegate the planning, never skip the verification.

1. **Explore.** Read the code yourself — the files you will touch, their callers, and any tests around them. You cannot plan or judge what you have not read.
2. **Plan.** A handful of lines, not a design document: the change, the file scope, the acceptance criteria, and anything that must not break. Every criterion must be checkable.
3. **Delegate.** Spawn exactly one sub-agent to implement the plan. Keep the prompt concise, like a Jira task: the goal and intended design, the file scope and owner, the acceptance criteria, and a reminder that the workspace may be shared — preserve unrelated changes, never revert another agent's work. Say what must be true, not line by line how to get there. Do not pass the conversation history, and do not let it spawn its own sub-agents.
4. **Verify.** Treat the sub-agent's summary as a claim, not a fact. Read the actual diff, run the tests, build, and linter, and check each acceptance criterion against what you see. Fix anything trivial (under ten lines) yourself.
5. **Fix.** Route substantial failures back to the sub-agent with the exact error output, and verify again after it returns. Repeat until the result is clean or the user explicitly accepts the remaining risk.

## Rules

- Verify from the artefact, never from the sub-agent's prose.
- One implementer. If you need review by a different agent or parallel workstreams, use `orchestrate` instead.
- Do not declare completion until verification is clean or the user accepts the remaining risk.
