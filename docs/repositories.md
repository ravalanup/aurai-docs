# Repositories

Aurai is split by ownership, release cadence and security boundary.

| # | Repository | Contents | Depends on |
|---|---|---|---|
| 0 | `aurai-docs` | Product docs, architecture, governance, decisions | none |
| 1 | `aurai-infra` | Helm charts, Terraform (AWS), shared CI templates, secrets patterns | none |
| 2 | `aurai-gateway` | LiteLLM configuration, routing, budgets, rate limits, PII masking | infra |
| 3 | `aurai-eval-governance` | Tracing config, risk-tier rubric, policy-as-code, eval suites, promotion gates | infra, gateway |
| 4 | `aurai-workspace` | Open WebUI configuration, roles, SSO integration | gateway |
| 5 | `aurai-knowledge-rag` | Ingestion pipelines, Qdrant retrieval, permission filters, citations | infra, gateway |
| 6 | `aurai-mcp-connectors` | MCP servers with Open Policy Agent checks | gateway |
| 7 | `aurai-agent-runtime` | LangGraph, n8n, Claude Agent SDK and CrewAI agents with approval gates | gateway, knowledge, connectors |

Build status, verification and differences from this plan are in [status.md](status.md).

## Why these boundaries
- **Infra** carries the highest privilege and needs the strictest review.
- **Gateway** sits on every request, so a bad change affects everyone.
- **Workspace** releases frequently and faces end users.
- **Agent runtime** executes tools, so it needs its own review and sandboxing path.
- **Connectors** each need a security review and can later split per system.
- **Knowledge** owns data pipelines and entitlement rules.
- **Eval and governance** gate promotion, so the teams they check cannot edit them.

## Build order
`aurai-docs` → `aurai-infra` → `aurai-gateway` → `aurai-eval-governance` (tracing and risk tiers) → `aurai-workspace` → `aurai-knowledge-rag` → `aurai-mcp-connectors` → `aurai-agent-runtime` → `aurai-eval-governance` (evals and gates) → `aurai-docs` (final updates)

Use-case applications built by business teams live in their own repositories and consume Aurai through the gateway, knowledge service, connectors and runtime templates.
