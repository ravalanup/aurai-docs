# Roadmap

The roadmap follows the platform build order. Each phase ends with something a team can use.

## Phase 0: Foundation
**Outcome:** the platform can be deployed reproducibly and every request is traceable.
- Product documentation and decisions (`aurai-docs`)
- Helm charts, Terraform for AWS, CI templates (`aurai-infra`)
- Tracing and risk-tier rubric (`aurai-eval-governance`, part 1)

## Phase 1: Core access
**Outcome:** employees can use approved models safely, with spend under control.
- AI gateway with team keys, budgets, fallback, PII masking (`aurai-gateway`)
- Workspace with SSO and roles (`aurai-workspace`)

## Phase 2: Grounded answers
**Outcome:** answers come from company knowledge, and respect who may see what.
- Ingestion, Qdrant retrieval, permission filters, citations (`aurai-knowledge-rag`)

## Phase 3: Action
**Outcome:** agents and workflows can act on systems, with the right approvals.
- First MCP connector with policy checks (`aurai-mcp-connectors`)
- LangGraph production agents with approval gates; n8n workflows; Claude Agent SDK and CrewAI reference agents (`aurai-agent-runtime`)

## Phase 4: Quality and trust
**Outcome:** promotion from pilot to production depends on evidence.
- Golden test sets, model-graded checks, red-team tests, promotion gates (`aurai-eval-governance`, part 2). Built; no live evaluation has been run yet
- Production monitoring in Langfuse and Phoenix. Tracing is built; live quality, cost and drift scoring (EV-4) and scheduled red-team runs (EV-5) are not

## Phase 5: Scale and adoption
**Outcome:** broad rollout with reporting to leadership.
- Pilot and rollout plan executed ([pilot and rollout](pilot-and-rollout.md))
- Additional connectors, regional routing, sandboxed tool execution

## Now / Next / Later

| Now | Next | Later |
|---|---|---|
| Docs, infra, gateway | Workspace, knowledge, first connector | Agents at scale, regional routing, sandboxed tools |

## Sequencing rules
- Tracing exists before any feature sends traffic.
- Nothing reaches the next risk tier without passing its eval gate.
- A capability is "done" when a pilot team could use it, not when code is merged.
