# Assumption Taxonomy

A comprehensive classification system for identifying, categorizing, and understanding different types of assumptions in decisions, strategies, plans, and architectures.

---

## Overview

### The Six Assumption Types

| Type | Definition | Visibility | Risk Level | Detection Difficulty |
|------|------------|------------|------------|---------------------|
| **EXPLICIT** | Directly stated in subject document | High | Low | Easy |
| **IMPLICIT** | Required for conclusions but unstated | Medium | Medium | Moderate |
| **STRUCTURAL** | Embedded in problem framing | Low | High | Hard |
| **LOAD-BEARING** | Collapse point if wrong | Variable | Critical | Moderate |
| **CONTEXTUAL** | About environment/conditions | Medium | Variable | Easy |
| **BEHAVIORAL** | About human/system actions | Medium | Medium-High | Moderate |

### Type Relationships

```
                    ┌─────────────┐
                    │  EXPLICIT   │  ← Visible, acknowledged
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │  IMPLICIT   │  ← Hidden in reasoning
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │ STRUCTURAL  │  ← Embedded in framing
                    └─────────────┘

Any of the above can also be:

┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  LOAD-BEARING   │     │   CONTEXTUAL    │     │   BEHAVIORAL    │
│ (critical dep)  │     │  (environment)  │     │ (human/system)  │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

An assumption can have multiple types. For example, an implicit assumption about market conditions is both IMPLICIT and CONTEXTUAL.

---

## 1. EXPLICIT Assumptions

### Definition

Assumptions that are directly stated, acknowledged, or documented in the subject material. The author consciously recognizes these as assumptions.

### Characteristics

- **Visibility:** High — appears in text, documentation, or is verbally stated
- **Awareness:** Author knows it's an assumption
- **Documentation:** Often found in formal "Assumptions" sections
- **Risk:** Low (because acknowledged) — but not zero

### Detection Heuristics

#### Linguistic Markers

| Marker Pattern | Example |
|---------------|---------|
| "We assume..." | "We assume budget approval by Q2" |
| "Given that..." | "Given that market conditions remain stable" |
| "Assuming..." | "Assuming the API maintains backward compatibility" |
| "This depends on..." | "This depends on vendor delivery by March" |
| "If [condition]..." | "If interest rates stay below 5%" |
| "We're betting that..." | "We're betting that competitors won't react" |
| "Our hypothesis is..." | "Our hypothesis is that users want simplicity" |
| "Predicated on..." | "Success is predicated on team availability" |
| "Contingent upon..." | "Timeline is contingent upon approvals" |

#### Document Locations

| Location | Likelihood |
|----------|------------|
| "Assumptions" section header | Very High |
| Executive summary caveats | High |
| Footnotes and endnotes | High |
| Risk register "assumptions" column | High |
| Appendix disclaimers | Medium |
| Inline parenthetical notes | Medium |

### Common Hiding Places by Domain

| Domain | Where to Look |
|--------|---------------|
| **Business case** | Financial projections, market sizing, growth rates |
| **Technical spec** | Performance requirements, scalability targets, integration points |
| **Project plan** | Resource availability, timeline estimates, dependencies |
| **Strategy doc** | Market assumptions, competitive dynamics, customer behavior |
| **Architecture** | Non-functional requirements, technology choices, constraints |

### Examples by Context

#### Decision Context
> "This business case assumes 15% year-over-year revenue growth."
>
> - **Type:** EXPLICIT (stated directly)
> - **Domain:** Financial projection
> - **Validation need:** Check against historical data, market trends

#### Strategy Context
> "We assume our competitor will not enter the SMB market for 18 months."
>
> - **Type:** EXPLICIT (stated directly)
> - **Domain:** Competitive dynamics
> - **Validation need:** Competitive intelligence, market signals

#### Architecture Context
> "This design assumes PostgreSQL can handle 10,000 transactions per second."
>
> - **Type:** EXPLICIT (stated directly)
> - **Domain:** Technical capability
> - **Validation need:** Benchmarking, vendor specifications

### Surfacing Techniques

| Technique | Protocol |
|-----------|----------|
| **Document scan** | Text search for assumption markers (above) |
| **Section review** | Read "Assumptions" and "Constraints" sections |
| **Footnote mining** | Check all footnotes and appendices |
| **Author interview** | "What assumptions did you document?" |

### Validation Protocol

When an explicit assumption is found:

1. **Document verbatim** — Capture exact wording
2. **Note source** — Page, section, speaker
3. **Confirm scope** — "When you say X, does that include Y?"
4. **Test importance** — "What would change if this were wrong?"
5. **Check evidence** — "What supports this assumption?"
6. **Identify owner** — "Who can validate this?"

---

## 2. IMPLICIT Assumptions

### Definition

Assumptions that are required for conclusions to hold but are never stated. They exist in the reasoning chain but aren't articulated. The author may or may not be aware of them.

### Characteristics

- **Visibility:** Medium — not stated, but can be inferred
- **Awareness:** Author often unaware
- **Detection:** Requires probing the reasoning chain
- **Risk:** Medium — can be surfaced with effort

### Detection Heuristics

#### Reasoning Signals

| Signal | What It Suggests | Example |
|--------|------------------|---------|
| **Certainty language** | Unexamined assumption | "Obviously we need real-time updates" |
| **Embedded causation** | Causal assumption | "Because users want X, we should build Y" |
| **Omission** | Assumption by absence | No mention of mobile → desktop-first assumed |
| **Undefined jargon** | Shared understanding assumed | "We'll use the standard approach" |
| **Time references** | Timeline assumptions | "When this launches..." assumes launch happens |
| **Quantification without source** | Data assumption | "Most users prefer..." — based on what? |
| **Universal claims** | Generalization assumption | "Everyone knows that..." |

#### Question Patterns That Reveal Implicit Assumptions

| Question | What It Surfaces |
|----------|------------------|
| "What would have to be true for that to work?" | Necessary conditions |
| "Why do you believe that?" | Reasoning foundation |
| "What if the opposite were true?" | Hidden dependency |
| "How do you know?" | Evidence assumption |
| "What are you taking for granted?" | Unconscious beliefs |

### Common Hiding Places by Domain

| Domain | Common Implicit Assumptions |
|--------|----------------------------|
| **Product** | Users will understand value; users will adopt; users have time/motivation |
| **Technical** | System will perform; integration will work; data will be available |
| **Organizational** | People will cooperate; resources will be available; skills exist |
| **Market** | Demand exists; pricing works; channels are effective |
| **Timeline** | Tasks are well-estimated; dependencies are understood; no blockers |

### Examples by Context

#### Product Decision
> **Stated:** "Users will migrate to the new workflow."
>
> **Implicit assumptions:**
> - Users have time to learn new workflow
> - New workflow is better enough to justify switching cost
> - Training/support will be sufficient
> - No regulatory/compliance barriers to change

#### Technical Architecture
> **Stated:** "We'll use microservices for scalability."
>
> **Implicit assumptions:**
> - Team has microservices expertise
> - Operational complexity is manageable
> - Service boundaries are well-understood
> - Deployment infrastructure exists

#### Strategy
> **Stated:** "We'll expand to three new markets next year."
>
> **Implicit assumptions:**
> - Capital is available for expansion
> - Existing product translates to new markets
> - Regulatory compliance is achievable
> - Leadership bandwidth exists

### Surfacing Techniques

| Technique | Protocol | Typical Yield |
|-----------|----------|---------------|
| **Inversion** | "What would have to be true for this to fail?" | 5-15 assumptions |
| **Five Whys** | Drill into reasoning chain, asking "Why?" | 3-8 per chain |
| **Outsider Test** | "What would a skeptic question first?" | 5-10 assumptions |
| **Fill-in-the-Blank** | "When you say X, you mean...?" | 2-5 clarifications |
| **Reverse Assumption** | "What if [opposite] were true?" | 1 per assumption |

**See:** `surfacing-techniques.md` for detailed protocols.

### Validation Protocol

When an implicit assumption is surfaced:

1. **Articulate clearly** — Convert to explicit statement
2. **Confirm interpretation** — "Is this what you're assuming?"
3. **Document as explicit** — Add to assumption inventory
4. **Assess importance** — Load-bearing analysis
5. **Validate if critical** — Evidence check, counterfactual

---

## 3. STRUCTURAL Assumptions

### Definition

Assumptions embedded in how the problem is framed — what's in scope, how concepts are defined, which perspectives are included. These shape what questions get asked and what answers seem relevant.

### Characteristics

- **Visibility:** Low — invisible to those inside the frame
- **Awareness:** Rarely conscious; "just how we think about it"
- **Detection:** Requires stepping outside the frame
- **Risk:** High — often only visible in hindsight

### Detection Heuristics

#### Frame Indicators

| Indicator | Structural Assumption |
|-----------|----------------------|
| Single user type focus | Other users don't matter |
| Technical-only framing | Organizational factors irrelevant |
| Current state focus | Future evolution not important |
| Success metrics undefined | "We agree on what good means" |
| Stakeholder list missing | "We know who matters" |
| Problem defined as X | X is the right problem frame |
| Solution category chosen | This is the right category |

#### Questions That Reveal Frame

| Question | What It Exposes |
|----------|-----------------|
| "Why did we frame this as X instead of Y?" | Problem definition |
| "Whose perspective isn't represented?" | Stakeholder scope |
| "What did we decide not to consider?" | Intentional exclusions |
| "What dimensions aren't we measuring?" | Metric assumptions |
| "Why is this the right level of analysis?" | Abstraction level |

### Common Hiding Places by Domain

| Domain | Structural Assumptions Hidden In |
|--------|----------------------------------|
| **Strategy** | Market definition, competitive set, time horizon |
| **Product** | User persona scope, problem definition, success metrics |
| **Architecture** | System boundaries, technology paradigm, quality attributes |
| **Research** | Interview subjects, question framing, analysis method |
| **Finance** | Projection period, discount rate, comparable selection |

### Examples by Context

#### Product Problem Frame
> **Frame:** "How do we improve our mobile app?"
>
> **Structural assumptions:**
> - Mobile app is the right solution channel
> - Problem is app quality, not product-market fit
> - Current app architecture is salvageable
> - Users want app improvements (vs. different solution)

#### Technical Architecture Frame
> **Frame:** "Which cloud provider should we choose?"
>
> **Structural assumptions:**
> - Cloud is the right infrastructure model
> - Single provider (vs. multi-cloud)
> - "Provider" means hyperscaler (vs. specialized)
> - Migration is feasible

#### Research Frame
> **Frame:** "We interviewed the product manager to understand requirements."
>
> **Structural assumptions:**
> - PM has complete knowledge of requirements
> - PM perspective is sufficient
> - PM's framing is correct
> - Requirements can be known upfront

### Surfacing Techniques

| Technique | Protocol | Typical Yield |
|-----------|----------|---------------|
| **Frame Questioning** | "Why this frame, not another?" | 2-5 assumptions |
| **Missing Voices** | "Whose perspective is absent?" | 2-4 assumptions |
| **Alternative Structures** | "What if we organized around different dimensions?" | 2-4 assumptions |
| **Scope Boundary Probe** | "Why is X out of scope? What if it weren't?" | 2-6 assumptions |
| **Problem Ladder** | "Is this the right problem? What's the problem behind the problem?" | 1-3 assumptions |

**See:** `surfacing-techniques.md` for detailed protocols.

### Validation Protocol

Structural assumptions are rarely "validated" in the traditional sense. Instead:

1. **Make visible** — Articulate the frame explicitly
2. **Explore alternatives** — What would change with different frame?
3. **Assess consequences** — What do we miss with this frame?
4. **Document consciously** — Record frame choice and rationale
5. **Monitor for frame failure** — Watch for signs frame is wrong

---

## 4. LOAD-BEARING Assumptions

### Definition

Assumptions where failure causes disproportionate damage — if wrong, the entire decision, plan, or strategy collapses. These are single points of failure in the assumption architecture.

### Characteristics

- **Visibility:** Variable — can be explicit, implicit, or structural
- **Dependency:** High — many other things depend on this
- **Reversibility:** Low — hard to recover if wrong
- **Risk:** Critical — the stakes are high

### Detection Heuristics

#### Dependency Signals

| Signal | Load-Bearing Indicator |
|--------|------------------------|
| "Everything depends on X" | Direct statement of dependency |
| Single supplier/partner/resource | Concentration risk |
| Timeline critical path item | No slack if wrong |
| Foundational technical choice | Architecture depends on it |
| Core market assumption | Business model depends on it |

#### Questions That Identify Load-Bearing Assumptions

| Question | What It Finds |
|----------|---------------|
| "What would cause total failure?" | Critical failure points |
| "If X is wrong, what still works?" | Dependency mapping |
| "What's on the critical path?" | Timeline dependencies |
| "What's our single biggest bet?" | Concentrated risk |
| "What can't we change later?" | Irreversibility |

### Common Hiding Places by Domain

| Domain | Typical Load-Bearing Assumptions |
|--------|----------------------------------|
| **Startup** | Product-market fit; funding availability; team capability |
| **M&A** | Synergy realization; integration feasibility; retention |
| **Product** | User adoption; technical feasibility; competitive advantage |
| **Architecture** | Technology scalability; vendor viability; security model |
| **Strategy** | Market growth; competitive response; execution capability |

### Examples by Context

#### Strategy Load-Bearing
> "Success depends on competitor not reacting for 18 months."
>
> - **Why load-bearing:** Entire competitive positioning depends on it
> - **If wrong:** First-mover advantage lost; pricing pressure; strategy fails
> - **Validation priority:** CRITICAL — validate before commitment

#### Technical Load-Bearing
> "The system will handle 100K concurrent users."
>
> - **Why load-bearing:** Business case depends on this scale
> - **If wrong:** Revenue projections fail; refactoring required; credibility lost
> - **Validation priority:** CRITICAL — benchmark before launch

#### Organizational Load-Bearing
> "The acquired team will stay through integration."
>
> - **Why load-bearing:** Knowledge transfer depends on retention
> - **If wrong:** Acquisition value destroyed; capability gap; timeline slip
> - **Validation priority:** CRITICAL — retention agreements before close

### Identification Framework

Use load-bearing analysis scoring:

```
Priority = (Dependency × (1 - Confidence)) / Validation Cost
```

Assumptions with Priority > 3.0 are typically load-bearing.

**See:** `load-bearing-analysis.md` for detailed scoring framework.

### Validation Protocol

Load-bearing assumptions require special attention:

1. **Confirm load-bearing status** — Verify dependency and reversibility
2. **Prioritize validation** — These get validated first
3. **Multiple validation methods** — Don't rely on single method
4. **Contingency planning** — What if it's wrong?
5. **Monitoring** — Ongoing validation even after initial check
6. **Escalation path** — Who needs to know if this changes?

---

## 5. CONTEXTUAL Assumptions

### Definition

Assumptions about the external environment, market conditions, regulatory landscape, technology trends, or other factors outside the organization's direct control.

### Characteristics

- **Visibility:** Medium — often stated but not examined
- **Stability:** Variable — can change without warning
- **Control:** Low — organization cannot influence
- **Risk:** Variable — depends on volatility of context

### Detection Heuristics

#### Context Categories

| Category | Examples |
|----------|----------|
| **Market** | Demand, pricing, competition, growth |
| **Regulatory** | Laws, compliance, standards, enforcement |
| **Economic** | Interest rates, inflation, exchange rates, GDP |
| **Technology** | Standards, platforms, vendor viability |
| **Social** | User behavior, preferences, demographics |
| **Political** | Policy, trade, geopolitical |

#### Questions That Surface Contextual Assumptions

| Question | What It Finds |
|----------|---------------|
| "What external factors is this based on?" | Environmental dependencies |
| "What market conditions are assumed?" | Market assumptions |
| "What regulatory requirements apply?" | Compliance assumptions |
| "What technology trends are assumed?" | Technology assumptions |
| "What's assumed about the economy?" | Economic assumptions |

### Common Hiding Places by Domain

| Domain | Contextual Assumptions Often Hidden In |
|--------|----------------------------------------|
| **Financial projections** | Growth rates, market size, pricing power |
| **Go-to-market** | Channel effectiveness, buyer behavior, sales cycles |
| **Technology roadmap** | Platform stability, vendor roadmaps, standards evolution |
| **Compliance** | Regulatory stability, enforcement patterns |
| **International** | Exchange rates, trade policy, cultural factors |

### Examples by Context

#### Market Contextual
> "The addressable market is $5B and growing 20% annually."
>
> - **Context dependency:** Industry analyst projections
> - **Volatility:** Medium — market conditions change
> - **Validation:** Cross-check sources; primary research

#### Regulatory Contextual
> "No new data privacy regulations expected in this jurisdiction."
>
> - **Context dependency:** Regulatory landscape stability
> - **Volatility:** High — regulations can change quickly
> - **Validation:** Regulatory tracking; legal counsel

#### Technology Contextual
> "Kubernetes will remain the container orchestration standard."
>
> - **Context dependency:** Technology ecosystem evolution
> - **Volatility:** Low-Medium — standards shift slowly
> - **Validation:** Industry trends; vendor commitments

### Surfacing Techniques

| Technique | Protocol | Typical Yield |
|-----------|----------|---------------|
| **PESTLE Scan** | Systematic review of Political, Economic, Social, Technology, Legal, Environmental factors | 5-15 assumptions |
| **Time Decay Test** | "Will this still be true in 1/3/5 years?" | 2-5 time-sensitive assumptions |
| **External Dependency Audit** | List all external factors success depends on | 5-10 assumptions |
| **Black Swan Exercise** | "What external event would invalidate this?" | 3-7 vulnerability points |

### Validation Protocol

Contextual assumptions require external validation:

1. **Identify sources** — Who knows about this context?
2. **Cross-reference** — Multiple independent sources
3. **Assess volatility** — How stable is this context?
4. **Set monitoring** — Ongoing tracking for changes
5. **Build contingencies** — What if context changes?
6. **Time-bound** — When does this assumption expire?

---

## 6. BEHAVIORAL Assumptions

### Definition

Assumptions about how people, teams, organizations, or systems will act, respond, or behave. Often the most optimistic and the most frequently wrong.

### Characteristics

- **Visibility:** Medium — often implicit
- **Optimism bias:** High — we tend to assume best case
- **Predictability:** Low — humans are unpredictable
- **Risk:** Medium-High — behavior frequently surprises

### Detection Heuristics

#### Behavioral Subjects

| Subject | Common Behavioral Assumptions |
|---------|------------------------------|
| **Customers** | Will adopt; will pay; will be satisfied; will recommend |
| **Employees** | Will perform; will stay; will adapt; will collaborate |
| **Partners** | Will deliver; will cooperate; will share; will prioritize |
| **Competitors** | Will not react; will be slow; will make mistakes |
| **Regulators** | Will approve; will be reasonable; will be predictable |
| **Technology** | Will work; will scale; will integrate; will be secure |

#### Questions That Surface Behavioral Assumptions

| Question | What It Finds |
|----------|---------------|
| "Why would they do that?" | Motivation assumptions |
| "What incentives are at play?" | Incentive alignment |
| "Have they done this before?" | Behavioral precedent |
| "What could cause them to act differently?" | Behavioral triggers |
| "What's in it for them?" | Self-interest analysis |

### Common Hiding Places by Domain

| Domain | Behavioral Assumptions Often Hidden In |
|--------|----------------------------------------|
| **Product** | User adoption, engagement, retention, referral |
| **Sales** | Buyer behavior, sales cycle, win rate |
| **Operations** | Team velocity, quality, collaboration |
| **Change management** | Adoption curve, resistance, champions |
| **Partnerships** | Cooperation, priority, resource commitment |

### Examples by Context

#### User Behavioral
> "Users will complete the onboarding flow."
>
> **Implicit behavioral assumptions:**
> - Users have motivation to complete
> - Onboarding is understandable
> - Users have time/attention
> - Value is clear enough to persist

#### Organizational Behavioral
> "Engineering will adopt the new development practices."
>
> **Implicit behavioral assumptions:**
> - Engineers see value in practices
> - Management will support transition time
> - Champions will emerge
> - Resistance will be manageable

#### Competitive Behavioral
> "Competitors won't match our pricing for 6 months."
>
> **Implicit behavioral assumptions:**
> - Competitors are slow to react
> - Competitors have higher cost structure
> - Competitors don't see us as threat
> - Price wars aren't in competitor interest

### Surfacing Techniques

| Technique | Protocol | Typical Yield |
|-----------|----------|---------------|
| **Stakeholder Modeling** | Map each stakeholder's incentives and constraints | 3-8 assumptions per stakeholder |
| **Incentive Analysis** | "What incentives drive this behavior?" | 2-5 misalignment points |
| **Historical Behavior** | "Have they acted this way before?" | Precedent-based validation |
| **Failure Mode Analysis** | "How could people fail to do what we expect?" | 3-7 failure modes |
| **Devil's Advocate** | Argue against expected behavior | 2-5 counterarguments |

### Validation Protocol

Behavioral assumptions require special caution:

1. **Assume optimism bias** — Adjust for overconfidence
2. **Check precedent** — Have they behaved this way before?
3. **Analyze incentives** — Are incentives aligned with expected behavior?
4. **Consider constraints** — What might prevent expected behavior?
5. **Build in verification** — How will we know if behavior matches?
6. **Plan for deviation** — What if behavior differs?

---

## Detection Quick Reference

### By Assumption Type

| Type | Primary Detection Method | Key Question |
|------|--------------------------|--------------|
| EXPLICIT | Document scan | "What does the document say we're assuming?" |
| IMPLICIT | Inversion, Five Whys | "What would have to be true for this to work?" |
| STRUCTURAL | Frame questioning | "Why did we frame it this way?" |
| LOAD-BEARING | Dependency mapping | "What happens if this is wrong?" |
| CONTEXTUAL | PESTLE scan | "What external factors is this based on?" |
| BEHAVIORAL | Stakeholder modeling | "Why would they do that?" |

### Red Flags by Type

| Type | Red Flag | Action |
|------|----------|--------|
| EXPLICIT | "Assumptions" section empty | Ask what was assumed |
| IMPLICIT | High certainty, no evidence | Apply inversion |
| STRUCTURAL | Single perspective | Seek missing voices |
| LOAD-BEARING | "Everything depends on X" | Validate immediately |
| CONTEXTUAL | Stale data | Check current conditions |
| BEHAVIORAL | "They will definitely..." | Check incentives |

### Cross-Reference to Techniques

**See:** `surfacing-techniques.md` for full technique protocols.

| Assumption Type | Recommended Techniques |
|-----------------|------------------------|
| EXPLICIT | Document scan, Author interview |
| IMPLICIT | Inversion, Five Whys, Outsider test |
| STRUCTURAL | Frame questioning, Missing voices, Scope boundary probe |
| LOAD-BEARING | Dependency mapping, Pre-mortem, Failure mode analysis |
| CONTEXTUAL | PESTLE scan, Time decay test, External dependency audit |
| BEHAVIORAL | Stakeholder modeling, Incentive analysis, Historical behavior |
