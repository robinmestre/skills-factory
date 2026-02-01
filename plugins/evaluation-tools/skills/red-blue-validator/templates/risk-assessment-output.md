# Risk Assessment Output Template

> CONTRACT-08 compliant output with adversarial validation extensions.

Use this template to generate the primary output artifact from Red/Blue Team Validator.

---

## Template

```xml
<?xml version="1.0" encoding="UTF-8"?>
<risk_assessment contract="CONTRACT-08" version="2.0">

  <!-- ═══════════════════════════════════════════════════════════════════════
       METADATA
       ═══════════════════════════════════════════════════════════════════════ -->
  <metadata>
    <artifact_id>RA-[YYYYMMDD]-[HASH]</artifact_id>
    <created_at>[ISO 8601 timestamp]</created_at>
    <created_by>red-blue-validator</created_by>
    <skill_version>2.0</skill_version>
    <subject_reference>[Brief description of what was assessed]</subject_reference>
    <subject_type>[decision | strategy | architecture | plan | policy | investment | security]</subject_type>
  </metadata>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ADVERSARIAL VALIDATION CONTEXT
       Extension specific to Red/Blue Team Validator
       ═══════════════════════════════════════════════════════════════════════ -->
  <adversarial_context>
    <validation_parameters>
      <max_rounds>[configured max_rounds]</max_rounds>
      <rounds_completed>[actual rounds completed]</rounds_completed>
      <attack_intensity>[light | standard | aggressive]</attack_intensity>
      <convergence_mode>[no_new_critical | all_addressed | round_limit]</convergence_mode>
      <convergence_achieved>[true | false]</convergence_achieved>
      <convergence_reason>[How convergence was determined]</convergence_reason>
      <steel_manning_level>[minimal | standard | maximum]</steel_manning_level>
      <experience_pool_used>[true | false]</experience_pool_used>
    </validation_parameters>

    <attack_categories_used>
      <category>[ASSUMPTIONS]</category>
      <category>[DEPENDENCIES]</category>
      <!-- Add all categories used -->
    </attack_categories_used>

    <adversarial_summary>
      <total_attacks>[count across all rounds]</total_attacks>
      <attacks_by_severity>
        <critical>[count]</critical>
        <high>[count]</high>
        <medium>[count]</medium>
        <low>[count]</low>
      </attacks_by_severity>
      <defenses_by_type>
        <refute>[count]</refute>
        <mitigate>[count]</mitigate>
        <harden>[count]</harden>
        <accept>[count]</accept>
      </defenses_by_type>
      <proposition_modifications>[count of HARDEN changes]</proposition_modifications>
      <battle_tested_confidence>[0-100]</battle_tested_confidence>
    </adversarial_summary>
  </adversarial_context>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ASSESSMENT METHOD
       Standard CONTRACT-08 field with adversarial technique
       ═══════════════════════════════════════════════════════════════════════ -->
  <assessment_method>
    <technique>adversarial_validation</technique>
    <description>Iterative Red/Blue team stress-testing with steel-manned attacks</description>
    <assumptions_surfaced>[count if applicable]</assumptions_surfaced>
    <time_horizon>[short_term | medium_term | long_term | all]</time_horizon>
  </assessment_method>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUBJECT CONTEXT
       What was assessed
       ═══════════════════════════════════════════════════════════════════════ -->
  <subject>
    <original_proposition>
      [The proposition as originally stated before Red/Blue validation]
    </original_proposition>
    <hardened_proposition>
      [The proposition after all HARDEN modifications - battle-tested version]
    </hardened_proposition>
    <stakeholders>
      <stakeholder role="[role]">[name or team]</stakeholder>
      <!-- Add all relevant stakeholders -->
    </stakeholders>
    <constraints>
      <constraint>[Key constraint 1]</constraint>
      <constraint>[Key constraint 2]</constraint>
    </constraints>
  </subject>

  <!-- ═══════════════════════════════════════════════════════════════════════
       RISKS
       Derived from unresolved attacks and ACCEPT responses
       ═══════════════════════════════════════════════════════════════════════ -->
  <risks>

    <!-- Risk derived from ACCEPT response -->
    <risk id="R1">
      <source_attack>ATK-[round]-[number]</source_attack>
      <category>[technical | market | operational | financial | regulatory | strategic | reputational | organizational]</category>
      <severity>[CRITICAL | HIGH | MEDIUM | LOW]</severity>
      <description>[Clear description of the risk]</description>
      <trigger>[What would cause this risk to materialize]</trigger>
      <probability>[very_low | low | medium | high | very_high]</probability>
      <impact>[negligible | minor | moderate | major | catastrophic]</impact>
      <risk_score>[calculated: probability × impact mapping]</risk_score>
      <detection_difficulty>[easy | moderate | difficult | very_difficult]</detection_difficulty>

      <attack_context>
        <original_attack>[Brief description of the attack that identified this risk]</original_attack>
        <defense_response>[ACCEPT]</defense_response>
        <defense_rationale>[Why this was accepted rather than mitigated]</defense_rationale>
      </attack_context>

      <mitigation>
        <strategy>[accept - with monitoring and contingency]</strategy>
        <actions>
          <action owner="[responsible party]" timeline="[when]">
            [Monitoring or contingency action]
          </action>
        </actions>
        <residual_risk>[unchanged - accepted as residual risk]</residual_risk>
      </mitigation>

      <monitoring>
        <early_warning_signs>
          <sign>[What to watch for]</sign>
        </early_warning_signs>
        <trigger_condition>[When to escalate or activate contingency]</trigger_condition>
        <review_frequency>[How often to reassess]</review_frequency>
        <owner>[Who monitors]</owner>
      </monitoring>
    </risk>

    <!-- Risk derived from MITIGATE response with residual -->
    <risk id="R2">
      <source_attack>ATK-[round]-[number]</source_attack>
      <category>[category]</category>
      <severity>[severity after mitigation]</severity>
      <description>[Residual risk after mitigation]</description>
      <trigger>[Trigger condition]</trigger>
      <probability>[reduced probability]</probability>
      <impact>[reduced impact]</impact>
      <risk_score>[reduced score]</risk_score>
      <detection_difficulty>[difficulty]</detection_difficulty>

      <attack_context>
        <original_attack>[The attack]</original_attack>
        <defense_response>[MITIGATE]</defense_response>
        <defense_rationale>[How it was mitigated]</defense_rationale>
      </attack_context>

      <mitigation>
        <strategy>[mitigate]</strategy>
        <actions>
          <action owner="[party]" timeline="[when]">[Action taken]</action>
        </actions>
        <residual_risk>[reduced]</residual_risk>
      </mitigation>

      <monitoring>
        <early_warning_signs>
          <sign>[Warning sign]</sign>
        </early_warning_signs>
        <trigger_condition>[Escalation trigger]</trigger_condition>
        <review_frequency>[Frequency]</review_frequency>
        <owner>[Owner]</owner>
      </monitoring>
    </risk>

    <!-- Add additional risks -->

  </risks>

  <!-- ═══════════════════════════════════════════════════════════════════════
       FAILURE SCENARIOS (Optional - from pre-mortem attacks)
       ═══════════════════════════════════════════════════════════════════════ -->
  <failure_scenarios>
    <scenario id="FS1">
      <name>[Scenario name]</name>
      <narrative>
        [Story of how failure unfolds - derived from pre-mortem attacks]
      </narrative>
      <contributing_risks>
        <ref risk_id="R1"/>
        <ref risk_id="R2"/>
      </contributing_risks>
      <likelihood>[0.0-1.0 probability]</likelihood>
      <early_warning_signs>
        <sign>[Observable indicator]</sign>
      </early_warning_signs>
    </scenario>
  </failure_scenarios>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ATTACK RESOLUTION SUMMARY
       How attacks were handled
       ═══════════════════════════════════════════════════════════════════════ -->
  <attack_resolution>
    <resolved_attacks>
      <!-- Attacks that were REFUTE or HARDEN (fully resolved) -->
      <attack id="ATK-1-1" resolution="REFUTE">
        <summary>[Attack summary]</summary>
        <resolution_summary>[How it was refuted]</resolution_summary>
      </attack>
      <attack id="ATK-1-3" resolution="HARDEN">
        <summary>[Attack summary]</summary>
        <resolution_summary>[How proposition was hardened]</resolution_summary>
        <proposition_change>[Specific change made]</proposition_change>
      </attack>
    </resolved_attacks>

    <mitigated_attacks>
      <!-- Attacks that were MITIGATE (risk reduced) -->
      <attack id="ATK-1-2" residual_risk="R2">
        <summary>[Attack summary]</summary>
        <mitigation_summary>[How it was mitigated]</mitigation_summary>
      </attack>
    </mitigated_attacks>

    <accepted_attacks>
      <!-- Attacks that were ACCEPT (risk accepted) -->
      <attack id="ATK-2-1" residual_risk="R1">
        <summary>[Attack summary]</summary>
        <acceptance_rationale>[Why accepted]</acceptance_rationale>
      </attack>
    </accepted_attacks>
  </attack_resolution>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUMMARY
       ═══════════════════════════════════════════════════════════════════════ -->
  <summary>
    <total_risks>[count of residual risks]</total_risks>
    <risks_by_severity>
      <critical>[count]</critical>
      <high>[count]</high>
      <medium>[count]</medium>
      <low>[count]</low>
    </risks_by_severity>
    <risk_profile>[very_high | high | moderate | low | very_low]</risk_profile>

    <top_risks>
      <ref risk_id="R1">[Brief description]</ref>
      <ref risk_id="R2">[Brief description]</ref>
      <ref risk_id="R3">[Brief description]</ref>
    </top_risks>

    <go_no_go_assessment>[proceed | proceed_with_caution | significant_concerns | do_not_proceed]</go_no_go_assessment>

    <battle_tested_confidence>
      <score>[0-100]</score>
      <rationale>[Why this confidence level]</rationale>
    </battle_tested_confidence>

    <key_findings>
      <finding>[Key insight 1 from adversarial validation]</finding>
      <finding>[Key insight 2]</finding>
      <finding>[Key insight 3]</finding>
    </key_findings>

    <recommendation>
      [Narrative recommendation based on adversarial validation.
       Include specific conditions, mitigations, and monitoring requirements.
       Reference key risks and how they should be managed.]
    </recommendation>
  </summary>

</risk_assessment>
```

---

## Field Guidance

### Risk Score Calculation

Map probability and impact to numeric values:

**Probability:**
| Level | Value |
|-------|-------|
| very_low | 1 |
| low | 2 |
| medium | 3 |
| high | 4 |
| very_high | 5 |

**Impact:**
| Level | Value |
|-------|-------|
| negligible | 1 |
| minor | 2 |
| moderate | 3 |
| major | 4 |
| catastrophic | 5 |

**Risk Score = Probability × Impact** (range: 1-25)

| Score | Risk Level |
|-------|------------|
| 1-4 | LOW |
| 5-9 | MEDIUM |
| 10-15 | HIGH |
| 16-25 | CRITICAL |

### Risk Profile Determination

| Profile | Criteria |
|---------|----------|
| very_high | Any CRITICAL risk OR 3+ HIGH risks |
| high | 1-2 HIGH risks OR 5+ MEDIUM risks |
| moderate | 1-4 MEDIUM risks OR many LOW risks |
| low | Only LOW risks |
| very_low | No significant risks |

### Go/No-Go Assessment

| Assessment | When |
|------------|------|
| proceed | Low/very low risk profile; proposition battle-tested |
| proceed_with_caution | Moderate risk; mitigations in place; monitoring required |
| significant_concerns | High risk; key attacks unresolved; major conditions |
| do_not_proceed | Very high risk; CRITICAL issues; fundamental flaws |

### Battle-Tested Confidence

| Score | Meaning | Conditions |
|-------|---------|------------|
| 80-100 | High confidence | 3+ rounds, aggressive attacks survived, few ACCEPT |
| 60-79 | Moderate confidence | 2+ rounds, substantive attacks, manageable risks |
| 40-59 | Low confidence | Limited rounds or significant ACCEPT responses |
| 0-39 | Very low confidence | Convergence not achieved or fundamental issues |

---

## Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<risk_assessment contract="CONTRACT-08" version="2.0">

  <metadata>
    <artifact_id>RA-20240115-A7B3</artifact_id>
    <created_at>2024-01-15T14:30:00Z</created_at>
    <created_by>red-blue-validator</created_by>
    <skill_version>2.0</skill_version>
    <subject_reference>Microservices migration for payment processing</subject_reference>
    <subject_type>architecture</subject_type>
  </metadata>

  <adversarial_context>
    <validation_parameters>
      <max_rounds>3</max_rounds>
      <rounds_completed>3</rounds_completed>
      <attack_intensity>standard</attack_intensity>
      <convergence_mode>no_new_critical</convergence_mode>
      <convergence_achieved>true</convergence_achieved>
      <convergence_reason>Round 3 produced 0 new CRITICAL or HIGH attacks</convergence_reason>
      <steel_manning_level>standard</steel_manning_level>
      <experience_pool_used>true</experience_pool_used>
    </validation_parameters>

    <attack_categories_used>
      <category>ASSUMPTIONS</category>
      <category>DEPENDENCIES</category>
      <category>SCALABILITY</category>
      <category>OPERATIONAL</category>
      <category>ORGANIZATIONAL</category>
    </attack_categories_used>

    <adversarial_summary>
      <total_attacks>12</total_attacks>
      <attacks_by_severity>
        <critical>2</critical>
        <high>4</high>
        <medium>4</medium>
        <low>2</low>
      </attacks_by_severity>
      <defenses_by_type>
        <refute>2</refute>
        <mitigate>6</mitigate>
        <harden>3</harden>
        <accept>1</accept>
      </defenses_by_type>
      <proposition_modifications>3</proposition_modifications>
      <battle_tested_confidence>72</battle_tested_confidence>
    </adversarial_summary>
  </adversarial_context>

  <assessment_method>
    <technique>adversarial_validation</technique>
    <description>3 rounds of Red/Blue team stress-testing with standard steel-manning</description>
    <assumptions_surfaced>8</assumptions_surfaced>
    <time_horizon>long_term</time_horizon>
  </assessment_method>

  <subject>
    <original_proposition>
      Migrate payment processing from monolith to 5 microservices over 12 months
    </original_proposition>
    <hardened_proposition>
      Migrate to 3 microservices + 1 payment service (ACID) over 18 months
      with 3-month buffer, after event storming confirms boundaries.
      Prerequisites: 2 senior engineers hired, architecture consultancy engaged,
      distributed tracing infrastructure deployed.
    </hardened_proposition>
    <stakeholders>
      <stakeholder role="sponsor">VP Engineering</stakeholder>
      <stakeholder role="technical_lead">Platform Architect</stakeholder>
      <stakeholder role="impacted">Payment Operations Team</stakeholder>
    </stakeholders>
    <constraints>
      <constraint>Payment processing cannot have downtime during migration</constraint>
      <constraint>PCI compliance must be maintained</constraint>
    </constraints>
  </subject>

  <risks>
    <risk id="R1">
      <source_attack>ATK-2-1</source_attack>
      <category>organizational</category>
      <severity>HIGH</severity>
      <description>Senior engineer hiring timeline may slip, delaying project start</description>
      <trigger>Hiring takes longer than 6 months due to competitive market</trigger>
      <probability>medium</probability>
      <impact>moderate</impact>
      <risk_score>9</risk_score>
      <detection_difficulty>easy</detection_difficulty>

      <attack_context>
        <original_attack>Hiring 2 senior engineers in 6 months is optimistic given market conditions</original_attack>
        <defense_response>MITIGATE</defense_response>
        <defense_rationale>Begin hiring immediately with contingency plan for consultancy bridge</defense_rationale>
      </attack_context>

      <mitigation>
        <strategy>mitigate</strategy>
        <actions>
          <action owner="Engineering Manager" timeline="Immediate">
            Begin senior engineer recruiting
          </action>
          <action owner="VP Engineering" timeline="If hiring slips">
            Extend architecture consultancy as bridge
          </action>
        </actions>
        <residual_risk>reduced</residual_risk>
      </mitigation>

      <monitoring>
        <early_warning_signs>
          <sign>No qualified candidates after 8 weeks</sign>
          <sign>Offer rejections due to compensation</sign>
        </early_warning_signs>
        <trigger_condition>No hire after 4 months</trigger_condition>
        <review_frequency>Bi-weekly</review_frequency>
        <owner>Engineering Manager</owner>
      </monitoring>
    </risk>

    <risk id="R2">
      <source_attack>ATK-2-2</source_attack>
      <category>operational</category>
      <severity>MEDIUM</severity>
      <description>Distributed tracing infrastructure adds operational overhead</description>
      <trigger>Ongoing maintenance and expertise required for observability platform</trigger>
      <probability>high</probability>
      <impact>minor</impact>
      <risk_score>8</risk_score>
      <detection_difficulty>easy</detection_difficulty>

      <attack_context>
        <original_attack>Distributed tracing adds operational complexity itself</original_attack>
        <defense_response>ACCEPT</defense_response>
        <defense_rationale>Accepted as necessary cost of observability; allocate 0.5 FTE</defense_rationale>
      </attack_context>

      <mitigation>
        <strategy>accept</strategy>
        <actions>
          <action owner="Platform Team" timeline="Ongoing">
            Allocate 0.5 FTE for observability platform maintenance
          </action>
        </actions>
        <residual_risk>unchanged</residual_risk>
      </mitigation>

      <monitoring>
        <early_warning_signs>
          <sign>Platform maintenance consuming more than planned time</sign>
        </early_warning_signs>
        <trigger_condition>Platform maintenance exceeds 1 FTE</trigger_condition>
        <review_frequency>Monthly</review_frequency>
        <owner>Platform Lead</owner>
      </monitoring>
    </risk>
  </risks>

  <attack_resolution>
    <resolved_attacks>
      <attack id="ATK-1-3" resolution="HARDEN">
        <summary>Distributed transactions will break payment consistency</summary>
        <resolution_summary>Keep payment processing in single ACID service</resolution_summary>
        <proposition_change>5 microservices → 3 microservices + 1 payment service</proposition_change>
      </attack>
      <attack id="ATK-1-2" resolution="HARDEN">
        <summary>12-month timeline ignores learning curve</summary>
        <resolution_summary>Extended to 18 months with 3-month buffer</resolution_summary>
        <proposition_change>12 months → 18 months + buffer</proposition_change>
      </attack>
    </resolved_attacks>

    <mitigated_attacks>
      <attack id="ATK-1-1" residual_risk="R1">
        <summary>Team lacks microservices expertise</summary>
        <mitigation_summary>Hire 2 senior engineers + engage consultancy</mitigation_summary>
      </attack>
    </mitigated_attacks>

    <accepted_attacks>
      <attack id="ATK-2-2" residual_risk="R2">
        <summary>Observability platform adds operational overhead</summary>
        <acceptance_rationale>Necessary cost; overhead is manageable with 0.5 FTE allocation</acceptance_rationale>
      </attack>
    </accepted_attacks>
  </attack_resolution>

  <summary>
    <total_risks>4</total_risks>
    <risks_by_severity>
      <critical>0</critical>
      <high>1</high>
      <medium>3</medium>
      <low>0</low>
    </risks_by_severity>
    <risk_profile>moderate</risk_profile>

    <top_risks>
      <ref risk_id="R1">Hiring timeline slip may delay project</ref>
      <ref risk_id="R2">Observability platform operational overhead</ref>
    </top_risks>

    <go_no_go_assessment>proceed_with_caution</go_no_go_assessment>

    <battle_tested_confidence>
      <score>72</score>
      <rationale>Proposition survived 3 rounds of substantive attacks. Critical issues
        (payment consistency, timeline, team capability) addressed through hardening
        and mitigation. Residual risks are manageable with monitoring.</rationale>
    </battle_tested_confidence>

    <key_findings>
      <finding>Original 5-microservice plan had critical flaw in payment consistency;
        hardened to 3+1 architecture eliminates distributed transaction risk</finding>
      <finding>Team capability gap is the highest remaining risk; requires proactive
        hiring with contingency plan</finding>
      <finding>Timeline was unrealistic; 18 months with buffer is credible based
        on industry benchmarks</finding>
    </key_findings>

    <recommendation>
      PROCEED WITH CAUTION — The hardened proposition addresses the critical flaws
      in the original plan. Key conditions for success:

      1. Begin senior engineer hiring immediately; do not start migration without
         at least one hire in place
      2. Conduct event storming before finalizing service boundaries
      3. Deploy observability infrastructure before first service extraction
      4. Maintain architecture consultancy engagement through first major milestone

      Monitor hiring progress bi-weekly. If no qualified hire after 4 months,
      activate consultancy bridge or reassess timeline.
    </recommendation>
  </summary>

</risk_assessment>
```
