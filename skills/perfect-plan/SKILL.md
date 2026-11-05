---
name: perfect-plan
description: Create or refine a persistent plan through independent reviews without implementing it. Use when the user asks for a perfect plan.
---

# Perfect Plan

1. Start from the existing plan if there is one; otherwise create one. Save it in a persistent project directory, not a temporary directory. Keep it a plan of changes, with no review history or previously fixed issues.
2. Spawn a fresh, read-only frontier-model subagent with no conversation or prior review context. Give it only the plan path and a minimal request: review the plan and report and count blocking issues (prevent correct execution) and non-blocking issues (improvements, minor gaps or questions). Let it inspect relevant project files read-only.
3. If the review reports any blocking issues, fix all reported issues in the plan and repeat step 2 with a new independent subagent. Do not pass previous feedback to it.
4. If the review reports zero blocking issues, fix the remaining non-blocking issues in the plan and output the plan's absolute path. Do not implement the plan unless the user explicitly asks.

If an independent read-only frontier-model review cannot be run or completed, report the blocker and the plan path; do not claim the plan passed review.
