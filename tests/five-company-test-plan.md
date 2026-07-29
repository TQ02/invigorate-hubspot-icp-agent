# Five-Company Test Plan

All records must be clearly labelled `[TEST]` and use public domains suitable for controlled research.

| Case | Scenario | Expected branch |
|---:|---|---|
| 1 | Ideal ICP plus strong current signal | Prioritise |
| 2 | Ideal ICP with no meaningful current signal | Monitor |
| 3 | Moderate fit plus strong signal | Review |
| 4 | Poor fit | Exclude |
| 5 | Incomplete or conflicting evidence | Review / Pending review |

## Execution

Run Case 1 first. Verify agent run, sources, six outputs, property writes, workflow history, deterministic branch, close-out and request reset. Make only the smallest justified correction. Then run Cases 2–5.

## Rerun

After the initial pass, reset Case 1 through the documented request transition and verify that values are overwritten safely without duplicate tasks or stuck status.

## Integrity

The expected branch is a test hypothesis, not a scoring target. Record reasonable AI variation and source limitations honestly.
