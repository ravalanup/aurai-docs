# Pilot and rollout plan

## Approach
Roll out in waves. Each wave must meet exit criteria before the next begins.

| Wave | Audience | Purpose |
|---|---|---|
| **Wave 0: Internal** | Platform team | Validate deployment, tracing and gateway basics |
| **Wave 1: Champions pilot** | 1–2 volunteer business units, about 10–25 users each | Test onboarding, workspace, knowledge answers and support model |
| **Wave 2: Early adopters** | 3–5 additional teams, including at least one builder team | Test agents, workflows and the first connector |
| **Wave 3: General availability** | All eligible business units | Self-service onboarding with support and reporting |

## Selecting pilot teams
Choose teams that have:
- an executive sponsor and a named owner
- a concrete use case with a measurable outcome
- documents or data suitable for the knowledge service
- willingness to give structured feedback

## Entry criteria per wave
- Wave 1: gateway, workspace, tracing and PII masking working; support channel staffed; risk tier defined for each pilot use case.
- Wave 2: knowledge service meets citation and permission requirements; first connector passes security review; eval gate operating.
- Wave 3: runbooks and incident process tested; cost reporting in place; onboarding documented.

## Exit criteria per wave
- No unresolved high-severity safety or data-handling issues.
- Success metrics for each pilot use case measured and reported.
- Usage, cost and quality within agreed thresholds.
- Feedback reviewed and incorporated into the roadmap.

## Onboarding path for a team
1. Submit a use case with owner, goal, data involved and success metric.
2. Receive a risk tier and the controls that apply.
3. Get a team key, budget and workspace access.
4. Start from a template (chat, knowledge Q&A, workflow or agent).
5. Pass the eval gate for the tier.
6. Launch, then monitor in the dashboards.

## Enablement
- Getting-started guide and short walkthroughs.
- Template library for common patterns.
- Office hours and a champions network.
- A published list of approved models, connectors and document collections.

## Support model
- Self-service documentation first.
- A shared support channel with response targets by severity.
- Platform on-call for gateway and runtime incidents.
- Escalation path to security and compliance.

## Communication
- Kickoff note to wave audiences stating purpose, scope and rules of use.
- Weekly pilot update to sponsors: adoption, issues, spend.
- Release notes for each capability.

## Risks
| Risk | Mitigation |
|---|---|
| Teams bypass the platform | Make onboarding faster than going alone; report unmanaged usage |
| Overly broad pilot scope | Cap use cases per team; require success metrics |
| Support overload | Templates, documentation, champions network |
| Uneven data quality in knowledge sources | Curate collections; measure retrieval quality |
