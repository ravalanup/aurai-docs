# ADR 0002: Route all model traffic through a single gateway (LiteLLM)

**Status:** Accepted
**Date:** 2026-11-19

## Context
Teams need many models, but cost control, PII handling, fallbacks and auditing must be consistent.

## Decision
All model calls go through LiteLLM. Teams receive virtual keys with budgets and rate limits. PII masking runs as a gateway guardrail.

## Consequences
- One place to enforce policy, measure spend and swap providers.
- The gateway becomes critical infrastructure and needs high availability and careful change control.
- Teams calling providers directly fall outside governance; adoption reporting must track unmanaged usage.
