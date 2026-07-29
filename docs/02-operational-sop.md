# Operational SOP

## Knowledge prerequisite — verified for V1

GitHub is the canonical source for `config/icp-rules-v1.md` and `config/signal-rules-v1.md`, but those files are not automatically available to the HubSpot agent. Before publishing or republishing the agent:

Files data is enabled. Both approved Markdown files are in `Invigorate OS — ICP & Signal Rules V1`; the vault is attached to `Invigorate OS — ICP & Signal Research Agent V1`; and agent access has been verified. The vault name and rules version are recorded in private Notion.

Before any rule or agent update:

1. Download both current approved Markdown files from GitHub.
2. Replace the corresponding files in `Invigorate OS — ICP & Signal Rules V1`.
3. Verify the agent can access both documents.
4. Record the rules version in private Notion.
5. Complete the inactive simulation and controlled regression before deployment.

## Request research

1. Confirm the company is a controlled test record during validation.
2. Confirm a usable company domain exists.
3. Confirm the published agent has the approved knowledge vault and rule versions.
4. Confirm current outputs have been reviewed or intentionally superseded.
5. During controlled validation, confirm the workflow was activated with no-existing-record enrollment and set `AI research requested` to Yes on one approved `[TEST]` company only.
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
