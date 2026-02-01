# PRD Requirements Checklist

Comprehensive 116-item checklist for Product Requirements Document completeness audits.

---

## Overview

This checklist covers all elements a complete PRD should contain, organized by section. Each item includes verification criteria and severity guidance.

**Total Items:** 116
**Sections:** 10
**Applicability:** Varies by PRD type (feature, epic, product, initiative)

---

## Checklist Summary

| Section | ID Range | Item Count | Feature | Epic | Product | Initiative |
|---------|----------|------------|---------|------|---------|------------|
| Problem & Context | PC-01 to PC-15 | 15 | yes | yes | yes | yes |
| User & Stakeholder | US-01 to US-12 | 12 | yes | yes | yes | yes |
| Goals & Success | GS-01 to GS-10 | 10 | yes | yes | yes | yes |
| Requirements | RQ-01 to RQ-18 | 18 | yes | yes | yes | yes |
| User Stories | ST-01 to ST-14 | 14 | yes | yes | optional | no |
| Acceptance Criteria | AC-01 to AC-12 | 12 | yes | yes | yes | optional |
| Dependencies | DP-01 to DP-08 | 8 | yes | yes | yes | yes |
| Risks & Assumptions | RA-01 to RA-10 | 10 | yes | yes | yes | yes |
| Timeline & Scope | TS-01 to TS-09 | 9 | yes | yes | yes | yes |
| Technical Considerations | TC-01 to TC-08 | 8 | optional | optional | yes | yes |
| **TOTAL** | | **116** | **106** | **106** | **100** | **92** |

---

## Section 1: Problem & Context (15 items)

### PC-01: Problem Statement
| Attribute | Value |
|-----------|-------|
| **Description** | Clear articulation of the problem being solved |
| **Detection** | Look for "Problem:", "Pain point:", or similar headers |
| **Quality Criteria** | Describes problem (not solution); specific (not generic); actionable |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

**Good Example:**
> "Enterprise customers are losing an average of 4.2 hours per week manually reconciling invoice data between our platform and their ERP systems, leading to 23% higher operational costs."

**Poor Example:**
> "Users have problems with the system" (too vague, no evidence)

---

### PC-02: Problem Evidence
| Attribute | Value |
|-----------|-------|
| **Description** | Data, research, or user feedback supporting problem existence |
| **Detection** | Quantitative data, user quotes, research references, support tickets |
| **Quality Criteria** | Cites sources; not just assertions; includes methodology |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

**Verification Questions:**
- Is there quantitative data (numbers, percentages)?
- Are user quotes or feedback included?
- Is the source of evidence cited?
- Is sample size or methodology mentioned?

---

### PC-03: Current State
| Attribute | Value |
|-----------|-------|
| **Description** | Description of how the problem is currently handled |
| **Detection** | "Current state", "As-is", "Today's process" sections |
| **Quality Criteria** | Describes existing workflow; identifies workarounds |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### PC-04: Problem Scope
| Attribute | Value |
|-----------|-------|
| **Description** | Boundaries of the problem being addressed |
| **Detection** | "Scope", "Boundaries", "This PRD addresses" sections |
| **Quality Criteria** | Clear what's included vs excluded in problem space |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### PC-05: Problem Impact
| Attribute | Value |
|-----------|-------|
| **Description** | Quantified cost or impact of not solving the problem |
| **Detection** | Cost figures, time lost, revenue impact, customer churn |
| **Quality Criteria** | Measurable impact; time-bounded; attributable to problem |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### PC-06: Root Cause Analysis
| Attribute | Value |
|-----------|-------|
| **Description** | Understanding of why the problem exists |
| **Detection** | "Root cause", "Why this happens", causal analysis |
| **Quality Criteria** | Goes beyond symptoms; identifies underlying factors |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, product |

---

### PC-07: Previous Attempts
| Attribute | Value |
|-----------|-------|
| **Description** | What has been tried before to solve this problem |
| **Detection** | "Previous solutions", "What we've tried", historical context |
| **Quality Criteria** | Documents past attempts and why they failed |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### PC-08: Market Context
| Attribute | Value |
|-----------|-------|
| **Description** | How competitors or the market addresses this problem |
| **Detection** | "Competitive analysis", "Market landscape", alternatives |
| **Quality Criteria** | Identifies alternatives users have; competitive positioning |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### PC-09: Strategic Alignment
| Attribute | Value |
|-----------|-------|
| **Description** | How this problem connects to company/product strategy |
| **Detection** | "Strategic fit", "OKR alignment", "Company goals" |
| **Quality Criteria** | Links to documented strategic objectives |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

### PC-10: Opportunity Size
| Attribute | Value |
|-----------|-------|
| **Description** | Scale of the opportunity if problem is solved |
| **Detection** | TAM, SAM, SOM figures; user counts; revenue potential |
| **Quality Criteria** | Quantified opportunity with assumptions stated |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### PC-11: Problem Urgency
| Attribute | Value |
|-----------|-------|
| **Description** | Why this problem needs to be solved now |
| **Detection** | "Why now", timing drivers, urgency factors |
| **Quality Criteria** | Explains time-sensitivity; consequences of delay |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### PC-12: Problem Frequency
| Attribute | Value |
|-----------|-------|
| **Description** | How often users encounter this problem |
| **Detection** | Frequency data, occurrence rates, usage patterns |
| **Quality Criteria** | Quantified frequency; relevant time period |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### PC-13: Problem Validation
| Attribute | Value |
|-----------|-------|
| **Description** | How the problem statement has been validated |
| **Detection** | "Validation", "Research methodology", user testing |
| **Quality Criteria** | Describes validation approach; participant count |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### PC-14: Problem Owner
| Attribute | Value |
|-----------|-------|
| **Description** | Who is accountable for solving this problem |
| **Detection** | "Owner", "DRI", "Accountable" designations |
| **Quality Criteria** | Named individual with clear accountability |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### PC-15: Background Context
| Attribute | Value |
|-----------|-------|
| **Description** | Historical or organizational context needed to understand problem |
| **Detection** | "Background", "History", "Context" sections |
| **Quality Criteria** | Provides necessary context without over-explaining |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 2: User & Stakeholder (12 items)

### US-01: Primary User Persona
| Attribute | Value |
|-----------|-------|
| **Description** | Definition of the primary user who will use this feature |
| **Detection** | "Primary user", "Target user", "Persona" sections |
| **Quality Criteria** | Named persona; specific characteristics; not generic "users" |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

**Required Sub-elements:**
- [ ] Persona name/label
- [ ] Role or job title
- [ ] Key characteristics
- [ ] Technical proficiency level

---

### US-02: User Goals
| Attribute | Value |
|-----------|-------|
| **Description** | What the user is trying to accomplish |
| **Detection** | "User goals", "Jobs to be done", "User objectives" |
| **Quality Criteria** | Outcome-focused (not feature-focused); tied to persona |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### US-03: User Pain Points
| Attribute | Value |
|-----------|-------|
| **Description** | Specific frustrations or difficulties users face |
| **Detection** | "Pain points", "Frustrations", "Challenges" |
| **Quality Criteria** | Specific; tied to evidence; ranked by severity |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### US-04: User Context
| Attribute | Value |
|-----------|-------|
| **Description** | Environment and circumstances in which users operate |
| **Detection** | "User context", "Usage environment", "Conditions" |
| **Quality Criteria** | Describes where/when/how users encounter problem |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### US-05: Secondary Personas
| Attribute | Value |
|-----------|-------|
| **Description** | Other users who will interact with feature |
| **Detection** | "Secondary users", "Other personas", "Stakeholders" |
| **Quality Criteria** | Distinct from primary; explained why secondary |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic, product |

---

### US-06: Anti-Personas
| Attribute | Value |
|-----------|-------|
| **Description** | Users explicitly NOT being designed for |
| **Detection** | "Anti-personas", "Not for", "Out of scope users" |
| **Quality Criteria** | Explicit exclusions; reasoning provided |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, product |

---

### US-07: User Segments
| Attribute | Value |
|-----------|-------|
| **Description** | How users are segmented (if multiple groups) |
| **Detection** | "Segments", "User types", "Cohorts" |
| **Quality Criteria** | MECE segmentation; criteria for each segment |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### US-08: User Workflow
| Attribute | Value |
|-----------|-------|
| **Description** | Current workflow users follow |
| **Detection** | "Current workflow", "User journey", "Process flow" |
| **Quality Criteria** | Step-by-step; identifies pain points in flow |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### US-09: Business Stakeholders
| Attribute | Value |
|-----------|-------|
| **Description** | Internal stakeholders with interest in this work |
| **Detection** | "Stakeholders", "Business owners", "Sponsors" |
| **Quality Criteria** | Named individuals; their interest/stake defined |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### US-10: Decision Makers
| Attribute | Value |
|-----------|-------|
| **Description** | Who approves decisions and changes |
| **Detection** | "Decision makers", "Approvers", "RACI" |
| **Quality Criteria** | Named individuals; decision authority scope |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

### US-11: User Research Sources
| Attribute | Value |
|-----------|-------|
| **Description** | How user information was gathered |
| **Detection** | "Research", "Interviews", "Surveys", "Analytics" |
| **Quality Criteria** | Methods documented; sample sizes; recency |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### US-12: User Success Definition
| Attribute | Value |
|-----------|-------|
| **Description** | How users will know they've succeeded |
| **Detection** | "User success", "Definition of done for users" |
| **Quality Criteria** | Observable outcome; from user's perspective |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 3: Goals & Success (10 items)

### GS-01: Primary Business Goal
| Attribute | Value |
|-----------|-------|
| **Description** | Main business objective this work serves |
| **Detection** | "Business goal", "Objective", "Purpose" |
| **Quality Criteria** | Single clear goal; tied to company objectives |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### GS-02: Success Metrics Definition
| Attribute | Value |
|-----------|-------|
| **Description** | How success will be measured |
| **Detection** | "Success metrics", "KPIs", "Measures of success" |
| **Quality Criteria** | Named metrics; measurable; owned |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### GS-03: Metric Targets
| Attribute | Value |
|-----------|-------|
| **Description** | Specific targets for success metrics |
| **Detection** | Numeric targets, percentages, thresholds |
| **Quality Criteria** | Quantified; timebound; achievable |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### GS-04: Baseline Measurements
| Attribute | Value |
|-----------|-------|
| **Description** | Current state of success metrics |
| **Detection** | "Baseline", "Current state", "Before" measurements |
| **Quality Criteria** | Current values documented; measurement date |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### GS-05: Measurement Method
| Attribute | Value |
|-----------|-------|
| **Description** | How metrics will be measured |
| **Detection** | "Measurement", "Tracking", "Analytics" approach |
| **Quality Criteria** | Tools identified; methodology clear |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### GS-06: Leading Indicators
| Attribute | Value |
|-----------|-------|
| **Description** | Early signals of success or failure |
| **Detection** | "Leading indicators", "Early signals", "Proxy metrics" |
| **Quality Criteria** | Predictive of outcome; measurable sooner |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### GS-07: Lagging Indicators
| Attribute | Value |
|-----------|-------|
| **Description** | Final outcome metrics |
| **Detection** | "Lagging indicators", "Outcome metrics", "Final measures" |
| **Quality Criteria** | Definitive success measures; appropriate timeframe |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### GS-08: Non-Goals
| Attribute | Value |
|-----------|-------|
| **Description** | What this work explicitly does NOT aim to achieve |
| **Detection** | "Non-goals", "Not trying to", "Explicitly not" |
| **Quality Criteria** | Clear exclusions; prevents scope creep |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### GS-09: Success Timeline
| Attribute | Value |
|-----------|-------|
| **Description** | When success metrics will be evaluated |
| **Detection** | "Measurement timeline", "Evaluation period" |
| **Quality Criteria** | Specific dates; appropriate for metric type |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### GS-10: ROI Projection
| Attribute | Value |
|-----------|-------|
| **Description** | Expected return on investment |
| **Detection** | "ROI", "Business case", "Cost-benefit" |
| **Quality Criteria** | Quantified; assumptions stated; timeframe |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

## Section 4: Requirements (18 items)

### RQ-01: Functional Requirements List
| Attribute | Value |
|-----------|-------|
| **Description** | List of what the system must do |
| **Detection** | "Functional requirements", "Features", "Capabilities" |
| **Quality Criteria** | Each requirement testable; prioritized |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### RQ-02: Requirement Prioritization
| Attribute | Value |
|-----------|-------|
| **Description** | Priority ranking of requirements |
| **Detection** | "Priority", "MoSCoW", "P0/P1/P2" labels |
| **Quality Criteria** | All requirements prioritized; criteria explained |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RQ-03: Requirement Rationale
| Attribute | Value |
|-----------|-------|
| **Description** | Why each requirement is needed |
| **Detection** | "Rationale", "Because", "Needed for" explanations |
| **Quality Criteria** | Links to user need or business goal |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### RQ-04: Non-Functional Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Quality attributes (performance, security, etc.) |
| **Detection** | "NFRs", "Quality requirements", "-ilities" |
| **Quality Criteria** | Quantified where possible; testable |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RQ-05: Performance Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Speed, throughput, latency requirements |
| **Detection** | "Performance", "Speed", "Latency", "Throughput" |
| **Quality Criteria** | Specific numbers; measurement conditions |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic, product |

---

### RQ-06: Security Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Security constraints and requirements |
| **Detection** | "Security", "Authentication", "Authorization" |
| **Quality Criteria** | Specific requirements; compliance mentioned |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### RQ-07: Scalability Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Scale the system must handle |
| **Detection** | "Scalability", "Scale", "Load", "Volume" |
| **Quality Criteria** | Specific numbers; growth projections |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic, product |

---

### RQ-08: Reliability Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Uptime, availability, fault tolerance |
| **Detection** | "Reliability", "Availability", "Uptime", "SLA" |
| **Quality Criteria** | Specific percentages; recovery requirements |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic, product |

---

### RQ-09: Accessibility Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Accessibility standards to meet |
| **Detection** | "Accessibility", "A11y", "WCAG", "ADA" |
| **Quality Criteria** | Standard level specified (WCAG 2.1 AA) |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, product |

---

### RQ-10: Localization Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Language and locale support |
| **Detection** | "Localization", "i18n", "Languages", "Locales" |
| **Quality Criteria** | Languages listed; locale handling specified |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, product |

---

### RQ-11: Data Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Data the feature needs to function |
| **Detection** | "Data requirements", "Data inputs", "Data sources" |
| **Quality Criteria** | Data sources identified; format specified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RQ-12: Integration Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Systems the feature must integrate with |
| **Detection** | "Integrations", "APIs", "Connections" |
| **Quality Criteria** | Systems named; integration type specified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RQ-13: Compliance Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Regulatory or policy compliance needs |
| **Detection** | "Compliance", "Regulatory", "Legal", "Policy" |
| **Quality Criteria** | Specific regulations named; requirements extracted |
| **Severity if Missing** | HIGH (if applicable) |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### RQ-14: Constraint List
| Attribute | Value |
|-----------|-------|
| **Description** | Hard constraints on the solution |
| **Detection** | "Constraints", "Limitations", "Boundaries" |
| **Quality Criteria** | Technical and business constraints listed |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### RQ-15: Out of Scope
| Attribute | Value |
|-----------|-------|
| **Description** | What is explicitly NOT included |
| **Detection** | "Out of scope", "Not included", "Excluded" |
| **Quality Criteria** | Explicit list; prevents scope creep |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RQ-16: Backward Compatibility
| Attribute | Value |
|-----------|-------|
| **Description** | Compatibility with existing functionality |
| **Detection** | "Backward compatible", "Legacy support", "Migration" |
| **Quality Criteria** | Compatibility requirements specified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### RQ-17: Requirement Traceability
| Attribute | Value |
|-----------|-------|
| **Description** | Links between requirements and user needs |
| **Detection** | "Traceability", requirement-to-need mappings |
| **Quality Criteria** | Each requirement traces to user need |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product |

---

### RQ-18: Requirement Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | Dependencies between requirements |
| **Detection** | "Depends on", "Blocked by", "Enables" |
| **Quality Criteria** | Inter-requirement dependencies mapped |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product |

---

## Section 5: User Stories (14 items)

### ST-01: User Story Format
| Attribute | Value |
|-----------|-------|
| **Description** | Stories follow standard format |
| **Detection** | "As a [user] I want [action] so that [benefit]" |
| **Quality Criteria** | Consistent format; all three parts present |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-02: Story Completeness
| Attribute | Value |
|-----------|-------|
| **Description** | Stories cover all requirements |
| **Detection** | Mapping between requirements and stories |
| **Quality Criteria** | Every requirement has story coverage |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-03: Story Size
| Attribute | Value |
|-----------|-------|
| **Description** | Stories are appropriately sized |
| **Detection** | Story points, effort estimates |
| **Quality Criteria** | No stories too large (epic-sized); no trivial stories |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-04: Story Independence
| Attribute | Value |
|-----------|-------|
| **Description** | Stories can be implemented independently |
| **Detection** | Dependency analysis; story sequencing |
| **Quality Criteria** | Minimal dependencies between stories |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-05: Story Persona Match
| Attribute | Value |
|-----------|-------|
| **Description** | Stories reference defined personas |
| **Detection** | "As a" references match persona definitions |
| **Quality Criteria** | No undefined users; consistent naming |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-06: Happy Path Coverage
| Attribute | Value |
|-----------|-------|
| **Description** | Main success scenarios documented |
| **Detection** | Primary user flows covered |
| **Quality Criteria** | Core functionality has stories |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-07: Edge Case Coverage
| Attribute | Value |
|-----------|-------|
| **Description** | Edge cases and exceptions documented |
| **Detection** | Stories for error states, boundaries, exceptions |
| **Quality Criteria** | Key edge cases identified; not exhaustive |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-08: Error Handling Stories
| Attribute | Value |
|-----------|-------|
| **Description** | How errors are handled |
| **Detection** | Stories for failure modes |
| **Quality Criteria** | Key error scenarios covered |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### ST-09: Story Prioritization
| Attribute | Value |
|-----------|-------|
| **Description** | Stories are prioritized |
| **Detection** | Priority labels or ordering |
| **Quality Criteria** | Clear priority; criteria explained |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-10: Story Estimation
| Attribute | Value |
|-----------|-------|
| **Description** | Stories have effort estimates |
| **Detection** | Story points, t-shirt sizes, hours |
| **Quality Criteria** | Consistent estimation approach |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-11: INVEST Compliance
| Attribute | Value |
|-----------|-------|
| **Description** | Stories follow INVEST criteria |
| **Detection** | Independent, Negotiable, Valuable, Estimable, Small, Testable |
| **Quality Criteria** | Most stories meet most criteria |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-12: Story Grouping
| Attribute | Value |
|-----------|-------|
| **Description** | Stories organized logically |
| **Detection** | Epics, themes, features grouping |
| **Quality Criteria** | Logical groupings; hierarchy clear |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic |

---

### ST-13: Negative Stories
| Attribute | Value |
|-----------|-------|
| **Description** | What users should NOT be able to do |
| **Detection** | "As a user I should not be able to..." |
| **Quality Criteria** | Security and access control stories |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### ST-14: Admin Stories
| Attribute | Value |
|-----------|-------|
| **Description** | Administrative functionality |
| **Detection** | Admin user stories |
| **Quality Criteria** | Admin needs covered if applicable |
| **Severity if Missing** | LOW (if applicable) |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

## Section 6: Acceptance Criteria (12 items)

### AC-01: Criteria Presence
| Attribute | Value |
|-----------|-------|
| **Description** | Each story has acceptance criteria |
| **Detection** | AC listed per story |
| **Quality Criteria** | No stories without AC |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | feature, epic, product |

---

### AC-02: Criteria Testability
| Attribute | Value |
|-----------|-------|
| **Description** | Criteria are objectively testable |
| **Detection** | Given/When/Then format or equivalent |
| **Quality Criteria** | Clear pass/fail determination possible |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### AC-03: Criteria Specificity
| Attribute | Value |
|-----------|-------|
| **Description** | Criteria are specific, not vague |
| **Detection** | No subjective terms like "fast", "easy" |
| **Quality Criteria** | Measurable or observable outcomes |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### AC-04: Criteria Completeness
| Attribute | Value |
|-----------|-------|
| **Description** | Criteria cover full story scope |
| **Detection** | All story aspects have criteria |
| **Quality Criteria** | No untested aspects of story |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### AC-05: Negative Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | What should NOT happen |
| **Detection** | Negative test criteria |
| **Quality Criteria** | Key negative scenarios covered |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### AC-06: Boundary Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | Behavior at boundaries defined |
| **Detection** | Min/max values, edge cases |
| **Quality Criteria** | Key boundaries specified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### AC-07: Error Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | Expected error handling |
| **Detection** | Error messages, fallbacks |
| **Quality Criteria** | Error scenarios have expected behavior |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic |

---

### AC-08: Performance Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | Performance thresholds for story |
| **Detection** | Timing, throughput acceptance criteria |
| **Quality Criteria** | Specific numbers for key operations |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### AC-09: UI/UX Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | Visual and interaction acceptance |
| **Detection** | Design references, interaction specs |
| **Quality Criteria** | Clear visual acceptance criteria |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### AC-10: Data Criteria
| Attribute | Value |
|-----------|-------|
| **Description** | Data validation and handling |
| **Detection** | Data format, validation rules |
| **Quality Criteria** | Data acceptance criteria clear |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### AC-11: Definition of Done
| Attribute | Value |
|-----------|-------|
| **Description** | What "done" means for this work |
| **Detection** | "Done when", "Complete when" statements |
| **Quality Criteria** | Unambiguous completion criteria |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### AC-12: Validation Approach
| Attribute | Value |
|-----------|-------|
| **Description** | How criteria will be validated |
| **Detection** | Testing approach, validation method |
| **Quality Criteria** | Validation method clear |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 7: Dependencies (8 items)

### DP-01: External System Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | External systems required |
| **Detection** | "Depends on", "Requires", external system names |
| **Quality Criteria** | All external dependencies listed |
| **Severity if Missing** | CRITICAL |
| **Severity if Incomplete** | HIGH |
| **Applicability** | All types |

---

### DP-02: Internal Team Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | Other teams needed |
| **Detection** | Team names, cross-functional needs |
| **Quality Criteria** | Teams identified; contacts named |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### DP-03: Data Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | Data needed from other sources |
| **Detection** | Data sources, feeds, APIs |
| **Quality Criteria** | Data sources identified; availability confirmed |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### DP-04: Timeline Dependencies
| Attribute | Value |
|-----------|-------|
| **Description** | When dependencies will be ready |
| **Detection** | Dates, milestones for dependencies |
| **Quality Criteria** | Dependency readiness dates specified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### DP-05: Dependency Owners
| Attribute | Value |
|-----------|-------|
| **Description** | Who owns each dependency |
| **Detection** | Owner names, contact info |
| **Quality Criteria** | Named individuals; communication established |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### DP-06: Dependency Status
| Attribute | Value |
|-----------|-------|
| **Description** | Current status of dependencies |
| **Detection** | "Ready", "In progress", "Blocked" status |
| **Quality Criteria** | Current status documented |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### DP-07: Blocking vs Non-blocking
| Attribute | Value |
|-----------|-------|
| **Description** | Classification of dependencies |
| **Detection** | "Blocking", "Required", "Nice to have" labels |
| **Quality Criteria** | Each dependency classified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### DP-08: Dependency Mitigation
| Attribute | Value |
|-----------|-------|
| **Description** | What to do if dependency isn't ready |
| **Detection** | Fallback plans, alternatives |
| **Quality Criteria** | Mitigation for blocking dependencies |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 8: Risks & Assumptions (10 items)

### RA-01: Risk Register
| Attribute | Value |
|-----------|-------|
| **Description** | List of identified risks |
| **Detection** | "Risks", "Risk register", risk table |
| **Quality Criteria** | Comprehensive risk list |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RA-02: Risk Assessment
| Attribute | Value |
|-----------|-------|
| **Description** | Impact and probability for risks |
| **Detection** | Impact/probability ratings |
| **Quality Criteria** | Each risk assessed |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RA-03: Risk Mitigation
| Attribute | Value |
|-----------|-------|
| **Description** | Plans to address risks |
| **Detection** | "Mitigation", "Contingency" plans |
| **Quality Criteria** | High-impact risks have mitigations |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RA-04: Risk Owners
| Attribute | Value |
|-----------|-------|
| **Description** | Who owns each risk |
| **Detection** | Owner assignments |
| **Quality Criteria** | Key risks have owners |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### RA-05: Technical Risks
| Attribute | Value |
|-----------|-------|
| **Description** | Technical challenges and unknowns |
| **Detection** | Technical risk items |
| **Quality Criteria** | Technical risks specifically called out |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### RA-06: Business Risks
| Attribute | Value |
|-----------|-------|
| **Description** | Business and market risks |
| **Detection** | Business risk items |
| **Quality Criteria** | Business risks identified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### RA-07: Assumptions List
| Attribute | Value |
|-----------|-------|
| **Description** | Assumptions being made |
| **Detection** | "Assumptions", "We assume" statements |
| **Quality Criteria** | Key assumptions documented |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### RA-08: Assumption Validation
| Attribute | Value |
|-----------|-------|
| **Description** | How assumptions will be validated |
| **Detection** | Validation plans for assumptions |
| **Quality Criteria** | Critical assumptions have validation plan |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### RA-09: Risk Triggers
| Attribute | Value |
|-----------|-------|
| **Description** | Signals that risk is materializing |
| **Detection** | Early warning indicators |
| **Quality Criteria** | High-impact risks have triggers |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

### RA-10: Contingency Plans
| Attribute | Value |
|-----------|-------|
| **Description** | What to do if risk materializes |
| **Detection** | "If X happens, then Y" plans |
| **Quality Criteria** | High-impact risks have contingencies |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 9: Timeline & Scope (9 items)

### TS-01: Overall Timeline
| Attribute | Value |
|-----------|-------|
| **Description** | High-level timeline for delivery |
| **Detection** | Start date, end date, duration |
| **Quality Criteria** | Specific dates; realistic |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### TS-02: Milestones
| Attribute | Value |
|-----------|-------|
| **Description** | Key checkpoints in timeline |
| **Detection** | "Milestones", checkpoint dates |
| **Quality Criteria** | Meaningful milestones; not just phases |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### TS-03: Phases/Releases
| Attribute | Value |
|-----------|-------|
| **Description** | How work is phased |
| **Detection** | "Phase 1, 2, 3", "MVP, v1, v2" |
| **Quality Criteria** | Clear phase boundaries; scope per phase |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | epic, product, initiative |

---

### TS-04: MVP Definition
| Attribute | Value |
|-----------|-------|
| **Description** | What's included in MVP |
| **Detection** | "MVP", "Minimum viable", "Phase 1 scope" |
| **Quality Criteria** | Explicit MVP scope; truly minimum |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | feature, epic, product |

---

### TS-05: Scope Boundaries
| Attribute | Value |
|-----------|-------|
| **Description** | Clear scope definition |
| **Detection** | "In scope", "Out of scope" sections |
| **Quality Criteria** | Explicit boundaries; no ambiguity |
| **Severity if Missing** | HIGH |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | All types |

---

### TS-06: Resource Requirements
| Attribute | Value |
|-----------|-------|
| **Description** | Team/resources needed |
| **Detection** | "Resources", "Team", "Headcount" |
| **Quality Criteria** | Skills and capacity identified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

### TS-07: Key Dates
| Attribute | Value |
|-----------|-------|
| **Description** | Important external dates |
| **Detection** | Conferences, holidays, dependencies |
| **Quality Criteria** | External constraints noted |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### TS-08: Rollout Strategy
| Attribute | Value |
|-----------|-------|
| **Description** | How feature will be rolled out |
| **Detection** | "Rollout", "Launch", "GA plan" |
| **Quality Criteria** | Phased rollout plan; criteria for expansion |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic, product |

---

### TS-09: Timeline Assumptions
| Attribute | Value |
|-----------|-------|
| **Description** | What timeline depends on |
| **Detection** | "Assumes", timeline prerequisites |
| **Quality Criteria** | Key assumptions affecting timeline noted |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

## Section 10: Technical Considerations (8 items)

### TC-01: Architecture Fit
| Attribute | Value |
|-----------|-------|
| **Description** | How this fits existing architecture |
| **Detection** | "Architecture", "System design" notes |
| **Quality Criteria** | Integration with current systems considered |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | epic, product, initiative |

---

### TC-02: Technical Approach
| Attribute | Value |
|-----------|-------|
| **Description** | High-level technical approach |
| **Detection** | "Technical approach", "Implementation notes" |
| **Quality Criteria** | Feasibility considered; approach reasonable |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### TC-03: Technical Constraints
| Attribute | Value |
|-----------|-------|
| **Description** | Technical limitations |
| **Detection** | "Constraints", "Limitations", technology bounds |
| **Quality Criteria** | Key constraints documented |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | All types |

---

### TC-04: Data Model Impacts
| Attribute | Value |
|-----------|-------|
| **Description** | Changes to data model |
| **Detection** | "Data model", "Schema changes" |
| **Quality Criteria** | Data changes identified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### TC-05: Infrastructure Needs
| Attribute | Value |
|-----------|-------|
| **Description** | Infrastructure requirements |
| **Detection** | "Infrastructure", "Hosting", "Deployment" |
| **Quality Criteria** | Infrastructure needs identified |
| **Severity if Missing** | MEDIUM |
| **Severity if Incomplete** | LOW |
| **Applicability** | product, initiative |

---

### TC-06: Technical Debt
| Attribute | Value |
|-----------|-------|
| **Description** | Tech debt implications |
| **Detection** | "Technical debt", "Future work" |
| **Quality Criteria** | Debt acknowledged; plan noted |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic |

---

### TC-07: Migration Needs
| Attribute | Value |
|-----------|-------|
| **Description** | Data or user migration |
| **Detection** | "Migration", "Transition", "Cutover" |
| **Quality Criteria** | Migration plan if applicable |
| **Severity if Missing** | MEDIUM (if applicable) |
| **Severity if Incomplete** | MEDIUM |
| **Applicability** | epic, product |

---

### TC-08: Monitoring/Observability
| Attribute | Value |
|-----------|-------|
| **Description** | How to monitor in production |
| **Detection** | "Monitoring", "Observability", "Alerts" |
| **Quality Criteria** | Key metrics to monitor identified |
| **Severity if Missing** | LOW |
| **Severity if Incomplete** | LOW |
| **Applicability** | feature, epic, product |

---

## Quick Reference: Critical Items by PRD Type

### Feature PRD (Must Have)
- PC-01: Problem Statement
- US-01: Primary User Persona
- GS-01: Primary Business Goal
- GS-02: Success Metrics
- RQ-01: Functional Requirements
- AC-01: Acceptance Criteria
- DP-01: External Dependencies
- TS-05: Scope Boundaries

### Epic PRD (Must Have)
- PC-01: Problem Statement
- US-01: Primary User Persona
- GS-01: Primary Business Goal
- GS-02: Success Metrics
- RQ-01: Functional Requirements
- RQ-15: Out of Scope
- RA-01: Risk Register
- TS-03: Phases/Releases
- TS-04: MVP Definition

### Product PRD (Must Have)
- PC-01: Problem Statement
- PC-05: Problem Impact
- US-01: Primary User Persona
- GS-01: Primary Business Goal
- GS-02: Success Metrics
- GS-03: Metric Targets
- RQ-01: Functional Requirements
- RQ-04: Non-Functional Requirements
- TC-01: Architecture Fit

### Initiative PRD (Must Have)
- PC-01: Problem Statement
- PC-09: Strategic Alignment
- GS-01: Primary Business Goal
- GS-10: ROI Projection
- RA-01: Risk Register
- RA-07: Assumptions List
- TS-01: Overall Timeline
- TS-06: Resource Requirements
