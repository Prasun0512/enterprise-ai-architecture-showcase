# System Design: Multi-Agent Workflow Platform

## Agent Roles

- Planner Agent: decomposes the task.
- Research Agent: gathers approved context.
- Retrieval Agent: retrieves grounded evidence.
- Validator Agent: checks policy, confidence, and schema.
- Execution Agent: performs approved actions.

## Sequence

```mermaid
sequenceDiagram
  participant User
  participant Planner
  participant Research
  participant Retrieval
  participant Validator
  participant Human
  participant Executor

  User->>Planner: Request
  Planner->>Research: Plan steps
  Research->>Retrieval: Need evidence
  Retrieval->>Validator: Context + citations
  Validator->>Human: Approval if needed
  Human->>Executor: Approve action
  Executor-->>User: Result + audit trace
```

## Operational Strategy

- Persist state between nodes.
- Emit audit event per node.
- Apply tool allowlists per agent.
- Set retry and cost budgets per workflow.
