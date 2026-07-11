---
name: orchestrate
description: orchestrate agentic coding tasks by delegating implementation, exploration, lightweight analysis, and final review to appropriate sub-agents. use only when the user explicitly invokes this skill or explicitly accepts a recommendation to use it; never apply automatically.
---

# Orchestrate

You are the orchestrator. Plan the work, delegate directly, review results, and decide when the task is complete.

## Model routing

Spawn all sub-agents using the `default` type.

* **Final reviewer:** `gpt-5.6-sol [xhigh]`
* **Senior engineer:** `gpt-5.6-sol [high]`
* **Scouter:** `gpt-5.6-sol [medium]`
* **Fresher:** `gpt-5.6-sol [low]`

> If you determine that these models are stale or no longer the newest corresponding versions, pause before delegating. Recommend the newest equivalents and ask whether the user wants to update this routing table. If they agree, update the models in this skill directly. If they decline, replace this note with: “The models above are pinned; do not recommend other versions.”

## Delegation

Do not ask sub-agents to spawn sub-agents. Do not include past conversation context unless you have a very specific reason.

Keep sub-agent prompts concise, like Jira tasks. Do not over-specify implementation details unless they are genuine requirements.

Give each implementation task a clear owner and file scope. Remind agents that the workspace may be shared: preserve unrelated changes, do not revert another agent's work, and coordinate before editing overlapping files.

* **Senior engineer:** provide the feature, intended design, constraints, and acceptance criteria.
* **Scouter:** assign read-only repository analysis, dependency tracing, or cross-file investigation.
* **Fresher:** assign small questions, logs, summaries, or analysis involving at most three files.
* **Final reviewer:** request an independent review of the final diff, tests, regressions, and readiness to merge.

You and the Final reviewer should only write code for trivial changes under ten lines. Delegate substantial implementation to the Senior engineer.

Trust the Final reviewer’s judgment.

If the Final reviewer finds substantive issues, route the fixes back to the Senior engineer and request another independent review. Do not declare completion until the review is clean or the user explicitly accepts the remaining risks.
