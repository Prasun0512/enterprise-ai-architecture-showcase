# ADR-005: Event-Driven Architecture for AI Automation

## Status

Accepted

## Context

Email-to-case, document extraction, and workflow automation systems involve
bursting workloads, external APIs, retries, and occasional human review.

## Decision

Use event-driven architecture for ingestion and processing. Queue events between
ingestion, OCR, extraction, validation, review, and downstream writes.

## Tradeoffs Considered

- Synchronous API processing: simpler but fragile for long-running extraction.
- Batch processing: efficient for backlogs but weak for near-real-time workflows.
- Event-driven processing: operationally stronger for retries, DLQ, and scale.

## Consequences

- Adds queue and retry design complexity.
- Improves resilience and observability.
- Supports human approval pauses without blocking ingestion.
