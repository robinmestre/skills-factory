# Red Team Techniques

> Systematic approaches for generating substantive, steel-manned attacks.

This document provides 8 attack generation techniques with step-by-step protocols. Use these to ensure Red Team attacks are substantive, creative, and genuinely challenging—not strawmen or trivial objections.

---

## Overview

| # | Technique | Best For | Expected Yield |
|---|-----------|----------|----------------|
| 1 | Pre-mortem Attack | All propositions | 3-5 attacks |
| 2 | Inversion Attack | Strategy, Decision | 2-4 attacks |
| 3 | Black Hat Thinking | Security, Competitive | 3-5 attacks |
| 4 | Competitor Simulation | Strategy, Investment | 2-3 attacks |
| 5 | Historical Pattern Matching | All (with experience pool) | 2-4 attacks |
| 6 | Devil's Advocate Protocol | Policy, Decision | 2-3 attacks |
| 7 | Stress Test Amplification | Architecture, Plan | 2-4 attacks |
| 8 | Blind Spot Hunter | All propositions | 1-3 attacks |

---

## 1. Pre-mortem Attack

**Definition:** Assume the proposition has failed catastrophically. Work backward to identify what went wrong.

**Best For:** All proposition types, especially plans and strategies

**Cognitive Basis:** Hindsight bias reversal—easier to explain failure than prevent it

### Protocol

**Step 1: Set the scene**
```
"It is [future date]. The [proposition] has failed completely.
The project was cancelled / the strategy failed / the architecture collapsed.
Everyone agrees it was a disaster."
```

**Step 2: Generate failure narratives**
Answer: "What went wrong?" Generate 3-5 distinct failure stories:
- "The technical approach was fundamentally flawed because..."
- "The market didn't respond as expected because..."
- "The team couldn't execute because..."
- "External factors intervened when..."
- "A hidden assumption proved false when..."

**Step 3: Extract attacks**
For each failure narrative, formulate as an attack:
```
"The proposition will fail because [failure mechanism] when [trigger condition]."
```

**Step 4: Steel-man each attack**
Apply steel-manning protocol to strengthen each attack.

### Example

**Proposition:** "Launch AI-powered customer service chatbot in Q3"

**Pre-mortem scene:** "It's January next year. The chatbot project was cancelled after launch. Customer satisfaction dropped 15 points. The CEO called it a 'humiliating failure.'"

**Failure narratives:**
1. "Customers hated the bot because it couldn't handle their actual questions, only the questions we trained it on."
2. "The AI hallucinated incorrect information about our return policy, leading to $200K in unnecessary refunds."
3. "Call center staff actively sabotaged the bot by telling customers 'just say agent' to bypass it."
4. "A viral social media post mocked our bot's responses, damaging brand reputation."

**Extracted attacks:**
- ATK: "Training data doesn't cover real customer inquiries; bot will frustrate users"
- ATK: "AI hallucination risk with policy information; financial and brand damage"
- ATK: "Call center staff have incentive to undermine bot; adoption will fail"
- ATK: "Social media amplification of failures; reputational risk"

### Quality Criteria

- [ ] Failure is specific and plausible
- [ ] Failure mechanism is clear
- [ ] Attack is actionable (Blue Team can respond)
- [ ] Attack is not redundant with others

### Common Mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| Vague failures | "It just didn't work" | Specify mechanism |
| Implausible scenarios | "Asteroid hits data center" | Keep realistic |
| External-only failures | "Economy crashed" | Include internal failures |
| Single failure mode | Only technical failures | Diversify categories |

---

## 2. Inversion Attack

**Definition:** Ask "What would guarantee failure?" then check if those conditions exist or could arise.

**Best For:** Strategy, decision validation

**Cognitive Basis:** Via negativa—defining what to avoid clarifies the path

### Protocol

**Step 1: Invert the goal**
```
"If we WANTED this [proposition] to fail, what would we do?"
"What conditions would GUARANTEE failure?"
```

**Step 2: List failure guarantors**
Generate conditions that would ensure failure:
- "We would fail if we [action/condition]..."
- "Guaranteed failure requires [specific circumstance]..."
- "The proposition cannot survive [threat]..."

**Step 3: Check for presence**
For each failure guarantor, assess:
- Is this condition present today?
- Could this condition arise?
- How likely is this condition?

**Step 4: Formulate attacks**
For present or likely conditions:
```
"[Failure guarantor] exists/is likely. The proposition will fail because..."
```

### Example

**Proposition:** "Migrate to microservices architecture"

**Inversion:** "If we wanted this migration to fail, what would we do?"

**Failure guarantors:**
1. "We'd start without understanding our domain boundaries"
2. "We'd have a team with no distributed systems experience"
3. "We'd try to migrate everything at once instead of incrementally"
4. "We'd skip observability investment and debug blindly"
5. "We'd ignore data consistency requirements"

**Present condition check:**
- Domain boundaries: Not documented → PRESENT
- Team experience: 0 production microservices experience → PRESENT
- Migration approach: Unclear → AT RISK
- Observability: No distributed tracing → PRESENT

**Attacks:**
- ATK: "Domain boundaries are undefined; service splits will be wrong"
- ATK: "Team has no distributed systems experience; common pitfalls guaranteed"
- ATK: "No observability; failures will be undebuggable"

### Quality Criteria

- [ ] Failure guarantors are specific
- [ ] Presence/likelihood assessed honestly
- [ ] Attacks focus on present or likely conditions

---

## 3. Black Hat Thinking

**Definition:** Adopt a purely adversarial mindset. What would a malicious actor, saboteur, or determined opponent do?

**Best For:** Security review, competitive analysis

**Cognitive Basis:** Red team methodology from military/security domains

### Protocol

**Step 1: Adopt adversary persona**
```
"I am [adversary type] who wants to destroy this proposition."
```

Adversary types:
- **Competitor:** Wants your proposition to fail in market
- **Attacker:** Wants to exploit vulnerabilities
- **Saboteur:** Wants to undermine from within
- **Critic:** Wants to discredit publicly
- **Regulator:** Wants to find compliance violations

**Step 2: Map attack surface**
From adversary perspective:
- "What are the weakest points I could attack?"
- "What information would I need to cause maximum damage?"
- "What actions would be hardest to detect?"
- "What timing would maximize impact?"

**Step 3: Plan attacks**
Generate specific attack plans:
```
"As [adversary], I would attack by [method] targeting [weakness]
because [rationale]. This would cause [impact]."
```

**Step 4: Assess feasibility**
For each attack:
- How difficult to execute?
- How likely to be attempted?
- How damaging if successful?

### Example

**Proposition:** "Launch new pricing tier for enterprise customers"

**Adversary: Competitor**

**Attack surface mapping:**
- Pricing transparency (can study and undercut)
- Sales team incentives (can poach reps)
- Enterprise relationships (can counter-sell)
- Feature gaps (can highlight weaknesses)

**Attack plans:**
- "As competitor, I would immediately match pricing minus 10% for any deal in progress"
- "As competitor, I would recruit their enterprise sales lead with 2x comp"
- "As competitor, I would publish comparison showing feature gaps"

**Attacks:**
- ATK: "Competitor will price-match and undercut; first-mover advantage is 3 months max"
- ATK: "Key sales personnel are poach targets; relationship continuity at risk"
- ATK: "Feature gaps will be weaponized in competitive deals"

### Quality Criteria

- [ ] Adversary persona is realistic
- [ ] Attacks are within adversary's capability
- [ ] Impact assessment is honest

---

## 4. Competitor Simulation

**Definition:** Role-play as specific competitors and predict their response to your proposition.

**Best For:** Strategy, go-to-market, competitive positioning

**Cognitive Basis:** War gaming, competitive intelligence methodology

### Protocol

**Step 1: Identify key competitors**
List 2-3 competitors most relevant to proposition:
- Direct competitors (same market, same solution)
- Indirect competitors (same market, different solution)
- Potential entrants (adjacent market, could enter)

**Step 2: Build competitor profiles**
For each competitor:
```
Name: [Competitor]
Resources: [Team size, funding, tech capability]
Strategy: [Current positioning, recent moves]
Motivations: [What do they optimize for?]
Constraints: [What limits their response?]
```

**Step 3: Simulate response**
For each competitor, predict:
- "When they see [proposition], they will think..."
- "Their most likely response is..."
- "Timeline for response: [estimate]"
- "Their response would impact us by..."

**Step 4: Formulate attacks**
```
"[Competitor] will respond with [action] within [timeline],
which will [impact] our proposition because [mechanism]."
```

### Example

**Proposition:** "Launch freemium tier to capture SMB market"

**Competitor 1: Established Incumbent**
- Resources: $100M ARR, 500 engineers, enterprise focus
- Strategy: Premium positioning, high-touch sales
- Motivation: Protect enterprise margins, grow new segments
- Constraints: Brand dilution concerns, sales incentive structure

**Simulated response:**
"They'll likely do nothing for 6 months (enterprise focus), then launch 'lite' tier if we gain traction. Their sales team will dismiss freemium as 'not serious.' However, if we start winning mid-market, they'll respond aggressively with bundled pricing."

**Competitor 2: VC-Funded Upstart**
- Resources: $50M funding, 80 engineers, growth focus
- Strategy: Land-and-expand, product-led growth
- Motivation: User growth metrics for Series C
- Constraints: Burn rate, need to show path to monetization

**Simulated response:**
"They'll match freemium immediately. They can sustain losses longer than us. They'll likely undercut on paid tiers too. This becomes a war of attrition."

**Attacks:**
- ATK: "VC-funded competitor will match freemium and sustain losses; we'll be outspent"
- ATK: "If we gain mid-market traction, incumbent will bundle aggressively"

### Quality Criteria

- [ ] Competitor profiles are evidence-based
- [ ] Response predictions are plausible
- [ ] Timeline estimates are realistic

---

## 5. Historical Pattern Matching

**Definition:** Search for historical precedents where similar propositions failed. Apply those failure patterns.

**Best For:** All propositions, especially when experience pool is loaded

**Cognitive Basis:** Learning from history, pattern recognition

### Protocol

**Step 1: Abstract the proposition**
Reduce proposition to pattern:
```
Proposition: "Migrate to microservices"
Pattern: "Large-scale architecture migration in growing company"

Proposition: "Enter European market"
Pattern: "Geographic expansion to new regulatory environment"
```

**Step 2: Search for precedents**
Look for historical examples:
- Same company: "Have we tried this before?"
- Same industry: "What happened when [competitor] did this?"
- Analogous situation: "What similar patterns have failed?"

Use experience pool (references/experience-pool-patterns.md) for common patterns.

**Step 3: Extract failure mechanisms**
For each precedent:
- What specifically went wrong?
- What warning signs preceded failure?
- What would have prevented failure?

**Step 4: Apply to current proposition**
```
"[Precedent] failed because [mechanism]. Our proposition has
[similar condition]. Risk: [specific failure mode]."
```

### Example

**Proposition:** "Rewrite legacy system from scratch"

**Abstract pattern:** "Full system rewrite of working production system"

**Historical precedents:**
1. Netscape 6.0 rewrite (failed, lost browser war)
2. Internal CRM rewrite at [Company] (18 months late, abandoned)
3. Joel Spolsky's "Things You Should Never Do" essay

**Failure mechanisms:**
- Precedent 1: "New system never caught up with old system's features"
- Precedent 2: "Requirements changed during rewrite; perpetual catch-up"
- Pattern: "Second-system effect: new system becomes over-engineered"

**Attacks:**
- ATK: "Feature parity target is a moving target; old system gets features during rewrite"
- ATK: "Rewrite will take 2x estimate (industry average); requirements will change"
- ATK: "Second-system effect: team will over-engineer, adding 'missing' features"

### Quality Criteria

- [ ] Precedents are genuinely analogous
- [ ] Failure mechanisms are specific
- [ ] Application to current proposition is concrete

---

## 6. Devil's Advocate Protocol

**Definition:** Systematically argue the opposing position with genuine effort, regardless of personal views.

**Best For:** Policy decisions, value-laden choices

**Cognitive Basis:** Dialectical reasoning, position independence

### Protocol

**Step 1: Identify the position**
```
Proposition asserts: "[Core claim]"
Opposing position: "[Negation or alternative]"
```

**Step 2: Steelman the opposition**
Build the strongest case for the opposing position:
- "The best argument against this proposition is..."
- "A reasonable person would oppose this because..."
- "The evidence that supports opposition includes..."

**Step 3: Argue with conviction**
Write arguments as if you genuinely believe the opposition:
- Use strong language
- Cite evidence
- Address counterarguments
- Make emotional appeals where appropriate

**Step 4: Extract attacks**
Convert strongest opposition arguments to attacks:
```
"The proposition fails because [opposition argument], which is supported by
[evidence] and not addressed by the current plan."
```

### Example

**Proposition:** "Implement mandatory code review for all changes"

**Position:** "All code changes should require peer review before merge"
**Opposition:** "Mandatory code review is counterproductive"

**Steelmanned opposition:**
"Mandatory code review creates bottlenecks that slow delivery. Studies show code review catches only 15% of bugs—less than automated testing. The social dynamics create rubber-stamping or nitpicking, neither of which improves quality. Senior developers spend review time instead of building. Async review adds hours/days to cycle time. Google's research shows review quality degrades with queue length. The ritual of review provides false confidence while creating real friction."

**Attacks:**
- ATK: "Code review bottleneck will slow deployment velocity by 30-50%"
- ATK: "Review quality degrades under pressure; will become rubber-stamping"
- ATK: "Senior developer time shifted to review instead of building"

### Quality Criteria

- [ ] Opposition is steelmanned, not strawmanned
- [ ] Arguments are evidence-based where possible
- [ ] Personal views are set aside

---

## 7. Stress Test Amplification

**Definition:** Push parameters to extremes and observe failure modes. What breaks at 10x? 100x? 0.1x?

**Best For:** Architecture, scalability, operational plans

**Cognitive Basis:** Boundary testing, chaos engineering principles

### Protocol

**Step 1: Identify key parameters**
List parameters that could vary:
- Scale: users, data, transactions, requests
- Time: deadlines, duration, response time
- Resources: budget, team size, compute
- Quality: data quality, availability, accuracy

**Step 2: Define extremes**
For each parameter:
```
Parameter: [name]
Current assumption: [value]
10x stress: [value × 10]
0.1x stress: [value × 0.1]
Worst case: [plausible extreme]
```

**Step 3: Apply stress**
For each extreme, analyze:
- "What happens at [extreme]?"
- "What breaks first?"
- "What's the failure mode?"
- "How bad is the impact?"

**Step 4: Formulate attacks**
For failure modes that are concerning:
```
"At [extreme condition], [component] fails because [mechanism].
Impact: [consequences]. Likelihood: [assessment]."
```

### Example

**Proposition:** "New API can handle 1,000 requests/second"

**Parameter:** Request rate
- Current assumption: 1,000 req/s
- 10x stress: 10,000 req/s
- 0.1x stress: 100 req/s (low load)
- Worst case: 50,000 req/s (viral spike)

**Stress analysis:**
- 10,000 req/s: Database connection pool exhausted at 3,000. Connection timeout cascades to all requests.
- 100 req/s: Cold start latency spikes because auto-scaling is too aggressive. P99 jumps 5x.
- 50,000 req/s: Load balancer rate limiting kicks in at 10,000. No graceful degradation; 80% requests fail.

**Attacks:**
- ATK: "Database connection pool exhausted at 3x load; cascade failure"
- ATK: "Cold start latency at low load; P99 SLA violated during off-peak"
- ATK: "No graceful degradation above 10K; viral spike causes 80% failure rate"

### Quality Criteria

- [ ] Parameters are meaningful (not arbitrary)
- [ ] Extremes are plausible (could actually happen)
- [ ] Failure modes are specific and testable

---

## 8. Blind Spot Hunter

**Definition:** Systematically search for what's NOT being discussed, measured, or considered.

**Best For:** All propositions, especially mature plans that feel "complete"

**Cognitive Basis:** Unknown unknowns, absence blindness

### Protocol

**Step 1: List what IS being discussed**
Catalog everything explicitly addressed:
- Topics covered
- Metrics tracked
- Risks acknowledged
- Stakeholders mentioned
- Scenarios planned for

**Step 2: Generate "what about..." questions**
For each category, ask what's missing:
- "What topic should be here but isn't?"
- "What metric isn't being tracked?"
- "What risk isn't acknowledged?"
- "Whose voice is absent?"
- "What scenario isn't planned for?"

**Step 3: Investigate absences**
For each suspicious absence:
- "Why isn't this discussed?"
- "Is it intentionally excluded or overlooked?"
- "What's the impact of ignoring this?"

**Step 4: Formulate attacks**
For significant blind spots:
```
"The proposition doesn't address [blind spot]. This matters because
[rationale]. If ignored, [consequence]."
```

### Example

**Proposition:** "Product launch plan for new mobile app"

**What's discussed:**
- Features, timeline, marketing, pricing
- User acquisition, retention metrics
- Technical architecture, testing
- Competitor analysis

**What-about questions:**
- "What about accessibility compliance?" → Not mentioned
- "What about app store rejection risk?" → Not mentioned
- "What about customer support capacity?" → Not mentioned
- "What about data privacy regulation?" → Mentioned briefly
- "What about device/OS fragmentation?" → Not mentioned

**Investigation:**
- Accessibility: App store requires accessibility. Not addressing = rejection risk.
- App store rejection: First submission has 40% rejection rate. No timeline buffer.
- Support: Launch spike will overwhelm support. No capacity plan.
- Device fragmentation: Android has 1000+ device profiles. Testing covers 12.

**Attacks:**
- ATK: "Accessibility compliance not addressed; app store rejection risk"
- ATK: "No buffer for app store rejection; 40% first-submission rejection rate"
- ATK: "Support capacity not planned; launch spike will create bad reviews"
- ATK: "Device testing covers 1% of Android profiles; compatibility issues guaranteed"

### Quality Criteria

- [ ] Absences are genuinely significant (not nitpicking)
- [ ] Impact of ignoring is material
- [ ] Attack is actionable

---

## Generating Quality Attacks

### Attack Quality Checklist

Every attack should pass these criteria:

| Criterion | Question | Fail Example | Pass Example |
|-----------|----------|--------------|--------------|
| **Specific** | Is it concrete? | "This might not work" | "Database can't handle 10x load" |
| **Mechanism** | How does harm occur? | "Users won't like it" | "Users churn because onboarding is 15 steps" |
| **Plausible** | Could this happen? | "Meteor destroys servers" | "AWS us-east-1 has regional outage" |
| **Substantive** | Does it matter? | "Documentation has typos" | "API documentation is wrong; integration failures" |
| **Actionable** | Can Blue Team respond? | "The economy might crash" | "Revenue depends on one customer segment" |

### Avoiding Weak Attacks

| Weak Pattern | Why It's Weak | How to Strengthen |
|--------------|---------------|-------------------|
| Vague concerns | Not actionable | Add specific mechanism |
| Obvious objections | Already considered | Find non-obvious angles |
| Hypotheticals without basis | Not credible | Ground in evidence or precedent |
| Personal preferences | Not substantive | Focus on objective impact |
| Rehashes | Already addressed | Find new angle or escalate |

### Attack Diversity

Ensure attacks cover multiple dimensions:

- **Technical** and **Non-technical**
- **Internal** and **External**
- **Short-term** and **Long-term**
- **Likely** and **Low-probability but high-impact**

### Documentation Format

```
Attack ID: ATK-[round]-[number]
Technique: [Which technique generated this]
Category: [From attack-vector-catalog]
Target: [What aspect of proposition]
Statement: [Clear attack formulation]
Mechanism: [How this causes harm]
Evidence/Precedent: [Why this is credible]
Severity: [CRITICAL | HIGH | MEDIUM | LOW]
Steel-manning: [Level applied] - [Notes on strengthening]
```
