# Consolidated HubSpot UI Checklist

Complete this checklist only in the verified **LeadHubAI - Demo client portal**. Keep the workflow inactive until the single-record test passes. Do not select or enroll non-test records.

## 1. Enable the required AI setting

1. Open **Settings → AI**.
2. Confirm generative AI and CRM data access remain enabled.
3. Enable **Files data**.
4. Record the available credit estimate, monthly run allowance, and any per-run warning in the private Notion operating page. Do not copy account identifiers or billing details into this public repository.

## 2. Configure and publish the read-only agent

1. Open **Breeze → Agent Hub**.
2. Start from the visible **Company Research Agent** template.
3. Set the name to `Invigorate OS — ICP & Signal Research Agent V1`.
4. Replace the instructions with the complete contents of `config/agent-instructions-v1.md`.
5. Give the agent only company-CRM read access and permitted public-web research.
6. Remove or disable every CRM create, update, delete, task, note, activity, contact, deal, or company write action.
7. Confirm the agent does not assign Prioritise, Monitor, Review, or Exclude.
8. Save and publish the agent.
9. Re-open it and verify the name, instructions, allowed tools, prohibited writes, and version `1.0`.

## 3. Build the inactive company workflow

1. Open **Automation → Workflows** and create a blank company-based workflow.
2. Name it `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1`.
3. Leave it inactive.
4. Set enrollment to:
   - `[TEST] AI research requested` is Yes; and
   - company domain is known.
5. Enable re-enrollment only when `[TEST] AI research requested` changes to Yes.
6. When the workflow is eventually activated, choose **No, only enroll companies which meet the trigger criteria after turning the workflow on**.
7. Add the initial actions in this order:
   - research status = `Researching`;
   - agent version = `1.0`;
   - rules version = `1.0`;
   - workflow version = `1.0`;
   - clear research failure reason.
8. Add **Run agent** and select `Invigorate OS — ICP & Signal Research Agent V1`.
9. Configure these structured outputs:

| Output | Type |
|---|---|
| `icp_score` | Number |
| `signal_score` | Number |
| `icp_classification` | Enumeration: Ideal, Strong, Possible, Weak, Poor |
| `primary_signal` | Text |
| `qualification_reasoning` | Text |
| `research_confidence` | Number |

10. Branch immediately on the Run-agent action outcome.
11. On success, map all six outputs to the corresponding `inv_ai_` properties.
12. Add no delay initially. Add only the smallest delay demonstrated necessary by the single-record test.
13. Add deterministic success branches in this exact order:

| Order | Condition | Priority | Status |
|---:|---|---|---|
| 1 | confidence missing, ICP missing, signal missing, or confidence below 60 | Review | Pending review |
| 2 | confidence at least 60, ICP at least 70, signal at least 65 | Prioritise | Complete |
| 3 | confidence at least 60, ICP at least 70, signal below 65 | Monitor | Complete |
| 4 | confidence at least 60, ICP from 50 through 69 | Review | Pending review |
| 5 | confidence at least 60, ICP below 50 | Exclude | Complete |

14. Configure the Run-agent failure path:
   - research status = `Failed`;
   - account priority = `Review`;
   - qualification reasoning = `AI research unavailable — manual review required.`;
   - failure reason = `Agent run failed or returned no usable output. Manual review required.`;
   - completed date = current time;
   - research requested = No;
   - create a manual-review task if the action is available.
15. Configure the none-met path:
   - priority = `Review`;
   - status = `Pending review`;
   - failure reason = `Unexpected branch output — manual review required.`;
   - create a manual-review task if the action is available.
16. Close every success and none-met branch by setting completed date to current time and research requested to No.
17. Review workflow actions, mappings, branch order, re-enrollment, and the no-existing-records activation choice. Keep the workflow inactive.

## 4. Single-record runtime handoff

1. Use only `[TEST] ICP Signal Case 1`.
2. Test the workflow from the HubSpot workflow editor while it remains otherwise inactive.
3. Verify the agent history, sources, all six outputs, property mappings, workflow branch, completion date, and requested reset.
4. Record sanitized expected-versus-actual results under `tests/results/`.
5. Correct only the smallest demonstrated issue.
6. Test the No-to-Yes rerun transition and confirm values overwrite safely without duplicate tasks.
7. Only after Case 1 passes, run Cases 2–5 and complete the production audit. Do not activate for general enrollment.
