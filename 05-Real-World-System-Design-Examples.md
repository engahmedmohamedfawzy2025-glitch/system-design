# 🌍 Stage 5: Real-World System Design Examples

> **Goal**  
> Apply everything to practical architectures with DevOps-grade build/run/secure/observe workflows.

---

## Example 1: URL Shortener (bit.ly-style)
**HLD:**  
Client → CDN → API Gateway/Ingress → App (stateless) → Redis (hot cache) → DB (NoSQL with TTL)  
Side: queue for async analytics, object storage for logs, dashboards.

**Key Decisions:** short-code generation (hash vs ID), cache TTLs, read replicas, rate limiting.  
**DevOps:** Terraform stacks, Helm charts, HPA, Redis eviction policy, latency SLO, synthetic checks.

---

## Example 2: Centralized Logging & Monitoring
**Flow:**  
Apps → Fluent Bit/Filebeat → Logstash/OpenSearch-Ingest → Elasticsearch/OpenSearch → Kibana  
Metrics via Prometheus; alerting via Alertmanager/PagerDuty.

**DevOps:** index lifecycle mgmt (ILM), hot/warm/cold tiers, dashboards, budget alerts.

---

## Example 3: Notification Service (Email/SMS/Push)
**HLD:**  
API → Queue (SQS/Kafka) → Worker Pool (auto-scaled) → Providers (SES/Twilio/FCM)  
DLQ for failures, outbox pattern, idempotency keys.

**DevOps:** worker autoscaling on queue depth, canary per provider, delivery rate SLOs, retry/backoff policies.

---

## Example 4: CI/CD Platform Architecture
**Pipeline:**  
Git → CI (GitHub Actions/Jenkins) → Scan/Sign → Push Image (ECR/GHCR) → CD (Argo CD/Helm) → K8s  
Infra via Terraform modules; policy checks (OPA/Conftest); secrets via external store.

**DevOps:** trunk-based development, protected branches, SBOM generation, rollout strategies with health gates.

---

## Example 5: File Storage (Drive-like)
**HLD:**  
Client → API → Object Storage (S3) with presigned URLs → Metadata DB (SQL) → Event bus for thumbnails/AV scanning.  
**DevOps:** multipart upload, lifecycle/archival, antivirus lambda, cost dashboards.

---

## Key Takeaways
- Start with a **clear HLD**; isolate state; push compute stateless; cache aggressively.  
- Pair architecture with **IaC, CI/CD, guardrails, and SLOs**.  
- Observe everything; automate rollbacks; rehearse DR.