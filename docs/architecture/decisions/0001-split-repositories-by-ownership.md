# ADR 0001: Split repositories by ownership and security boundary

**Status:** Accepted
**Date:** 2026-11-19

## Context
Aurai spans infrastructure, a gateway on every request, end-user interfaces, agent execution, data pipelines and governance. These have different owners, release cadences and review needs.

## Decision
Use eight repositories (documentation plus seven platform repositories), split where owner, cadence or security boundary differ. Business use-case applications live in their own repositories.

## Consequences
- Clear ownership and independent releases.
- Stricter review where blast radius is high (infrastructure, gateway, connectors).
- More coordination: cross-repo changes need linked pull requests; `aurai-docs` tracks the map.
