# ADR 0005: Qdrant with entitlement filters for retrieval

**Status:** Accepted
**Date:** 2026-11-19

## Context
Retrieval must not expose documents a user is not entitled to see. A vector store must support filtered search efficiently and scale separately from transactional data.

## Decision
Use Qdrant. Each chunk carries entitlement metadata (collection, team, classification). Queries always apply a filter derived from the caller's identity. The workspace UI does not run its own retrieval; it calls the knowledge service.

## Consequences
- A single, testable enforcement point for document access.
- Ingestion must attach correct metadata; missing metadata means the chunk is not retrievable.
- Retrieval quality and filter correctness are covered by evals.
