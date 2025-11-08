# ⚙️ System Design for DevOps Engineers – Stage 2: Core Concepts

> **🎯 Goal:**  
> Master the building blocks behind any large-scale system and understand the DevOps actions that make them real.

---

## 🧱 1. Scalability

Scalability means your system can handle growth without downtime or performance loss.

- **Vertical Scaling (Scale-Up):** Add more resources (CPU, RAM) to one server.  
- **Horizontal Scaling (Scale-Out):** Add more servers to distribute the load.  
  - ✅ Preferred for elasticity, cost control, and fault isolation.

**DevOps Responsibilities:**
- Configure **Auto Scaling Groups (ASG)** or **VMSS**.  
- Use **Kubernetes HPA/VPA** for pod scaling.  
- Run **capacity planning** and **load testing**.

---

## ⚖️ 2. Load Balancing

Distribute incoming traffic across multiple servers to improve reliability and performance.

**Layers:**
- **Layer 4 (Transport):** Operates at TCP/UDP level.  
- **Layer 7 (Application):** Routes based on HTTP headers, URLs, etc.

**Common Algorithms:**
- Round Robin  
- Least Connections  
- IP Hash  
- Weighted Distribution

**DevOps Responsibilities:**
- Configure health checks and **TLS termination**.  
- Manage **sticky sessions** (only if needed).  
- Implement **Blue/Green or Canary routing**.

---

## ⚡ 3. Caching

Caching reduces latency and decreases the load on origin systems.

| Layer | Purpose | Common Tools |
|--------|----------|---------------|
| **CDN (Edge)** | Cache static assets closer to users | CloudFront, Akamai |
| **Application/Data Cache** | Store frequently accessed data or expensive queries | Redis, Memcached |
| **Browser Cache** | Control client-side caching | Cache-Control headers, ETags |

**DevOps Responsibilities:**
- Define **eviction policies** (LRU, TTL).  
- Handle **cache invalidation**.  
- Monitor **cache hit/miss ratios** via dashboards.

---

## 🧮 4. Databases

Choose the right database type and scaling strategy.

**SQL (Relational):**
- Structured schema (tables, joins).  
- Follows **ACID** properties.  
- Best for complex queries and transactions.  
- Examples: MySQL, PostgreSQL.

**NoSQL (Non-Relational):**
- Flexible schema.  
- Prioritizes scalability and availability.  
- Examples: MongoDB, Cassandra, DynamoDB.

**Key Patterns:**
- **Replication:** Duplicate data for availability.  
- **Sharding:** Split data horizontally across nodes.  
- **Partitioning:** Logical division inside a DB.  
- **Read Replicas:** Offload reads from the master.  
- **Write Leaders:** Control consistency and concurrency.

**DevOps Responsibilities:**
- Manage **backups** and **Point-in-Time Recovery (PITR)**.  
- Automate **failover** testing.  
- Implement DB management via **Infrastructure as Code (IaC)**.  
- Track storage usage and drift.

---

## 🧠 5. CAP Theorem

In distributed systems, you can guarantee **only two** of the following three:

| Property | Meaning |
|-----------|----------|
| **Consistency (C)** | All nodes see the same data at the same time. |
| **Availability (A)** | Every request gets a response — even if some nodes fail. |
| **Partition Tolerance (P)** | The system continues working despite network splits. |

👉 Most real-world systems must tolerate partitions (**P**),  
so they trade off between **Consistency** and **Availability** depending on business needs.

---

## 🧍 6. Stateless vs Stateful

| Type | Description | Example |
|-------|--------------|----------|
| **Stateless** | Each request is independent — no saved session. | REST APIs, serverless functions |
| **Stateful** | Server keeps session or user state. | Databases, legacy apps |

**Why it matters:**  
Stateless systems are easier to scale horizontally because any instance can handle any request.

**DevOps Responsibilities:**
- Design apps to be **Stateless** whenever possible.  
- Externalize state to managed stores (Redis, S3, RDS).  
- Use **Kubernetes StatefulSets** only when persistence is required.

---

## 📘 Summary

| Concept | Purpose | DevOps Role |
|----------|----------|--------------|
| **Scalability** | Handle increased traffic | Autoscaling, capacity planning |
| **Load Balancing** | Distribute workload | Health checks, traffic routing |
| **Caching** | Reduce latency | Cache strategy, monitoring |
| **Databases** | Persistent data storage | Backup, IaC, replication |
| **CAP Theorem** | Understand trade-offs | Design consistent/available services |
| **Stateless Design** | Easier scaling | Use external storage for state |

**Formula:**  
`LB + Stateless App + Cache + Replicated DB + CDN + Queues + Observability`

**DevOps = the glue that connects it all through IaC and CI/CD.**

---
