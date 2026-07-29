# Regression Preparation — 2026-07-29

Status: workflow prepared and read back; simulation and runtime not executed.

Five exact `[TEST]` company records were created in the verified developer-test portal and fetched back. Each record has the public domain recorded in `tests/test-company-manifest.csv`, `inv_ai_research_requested = false`, and `inv_ai_research_status = Not requested`.

The knowledge vault is attached, the agent is published, and the complete inactive workflow has been read back. It contains the approved enrollment event and domain refinement, Run-agent input, six output mappings, five deterministic branches, seven completion/reset paths and one failure-review task.

No record was enrolled and no agent or workflow run occurred. The post-build safety audit found all five test companies at requested = No with no scores, completion timestamp or failure reason, and zero companies in the portal at requested = Yes.

The inactive workflow Test feature may be used for structural simulation, but it will not execute the agent or any workflow action and will not provide runtime evidence. The first real evidence must come from activating the restricted workflow with no-existing-record enrollment selected, then changing only Case 1 from requested = No to Yes.

The post-write company audit returned exactly these five `[TEST]` records. Because the workflow remained OFF and no record was requested, no workflow-triggered test or non-test company write occurred.

No HubSpot record IDs, private CRM data, or screenshots are stored here.
