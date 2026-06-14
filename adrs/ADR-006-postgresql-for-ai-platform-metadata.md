# ADR-006: PostgreSQL for AI Platform Metadata

## Status

Accepted as default metadata store

## Context

AI platforms need durable metadata for documents, chunks, prompts, evaluations,
workflow runs, review decisions, and audit records.

## Decision

Use PostgreSQL as the default relational metadata store. Use pgvector when a
portable vector backend is sufficient, while keeping search/vector abstractions
for managed search platforms.

## Tradeoffs Considered

- PostgreSQL: strong transactional metadata and operational familiarity.
- NoSQL stores: flexible schema but weaker relational audit queries.
- Managed vector stores: strong retrieval operations but not a full metadata system.

## Consequences

- Enables consistent audit and reporting queries.
- Supports local development and enterprise deployment.
- Requires schema governance and migration discipline.
