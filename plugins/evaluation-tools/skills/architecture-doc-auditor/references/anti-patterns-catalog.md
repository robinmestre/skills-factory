# Architecture Anti-Pattern Catalog

This catalog defines 25 architecture anti-patterns detectable through documentation review, organized by category with detection signals and remediation guidance.

---

## Anti-Pattern Categories

| Category | Count | Severity Range | Focus Area |
|----------|-------|----------------|------------|
| **Structural** | 8 | HIGH-CRITICAL | System design |
| **Documentation** | 8 | MEDIUM-CRITICAL | Knowledge capture |
| **Operational** | 5 | MEDIUM-CRITICAL | Operations |
| **Security** | 4 | HIGH-CRITICAL | Security posture |

---

## Structural Anti-Patterns

### AA-01: Big Ball of Mud

| Attribute | Value |
|-----------|-------|
| **ID** | AA-01 |
| **Name** | Big Ball of Mud |
| **Severity** | CRITICAL |
| **Frequency** | Common in legacy systems |
| **Primary Impact** | Maintainability, Scalability |

**Description:**
A system lacking clear structure, where boundaries between components are unclear or non-existent. The architecture has grown organically without design.

**Detection Heuristics:**
- No clear component boundaries in diagrams
- Responsibilities spread across many areas
- "Everything calls everything" patterns
- No layering or modularization visible
- Monolithic deployment without internal structure

**Detection Signals:**
```
⚠ No component diagram exists
⚠ Single large codebase without modules
⚠ Database schema has 100+ tables without domain grouping
⚠ Any team can change any code
⚠ "It's all connected"
```

**Example Violation:**
```
Architecture describes "the system" as a single unit
with no internal decomposition, all functionality
in one deployable, with a single shared database.
```

**Impact:**
- Changes ripple unpredictably
- Cannot understand system behavior
- Testing is all-or-nothing
- Deployment risk is high
- New team members struggle

**Remediation Steps:**
1. Identify potential boundaries through domain analysis
2. Create module/package structure
3. Enforce boundaries with interfaces
4. Extract services gradually
5. Document emerging architecture

---

### AA-02: Distributed Monolith

| Attribute | Value |
|-----------|-------|
| **ID** | AA-02 |
| **Name** | Distributed Monolith |
| **Severity** | CRITICAL |
| **Frequency** | Common in microservice migrations |
| **Primary Impact** | Reliability, Deployability |

**Description:**
A system with microservice topology but monolith characteristics: services that must be deployed together, tight coupling, shared databases.

**Detection Heuristics:**
- Services described as needing synchronized deployment
- Shared database between services
- Synchronous call chains for all operations
- No independent service ownership
- All services version-locked

**Detection Signals:**
```
⚠ "Services must be deployed together"
⚠ Multiple services pointing to same database
⚠ Service A cannot function without Services B, C, D
⚠ Single shared data model across services
⚠ Distributed transactions required
```

**Example Violation:**
```
Container diagram shows 5 microservices, but all
connect to "SharedDB" and description notes
"coordinate deployments across all services."
```

**Impact:**
- Worst of both worlds (complexity + coupling)
- Cascading failures
- Cannot scale independently
- Coordination overhead
- Slower development

**Remediation Steps:**
1. Identify true service boundaries
2. Establish data ownership per service
3. Introduce async communication
4. Enable independent deployment
5. Accept some data duplication

---

### AA-03: Database Monolith

| Attribute | Value |
|-----------|-------|
| **ID** | AA-03 |
| **Name** | Database Monolith |
| **Severity** | HIGH |
| **Frequency** | Very common |
| **Primary Impact** | Scalability, Maintainability |

**Description:**
All services share a single database, creating coupling at the data layer even if services are otherwise decoupled.

**Detection Heuristics:**
- Single database in container diagram with multiple services connected
- No data ownership boundaries defined
- Schema changes require coordination
- Services query each other's tables

**Detection Signals:**
```
⚠ One database serves multiple services
⚠ "Shared schema"
⚠ Services JOIN across domain boundaries
⚠ No data ownership mentioned
```

**Example Violation:**
```
Container diagram shows Order Service, User Service,
and Payment Service all connecting to "PostgreSQL".
```

**Impact:**
- Database becomes bottleneck
- Schema changes affect everyone
- Cannot scale data independently
- Testing requires full database
- Tight coupling at data layer

**Remediation Steps:**
1. Define data ownership
2. Create service-specific databases
3. Implement data synchronization patterns
4. Use events for cross-service data
5. Accept eventual consistency

---

### AA-04: God Service

| Attribute | Value |
|-----------|-------|
| **ID** | AA-04 |
| **Name** | God Service |
| **Severity** | HIGH |
| **Frequency** | Common |
| **Primary Impact** | Maintainability, Scalability |

**Description:**
A single service that does too much, becoming a bottleneck for development and deployment.

**Detection Heuristics:**
- One service with many responsibilities listed
- Service mentioned in most flows
- Large team dedicated to one service
- Disproportionate connection count

**Detection Signals:**
```
⚠ Service has 10+ major responsibilities
⚠ Service has connections to most other services
⚠ Multiple teams work on same service
⚠ Service is bottleneck for releases
```

**Example Violation:**
```
Core Service: "Handles user management, authentication,
authorization, billing, notifications, reporting,
analytics, configuration, and feature flags."
```

**Impact:**
- Deployment bottleneck
- Team coordination overhead
- Single point of failure
- Difficult to understand
- Long release cycles

**Remediation Steps:**
1. Identify responsibility boundaries
2. Plan service extraction
3. Define clear APIs
4. Migrate gradually (strangler pattern)
5. Establish team ownership

---

### AA-05: Circular Dependencies

| Attribute | Value |
|-----------|-------|
| **ID** | AA-05 |
| **Name** | Circular Dependencies |
| **Severity** | CRITICAL |
| **Frequency** | Moderate |
| **Primary Impact** | Deployability, Testability |

**Description:**
Services or components have circular dependencies (A→B→C→A), making deployment order impossible and creating tight coupling.

**Detection Heuristics:**
- Dependency arrows form cycles in diagrams
- Services "both call each other"
- Build order conflicts
- Deployment ordering issues mentioned

**Detection Signals:**
```
⚠ Bidirectional arrows between services
⚠ "Deploy A before B, but B before A"
⚠ Service A calls B calls C calls A
⚠ Cannot start service in isolation
```

**Example Violation:**
```
Order Service → Payment Service → Inventory Service → Order Service
(to check order status after inventory update)
```

**Impact:**
- Cannot determine deployment order
- Cannot test in isolation
- Difficult startup sequencing
- Changes cascade unpredictably

**Remediation Steps:**
1. Identify all cycles
2. Find shared abstraction to extract
3. Use events instead of calls
4. Introduce intermediary service
5. Break dependency direction

---

### AA-06: Golden Hammer

| Attribute | Value |
|-----------|-------|
| **ID** | AA-06 |
| **Name** | Golden Hammer |
| **Severity** | MEDIUM |
| **Frequency** | Common |
| **Primary Impact** | Efficiency, Fit |

**Description:**
Using the same technology for all problems regardless of fit, because it's familiar.

**Detection Heuristics:**
- Same technology used everywhere
- Technology choice without rationale
- Mismatched technology to problem
- No alternatives considered

**Detection Signals:**
```
⚠ All services use same tech stack
⚠ SQL database for graph data
⚠ REST for real-time updates
⚠ No justification for choices
```

**Example Violation:**
```
"All services are Java Spring Boot with PostgreSQL"
including services that process streams, handle
graph relationships, and serve real-time data.
```

**Impact:**
- Suboptimal solutions
- Fighting the technology
- Missed opportunities
- Higher complexity

**Remediation Steps:**
1. Evaluate technology fit per use case
2. Allow polyglot where appropriate
3. Document technology selection criteria
4. Create ADRs for choices
5. Balance standardization vs fit

---

### AA-07: Vendor Lock-in Blindness

| Attribute | Value |
|-----------|-------|
| **ID** | AA-07 |
| **Name** | Vendor Lock-in Blindness |
| **Severity** | HIGH |
| **Frequency** | Moderate |
| **Primary Impact** | Portability, Flexibility |

**Description:**
Direct coupling to proprietary cloud services without abstraction, making migration difficult.

**Detection Heuristics:**
- Direct cloud service references throughout
- No abstraction layer mentioned
- Proprietary features used extensively
- No portability consideration

**Detection Signals:**
```
⚠ Services call AWS SDK directly
⚠ Lambda-specific code patterns
⚠ DynamoDB-specific data modeling
⚠ No abstraction over cloud services
```

**Example Violation:**
```
"Service uses AWS Lambda with Step Functions,
DynamoDB with DAX, and SNS/SQS directly" with
no abstraction layer or alternative consideration.
```

**Impact:**
- Cannot migrate providers
- Vendor pricing power
- Limited negotiation leverage
- Feature dependency

**Remediation Steps:**
1. Identify proprietary dependencies
2. Create abstraction interfaces
3. Implement portable adapters
4. Evaluate multi-cloud necessity
5. Document intentional lock-in decisions

---

### AA-08: Accidental Complexity

| Attribute | Value |
|-----------|-------|
| **ID** | AA-08 |
| **Name** | Accidental Complexity |
| **Severity** | HIGH |
| **Frequency** | Common |
| **Primary Impact** | Maintainability |

**Description:**
Architecture more complex than the problem requires, due to over-engineering or premature optimization.

**Detection Heuristics:**
- Many technologies for simple problem
- Microservices for simple CRUD
- Event sourcing without clear need
- Kubernetes for single app

**Detection Signals:**
```
⚠ 10 services for simple app
⚠ Event sourcing for static data
⚠ CQRS without read/write asymmetry
⚠ Complex patterns without justification
```

**Example Violation:**
```
"User profile service uses event sourcing,
CQRS, GraphQL federation, and Kubernetes"
for a 1000-user internal tool.
```

**Impact:**
- Unnecessary operational burden
- Slower development
- Higher costs
- Difficult onboarding

**Remediation Steps:**
1. Question complexity necessity
2. Start simple, add complexity when needed
3. Document why patterns chosen
4. Consider maintenance cost
5. Simplify where possible

---

## Documentation Anti-Patterns

### AA-09: Diagram Divorce

| Attribute | Value |
|-----------|-------|
| **ID** | AA-09 |
| **Name** | Diagram Divorce |
| **Severity** | CRITICAL |
| **Frequency** | Very common |
| **Primary Impact** | Trustworthiness |

**Description:**
Diagrams don't match the text description or each other, creating confusion about actual architecture.

**Detection Heuristics:**
- Text mentions services not in diagrams
- Diagrams show different service counts
- Inconsistent naming between text and diagrams
- Conflicting relationship descriptions

**Detection Signals:**
```
⚠ Text says 5 services, diagram shows 7
⚠ Service named "OrderService" in text, "Orders" in diagram
⚠ Text describes sync call, diagram shows queue
⚠ Different database technologies in different views
```

**Example Violation:**
```
Text: "The system consists of User, Order, and Payment services"
Container Diagram: Shows User, Order, Payment, Notification, Analytics
No mention of Notification and Analytics in text.
```

**Impact:**
- Don't know what's true
- Wrong decisions based on wrong info
- Trust in documentation lost
- Onboarding confusion

**Remediation Steps:**
1. Single source of truth for architecture
2. Generate diagrams from model where possible
3. Regular documentation review
4. Cross-reference checks in review
5. Version diagrams with code

---

### AA-10: ADR Amnesia

| Attribute | Value |
|-----------|-------|
| **ID** | AA-10 |
| **Name** | ADR Amnesia |
| **Severity** | HIGH |
| **Frequency** | Very common |
| **Primary Impact** | Institutional knowledge |

**Description:**
Major architectural decisions made without recording them, losing context for future teams.

**Detection Heuristics:**
- No ADR files or section
- Technology choices without rationale
- "We just used X"
- No alternatives documented

**Detection Signals:**
```
⚠ No ADR directory or section
⚠ "Why did we choose X?" unanswered
⚠ Technology stated without justification
⚠ No decision history
```

**Example Violation:**
```
Architecture doc states "Using Kafka for messaging"
with no explanation of why Kafka was chosen over
RabbitMQ, SQS, or other alternatives.
```

**Impact:**
- Cannot understand past reasoning
- May repeat mistakes
- Difficult to evaluate changes
- Knowledge leaves with people

**Remediation Steps:**
1. Establish ADR practice
2. Retroactively document key decisions
3. Include in review process
4. Link ADRs to implementation
5. Regular ADR reviews

---

### AA-11: Stale Blueprints

| Attribute | Value |
|-----------|-------|
| **ID** | AA-11 |
| **Name** | Stale Blueprints |
| **Severity** | HIGH |
| **Frequency** | Very common |
| **Primary Impact** | Accuracy |

**Description:**
Documentation references deprecated, removed, or renamed components.

**Detection Heuristics:**
- References to decommissioned services
- Old technology names
- Deprecated APIs mentioned
- Removed features documented

**Detection Signals:**
```
⚠ References "LegacyAuthService" (decommissioned)
⚠ Shows "MySQL" but system uses PostgreSQL now
⚠ Documents API v1 when v3 is current
⚠ Features removed but still documented
```

**Example Violation:**
```
Context diagram shows integration with "Legacy ERP"
which was decommissioned 6 months ago during
modernization project.
```

**Impact:**
- Misleading architecture picture
- Wrong integration assumptions
- Wasted investigation time
- Incorrect planning

**Remediation Steps:**
1. Review documentation currency
2. Add "last updated" dates
3. Establish refresh cadence
4. Automate staleness detection
5. Link docs to deployments

---

### AA-12: View Vacuum

| Attribute | Value |
|-----------|-------|
| **ID** | AA-12 |
| **Name** | View Vacuum |
| **Severity** | CRITICAL |
| **Frequency** | Common |
| **Primary Impact** | Completeness |

**Description:**
Entire architecture viewpoints are completely missing.

**Detection Heuristics:**
- No deployment view
- No security architecture
- No operations documentation
- Key viewpoint completely absent

**Detection Signals:**
```
⚠ No deployment topology documented
⚠ Security section is empty or absent
⚠ No operational concerns addressed
⚠ No data architecture view
```

**Example Violation:**
```
Architecture documentation has detailed container
and component diagrams but zero information about
deployment topology, infrastructure, or operations.
```

**Impact:**
- Incomplete understanding
- Blind spots in review
- Missing concerns
- Implementation surprises

**Remediation Steps:**
1. Audit against viewpoint checklist
2. Prioritize critical missing viewpoints
3. Create minimal viable documentation
4. Iterate to full coverage
5. Make viewpoint coverage a gate

---

### AA-13: C4 Confusion

| Attribute | Value |
|-----------|-------|
| **ID** | AA-13 |
| **Name** | C4 Confusion |
| **Severity** | MEDIUM |
| **Frequency** | Common with C4 adoption |
| **Primary Impact** | Clarity |

**Description:**
Mixing abstraction levels in the same diagram (e.g., components inside a context diagram).

**Detection Heuristics:**
- Different zoom levels in same diagram
- Containers inside context diagram
- Code details in container view
- Inconsistent abstraction

**Detection Signals:**
```
⚠ Context diagram shows internal services
⚠ Container diagram shows classes
⚠ Mixed notation in single diagram
⚠ No clear level labeling
```

**Example Violation:**
```
"System Context Diagram" showing the system boundary
but also including internal microservices like
"Order Service" and "Payment Service" inside.
```

**Impact:**
- Confusing diagrams
- Wrong audience targeting
- Difficult to maintain
- Communication problems

**Remediation Steps:**
1. Understand C4 levels properly
2. One abstraction level per diagram
3. Label diagram levels clearly
4. Create separate diagrams
5. Train team on C4

---

### AA-14: Prose Overload

| Attribute | Value |
|-----------|-------|
| **ID** | AA-14 |
| **Name** | Prose Overload |
| **Severity** | MEDIUM |
| **Frequency** | Common |
| **Primary Impact** | Accessibility |

**Description:**
Architecture described entirely in prose with no diagrams.

**Detection Heuristics:**
- Walls of text without visuals
- "The system consists of..." paragraphs
- No diagram files
- Text-only architecture section

**Detection Signals:**
```
⚠ Multiple pages of text, no diagrams
⚠ "See description below" with no diagram
⚠ Components listed in bullet points
⚠ Relationships described in sentences
```

**Example Violation:**
```
5-page architecture section describing all services,
their responsibilities, interactions, data stores,
and deployment topology entirely in prose.
```

**Impact:**
- Difficult to understand
- Can't see relationships
- Slow comprehension
- Error-prone interpretation

**Remediation Steps:**
1. Add context diagram minimum
2. Create container diagram
3. Visualize key flows
4. Use prose to explain diagrams
5. Balance text and visuals

---

### AA-15: Technology Tourism

| Attribute | Value |
|-----------|-------|
| **ID** | AA-15 |
| **Name** | Technology Tourism |
| **Severity** | LOW |
| **Frequency** | Moderate |
| **Primary Impact** | Signal/noise ratio |

**Description:**
Excessive technology name-dropping without explaining why or how they're used.

**Detection Heuristics:**
- Long tech stack lists
- Buzzword density
- No rationale for choices
- Technologies mentioned once

**Detection Signals:**
```
⚠ "Uses Kubernetes, Istio, Prometheus, Grafana, Jaeger..."
⚠ Technology list without explanations
⚠ Buzzword-heavy descriptions
⚠ No "why" for any technology
```

**Example Violation:**
```
"Built with React, Next.js, TypeScript, TailwindCSS,
Prisma, PostgreSQL, Redis, Elasticsearch, Kafka,
Kubernetes, ArgoCD, Prometheus, Grafana, Loki..."
with no explanation of why each is used.
```

**Impact:**
- Difficult to understand what matters
- Hides actual architecture
- Confuses readers
- No actionable information

**Remediation Steps:**
1. Focus on architectural significance
2. Explain technology purposes
3. Group related technologies
4. Highlight key choices
5. Document in ADRs

---

### AA-16: Abstraction Allergy

| Attribute | Value |
|-----------|-------|
| **ID** | AA-16 |
| **Name** | Abstraction Allergy |
| **Severity** | MEDIUM |
| **Frequency** | Moderate |
| **Primary Impact** | Understanding |

**Description:**
Only low-level (code-level) details documented with no conceptual overview.

**Detection Heuristics:**
- Jump straight to code structure
- No high-level system view
- Class diagrams only
- Missing context

**Detection Signals:**
```
⚠ Starts at component/class level
⚠ No system context
⚠ No container overview
⚠ "Architecture" means code structure
```

**Example Violation:**
```
Architecture documentation begins with package
structure and class diagrams without ever
explaining what the system is or does.
```

**Impact:**
- Hard to get big picture
- Wrong audience
- Missing forest for trees
- No context for decisions

**Remediation Steps:**
1. Start with context
2. Layer abstraction levels
3. Add business context
4. Create overview diagrams
5. Link levels together

---

## Operational Anti-Patterns

### AA-17: Observability Omission

| Attribute | Value |
|-----------|-------|
| **ID** | AA-17 |
| **Name** | Observability Omission |
| **Severity** | HIGH |
| **Frequency** | Common |
| **Primary Impact** | Operations |

**Description:**
No monitoring, logging, or tracing strategy documented.

**Detection Heuristics:**
- No monitoring section
- Observability is "TBD"
- No metrics defined
- No alerting rules

**Detection Signals:**
```
⚠ Monitoring/observability section empty
⚠ "Will add monitoring later"
⚠ No metrics defined
⚠ No dashboards planned
```

**Example Violation:**
```
Comprehensive architecture document with detailed
service design but only "Monitoring: TBD" for
observability strategy.
```

**Impact:**
- Blind operations
- Slow incident detection
- Cannot measure SLOs
- Debugging difficult

**Remediation Steps:**
1. Define key metrics
2. Plan logging strategy
3. Implement tracing
4. Create dashboards
5. Define alerts

---

### AA-18: SLO Silence

| Attribute | Value |
|-----------|-------|
| **ID** | AA-18 |
| **Name** | SLO Silence |
| **Severity** | HIGH |
| **Frequency** | Common |
| **Primary Impact** | Reliability targets |

**Description:**
No Service Level Objectives defined for reliability.

**Detection Heuristics:**
- No SLO section
- Availability is "high"
- No quantified targets
- No error budgets

**Detection Signals:**
```
⚠ No SLO definitions
⚠ "Highly available" without numbers
⚠ No latency targets
⚠ No error rate goals
```

**Example Violation:**
```
Architecture states "system must be reliable and
performant" without defining 99.9% availability,
P99 latency < 200ms, or error rate < 0.1%.
```

**Impact:**
- No reliability targets
- Cannot measure success
- No prioritization guide
- Unclear investments

**Remediation Steps:**
1. Define availability SLO
2. Set latency SLOs
3. Define error rate SLO
4. Create error budgets
5. Align with business needs

---

### AA-19: Deployment Darkness

| Attribute | Value |
|-----------|-------|
| **ID** | AA-19 |
| **Name** | Deployment Darkness |
| **Severity** | CRITICAL |
| **Frequency** | Moderate |
| **Primary Impact** | Deployability |

**Description:**
No deployment documentation - unclear how system is deployed.

**Detection Heuristics:**
- No deployment view
- No CI/CD documentation
- Unclear environments
- No deployment process

**Detection Signals:**
```
⚠ No deployment section
⚠ "Deployed to production" without how
⚠ No environment definitions
⚠ No rollback process
```

**Example Violation:**
```
Architecture describes services in detail but
has no information about how they're deployed,
where they run, or how releases happen.
```

**Impact:**
- Cannot deploy reliably
- No runbook for releases
- Recovery unclear
- Onboarding difficult

**Remediation Steps:**
1. Document deployment topology
2. Define CI/CD pipeline
3. Document environments
4. Create rollback procedure
5. Define deployment process

---

### AA-20: Capacity Blindness

| Attribute | Value |
|-----------|-------|
| **ID** | AA-20 |
| **Name** | Capacity Blindness |
| **Severity** | HIGH |
| **Frequency** | Common |
| **Primary Impact** | Scalability |

**Description:**
No capacity planning or scaling strategy documented.

**Detection Heuristics:**
- No load projections
- No scaling strategy
- No resource requirements
- No capacity limits

**Detection Signals:**
```
⚠ No expected load mentioned
⚠ No scaling approach
⚠ No resource sizing
⚠ No growth projections
```

**Example Violation:**
```
Architecture document doesn't mention expected
users, transactions per second, data volume,
or how the system will scale.
```

**Impact:**
- Surprise scaling issues
- Over/under provisioning
- Cost unpredictability
- Performance problems

**Remediation Steps:**
1. Define expected load
2. Plan scaling strategy
3. Document resource needs
4. Project growth
5. Define capacity triggers

---

### AA-21: Runbook Roulette

| Attribute | Value |
|-----------|-------|
| **ID** | AA-21 |
| **Name** | Runbook Roulette |
| **Severity** | MEDIUM |
| **Frequency** | Common |
| **Primary Impact** | Operations |

**Description:**
No runbooks or operational procedures documented.

**Detection Heuristics:**
- No runbook references
- Operations section empty
- No incident procedures
- No maintenance docs

**Detection Signals:**
```
⚠ No runbook directory
⚠ "Operations: manual"
⚠ No incident response
⚠ No maintenance procedures
```

**Example Violation:**
```
No documentation for common operations like
scaling, database maintenance, certificate
rotation, or incident response.
```

**Impact:**
- Slow incident response
- Knowledge silos
- Inconsistent operations
- Burnout risk

**Remediation Steps:**
1. Document common procedures
2. Create incident runbooks
3. Define maintenance tasks
4. Establish on-call docs
5. Regular runbook review

---

## Security Anti-Patterns

### AA-22: Trust Assumption

| Attribute | Value |
|-----------|-------|
| **ID** | AA-22 |
| **Name** | Trust Assumption |
| **Severity** | CRITICAL |
| **Frequency** | Common |
| **Primary Impact** | Security |

**Description:**
Assuming internal network or systems are inherently trustworthy without verification.

**Detection Heuristics:**
- "Internal network is secure"
- No internal authentication
- Trust based on location
- No zero trust

**Detection Signals:**
```
⚠ "Secured by VPC"
⚠ "Internal services don't need auth"
⚠ "Firewall protects us"
⚠ No service-to-service auth
```

**Example Violation:**
```
Security section states "Internal services communicate
over private VPC so authentication is not needed"
without any service identity or verification.
```

**Impact:**
- Lateral movement risk
- No defense in depth
- Compliance issues
- Single point of failure

**Remediation Steps:**
1. Implement zero trust
2. Add service authentication
3. Encrypt all traffic
4. Verify every request
5. Log all access

---

### AA-23: Auth Afterthought

| Attribute | Value |
|-----------|-------|
| **ID** | AA-23 |
| **Name** | Auth Afterthought |
| **Severity** | HIGH |
| **Frequency** | Moderate |
| **Primary Impact** | Security |

**Description:**
Security/authentication added as an afterthought, not designed into architecture.

**Detection Heuristics:**
- Security section is sparse
- Auth mentioned briefly
- No security design
- "Will add security later"

**Detection Signals:**
```
⚠ Security section is one paragraph
⚠ "Authentication: JWT" without details
⚠ No authorization model
⚠ Security not in diagrams
```

**Example Violation:**
```
Detailed architecture with security section
that just says "Will use OAuth2 for authentication"
with no details on flows, authorization, or integration.
```

**Impact:**
- Security bolted on poorly
- Design doesn't support security
- Gaps and vulnerabilities
- Difficult to fix later

**Remediation Steps:**
1. Design security in from start
2. Document auth flows completely
3. Define authorization model
4. Include security in reviews
5. Threat modeling

---

### AA-24: Secret Scatter

| Attribute | Value |
|-----------|-------|
| **ID** | AA-24 |
| **Name** | Secret Scatter |
| **Severity** | CRITICAL |
| **Frequency** | Common |
| **Primary Impact** | Security |

**Description:**
Credentials, secrets, or API keys scattered in configuration files or code.

**Detection Heuristics:**
- No secrets management documented
- Config examples with credentials
- No Vault/KMS mentioned
- Secrets in env files without protection

**Detection Signals:**
```
⚠ No secrets management in architecture
⚠ ".env files" without protection discussion
⚠ API keys in config examples
⚠ Database passwords in diagrams
```

**Example Violation:**
```
Architecture documentation includes config examples
showing "DB_PASSWORD=prod123" and no mention of
secrets management approach.
```

**Impact:**
- Credential exposure
- Compliance violation
- Security breach risk
- Difficult to rotate

**Remediation Steps:**
1. Audit for exposed secrets
2. Implement secrets management
3. Remove from all locations
4. Define rotation process
5. Train team

---

### AA-25: Compliance Complacency

| Attribute | Value |
|-----------|-------|
| **ID** | AA-25 |
| **Name** | Compliance Complacency |
| **Severity** | HIGH |
| **Frequency** | Common in regulated industries |
| **Primary Impact** | Compliance |

**Description:**
Regulatory compliance not mapped to architecture in regulated contexts.

**Detection Heuristics:**
- No compliance section
- Regulations not mentioned
- No control mapping
- Audit requirements unclear

**Detection Signals:**
```
⚠ Handles PCI data, no PCI-DSS mapping
⚠ GDPR scope, no data protection architecture
⚠ No compliance matrix
⚠ Audit requirements not documented
```

**Example Violation:**
```
System processes payment cards but architecture
has no mention of PCI-DSS compliance, cardholder
data environment, or required controls.
```

**Impact:**
- Compliance violations
- Audit failures
- Fines and penalties
- Business disruption

**Remediation Steps:**
1. Identify applicable regulations
2. Map architecture to controls
3. Document evidence locations
4. Plan compliance testing
5. Regular compliance review

---

## Anti-Pattern Detection Integration

### Integration with Gap Detection

Anti-patterns are scanned during Phase 5 (Technical Debt & Anti-Pattern Detection) after item-by-item verification. Detection follows this process:

```python
def scan_anti_patterns(document_analysis):
    findings = []
    for pattern in ANTI_PATTERNS:
        if has_detection_signals(document_analysis, pattern.signals):
            findings.append({
                'pattern_id': pattern.id,
                'name': pattern.name,
                'severity': pattern.severity,
                'evidence': extract_evidence(document_analysis, pattern),
                'remediation': pattern.remediation
            })
    return findings
```

### XML Output Structure

```xml
<anti_patterns>
  <pattern id="AA-02">
    <name>Distributed Monolith</name>
    <severity>CRITICAL</severity>
    <instances>
      <instance location="Container Diagram">
        "All services connect to SharedDB"
      </instance>
      <instance location="Deployment Section">
        "Services must be deployed together"
      </instance>
    </instances>
    <remediation>
      Define data ownership per service and introduce
      async communication to decouple deployments.
    </remediation>
  </pattern>
</anti_patterns>
```

---

## References

- [Software Architecture Patterns](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/)
- [Fundamentals of Software Architecture](https://www.oreilly.com/library/view/fundamentals-of-software/9781492043447/)
- [Microservices AntiPatterns](https://www.oreilly.com/library/view/microservices-antipatterns-and/9781492042716/)
