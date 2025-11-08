# 🛡️ Stage 4: Reliability, Security & Observability

> **Goal**  
> Make the system production-ready: highly available, secure by design, and observable with actionable signals.

---

## High Availability (HA)
Principles: **redundancy**, **health checks**, **failover**, **multi-AZ/region**.

**Patterns:**  
- Active-active across zones/regions,  
- Read replicas, quorum leaders,  
- Circuit breakers, retries with backoff, idempotency.

**DevOps:** chaos testing, capacity buffers, autoscaling policies, SLO error budgets.

---

## Fault Tolerance & Disaster Recovery (DR)
**Strategies:** backups/PITR, **pilot light**, **warm standby**, **active-active**.  
Define **RPO** (data loss window) and **RTO** (downtime window).  
Rehearse DR and document runbooks.

---

## Security Layers
- **Network:** VPCs, subnets, SGs, firewalls, private endpoints, zero-trust networking.  
- **Identity:** IAM, RBAC, SSO/MFA, least privilege, workload identity.  
- **App:** WAF, API gateways, input validation, rate limiting.  
- **Secrets:** Vault/Secrets Manager, short-lived creds, KMS.  
- **Crypto:** TLS everywhere, encryption at rest (KMS/CMK).  
- **Compliance & Audit:** logging, CloudTrail, policy-as-code, vulnerability mgmt.

**DevOps:** secure baselines, golden images, image signing/verification (cosign), SBOM, supply-chain checks.

---

## Observability (Metrics, Logs, Traces)
- **Metrics:** SLI/SLOs for latency, error rate, saturation. Prometheus + Grafana.  
- **Logs:** structured, centralized (EFK/ELK), retention + search.  
- **Traces:** request path across services (OpenTelemetry, Jaeger/Tempo).  
- **Alerting:** paging on SLO burn; dashboards for capacity and cost.

---

## Progressive Delivery
- **Blue/Green** and **Canary** with traffic shifting and automated rollback on SLO/SLA violations.  
- Feature flags to decouple deploy from release.

---

## Summary
Reliability = engineering + **continuous verification**.  
Security = **defense-in-depth**.  
Observability = **evidence-driven ops**.
