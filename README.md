# Invigorate HubSpot ICP Agent

Native HubSpot AI agent, workflow, testing and production-audit documentation for Invigorate OS.

## Purpose

This repository is the canonical technical source of truth for a native HubSpot company research, ICP scoring, signal scoring and deterministic account-prioritisation workflow.

The workflow will be built and tested in the **LeadHubAI - Demo client portal** using controlled test records.

## Architecture

- **Codex project:** `hubspot-leadhub-mcp` — execution environment and HubSpot MCP runtime
- **GitHub:** this repository — canonical technical documentation, rules, tests and change history
- **HubSpot:** deployed agent, workflow, properties and runtime results
- **Notion:** human-facing SOP, monitoring summary and audit workspace

## Current status

Phases 0–4 are complete. The correct developer-test portal and integrations are verified, the V1 scoring contracts are canonical, and all fourteen test-labelled HubSpot company properties exist with verified types and options.

Five controlled test companies and all six Notion operating pages are prepared and verified. Agent execution is blocked pending Files data, creation and attachment of `Invigorate OS — ICP & Signal Rules V1`, and the UI-only Agent Builder plus `Run agent` configuration. GitHub rule files are canonical but are not automatically available to the HubSpot agent.

Complete `docs/09-consolidated-hubspot-ui-checklist.md`: first verify the inactive simulation, then activate only the restricted test workflow with no-existing-record enrollment and deliberately request Case 1. HubSpot's Test feature does not execute the agent or write properties.

## Current versions

- Agent: `1.0`
- ICP rules: `1.0`
- Signal rules: `1.0`
- Workflow: `1.0`

## Start here

1. Read `AGENTS.md`.
2. Execute `BUILD_SPEC.md` from the `hubspot-leadhub-mcp` Codex project.
3. Resume from `state/build-state.json` after any interruption.

## Owner

Thomas Quinn

## Security

This repository is public. Never commit credentials, tokens, private CRM data, confidential portal information, unsanitised screenshots or customer exports. See `SECURITY.md`.
