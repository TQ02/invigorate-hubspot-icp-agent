# Testing and Regression

## A. Inactive simulation test

Status: pending. The workflow is fully configured and remains inactive.

1. Record expected outcomes before execution.
2. Confirm every company is clearly labelled `[TEST]`.
3. Keep the workflow inactive.
4. Use the workflow **Test** feature to verify enrollment criteria, workflow structure, branch ordering, no accidental general enrollment, and anticipated paths only.
5. Record structural corrections before activation.

HubSpot's workflow Test feature simulates the path. It does not execute the agent or actions and does not write properties. A simulation result is not runtime evidence.

## B. Real Case 1 runtime test

Status: not started. Do not begin until the inactive simulation passes.

1. Confirm all five test companies have requested = No.
2. Turn on the workflow.
3. Choose **No, only enroll companies which meet the trigger criteria after turning the workflow on**.
4. Confirm the workflow has only the requested = Yes and domain-known enrollment route, and confirm no existing company enrolled.
5. Set requested = Yes only for `[TEST] ICP Signal Case 1`.
6. Monitor the actual enrollment.
7. Verify agent history, sources, six outputs, stored properties, workflow history, deterministic branch, completed date, request reset, and no non-test company changes.
8. Make only the smallest justified correction.
9. Test the Case 1 No-to-Yes rerun only after the first run passes.
10. Run the remaining four cases only after Case 1 and its rerun pass.

Do not activate this workflow for general or production enrollment.

## Pass criteria

- The agent run is visible and its sources are reviewable.
- All six outputs are usable and mapped correctly.
- Numeric values are within 0–100.
- Classification matches the ICP score.
- HubSpot selects the expected deterministic branch given the actual outputs.
- Every path sets a completion date and resets requested to No.
- Failure and none-met paths route to Review.
- No non-test record changes.

## Regression trigger

Repeat the five cases after any change to prompts, tools, rules, properties, thresholds, workflow actions, mappings, delays, or branch order.

## Evidence

Store sanitized expected-versus-actual results under `tests/results/`. Do not commit record IDs, private CRM data, or unsanitized screenshots.
