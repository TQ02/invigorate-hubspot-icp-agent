# Consolidated HubSpot UI Checklist

Complete this checklist only in the verified **LeadHubAI - Demo client portal**. Do not select or enroll non-test records. GitHub files are not automatically available to a HubSpot agent.

## 1. Enable Files data and create the approved knowledge vault

1. Open **Settings → AI**.
2. Confirm generative AI and CRM data access remain enabled.
3. Enable **Files data**.
4. Download the current approved versions of:
   - `config/icp-rules-v1.md`
   - `config/signal-rules-v1.md`
5. Open **Agents → Agent Hub → Context → Knowledge vaults**.
6. Click **Create vault**.
7. Name the vault exactly `Invigorate OS — ICP & Signal Rules V1`.
8. Upload both downloaded Markdown files and create the vault.
9. Open the vault and verify both filenames are present and readable.
10. Record the available credit estimate, monthly run allowance, and any per-run warning in private Notion. Do not copy account identifiers or billing details into this public repository.

## 2. Configure and publish the read-only agent

1. Open **Agents → Agent Hub → Agents**.
2. Start from the visible **Company Research Agent** template.
3. Set the name to `Invigorate OS — ICP & Signal Research Agent V1`.
4. Replace the instructions with the complete contents of `config/agent-instructions-v1.md`.
5. Under **What this agent knows** or **Knowledge**, click **Add knowledge**.
6. Attach `Invigorate OS — ICP & Signal Rules V1`.
7. Open the attached vault details and verify the agent can access both `icp-rules-v1.md` and `signal-rules-v1.md` before publishing.
8. Record the knowledge-vault name and rules version `1.0` in the private Notion operating documentation.
9. Give the agent only company-CRM read access and permitted public-web research.
10. Remove or disable every CRM create, update, delete, task, note, activity, contact, deal, or company write action.
11. Confirm the agent does not assign Prioritise, Monitor, Review, or Exclude.
12. Save and publish the agent.
13. Re-open it and verify the name, instructions, attached vault, both rule documents, allowed tools, prohibited writes, and version `1.0`.

Never assume that files stored in GitHub are directly available to the HubSpot agent. When approved rule files change, download the new canonical versions, replace or update the vault files, verify agent access, record the version, and complete the regression before deployment.

## 3. Build the inactive company workflow

1. Open **Automation → Workflows** and create a blank company-based workflow.
2. Name it `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1`.
3. Leave it inactive while configuring and simulating.
4. Set the only enrollment route to:
   - `[TEST] AI research requested` is Yes; and
   - company domain is known.
5. Enable re-enrollment only when `[TEST] AI research requested` changes from No to Yes.
6. Add the initial actions in this order:
   - research status = `Researching`;
   - agent version = `1.0`;
   - rules version = `1.0`;
   - workflow version = `1.0`;
   - clear research failure reason.
7. Add **Run agent** and select `Invigorate OS — ICP & Signal Research Agent V1`.
8. Configure these structured outputs:

| Output | Type |
|---|---|
| `icp_score` | Number |
| `signal_score` | Number |
| `icp_classification` | Enumeration: Ideal, Strong, Possible, Weak, Poor |
| `primary_signal` | Text |
| `qualification_reasoning` | Text |
| `research_confidence` | Number |

9. Branch immediately on the Run-agent action outcome.
10. On success, map all six outputs to the corresponding `inv_ai_` properties.
11. Add no delay initially. Add only the smallest delay demonstrated necessary by the real Case 1 runtime test.
12. Add deterministic success branches in this exact order:

| Order | Condition | Priority | Status |
|---:|---|---|---|
| 1 | confidence missing, ICP missing, signal missing, or confidence below 60 | Review | Pending review |
| 2 | confidence at least 60, ICP at least 70, signal at least 65 | Prioritise | Complete |
| 3 | confidence at least 60, ICP at least 70, signal below 65 | Monitor | Complete |
| 4 | confidence at least 60, ICP from 50 through 69 | Review | Pending review |
| 5 | confidence at least 60, ICP below 50 | Exclude | Complete |

13. Configure the Run-agent failure path:
   - research status = `Failed`;
   - account priority = `Review`;
   - qualification reasoning = `AI research unavailable — manual review required.`;
   - failure reason = `Agent run failed or returned no usable output. Manual review required.`;
   - completed date = current time;
   - research requested = No;
   - create a manual-review task if the action is available.
14. Configure the none-met path:
   - priority = `Review`;
   - status = `Pending review`;
   - failure reason = `Unexpected branch output — manual review required.`;
   - create a manual-review task if the action is available.
15. Close every success and none-met branch by setting completed date to current time and research requested to No.
16. Review workflow actions, mappings, branch order, re-enrollment, and the single enrollment route. Keep the workflow inactive.

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
