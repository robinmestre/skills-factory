# Gap Taxonomy

Six mutually exclusive gap types with detection heuristics for PRD completeness audits.

---

## Overview

Every gap detected in a PRD audit must be classified into exactly one of six categories. This taxonomy ensures consistent classification and guides appropriate remediation.

**Taxonomy Principle:**
- Categories are **mutually exclusive** (each gap fits one type only)
- Categories are **collectively exhaustive** (every gap fits a type)
- Classification drives **remediation approach**

---

## The 6 Gap Types

| # | Type | Definition | Primary Remediation |
|---|------|------------|---------------------|
| 1 | **MISSING** | Required element completely absent | Add content |
| 2 | **INCOMPLETE** | Element present but lacking detail | Expand content |
| 3 | **INCONSISTENT** | Element contradicts other sections | Reconcile content |
| 4 | **AMBIGUOUS** | Multiple interpretations possible | Clarify content |
| 5 | **INCORRECT** | Factually wrong information | Correct content |
| 6 | **OUTDATED** | Was correct but no longer current | Update content |

---

## Gap Type Details

### 1. MISSING

**Definition:** A required element is completely absent from the PRD. No section, content, or reference exists for this item.

**Detection Heuristics:**
- Checklist item has no corresponding section
- Expected section header not found
- Search for related keywords returns no results
- No textual evidence of item anywhere in document

**Detection Signals:**
```
✗ No "Problem Statement" section
✗ Search for "persona", "user type", "target audience" returns nothing
✗ Dependencies section missing entirely
✗ No mention of risks anywhere in document
```

**Common Causes:**
- PRD template section skipped
- Author assumed information was obvious
- Time pressure led to omission
- Section deemed "not applicable" without noting

**Examples:**
| Checklist Item | MISSING Gap |
|----------------|-------------|
| PC-01: Problem Statement | No problem statement section exists |
| US-01: Primary User Persona | No user personas defined anywhere |
| DP-01: External Dependencies | No dependencies section in PRD |
| RA-01: Risk Register | No risks or assumptions documented |

**Severity Tendency:** Usually HIGH or CRITICAL (fundamental information absent)

**Remediation Pattern:** ADD CONTENT
- Create new section using template
- Gather information from stakeholders
- Document even if "not applicable" (state why)

---

### 2. INCOMPLETE

**Definition:** The element exists in the PRD but lacks required detail, depth, or coverage to be actionable.

**Detection Heuristics:**
- Section present but below quality threshold
- Partial coverage (e.g., 2 of 5 expected sub-items)
- Placeholders present ("TBD", "TODO", "[add later]")
- Truncated or abbreviated content
- Bullet points without elaboration
- Missing required sub-sections

**Detection Signals:**
```
△ Problem statement exists but no evidence cited
△ 3 user personas listed, only 1 has details
△ "Acceptance criteria: TBD"
△ Risk section says "risks to be identified"
△ Single bullet point where paragraph expected
```

**Common Causes:**
- Work in progress not completed
- Author ran out of time
- Assumed details would be added later
- Different understanding of required depth

**Examples:**
| Checklist Item | INCOMPLETE Gap |
|----------------|----------------|
| PC-02: Problem Evidence | Problem stated but no data/research cited |
| US-03: User Goals | Persona exists but goals not articulated |
| AC-01: Story Acceptance | User story has no acceptance criteria |
| RA-03: Risk Mitigation | Risks listed but no mitigation strategies |

**Severity Tendency:** Usually MEDIUM or HIGH (foundation exists but insufficient)

**Remediation Pattern:** EXPAND CONTENT
- Fill in missing details within existing section
- Complete placeholders with actual content
- Add depth to shallow descriptions
- Include all required sub-items

---

### 3. INCONSISTENT

**Definition:** The element contradicts or conflicts with other parts of the PRD, creating confusion about what's actually required.

**Detection Heuristics:**
- Conflicting statements in different sections
- Numbers that don't add up
- Timeline mismatches
- Scope definition contradicts requirements list
- Success metrics don't align with stated goals
- User story describes different persona than defined

**Detection Signals:**
```
⚠ Problem says "mobile users" but requirements are desktop-only
⚠ MVP scope excludes feature X, but user story references feature X
⚠ Timeline shows 6 weeks, milestones sum to 10 weeks
⚠ Success metric "reduce load time to <2s" but NFR says <5s acceptable
⚠ Persona is "enterprise admin" but stories are for end consumers
```

**Common Causes:**
- Multiple authors without coordination
- PRD evolved but not all sections updated
- Copy-paste from other PRDs
- Requirements changed but dependencies not

**Examples:**
| Checklist Item | INCONSISTENT Gap |
|----------------|------------------|
| RQ-05: Scope Alignment | Requirement contradicts out-of-scope list |
| GS-03: Success Metrics | Metrics don't measure stated goals |
| ST-07: Story Persona | Story references undefined persona |
| TS-02: Milestone Alignment | Milestones don't fit timeline |

**Severity Tendency:** Usually HIGH or CRITICAL (creates implementation confusion)

**Remediation Pattern:** RECONCILE CONTENT
- Identify authoritative source of truth
- Update conflicting sections to align
- Add explicit notes when intentional differences exist
- Have stakeholder resolve contradictions

---

### 4. AMBIGUOUS

**Definition:** The element is present but unclear, vague, or open to multiple reasonable interpretations.

**Detection Heuristics:**
- Subjective terms without definition ("fast", "simple", "user-friendly")
- Missing quantification where numbers expected
- Passive voice hiding responsible actors
- Pronouns without clear antecedents
- "Etc.", "and more", "as needed" without bounds
- Multiple valid interpretations of requirement

**Detection Signals:**
```
? "System should be performant" — what metric? what threshold?
? "Users can easily find items" — what is "easily"?
? "Some users may need..." — which users?
? "The data should be processed quickly" — by whom? how fast?
? "Support various formats" — which formats specifically?
? "Appropriate error handling" — what's appropriate?
```

**Common Causes:**
- Author assumed shared understanding
- Specifics not yet decided
- Fear of over-committing to details
- Domain jargon not defined
- Rushed writing without review

**Examples:**
| Checklist Item | AMBIGUOUS Gap |
|----------------|---------------|
| RQ-08: Performance NFR | "Fast response times" without metric |
| AC-05: Testable Criteria | "Works correctly" is not testable |
| US-05: User Context | "Advanced users" undefined |
| GS-02: Success Definition | "Improved user satisfaction" unmeasurable |

**Severity Tendency:** Usually MEDIUM (can be clarified, but delays decisions)

**Remediation Pattern:** CLARIFY CONTENT
- Add specific metrics and thresholds
- Define subjective terms explicitly
- Replace passive voice with active
- Enumerate bounded lists (no "etc.")
- Get stakeholder to commit to specifics

---

### 5. INCORRECT

**Definition:** The element contains factually wrong information, technical impossibilities, or demonstrable errors.

**Detection Heuristics:**
- Technical impossibilities stated as requirements
- Contradicts known facts about existing systems
- References non-existent entities (APIs, services, features)
- Dates or numbers demonstrably wrong
- Regulatory/compliance requirements misrepresented
- External dependencies incorrectly described

**Detection Signals:**
```
✗ "Integrate with UserService API v2" — API v2 doesn't exist
✗ "Current system handles 10K rps" — actual capacity is 2K
✗ "GDPR requires 30-day retention" — actually requires deletion
✗ "Launch by Q2 2023" — document written in 2024
✗ "Payment team will provide webhook" — no such commitment made
```

**Common Causes:**
- Outdated information sources
- Assumptions stated as facts
- Misremembered technical details
- Copy-paste from obsolete documents
- Miscommunication about commitments

**Examples:**
| Checklist Item | INCORRECT Gap |
|----------------|---------------|
| TC-02: Architecture Fit | References deprecated system |
| DP-02: Integration Point | API doesn't exist as described |
| TS-03: Resource Availability | Team availability misstated |
| RA-05: Compliance Requirement | Regulatory requirement wrong |

**Severity Tendency:** Usually HIGH or CRITICAL (building on false foundation)

**Remediation Pattern:** CORRECT CONTENT
- Verify facts with authoritative sources
- Update to accurate information
- Remove false claims
- Add "[verified DATE]" annotations for critical facts

---

### 6. OUTDATED

**Definition:** The element was once correct but is no longer current due to changes in context, systems, or decisions.

**Detection Heuristics:**
- References deprecated systems or versions
- Mentions completed features as future work
- Stakeholders or owners no longer in role
- Competitive information is stale
- Market conditions have changed
- Dependencies have been completed or cancelled

**Detection Signals:**
```
⏰ "Will integrate with legacy auth system" — legacy auth retired
⏰ "Pending design review" — review completed 3 months ago
⏰ "Product Owner: Jane Smith" — Jane left company
⏰ "Competitor X lacks feature Y" — they launched Y last month
⏰ "Blocked by Platform team" — blocker resolved
```

**Common Causes:**
- PRD not maintained after initial writing
- No owner to keep document current
- External changes not tracked
- Long-running projects drift from reality

**Examples:**
| Checklist Item | OUTDATED Gap |
|----------------|--------------|
| DP-04: Dependency Status | Dependency marked blocked but resolved |
| US-08: User Workflow | Describes old process, not current |
| TC-05: System Version | References outdated platform version |
| TS-06: Team Assignment | Lists people no longer on project |

**Severity Tendency:** Usually LOW or MEDIUM (unless outdated info drives decisions)

**Remediation Pattern:** UPDATE CONTENT
- Verify current state of all referenced items
- Update or remove stale references
- Add "last reviewed" dates
- Establish PRD maintenance cadence

---

## Gap Type Decision Tree

Use this flowchart to classify each detected gap:

```
START: Checklist item evaluation
         │
         ▼
┌────────────────────────┐
│ Is the element present │
│ in the PRD?            │
└────────────────────────┘
         │
    ┌────┴────┐
    │         │
   NO        YES
    │         │
    ▼         ▼
┌────────┐  ┌────────────────────────┐
│MISSING │  │ Is the element         │
└────────┘  │ complete (all required │
            │ sub-elements present)? │
            └────────────────────────┘
                      │
                 ┌────┴────┐
                 │         │
                NO        YES
                 │         │
                 ▼         ▼
          ┌──────────┐  ┌────────────────────────┐
          │INCOMPLETE│  │ Does it contradict     │
          └──────────┘  │ other PRD content?     │
                        └────────────────────────┘
                                  │
                             ┌────┴────┐
                             │         │
                            YES       NO
                             │         │
                             ▼         ▼
                      ┌────────────┐ ┌────────────────────────┐
                      │INCONSISTENT│ │ Is it clear and        │
                      └────────────┘ │ unambiguous?           │
                                     └────────────────────────┘
                                               │
                                          ┌────┴────┐
                                          │         │
                                         NO        YES
                                          │         │
                                          ▼         ▼
                                   ┌──────────┐  ┌────────────────────────┐
                                   │AMBIGUOUS │  │ Is it factually        │
                                   └──────────┘  │ correct?               │
                                                 └────────────────────────┘
                                                           │
                                                      ┌────┴────┐
                                                      │         │
                                                     NO        YES
                                                      │         │
                                                      ▼         ▼
                                               ┌──────────┐  ┌────────────────────────┐
                                               │INCORRECT │  │ Is it current          │
                                               └──────────┘  │ (not stale)?           │
                                                             └────────────────────────┘
                                                                       │
                                                                  ┌────┴────┐
                                                                  │         │
                                                                 NO        YES
                                                                  │         │
                                                                  ▼         ▼
                                                           ┌──────────┐  ┌────────┐
                                                           │ OUTDATED │  │ NO GAP │
                                                           └──────────┘  └────────┘
```

---

## Gap Type Distribution by Section

Typical distribution of gap types across PRD sections:

| Section | Common Gap Types | Notes |
|---------|------------------|-------|
| Problem & Context | MISSING, INCOMPLETE | Often skipped or shallow |
| User & Stakeholder | INCOMPLETE, AMBIGUOUS | Personas lack specificity |
| Goals & Success | AMBIGUOUS, MISSING | Metrics often vague |
| Requirements | AMBIGUOUS, INCOMPLETE | Detail gaps common |
| User Stories | INCOMPLETE, INCONSISTENT | Stories vs scope conflicts |
| Acceptance Criteria | MISSING, AMBIGUOUS | Most commonly missing |
| Dependencies | MISSING, OUTDATED | Often absent or stale |
| Risks & Assumptions | MISSING, INCOMPLETE | Frequently skipped |
| Timeline & Scope | INCONSISTENT, INCORRECT | Math errors, conflicts |
| Technical | MISSING, OUTDATED | Non-technical authors skip |

---

## Severity Correlation

While severity is scored independently, gap types have tendencies:

| Gap Type | Typical Severity | Rationale |
|----------|------------------|-----------|
| MISSING | HIGH-CRITICAL | Fundamental info absent |
| INCOMPLETE | MEDIUM-HIGH | Foundation exists but insufficient |
| INCONSISTENT | HIGH-CRITICAL | Creates confusion and rework |
| AMBIGUOUS | MEDIUM | Can be clarified relatively easily |
| INCORRECT | HIGH-CRITICAL | Building on false foundation |
| OUTDATED | LOW-MEDIUM | Usually cosmetic unless drives decisions |

---

## Remediation Effort by Type

Typical effort to remediate each gap type:

| Gap Type | Effort Range | Key Activities |
|----------|--------------|----------------|
| MISSING | Medium-Large | Research, stakeholder interviews, writing |
| INCOMPLETE | Small-Medium | Gather details, expand existing content |
| INCONSISTENT | Medium | Identify truth, reconcile across sections |
| AMBIGUOUS | Small | Add specificity, define terms |
| INCORRECT | Trivial-Small | Fact-check and correct |
| OUTDATED | Trivial-Small | Verify and update |

---

## Multiple Classification Scenarios

Sometimes a gap seems to fit multiple types. Use these rules:

### Rule 1: Primary Classification

Choose the type that **best describes the core problem**, not all problems.

**Example:** "Problem statement exists but mentions deprecated system"
- Could be INCOMPLETE (statement exists but...) or OUTDATED (deprecated)
- **Choose OUTDATED** — the core issue is staleness, not depth

### Rule 2: Cascade Priority

When genuinely torn, use this priority order:
1. MISSING (if truly absent, nothing else matters)
2. INCORRECT (factual errors trump vagueness)
3. INCONSISTENT (contradictions before ambiguity)
4. INCOMPLETE (present but shallow)
5. AMBIGUOUS (present but unclear)
6. OUTDATED (stale but was once correct)

### Rule 3: Log Multiple Issues

If an element has multiple distinct problems, create separate gap entries:

**Example:** User persona section
- GAP-001: INCOMPLETE — Persona B has no goals listed
- GAP-002: INCONSISTENT — Persona A contradicts story ST-05
- GAP-003: OUTDATED — Persona C references old workflow

---

## Integration with Severity Scoring

After classification, each gap is scored using RUBRIC-07:

```
Gap Classification (Type) → Severity Scoring (RUBRIC-07)
                                   │
                                   ├─ Impact (0.5 weight)
                                   ├─ Likelihood (0.3 weight)
                                   └─ Detectability (0.2 weight)
                                   │
                                   ▼
                            CRITICAL | HIGH | MEDIUM | LOW
```

See `severity-classification.md` for scoring details.
