# Phase 0 Preflight

Date: 2026-07-29

## Acceptance boundary

This report is sanitized for a public repository. The target HubSpot portal ID was verified against the connected runtime but is intentionally redacted here. No credentials, CRM record IDs, private data, or screenshots are included.

## Verified environment

- Codex execution project: `hubspot-leadhub-mcp`
- Canonical repository: `TQ02/invigorate-hubspot-icp-agent`
- Connected portal name: `LeadHubAI - Demo client portal`
- Connected portal ID: verified against the expected ID; redacted from public files
- Account type: HubSpot developer test account
- Seats visible to the connected user: developer, core, Sales Hub Enterprise trial, and Service Hub Enterprise trial
- Company CRM access: read and write available
- GitHub write access: verified
- Notion workspace connection and page-creation access: verified

## Existing matching assets

- Preferred `inv_ai_` company properties: none found
- Exact target workflow: none found
- Exact target agent: none found
- Clearly labelled `[TEST]` companies: none found

Existing unrelated properties and workflows were not selected for reuse because their semantics do not match the required V1 system.

## Initial agent and workflow capability findings

- Agent Hub Beta is accessible.
- Agent Inbox is accessible.
- The HubSpot Company Research Agent template is visible.
- Blank custom agent creation is currently disabled in the portal UI.
- The Agents page initially reported that `Files data` had to be enabled in AI Settings before agents could be used.
- Generative AI access, CRM data access, customer conversation access, and Breeze Assistant access are enabled.
- `Files data` was disabled at initial preflight.
- The HubSpot MCP initially exposed CRM, property, record and guarded workflow operations, but no dedicated Agent Builder or Run-agent helper.
- Structured workflow outputs were documented by HubSpot but had not yet been verified in this portal.

## Current capability reassessment

- Files data is enabled.
- `Invigorate OS — ICP & Signal Rules V1` exists, contains both approved Markdown files, and is attached to the published agent.
- The published agent and all six structured outputs were verified in the HubSpot editor.
- A portal-created Run-agent card and output mapping were read through the workflow API to learn HubSpot's accepted native representation.
- The local MCP now has a narrowly scoped finalizer for the exact inactive Invigorate workflow. It validates the portal, workflow name, company object type, inactive state, revision, sole enrollment event, domain refinement, approved agent/input, six output mappings, branch order, close-out paths and failure task before one PUT and again after readback.
- The complete workflow was finalized and independently read back while inactive.

## Limits and subscription observations

- No account credit balance or per-run estimate was visible in the read-only preflight.
- HubSpot states that agent runs consume HubSpot Credits from 2026-07-23 and that run limits can be set in Agent Builder.
- HubSpot's current `Run agent` workflow documentation describes a beta execution limit of 500 runs per day.
- Actual credit cost and the configured monthly run limit must be checked when the agent is created.

Official references:

- https://knowledge.hubspot.com/ai/install-agents-from-the-agent-marketplace
- https://knowledge.hubspot.com/ai/review-estimated-credit-costs-when-using-agents
- https://knowledge.hubspot.com/workflows/run-agents-using-workflows

## Supported MCP operations

Available and relevant:

- verify connected portal ID;
- search and read CRM properties;
- create company properties;
- search, create, and update test CRM records;
- list and read workflows;
- create or clone limited disabled workflow structures from existing templates;
- create test tasks;
- reset supported demo scenarios.

Still unsupported through MCP:

- create or configure an Agent Builder agent;
- install the Company Research Agent;
- publish an agent;
- inspect agent run history through MCP.

Now supported for this exact inactive workflow:

- preserve and select the accepted Run-agent action;
- map the enrolled-company domain into the approved input;
- reference all six structured outputs in property actions;
- finalize deterministic and failure routing;
- stamp execution time, reset the request and create the failure-review task;
- read back and validate the complete definition.

## Phase 0 conclusion

The portal is correct. The knowledge vault, published agent and complete inactive workflow are configured. Runtime evidence remains intentionally pending: first run the inactive simulation, then use the controlled Case 1 activation procedure. No Case 1 run has begun.
