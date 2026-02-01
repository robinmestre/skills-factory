# Convergence Criteria

> Know when to stop iterating.

This document defines criteria for determining when Red/Blue cycles have converged—when sufficient adversarial pressure has been applied and the proposition has been adequately stress-tested.

---

## Overview

| Mode | Stop Condition | Best For |
|------|---------------|----------|
| `no_new_critical` | Round produces 0 new CRITICAL or HIGH attacks | Standard validation |
| `all_addressed` | No ACCEPT responses remain | High-stakes decisions |
| `round_limit` | max_rounds reached | Time-constrained reviews |

---

## Mode 1: no_new_critical

**Definition:** Stop when the Red Team cannot generate substantive new attacks.

**Stop condition:**
```
New CRITICAL attacks in round = 0
AND
New HIGH attacks in round = 0
```

### Measurement Protocol

**Step 1: Count new attacks by severity**
```
Round [N] new attacks:
- CRITICAL: [count]
- HIGH: [count]
- MEDIUM: [count]
- LOW: [count]
```

**Step 2: Identify genuinely new attacks**
An attack is "new" if:
- Not a reformulation of a previous attack
- Not a minor variation of a previous attack
- Addresses a genuinely different vulnerability

**Duplicate/variant detection:**
```
ATK-2-3: "Team lacks K8s experience"
ATK-3-1: "Team lacks distributed systems experience"
→ This is a VARIANT (same underlying concern, broader framing)
→ Does NOT count as new unless substantially different
```

**Step 3: Apply stop condition**
```
If new_critical == 0 AND new_high == 0:
  → CONVERGED
Else:
  → CONTINUE to Round N+1
```

### Quality Signals

**Good convergence:**
- Red Team genuinely struggled to find new attacks
- Attacks in final round are variations of earlier attacks
- Attack severity declining across rounds

**Suspicious convergence:**
- Converged in Round 1 (too fast)
- Red Team didn't use all attack categories
- Steel-manning level was minimal

### Example

```
Round 1: 2 CRITICAL, 3 HIGH, 4 MEDIUM
Round 2: 0 CRITICAL, 1 HIGH, 3 MEDIUM
Round 3: 0 CRITICAL, 0 HIGH, 2 MEDIUM

Decision: CONVERGED (no new CRITICAL or HIGH in Round 3)
```

---

## Mode 2: all_addressed

**Definition:** Stop when every attack has been addressed with REFUTE, MITIGATE, or HARDEN (no ACCEPT responses remain).

**Stop condition:**
```
Count of ACCEPT responses across all rounds = 0
```

### Measurement Protocol

**Step 1: Tally response types**
```
Total attacks: [N]
- REFUTE: [count]
- MITIGATE: [count]
- HARDEN: [count]
- ACCEPT: [count]
```

**Step 2: Apply stop condition**
```
If accept_count == 0:
  → CONVERGED
Else:
  → CONTINUE (address remaining ACCEPT responses)
```

### Addressing ACCEPT Responses

When an ACCEPT exists, the Blue Team must either:
1. **Upgrade to MITIGATE:** Find a mitigation that reduces risk
2. **Upgrade to HARDEN:** Modify proposition to eliminate vulnerability
3. **Upgrade to REFUTE:** Find evidence that invalidates the attack
4. **Justify continued ACCEPT:** Provide strong rationale (documented residual risk)

**Justifiable ACCEPT reasons:**
- Cost of mitigation exceeds value at risk
- Risk is inherent to all alternatives
- External factors make mitigation impossible

### Quality Signals

**Good convergence:**
- All ACCEPT responses have documented rationale
- No CRITICAL or HIGH attacks ended as ACCEPT
- Residual risks are genuinely acceptable

**Suspicious convergence:**
- ACCEPT responses "disappeared" without real mitigation
- Blue Team hand-waved mitigations to avoid ACCEPT
- CRITICAL attacks were forced to MITIGATE without substantive response

### Example

```
Round 1:
- 8 attacks → 2 REFUTE, 4 MITIGATE, 1 HARDEN, 1 ACCEPT

Round 2:
- New attacks: 3 → 1 REFUTE, 2 MITIGATE
- Previous ACCEPT upgraded to MITIGATE (found mitigation)

Round 3:
- New attacks: 1 → 1 MITIGATE
- No ACCEPT responses remaining

Decision: CONVERGED (0 ACCEPT across all rounds)
```

---

## Mode 3: round_limit

**Definition:** Stop when max_rounds is reached, regardless of attack/defense state.

**Stop condition:**
```
current_round >= max_rounds
```

### When to Use

- Time-constrained reviews
- Propositions with lower stakes
- When `no_new_critical` would take too long
- Light intensity validation

### Measurement Protocol

Simple counter:
```
Round 1 complete
Round 2 complete
Round 3 complete (max_rounds = 3)
→ CONVERGED (round limit)
```

### Quality Signals

**Good use:**
- max_rounds appropriate to stakes
- Attacks adequately explored within rounds
- Clear documented residual risks

**Poor use:**
- max_rounds = 1 for high-stakes decision
- Converged with CRITICAL attacks still ACCEPT
- Red Team clearly had more attacks to explore

### Example

```
max_rounds: 2
attack_intensity: light

Round 1: 4 attacks, all addressed
Round 2: 2 attacks, 1 ACCEPT remaining

Decision: CONVERGED (round limit reached)
Note: 1 ACCEPT documented as residual risk
```

---

## Override Conditions

Sometimes you should continue despite meeting convergence criteria.

### Continue Despite Convergence When:

**1. Key attack categories unexplored**
```
Attack categories used: [ASSUMPTIONS, DEPENDENCIES, SCALABILITY]
Attack categories available: [+ SECURITY, COMPETITIVE, ORGANIZATIONAL]

If high-stakes and missing categories are relevant:
→ CONTINUE (explore missing categories)
```

**2. Blue Team defenses appear superficial**
```
Defense quality assessment:
- DEF-2-1: Vague mitigation ("we'll be careful")
- DEF-2-2: No owner or timeline
- DEF-2-3: Hand-waving ("that won't happen")

If multiple defenses are low quality:
→ CONTINUE (require substantive defenses)
```

**3. Stakeholder requests additional scrutiny**
```
If stakeholder says:
- "I'm not convinced this attack was addressed"
- "What about [specific concern]?"
- "This feels too easy"

→ CONTINUE (honor stakeholder scrutiny)
```

**4. Recent HARDEN changes may introduce vulnerabilities**
```
If Round N included major proposition changes:
- New architecture element
- New dependency
- New workflow

→ CONTINUE (stress-test the hardened proposition)
```

### Override Documentation

```
Convergence met: YES (no_new_critical)
Override: YES
Reason: [Security attack category not explored; high-stakes decision]
Decision: CONTINUE to Round [N+1]
```

---

## Premature Termination Signs

Don't stop too early. Watch for these signs:

### 1. Converged in Round 1

**Suspicious:** Almost always indicates Red Team under-performed

**Check:**
- Was steel-manning level adequate?
- Were all attack categories explored?
- Did Red Team genuinely try?

**Action:** Consider continuing or re-running Round 1 with higher intensity

### 2. CRITICAL Attacks Still ACCEPT

**Suspicious:** Should not happen in quality validation

**Rule:** CRITICAL attacks must be REFUTE, MITIGATE, or HARDEN

**Action:** Continue until no CRITICAL attacks are ACCEPT

### 3. Attack Quality Improving

**Suspicious:** Convergence should show declining attack quality

**Signs of improving attacks:**
- Round N attacks are more severe than Round N-1
- Red Team found new fruitful attack vector
- Blue Team's defenses revealed new vulnerabilities

**Action:** Continue until attack quality stabilizes

### 4. Experience Pool Patterns Not Probed

**Suspicious:** If experience pool loaded but patterns not used

**Check:**
- Were relevant historical patterns applied?
- Did any attacks reference experience pool?

**Action:** Continue and explicitly apply experience pool patterns

---

## Convergence Decision Template

Use this template for each round's evaluation:

```markdown
## Round [N] Convergence Evaluation

### Attack Summary
- New CRITICAL attacks: [count]
- New HIGH attacks: [count]
- New MEDIUM attacks: [count]
- New LOW attacks: [count]
- Genuine new attacks (not variants): [count]

### Defense Summary
- REFUTE: [count]
- MITIGATE: [count]
- HARDEN: [count]
- ACCEPT: [count]

### Convergence Check

**Mode:** [no_new_critical | all_addressed | round_limit]

**Criteria:**
- [Specific criterion for mode]

**Result:** [MET | NOT MET]

### Override Check

- [ ] All attack categories explored
- [ ] Defense quality is substantive
- [ ] No stakeholder concerns
- [ ] No recent HARDEN changes

**Override:** [YES/NO]
**Reason:** [If yes, explain]

### Decision

**CONVERGED / CONTINUE**

**Rationale:** [Explain decision]
```

---

## Intensity-Based Defaults

| Intensity | Default Convergence Mode | max_rounds |
|-----------|--------------------------|------------|
| light | round_limit | 2 |
| standard | no_new_critical | 3 |
| aggressive | no_new_critical (strict) | 5 |

**Aggressive mode strictness:**
- Requires 2 consecutive rounds with no new CRITICAL/HIGH
- No ACCEPT responses for CRITICAL or HIGH attacks
- All attack categories must be explored
