# Governance and Handoff

## Change control

- GitHub is the canonical source for instructions, rules, schemas, tests and decisions.
- GitHub rule files are not automatically available to HubSpot agents. Approved rule updates must be downloaded, uploaded to the named knowledge vault, attached, verified, version-recorded, and regression-tested.
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
- `Invigorate OS — ICP & Signal Rules V1` contains both approved Markdown rule files and is attached to the agent.
- Agent access to both rule documents verified before publication.
- Property mappings reviewed.
- Inactive workflow simulation completed and understood not to execute actions.
- Real Case 1 activation uses no-existing-record enrollment and the sole deliberate request route.
- Monitoring owner and cadence agreed.
- Recovery owner and steps agreed.
- Known limitations accepted.
- Production deployment checklist signed.
