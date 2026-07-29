# HubSpot Academy Production Audit Evidence

## 1. Workflow overview

The company workflow runs a read-only research agent with the explicitly attached `Invigorate OS — ICP & Signal Rules V1` knowledge vault, maps six structured outputs to company properties, and uses ordered deterministic branches to assign Prioritise, Monitor, Review, or Exclude. GitHub remains canonical, but its files are not assumed to be directly available to the agent.

## 2. Monitoring

Monthly review covers five recent runs, every failure and Pending review record, knowledge-vault attachment and rule versions, source quality, confidence, blank outputs, branch distribution, execution time and credit estimates.

## 3. Recovery

Failures and malformed results route to Review, stamp completion, reset the request and optionally create a task. Recovery verifies both vault files, simulates the repaired structure, then uses a real single controlled enrollment before regression.

## 4. Governance

GitHub controls versions and technical truth. Approved rule files must be explicitly transferred into the named HubSpot knowledge vault, attached to the agent, and verified. The agent cannot write CRM. Workflow writes and routing are inspectable. Material changes require change logging and regression.

## 5. Audit findings

Phase 0 found two genuine control gaps: Files data is disabled, and Agent Builder plus Run-agent configuration are not exposed through MCP. The current-behaviour review added two further controls: GitHub files are not agent knowledge until uploaded and attached through a vault, and HubSpot's workflow Test feature is simulation-only with no executed actions.

## This-week improvement

The build added explicit knowledge provenance and separated inactive simulation from real runtime evidence. The real Case 1 procedure turns on the restricted workflow with no-existing-record enrollment, then deliberately changes only the test record from No to Yes. This reduces false assurance from simulated paths and prevents accidental bulk enrollment.

Evidence remains provisional until the agent, workflow and five-company regression are directly verified.

## Official current-behaviour references

- Knowledge vault creation and agent attachment: https://knowledge.hubspot.com/ai/manage-breeze-context-with-knowledge-vaults
- Workflow Test simulation and no-action behaviour: https://knowledge.hubspot.com/workflows/test-your-workflow
- Safe activation without enrolling existing records: https://knowledge.hubspot.com/workflows/create-workflows
