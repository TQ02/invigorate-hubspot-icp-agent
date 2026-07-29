# HubSpot Academy Production Audit Evidence

## 1. Workflow overview

The company workflow runs a read-only research agent, maps six structured outputs to company properties, and uses ordered deterministic branches to assign Prioritise, Monitor, Review, or Exclude.

## 2. Monitoring

Monthly review covers five recent runs, every failure and Pending review record, source quality, confidence, blank outputs, branch distribution, versions, execution time and credit estimates.

## 3. Recovery

Failures and malformed results route to Review, stamp completion, reset the request and optionally create a task. Recovery uses a single controlled record before regression.

## 4. Governance

GitHub controls versions and technical truth. The agent cannot write CRM. Workflow writes and routing are inspectable. Material changes require change logging and regression.

## 5. Audit findings

Phase 0 found two genuine control gaps: Files data is disabled, and Agent Builder plus Run-agent configuration are not exposed through MCP.

## This-week improvement

The build added an explicit low-confidence/missing-value branch before commercial routing and a request-reset requirement on every close-out path. This reduces silent misrouting and makes reruns controlled.

Evidence remains provisional until the agent, workflow and five-company regression are directly verified.
