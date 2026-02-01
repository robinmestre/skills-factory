# RISK-ASSESSMENT Output Template

Primary output artifact for the Assumption Validator skill. Compliant with CONTRACT-08 from `artifact-contracts.yaml`.

---

## Template Overview

The RISK-ASSESSMENT artifact captures:
- What was assessed and how
- Assumptions that were surfaced
- Risks derived from assumption analysis
- Mitigations for identified risks
- Go/no-go recommendation

---

## XML Schema

```xml
<risk_assessment contract="CONTRACT-08" version="2.0">

  <!-- ═══════════════════════════════════════════════════════════════════════
       METADATA SECTION
       Basic identification and context for the assessment
       ═══════════════════════════════════════════════════════════════════════ -->
  <metadata>
    <artifact_id>[UNIQUE-ID: e.g., RA-2024-001]</artifact_id>
    <created>[ISO 8601 timestamp]</created>
    <skill>assumption-validator</skill>
    <skill_version>2.0</skill_version>
  </metadata>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUBJECT SECTION
       What was risk-assessed
       ═══════════════════════════════════════════════════════════════════════ -->
  <subject>
    <subject_reference>[Identifier or title of assessed artifact]</subject_reference>
    <subject_type>[decision | strategy | plan | architecture | investment | product_direction]</subject_type>
    <description>[Brief description of what was assessed]</description>
    <stakeholders>
      <stakeholder>[Primary stakeholder 1]</stakeholder>
      <stakeholder>[Primary stakeholder 2]</stakeholder>
    </stakeholders>
  </subject>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ASSESSMENT METHOD SECTION
       How the assessment was conducted
       ═══════════════════════════════════════════════════════════════════════ -->
  <assessment_method>
    <technique>assumption_validation</technique>
    <validation_intensity>[light | standard | rigorous]</validation_intensity>
    <assumption_depth>[explicit_only | include_implicit | full_structural]</assumption_depth>
    <counterfactual_analysis>[true | false]</counterfactual_analysis>
    <time_horizon>[short_term | medium_term | long_term | all]</time_horizon>
    <confidence_threshold>[0.0-1.0]</confidence_threshold>

    <surfacing_techniques_applied>
      <technique>document_scan</technique>
      <technique>inversion</technique>
      <technique>pre_mortem</technique>
      <technique>frame_questioning</technique>
      <!-- List all techniques actually applied -->
    </surfacing_techniques_applied>

    <assumptions_surfaced>
      <total>[Number of assumptions identified]</total>
      <by_type>
        <explicit>[Count]</explicit>
        <implicit>[Count]</implicit>
        <structural>[Count]</structural>
        <load_bearing>[Count]</load_bearing>
        <contextual>[Count]</contextual>
        <behavioral>[Count]</behavioral>
      </by_type>
      <validated>[Count of assumptions validated]</validated>
      <unvalidated>[Count remaining unvalidated]</unvalidated>
    </assumptions_surfaced>
  </assessment_method>

  <!-- ═══════════════════════════════════════════════════════════════════════
       KEY ASSUMPTIONS SECTION
       Summary of the most critical assumptions
       ═══════════════════════════════════════════════════════════════════════ -->
  <key_assumptions>
    <!-- Top 5-7 most important assumptions -->
    <assumption id="A1" load_bearing="true">
      <statement>[Clear assumption statement]</statement>
      <type>[EXPLICIT | IMPLICIT | STRUCTURAL | CONTEXTUAL | BEHAVIORAL]</type>
      <confidence>[0.0-1.0]</confidence>
      <epistemic_label>[VERIFIED | LIKELY | POSSIBLE | SPECULATIVE | UNKNOWN]</epistemic_label>
      <validation_status>[VALIDATED | PARTIAL | UNVALIDATED | INVALIDATED | CONTESTED]</validation_status>
      <risk_if_wrong>[Brief description of what happens if false]</risk_if_wrong>
    </assumption>

    <assumption id="A2" load_bearing="false">
      <statement>[Clear assumption statement]</statement>
      <type>[Type]</type>
      <confidence>[0.0-1.0]</confidence>
      <epistemic_label>[Label]</epistemic_label>
      <validation_status>[Status]</validation_status>
      <risk_if_wrong>[Brief description]</risk_if_wrong>
    </assumption>

    <!-- Additional key assumptions -->
  </key_assumptions>

  <!-- ═══════════════════════════════════════════════════════════════════════
       RISKS SECTION
       Risks derived from assumption analysis
       ═══════════════════════════════════════════════════════════════════════ -->
  <risks>
    <risk id="R1">
      <category>[assumption_failure | dependency | cascade | behavioral | contextual | structural]</category>
      <description>[Clear description of the risk]</description>
      <source_assumptions>
        <ref assumption_id="A1"/>
        <ref assumption_id="A3"/>
        <!-- Assumptions that give rise to this risk -->
      </source_assumptions>
      <trigger>[What would cause this risk to materialize]</trigger>

      <assessment>
        <probability>[very_low | low | medium | high | very_high]</probability>
        <probability_rationale>[Why this probability]</probability_rationale>
        <impact>[negligible | minor | moderate | major | catastrophic]</impact>
        <impact_rationale>[Why this impact level]</impact_rationale>
        <risk_score>[1.0-5.0, calculated from probability × impact]</risk_score>
      </assessment>

      <mitigation>
        <strategy>[avoid | transfer | mitigate | accept]</strategy>
        <actions>
          <action owner="[Role]" timeline="[When]">[Specific mitigation action]</action>
          <action owner="[Role]" timeline="[When]">[Another action]</action>
        </actions>
        <residual_risk>[eliminated | reduced | unchanged]</residual_risk>
        <residual_risk_level>[Very Low | Low | Medium | High]</residual_risk_level>
      </mitigation>

      <monitoring>
        <early_warning>[Signal to watch]</early_warning>
        <trigger_condition>[When to escalate]</trigger_condition>
        <owner>[Who monitors]</owner>
      </monitoring>
    </risk>

    <risk id="R2">
      <!-- Structure repeats for each risk -->
    </risk>

    <!-- Additional risks -->
  </risks>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUMMARY SECTION
       Overall assessment and recommendation
       ═══════════════════════════════════════════════════════════════════════ -->
  <summary>
    <total_risks>[Count of risks identified]</total_risks>
    <risks_by_severity>
      <critical>[Count]</critical>
      <high>[Count]</high>
      <medium>[Count]</medium>
      <low>[Count]</low>
    </risks_by_severity>

    <risk_profile>[very_high | high | moderate | low | very_low]</risk_profile>
    <risk_profile_rationale>[Why this profile]</risk_profile_rationale>

    <top_risks>
      <ref risk_id="R1">[Brief: Why this is top risk]</ref>
      <ref risk_id="R3">[Brief: Why this is top risk]</ref>
      <ref risk_id="R5">[Brief: Why this is top risk]</ref>
    </top_risks>

    <critical_assumptions>
      <!-- Assumptions that if wrong would change the entire assessment -->
      <ref assumption_id="A1">[Brief: Why critical]</ref>
      <ref assumption_id="A4">[Brief: Why critical]</ref>
    </critical_assumptions>

    <go_no_go_assessment>
      <recommendation>[proceed | proceed_with_caution | significant_concerns | do_not_proceed]</recommendation>
      <conditions>
        <!-- Conditions required for the recommendation to be valid -->
        <condition>[Condition 1 that must hold]</condition>
        <condition>[Condition 2 that must hold]</condition>
      </conditions>
    </go_no_go_assessment>

    <recommendation_narrative>
      [2-3 paragraph narrative summarizing:
       - Key findings from assumption analysis
       - Most significant risks and their implications
       - Recommended actions before proceeding
       - Conditions under which recommendation changes]
    </recommendation_narrative>

    <next_actions>
      <action priority="1">[Most important next action]</action>
      <action priority="2">[Second priority action]</action>
      <action priority="3">[Third priority action]</action>
    </next_actions>
  </summary>

  <!-- ═══════════════════════════════════════════════════════════════════════
       APPENDICES (Optional)
       Supporting detail for traceability
       ═══════════════════════════════════════════════════════════════════════ -->
  <appendices>
    <full_assumption_inventory ref="[Link to assumption-inventory output]"/>
    <sensitivity_analysis ref="[Link to sensitivity-analysis output]"/>
  </appendices>

</risk_assessment>
```

---

## Field Guidance

### Subject Section

| Field | Guidance |
|-------|----------|
| `subject_reference` | Unique identifier or descriptive title |
| `subject_type` | Must be one of the 6 valid types |
| `description` | 1-2 sentences describing what was assessed |
| `stakeholders` | List key stakeholders whose concerns were considered |

### Assessment Method Section

| Field | Guidance |
|-------|----------|
| `technique` | Always "assumption_validation" for this skill |
| `validation_intensity` | Must match parameter used |
| `surfacing_techniques_applied` | List actual techniques used, not all possible |
| `assumptions_surfaced` | Accurate counts from Phase 2-3 |

### Key Assumptions Section

Include 5-7 most important assumptions. Prioritize:
1. All load-bearing assumptions
2. Assumptions with validation issues (INVALIDATED, CONTESTED, UNVALIDATED)
3. Assumptions with low confidence (<0.5)

### Risks Section

| Field | Guidance |
|-------|----------|
| `category` | Primary category; use most specific applicable |
| `source_assumptions` | Link to assumptions that generate this risk |
| `trigger` | Specific, observable condition |
| `probability` | Based on assumption confidence |
| `impact` | Based on counterfactual analysis |
| `risk_score` | Calculated: probability × impact (1-5 scale each) |
| `mitigation.strategy` | One of: avoid, transfer, mitigate, accept |
| `mitigation.actions` | Specific, actionable, assigned |
| `residual_risk` | After mitigation is applied |

### Probability Scale

| Level | Value | Definition |
|-------|-------|------------|
| very_low | 1 | < 10% chance |
| low | 2 | 10-30% chance |
| medium | 3 | 30-60% chance |
| high | 4 | 60-85% chance |
| very_high | 5 | > 85% chance |

### Impact Scale

| Level | Value | Definition |
|-------|-------|------------|
| negligible | 1 | No meaningful impact |
| minor | 2 | Small inconvenience; <10% deviation |
| moderate | 3 | Significant rework; 10-30% deviation |
| major | 4 | Large-scale impact; >30% deviation |
| catastrophic | 5 | Project/strategy failure |

### Risk Score Interpretation

| Score Range | Severity | Action |
|-------------|----------|--------|
| 15-25 | CRITICAL | Block; must resolve before proceeding |
| 10-14 | HIGH | Address immediately; escalate |
| 5-9 | MEDIUM | Plan mitigation; monitor |
| 1-4 | LOW | Document; accept with monitoring |

### Go/No-Go Recommendation

| Recommendation | When to Use |
|----------------|-------------|
| `proceed` | Low/very low risk; key assumptions validated |
| `proceed_with_caution` | Moderate risk; mitigations in place |
| `significant_concerns` | High risk; critical assumptions unvalidated |
| `do_not_proceed` | Very high risk; load-bearing assumptions invalid |

---

## Validation Rules

Before finalizing RISK-ASSESSMENT:

- [ ] Every risk has probability AND impact assigned
- [ ] Risk scores are calculated correctly
- [ ] High-scoring risks (>10) have mitigation plans
- [ ] Source assumptions are linked for every risk
- [ ] Go/no-go recommendation is justified
- [ ] Top risks are identified (3-5 maximum)
- [ ] Critical assumptions are flagged
- [ ] Narrative summary is complete

---

## Example Output

```xml
<risk_assessment contract="CONTRACT-08" version="2.0">
  <metadata>
    <artifact_id>RA-2024-017</artifact_id>
    <created>2024-03-15T14:30:00Z</created>
    <skill>assumption-validator</skill>
    <skill_version>2.0</skill_version>
  </metadata>

  <subject>
    <subject_reference>ADR-042: Microservices Migration</subject_reference>
    <subject_type>architecture</subject_type>
    <description>Decision to migrate order processing from monolith to microservices architecture</description>
    <stakeholders>
      <stakeholder>CTO</stakeholder>
      <stakeholder>VP Engineering</stakeholder>
      <stakeholder>Platform Team Lead</stakeholder>
    </stakeholders>
  </subject>

  <assessment_method>
    <technique>assumption_validation</technique>
    <validation_intensity>rigorous</validation_intensity>
    <assumption_depth>full_structural</assumption_depth>
    <counterfactual_analysis>true</counterfactual_analysis>
    <time_horizon>long_term</time_horizon>
    <confidence_threshold>0.7</confidence_threshold>

    <surfacing_techniques_applied>
      <technique>document_scan</technique>
      <technique>inversion</technique>
      <technique>five_whys</technique>
      <technique>pre_mortem</technique>
      <technique>dependency_mapping</technique>
      <technique>frame_questioning</technique>
      <technique>expert_challenge</technique>
    </surfacing_techniques_applied>

    <assumptions_surfaced>
      <total>14</total>
      <by_type>
        <explicit>4</explicit>
        <implicit>6</implicit>
        <structural>2</structural>
        <load_bearing>3</load_bearing>
        <contextual>1</contextual>
        <behavioral>3</behavioral>
      </by_type>
      <validated>8</validated>
      <unvalidated>6</unvalidated>
    </assumptions_surfaced>
  </assessment_method>

  <key_assumptions>
    <assumption id="A3" load_bearing="true">
      <statement>Engineering team has sufficient microservices expertise to execute migration</statement>
      <type>BEHAVIORAL</type>
      <confidence>0.35</confidence>
      <epistemic_label>SPECULATIVE</epistemic_label>
      <validation_status>UNVALIDATED</validation_status>
      <risk_if_wrong>Delays, poor architecture decisions, production incidents</risk_if_wrong>
    </assumption>

    <assumption id="A7" load_bearing="true">
      <statement>Service boundaries can be cleanly defined from existing domain model</statement>
      <type>IMPLICIT</type>
      <confidence>0.50</confidence>
      <epistemic_label>POSSIBLE</epistemic_label>
      <validation_status>PARTIAL</validation_status>
      <risk_if_wrong>Distributed monolith; worse than before</risk_if_wrong>
    </assumption>

    <assumption id="A1" load_bearing="false">
      <statement>Current monolith cannot scale beyond 10K concurrent users</statement>
      <type>EXPLICIT</type>
      <confidence>0.65</confidence>
      <epistemic_label>POSSIBLE</epistemic_label>
      <validation_status>PARTIAL</validation_status>
      <risk_if_wrong>Migration may not be necessary; could optimize monolith</risk_if_wrong>
    </assumption>
  </key_assumptions>

  <risks>
    <risk id="R1">
      <category>behavioral</category>
      <description>Team capability gap causes delivery failure and quality issues</description>
      <source_assumptions>
        <ref assumption_id="A3"/>
      </source_assumptions>
      <trigger>Team attempts complex distributed system design without expertise</trigger>

      <assessment>
        <probability>high</probability>
        <probability_rationale>Only 1 team member has production microservices experience</probability_rationale>
        <impact>major</impact>
        <impact_rationale>Would cause 6-12 month delay and significant rework</impact_rationale>
        <risk_score>16</risk_score>
      </assessment>

      <mitigation>
        <strategy>mitigate</strategy>
        <actions>
          <action owner="VP Engineering" timeline="Before project start">Hire 2+ engineers with microservices production experience</action>
          <action owner="Platform Lead" timeline="Q1">Engage architecture consultancy for design review</action>
          <action owner="Engineering Manager" timeline="Ongoing">Implement pair programming with experienced hires</action>
        </actions>
        <residual_risk>reduced</residual_risk>
        <residual_risk_level>Medium</residual_risk_level>
      </mitigation>

      <monitoring>
        <early_warning>Code review quality scores; architecture decision conflicts</early_warning>
        <trigger_condition>More than 2 significant architecture pivots in first quarter</trigger_condition>
        <owner>VP Engineering</owner>
      </monitoring>
    </risk>

    <risk id="R2">
      <category>structural</category>
      <description>Service boundaries are wrong, creating distributed monolith</description>
      <source_assumptions>
        <ref assumption_id="A7"/>
      </source_assumptions>
      <trigger>Team defines services based on existing code modules rather than domain boundaries</trigger>

      <assessment>
        <probability>medium</probability>
        <probability_rationale>Domain model exists but hasn't been validated for service decomposition</probability_rationale>
        <impact>catastrophic</impact>
        <impact_rationale>Distributed monolith would be worse than current state; 12+ month recovery</impact_rationale>
        <risk_score>15</risk_score>
      </assessment>

      <mitigation>
        <strategy>mitigate</strategy>
        <actions>
          <action owner="Platform Lead" timeline="Pre-project">Conduct event storming workshop to validate domain boundaries</action>
          <action owner="Architect" timeline="Q1">Define service contracts before implementation</action>
          <action owner="Tech Lead" timeline="Ongoing">Implement fitness functions to detect coupling</action>
        </actions>
        <residual_risk>reduced</residual_risk>
        <residual_risk_level>Medium</residual_risk_level>
      </mitigation>

      <monitoring>
        <early_warning>Cross-service call frequency; shared database access patterns</early_warning>
        <trigger_condition>Any service making >50 calls to another service per request</trigger_condition>
        <owner>Platform Lead</owner>
      </monitoring>
    </risk>
  </risks>

  <summary>
    <total_risks>7</total_risks>
    <risks_by_severity>
      <critical>0</critical>
      <high>2</high>
      <medium>3</medium>
      <low>2</low>
    </risks_by_severity>

    <risk_profile>high</risk_profile>
    <risk_profile_rationale>Two high-scoring risks with load-bearing assumptions at low confidence</risk_profile_rationale>

    <top_risks>
      <ref risk_id="R1">Team capability gap is unmitigated; hiring not started</ref>
      <ref risk_id="R2">Service boundary definition hasn't been validated</ref>
    </top_risks>

    <critical_assumptions>
      <ref assumption_id="A3">Team expertise (0.35 confidence) - everything depends on execution capability</ref>
      <ref assumption_id="A7">Service boundaries (0.50 confidence) - wrong boundaries cause distributed monolith</ref>
    </critical_assumptions>

    <go_no_go_assessment>
      <recommendation>significant_concerns</recommendation>
      <conditions>
        <condition>Hire 2+ experienced microservices engineers before project kickoff</condition>
        <condition>Complete event storming workshop to validate service boundaries</condition>
        <condition>Engage external architecture review for first milestone</condition>
      </conditions>
    </go_no_go_assessment>

    <recommendation_narrative>
      The microservices migration decision rests on two load-bearing assumptions with low confidence: team expertise (A3, 0.35) and service boundary clarity (A7, 0.50). Without addressing these, the project has high probability of failure.

      The most significant risk is team capability gap (R1). With only one team member having production microservices experience, attempting a complex distributed system migration is high-risk. The mitigation (hiring, consultancy) is sound but not yet executed.

      Recommend NOT proceeding until conditions are met: complete hiring of experienced engineers, validate domain boundaries through event storming, and secure architecture consulting engagement. With these mitigations in place, risk profile would drop to moderate and recommendation would change to proceed_with_caution.
    </recommendation_narrative>

    <next_actions>
      <action priority="1">Post job requisitions for 2 senior microservices engineers</action>
      <action priority="2">Schedule event storming workshop with domain experts</action>
      <action priority="3">Identify and engage architecture consultancy</action>
    </next_actions>
  </summary>

  <appendices>
    <full_assumption_inventory ref="AI-2024-017"/>
    <sensitivity_analysis ref="SA-2024-017"/>
  </appendices>

</risk_assessment>
```

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Core contract | `core/artifact-contracts.yaml` CONTRACT-08 |
| Scoring rubric | `core/scoring-rubrics.yaml` RUBRIC-07 |
| Confidence labels | `references/confidence-calibration.md` |
| What-if analysis | `references/what-if-framework.md` |
| Assumption inventory | `templates/assumption-inventory-output.md` |
