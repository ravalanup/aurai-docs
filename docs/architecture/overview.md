# Architecture overview

## Layers

```mermaid
flowchart TB
    subgraph EXP[Experience]
        W[Workspace<br/>Open WebUI]
        APPS[Business applications]
    end
    subgraph ORC[Orchestration]
        LG[LangGraph agents]
        N8N[n8n workflows]
        CAS[Claude Agent SDK agents]
        CR[CrewAI crews]
    end
    subgraph PS[Platform services]
        GW[AI Gateway<br/>LiteLLM]
        KN[Knowledge service<br/>Qdrant]
        MCP[MCP connectors]
        POL[Policy engine<br/>Open Policy Agent]
        PII[PII masking<br/>Presidio]
    end
    subgraph TR[Trust]
        OBS[Tracing and monitoring<br/>Langfuse + Phoenix via OpenTelemetry]
        EVAL[Eval gates<br/>Promptfoo]
        GOV[Risk tiers and approvals]
    end
    subgraph FND[Foundation]
        K8S[Kubernetes via Helm]
        TF[Terraform on AWS]
        ID[Identity<br/>Keycloak OIDC]
        SEC[Secrets management]
    end
    EXP --> ORC
    EXP --> GW
    ORC --> GW
    ORC --> KN
    ORC --> MCP
    MCP --> POL
    GW --> PII
    GW --> MODELS[(Model providers)]
    ORC -.-> OBS
    GW -.-> OBS
    KN -.-> OBS
    EVAL --> GOV
    GOV --> POL
    PS --> FND
```

## Request flow: grounded answer
1. User signs in through Keycloak and asks a question in the workspace.
2. The workspace calls the knowledge service with the user identity.
3. The knowledge service retrieves from Qdrant, filtering by the user's entitlements.
4. The prompt and retrieved passages go to the gateway; Presidio masks PII where required.
5. The gateway routes to the configured model, applying budget and rate limits, and falls back if needed.
6. The answer returns with citations; the whole chain is traced.

## Request flow: agent action
1. An agent plans a step that needs a tool.
2. The tool call goes to an MCP connector; Open Policy Agent allows or denies based on team, risk tier and action.
3. If the action is consequential, the agent pauses for human approval.
4. After approval, the connector executes; result and approval are traced and audited.

## Cross-cutting concerns
- **Identity:** OIDC for users; scoped service identities for agents and connectors.
- **Observability:** every model call, retrieval and tool call emits OpenTelemetry traces to Langfuse and Phoenix.
- **Cost:** gateway spend tracking by team key, reported in dashboards.
- **Governance:** each use case has a risk tier that sets controls, eval requirements and approvals (see [risk tiers](../governance/risk-tiers.md)).
- **Resilience:** gateway is stateless behind a load balancer; model fallbacks tested in CI.
