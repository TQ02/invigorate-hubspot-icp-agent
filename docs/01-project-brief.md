# Project Brief

## Outcome

Create a native HubSpot company-research system that interprets evidence with AI and assigns operational priority through deterministic workflow logic.

## Flow

`Research requested → agent research → six structured outputs → workflow property writes → deterministic priority`

## Boundaries

- Company-only V1.
- No contact selection, sequences, email drafting, external enrichment, webhooks, or custom code.
- The agent reads CRM and public sources but never writes CRM.
- HubSpot workflow actions perform every property write and final routing decision.
- Testing uses only clearly labelled `[TEST]` companies.

## Ownership

- Owner: Thomas Quinn
- GitHub: canonical technical source
- HubSpot: runtime
- Notion: operating documentation

## Versions

- Agent: 1.0
- ICP rules: 1.0
- Signal rules: 1.0
- Workflow: 1.0
