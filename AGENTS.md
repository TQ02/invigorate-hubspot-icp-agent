# AGENTS.md

## Purpose

Build, test and document the Invigorate OS native HubSpot ICP and signal-prioritisation workflow described in `BUILD_SPEC.md`.

## Execution environment

Remain in the Codex project `hubspot-leadhub-mcp` when HubSpot MCP access is required.

Canonical documentation repository:
`TQ02/invigorate-hubspot-icp-agent`

Target HubSpot portal:
`LeadHubAI - Demo client portal`

## Source-of-truth model

- GitHub: canonical technical source
- HubSpot: deployed runtime state
- Notion: human-facing operating layer

## Before every HubSpot write

1. Confirm portal name and portal ID.
2. Confirm the asset or record is test-only.
3. Search for an existing equivalent.
4. Avoid duplicates.
5. Verify that no non-test record can be affected.

## Required behaviour

- Follow `BUILD_SPEC.md` end to end.
- Update `state/build-state.json` after every phase.
- Prefix test-only HubSpot records and assets with `[TEST]`.
- Never modify non-test CRM data.
- Never enrol existing records automatically.
- The agent may read CRM data and browse approved public sources.
- The agent must not write directly to CRM.
- HubSpot workflow actions must perform CRM writes.
- Verify business outcomes, not only successful API responses.
- Update `CHANGELOG.md` after material changes.
- Update `DECISIONS.md` after architectural decisions.
- Run regression tests after material changes.

## Public-repository safety

Never commit:
- tokens, keys or credentials;
- `.env` files;
- private CRM data;
- real customer exports;
- confidential portal details;
- unsanitised screenshots;
- unnecessary HubSpot record IDs.

## Autonomy

Continue automatically through safe test-portal work.

Stop only for:
- authentication failure;
- incorrect portal;
- unavailable subscription feature;
- unsupported Agent Builder or Run agent action;
- risk to non-test data;
- destructive action;
- a decision that cannot be discovered.

When blocked, complete all other supported work and return one consolidated manual checklist.
