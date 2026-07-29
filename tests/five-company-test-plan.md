# Five-Company Test Plan

All records must be clearly labelled `[TEST]` and use public domains suitable for controlled research.

| Case | Scenario | Expected branch |
|---:|---|---|
| 1 | Ideal ICP plus strong current signal | Prioritise |
| 2 | Ideal ICP with no meaningful current signal | Monitor |
| 3 | Moderate fit plus strong signal | Review |
| 4 | Poor fit | Exclude |
| 5 | Incomplete or conflicting evidence | Review / Pending review |

## A. Simulation

Status: pending. The workflow is configured and inactive. Use HubSpot Test to verify enrollment criteria, structure, branch order, no accidental general enrollment, and anticipated paths. This simulation does not run the agent or write properties.

## B. Real execution

Status: not started.

Confirm every test company has requested = No. Turn on the restricted workflow. Choose **No, only enroll companies which meet the trigger criteria after turning the workflow on**. Confirm there is no other enrollment route and no existing company enrolled, then set requested = Yes only for Case 1.

Verify the actual agent run, sources, six outputs, property writes, workflow history, deterministic branch, completed date, request reset, and no non-test company changes. Make only the smallest justified correction. Run Cases 2–5 only after Case 1 and its rerun pass.

## Rerun

Only after the first real Case 1 run is verified, use the documented No-to-Yes transition and verify that values are overwritten safely without duplicate tasks or stuck status.

## Integrity

The expected branch is a test hypothesis, not a scoring target. Record reasonable AI variation and source limitations honestly.
