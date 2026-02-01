# Attack/Defense Log Template

> Round-by-round documentation of adversarial validation.

Use this template to document each round of Red/Blue Team validation, tracking attacks, defenses, and convergence decisions.

---

## Template

```markdown
# Attack/Defense Log

## Validation Metadata

| Field | Value |
|-------|-------|
| **Subject** | [Brief description of proposition] |
| **Subject Type** | [decision \| strategy \| architecture \| plan \| policy \| investment \| security] |
| **Date** | [YYYY-MM-DD] |
| **Validator** | [Who performed validation] |

### Parameters

| Parameter | Value |
|-----------|-------|
| max_rounds | [N] |
| attack_intensity | [light \| standard \| aggressive] |
| convergence_mode | [no_new_critical \| all_addressed \| round_limit] |
| steel_manning_level | [minimal \| standard \| maximum] |
| experience_pool | [enabled \| disabled] |
| attack_categories | [List of categories used] |

---

## Original Proposition

[Full text of the proposition as submitted for validation]

---

## Pre-Round Setup

### Attack Surface Analysis

| Dimension | Attackable Elements |
|-----------|---------------------|
| Assumptions | [List key assumptions identified] |
| Dependencies | [List key dependencies] |
| Constraints | [List key constraints] |
| Stakeholders | [List key stakeholders] |

### Experience Pool Patterns Loaded

| Pattern ID | Pattern Name | Relevance |
|------------|--------------|-----------|
| [ARCH-01] | [Distributed Monolith] | [Why relevant] |
| [STRAT-02] | [Competitive Response Blindness] | [Why relevant] |
<!-- Add all loaded patterns -->

### Attack Categories Selected

| Category | Rationale for Inclusion |
|----------|------------------------|
| [ASSUMPTIONS] | [Why this category is relevant] |
| [DEPENDENCIES] | [Why this category is relevant] |
<!-- Add all selected categories -->

---

## Round 1

### Red Team Attacks

| ID | Category | Target | Attack Statement | Severity | Steel-manned |
|----|----------|--------|------------------|----------|--------------|
| ATK-1-1 | [Category] | [What aspect] | [Clear attack] | [CRITICAL/HIGH/MEDIUM/LOW] | [Yes/No + notes] |
| ATK-1-2 | [Category] | [What aspect] | [Clear attack] | [Severity] | [Steel-manning notes] |
| ATK-1-3 | [Category] | [What aspect] | [Clear attack] | [Severity] | [Steel-manning notes] |
<!-- Add all attacks -->

**Attack Generation Notes:**
- [Techniques used: pre-mortem, inversion, etc.]
- [Experience pool patterns matched]
- [Areas not yet attacked]

### Blue Team Defenses

| ID | Attack | Response | Defense Statement | Residual Risk |
|----|--------|----------|-------------------|---------------|
| DEF-1-1 | ATK-1-1 | [REFUTE/MITIGATE/ACCEPT/HARDEN] | [Specific defense] | [ELIMINATED/REDUCED/UNCHANGED] |
| DEF-1-2 | ATK-1-2 | [Response type] | [Defense details] | [Residual] |
| DEF-1-3 | ATK-1-3 | [Response type] | [Defense details] | [Residual] |
<!-- Add all defenses -->

**Proposition Changes (HARDEN responses):**
- [DEF-1-X]: [Original] → [Modified]
<!-- List all proposition modifications -->

### Round 1 Convergence Evaluation

| Metric | Count |
|--------|-------|
| New CRITICAL attacks | [N] |
| New HIGH attacks | [N] |
| New MEDIUM attacks | [N] |
| New LOW attacks | [N] |
| ACCEPT responses | [N] |

**Convergence Check:**
- Mode: [convergence_mode]
- Criterion: [Specific criterion for this mode]
- Result: [MET / NOT MET]

**Override Check:**
- [ ] All attack categories explored: [Yes/No]
- [ ] Defense quality substantive: [Yes/No]
- [ ] No stakeholder concerns: [Yes/No]

**Decision:** [CONTINUE / CONVERGED]

**Rationale:** [Why this decision]

---

## Round 2

### Current Proposition (after Round 1 hardening)

[Updated proposition incorporating Round 1 HARDEN changes]

### Red Team Attacks

| ID | Category | Target | Attack Statement | Severity | Steel-manned |
|----|----------|--------|------------------|----------|--------------|
| ATK-2-1 | [Category] | [What aspect] | [Clear attack] | [Severity] | [Notes] |
| ATK-2-2 | [Category] | [What aspect] | [Clear attack] | [Severity] | [Notes] |
<!-- Add Round 2 attacks -->

**Attack Generation Notes:**
- [New angles explored]
- [Response to Round 1 hardening]
- [Diminishing returns observed?]

### Blue Team Defenses

| ID | Attack | Response | Defense Statement | Residual Risk |
|----|--------|----------|-------------------|---------------|
| DEF-2-1 | ATK-2-1 | [Response type] | [Defense] | [Residual] |
| DEF-2-2 | ATK-2-2 | [Response type] | [Defense] | [Residual] |
<!-- Add Round 2 defenses -->

**Proposition Changes (HARDEN responses):**
- [Changes from this round]

### Round 2 Convergence Evaluation

| Metric | Count |
|--------|-------|
| New CRITICAL attacks | [N] |
| New HIGH attacks | [N] |
| New MEDIUM attacks | [N] |
| New LOW attacks | [N] |
| ACCEPT responses (cumulative) | [N] |

**Convergence Check:**
- Result: [MET / NOT MET]

**Decision:** [CONTINUE / CONVERGED]

**Rationale:** [Why]

---

## Round 3

<!-- Follow same structure as Round 2 -->
<!-- Continue for additional rounds as needed -->

---

## Convergence Summary

| Round | CRITICAL | HIGH | MEDIUM | LOW | Decision |
|-------|----------|------|--------|-----|----------|
| 1 | [N] | [N] | [N] | [N] | CONTINUE |
| 2 | [N] | [N] | [N] | [N] | CONTINUE |
| 3 | [N] | [N] | [N] | [N] | CONVERGED |

**Final Convergence:**
- Mode: [convergence_mode]
- Achieved: [Yes/No]
- Reason: [How convergence was determined]

---

## Attack Resolution Summary

### Fully Resolved (REFUTE + HARDEN)

| Attack ID | Resolution | Summary |
|-----------|------------|---------|
| ATK-1-1 | REFUTE | [Brief summary] |
| ATK-1-3 | HARDEN | [Brief summary + change] |
<!-- All REFUTE and HARDEN -->

### Mitigated (Risk Reduced)

| Attack ID | Mitigation | Residual Risk |
|-----------|------------|---------------|
| ATK-1-2 | [Mitigation summary] | [Risk description] |
<!-- All MITIGATE with residual -->

### Accepted (Risk Unchanged)

| Attack ID | Rationale | Risk Description |
|-----------|-----------|------------------|
| ATK-2-3 | [Why accepted] | [Risk that remains] |
<!-- All ACCEPT -->

---

## Defense Quality Assessment

### Response Type Distribution

| Type | Count | Percentage |
|------|-------|------------|
| REFUTE | [N] | [%] |
| MITIGATE | [N] | [%] |
| HARDEN | [N] | [%] |
| ACCEPT | [N] | [%] |

### Quality Indicators

| Indicator | Assessment |
|-----------|------------|
| REFUTE claims have evidence | [Yes/No/Partial] |
| MITIGATE responses are actionable | [Yes/No/Partial] |
| HARDEN changes are documented | [Yes/No] |
| ACCEPT responses have rationale | [Yes/No] |
| No CRITICAL attacks are ACCEPT | [Yes/No] |

---

## Severity Distribution

### By Round

| Severity | Round 1 | Round 2 | Round 3 | Total |
|----------|---------|---------|---------|-------|
| CRITICAL | [N] | [N] | [N] | [N] |
| HIGH | [N] | [N] | [N] | [N] |
| MEDIUM | [N] | [N] | [N] | [N] |
| LOW | [N] | [N] | [N] | [N] |

### Severity Trend

[Describe whether severity decreased across rounds - indicator of convergence quality]

---

## Proposition Evolution

### Original → Hardened

**Original:**
[Original proposition]

**After Round 1:**
[Proposition with Round 1 changes]

**After Round 2:**
[Proposition with Round 2 changes]

**Final (Battle-Tested):**
[Final hardened proposition]

### Modification Log

| ID | Round | Change | Attack Addressed |
|----|-------|--------|-----------------|
| MOD-1 | 1 | [Original] → [New] | ATK-1-3 |
| MOD-2 | 1 | [Original] → [New] | ATK-1-4 |
| MOD-3 | 2 | [Original] → [New] | ATK-2-1 |
<!-- All modifications -->

---

## Residual Risks

| Risk | Source Attack | Severity | Mitigation Status | Monitoring |
|------|--------------|----------|-------------------|------------|
| [Description] | ATK-X-Y | [Severity] | [MITIGATED/ACCEPTED] | [How monitored] |
<!-- All residual risks -->

---

## Log Metadata

| Field | Value |
|-------|-------|
| Total attacks generated | [N] |
| Total defenses provided | [N] |
| Rounds completed | [N] |
| Proposition modifications | [N] |
| Residual risks | [N] |
| Log generated | [Timestamp] |
```

---

## Compact Format (for shorter validations)

For light-intensity or quick validations, use this condensed format:

```markdown
# Attack/Defense Log (Compact)

**Subject:** [Proposition]
**Date:** [Date]
**Rounds:** [N]
**Intensity:** [light/standard/aggressive]

## Round 1

**Attacks:**
1. [ATK-1-1] [SEVERITY]: [Attack statement]
2. [ATK-1-2] [SEVERITY]: [Attack statement]

**Defenses:**
1. [DEF-1-1] [REFUTE/MITIGATE/HARDEN/ACCEPT]: [Defense]
2. [DEF-1-2] [Type]: [Defense]

**Convergence:** [CONTINUE/CONVERGED] - [Brief reason]

## Round 2

[Same format]

## Summary

**Resolved:** [N] attacks fully resolved
**Mitigated:** [N] attacks with reduced risk
**Accepted:** [N] residual risks

**Proposition Changes:**
- [MOD-1]: [Change]
- [MOD-2]: [Change]

**Residual Risks:**
- [Risk 1]
- [Risk 2]
```

---

## Example (Full Format)

```markdown
# Attack/Defense Log

## Validation Metadata

| Field | Value |
|-------|-------|
| **Subject** | Migrate payment processing to microservices |
| **Subject Type** | architecture |
| **Date** | 2024-01-15 |
| **Validator** | Platform Architecture Team |

### Parameters

| Parameter | Value |
|-----------|-------|
| max_rounds | 3 |
| attack_intensity | standard |
| convergence_mode | no_new_critical |
| steel_manning_level | standard |
| experience_pool | enabled |
| attack_categories | ASSUMPTIONS, DEPENDENCIES, SCALABILITY, OPERATIONAL, ORGANIZATIONAL |

---

## Original Proposition

Migrate payment processing from monolith to 5 microservices over 12 months.

---

## Round 1

### Red Team Attacks

| ID | Category | Target | Attack Statement | Severity | Steel-manned |
|----|----------|--------|------------------|----------|--------------|
| ATK-1-1 | ORGANIZATIONAL | Team capability | Team has zero Kubernetes production experience; 70% first-deployment incident rate means major outage guaranteed | CRITICAL | Yes: Added industry statistics |
| ATK-1-2 | TEMPORAL | Timeline | 12-month timeline ignores industry benchmarks showing 2-3x overrun for microservices migrations | HIGH | Yes: Added comparable data |
| ATK-1-3 | EDGE_CASES | Data consistency | Distributed transactions across payment services will fail under network partitions; payment consistency violated | CRITICAL | Yes: Technical specificity |
| ATK-1-4 | OPERATIONAL | Debugging | Debugging distributed payment failures at 3 AM without tracing expertise; MTTR will exceed SLA | HIGH | Yes: Added SLA impact |

### Blue Team Defenses

| ID | Attack | Response | Defense Statement | Residual Risk |
|----|--------|----------|-------------------|---------------|
| DEF-1-1 | ATK-1-1 | MITIGATE | Hire 2 senior engineers with microservices experience. Engage architecture consultancy for first 6 months. | REDUCED |
| DEF-1-2 | ATK-1-2 | HARDEN | Extend timeline to 18 months with 3-month buffer for unknowns | ELIMINATED |
| DEF-1-3 | ATK-1-3 | HARDEN | Keep payment processing in single service with ACID guarantees. Only extract non-payment services. | ELIMINATED |
| DEF-1-4 | ATK-1-4 | MITIGATE | Implement distributed tracing (Jaeger) before migration. Establish on-call runbooks. | REDUCED |

**Proposition Changes:**
- DEF-1-2: "12 months" → "18 months with 3-month buffer"
- DEF-1-3: "5 microservices" → "3 microservices + 1 payment service (ACID)"

### Round 1 Convergence Evaluation

| Metric | Count |
|--------|-------|
| New CRITICAL attacks | 2 |
| New HIGH attacks | 2 |
| ACCEPT responses | 0 |

**Decision:** CONTINUE (new CRITICAL attacks found)

---

## Round 2

### Current Proposition

Migrate to 3 microservices + 1 payment service over 18 months with 3-month buffer.

### Red Team Attacks

| ID | Category | Target | Attack Statement | Severity | Steel-manned |
|----|----------|--------|------------------|----------|--------------|
| ATK-2-1 | ORGANIZATIONAL | Hiring | Hiring 2 senior engineers in 6 months is optimistic; market is extremely competitive | HIGH | Yes |
| ATK-2-2 | OPERATIONAL | Tracing | Distributed tracing infrastructure adds operational complexity itself | MEDIUM | Yes |
| ATK-2-3 | ASSUMPTIONS | Boundaries | Service boundaries may be wrong without event storming; rework risk | MEDIUM | Yes |

### Blue Team Defenses

| ID | Attack | Response | Defense Statement | Residual Risk |
|----|--------|----------|-------------------|---------------|
| DEF-2-1 | ATK-2-1 | MITIGATE | Begin hiring immediately. Contingency: extend consultancy if hiring slips. | REDUCED |
| DEF-2-2 | ATK-2-2 | ACCEPT | Accept as cost of observability. Allocate 0.5 FTE for platform maintenance. | UNCHANGED |
| DEF-2-3 | ATK-2-3 | HARDEN | Conduct event storming workshop before finalizing boundaries. Add 4 weeks. | ELIMINATED |

**Proposition Changes:**
- DEF-2-3: Add event storming prerequisite

### Round 2 Convergence Evaluation

| Metric | Count |
|--------|-------|
| New CRITICAL attacks | 0 |
| New HIGH attacks | 1 |
| ACCEPT responses | 1 |

**Decision:** CONTINUE (new HIGH attack found)

---

## Round 3

### Red Team Attacks

| ID | Category | Target | Attack Statement | Severity | Steel-manned |
|----|----------|--------|------------------|----------|--------------|
| ATK-3-1 | ASSUMPTIONS | Migration necessity | Event storming may reveal microservices unnecessary; wasted planning | MEDIUM | Yes |
| ATK-3-2 | DEPENDENCIES | Consultancy | Consultancy knowledge transfer risk; expertise leaves when they do | MEDIUM | Yes |

### Blue Team Defenses

| ID | Attack | Response | Defense Statement | Residual Risk |
|----|--------|----------|-------------------|---------------|
| DEF-3-1 | ATK-3-1 | ACCEPT | Valid. Event storming is a gate; prepared to pivot to modular monolith if appropriate. | UNCHANGED |
| DEF-3-2 | ATK-3-2 | MITIGATE | Require knowledge transfer sessions, documentation deliverables, pair programming in contract. | REDUCED |

### Round 3 Convergence Evaluation

| Metric | Count |
|--------|-------|
| New CRITICAL attacks | 0 |
| New HIGH attacks | 0 |
| ACCEPT responses | 2 |

**Decision:** CONVERGED (no new CRITICAL or HIGH attacks)

---

## Convergence Summary

| Round | CRITICAL | HIGH | MEDIUM | LOW | Decision |
|-------|----------|------|--------|-----|----------|
| 1 | 2 | 2 | 0 | 0 | CONTINUE |
| 2 | 0 | 1 | 2 | 0 | CONTINUE |
| 3 | 0 | 0 | 2 | 0 | CONVERGED |

---

## Proposition Evolution

**Original:**
Migrate payment processing from monolith to 5 microservices over 12 months.

**Final (Battle-Tested):**
Migrate to 3 microservices + 1 payment service (ACID) over 18 months with 3-month buffer, after event storming confirms boundaries. Prerequisites: 2 senior engineers hired, architecture consultancy engaged, distributed tracing infrastructure deployed.

### Modification Log

| ID | Round | Change | Attack Addressed |
|----|-------|--------|-----------------|
| MOD-1 | 1 | 5 services → 3 + 1 payment | ATK-1-3 |
| MOD-2 | 1 | 12 months → 18 months + buffer | ATK-1-2 |
| MOD-3 | 2 | Add event storming prerequisite | ATK-2-3 |

---

## Residual Risks

| Risk | Source Attack | Severity | Status | Monitoring |
|------|--------------|----------|--------|------------|
| Hiring timeline slip | ATK-2-1 | HIGH | MITIGATED | Bi-weekly recruiting review |
| Observability overhead | ATK-2-2 | MEDIUM | ACCEPTED | Monthly capacity review |
| Event storming may show migration unnecessary | ATK-3-1 | MEDIUM | ACCEPTED | N/A - decision gate |
| Consultancy knowledge transfer | ATK-3-2 | MEDIUM | MITIGATED | Contract requirements |
```
