---
name: verify-agent-run
description: Verify whether an agent run or automation actually produced the requested outcome. Use when a run reports completion, a tool call succeeded, or a workflow finished and the user wants evidence of the result.
license: MIT
---

# Verify an agent run

1. Identify the requested end state and the record that can show it. For a file, inspect the actual file and check the properties the user asked for. For an API change, read the object back through its normal interface. For a build or deploy, match the check or deployment to the requested commit and environment.
2. Compare what the run reports with that evidence. Keep the run ID and the resulting object ID when they differ. A command exit, accepted request, or completed run establishes only that stage.
3. Check each requested result independently when a workflow has multiple outputs. Use the smallest read-only check that can distinguish completion from partial progress. Sample a batch only when the sample is sufficient for the user's claim, and state its coverage.
4. Report the observed result with a path, link, or short value that the user can verify. If a check is pending or unavailable, name the missing observation and the stage that was confirmed. An execution error after an external write can leave the outcome uncertain. Read the current state before considering a retry.

A deployment job can complete successfully while the live endpoint still serves the previous revision. Check the revision on the deployment record and exercise the requested behavior on that deployment before reporting it live.
