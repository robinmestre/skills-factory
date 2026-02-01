# What-If Framework

A structured protocol for counterfactual analysis — systematically exploring what would happen if key assumptions were false. This framework enables rigorous stress-testing of decisions, strategies, and plans.

---

## Overview

### Purpose

Counterfactual analysis ("What-If") helps answer:
- How important is this assumption?
- What breaks if it's wrong?
- How robust is our plan to assumption failure?
- What contingencies do we need?

### When to Use

| Use Case | Priority |
|----------|----------|
| Load-bearing assumptions | Required |
| High-dependency assumptions | Recommended |
| Major decision validation | Recommended |
| Strategy stress-testing | Recommended |
| Risk assessment | Required |

### Framework Structure

```
┌─────────────────────────────────────────────┐
│            WHAT-IF ANALYSIS                  │
├─────────────────────────────────────────────┤
│  1. Assumption Statement                     │
│         ↓                                    │
│  2. Counterfactual Construction              │
│         ↓                                    │
│  3. Immediate Impact Assessment              │
│         ↓                                    │
│  4. Cascade Effect Mapping                   │
│         ↓                                    │
│  5. Decision Change Analysis                 │
│         ↓                                    │
│  6. Impact Magnitude Classification          │
│         ↓                                    │
│  7. Contingency Identification               │
└─────────────────────────────────────────────┘
```

---

## The What-If Protocol

### Step 1: Assumption Statement

State the assumption clearly and falsifiably.

**Format:**
```
Assumption [ID]: [Clear, specific, falsifiable statement]
```

**Good Examples:**
- "Customer acquisition cost will remain below $50"
- "Team can deliver feature X by Q3"
- "Competitor will not enter our market segment"

**Poor Examples:**
- "Things will work out" (vague)
- "Market is favorable" (unclear what would falsify)
- "We'll be successful" (not specific)

### Step 2: Counterfactual Construction

Construct the specific opposite or failure case.

**Format:**
```
WHAT-IF: [Assumption] is FALSE

Specific scenario: [Describe what "false" means concretely]
```

**Types of Counterfactuals:**

| Type | Description | Example |
|------|-------------|---------|
| **Direct negation** | Assumption is exactly wrong | "CAC is $100 (not $50)" |
| **Partial failure** | Assumption partially holds | "CAC is $75 (50% higher)" |
| **Worse than expected** | Magnitude is wrong | "Team delivers 3 months late" |
| **Complete failure** | Assumption entirely fails | "Competitor enters immediately" |

### Step 3: Immediate Impact Assessment

Document what breaks immediately if the assumption is false.

**Questions to answer:**
- What stops working right away?
- What becomes invalid?
- What resources are wasted?
- What commitments are affected?

**Format:**
```
Immediate Impacts:
1. [Impact 1]: [Description]
2. [Impact 2]: [Description]
3. [Impact 3]: [Description]
```

### Step 4: Cascade Effect Mapping

Trace second-order and third-order effects.

**Questions to answer:**
- What depends on the things that break?
- What downstream plans are affected?
- What other assumptions are invalidated?
- What stakeholders are impacted?

**Cascade mapping:**
```
[Assumption fails]
    └── [Immediate impact 1]
            └── [Second-order effect 1.1]
            └── [Second-order effect 1.2]
                    └── [Third-order effect 1.2.1]
    └── [Immediate impact 2]
            └── [Second-order effect 2.1]
```

### Step 5: Decision Change Analysis

Determine whether the original decision would change.

**Questions to answer:**
- Knowing this, would we still make the same decision?
- What alternative would we have chosen?
- Is the decision recoverable or fundamentally different?

**Decision change categories:**

| Category | Description |
|----------|-------------|
| **No change** | Decision still valid, minor adjustments |
| **Adjustment** | Same direction, different parameters |
| **Major revision** | Significantly different approach needed |
| **Reversal** | Opposite decision would be better |
| **Cannot proceed** | No viable path forward |

### Step 6: Impact Magnitude Classification

Classify the overall impact.

| Magnitude | Definition | Criteria |
|-----------|------------|----------|
| **NEGLIGIBLE** | No meaningful impact | Decision unchanged; minor inconvenience |
| **MINOR** | Small, manageable impact | Adjustments needed; timeline/cost increase <10% |
| **MODERATE** | Significant but recoverable | Major rework; timeline/cost increase 10-30% |
| **MAJOR** | Substantial impact | Strategy revision needed; timeline/cost increase >30% |
| **CATASTROPHIC** | Existential threat | Project/strategy failure; cannot recover |

### Step 7: Contingency Identification

Based on impact analysis, identify needed contingencies.

**Questions to answer:**
- What early warning signs should we monitor?
- What fallback options exist?
- What preparations should we make now?
- What decision points should we establish?

**Contingency format:**
```
Contingencies if [assumption] fails:
1. Early warning: [Signal to watch]
2. Trigger: [When to activate contingency]
3. Fallback: [Alternative action]
4. Preparation: [What to do now]
```

---

## Complete What-If Template

```markdown
## What-If Analysis: [Assumption ID]

### Assumption
**Statement:** [Clear, falsifiable assumption]
**Current confidence:** [0.0-1.0] ([EPISTEMIC LABEL])

### Counterfactual Scenario
**WHAT-IF:** [Assumption] is FALSE

**Specific scenario:** [Concrete description of failure]

### Immediate Impacts
1. [Impact 1]
2. [Impact 2]
3. [Impact 3]

### Cascade Effects
```
[Assumption fails]
    └── [Immediate 1]
            └── [Second-order 1.1]
            └── [Second-order 1.2]
    └── [Immediate 2]
            └── [Second-order 2.1]
```

### Decision Change
**Would decision change?** [No change | Adjustment | Major revision | Reversal | Cannot proceed]
**Alternative:** [What we would do instead]

### Impact Magnitude
**Classification:** [NEGLIGIBLE | MINOR | MODERATE | MAJOR | CATASTROPHIC]
**Rationale:** [Why this classification]

### Contingencies
1. **Early warning:** [Signal]
2. **Trigger:** [Condition to activate]
3. **Fallback:** [Alternative action]
4. **Preparation:** [Pre-emptive action]

### Conclusion
[Summary assessment of assumption importance and validation priority]
```

---

## Worked Examples

### Example 1: Technical Assumption

**Assumption A3:** "Database can handle 100K transactions per second"

**Current confidence:** 0.55 (POSSIBLE) — benchmarks show 80K, extrapolated

**Counterfactual Scenario:**
WHAT-IF: Database maxes out at 60K TPS

**Immediate Impacts:**
1. Performance degrades during peak hours (4-6pm daily)
2. User experience suffers — increased latency, timeouts
3. Revenue impacted — checkout failures during peak

**Cascade Effects:**
```
[Database can't handle load]
    └── [Peak hour degradation]
            └── [User complaints increase]
            └── [Cart abandonment rises 15%]
                    └── [Revenue drops $50K/month]
    └── [Architecture needs revision]
            └── [3-month redesign project]
            └── [Team diverted from roadmap]
```

**Decision Change:**
- **Would decision change?** Major revision
- **Alternative:** Would have chosen different database or sharding strategy

**Impact Magnitude:** MAJOR
- 3-month delay to fix
- $150K opportunity cost
- Reputation risk with customers

**Contingencies:**
1. **Early warning:** Monitor TPS approaching 50K (80% of assumed failure point)
2. **Trigger:** Activate contingency if TPS exceeds 50K for 3 consecutive days
3. **Fallback:** Pre-designed horizontal scaling plan; read replicas ready
4. **Preparation:** Load test to true failure point before launch; have DBA on call

**Conclusion:** This is a load-bearing assumption. Must validate through load testing before committing to launch date.

---

### Example 2: Market Assumption

**Assumption A7:** "Market will grow 15% annually for next 3 years"

**Current confidence:** 0.70 (LIKELY) — multiple analyst reports agree

**Counterfactual Scenario:**
WHAT-IF: Market grows only 5% annually (or contracts)

**Immediate Impacts:**
1. Revenue projections are 30% too high by Year 3
2. Competitive intensity increases as players fight for share
3. Investor expectations misaligned

**Cascade Effects:**
```
[Market grows only 5%]
    └── [Revenue targets missed]
            └── [Hiring plans delayed]
            └── [Investor confidence shaken]
                    └── [Next funding round harder]
    └── [Competitors fight harder]
            └── [Price pressure increases]
            └── [CAC rises]
```

**Decision Change:**
- **Would decision change?** Adjustment
- **Alternative:** Still enter market, but with lower investment and longer timeline

**Impact Magnitude:** MODERATE
- Business case still positive, but margins thinner
- Timeline extends 12-18 months
- Must adjust investor communication

**Contingencies:**
1. **Early warning:** Track quarterly market reports; watch for growth slowdown
2. **Trigger:** If growth <8% for 2 consecutive quarters
3. **Fallback:** Reduce burn rate; focus on profitability over growth
4. **Preparation:** Maintain option to slow expansion; don't over-commit to fixed costs

**Conclusion:** Market assumption is important but not load-bearing. Monitor closely but don't delay decision.

---

### Example 3: Behavioral Assumption

**Assumption A12:** "Engineering team will adopt new CI/CD practices within 4 weeks"

**Current confidence:** 0.45 (POSSIBLE) — similar changes have taken longer

**Counterfactual Scenario:**
WHAT-IF: Adoption takes 4 months (10× longer)

**Immediate Impacts:**
1. Expected productivity gains don't materialize
2. Release velocity stays flat
3. Team frustration if pushed too hard

**Cascade Effects:**
```
[Adoption takes 4 months]
    └── [Q3 roadmap at risk]
            └── [Customer commitments in jeopardy]
            └── [Sales pipeline affected]
    └── [Team morale issues]
            └── [Key engineer attrition risk]
    └── [Change management questioned]
            └── [Future initiatives harder to sell]
```

**Decision Change:**
- **Would decision change?** Major revision
- **Alternative:** Would phase adoption differently; start with pilot team

**Impact Magnitude:** MODERATE
- Can recover, but at significant cost
- Cultural damage if handled poorly

**Contingencies:**
1. **Early warning:** Track adoption metrics weekly; watch for resistance
2. **Trigger:** If <50% adoption at 4 weeks
3. **Fallback:** Reduce scope; focus on key workflows first
4. **Preparation:** Identify champions; over-invest in training; have executive air cover

**Conclusion:** Behavioral assumption with moderate risk. Validate with pilot before full rollout.

---

## Scenario Construction Techniques

### Direct Negation

Simply negate the assumption.

```
Assumption: "Users will pay $50/month"
Counterfactual: "Users will NOT pay $50/month"
```

### Magnitude Variation

Test different failure magnitudes.

| Scenario | Assumption Value | Counterfactual |
|----------|------------------|----------------|
| Base | $50/month | As expected |
| Minor fail | $40/month | 20% lower |
| Moderate fail | $25/month | 50% lower |
| Major fail | $10/month | 80% lower |
| Total fail | $0 | No willingness to pay |

### Timing Variation

Test different timing failures.

| Scenario | Assumption | Counterfactual |
|----------|------------|----------------|
| Base | Delivered by Q3 | On time |
| Minor delay | Q3 + 1 month | Slight slip |
| Moderate delay | Q4 | Quarter delay |
| Major delay | Next year | Significant slip |
| No delivery | Never | Project fails |

### Combination Scenarios

Combine multiple assumption failures.

```
Combined scenario:
- A1: Database fails to scale AND
- A3: Team adoption is slow AND
- A7: Market growth is lower

Joint impact: [Assess combined effect]
```

---

## Sensitivity Bands

### Classifying Sensitivity

| Sensitivity | Definition | Implication |
|-------------|------------|-------------|
| **INSENSITIVE** | Outcome barely changes | Assumption not critical |
| **LOW** | Minor outcome variation | Monitor assumption |
| **MEDIUM** | Notable outcome variation | Validate assumption |
| **HIGH** | Major outcome variation | Must validate; contingency needed |
| **EXTREME** | Outcome determined by assumption | Load-bearing; block if unvalidated |

### Sensitivity Assessment

For each assumption:

```
Sensitivity = (Outcome if true - Outcome if false) / Outcome if true
```

| Sensitivity % | Band |
|---------------|------|
| < 5% | INSENSITIVE |
| 5-15% | LOW |
| 15-30% | MEDIUM |
| 30-50% | HIGH |
| > 50% | EXTREME |

---

## Integration with Risk Assessment

### From What-If to Risk

Each What-If analysis can generate risks:

| What-If Finding | Risk Derivation |
|-----------------|-----------------|
| Impact = MAJOR/CATASTROPHIC | Direct high-priority risk |
| Cascade effects identified | Multiple related risks |
| Contingency gaps | Risk of unpreparedness |
| Decision change = Reversal | Fundamental viability risk |

### Risk Template from What-If

```xml
<risk id="R[n]" source_assumption="A[m]">
  <category>assumption_failure</category>
  <description>[From What-If immediate impact]</description>
  <trigger>[From counterfactual scenario]</trigger>
  <probability>[Based on assumption confidence]</probability>
  <impact>[From impact magnitude]</impact>
  <mitigation>
    <strategy>[From contingency analysis]</strategy>
    <actions>[From preparation and fallback]</actions>
  </mitigation>
</risk>
```

**See:** `templates/risk-assessment-output.md` for full risk template.

---

## Quick Reference

### What-If Checklist

For each load-bearing assumption:

- [ ] Assumption clearly stated?
- [ ] Counterfactual specifically defined?
- [ ] Immediate impacts enumerated?
- [ ] Cascade effects mapped?
- [ ] Decision change assessed?
- [ ] Impact magnitude classified?
- [ ] Contingencies identified?

### Impact Magnitude Quick Guide

| Ask | Magnitude |
|-----|-----------|
| "Would anyone notice?" | NEGLIGIBLE if no |
| "Can we absorb this easily?" | MINOR if yes |
| "Do we need to change plans?" | MODERATE if yes |
| "Is the project at risk?" | MAJOR if yes |
| "Could this kill the project?" | CATASTROPHIC if yes |

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Assumption types | `assumption-taxonomy.md` |
| Load-bearing analysis | `load-bearing-analysis.md` |
| Validation methods | `validation-methods.md` |
| Confidence calibration | `confidence-calibration.md` |
| Risk output | `templates/risk-assessment-output.md` |
| Sensitivity output | `templates/sensitivity-analysis-output.md` |
