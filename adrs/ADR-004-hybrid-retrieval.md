# ADR-004: Hybrid Retrieval for Enterprise Knowledge

## Status

Accepted

## Context

Enterprise documents contain exact identifiers, policy names, case numbers, and
domain-specific language. Pure vector search can miss exact matches, while pure
keyword search can miss semantic matches.

## Decision

Use hybrid retrieval combining keyword/BM25, vector similarity, metadata
filters, and optional reranking.

## Tradeoffs Considered

- Pure vector retrieval: strong semantic matching, weaker exact identifier handling.
- Pure keyword retrieval: reliable exact matching, weaker semantic matching.
- Hybrid retrieval: more moving parts, but better enterprise recall and trust.

## Consequences

- Retrieval quality can be tuned by query type.
- Evaluation must track recall@k and precision@k across both semantic and exact-match queries.
- Reranking should be measured, not assumed to improve quality.
