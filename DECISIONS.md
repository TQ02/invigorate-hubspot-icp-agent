# Decision Log

## D-001 — Separate ICP fit from current signals

**Decision:** Score structural ICP fit and current timing/signals separately.

**Reason:** A strong signal does not make a poor-fit company suitable, and a strong-fit company without a current signal may still deserve monitoring.

## D-002 — Deterministic final priority

**Decision:** The agent interprets evidence; HubSpot workflow logic assigns Prioritise, Monitor, Review or Exclude.

**Reason:** Operational routing should remain inspectable and reproducible.

## D-003 — No direct agent CRM writes

**Decision:** The agent may read and research but must not write directly to CRM records.

**Reason:** Workflow-controlled writes are easier to monitor, recover and audit.

## D-004 — Company-only V1

**Decision:** V1 excludes contacts, sequences, email drafting and external enrichment.

**Reason:** Prove the core fit-and-timing logic quickly before adding complexity.

## D-005 — Three-layer documentation model

**Decision:** GitHub is canonical, HubSpot is runtime, Notion is the operating layer.

**Reason:** Avoid duplicated technical truth while keeping the system usable by humans.

## D-006 — MCP-first build with a consolidated UI handoff

**Decision:** Complete all repository, property, test-data and documentation work through supported connectors, then consolidate genuinely unavailable Agent Builder steps into one manual HubSpot UI checklist.

**Reason:** Agent Builder remains a UI surface, but the later capability review demonstrated that a published agent's accepted Run-agent action, structured outputs and output references can be learned from HubSpot readback and finalized through a narrowly guarded MCP extension.

## D-007 — Extend the connector's generic property contract

**Decision:** Expand the local guarded `create_property` MCP schema to accept HubSpot number, datetime, text, number-field and date-field property definitions.

**Reason:** The API client was already generic, but its exposed tool contract allowed only boolean, enumeration and textarea definitions. The approved V1 schema could not otherwise be created through the guarded MCP. The change affects only schema compatibility; portal checks, duplicate handling and readback verification remain in force.

## D-008 — Preserve the native Run-agent representation and fail closed

**Decision:** Preserve the portal-created Run-agent action and its structured-output definition, map the company domain into the single approved input, and route a usable numeric ICP output to deterministic processing while sending missing or unusable output to the failure path.

**Reason:** HubSpot's public workflow API accepts the native Run-agent action and downstream `FIELD_DATA` references but does not expose every editor-only output-definition detail in the workflow readback. Preserving the accepted action identity avoids reconstructing hidden editor state, while the exact-name, inactive-state, portal, revision, enrollment and graph validators prevent broader workflow mutation.
