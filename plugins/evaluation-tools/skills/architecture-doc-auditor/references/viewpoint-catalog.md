# Architecture Viewpoint Catalog

This catalog defines the 14 architecture viewpoints used by the Architecture Documentation Auditor: 10 core viewpoints (always assessed) and 4 conditional viewpoints (assessed when applicable).

---

## Viewpoint Framework Overview

| ID | Viewpoint | Category | Items | Maps To |
|----|-----------|----------|-------|---------|
| V1 | Context & Scope | Core | 15 | C4 Context, 4+1 Scenarios |
| V2 | Container Architecture | Core | 25 | C4 Container, 4+1 Logical |
| V3 | Component Design | Core | 18 | C4 Component, 4+1 Development |
| V4 | Deployment Topology | Core | 22 | C4 Deployment, 4+1 Physical |
| V5 | Data Architecture | Core | 18 | arc42 Section 5 |
| V6 | Integration & APIs | Core | 15 | arc42 Section 6 |
| V7 | Security Architecture | Core | 25 | ISO 27001 |
| V8 | Operational Concerns | Core | 18 | SRE/DevOps |
| V9 | Cross-Cutting Concerns | Core | 12 | arc42 Section 8 |
| V10 | Decision Record | Core | 20 | ADR/MADR |
| V11 | Multi-tenancy | Conditional | 10 | SaaS patterns |
| V12 | Event Architecture | Conditional | 12 | EDA patterns |
| V13 | Migration Path | Conditional | 10 | Strangler Fig |
| V14 | Compliance Matrix | Conditional | 15 | SOC2/GDPR/PCI |

---

## Core Viewpoints

### V1: Context & Scope

**Purpose:** Define the system boundary and its relationship with external entities.

| Attribute | Value |
|-----------|-------|
| **ID** | V1 |
| **Name** | Context & Scope |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 15 (V1-01 to V1-15) |
| **Framework Mapping** | C4 System Context, 4+1 Scenarios/Use Cases |

**Stakeholder Concerns:**
- What does the system do?
- Who uses it?
- What does it connect to?
- What data flows in and out?
- Where are the trust boundaries?

**Required Artifacts:**
- System context diagram
- External actor/user list
- External system inventory
- Integration summary

**Validation Criteria:**
- [ ] System boundary clearly delineated
- [ ] All external users/actors identified
- [ ] All external systems listed
- [ ] Communication protocols specified
- [ ] Data flow directions shown
- [ ] Trust boundaries marked

**Common Gaps:**
- Missing external systems (especially monitoring, logging)
- Undefined trust boundaries
- Vague system purpose
- Missing authentication flows to external parties

**Quality Attributes Covered:**
- Interoperability (PRIMARY)
- Security (SECONDARY)

---

### V2: Container Architecture

**Purpose:** Document the high-level technology decisions and major components.

| Attribute | Value |
|-----------|-------|
| **ID** | V2 |
| **Name** | Container Architecture |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 25 (V2-01 to V2-25) |
| **Framework Mapping** | C4 Container, 4+1 Logical View |

**Stakeholder Concerns:**
- What are the major deployable units?
- What technology is each built with?
- How do they communicate?
- Where is data stored?
- How does authentication work between services?

**Required Artifacts:**
- Container diagram
- Technology stack documentation
- Service inventory
- Database inventory
- Communication matrix

**Validation Criteria:**
- [ ] All containers/services enumerated
- [ ] Technology choices per container documented
- [ ] Container responsibilities defined
- [ ] Inter-container communication specified
- [ ] Data stores identified with technology

**Common Gaps:**
- Technology choices without rationale
- Missing async communication patterns
- Undefined container boundaries
- Unclear scaling units

**Quality Attributes Covered:**
- Scalability (PRIMARY)
- Maintainability (SECONDARY)
- Portability (SECONDARY)

---

### V3: Component Design

**Purpose:** Document the internal structure of containers.

| Attribute | Value |
|-----------|-------|
| **ID** | V3 |
| **Name** | Component Design |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 18 (V3-01 to V3-18) |
| **Framework Mapping** | C4 Component, 4+1 Development View |

**Stakeholder Concerns:**
- What are the key modules/components?
- How are responsibilities divided?
- What are the internal interfaces?
- What design patterns are used?

**Required Artifacts:**
- Component diagrams (per container)
- Interface definitions
- Domain model
- Design pattern documentation

**Validation Criteria:**
- [ ] Key components identified per container
- [ ] Component responsibilities clear
- [ ] Interfaces documented
- [ ] Dependencies shown

**Common Gaps:**
- Only high-level without component detail
- Missing interface contracts
- Unclear transaction boundaries
- No design pattern documentation

**Quality Attributes Covered:**
- Maintainability (PRIMARY)
- Testability (SECONDARY)

---

### V4: Deployment Topology

**Purpose:** Document infrastructure and deployment approach.

| Attribute | Value |
|-----------|-------|
| **ID** | V4 |
| **Name** | Deployment Topology |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 22 (V4-01 to V4-22) |
| **Framework Mapping** | C4 Deployment, 4+1 Physical View |

**Stakeholder Concerns:**
- Where does the system run?
- How is it deployed?
- How does it scale?
- What happens when things fail?
- How do we recover from disasters?

**Required Artifacts:**
- Infrastructure diagram
- Deployment diagram
- Environment specifications
- DR/backup documentation

**Validation Criteria:**
- [ ] Infrastructure topology documented
- [ ] Cloud provider/platform specified
- [ ] Scaling strategy defined
- [ ] Environments enumerated
- [ ] DR plan documented

**Common Gaps:**
- Missing DR strategy (CRITICAL)
- Environment differences undocumented
- No rollback procedure
- Scaling triggers undefined

**Quality Attributes Covered:**
- Reliability (PRIMARY)
- Scalability (PRIMARY)
- Performance (SECONDARY)

---

### V5: Data Architecture

**Purpose:** Document data stores, flows, and governance.

| Attribute | Value |
|-----------|-------|
| **ID** | V5 |
| **Name** | Data Architecture |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 18 (V5-01 to V5-18) |
| **Framework Mapping** | arc42 Section 5, Data Flow Diagrams |

**Stakeholder Concerns:**
- Where is data stored?
- How does data flow through the system?
- Who owns which data?
- How long is data retained?
- How is sensitive data protected?

**Required Artifacts:**
- Data store inventory
- Data flow diagrams
- Data model (high-level)
- Retention policies

**Validation Criteria:**
- [ ] All data stores listed
- [ ] Data ownership clear
- [ ] Data flows documented
- [ ] Retention policies defined
- [ ] Encryption documented

**Common Gaps:**
- Data ownership unclear
- Missing retention policies
- No data classification
- Encryption undocumented

**Quality Attributes Covered:**
- Security (PRIMARY)
- Performance (SECONDARY)
- Compliance (SECONDARY)

---

### V6: Integration & APIs

**Purpose:** Document APIs and integration patterns.

| Attribute | Value |
|-----------|-------|
| **ID** | V6 |
| **Name** | Integration & APIs |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 15 (V6-01 to V6-15) |
| **Framework Mapping** | arc42 Section 6, API Documentation |

**Stakeholder Concerns:**
- What APIs does the system expose?
- What APIs does it consume?
- How are APIs versioned?
- How is authentication handled?
- What integration patterns are used?

**Required Artifacts:**
- API inventory
- API specifications (OpenAPI, etc.)
- Sequence diagrams
- Integration patterns documentation

**Validation Criteria:**
- [ ] All APIs enumerated
- [ ] API spec format defined
- [ ] Versioning strategy documented
- [ ] Authentication per API clear
- [ ] Key flows diagrammed

**Common Gaps:**
- Missing versioning strategy
- No backward compatibility policy
- Rate limiting undocumented
- Error handling inconsistent

**Quality Attributes Covered:**
- Interoperability (PRIMARY)
- Usability (SECONDARY)

---

### V7: Security Architecture

**Purpose:** Document security controls and compliance.

| Attribute | Value |
|-----------|-------|
| **ID** | V7 |
| **Name** | Security Architecture |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 25 (V7-01 to V7-25) |
| **Framework Mapping** | ISO 27001, OWASP |

**Stakeholder Concerns:**
- How is authentication implemented?
- How are authorization decisions made?
- How is data protected?
- How are secrets managed?
- What compliance requirements apply?

**Required Artifacts:**
- Security architecture diagram
- Authentication flow diagrams
- Authorization model documentation
- Encryption documentation
- Compliance matrix

**Validation Criteria:**
- [ ] Authentication architecture documented
- [ ] Authorization model specified
- [ ] Encryption standards defined
- [ ] Secrets management documented
- [ ] Audit logging defined

**Common Gaps:**
- Missing authorization model (CRITICAL)
- Secrets in code/config
- No incident response plan
- Compliance mapping absent

**Quality Attributes Covered:**
- Security (PRIMARY)
- Compliance (PRIMARY)

---

### V8: Operational Concerns

**Purpose:** Document monitoring, alerting, and operational procedures.

| Attribute | Value |
|-----------|-------|
| **ID** | V8 |
| **Name** | Operational Concerns |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 18 (V8-01 to V8-18) |
| **Framework Mapping** | SRE Practices, DevOps |

**Stakeholder Concerns:**
- How do we know if the system is healthy?
- What are our reliability targets?
- How do we respond to incidents?
- What operational procedures exist?

**Required Artifacts:**
- Monitoring strategy
- SLO/SLI definitions
- Alerting rules
- Runbooks
- Incident response plan

**Validation Criteria:**
- [ ] Monitoring strategy documented
- [ ] SLOs defined with numbers
- [ ] Alerting rules specified
- [ ] Runbooks exist for key scenarios
- [ ] Incident process documented

**Common Gaps:**
- No SLO definitions (HIGH)
- Missing monitoring strategy (CRITICAL)
- No runbooks
- Alerting rules undefined

**Quality Attributes Covered:**
- Reliability (PRIMARY)
- Operability (PRIMARY)

---

### V9: Cross-Cutting Concerns

**Purpose:** Document patterns that apply across the system.

| Attribute | Value |
|-----------|-------|
| **ID** | V9 |
| **Name** | Cross-Cutting Concerns |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 12 (V9-01 to V9-12) |
| **Framework Mapping** | arc42 Section 8 |

**Stakeholder Concerns:**
- How is logging standardized?
- How is configuration managed?
- What are the retry/timeout policies?
- How are errors handled consistently?

**Required Artifacts:**
- Logging standards
- Configuration management approach
- Error handling patterns
- Resilience patterns

**Validation Criteria:**
- [ ] Logging standards documented
- [ ] Configuration approach clear
- [ ] Error handling pattern defined
- [ ] Retry/timeout policies documented

**Common Gaps:**
- Inconsistent logging format
- No standard error codes
- Timeout policies undefined
- Configuration scattered

**Quality Attributes Covered:**
- Maintainability (PRIMARY)
- Operability (SECONDARY)

---

### V10: Decision Record

**Purpose:** Document architectural decisions and their rationale.

| Attribute | Value |
|-----------|-------|
| **ID** | V10 |
| **Name** | Decision Record |
| **Category** | Core (Always Assess) |
| **Checklist Items** | 20 (V10-01 to V10-20) |
| **Framework Mapping** | ADR, MADR, arc42 Section 9 |

**Stakeholder Concerns:**
- What key decisions were made?
- Why were they made?
- What alternatives were considered?
- What are the consequences?

**Required Artifacts:**
- Architecture Decision Records (ADRs)
- Decision log
- Alternative analysis

**Validation Criteria:**
- [ ] ADRs exist for key decisions
- [ ] Context explains why decision was needed
- [ ] Decision statement is clear
- [ ] Alternatives were considered
- [ ] Consequences documented

**Common Gaps:**
- Missing ADRs (CRITICAL)
- No alternatives documented
- Consequences not listed
- No stakeholder sign-off

**Quality Attributes Covered:**
- Maintainability (PRIMARY)
- Documentation Quality (PRIMARY)

---

## Conditional Viewpoints

### V11: Multi-tenancy

**Purpose:** Document tenant isolation and multi-tenant patterns.

| Attribute | Value |
|-----------|-------|
| **ID** | V11 |
| **Name** | Multi-tenancy |
| **Category** | Conditional |
| **When Required** | SaaS applications, multi-tenant systems |
| **Checklist Items** | 10 |
| **Trigger Detection** | "tenant", "multi-tenant", "SaaS", "B2B platform" |

**Required When:**
- System serves multiple tenants/customers
- Data isolation between customers required
- Per-tenant configuration needed

**Checklist Items:**
```
V11-01: Tenant isolation model (silo/pool/bridge)
V11-02: Data isolation approach
V11-03: Tenant onboarding process
V11-04: Tenant identification mechanism
V11-05: Per-tenant configuration
V11-06: Tenant-specific customization
V11-07: Cross-tenant data access controls
V11-08: Tenant resource limits
V11-09: Tenant billing/metering
V11-10: Tenant offboarding process
```

**Common Gaps:**
- Unclear isolation model
- Missing tenant identification in flows
- No resource limits per tenant

---

### V12: Event Architecture

**Purpose:** Document event-driven patterns and event flows.

| Attribute | Value |
|-----------|-------|
| **ID** | V12 |
| **Name** | Event Architecture |
| **Category** | Conditional |
| **When Required** | Event-driven systems, async-heavy architectures |
| **Checklist Items** | 12 |
| **Trigger Detection** | "event-driven", "Kafka", "pub/sub", "CQRS", "event sourcing" |

**Required When:**
- System uses event-driven architecture
- Significant async communication
- Event sourcing patterns used

**Checklist Items:**
```
V12-01: Event catalog/registry
V12-02: Event schema definitions
V12-03: Event versioning strategy
V12-04: Event ordering guarantees
V12-05: Event delivery guarantees
V12-06: Dead letter queue strategy
V12-07: Event replay capability
V12-08: Event-driven saga patterns
V12-09: Event storage/retention
V12-10: Event correlation patterns
V12-11: Event monitoring
V12-12: Event schema evolution
```

**Common Gaps:**
- No event catalog
- Schema evolution undefined
- Missing delivery guarantees

---

### V13: Migration Path

**Purpose:** Document migration strategy from legacy systems.

| Attribute | Value |
|-----------|-------|
| **ID** | V13 |
| **Name** | Migration Path |
| **Category** | Conditional |
| **When Required** | Legacy modernization, system replacement |
| **Checklist Items** | 10 |
| **Trigger Detection** | "migration", "legacy", "modernization", "strangler", "lift and shift" |

**Required When:**
- Replacing an existing system
- Modernizing legacy architecture
- Phased rollout from old to new

**Checklist Items:**
```
V13-01: Current state documentation
V13-02: Target state documentation
V13-03: Migration strategy (strangler/big bang/parallel)
V13-04: Data migration plan
V13-05: Cutover criteria
V13-06: Rollback plan
V13-07: Coexistence approach
V13-08: Feature parity tracking
V13-09: Migration timeline
V13-10: Risk mitigation during migration
```

**Common Gaps:**
- No rollback plan
- Coexistence undefined
- Feature parity unclear

---

### V14: Compliance Matrix

**Purpose:** Document regulatory compliance requirements and controls.

| Attribute | Value |
|-----------|-------|
| **ID** | V14 |
| **Name** | Compliance Matrix |
| **Category** | Conditional |
| **When Required** | Regulated industries, enterprise governance |
| **Checklist Items** | 15 |
| **Trigger Detection** | "SOC2", "GDPR", "PCI-DSS", "HIPAA", "compliance", "audit" |

**Required When:**
- System handles regulated data
- Compliance certifications required
- Enterprise governance requirements

**Checklist Items:**
```
V14-01: Applicable regulations identified
V14-02: Compliance control mapping
V14-03: Data classification per regulation
V14-04: Access control compliance
V14-05: Encryption compliance
V14-06: Audit logging compliance
V14-07: Data retention compliance
V14-08: Breach notification process
V14-09: Third-party compliance
V14-10: Compliance monitoring
V14-11: Evidence collection approach
V14-12: Audit trail requirements
V14-13: Privacy impact assessment
V14-14: Compliance training
V14-15: Compliance documentation index
```

**Common Gaps:**
- Missing control mapping
- Evidence collection undefined
- Audit trail incomplete

---

## Quality Attribute Mapping

### Primary Viewpoint Coverage

| Quality Attribute | Primary Viewpoints | Coverage Requirement |
|------------------|-------------------|----------------------|
| **Performance** | V4, V5 | EXPLICIT in at least one |
| **Scalability** | V4, V2 | EXPLICIT in at least one |
| **Security** | V7, V6 | EXPLICIT in V7 |
| **Reliability** | V8, V4 | EXPLICIT in at least one |
| **Maintainability** | V3, V10 | EXPLICIT in at least one |
| **Interoperability** | V6, V1 | EXPLICIT in at least one |
| **Portability** | V4, V2 | IMPLICIT acceptable |
| **Usability** | V6, V10 | IMPLICIT acceptable |

### Coverage Assessment Rules

```yaml
coverage_levels:
  EXPLICIT:
    definition: "Quality attribute directly addressed with metrics/requirements"
    examples:
      - "Latency must be < 100ms for 99th percentile"
      - "System must achieve 99.9% availability"

  IMPLICIT:
    definition: "Quality attribute implied but not explicitly documented"
    examples:
      - "Uses caching" (implies performance consideration)
      - "Kubernetes deployment" (implies some scalability)

  MISSING:
    definition: "No evidence of quality attribute consideration"
    severity:
      primary_viewpoint: HIGH
      all_viewpoints: CRITICAL (for regulated contexts)
```

---

## Viewpoint Detection Algorithm

```python
def detect_applicable_viewpoints(document: str) -> list[str]:
    """
    Detect which viewpoints should be assessed for a document.
    Always returns V1-V10 (core) plus applicable conditional viewpoints.
    """
    viewpoints = ["V1", "V2", "V3", "V4", "V5", "V6", "V7", "V8", "V9", "V10"]

    # Check for conditional viewpoints
    if has_multi_tenancy_signals(document):
        viewpoints.append("V11")

    if has_event_architecture_signals(document):
        viewpoints.append("V12")

    if has_migration_signals(document):
        viewpoints.append("V13")

    if has_compliance_signals(document):
        viewpoints.append("V14")

    return viewpoints

def has_multi_tenancy_signals(document: str) -> bool:
    signals = ["tenant", "multi-tenant", "saas", "b2b platform",
               "customer isolation", "per-customer"]
    return any(signal in document.lower() for signal in signals)

def has_event_architecture_signals(document: str) -> bool:
    signals = ["event-driven", "kafka", "pub/sub", "rabbitmq",
               "event sourcing", "cqrs", "message queue"]
    return any(signal in document.lower() for signal in signals)

def has_migration_signals(document: str) -> bool:
    signals = ["migration", "legacy", "modernization", "strangler",
               "lift and shift", "replatform", "cutover"]
    return any(signal in document.lower() for signal in signals)

def has_compliance_signals(document: str) -> bool:
    signals = ["soc2", "gdpr", "pci-dss", "hipaa", "fedramp",
               "compliance", "regulatory", "audit"]
    return any(signal in document.lower() for signal in signals)
```

---

## References

- [C4 Model](https://c4model.com/)
- [arc42 Template](https://arc42.org/)
- [4+1 Architectural View Model](https://en.wikipedia.org/wiki/4%2B1_architectural_view_model)
- [IEEE 42010](https://www.iso.org/standard/74393.html)
- [ADR Templates](https://adr.github.io/)
