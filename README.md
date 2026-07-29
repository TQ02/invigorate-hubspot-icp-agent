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

The published `Invigorate OS — ICP & Signal Research Agent V1` uses the attached `Invigorate OS — ICP & Signal Rules V1` knowledge vault, and access to both approved Markdown rule files has been verified. The inactive company workflow `[TEST] Invigorate OS — AI ICP & Signal Prioritisation V1` is built and read back with its Run-agent action, six structured-output mappings, ordered deterministic branches, close-out actions, failure path and one manual-review task.

Five controlled test companies remain at requested = No with no completion timestamps or scores, and no company is currently queued. The workflow remains OFF. Complete the remaining sections of `docs/09-consolidated-hubspot-ui-checklist.md`: first run the inactive structural simulation, then—only when ready for runtime evidence—activate the restricted test workflow with no-existing-record enrollment and deliberately request Case 1. HubSpot's Test feature does not execute the agent or write properties.

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
