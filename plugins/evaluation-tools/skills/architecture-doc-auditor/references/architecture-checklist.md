# Architecture Documentation Checklist

This checklist contains 188 items organized by viewpoint for systematic architecture documentation auditing. Each item includes severity levels for missing and incomplete states.

---

## Checklist Structure

Each item follows this format:
- **ID**: `V[viewpoint]-[number]` (e.g., V1-01)
- **Name**: Brief item name
- **Description**: What to check
- **Severity if Missing**: CRITICAL | HIGH | MEDIUM | LOW
- **Severity if Incomplete**: Typically one level lower
- **Applicability**: Document types where this item applies

---

## V1: Context & Scope (15 Items)

### V1-01: System Boundary Definition
| Attribute | Value |
|-----------|-------|
| **Description** | System boundary is explicitly defined with clear delineation of what's inside vs. outside |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | All document types |
| **Detection** | Look for boundary boxes, "in scope" / "out of scope" sections |
| **Quality Criteria** | Boundary is unambiguous; no elements in gray area |

### V1-02: External User Identification
| Attribute | Value |
|-----------|-------|
| **Description** | All external users/actors/personas interacting with the system are identified |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for user icons, persona names, actor lists |
| **Quality Criteria** | Each user type named and role described |

### V1-03: External System Identification
| Attribute | Value |
|-----------|-------|
| **Description** | All external systems the solution interacts with are identified |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for external system boxes, integration lists |
| **Quality Criteria** | Each system named with purpose of integration |

### V1-04: Communication Protocols
| Attribute | Value |
|-----------|-------|
| **Description** | Protocols used to communicate with external systems are specified |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for REST, gRPC, SOAP, messaging protocol labels |
| **Quality Criteria** | Protocol specified for each integration |

### V1-05: Data Flow Directions
| Attribute | Value |
|-----------|-------|
| **Description** | Direction of data flow between system and external entities is shown |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | system_context, data_flow |
| **Detection** | Look for arrows with direction, data labels |
| **Quality Criteria** | Each flow has direction and data type |

### V1-06: System Purpose Statement
| Attribute | Value |
|-----------|-------|
| **Description** | Clear statement of what the system does and why it exists |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | All document types |
| **Detection** | Look for "purpose", "mission", "overview" sections |
| **Quality Criteria** | Purpose is specific, not generic boilerplate |

### V1-07: Key Business Capabilities
| Attribute | Value |
|-----------|-------|
| **Description** | Business capabilities the system enables are listed |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for capability lists, business value sections |
| **Quality Criteria** | Capabilities tied to business outcomes |

### V1-08: External Dependency Ownership
| Attribute | Value |
|-----------|-------|
| **Description** | Ownership/responsibility for external dependencies is documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for owner labels, responsibility matrices |
| **Quality Criteria** | Each external system has identified owner |

### V1-09: Trust Boundaries
| Attribute | Value |
|-----------|-------|
| **Description** | Security trust boundaries are marked between zones |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for dashed lines, "trust boundary" labels, zones |
| **Quality Criteria** | Boundaries align with security model |

### V1-10: Integration Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Sync vs async integration patterns are specified |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for sync/async labels, queue indicators |
| **Quality Criteria** | Pattern choice justified |

### V1-11: Authentication Flows (External)
| Attribute | Value |
|-----------|-------|
| **Description** | How users authenticate to the system is documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | system_context, design_doc |
| **Detection** | Look for auth flow diagrams, SSO references |
| **Quality Criteria** | Auth mechanism specified per user type |

### V1-12: Data Ownership Boundaries
| Attribute | Value |
|-----------|-------|
| **Description** | Which system owns which data is documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc, data_flow |
| **Detection** | Look for "system of record", ownership labels |
| **Quality Criteria** | No ambiguous data ownership |

### V1-13: SLA Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | SLA expectations on external dependencies are documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for SLA tables, availability requirements |
| **Quality Criteria** | SLA numbers specified, not just "high availability" |

### V1-14: Compliance Scope
| Attribute | Value |
|-----------|-------|
| **Description** | Regulatory/compliance scope is defined |
| **Severity Missing** | HIGH (regulated) / LOW (unregulated) |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for compliance framework references |
| **Quality Criteria** | Applicable regulations listed |

### V1-15: Context Diagram Date/Version
| Attribute | Value |
|-----------|-------|
| **Description** | Context diagram has date or version indicator |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | system_context |
| **Detection** | Look for date stamps, version numbers |
| **Quality Criteria** | Date within 6 months |

---

## V2: Container Architecture (25 Items)

### V2-01: Container Enumeration
| Attribute | Value |
|-----------|-------|
| **Description** | All containers/services/applications are identified |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | container, design_doc |
| **Detection** | Look for service lists, container diagrams |
| **Quality Criteria** | Every deployable unit named |

### V2-02: Technology Stack per Container
| Attribute | Value |
|-----------|-------|
| **Description** | Technology/language/framework for each container is specified |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for tech labels, stack specifications |
| **Quality Criteria** | Language + framework + runtime specified |

### V2-03: Container Responsibilities
| Attribute | Value |
|-----------|-------|
| **Description** | Each container's purpose and responsibilities are documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for responsibility descriptions per container |
| **Quality Criteria** | Clear, bounded responsibilities |

### V2-04: Inter-Container Communication
| Attribute | Value |
|-----------|-------|
| **Description** | How containers communicate with each other is documented |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | container, design_doc |
| **Detection** | Look for arrows, protocol labels between containers |
| **Quality Criteria** | Protocol and data format specified |

### V2-05: Data Store Identification
| Attribute | Value |
|-----------|-------|
| **Description** | All data stores (databases, caches, queues) are identified |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | container, design_doc |
| **Detection** | Look for database icons, storage elements |
| **Quality Criteria** | All persistent storage identified |

### V2-06: Data Store Technology
| Attribute | Value |
|-----------|-------|
| **Description** | Technology for each data store is specified |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for PostgreSQL, Redis, Kafka labels |
| **Quality Criteria** | Specific technology, not just "database" |

### V2-07: Container Boundaries/APIs
| Attribute | Value |
|-----------|-------|
| **Description** | API boundaries for each container are defined |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for API endpoint lists, interface specs |
| **Quality Criteria** | APIs documented per container |

### V2-08: Scaling Boundaries
| Attribute | Value |
|-----------|-------|
| **Description** | Which containers scale together vs independently |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for scaling unit indicators |
| **Quality Criteria** | Scaling strategy per container |

### V2-09: Container Ownership
| Attribute | Value |
|-----------|-------|
| **Description** | Team ownership per container is documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for team labels, ownership matrices |
| **Quality Criteria** | Clear ownership, no orphans |

### V2-10: Container Versioning Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How containers are versioned is documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for versioning scheme, release strategy |
| **Quality Criteria** | Semantic versioning or equivalent |

### V2-11: Authentication Between Containers
| Attribute | Value |
|-----------|-------|
| **Description** | How containers authenticate to each other |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for mTLS, service mesh, JWT references |
| **Quality Criteria** | Auth mechanism specified |

### V2-12: Data Flows Between Containers
| Attribute | Value |
|-----------|-------|
| **Description** | What data flows between containers is documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, data_flow |
| **Detection** | Look for data labels on arrows |
| **Quality Criteria** | Data entities/events named |

### V2-13: Async Communication Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Async messaging patterns are documented (pub/sub, queue, etc.) |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | container, design_doc |
| **Detection** | Look for queue icons, event bus references |
| **Quality Criteria** | Pattern and broker specified |

### V2-14: Message Broker Usage
| Attribute | Value |
|-----------|-------|
| **Description** | Message brokers/queues are identified and usage documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | container, design_doc |
| **Detection** | Look for Kafka, RabbitMQ, SQS references |
| **Quality Criteria** | Topics/queues enumerated |

### V2-15: Service Mesh Presence
| Attribute | Value |
|-----------|-------|
| **Description** | Service mesh usage is documented if applicable |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for Istio, Linkerd references |
| **Quality Criteria** | Mesh features used listed |

### V2-16: Container Runtime Environment
| Attribute | Value |
|-----------|-------|
| **Description** | Runtime environment (container, serverless, VM) specified |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | container, design_doc |
| **Detection** | Look for Docker, K8s, Lambda references |
| **Quality Criteria** | Runtime per container clear |

### V2-17: Configuration Management
| Attribute | Value |
|-----------|-------|
| **Description** | How containers are configured is documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for config maps, env vars, secrets management |
| **Quality Criteria** | Config mechanism per container |

### V2-18: Container Health Checks
| Attribute | Value |
|-----------|-------|
| **Description** | Health check endpoints/mechanisms defined |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for /health, liveness, readiness probes |
| **Quality Criteria** | Health check per container |

### V2-19: Container Resource Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | CPU/memory requirements per container |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc, deployment |
| **Detection** | Look for resource limits, sizing |
| **Quality Criteria** | Min/max resources specified |

### V2-20: Circuit Breaker Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Circuit breaker/retry patterns documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for circuit breaker, retry, timeout configs |
| **Quality Criteria** | Resilience patterns per integration |

### V2-21: Container Logging Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Logging approach per container documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for log format, aggregation references |
| **Quality Criteria** | Logging format and destination |

### V2-22: Service Discovery
| Attribute | Value |
|-----------|-------|
| **Description** | How containers discover each other |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for DNS, service registry references |
| **Quality Criteria** | Discovery mechanism specified |

### V2-23: Shared Libraries/Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | Shared code libraries across containers documented |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for shared lib references, monorepo structure |
| **Quality Criteria** | Shared dependencies listed |

### V2-24: Container Diagram Legend
| Attribute | Value |
|-----------|-------|
| **Description** | Diagram has legend explaining symbols |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | container |
| **Detection** | Look for legend box |
| **Quality Criteria** | All symbols explained |

### V2-25: Technology Choice Rationale
| Attribute | Value |
|-----------|-------|
| **Description** | Why specific technologies were chosen |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc, adr |
| **Detection** | Look for decision records, rationale sections |
| **Quality Criteria** | Rationale documented per major choice |

---

## V3: Component Design (18 Items)

### V3-01: Key Components Identified
| Attribute | Value |
|-----------|-------|
| **Description** | Major components within each container are listed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | component, design_doc |
| **Detection** | Look for component diagrams, module lists |
| **Quality Criteria** | Components per container enumerated |

### V3-02: Component Responsibilities
| Attribute | Value |
|-----------|-------|
| **Description** | Each component's responsibility is defined |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | component, design_doc |
| **Detection** | Look for responsibility descriptions |
| **Quality Criteria** | Single responsibility per component |

### V3-03: Component Interfaces
| Attribute | Value |
|-----------|-------|
| **Description** | Public interfaces of components documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | component, design_doc |
| **Detection** | Look for interface definitions |
| **Quality Criteria** | Methods/contracts specified |

### V3-04: Internal vs External Interfaces
| Attribute | Value |
|-----------|-------|
| **Description** | Distinction between internal and external interfaces |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | component |
| **Detection** | Look for public/private/internal labels |
| **Quality Criteria** | Access levels clear |

### V3-05: Domain Model Overview
| Attribute | Value |
|-----------|-------|
| **Description** | Core domain entities and relationships |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for entity diagrams, domain models |
| **Quality Criteria** | Key entities defined |

### V3-06: Design Patterns Used
| Attribute | Value |
|-----------|-------|
| **Description** | Design patterns applied are documented |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc, component |
| **Detection** | Look for pattern names (Repository, Factory, etc.) |
| **Quality Criteria** | Patterns named and justified |

### V3-07: Dependency Injection Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How dependencies are managed/injected |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for DI framework references |
| **Quality Criteria** | DI approach specified |

### V3-08: Component Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | Dependencies between components shown |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | component |
| **Detection** | Look for dependency arrows |
| **Quality Criteria** | Dependency direction clear |

### V3-09: Error Handling Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How errors are handled within components |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for error handling patterns |
| **Quality Criteria** | Error propagation documented |

### V3-10: Validation Approach
| Attribute | Value |
|-----------|-------|
| **Description** | Input validation strategy documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for validation layer references |
| **Quality Criteria** | Validation points identified |

### V3-11: Transaction Boundaries
| Attribute | Value |
|-----------|-------|
| **Description** | Transaction scope and boundaries defined |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for transaction management references |
| **Quality Criteria** | Transaction scope clear |

### V3-12: Caching Strategy (Component Level)
| Attribute | Value |
|-----------|-------|
| **Description** | Component-level caching approach |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for cache references |
| **Quality Criteria** | Cache invalidation documented |

### V3-13: Thread Safety Considerations
| Attribute | Value |
|-----------|-------|
| **Description** | Concurrency/thread safety documented |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for concurrency patterns |
| **Quality Criteria** | Thread safety approach clear |

### V3-14: Plugin/Extension Points
| Attribute | Value |
|-----------|-------|
| **Description** | Extension mechanisms documented |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for plugin architecture references |
| **Quality Criteria** | Extension points identified |

### V3-15: Component Testing Approach
| Attribute | Value |
|-----------|-------|
| **Description** | How components will be tested |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for test strategy references |
| **Quality Criteria** | Testing approach per component |

### V3-16: Abstraction Layers
| Attribute | Value |
|-----------|-------|
| **Description** | Abstraction layers (ports/adapters, etc.) documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for layer diagrams |
| **Quality Criteria** | Layer boundaries clear |

### V3-17: State Management
| Attribute | Value |
|-----------|-------|
| **Description** | How state is managed within components |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for state machine references |
| **Quality Criteria** | Stateful vs stateless clear |

### V3-18: Component Versioning
| Attribute | Value |
|-----------|-------|
| **Description** | How component versions are managed |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for versioning strategy |
| **Quality Criteria** | Version scheme documented |

---

## V4: Deployment Topology (22 Items)

### V4-01: Infrastructure Overview
| Attribute | Value |
|-----------|-------|
| **Description** | High-level infrastructure topology documented |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for infrastructure diagrams |
| **Quality Criteria** | All infrastructure elements shown |

### V4-02: Cloud Provider/Platform
| Attribute | Value |
|-----------|-------|
| **Description** | Cloud provider or platform specified |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for AWS, GCP, Azure references |
| **Quality Criteria** | Provider and region specified |

### V4-03: Container Orchestration
| Attribute | Value |
|-----------|-------|
| **Description** | Container orchestration platform documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for Kubernetes, ECS references |
| **Quality Criteria** | Orchestration platform specified |

### V4-04: Network Topology
| Attribute | Value |
|-----------|-------|
| **Description** | Network layout (VPCs, subnets, zones) documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for network diagrams |
| **Quality Criteria** | Network segments defined |

### V4-05: Scaling Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How system scales (horizontal/vertical/auto) |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for auto-scaling references |
| **Quality Criteria** | Scaling triggers defined |

### V4-06: Load Balancing
| Attribute | Value |
|-----------|-------|
| **Description** | Load balancing approach documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for LB types, algorithms |
| **Quality Criteria** | LB technology and config |

### V4-07: CDN Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | CDN usage and configuration |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for CloudFront, Cloudflare references |
| **Quality Criteria** | CDN caching rules documented |

### V4-08: DNS Configuration
| Attribute | Value |
|-----------|-------|
| **Description** | DNS strategy and configuration |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for DNS references, Route53 |
| **Quality Criteria** | DNS records documented |

### V4-09: SSL/TLS Configuration
| Attribute | Value |
|-----------|-------|
| **Description** | SSL/TLS termination and certificate management |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for certificate management references |
| **Quality Criteria** | Certificate lifecycle documented |

### V4-10: Environment Definitions
| Attribute | Value |
|-----------|-------|
| **Description** | Dev/staging/prod environments defined |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for environment lists |
| **Quality Criteria** | All environments enumerated |

### V4-11: Environment Parity
| Attribute | Value |
|-----------|-------|
| **Description** | Differences between environments documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for environment comparison |
| **Quality Criteria** | Differences explicit |

### V4-12: Deployment Process
| Attribute | Value |
|-----------|-------|
| **Description** | How deployments are executed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for CI/CD references |
| **Quality Criteria** | Deployment steps documented |

### V4-13: Blue-Green/Canary Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Deployment strategy (blue-green, canary, rolling) |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for deployment strategy references |
| **Quality Criteria** | Strategy specified |

### V4-14: Rollback Procedure
| Attribute | Value |
|-----------|-------|
| **Description** | How to rollback failed deployments |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for rollback procedures |
| **Quality Criteria** | Rollback steps documented |

### V4-15: Infrastructure as Code
| Attribute | Value |
|-----------|-------|
| **Description** | IaC approach documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for Terraform, CloudFormation references |
| **Quality Criteria** | IaC tool specified |

### V4-16: Secrets Management
| Attribute | Value |
|-----------|-------|
| **Description** | How secrets are managed in deployment |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for Vault, AWS Secrets Manager references |
| **Quality Criteria** | Secrets management documented |

### V4-17: Backup Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Data backup approach documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for backup schedule, retention |
| **Quality Criteria** | RPO/RTO documented |

### V4-18: Disaster Recovery Plan
| Attribute | Value |
|-----------|-------|
| **Description** | DR strategy and procedures |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | design_doc |
| **Detection** | Look for DR sections |
| **Quality Criteria** | RTO/RPO targets, failover process |

### V4-19: Multi-Region Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Multi-region deployment approach if applicable |
| **Severity Missing** | MEDIUM (if applicable) |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for region references |
| **Quality Criteria** | Region strategy documented |

### V4-20: Container Registry
| Attribute | Value |
|-----------|-------|
| **Description** | Where container images are stored |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | deployment |
| **Detection** | Look for ECR, GCR references |
| **Quality Criteria** | Registry specified |

### V4-21: Database Deployment
| Attribute | Value |
|-----------|-------|
| **Description** | How databases are deployed and managed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | deployment, design_doc |
| **Detection** | Look for RDS, managed DB references |
| **Quality Criteria** | DB deployment approach |

### V4-22: Capacity Planning
| Attribute | Value |
|-----------|-------|
| **Description** | Expected capacity and growth projections |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for capacity numbers |
| **Quality Criteria** | Load projections documented |

---

## V5: Data Architecture (18 Items)

### V5-01: Data Store Inventory
| Attribute | Value |
|-----------|-------|
| **Description** | All data stores comprehensively listed |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | data_flow, design_doc |
| **Detection** | Look for database lists |
| **Quality Criteria** | All data stores enumerated |

### V5-02: Data Model Overview
| Attribute | Value |
|-----------|-------|
| **Description** | High-level data model documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | data_flow, design_doc |
| **Detection** | Look for ER diagrams, data models |
| **Quality Criteria** | Core entities defined |

### V5-03: Data Ownership
| Attribute | Value |
|-----------|-------|
| **Description** | Which service owns which data |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for data ownership labels |
| **Quality Criteria** | Clear ownership per entity |

### V5-04: Data Flow Diagrams
| Attribute | Value |
|-----------|-------|
| **Description** | How data flows through the system |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | data_flow, design_doc |
| **Detection** | Look for DFD diagrams |
| **Quality Criteria** | Major flows documented |

### V5-05: Data Retention Policy
| Attribute | Value |
|-----------|-------|
| **Description** | How long data is retained |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for retention periods |
| **Quality Criteria** | Retention per data type |

### V5-06: Data Classification
| Attribute | Value |
|-----------|-------|
| **Description** | Data sensitivity classification |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for PII, PHI labels |
| **Quality Criteria** | Classification scheme applied |

### V5-07: Data Encryption at Rest
| Attribute | Value |
|-----------|-------|
| **Description** | Encryption approach for stored data |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for encryption references |
| **Quality Criteria** | Encryption method specified |

### V5-08: Data Encryption in Transit
| Attribute | Value |
|-----------|-------|
| **Description** | Encryption for data movement |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for TLS references |
| **Quality Criteria** | TLS version specified |

### V5-09: Database Schema Management
| Attribute | Value |
|-----------|-------|
| **Description** | How schema migrations are handled |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for migration tool references |
| **Quality Criteria** | Migration approach documented |

### V5-10: Event/Message Schemas
| Attribute | Value |
|-----------|-------|
| **Description** | Event schemas documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for event definitions |
| **Quality Criteria** | Schema evolution strategy |

### V5-11: Data Consistency Model
| Attribute | Value |
|-----------|-------|
| **Description** | Consistency guarantees documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for eventual consistency references |
| **Quality Criteria** | Consistency model per service |

### V5-12: Cache Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Caching approach documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for Redis, Memcached references |
| **Quality Criteria** | Cache invalidation documented |

### V5-13: Data Archival Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How old data is archived |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for archival references |
| **Quality Criteria** | Archive triggers defined |

### V5-14: Analytics/Reporting Data
| Attribute | Value |
|-----------|-------|
| **Description** | Analytics data strategy |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for data warehouse references |
| **Quality Criteria** | Analytics pipeline documented |

### V5-15: Data Quality Monitoring
| Attribute | Value |
|-----------|-------|
| **Description** | How data quality is monitored |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for data quality checks |
| **Quality Criteria** | Quality metrics defined |

### V5-16: Master Data Management
| Attribute | Value |
|-----------|-------|
| **Description** | MDM approach if applicable |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for MDM references |
| **Quality Criteria** | Master data sources identified |

### V5-17: Data Access Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Read/write patterns documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for access pattern descriptions |
| **Quality Criteria** | Hot paths identified |

### V5-18: GDPR/Data Subject Rights
| Attribute | Value |
|-----------|-------|
| **Description** | How data subject rights are handled |
| **Severity Missing** | HIGH (if applicable) |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for GDPR, right-to-delete references |
| **Quality Criteria** | Deletion/export capability |

---

## V6: Integration & APIs (15 Items)

### V6-01: API Inventory
| Attribute | Value |
|-----------|-------|
| **Description** | All APIs comprehensively listed |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | design_doc, sequence |
| **Detection** | Look for API lists |
| **Quality Criteria** | All APIs enumerated |

### V6-02: API Specification Format
| Attribute | Value |
|-----------|-------|
| **Description** | API spec format (OpenAPI, gRPC, GraphQL) |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for spec file references |
| **Quality Criteria** | Spec format documented |

### V6-03: API Versioning Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How APIs are versioned |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for /v1/, version headers |
| **Quality Criteria** | Versioning scheme documented |

### V6-04: API Authentication
| Attribute | Value |
|-----------|-------|
| **Description** | API authentication mechanisms |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for OAuth, API key references |
| **Quality Criteria** | Auth per API documented |

### V6-05: API Rate Limiting
| Attribute | Value |
|-----------|-------|
| **Description** | Rate limiting strategy |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for rate limit references |
| **Quality Criteria** | Limits per API documented |

### V6-06: API Error Handling
| Attribute | Value |
|-----------|-------|
| **Description** | Standard error response format |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for error code lists |
| **Quality Criteria** | Error schema documented |

### V6-07: Webhook/Callback Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Webhook patterns documented |
| **Severity Missing** | MEDIUM (if applicable) |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for webhook references |
| **Quality Criteria** | Webhook contracts documented |

### V6-08: Integration Sequence Diagrams
| Attribute | Value |
|-----------|-------|
| **Description** | Key integration flows documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | sequence, design_doc |
| **Detection** | Look for sequence diagrams |
| **Quality Criteria** | Critical flows documented |

### V6-09: Third-Party API Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | External API dependencies listed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for external API references |
| **Quality Criteria** | All external APIs listed |

### V6-10: API Gateway Configuration
| Attribute | Value |
|-----------|-------|
| **Description** | API gateway usage documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for gateway references |
| **Quality Criteria** | Gateway config documented |

### V6-11: Idempotency Handling
| Attribute | Value |
|-----------|-------|
| **Description** | Idempotency approach for APIs |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for idempotency keys |
| **Quality Criteria** | Idempotent operations identified |

### V6-12: API Pagination
| Attribute | Value |
|-----------|-------|
| **Description** | Pagination strategy |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for pagination parameters |
| **Quality Criteria** | Pagination scheme documented |

### V6-13: API Documentation
| Attribute | Value |
|-----------|-------|
| **Description** | Developer documentation approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for API doc references |
| **Quality Criteria** | Docs location specified |

### V6-14: Backward Compatibility Policy
| Attribute | Value |
|-----------|-------|
| **Description** | How backward compatibility is maintained |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for compatibility guarantees |
| **Quality Criteria** | Deprecation policy documented |

### V6-15: API Monitoring
| Attribute | Value |
|-----------|-------|
| **Description** | How APIs are monitored |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for API metrics references |
| **Quality Criteria** | Key metrics identified |

---

## V7: Security Architecture (25 Items)

### V7-01: Authentication Architecture
| Attribute | Value |
|-----------|-------|
| **Description** | How authentication is implemented |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | design_doc |
| **Detection** | Look for auth flow diagrams |
| **Quality Criteria** | Auth mechanism fully documented |

### V7-02: Authorization Model
| Attribute | Value |
|-----------|-------|
| **Description** | How authorization decisions are made |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | design_doc |
| **Detection** | Look for RBAC, ABAC references |
| **Quality Criteria** | Authorization model specified |

### V7-03: Identity Provider Integration
| Attribute | Value |
|-----------|-------|
| **Description** | IdP integration documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for SSO, SAML, OIDC references |
| **Quality Criteria** | IdP specified |

### V7-04: Session Management
| Attribute | Value |
|-----------|-------|
| **Description** | Session handling approach |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for session, token references |
| **Quality Criteria** | Session lifecycle documented |

### V7-05: Encryption Standards
| Attribute | Value |
|-----------|-------|
| **Description** | Encryption algorithms and key sizes |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for AES-256, RSA references |
| **Quality Criteria** | Algorithms specified |

### V7-06: Key Management
| Attribute | Value |
|-----------|-------|
| **Description** | How encryption keys are managed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for KMS references |
| **Quality Criteria** | Key rotation documented |

### V7-07: Secrets Storage
| Attribute | Value |
|-----------|-------|
| **Description** | Where secrets are stored |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for Vault, secrets manager |
| **Quality Criteria** | Secrets never in code/config |

### V7-08: Network Security
| Attribute | Value |
|-----------|-------|
| **Description** | Network security controls |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for firewall, security groups |
| **Quality Criteria** | Network controls documented |

### V7-09: API Security
| Attribute | Value |
|-----------|-------|
| **Description** | API-specific security controls |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for OWASP API references |
| **Quality Criteria** | API security measures documented |

### V7-10: Audit Logging
| Attribute | Value |
|-----------|-------|
| **Description** | Security audit logging approach |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for audit trail references |
| **Quality Criteria** | What's logged documented |

### V7-11: Input Validation
| Attribute | Value |
|-----------|-------|
| **Description** | Input validation strategy |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for validation references |
| **Quality Criteria** | Validation approach documented |

### V7-12: Output Encoding
| Attribute | Value |
|-----------|-------|
| **Description** | Output encoding for XSS prevention |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for encoding references |
| **Quality Criteria** | Encoding strategy documented |

### V7-13: SQL Injection Prevention
| Attribute | Value |
|-----------|-------|
| **Description** | SQL injection mitigation |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for parameterized query references |
| **Quality Criteria** | Prevention approach documented |

### V7-14: CSRF Protection
| Attribute | Value |
|-----------|-------|
| **Description** | CSRF mitigation approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for CSRF token references |
| **Quality Criteria** | CSRF approach documented |

### V7-15: Security Headers
| Attribute | Value |
|-----------|-------|
| **Description** | HTTP security headers |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for CSP, HSTS references |
| **Quality Criteria** | Headers listed |

### V7-16: Vulnerability Management
| Attribute | Value |
|-----------|-------|
| **Description** | How vulnerabilities are tracked |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for scanning references |
| **Quality Criteria** | Scanning approach documented |

### V7-17: Dependency Security
| Attribute | Value |
|-----------|-------|
| **Description** | Third-party dependency security |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for Snyk, Dependabot references |
| **Quality Criteria** | Dependency scanning documented |

### V7-18: Penetration Testing
| Attribute | Value |
|-----------|-------|
| **Description** | Pen testing approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for pen test references |
| **Quality Criteria** | Testing schedule documented |

### V7-19: Incident Response Plan
| Attribute | Value |
|-----------|-------|
| **Description** | Security incident response |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for IR plan references |
| **Quality Criteria** | IR process documented |

### V7-20: Data Breach Notification
| Attribute | Value |
|-----------|-------|
| **Description** | Breach notification process |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for breach notification |
| **Quality Criteria** | Notification process documented |

### V7-21: Privacy by Design
| Attribute | Value |
|-----------|-------|
| **Description** | Privacy considerations |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for privacy references |
| **Quality Criteria** | Privacy controls documented |

### V7-22: Compliance Mapping
| Attribute | Value |
|-----------|-------|
| **Description** | Regulatory compliance mapping |
| **Severity Missing** | HIGH (if regulated) |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for compliance matrix |
| **Quality Criteria** | Regulations mapped |

### V7-23: Security Training Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Team security training |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for training references |
| **Quality Criteria** | Training requirements listed |

### V7-24: Third-Party Security Assessment
| Attribute | Value |
|-----------|-------|
| **Description** | Vendor security assessment |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for vendor security references |
| **Quality Criteria** | Vendor assessment process |

### V7-25: Security Architecture Diagram
| Attribute | Value |
|-----------|-------|
| **Description** | Dedicated security view diagram |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for security diagram |
| **Quality Criteria** | Security controls visualized |

---

## V8: Operational Concerns (18 Items)

### V8-01: Monitoring Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Overall monitoring approach |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | design_doc |
| **Detection** | Look for monitoring section |
| **Quality Criteria** | Monitoring stack documented |

### V8-02: Metrics Collection
| Attribute | Value |
|-----------|-------|
| **Description** | What metrics are collected |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for metric lists |
| **Quality Criteria** | Key metrics defined |

### V8-03: Logging Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Centralized logging approach |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for logging references |
| **Quality Criteria** | Log aggregation documented |

### V8-04: Tracing Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | Distributed tracing approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for tracing references |
| **Quality Criteria** | Tracing tool specified |

### V8-05: SLO Definitions
| Attribute | Value |
|-----------|-------|
| **Description** | Service Level Objectives defined |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for SLO tables |
| **Quality Criteria** | SLOs quantified |

### V8-06: SLI Definitions
| Attribute | Value |
|-----------|-------|
| **Description** | Service Level Indicators defined |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for SLI definitions |
| **Quality Criteria** | SLIs measurable |

### V8-07: Error Budget Policy
| Attribute | Value |
|-----------|-------|
| **Description** | How error budgets are managed |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for error budget references |
| **Quality Criteria** | Policy documented |

### V8-08: Alerting Rules
| Attribute | Value |
|-----------|-------|
| **Description** | Alert conditions and thresholds |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for alert definitions |
| **Quality Criteria** | Thresholds documented |

### V8-09: On-Call Rotation
| Attribute | Value |
|-----------|-------|
| **Description** | On-call responsibilities |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for on-call references |
| **Quality Criteria** | On-call structure defined |

### V8-10: Runbook Presence
| Attribute | Value |
|-----------|-------|
| **Description** | Operational runbooks exist |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for runbook references |
| **Quality Criteria** | Runbooks for key scenarios |

### V8-11: Dashboards Defined
| Attribute | Value |
|-----------|-------|
| **Description** | Operational dashboards |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for dashboard references |
| **Quality Criteria** | Key dashboards listed |

### V8-12: Capacity Monitoring
| Attribute | Value |
|-----------|-------|
| **Description** | Resource capacity tracking |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for capacity references |
| **Quality Criteria** | Capacity metrics defined |

### V8-13: Cost Monitoring
| Attribute | Value |
|-----------|-------|
| **Description** | Infrastructure cost tracking |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for cost references |
| **Quality Criteria** | Cost attribution documented |

### V8-14: Performance Baseline
| Attribute | Value |
|-----------|-------|
| **Description** | Expected performance benchmarks |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for performance targets |
| **Quality Criteria** | Baselines quantified |

### V8-15: Maintenance Windows
| Attribute | Value |
|-----------|-------|
| **Description** | Scheduled maintenance approach |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for maintenance references |
| **Quality Criteria** | Maintenance process documented |

### V8-16: Health Check Endpoints
| Attribute | Value |
|-----------|-------|
| **Description** | Health check approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for health endpoint references |
| **Quality Criteria** | Health checks per service |

### V8-17: Incident Management Process
| Attribute | Value |
|-----------|-------|
| **Description** | How incidents are managed |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for incident process |
| **Quality Criteria** | Process documented |

### V8-18: Post-Incident Review
| Attribute | Value |
|-----------|-------|
| **Description** | Post-mortem process |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for post-mortem references |
| **Quality Criteria** | Review process documented |

---

## V9: Cross-Cutting Concerns (12 Items)

### V9-01: Logging Standards
| Attribute | Value |
|-----------|-------|
| **Description** | Standard log format |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for log format specifications |
| **Quality Criteria** | Format standardized |

### V9-02: Error Handling Pattern
| Attribute | Value |
|-----------|-------|
| **Description** | Standard error handling |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for error handling section |
| **Quality Criteria** | Pattern documented |

### V9-03: Configuration Management
| Attribute | Value |
|-----------|-------|
| **Description** | How configuration is managed |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for config references |
| **Quality Criteria** | Config approach documented |

### V9-04: Feature Flags
| Attribute | Value |
|-----------|-------|
| **Description** | Feature flag approach |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for feature flag references |
| **Quality Criteria** | Flag system documented |

### V9-05: Internationalization
| Attribute | Value |
|-----------|-------|
| **Description** | i18n approach |
| **Severity Missing** | LOW (if applicable) |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for i18n references |
| **Quality Criteria** | i18n approach documented |

### V9-06: Time Zone Handling
| Attribute | Value |
|-----------|-------|
| **Description** | Time zone strategy |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for UTC references |
| **Quality Criteria** | TZ handling documented |

### V9-07: Correlation IDs
| Attribute | Value |
|-----------|-------|
| **Description** | Request tracing IDs |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for correlation ID references |
| **Quality Criteria** | ID propagation documented |

### V9-08: Retry Patterns
| Attribute | Value |
|-----------|-------|
| **Description** | Standard retry approach |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for retry references |
| **Quality Criteria** | Retry policy documented |

### V9-09: Timeout Policies
| Attribute | Value |
|-----------|-------|
| **Description** | Standard timeout handling |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for timeout values |
| **Quality Criteria** | Timeouts documented |

### V9-10: Code Style Standards
| Attribute | Value |
|-----------|-------|
| **Description** | Coding standards |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for style guide references |
| **Quality Criteria** | Standards referenced |

### V9-11: Documentation Standards
| Attribute | Value |
|-----------|-------|
| **Description** | Doc standards |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for doc standards |
| **Quality Criteria** | Standards referenced |

### V9-12: Naming Conventions
| Attribute | Value |
|-----------|-------|
| **Description** | Naming standards |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for naming conventions |
| **Quality Criteria** | Conventions documented |

---

## V10: Decision Records (20 Items)

### V10-01: ADR Presence
| Attribute | Value |
|-----------|-------|
| **Description** | Architecture Decision Records exist |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | adr, design_doc |
| **Detection** | Look for ADR files/sections |
| **Quality Criteria** | ADRs present |

### V10-02: ADR Title
| Attribute | Value |
|-----------|-------|
| **Description** | Descriptive decision title |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for title field |
| **Quality Criteria** | Title describes decision |

### V10-03: ADR Status
| Attribute | Value |
|-----------|-------|
| **Description** | Decision status (proposed/accepted/deprecated) |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for status field |
| **Quality Criteria** | Valid status present |

### V10-04: ADR Date
| Attribute | Value |
|-----------|-------|
| **Description** | Decision date |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for date field |
| **Quality Criteria** | Date present |

### V10-05: ADR Context
| Attribute | Value |
|-----------|-------|
| **Description** | Why decision was needed |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | adr |
| **Detection** | Look for context section |
| **Quality Criteria** | Context explains need |

### V10-06: ADR Decision Statement
| Attribute | Value |
|-----------|-------|
| **Description** | What was decided |
| **Severity Missing** | CRITICAL |
| **Severity Incomplete** | HIGH |
| **Applicability** | adr |
| **Detection** | Look for decision section |
| **Quality Criteria** | Decision is clear |

### V10-07: Alternatives Considered
| Attribute | Value |
|-----------|-------|
| **Description** | Other options evaluated |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for alternatives section |
| **Quality Criteria** | Alternatives listed |

### V10-08: Consequences (Positive)
| Attribute | Value |
|-----------|-------|
| **Description** | Positive consequences documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for consequences section |
| **Quality Criteria** | Benefits listed |

### V10-09: Consequences (Negative)
| Attribute | Value |
|-----------|-------|
| **Description** | Negative consequences documented |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for consequences section |
| **Quality Criteria** | Tradeoffs listed |

### V10-10: Stakeholders/Participants
| Attribute | Value |
|-----------|-------|
| **Description** | Who participated in decision |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for participants |
| **Quality Criteria** | Participants listed |

### V10-11: Related ADRs
| Attribute | Value |
|-----------|-------|
| **Description** | Links to related decisions |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for links/references |
| **Quality Criteria** | Related ADRs linked |

### V10-12: Supersedes Reference
| Attribute | Value |
|-----------|-------|
| **Description** | What this decision supersedes |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for supersedes field |
| **Quality Criteria** | Supersedes documented |

### V10-13: Compliance Impact
| Attribute | Value |
|-----------|-------|
| **Description** | Compliance considerations |
| **Severity Missing** | MEDIUM (if regulated) |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for compliance section |
| **Quality Criteria** | Compliance impact noted |

### V10-14: Security Impact
| Attribute | Value |
|-----------|-------|
| **Description** | Security implications |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | adr |
| **Detection** | Look for security section |
| **Quality Criteria** | Security impact noted |

### V10-15: Rollback Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How to reverse decision |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for rollback section |
| **Quality Criteria** | Rollback documented |

### V10-16: Decision Coverage (Tech Selection)
| Attribute | Value |
|-----------|-------|
| **Description** | Technology selection decisions exist |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for tech selection ADRs |
| **Quality Criteria** | Major tech choices have ADRs |

### V10-17: Decision Coverage (Architecture Style)
| Attribute | Value |
|-----------|-------|
| **Description** | Architectural style decisions exist |
| **Severity Missing** | HIGH |
| **Severity Incomplete** | MEDIUM |
| **Applicability** | design_doc |
| **Detection** | Look for architecture style ADRs |
| **Quality Criteria** | Style choices documented |

### V10-18: Decision Coverage (Integration)
| Attribute | Value |
|-----------|-------|
| **Description** | Integration approach decisions exist |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | design_doc |
| **Detection** | Look for integration ADRs |
| **Quality Criteria** | Integration decisions documented |

### V10-19: ADR Review Date
| Attribute | Value |
|-----------|-------|
| **Description** | Next review date |
| **Severity Missing** | LOW |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for review date |
| **Quality Criteria** | Review scheduled |

### V10-20: ADR Sign-off
| Attribute | Value |
|-----------|-------|
| **Description** | Approval/sign-off documented |
| **Severity Missing** | MEDIUM |
| **Severity Incomplete** | LOW |
| **Applicability** | adr |
| **Detection** | Look for approval field |
| **Quality Criteria** | Approvals recorded |

---

## Summary Statistics

| Viewpoint | ID Range | Item Count | Critical Items |
|-----------|----------|------------|----------------|
| V1: Context & Scope | V1-01 to V1-15 | 15 | V1-01, V1-02, V1-03 |
| V2: Container | V2-01 to V2-25 | 25 | V2-01, V2-04, V2-05 |
| V3: Component | V3-01 to V3-18 | 18 | V3-01, V3-02, V3-03 |
| V4: Deployment | V4-01 to V4-22 | 22 | V4-01, V4-18 |
| V5: Data | V5-01 to V5-18 | 18 | V5-01, V5-02 |
| V6: Integration | V6-01 to V6-15 | 15 | V6-01 |
| V7: Security | V7-01 to V7-25 | 25 | V7-01, V7-02 |
| V8: Operations | V8-01 to V8-18 | 18 | V8-01 |
| V9: Cross-Cutting | V9-01 to V9-12 | 12 | — |
| V10: Decisions | V10-01 to V10-20 | 20 | V10-01, V10-05, V10-06 |
| **Total** | | **188** | **15** |

---

## Quick Reference: Critical Items

Items with CRITICAL severity if missing (must fix before implementation):

1. **V1-01**: System Boundary Definition
2. **V1-02**: External User Identification
3. **V1-03**: External System Identification
4. **V2-01**: Container Enumeration
5. **V2-04**: Inter-Container Communication
6. **V2-05**: Data Store Identification
7. **V4-01**: Infrastructure Overview
8. **V4-18**: Disaster Recovery Plan
9. **V5-01**: Data Store Inventory
10. **V6-01**: API Inventory
11. **V7-01**: Authentication Architecture
12. **V7-02**: Authorization Model
13. **V8-01**: Monitoring Strategy
14. **V10-01**: ADR Presence
15. **V10-05**: ADR Context
16. **V10-06**: ADR Decision Statement
