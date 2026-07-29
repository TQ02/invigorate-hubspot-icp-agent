# Monitoring and Recovery

## Monthly monitoring

Review five recent runs plus every Failed and Pending review record.

Inspect:

- source authority and freshness;
- confidence distribution;
- blank or malformed outputs;
- branch distribution;
- agent, rules and workflow versions;
- execution time and credit estimates;
- duplicate or stuck requests.

## Alerts and review queue

The workflow routes failures, low confidence, missing values and unexpected branch results to Review. A review task should be created when supported.

## Recovery

1. Keep or return the workflow to inactive if systemic risk exists.
2. Identify whether the issue is source quality, agent output, mapping, branch logic, permission, credit limit, or HubSpot availability.
3. Correct the smallest safe component.
4. Reset only the affected `[TEST]` record.
5. Run one recovery test.
6. Verify close-out and request reset.
7. Repeat the five-company regression after material changes.

Never bulk-reset or re-enroll production records.
