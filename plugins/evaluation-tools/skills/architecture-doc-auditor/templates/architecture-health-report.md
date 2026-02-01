# Architecture Health Report Template

This template defines the executive dashboard output format for the Architecture Documentation Auditor, designed for stakeholder consumption and governance reporting.

---

## Report Structure

The Architecture Health Report consists of these sections:

1. **Executive Summary** - One-page health overview
2. **Viewpoint Coverage** - Spider chart data for viewpoint completeness
3. **Quality Attribute Assessment** - Radar chart data for quality coverage
4. **Risk Heat Map** - Severity × Likelihood matrix
5. **Technical Debt Summary** - Debt indicators with remediation priorities
6. **Trend Indicators** - Progress tracking (if historical data available)
7. **Stakeholder Views** - Role-specific summaries
8. **Recommendations** - Prioritized action items

---

## Complete Report Template

```markdown
# Architecture Health Report

**Document:** [Document Title]
**Audit Date:** [YYYY-MM-DD]
**Auditor:** architecture-doc-auditor v2.0
**Report ID:** AHR-[YYYY-MM-DD]-[5-char-hash]

---

## Executive Summary

### Overall Health Score

| Metric | Value | Status |
|--------|-------|--------|
| **Overall Score** | [0-100]/100 | [HEALTHY/ADEQUATE/AT_RISK/CRITICAL] |
| **Viewpoints Assessed** | [N]/14 | [Coverage %] |
| **Checklist Items Passed** | [N]/[Total] | [Pass %] |
| **Critical Gaps** | [N] | [Trend ↑/↓/→] |
| **Anti-Patterns Detected** | [N] | [Severity Distribution] |
| **Technical Debt Indicators** | [N] | [Remediation Cost] |

### Health Status Indicator

```
[████████████████████░░░░░░░░░░] 67/100 - ADEQUATE
```

### Key Findings (Top 5)

1. **[CRITICAL]** [Brief description of most critical gap]
2. **[CRITICAL]** [Second critical gap]
3. **[HIGH]** [High severity gap]
4. **[HIGH]** [High severity gap]
5. **[MEDIUM]** [Medium severity gap]

### Blocking Issues

These issues MUST be resolved before architecture approval:

| # | Issue | Gap Ref | Remediation Effort |
|---|-------|---------|-------------------|
| 1 | [Issue description] | GAP-001 | [small/medium/large] |
| 2 | [Issue description] | GAP-002 | [small/medium/large] |

---

## Viewpoint Coverage Analysis

### Coverage Scores by Viewpoint

| Viewpoint | Score | Status | Items Passed | Critical Gaps |
|-----------|-------|--------|--------------|---------------|
| V1: Context & Scope | [0-100] | [Status] | [N]/15 | [N] |
| V2: Container Architecture | [0-100] | [Status] | [N]/25 | [N] |
| V3: Component Design | [0-100] | [Status] | [N]/18 | [N] |
| V4: Deployment Topology | [0-100] | [Status] | [N]/22 | [N] |
| V5: Data Architecture | [0-100] | [Status] | [N]/18 | [N] |
| V6: Integration & APIs | [0-100] | [Status] | [N]/15 | [N] |
| V7: Security Architecture | [0-100] | [Status] | [N]/25 | [N] |
| V8: Operational Concerns | [0-100] | [Status] | [N]/18 | [N] |
| V9: Cross-Cutting Concerns | [0-100] | [Status] | [N]/12 | [N] |
| V10: Decision Records | [0-100] | [Status] | [N]/20 | [N] |

### Conditional Viewpoints (If Assessed)

| Viewpoint | Applicable | Score | Status |
|-----------|------------|-------|--------|
| V11: Multi-tenancy | [Yes/No] | [0-100 or N/A] | [Status] |
| V12: Event Architecture | [Yes/No] | [0-100 or N/A] | [Status] |
| V13: Migration Path | [Yes/No] | [0-100 or N/A] | [Status] |
| V14: Compliance Matrix | [Yes/No] | [0-100 or N/A] | [Status] |

### Spider Chart Data (Viewpoint Coverage)

```yaml
spider_chart:
  labels:
    - "Context & Scope"
    - "Container"
    - "Component"
    - "Deployment"
    - "Data"
    - "Integration"
    - "Security"
    - "Operations"
    - "Cross-Cutting"
    - "Decisions"
  values: [85, 72, 68, 45, 78, 82, 38, 55, 70, 60]
  max_value: 100
  thresholds:
    healthy: 80
    adequate: 60
    at_risk: 40
```

### Viewpoint Gap Distribution

```
V1: Context     ████████████████████░░░░░ 85%  (2 gaps)
V2: Container   ██████████████████░░░░░░░ 72%  (7 gaps)
V3: Component   █████████████████░░░░░░░░ 68%  (6 gaps)
V4: Deployment  ███████████░░░░░░░░░░░░░░ 45%  (12 gaps) ⚠️
V5: Data        ███████████████████░░░░░░ 78%  (4 gaps)
V6: Integration ████████████████████░░░░░ 82%  (3 gaps)
V7: Security    █████████░░░░░░░░░░░░░░░░ 38%  (16 gaps) 🔴
V8: Operations  █████████████░░░░░░░░░░░░ 55%  (8 gaps) ⚠️
V9: Cross-Cut   █████████████████░░░░░░░░ 70%  (4 gaps)
V10: Decisions  ███████████████░░░░░░░░░░ 60%  (8 gaps)
```

---

## Quality Attribute Assessment

### Coverage by Quality Attribute

| Quality Attribute | Coverage Level | Primary Viewpoints | Gap Count |
|------------------|----------------|-------------------|-----------|
| Performance | [EXPLICIT/IMPLICIT/MISSING] | V4, V5 | [N] |
| Security | [EXPLICIT/IMPLICIT/MISSING] | V7, V6 | [N] |
| Reliability | [EXPLICIT/IMPLICIT/MISSING] | V8, V4 | [N] |
| Scalability | [EXPLICIT/IMPLICIT/MISSING] | V4, V2 | [N] |
| Maintainability | [EXPLICIT/IMPLICIT/MISSING] | V3, V10 | [N] |
| Interoperability | [EXPLICIT/IMPLICIT/MISSING] | V6, V1 | [N] |
| Portability | [EXPLICIT/IMPLICIT/MISSING] | V4, V2 | [N] |
| Usability | [EXPLICIT/IMPLICIT/MISSING] | V6, V10 | [N] |

### Radar Chart Data (Quality Attributes)

```yaml
radar_chart:
  labels:
    - "Performance"
    - "Security"
    - "Reliability"
    - "Scalability"
    - "Maintainability"
    - "Interoperability"
    - "Portability"
    - "Usability"
  values: [75, 35, 50, 60, 70, 80, 65, 55]
  coverage_levels:
    explicit: 3    # Full score
    implicit: 2    # Partial score
    missing: 0     # No score
```

### Quality Attribute Details

#### Performance (Score: [N]/100)

| Aspect | Status | Evidence |
|--------|--------|----------|
| Latency targets defined | [✓/✗] | [Quote or N/A] |
| Throughput requirements | [✓/✗] | [Quote or N/A] |
| Resource limits | [✓/✗] | [Quote or N/A] |
| Caching strategy | [✓/✗] | [Quote or N/A] |

#### Security (Score: [N]/100)

| Aspect | Status | Evidence |
|--------|--------|----------|
| Authentication mechanism | [✓/✗] | [Quote or N/A] |
| Authorization model | [✓/✗] | [Quote or N/A] |
| Encryption at rest | [✓/✗] | [Quote or N/A] |
| Encryption in transit | [✓/✗] | [Quote or N/A] |
| Audit logging | [✓/✗] | [Quote or N/A] |
| Secrets management | [✓/✗] | [Quote or N/A] |

#### Reliability (Score: [N]/100)

| Aspect | Status | Evidence |
|--------|--------|----------|
| Availability target | [✓/✗] | [Quote or N/A] |
| SLOs defined | [✓/✗] | [Quote or N/A] |
| DR plan exists | [✓/✗] | [Quote or N/A] |
| RTO/RPO defined | [✓/✗] | [Quote or N/A] |
| Failover mechanism | [✓/✗] | [Quote or N/A] |

---

## Risk Heat Map

### Severity × Likelihood Matrix

|              | Low Likelihood | Medium Likelihood | High Likelihood |
|--------------|----------------|-------------------|-----------------|
| **Critical** | [N] gaps       | [N] gaps          | [N] gaps 🔴     |
| **High**     | [N] gaps       | [N] gaps          | [N] gaps        |
| **Medium**   | [N] gaps       | [N] gaps          | [N] gaps        |
| **Low**      | [N] gaps       | [N] gaps          | [N] gaps        |

### Risk Quadrant Summary

```
                    HIGH LIKELIHOOD
                          │
         Mitigate         │        Immediate
         Urgently         │         Action
                          │
    ──────────────────────┼──────────────────────
                          │
          Monitor         │        Plan for
                          │       Remediation
                          │
                    LOW LIKELIHOOD
         LOW IMPACT                  HIGH IMPACT
```

### Top Risks by Composite Score

| Rank | Gap ID | Description | Impact | Likelihood | Detectability | Composite |
|------|--------|-------------|--------|------------|---------------|-----------|
| 1 | GAP-007 | [Description] | 4 | 4 | 2 | 3.6 |
| 2 | GAP-012 | [Description] | 4 | 3 | 3 | 3.5 |
| 3 | GAP-003 | [Description] | 3 | 4 | 2 | 3.2 |
| 4 | GAP-015 | [Description] | 4 | 3 | 2 | 3.3 |
| 5 | GAP-001 | [Description] | 3 | 3 | 3 | 3.0 |

---

## Technical Debt Summary

### Debt Indicators by Category

| Category | Count | High Severity | Remediation Cost |
|----------|-------|---------------|------------------|
| Architectural | [N] | [N] | [Estimated effort] |
| Documentation | [N] | [N] | [Estimated effort] |
| Infrastructure | [N] | [N] | [Estimated effort] |
| Security | [N] | [N] | [Estimated effort] |
| API | [N] | [N] | [Estimated effort] |
| **Total** | **[N]** | **[N]** | **[Total effort]** |

### Debt Distribution Chart Data

```yaml
debt_chart:
  type: "pie"
  labels:
    - "Architectural"
    - "Documentation"
    - "Infrastructure"
    - "Security"
    - "API"
  values: [4, 5, 2, 1, 2]
  colors:
    - "#FF6B6B"  # Red
    - "#4ECDC4"  # Teal
    - "#45B7D1"  # Blue
    - "#96CEB4"  # Green
    - "#FFEAA7"  # Yellow
```

### High-Severity Debt Items

| ID | Category | Indicator | Severity | Location | Remediation Cost |
|----|----------|-----------|----------|----------|------------------|
| TD-A01 | Architectural | Shared database | HIGH | Container Diagram | large |
| TD-S02 | Security | Missing encryption spec | CRITICAL | Security Section | medium |
| TD-I03 | Infrastructure | No DR strategy | CRITICAL | Deployment Section | large |

---

## Anti-Patterns Detected

### Summary by Category

| Category | Count | Critical | High | Medium |
|----------|-------|----------|------|--------|
| Structural | [N] | [N] | [N] | [N] |
| Documentation | [N] | [N] | [N] | [N] |
| Operational | [N] | [N] | [N] | [N] |
| Security | [N] | [N] | [N] | [N] |

### Detected Anti-Patterns

| ID | Name | Severity | Instances | Remediation Priority |
|----|------|----------|-----------|---------------------|
| AA-02 | Distributed Monolith | CRITICAL | 3 | Immediate |
| AA-09 | Diagram Divorce | HIGH | 2 | Short-term |
| AA-17 | Observability Omission | HIGH | 1 | Short-term |
| AA-22 | Trust Assumption | CRITICAL | 1 | Immediate |

---

## C4 Model Maturity (If Applicable)

### Level Completion Status

| Level | Name | Complete | Coverage | Gaps |
|-------|------|----------|----------|------|
| L1 | System Context | [✓/✗] | [N]% | [N] |
| L2 | Container | [✓/✗] | [N]% | [N] |
| L3 | Component | [✓/✗] | [N]% | [N] |
| L4 | Code | [✓/✗/N/A] | [N]% | [N] |

### C4 Maturity Score

```
L1 Context    [████████████████████] 100% ✓
L2 Container  [█████████████████░░░]  85% ✓
L3 Component  [█████████░░░░░░░░░░░]  45% ✗
L4 Code       [░░░░░░░░░░░░░░░░░░░░]   0% N/A
```

---

## ADR Health (If ADRs Present)

### ADR Statistics

| Metric | Value |
|--------|-------|
| Total ADRs | [N] |
| Complete ADRs | [N] |
| Completion Rate | [N]% |
| Average Decision Age | [N] days |
| Decisions Needing Review | [N] |

### ADR Coverage Gaps

| Decision Area | ADR Exists | Status |
|---------------|------------|--------|
| Technology selection | [✓/✗] | [Active/Superseded/Deprecated] |
| Authentication approach | [✓/✗] | [Status] |
| Database choice | [✓/✗] | [Status] |
| API design | [✓/✗] | [Status] |
| Deployment strategy | [✓/✗] | [Status] |
| Caching strategy | [✓/✗] | [Status] |

---

## Trend Indicators (If Historical Data Available)

### Health Score Trend

```
Score
100 ┤
 90 ┤
 80 ┤                                    ╭──
 70 ┤                              ╭─────╯
 60 ┤                    ╭─────────╯
 50 ┤          ╭─────────╯
 40 ┤    ╭─────╯
 30 ┼────╯
    └──────────────────────────────────────────
      Jan   Feb   Mar   Apr   May   Jun   Jul
```

### Trend Summary

| Metric | Previous | Current | Change |
|--------|----------|---------|--------|
| Overall Score | [N] | [N] | [↑/↓/→] [N]% |
| Critical Gaps | [N] | [N] | [↑/↓/→] [N] |
| Anti-Patterns | [N] | [N] | [↑/↓/→] [N] |
| Debt Indicators | [N] | [N] | [↑/↓/→] [N] |

---

## Stakeholder Views

### For Engineering Leadership

**Summary:** [One paragraph executive summary]

**Key Metrics:**
- Architecture Health: [Score]/100 ([Status])
- Critical Issues: [N] requiring immediate attention
- Estimated Remediation: [N] person-days

**Action Required:**
1. [First action item]
2. [Second action item]

### For Security Team

**Summary:** [Security-focused summary]

**Security Score:** [N]/100

**Critical Security Gaps:**
| Gap | Severity | Compliance Impact |
|-----|----------|-------------------|
| [Gap 1] | CRITICAL | [SOC2/GDPR/PCI-DSS] |
| [Gap 2] | HIGH | [Compliance area] |

### For Operations Team

**Summary:** [Operations-focused summary]

**Operational Readiness:** [N]/100

**Key Operational Gaps:**
- [ ] Monitoring strategy documented
- [ ] SLOs defined
- [ ] Runbooks exist
- [ ] DR plan documented
- [ ] Deployment process clear

### For Architects

**Summary:** [Architecture-focused summary]

**Framework Compliance:** [Framework detected] - [N]% compliant

**Viewpoint Coverage Heat Map:**
```
V1 [██████████] V2 [████████░░] V3 [███████░░░]
V4 [█████░░░░░] V5 [████████░░] V6 [█████████░]
V7 [████░░░░░░] V8 [██████░░░░] V9 [███████░░░]
V10[██████░░░░]
```

---

## Recommendations

### Immediate Actions (0-2 weeks)

| Priority | Recommendation | Effort | Impact | Owner |
|----------|---------------|--------|--------|-------|
| 1 | [Action item] | [small/medium/large] | [high/medium/low] | [Role] |
| 2 | [Action item] | [effort] | [impact] | [Role] |
| 3 | [Action item] | [effort] | [impact] | [Role] |

### Short-Term Actions (2-4 weeks)

| Priority | Recommendation | Effort | Impact | Owner |
|----------|---------------|--------|--------|-------|
| 1 | [Action item] | [effort] | [impact] | [Role] |
| 2 | [Action item] | [effort] | [impact] | [Role] |

### Medium-Term Actions (1-3 months)

| Priority | Recommendation | Effort | Impact | Owner |
|----------|---------------|--------|--------|-------|
| 1 | [Action item] | [effort] | [impact] | [Role] |
| 2 | [Action item] | [effort] | [impact] | [Role] |

### Quick Wins

These items can be addressed with minimal effort for immediate improvement:

1. **[Quick Win 1]** - [Brief description] (Effort: trivial)
2. **[Quick Win 2]** - [Brief description] (Effort: small)
3. **[Quick Win 3]** - [Brief description] (Effort: small)

---

## Appendix: Gap Details

### Gap List by Severity

#### Critical Gaps

| ID | Viewpoint | Category | Description | Checklist Ref |
|----|-----------|----------|-------------|---------------|
| GAP-001 | V7 | missing | [Description] | V7-01 |
| GAP-002 | V4 | missing | [Description] | V4-18 |

#### High Gaps

| ID | Viewpoint | Category | Description | Checklist Ref |
|----|-----------|----------|-------------|---------------|
| GAP-003 | V2 | incomplete | [Description] | V2-05 |

#### Medium Gaps

| ID | Viewpoint | Category | Description | Checklist Ref |
|----|-----------|----------|-------------|---------------|
| GAP-010 | V3 | ambiguous | [Description] | V3-12 |

#### Low Gaps

| ID | Viewpoint | Category | Description | Checklist Ref |
|----|-----------|----------|-------------|---------------|
| GAP-015 | V9 | incomplete | [Description] | V9-08 |

---

## Report Metadata

| Field | Value |
|-------|-------|
| Generated By | architecture-doc-auditor v2.0 |
| Report Format | Architecture Health Report v1.0 |
| Generation Date | [ISO 8601 datetime] |
| Source Document | [Document path/identifier] |
| Audit Depth | [surface/standard/exhaustive] |
| Framework Detected | [togaf/c4/arc42/ieee_42010/custom] |
| Confidence Level | [0.0-1.0] |
| Related Artifacts | GI-ARCH-[date]-[hash] (GAP-INVENTORY) |
```

---

## Field Definitions

### Health Score Calculation

```python
def calculate_health_score(viewpoint_scores, gaps, anti_patterns, debt_indicators):
    """
    Calculate overall architecture health score.

    Args:
        viewpoint_scores: dict of {viewpoint_id: score (0-100)}
        gaps: list of gap objects with severity
        anti_patterns: list of detected anti-patterns
        debt_indicators: list of debt indicators

    Returns:
        int: Overall health score (0-100)
    """
    # Weighted average of viewpoint scores
    weights = {
        'V1': 1.0, 'V2': 1.2, 'V3': 1.0, 'V4': 1.2, 'V5': 1.0,
        'V6': 1.0, 'V7': 1.5, 'V8': 1.2, 'V9': 0.8, 'V10': 1.0
    }

    weighted_sum = sum(viewpoint_scores[v] * weights[v] for v in viewpoint_scores)
    total_weight = sum(weights[v] for v in viewpoint_scores)
    base_score = weighted_sum / total_weight

    # Apply penalties
    severity_penalties = {
        'critical': 10,
        'high': 5
    }

    gap_penalty = sum(
        severity_penalties.get(gap['severity'], 0)
        for gap in gaps
    )

    anti_pattern_penalty = len(anti_patterns) * 3
    debt_penalty = len(debt_indicators) * 2

    final_score = base_score - gap_penalty - anti_pattern_penalty - debt_penalty
    return max(0, min(100, int(final_score)))
```

### Status Thresholds

| Status | Score Range | Description |
|--------|-------------|-------------|
| HEALTHY | 80-100 | Architecture documentation is comprehensive |
| ADEQUATE | 60-79 | Minor gaps exist but not blocking |
| AT_RISK | 40-59 | Significant gaps requiring attention |
| CRITICAL | 0-39 | Major gaps blocking implementation |

### Coverage Levels

| Level | Definition | Scoring |
|-------|------------|---------|
| EXPLICIT | Directly documented with specifics | Full credit |
| IMPLICIT | Can be inferred but not stated | Partial credit (50%) |
| MISSING | Not documented or inferable | No credit |

---

## Visualization Guidelines

### Spider Chart (Viewpoint Coverage)

- **Axes:** 10 viewpoint names arranged radially
- **Scale:** 0-100 with rings at 20, 40, 60, 80, 100
- **Colors:**
  - Green fill for scores ≥80
  - Yellow fill for scores 60-79
  - Orange fill for scores 40-59
  - Red fill for scores <40

### Radar Chart (Quality Attributes)

- **Axes:** 8 quality attributes arranged radially
- **Scale:** 0-100 with rings at 25, 50, 75, 100
- **Colors:** Same as spider chart

### Heat Map (Risk Matrix)

- **Rows:** Severity levels (Critical, High, Medium, Low)
- **Columns:** Likelihood levels (Low, Medium, High)
- **Colors:**
  - Dark red: Critical + High Likelihood
  - Red: Critical + Medium or High + High
  - Orange: High + Medium or Medium + High
  - Yellow: Medium + Medium or lower
  - Green: Low severity combinations

---

## Report Distribution

### Recommended Recipients by Role

| Role | Sections | Frequency |
|------|----------|-----------|
| Engineering VP | Executive Summary, Recommendations | Per milestone |
| Solution Architect | Full Report | Every audit |
| Security Lead | Security Gaps, Compliance | Every audit |
| DevOps Lead | Operations, Deployment | Every audit |
| Tech Lead | Viewpoint Details, ADR Health | Every audit |
| Governance Board | Executive Summary, Trend | Quarterly |

---

## References

- [GAP-INVENTORY Output](gap-inventory-output.md) - Detailed gap data
- [Debt Remediation Roadmap](debt-remediation-roadmap.md) - Prioritized actions
- [Architecture Checklist](../references/architecture-checklist.md) - Full checklist
- [Viewpoint Catalog](../references/viewpoint-catalog.md) - Viewpoint definitions
