# Steel-Manning Protocol

> Make attacks as strong as possible. The goal is truth, not victory.

Steel-manning is the opposite of straw-manning. Instead of weakening opposing arguments to make them easy to defeat, we strengthen them to their maximum potency. This ensures that when Blue Team defeats an attack, they've defeated something genuinely challenging.

---

## Core Principle

> "Argue the strongest version of the opposing position, not the weakest."

**Why steel-man attacks?**
- Weak attacks waste everyone's time
- Defenses against weak attacks provide false confidence
- Reality attacks with steel-manned arguments
- Surviving steel-manned attacks proves robustness

**The test:** Would a genuine opponent—a competitor, critic, or hostile stakeholder—consider this attack strong? If not, strengthen it.

---

## Three-Pass Steel-Manning Protocol

### Pass 1: Initial Formulation

Generate the basic attack:
```
"The proposition will fail because [vulnerability] when [trigger]."
```

**Quality bar:** Attack identifies a real vulnerability with a plausible trigger.

**Example (Pass 1):**
```
"The migration will fail because the team lacks experience."
```

This is a valid concern but vague and easily dismissed.

---

### Pass 2: Strengthen the Attack

Ask: "How can I make this attack more damaging?"

**Strengthening dimensions:**

| Dimension | Question | Technique |
|-----------|----------|-----------|
| **Specificity** | What exactly fails? | Add concrete details |
| **Mechanism** | How does failure occur? | Trace cause-effect chain |
| **Evidence** | What supports this? | Add data, precedents |
| **Scope** | How widespread is impact? | Identify cascades |
| **Likelihood** | How probable? | Cite base rates |
| **Timing** | When does it hit? | Identify critical moments |

**Pass 2 protocol:**

1. Take Pass 1 attack
2. Apply each strengthening dimension
3. Rewrite with added strength

**Example (Pass 2):**
```
Pass 1: "The migration will fail because the team lacks experience."

Strengthening:
- Specificity: "lacks Kubernetes production experience"
- Mechanism: "will make configuration errors that cause outages"
- Evidence: "industry data shows 70% of first K8s deployments have major incidents"
- Scope: "payment processing downtime affects all transactions"
- Likelihood: "team has zero production K8s experience"
- Timing: "first incident will occur during holiday peak traffic"

Pass 2: "The migration will fail because the team has zero Kubernetes
production experience. Industry data shows 70% of first K8s deployments
experience major incidents. Given our payment processing criticality,
the first configuration error—likely during peak traffic—will cause
transaction-affecting downtime. The question is not if, but when."
```

---

### Pass 3: Ideological Turing Test

Ask: "Would a genuine opponent accept this as a strong attack?"

**The Ideological Turing Test:**
> Can you argue this position so well that a true believer in that position
> couldn't tell you're playing devil's advocate?

**Pass 3 protocol:**

1. Read your Pass 2 attack
2. Imagine presenting it to:
   - A competitor trying to stop your project
   - A board member looking for reasons to cut budget
   - A critic writing a takedown article
3. Ask: "Would they say 'yes, that's a strong argument'?"
4. If no: identify what they'd add or change
5. Incorporate their perspective

**Turing Test questions:**
- "What would [Skeptical Stakeholder] add to this attack?"
- "What data would a determined critic cite?"
- "What worst-case scenario am I leaving out?"
- "What's the most damaging framing of this concern?"

**Example (Pass 3):**
```
Pass 2: [See above]

Turing Test: Would the CTO at a competitor think this is strong?

Competitor CTO perspective: "They're underselling the risk. It's not just
K8s—it's distributed systems in general. And the real risk isn't the first
incident, it's the debugging. Their team will spend weeks on issues that
experienced teams solve in hours. Meanwhile, we ship features."

Pass 3: "The migration will fail because your team is attempting distributed
systems at scale with zero production experience—not just Kubernetes, but
microservices, service mesh, distributed tracing, all of it. Industry data
shows 70% of first K8s deployments have major incidents, but the real cost
is the weeks your team will spend debugging issues that experienced teams
solve in hours. Every debugging session is a week your competitors ship
features. The gap compounds. By the time you're stable, you're 6 months
behind where you'd be with a pragmatic monolith approach. And that first
major incident? It will happen during peak traffic—it always does—and your
MTTR with an inexperienced team will exceed your SLA. The board will ask
why you didn't hire experience first. What's your answer?"
```

---

## Steel-Manning Checklist

Before accepting an attack, verify:

| Criterion | Question | Pass | Fail |
|-----------|----------|------|------|
| **Specific** | Is the vulnerability concrete? | "K8s config errors" | "Technical issues" |
| **Mechanistic** | Is cause-effect clear? | "Config error → outage → SLA breach" | "Things will break" |
| **Evidenced** | Is there supporting data? | "70% first-deployment incident rate" | "Probably will fail" |
| **Scoped** | Is impact identified? | "Payment processing for all customers" | "Might cause problems" |
| **Plausible** | Could this realistically happen? | Based on industry patterns | Hypothetical extreme |
| **Damaging** | Does it threaten the proposition? | "Project cancellation risk" | "Minor inconvenience" |
| **Non-dismissible** | Can't be easily waved away? | Requires substantive response | "We'll figure it out" |

---

## Common Steel-Manning Failures

### 1. Strawman Disguised as Steel

**Problem:** Attack looks strong but has obvious flaw
**Example:** "AI will become sentient and refuse to work"
**Fix:** Ground in realistic failure modes

### 2. Weak Framing

**Problem:** Attack is valid but stated weakly
**Example:** "Users might not like the new design"
**Fix:** "Users will abandon the product because the new design violates established UX patterns they've learned over 5 years, and the switching cost to competitor with familiar UX is zero"

### 3. Missing Mechanism

**Problem:** Attack states outcome without path
**Example:** "The project will be late"
**Fix:** "The project will be late because integration testing is scheduled for 2 weeks but similar integrations have taken 6 weeks historically, and there's no buffer"

### 4. Isolated Attack

**Problem:** Attack doesn't connect to broader impact
**Example:** "Database queries are slow"
**Fix:** "Database queries are slow because of missing indexes. At 10x scale, P99 latency will exceed 5s, triggering user-facing timeouts, which will generate support tickets, which will overwhelm the 2-person support team, which will create negative reviews"

### 5. Premature Softening

**Problem:** Attack hedged with qualifiers
**Example:** "This might possibly be a minor concern if certain conditions happen"
**Fix:** "This will cause [impact] because [mechanism]. Likelihood is [%] based on [evidence]."

---

## Steel-Manning Examples

### Example 1: Strategy Attack

**Weak (Strawman):**
"Expanding to Europe is risky"

**Medium (Valid but weak):**
"Expanding to Europe is risky because of GDPR compliance requirements"

**Strong (Steel-manned):**
"European expansion will fail because GDPR compliance requires 6-12 months of engineering work you've budgeted 3 months for. You'll either launch non-compliant (risking 4% global revenue fines) or launch late (ceding the market window to [Competitor] who's already GDPR-compliant). Your legal team hasn't done a gap analysis, your DPO position is unfilled, and your data architecture requires a redesign for data residency requirements you haven't scoped. The choice is: delay launch 9 months, or launch into regulatory risk that could cost 10x your European revenue target."

### Example 2: Architecture Attack

**Weak (Strawman):**
"Microservices add complexity"

**Medium (Valid but weak):**
"Microservices add operational complexity that your team may not be ready for"

**Strong (Steel-manned):**
"Your microservices migration will create an operational burden that exceeds your team's capacity. You're going from 1 deployment pipeline to 12, from 1 on-call rotation to 6 service teams, from 1 database to 8 data stores. Your 4-person ops team currently struggles with the monolith's operational load (3 incidents/week, 4-hour MTTR). Distributing the same functionality across 12 services doesn't reduce incidents—industry benchmarks show 3-5x increase during migration. Your team will be firefighting instead of building. After 6 months, your best engineers will burn out and leave for companies with saner architectures. You'll end up with a distributed monolith that has all the complexity of microservices with none of the benefits."

### Example 3: Investment Attack

**Weak (Strawman):**
"The market might be smaller than projected"

**Medium (Valid but weak):**
"The TAM analysis assumes 100% market capture which is unrealistic"

**Strong (Steel-manned):**
"Your $500M TAM is fiction. It assumes every company in the vertical adopts software (only 40% have today), at price points you've never validated ($50K average when competitors charge $20K), for a problem that 60% of prospects don't think they have. Your realistic SAM is $80M. Of that, your SOM—given your current sales capacity and product-market fit—is $4M in Year 3, not $40M. Your investors' return model requires $50M ARR for viable exit multiple. At your actual growth trajectory, that's 15 years, not 5. Your runway is 3 years. The math doesn't work."

---

## When to Stop Steel-Manning

Steel-manning has diminishing returns. Stop when:

1. **Turing test passes:** A genuine opponent would accept the attack as strong
2. **Specificity maxed:** All relevant details are included
3. **Evidence cited:** Supporting data or precedents are referenced
4. **Mechanism complete:** Full cause-effect chain is traced
5. **Impact scoped:** All downstream consequences are identified

**Signs of over-engineering:**
- Adding hypotheticals with no basis
- Including irrelevant details
- Making the attack less credible through extremism
- Spending more than 5 minutes on a single attack

---

## Integration with Red Team Workflow

### During Attack Generation

1. Generate basic attack (Pass 1)
2. Quick strengthening check: "Can I make this more specific?"
3. If obviously weak, do Pass 2 immediately
4. Document attack with steel-manning notes

### During Attack Review

Before submitting attacks to Blue Team:
1. Review all attacks with Pass 2 lens
2. Select 2-3 most important for Pass 3
3. Apply full Turing test to critical attacks
4. Document steel-manning level applied

### Steel-Manning Levels (Parameter)

| Level | Protocol | When to Use |
|-------|----------|-------------|
| **minimal** | Pass 1 only | Light intensity, time-constrained |
| **standard** | Pass 1 + Pass 2 | Standard intensity |
| **maximum** | All 3 passes | Aggressive intensity, high-stakes |
