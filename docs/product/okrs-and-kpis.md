# OKRs and KPIs

All targets are **proposed** for the first pilot year and will be revised once baseline data exists.

## Objective 1: Make Aurai the default path to AI
| Key result | Metric | Proposed target |
|---|---|---|
| KR1.1 | Share of eligible teams onboarded | 60% of targeted business units |
| KR1.2 | Weekly active users across the workspace | Set after pilot baseline |
| KR1.3 | Time from approved idea to first working use case | Under 2 weeks for tier 0 and 1 |
| KR1.4 | Share of AI model traffic routed via the gateway | 90% of known workloads |

## Objective 2: Keep AI safe, governed and auditable
| Key result | Metric | Proposed target |
|---|---|---|
| KR2.1 | Use cases with an assigned risk tier | 100% |
| KR2.2 | Use cases at tier 2+ with passing eval evidence before launch | 100% |
| KR2.3 | Requests with PII masking applied where required | 100% |
| KR2.4 | Time to pause a use case after a decision | Under 1 hour |

## Objective 3: Deliver measurable value at controlled cost
| Key result | Metric | Proposed target |
|---|---|---|
| KR3.1 | Use cases with defined success metrics | 100% before pilot exit |
| KR3.2 | Cost per active user and cost per use case reported monthly | Reported for all teams |
| KR3.3 | Teams staying within budget | 95% |
| KR3.4 | Pilot use cases promoted to production | Set after pilot baseline |

## Objective 4: Make answers trustworthy
| Key result | Metric | Proposed target |
|---|---|---|
| KR4.1 | Knowledge answers that include citations | 100% |
| KR4.2 | Retrieval and groundedness scores on golden sets | Thresholds set per tier |
| KR4.3 | User-reported answer helpfulness | Set after pilot baseline |

## KPI definitions

| KPI | Definition | Source |
|---|---|---|
| Weekly active users | Distinct signed-in users with at least one request in a week | Gateway and workspace logs |
| Onboarded team | Team with provisioned key, budget and assigned owner | Gateway admin data |
| Activated team | Onboarded team with a working use case that passed its first eval | Governance records |
| Cost per active user | Model spend divided by weekly active users | Gateway spend tracking |
| Grounded answer rate | Share of knowledge answers whose claims are supported by cited sources | Eval pipeline |
| Approval turnaround | Time from submission to risk-tier decision | Governance records |
| Incident count | Safety or data-handling incidents per period | Incident process |

## Reporting cadence
- **Weekly:** platform health, spend, adoption funnel.
- **Monthly:** OKR progress, cost by team, quality trends, incidents.
- **Quarterly:** executive review of value delivered and roadmap changes.
