# Prototype vs. production

Aurai is built and demonstrated at prototype scale with production-grade tools and configuration. This page states what exists at each level so nobody confuses the two.

| Capability | Production target | Built in the Aurai repositories |
|---|---|---|
| **Gateway** | Highly available LiteLLM on Kubernetes, enterprise SSO, per-team budgets and chargeback, regional and data-residency controls, multiple vendor contracts | LiteLLM with two or more models, virtual keys for several sample business units, budget limits and a demonstrated fallback |
| **Workspace** | Open WebUI behind enterprise SSO with audit retention and content filters | Open WebUI with Keycloak, several roles, document upload Q&A |
| **Agents and workflows** | Governed runtime with approval gates, secrets management, sandboxed tool execution and SLAs | LangGraph ops-insights agent with a separate approval service, an agent template, an n8n workflow example and a Claude Agent SDK reference agent. A CrewAI reference agent is not built |
| **MCP and tools** | Vetted connectors to ticketing, HR and content systems, scoped per team and security-reviewed | An MCP connector over synthetic data with an Open Policy Agent check |
| **Knowledge (RAG)** | Managed vector store, entitlement-aware retrieval, ingestion pipelines, freshness SLAs | Qdrant with a curated synthetic document set, permission filters and citations |
| **Evals and observability** | Continuous eval pipelines, drift and cost monitoring, incident process, red-teaming | Langfuse and Phoenix tracing; Promptfoo golden, red-team and grounding suites; an evidence-backed promotion gate. No live evaluation has been run, and live quality and drift monitoring is not built |
| **Governance and security** | PII redaction, DLP, IP and licensing controls, legal review, audit retention, model risk tiers | Risk-tier rubric, Presidio masking, audit logging, documented production requirements |
| **Infrastructure** | Multi-account AWS, EKS, managed Postgres and cache, secrets manager, CI/CD with environments | Helm charts tested on a local cluster, Terraform for AWS validated in CI |
| **Adoption** | Org-wide rollout, training, champions, support model and executive reporting | Pilot and rollout plan, adoption funnel and OKRs (see product docs) |

## Not built here (production work remaining)
- Multi-region deployment and disaster recovery drills
- Contractual vendor arrangements and enterprise data-processing agreements
- Full DLP integration with enterprise tooling
- Large-scale load testing and capacity planning
- Third-party penetration testing and compliance certifications
- Production incident response staffing

## Why show it this way
The goal is to show sound product and platform judgment: pick the right production tools, build a working slice end to end, and be explicit about what a real enterprise rollout adds.
