# Governance and Handoff

## Change control

- GitHub is the canonical source for instructions, rules, schemas, tests and decisions.
- Every material change updates `CHANGELOG.md`, `DECISIONS.md` when architectural, and `state/build-state.json`.
- Versions must be incremented intentionally and stamped on every run.
- Material changes require the five-company regression before deployment.

## Access

- Agent tools are limited to CRM read and permitted public web browsing.
- Direct agent CRM writes are prohibited.
- Workflow activation, AI settings and credit limits require an authorized HubSpot operator.
- Public evidence must be sanitized.

## Handoff checklist

- Owner named.
- Portal verified.
- Agent instructions and tools reviewed.
- Property mappings reviewed.
- Workflow inactive until validation passes.
- Monitoring owner and cadence agreed.
- Recovery owner and steps agreed.
- Known limitations accepted.
- Production deployment checklist signed.
