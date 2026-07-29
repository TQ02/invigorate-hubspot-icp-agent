# Monitoring and Recovery

## Monthly monitoring

Review five recent runs plus every Failed and Pending review record.

Inspect:

- source authority and freshness;
- attached knowledge-vault name, both canonical rule files, and stamped rules version;
- confidence distribution;
- blank or malformed outputs;
- branch distribution;
- agent, rules and workflow versions;
- execution time and credit estimates;
- duplicate or stuck requests.

## Alerts and review queue

The configured workflow routes failures, low confidence, missing values and unexpected branch results to Review. The agent-failure path creates one high-priority manual-review task.

## Recovery

1. Keep or return the workflow to inactive if systemic risk exists.
2. Verify the agent still has access to both approved files in `Invigorate OS — ICP & Signal Rules V1`.
3. Identify whether the issue is knowledge availability, source quality, agent output, mapping, branch logic, permission, credit limit, or HubSpot availability.
4. Correct the smallest safe component.
5. Reset only the affected `[TEST]` record.
6. Run the inactive simulation for structural verification.
7. Run one real recovery test through deliberate No-to-Yes enrollment.
8. Verify close-out and request reset.
9. Repeat the five-company regression after material changes.

Never bulk-reset or re-enroll production records.

## Current verification baseline

Before Case 1, the workflow readback showed six output mappings, the five approved deterministic branches in order, seven current-time completion stamps, seven request resets and one failure task. All five test companies were requested = No with no completion timestamp, score or failure reason, and no company in the portal was requested = Yes.
