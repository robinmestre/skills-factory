# Assumption Validation Methods

A comprehensive toolkit of 8 validation methods for testing assumptions against evidence, counterfactuals, and expert judgment. Each method includes protocols, cost-benefit analysis, and guidance on when an assumption is "validated enough."

---

## Overview

### Method Catalog

| # | Method | Best For | Evidence Type | Cost | Reliability |
|---|--------|----------|---------------|------|-------------|
| 1 | Evidence Check | All | Documentary | Low | Medium |
| 2 | Counterfactual Analysis | Load-bearing | Analytical | Medium | High |
| 3 | Sensitivity Analysis | Quantitative | Analytical | Medium | High |
| 4 | Historical Precedent | Contextual, Behavioral | Comparative | Low | Medium |
| 5 | Expert Challenge | Technical, Specialized | Opinion | Medium | Variable |
| 6 | Cross-Validation | Critical | Multi-source | High | Very High |
| 7 | Stress Test | Robustness | Analytical | Medium | High |
| 8 | Time Decay Test | Contextual | Analytical | Low | Medium |

### Method Selection Matrix

| Assumption Type | Primary Methods | Secondary Methods |
|-----------------|-----------------|-------------------|
| EXPLICIT | Evidence Check | Cross-Validation |
| IMPLICIT | Counterfactual | Expert Challenge |
| STRUCTURAL | Expert Challenge | Historical Precedent |
| LOAD-BEARING | Cross-Validation + Counterfactual | Stress Test |
| CONTEXTUAL | Historical Precedent | Time Decay Test |
| BEHAVIORAL | Expert Challenge | Historical Precedent |

---

## 1. Evidence Check

### Purpose

Systematically search for and evaluate evidence that supports or contradicts the assumption.

### When to Use

- First-line validation for any assumption
- Works for all assumption types
- Quick and low-cost

### Protocol

**Step 1: Define evidence targets**

What evidence would confirm/disconfirm this assumption?

| Confirming Evidence | Disconfirming Evidence |
|---------------------|------------------------|
| [What would prove true] | [What would prove false] |

**Step 2: Search for evidence**

Sources to check:

| Source Type | Examples |
|-------------|----------|
| **Internal docs** | Reports, meeting notes, prior analysis |
| **Data/metrics** | Analytics, financial data, surveys |
| **External docs** | Vendor specs, industry reports, research |
| **Expert knowledge** | Team members, subject matter experts |
| **Public information** | News, filings, documentation |

**Step 3: Evaluate evidence quality**

| Quality Level | Weight | Criteria |
|---------------|--------|----------|
| **Primary** | 1.0 | Direct observation, official documentation |
| **Secondary** | 0.7 | Credible third-party report |
| **Expert** | 0.6 | Domain expert opinion |
| **Inference** | 0.4 | Logical derivation |
| **Assumption** | 0.2 | Based on another assumption |

**Step 4: Document findings**

```
Evidence found:
- [Evidence 1]: [Quality], [Source]
- [Evidence 2]: [Quality], [Source]

Evidence missing:
- [What we couldn't find]

Assessment: [CONFIRMS | PARTIAL | CONTRADICTS | INCONCLUSIVE]
```

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 1-4 hours typically |
| Resources | Minimal (research tools) |
| Expertise needed | Low to moderate |
| Reliability | Medium (depends on evidence available) |

### "Validated Enough" Threshold

An assumption is validated by evidence check when:

- [ ] Primary or strong secondary evidence found
- [ ] No contradicting evidence of equal or higher quality
- [ ] Resulting confidence ≥ `confidence_threshold`

### Example

**Assumption:** "PostgreSQL can handle our query patterns"

**Evidence search:**

| Source | Finding | Quality |
|--------|---------|---------|
| PostgreSQL docs | Supports JSONB, indexes | Primary (1.0) |
| Stack Overflow | Performance reports mixed | Secondary (0.7) |
| Internal DBA | "Should work, haven't tested our scale" | Expert (0.6) |

**Assessment:** PARTIAL — need performance testing to fully validate

---

## 2. Counterfactual Analysis

### Purpose

Test an assumption by systematically exploring what would happen if it were false.

### When to Use

- Critical for load-bearing assumptions
- When direct evidence is unavailable
- To understand impact of assumption failure

### Protocol

**Step 1: State the assumption clearly**

> Assumption: [Clear, falsifiable statement]

**Step 2: Construct the counterfactual**

> What if [assumption] were FALSE?

**Step 3: Trace immediate impacts**

| Impact Category | If Assumption is False... |
|-----------------|---------------------------|
| Immediate consequences | What breaks right away? |
| Cascade effects | What fails as a result? |
| Decision change | Would we decide differently? |
| Recovery needed | What would we need to do? |

**Step 4: Assess impact magnitude**

| Magnitude | Definition |
|-----------|------------|
| NEGLIGIBLE | No meaningful impact |
| MINOR | Small inconvenience, easily handled |
| MODERATE | Significant rework, manageable |
| MAJOR | Large-scale rework, timeline/budget impact |
| CATASTROPHIC | Project failure, existential threat |

**Step 5: Evaluate assumption strength**

| Counterfactual Impact | Assumption Strength |
|-----------------------|---------------------|
| NEGLIGIBLE | Assumption not important (may skip validation) |
| MINOR-MODERATE | Assumption important but recoverable |
| MAJOR-CATASTROPHIC | Load-bearing assumption — must validate |

**See:** `what-if-framework.md` for detailed counterfactual protocol.

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 30-60 minutes per assumption |
| Resources | Moderate (requires thought) |
| Expertise needed | Domain knowledge helpful |
| Reliability | High (stress-tests importance) |

### Example

**Assumption:** "Users will adopt new workflow within 2 weeks"

**Counterfactual:** What if adoption takes 3+ months?

| Impact Category | Consequences |
|-----------------|--------------|
| Immediate | Training costs increase; productivity dip lasts longer |
| Cascade | Q3 efficiency goals missed; support burden increases |
| Decision change | Might have chosen simpler workflow; phased rollout |
| Recovery | Extended training, dedicated change management |

**Impact Magnitude:** MODERATE-MAJOR

**Conclusion:** Load-bearing assumption — validate with pilot program

---

## 3. Sensitivity Analysis

### Purpose

Determine how sensitive the outcome is to changes in the assumption's value.

### When to Use

- Quantitative assumptions (numbers, percentages, timeframes)
- Financial projections
- Performance estimates

### Protocol

**Step 1: Identify the assumption value**

> Assumption: [Parameter] = [Value]

**Step 2: Define a range of variation**

| Scenario | Value | Range |
|----------|-------|-------|
| Base case | [Original value] | Assumption as stated |
| Optimistic | [+20-30%] | Better than expected |
| Pessimistic | [-20-30%] | Worse than expected |
| Extreme negative | [-50%] | Significantly worse |

**Step 3: Calculate outcome for each scenario**

| Scenario | Assumption Value | Outcome Impact |
|----------|------------------|----------------|
| Base | [Original] | [Baseline outcome] |
| Optimistic | [+X%] | [Impact on outcome] |
| Pessimistic | [-X%] | [Impact on outcome] |
| Extreme | [-50%] | [Impact on outcome] |

**Step 4: Assess sensitivity**

| Sensitivity | Definition | Action |
|-------------|------------|--------|
| LOW | Outcome changes < 10% | Assumption not critical |
| MEDIUM | Outcome changes 10-30% | Monitor assumption |
| HIGH | Outcome changes > 30% | Validate assumption |
| EXTREME | Outcome changes > 50% | Load-bearing — must validate |

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 1-2 hours (more if modeling needed) |
| Resources | May need spreadsheet/model |
| Expertise needed | Moderate (analytical) |
| Reliability | High (quantitative) |

### Example

**Assumption:** "Market growth is 15% annually"

**Sensitivity analysis:**

| Scenario | Growth Rate | 5-Year Revenue Impact |
|----------|-------------|-----------------------|
| Base | 15% | $100M |
| Optimistic | 20% | $125M (+25%) |
| Pessimistic | 10% | $81M (-19%) |
| Extreme | 5% | $68M (-32%) |

**Sensitivity:** HIGH — revenue swings significantly with growth rate

**Conclusion:** Validate market growth assumption with multiple sources

---

## 4. Historical Precedent

### Purpose

Evaluate whether the assumption has held true in similar past situations.

### When to Use

- Contextual assumptions about markets, conditions
- Behavioral assumptions about people/organizations
- Repeating patterns from past projects

### Protocol

**Step 1: Identify analogous situations**

What past situations are similar to the current one?

| Past Situation | Similarity to Current | Outcome |
|----------------|----------------------|---------|
| [Situation 1] | [How similar?] | [What happened?] |
| [Situation 2] | [How similar?] | [What happened?] |

**Step 2: Assess analogy strength**

| Factor | Strong Analogy | Weak Analogy |
|--------|----------------|--------------|
| Context | Very similar | Quite different |
| Time | Recent | Distant past |
| Scale | Similar | Very different |
| Actors | Same or similar | Different |

**Step 3: Examine precedent outcomes**

| Precedent | Assumption Held? | Notes |
|-----------|------------------|-------|
| [Situation 1] | Yes/No/Partial | [Context] |
| [Situation 2] | Yes/No/Partial | [Context] |

**Step 4: Adjust confidence based on precedent**

| Precedent Pattern | Confidence Adjustment |
|-------------------|----------------------|
| Always held | Increase confidence |
| Usually held | Slight increase |
| Mixed results | No change / depends |
| Usually didn't hold | Decrease confidence |
| Never held | Strong decrease |

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 1-2 hours |
| Resources | Historical data/institutional knowledge |
| Expertise needed | Domain experience helpful |
| Reliability | Medium (past ≠ future) |

### Caveats

- Past performance doesn't guarantee future results
- Context may have changed
- Sample size matters (1 precedent is weak)

### Example

**Assumption:** "Team can deliver in 3-month sprints"

**Historical precedent:**

| Past Project | Similar Scope? | Delivery vs. Estimate |
|--------------|---------------|----------------------|
| Project Alpha | Yes | 3.5 months (17% over) |
| Project Beta | Smaller | 2.8 months (on time) |
| Project Gamma | Similar | 4 months (33% over) |

**Pattern:** Similar projects typically run 15-30% over estimate

**Conclusion:** Assumption is OPTIMISTIC — adjust timeline or confidence

---

## 5. Expert Challenge

### Purpose

Have a domain expert critically evaluate the assumption.

### When to Use

- Technical assumptions requiring specialized knowledge
- When you lack expertise to evaluate
- To stress-test assumptions in unfamiliar domains

### Protocol

**Step 1: Identify appropriate expert**

| Expert Type | Good For |
|-------------|----------|
| Internal SME | Company-specific knowledge |
| External consultant | Industry expertise |
| Academic | Theoretical/research-based |
| Practitioner | Hands-on experience |

**Step 2: Frame the assumption clearly**

Present to expert:
> "We're assuming [assumption]. Based on your expertise, what's your assessment?"

**Step 3: Structured expert interview**

| Question | Purpose |
|----------|---------|
| "Is this assumption reasonable?" | Initial assessment |
| "What conditions must hold for this to be true?" | Boundary conditions |
| "What would make this false?" | Failure modes |
| "How confident are you in this assessment?" | Expert confidence |
| "What evidence would change your view?" | Validation criteria |

**Step 4: Document expert assessment**

```
Expert: [Name], [Credentials]
Assessment: [VALID | QUESTIONABLE | INVALID]
Confidence: [Expert's confidence level]
Conditions: [When assumption holds]
Risks: [When assumption fails]
Validation suggested: [What expert recommends]
```

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 1-2 hours (interview + prep) |
| Resources | Expert access (may cost) |
| Expertise needed | Expert has it |
| Reliability | Variable (depends on expert quality) |

### Expert Selection Criteria

Choose experts who:
- Have direct experience with similar situations
- Will give honest assessment (not just confirm)
- Can articulate reasoning, not just opinion
- Have calibrated judgment (aware of uncertainty)

### Example

**Assumption:** "Event sourcing pattern will scale to 10K events/second"

**Expert:** Senior architect with event sourcing production experience

**Expert assessment:**
> "Pattern can scale, but depends on:
> - Event store technology (Kafka yes, PostgreSQL maybe not)
> - Read model rebuild strategy
> - Consumer lag tolerance
>
> I'd rate this QUESTIONABLE without knowing your specific tech stack. Need benchmarks."

---

## 6. Cross-Validation

### Purpose

Validate critical assumptions using multiple independent sources or methods.

### When to Use

- Load-bearing assumptions
- When single source isn't trustworthy
- High-stakes decisions

### Protocol

**Step 1: Identify independent sources/methods**

| Source/Method | Independence | Perspective |
|---------------|--------------|-------------|
| [Source 1] | [How independent?] | [What angle?] |
| [Source 2] | [How independent?] | [What angle?] |
| [Source 3] | [How independent?] | [What angle?] |

Independence means: Different methodologies, different data sources, different biases.

**Step 2: Gather validation from each source**

| Source | Assessment | Confidence | Notes |
|--------|------------|------------|-------|
| Source 1 | [Finding] | [Level] | [Context] |
| Source 2 | [Finding] | [Level] | [Context] |
| Source 3 | [Finding] | [Level] | [Context] |

**Step 3: Compare and reconcile**

| Agreement Pattern | Interpretation |
|-------------------|----------------|
| All agree | Strong validation |
| Majority agree | Moderate validation |
| Mixed | Inconclusive — investigate divergence |
| All disagree | Assumption likely invalid |

**Step 4: Resolve disagreements**

If sources disagree:
- Understand why (different data? Different interpretation?)
- Weight by source quality and relevance
- Document disagreement and uncertainty

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | High (3× single validation) |
| Resources | Multiple sources needed |
| Expertise needed | May need diverse expertise |
| Reliability | Very high (triangulation) |

### Example

**Assumption:** "Market opportunity is $50M annually"

**Cross-validation:**

| Source | Estimate | Method | Quality |
|--------|----------|--------|---------|
| Gartner report | $45M | Industry survey | Secondary |
| Internal analysis | $55M | Bottom-up from customers | Primary |
| Competitor financials | $40M | Public filings inference | Secondary |

**Reconciliation:** Range is $40-55M, central estimate ~$47M

**Conclusion:** Assumption is APPROXIMATELY valid but possibly optimistic; use $45M for planning

---

## 7. Stress Test

### Purpose

Test assumption under extreme conditions to assess robustness.

### When to Use

- Performance/capacity assumptions
- Resilience assumptions
- When failure would be catastrophic

### Protocol

**Step 1: Define stress scenarios**

| Scenario | Condition | Purpose |
|----------|-----------|---------|
| Peak load | 2-3× normal | Test capacity headroom |
| Failure mode | Component failure | Test resilience |
| Extreme input | Edge cases | Test boundary handling |
| Duration | Extended period | Test sustained performance |

**Step 2: Apply stress to assumption**

| Stress Applied | Assumption Response |
|----------------|---------------------|
| [Scenario 1] | [What happens?] |
| [Scenario 2] | [What happens?] |

**Step 3: Identify breaking points**

At what point does the assumption fail?

| Factor | Safe Range | Breaking Point |
|--------|------------|----------------|
| [Factor 1] | [Range] | [Limit] |
| [Factor 2] | [Range] | [Limit] |

**Step 4: Assess margin of safety**

```
Margin = (Breaking Point - Expected Operation) / Expected Operation
```

| Margin | Assessment |
|--------|------------|
| > 50% | Strong margin — assumption robust |
| 20-50% | Adequate margin — monitor closely |
| < 20% | Thin margin — assumption vulnerable |
| Negative | Already at risk — assumption questionable |

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | High (requires testing) |
| Resources | May need test environment |
| Expertise needed | Technical |
| Reliability | Very high (empirical) |

### Example

**Assumption:** "System handles 5K concurrent users"

**Stress test results:**

| Load | Response Time | Error Rate | Status |
|------|---------------|------------|--------|
| 3K | 200ms | 0% | OK |
| 5K | 350ms | 0.1% | OK |
| 7K | 800ms | 2% | Degraded |
| 10K | 2000ms | 15% | Failed |

**Breaking point:** ~7K users

**Margin of safety:** (7K - 5K) / 5K = 40% — adequate but not strong

---

## 8. Time Decay Test

### Purpose

Evaluate whether the assumption will remain valid over the relevant time horizon.

### When to Use

- Long-term plans and strategies
- Contextual assumptions about markets, technology
- Regulatory and policy assumptions

### Protocol

**Step 1: State the assumption with time context**

> Assumption: [Statement] — must hold for [time period]

**Step 2: Assess decay factors**

| Factor | Current State | Trend | Time to Change |
|--------|---------------|-------|----------------|
| Technology | [State] | [Direction] | [Estimate] |
| Market | [State] | [Direction] | [Estimate] |
| Competition | [State] | [Direction] | [Estimate] |
| Regulation | [State] | [Direction] | [Estimate] |
| Other | [State] | [Direction] | [Estimate] |

**Step 3: Project assumption validity**

| Time Horizon | Assumption Valid? | Confidence |
|--------------|-------------------|------------|
| 6 months | Yes/No/Maybe | [Level] |
| 1 year | Yes/No/Maybe | [Level] |
| 3 years | Yes/No/Maybe | [Level] |
| 5 years | Yes/No/Maybe | [Level] |

**Step 4: Identify triggers for re-validation**

What events/changes should trigger re-evaluation of this assumption?

### Cost-Benefit Analysis

| Factor | Assessment |
|--------|------------|
| Time | 1-2 hours (research + analysis) |
| Resources | Trend data, forecasts |
| Expertise needed | Domain knowledge |
| Reliability | Medium (prediction is hard) |

### Example

**Assumption:** "React will remain the dominant frontend framework"

**Time decay analysis:**

| Time | Assessment | Rationale |
|------|------------|-----------|
| 1 year | LIKELY (0.85) | Strong ecosystem, no clear challenger |
| 3 years | POSSIBLE (0.60) | Emerging alternatives (Solid, Qwik) |
| 5 years | SPECULATIVE (0.35) | Technology shifts unpredictable |

**Trigger for re-validation:** If React npm downloads decline >20% YoY

---

## Validation Decision Matrix

### When Is "Validated Enough"?

| Assumption Priority | Validation Requirement |
|---------------------|------------------------|
| CRITICAL | Multiple methods agree; confidence ≥ 0.85 |
| HIGH | Primary method validates; confidence ≥ 0.75 |
| MEDIUM | Evidence check passes; confidence ≥ 0.65 |
| LOW | Documented with light check; confidence ≥ 0.50 |
| MINIMAL | Documented only; any confidence |

### Validation Status Definitions

| Status | Criteria |
|--------|----------|
| **VALIDATED** | Confidence ≥ threshold; evidence quality ≥ 0.7 |
| **PARTIAL** | Some evidence; confidence < threshold |
| **UNVALIDATED** | No evidence found or conflicting evidence |
| **INVALIDATED** | Evidence contradicts assumption |
| **CONTESTED** | Sources/experts disagree |

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Assumption types | `assumption-taxonomy.md` |
| Prioritization | `load-bearing-analysis.md` |
| Counterfactual protocol | `what-if-framework.md` |
| Confidence levels | `confidence-calibration.md` |
| Surfacing techniques | `surfacing-techniques.md` |
