# MECE Coverage Framework for PRD Audits

Mutually Exclusive, Collectively Exhaustive coverage verification for Product Requirements Documents.

---

## Overview

A complete PRD must address all 10 dimensions without overlap. This framework ensures systematic coverage assessment and identifies structural gaps that item-level checklists might miss.

**MECE Principle:**
- **Mutually Exclusive:** Each PRD section maps to exactly ONE dimension
- **Collectively Exhaustive:** All 10 dimensions together cover everything a PRD should address

---

## The 10 Coverage Dimensions

| Dim | Name | Core Question | Critical Checklist Items |
|-----|------|---------------|--------------------------|
| D1 | Problem Space | What problem are we solving? | PC-01, PC-02, PC-03, PC-05 |
| D2 | User Context | Who has this problem? | US-01, US-02, US-03, US-05 |
| D3 | Business Context | Why does the business care? | GS-01, GS-02, GS-03 |
| D4 | Solution Requirements | What must the solution do? | RQ-01 to RQ-10 |
| D5 | User Experience | How will users interact? | ST-01 to ST-10 |
| D6 | Quality Criteria | How do we know it's right? | AC-01 to AC-12 |
| D7 | Dependencies | What do we need from others? | DP-01 to DP-08 |
| D8 | Risk Landscape | What could go wrong? | RA-01 to RA-10 |
| D9 | Execution Context | When and how will we build? | TS-01 to TS-09 |
| D10 | Technical Fit | How does it fit the system? | TC-01 to TC-08 |

---

## Dimension Details

### D1: Problem Space

**Purpose:** Establish the problem worth solving and evidence it exists.

**Key Questions:**
- What is the specific problem?
- Who experiences this problem?
- What evidence proves the problem exists?
- What is the cost of not solving it?
- What has been tried before?

**Expected PRD Sections:**
- Problem Statement
- Background/Context
- Current State Analysis
- Problem Evidence/Data

**Coverage Indicators:**
- [ ] Problem is stated (not solution)
- [ ] Evidence supports problem existence
- [ ] Impact/cost is quantified
- [ ] Root cause is identified

**Common Gaps:**
- Solution masquerading as problem
- Assertion without evidence
- Problem too vague or broad

---

### D2: User Context

**Purpose:** Define who has the problem and what they need.

**Key Questions:**
- Who are the primary users?
- What are their characteristics?
- What are their goals and motivations?
- What is their current workflow?
- What constraints do they have?

**Expected PRD Sections:**
- User Personas
- Target Audience
- User Segments
- Jobs-to-be-Done

**Coverage Indicators:**
- [ ] Primary persona defined
- [ ] User goals articulated
- [ ] Current behavior documented
- [ ] User constraints identified

**Common Gaps:**
- Generic "users" without specificity
- Missing secondary personas
- No distinction between user types

---

### D3: Business Context

**Purpose:** Connect to business objectives and success criteria.

**Key Questions:**
- What business goal does this serve?
- How will we measure success?
- What is the expected ROI?
- How does this align with strategy?
- What is the opportunity cost?

**Expected PRD Sections:**
- Business Goals
- Success Metrics
- KPIs
- Strategic Alignment

**Coverage Indicators:**
- [ ] Business goal explicitly stated
- [ ] Success metrics are measurable
- [ ] Metrics have targets
- [ ] Timeframe for measurement defined

**Common Gaps:**
- Vanity metrics only
- No quantified targets
- Disconnect from company OKRs

---

### D4: Solution Requirements

**Purpose:** Specify what the solution must do functionally.

**Key Questions:**
- What features are required?
- What are the functional requirements?
- What are the non-functional requirements?
- What are the constraints?
- What is explicitly out of scope?

**Expected PRD Sections:**
- Functional Requirements
- Non-Functional Requirements
- Feature List
- Constraints
- Out of Scope

**Coverage Indicators:**
- [ ] Functional requirements listed
- [ ] Requirements are testable
- [ ] NFRs specified (performance, security)
- [ ] Scope boundaries explicit

**Common Gaps:**
- Requirements describe HOW not WHAT
- Missing NFRs
- No explicit out-of-scope

---

### D5: User Experience

**Purpose:** Describe how users will interact with the solution.

**Key Questions:**
- What is the user workflow?
- What are the key user stories?
- What are the interaction points?
- What is the expected user journey?
- What are the edge cases?

**Expected PRD Sections:**
- User Stories
- User Flows
- Use Cases
- Scenarios

**Coverage Indicators:**
- [ ] User stories follow format (As a... I want... So that...)
- [ ] Happy path defined
- [ ] Edge cases covered
- [ ] Error states addressed

**Common Gaps:**
- Stories too large (epics)
- Missing edge cases
- No error handling scenarios

---

### D6: Quality Criteria

**Purpose:** Define how to verify the solution meets requirements.

**Key Questions:**
- How will we test each requirement?
- What are the acceptance criteria?
- What defines "done"?
- How will we validate with users?
- What are the quality thresholds?

**Expected PRD Sections:**
- Acceptance Criteria
- Definition of Done
- Test Scenarios
- Validation Plan

**Coverage Indicators:**
- [ ] AC for each user story
- [ ] AC are testable (Given/When/Then)
- [ ] Quality thresholds specified
- [ ] Validation approach defined

**Common Gaps:**
- Vague acceptance criteria
- Missing negative test cases
- No performance thresholds

---

### D7: Dependencies

**Purpose:** Identify what's needed from other teams/systems.

**Key Questions:**
- What external systems are involved?
- What teams must contribute?
- What are the integration points?
- What data is needed?
- What are the blocking dependencies?

**Expected PRD Sections:**
- Dependencies
- Integrations
- External Requirements
- Cross-team Coordination

**Coverage Indicators:**
- [ ] External systems listed
- [ ] Team dependencies identified
- [ ] Data dependencies mapped
- [ ] Blocking vs non-blocking classified

**Common Gaps:**
- No dependencies section
- Missing data dependencies
- Undocumented API needs

---

### D8: Risk Landscape

**Purpose:** Anticipate what could go wrong and how to respond.

**Key Questions:**
- What could prevent success?
- What are the technical risks?
- What are the business risks?
- What are the mitigation strategies?
- What assumptions might be wrong?

**Expected PRD Sections:**
- Risks
- Assumptions
- Mitigations
- Contingencies

**Coverage Indicators:**
- [ ] Risks identified
- [ ] Impact assessed
- [ ] Probability estimated
- [ ] Mitigations planned
- [ ] Assumptions explicit

**Common Gaps:**
- No risk section
- Risks without mitigations
- Hidden assumptions

---

### D9: Execution Context

**Purpose:** Define when and how this will be built.

**Key Questions:**
- What is the timeline?
- What are the milestones?
- What are the phases?
- What is the prioritization?
- What resources are needed?

**Expected PRD Sections:**
- Timeline
- Milestones
- Phases/Releases
- Prioritization
- Resource Requirements

**Coverage Indicators:**
- [ ] Timeline realistic
- [ ] Milestones defined
- [ ] Phases scoped
- [ ] Priorities clear (MoSCoW)

**Common Gaps:**
- Unrealistic timeline
- No phasing strategy
- Everything is P0

---

### D10: Technical Fit

**Purpose:** Ensure solution fits technical landscape.

**Key Questions:**
- How does this fit existing architecture?
- What technical constraints exist?
- What technical debt implications?
- What infrastructure is needed?
- What security considerations?

**Expected PRD Sections:**
- Technical Considerations
- Architecture Notes
- Infrastructure Requirements
- Security Requirements
- Technical Constraints

**Coverage Indicators:**
- [ ] Architecture fit assessed
- [ ] Technical constraints noted
- [ ] Security considered
- [ ] Infrastructure needs identified

**Common Gaps:**
- No technical section
- Ignoring existing systems
- Missing security review

---

## MECE Verification Process

### Step 1: Section Enumeration

List all sections in the PRD:

```
| # | Section Title | Content Summary |
|---|---------------|-----------------|
| 1 | [Title] | [Brief summary] |
| 2 | ... | ... |
```

### Step 2: Dimension Mapping

Map each section to exactly one dimension:

```
| Section | Assigned Dimension | Confidence |
|---------|-------------------|------------|
| Problem Statement | D1: Problem Space | HIGH |
| User Personas | D2: User Context | HIGH |
| ... | ... | ... |
```

**Mapping Rules:**
- Each section maps to ONE dimension only
- If section spans multiple, assign to primary
- Note secondary dimension coverage in comments
- Flag "orphan" sections that don't fit any dimension

### Step 3: Coverage Assessment

Calculate coverage per dimension:

```
| Dimension | Sections Mapped | Items Covered | Coverage Score | Status |
|-----------|-----------------|---------------|----------------|--------|
| D1 | 2 | 12/15 | 80% | COVERED |
| D2 | 1 | 8/12 | 67% | PARTIAL |
| D3 | 0 | 0/10 | 0% | MISSING |
| ... | ... | ... | ... | ... |
```

**Coverage Status:**
- **COVERED:** >80% of critical items present
- **PARTIAL:** 50-80% coverage
- **MINIMAL:** 20-50% coverage
- **MISSING:** <20% or no mapping

### Step 4: Gap Identification

Flag structural gaps:

```
STRUCTURAL GAPS IDENTIFIED:

1. D3 (Business Context) - MISSING
   - No sections map to business goals
   - Impact: Cannot assess success criteria
   - Severity: CRITICAL

2. D7 (Dependencies) - MINIMAL
   - Brief mention but no detail
   - Impact: Unknown integration risk
   - Severity: HIGH
```

### Step 5: Overlap Detection

Check for MECE violations:

```
OVERLAP DETECTED:

- "Requirements" section contains:
  - Functional requirements (D4) ✓
  - Acceptance criteria (D6) ✗ Should be separate

RECOMMENDATION: Split into distinct sections
```

---

## Coverage Score Calculation

### Per-Dimension Score

```
dimension_coverage = (present_items / required_items) × quality_factor

quality_factor:
  - All items present and clear: 1.0
  - Items present but some ambiguous: 0.8
  - Items present but incomplete: 0.6
  - Items present but low quality: 0.4
```

### Overall Coverage Score

```
overall_coverage = Σ(dimension_coverage × dimension_weight) / Σ(dimension_weight)

Dimension weights (by PRD type):
  feature: D4=1.5, D5=1.5, D6=1.5, others=1.0
  epic: D4=1.5, D7=1.5, D9=1.5, others=1.0
  product: D1=1.5, D3=1.5, D10=1.5, others=1.0
  initiative: D1=1.5, D3=1.5, D8=1.5, others=1.0
```

---

## Quick MECE Audit Checklist

Use this for rapid assessment:

```
[ ] D1: Problem clearly defined with evidence
[ ] D2: Users identified with specific personas
[ ] D3: Business goals stated with measurable metrics
[ ] D4: Functional requirements are testable
[ ] D5: User stories follow standard format
[ ] D6: Acceptance criteria are verifiable
[ ] D7: Dependencies mapped (internal + external)
[ ] D8: Risks identified with mitigations
[ ] D9: Timeline defined with milestones
[ ] D10: Technical considerations documented
```

**Quick Score:**
- 10/10: Excellent structure
- 8-9/10: Good, minor gaps
- 6-7/10: Acceptable, address gaps
- 4-5/10: Significant gaps
- <4/10: Incomplete, major revision needed

---

## Dimension-Checklist Item Mapping

### Quick Reference

| Dimension | Checklist Items | Count |
|-----------|-----------------|-------|
| D1: Problem Space | PC-01 to PC-15 | 15 |
| D2: User Context | US-01 to US-12 | 12 |
| D3: Business Context | GS-01 to GS-10 | 10 |
| D4: Solution Requirements | RQ-01 to RQ-18 | 18 |
| D5: User Experience | ST-01 to ST-14 | 14 |
| D6: Quality Criteria | AC-01 to AC-12 | 12 |
| D7: Dependencies | DP-01 to DP-08 | 8 |
| D8: Risk Landscape | RA-01 to RA-10 | 10 |
| D9: Execution Context | TS-01 to TS-09 | 9 |
| D10: Technical Fit | TC-01 to TC-08 | 8 |
| **TOTAL** | | **116** |

---

## Common MECE Violations

### 1. Missing Dimensions

**Pattern:** Entire dimension absent from PRD.

**Most Common:**
- D7 (Dependencies) - 45% of PRDs missing
- D8 (Risk Landscape) - 38% of PRDs missing
- D10 (Technical Fit) - 30% of PRDs missing

**Fix:** Add explicit section for dimension.

### 2. Blurred Boundaries

**Pattern:** Single section tries to cover multiple dimensions.

**Most Common:**
- "Requirements" covering D4+D5+D6
- "Overview" covering D1+D2+D3
- "Technical" covering D7+D10

**Fix:** Split into distinct sections per dimension.

### 3. Orphan Content

**Pattern:** Content that doesn't fit any dimension.

**Examples:**
- Historical context (may indicate scope creep)
- Future roadmap (beyond current scope)
- Team org charts (not requirements)

**Fix:** Remove or explicitly scope out.

### 4. Dimension Imbalance

**Pattern:** Some dimensions over-documented, others under.

**Example:**
- D5 (User Experience) with 50 user stories
- D6 (Quality Criteria) with 2 acceptance criteria

**Fix:** Balance depth across dimensions.

---

## Integration with Item-Level Audit

The MECE framework works in conjunction with item-level verification:

1. **Phase 2** uses MECE mapping to identify structural gaps
2. **Phase 3** uses checklist items within each dimension
3. **Phase 6** reports both structural and item-level findings

```
MECE Framework (Structural)
         │
         ▼
┌─────────────────┐
│ D1: Problem     │ ← PC-01 to PC-15 (15 items)
│ D2: User        │ ← US-01 to US-12 (12 items)
│ D3: Business    │ ← GS-01 to GS-10 (10 items)
│ ...             │
└─────────────────┘
         │
         ▼
Item-Level Checklist (Detail)
```

This two-layer approach catches both:
- Structural gaps (missing entire dimensions)
- Detail gaps (present but incomplete dimensions)
