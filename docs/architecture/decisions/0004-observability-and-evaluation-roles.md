# ADR 0004: Separate roles for Langfuse, Phoenix and Promptfoo

**Status:** Accepted
**Date:** 2026-11-19

## Context
Several tools can trace and evaluate LLM applications. Without clear roles they duplicate effort.

## Decision
- OpenTelemetry collector is the single trace pipeline.
- Langfuse handles production monitoring, prompt management and cost by team.
- Phoenix handles trace exploration and retrieval/eval debugging for developers.
- Promptfoo runs golden-set tests and red-team checks in CI and gates promotion.

## Consequences
- Each tool has a defined job; traces are emitted once and consumed by both viewers.
- Phoenix uses Elastic License 2.0 (source-available); acceptable for self-hosted internal use, to be reviewed if distribution terms change.
- More components to operate than a single-tool approach.
