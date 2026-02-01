# PRD Anti-Patterns Catalog

15+ common PRD anti-patterns with detection heuristics and remediation guidance.

---

## Overview

Anti-patterns are recurring design mistakes in PRDs that predictably lead to project problems. This catalog helps identify and address these issues before they impact development.

**Purpose:** Detect systemic PRD quality issues beyond individual item gaps.

---

## Anti-Pattern Summary

| ID | Name | Severity | Frequency | Primary Impact |
|----|------|----------|-----------|----------------|
| AP-01 | Scope Creep Enabler | HIGH | Very Common | Unbounded scope |
| AP-02 | Solution Contamination | CRITICAL | Common | Design constraints |
| AP-03 | Stakeholder Soup | MEDIUM | Common | Decision paralysis |
| AP-04 | Metric-Free Zone | HIGH | Very Common | Unmeasurable success |
| AP-05 | Assumption Blindness | HIGH | Common | Hidden risks |
| AP-06 | Edge Case Avoidance | MEDIUM | Very Common | Production surprises |
| AP-07 | Dependency Denial | CRITICAL | Common | Integration failures |
| AP-08 | Timeline Fantasy | HIGH | Very Common | Missed deadlines |
| AP-09 | Acceptance Vagueness | CRITICAL | Common | Endless debates |
| AP-10 | User Story Stuffing | MEDIUM | Common | Estimation failures |
| AP-11 | Risk Minimization | HIGH | Common | Unprepared for problems |
| AP-12 | Technical Debt Deferral | MEDIUM | Common | Maintenance burden |
| AP-13 | Stakeholder Exclusion | HIGH | Uncommon | Rework from feedback |
| AP-14 | Scope Definition Deficit | CRITICAL | Common | Scope confusion |
| AP-15 | Priority Inflation | MEDIUM | Very Common | Everything urgent |
| AP-16 | Persona Proliferation | MEDIUM | Common | Unfocused design |
| AP-17 | Requirements Spaghetti | HIGH | Common | Untraceable needs |

---

## AP-01: Scope Creep Enabler

**Description:** PRD lacks clear boundaries, making it easy to expand scope continuously.

**Severity:** HIGH

**Detection Heuristics:**
- No "Out of Scope" section present
- Vague feature boundaries ("and more", "etc.")
- Open-ended language throughout
- No version or phase distinctions
- Missing "not included" items for each feature

**Detection Signals:**
```
⚠ "This feature will also support..."
⚠ "Future iterations may include..."
⚠ "...and other related functionality"
⚠ Lists ending with "etc." or "and more"
⚠ No explicit exclusions anywhere
⚠ "Nice-to-have" items mixed with requirements
```

**Example Violation:**
> "The reporting feature will provide dashboards, exports, scheduled reports, custom visualizations, and any other reporting needs the business may have."

**Impact:**
- Scope expands during development
- Estimates become meaningless
- Delivery dates slip repeatedly
- Team frustration increases

**Remediation:**
1. Add explicit "Out of Scope" section
2. Define clear version boundaries (v1.0, v1.1, future)
3. Replace "etc." with complete, bounded lists
4. Add explicit exclusions for each feature area
5. Require change request for any scope additions

**Template:**
```markdown
## Out of Scope (v1.0)

The following are explicitly NOT included in this release:
- [Specific exclusion 1]
- [Specific exclusion 2]
- [Specific exclusion 3]

These may be considered for future releases pending v1.0 success.
```

---

## AP-02: Solution Contamination

**Description:** PRD describes HOW to implement instead of WHAT to achieve, constraining design options.

**Severity:** CRITICAL

**Detection Heuristics:**
- Technical implementation details in requirements
- UI/UX specifics without user need context
- Database schema references
- API specifications before problem definition
- Technology choices embedded in requirements
- "Use [technology/framework]" statements

**Detection Signals:**
```
⚠ "Use React components to build..."
⚠ "The database should store..."
⚠ "Implement using microservices..."
⚠ "The button should be blue and 44px..."
⚠ "Call the /api/v2/users endpoint..."
⚠ "Store in PostgreSQL with..."
```

**Example Violation:**
> Requirement: "Use a React modal with Material UI to display a form with three input fields that posts to the /api/users endpoint."

**Correct Framing:**
> Requirement: "Users must be able to submit their contact information (name, email, phone) to request a callback."

**Impact:**
- Precludes potentially better solutions
- Ties engineering's hands
- Creates technical debt if implementation is forced
- Mixes product and engineering concerns

**Remediation:**
1. Reframe requirements as user needs, not solutions
2. Move technical details to separate technical design doc
3. Use "should enable" instead of "should implement"
4. Focus on WHAT, leave HOW to engineering
5. Remove technology-specific language

**Test:** Can this requirement be satisfied by multiple technical approaches? If no, it's solution contamination.

---

## AP-03: Stakeholder Soup

**Description:** Too many stakeholders with undefined decision authority, leading to paralysis.

**Severity:** MEDIUM

**Detection Heuristics:**
- Long stakeholder list with no RACI
- Everyone listed as "informed" or "consulted"
- No clear decision maker identified
- Multiple "co-owners" or "co-leads"
- Approval process undefined

**Detection Signals:**
```
⚠ "Stakeholders: Engineering, Design, Product, Marketing, Sales, Legal, Finance, Support..."
⚠ No single decision maker named
⚠ "All stakeholders must approve..."
⚠ "Consensus required from..."
⚠ Multiple people listed as "owner"
```

**Example Violation:**
> "Stakeholders: Product team, Engineering leads, Design, UX Research, Marketing, Customer Success, Legal, Security, Executive sponsors, Regional PMs (all regions)"

**Impact:**
- Decisions take forever
- Conflicting feedback not resolved
- No one accountable
- Death by committee

**Remediation:**
1. Define clear RACI matrix
2. Identify single decision maker (DRI)
3. Limit approvers to essential few
4. Specify escalation path
5. Define what "stakeholder input" means

**Template:**
```markdown
## Decision Authority

**Decision Maker (DRI):** [Name] - Final authority on scope and priorities
**Approvers:** [Name 1], [Name 2] - Must sign off before development
**Contributors:** [Team] - Provide input, no veto
**Informed:** [Distribution list] - Kept updated, no input required

Escalation path: DRI → [Manager] → [VP]
```

---

## AP-04: Metric-Free Zone

**Description:** PRD has no measurable success criteria or uses vanity metrics only.

**Severity:** HIGH

**Detection Heuristics:**
- No "Success Metrics" section
- Metrics are vague or unmeasurable
- No numeric targets
- Only vanity metrics (page views, downloads)
- No timeline for measurement

**Detection Signals:**
```
⚠ "Success: Happy users"
⚠ "Measure: User satisfaction improves"
⚠ "KPI: Adoption"
⚠ No numbers anywhere in goals section
⚠ "Metrics: TBD"
⚠ Only measuring outputs, not outcomes
```

**Example Violation:**
> "Success Metrics: We will know this is successful when users are satisfied and adoption increases."

**Correct Framing:**
> "Success Metrics:
> - Task completion rate increases from 67% to 85% within 30 days
> - User-reported satisfaction (NPS) improves from 32 to 45
> - Feature adoption reaches 40% of active users by week 8"

**Impact:**
- Cannot determine if feature succeeded
- No basis for iteration decisions
- Debates about "success" post-launch
- Impossible to learn from results

**Remediation:**
1. Define specific, measurable metrics
2. Set numeric targets with timeframes
3. Document baseline measurements
4. Identify leading and lagging indicators
5. Specify measurement methodology

---

## AP-05: Assumption Blindness

**Description:** Critical assumptions are unstated, creating hidden risk.

**Severity:** HIGH

**Detection Heuristics:**
- No "Assumptions" section
- Statements presented as facts without evidence
- Dependencies assumed to be ready
- User behavior assumptions not documented
- Market assumptions not stated

**Detection Signals:**
```
⚠ No assumptions section exists
⚠ "Users will..." without research backing
⚠ "The API will be ready..." without confirmation
⚠ "The market wants..." without evidence
⚠ Technical feasibility assumed, not verified
```

**Example Violation:**
Entire PRD proceeds without stating: "We assume mobile users have consistent internet connectivity."

**Impact:**
- Hidden risks emerge late
- Wrong assumptions lead to failed features
- No plan to validate assumptions
- Surprises during development

**Remediation:**
1. Add explicit "Assumptions" section
2. For each assumption, document:
   - The assumption
   - Why we believe it
   - How we'll validate it
   - What happens if wrong
3. Review assumptions with stakeholders
4. Create validation plan for critical assumptions

**Template:**
```markdown
## Assumptions

| # | Assumption | Basis | Validation | If Wrong |
|---|------------|-------|------------|----------|
| A1 | [Assumption] | [Why we think this] | [How to verify] | [Fallback plan] |
```

---

## AP-06: Edge Case Avoidance

**Description:** PRD only describes happy paths, ignoring error cases and exceptions.

**Severity:** MEDIUM

**Detection Heuristics:**
- No error handling requirements
- No boundary conditions specified
- Only success scenarios documented
- "Edge cases will be handled" without specifics
- No negative requirements

**Detection Signals:**
```
⚠ User stories only describe success
⚠ No "When X fails..." scenarios
⚠ No validation rules for inputs
⚠ Missing: timeout, retry, fallback specs
⚠ No empty state definitions
⚠ "Errors handled gracefully" (undefined)
```

**Example Violation:**
> "User story: As a user, I can upload my profile photo."
> (No mention of: invalid formats, file too large, upload fails, storage full, network timeout)

**Impact:**
- Edge cases discovered in production
- Poor error experience for users
- Security vulnerabilities
- Support burden increases

**Remediation:**
1. For each feature, ask "What could go wrong?"
2. Document error scenarios as requirements
3. Specify expected error behavior
4. Include boundary conditions (min/max)
5. Define empty states and loading states

---

## AP-07: Dependency Denial

**Description:** PRD ignores or minimizes external dependencies.

**Severity:** CRITICAL

**Detection Heuristics:**
- No "Dependencies" section
- Integration points not identified
- Other teams not mentioned
- Third-party services assumed available
- Data sources unspecified

**Detection Signals:**
```
⚠ No dependencies section exists
⚠ "Will integrate with..." but no details
⚠ External APIs mentioned but not specified
⚠ No team collaboration identified
⚠ Data requirements without source
```

**Example Violation:**
PRD requires "user authentication" but never mentions the identity team, auth service, or SSO integration needed.

**Impact:**
- Integration surprises mid-development
- Blocked on other teams
- Missing data or APIs
- Timeline slips from unplanned work

**Remediation:**
1. Add explicit "Dependencies" section
2. List all external systems
3. Identify all team dependencies
4. Document API/data dependencies
5. Confirm availability and timeline with dependency owners

---

## AP-08: Timeline Fantasy

**Description:** Timeline is unrealistic given scope, dependencies, and resources.

**Severity:** HIGH

**Detection Heuristics:**
- Timeline doesn't account for dependencies
- No buffer for unknowns
- Milestone dates arbitrary
- Resources not aligned with timeline
- History of similar estimates being wrong

**Detection Signals:**
```
⚠ "Launch: 6 weeks" for large scope
⚠ Dependencies not factored in
⚠ No mention of testing time
⚠ Milestones evenly spaced (suspicious)
⚠ No contingency buffer
⚠ Timeline set before scoping
```

**Example Violation:**
> "Timeline: 8 weeks to build complete payment system with PCI compliance"
> (Historically, payment projects take 16+ weeks)

**Impact:**
- Missed deadlines
- Quality compromised by rushing
- Team burnout
- Stakeholder trust erodes

**Remediation:**
1. Base estimates on similar past work
2. Include dependency wait times
3. Add contingency buffer (20-30%)
4. Get engineering input before committing
5. Define what's cut if timeline pressure

---

## AP-09: Acceptance Vagueness

**Description:** Acceptance criteria are subjective or untestable.

**Severity:** CRITICAL

**Detection Heuristics:**
- Subjective terms in criteria ("fast", "easy", "user-friendly")
- No numeric thresholds
- Criteria not testable
- "Works correctly" type criteria
- Missing criteria entirely

**Detection Signals:**
```
⚠ "System is responsive"
⚠ "User can easily find..."
⚠ "Works as expected"
⚠ "Acceptable performance"
⚠ No Given/When/Then structure
⚠ AC missing for user stories
```

**Example Violation:**
> "Acceptance Criteria: The search is fast and returns relevant results."

**Correct Framing:**
> "Acceptance Criteria:
> - Given a search query, when executed, then results return in < 200ms
> - Given a search for 'widget', when results display, then top 5 results contain 'widget' in title or description"

**Impact:**
- Debates about "done"
- QA cannot write tests
- Features never accepted
- Rework from misalignment

**Remediation:**
1. Use Given/When/Then format
2. Quantify all thresholds
3. Make every criterion testable
4. Review AC with QA before development
5. Include negative criteria

---

## AP-10: User Story Stuffing

**Description:** User stories are too large, essentially being epics disguised as stories.

**Severity:** MEDIUM

**Detection Heuristics:**
- Single story covers multiple features
- Story cannot be completed in one sprint
- Story has multiple acceptance criteria covering different functions
- "As a user I want to manage all aspects of..."
- AND clauses in the "I want" portion

**Detection Signals:**
```
⚠ "As a user I want to manage my account, update settings, and handle billing..."
⚠ Story estimated at >13 points
⚠ Multiple features in one story
⚠ "I want" has AND clauses
⚠ AC covers disparate functionality
```

**Example Violation:**
> "As an admin, I want to manage users, configure permissions, generate reports, set up integrations, and customize branding."

**Impact:**
- Estimation fails
- Sprint planning unreliable
- Stories never "done"
- Progress hard to track

**Remediation:**
1. Split into independent stories
2. Ensure each story is completable in < 3 days
3. Remove AND from "I want"
4. One "so that" benefit per story
5. Apply INVEST criteria

---

## AP-11: Risk Minimization

**Description:** Risks are downplayed or ignored entirely.

**Severity:** HIGH

**Detection Heuristics:**
- No risk section
- Only minor risks listed
- No mitigation plans
- "Low risk" assessment without analysis
- Known issues not acknowledged

**Detection Signals:**
```
⚠ No risks section exists
⚠ "This project has minimal risk"
⚠ Only 1-2 minor risks listed
⚠ High-impact risks without mitigation
⚠ Technical unknowns not called out
```

**Impact:**
- Unprepared for problems
- No contingency plans
- Surprised by predictable issues
- Delayed response when risks materialize

**Remediation:**
1. Add comprehensive risk register
2. Include technical, business, and execution risks
3. Document mitigation for each risk
4. Assign risk owners
5. Define triggers and response plans

---

## AP-12: Technical Debt Deferral

**Description:** Technical considerations are ignored or deferred indefinitely.

**Severity:** MEDIUM

**Detection Heuristics:**
- No technical considerations section
- "We'll address technical debt later"
- Architecture impact ignored
- No mention of existing system constraints
- Migration needs unaddressed

**Detection Signals:**
```
⚠ No technical section exists
⚠ "Technical details to be worked out"
⚠ Existing architecture ignored
⚠ "Scalability: future consideration"
⚠ No mention of monitoring/observability
```

**Impact:**
- Accumulating technical debt
- Architecture constraints hit late
- Performance problems post-launch
- Maintenance burden grows

**Remediation:**
1. Add technical considerations section
2. Get engineering review before finalizing
3. Document known technical constraints
4. Acknowledge debt being created
5. Plan for technical improvements

---

## AP-13: Stakeholder Exclusion

**Description:** Key stakeholders not involved, leading to late feedback loops.

**Severity:** HIGH

**Detection Heuristics:**
- Legal/Compliance not consulted for regulated features
- Security not involved for auth/data features
- Ops not included for infrastructure needs
- Customer-facing teams not consulted
- No stakeholder review documented

**Detection Signals:**
```
⚠ Security feature with no security review
⚠ Compliance requirement with no legal input
⚠ Customer-facing change without CS input
⚠ Infrastructure needs without ops review
⚠ "Will be reviewed later" for critical stakeholders
```

**Impact:**
- Late vetoes from forgotten stakeholders
- Significant rework late in project
- Compliance or security issues
- Launch delays

**Remediation:**
1. Identify all affected stakeholders early
2. Get input from specialist teams (legal, security)
3. Document stakeholder reviews conducted
4. Include support/ops for operational features
5. Build stakeholder review into timeline

---

## AP-14: Scope Definition Deficit

**Description:** What's in scope is unclear, leading to different interpretations.

**Severity:** CRITICAL

**Detection Heuristics:**
- No explicit "In Scope" section
- Boundaries described vaguely
- Conflicting scope statements
- Phase/version scope unclear
- Easy to argue either way on inclusions

**Detection Signals:**
```
⚠ "Scope: User management features"
⚠ Different team members have different scope understanding
⚠ No explicit list of what's included
⚠ "Scope may evolve..."
⚠ Phase 1 vs Phase 2 not defined
```

**Impact:**
- Different expectations across team
- Scope debates throughout project
- Surprise discoveries late
- Rework from misalignment

**Remediation:**
1. Create explicit "In Scope" list
2. Create explicit "Out of Scope" list
3. Define phase boundaries clearly
4. Get alignment sign-off
5. Create change management process

---

## AP-15: Priority Inflation

**Description:** Everything is marked as highest priority, making prioritization meaningless.

**Severity:** MEDIUM

**Detection Heuristics:**
- All requirements marked P0 or "Must Have"
- No P2/P3 or "Nice to Have" items
- "Critical" used liberally
- No prioritization rationale
- Prioritization done by loudest voice

**Detection Signals:**
```
⚠ All 50 requirements are P0
⚠ No "Nice to Have" section
⚠ Every item is "critical for launch"
⚠ No priority criteria documented
⚠ "We need everything"
```

**Impact:**
- Can't make scope tradeoffs
- Timeline pressure impossible to manage
- Everything delivered late
- Team can't focus

**Remediation:**
1. Force rank all requirements
2. Use MoSCoW or similar framework
3. Limit P0/Must-Have to true essentials
4. Document prioritization criteria
5. Get stakeholder buy-in on priorities

---

## AP-16: Persona Proliferation

**Description:** Too many user personas dilute focus.

**Severity:** MEDIUM

**Detection Heuristics:**
- More than 4-5 personas defined
- No primary persona identified
- Personas overlap significantly
- Trying to serve everyone
- Each stakeholder added their persona

**Detection Signals:**
```
⚠ 8+ distinct personas listed
⚠ "Primary personas: A, B, C, D, E, F"
⚠ Personas differ only slightly
⚠ "We serve all user types"
⚠ No prioritization of personas
```

**Impact:**
- Design tries to please everyone
- Pleases no one effectively
- Conflicting requirements
- Feature bloat

**Remediation:**
1. Identify ONE primary persona
2. Limit to 3-4 total personas
3. Ensure personas are meaningfully different
4. Define primary vs secondary
5. Design for primary, accommodate secondary

---

## AP-17: Requirements Spaghetti

**Description:** Requirements are scattered, duplicated, and untraceable.

**Severity:** HIGH

**Detection Heuristics:**
- Same requirement appears in multiple places
- No requirement IDs
- Requirements in prose paragraphs
- No traceability to user needs
- Can't tell if all requirements are captured

**Detection Signals:**
```
⚠ Requirement X appears in 3 different sections
⚠ No requirement numbering/IDs
⚠ Requirements buried in prose
⚠ No requirements table/list
⚠ "See also..." with circular references
```

**Impact:**
- Requirements missed in implementation
- Duplicated work
- Conflicting versions of same requirement
- Cannot verify completeness

**Remediation:**
1. Create single requirements list
2. Assign unique ID to each requirement
3. Use structured format (not prose)
4. Eliminate duplicates
5. Create traceability matrix

---

## Anti-Pattern Detection Checklist

Quick scan for anti-patterns:

```
[ ] AP-01: Is there an "Out of Scope" section?
[ ] AP-02: Do requirements describe WHAT not HOW?
[ ] AP-03: Is there a single decision maker?
[ ] AP-04: Are success metrics specific and measurable?
[ ] AP-05: Are assumptions documented?
[ ] AP-06: Are error cases and edge cases covered?
[ ] AP-07: Are all dependencies identified?
[ ] AP-08: Is the timeline realistic?
[ ] AP-09: Are acceptance criteria testable?
[ ] AP-10: Are user stories appropriately sized?
[ ] AP-11: Are risks comprehensively documented?
[ ] AP-12: Are technical considerations addressed?
[ ] AP-13: Have all key stakeholders been consulted?
[ ] AP-14: Is scope explicitly defined?
[ ] AP-15: Is prioritization meaningful (not all P0)?
[ ] AP-16: Is there a focused set of personas?
[ ] AP-17: Are requirements organized and traceable?
```

---

## Integration with Gap Detection

Anti-patterns are detected in **Phase 4** of the audit workflow:

1. After item-by-item verification (Phase 3)
2. Scan for anti-pattern signals
3. Document instances with evidence
4. Include in GAP-INVENTORY output
5. Generate anti-pattern specific remediation

```xml
<anti_patterns>
  <pattern id="AP-02">
    <name>Solution Contamination</name>
    <instances>
      <instance location="Requirements section, line 45">
        "Use React to build the component..."
      </instance>
      <instance location="User Story 7">
        "Implement with Redux..."
      </instance>
    </instances>
    <remediation>Reframe as user needs, move implementation to tech spec</remediation>
  </pattern>
</anti_patterns>
```
