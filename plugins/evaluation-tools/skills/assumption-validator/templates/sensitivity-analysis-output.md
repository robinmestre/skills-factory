# Sensitivity Analysis Output Template

Secondary output artifact for the Assumption Validator skill. Captures what-if analysis results showing how sensitive outcomes are to each key assumption.

---

## Template Overview

The Sensitivity Analysis captures:
- What-if scenarios for each analyzed assumption
- Impact magnitude if assumption is wrong
- Cascade effects and decision changes
- Overall decision robustness score
- Most sensitive assumptions ranked

---

## XML Schema

```xml
<sensitivity_analysis version="2.0">

  <!-- ═══════════════════════════════════════════════════════════════════════
       METADATA SECTION
       ═══════════════════════════════════════════════════════════════════════ -->
  <metadata>
    <artifact_id>[UNIQUE-ID: e.g., SA-2024-001]</artifact_id>
    <created>[ISO 8601 timestamp]</created>
    <subject_reference>[What was analyzed]</subject_reference>
    <subject_type>[decision | strategy | plan | architecture | investment | product_direction]</subject_type>
    <related_risk_assessment ref="[RA-ID]"/>
    <related_assumption_inventory ref="[AI-ID]"/>
  </metadata>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ANALYSIS PARAMETERS
       ═══════════════════════════════════════════════════════════════════════ -->
  <parameters>
    <assumptions_analyzed>[Count]</assumptions_analyzed>
    <analysis_depth>[light | standard | rigorous]</analysis_depth>
    <counterfactual_types>
      <type>direct_negation</type>
      <type>magnitude_variation</type>
      <type>timing_variation</type>
    </counterfactual_types>
  </parameters>

  <!-- ═══════════════════════════════════════════════════════════════════════
       WHAT-IF SCENARIOS
       ═══════════════════════════════════════════════════════════════════════ -->
  <scenarios>

    <scenario id="S1" assumption_id="A1">
      <!-- Scenario setup -->
      <assumption_statement>[Original assumption statement]</assumption_statement>
      <what_if>[Description of counterfactual: "What if [assumption] is FALSE?"]</what_if>
      <counterfactual_type>[direct_negation | partial_failure | magnitude_variation | timing_variation]</counterfactual_type>

      <!-- Scenario details (for magnitude/timing variation) -->
      <scenario_parameters>
        <base_value>[Original assumed value, if quantitative]</base_value>
        <scenario_value>[Counterfactual value being tested]</scenario_value>
        <variation_percentage>[How much different, e.g., "-50%"]</variation_percentage>
      </scenario_parameters>

      <!-- Impact assessment -->
      <immediate_impacts>
        <impact severity="[high | medium | low]">[Description of immediate consequence]</impact>
        <impact severity="[high | medium | low]">[Another immediate consequence]</impact>
      </immediate_impacts>

      <cascade_effects>
        <effect order="2">[Second-order effect]</effect>
        <effect order="2">[Another second-order effect]</effect>
        <effect order="3">[Third-order effect]</effect>
      </cascade_effects>

      <!-- Decision implications -->
      <decision_change>
        <would_change>[yes | no | partially]</would_change>
        <change_type>[no_change | adjustment | major_revision | reversal | cannot_proceed]</change_type>
        <alternative>[What we would do instead if we knew assumption was wrong]</alternative>
      </decision_change>

      <!-- Impact classification -->
      <impact_magnitude>[NEGLIGIBLE | MINOR | MODERATE | MAJOR | CATASTROPHIC]</impact_magnitude>
      <magnitude_rationale>[Why this magnitude classification]</magnitude_rationale>

      <!-- Sensitivity score -->
      <sensitivity>
        <band>[INSENSITIVE | LOW | MEDIUM | HIGH | EXTREME]</band>
        <outcome_change_percentage>[How much outcome changes, e.g., "35%"]</outcome_change_percentage>
      </sensitivity>

      <!-- Contingencies identified -->
      <contingencies>
        <early_warning>[Signal to monitor]</early_warning>
        <trigger_condition>[When to activate contingency]</trigger_condition>
        <fallback_action>[What to do if assumption fails]</fallback_action>
        <preparation_needed>[What to do now to be ready]</preparation_needed>
      </contingencies>

    </scenario>

    <!-- Additional scenarios -->
    <scenario id="S2" assumption_id="A3">
      <!-- ... -->
    </scenario>

  </scenarios>

  <!-- ═══════════════════════════════════════════════════════════════════════
       MULTI-ASSUMPTION SCENARIOS (Combined failures)
       ═══════════════════════════════════════════════════════════════════════ -->
  <combined_scenarios>
    <combined_scenario id="CS1">
      <name>[Scenario name, e.g., "Perfect Storm"]</name>
      <description>[Description of combined failure scenario]</description>
      <assumptions_failing>
        <ref assumption_id="A1"/>
        <ref assumption_id="A3"/>
        <ref assumption_id="A7"/>
      </assumptions_failing>
      <probability>[very_low | low | medium | high]</probability>
      <combined_impact>[MODERATE | MAJOR | CATASTROPHIC]</combined_impact>
      <would_invalidate_decision>[yes | no]</would_invalidate_decision>
      <mitigation_required>[What must be done to protect against this scenario]</mitigation_required>
    </combined_scenario>
  </combined_scenarios>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SENSITIVITY SUMMARY
       ═══════════════════════════════════════════════════════════════════════ -->
  <summary>
    <!-- Robustness score -->
    <decision_robustness>
      <score>[0-100]</score>
      <interpretation>[LOW | MODERATE | HIGH | VERY_HIGH]</interpretation>
      <rationale>[Why this robustness score]</rationale>
    </decision_robustness>

    <!-- Ranked sensitivity -->
    <most_sensitive_assumptions>
      <rank position="1">
        <ref assumption_id="A3"/>
        <sensitivity_band>EXTREME</sensitivity_band>
        <impact_if_wrong>MAJOR</impact_if_wrong>
        <summary>[Brief: Why most sensitive]</summary>
      </rank>
      <rank position="2">
        <ref assumption_id="A7"/>
        <sensitivity_band>HIGH</sensitivity_band>
        <impact_if_wrong>MODERATE</impact_if_wrong>
        <summary>[Brief: Why second most sensitive]</summary>
      </rank>
      <rank position="3">
        <ref assumption_id="A1"/>
        <sensitivity_band>HIGH</sensitivity_band>
        <impact_if_wrong>MODERATE</impact_if_wrong>
        <summary>[Brief: Why third most sensitive]</summary>
      </rank>
    </most_sensitive_assumptions>

    <!-- Assumptions with low sensitivity (can be deprioritized) -->
    <least_sensitive_assumptions>
      <ref assumption_id="A5">[Can accept without deep validation]</ref>
      <ref assumption_id="A9">[Low impact if wrong]</ref>
    </least_sensitive_assumptions>

    <!-- Key findings -->
    <key_findings>
      <finding severity="critical">[Most important finding]</finding>
      <finding severity="high">[Second finding]</finding>
      <finding severity="medium">[Third finding]</finding>
    </key_findings>

    <!-- Robustness narrative -->
    <robustness_assessment>
      [2-3 paragraph narrative explaining:
       - Overall how robust the decision is to assumption failures
       - Which assumptions the decision is most sensitive to
       - Where contingencies are needed
       - Recommendations for improving robustness]
    </robustness_assessment>

  </summary>

</sensitivity_analysis>
```

---

## Field Guidance

### Sensitivity Bands

| Band | Outcome Change | Implication |
|------|---------------|-------------|
| **INSENSITIVE** | < 5% | Assumption not critical; accept |
| **LOW** | 5-15% | Minor sensitivity; monitor |
| **MEDIUM** | 15-30% | Notable sensitivity; validate |
| **HIGH** | 30-50% | Major sensitivity; must validate |
| **EXTREME** | > 50% | Outcome determined by assumption; block if unvalidated |

### Impact Magnitude

| Magnitude | Definition |
|-----------|------------|
| **NEGLIGIBLE** | No meaningful change to outcome or decision |
| **MINOR** | Small adjustments needed; <10% deviation |
| **MODERATE** | Significant rework; 10-30% deviation |
| **MAJOR** | Strategy revision needed; >30% deviation |
| **CATASTROPHIC** | Project/strategy fails; cannot recover |

### Decision Change Types

| Type | Description |
|------|-------------|
| **no_change** | Decision still valid; minor adjustments at most |
| **adjustment** | Same direction; different parameters |
| **major_revision** | Significantly different approach needed |
| **reversal** | Opposite decision would be better |
| **cannot_proceed** | No viable path forward |

### Robustness Score

| Score | Interpretation | Meaning |
|-------|----------------|---------|
| 80-100 | VERY HIGH | Decision robust to most assumption failures |
| 60-79 | HIGH | Decision generally robust; few vulnerabilities |
| 40-59 | MODERATE | Some sensitivity; contingencies needed |
| 20-39 | LOW | High sensitivity; validate before proceeding |
| 0-19 | VERY LOW | Decision rests on fragile assumptions |

**Calculation:**
```
Robustness = 100 - (Σ sensitivity_impact) / n

Where sensitivity_impact per assumption:
- EXTREME: 25 points
- HIGH: 15 points
- MEDIUM: 8 points
- LOW: 3 points
- INSENSITIVE: 0 points
```

---

## Example Output (Condensed)

```xml
<sensitivity_analysis version="2.0">
  <metadata>
    <artifact_id>SA-2024-017</artifact_id>
    <created>2024-03-15T14:30:00Z</created>
    <subject_reference>ADR-042: Microservices Migration</subject_reference>
    <subject_type>architecture</subject_type>
    <related_risk_assessment ref="RA-2024-017"/>
    <related_assumption_inventory ref="AI-2024-017"/>
  </metadata>

  <parameters>
    <assumptions_analyzed>5</assumptions_analyzed>
    <analysis_depth>rigorous</analysis_depth>
    <counterfactual_types>
      <type>direct_negation</type>
      <type>magnitude_variation</type>
    </counterfactual_types>
  </parameters>

  <scenarios>
    <scenario id="S1" assumption_id="A3">
      <assumption_statement>Engineering team has sufficient microservices expertise</assumption_statement>
      <what_if>Team lacks sufficient expertise; only 1 of 8 has relevant experience</what_if>
      <counterfactual_type>direct_negation</counterfactual_type>

      <immediate_impacts>
        <impact severity="high">Poor architectural decisions in early design</impact>
        <impact severity="high">Delivery timeline slips 6-12 months</impact>
        <impact severity="medium">Increased bug rate in production services</impact>
      </immediate_impacts>

      <cascade_effects>
        <effect order="2">Technical debt accumulates faster than anticipated</effect>
        <effect order="2">Team morale drops due to struggling with unfamiliar patterns</effect>
        <effect order="3">Key engineers may leave due to frustration</effect>
      </cascade_effects>

      <decision_change>
        <would_change>yes</would_change>
        <change_type>major_revision</change_type>
        <alternative>Would hire expertise first, or choose simpler architecture (modular monolith)</alternative>
      </decision_change>

      <impact_magnitude>MAJOR</impact_magnitude>
      <magnitude_rationale>6-12 month delay, significant rework, possible project failure</magnitude_rationale>

      <sensitivity>
        <band>EXTREME</band>
        <outcome_change_percentage>65%</outcome_change_percentage>
      </sensitivity>

      <contingencies>
        <early_warning>Architecture review quality; delivery velocity in first sprint</early_warning>
        <trigger_condition>First service delivery >50% over estimate; major design pivot needed</trigger_condition>
        <fallback_action>Pause migration; engage consultancy; extend timeline</fallback_action>
        <preparation_needed>Hire experienced engineers NOW; establish architecture review process</preparation_needed>
      </contingencies>
    </scenario>

    <scenario id="S2" assumption_id="A7">
      <assumption_statement>Service boundaries can be cleanly defined from domain model</assumption_statement>
      <what_if>Boundaries are unclear; team creates distributed monolith</what_if>
      <counterfactual_type>direct_negation</counterfactual_type>

      <immediate_impacts>
        <impact severity="high">Services are tightly coupled; changes require coordinated deployments</impact>
        <impact severity="high">Latency increases due to excessive cross-service calls</impact>
      </immediate_impacts>

      <cascade_effects>
        <effect order="2">Operational complexity worse than monolith</effect>
        <effect order="2">Debugging distributed issues becomes nightmare</effect>
        <effect order="3">Team loses confidence in architecture direction</effect>
      </cascade_effects>

      <decision_change>
        <would_change>yes</would_change>
        <change_type>reversal</change_type>
        <alternative>Would not migrate to microservices; would optimize monolith or try modular monolith</alternative>
      </decision_change>

      <impact_magnitude>CATASTROPHIC</impact_magnitude>
      <magnitude_rationale>Distributed monolith worse than starting point; 12+ month recovery</magnitude_rationale>

      <sensitivity>
        <band>EXTREME</band>
        <outcome_change_percentage>80%</outcome_change_percentage>
      </sensitivity>

      <contingencies>
        <early_warning>Cross-service call frequency; shared database access</early_warning>
        <trigger_condition>Any service with >50 calls to another per request</trigger_condition>
        <fallback_action>Stop migration; consolidate services; reassess boundaries</fallback_action>
        <preparation_needed>Event storming workshop; service contract definition; fitness functions</preparation_needed>
      </contingencies>
    </scenario>

    <scenario id="S3" assumption_id="A1">
      <assumption_statement>Current monolith cannot scale beyond 10K concurrent users</assumption_statement>
      <what_if>Monolith could actually scale to 25K with optimization</what_if>
      <counterfactual_type>magnitude_variation</counterfactual_type>

      <scenario_parameters>
        <base_value>10K users (assumed limit)</base_value>
        <scenario_value>25K users (actual limit with optimization)</scenario_value>
        <variation_percentage>+150%</variation_percentage>
      </scenario_parameters>

      <immediate_impacts>
        <impact severity="medium">Migration may not be necessary for next 2-3 years</impact>
      </immediate_impacts>

      <decision_change>
        <would_change>partially</would_change>
        <change_type>adjustment</change_type>
        <alternative>Would optimize monolith first; defer migration 18-24 months</alternative>
      </decision_change>

      <impact_magnitude>MODERATE</impact_magnitude>
      <sensitivity>
        <band>HIGH</band>
        <outcome_change_percentage>40%</outcome_change_percentage>
      </sensitivity>
    </scenario>
  </scenarios>

  <combined_scenarios>
    <combined_scenario id="CS1">
      <name>Execution Failure Scenario</name>
      <description>Team lacks expertise AND service boundaries are wrong</description>
      <assumptions_failing>
        <ref assumption_id="A3"/>
        <ref assumption_id="A7"/>
      </assumptions_failing>
      <probability>medium</probability>
      <combined_impact>CATASTROPHIC</combined_impact>
      <would_invalidate_decision>yes</would_invalidate_decision>
      <mitigation_required>Both assumptions must be validated before proceeding; if either fails, do not start migration</mitigation_required>
    </combined_scenario>
  </combined_scenarios>

  <summary>
    <decision_robustness>
      <score>35</score>
      <interpretation>LOW</interpretation>
      <rationale>Two EXTREME sensitivity assumptions (A3, A7) create high vulnerability; decision outcome strongly dependent on unvalidated assumptions</rationale>
    </decision_robustness>

    <most_sensitive_assumptions>
      <rank position="1">
        <ref assumption_id="A7"/>
        <sensitivity_band>EXTREME</sensitivity_band>
        <impact_if_wrong>CATASTROPHIC</impact_if_wrong>
        <summary>Wrong service boundaries create distributed monolith; worse than starting point</summary>
      </rank>
      <rank position="2">
        <ref assumption_id="A3"/>
        <sensitivity_band>EXTREME</sensitivity_band>
        <impact_if_wrong>MAJOR</impact_if_wrong>
        <summary>Team capability gap causes delays, poor quality, potential failure</summary>
      </rank>
      <rank position="3">
        <ref assumption_id="A1"/>
        <sensitivity_band>HIGH</sensitivity_band>
        <impact_if_wrong>MODERATE</impact_if_wrong>
        <summary>If monolith can scale further, migration may be premature</summary>
      </rank>
    </most_sensitive_assumptions>

    <least_sensitive_assumptions>
      <ref assumption_id="A5">Cloud provider choice has low sensitivity; easy to change</ref>
      <ref assumption_id="A9">CI/CD tooling decision reversible with minor cost</ref>
    </least_sensitive_assumptions>

    <key_findings>
      <finding severity="critical">Decision is highly sensitive to service boundary definition (A7) - if wrong, outcome is catastrophic</finding>
      <finding severity="critical">Team capability (A3) is second most sensitive - without expertise, execution fails</finding>
      <finding severity="high">These two assumptions are correlated - if team lacks expertise, they're more likely to get boundaries wrong</finding>
    </key_findings>

    <robustness_assessment>
      The microservices migration decision has LOW robustness (score: 35). The outcome is highly dependent on two unvalidated assumptions: team expertise (A3) and service boundary clarity (A7). Both show EXTREME sensitivity - if either is wrong, the decision outcome changes dramatically.

      Most critically, these assumptions are correlated. A team lacking microservices expertise is more likely to define poor service boundaries, creating a distributed monolith. This combined scenario has medium probability and catastrophic impact.

      To improve robustness: (1) Validate team capability through hiring before project start, (2) Conduct event storming to validate domain boundaries before implementation, (3) Establish architecture fitness functions to detect coupling early. Without these mitigations, decision robustness remains unacceptably low.
    </robustness_assessment>
  </summary>

</sensitivity_analysis>
```

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| What-if protocol | `references/what-if-framework.md` |
| Load-bearing analysis | `references/load-bearing-analysis.md` |
| Confidence calibration | `references/confidence-calibration.md` |
| Risk output | `templates/risk-assessment-output.md` |
| Assumption inventory | `templates/assumption-inventory-output.md` |
