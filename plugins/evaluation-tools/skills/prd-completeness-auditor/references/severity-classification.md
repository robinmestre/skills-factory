# Severity Classification Matrix

Implementation of RUBRIC-07 (SEVERITY-SCORING) for PRD completeness audits.

---

## Overview

Every gap detected in a PRD audit must be assigned a severity level based on three dimensions: impact, likelihood, and detectability. This structured approach ensures consistent, defensible severity assignments across audits.

**Based on:** RUBRIC-07 from `@core/scoring-rubrics.yaml`

---

## Severity Levels

| Level | Numeric | Definition | Response Time | Color |
|-------|---------|------------|---------------|-------|
| **CRITICAL** | 4 | Blocks development; cannot proceed without resolution | Immediate | Red |
| **HIGH** | 3 | Significant impact; major rework likely if not addressed | Before sprint start | Orange |
| **MEDIUM** | 2 | Degrades quality; should fix but development can proceed | Within sprint | Yellow |
| **LOW** | 1 | Minor issue; cosmetic or nice-to-have | When convenient | Green |

---

## Level Definitions

### CRITICAL (4)

**Definition:** This gap blocks the primary development objective. Work cannot meaningfully proceed until resolved.

**Characteristics:**
- Development team cannot start without this information
- Creates fundamental uncertainty about what to build
- No reasonable assumption can bridge the gap
- Wrong assumption would waste significant effort

**PRD Examples:**
- No problem statement (don't know what problem we're solving)
- No primary user persona (don't know who we're building for)
- Acceptance criteria that contradict requirements
- Missing critical dependency information

**Response:** Immediate escalation. Stop audit to resolve if possible.

---

### HIGH (3)

**Definition:** This gap will cause significant impact if not addressed. Major rework is likely during or after development.

**Characteristics:**
- Development could start but with high risk
- Gap will likely surface as scope creep
- Rework probability >50%
- Multiple teams may be affected

**PRD Examples:**
- Vague success metrics (can't measure completion)
- Missing edge case handling
- Incomplete dependency mapping
- User stories without acceptance criteria

**Response:** Resolve before development sprint begins.

---

### MEDIUM (2)

**Definition:** This gap degrades quality but doesn't block progress. Development can proceed with reasonable assumptions.

**Characteristics:**
- Gap can be filled during development
- Team can make reasonable assumptions
- Rework probability 20-50%
- Impact limited to one area

**PRD Examples:**
- Incomplete persona details
- Missing error message specifications
- Partial risk assessment
- Timeline without detailed milestones

**Response:** Address within current sprint. Track as technical debt if deferred.

---

### LOW (1)

**Definition:** Minor issue with limited impact. Nice-to-have improvement rather than necessary fix.

**Characteristics:**
- Gap is cosmetic or polish-related
- No impact on development decisions
- Rework probability <20%
- Easy to fix at any time

**PRD Examples:**
- Formatting inconsistencies
- Minor terminology variations
- Missing optional sections
- Documentation completeness gaps

**Response:** Fix when convenient. May defer indefinitely.

---

## Scoring Dimensions

Each gap is scored on three dimensions:

| Dimension | Weight | Description |
|-----------|--------|-------------|
| **Impact** | 0.5 (50%) | How much does this gap affect downstream development? |
| **Likelihood** | 0.3 (30%) | How likely is this gap to cause actual problems? |
| **Detectability** | 0.2 (20%) | How difficult is it to detect this issue later? |

---

## Dimension: Impact (Weight 0.5)

**Question:** How much does this gap affect downstream development?

| Score | Label | Description | Examples |
|-------|-------|-------------|----------|
| 4 | **Critical** | Stops development entirely | No user definition, no problem statement, fundamental contradictions |
| 3 | **High** | Causes major scope uncertainty | Vague acceptance criteria, missing key dependencies |
| 2 | **Medium** | Leads to rework or confusion | Incomplete edge cases, weak success metrics |
| 1 | **Low** | Minor clarification needed | Formatting, minor ambiguity, optional items |

**Assessment Guide:**

```
Who is affected?
├─ Entire development team + stakeholders → 4 (Critical)
├─ Multiple team members or downstream teams → 3 (High)
├─ Individual team members → 2 (Medium)
└─ Documentation only → 1 (Low)

What decisions depend on this?
├─ Build/no-build or scope decisions → 4 (Critical)
├─ Implementation approach decisions → 3 (High)
├─ Detail-level decisions → 2 (Medium)
└─ Polish/cleanup decisions → 1 (Low)
```

---

## Dimension: Likelihood (Weight 0.3)

**Question:** How likely is this gap to cause actual problems?

| Score | Label | Description | Examples |
|-------|-------|-------------|----------|
| 4 | **Certain** | Will definitely cause issues | Missing critical info with no alternative source |
| 3 | **Likely** | Probably will cause issues | Gap in frequently used requirement |
| 2 | **Possible** | May cause issues depending on team/context | Gap in edge case scenario |
| 1 | **Rare** | Unlikely to cause issues | Gap in rarely exercised path |

**Assessment Guide:**

```
How often will this gap be encountered?
├─ Core flow, every developer will hit this → 4 (Certain)
├─ Main paths, most developers will encounter → 3 (Likely)
├─ Secondary paths, some developers may encounter → 2 (Possible)
└─ Edge cases, rarely encountered → 1 (Rare)

Does the team have context to fill the gap?
├─ No way to reasonably infer → 4 (Certain)
├─ Some team members might guess wrong → 3 (Likely)
├─ Most team members can make reasonable assumption → 2 (Possible)
└─ Gap is obvious/trivial to fill → 1 (Rare)
```

---

## Dimension: Detectability (Weight 0.2)

**Question:** How difficult is it to detect this issue later in the process?

| Score | Label | Description | Examples |
|-------|-------|-------------|----------|
| 4 | **Hidden** | Won't be discovered until production | Edge case with no test coverage |
| 3 | **Difficult** | Requires testing or review to find | Issues caught only in QA |
| 2 | **Moderate** | Visible during development | Issues caught in code review |
| 1 | **Obvious** | Immediately apparent | Issues caught by developer immediately |

**Assessment Guide:**

```
When would this issue be discovered?
├─ In production by users → 4 (Hidden)
├─ During QA/UAT testing → 3 (Difficult)
├─ During development/code review → 2 (Moderate)
└─ Immediately when starting work → 1 (Obvious)

What catches this issue?
├─ Only production monitoring/user reports → 4 (Hidden)
├─ Automated tests or QA processes → 3 (Difficult)
├─ Code review or developer attention → 2 (Moderate)
└─ Obvious during task breakdown → 1 (Obvious)
```

---

## Severity Calculation

### Formula

```
severity_score = (impact × 0.5) + (likelihood × 0.3) + (detectability × 0.2)
```

### Thresholds

| Severity | Score Range | Calculation |
|----------|-------------|-------------|
| **CRITICAL** | >= 3.5 | Very high impact + high likelihood |
| **HIGH** | 2.5 to < 3.5 | Significant combined score |
| **MEDIUM** | 1.5 to < 2.5 | Moderate combined score |
| **LOW** | < 1.5 | Low combined score |

### Example Calculations

**Example 1: Missing Problem Statement**
```
Impact: 4 (Critical - stops understanding)
Likelihood: 4 (Certain - every developer needs this)
Detectability: 1 (Obvious - immediately noticed)

Score = (4 × 0.5) + (4 × 0.3) + (1 × 0.2)
      = 2.0 + 1.2 + 0.2
      = 3.4 → HIGH

Note: Even though detectability is low (good), the impact is so
severe that overall severity is HIGH.
```

**Example 2: Vague Success Metric**
```
Impact: 3 (High - affects completion criteria)
Likelihood: 3 (Likely - will come up in sprint review)
Detectability: 3 (Difficult - may not surface until demo)

Score = (3 × 0.5) + (3 × 0.3) + (3 × 0.2)
      = 1.5 + 0.9 + 0.6
      = 3.0 → HIGH
```

**Example 3: Missing Edge Case**
```
Impact: 2 (Medium - rework in specific area)
Likelihood: 2 (Possible - depends on user behavior)
Detectability: 3 (Difficult - may miss in testing)

Score = (2 × 0.5) + (2 × 0.3) + (3 × 0.2)
      = 1.0 + 0.6 + 0.6
      = 2.2 → MEDIUM
```

**Example 4: Formatting Inconsistency**
```
Impact: 1 (Low - cosmetic only)
Likelihood: 1 (Rare - doesn't affect development)
Detectability: 1 (Obvious - visible immediately)

Score = (1 × 0.5) + (1 × 0.3) + (1 × 0.2)
      = 0.5 + 0.3 + 0.2
      = 1.0 → LOW
```

---

## Quick Reference Tables

### Impact Quick Reference

| Checklist Area | Score 4 | Score 3 | Score 2 | Score 1 |
|----------------|---------|---------|---------|---------|
| Problem (PC) | No statement | Weak evidence | Vague scope | Minor clarity |
| Users (US) | No persona | Incomplete persona | Missing details | Formatting |
| Goals (GS) | No metrics | Unmeasurable | Vague targets | Missing optional |
| Requirements (RQ) | Contradictions | Missing NFRs | Incomplete | Minor gaps |
| Stories (ST) | No stories | Missing AC | Too large | Minor format |
| Acceptance (AC) | None present | Not testable | Incomplete | Minor clarity |
| Dependencies (DP) | No section | Missing critical | Incomplete map | Minor items |
| Risks (RA) | No section | No mitigations | Incomplete | Minor risks |
| Timeline (TS) | No timeline | Inconsistent | Missing detail | Formatting |
| Technical (TC) | Incorrect tech | Missing fit | Incomplete | Minor notes |

### Likelihood Quick Reference

| Scenario | Score |
|----------|-------|
| Every developer will encounter immediately | 4 |
| Most work will be affected | 3 |
| Some work will be affected | 2 |
| Rarely encountered edge cases | 1 |

### Detectability Quick Reference

| Detection Point | Score |
|-----------------|-------|
| Only users in production | 4 |
| QA testing phase | 3 |
| Development / code review | 2 |
| Task breakdown / immediately | 1 |

---

## Severity Override Rules

In some cases, override calculated severity:

### Auto-Promote to CRITICAL

Regardless of calculated score, promote to CRITICAL if:
- Gap involves security requirements
- Gap affects data privacy or compliance
- Gap blocks understanding of primary user
- Gap creates legal/contractual risk

### Auto-Demote to LOW

Regardless of calculated score, demote to LOW if:
- Gap is in explicitly optional section
- Gap is cosmetic only (no functional impact)
- Gap already has workaround documented
- Gap is acknowledged as intentional

---

## Severity Distribution Guidelines

A healthy PRD audit typically shows:

| Severity | Expected % | Red Flag If |
|----------|------------|-------------|
| CRITICAL | 0-5% | Any CRITICAL present |
| HIGH | 5-15% | >20% HIGH |
| MEDIUM | 20-40% | <10% MEDIUM (audit too lenient?) |
| LOW | 40-60% | <30% LOW (audit too strict?) |

**Interpretation:**
- PRD with 0 CRITICAL, <5 HIGH = Ready for development
- PRD with >0 CRITICAL = Blocking issues, escalate
- PRD with >5 HIGH = Significant rework needed
- PRD with only LOW = Either excellent or audit too lenient

---

## Scoring Worksheet

Use this template for each gap:

```
Gap ID: ___________
Checklist Item: ___________
Gap Type: ___________

IMPACT ASSESSMENT
Who is affected? ___________
What decisions depend? ___________
→ Impact Score: [ 1  2  3  4 ]

LIKELIHOOD ASSESSMENT
How often encountered? ___________
Can team fill gap? ___________
→ Likelihood Score: [ 1  2  3  4 ]

DETECTABILITY ASSESSMENT
When discovered? ___________
What catches it? ___________
→ Detectability Score: [ 1  2  3  4 ]

CALCULATION
(Impact × 0.5) + (Likelihood × 0.3) + (Detectability × 0.2)
= (___×0.5) + (___×0.3) + (___×0.2)
= ___ + ___ + ___
= ___

SEVERITY: [ CRITICAL  HIGH  MEDIUM  LOW ]

Override Applied? [ Yes / No ]
Override Reason: ___________
```

---

## Integration with Gap Inventory

Severity scores are recorded in GAP-INVENTORY as:

```xml
<gap id="GAP-001">
  <severity>high</severity>
  <severity_score>
    <impact>3</impact>
    <likelihood>3</likelihood>
    <detectability>2</detectability>
    <composite>2.8</composite>
  </severity_score>
  ...
</gap>
```

This enables:
- Sorting gaps by severity for prioritization
- Summary statistics (by_severity counts)
- Threshold-based filtering (critical_only, high_and_above)
- Trend analysis across multiple audits
