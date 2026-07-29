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

## Agent and workflow capability findings

- Agent Hub Beta is accessible.
- Agent Inbox is accessible.
- The HubSpot Company Research Agent template is visible.
- Blank custom agent creation is currently disabled in the portal UI.
- The Agents page reports that `Files data` must be enabled in AI Settings before agents can be used.
- Generative AI access, CRM data access, customer conversation access, and Breeze Assistant access are enabled.
- `Files data` is disabled.
- The HubSpot MCP exposes CRM, property, record, and guarded workflow operations, but no Agent Builder or Run-agent configuration operation.
- Structured workflow outputs are documented by HubSpot for the `Run agent` action, but could not be safely verified in the portal editor without beginning a UI-only configuration.

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

Unsupported for this build:

- create or configure an Agent Builder agent;
- install the Company Research Agent;
- configure a workflow `Run agent` action;
- configure structured Run-agent outputs;
- publish an agent;
- inspect agent run history through MCP.

## Phase 0 conclusion

The portal is correct and safe repository, CRM-property, and test-record work can continue. Agent execution is blocked until `Files data` is enabled, and agent plus Run-agent configuration require consolidated manual HubSpot UI steps after all automatable work is complete.
