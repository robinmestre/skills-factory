# Assumption Surfacing Techniques

A comprehensive toolkit of 12 techniques for systematically uncovering explicit, implicit, and structural assumptions. Each technique includes step-by-step protocols, when to use, expected yield, and worked examples.

---

## Overview

### Technique Catalog

| # | Technique | Primary Target | Expected Yield | Time |
|---|-----------|----------------|----------------|------|
| 1 | Document Scan | EXPLICIT | 3-10 assumptions | 15 min |
| 2 | Inversion | IMPLICIT | 5-15 assumptions | 30 min |
| 3 | Five Whys | IMPLICIT | 3-8 per chain | 20 min |
| 4 | Outsider Test | IMPLICIT | 5-10 assumptions | 20 min |
| 5 | Pre-mortem | LOAD-BEARING | 5-12 assumptions | 30 min |
| 6 | Dependency Mapping | LOAD-BEARING | 3-8 dependencies | 30 min |
| 7 | Frame Questioning | STRUCTURAL | 2-5 assumptions | 20 min |
| 8 | Missing Voices | STRUCTURAL | 2-4 assumptions | 15 min |
| 9 | Scope Boundary Probe | STRUCTURAL | 2-6 assumptions | 15 min |
| 10 | Fill-in-the-Blank | IMPLICIT | 2-5 clarifications | 10 min |
| 11 | Reverse Assumption | ALL | 1 per assumption | 5 min each |
| 12 | PESTLE Scan | CONTEXTUAL | 5-15 assumptions | 30 min |

### Selection Matrix by Intensity

| Intensity | Minimum Techniques | Recommended Set |
|-----------|-------------------|-----------------|
| **Light** | 2 | Document Scan + Inversion |
| **Standard** | 4 | Document Scan + Inversion + Pre-mortem + Frame Questioning |
| **Rigorous** | All | Complete set with multiple passes |

---

## 1. Document Scan

### Purpose

Systematically extract all explicitly stated assumptions from the subject document.

### When to Use

- Always — the first technique in any assumption validation
- Works for: decisions, strategies, plans, architectures, proposals

### Protocol

**Step 1: Prepare scan targets**

Create a checklist of linguistic markers:

```
□ "We assume..."        □ "Assuming..."
□ "Given that..."       □ "This depends on..."
□ "If [condition]..."   □ "We're betting that..."
□ "Our hypothesis..."   □ "Predicated on..."
□ "Contingent upon..."  □ "Subject to..."
□ "Based on the premise..." □ "Taking as given..."
```

**Step 2: Scan document sections**

Prioritize these locations:

| Priority | Location | Why |
|----------|----------|-----|
| 1 | "Assumptions" section | Explicit listing |
| 2 | Executive summary | Key assumptions often summarized |
| 3 | Risk section | Assumptions often frame risks |
| 4 | Appendices/footnotes | Caveats and conditions |
| 5 | Financial projections | Embedded in numbers |
| 6 | Timeline/roadmap | Dependency assumptions |

**Step 3: Extract and document**

For each assumption found:

```
- ID: A[n]
- Statement: [verbatim text]
- Source: [page, section, paragraph]
- Type: EXPLICIT
- Initial confidence: [assess based on evidence cited]
```

**Step 4: Confirm with author (if available)**

Ask: "Are there any assumptions you documented that I may have missed?"

### Expected Yield

- Documents with formal "Assumptions" section: 5-15 assumptions
- Informal documents: 3-10 assumptions
- Presentations/briefs: 2-5 assumptions

### Example

**Source document excerpt:**
> "This business case assumes (1) budget approval by Q2, (2) 15% YoY growth, and (3) no new competitors entering the market. Given that exchange rates remain within 5% of current levels, the ROI projection stands at 18%."

**Extracted assumptions:**
- A1: Budget approval by Q2 (EXPLICIT, source: paragraph 1)
- A2: 15% YoY growth (EXPLICIT, source: paragraph 1)
- A3: No new competitors entering market (EXPLICIT, source: paragraph 1)
- A4: Exchange rates remain within 5% of current (EXPLICIT, source: paragraph 1)

---

## 2. Inversion

### Purpose

Surface implicit assumptions by asking what would have to be true for the plan to succeed — then inverting to find failure conditions.

### When to Use

- After document scan to find implicit assumptions
- Especially effective for plans, strategies, architectures
- High yield technique — use on all validation intensities

### Protocol

**Step 1: Identify key claims or conclusions**

From the subject document, list:
- Key assertions ("This will work because...")
- Success criteria ("We'll achieve X by Y")
- Causal claims ("A leads to B")

**Step 2: Apply inversion question**

For each claim, ask:

> "What would have to be true for this to work?"

Document all necessary conditions.

**Step 3: Invert to find hidden assumptions**

For each necessary condition, ask:

> "What would cause this to fail?"

This reveals assumptions that aren't being examined.

**Step 4: Probe deeper**

For important conditions:

> "What else would have to be true for [condition] to hold?"

### Expected Yield

- 5-15 implicit assumptions per major claim
- Each claim typically generates 3-5 necessary conditions
- Each condition often reveals 1-2 hidden assumptions

### Example

**Claim:** "Migrating to microservices will improve our scalability."

**Step 2: What would have to be true?**
- Team has microservices expertise
- Service boundaries are well-understood
- Infrastructure supports container orchestration
- Operational complexity is manageable
- Performance overhead of distributed calls is acceptable

**Step 3: What would cause failure?**
- A1: Team lacks microservices experience → learning curve delays, poor design decisions
- A2: Service boundaries are unclear → creates distributed monolith
- A3: Infrastructure can't handle orchestration → deployment failures
- A4: Operational complexity exceeds capacity → incidents, downtime
- A5: Network latency degrades user experience → performance regression

**Implicit assumptions surfaced:**
- Team has sufficient microservices expertise (A1, IMPLICIT, BEHAVIORAL)
- Service boundaries are determinable from current architecture (A2, IMPLICIT, STRUCTURAL)
- Infrastructure team can build/maintain orchestration (A3, IMPLICIT, BEHAVIORAL)
- Operations can handle increased complexity (A4, IMPLICIT, BEHAVIORAL)
- Network latency is acceptable for use cases (A5, IMPLICIT, CONTEXTUAL)

---

## 3. Five Whys

### Purpose

Drill into the reasoning chain to expose foundational assumptions by repeatedly asking "Why?"

### When to Use

- When initial assumptions seem obvious or shallow
- To find the root assumptions behind surface-level claims
- When you sense "there's something deeper here"

### Protocol

**Step 1: Identify a key claim or decision**

Select a statement that seems important but potentially under-examined.

**Step 2: Ask "Why?" and document the answer**

> Claim: "We should build this feature."
> Why? "Because users want it."

**Step 3: Ask "Why?" again on the answer**

> Why do users want it?
> "Because they've requested it in surveys."

**Step 4: Continue asking "Why?" (typically 5 times)**

> Why do we trust the survey results?
> "Because we had a good sample size."

> Why is sample size sufficient for confidence?
> "Because it represents our active user base."

> Why does active user base represent future users?
> "Because... [hesitation = assumption found]"

**Step 5: Document the assumption chain**

Each "Why?" answer reveals a layer of assumption.

### Expected Yield

- 3-8 assumptions per reasoning chain
- Deeper assumptions are often more critical
- Hesitation or uncertainty signals key assumptions

### Example

**Starting claim:** "We should enter the European market."

| Level | Question | Answer | Assumption Revealed |
|-------|----------|--------|---------------------|
| 1 | Why? | Market opportunity is $50M | A1: Market sizing is accurate |
| 2 | Why believe sizing? | Industry analysts say so | A2: Analyst projections are reliable |
| 3 | Why trust analysts? | They've been right before | A3: Past accuracy predicts future |
| 4 | Why does past = future? | Market conditions are similar | A4: EU market conditions match historical |
| 5 | Why similar? | [hesitation] | A5: No major disruptions expected |

**Assumptions surfaced:**
- A1: $50M market sizing is accurate (EXPLICIT, CONTEXTUAL)
- A2: Industry analyst projections are reliable for our segment (IMPLICIT)
- A3: Historical analyst accuracy predicts future accuracy (IMPLICIT)
- A4: Current EU market conditions resemble historical patterns (IMPLICIT, CONTEXTUAL)
- A5: No major market disruptions expected (IMPLICIT, CONTEXTUAL)

---

## 4. Outsider Test

### Purpose

Identify assumptions that insiders take for granted but outsiders would question immediately.

### When to Use

- When the team has deep domain expertise
- When assumptions might be "obvious" to insiders
- To escape echo chamber effects

### Protocol

**Step 1: Define the outsider persona**

Choose a relevant outsider perspective:

| Persona | Good For |
|---------|----------|
| New employee (Day 1) | Internal process assumptions |
| Competitor analyst | Strategic assumptions |
| Customer unfamiliar with product | UX/value assumptions |
| Investor/board member | Business model assumptions |
| Regulator | Compliance assumptions |
| Security auditor | Technical assumptions |

**Step 2: Present the subject through outsider eyes**

Ask: "If [outsider persona] read this document, what would they question first?"

**Step 3: List "obvious" things that aren't**

> "They'd probably ask why we..."
> "They might not understand that..."
> "They'd challenge whether..."

**Step 4: Convert questions to assumptions**

Each outsider question reveals an insider assumption.

### Expected Yield

- 5-10 assumptions, often high-value
- Particularly good at finding "obvious" assumptions
- Different personas find different assumptions

### Example

**Subject:** "Product roadmap for enterprise CRM"

**Outsider persona:** New employee (Day 1)

**What would they question?**

| Outsider Question | Assumption Revealed |
|-------------------|---------------------|
| "Why do we assume enterprises will buy?" | A1: Enterprise sales motion is viable |
| "What makes us different from Salesforce?" | A2: Differentiation is clear and compelling |
| "How do we know the timeline is realistic?" | A3: Estimation methodology is reliable |
| "Who decided these features?" | A4: Prioritization reflects customer needs |
| "Why is security not on the roadmap?" | A5: Security is "table stakes" (implicit, not planned) |

**Assumptions surfaced:**
- A1: Enterprise sales motion is viable for our company (IMPLICIT, BEHAVIORAL)
- A2: Product differentiation is clear and compelling vs. incumbents (IMPLICIT, CONTEXTUAL)
- A3: Timeline estimates are reliable based on past performance (IMPLICIT)
- A4: Feature prioritization accurately reflects customer needs (IMPLICIT, BEHAVIORAL)
- A5: Security capabilities are sufficient without explicit work (IMPLICIT, STRUCTURAL)

---

## 5. Pre-mortem

### Purpose

Surface assumptions by imagining the plan has failed and reasoning backward to identify what went wrong.

### When to Use

- Critical for finding load-bearing assumptions
- Especially effective for strategies and major decisions
- Use when stakes are high

### Protocol

**Step 1: Set the scene**

State clearly:
> "It's [future date]. This [decision/strategy/plan] has failed completely. What happened?"

**Step 2: Brainstorm failure causes**

Generate failure scenarios without filtering:
- What went wrong internally?
- What changed externally?
- What did we miss?
- What assumption was catastrophically wrong?

**Step 3: Categorize failures**

Group by root cause:
- Assumption failures (something we believed that was wrong)
- Execution failures (we didn't do what we planned)
- External changes (the world changed)

**Step 4: Extract assumptions from each failure**

For each assumption failure, document:
- What was assumed?
- Why was it wrong?
- What would have validated it earlier?

### Expected Yield

- 5-12 assumptions, typically high-criticality
- Often identifies load-bearing assumptions
- Surfaces risks that optimism bias hides

### Example

**Subject:** "Launch new pricing tier by Q3"

**Pre-mortem:** "It's Q4. The new pricing tier launch failed. What happened?"

**Failure brainstorm:**

| Failure Scenario | Root Cause | Assumption Revealed |
|------------------|------------|---------------------|
| "Customers didn't adopt new tier" | Value proposition unclear | A1: Customers understand/want tiered value |
| "Sales couldn't explain it" | Sales enablement insufficient | A2: Sales can be trained in time |
| "Backend couldn't handle billing complexity" | Engineering underestimated | A3: Billing system supports tiered model |
| "Competitor matched our price" | Competitive response | A4: Competitors won't respond quickly |
| "Legal had compliance concerns" | Late legal review | A5: Pricing model is compliant |
| "Finance couldn't report accurately" | Revenue recognition complexity | A6: Finance systems handle new model |

**Load-bearing assumptions identified:**
- A3: Billing system supports tiered pricing (LOAD-BEARING, IMPLICIT)
- A5: Pricing model is legally/regulatory compliant (LOAD-BEARING, IMPLICIT)

---

## 6. Dependency Mapping

### Purpose

Visualize and trace what depends on what to identify load-bearing assumptions.

### When to Use

- When analyzing complex plans or architectures
- To identify single points of failure
- To understand assumption cascades

### Protocol

**Step 1: List key outcomes**

What are the success criteria or key deliverables?

**Step 2: For each outcome, ask "What does this depend on?"**

Trace dependencies recursively:
```
Outcome → Depends on → Which depends on → Which depends on...
```

**Step 3: Build dependency tree**

```
[Outcome]
    ├── [Dependency 1]
    │   ├── [Sub-dependency 1.1]
    │   │   └── [ASSUMPTION A1]
    │   └── [Sub-dependency 1.2]
    └── [Dependency 2]
        └── [ASSUMPTION A2]
```

**Step 4: Identify assumption nodes**

Mark nodes that are:
- Unverified beliefs (assumptions)
- External dependencies
- Single points of failure

**Step 5: Score for load-bearing**

Count how many outcomes depend on each assumption node.

### Expected Yield

- 3-8 assumption dependencies per major outcome
- Clear identification of load-bearing assumptions
- Visual representation of assumption cascade

### Example

**Subject:** "Successfully launch mobile app by Q2"

**Dependency map:**

```
[Q2 Mobile App Launch]
    ├── [Development complete by March]
    │   ├── [Engineering capacity available]
    │   │   └── A1: No competing priorities
    │   ├── [Technical design finalized]
    │   │   └── A2: Requirements are stable
    │   └── [Third-party SDK works]
    │       └── A3: Vendor delivers on time ← LOAD-BEARING
    ├── [App Store approval by April]
    │   ├── [Compliance requirements met]
    │   │   └── A4: We understand Apple guidelines
    │   └── [Review turnaround < 2 weeks]
    │       └── A5: No major policy changes
    └── [Marketing ready by launch]
        └── A6: Creative assets complete
```

**Load-bearing assumption:** A3 (vendor delivery) — all paths depend on it

---

## 7. Frame Questioning

### Purpose

Surface structural assumptions embedded in how the problem is framed.

### When to Use

- When problem definition seems too narrow
- When "obvious" solution exists (why is it obvious?)
- To escape groupthink on problem framing

### Protocol

**Step 1: Articulate the current frame**

> "The problem we're solving is: [description]"
> "The solution space we're exploring is: [category]"

**Step 2: Question the frame**

Ask:
> "Why did we frame this as [X] rather than [Y]?"
> "What would change if we framed it differently?"
> "Who framed it this way? What was their perspective?"

**Step 3: Generate alternative frames**

| Current Frame | Alternative Frame | What Changes |
|---------------|-------------------|--------------|
| [Current] | [Alternative 1] | [Implications] |
| [Current] | [Alternative 2] | [Implications] |

**Step 4: Extract structural assumptions**

The difference between frames reveals structural assumptions.

### Expected Yield

- 2-5 structural assumptions
- Often high-impact findings
- May challenge fundamental premises

### Example

**Current frame:** "How do we improve our mobile app's performance?"

**Step 2: Question the frame**
- Why "mobile app" and not "digital experience"?
- Why "improve" rather than "rebuild" or "replace"?
- Why "performance" and not "user satisfaction"?

**Step 3: Alternative frames**

| Current | Alternative | Structural Assumption |
|---------|-------------|----------------------|
| "Improve app" | "Rebuild from scratch" | A1: Current app is salvageable |
| "Mobile app" | "Cross-platform experience" | A2: Mobile is the right channel |
| "Performance" | "User value" | A3: Performance is the key issue |
| "Our app" | "Competitive landscape" | A4: Solution is internal, not buy/partner |

**Structural assumptions surfaced:**
- A1: Current mobile app architecture can be improved (not rebuilt) — STRUCTURAL
- A2: Mobile app is the right primary channel for users — STRUCTURAL
- A3: Performance (not features, UX, value) is the core problem — STRUCTURAL
- A4: Internal development (not acquisition/partnership) is the path — STRUCTURAL

---

## 8. Missing Voices

### Purpose

Identify whose perspective is absent, revealing stakeholder-related structural assumptions.

### When to Use

- When decision was made by a small group
- When certain stakeholders seem "obvious" to exclude
- To find blind spots from homogeneous perspectives

### Protocol

**Step 1: List who was consulted**

Who provided input to this decision/plan/strategy?

**Step 2: List who is affected**

Who will be impacted by this decision?

**Step 3: Identify the gap**

Who is affected but wasn't consulted?

**Step 4: Ask why they're missing**

For each missing voice:
> "Why wasn't [stakeholder] consulted?"
> "What would they say if asked?"
> "What do we assume about their perspective?"

**Step 5: Extract assumptions**

Each excluded perspective reveals an assumption about what matters.

### Expected Yield

- 2-4 structural assumptions
- Often reveals bias in decision-making
- Can surface significant blind spots

### Example

**Subject:** "New employee onboarding process redesign"

**Step 1: Who was consulted?**
- HR leadership
- HRBP team
- Training department

**Step 2: Who is affected?**
- New employees
- Hiring managers
- IT (equipment provisioning)
- Security (access provisioning)
- Buddy/mentor assignments
- Department leaders

**Step 3: Gap analysis**

| Affected | Consulted? | If No, Why? |
|----------|------------|-------------|
| New employees | No | "We know what they need" |
| Hiring managers | No | "Too busy to involve" |
| IT | No | "They just do provisioning" |
| Security | No | "Standard process" |

**Step 4: Extract assumptions**

- A1: HR knows new employee needs without asking them — STRUCTURAL, BEHAVIORAL
- A2: Hiring managers don't need input into onboarding — STRUCTURAL
- A3: IT provisioning is a solved problem — STRUCTURAL
- A4: Security access is standard and doesn't need review — STRUCTURAL

---

## 9. Scope Boundary Probe

### Purpose

Examine why certain things are in/out of scope, revealing scoping assumptions.

### When to Use

- When scope seems arbitrarily defined
- When "out of scope" is used without justification
- To challenge assumptions about boundaries

### Protocol

**Step 1: List what's explicitly in scope**

**Step 2: List what's explicitly out of scope**

**Step 3: For each out-of-scope item, ask:**
> "Why is this out of scope?"
> "What if it were in scope?"
> "Who decided this boundary?"

**Step 4: For each in-scope boundary, ask:**
> "Why stop here?"
> "What adjacent items were excluded?"
> "Is this boundary logical or arbitrary?"

**Step 5: Extract assumptions from boundaries**

### Expected Yield

- 2-6 structural assumptions
- Often reveals convenience-based scoping
- May identify critical missing scope

### Example

**Subject:** "Customer feedback system redesign"

**In scope:**
- Survey collection
- Response dashboard
- Basic reporting

**Out of scope:**
- Integration with CRM
- Sentiment analysis
- Action tracking
- Customer follow-up

**Scope probe:**

| Out of Scope | Why? | Assumption |
|--------------|------|------------|
| CRM integration | "Separate system" | A1: Feedback doesn't need customer context |
| Sentiment analysis | "Nice to have" | A2: Manual reading is sufficient |
| Action tracking | "Different team" | A3: Feedback → action is someone else's problem |
| Customer follow-up | "Not our scope" | A4: Closing the loop doesn't drive value |

**Structural assumptions surfaced:**
- A1: Feedback analysis doesn't require customer history — STRUCTURAL
- A2: Volume is low enough for manual sentiment reading — STRUCTURAL
- A3: Someone else will act on insights (diffusion of responsibility) — STRUCTURAL
- A4: Customers don't expect/value follow-up — STRUCTURAL, BEHAVIORAL

---

## 10. Fill-in-the-Blank

### Purpose

Clarify vague language that hides assumptions.

### When to Use

- When jargon or vague terms are used
- When "everyone knows" something
- To make implicit definitions explicit

### Protocol

**Step 1: Identify vague or jargon terms**

Look for:
- Undefined acronyms
- Industry jargon
- Vague quantifiers ("most," "many," "often")
- Assumed shared understanding

**Step 2: Ask for clarification**

> "When you say [term], you mean...?"
> "By [X], specifically you're referring to...?"
> "'Most users' — what percentage is that?"

**Step 3: Document the clarified meaning**

**Step 4: Note where clarification reveals assumption**

### Expected Yield

- 2-5 clarifications
- Often surfaces implicit definitions
- Reveals "obvious" things that aren't

### Example

**Subject:** "We'll use the standard approach for authentication."

**Fill-in-the-blank questions:**

| Vague Term | Clarification Question | Answer | Assumption Revealed |
|------------|----------------------|--------|---------------------|
| "Standard approach" | Which standard specifically? | "OAuth 2.0" | A1: OAuth 2.0 is appropriate for our use case |
| "Authentication" | Auth vs. authz? Just login? | "Just login, authz is separate" | A2: Authorization is already handled |
| "We'll use" | Build, buy, or configure? | "Configure existing IdP" | A3: We have an IdP that supports this |

---

## 11. Reverse Assumption

### Purpose

Test an assumption by explicitly considering its opposite.

### When to Use

- To validate individual assumptions
- When an assumption seems "obviously true"
- To stress-test key assumptions

### Protocol

**Step 1: State the assumption clearly**

> Assumption: "Users prefer mobile app over web."

**Step 2: State the opposite**

> Opposite: "Users prefer web over mobile app."

**Step 3: Generate evidence for the opposite**

> "What evidence would support the opposite being true?"

**Step 4: Assess plausibility**

> "How plausible is the opposite? What would change if it were true?"

**Step 5: Determine assumption strength**

- Strong assumption: Opposite is implausible
- Weak assumption: Opposite is plausible
- Invalid assumption: Opposite is likely true

### Expected Yield

- 1 validated/invalidated assumption per application
- Quick technique (5 minutes per assumption)
- Good for testing critical assumptions

### Example

**Assumption:** "Customers will pay a premium for our differentiated features."

**Opposite:** "Customers won't pay a premium for our differentiated features."

**Evidence for opposite:**
- Competitors offer similar features at lower price
- Customer research shows price sensitivity
- Feature differentiation is hard to communicate
- Switching costs are low

**Assessment:** Opposite is plausible → Assumption is WEAK → needs validation

---

## 12. PESTLE Scan

### Purpose

Systematically surface contextual assumptions about the external environment.

### When to Use

- For strategies with external dependencies
- When market/regulatory/economic factors matter
- To ensure comprehensive environmental coverage

### Protocol

**Step 1: Review each PESTLE dimension**

| Dimension | Focus Areas |
|-----------|-------------|
| **P**olitical | Government policy, trade, stability |
| **E**conomic | Growth, interest rates, exchange rates, inflation |
| **S**ocial | Demographics, culture, trends, behavior |
| **T**echnological | Innovation, standards, disruption |
| **L**egal | Regulations, compliance, litigation |
| **E**nvironmental | Climate, sustainability, resources |

**Step 2: For each dimension, ask:**

> "What external factors in [dimension] does this plan depend on?"
> "What are we assuming about [dimension]?"
> "What changes in [dimension] would invalidate this?"

**Step 3: Document contextual assumptions**

**Step 4: Assess volatility**

Rate each assumption's stability: HIGH | MEDIUM | LOW

### Expected Yield

- 5-15 contextual assumptions
- Comprehensive external coverage
- Good for strategies and long-term plans

### Example

**Subject:** "Expand to Southeast Asian markets"

**PESTLE scan:**

| Dimension | Contextual Assumption | Volatility |
|-----------|----------------------|------------|
| Political | A1: Trade policies remain favorable | Medium |
| Political | A2: No major political instability | Medium |
| Economic | A3: USD/local currency stable | High |
| Economic | A4: Middle class continues growing | Low |
| Social | A5: Consumer preferences match product | Medium |
| Technology | A6: Mobile infrastructure supports app | Low |
| Legal | A7: Data localization requirements manageable | Medium |
| Legal | A8: No major regulatory changes | Medium |
| Environmental | A9: Supply chain not disrupted by climate | High |

---

## Technique Combination Strategies

### Standard Combination (4 techniques)

```
Document Scan → Inversion → Pre-mortem → Frame Questioning
```

1. Start with explicit assumptions (Document Scan)
2. Surface implicit assumptions (Inversion)
3. Find load-bearing assumptions (Pre-mortem)
4. Check structural assumptions (Frame Questioning)

### Rigorous Combination (All techniques)

```
Pass 1: Document Scan + Five Whys + Outsider Test
Pass 2: Inversion + Pre-mortem + Dependency Mapping
Pass 3: Frame Questioning + Missing Voices + Scope Boundary
Pass 4: Reverse Assumption on top findings + PESTLE Scan
```

### Quick Validation (2 techniques)

```
Document Scan → Inversion
```

For time-constrained situations, these two provide best coverage.

---

## Cross-Reference

| Technique | Assumption Types Best For | See Also |
|-----------|---------------------------|----------|
| Document Scan | EXPLICIT | `assumption-taxonomy.md` §1 |
| Inversion | IMPLICIT | `assumption-taxonomy.md` §2 |
| Five Whys | IMPLICIT | `assumption-taxonomy.md` §2 |
| Outsider Test | IMPLICIT | `assumption-taxonomy.md` §2 |
| Pre-mortem | LOAD-BEARING | `assumption-taxonomy.md` §4 |
| Dependency Mapping | LOAD-BEARING | `load-bearing-analysis.md` |
| Frame Questioning | STRUCTURAL | `assumption-taxonomy.md` §3 |
| Missing Voices | STRUCTURAL | `assumption-taxonomy.md` §3 |
| Scope Boundary Probe | STRUCTURAL | `assumption-taxonomy.md` §3 |
| Fill-in-the-Blank | IMPLICIT | — |
| Reverse Assumption | ALL | `validation-methods.md` |
| PESTLE Scan | CONTEXTUAL | `assumption-taxonomy.md` §5 |
