# Product requirements (PRD)

**Product:** Aurai enterprise AI platform
**Status:** Draft v0.1
**Scope:** Platform capabilities delivered across the `aurai-*` repositories

## 1. Goals
1. Give every team a single, governed entry point to AI models and tooling.
2. Cut the time from approved idea to first working use case.
3. Make AI usage observable: who uses it, what it costs, how well it works.
4. Make risk controls proportional, automatic and auditable.
5. Make building agents and workflows safe enough for non-engineers to try.

## 2. Non-goals
- Training or hosting proprietary foundation models.
- Replacing domain applications or data platforms.
- Fully autonomous agents acting on high-risk systems without human approval.

## 3. Requirements

Priority: **P0** required for first pilot, **P1** required for broad rollout, **P2** later.

### 3.1 AI Gateway
| ID | Requirement | Priority |
|---|---|---|
| GW-1 | Single OpenAI-compatible API to multiple model providers | P0 |
| GW-2 | Per-team virtual keys with budgets and rate limits | P0 |
| GW-3 | Automatic fallback between models/providers | P0 |
| GW-4 | PII masking before requests leave the platform | P0 |
| GW-5 | Usage and cost reporting by team and use case | P1 |
| GW-6 | Regional routing and data-residency controls | P2 |

### 3.2 Workspace
| ID | Requirement | Priority |
|---|---|---|
| WS-1 | Secure chat with approved models, SSO login | P0 |
| WS-2 | Role-based access (member, builder, admin) | P0 |
| WS-3 | Document Q&A with citations from permitted sources | P0 |
| WS-4 | Audit log of usage retained per policy | P1 |
| WS-5 | Content filters aligned to risk tier | P1 |

### 3.3 Knowledge (RAG)
| ID | Requirement | Priority |
|---|---|---|
| KN-1 | Ingestion pipeline for approved document collections | P0 |
| KN-2 | Retrieval that respects user entitlements | P0 |
| KN-3 | Answers include source citations | P0 |
| KN-4 | Freshness tracking and re-ingestion schedule | P1 |
| KN-5 | Retrieval quality evaluation | P1 |

### 3.4 Tools and connectors (MCP)
| ID | Requirement | Priority |
|---|---|---|
| MC-1 | Standard connector pattern using MCP | P0 |
| MC-2 | Policy check (allow/deny) on every tool call | P0 |
| MC-3 | Per-team scoping of connector access | P1 |
| MC-4 | Security review workflow for new connectors | P1 |

### 3.5 Agents and workflows
| ID | Requirement | Priority |
|---|---|---|
| AG-1 | Production agent runtime with state and checkpoints | P0 |
| AG-2 | Human approval gate for consequential actions | P0 |
| AG-3 | Low-code workflow option for business builders | P1 |
| AG-4 | Templates for common agent patterns | P1 |
| AG-5 | Sandboxed tool execution | P2 |

### 3.6 Evals, observability and governance
| ID | Requirement | Priority |
|---|---|---|
| EV-1 | End-to-end tracing for every model, retrieval and tool call | P0 |
| EV-2 | Risk-tier assignment for each use case | P0 |
| EV-3 | Automated test suite gates promotion between stages | P0 |
| EV-4 | Quality, cost and drift monitoring in production | P1 |
| EV-5 | Red-team tests for higher risk tiers | P1 |
| EV-6 | Ability to pause a use case quickly | P1 |

### 3.7 Platform operations
| ID | Requirement | Priority |
|---|---|---|
| OP-1 | Reproducible deployment via Helm and Terraform | P0 |
| OP-2 | Secrets management; no keys in code or images | P0 |
| OP-3 | High availability for the gateway | P1 |
| OP-4 | Documented runbooks and incident process | P1 |

## 4. Success metrics
Defined in [OKRs and KPIs](okrs-and-kpis.md) and measured through the [adoption funnel](adoption-funnel.md).

## 5. Risks and mitigations
| Risk | Mitigation |
|---|---|
| Sensitive data sent to models | PII masking at the gateway, tier-based data rules, audit logging |
| Cost growth | Per-team budgets, usage dashboards, alerts |
| Low adoption | Pilot with champions, templates, self-service onboarding |
| Poor answer quality | Citations, eval gates, feedback capture |
| Connector misuse | Policy check on each call, scoped access, approval gates |
| Vendor dependency | Model-agnostic gateway, tested fallbacks |

## 6. Open questions
- Which business unit is the first pilot team?
- Which document collections are approved for the first knowledge sources?
- What retention period applies to prompts and responses by risk tier?
- Which connectors should be built first after the initial example?
