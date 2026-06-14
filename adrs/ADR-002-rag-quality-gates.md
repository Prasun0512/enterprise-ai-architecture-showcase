# ADR-002: RAG Quality Gates Before Answer Delivery

## Status

Accepted

## Context

RAG systems can produce fluent but unsupported answers when retrieval quality is
weak. Enterprise users need citations, measurable retrieval quality, and review
routing for low-confidence answers.

## Decision

Introduce quality gates before final answer delivery:

- recall@k and precision@k for benchmark questions
- citation support checks
- minimum retrieval confidence
- human review for low-confidence or sensitive answers

## Consequences

- Answers become more defensible.
- Quality can be tracked across prompt, chunking, and retrieval changes.
- Sensitive workflows can block unsupported answers before user exposure.
