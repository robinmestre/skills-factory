# Technical Debt Indicators

This reference catalogs 25+ technical debt signals detectable through architecture documentation review. Each indicator includes detection heuristics, severity assessment, and remediation guidance.

---

## Technical Debt Categories

| Category | Indicator Count | Severity Range | Impact Area |
|----------|-----------------|----------------|-------------|
| **Architectural Debt** | 8 | HIGH-CRITICAL | System structure |
| **Documentation Debt** | 6 | MEDIUM-HIGH | Knowledge capture |
| **Infrastructure Debt** | 5 | MEDIUM-HIGH | Operations |
| **Security Debt** | 4 | HIGH-CRITICAL | Risk exposure |
| **API Debt** | 4 | MEDIUM-HIGH | Integration |

---

## Architectural Debt

### TD-A01: Shared Database Between Services

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A01 |
| **Name** | Shared Database Between Services |
| **Category** | Architectural |
| **Severity** | HIGH |
| **Viewpoints** | V2 (Container), V5 (Data) |

**Description:**
Multiple services share a single database, creating tight coupling and making independent deployment and scaling difficult.

**Detection Signals:**
- Multiple services pointing to same database in container diagram
- No data ownership boundaries defined
- Schema shared across service boundaries
- Direct SQL queries crossing service contexts

**Evidence Patterns:**
```
- "Service A and Service B both connect to UserDB"
- "Shared schema for user and order data"
- Database without clear service ownership
```

**Impact:**
- Cannot deploy services independently
- Schema changes affect multiple teams
- Database becomes bottleneck
- Testing requires full system

**Remediation Cost:** LARGE (weeks to months)

**Remediation Approach:**
1. Define data ownership per service
2. Create service-specific databases
3. Implement data synchronization patterns
4. Use event-driven data propagation

---

### TD-A02: Synchronous Coupling Across Boundaries

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A02 |
| **Name** | Synchronous Coupling Across Boundaries |
| **Category** | Architectural |
| **Severity** | MEDIUM |
| **Viewpoints** | V2 (Container), V6 (Integration) |

**Description:**
Services use synchronous (blocking) calls for operations that could be async, creating cascading failure risks.

**Detection Signals:**
- All inter-service arrows labeled as REST/HTTP
- No message queue or event bus in architecture
- Missing circuit breaker patterns
- Synchronous calls for non-critical operations

**Evidence Patterns:**
```
- "Order service calls Inventory service synchronously"
- "All communication is REST"
- No mention of async patterns
```

**Impact:**
- Cascading failures
- Latency accumulation
- Reduced resilience
- Tight temporal coupling

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Identify operations that can be async
2. Introduce message broker
3. Implement event-driven patterns
4. Add circuit breakers for sync calls

---

### TD-A03: Missing Bounded Contexts

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A03 |
| **Name** | Missing Bounded Contexts |
| **Category** | Architectural |
| **Severity** | HIGH |
| **Viewpoints** | V2 (Container), V3 (Component) |

**Description:**
No clear domain boundaries defined, leading to overlapping responsibilities and data model confusion.

**Detection Signals:**
- No domain model documented
- Services with overlapping responsibilities
- Same entities defined differently across services
- No ubiquitous language defined

**Evidence Patterns:**
```
- "User" entity appears in multiple services with different attributes
- No context mapping diagram
- Services named by technical function, not business capability
```

**Impact:**
- Feature ownership unclear
- Model inconsistencies
- Communication overhead
- Difficult to evolve independently

**Remediation Cost:** LARGE

**Remediation Approach:**
1. Run domain modeling workshops
2. Define bounded contexts
3. Create context mapping
4. Establish anti-corruption layers

---

### TD-A04: God Service

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A04 |
| **Name** | God Service |
| **Category** | Architectural |
| **Severity** | HIGH |
| **Viewpoints** | V2 (Container), V3 (Component) |

**Description:**
A single service handles too many responsibilities, becoming a deployment bottleneck and single point of failure.

**Detection Signals:**
- One service with many responsibilities listed
- Service connected to many databases
- Disproportionate team size for one service
- Service mentioned in most integration flows

**Evidence Patterns:**
```
- "Core service handles: user management, authentication, billing, notifications, reporting..."
- Service with 10+ endpoints
- Service owned by multiple teams
```

**Impact:**
- Deployment bottleneck
- Team coordination overhead
- Testing complexity
- Single point of failure

**Remediation Cost:** LARGE

**Remediation Approach:**
1. Identify responsibility boundaries
2. Extract focused services
3. Define clear APIs
4. Gradual migration with strangler pattern

---

### TD-A05: Circular Dependencies

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A05 |
| **Name** | Circular Dependencies |
| **Category** | Architectural |
| **Severity** | CRITICAL |
| **Viewpoints** | V2 (Container), V3 (Component) |

**Description:**
Services or components have circular dependencies (A→B→C→A), making deployment order difficult and creating coupling.

**Detection Signals:**
- Dependency arrows form cycles in diagrams
- Services that "both call each other"
- Build order dependencies that conflict
- Deployment must happen in specific order

**Evidence Patterns:**
```
- "Service A calls Service B, which calls Service C, which calls Service A"
- Bidirectional arrows between services
- "Deploy B before A, but A before B"
```

**Impact:**
- Deployment order impossible
- Cannot test in isolation
- Difficult to understand
- Cascading changes

**Remediation Cost:** MEDIUM-LARGE

**Remediation Approach:**
1. Identify cycles
2. Extract shared functionality
3. Use event-driven decoupling
4. Introduce intermediary service

---

### TD-A06: Missing Abstraction Layers

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A06 |
| **Name** | Missing Abstraction Layers |
| **Category** | Architectural |
| **Severity** | MEDIUM |
| **Viewpoints** | V2 (Container), V3 (Component) |

**Description:**
Direct dependencies on infrastructure or third-party services without abstraction, making changes difficult.

**Detection Signals:**
- Direct cloud service calls without wrappers
- Database technology directly in business logic
- Third-party SDK usage without facade
- No port/adapter pattern

**Evidence Patterns:**
```
- "Service directly calls AWS S3 API"
- "Business logic contains SQL queries"
- "Stripe SDK used throughout codebase"
```

**Impact:**
- Vendor lock-in
- Difficult to test
- Hard to replace services
- Technology changes ripple through

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Identify direct dependencies
2. Create abstraction interfaces
3. Implement adapters
4. Inject dependencies

---

### TD-A07: Hardcoded Configuration

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A07 |
| **Name** | Hardcoded Configuration |
| **Category** | Architectural |
| **Severity** | MEDIUM |
| **Viewpoints** | V4 (Deployment), V9 (Cross-Cutting) |

**Description:**
Configuration values (URLs, credentials, feature flags) hardcoded instead of externalized.

**Detection Signals:**
- No configuration management documented
- Environment URLs in code references
- No mention of config maps or env vars
- Same codebase for all environments without config

**Evidence Patterns:**
```
- No configuration section in architecture doc
- "Uses localhost:5432 for database"
- Environment-specific values visible in docs
```

**Impact:**
- Cannot change without redeploy
- Environment parity issues
- Secrets possibly in code
- Difficult ops management

**Remediation Cost:** SMALL-MEDIUM

**Remediation Approach:**
1. Audit hardcoded values
2. Externalize to config
3. Use config management tool
4. Document configuration approach

---

### TD-A08: No API Gateway

| Attribute | Value |
|-----------|-------|
| **ID** | TD-A08 |
| **Name** | No API Gateway |
| **Category** | Architectural |
| **Severity** | MEDIUM |
| **Viewpoints** | V2 (Container), V6 (Integration) |

**Description:**
Direct client-to-service communication without an API gateway for cross-cutting concerns.

**Detection Signals:**
- Clients connecting directly to multiple services
- Auth implemented in each service
- No centralized rate limiting
- No request routing layer

**Evidence Patterns:**
```
- "Web app calls Service A, Service B, Service C directly"
- Auth mentioned in each service description
- No gateway in container diagram
```

**Impact:**
- Duplicated cross-cutting concerns
- No centralized observability
- Complex client logic
- Difficult to add new concerns

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Introduce API gateway
2. Centralize auth
3. Add rate limiting
4. Implement request routing

---

## Documentation Debt

### TD-D01: Stale Architecture Diagrams

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D01 |
| **Name** | Stale Architecture Diagrams |
| **Category** | Documentation |
| **Severity** | MEDIUM |
| **Viewpoints** | All |

**Description:**
Diagrams are outdated and don't reflect current system state.

**Detection Signals:**
- Diagram dates > 6 months old
- References to deprecated services
- Missing recently added components
- Inconsistencies between text and diagrams

**Evidence Patterns:**
```
- "Diagram created: January 2023" (now December 2024)
- References "Legacy Service" that was decommissioned
- New Payment Service not shown
```

**Impact:**
- Misleading documentation
- Onboarding confusion
- Wrong decisions based on outdated info
- Technical debt accumulation

**Remediation Cost:** SMALL

**Remediation Approach:**
1. Audit diagram currency
2. Update to current state
3. Add date/version to diagrams
4. Establish refresh cadence

---

### TD-D02: Missing ADRs for Key Decisions

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D02 |
| **Name** | Missing ADRs for Key Decisions |
| **Category** | Documentation |
| **Severity** | HIGH |
| **Viewpoints** | V10 (Decisions) |

**Description:**
Major architectural decisions made without documenting the rationale.

**Detection Signals:**
- Technology choices without explanation
- No ADR files or section
- "We chose X" without "because"
- No alternatives mentioned

**Evidence Patterns:**
```
- "Using PostgreSQL" without explaining why
- No ADR directory
- Major technology choice undocumented
```

**Impact:**
- Cannot understand past decisions
- May repeat mistakes
- Difficult to evaluate changes
- Knowledge leaves with people

**Remediation Cost:** MEDIUM (ongoing)

**Remediation Approach:**
1. Retroactively document key decisions
2. Establish ADR process
3. Link decisions to implementation
4. Regular ADR review

---

### TD-D03: Undocumented Interfaces

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D03 |
| **Name** | Undocumented Interfaces |
| **Category** | Documentation |
| **Severity** | HIGH |
| **Viewpoints** | V3 (Component), V6 (Integration) |

**Description:**
Service interfaces (APIs, events, contracts) not formally documented.

**Detection Signals:**
- No API specification files
- Interface described only in prose
- No event schema documentation
- Contract testing not possible

**Evidence Patterns:**
```
- "Service exposes REST API" without spec
- No OpenAPI/Swagger reference
- Events mentioned without schema
```

**Impact:**
- Integration errors
- Consumer confusion
- Cannot generate clients
- Testing difficult

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Create API specifications
2. Document event schemas
3. Establish spec-first approach
4. Generate documentation

---

### TD-D04: Inconsistent Terminology

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D04 |
| **Name** | Inconsistent Terminology |
| **Category** | Documentation |
| **Severity** | MEDIUM |
| **Viewpoints** | All |

**Description:**
Same concepts referred to by different names across documentation.

**Detection Signals:**
- Entity called different names in different sections
- Service renamed but old name still used
- Domain terms used inconsistently
- No glossary

**Evidence Patterns:**
```
- "User" in one section, "Customer" in another, "Account" in third
- "Order Service" vs "Ordering Service" vs "Orders"
- No ubiquitous language
```

**Impact:**
- Communication confusion
- Wrong integrations
- Onboarding difficulty
- Misaligned mental models

**Remediation Cost:** SMALL

**Remediation Approach:**
1. Create glossary
2. Standardize terms
3. Search and replace
4. Establish naming conventions

---

### TD-D05: No Operational Documentation

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D05 |
| **Name** | No Operational Documentation |
| **Category** | Documentation |
| **Severity** | HIGH |
| **Viewpoints** | V8 (Operations) |

**Description:**
Runbooks, playbooks, and operational procedures not documented.

**Detection Signals:**
- No runbook references
- Operations section empty
- Incident response undefined
- On-call procedures missing

**Evidence Patterns:**
```
- "Operations: TBD"
- No runbook directory
- Incident process not mentioned
```

**Impact:**
- Slow incident response
- Knowledge silos
- Inconsistent operations
- Burnout risk

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Document common procedures
2. Create runbooks for incidents
3. Establish on-call rotation
4. Post-incident documentation

---

### TD-D06: Missing Non-Functional Requirements

| Attribute | Value |
|-----------|-------|
| **ID** | TD-D06 |
| **Name** | Missing Non-Functional Requirements |
| **Category** | Documentation |
| **Severity** | HIGH |
| **Viewpoints** | V4, V7, V8 |

**Description:**
Non-functional requirements (performance, security, reliability) not documented.

**Detection Signals:**
- No SLO section
- Performance requirements absent
- Security requirements vague
- No capacity projections

**Evidence Patterns:**
```
- "System should be fast" without metrics
- No availability target
- Security: "Will be secure"
```

**Impact:**
- Cannot validate system
- Unclear success criteria
- Scope creep on NFRs
- Inadequate architecture

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Define SLOs
2. Specify performance requirements
3. Document security requirements
4. Create NFR checklist

---

## Infrastructure Debt

### TD-I01: Missing Disaster Recovery Plan

| Attribute | Value |
|-----------|-------|
| **ID** | TD-I01 |
| **Name** | Missing Disaster Recovery Plan |
| **Category** | Infrastructure |
| **Severity** | CRITICAL |
| **Viewpoints** | V4 (Deployment), V8 (Operations) |

**Description:**
No documented disaster recovery strategy or procedures.

**Detection Signals:**
- No DR section
- RTO/RPO undefined
- Backup strategy missing
- Failover process undocumented

**Evidence Patterns:**
```
- "DR: TBD"
- No RTO/RPO mentioned
- Single region deployment without backup
```

**Impact:**
- Extended outages
- Data loss risk
- Compliance violations
- Business continuity risk

**Remediation Cost:** LARGE

**Remediation Approach:**
1. Define RTO/RPO targets
2. Design DR architecture
3. Document failover procedures
4. Test DR regularly

---

### TD-I02: Manual Deployment Steps

| Attribute | Value |
|-----------|-------|
| **ID** | TD-I02 |
| **Name** | Manual Deployment Steps |
| **Category** | Infrastructure |
| **Severity** | MEDIUM |
| **Viewpoints** | V4 (Deployment) |

**Description:**
Deployment process includes manual steps that should be automated.

**Detection Signals:**
- "SSH to server" in deployment
- Manual database migrations
- Config changes by hand
- No CI/CD pipeline mentioned

**Evidence Patterns:**
```
- "Run these commands on production server"
- "Manually update config file"
- No pipeline documentation
```

**Impact:**
- Human error risk
- Slow deployments
- Inconsistent environments
- Cannot rollback easily

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Implement CI/CD pipeline
2. Automate all deployments
3. Infrastructure as Code
4. Remove manual steps

---

### TD-I03: No Infrastructure as Code

| Attribute | Value |
|-----------|-------|
| **ID** | TD-I03 |
| **Name** | No Infrastructure as Code |
| **Category** | Infrastructure |
| **Severity** | MEDIUM |
| **Viewpoints** | V4 (Deployment) |

**Description:**
Infrastructure provisioned manually or through console, not codified.

**Detection Signals:**
- No Terraform/CloudFormation mentioned
- Infrastructure described but not coded
- Manual cloud console usage
- Environment drift mentioned

**Evidence Patterns:**
```
- "Create EC2 instance through AWS console"
- No IaC tool referenced
- Infrastructure section is prose only
```

**Impact:**
- Cannot reproduce environments
- Configuration drift
- No audit trail
- Slow provisioning

**Remediation Cost:** MEDIUM-LARGE

**Remediation Approach:**
1. Choose IaC tool
2. Import existing infrastructure
3. Codify all resources
4. Version control infrastructure

---

### TD-I04: Single Point of Failure

| Attribute | Value |
|-----------|-------|
| **ID** | TD-I04 |
| **Name** | Single Point of Failure |
| **Category** | Infrastructure |
| **Severity** | HIGH |
| **Viewpoints** | V4 (Deployment), V8 (Operations) |

**Description:**
Critical components have no redundancy.

**Detection Signals:**
- Single instance of critical service
- No load balancer
- Single database without replica
- One availability zone

**Evidence Patterns:**
```
- "Single PostgreSQL instance"
- No mention of redundancy
- One AZ deployment
```

**Impact:**
- Outage on any failure
- No maintenance window
- Capacity ceiling
- SLA risk

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Identify SPOFs
2. Add redundancy
3. Configure failover
4. Test resilience

---

### TD-I05: Missing Monitoring and Alerting

| Attribute | Value |
|-----------|-------|
| **ID** | TD-I05 |
| **Name** | Missing Monitoring and Alerting |
| **Category** | Infrastructure |
| **Severity** | HIGH |
| **Viewpoints** | V8 (Operations) |

**Description:**
No monitoring strategy or alerting configured.

**Detection Signals:**
- No monitoring section
- No metrics defined
- Alert rules missing
- Dashboards not mentioned

**Evidence Patterns:**
```
- "Monitoring: TBD"
- No metrics listed
- No alerting rules
```

**Impact:**
- Blind to issues
- Slow incident detection
- Cannot measure SLOs
- Reactive operations

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Define key metrics
2. Set up monitoring tool
3. Create alert rules
4. Build dashboards

---

## Security Debt

### TD-S01: Credentials in Configuration

| Attribute | Value |
|-----------|-------|
| **ID** | TD-S01 |
| **Name** | Credentials in Configuration |
| **Category** | Security |
| **Severity** | CRITICAL |
| **Viewpoints** | V7 (Security), V4 (Deployment) |

**Description:**
Secrets, credentials, or API keys in code, config files, or documentation.

**Detection Signals:**
- No secrets management mentioned
- Config samples with real-looking credentials
- No mention of Vault/KMS
- .env files without protection

**Evidence Patterns:**
```
- "DB_PASSWORD=mysecretpassword"
- No secrets management in architecture
- API keys visible in examples
```

**Impact:**
- Credential exposure
- Compliance violation
- Security breach risk
- Audit failure

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Audit for exposed secrets
2. Implement secrets management
3. Rotate compromised credentials
4. Remove from history

---

### TD-S02: No Authentication Between Services

| Attribute | Value |
|-----------|-------|
| **ID** | TD-S02 |
| **Name** | No Authentication Between Services |
| **Category** | Security |
| **Severity** | HIGH |
| **Viewpoints** | V7 (Security), V2 (Container) |

**Description:**
Internal services communicate without authentication.

**Detection Signals:**
- No service-to-service auth mentioned
- Trust based on network location
- No mTLS or service mesh
- "Internal network is secure"

**Evidence Patterns:**
```
- Services call each other without auth
- "Secured by VPC"
- No service identity
```

**Impact:**
- Lateral movement risk
- No zero trust
- Audit gaps
- Compliance issues

**Remediation Cost:** MEDIUM-LARGE

**Remediation Approach:**
1. Implement service mesh or mTLS
2. Add service identity
3. Enforce auth on all calls
4. Log service-to-service calls

---

### TD-S03: Missing Audit Logging

| Attribute | Value |
|-----------|-------|
| **ID** | TD-S03 |
| **Name** | Missing Audit Logging |
| **Category** | Security |
| **Severity** | HIGH |
| **Viewpoints** | V7 (Security), V8 (Operations) |

**Description:**
Security-relevant events not logged for audit purposes.

**Detection Signals:**
- No audit logging section
- Only technical logs mentioned
- No compliance logging
- Cannot answer "who did what"

**Evidence Patterns:**
```
- Logging only for debugging
- No security event logging
- No audit trail requirements
```

**Impact:**
- Cannot investigate incidents
- Compliance violations
- No forensic capability
- No deterrence

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Define audit events
2. Implement audit logging
3. Secure log storage
4. Retention policy

---

### TD-S04: No Security Testing

| Attribute | Value |
|-----------|-------|
| **ID** | TD-S04 |
| **Name** | No Security Testing |
| **Category** | Security |
| **Severity** | HIGH |
| **Viewpoints** | V7 (Security) |

**Description:**
No security testing (SAST, DAST, pen testing) documented.

**Detection Signals:**
- No security testing section
- No SAST/DAST tools mentioned
- No pen testing schedule
- Dependency scanning absent

**Evidence Patterns:**
```
- "Security testing: TBD"
- No Snyk/SonarQube mentioned
- No pen test schedule
```

**Impact:**
- Unknown vulnerabilities
- Late discovery of issues
- Compliance gaps
- Security tech debt grows

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Add SAST to pipeline
2. Implement DAST
3. Schedule pen testing
4. Dependency scanning

---

## API Debt

### TD-P01: No API Versioning

| Attribute | Value |
|-----------|-------|
| **ID** | TD-P01 |
| **Name** | No API Versioning |
| **Category** | API |
| **Severity** | HIGH |
| **Viewpoints** | V6 (Integration) |

**Description:**
APIs have no versioning strategy, making evolution difficult.

**Detection Signals:**
- No version in URLs or headers
- No versioning strategy documented
- Breaking changes mentioned as problems
- No deprecation policy

**Evidence Patterns:**
```
- "/api/users" without version
- No versioning approach mentioned
- "Had to break API for feature"
```

**Impact:**
- Breaking changes affect consumers
- Cannot evolve safely
- Consumer coordination required
- Technical debt accumulates

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Define versioning strategy
2. Add version to existing APIs
3. Establish deprecation policy
4. Document migration guides

---

### TD-P02: Inconsistent API Design

| Attribute | Value |
|-----------|-------|
| **ID** | TD-P02 |
| **Name** | Inconsistent API Design |
| **Category** | API |
| **Severity** | MEDIUM |
| **Viewpoints** | V6 (Integration) |

**Description:**
APIs across services follow different conventions.

**Detection Signals:**
- Different naming conventions
- Inconsistent error formats
- Mixed pagination approaches
- No API style guide

**Evidence Patterns:**
```
- "/getUsers" vs "/users" vs "/user/list"
- Different error schemas per service
- No API guidelines referenced
```

**Impact:**
- Consumer confusion
- Integration overhead
- Documentation burden
- Maintenance cost

**Remediation Cost:** MEDIUM-LARGE

**Remediation Approach:**
1. Define API style guide
2. Create linting rules
3. Standardize existing APIs
4. Review process for new APIs

---

### TD-P03: Missing API Documentation

| Attribute | Value |
|-----------|-------|
| **ID** | TD-P03 |
| **Name** | Missing API Documentation |
| **Category** | API |
| **Severity** | HIGH |
| **Viewpoints** | V6 (Integration) |

**Description:**
APIs not documented or documentation is inadequate.

**Detection Signals:**
- No OpenAPI/Swagger files
- Documentation is prose only
- No examples provided
- Error codes not documented

**Evidence Patterns:**
```
- "API available" without spec
- No reference to API docs
- Code is the documentation
```

**Impact:**
- Consumer onboarding slow
- Integration errors
- Support burden
- Cannot generate clients

**Remediation Cost:** MEDIUM

**Remediation Approach:**
1. Create OpenAPI specs
2. Add examples
3. Document errors
4. Generate documentation

---

### TD-P04: No Rate Limiting

| Attribute | Value |
|-----------|-------|
| **ID** | TD-P04 |
| **Name** | No Rate Limiting |
| **Category** | API |
| **Severity** | MEDIUM |
| **Viewpoints** | V6 (Integration), V7 (Security) |

**Description:**
APIs have no rate limiting or throttling.

**Detection Signals:**
- No rate limits documented
- No throttling mentioned
- No quota management
- API gateway without limits

**Evidence Patterns:**
```
- Rate limiting not mentioned
- "Open API" without limits
- No quota system
```

**Impact:**
- DoS vulnerability
- Resource exhaustion
- Noisy neighbor problems
- Cost overruns

**Remediation Cost:** SMALL-MEDIUM

**Remediation Approach:**
1. Define rate limits
2. Implement at gateway
3. Document limits
4. Add quota management

---

## Debt Severity Matrix

| Severity | Impact | Response Time | Examples |
|----------|--------|---------------|----------|
| **CRITICAL** | Blocks operations or creates major risk | Immediate | TD-I01, TD-S01, TD-A05 |
| **HIGH** | Significant impact on quality/velocity | Within sprint | TD-A01, TD-D02, TD-S02 |
| **MEDIUM** | Degrades quality over time | Within quarter | TD-A02, TD-D01, TD-P02 |
| **LOW** | Minor inconvenience | When convenient | Documentation formatting |

---

## Remediation Cost Guide

| Cost Level | Time Range | Characteristics |
|------------|------------|-----------------|
| **TRIVIAL** | < 1 day | Documentation update, simple config |
| **SMALL** | 1-3 days | Focused code change, simple tool integration |
| **MEDIUM** | 1-2 weeks | Multiple services affected, some testing |
| **LARGE** | Weeks to months | Architectural change, data migration |

---

## References

- [Managing Technical Debt](https://www.amazon.com/Managing-Technical-Debt-Reducing-Development/dp/013564593X)
- [Technical Debt Quadrant](https://martinfowler.com/bliki/TechnicalDebtQuadrant.html)
- [Architecture Decision Records](https://adr.github.io/)
