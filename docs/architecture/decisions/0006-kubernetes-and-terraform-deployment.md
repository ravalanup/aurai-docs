# ADR 0006: Helm on Kubernetes and Terraform on AWS

**Status:** Accepted
**Date:** 2026-11-19

## Context
Deployment format should match production so that what is tested locally is what is deployed.

## Decision
Package services as Helm charts, tested on a local Kubernetes cluster. Use Terraform to define AWS infrastructure (EKS, RDS Postgres, ElastiCache, Secrets Manager). Terraform is validated and planned in CI; applying to a real account is optional and short-lived.

## Consequences
- One deployment format from laptop to cloud.
- Higher setup effort than Docker Compose, offset by production fidelity.
- Cloud cost is controlled by not leaving environments running.
