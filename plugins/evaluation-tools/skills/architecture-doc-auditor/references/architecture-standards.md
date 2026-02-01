# Architecture Standards Reference

This reference covers the four primary architecture documentation frameworks supported by the Architecture Documentation Auditor: TOGAF, C4 Model, arc42, and IEEE 42010.

---

## 1. TOGAF (The Open Group Architecture Framework)

### Overview

TOGAF is an enterprise architecture framework providing a comprehensive approach for designing, planning, implementing, and governing enterprise information architecture.

### Architecture Development Method (ADM) Phases

| Phase | Name | Key Artifacts |
|-------|------|---------------|
| **Preliminary** | Framework Setup | Architecture Principles, Governance Framework |
| **A** | Architecture Vision | Architecture Vision Document, Stakeholder Map |
| **B** | Business Architecture | Business Architecture Document, Process Models |
| **C** | Information Systems Architecture | Data Architecture, Application Architecture |
| **D** | Technology Architecture | Technology Architecture Document, Platform Models |
| **E** | Opportunities & Solutions | Implementation Strategy, Migration Plan |
| **F** | Migration Planning | Implementation & Migration Plan |
| **G** | Implementation Governance | Architecture Compliance Reports |
| **H** | Architecture Change Management | Change Requests, Impact Assessments |
| **Requirements** | Requirements Management | Architecture Requirements Specification |

### Key Artifacts Checklist

| Artifact | Phase | Audit Relevance |
|----------|-------|-----------------|
| Architecture Principles | Preliminary | V10 - Decision rationale |
| Stakeholder Map | A | V1 - Context stakeholders |
| Architecture Vision | A | V1 - System scope |
| Business Process Models | B | V1 - Business context |
| Data Entity/Relationship | C | V5 - Data architecture |
| Application Portfolio | C | V2 - Container inventory |
| Technology Standards | D | V2 - Technology choices |
| Migration Plan | E/F | V13 - Migration path |
| Compliance Report | G | V14 - Compliance matrix |

### Detection Signals

```
TOGAF document indicators:
- References to "ADM phases"
- "Architecture Building Blocks (ABB)"
- "Solution Building Blocks (SBB)"
- "Architecture Continuum"
- "Enterprise Continuum"
- Formal stakeholder concern matrices
- Architecture Repository references
```

---

## 2. C4 Model

### Overview

The C4 model provides a hierarchical approach to visualizing software architecture at four abstraction levels: Context, Containers, Components, and Code.

### The Four Levels

| Level | Scope | Audience | Elements Shown |
|-------|-------|----------|----------------|
| **1. System Context** | System + external entities | Everyone | System, users, external systems |
| **2. Container** | Inside the system boundary | Technical stakeholders | Applications, data stores, microservices |
| **3. Component** | Inside a container | Developers | Modules, classes, interfaces |
| **4. Code** | Inside a component | Developers | Classes, methods, relationships |

### Level 1: System Context Diagram

**Required Elements:**
- [ ] System under design (central box)
- [ ] All external users/personas
- [ ] All external systems
- [ ] Relationships with labels
- [ ] System boundary indication

**Audit Items (V1-01 to V1-15):**
```
V1-01: System boundary clearly defined
V1-02: All user types identified
V1-03: All external systems identified
V1-04: Relationship descriptions present
V1-05: Data flow directions shown
V1-06: Trust boundaries marked
V1-07: System purpose stated
```

### Level 2: Container Diagram

**Required Elements:**
- [ ] All major containers (services, apps, databases)
- [ ] Technology choices per container
- [ ] Communication protocols between containers
- [ ] External system connections
- [ ] Container responsibilities

**Audit Items (V2-01 to V2-25):**
```
V2-01: All containers enumerated
V2-02: Technology stack per container
V2-03: Container responsibilities documented
V2-04: Inter-container communication protocols
V2-05: Database technologies specified
V2-06: API boundaries defined
```

### Level 3: Component Diagram

**Required Elements:**
- [ ] Major components within container
- [ ] Component responsibilities
- [ ] Inter-component relationships
- [ ] External interfaces

**Audit Items (V3-01 to V3-18):**
```
V3-01: Key components identified
V3-02: Component responsibilities defined
V3-03: Interface contracts documented
V3-04: Dependency directions shown
```

### Level 4: Code Diagram (Optional)

**Required Elements:**
- [ ] Class/package structure
- [ ] Key interfaces
- [ ] Design patterns used

### C4 Maturity Assessment

```yaml
c4_maturity:
  level_1_complete:
    criteria:
      - System boundary defined
      - All external actors identified
      - All external systems listed
      - Relationships labeled
    minimum_items: 5

  level_2_complete:
    criteria:
      - All containers identified
      - Technology choices documented
      - Communication protocols specified
      - Data stores identified
    minimum_items: 10

  level_3_complete:
    criteria:
      - Key components per container
      - Component responsibilities
      - Interface definitions
    minimum_items: 15 per container

  level_4_complete:
    criteria:
      - Class diagrams for critical components
      - Design patterns documented
    optional: true
```

### Detection Signals

```
C4 document indicators:
- Explicit level labels (Level 1, Level 2, etc.)
- "System Context Diagram"
- "Container Diagram"
- "Component Diagram"
- Blue person icons for users
- Gray boxes for external systems
- Container boundary boxes
- References to "c4model.com" or Simon Brown
```

---

## 3. arc42

### Overview

arc42 is a template for documenting software and system architectures. It provides 12 sections covering all essential aspects of architecture documentation.

### Template Sections

| # | Section | Content | Viewpoint Mapping |
|---|---------|---------|-------------------|
| 1 | Introduction and Goals | Business context, quality goals, stakeholders | V1 |
| 2 | Constraints | Technical, organizational, conventions | V1, V9 |
| 3 | Context and Scope | System context, business/technical interfaces | V1, V6 |
| 4 | Solution Strategy | Technology decisions, patterns, quality approach | V10, V2 |
| 5 | Building Block View | Static decomposition (levels 1, 2, 3) | V2, V3 |
| 6 | Runtime View | Dynamic behavior, scenarios | V6 |
| 7 | Deployment View | Infrastructure, topology, mapping | V4 |
| 8 | Crosscutting Concepts | Technical concepts applied throughout | V9 |
| 9 | Architecture Decisions | ADRs, key decisions | V10 |
| 10 | Quality Requirements | Quality tree, quality scenarios | V7, V8 |
| 11 | Risks and Technical Debt | Known issues, risks | V8 |
| 12 | Glossary | Terms and definitions | V9 |

### Section Details

#### Section 1: Introduction and Goals

**Required Content:**
- Requirements overview
- Quality goals (top 3-5)
- Stakeholder table with expectations

**Audit Items:**
```
arc42-01: Requirements overview present
arc42-02: Quality goals prioritized (3-5)
arc42-03: Stakeholder table with roles
arc42-04: Stakeholder expectations documented
```

#### Section 3: Context and Scope

**Required Content:**
- Business context diagram
- Technical context diagram
- External interfaces list

**Audit Items:**
```
arc42-10: Business context diagram exists
arc42-11: Technical context diagram exists
arc42-12: All external interfaces listed
arc42-13: Interface protocols documented
```

#### Section 5: Building Block View

**Required Content:**
- Level 1: White-box of overall system
- Level 2: White-box of contained building blocks
- Level 3: Details as needed

**Audit Items:**
```
arc42-20: Level 1 decomposition present
arc42-21: Building block responsibilities defined
arc42-22: Interface descriptions present
arc42-23: Black-box descriptions for external
```

#### Section 7: Deployment View

**Required Content:**
- Infrastructure overview
- Mapping of building blocks to infrastructure
- Environment specifications (dev/staging/prod)

**Audit Items:**
```
arc42-30: Infrastructure topology defined
arc42-31: Building block to node mapping
arc42-32: Environment differences documented
arc42-33: Deployment process outlined
```

#### Section 9: Architecture Decisions

**Required Content:**
- Key decisions as ADRs
- Context, decision, consequences

**Audit Items:**
```
arc42-40: Decisions captured as ADRs
arc42-41: Decision context documented
arc42-42: Alternatives considered
arc42-43: Consequences (positive/negative)
```

### Completeness Matrix

| Section | Critical | Minimum Content |
|---------|----------|-----------------|
| 1 | HIGH | Quality goals + stakeholders |
| 2 | MEDIUM | Key constraints listed |
| 3 | CRITICAL | Context diagrams |
| 4 | HIGH | Technology decisions |
| 5 | CRITICAL | Level 1 decomposition |
| 6 | MEDIUM | Key runtime scenarios |
| 7 | HIGH | Deployment topology |
| 8 | MEDIUM | Crosscutting patterns |
| 9 | HIGH | Key ADRs |
| 10 | HIGH | Quality scenarios |
| 11 | MEDIUM | Known risks |
| 12 | LOW | Key terms |

### Detection Signals

```
arc42 document indicators:
- Numbered sections 1-12
- "Building Block View"
- "Crosscutting Concepts"
- "Quality Scenarios"
- "Whitebox" / "Blackbox" terminology
- References to arc42.org
- German engineering terms (sometimes)
```

---

## 4. IEEE 42010 (ISO/IEC/IEEE 42010)

### Overview

IEEE 42010 is the international standard for architecture description of systems and software. It provides a conceptual model for architecture documentation.

### Core Concepts

| Concept | Definition |
|---------|------------|
| **Architecture** | Fundamental concepts or properties of a system |
| **Architecture Description** | Work product expressing an architecture |
| **Stakeholder** | Individual with interests in the system |
| **Concern** | Interest in a system relevant to stakeholders |
| **Architecture Viewpoint** | Specification of conventions for constructing and using a view |
| **Architecture View** | Representation of a system from a viewpoint |
| **Model Kind** | Conventions for a type of modeling |
| **Architecture Model** | Model of architecture in accordance with a model kind |

### Required Content per Standard

| Element | Requirement | Audit Item |
|---------|-------------|------------|
| System Identification | Name, scope, purpose | V1-01 |
| Stakeholder Identification | All stakeholders listed | V1-02 |
| Concern Identification | All concerns cataloged | V1-03 |
| Viewpoint Selection | Viewpoints justified | V1-04 |
| View Documentation | One view per viewpoint | V2-01 |
| Correspondence Rules | Cross-view consistency | V9-01 |
| Architecture Rationale | Decisions justified | V10-01 |

### Standard Viewpoints (4+1 Model Integration)

| Viewpoint | Concerns Addressed | Stakeholders |
|-----------|-------------------|--------------|
| **Logical** | Functionality, structure | Designers, developers |
| **Process** | Concurrency, distribution | Integrators, testers |
| **Development** | Organization, modularity | Developers, managers |
| **Physical** | Deployment, topology | System engineers, operators |
| **Scenarios** | Use cases, validation | Users, architects |

### Correspondence Rules

```yaml
correspondence_rules:
  - rule: "Elements in Logical must appear in Development"
    viewpoints: [Logical, Development]
    severity: HIGH

  - rule: "Containers in Process must map to Physical nodes"
    viewpoints: [Process, Physical]
    severity: CRITICAL

  - rule: "All Scenarios must trace to Logical elements"
    viewpoints: [Scenarios, Logical]
    severity: MEDIUM
```

### Detection Signals

```
IEEE 42010 indicators:
- Formal viewpoint definitions
- "Concerns" and "Stakeholders" matrices
- Viewpoint correspondence documentation
- References to ISO/IEC/IEEE 42010
- Architecture rationale sections
- Model kind specifications
```

---

## Framework Comparison Matrix

| Aspect | TOGAF | C4 | arc42 | IEEE 42010 |
|--------|-------|-----|-------|------------|
| **Scope** | Enterprise | Software | Software | System |
| **Complexity** | High | Low-Medium | Medium | High |
| **Prescriptiveness** | High | Low | Medium | High |
| **Diagram Types** | Many | 4 types | Flexible | Viewpoint-based |
| **Decision Records** | Separate | Not prescribed | Section 9 | Rationale |
| **Best For** | Large enterprises | Development teams | Technical documentation | Standards compliance |
| **Learning Curve** | Steep | Gentle | Moderate | Steep |

### Framework Selection Guidance

```
Choose TOGAF when:
- Enterprise-wide architecture initiative
- Need governance framework
- Multiple systems/portfolios
- Regulatory requirements

Choose C4 when:
- Software development team documentation
- Need quick communication of architecture
- Agile environment
- Visual-first documentation

Choose arc42 when:
- Comprehensive technical documentation needed
- Development team owns documentation
- Need structured template
- German-speaking teams (native support)

Choose IEEE 42010 when:
- Standards compliance required
- Government/defense contracts
- Formal viewpoint documentation needed
- Multi-stakeholder complex systems
```

---

## Framework Detection Algorithm

```python
def detect_framework(document):
    """
    Detect architecture framework from document content.
    Returns: 'togaf' | 'c4' | 'arc42' | 'ieee_42010' | 'custom'
    """
    signals = {
        'togaf': [
            'ADM', 'Architecture Building Block', 'Solution Building Block',
            'Architecture Continuum', 'TOGAF'
        ],
        'c4': [
            'System Context', 'Container Diagram', 'Component Diagram',
            'Level 1', 'Level 2', 'Level 3', 'c4model'
        ],
        'arc42': [
            'Building Block View', 'Crosscutting Concepts', 'Quality Scenarios',
            'Whitebox', 'Blackbox', 'arc42'
        ],
        'ieee_42010': [
            'Viewpoint', 'Concern', 'Correspondence', 'ISO/IEC/IEEE 42010',
            'Architecture Rationale', 'Model Kind'
        ]
    }

    scores = {fw: 0 for fw in signals}

    for framework, keywords in signals.items():
        for keyword in keywords:
            if keyword.lower() in document.lower():
                scores[framework] += 1

    max_score = max(scores.values())
    if max_score < 2:
        return 'custom'

    return max(scores, key=scores.get)
```

---

## References

- [TOGAF Standard](https://pubs.opengroup.org/architecture/togaf9-doc/arch/)
- [C4 Model](https://c4model.com/)
- [arc42 Template](https://arc42.org/)
- [IEEE 42010:2022](https://www.iso.org/standard/74393.html)
