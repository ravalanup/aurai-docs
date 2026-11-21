# ADR 0003: LangGraph as the primary agent framework

**Status:** Accepted
**Date:** 2026-11-19

## Context
Agent frameworks overlap. Production agents need durable state, checkpoints, human approval steps and model neutrality.

## Decision
LangGraph is the default for production agents. n8n serves business-user workflows. Claude Agent SDK and CrewAI are maintained as reference implementations for specific patterns (MCP-heavy operational agents; role-based crews).

## Consequences
- One well-supported path for engineers, clear templates and testing patterns.
- Reference agents show breadth without multiplying production obligations.
- A team needing a different framework must justify it in a new ADR.
