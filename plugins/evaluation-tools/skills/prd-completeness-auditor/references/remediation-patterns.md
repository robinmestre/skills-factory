# Remediation Patterns Catalog

Standard remediation approaches for PRD gaps organized by gap type and section.

---

## Overview

Each gap detected in an audit needs a clear path to resolution. This catalog provides remediation patterns—proven approaches to fixing common PRD gaps with templates and examples.

**Purpose:** Transform gap detection into actionable improvement.

---

## Remediation by Gap Type

| Gap Type | Primary Pattern | Action Verb | Typical Effort |
|----------|-----------------|-------------|----------------|
| MISSING | Add Content | Create | Medium-Large |
| INCOMPLETE | Expand Content | Extend | Small-Medium |
| INCONSISTENT | Reconcile Content | Align | Medium |
| AMBIGUOUS | Clarify Content | Specify | Small |
| INCORRECT | Correct Content | Fix | Trivial-Small |
| OUTDATED | Update Content | Refresh | Trivial-Small |

---

## Pattern: Add Content (MISSING Gaps)

**When to Use:** Required element is completely absent from PRD.

**Approach:**
1. Identify the appropriate section location
2. Use section template from this catalog
3. Gather information from stakeholders
4. Write new content following template
5. Review with PRD owner

### Templates by Section

#### Problem Statement (PC-01)
```markdown
## Problem Statement

### The Problem
[User segment] experiences [specific pain point] when [context/situation],
resulting in [measurable negative outcome].

### Evidence
- [Quantitative evidence: metrics, support tickets, research data]
- [Qualitative evidence: user quotes, feedback themes]
- Source: [Research study, survey, analytics]

### Impact
- [Business impact: revenue, costs, churn]
- [User impact: time lost, frustration, workarounds]
- [Scale: number of users affected, frequency]

### Why Now
[Urgency factors, market timing, strategic alignment]
```

#### User Persona (US-01)
```markdown
## Primary User Persona: [Name]

**Role:** [Job title or function]
**Context:** [Where they work, team size, industry]

### Characteristics
- Technical proficiency: [Novice/Intermediate/Expert]
- Decision authority: [Yes/No, scope]
- Frequency of use: [Daily/Weekly/Monthly]

### Goals
1. [Primary goal: what they're trying to achieve]
2. [Secondary goal]
3. [Tertiary goal]

### Pain Points
1. [Pain point related to problem]
2. [Current workaround]

### Quote
> "[Verbatim quote from research that captures their perspective]"
```

#### Success Metrics (GS-02, GS-03)
```markdown
## Success Metrics

| Metric | Baseline | Target | Timeline | Measurement |
|--------|----------|--------|----------|-------------|
| [Metric name] | [Current value] | [Target value] | [By when] | [How measured] |

### Primary Success Metric
**[Metric name]:** [Definition]
- Baseline: [Current value] as of [date]
- Target: [Target value] by [date]
- Measurement: [Tool/method]

### Secondary Metrics
1. **[Metric]:** [Target]
2. **[Metric]:** [Target]

### Leading Indicators (Early Signals)
- [Indicator that predicts success]
```

#### Dependencies (DP-01)
```markdown
## Dependencies

### External System Dependencies
| System | Type | Status | Owner | ETA | Risk if Delayed |
|--------|------|--------|-------|-----|-----------------|
| [Name] | API/Data/Service | Ready/In Progress/Blocked | [Name] | [Date] | [Impact] |

### Team Dependencies
| Team | Dependency | Status | Contact | Notes |
|------|------------|--------|---------|-------|
| [Team] | [What we need] | [Status] | [Name] | [Details] |

### Mitigation Plans
- If [dependency] is delayed: [fallback plan]
```

#### Risk Register (RA-01)
```markdown
## Risks

| ID | Risk | Probability | Impact | Mitigation | Owner |
|----|------|-------------|--------|------------|-------|
| R1 | [Risk description] | [H/M/L] | [H/M/L] | [Mitigation plan] | [Name] |

### Risk Details

#### R1: [Risk Name]
**Description:** [Full risk description]
**Trigger:** [What would indicate this risk is materializing]
**Mitigation:** [Steps to reduce probability or impact]
**Contingency:** [What to do if risk occurs]
**Owner:** [Name]
```

---

## Pattern: Expand Content (INCOMPLETE Gaps)

**When to Use:** Element exists but lacks required detail.

**Approach:**
1. Identify what specific sub-elements are missing
2. Use expansion template for that element
3. Gather missing information
4. Add detail within existing structure
5. Verify completeness against checklist

### Expansion Templates

#### Incomplete Persona → Expand
```markdown
### [Existing Persona Name] — EXPANDED

[Keep existing content]

#### ADDED: Goals (was missing)
1. [Primary goal]
2. [Secondary goal]

#### ADDED: Pain Points (was missing)
1. [Pain point 1]
2. [Pain point 2]

#### ADDED: Context (was missing)
- Work environment: [Description]
- Tools they use: [List]
- Constraints: [What limits them]
```

#### Incomplete Acceptance Criteria → Expand
```markdown
### [User Story] — EXPANDED AC

[Keep existing criteria]

#### ADDED: Negative Criteria
- Given [condition], when [action], then [should NOT happen]

#### ADDED: Boundary Criteria
- Given [boundary condition], when [action], then [expected behavior]

#### ADDED: Error Criteria
- Given [error condition], when [action], then [error handling]
```

#### Incomplete Risk → Expand
```markdown
### [Risk Name] — EXPANDED

[Keep existing risk description]

#### ADDED: Mitigation Plan
1. [Preventive action]
2. [Monitoring action]
3. [Response action]

#### ADDED: Trigger Indicators
- [Signal 1 that risk is materializing]
- [Signal 2]

#### ADDED: Contingency
If this risk occurs: [response plan]
```

---

## Pattern: Reconcile Content (INCONSISTENT Gaps)

**When to Use:** Element contradicts other parts of PRD.

**Approach:**
1. Document both conflicting statements
2. Identify which is authoritative (or escalate to stakeholder)
3. Update non-authoritative statement to align
4. Add note explaining reconciliation
5. Review for cascade effects

### Reconciliation Process

#### Step 1: Document Conflict
```markdown
## Conflict Identified

**Location A:** [Section, line number]
> "[Exact quote from A]"

**Location B:** [Section, line number]
> "[Exact quote from B]"

**Nature of Conflict:** [Describe how they contradict]
```

#### Step 2: Determine Truth
```markdown
## Resolution Decision

**Authoritative Source:** [A or B]
**Rationale:** [Why this source is correct]
**Decided By:** [Name, date]
```

#### Step 3: Apply Fix
```markdown
## Applied Fix

**Updated Location:** [Which was changed]
**Original Text:** "[What it said]"
**New Text:** "[What it now says]"
**Reconciliation Note:** [Optional note explaining history]
```

### Common Reconciliation Scenarios

| Conflict Type | Resolution Approach |
|---------------|---------------------|
| Scope vs Requirements | Requirements define scope |
| Timeline vs Milestones | Adjust whichever is less constrained |
| Persona vs User Story | User story should match persona |
| Goals vs Metrics | Metrics should measure goals |
| MVP vs Full Scope | MVP is authoritative for v1 |

---

## Pattern: Clarify Content (AMBIGUOUS Gaps)

**When to Use:** Element is unclear or open to interpretation.

**Approach:**
1. Identify the ambiguous term or statement
2. Define specifically or add metrics
3. Replace vague language with precise language
4. Get stakeholder confirmation of intended meaning
5. Update PRD with clarified language

### Clarification Templates

#### Vague Performance → Specific
```markdown
**BEFORE (Ambiguous):**
> "The system should be fast."

**AFTER (Clarified):**
> "The system should return search results within 200ms at the 95th percentile
> under normal load (1000 concurrent users)."
```

#### Vague User Reference → Specific
```markdown
**BEFORE (Ambiguous):**
> "Some users may need advanced features."

**AFTER (Clarified):**
> "Power Users (see Persona section) require access to advanced export
> features including custom date ranges and field selection."
```

#### Vague Acceptance → Specific
```markdown
**BEFORE (Ambiguous):**
> "User can easily navigate to settings."

**AFTER (Clarified):**
> "Given a logged-in user on any page, when they click the profile icon
> in the header, then the settings page loads within 2 clicks and < 3 seconds."
```

### Clarification Checklist

For any vague term, ask:
- [ ] Can this be quantified? (Add numbers)
- [ ] Does this reference a defined persona? (Link to persona)
- [ ] Is there a threshold or boundary? (Specify limit)
- [ ] Can this be tested objectively? (Add test criteria)
- [ ] Who decides if this is satisfied? (Name decider)

---

## Pattern: Correct Content (INCORRECT Gaps)

**When to Use:** Element contains factually wrong information.

**Approach:**
1. Document the incorrect statement
2. Identify the correct information with source
3. Replace incorrect with correct
4. Add verification note
5. Check for cascade effects

### Correction Template

```markdown
## Correction Applied

**Location:** [Section, line number]

**Incorrect Statement:**
> "[Original incorrect text]"

**Correct Statement:**
> "[New corrected text]"

**Source/Verification:**
- [How we verified the correct information]
- [Source: documentation, SME, system check]
- [Verified by: Name, Date]

**Cascade Check:**
- [ ] Checked for other references to this information
- [ ] Updated all instances
```

### Common Corrections

| Error Type | Verification Method |
|------------|---------------------|
| API/Endpoint wrong | Check API documentation |
| System capacity wrong | Check monitoring/architecture docs |
| Date/Timeline wrong | Check project records |
| Compliance requirement wrong | Check legal/compliance team |
| Owner/Contact wrong | Check org chart/directory |
| Technical specification wrong | Check with engineering |

---

## Pattern: Update Content (OUTDATED Gaps)

**When to Use:** Element was once correct but is now stale.

**Approach:**
1. Identify the outdated information
2. Research current state
3. Update to current information
4. Add "last verified" notation
5. Consider adding maintenance reminder

### Update Template

```markdown
## Update Applied

**Location:** [Section, line number]

**Outdated Statement:**
> "[Original outdated text]"

**Updated Statement:**
> "[New current text]"
>
> _Last verified: [Date] by [Name]_

**Change Context:**
- Previous state was accurate as of: [When it was correct]
- Changed because: [What changed in the real world]
```

### Staleness Prevention

Add maintenance prompts:
```markdown
<!-- PRD MAINTENANCE NOTE -->
The following sections require periodic review:
- Dependencies: Review monthly or when dependency ships
- Timeline: Review at each milestone
- Stakeholders: Review if org changes
- Technical constraints: Review with architecture changes

Last full review: [Date]
Next review due: [Date]
```

---

## Section-Specific Remediation Quick Reference

### Problem & Context Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| PC-01 Problem | Stakeholder interview | Add evidence | Quantify impact |
| PC-02 Evidence | Gather data | Add sources | Cite methodology |
| PC-05 Impact | Calculate costs | Add dimensions | Add numbers |

### User & Stakeholder Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| US-01 Persona | User research | Add goals/pains | Define characteristics |
| US-02 Goals | Interview users | Prioritize goals | Add measurable outcomes |
| US-08 Workflow | Map current flow | Add steps | Add decision points |

### Goals & Success Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| GS-01 Goal | Define with stakeholders | Link to strategy | Make measurable |
| GS-02 Metrics | Choose key metrics | Add baseline/target | Define measurement |
| GS-03 Targets | Set with stakeholders | Add timeframe | Add thresholds |

### Requirements Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| RQ-01 Functional | Derive from goals | Add details | Make testable |
| RQ-04 NFRs | Review quality needs | Add specifics | Add numbers |
| RQ-15 Out of Scope | Define boundaries | Add items | Be explicit |

### User Stories Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| ST-01 Format | Write stories | Complete format | Clarify "so that" |
| ST-06 Happy Path | Map core flows | Add steps | Add specifics |
| ST-07 Edge Cases | Brainstorm failures | Add scenarios | Define boundaries |

### Acceptance Criteria Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| AC-01 Presence | Write for each story | Cover all aspects | Use Given/When/Then |
| AC-02 Testability | Reframe as tests | Add test steps | Add pass/fail criteria |
| AC-06 Boundaries | Identify limits | Add min/max | Specify exact values |

### Dependencies Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| DP-01 External | Map integrations | Add details | Specify API/data |
| DP-04 Timeline | Get ETAs | Add milestones | Add committed dates |
| DP-08 Mitigation | Plan alternatives | Add details | Define triggers |

### Risks & Assumptions Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| RA-01 Risks | Brainstorm threats | Add assessment | Quantify probability |
| RA-03 Mitigation | Plan responses | Add steps | Define ownership |
| RA-07 Assumptions | Surface beliefs | Add validation | Make explicit |

### Timeline & Scope Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| TS-01 Timeline | Work with eng | Add milestones | Add specific dates |
| TS-04 MVP | Define minimum | Clarify boundaries | List explicit features |
| TS-05 Boundaries | Create In/Out lists | Add items | Remove "etc." |

### Technical Gaps

| Item | If MISSING | If INCOMPLETE | If AMBIGUOUS |
|------|------------|---------------|--------------|
| TC-01 Architecture | Consult engineering | Add considerations | Specify systems |
| TC-03 Constraints | Review with tech lead | Add details | Quantify limits |
| TC-07 Migration | Plan transition | Add steps | Define rollback |

---

## Effort Estimation Guide

| Effort Level | Definition | Activities | Time Range |
|--------------|------------|------------|------------|
| **Trivial** | Quick fix, obvious solution | Correct typo, update date, fix reference | < 30 min |
| **Small** | Clear scope, single section | Clarify term, expand incomplete item, add missing detail | 30 min - 2 hrs |
| **Medium** | Multiple sections or research | Write new section, reconcile conflicts, gather stakeholder input | 2 - 8 hrs |
| **Large** | Significant rework or discovery | Major section missing, fundamental restructure, extensive research | 1+ days |

### Effort by Gap Type

| Gap Type | Typical Effort | Effort Drivers |
|----------|----------------|----------------|
| MISSING | Medium-Large | Need to create from scratch, may need research |
| INCOMPLETE | Small-Medium | Structure exists, filling in details |
| INCONSISTENT | Medium | Need to identify truth, update multiple places |
| AMBIGUOUS | Small | Clarification usually straightforward |
| INCORRECT | Trivial-Small | Once truth known, quick to fix |
| OUTDATED | Trivial-Small | Update to current state |

---

## Priority Assignment Guide

| Priority | Criteria | Action Timeline |
|----------|----------|-----------------|
| **Immediate** | CRITICAL severity; blocks understanding | Before any development |
| **Short-term** | HIGH severity; causes significant rework | Before sprint start |
| **Long-term** | MEDIUM severity; degrades quality | During development |
| **Optional** | LOW severity; nice-to-have | When convenient |

### Priority Decision Tree

```
Is this gap CRITICAL severity?
├─ YES → IMMEDIATE
└─ NO
    ├─ Is it HIGH severity AND in core path?
    │   ├─ YES → SHORT-TERM
    │   └─ NO
    │       ├─ Is it MEDIUM severity?
    │       │   ├─ YES → LONG-TERM
    │       │   └─ NO → OPTIONAL
```
