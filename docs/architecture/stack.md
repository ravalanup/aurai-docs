# Stack and rejected alternatives

## Selected stack

| Layer | Choice | Role |
|---|---|---|
| Gateway | LiteLLM | Unified model API, team keys, budgets, rate limits, fallbacks |
| Workspace | Open WebUI | Employee chat interface; UI only, retrieval goes through the knowledge service |
| Identity | Keycloak (OIDC) | SSO, roles |
| Agents (primary) | LangGraph | Stateful production agents with checkpoints and approval gates |
| Workflows | n8n | Low-code automation for business builders |
| Agents (reference) | Claude Agent SDK | MCP-heavy operational agent |
| Agents (reference) | CrewAI | Role-based multi-agent crew for business workflows |
| Tools | MCP (Python SDK) | Standard connector interface |
| Policy | Open Policy Agent | Allow/deny decisions for tools and data |
| Retrieval | Qdrant | Vector search with payload filters for entitlements |
| PII | Microsoft Presidio | Detection and masking in the gateway |
| Tracing | OpenTelemetry collector | Vendor-neutral trace pipeline |
| Observability | Langfuse | Production monitoring, prompt management, cost by team |
| Observability | Phoenix | OTel-native tracing and RAG/eval debugging (Elastic License 2.0) |
| Evals | Promptfoo | CI gates and red-team tests |
| Orchestration | Kubernetes (Helm) | Deployment format |
| Cloud IaC | Terraform (AWS) | EKS, RDS Postgres, ElastiCache, Secrets Manager |

## Distinct roles where tools look alike
- **LangGraph vs. n8n:** engineers build durable, tested agents in LangGraph; business builders assemble workflows in n8n.
- **Claude Agent SDK and CrewAI:** reference implementations showing different agent styles; production agents default to LangGraph.
- **Langfuse vs. Phoenix:** Langfuse for production monitoring and cost; Phoenix for deep trace and retrieval debugging.
- **Promptfoo vs. Langfuse evals:** Promptfoo gates releases before deployment; Langfuse scores live traffic.

## Considered and rejected

| Option | Decision | Reason |
|---|---|---|
| OpenAI Agents SDK | Not selected | Overlaps LangGraph and is OpenAI-first; revisit if a team standardizes on OpenAI |
| Custom LLM-as-judge scripts | Not selected | Promptfoo model-graded checks and Langfuse evaluators cover the need |
| Docker Compose as primary deployment | Not selected | Helm on a local cluster uses the same charts as production |
| pgvector | Not selected | Qdrant offers dedicated filtering and scales independently of the relational database |
| OpenSearch | Not selected | Adds operational weight; hybrid search can be added later if needed |
| Managed gateways (Portkey, Cloudflare AI Gateway) | Not selected | LiteLLM is open source, self-hostable and fits data-residency needs |
| Zapier / Make | Not selected | Not self-hostable; weaker fit for enterprise control |

Decisions are recorded in [architecture decision records](decisions/).
