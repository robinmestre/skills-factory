# Technical Debt Remediation Roadmap Template

This template defines the prioritized action plan output for addressing technical debt and gaps identified by the Architecture Documentation Auditor.

---

## Roadmap Structure

The Debt Remediation Roadmap consists of these sections:

1. **Executive Summary** - High-level debt overview and investment case
2. **Debt Inventory** - All debt items with metadata
3. **Prioritization Matrix** - Effort × Impact quadrant analysis
4. **Remediation Phases** - Sequenced action plan
5. **Quick Wins** - Low-effort, high-impact items
6. **Strategic Investments** - High-effort, high-value initiatives
7. **Progress Tracking** - Metrics and milestones
8. **Risk Mitigation** - Addressing blockers and dependencies

---

## Complete Roadmap Template

```markdown
# Technical Debt Remediation Roadmap

**Source Document:** [Document Title]
**Audit Date:** [YYYY-MM-DD]
**Roadmap Created:** [YYYY-MM-DD]
**Roadmap ID:** DRR-[YYYY-MM-DD]-[5-char-hash]
**Related Artifacts:**
- GAP-INVENTORY: GI-ARCH-[date]-[hash]
- Architecture Health Report: AHR-[date]-[hash]

---

## Executive Summary

### Current State

| Metric | Value | Target |
|--------|-------|--------|
| Architecture Health Score | [N]/100 | 80+/100 |
| Total Debt Items | [N] | 0 |
| Critical/High Severity | [N] | 0 |
| Estimated Remediation Effort | [N] person-days | - |
| Blocking Issues | [N] | 0 |

### Investment Case

**Problem Statement:**
[1-2 paragraphs describing the current technical debt situation and its impact on the organization]

**Business Impact of Inaction:**
- [Impact 1: e.g., "Development velocity reduced by X%"]
- [Impact 2: e.g., "Security vulnerabilities remain unaddressed"]
- [Impact 3: e.g., "Compliance certification at risk"]

**Expected ROI from Remediation:**
- [Benefit 1: e.g., "Reduced incident response time by Y%"]
- [Benefit 2: e.g., "Improved developer onboarding by Z days"]
- [Benefit 3: e.g., "Compliance readiness achieved"]

### Recommended Approach

**Phase 1 (Weeks 1-2):** Address critical blockers and quick wins
- [N] items | [N] person-days | Target: Remove blocking issues

**Phase 2 (Weeks 3-6):** Core remediation
- [N] items | [N] person-days | Target: Achieve ADEQUATE status (60+)

**Phase 3 (Weeks 7-12):** Strategic improvements
- [N] items | [N] person-days | Target: Achieve HEALTHY status (80+)

---

## Debt Inventory

### Summary by Category

| Category | Count | Critical | High | Medium | Low | Total Effort |
|----------|-------|----------|------|--------|-----|--------------|
| Architectural | [N] | [N] | [N] | [N] | [N] | [N] days |
| Documentation | [N] | [N] | [N] | [N] | [N] | [N] days |
| Infrastructure | [N] | [N] | [N] | [N] | [N] | [N] days |
| Security | [N] | [N] | [N] | [N] | [N] | [N] days |
| API | [N] | [N] | [N] | [N] | [N] | [N] days |
| **Total** | **[N]** | **[N]** | **[N]** | **[N]** | **[N]** | **[N] days** |

### Complete Debt Item List

| ID | Category | Name | Severity | Effort | Impact | Priority Score | Phase |
|----|----------|------|----------|--------|--------|----------------|-------|
| TD-A01 | Architectural | Shared database | HIGH | large | high | 8.5 | 2 |
| TD-A02 | Architectural | Circular dependencies | CRITICAL | medium | high | 9.2 | 1 |
| TD-D01 | Documentation | Stale diagrams | MEDIUM | small | medium | 5.0 | 2 |
| TD-S01 | Security | Missing encryption spec | CRITICAL | medium | high | 9.5 | 1 |
| GAP-001 | Gap | No DR strategy | CRITICAL | large | high | 9.0 | 1 |
| GAP-002 | Gap | Missing API versioning | HIGH | medium | medium | 7.0 | 2 |
| AA-02 | Anti-Pattern | Distributed Monolith | CRITICAL | large | high | 9.3 | 3 |

### Effort Estimation Guide

| Effort Level | Person-Days | Description |
|--------------|-------------|-------------|
| trivial | 0.25-0.5 | Quick documentation update, single-line fix |
| small | 1-2 | Section addition, diagram update |
| medium | 3-5 | New section creation, multi-diagram update |
| large | 5-10 | Major documentation effort, architectural rework |
| x-large | 10+ | Fundamental restructuring required |

---

## Prioritization Matrix

### Effort × Impact Quadrant

```
                    HIGH IMPACT
                         │
    ┌────────────────────┼────────────────────┐
    │                    │                    │
    │   STRATEGIC        │    QUICK WINS      │
    │   INVESTMENTS      │    ★ DO FIRST ★    │
    │                    │                    │
    │   - TD-A01         │    - TD-D03        │
    │   - AA-02          │    - GAP-015       │
    │   - GAP-001        │    - TD-D01        │
    │                    │                    │
────┼────────────────────┼────────────────────┼────
    │                    │                    │
    │   CONSIDER         │    FILL-INS        │
    │   LATER            │    (Low Priority)  │
    │                    │                    │
    │   - TD-D05         │    - TD-D06        │
    │   - GAP-020        │    - GAP-025       │
    │                    │                    │
    └────────────────────┼────────────────────┘
                         │
                    LOW IMPACT
         HIGH EFFORT                LOW EFFORT
```

### Priority Score Calculation

```python
def calculate_priority_score(severity, effort, impact, blocking=False):
    """
    Calculate priority score for remediation sequencing.

    Severity weights: CRITICAL=4, HIGH=3, MEDIUM=2, LOW=1
    Effort weights: trivial=5, small=4, medium=3, large=2, x-large=1
    Impact weights: high=4, medium=3, low=2

    Formula: (severity * 0.4) + (effort_inverse * 0.3) + (impact * 0.3) + blocking_bonus

    Returns: float (1-10 scale)
    """
    severity_map = {'CRITICAL': 4, 'HIGH': 3, 'MEDIUM': 2, 'LOW': 1}
    effort_map = {'trivial': 5, 'small': 4, 'medium': 3, 'large': 2, 'x-large': 1}
    impact_map = {'high': 4, 'medium': 3, 'low': 2}

    base_score = (
        (severity_map[severity] * 0.4) +
        (effort_map[effort] * 0.3) +
        (impact_map[impact] * 0.3)
    )

    blocking_bonus = 2 if blocking else 0

    return min(10, base_score * 2.5 + blocking_bonus)
```

### Items Ranked by Priority Score

| Rank | ID | Name | Priority Score | Rationale |
|------|----|----- |----------------|-----------|
| 1 | TD-S01 | Missing encryption spec | 9.5 | Critical security gap, blocking compliance |
| 2 | AA-02 | Distributed Monolith | 9.3 | Critical anti-pattern, high impact |
| 3 | TD-A02 | Circular dependencies | 9.2 | Critical architectural issue |
| 4 | GAP-001 | No DR strategy | 9.0 | Critical gap, blocks production readiness |
| 5 | TD-A01 | Shared database | 8.5 | High severity, large impact |
| ... | ... | ... | ... | ... |

---

## Remediation Phases

### Phase 1: Critical Blockers (Weeks 1-2)

**Objective:** Remove all blocking issues and critical security gaps

**Success Criteria:**
- [ ] All critical severity items addressed
- [ ] No blocking issues remain
- [ ] Security compliance baseline met

**Items:**

| Seq | ID | Name | Owner | Effort | Dependencies | Status |
|-----|----|----- |-------|--------|--------------|--------|
| 1.1 | TD-S01 | Document encryption approach | Security Arch | medium | None | ⬜ Not Started |
| 1.2 | TD-A02 | Resolve circular dependencies | Lead Architect | medium | None | ⬜ Not Started |
| 1.3 | GAP-001 | Create DR strategy document | Ops Lead | large | 1.1 | ⬜ Not Started |
| 1.4 | GAP-007 | Define authentication flow | Security Arch | small | 1.1 | ⬜ Not Started |

**Estimated Effort:** [N] person-days
**Risk Level:** High (blocking issues)

---

### Phase 2: Core Remediation (Weeks 3-6)

**Objective:** Address high-severity items and achieve ADEQUATE health status (60+)

**Success Criteria:**
- [ ] All high severity items addressed
- [ ] Architecture Health Score ≥ 60
- [ ] All viewpoints have at least 50% coverage

**Items:**

| Seq | ID | Name | Owner | Effort | Dependencies | Status |
|-----|----|----- |-------|--------|--------------|--------|
| 2.1 | TD-A01 | Define data ownership | Lead Architect | large | Phase 1 | ⬜ Not Started |
| 2.2 | GAP-002 | Document API versioning | API Lead | medium | None | ⬜ Not Started |
| 2.3 | TD-D01 | Update stale diagrams | Tech Writer | small | 2.1, 2.2 | ⬜ Not Started |
| 2.4 | GAP-010 | Add deployment diagrams | DevOps | medium | None | ⬜ Not Started |
| 2.5 | TD-I01 | Document monitoring strategy | SRE Lead | medium | 2.4 | ⬜ Not Started |

**Estimated Effort:** [N] person-days
**Risk Level:** Medium

---

### Phase 3: Strategic Improvements (Weeks 7-12)

**Objective:** Address medium-severity items and achieve HEALTHY status (80+)

**Success Criteria:**
- [ ] All medium severity items addressed
- [ ] Architecture Health Score ≥ 80
- [ ] All viewpoints have at least 70% coverage
- [ ] No anti-patterns remain unaddressed

**Items:**

| Seq | ID | Name | Owner | Effort | Dependencies | Status |
|-----|----|----- |-------|--------|--------------|--------|
| 3.1 | AA-02 | Refactor to true microservices | Lead Architect | x-large | Phase 2 | ⬜ Not Started |
| 3.2 | TD-D02 | Create component diagrams | Tech Writer | medium | 3.1 | ⬜ Not Started |
| 3.3 | GAP-015 | Document caching strategy | Senior Dev | small | 3.1 | ⬜ Not Started |
| 3.4 | TD-P01 | Standardize API error format | API Lead | medium | None | ⬜ Not Started |

**Estimated Effort:** [N] person-days
**Risk Level:** Low (no blocking dependencies)

---

### Phase 4: Continuous Improvement (Ongoing)

**Objective:** Address remaining low-severity items and maintain health score

**Items for Backlog:**

| ID | Name | Severity | Effort | Notes |
|----|------|----------|--------|-------|
| TD-D05 | Add code examples | LOW | small | Nice to have |
| GAP-025 | Document edge cases | LOW | trivial | When time permits |

---

## Quick Wins

Items that can be completed quickly with immediate benefit.

### Criteria
- Effort: trivial or small (≤2 person-days)
- Impact: medium or high
- Dependencies: none or minimal

### Quick Win List

| # | ID | Name | Effort | Impact | Owner | Target Date |
|---|----|----- |--------|--------|-------|-------------|
| 1 | TD-D03 | Add missing decision rationale | small | high | [Owner] | Week 1 |
| 2 | GAP-015 | Document existing caching | trivial | medium | [Owner] | Week 1 |
| 3 | TD-D01 | Update context diagram | small | medium | [Owner] | Week 1 |
| 4 | GAP-018 | Add API examples | trivial | medium | [Owner] | Week 1 |
| 5 | TD-D04 | Fix terminology inconsistencies | trivial | low | [Owner] | Week 2 |

**Total Quick Win Effort:** [N] person-days
**Expected Impact:** +[N] points to health score

---

## Strategic Investments

High-effort items that provide significant long-term value.

### Criteria
- Effort: large or x-large (≥5 person-days)
- Impact: high
- Strategic value: enables future capabilities or removes systemic issues

### Strategic Investment List

| # | ID | Name | Effort | Impact | Business Value | Recommended Timing |
|---|----|----- |--------|--------|----------------|-------------------|
| 1 | AA-02 | Resolve Distributed Monolith | x-large | high | Enables independent deployment | Q2 |
| 2 | TD-A01 | Implement data ownership | large | high | Enables scaling, reduces coupling | Q1 |
| 3 | GAP-001 | Create comprehensive DR plan | large | high | Business continuity, compliance | Q1 |

### Investment Analysis

#### Strategic Investment 1: Resolve Distributed Monolith (AA-02)

**Current State:**
[Description of the current problematic state]

**Target State:**
[Description of the desired future state]

**Effort Breakdown:**
| Activity | Effort | Owner |
|----------|--------|-------|
| Architecture redesign | 3 days | Lead Architect |
| Documentation update | 2 days | Tech Writer |
| Team review and alignment | 2 days | Team |
| Implementation planning | 3 days | Tech Leads |
| **Total** | **10 days** | |

**Benefits:**
- Independent service deployment
- Reduced blast radius for failures
- Improved team autonomy
- Better scalability

**Risks:**
- Requires significant refactoring
- May impact delivery timelines
- Needs cross-team coordination

**Recommendation:** Schedule for [Quarter] with dedicated sprint

---

## Progress Tracking

### Milestone Schedule

| Milestone | Target Date | Success Criteria | Status |
|-----------|-------------|------------------|--------|
| M1: Blockers Resolved | [Date] | 0 critical items, 0 blocking issues | ⬜ |
| M2: ADEQUATE Status | [Date] | Health Score ≥ 60 | ⬜ |
| M3: Security Baseline | [Date] | V7 score ≥ 70 | ⬜ |
| M4: Operations Ready | [Date] | V8 score ≥ 70 | ⬜ |
| M5: HEALTHY Status | [Date] | Health Score ≥ 80 | ⬜ |

### Progress Metrics

**Track Weekly:**

| Metric | Baseline | Week 1 | Week 2 | Week 3 | Week 4 | Target |
|--------|----------|--------|--------|--------|--------|--------|
| Health Score | [N] | - | - | - | - | 80+ |
| Open Critical | [N] | - | - | - | - | 0 |
| Open High | [N] | - | - | - | - | 0 |
| Items Completed | 0 | - | - | - | - | [Total] |
| Person-Days Spent | 0 | - | - | - | - | [Budget] |

### Burndown Chart Data

```yaml
burndown:
  total_items: [N]
  by_week:
    - week: 0
      remaining: [N]
      completed: 0
    - week: 1
      remaining: [N-x]
      completed: [x]
    - week: 2
      remaining: [N-y]
      completed: [y]
    # Continue for each planned week
```

### Health Score Projection

```
Score
100 ┤                                         ╭── Target
 90 ┤                                    ╭────╯
 80 ┤                              ╭─────╯  ← HEALTHY
 70 ┤                        ╭─────╯
 60 ┤                  ╭─────╯              ← ADEQUATE
 50 ┤            ╭─────╯
 40 ┤      ╭─────╯
 30 ┼──────╯ Current
    └──────────────────────────────────────────────
      W0   W2   W4   W6   W8   W10  W12
```

---

## Risk Mitigation

### Identified Risks

| Risk | Likelihood | Impact | Mitigation Strategy |
|------|------------|--------|---------------------|
| Resource unavailability | Medium | High | Identify backup owners for each item |
| Scope creep | High | Medium | Strict change control, defer non-critical |
| Technical complexity | Medium | High | Spike high-risk items early, get expert review |
| Dependency delays | Medium | Medium | Parallelize where possible, identify critical path |
| Stakeholder alignment | Low | High | Regular progress reviews, early escalation |

### Dependency Management

**Critical Path Items:**
```
TD-S01 (Encryption) ──► GAP-001 (DR Strategy) ──► M3 (Security Baseline)
                   └──► GAP-007 (Auth Flow)

TD-A01 (Data Ownership) ──► 3.1 (Microservices) ──► AA-02 Resolution
```

**Parallelizable Streams:**
- Stream A: Security (TD-S01, GAP-007, V7 items)
- Stream B: Operations (TD-I01, GAP-010, V8 items)
- Stream C: Documentation (TD-D01, TD-D02, diagrams)

### Escalation Triggers

| Trigger | Escalation Path |
|---------|----------------|
| Critical item blocked >3 days | Engineering Manager |
| Phase milestone missed | Architecture Review Board |
| Resource conflict | Program Manager |
| Scope change requested | Product Owner |

---

## Appendix: Item Details

### Detailed Remediation Guidance

#### TD-A01: Shared Database Between Services

**Current State:**
Multiple services (Order, User, Payment) connect directly to a shared PostgreSQL database, creating tight coupling and preventing independent scaling.

**Evidence:**
> "Container diagram shows Order, User, and Payment services all connecting to PostgreSQL"

**Target State:**
Each service owns its data with clear boundaries. Services communicate via well-defined APIs or events.

**Remediation Steps:**
1. [ ] Document current data access patterns per service
2. [ ] Define data ownership boundaries
3. [ ] Identify shared data requiring synchronization
4. [ ] Design event-driven data flow
5. [ ] Update container diagram to show separated data stores
6. [ ] Document migration path (for implementation phase)

**Effort:** large (5-10 person-days)
**Owner:** [Lead Architect]
**Dependencies:** None
**Risk:** Medium - requires careful coordination

---

#### GAP-001: No Disaster Recovery Strategy

**Current State:**
Deployment section covers the deployment process but has no DR subsection. No RTO/RPO targets found anywhere in document.

**Evidence:**
> Deployment section reviewed; no references to "disaster recovery", "DR", "RTO", "RPO", "backup", or "failover" found.

**Target State:**
Comprehensive DR section documenting backup strategy, failover process, and recovery objectives.

**Remediation Steps:**
1. [ ] Define RTO/RPO targets with stakeholders
2. [ ] Document backup strategy (what, where, frequency)
3. [ ] Document failover process
4. [ ] Document recovery procedures
5. [ ] Identify DR testing approach
6. [ ] Add DR section to deployment documentation

**Effort:** large (5-10 person-days)
**Owner:** [Ops Lead]
**Dependencies:** TD-S01 (encryption approach affects backup security)
**Risk:** High - requires business input for RTO/RPO

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | architecture-doc-auditor | Initial roadmap generation |
| | | | |

---

## References

- [GAP-INVENTORY](gap-inventory-output.md) - Detailed gap data
- [Architecture Health Report](architecture-health-report.md) - Current health status
- [Technical Debt Indicators](../references/technical-debt-indicators.md) - Debt catalog
- [Anti-Patterns Catalog](../references/anti-patterns-catalog.md) - Anti-pattern definitions
```

---

## Generation Guidelines

### When to Generate This Roadmap

Generate a Debt Remediation Roadmap when:
1. GAP-INVENTORY contains ≥5 gaps or debt items
2. Architecture Health Score is AT_RISK (<60) or CRITICAL (<40)
3. Any CRITICAL severity items exist
4. User explicitly requests remediation planning
5. Governance requires a remediation plan

### Roadmap Customization

**By Governance Context:**

| Context | Focus | Typical Phases |
|---------|-------|----------------|
| Enterprise | Compliance, standards alignment | 4 phases, formal milestones |
| Team | Practical improvement | 2-3 phases, informal tracking |
| Project | Delivery enablement | 1-2 phases, sprint-aligned |

**By Urgency:**

| Urgency | Approach | Timeline |
|---------|----------|----------|
| Critical | Blockers first, parallel streams | 2-4 weeks |
| Standard | Phased approach | 8-12 weeks |
| Strategic | Long-term improvement | 3-6 months |

### Effort Estimation Heuristics

| Item Type | Typical Effort |
|-----------|---------------|
| Missing section (new content) | medium to large |
| Incomplete section (additions) | small to medium |
| Inconsistent content (fixes) | trivial to small |
| Ambiguous content (clarification) | trivial to small |
| Outdated content (updates) | small to medium |
| Anti-pattern resolution (doc only) | medium |
| Anti-pattern resolution (with code) | large to x-large |
| Technical debt indicator | varies by category |

### Owner Assignment Guidelines

| Category | Typical Owner |
|----------|---------------|
| Architectural items | Lead Architect, Solution Architect |
| Security items | Security Architect, Security Lead |
| Operations items | SRE Lead, DevOps Lead |
| Documentation items | Tech Writer, assigned engineer |
| API items | API Lead, Backend Lead |
| Data items | Data Architect, Database Lead |

---

## Validation Checklist

Before finalizing the roadmap, verify:

- [ ] All items from GAP-INVENTORY are included
- [ ] All items from anti-patterns are included
- [ ] All items from technical debt are included
- [ ] Priority scores are calculated correctly
- [ ] Phase assignments align with dependencies
- [ ] Effort estimates are realistic
- [ ] Critical items are in Phase 1
- [ ] Quick wins are identified correctly
- [ ] Milestones have measurable success criteria
- [ ] Dependencies are mapped correctly
- [ ] Risk mitigations are actionable
- [ ] Total effort aligns with available resources
