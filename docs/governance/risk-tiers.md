# Risk tiers

Every Aurai use case is assigned a risk tier. The tier sets required controls, evaluation evidence and approvals. Higher tiers add controls; they never remove them.

## Tier definitions

| Tier | Description | Examples |
|---|---|---|
| **T0: Personal productivity** | Individual use of approved models with non-sensitive information; no stored company data; no actions | Drafting, brainstorming, summarizing public or non-sensitive text |
| **T1: Internal knowledge** | Answers grounded in approved internal collections; read-only; internal audience | Policy Q&A, operating-procedure lookup |
| **T2: Business process** | Touches confidential data or drives decisions; actions require approval | Report generation from operational data, draft communications for review, ticket triage with human approval |
| **T3: High impact** | Affects guests, employees, finances, safety, legal obligations or protected IP; external-facing or automated actions | Guest-facing assistants, automated approvals, content generation using licensed IP |

## Classification questions
A use case moves up a tier if the answer to any question is yes:
1. Does it use data classified above "internal"?
2. Does it take actions in other systems?
3. Does its output reach people outside the company?
4. Could an error affect safety, money, legal standing or employment?
5. Does it involve licensed or protected creative IP?

## Required controls by tier

| Control | T0 | T1 | T2 | T3 |
|---|---|---|---|---|
| Access through gateway with team key | Yes | Yes | Yes | Yes |
| Tracing enabled | Yes | Yes | Yes | Yes |
| PII masking | Yes | Yes | Yes | Yes |
| Entitlement-aware retrieval | n/a | Yes | Yes | Yes |
| Citations required | n/a | Yes | Yes | Yes |
| Human approval for actions | n/a | n/a | Yes | Yes, plus second reviewer |
| Golden-set evaluation before launch | Optional | Yes | Yes | Yes |
| Red-team testing | No | Optional | Yes | Yes |
| Audit log retention | Standard | Standard | Extended | Extended |
| Risk and compliance review | No | Team lead | Compliance reviewer | Compliance and legal |
| Production monitoring and alerts | Basic | Yes | Yes | Yes, with incident runbook |

## Promotion gates
A use case moves from sandbox to pilot to production only when:
- its tier is assigned and recorded
- required controls are in place and verified
- its evaluation suite meets the thresholds for the tier
- an owner is named and a pause procedure is documented

Promotion is enforced in CI by `aurai-eval-governance`. A failing gate blocks deployment.

A control claimed as passing needs evidence, not a declaration: committed results from a live run of the current evaluation suite, recorded at or above the use case's tier, recent enough for the tier and meeting its thresholds. Production also needs a fresh gateway smoke test. Offline replays do not count. The rules and thresholds are in `aurai-eval-governance` (`docs/promotion-gates.md`).

## Review and change
Tiers are re-evaluated when a use case adds data sources, tools, audiences or actions. Any incident triggers a review of the tier and controls.
