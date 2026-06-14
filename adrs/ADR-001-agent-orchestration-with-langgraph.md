# ADR-001: Agent Orchestration With Graph-Based State Machines

## Status

Accepted

## Context

Enterprise AI agents need controlled execution, not open-ended prompt loops.
Production workflows require state, retries, human approval, audit events, and
tool policies. A graph-based workflow makes routing explicit and reviewable.

## Decision

Use a graph-based orchestration model for agentic workflows. LangGraph is the
preferred implementation when runtime dependencies are available. A deterministic
local graph runner can be used for demos and offline tests.

## Consequences

- Workflow state becomes explicit and testable.
- Human approval gates are modeled as first-class nodes.
- Tool access can be constrained per node.
- The system is easier to observe and reason about than a single agent loop.

## Trade-Offs

- More upfront design than a simple prompt chain.
- Requires careful state schema ownership.
- Adds orchestration complexity, but improves production control.
