# Build status

Aurai is a prototype with production patterns, built in the order below. Every repository has its own README with a
"Verified / Not verified / What production would add" section; this page summarizes what differs from the plan.

| Repository | State | Notes |
|---|---|---|
| `aurai-docs` | Built | This repository |
| `aurai-infra` | Built (prototype) | Local-cluster and AWS foundations; see its README for what was and was not applied |
| `aurai-gateway` | Built (prototype) | LiteLLM configuration, PII guardrail, teams and model catalog |
| `aurai-eval-governance` | Built (prototype) | Tracing, risk tiers, evaluation suites and promotion gates |
| `aurai-workspace` | Built (prototype) | Open WebUI configuration and Keycloak realm |
| `aurai-knowledge-rag` | Built (prototype) | Ingestion, Qdrant retrieval with entitlement filters, citations, golden set |
| `aurai-mcp-connectors` | Built (prototype) | MCP servers with policy checks over synthetic data |
| `aurai-agent-runtime` | Built (prototype) | LangGraph agent, approval service, template, n8n and Claude Agent SDK examples |

## Differences from the plan

- **CrewAI** is in the stack and architecture documents but no CrewAI reference agent was built.
- **Approvals** are a separate service with an API and signed tokens. There is no approval screen yet.
- **Evaluation** is built and tested but has never been run against a live gateway or model, so no use case claims
  `passing` for golden-set or red-team evaluation. Live quality, cost and drift monitoring (EV-4) and scheduled red-team
  runs (EV-5) are not built.
- **Use cases registered** in `aurai-eval-governance`: ops-insights (pilot), internal-help and knowledge-search (sandbox).

## Evaluation requirements

| Requirement | Priority | State |
|---|---|---|
| EV-1 Tracing for every model, retrieval and tool call | P0 | Conventions and collectors built; not verified against a live gateway |
| EV-2 Risk-tier assignment | P0 | Built (rubric and policy checks in CI) |
| EV-3 Test suites gate promotion | P0 | Built and tested with synthetic evidence; waiting on live runs |
| EV-4 Quality, cost and drift monitoring | P1 | Not built |
| EV-5 Red-team tests for higher tiers | P1 | Suite built for ops-insights; not run live; no scheduled runs |
| EV-6 Pause a use case | P1 | Built; not exercised against a live gateway |

## What nobody has verified

Several pieces were written without access to a running cluster, gateway, identity provider or model: Helm and Terraform
applies, real Keycloak and LiteLLM behavior, live model output and judge agreement, and PII detection on a real gateway.
Each repository lists its own gaps. Treat this platform as a design and a tested prototype, not a deployment.
