# Operational SOP

## Knowledge prerequisite

GitHub is the canonical source for `config/icp-rules-v1.md` and `config/signal-rules-v1.md`, but those files are not automatically available to the HubSpot agent. Before publishing or republishing the agent:

1. Enable Files data.
2. Download both current approved Markdown files from GitHub.
3. Upload them to `Invigorate OS — ICP & Signal Rules V1`.
4. Attach that knowledge vault to `Invigorate OS — ICP & Signal Research Agent V1`.
5. Verify the agent can access both documents.
6. Record the vault name and rules version in private Notion.

## Request research

1. Confirm the company is a controlled test record during validation.
2. Confirm a usable company domain exists.
3. Confirm the published agent has the approved knowledge vault and rule versions.
4. Confirm current outputs have been reviewed or intentionally superseded.
5. Set `AI research requested` to Yes.
6. Monitor status until Complete, Pending review, or Failed.

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

Stop and escalate on missing or stale vault files, non-test enrollment, wrong portal, unexpected credit use, direct agent CRM writes, incomplete property mapping, or evidence that a workflow branch can affect unrelated records.
