# Consolidated HubSpot UI Checklist

Complete this checklist only in the verified **LeadHubAI - Demo client portal**. Do not select or enroll non-test records. GitHub files are not automatically available to a HubSpot agent.

## 1. Verify the completed knowledge setup

1. Open **Settings → AI** and confirm generative AI, CRM data access and **Files data** remain enabled.
2. Confirm the current approved versions of these files are still canonical:
   - `config/icp-rules-v1.md`
   - `config/signal-rules-v1.md`
3. Open **Agents → Agent Hub → Context → Knowledge vaults**.
4. Open `Invigorate OS — ICP & Signal Rules V1`.
5. Verify both filenames are present and readable.
6. Confirm the private Notion operating documentation records this vault and rules version `1.0`.
7. Record the available credit estimate, monthly run allowance and any per-run warning in private Notion. Do not copy account identifiers or billing details into this public repository.

## 2. Verify the published read-only agent

1. Open **Agents → Agent Hub → Agents**.
2. Open the published `Invigorate OS — ICP & Signal Research Agent V1`.
3. Verify its instructions match `config/agent-instructions-v1.md`.
4. Verify `Invigorate OS — ICP & Signal Rules V1` is attached and both `icp-rules-v1.md` and `signal-rules-v1.md` are accessible.
5. Verify the agent has only company-CRM read access and permitted public-web research.
6. Confirm every CRM create, update, delete, task, note, activity, contact, deal or company write action is absent or disabled.
7. Confirm the agent does not assign Prioritise, Monitor, Review or Exclude.
8. Verify version `1.0`.

Never assume that files stored in GitHub are directly available to the HubSpot agent. When approved rule files change, download the new canonical versions, replace or update the vault files, verify agent access, record the version, and complete the regression before deployment.

## 3. Verify the completed inactive company workflow

1. Open **Automation → Workflows** and open `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1`.
2. Confirm it is company-based and **OFF**.
3. Verify the only enrollment route is:
   - `[TEST] AI research requested` is Yes; and
   - company domain is known.
4. Verify re-enrollment is permitted only when `[TEST] AI research requested` changes from No to Yes.
5. Verify the initial actions are in this order:
   - research status = `Researching`;
   - agent version = `1.0`;
   - rules version = `1.0`;
   - workflow version = `1.0`;
   - clear research failure reason.
6. Verify **Run agent** selects `Invigorate OS — ICP & Signal Research Agent V1` and maps the enrolled company domain into `Domain or Company Name`.
7. Verify these structured outputs:

| Output | Type |
|---|---|
| `icp_score` | Number |
| `signal_score` | Number |
| `icp_classification` | Enumeration: Ideal, Strong, Possible, Weak, Poor |
| `primary_signal` | Text |
| `qualification_reasoning` | Text |
| `research_confidence` | Number |

8. Verify usable output is routed when `icp_score > -1`; missing or unusable output goes to `AGENT FAILURE OR UNUSABLE OUTPUT`.
9. Verify all six outputs map to the corresponding `inv_ai_` properties.
10. Confirm there is no delay.
11. Verify deterministic success branches in this exact order:

| Order | Condition | Priority | Status |
|---:|---|---|---|
| 1 | confidence missing, ICP missing, signal missing, or confidence below 60 | Review | Pending review |
| 2 | confidence at least 60, ICP at least 70, signal at least 65 | Prioritise | Complete |
| 3 | confidence at least 60, ICP at least 70, signal below 65 | Monitor | Complete |
| 4 | confidence at least 60, ICP from 50 through 69 | Review | Pending review |
| 5 | confidence at least 60, ICP below 50 | Exclude | Complete |

12. Verify the Run-agent failure path:
   - research status = `Failed`;
   - account priority = `Review`;
   - qualification reasoning = `AI research unavailable — manual review required.`;
   - failure reason = `Agent run failed or returned no usable output. Manual review required.`;
   - completed date = current time;
   - research requested = No;
   - create one high-priority manual-review task.
13. Verify the none-met path:
   - priority = `Review`;
   - status = `Pending review`;
   - failure reason = `Unexpected branch output — manual review required.`;
14. Verify every success and none-met branch sets completed date to current time and research requested to No.
15. Confirm the readback baseline: 46 actions, six output mappings, five ordered deterministic branches, seven completion/reset paths and one agent-failure review task. Keep the workflow inactive.

## 4. Run the inactive simulation test

1. In the workflow editor, click **Test**.
2. Simulate the controlled test records as needed.
3. Verify enrollment criteria, workflow structure, branch ordering, absence of accidental general enrollment, and anticipated paths only.
4. Treat branch outcomes as predictions based on each record's current values.
5. Record any structural correction before activation.

The workflow Test feature is a simulation. It does not run the agent, execute actions, write properties, create tasks, stamp completion dates, or reset the request field. Simulation is not runtime evidence.

## 5. Run the real Case 1 runtime test

1. Confirm all five `[TEST]` companies have `[TEST] AI research requested = No`.
2. Turn on the workflow.
3. Choose **No, only enroll companies which meet the trigger criteria after turning the workflow on**.
4. Confirm the workflow has no enrollment route other than requested = Yes **and** domain is known, and confirm no company enrolled at activation.
5. Set `[TEST] AI research requested = Yes` only for `[TEST] ICP Signal Case 1`.
6. Monitor the real workflow enrollment and its action history.
7. Verify the actual agent run, agent sources, six structured outputs, actual HubSpot property writes, actual deterministic branch, completed date, request reset to No, and that no non-test company changed. Record sanitized expected-versus-actual evidence under `tests/results/` and correct only the smallest demonstrated issue.
8. Only after the first real Case 1 run is verified, change Case 1 from requested = No to Yes again. Confirm outputs are safely overwritten, close-out succeeds, requested resets to No, and no duplicate task is created.
9. Run Cases 2–5 only after Case 1 and its rerun pass. Verify no non-test company changes after every run.
10. Do not add a general or production enrollment route. This workflow remains restricted to deliberate `[TEST]` requests and is not production-approved.
