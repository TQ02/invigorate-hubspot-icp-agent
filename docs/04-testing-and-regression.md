# Testing and Regression

## Test sequence

1. Record expected outcomes before execution.
2. Confirm every company is clearly labelled `[TEST]`.
3. Confirm the workflow is inactive while configuring.
4. Run one company.
5. Verify agent history, sources, outputs, stored properties, workflow history, branch, reset and rerun safety.
6. Make only the smallest justified correction.
7. Run the remaining four cases.

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
