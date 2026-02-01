# Quality Attributes Reference

This reference documents the ISO 25010 quality model adapted for architecture documentation auditing, including validation heuristics and common gaps for each attribute.

---

## ISO 25010 Quality Model Overview

| Attribute | Sub-Characteristics | Primary Viewpoints |
|-----------|--------------------|--------------------|
| **Performance Efficiency** | Time behavior, Resource utilization, Capacity | V4, V5 |
| **Security** | Confidentiality, Integrity, Non-repudiation, Accountability, Authenticity | V7, V6 |
| **Reliability** | Maturity, Availability, Fault tolerance, Recoverability | V8, V4 |
| **Maintainability** | Modularity, Reusability, Analyzability, Modifiability, Testability | V3, V10 |
| **Scalability** | Horizontal scaling, Vertical scaling, Elasticity | V4, V2 |
| **Interoperability** | Co-existence, Interchangeability | V6, V1 |
| **Portability** | Adaptability, Installability, Replaceability | V4, V2 |
| **Usability** | Appropriateness recognizability, Learnability, Operability | V6, V10 |

---

## 1. Performance Efficiency

### Definition
The degree to which a system performs its functions within specified time and resource constraints.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Time Behavior** | Response time, processing time, throughput | What are the latency requirements? |
| **Resource Utilization** | CPU, memory, storage, network usage | What are the resource limits? |
| **Capacity** | Maximum load the system can handle | What is the expected load? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V4, V5]
  elements:
    - Latency targets (e.g., "P99 < 100ms")
    - Throughput requirements (e.g., "1000 TPS")
    - Resource budgets per container
    - Caching strategy
    - Database query optimization approach

implicit_coverage:
  indicators:
    - CDN mentioned
    - Caching layer present
    - Read replicas configured
    - Connection pooling mentioned
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Latency targets defined | Look for "ms", "latency", "response time" | HIGH |
| Throughput requirements | Look for "TPS", "requests per second" | MEDIUM |
| Resource limits per service | Look for CPU/memory limits | MEDIUM |
| Caching strategy | Look for Redis, Memcached, CDN | MEDIUM |
| Database optimization | Look for indexes, query patterns | LOW |

### Common Gaps

1. **Vague performance goals**: "System should be fast" without numbers
2. **Missing capacity planning**: No expected load projections
3. **Undefined hot paths**: Critical performance paths not identified
4. **No baseline metrics**: No current performance benchmarks

### Measurement Approaches

| Metric | Measurement Method | Target Example |
|--------|-------------------|----------------|
| Latency P50 | APM tool | < 50ms |
| Latency P99 | APM tool | < 200ms |
| Throughput | Load testing | > 1000 RPS |
| Error rate under load | Load testing | < 0.1% |

---

## 2. Security

### Definition
The degree to which a system protects information and data from unauthorized access while ensuring access to authorized users.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Confidentiality** | Data accessible only to authorized | How is data protected from unauthorized access? |
| **Integrity** | Data accuracy and completeness protected | How is data modification controlled? |
| **Non-repudiation** | Actions can be proven to have occurred | How are actions tracked? |
| **Accountability** | Actions traceable to entity | How is audit logging implemented? |
| **Authenticity** | Identity of subject verified | How is identity verified? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V7]
  elements:
    - Authentication mechanism
    - Authorization model (RBAC, ABAC, etc.)
    - Encryption at rest specification
    - Encryption in transit specification
    - Key management approach
    - Secrets storage
    - Audit logging strategy
    - Input validation approach

implicit_coverage:
  indicators:
    - TLS mentioned
    - OAuth/OIDC referenced
    - Security headers mentioned
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Auth mechanism documented | Look for OAuth, JWT, SAML | CRITICAL |
| Authorization model | Look for RBAC, permissions | CRITICAL |
| Encryption at rest | Look for AES, encryption | HIGH |
| Encryption in transit | Look for TLS, HTTPS | HIGH |
| Audit logging | Look for audit trail, logging | HIGH |
| Secrets management | Look for Vault, KMS | HIGH |

### Common Gaps

1. **Auth afterthought**: Security added late without integration
2. **Missing authorization model**: Authentication but no authorization
3. **Secrets in code**: Credentials not properly managed
4. **No audit trail**: Security events not logged
5. **Trust assumptions**: "Internal network is secure"

### Compliance Mapping

| Compliance | Key Security Requirements |
|------------|--------------------------|
| SOC2 | Access control, encryption, audit logging |
| GDPR | Data protection, consent, access controls |
| PCI-DSS | Encryption, network segmentation, key management |
| HIPAA | PHI protection, access controls, audit trails |

---

## 3. Reliability

### Definition
The degree to which a system performs specified functions under specified conditions for a specified period of time.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Maturity** | Frequency of failures | What is the expected error rate? |
| **Availability** | System operational when required | What is the availability target? |
| **Fault Tolerance** | Operation despite failures | How does the system handle failures? |
| **Recoverability** | Recovery after failure | How quickly can the system recover? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V8, V4]
  elements:
    - Availability target (e.g., "99.9%")
    - SLO definitions
    - SLI definitions
    - Error budget policy
    - Disaster recovery plan
    - RTO/RPO targets
    - Failover mechanism
    - Circuit breaker patterns

implicit_coverage:
  indicators:
    - Multi-region deployment
    - Health checks mentioned
    - Retry patterns
    - Redundancy mentioned
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Availability target | Look for "99.9%", "uptime" | HIGH |
| SLOs defined | Look for SLO section | HIGH |
| DR plan exists | Look for disaster recovery | CRITICAL |
| RTO/RPO defined | Look for recovery time | HIGH |
| Failover mechanism | Look for failover, redundancy | HIGH |

### Common Gaps

1. **No availability targets**: No SLO/SLA defined
2. **Missing DR strategy**: No disaster recovery plan
3. **Single points of failure**: No redundancy identified
4. **No RTO/RPO**: Recovery objectives undefined

### Measurement Approaches

| Metric | Measurement Method | Target Example |
|--------|-------------------|----------------|
| Availability | Uptime monitoring | 99.9% |
| MTTR | Incident tracking | < 1 hour |
| MTBF | Incident tracking | > 30 days |
| Error rate | APM/monitoring | < 0.1% |

---

## 4. Maintainability

### Definition
The degree of effectiveness and efficiency with which a system can be modified.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Modularity** | System composed of discrete components | Are components loosely coupled? |
| **Reusability** | Asset usable in more than one system | Are common patterns extracted? |
| **Analyzability** | Effort to diagnose issues | How easy is it to debug? |
| **Modifiability** | Effort to make changes | How easy is it to modify? |
| **Testability** | Effort to test | How easy is it to test? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V3, V10]
  elements:
    - Component boundaries
    - Interface contracts
    - Design patterns documented
    - ADRs for key decisions
    - Abstraction layers
    - Testing approach

implicit_coverage:
  indicators:
    - Microservices architecture
    - Clear module structure
    - Dependency injection
    - Interface-based design
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Clear component boundaries | Look for component diagram | HIGH |
| ADRs exist | Look for decision records | CRITICAL |
| Interface contracts | Look for interface definitions | HIGH |
| Testing approach | Look for test strategy | MEDIUM |
| Abstraction layers | Look for layer diagrams | MEDIUM |

### Common Gaps

1. **No ADRs**: Decisions not documented
2. **Tight coupling**: Components directly dependent
3. **No testing strategy**: Testing approach undefined
4. **Missing interfaces**: Direct implementation dependencies

---

## 5. Scalability

### Definition
The ability of a system to handle increased load by adding resources.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Horizontal Scaling** | Adding more instances | Can we add more nodes? |
| **Vertical Scaling** | Adding more resources to existing | Can we increase resources? |
| **Elasticity** | Automatic scaling based on demand | Does it auto-scale? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V4, V2]
  elements:
    - Scaling strategy (horizontal/vertical)
    - Auto-scaling configuration
    - Scaling triggers and thresholds
    - Stateless service design
    - Database scaling approach
    - Session management for scaling

implicit_coverage:
  indicators:
    - Kubernetes/container orchestration
    - Load balancer mentioned
    - Stateless services
    - Read replicas
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Scaling strategy defined | Look for horizontal/vertical | HIGH |
| Auto-scaling configured | Look for auto-scaling rules | MEDIUM |
| Stateless services | Look for stateless design | MEDIUM |
| Database scaling | Look for sharding, replicas | MEDIUM |

### Common Gaps

1. **No scaling strategy**: How to scale undefined
2. **Stateful services without plan**: State prevents scaling
3. **Database bottleneck**: Only app layer scales
4. **Missing load projections**: Capacity planning absent

---

## 6. Interoperability

### Definition
The degree to which a system can exchange information with other systems and use the exchanged information.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Co-existence** | Perform functions while sharing environment | How does it work with other systems? |
| **Interchangeability** | Used in place of another system | Is it replaceable? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V6, V1]
  elements:
    - API specifications
    - Standard protocols used
    - Data format standards
    - Integration patterns
    - API versioning strategy

implicit_coverage:
  indicators:
    - REST/gRPC/GraphQL mentioned
    - OpenAPI/Swagger referenced
    - JSON/XML standards
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| API spec format | Look for OpenAPI, gRPC | HIGH |
| Standard protocols | Look for REST, HTTP | MEDIUM |
| Data formats | Look for JSON, Protobuf | MEDIUM |
| API versioning | Look for /v1/, version headers | HIGH |

### Common Gaps

1. **No API specification**: APIs undocumented
2. **Non-standard protocols**: Custom protocols without justification
3. **No versioning**: Breaking changes not managed

---

## 7. Portability

### Definition
The degree of effectiveness and efficiency with which a system can be transferred from one environment to another.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Adaptability** | Adapted for different environments | Can it run elsewhere? |
| **Installability** | Successfully installed/uninstalled | How complex is deployment? |
| **Replaceability** | Used in place of another component | Can components be swapped? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V4, V2]
  elements:
    - Container strategy
    - Infrastructure as Code
    - Configuration externalization
    - Platform abstractions

implicit_coverage:
  indicators:
    - Docker/containers
    - Terraform/CloudFormation
    - Environment variables
    - 12-factor app principles
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| Containerized | Look for Docker, Kubernetes | MEDIUM |
| IaC present | Look for Terraform | MEDIUM |
| Config externalized | Look for env vars, config maps | MEDIUM |
| Vendor abstraction | Look for abstraction layers | LOW |

### Common Gaps

1. **Vendor lock-in**: Direct cloud service dependencies
2. **Hardcoded config**: Environment-specific values in code
3. **No IaC**: Manual infrastructure

---

## 8. Usability (API/Developer Experience)

### Definition
For architecture, this focuses on API usability and developer experience.

### Sub-Characteristics

| Sub-Characteristic | Definition | Validation Questions |
|-------------------|------------|---------------------|
| **Appropriateness** | Suitable for needs | Does it meet developer needs? |
| **Learnability** | Easy to learn | How easy is it to onboard? |
| **Operability** | Easy to operate | How easy is it to use? |

### Architecture Documentation Requirements

```yaml
explicit_coverage:
  required_in: [V6, V10]
  elements:
    - API documentation strategy
    - SDK/client library availability
    - Error message standards
    - Developer onboarding approach

implicit_coverage:
  indicators:
    - OpenAPI/Swagger docs
    - Code samples
    - Getting started guide
```

### Validation Heuristics

| Heuristic | Detection | Severity if Missing |
|-----------|-----------|---------------------|
| API docs exist | Look for documentation references | MEDIUM |
| Error codes standard | Look for error format | LOW |
| Examples provided | Look for code samples | LOW |

### Common Gaps

1. **No API documentation**: APIs undocumented
2. **Inconsistent errors**: Error format varies
3. **Missing examples**: No code samples

---

## Quality Attribute Coverage Matrix

### Coverage Assessment by Viewpoint

| Quality Attribute | V1 | V2 | V3 | V4 | V5 | V6 | V7 | V8 | V9 | V10 |
|------------------|----|----|----|----|----|----|----|----|----|----|
| Performance | - | S | - | **P** | **P** | S | - | S | - | - |
| Security | S | - | - | S | **P** | **P** | **P** | - | S | - |
| Reliability | - | S | - | **P** | S | - | - | **P** | - | - |
| Maintainability | - | S | **P** | - | - | - | - | - | **P** | **P** |
| Scalability | - | **P** | - | **P** | S | S | - | - | - | - |
| Interoperability | **P** | - | - | - | S | **P** | - | - | - | - |
| Portability | - | **P** | - | **P** | - | - | - | - | - | - |
| Usability | - | - | - | - | - | **P** | - | - | - | **P** |

**Legend:**
- **P** = Primary coverage expected
- **S** = Secondary/supporting coverage
- **-** = Not expected

---

## Severity Guidelines

### Coverage Gap Severity

| Scenario | Severity |
|----------|----------|
| Primary viewpoint has MISSING coverage | CRITICAL (regulated) / HIGH (unregulated) |
| All viewpoints have MISSING coverage | CRITICAL |
| Primary viewpoint has only IMPLICIT | MEDIUM |
| Secondary viewpoint has MISSING | LOW |

### Quality Attribute Priority by Context

| Context | High Priority Attributes |
|---------|-------------------------|
| Financial services | Security, Reliability, Compliance |
| Healthcare | Security, Reliability, Compliance |
| E-commerce | Performance, Scalability, Reliability |
| SaaS platform | Scalability, Maintainability, Security |
| Internal tools | Maintainability, Usability |
| IoT systems | Reliability, Security, Performance |

---

## References

- [ISO/IEC 25010:2011](https://www.iso.org/standard/35733.html)
- [Software Quality Models](https://en.wikipedia.org/wiki/ISO/IEC_9126)
- [Quality Attribute Workshop](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=513807)
