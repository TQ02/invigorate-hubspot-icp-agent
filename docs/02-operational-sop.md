# Operational SOP

## Request research

1. Confirm the company is a controlled test record during validation.
2. Confirm a usable company domain exists.
3. Confirm current outputs have been reviewed or intentionally superseded.
4. Set `AI research requested` to Yes.
5. Monitor status until Complete, Pending review, or Failed.

## Interpret outcomes

- Prioritise: strong fit and strong signal with adequate confidence.
- Monitor: strong fit without a strong current signal.
- Review: moderate fit, low confidence, missing values, failure, or unexpected branch result.
- Exclude: poor fit with adequate confidence.

## Manual review

Review sources, missing data, conflicts, scores, confidence, versions, workflow history and agent history. Do not manually force scores simply to reach a desired branch.

## Rerun

Correct the source record or configuration, confirm the workflow is safe, then change `AI research requested` from No to Yes. Verify that old outputs and failure text are replaced correctly.

## Stop conditions

Stop and escalate on non-test enrollment, wrong portal, unexpected credit use, direct agent CRM writes, incomplete property mapping, or evidence that a workflow branch can affect unrelated records.
