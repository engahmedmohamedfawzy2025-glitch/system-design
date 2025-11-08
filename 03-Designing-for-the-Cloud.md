# ☁️ System Design – Stage 3: Designing for the Cloud

> **Goal**  
> Translate core concepts into a practical cloud architecture with containers, Kubernetes, and IaC.

---

## Monolith vs Microservices
| Aspect | Monolith | Microservices |
|---|---|---|
| Deployment | Single unit | Independent services |
| Scaling | Coarse-grained | Per service |
| Complexity | Simple early | Ops/observability overhead |
| Team ownership | Shared | Strong boundaries |

**Guidance:** Start simple; break out clear bounded contexts. Use a platform that standardizes CI/CD, telemetry, and security across services.

---

## Containerization
**Containers** package runtime + dependencies → consistent deploys, faster start.  
**DevOps:** Dockerfiles, multi-stage builds, image scanning, SBOMs, registries.

---

## Orchestration (Kubernetes)
K8s provides scheduling, service discovery, autoscaling, self-healing, and RBAC.

**Building blocks:** Deployments, Services/Ingress, ConfigMaps/Secrets, HPA, PDBs, StatefulSets, PV/PVC, NetworkPolicies.  
**DevOps:** GitOps (Argo CD), Helm/Kustomize, admission policies, cost dashboards.

---

## Infrastructure as Code (IaC)
Define cloud infra declaratively.

- **Terraform** for multi-cloud resources,
- **CloudFormation** (AWS), **Bicep/ARM** (Azure), **Deployment Manager** (GCP),
- **Pulumi** for general-purpose languages.

**Practices:** modules, environments, remote state, policy-as-code (OPA), drift detection, CI checks.

---

## Serverless
Event-driven functions (Lambda/Functions) + managed DB/queues → zero server mgmt, auto scale, pay-per-use.  
Use when workloads are spiky or glue-logic heavy; mind cold starts, timeouts, and observability.

---

## CI/CD as Part of Architecture
- **CI:** build, test, scan, sign images, SBOM.
- **CD:** progressive delivery (blue/green, canary), GitOps, infra and app rollouts, automated rollbacks.

**Typical flow:**  
Developer → PR → CI (build/test/scan) → push image → CD (Helm/Argo) → K8s/ECS → telemetry & alerts.

---

## Summary
Cloud design = **standardized platform + IaC + containers/K8s + CI/CD + guardrails**.  
You optimize for **velocity with safety**.