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

Phase 0 preflight complete. The correct developer-test portal, GitHub write access and Notion write access are verified. Safe repository and CRM-property work can continue.

Agent execution is blocked pending one AI Settings toggle, and Agent Builder plus `Run agent` configuration are UI-only with the currently connected MCP. See `docs/00-phase-0-preflight.md`.

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
