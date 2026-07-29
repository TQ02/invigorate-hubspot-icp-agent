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

**Decision:** Complete all repository, property, test-data and documentation work through supported connectors, then consolidate Agent Builder and `Run agent` configuration into one manual HubSpot UI checklist.

**Reason:** The connected MCP does not expose agent creation, agent publication, structured Run-agent outputs or agent run history. Attempting unsupported workflow representations would be less safe than an explicit UI handoff.
