# Blue Team Techniques

> Systematic approaches for generating genuine, actionable defenses.

This document provides 8 defense techniques with step-by-step protocols. Use these to ensure Blue Team responses are substantive—not hand-waving dismissals or defensive denial.

---

## Overview

| # | Technique | Response Type | Best For |
|---|-----------|--------------|----------|
| 1 | Evidence-Based Refutation | REFUTE | Attacks that are factually wrong |
| 2 | Mitigation Design | MITIGATE | Valid attacks requiring safeguards |
| 3 | Contingency Planning | MITIGATE | Attacks with uncertain timing |
| 4 | Monitoring & Detection | MITIGATE | Attacks needing early warning |
| 5 | Hardening Protocol | HARDEN | Attacks revealing proposition weakness |
| 6 | Risk Transfer | MITIGATE | Attacks involving external parties |
| 7 | Staged Commitment | MITIGATE | Attacks about overcommitment |
| 8 | Kill Switch Design | MITIGATE | Attacks about irreversibility |

---

## Response Type Decision Tree

```
Receive Attack
    │
    ▼
Is the attack factually incorrect?
    │
    ├── YES → Use REFUTE (Technique 1)
    │
    └── NO → Is the attack valid?
                │
                ├── NO → Investigate further (may be REFUTE or ACCEPT)
                │
                └── YES → Can the proposition be modified to eliminate it?
                            │
                            ├── YES → Use HARDEN (Technique 5)
                            │
                            └── NO → Can the risk be reduced?
                                        │
                                        ├── YES → Use MITIGATE (Techniques 2-4, 6-8)
                                        │
                                        └── NO → Use ACCEPT (document residual risk)
```

---

## 1. Evidence-Based Refutation

**Definition:** Counter the attack with factual evidence that proves it invalid.

**Response Type:** REFUTE

**When to Use:**
- Attack is based on incorrect assumptions
- Attack contradicts available data
- Attack misunderstands the proposition

**When NOT to Use:**
- You don't have actual evidence (hope is not evidence)
- Evidence is weak or circumstantial
- Attack is valid but uncomfortable

### Protocol

**Step 1: Identify the attack's factual claim**
```
Attack claims: "[Specific factual assertion]"
```

**Step 2: Locate contradicting evidence**
Find evidence that disproves the claim:
- Data and metrics
- Documentation
- Expert testimony
- Historical precedent
- Logical necessity

**Step 3: Present refutation**
```
"The attack claims [X]. However, [evidence] shows [Y].
Specifically: [details]. Therefore, the attack is invalid."
```

**Step 4: Verify strength**
Ask: "Is this evidence strong enough that the attack is truly invalid?"
- If yes: REFUTE
- If no: Consider MITIGATE or ACCEPT

### Example

**Attack:** "The database can't handle 10,000 concurrent connections"

**Refutation process:**
1. Claim: Database has 10K connection limit
2. Evidence: Load test results from last month
3. Data: "Load test showed 15,000 concurrent connections sustained for 4 hours with 99.9% success rate"

**Defense:**
```
Response Type: REFUTE
Defense: "Attack claims database can't handle 10K connections. Our load test
on [date] demonstrated 15,000 concurrent connections sustained for 4 hours
with 99.9% success rate. Test report: [link]. The attack is factually
incorrect based on empirical testing."
Residual Risk: ELIMINATED
```

### Quality Criteria

- [ ] Evidence is concrete, not "I believe..."
- [ ] Evidence directly addresses the attack
- [ ] Evidence is verifiable
- [ ] Evidence is current (not outdated)

### Common Mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| Anecdotal evidence | "It worked before" | Cite specific data |
| Appeal to authority | "Expert says it's fine" | Provide expert's reasoning |
| Dismissive refutation | "That won't happen" | Explain why it won't happen |
| Incomplete refutation | Addresses only part of attack | Address full attack |

---

## 2. Mitigation Design

**Definition:** Accept the attack's validity but design safeguards to reduce risk.

**Response Type:** MITIGATE

**When to Use:**
- Attack identifies a real vulnerability
- Vulnerability can be addressed without changing the proposition
- Cost of mitigation is acceptable

### Protocol

**Step 1: Accept the vulnerability**
```
"The attack correctly identifies that [vulnerability exists]."
```

**Step 2: Design mitigation**
Choose mitigation type:

| Type | Description | Example |
|------|-------------|---------|
| **Prevention** | Stop the attack from occurring | Input validation |
| **Detection** | Know when attack occurs | Monitoring alerts |
| **Response** | React when attack occurs | Incident playbook |
| **Recovery** | Restore after attack | Backup restoration |

**Step 3: Specify mitigation details**
```
Mitigation: [Specific action]
Implementation: [How to implement]
Owner: [Who is responsible]
Timeline: [When complete]
Cost: [Resources required]
```

**Step 4: Assess residual risk**
```
Before mitigation: [Risk level]
After mitigation: [Risk level]
Residual: REDUCED | ELIMINATED
```

### Example

**Attack:** "API is vulnerable to brute force authentication attacks"

**Mitigation design:**
1. Accept: API lacks rate limiting on auth endpoint
2. Mitigation type: Prevention + Detection
3. Design:
   - Rate limit: 5 attempts per minute per IP
   - Account lockout: 10 failed attempts = 30 min lockout
   - Alert: Notify security team on lockout trigger

**Defense:**
```
Response Type: MITIGATE
Defense: "Attack is valid—API lacks brute force protection. Implementing:
(1) Rate limit: 5 auth attempts/min/IP
(2) Account lockout after 10 failures for 30 min
(3) Security alert on lockout trigger
Owner: Security team. Timeline: Sprint 14. Estimated effort: 3 dev-days."
Residual Risk: REDUCED (brute force still possible at rate limit, but
impractical for credential stuffing)
```

### Quality Criteria

- [ ] Mitigation addresses the specific attack
- [ ] Implementation is actionable
- [ ] Owner and timeline are specified
- [ ] Residual risk is honestly assessed

---

## 3. Contingency Planning

**Definition:** Prepare response plans for attacks that may or may not materialize.

**Response Type:** MITIGATE

**When to Use:**
- Attack timing or occurrence is uncertain
- Preparing in advance reduces impact
- Reactive response is feasible

### Protocol

**Step 1: Define trigger condition**
```
"If [specific event occurs], then [contingency activates]."
```

**Step 2: Design contingency response**
```
Trigger: [What activates the plan]
Response: [What we do]
Decision maker: [Who activates]
Resources: [What's needed]
Timeline: [How fast we respond]
```

**Step 3: Validate readiness**
- Are resources pre-positioned?
- Is decision authority clear?
- Has the team rehearsed?

**Step 4: Document as defense**
```
"We have contingency plan for [attack]. If [trigger], we will [response]."
```

### Example

**Attack:** "Key vendor might discontinue the API we depend on"

**Contingency planning:**
1. Trigger: Vendor announces deprecation or shows instability signs
2. Response: Activate migration to Vendor B (already evaluated)
3. Decision maker: VP Engineering
4. Resources: 2 engineers, 6 weeks, Vendor B contract ready to sign
5. Timeline: Begin within 1 week of trigger

**Defense:**
```
Response Type: MITIGATE
Defense: "Contingency plan in place. If vendor shows instability (defined as:
deprecation announcement, 3+ major outages in 30 days, or acquisition by
competitor), we activate migration to Vendor B. Pre-work completed: Vendor B
evaluated, contract template ready, migration runbook drafted. Migration
requires 2 engineers, 6 weeks. VP Engineering has authority to activate.
Total switch time: 7 weeks from trigger."
Residual Risk: REDUCED (migration cost if triggered, but not business-ending)
```

### Quality Criteria

- [ ] Trigger is specific and measurable
- [ ] Response is realistic and tested
- [ ] Resources are actually available
- [ ] Timeline is credible

---

## 4. Monitoring & Detection

**Definition:** Implement early warning systems to detect attacks before full impact.

**Response Type:** MITIGATE

**When to Use:**
- Attack develops gradually
- Early detection enables response
- Monitoring is technically feasible

### Protocol

**Step 1: Define what to monitor**
```
"To detect [attack], we need to monitor [metrics/signals]."
```

**Step 2: Set thresholds and alerts**
```
Metric: [What we measure]
Normal range: [Expected values]
Warning threshold: [When to pay attention]
Critical threshold: [When to act]
Alert mechanism: [How we're notified]
```

**Step 3: Define response to alerts**
```
When [threshold] crossed:
1. [First response action]
2. [Escalation if continued]
3. [Emergency response]
```

**Step 4: Document as defense**

### Example

**Attack:** "Database performance will degrade silently until catastrophic failure"

**Monitoring design:**
1. Monitor: Query latency, connection pool usage, disk I/O
2. Thresholds:
   - Warning: P99 latency > 200ms (normal: 50ms)
   - Critical: P99 latency > 500ms or connection pool > 80%
3. Alerts: PagerDuty to on-call, Slack to #db-alerts
4. Response: Warning → investigate; Critical → scale up + page DBA

**Defense:**
```
Response Type: MITIGATE
Defense: "Implementing database monitoring dashboard with alerts:
- P99 latency: warning >200ms, critical >500ms (baseline: 50ms)
- Connection pool: warning >70%, critical >80%
- Disk I/O: warning >70%, critical >85%
Alerts route to PagerDuty (critical) and Slack (warning). On-call
engineer responds within 15 min. DBA escalation for critical.
Dashboard: [link]. Runbook: [link]."
Residual Risk: REDUCED (degradation detected before user impact)
```

### Quality Criteria

- [ ] Metrics are actually measurable
- [ ] Thresholds are calibrated (not arbitrary)
- [ ] Alerts reach the right people
- [ ] Response actions are defined

---

## 5. Hardening Protocol

**Definition:** Modify the proposition itself to eliminate the vulnerability.

**Response Type:** HARDEN

**When to Use:**
- Attack reveals fundamental flaw in proposition
- Modification is feasible
- Modified proposition is still valuable

**When NOT to Use:**
- Modification destroys proposition's value
- Attack doesn't warrant fundamental change

### Protocol

**Step 1: Identify the vulnerability root cause**
```
"The attack succeeds because [specific weakness in proposition]."
```

**Step 2: Design proposition modification**
```
Original: [Original proposition element]
Modified: [Strengthened version]
Rationale: [Why this eliminates vulnerability]
```

**Step 3: Verify modification doesn't introduce new vulnerabilities**
- Does the change create new attack surfaces?
- Does the change affect other parts of the proposition?
- Is the modified proposition still valuable?

**Step 4: Document the hardening**
```
Response Type: HARDEN
Proposition Change: [Original] → [Modified]
Attack Eliminated: [Yes/No]
New Risks Introduced: [Any?]
```

### Example

**Attack:** "Distributed transactions across services will fail under network partitions"

**Hardening:**
1. Root cause: Proposition splits payment logic across 3 services
2. Modification: Keep payment logic in single service with ACID guarantees
3. Verify: Single service approach removes distributed transaction issue; no new risks identified

**Defense:**
```
Response Type: HARDEN
Defense: "Attack is valid—distributed transactions are problematic. Modifying
architecture: payment processing remains in single service (payment-core)
with PostgreSQL ACID transactions. Only non-payment services are extracted.
This eliminates the distributed transaction vulnerability entirely."
Proposition Change: "5 microservices" → "3 microservices + 1 payment monolith"
Residual Risk: ELIMINATED (no distributed transactions in payment path)
```

### Quality Criteria

- [ ] Modification addresses root cause
- [ ] Modified proposition is documented
- [ ] No new vulnerabilities introduced
- [ ] Proposition still achieves goals

---

## 6. Risk Transfer

**Definition:** Shift the risk to a party better positioned to handle it.

**Response Type:** MITIGATE

**When to Use:**
- Another party can absorb the risk more efficiently
- Transfer mechanism exists (insurance, contracts, partnerships)
- Cost of transfer is acceptable

### Protocol

**Step 1: Identify transfer target**
```
"[Party] is better positioned to handle this risk because [reason]."
```

Transfer targets:
- Insurance providers
- Vendors (via SLA/contract)
- Partners (via agreement)
- Customers (via terms of service)

**Step 2: Define transfer mechanism**
```
Mechanism: [Insurance policy | Contract clause | Partnership agreement]
Coverage: [What risk is transferred]
Cost: [Premium | Contract terms | Partner share]
Limitations: [What's not covered]
```

**Step 3: Verify transfer is effective**
- Does transfer actually cover this risk?
- Are there coverage gaps?
- Is the transfer party reliable?

### Example

**Attack:** "Cloud provider outage could cause 24+ hour downtime"

**Risk transfer:**
1. Target: Cloud provider (via SLA) + Insurance (business interruption)
2. Mechanism:
   - SLA: 99.99% uptime guarantee with financial credits
   - Insurance: Business interruption policy for >4 hour outages
3. Coverage: SLA covers provider outages; insurance covers lost revenue
4. Limitations: SLA credits don't cover consequential damages

**Defense:**
```
Response Type: MITIGATE
Defense: "Risk transferred via: (1) Cloud provider SLA with 99.99% uptime
guarantee and financial credits for breaches; (2) Business interruption
insurance covering lost revenue for outages >4 hours. Combined coverage
limits financial impact of provider outage. Residual: reputational impact
not transferable."
Residual Risk: REDUCED (financial impact transferred; reputation remains)
```

### Quality Criteria

- [ ] Transfer target can actually absorb the risk
- [ ] Transfer mechanism is legally sound
- [ ] Coverage gaps are identified
- [ ] Cost/benefit of transfer is acceptable

---

## 7. Staged Commitment

**Definition:** Reduce exposure by implementing in phases with go/no-go gates.

**Response Type:** MITIGATE

**When to Use:**
- Attack involves overcommitment to uncertain outcome
- Phased approach provides learning opportunities
- Exit points reduce total risk exposure

### Protocol

**Step 1: Define stages**
```
Stage 1: [Limited scope commitment]
Gate 1: [Decision criteria to proceed]
Stage 2: [Expanded scope]
Gate 2: [Decision criteria to proceed]
...
Full commitment: [Only after gates passed]
```

**Step 2: Define gate criteria**
```
Gate [N] requires:
- Metric A > threshold
- Metric B confirmed
- Risk X not materialized
Decision maker: [Who decides]
Fallback: [What if gate fails]
```

**Step 3: Quantify risk reduction**
```
Full commitment risk: [X]
Staged commitment risk: [Y] (if we stop at each gate)
Risk reduction: [X - Y]
```

### Example

**Attack:** "Full market expansion could fail, wasting entire $10M budget"

**Staged commitment:**
1. Stage 1: Launch in 2 pilot markets with $1M budget
   - Gate 1: CAC < $100, retention > 60%, NPS > 30
2. Stage 2: Expand to 5 markets with $3M budget
   - Gate 2: Unit economics positive, payback < 18 months
3. Stage 3: Full expansion with remaining $6M
   - Gate 3: Clear path to profitability

**Defense:**
```
Response Type: MITIGATE
Defense: "Staging expansion to reduce commitment risk:
- Stage 1: 2 pilot markets, $1M. Gate: CAC<$100, retention>60%, NPS>30
- Stage 2: 5 markets, $3M. Gate: Unit economics positive
- Stage 3: Full expansion, $6M. Gate: Profitability path validated
Maximum loss if Stage 1 fails: $1M (not $10M). Each gate provides data
to validate assumptions before deeper commitment."
Residual Risk: REDUCED (max exposure reduced 10x; learning enabled)
```

### Quality Criteria

- [ ] Stages are meaningful (not artificial)
- [ ] Gate criteria are measurable
- [ ] Fallback at each gate is viable
- [ ] Risk reduction is quantified

---

## 8. Kill Switch Design

**Definition:** Build reversibility into the proposition to enable retreat if attack materializes.

**Response Type:** MITIGATE

**When to Use:**
- Proposition could fail in ways requiring rapid retreat
- Reversibility is technically feasible
- Cost of building kill switch is acceptable

### Protocol

**Step 1: Define what needs to be reversible**
```
"If [attack materializes], we need to [reversal action]."
```

**Step 2: Design the kill switch**
```
Trigger: [When to activate]
Mechanism: [How reversal works]
Timeline: [How long reversal takes]
Side effects: [What's lost in reversal]
```

**Step 3: Validate kill switch works**
- Has it been tested?
- Can it execute under stress?
- Are there dependencies that prevent reversal?

### Example

**Attack:** "New feature might cause user revolt, requiring rapid rollback"

**Kill switch design:**
1. Reversal needed: Remove new feature instantly
2. Mechanism: Feature flag with instant disable
3. Timeline: < 1 minute to disable globally
4. Side effects: Users mid-action see fallback; data preserved

**Defense:**
```
Response Type: MITIGATE
Defense: "Kill switch implemented via feature flag:
- Trigger: >5% user complaints or >10% churn in first 48 hours
- Mechanism: Feature flag disables new UI instantly (< 1 min global)
- Data: All user data preserved; can re-enable seamlessly
- Tested: Kill switch exercised in staging; works as designed
Authority: Product lead can trigger; no engineering required."
Residual Risk: REDUCED (can reverse decision within minutes if negative signal)
```

### Quality Criteria

- [ ] Kill switch actually works (tested)
- [ ] Trigger criteria are clear
- [ ] Timeline is fast enough
- [ ] Side effects are acceptable

---

## Generating Quality Defenses

### Defense Quality Checklist

Every defense should pass these criteria:

| Criterion | Question | Fail | Pass |
|-----------|----------|------|------|
| **Addresses attack** | Does it respond to specific attack? | Generic response | Specific response |
| **Actionable** | Can it be implemented? | "We'll be careful" | Concrete action |
| **Owned** | Is someone responsible? | "The team" | "Sarah (Engineering)" |
| **Timed** | When will it happen? | "Soon" | "Sprint 14 (March 15)" |
| **Verified** | How do we know it works? | "It should work" | "Tested in staging" |
| **Honest** | Is residual risk stated? | "Fully mitigated" | "Reduced but X remains" |

### Avoiding Poor Defenses

| Poor Pattern | Problem | Quality Defense |
|--------------|---------|-----------------|
| "We'll figure it out" | Not actionable | Specific mitigation plan |
| "That won't happen" | Dismissive | Evidence or accept risk |
| "We have smart people" | Not a defense | Specific capability evidence |
| "It's industry standard" | Appeal to authority | Explain why standard helps |
| "We'll monitor it" | Vague | Specific metrics and thresholds |

### Defense Diversity

Ensure defenses don't all rely on same mechanism:
- Mix of REFUTE, MITIGATE, HARDEN, ACCEPT
- Multiple mitigation types (prevention, detection, response)
- Different owners and timelines
- Independent failure modes

### Documentation Format

```
Defense ID: DEF-[round]-[number]
Attack Addressed: ATK-[round]-[number]
Response Type: [REFUTE | MITIGATE | ACCEPT | HARDEN]
Defense: [Specific response]
Evidence/Implementation: [How this works]
Owner: [Responsible party]
Timeline: [When complete]
Residual Risk: [ELIMINATED | REDUCED | UNCHANGED]
Proposition Change: [If HARDEN]
```

---

## ACCEPT: The Honest Response

Sometimes, the honest response is to accept the risk:

**When to ACCEPT:**
- Attack is valid but impact is acceptable
- Cost of mitigation exceeds cost of risk
- Risk is inherent to the value proposition
- External factors make mitigation impossible

**ACCEPT documentation:**
```
Response Type: ACCEPT
Defense: "Attack is valid. We accept this risk because:
- Impact: [Quantified impact if attack materializes]
- Likelihood: [Probability assessment]
- Mitigation cost: [What it would take to mitigate]
- Rationale: [Why we're accepting]
Monitoring: [How we'll track if risk materializes]"
Residual Risk: UNCHANGED
```

**ACCEPT constraints:**
- CRITICAL attacks cannot be ACCEPT (must address)
- HIGH attacks require strong rationale for ACCEPT
- All ACCEPT responses become documented residual risks
