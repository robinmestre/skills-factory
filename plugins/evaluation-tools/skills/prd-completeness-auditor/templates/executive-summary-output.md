# Executive Summary Output Template

Stakeholder-friendly summary of PRD audit findings.

---

## Overview

The executive summary distills audit findings into a concise format for stakeholders who need to understand PRD readiness without diving into full details.

**Use when:** `output_format: executive` or as part of `output_format: full`

---

## Template

```markdown
# PRD Audit Summary: [PRD Title]

**Audit Date:** [YYYY-MM-DD]
**PRD Type:** [Feature / Epic / Product / Initiative]
**Audit Depth:** [Quick / Standard / Comprehensive]
**Overall Assessment:** [CRITICAL ISSUES / SIGNIFICANT GAPS / MINOR ISSUES / ACCEPTABLE / EXCELLENT]

---

## At a Glance

| Metric | Value | Status |
|--------|-------|--------|
| Total Gaps Found | [N] | [indicator] |
| Critical Issues | [N] | [RED if >0, GREEN if 0] |
| High Priority Issues | [N] | [YELLOW if >3, GREEN if ≤3] |
| Blocking Issues | [N] | [RED if >0, GREEN if 0] |
| Anti-Patterns Detected | [N] | [YELLOW if >0, GREEN if 0] |
| Checklist Coverage | [N%] | [RED <60%, YELLOW 60-80%, GREEN >80%] |
| Ready for Development | [YES / NO / WITH CONDITIONS] | [indicator] |

---

## Readiness Verdict

### [IF READY]: Ready for Development

This PRD is ready for development with minor improvements recommended during implementation.

**Confidence Level:** [HIGH / MEDIUM]

**Proceed with:** Normal sprint planning. Address [N] low-priority items during development.

---

### [IF READY WITH CONDITIONS]: Ready with Conditions

This PRD can proceed to development IF the following [N] conditions are met:

1. **[Condition 1]:** [Brief description of what must be done]
   - Gap: [GAP-XXX]
   - Effort: [effort level]
   - Owner: [TBD or assigned]

2. **[Condition 2]:** [Brief description]
   - Gap: [GAP-XXX]
   - Effort: [effort level]
   - Owner: [TBD or assigned]

**Estimated Time to Ready:** [X hours/days] of focused PRD work

---

### [IF NOT READY]: Not Ready for Development

This PRD has [N] critical issues that must be resolved before development can begin.

**Blocking Issues:**
1. **[Issue Title]:** [Brief description]
   - Impact: [What happens if we proceed]
   - Effort to Fix: [effort level]

2. **[Issue Title]:** [Brief description]
   - Impact: [What happens if we proceed]
   - Effort to Fix: [effort level]

**Recommended Action:** Schedule PRD revision session before sprint planning.

---

## Key Findings

### Strengths

The PRD demonstrates strength in these areas:

1. **[Strength Area 1]:** [What's done well]
   - Sections: [Which sections are strong]
   - Coverage: [N%]

2. **[Strength Area 2]:** [What's done well]
   - Sections: [Which sections are strong]
   - Coverage: [N%]

3. **[Strength Area 3]:** [What's done well]
   - Sections: [Which sections are strong]
   - Coverage: [N%]

---

### Critical Issues (Must Fix Before Development)

[Include only if CRITICAL gaps exist]

| # | Issue | Section | Impact | Fix Effort |
|---|-------|---------|--------|------------|
| 1 | [Issue title] | [Section] | [Impact in 5 words] | [Effort] |
| 2 | [Issue title] | [Section] | [Impact in 5 words] | [Effort] |

**Detailed Critical Issues:**

#### 1. [Issue Title]

**Problem:** [Clear description of what's wrong]

**Impact if Not Fixed:** [What happens to development]

**Recommended Fix:** [Action in one sentence]

**Effort:** [Level] ([time estimate if known])

---

### Significant Gaps (Should Fix Before Sprint Start)

[Include only if HIGH severity gaps exist]

| # | Gap | Section | Quick Fix |
|---|-----|---------|-----------|
| 1 | [Gap title] | [Section] | [Action in 5-7 words] |
| 2 | [Gap title] | [Section] | [Action in 5-7 words] |
| 3 | [Gap title] | [Section] | [Action in 5-7 words] |

---

### Anti-Patterns Detected

[Include only if anti-patterns found]

| Pattern | Instances | Severity | Quick Description |
|---------|-----------|----------|-------------------|
| [AP-XX Name] | [N] | [Level] | [5-word description] |

---

## Coverage by Section

| Section | Items | Passed | Coverage | Status |
|---------|-------|--------|----------|--------|
| Problem & Context | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| User & Stakeholder | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Goals & Success | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Requirements | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| User Stories | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Acceptance Criteria | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Dependencies | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Risks & Assumptions | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Timeline & Scope | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| Technical | [N] | [N] | [N%] | [GREEN/YELLOW/RED] |
| **TOTAL** | **[N]** | **[N]** | **[N%]** | **[STATUS]** |

**Status Legend:**
- GREEN (≥80%): Strong coverage
- YELLOW (60-79%): Adequate but gaps exist
- RED (<60%): Significant gaps

---

## Recommended Next Steps

### Immediate (Before Any Development)

- [ ] [Action 1 - highest priority]
- [ ] [Action 2]

### Before Sprint Start

- [ ] [Action 1]
- [ ] [Action 2]
- [ ] [Action 3]

### During Development

- [ ] [Action 1]
- [ ] [Action 2]

---

## Summary

[1-2 paragraph narrative summarizing the audit findings, overall assessment, and recommended path forward. Should be readable standalone for executives who skip the details.]

---

*Full audit details available in GAP-INVENTORY artifact: [artifact_id]*

*Audit performed by: prd-completeness-auditor v2.0*
```

---

## Status Indicator Guide

### Traffic Light Colors

| Color | Meaning | When to Use |
|-------|---------|-------------|
| GREEN | Good / Pass | ≥80% coverage, 0 critical issues, ready |
| YELLOW | Caution / Needs Work | 60-79% coverage, some issues |
| RED | Alert / Blocking | <60% coverage, critical issues |

### Readiness Verdict Criteria

| Verdict | Criteria |
|---------|----------|
| **Ready** | 0 CRITICAL, ≤2 HIGH, coverage ≥75% |
| **Ready with Conditions** | 0 CRITICAL, ≤5 HIGH (actionable), coverage ≥60% |
| **Not Ready** | Any CRITICAL OR >5 HIGH OR coverage <60% |

### Coverage Status Thresholds

| Coverage % | Status | Meaning |
|------------|--------|---------|
| ≥80% | GREEN | Strong - minor improvements only |
| 60-79% | YELLOW | Adequate - gaps should be addressed |
| <60% | RED | Insufficient - significant work needed |

---

## Example Populated Summary

```markdown
# PRD Audit Summary: Checkout Optimization Feature

**Audit Date:** 2024-03-15
**PRD Type:** Feature
**Audit Depth:** Standard
**Overall Assessment:** SIGNIFICANT GAPS

---

## At a Glance

| Metric | Value | Status |
|--------|-------|--------|
| Total Gaps Found | 16 | YELLOW |
| Critical Issues | 1 | RED |
| High Priority Issues | 4 | YELLOW |
| Blocking Issues | 1 | RED |
| Anti-Patterns Detected | 1 | YELLOW |
| Checklist Coverage | 74% | YELLOW |
| Ready for Development | WITH CONDITIONS | YELLOW |

---

## Readiness Verdict

### Ready with Conditions

This PRD can proceed to development IF the following 2 conditions are met:

1. **Add Acceptance Criteria:** User stories ST-03 through ST-08 require acceptance criteria
   - Gap: GAP-001
   - Effort: Large (4-6 hours)
   - Owner: TBD

2. **Map Dependencies:** Payment and inventory integrations need documentation
   - Gap: GAP-003
   - Effort: Medium (2-4 hours)
   - Owner: TBD

**Estimated Time to Ready:** 6-10 hours of focused PRD work

---

## Key Findings

### Strengths

1. **Problem Definition:** Clear, evidence-backed problem statement
   - Sections: Problem & Context
   - Coverage: 87%

2. **User Understanding:** Well-defined primary persona with research backing
   - Sections: User & Stakeholder
   - Coverage: 83%

3. **Requirements Structure:** Functional requirements are clear and prioritized
   - Sections: Requirements
   - Coverage: 78%

---

### Critical Issues (Must Fix Before Development)

| # | Issue | Section | Impact | Fix Effort |
|---|-------|---------|--------|------------|
| 1 | Missing acceptance criteria | User Stories | Cannot test features | Large |

#### 1. Missing Acceptance Criteria

**Problem:** 6 of 8 user stories have no acceptance criteria defined

**Impact if Not Fixed:** QA cannot write tests, developers may misinterpret requirements, likely rework

**Recommended Fix:** Add Given/When/Then criteria for each story (2+ per story)

**Effort:** Large (4-6 hours)

---

### Significant Gaps (Should Fix Before Sprint Start)

| # | Gap | Section | Quick Fix |
|---|-----|---------|-----------|
| 1 | Vague success metrics | Goals | Add specific targets |
| 2 | No dependencies section | Dependencies | Map integrations |
| 3 | Missing edge cases | User Stories | Add error scenarios |
| 4 | No risk assessment | Risks | Document key risks |

---

### Anti-Patterns Detected

| Pattern | Instances | Severity | Quick Description |
|---------|-----------|----------|-------------------|
| Edge Case Avoidance | 1 | MEDIUM | Happy paths only documented |

---

## Coverage by Section

| Section | Items | Passed | Coverage | Status |
|---------|-------|--------|----------|--------|
| Problem & Context | 15 | 13 | 87% | GREEN |
| User & Stakeholder | 12 | 10 | 83% | GREEN |
| Goals & Success | 10 | 6 | 60% | YELLOW |
| Requirements | 18 | 14 | 78% | YELLOW |
| User Stories | 14 | 8 | 57% | RED |
| Acceptance Criteria | 12 | 4 | 33% | RED |
| Dependencies | 8 | 0 | 0% | RED |
| Risks & Assumptions | 10 | 5 | 50% | RED |
| Timeline & Scope | 9 | 8 | 89% | GREEN |
| Technical | 8 | 6 | 75% | YELLOW |
| **TOTAL** | **106** | **78** | **74%** | **YELLOW** |

---

## Recommended Next Steps

### Immediate (Before Any Development)

- [ ] Write acceptance criteria for ST-03 through ST-08 (4-6 hours)

### Before Sprint Start

- [ ] Define success metric targets with baseline measurements
- [ ] Create dependencies section for payment and inventory integrations
- [ ] Add 3-4 error-handling user stories

### During Development

- [ ] Document key risks and mitigations
- [ ] Expand edge case coverage as scenarios emerge

---

## Summary

The Checkout Optimization PRD has a solid foundation with clear problem definition
and user understanding. However, the critical gap in acceptance criteria must be
addressed before development—without testable criteria, the team cannot verify
implementation correctness. Additionally, unmapped dependencies with payment and
inventory systems pose integration risk.

Recommend scheduling a 2-hour PRD revision session to address the blocking
acceptance criteria gap, followed by dependency mapping with the platform team.
With these addressed, the PRD will be ready for sprint planning.

---

*Full audit details available in GAP-INVENTORY artifact: GI-2024-03-15-7f8a2*

*Audit performed by: prd-completeness-auditor v2.0*
```

---

## Formatting Guidelines

### Length Targets

| Section | Target Length |
|---------|---------------|
| At a Glance table | 7 rows |
| Readiness Verdict | 5-10 lines |
| Key Findings | 3 strengths, up to 5 issues |
| Coverage table | 10 section rows + total |
| Next Steps | 2-4 items per priority |
| Summary narrative | 1-2 paragraphs |

### Tone

- Factual, not judgmental
- Actionable, not just descriptive
- Concise, not verbose
- Clear recommendations
- Appropriate urgency without alarm

### For Different Audiences

| Audience | Emphasis |
|----------|----------|
| Product Manager | Readiness verdict, next steps, timeline impact |
| Engineering Lead | Critical issues, dependencies, technical gaps |
| Executive | At a Glance, Summary, Readiness verdict |
| QA Lead | Acceptance criteria gaps, testability |
