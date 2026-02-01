# Remediation Plan Output Template

Prioritized action plan for addressing PRD gaps.

---

## Overview

The remediation plan transforms audit findings into actionable work items organized by priority. It provides clear guidance on what to fix, how to fix it, and in what order.

**Use when:** `output_format: remediation_only` or as part of `output_format: full`

---

## Template

```markdown
# PRD Remediation Plan: [PRD Title]

**Generated:** [YYYY-MM-DD]
**Source Audit:** [GAP-INVENTORY artifact_id]
**Total Gaps to Address:** [N]
**Estimated Total Effort:** [X hours/days]

---

## Remediation Summary

| Priority | Gap Count | Total Effort | Target |
|----------|-----------|--------------|--------|
| Immediate | [N] | [X hours] | Before development |
| Short-term | [N] | [X hours] | Before sprint start |
| During Development | [N] | [X hours] | First sprint |
| Optional | [N] | [X hours] | When convenient |
| **TOTAL** | **[N]** | **[X hours]** | |

---

## Priority 1: Immediate (Blocking)

**Target Completion:** Before any development begins
**Impact if Skipped:** Development blocked or fundamentally misdirected

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |
| 2 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |

### Detailed Remediation Actions

---

#### 1. [GAP-XXX]: [Gap Title]

**Category:** [MISSING / INCOMPLETE / INCONSISTENT / AMBIGUOUS / INCORRECT / OUTDATED]
**Severity:** [CRITICAL / HIGH]
**Checklist Reference:** [PC-XX, US-XX, etc.]
**Location:** [PRD section/line or "Create new section"]

**Current State:**
> [Quote from PRD or description of what's missing/wrong]

**Required State:**
> [Description of what the PRD needs to contain]

**Action Steps:**
1. [Specific action step]
2. [Specific action step]
3. [Specific action step]
4. Review with [stakeholder/role]

**Template/Example:**
```markdown
[Provide template content or example of good content]
```

**Effort Estimate:** [Trivial / Small / Medium / Large] ([time range])

**Dependencies:** [What this action depends on, or "None"]

**Verification:** [How to confirm this is fixed]

---

#### 2. [GAP-XXX]: [Gap Title]

[Same structure as above]

---

## Priority 2: Short-Term (Important)

**Target Completion:** Before sprint planning begins
**Impact if Skipped:** Increased risk, likely rework, unclear scope

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |
| 2 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |

### Detailed Remediation Actions

[Same detailed structure as Priority 1]

---

## Priority 3: During Development

**Target Completion:** Address during first development sprint
**Impact if Skipped:** Quality degradation, maintenance burden

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |
| 2 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |

### Grouped Actions

[Can group similar gaps together for efficiency]

#### Documentation Gaps
- GAP-XXX: [Brief action]
- GAP-XXX: [Brief action]

#### Edge Case Gaps
- GAP-XXX: [Brief action]
- GAP-XXX: [Brief action]

---

## Priority 4: Optional Improvements

**Target Completion:** Time permitting
**Impact if Skipped:** Minor polish items; no functional impact

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |
| 2 | GAP-XXX | [Title] | [Type] | [Effort] | [TBD] |

### Quick Fixes
[One-line actions for each]

- GAP-XXX: [Action in one sentence]
- GAP-XXX: [Action in one sentence]

---

## Anti-Pattern Remediation

[If anti-patterns were detected]

### [AP-XX]: [Anti-Pattern Name]

**Instances Found:** [N]

**Remediation Approach:**
[Overall strategy to address this anti-pattern]

**Specific Actions:**
1. [Section/location]: [What to change]
2. [Section/location]: [What to change]

**Prevention:** [How to avoid this pattern in future PRDs]

---

## Effort Summary by Section

| Section | Gaps | Total Effort | Key Actions |
|---------|------|--------------|-------------|
| Problem & Context | [N] | [X hours] | [Key action] |
| User & Stakeholder | [N] | [X hours] | [Key action] |
| Goals & Success | [N] | [X hours] | [Key action] |
| Requirements | [N] | [X hours] | [Key action] |
| User Stories | [N] | [X hours] | [Key action] |
| Acceptance Criteria | [N] | [X hours] | [Key action] |
| Dependencies | [N] | [X hours] | [Key action] |
| Risks & Assumptions | [N] | [X hours] | [Key action] |
| Timeline & Scope | [N] | [X hours] | [Key action] |
| Technical | [N] | [X hours] | [Key action] |

---

## Remediation Tracking

### Master Checklist

| Gap ID | Priority | Section | Effort | Target Date | Owner | Status |
|--------|----------|---------|--------|-------------|-------|--------|
| GAP-001 | P1 | AC | Large | [Date] | [TBD] | [ ] |
| GAP-002 | P1 | GS | Small | [Date] | [TBD] | [ ] |
| GAP-003 | P2 | DP | Medium | [Date] | [TBD] | [ ] |
| GAP-004 | P2 | RA | Medium | [Date] | [TBD] | [ ] |
| GAP-005 | P3 | ST | Small | [Date] | [TBD] | [ ] |
| ... | ... | ... | ... | ... | ... | ... |

### Progress Dashboard

```
Priority 1 (Immediate):  [ ] [ ] [ ] [ ] [ ]  0/[N] complete
Priority 2 (Short-term): [ ] [ ] [ ] [ ] [ ]  0/[N] complete
Priority 3 (During Dev): [ ] [ ] [ ] [ ] [ ]  0/[N] complete
Priority 4 (Optional):   [ ] [ ] [ ] [ ] [ ]  0/[N] complete
─────────────────────────────────────────────
Total:                                        0/[N] complete
```

---

## Timeline Suggestion

### If Starting Today

| Date | Milestone | Items |
|------|-----------|-------|
| Day 1 | Priority 1 (Immediate) | GAP-001, GAP-002 |
| Day 2 | Priority 2 (Part 1) | GAP-003, GAP-004 |
| Day 3 | Priority 2 (Part 2) | GAP-005, GAP-006 |
| Sprint 1 | Priority 3 | GAP-007 through GAP-012 |
| Ongoing | Priority 4 | As time permits |

---

## Sign-Off Checklist

### Before Development Starts

- [ ] All Priority 1 (Immediate) items complete
- [ ] PRD updated with remediation changes
- [ ] Changes reviewed with product owner
- [ ] Development team acknowledges remaining gaps

### Before Sprint Closes

- [ ] All Priority 2 (Short-term) items complete
- [ ] Priority 3 items assigned to sprint backlog
- [ ] Re-audit completed (optional)

### Project Completion

- [ ] All Priority 3 items addressed
- [ ] Outstanding Priority 4 items documented for future
- [ ] Lessons learned captured

---

## Appendix: Remediation Templates

### A. Problem Statement Template
[Template for PC-01 gaps]

### B. User Persona Template
[Template for US-01 gaps]

### C. Success Metrics Template
[Template for GS-02/03 gaps]

### D. Acceptance Criteria Template
[Template for AC-01 gaps]

### E. Dependencies Template
[Template for DP-01 gaps]

### F. Risk Register Template
[Template for RA-01 gaps]

---

**Completed By:** _____________
**Date:** _____________
**Re-Audit Recommended:** [Yes / No]
```

---

## Example Populated Plan

```markdown
# PRD Remediation Plan: Checkout Optimization Feature

**Generated:** 2024-03-15
**Source Audit:** GI-2024-03-15-7f8a2
**Total Gaps to Address:** 16
**Estimated Total Effort:** 14-18 hours

---

## Remediation Summary

| Priority | Gap Count | Total Effort | Target |
|----------|-----------|--------------|--------|
| Immediate | 1 | 4-6 hours | Before development |
| Short-term | 4 | 6-8 hours | Before sprint start |
| During Development | 7 | 3-4 hours | First sprint |
| Optional | 4 | 1-2 hours | When convenient |
| **TOTAL** | **16** | **14-18 hours** | |

---

## Priority 1: Immediate (Blocking)

**Target Completion:** Before any development begins
**Impact if Skipped:** Development blocked - QA cannot write tests

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-001 | Missing acceptance criteria | MISSING | Large | TBD |

### Detailed Remediation Actions

---

#### 1. GAP-001: Missing Acceptance Criteria

**Category:** MISSING
**Severity:** CRITICAL
**Checklist Reference:** AC-01
**Location:** Create "Acceptance Criteria" subsection under each user story

**Current State:**
> User stories ST-03 through ST-08 have no acceptance criteria.
> Example: "As a customer, I want to save my cart so I can return later."
> [No criteria follow]

**Required State:**
> Each user story has 2+ acceptance criteria in Given/When/Then format
> covering happy path and primary error case.

**Action Steps:**
1. Review each user story (ST-03 through ST-08)
2. Identify the happy path scenario
3. Identify the primary error/edge case
4. Write acceptance criteria using template below
5. Review with QA lead before finalizing

**Template/Example:**
```markdown
### ST-03: Save Cart for Later

**Acceptance Criteria:**

AC-03.1: Successful cart save
- Given a customer with items in their cart
- When they click "Save for Later"
- Then cart contents are persisted to their account
- And a confirmation message appears within 2 seconds
- And saved cart appears in "My Saved Carts" list

AC-03.2: Save cart when not logged in
- Given a customer with items in cart who is not logged in
- When they click "Save for Later"
- Then they are prompted to log in or create account
- And cart contents are preserved during authentication
- And cart is saved upon successful authentication

AC-03.3: Save cart with unavailable items
- Given a customer with items where one is now out of stock
- When they click "Save for Later"
- Then cart is saved with all items
- And unavailable items are flagged in the saved cart
```

**Effort Estimate:** Large (4-6 hours for 6 stories × ~45 min each)

**Dependencies:** None

**Verification:** Each of ST-03 through ST-08 has ≥2 acceptance criteria

---

## Priority 2: Short-Term (Important)

**Target Completion:** Before sprint planning begins
**Impact if Skipped:** Increased risk, unclear success criteria, integration surprises

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-002 | Vague success metrics | AMBIGUOUS | Small | TBD |
| 2 | GAP-003 | Missing dependencies section | MISSING | Medium | TBD |
| 3 | GAP-007 | No risk assessment | MISSING | Medium | TBD |
| 4 | GAP-008 | Missing edge case stories | INCOMPLETE | Medium | TBD |

### Detailed Remediation Actions

---

#### 1. GAP-002: Vague Success Metrics

**Category:** AMBIGUOUS
**Severity:** HIGH
**Checklist Reference:** GS-03
**Location:** Goals section, line 23

**Current State:**
> "Success: Checkout completion rate improves significantly."

**Required State:**
> "Checkout completion rate increases from 67% (current baseline as of
> March 2024) to 78% within 30 days of launch, measured via analytics
> dashboard daily."

**Action Steps:**
1. Get current checkout completion rate from analytics
2. Set target improvement (suggest 10-15% relative improvement)
3. Define measurement period and frequency
4. Rewrite success metric with all specifics

**Effort Estimate:** Small (1-2 hours including analytics lookup)

---

#### 2. GAP-003: Missing Dependencies Section

**Category:** MISSING
**Severity:** HIGH
**Checklist Reference:** DP-01
**Location:** Create new "Dependencies" section after Requirements

**Action Steps:**
1. Identify all external systems (payment service, inventory system)
2. Contact integration owners for API versions and timelines
3. Document each dependency with owner, status, ETA
4. Add mitigation plans for blocking dependencies

**Template:**
```markdown
## Dependencies

### External System Dependencies

| System | Type | Status | Owner | ETA | Risk if Delayed |
|--------|------|--------|-------|-----|-----------------|
| Payment Service v2.3 | API | Ready | Platform Team | N/A | None |
| Inventory System | Data | In Progress | Commerce Team | Mar 30 | HIGH - blocks cart validation |

### Team Dependencies

| Team | Dependency | Status | Contact |
|------|------------|--------|---------|
| Platform | Payment API access | Ready | @john.smith |
| Commerce | Inventory webhook | In Progress | @jane.doe |

### Mitigation Plans

If Inventory webhook delayed:
- Fallback: Poll inventory API (higher latency, acceptable for MVP)
- Escalation: Product Director
```

**Effort Estimate:** Medium (2-3 hours including stakeholder outreach)

---

## Priority 3: During Development

**Target Completion:** Address during first development sprint
**Impact if Skipped:** Quality degradation, edge cases discovered late

| # | Gap ID | Gap Title | Category | Effort | Owner |
|---|--------|-----------|----------|--------|-------|
| 1 | GAP-009 | Incomplete persona details | INCOMPLETE | Small | TBD |
| 2 | GAP-010 | Missing error messages spec | MISSING | Small | TBD |
| 3 | GAP-011 | Vague performance requirements | AMBIGUOUS | Small | TBD |

### Grouped Actions

#### User Understanding Gaps
- GAP-009: Add "pain points" and "current workarounds" to primary persona

#### Specification Gaps
- GAP-010: Add error message copy for validation failures
- GAP-011: Specify response time targets: page load <2s, API calls <500ms

---

## Priority 4: Optional Improvements

| # | Gap ID | Gap Title | Category | Effort |
|---|--------|-----------|----------|--------|
| 1 | GAP-013 | Outdated stakeholder contact | OUTDATED | Trivial |
| 2 | GAP-014 | Minor formatting inconsistency | INCOMPLETE | Trivial |
| 3 | GAP-015 | Missing optional accessibility notes | INCOMPLETE | Small |
| 4 | GAP-016 | No admin user stories | MISSING | Small |

### Quick Fixes

- GAP-013: Update Sarah Johnson → Michael Chen as design lead
- GAP-014: Standardize heading levels in Requirements section
- GAP-015: Add note about WCAG 2.1 AA compliance target
- GAP-016: Add admin story for order management (if time permits)

---

## Anti-Pattern Remediation

### AP-06: Edge Case Avoidance

**Instances Found:** 1 (User Stories section)

**Remediation Approach:**
Add 3-4 user stories covering error and edge cases

**Specific Actions:**
1. User Stories section: Add "Payment failure handling" story
2. User Stories section: Add "Inventory unavailable" story
3. User Stories section: Add "Session timeout during checkout" story

**Prevention:** Future PRDs should include error-path stories template

---

## Remediation Tracking

### Master Checklist

| Gap ID | Priority | Section | Effort | Target Date | Owner | Status |
|--------|----------|---------|--------|-------------|-------|--------|
| GAP-001 | P1 | AC | Large | Mar 17 | TBD | [ ] |
| GAP-002 | P2 | GS | Small | Mar 18 | TBD | [ ] |
| GAP-003 | P2 | DP | Medium | Mar 18 | TBD | [ ] |
| GAP-007 | P2 | RA | Medium | Mar 19 | TBD | [ ] |
| GAP-008 | P2 | ST | Medium | Mar 19 | TBD | [ ] |
| GAP-009 | P3 | US | Small | Sprint 1 | TBD | [ ] |
| GAP-010 | P3 | RQ | Small | Sprint 1 | TBD | [ ] |
| GAP-011 | P3 | RQ | Small | Sprint 1 | TBD | [ ] |

---

## Sign-Off Checklist

### Before Development Starts

- [ ] GAP-001 (Acceptance criteria) complete
- [ ] PRD updated with AC changes
- [ ] Changes reviewed with product owner
- [ ] QA lead confirms criteria are testable

### Before Sprint Closes

- [ ] GAP-002, 003, 007, 008 complete
- [ ] Priority 3 items assigned to sprint backlog
- [ ] Dependencies confirmed with platform team

---

**Completed By:** _____________
**Date:** _____________
**Re-Audit Recommended:** Yes (after Priority 1-2 remediation)
```

---

## Formatting Guidelines

### Priority Naming

| Priority | Also Called | Color | Urgency |
|----------|-------------|-------|---------|
| Priority 1 | Immediate / Blocking | RED | Must do now |
| Priority 2 | Short-term / Important | ORANGE | Do before sprint |
| Priority 3 | During Development | YELLOW | Do during sprint |
| Priority 4 | Optional / Nice-to-have | GREEN | When convenient |

### Effort Estimation

| Level | Time Range | Examples |
|-------|------------|----------|
| Trivial | < 30 min | Fix typo, update contact |
| Small | 30 min - 2 hours | Clarify metric, add detail |
| Medium | 2 - 8 hours | Write section, map dependencies |
| Large | 1+ days | Major section, extensive research |

### Action Step Guidelines

- Start with verb (Review, Write, Contact, Document)
- Be specific enough to act on
- Include who to involve if needed
- Note verification criteria
