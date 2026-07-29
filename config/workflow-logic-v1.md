# Workflow Logic V1

Version: 1.0

Name: `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1`

Object: Company

Initial status: inactive

## Enrollment

Enroll only when:

- `inv_ai_research_requested` is Yes; and
- company domain is known.

Allow controlled re-enrollment when `inv_ai_research_requested` changes to Yes. Do not enroll existing records when the workflow is activated.

## Initial actions

1. Set research status to `Researching`.
2. Set agent version to `1.0`.
3. Set rules version to `1.0`.
4. Set workflow version to `1.0`.
5. Clear the research failure reason.
6. Run `Invigorate OS — ICP & Signal Research Agent V1`.

## Agent outputs

Configure structured data outputs:

- `icp_score` — number
- `signal_score` — number
- `icp_classification` — enumeration
- `primary_signal` — text
- `qualification_reasoning` — text
- `research_confidence` — number

The agent must not write CRM properties. Subsequent workflow actions map outputs to the corresponding company properties.

## Action outcome

Branch immediately on Run-agent action success.

### Failure path

1. Set research status to `Failed`.
2. Set account priority to `Review`.
3. Set qualification reasoning to `AI research unavailable — manual review required.`
4. Set failure reason to `Agent run failed or returned no usable output. Manual review required.`
5. Set completed date to the current time.
6. Set research requested to No.
7. Create a manual-review task if supported.

### Success path

1. Copy all six structured outputs to their company properties.
2. Add only the minimum delay demonstrated necessary by testing.
3. Evaluate branches in the following order.

| Order | Condition | Priority | Status |
|---:|---|---|---|
| 1 | confidence missing, score missing, or confidence <60 | Review | Pending review |
| 2 | confidence ≥60, ICP ≥70, signal ≥65 | Prioritise | Complete |
| 3 | confidence ≥60, ICP ≥70, signal <65 | Monitor | Complete |
| 4 | confidence ≥60, ICP 50–69 | Review | Pending review |
| 5 | confidence ≥60, ICP <50 | Exclude | Complete |

### None-met path

1. Set priority to `Review`.
2. Set status to `Pending review`.
3. Set failure reason to `Unexpected branch output — manual review required.`
4. Create a manual-review task if supported.

## Close every path

- Set completed date to the current time.
- Set research requested to No.

## Rerun safety

- A rerun begins only when requested changes from No to Yes.
- Initial actions overwrite versions and clear the prior failure reason.
- Success overwrites all six agent-output properties.
- Failure overwrites status, priority, reasoning and failure reason.
- Every path resets requested to No.
- The workflow remains inactive until the single-record test passes.
