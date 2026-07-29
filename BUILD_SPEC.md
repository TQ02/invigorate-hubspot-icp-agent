# Build Specification

## Objective

Build, test and document a native HubSpot company research, ICP scoring, signal scoring and deterministic account-prioritisation workflow in the **LeadHubAI - Demo client portal**.

Core flow:

```text
Company marked for research
  → native HubSpot agent researches company
  → agent returns structured ICP, signal and confidence outputs
  → workflow writes outputs to company properties
  → deterministic branches assign Prioritise / Monitor / Review / Exclude
```

The AI interprets evidence. HubSpot controls the operational outcome.

## Scope

### Include

- company research;
- ICP scoring;
- signal scoring;
- confidence;
- structured outputs;
- deterministic routing;
- review and failure paths;
- controlled reruns;
- version properties;
- five-company test;
- GitHub and Notion documentation;
- HubSpot Academy Production Audit evidence.

### Exclude

- contact research;
- contact selection;
- Sales Navigator;
- Apify;
- Clay;
- n8n;
- webhooks or custom-code enrichment;
- sequences;
- email drafting;
- automatic sequence enrolment;
- website intent;
- historical outcome learning;
- production CRM data.

## Safety rules

1. Verify portal name and portal ID before every HubSpot write.
2. Operate only in `LeadHubAI - Demo client portal`.
3. Search before creating assets.
4. Prefix test-only assets and records with `[TEST]`.
5. Never modify non-test records.
6. Never enrol existing companies automatically.
7. Keep the workflow inactive until verified.
8. The agent must not write directly to CRM.
9. Do not publish secrets or private data to this public repository.
10. Verify actual HubSpot results, not only API success.

## Phase 0 — Read-only preflight

Inspect without writing:

- current Codex project and HubSpot MCP availability;
- connected portal name and ID;
- portal subscription/trial and relevant beta availability;
- Agent Builder, Company Research Agent and blank custom agent access;
- company workflows and `Run agent` action;
- structured outputs, branches, Agent Inbox and histories;
- MCP support for properties, records, workflows and agents;
- existing matching properties, workflows, agents and `[TEST]` companies;
- GitHub and Notion write access.

Update `state/build-state.json` with confirmed facts. Continue automatically unless blocked.

## Phase 1 — Repository foundation

Create the full project structure:

```text
config/
docs/
docs/notion/
tests/
tests/results/
evidence/
```

Create:

- `config/icp-rules-v1.md`
- `config/signal-rules-v1.md`
- `config/agent-instructions-v1.md`
- `config/workflow-logic-v1.md`
- `config/hubspot-property-schema.json`
- `docs/01-project-brief.md`
- `docs/02-operational-sop.md`
- `docs/03-property-dictionary.md`
- `docs/04-testing-and-regression.md`
- `docs/05-monitoring-and-recovery.md`
- `docs/06-governance-and-handoff.md`
- `docs/07-production-deployment-checklist.md`
- `docs/08-certificate-audit-evidence.md`
- Notion-ready summaries under `docs/notion/`
- `tests/five-company-test-plan.md`
- `tests/expected-results.csv`
- `evidence/screenshot-checklist.md`

## Phase 2 — ICP scoring V1

Score out of 100:

1. B2B model and offer relevance — 20
2. Annual revenue fit — 20
3. Employee count fit — 15
4. Sales-team size fit — 15
5. CRM and GTM infrastructure need — 20
6. Geography and decision environment — 10

Principles:

- revenue and employee count remain separate;
- bigger is not automatically better;
- best revenue band: approximately €1m–€2m;
- strong secondary revenue band: approximately €2m–€5m;
- best employee band: approximately 20–50;
- strong secondary employee band: approximately 30–100;
- ideal sales-team range: approximately 4–10.

Classification:

- Ideal: 85–100
- Strong: 70–84
- Possible: 50–69
- Weak: 30–49
- Poor: 0–29

Document evidence, missing-data and conflict handling.

## Phase 3 — Signal scoring V1

Score out of 100:

- Relevance: 25
- Personalisation Value: 20
- Strength: 20
- Freshness: 15
- Reliability: 10
- Clustering: 10

Keep each question distinct. Clustering is an uplift, not a requirement.

Signal library:

- funding;
- hiring;
- growth;
- acquisitions;
- leadership changes;
- new markets;
- product launches;
- events;
- company news;
- job postings;
- promotions;
- public posts;
- technology-stack changes.

## Phase 4 — Company properties

Search for equivalents before creation. Preferred prefix: `inv_ai_`.

Agent outputs:

1. AI ICP score — number
2. AI signal score — number
3. AI ICP classification — dropdown: Ideal, Strong, Possible, Weak, Poor
4. AI primary signal — multi-line text
5. AI qualification reasoning — multi-line text
6. AI research confidence — number

Workflow control:

7. AI account priority — dropdown: Prioritise, Monitor, Review, Exclude
8. AI research status — dropdown: Not requested, Queued, Researching, Complete, Pending review, Failed
9. AI research requested — checkbox
10. AI research completed date — datetime
11. AI agent version — text
12. AI rules version — text
13. AI workflow version — text
14. AI research failure reason — multi-line text

Document final internal names and types.

## Phase 5 — Agent

Name: `Invigorate OS — ICP & Signal Research Agent V1`

Allowed:

- read company CRM data;
- browse permitted public information.

Not allowed:

- direct CRM writes.

Structured outputs:

- `icp_score` — number 0–100
- `signal_score` — number 0–100
- `icp_classification` — Ideal / Strong / Possible / Weak / Poor
- `primary_signal` — concise text or `No meaningful current signal found.`
- `qualification_reasoning` — concise evidence-based explanation
- `research_confidence` — number 0–100

Rules:

- keep fit separate from timing;
- do not invent facts;
- distinguish facts from inference;
- prefer recent reliable sources;
- lower confidence for missing or conflicting evidence;
- do not return final priority;
- do not write to CRM.

If Agent Builder is not automatable, create exact paste-ready configuration and one consolidated manual checklist.

## Phase 6 — Workflow

Name: `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1`

Object: Company

Enrollment:

- AI research requested = Yes
- company domain is known
- controlled re-enrollment when requested changes to Yes
- do not enroll existing records at activation

Initial actions:

- status = Researching
- agent version = 1.0
- rules version = 1.0
- workflow version = 1.0
- clear failure reason

Run agent, capture six outputs and branch immediately on action success.

Failure path:

- status = Failed
- priority = Review
- fallback reasoning = `AI research unavailable — manual review required.`
- failure reason = `Agent run failed or returned no usable output. Manual review required.`
- completed date = now
- requested = No
- create review task if supported

Success path:

- map all six outputs to properties;
- add only the minimum delay needed for reliable downstream branching;
- branch deterministically.

Branch order:

1. Review: confidence <60 or missing score/confidence
2. Prioritise: confidence ≥60, ICP ≥70, signal ≥65
3. Monitor: confidence ≥60, ICP ≥70, signal <65
4. Review: confidence ≥60, ICP 50–69
5. Exclude: confidence ≥60, ICP <50

None-met path:

- priority = Review
- status = Pending review
- failure reason = unexpected branch output
- create review task if supported

Close every path:

- completed date = now
- requested = No

## Phase 7 — Five-company regression

Use five controlled `[TEST]` company records with valid public domains where possible:

1. Ideal ICP + strong signal → Prioritise
2. Ideal ICP + no meaningful signal → Monitor
3. Moderate fit + strong signal → Review
4. Poor fit → Exclude
5. Incomplete/conflicting evidence → Review / Pending review

Document expected results before running. Run one record first, verify end to end, then run the other four. Confirm no non-test record changed and reruns are safe.

## Phase 8 — Documentation and Notion

GitHub remains canonical. Create concise Notion pages:

- System Overview
- One-Page Operating SOP
- Monitoring and Regression Summary
- Change Requests and Known Issues
- Production Audit Evidence
- Production Deployment Status

Every Notion page must link back to GitHub and show owner, versions and last review date.

## Phase 9 — Production Audit

Prepare evidence-based answers for:

1. Workflow overview
2. Monitoring
3. Recovery
4. Governance
5. Audit findings

Include a genuine this-week improvement. Do not fabricate capabilities or results.

## Phase 10 — Ongoing operation

Monthly:

- review five recent runs;
- review every failure and Pending review record;
- inspect source quality, confidence, blank properties, branch distribution and versions.

Quarterly:

- review ICP assumptions, signal weights, thresholds, ownership, documentation and deployment readiness.

Run the five-company regression after any material change to prompts, rules, tools, properties, thresholds or workflow logic.

## Completion criteria

Do not mark complete until:

- portal verified;
- properties created/reused;
- agent published;
- workflow configured and safely activated;
- five tests completed and documented;
- no non-test record changed;
- rerun safety verified;
- GitHub documentation complete;
- Notion operating pages complete;
- SOP, monitoring, recovery, governance and audit evidence complete;
- known gaps disclosed;
- version state aligned.

## Blocker behaviour

Complete every automatable step first. For unsupported HubSpot UI steps, return one consolidated manual checklist with exact clicks and paste-ready values, then resume after confirmation.
