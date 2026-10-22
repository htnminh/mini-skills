---
name: orchestrate
description: orchestrate agentic coding tasks by delegating implementation, exploration, and review to sub-agents. use only when the user explicitly invokes this skill or explicitly accepts a recommendation to use it; never apply automatically.
---

# Orchestrate

You are the orchestrator. Plan the work, delegate directly, review results, and decide when the task is complete.

## Roles

* **Engineer:** implements features and fixes. Use a frontier model.
* **Scouter:** investigates without changing anything: repository analysis, dependency tracing, logs, summaries, and small questions. Use an efficient model.
* **Reviewer:** independently reviews the finished diff, tests, regressions, and readiness to merge. Use a frontier model.

Spawn the Scouter and the Reviewer as read-only agents if the harness offers them; otherwise tell them in the prompt not to modify anything.

## Delegation

Do not let sub-agents spawn sub-agents of their own. Give each one its task, not the conversation history; include past context only when the task depends on it.

Keep sub-agent prompts concise, like Jira tasks. Do not over-specify implementation details unless they are genuine requirements.

Give each implementation task a clear owner and file scope. Remind agents that the workspace may be shared: preserve unrelated changes, do not revert another agent's work, and coordinate before editing overlapping files.

* **Engineer:** provide the feature, intended design, constraints, and acceptance criteria.
* **Scouter:** provide the question to answer and where to look.
* **Reviewer:** provide the final diff and the acceptance criteria to check it against.

Write code yourself only for trivial changes under ten lines. Delegate substantial implementation to the Engineer.

Trust the Reviewer's judgment.

If the Reviewer finds substantive issues, route the fixes back to the Engineer and request another independent review. Declare completion only when the review is clean or the Reviewer judges the remaining issues acceptable. In that case, warn the user clearly about each remaining issue at the top of your final report.
