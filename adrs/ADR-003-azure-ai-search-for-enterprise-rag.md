# ADR-003: Azure AI Search for Enterprise RAG

## Status

Accepted as a reference architecture option

## Context

Enterprise RAG systems often require keyword search, vector search, metadata
filters, access-control filters, and operational integration with Azure-native
services.

## Decision

Use Azure AI Search as the preferred managed search layer for Azure-first RAG
platforms. Keep a vector-store abstraction so PostgreSQL/pgvector, FAISS, or
other backends can be used for portability and cost-sensitive environments.

## Tradeoffs Considered

- Azure AI Search: strong managed operations, hybrid retrieval, filters.
- PostgreSQL/pgvector: simpler local operations and transactional metadata.
- FAISS: fast local experiments but requires more production plumbing.

## Consequences

- Faster enterprise integration in Azure environments.
- Better support for metadata filtering and operational monitoring.
- Requires cost management for index size, replicas, and query volume.
