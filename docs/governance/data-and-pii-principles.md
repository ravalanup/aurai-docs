# Data, PII and IP principles

## Data principles
1. **Minimum necessary.** Send models only what the task needs.
2. **Classification first.** Each knowledge collection and connector declares its data classification; use cases may use only what their tier permits.
3. **Entitlements travel with data.** Retrieval and connectors always evaluate the caller's permissions.
4. **No secrets in prompts or code.** Credentials live in the secrets manager.
5. **Traceable.** Every request records who, which use case, which model, which sources and which tools.

## PII handling
- PII detection and masking run in the gateway before requests leave the platform.
- Masking rules are configured per tier and tested in CI with synthetic examples.
- Traces store masked content by default; unmasked content is not retained unless a documented exception exists.
- Prompts and responses are retained according to tier-based retention periods.

## Intellectual property
- Protected creative content is handled only in T3 use cases with legal review.
- Model providers used for IP-sensitive work must contractually exclude training on company data.
- Generated content is labeled and reviewed according to tier before external use.

## Vendors and models
- Only models approved in the catalog are available through the gateway.
- Each approved model records data-handling terms, region and permitted tiers.
- Provider changes are tested against the golden sets before cutover.

## Incident response
1. Any team or reviewer can request a pause for a use case.
2. The platform team can disable a key, connector or model route immediately.
3. Incidents are triaged by severity, investigated using traces, and recorded with corrective actions.
4. Lessons feed back into tier definitions, evals and controls.

## Synthetic data
All data in the Aurai repositories is synthetic and contains no real personal, customer or proprietary information.
