# Vibekit Documentation

Generate domain-specific skills by composing techniques from established archetypes. Transform complex workflows into discrete, composable skills that leverage advanced AI reasoning techniques.

## When to Use

Trigger this workflow when asked to:
- "Create a skill for [domain]"
- "Generate [domain] analysis skill"
- "Build a skill that does [task]"
- "Vibekit: [description]"
- "Analyze this process", "Map this workflow", "Decompose this"
- "Design skill chain for", "Orchestrate"

---

## The 8 Canonical Archetypes

| Archetype | ID | Purpose | Primary Output | When to Use |
|-----------|-----|---------|----------------|-------------|
| **Evaluate** | EVAL | Multi-perspective assessment | Decision recommendation | Choosing between options, ranking, prioritization |
| **Audit** | AUDIT | Systematic gap detection | Gap inventory + remediation | Reviewing completeness, compliance verification |
| **Synthesize** | SYNTH | Multi-source consolidation | Unified findings | Combining research, reconciling contradictions |
| **Validate** | VALID | Stress-test assumptions | Risk assessment | Challenging strategy, pre-mortem analysis |
| **Transform** | XFORM | Format conversion | Structured artifact | Converting unstructured → structured |
| **Elicit** | ELICIT | Knowledge extraction | Documented decisions | Interviews, requirements gathering |
| **Generate** | GEN | Document creation | Complete document | Templates, specs, reports |
| **Orchestrate** | ORCH | Workflow coordination | Prompts or skill chains | Multi-skill composition, meta-operations |

### Archetype Selection Rules

```
IF task compares options or perspectives → EVAL
IF task validates completeness or compliance → AUDIT
IF task combines multiple sources → SYNTH
IF task stress-tests or challenges → VALID
IF task converts format or structure → XFORM
IF task extracts knowledge through questions → ELICIT
IF task produces documents from templates → GEN
IF task coordinates other skills/prompts → ORCH
```

### Archetype Patterns & Techniques

| Archetype | Pattern | Key Techniques | Token Budget |
|-----------|---------|----------------|--------------|
| **EVAL** | Multi-perspective → Tournament ranking → Adversarial validation → Recommendation | multi_persona_simulation, pairwise_tournament, bradley_terry, true_steel_manning, confidence_calibration | 6-10K |
| **AUDIT** | MECE scope → Exhaustive enumeration → Consistency verification → Gap analysis → Findings | mece_decomposition, complete_assumption_inventory, full_consistency_matrix, mece_gap_detection | 8-15K |
| **SYNTH** | Multi-source collection → Cross-reference → Confidence tiering → Unified framework | source_provenance_tracking, corroboration_matrix, confidence_tiering, unified_framework_synthesis | 6-10K |
| **VALID** | Assumption extraction → Disconfirmation → Scenario stress-test → Risk assessment | complete_assumption_inventory, disconfirmation_hunt, pre_mortem_analysis, sensitivity_analysis | 6-10K |

### Embedded Techniques by Archetype

Do NOT make these standalone skills:

| Archetype | Embedded Techniques |
|-----------|---------------------|
| EVAL | Red/Blue team, Bradley-Terry scoring, Sensitivity analysis, Stakeholder simulation, Pairwise comparison |
| AUDIT | Checklist validation, Coverage mapping, Compliance verification, Severity scoring, Anti-pattern detection |
| SYNTH | Claim extraction, Agreement matrix, Source triangulation, Gap identification, Citation quality scoring |
| VALID | Pre-mortem, Assumption surfacing, Inversion, Devil's advocate, Failure mode enumeration |
| XFORM | Format mapping, Schema validation, Contamination detection, Normalization |
| ELICIT | Progressive disclosure questioning, Follow-up branching, Completion criteria, Context synthesis |
| GEN | Template instantiation, Style enforcement, Cross-reference validation, Progressive disclosure tiering |
| ORCH | Skill chaining, Dependency management, State serialization, Conditional branching |

---

## Process Decomposition

**What you do**: Break complex workflows into discrete steps, identify decision points, map information flows, and determine skill boundaries.

### Decision Framework for Skill Boundaries

| Signal | Recommendation |
|--------|----------------|
| Step produces a distinct artifact | Separate skill |
| Step requires different archetype | Separate skill |
| Steps share context and must execute atomically | Single skill |
| Step is single-shot chain-of-thought | Embedded technique, not skill |
| Step is reused across multiple workflows | Separate skill (for composition) |

### Process Analysis Protocol

1. **Identify inputs**: What triggers the process? What information is required?
2. **Map transformations**: What changes between input and output?
3. **Locate decision points**: Where does the process branch based on conditions?
4. **Trace dependencies**: What must exist before each step can execute?
5. **Define outputs**: What artifacts are produced? Who consumes them?

---

## Skill Generation Workflow

### Phase 1: Requirements

1. **Identify core task**: What decision/analysis/audit? What output? Who consumes it?
2. **Select archetype**: Use archetype table above
3. **Identify domain**: architecture, product, strategy, research, security, data_modeling, operations, content
4. **Set token budget**: Minimal (~3-4K), Standard (~6-8K), Comprehensive (~10-15K)

### Phase 2: Technique Selection

1. **Load archetype file** from project knowledge
2. **Select techniques by phase** using archetype's `composition_rules`
3. **Apply domain configurations** (personas, lenses, criteria, edge case dimensions)
4. **Verify synergies**, avoid conflicts

### Phase 3: Skill Assembly

Generate complete SKILL.md with these sections:

```markdown
---
name: [domain]-[task]-skill
description: >
  [What it does, when to use, output type. Include trigger phrases.]
---

# [Skill Name]

[Brief overview]

<workflow>
## Execution Workflow
[Numbered steps from archetype phases, reference technique IDs]
</workflow>

<[domain]_configuration>
## Domain Configuration
[Pre-configured personas, lenses, criteria from technique metadata]
</[domain]_configuration>

<output_structure>
## Output Template
[Combined outputs from all selected techniques—complete artifact, not outline]
</output_structure>

<configurable_parameters>
## Parameters
| Parameter | Default | Options | When to Change |
</configurable_parameters>

<quality_gates>
## Quality Checklist
- [ ] [Gates derived from technique quality_criteria]
</quality_gates>

<technique_provenance>
## Technique Sources
| Phase | Technique | Source File |
</technique_provenance>
```

### Phase 4: Validation

- [ ] XML tags for major sections
- [ ] Under 500 lines
- [ ] All archetype phases represented
- [ ] Domain configurations applied (not generic)
- [ ] Output template is complete artifact
- [ ] Token estimate realistic

---

## Skill Specification Template (YAML)

```yaml
skill_id: [ARCHETYPE_CODE][NUMBER]  # e.g., E01, A02, S03
name: [Descriptive Name]
archetype: [EVAL | AUDIT | SYNTH | VALID | XFORM | ELICIT | GEN | ORCH]
domain: [architecture | product | strategy | research | security | operations]

purpose: |
  [One paragraph: What problem does this solve? What's the output?]

triggers:
  - "[Phrase that invokes this skill]"
  - "[Alternative trigger]"

inputs:
  - name: [input_name]
    type: [string | list | document | etc.]
    required: [true | false]
    description: [What this input is]

outputs:
  - name: [output_name]
    type: [artifact type]
    description: [What this output contains]

embedded_techniques:
  - [technique_1]: [brief purpose]
  - [technique_2]: [brief purpose]

workflow:
  phases:
    - name: "[Phase 1 Name]"
      techniques: [technique_1, technique_2]
      output: [intermediate artifact]
      quality_gate: "[Testable condition]"

    - name: "[Phase 2 Name]"
      techniques: [technique_3]
      output: [final artifact]
      quality_gate: "[Testable condition]"

quality_gates:
  - gate: "[Gate name]"
    condition: "[Testable condition]"
    severity: [error | warning]
    remediation: "[What to do if failed]"

anti_patterns:
  - pattern: "[Thing to avoid]"
    why: "[Why it's problematic]"
    instead: "[What to do instead]"

assumptions:
  - "[Assumption about inputs or context]"

confidence: [percentage]
confidence_rationale: |
  [Why this confidence level]
```

---

## Skill Composition

### Composition Principles

- **Loose coupling**: Skills communicate via artifacts, not shared state
- **Single responsibility**: Each skill does one thing well
- **Progressive disclosure**: Complex outputs tier information by audience
- **Fail-fast**: Quality gates catch problems early

### Synergy Matrix

| Combination | Synergy | Rationale |
|-------------|---------|-----------|
| EVAL → VALID | ★★★★★ | Evaluate options, then stress-test winner |
| SYNTH → EVAL | ★★★★★ | Synthesize research, then evaluate implications |
| ELICIT → XFORM | ★★★★☆ | Extract knowledge, then structure it |
| AUDIT → GEN | ★★★★☆ | Find gaps, then generate remediation |
| ORCH → any | ★★★☆☆ | Orchestration adds overhead; use only when composition is non-trivial |

### Anti-Pattern Compositions (Avoid)

| Anti-Pattern | Problem |
|--------------|---------|
| EVAL → EVAL | Recursion without new information |
| ORCH → ORCH | Meta-orchestration explosion |
| VALID → VALID | Infinite regress of validation |
| Any skill with >5 embedded techniques | Context explosion, quality degradation |

### Skill Chain Design

1. Identify required archetypes in sequence
2. Define artifact contract between skills (what passes between them)
3. Specify handoff conditions (when does control transfer?)
4. Design rollback strategy (what if a skill fails?)
5. Set iteration limits (prevent infinite loops)

---

## Quality Gate Design

Every skill must have quality gates. Gates must be:
- **Testable**: Can objectively verify pass/fail
- **Actionable**: Failure triggers specific remediation
- **Non-blocking where appropriate**: Warnings vs. hard stops

### Standard Gate Categories

| Gate Type | Purpose | Example |
|-----------|---------|---------|
| **Input validation** | Verify inputs meet requirements | "All required fields present" |
| **Completeness check** | Ensure nothing omitted | "All options evaluated" |
| **Consistency check** | No internal contradictions | "Recommendations align with findings" |
| **Confidence threshold** | Minimum certainty to proceed | "Confidence ≥70% on primary claim" |
| **Coverage verification** | Required dimensions addressed | "All stakeholder perspectives included" |

### Gate Design Protocol

1. What could go wrong at this step?
2. How would we detect it?
3. What's the remediation if detected?
4. Is this a warning or a hard stop?

---

## Decision Protocols

### Protocol 1: "Should this be a skill or a technique?"

```
START
│
├─ Does it produce a distinct artifact?
│   ├─ YES → Skill
│   └─ NO ──┐
│           │
├─ Is it multi-step with complex logic?
│   ├─ YES → Skill
│   └─ NO ──┐
│           │
├─ Is it reused across 3+ workflows?
│   ├─ YES → Skill (for composition)
│   └─ NO → Embedded technique
```

### Protocol 2: "Which archetype?"

```
START
│
├─ Are we choosing between options? → EVAL
├─ Are we checking completeness/compliance? → AUDIT
├─ Are we combining multiple sources? → SYNTH
├─ Are we stress-testing a decision? → VALID
├─ Are we converting format? → XFORM
├─ Are we extracting knowledge through questions? → ELICIT
├─ Are we producing a document from template? → GEN
├─ Are we coordinating multiple skills? → ORCH
```

### Protocol 3: "How many skills for this process?"

```
Count the number of:
- Distinct output artifacts: A
- Archetype changes: B
- Reusable components: C

Minimum skills = max(A, B)
Consider additional skills for C if reuse value > composition overhead
```

### Protocol 4: "Is this composition safe?"

```
CHECK:
□ No archetype appears twice consecutively without new input
□ Total embedded techniques across chain ≤ 12
□ Each skill has defined artifact contract
□ Iteration limits specified for any loops
□ Rollback strategy exists for critical skills
```

---

## Domain Configuration Reference

### Architecture Domain

**Personas**: Security Architect, Platform Engineer, Developer Experience, Cost Optimizer, Business Stakeholder

**Lenses**: Quality Attributes, Evolutionary Architecture, DDD, Cloud-Native, Cost-Efficiency

**Criteria**: Scalability (0.20), Maintainability (0.20), Security (0.20), Cost (0.15), Time (0.15), Reversibility (0.10)

**Edge Dimensions**: Load, Data State, Timing, Network, Dependencies

### Product Domain

**Personas**: Power User, Casual User, Enterprise Buyer, Churned User, Competitor Observer

**Lenses**: Jobs-to-be-Done, Blue Ocean, Kano Model, Lean Startup, Network Effects

**Criteria**: User Value (0.25), Business Value (0.20), Feasibility (0.20), Speed (0.15), Alignment (0.10), Risk (0.10)

### Strategy Domain

**Personas**: Board Member, Investor, Employee, Customer, Competitor

**Lenses**: Porter's Five Forces, Wardley Mapping, Resource-Based View, Game Theory, Real Options

### Security Domain

**MECE Dimensions**: Attack Surface (Network/App/Data/Identity/Physical), Control Type (Preventive/Detective/Corrective/Compensating)

**Edge Dimensions**: Authentication State, Input Content, Rate, Origin

**Invariants**: Safety (data integrity, access control), Confidentiality, Availability

---

## Token Budget Guidelines

### Minimal (~3-4K)

**EVAL**: multi_persona (4, shallow) → pairwise_tournament → confidence_calibration

**AUDIT**: completeness_verification → full_consistency_matrix → prioritized_findings_report

### Standard (~6-8K)

**EVAL**: multi_persona (5) → pairwise + bradley_terry → true_steel_manning (3 args) → confidence_calibration

**AUDIT**: mece_decomposition → assumption_inventory → consistency_matrix → mece_gap_detection → findings_report

### Comprehensive (~10-15K)

**EVAL**: multi_persona (6+, deep) + multi_lens (5) + multi_criteria (6) → tournament + bradley_terry → steel_manning + adversarial_collaboration + disconfirmation → confidence + scqa

**AUDIT**: All Phase 1-5 techniques with full depth

---

## Advanced Technique Categories

For complex skills requiring specialized reasoning:

| Category | Techniques | Use When |
|----------|------------|----------|
| **Parallel Processing** | Multi-hypothesis tracking, Multi-lens analysis, Parallel future cones | Multiple valid framings exist simultaneously |
| **Perfect Recall** | Complete assumption inventory, Exhaustive enumeration, Full traceability | Completeness is critical, nothing can be missed |
| **Unbiased Reasoning** | Disconfirmation hunt, True steel-manning, Base rate integration | Decision has high stakes, confirmation bias risk |
| **Meta-Cognitive** | Logical chain audit, Confidence calibration, Uncertainty decomposition | Need to verify own reasoning quality |

---

## Scoring Framework (for prioritization)

When prioritizing which skills to build:

**Impact** = (EPV × 0.30) + (SA × 0.30) + (TSU × 0.25) + (F_adj × 0.15)
- EPV: Error Prevention Value (1-5)
- SA: Strategic Alignment / enables other skills (1-5)
- TSU: Time Saved per Use (1-5)
- F_adj: Frequency, adjusted for consequence magnitude (1-5)

**Effort** = (TC × 0.40) + (DC × 0.30) + (MC × 0.30)
- TC: Technical Complexity (1-5)
- DC: Domain Complexity (1-5)
- MC: Maintenance Complexity (1-5)

**Priority** = Impact / Effort
- >1.5: Build first
- 1.0-1.5: Build next
- <1.0: Build later

---

## Anti-Patterns

### Global Anti-Patterns

| Anti-Pattern | Detection Signal | Remediation |
|--------------|------------------|-------------|
| **MoE recursion** | Expert panel evaluating expert panels | Use decision tree for meta-selection, not MoE |
| **Context explosion** | >12 techniques in chain | Split into multiple skills with artifact handoffs |
| **Reflection without revision** | Checkpoints that never change direction | Gates must have power to halt or redirect |
| **Confidence cosplay** | Percentages without calibration | Use actual calibration methodology |
| **Gap-free claims** | "Complete analysis" without limitations | Always acknowledge what's not covered |
| **Infinite regress** | Validating the validation of the validation | 2-3 meta-levels maximum |
| **Artifact theater** | Producing documents no one consumes | Verify downstream consumer exists |

### Process Anti-Patterns

- Monolithic processes that try to do everything
- Circular dependencies between steps
- Implicit handoffs without defined contracts
- Decision points without clear criteria

### Skill Generation Anti-Patterns

| Anti-Pattern | Problem | Fix |
|--------------|---------|-----|
| Generic personas | "Stakeholder A, B" adds no value | Use domain-specific defaults |
| Outline not template | Output requires interpretation | Combine technique outputs completely |
| All techniques selected | Token explosion | Match to budget |
| Ignoring conflicts | Wasted tokens | Check synergies in metadata |
| No provenance | Can't trace to improve | Document technique sources |

### Quality Gate Anti-Patterns

| Anti-Pattern | Problem | Fix |
|--------------|---------|-----|
| Gates without teeth | Checkpoint exists but changes nothing | Gates must be able to halt or redirect |
| Unmeasurable criteria | "Ensure quality" | Specify what quality means operationally |
| All-or-nothing | Single failure kills entire workflow | Tier gates by severity |
| Gate explosion | 20 gates for a 3-step skill | 2-4 gates per skill maximum |

---

## Reference Loading

When designing skills, load these technique references as needed:

| File | Load When |
|------|-----------|
| `technique-taxonomy.yaml` | Always—for archetype routing |
| `moe-decision-techniques.yaml` | Archetype = EVAL with ranking |
| `comprehensive-audit-techniques.yaml` | Archetype = AUDIT |
| `research-synthesis-techniques.yaml` | Archetype = SYNTH |
| `strategy-validation-techniques.yaml` | Archetype = VALID |
| `meta-cognitive-techniques.md` | Need reasoning quality verification |

---

## Output Standards

All outputs must:

1. **Be actionable**: Consumer knows what to do with it
2. **Be testable**: Can verify correctness
3. **Include confidence**: Epistemic status is explicit
4. **Acknowledge gaps**: What's NOT covered is stated
5. **Reference sources**: Technique provenance is traceable
