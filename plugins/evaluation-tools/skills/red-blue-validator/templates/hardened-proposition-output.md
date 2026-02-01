# Hardened Proposition Output Template

> Battle-tested version of the proposition after adversarial validation.

Use this template to document the final, hardened version of a proposition after Red/Blue Team validation.

---

## Template

```markdown
# Hardened Proposition

## Metadata

| Field | Value |
|-------|-------|
| **Original Subject** | [Brief description] |
| **Subject Type** | [decision \| strategy \| architecture \| plan \| policy \| investment \| security] |
| **Validation Date** | [YYYY-MM-DD] |
| **Rounds Completed** | [N] |
| **Battle-Tested Confidence** | [0-100] |

---

## Original Proposition

[Full text of the original proposition as submitted for validation]

---

## Battle-Tested Proposition

[Full text of the hardened proposition incorporating all HARDEN modifications]

---

## Key Modifications

| # | Original | Hardened | Reason | Source Attack |
|---|----------|----------|--------|---------------|
| 1 | [Original element] | [Modified element] | [Why changed] | ATK-X-Y |
| 2 | [Original element] | [Modified element] | [Why changed] | ATK-X-Y |
| 3 | [Original element] | [Modified element] | [Why changed] | ATK-X-Y |

---

## Modifications Detail

### MOD-1: [Brief title]

**Original:**
> [Exact original wording]

**Hardened:**
> [Exact modified wording]

**Attack that prompted this change:**
> ATK-X-Y: [Attack statement]

**Rationale:**
[Why this modification eliminates or reduces the vulnerability]

---

### MOD-2: [Brief title]

<!-- Repeat for each modification -->

---

## Residual Risks Accepted

These risks were identified through adversarial validation and accepted as part of the hardened proposition:

### Risk 1: [Risk title]

| Attribute | Value |
|-----------|-------|
| **Source Attack** | ATK-X-Y |
| **Severity** | [CRITICAL \| HIGH \| MEDIUM \| LOW] |
| **Defense Response** | [ACCEPT \| MITIGATE with residual] |

**Description:**
[Clear description of the residual risk]

**Why Accepted:**
[Rationale for accepting this risk]

**Monitoring:**
- Early warning signs: [What to watch for]
- Trigger condition: [When to escalate]
- Review frequency: [How often to reassess]
- Owner: [Who monitors]

**Contingency:**
[What to do if this risk materializes]

---

### Risk 2: [Risk title]

<!-- Repeat for each residual risk -->

---

## Battle-Tested Confidence

### Score: [0-100]

### Scoring Breakdown

| Factor | Assessment | Score Impact |
|--------|------------|--------------|
| Rounds completed | [N] rounds | [+X] |
| Attack quality | [substantive/weak] | [+/-X] |
| Attack diversity | [N] categories covered | [+X] |
| Defense quality | [genuine/hand-waving] | [+/-X] |
| ACCEPT responses | [N] remaining | [-X] |
| CRITICAL unresolved | [N] | [-X] |

### Confidence Rationale

[Narrative explanation of why this confidence score is appropriate]

---

## Conditions for Validity

The hardened proposition remains valid under these conditions. If any condition changes, re-validate.

### Assumption Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | [Assumption that must hold] | [How to verify] |
| 2 | [Assumption that must hold] | [How to verify] |

### Environmental Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | [External condition that must hold] | [How to verify] |
| 2 | [External condition that must hold] | [How to verify] |

### Resource Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | [Resource that must be available] | [How to verify] |
| 2 | [Resource that must be available] | [How to verify] |

---

## Review Triggers

Re-run Red/Blue Team validation if any of these occur:

### Automatic Triggers

- [ ] [Specific event that requires re-validation]
- [ ] [Specific event that requires re-validation]
- [ ] [Time-based trigger: e.g., "6 months have passed"]

### Conditional Triggers

- [ ] If [condition], then re-validate [aspect]
- [ ] If [condition], then re-validate [aspect]

### Stakeholder Triggers

- [ ] Stakeholder raises concern about [topic]
- [ ] New information about [risk area]

---

## Comparison: Original vs. Hardened

### Side-by-Side Summary

| Dimension | Original | Hardened | Change |
|-----------|----------|----------|--------|
| [Dimension 1] | [Original value] | [New value] | [Delta] |
| [Dimension 2] | [Original value] | [New value] | [Delta] |
| [Dimension 3] | [Original value] | [New value] | [Delta] |

### Improvement Assessment

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Attack vulnerabilities | [N] | [N] | [Delta] |
| CRITICAL/HIGH risks | [N] | [N] | [Delta] |
| Residual risks | N/A | [N] | — |
| Confidence | Unknown | [Score] | — |

---

## Go/No-Go Recommendation

### Recommendation: [PROCEED | PROCEED_WITH_CAUTION | SIGNIFICANT_CONCERNS | DO_NOT_PROCEED]

### Recommendation Rationale

[Narrative explanation of the recommendation, including:
- Key strengths of the hardened proposition
- Key risks that remain
- Conditions for success
- Monitoring requirements]

### Required Actions Before Proceeding

| # | Action | Owner | Timeline | Criticality |
|---|--------|-------|----------|-------------|
| 1 | [Action required] | [Who] | [When] | [Must do / Should do] |
| 2 | [Action required] | [Who] | [When] | [Criticality] |

### Monitoring Requirements

| # | What to Monitor | Owner | Frequency |
|---|-----------------|-------|-----------|
| 1 | [Metric/condition] | [Who] | [How often] |
| 2 | [Metric/condition] | [Who] | [How often] |

---

## Attestation

**Validated by:** [Name/Role]
**Validation date:** [YYYY-MM-DD]
**Validation method:** Red/Blue Team Validator v2.0
**Rounds completed:** [N]
**Convergence achieved:** [Yes/No]

---

## Appendix: Full Attack/Defense Summary

### Attacks by Round

| Round | Total | CRITICAL | HIGH | MEDIUM | LOW |
|-------|-------|----------|------|--------|-----|
| 1 | [N] | [N] | [N] | [N] | [N] |
| 2 | [N] | [N] | [N] | [N] | [N] |
| 3 | [N] | [N] | [N] | [N] | [N] |

### Defense Outcomes

| Outcome | Count | Percentage |
|---------|-------|------------|
| REFUTE | [N] | [%] |
| MITIGATE | [N] | [%] |
| HARDEN | [N] | [%] |
| ACCEPT | [N] | [%] |

### Reference Documents

- Full Attack/Defense Log: [link or reference]
- Risk Assessment: [link or reference]
```

---

## Example

```markdown
# Hardened Proposition

## Metadata

| Field | Value |
|-------|-------|
| **Original Subject** | Migrate payment processing from monolith to microservices |
| **Subject Type** | architecture |
| **Validation Date** | 2024-01-15 |
| **Rounds Completed** | 3 |
| **Battle-Tested Confidence** | 72 |

---

## Original Proposition

Migrate payment processing from monolith to 5 microservices over 12 months.

---

## Battle-Tested Proposition

Migrate to 3 microservices + 1 payment service (ACID) over 18 months with 3-month buffer, after event storming confirms service boundaries.

**Prerequisites:**
- 2 senior engineers with microservices experience hired
- Architecture consultancy engaged for first 6 months
- Distributed tracing infrastructure (Jaeger) deployed
- Event storming workshop completed with boundaries validated

**Execution constraints:**
- Payment processing remains in single ACID service (not distributed)
- Migration proceeds incrementally: one service at a time
- Each service extraction has rollback capability

---

## Key Modifications

| # | Original | Hardened | Reason | Source |
|---|----------|----------|--------|--------|
| 1 | 5 microservices | 3 microservices + 1 payment service | Payment consistency requires ACID; distributed transactions too risky | ATK-1-3 |
| 2 | 12 months | 18 months + 3-month buffer | Industry benchmarks show 2-3x overrun typical | ATK-1-2 |
| 3 | No prerequisites | Event storming + hiring + observability first | Address capability gap and boundary uncertainty | ATK-1-1, ATK-2-3 |

---

## Modifications Detail

### MOD-1: Payment Service Architecture

**Original:**
> 5 microservices including distributed payment processing

**Hardened:**
> 3 microservices + 1 payment service maintaining ACID guarantees

**Attack that prompted this change:**
> ATK-1-3: "Distributed transactions across payment services will fail under network partitions; payment consistency violated"

**Rationale:**
Payment processing requires strong consistency. Distributed transactions across services introduce network partition risks that can violate payment integrity. Keeping payment logic in a single service with traditional ACID transactions eliminates this vulnerability while still enabling microservices benefits for non-payment functions.

---

### MOD-2: Timeline Extension

**Original:**
> 12 months

**Hardened:**
> 18 months with 3-month buffer

**Attack that prompted this change:**
> ATK-1-2: "12-month timeline ignores industry benchmarks showing 2-3x overrun for microservices migrations"

**Rationale:**
Industry data shows microservices migrations typically take 2-3x initial estimates. A 12-month timeline creates pressure that leads to shortcuts and technical debt. 18 months with buffer provides realistic runway for learning curve, unexpected issues, and quality execution.

---

### MOD-3: Prerequisites Added

**Original:**
> No explicit prerequisites

**Hardened:**
> Prerequisites: senior engineers hired, consultancy engaged, observability deployed, event storming completed

**Attack that prompted this change:**
> ATK-1-1: "Team has zero Kubernetes production experience"
> ATK-2-3: "Service boundaries may be wrong without event storming"

**Rationale:**
Starting migration without capability and clarity creates high failure risk. Prerequisites ensure the team has necessary skills (via hiring and consultancy), can debug distributed systems (via observability), and has validated service boundaries (via event storming).

---

## Residual Risks Accepted

### Risk 1: Hiring Timeline Slip

| Attribute | Value |
|-----------|-------|
| **Source Attack** | ATK-2-1 |
| **Severity** | HIGH |
| **Defense Response** | MITIGATE |

**Description:**
Senior engineer hiring may take longer than 6 months due to competitive market conditions, potentially delaying project start.

**Why Accepted (as residual):**
Mitigation (begin hiring immediately, consultancy bridge) reduces but doesn't eliminate this risk. Cannot fully control hiring timeline in competitive market.

**Monitoring:**
- Early warning signs: No qualified candidates after 8 weeks; offer rejections
- Trigger condition: No hire after 4 months
- Review frequency: Bi-weekly
- Owner: Engineering Manager

**Contingency:**
Extend architecture consultancy engagement as bridge; potentially adjust timeline.

---

### Risk 2: Observability Platform Overhead

| Attribute | Value |
|-----------|-------|
| **Source Attack** | ATK-2-2 |
| **Severity** | MEDIUM |
| **Defense Response** | ACCEPT |

**Description:**
Distributed tracing infrastructure adds ongoing operational complexity requiring dedicated maintenance effort.

**Why Accepted:**
This overhead is a necessary cost of operating distributed systems safely. The alternative—operating without observability—creates much higher risk of extended outages.

**Monitoring:**
- Early warning signs: Platform maintenance exceeding planned allocation
- Trigger condition: Overhead exceeds 1 FTE
- Review frequency: Monthly
- Owner: Platform Lead

**Contingency:**
Evaluate managed observability services if self-hosted overhead becomes excessive.

---

## Battle-Tested Confidence

### Score: 72

### Scoring Breakdown

| Factor | Assessment | Score Impact |
|--------|------------|--------------|
| Rounds completed | 3 rounds | +15 |
| Attack quality | Substantive, steel-manned | +20 |
| Attack diversity | 5 categories covered | +10 |
| Defense quality | Genuine, actionable | +15 |
| ACCEPT responses | 2 remaining | -5 |
| CRITICAL unresolved | 0 | +0 |

### Confidence Rationale

The hardened proposition survived 3 rounds of substantive adversarial scrutiny. Critical vulnerabilities (payment consistency, team capability, timeline) were addressed through hardening and mitigation. Remaining residual risks (hiring, observability overhead) are manageable and monitored. The proposition is meaningfully stronger than the original, with clear prerequisites and realistic expectations.

---

## Conditions for Validity

### Assumption Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | Team successfully hires 2+ senior engineers | Bi-weekly recruiting review |
| 2 | Event storming confirms proposed service boundaries | Workshop outcome review |
| 3 | Architecture consultancy is available and engaged | Contract and engagement tracking |

### Environmental Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | No major changes to payment compliance requirements | Quarterly compliance review |
| 2 | Kubernetes/container ecosystem remains stable | Technology radar monitoring |

### Resource Conditions

| # | Condition | Monitoring Approach |
|---|-----------|---------------------|
| 1 | 18-month timeline is not compressed | Project governance |
| 2 | Budget for consultancy and hiring is maintained | Quarterly budget review |

---

## Review Triggers

### Automatic Triggers

- [ ] 6 months have passed since validation
- [ ] Major architecture decision is made that affects payment flow
- [ ] Key team member (hired senior engineer) leaves

### Conditional Triggers

- [ ] If hiring takes >6 months, re-validate timeline assumptions
- [ ] If event storming reveals different boundaries, re-validate architecture approach

### Stakeholder Triggers

- [ ] Stakeholder raises concern about payment consistency
- [ ] New information about compliance requirements

---

## Go/No-Go Recommendation

### Recommendation: PROCEED_WITH_CAUTION

### Recommendation Rationale

The hardened proposition addresses the critical flaws in the original plan:

**Strengths:**
- Payment consistency protected by keeping ACID service
- Realistic timeline based on industry benchmarks
- Clear prerequisites prevent premature start
- Observability enables safe operation

**Remaining risks:**
- Hiring timeline may slip (mitigated, monitored)
- Observability overhead (accepted as necessary cost)

**Conditions for success:**
- Begin hiring immediately; don't compromise on quality
- Complete event storming before finalizing boundaries
- Deploy observability before first service extraction
- Maintain consultancy engagement through initial milestones

### Required Actions Before Proceeding

| # | Action | Owner | Timeline | Criticality |
|---|--------|-------|----------|-------------|
| 1 | Begin senior engineer recruiting | Engineering Manager | Immediate | Must do |
| 2 | Engage architecture consultancy | VP Engineering | Within 2 weeks | Must do |
| 3 | Schedule event storming workshop | Platform Architect | Within 4 weeks | Must do |
| 4 | Plan observability infrastructure deployment | Platform Lead | Within 6 weeks | Must do |

### Monitoring Requirements

| # | What to Monitor | Owner | Frequency |
|---|-----------------|-------|-----------|
| 1 | Hiring pipeline progress | Engineering Manager | Bi-weekly |
| 2 | Consultancy engagement quality | VP Engineering | Monthly |
| 3 | Event storming preparation | Platform Architect | Weekly |
| 4 | Observability infrastructure readiness | Platform Lead | Weekly |

---

## Attestation

**Validated by:** Platform Architecture Team
**Validation date:** 2024-01-15
**Validation method:** Red/Blue Team Validator v2.0
**Rounds completed:** 3
**Convergence achieved:** Yes (no_new_critical)
```
