# Property Dictionary

The exact machine-readable schema is in `config/hubspot-property-schema.json`.

| Internal name | Type | Writer | Purpose |
|---|---|---|---|
| `inv_ai_icp_score` | Number | Workflow | Structural fit, 0–100 |
| `inv_ai_signal_score` | Number | Workflow | Current signal, 0–100 |
| `inv_ai_icp_classification` | Dropdown | Workflow | Ideal, Strong, Possible, Weak, Poor |
| `inv_ai_primary_signal` | Multi-line text | Workflow | Primary current signal |
| `inv_ai_qualification_reasoning` | Multi-line text | Workflow | Evidence-based explanation |
| `inv_ai_research_confidence` | Number | Workflow | Research confidence, 0–100 |
| `inv_ai_account_priority` | Dropdown | Workflow | Prioritise, Monitor, Review, Exclude |
| `inv_ai_research_status` | Dropdown | Workflow | Request and execution state |
| `inv_ai_research_requested` | Checkbox | Human/system | Controlled enrollment and rerun |
| `inv_ai_research_completed_date` | Datetime | Workflow | Completion time |
| `inv_ai_agent_version` | Text | Workflow | Agent version |
| `inv_ai_rules_version` | Text | Workflow | Rules version |
| `inv_ai_workflow_version` | Text | Workflow | Workflow version |
| `inv_ai_research_failure_reason` | Multi-line text | Workflow | Failure and fallback detail |

The agent writes none of these fields directly.
