# Load-Bearing Analysis Framework

A systematic methodology for identifying, scoring, and prioritizing assumptions based on their criticality — how much depends on them and what happens if they're wrong.

---

## Overview

### Why Load-Bearing Analysis Matters

Not all assumptions are equal. Some are minor details; others are structural foundations. Load-bearing assumptions are single points of failure — if wrong, the entire edifice collapses. This framework helps identify which assumptions deserve validation effort and which can be accepted with monitoring.

### The Four Scoring Dimensions

| Dimension | Question | Scale | Weight |
|-----------|----------|-------|--------|
| **Dependency (D)** | How much depends on this assumption? | 1-5 | Primary |
| **Reversibility (R)** | Can we recover if it's wrong? | 1-5 | Secondary |
| **Validation Cost (V)** | How hard is it to verify? | 1-5 | Efficiency |
| **Confidence (C)** | How confident are we now? | 0-1 | Current state |

### The Priority Formula

```
Priority = (Dependency × (1 - Confidence)) / Validation Cost
```

**Interpretation:**
- High dependency + Low confidence + Low validation cost = HIGHEST PRIORITY
- Low dependency + High confidence + High validation cost = LOWEST PRIORITY

---

## Dimension 1: Dependency Score

### Definition

How many other assumptions, conclusions, or outcomes depend on this assumption being true?

### Scoring Rubric

| Score | Label | Definition | Indicator |
|-------|-------|------------|-----------|
| **5** | Critical | Everything depends on this | Single point of failure |
| **4** | High | Most key outcomes depend | Major dependency hub |
| **3** | Moderate | Several important items depend | Significant but not sole |
| **2** | Low | Few things depend | Limited scope |
| **1** | Minimal | Almost nothing depends | Isolated assumption |

### Scoring Protocol

**Step 1: List what depends on the assumption**

For assumption A, list:
- Other assumptions that assume A is true
- Conclusions that require A
- Plans that build on A
- Decisions that incorporate A

**Step 2: Count dependency types**

| Count | Score |
|-------|-------|
| 10+ items depend | 5 |
| 7-9 items depend | 4 |
| 4-6 items depend | 3 |
| 2-3 items depend | 2 |
| 0-1 items depend | 1 |

**Step 3: Adjust for criticality**

If any dependent item is itself critical (strategy pillar, core capability, key milestone), increase score by 1 (max 5).

### Dependency Mapping Technique

Visualize dependencies:

```
[Assumption A]
    │
    ├── [Conclusion 1] ← depends on A
    │       └── [Sub-conclusion 1.1]
    ├── [Assumption B] ← also depends on A
    │       └── [Conclusion 2]
    ├── [Decision D] ← incorporates A
    └── [Plan P] ← builds on A

Dependency count: 4 direct + 2 indirect = 6 → Score: 3
But Conclusion 1 is a strategy pillar → Adjust to 4
```

### Examples

| Assumption | Dependencies | Score | Rationale |
|------------|--------------|-------|-----------|
| "Market grows 20% annually" | Financial projections, hiring plan, capacity plan, investor pitch | 5 | Everything built on this |
| "Team can learn new framework" | Project timeline, quality estimates | 3 | Moderate downstream impact |
| "Logo color preference is blue" | Marketing materials | 1 | Easily changed, minimal deps |

---

## Dimension 2: Reversibility Score

### Definition

How difficult and costly is it to recover if the assumption turns out to be wrong?

### Scoring Rubric

| Score | Label | Recovery Scenario | Examples |
|-------|-------|-------------------|----------|
| **5** | Catastrophic | Cannot recover; existential damage | Public failure, regulatory breach |
| **4** | Very Difficult | Major rework; significant loss | Architecture rebuild, market exit |
| **3** | Difficult | Substantial effort required | Process redesign, team restructure |
| **2** | Moderate | Some effort but manageable | Feature pivot, vendor change |
| **1** | Easy | Trivial to correct | Configuration change, minor update |

### Scoring Protocol

**Step 1: Imagine the assumption is wrong**

What happens? Describe the scenario.

**Step 2: Assess recovery requirements**

| Factor | Questions |
|--------|-----------|
| **Time** | How long to recover? Days? Months? Years? |
| **Cost** | What's the financial impact? Budget? Revenue? |
| **Reputation** | Is there public/stakeholder damage? |
| **Opportunity** | What's missed while recovering? |
| **Precedent** | Does this create lasting constraints? |

**Step 3: Score based on worst factor**

Use the highest-impact factor for scoring.

### Examples

| Assumption | If Wrong... | Recovery | Score |
|------------|-------------|----------|-------|
| "Database will scale to 1M users" | Entire architecture needs redesign | 12+ months, major cost | 4 |
| "Team prefers Slack over Teams" | Switch collaboration tools | Days, minor disruption | 1 |
| "Competitor won't sue for patent" | Litigation, possible injunction | Years, existential risk | 5 |
| "Users want dark mode" | Deprioritize feature | Weeks, minor impact | 2 |

---

## Dimension 3: Validation Cost

### Definition

How much effort, time, and resources are required to verify or validate the assumption?

### Scoring Rubric (Inverse Scale)

Note: Lower score = easier to validate = more efficient to check

| Score | Label | Effort Required | Examples |
|-------|-------|-----------------|----------|
| **1** | Trivial | < 1 hour, no resources | Quick search, ask one person |
| **2** | Easy | Hours, minimal resources | Document review, brief interview |
| **3** | Moderate | Days, some resources | Data analysis, expert consultation |
| **4** | Difficult | Weeks, significant resources | Research study, pilot project |
| **5** | Very Difficult | Months, major investment | Market test, prototype build |

### Validation Method → Cost Mapping

| Validation Method | Typical Cost Score |
|-------------------|-------------------|
| Document review | 1-2 |
| Internal expert query | 1-2 |
| Data analysis (existing data) | 2-3 |
| External expert consultation | 2-3 |
| Customer interviews (small sample) | 3 |
| Competitive analysis | 3 |
| Prototype/POC | 3-4 |
| Pilot program | 4-5 |
| Market research study | 4-5 |
| Full implementation test | 5 |

### Examples

| Assumption | Validation Method | Cost Score |
|------------|-------------------|------------|
| "API documentation exists" | Check vendor website | 1 |
| "Team has React experience" | Ask hiring manager | 1 |
| "Database supports our query patterns" | Run benchmark tests | 3 |
| "Customers will pay premium" | A/B price test | 4 |
| "Architecture scales to 10x" | Load testing at scale | 4 |

---

## Dimension 4: Confidence Score

### Definition

How confident are we that the assumption is true, based on current evidence?

### Scoring Rubric

| Score Range | Label | Definition | Evidence Basis |
|-------------|-------|------------|----------------|
| **0.9-1.0** | VERIFIED | Confirmed by direct evidence | Primary source, documented |
| **0.7-0.9** | LIKELY | Strong indirect evidence | Multiple secondary sources |
| **0.4-0.7** | POSSIBLE | Some supporting evidence | Single source or inference |
| **0.1-0.4** | SPECULATIVE | Limited evidence, mostly inference | Expert opinion only |
| **0.0-0.1** | UNKNOWN | Insufficient basis for judgment | No evidence |

### Confidence Assessment Protocol

**Step 1: List evidence supporting the assumption**

**Step 2: Categorize evidence quality**

| Evidence Type | Quality Weight |
|---------------|----------------|
| Primary source (direct observation, measurement) | 1.0 |
| Secondary source (reported by credible third party) | 0.7 |
| Expert opinion (domain expert judgment) | 0.6 |
| Inference (logical derivation) | 0.4 |
| Assumption (based on another assumption) | 0.2 |

**Step 3: Calculate weighted confidence**

```
Confidence = max(evidence_weight) × coverage_factor
```

Where coverage_factor adjusts for gaps:
- Full evidence coverage: 1.0
- Some gaps: 0.8
- Major gaps: 0.6

### Examples

| Assumption | Evidence | Confidence |
|------------|----------|------------|
| "PostgreSQL supports JSONB" | Vendor documentation (primary) | 0.95 VERIFIED |
| "Market is $5B" | Industry analyst report (secondary) | 0.75 LIKELY |
| "Users prefer simplicity" | 3 user interviews (limited primary) | 0.55 POSSIBLE |
| "Competitor won't react" | Gut feeling (no evidence) | 0.15 SPECULATIVE |

**See:** `confidence-calibration.md` for detailed calibration techniques.

---

## Priority Calculation

### The Formula

```
Priority = (Dependency × (1 - Confidence)) / Validation Cost
```

### Formula Rationale

| Component | Contribution |
|-----------|--------------|
| **Dependency (D)** | Higher dependency = more important to validate |
| **(1 - Confidence)** | Lower confidence = more uncertainty = more value from validation |
| **/ Validation Cost** | Lower cost = better ROI on validation effort |

### Priority Interpretation

| Priority Score | Category | Action |
|----------------|----------|--------|
| **> 3.0** | CRITICAL | Validate immediately; block decision if unvalidated |
| **2.0-3.0** | HIGH | Validate before major commitment |
| **1.0-2.0** | MEDIUM | Validate if time permits |
| **0.5-1.0** | LOW | Document and monitor |
| **< 0.5** | MINIMAL | Accept with light monitoring |

### Worked Examples

**Example 1: Critical Assumption**

| Assumption: "Database scales to 1M users" |
|-------------------------------------------|
| Dependency: 5 (architecture, business case, timeline depend) |
| Confidence: 0.35 (limited benchmarking done) |
| Validation Cost: 3 (load testing feasible in days) |
| **Priority = (5 × 0.65) / 3 = 1.08** |
| Category: MEDIUM — but adjust for reversibility |

If Reversibility = 4 (architecture rebuild if wrong):
**Adjusted Priority = 1.08 × 1.5 = 1.62** → HIGH

**Example 2: Low-Priority Assumption**

| Assumption: "Team prefers Jira over Asana" |
|--------------------------------------------|
| Dependency: 2 (affects workflow, not outcomes) |
| Confidence: 0.70 (team survey indicates preference) |
| Validation Cost: 1 (just ask again) |
| **Priority = (2 × 0.30) / 1 = 0.60** |
| Category: LOW — document and proceed |

**Example 3: High-Efficiency Validation Target**

| Assumption: "Vendor has SOC 2 certification" |
|---------------------------------------------|
| Dependency: 4 (security review, compliance depend) |
| Confidence: 0.20 (assumed but not verified) |
| Validation Cost: 1 (check vendor website/ask) |
| **Priority = (4 × 0.80) / 1 = 3.20** |
| Category: CRITICAL — validate immediately (easy to check!) |

---

## Criticality Assessment Matrix

### 2×2 Quick Classification

```
                    HIGH CONFIDENCE          LOW CONFIDENCE
                    ┌─────────────────────┬─────────────────────┐
       HIGH         │                     │                     │
       DEPENDENCY   │     MONITOR         │     VALIDATE        │
                    │   (confident but    │   (uncertain and    │
                    │    critical)        │    critical)        │
                    ├─────────────────────┼─────────────────────┤
       LOW          │                     │                     │
       DEPENDENCY   │     ACCEPT          │     DOCUMENT        │
                    │   (confident and    │   (uncertain but    │
                    │    non-critical)    │    non-critical)    │
                    └─────────────────────┴─────────────────────┘
```

### Quadrant Actions

| Quadrant | Action | Priority |
|----------|--------|----------|
| **VALIDATE** | Apply validation methods, require evidence | HIGH |
| **MONITOR** | Track for changes, set triggers for re-validation | MEDIUM |
| **DOCUMENT** | Record assumption, light monitoring | LOW |
| **ACCEPT** | Note and proceed | MINIMAL |

---

## Prioritization Workflow

### Step-by-Step Process

**Step 1: Score all assumptions**

Create scoring table:

| ID | Assumption | D | R | V | C | Priority | Reversibility-Adjusted |
|----|------------|---|---|---|---|----------|------------------------|
| A1 | ... | | | | | | |

**Step 2: Calculate raw priority**

Apply formula: Priority = (D × (1 - C)) / V

**Step 3: Adjust for reversibility**

For assumptions with Reversibility ≥ 4:
```
Adjusted Priority = Raw Priority × 1.5
```

**Step 4: Sort and categorize**

Order by adjusted priority, assign categories.

**Step 5: Apply validation intensity filter**

| Intensity | Focus On |
|-----------|----------|
| Light | Top 3 by priority |
| Standard | Top 5 by priority |
| Rigorous | All with priority > 1.0 |

### Example Prioritization Table

| ID | Assumption | D | R | V | C | Priority | Adj. | Category |
|----|------------|---|---|---|---|----------|------|----------|
| A3 | Competitor won't react | 5 | 4 | 4 | 0.25 | 0.94 | 1.41 | HIGH |
| A1 | Database scales | 5 | 4 | 3 | 0.35 | 1.08 | 1.62 | HIGH |
| A7 | Vendor SOC 2 | 4 | 3 | 1 | 0.20 | 3.20 | 3.20 | CRITICAL |
| A2 | Team expertise | 4 | 3 | 2 | 0.60 | 0.80 | 0.80 | LOW |
| A5 | Logo color | 1 | 1 | 1 | 0.70 | 0.30 | 0.30 | MINIMAL |

**Validation order:** A7 → A1 → A3 → A2 (A5 accepted)

---

## Load-Bearing Identification Criteria

An assumption is classified as **LOAD-BEARING** if any of the following are true:

| Criterion | Threshold | Rationale |
|-----------|-----------|-----------|
| Adjusted Priority > 3.0 | Automatic | High-value validation target |
| Dependency = 5 | Automatic | Single point of failure |
| Type = STRUCTURAL | Consider | Framing assumptions are foundational |
| Reversibility = 5 | Automatic | Catastrophic if wrong |
| Multiple outcomes depend | Review | Concentration risk |

### Load-Bearing Checklist

For each assumption, check:

- [ ] Does everything depend on this? (Dependency = 5)
- [ ] Is recovery catastrophic if wrong? (Reversibility = 5)
- [ ] Is this a framing assumption? (Type = STRUCTURAL)
- [ ] Does adjusted priority exceed 3.0?
- [ ] Would failure invalidate the entire plan/decision?

If **any** check is true, mark as LOAD-BEARING and prioritize validation.

---

## Integration with Validation

### From Priority to Validation Method

| Priority Category | Validation Approach |
|-------------------|---------------------|
| CRITICAL | Multiple methods, high rigor, block decision |
| HIGH | Primary method + one backup, validate before commit |
| MEDIUM | Single appropriate method, validate if time |
| LOW | Document, light monitoring |
| MINIMAL | Accept with awareness |

### Validation Intensity Matrix

| Assumption Priority | `validation_intensity: light` | `standard` | `rigorous` |
|---------------------|------------------------------|------------|------------|
| CRITICAL | Validate (top 3) | Validate | Validate |
| HIGH | Document | Validate (top 5) | Validate |
| MEDIUM | Document | Document | Validate |
| LOW | Skip | Document | Document |
| MINIMAL | Skip | Skip | Document |

**See:** `validation-methods.md` for validation protocols.

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Assumption types | `assumption-taxonomy.md` |
| Surfacing techniques | `surfacing-techniques.md` |
| Validation methods | `validation-methods.md` |
| Confidence calibration | `confidence-calibration.md` |
| Counterfactual analysis | `what-if-framework.md` |
