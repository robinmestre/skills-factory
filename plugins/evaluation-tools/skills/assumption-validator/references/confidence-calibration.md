# Confidence Calibration Guide

A framework for assigning, calibrating, and communicating confidence levels for assumptions. Based on RUBRIC-06 (CONFIDENCE-CALIBRATION) from the core library.

---

## Overview

### Why Calibration Matters

Confidence without calibration is meaningless. Overconfidence leads to missed risks; underconfidence leads to paralysis. Calibrated confidence means your stated confidence level matches reality — when you say 70% confident, you're right about 70% of the time.

### The Epistemic Label System

| Label | Confidence Range | Definition |
|-------|------------------|------------|
| **VERIFIED** | 0.90 - 1.00 | Confirmed by direct, primary evidence |
| **LIKELY** | 0.70 - 0.89 | Strong indirect evidence supports |
| **POSSIBLE** | 0.40 - 0.69 | Some evidence, meaningful uncertainty |
| **SPECULATIVE** | 0.10 - 0.39 | Limited evidence, mostly inference |
| **UNKNOWN** | 0.00 - 0.09 | Insufficient basis for judgment |

---

## Epistemic Labels in Detail

### VERIFIED (0.90-1.00)

**Definition:** Assumption is confirmed by direct observation, authoritative documentation, or empirical test.

**Evidence Requirements:**
- Primary source documentation
- Direct measurement or observation
- Official confirmation from authoritative source
- Empirical validation (test, experiment)

**Example Evidence:**
- Vendor documentation states specific capability
- Load test demonstrates performance threshold
- Legal review confirms compliance status
- Financial audit confirms numbers

**Language Signals:**

| Say | Don't Say |
|-----|-----------|
| "Confirmed by [source]" | "We think" |
| "Documented in [reference]" | "Should be" |
| "Tested and verified" | "Probably" |
| "Official specification states" | "We expect" |

**Example:**
> Assumption: "PostgreSQL supports JSON indexing"
>
> Evidence: PostgreSQL 14 documentation explicitly describes GIN indexes for JSONB
>
> Status: VERIFIED (0.95) — Documented official capability

---

### LIKELY (0.70-0.89)

**Definition:** Assumption is supported by strong but indirect evidence, multiple credible sources, or expert consensus.

**Evidence Requirements:**
- Multiple secondary sources agree
- Expert consensus supports
- Strong circumstantial evidence
- Historical precedent consistently supports

**Example Evidence:**
- Industry analysts agree on market trend
- Multiple team members confirm organizational pattern
- Competitor behavior consistent with assumption
- Similar past projects succeeded under similar conditions

**Language Signals:**

| Say | Don't Say |
|-----|-----------|
| "Multiple sources indicate" | "We're sure" |
| "Expert consensus supports" | "Definitely" |
| "Strong evidence suggests" | "Certainly" |
| "Historical precedent shows" | "No doubt" |

**Example:**
> Assumption: "Market will grow 10-15% annually"
>
> Evidence: Three independent analyst reports project 10-18% growth; market has grown 8-14% for past 5 years
>
> Status: LIKELY (0.78) — Consistent projections and historical pattern

---

### POSSIBLE (0.40-0.69)

**Definition:** Assumption has some supporting evidence but meaningful uncertainty remains. Could go either way.

**Evidence Requirements:**
- Single credible source
- Partial evidence
- Reasonable inference from known facts
- Mixed or conflicting signals

**Example Evidence:**
- One analyst report suggests trend
- Some but not all historical data supports
- Logical reasoning chain (not directly verified)
- Some experts agree, others uncertain

**Language Signals:**

| Say | Don't Say |
|-----|-----------|
| "Some evidence suggests" | "Probably" (without qualifier) |
| "Plausible based on" | "We're confident" |
| "May be true, given" | "We believe" |
| "Possible, though uncertain" | "We expect" |

**Example:**
> Assumption: "Users will complete onboarding within 2 weeks"
>
> Evidence: Similar product had 60% completion at 2 weeks; our UX is simpler but audience is different
>
> Status: POSSIBLE (0.55) — Partial precedent, uncertain applicability

---

### SPECULATIVE (0.10-0.39)

**Definition:** Assumption has limited evidence; primarily based on inference, intuition, or hope.

**Evidence Requirements:**
- Minimal direct evidence
- Single expert opinion (unconfirmed)
- Inference from loosely related data
- Plausible but unverified

**Example Evidence:**
- Gut feeling from experienced person
- Extrapolation from different context
- Hypothesis without testing
- Wishful thinking with some basis

**Language Signals:**

| Say | Don't Say |
|-----|-----------|
| "Speculative — limited evidence" | "We think" (without qualifier) |
| "Based on intuition/inference" | "Should work" |
| "Hypothesis, untested" | "Will probably" |
| "Possible, but uncertain" | "We're fairly confident" |

**Warning Signs:**
If you're using SPECULATIVE, consider whether you should be validating before proceeding.

**Example:**
> Assumption: "Competitor won't react for 6 months"
>
> Evidence: Competitor has been slow in past; no direct insight into their plans
>
> Status: SPECULATIVE (0.30) — Historical pattern but no current intelligence

---

### UNKNOWN (0.00-0.09)

**Definition:** Insufficient information to make any judgment. True uncertainty.

**Evidence Requirements:**
- No evidence available
- No relevant precedent
- No expert knowledge accessible
- Genuinely novel situation

**Language Signals:**

| Say | Don't Say |
|-----|-----------|
| "Unknown — no basis for estimate" | "Maybe" (implies some knowledge) |
| "Insufficient information" | Any confidence statement |
| "Cannot assess" | "We don't know, but probably..." |
| "Requires investigation" | Guessing |

**Action Required:**
UNKNOWN status should trigger:
- Explicit acknowledgment of gap
- Decision to either investigate or accept uncertainty
- Documentation of what would need to be known

**Example:**
> Assumption: "New regulation will be favorable"
>
> Evidence: Regulation not yet drafted; no signals from regulators
>
> Status: UNKNOWN (0.05) — Cannot assess until more information available

---

## Evidence Quality Assessment

### Evidence Weighting

| Evidence Type | Weight | Description |
|---------------|--------|-------------|
| **Primary source** | 1.0 | Direct observation, official documentation, measurement |
| **Secondary source** | 0.7 | Reported by credible third party, verified journalism |
| **Expert opinion** | 0.6 | Domain expert judgment, not independently verified |
| **Inference** | 0.4 | Logical derivation from known facts |
| **Assumption** | 0.2 | Based on another (unverified) assumption |

### Quality Factors

Adjust weight based on:

| Factor | Increase Weight | Decrease Weight |
|--------|-----------------|-----------------|
| Recency | Current data | Stale data |
| Relevance | Directly applicable | Tangentially related |
| Source credibility | Established track record | Unknown or biased source |
| Methodology | Rigorous, documented | Ad hoc, unclear |
| Sample size | Large, representative | Small, convenience |

### Calculating Confidence from Evidence

**Method 1: Highest Quality Evidence**

```
Confidence = max(evidence_weight) × relevance_factor
```

Use when single piece of strong evidence dominates.

**Method 2: Weighted Average**

```
Confidence = Σ(weight_i × relevance_i) / n
```

Use when multiple pieces of evidence contribute.

**Method 3: Adjusted for Gaps**

```
Confidence = evidence_confidence × (1 - gap_penalty)
```

Where gap_penalty reflects missing critical evidence.

---

## Calibration Techniques

### Reference Class Forecasting

Instead of estimating from first principles, find similar past situations.

**Protocol:**
1. Define the reference class (similar projects, decisions, situations)
2. Gather outcome data from reference class
3. Use reference class success rate as baseline confidence
4. Adjust for known differences from reference class

**Example:**
> Assumption: "Project will be delivered on time"
>
> Reference class: Similar-sized projects at this company
> Historical data: 30% on-time delivery rate
>
> Baseline confidence: 0.30 (not 0.70+ like we hoped)

### Base Rate Integration

Anchor estimates on base rates before adjusting for specifics.

**Protocol:**
1. Find the base rate (how often is this generally true?)
2. Identify distinguishing features of current case
3. Adjust up or down, but not too far from base rate
4. Document adjustment reasoning

**Example:**
> Assumption: "This startup will succeed"
>
> Base rate: ~10% of startups succeed (general)
> Distinguishing: Experienced founders (+10%), strong market (+ 10%), intense competition (-5%)
>
> Adjusted estimate: ~25% (not 80%+ from optimism)

### Pre-mortem Calibration

Use pre-mortem to check for overconfidence.

**Protocol:**
1. State your confidence level
2. Run pre-mortem: "If this assumption is wrong, why?"
3. List failure reasons
4. Adjust confidence down if failures seem plausible

**Example:**
> Initial confidence: 0.85 "Users will adopt new feature"
>
> Pre-mortem reveals: Change resistance, competing priorities, unclear value
>
> Adjusted confidence: 0.65 — meaningful failure modes exist

### Outside View

Force external perspective to combat insider bias.

**Protocol:**
1. State assumption from insider view
2. Restate from outsider view: "A neutral observer would see..."
3. Note discrepancies between views
4. Adjust toward outside view

**Example:**
> Insider view: "Our product is clearly differentiated" (0.85)
>
> Outside view: "New entrant claims differentiation; incumbents may not notice/care"
>
> Adjusted: 0.60 — differentiation is harder to see externally

---

## Overconfidence Detection

### Warning Signs

| Signal | What It Suggests |
|--------|------------------|
| "Obviously" / "Clearly" | Assumption not questioned |
| "Everyone knows" | Groupthink, not validation |
| No evidence cited | Confidence without basis |
| Round numbers | Estimates not calibrated |
| Extreme confidence (>0.95) on complex matters | Overconfidence |
| Quick, unhedged answers | Not enough consideration |

### Overconfidence Audit Questions

Ask yourself:
1. "What evidence would change my mind?"
2. "What's the base rate for this type of assumption?"
3. "What would a skeptic say?"
4. "Have I looked for disconfirming evidence?"
5. "Am I anchored on my initial estimate?"

### Confidence Intervals

Instead of single point estimates, use ranges:

| Confidence Level | Interval Width |
|------------------|----------------|
| VERIFIED | Narrow (±5%) |
| LIKELY | Moderate (±10-15%) |
| POSSIBLE | Wide (±15-25%) |
| SPECULATIVE | Very wide (±25-40%) |
| UNKNOWN | Cannot estimate |

**Example:**
> Assumption: "Market size is $50M"
>
> Instead of: Confidence 0.75
>
> Use: "Likely $40-60M" (range reflects uncertainty)

---

## Communicating Uncertainty

### Language Patterns

| Epistemic Label | Appropriate Language |
|-----------------|----------------------|
| VERIFIED | "Confirmed", "Documented", "Verified by [source]" |
| LIKELY | "Strong evidence suggests", "Multiple sources indicate" |
| POSSIBLE | "Some evidence supports", "May be true", "Uncertain but plausible" |
| SPECULATIVE | "Limited evidence", "Speculative", "Based on intuition" |
| UNKNOWN | "Cannot assess", "Insufficient information", "Requires investigation" |

### Avoid False Precision

| Bad | Better |
|-----|--------|
| "73% confident" | "Around 70-75%, LIKELY" |
| "We're 90% sure" | "LIKELY with strong evidence" (unless truly VERIFIED) |
| "I think..." | "Based on [evidence], this is POSSIBLE" |

### Uncertainty in Recommendations

When confidence affects recommendations:

| Confidence | Recommendation Language |
|------------|------------------------|
| VERIFIED | "Proceed with confidence" |
| LIKELY | "Proceed with monitoring" |
| POSSIBLE | "Proceed with contingencies" |
| SPECULATIVE | "Investigate before proceeding" |
| UNKNOWN | "Cannot recommend without more information" |

---

## Integration with Assumption Inventory

### Per-Assumption Documentation

```yaml
assumption:
  id: A1
  statement: "[Clear statement]"
  confidence: 0.65
  epistemic_label: POSSIBLE
  evidence:
    - type: secondary_source
      source: "[Reference]"
      weight: 0.7
    - type: inference
      source: "[Reasoning]"
      weight: 0.4
  calibration_method: reference_class
  calibration_notes: "Adjusted from initial 0.80 based on base rate of similar assumptions"
  uncertainty_factors:
    - "[What could make this wrong]"
  would_change_if:
    - "[Evidence that would change confidence]"
```

### Confidence Impact on Priority

Confidence feeds into load-bearing analysis:

```
Priority = (Dependency × (1 - Confidence)) / Validation Cost
```

Lower confidence → Higher priority for validation

**See:** `load-bearing-analysis.md` for full framework.

---

## Quick Reference

### Epistemic Labels at a Glance

| Label | Range | Evidence | Language |
|-------|-------|----------|----------|
| VERIFIED | 0.9-1.0 | Primary, documented | "Confirmed by..." |
| LIKELY | 0.7-0.89 | Strong, multiple | "Evidence suggests..." |
| POSSIBLE | 0.4-0.69 | Partial, mixed | "May be true..." |
| SPECULATIVE | 0.1-0.39 | Limited, inferred | "Speculative, based on..." |
| UNKNOWN | 0.0-0.09 | None | "Cannot assess..." |

### Calibration Checklist

Before assigning final confidence:

- [ ] Searched for disconfirming evidence?
- [ ] Consulted base rates / reference class?
- [ ] Applied outside view?
- [ ] Checked for overconfidence signals?
- [ ] Documented evidence and reasoning?
- [ ] Used appropriate language?

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Load-bearing analysis | `load-bearing-analysis.md` |
| Validation methods | `validation-methods.md` |
| Assumption types | `assumption-taxonomy.md` |
| Output template | `templates/assumption-inventory-output.md` |
