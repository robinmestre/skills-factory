# Assumption Inventory Output Template

Secondary output artifact for the Assumption Validator skill. Provides a complete structured catalog of all assumptions surfaced during validation.

---

## Template Overview

The Assumption Inventory captures:
- Every assumption identified (not just key ones)
- Complete metadata per assumption
- Validation status and evidence
- Dependencies and invalidation triggers
- Organized by type and priority

---

## XML Schema

```xml
<assumption_inventory version="2.0">

  <!-- ═══════════════════════════════════════════════════════════════════════
       METADATA SECTION
       ═══════════════════════════════════════════════════════════════════════ -->
  <metadata>
    <artifact_id>[UNIQUE-ID: e.g., AI-2024-001]</artifact_id>
    <created>[ISO 8601 timestamp]</created>
    <subject_reference>[What was analyzed]</subject_reference>
    <subject_type>[decision | strategy | plan | architecture | investment | product_direction]</subject_type>
    <related_risk_assessment ref="[RA-ID]"/>
  </metadata>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUMMARY STATISTICS
       ═══════════════════════════════════════════════════════════════════════ -->
  <summary>
    <total_assumptions>[Count]</total_assumptions>
    <by_type>
      <type name="EXPLICIT" count="[n]"/>
      <type name="IMPLICIT" count="[n]"/>
      <type name="STRUCTURAL" count="[n]"/>
      <type name="LOAD_BEARING" count="[n]"/>
      <type name="CONTEXTUAL" count="[n]"/>
      <type name="BEHAVIORAL" count="[n]"/>
    </by_type>
    <by_validation_status>
      <status name="VALIDATED" count="[n]"/>
      <status name="PARTIAL" count="[n]"/>
      <status name="UNVALIDATED" count="[n]"/>
      <status name="INVALIDATED" count="[n]"/>
      <status name="CONTESTED" count="[n]"/>
    </by_validation_status>
    <by_epistemic_label>
      <label name="VERIFIED" count="[n]"/>
      <label name="LIKELY" count="[n]"/>
      <label name="POSSIBLE" count="[n]"/>
      <label name="SPECULATIVE" count="[n]"/>
      <label name="UNKNOWN" count="[n]"/>
    </by_epistemic_label>
    <validation_coverage>[Percentage validated]%</validation_coverage>
    <average_confidence>[0.0-1.0]</average_confidence>
    <load_bearing_count>[n]</load_bearing_count>
  </summary>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ASSUMPTIONS BY PRIORITY (Ordered by load-bearing score)
       ═══════════════════════════════════════════════════════════════════════ -->
  <assumptions>

    <!-- ─────────────────────────────────────────────────────────────────────
         Individual Assumption Record
         ───────────────────────────────────────────────────────────────────── -->
    <assumption id="A1" priority_rank="1">

      <!-- Core identification -->
      <statement>[Clear, falsifiable assumption statement]</statement>
      <types>
        <type>IMPLICIT</type>
        <type>LOAD_BEARING</type>
        <!-- Multiple types allowed -->
      </types>

      <!-- Surfacing information -->
      <source>
        <technique>[Surfacing technique that found this]</technique>
        <location>[Where in subject document, if applicable]</location>
        <surfaced_by>[Who/what identified it]</surfaced_by>
        <surfaced_date>[When identified]</surfaced_date>
      </source>

      <!-- Load-bearing analysis scores -->
      <load_bearing_analysis>
        <dependency_score>[1-5]</dependency_score>
        <reversibility_score>[1-5]</reversibility_score>
        <validation_cost_score>[1-5]</validation_cost_score>
        <priority_score>[Calculated: (D × (1-C)) / V]</priority_score>
        <is_load_bearing>[true | false]</is_load_bearing>
      </load_bearing_analysis>

      <!-- Confidence and validation -->
      <confidence>
        <value>[0.0-1.0]</value>
        <epistemic_label>[VERIFIED | LIKELY | POSSIBLE | SPECULATIVE | UNKNOWN]</epistemic_label>
        <confidence_rationale>[Why this confidence level]</confidence_rationale>
      </confidence>

      <validation>
        <status>[VALIDATED | PARTIAL | UNVALIDATED | INVALIDATED | CONTESTED]</status>
        <methods_applied>
          <method>[Validation method 1]</method>
          <method>[Validation method 2]</method>
        </methods_applied>
        <evidence>
          <evidence_item type="[primary | secondary | expert | inference | assumption]">
            <description>[What evidence was found]</description>
            <source>[Where evidence came from]</source>
            <quality_weight>[0.2-1.0]</quality_weight>
          </evidence_item>
        </evidence>
        <validation_notes>[Additional notes on validation]</validation_notes>
      </validation>

      <!-- Dependencies and impacts -->
      <dependencies>
        <depends_on>
          <ref assumption_id="A5">[How this assumption depends on A5]</ref>
        </depends_on>
        <depended_on_by>
          <ref type="assumption" id="A8">[A8 depends on this]</ref>
          <ref type="conclusion" id="C2">[Conclusion C2 depends on this]</ref>
          <ref type="decision" id="D1">[Decision D1 incorporates this]</ref>
        </depended_on_by>
      </dependencies>

      <!-- What would invalidate -->
      <invalidation>
        <triggers>
          <trigger>[Condition that would make this assumption false]</trigger>
          <trigger>[Another invalidating condition]</trigger>
        </triggers>
        <impact_if_wrong>
          <immediate>[What breaks immediately]</immediate>
          <cascade>[Second-order effects]</cascade>
          <magnitude>[NEGLIGIBLE | MINOR | MODERATE | MAJOR | CATASTROPHIC]</magnitude>
        </impact_if_wrong>
      </invalidation>

      <!-- Risk linkage -->
      <related_risks>
        <ref risk_id="R1">[How this assumption relates to R1]</ref>
      </related_risks>

      <!-- Time considerations -->
      <time_horizon>
        <relevant_period>[How long assumption needs to hold]</relevant_period>
        <decay_risk>[HIGH | MEDIUM | LOW]</decay_risk>
        <revalidation_trigger>[When to recheck]</revalidation_trigger>
      </time_horizon>

      <!-- Action items -->
      <recommended_actions>
        <action priority="[1-3]">[Specific action to address this assumption]</action>
      </recommended_actions>

    </assumption>

    <!-- Additional assumptions follow same structure -->
    <assumption id="A2" priority_rank="2">
      <!-- ... -->
    </assumption>

  </assumptions>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ASSUMPTION CLUSTERS (Optional - related assumptions grouped)
       ═══════════════════════════════════════════════════════════════════════ -->
  <clusters>
    <cluster id="CL1" name="[Cluster name, e.g., 'Technical Capability Assumptions']">
      <description>[What unifies this cluster]</description>
      <members>
        <ref assumption_id="A1"/>
        <ref assumption_id="A4"/>
        <ref assumption_id="A7"/>
      </members>
      <cluster_risk>[Combined risk if cluster fails]</cluster_risk>
    </cluster>
  </clusters>

</assumption_inventory>
```

---

## Field Guidance

### Statement

Write assumptions as clear, falsifiable propositions:

| Good | Poor |
|------|------|
| "Database can handle 100K TPS" | "Database performs well" |
| "Users adopt within 2 weeks" | "Users will like it" |
| "Market grows 15% annually" | "Market is favorable" |

### Types

Each assumption can have multiple types. Common combinations:

| Primary Type | Often Combined With |
|--------------|---------------------|
| IMPLICIT | BEHAVIORAL, CONTEXTUAL |
| STRUCTURAL | LOAD_BEARING |
| CONTEXTUAL | Time-sensitive concerns |
| BEHAVIORAL | IMPLICIT |

### Validation Status

| Status | When to Use |
|--------|-------------|
| VALIDATED | Confidence ≥ threshold; quality evidence exists |
| PARTIAL | Some evidence, but confidence < threshold |
| UNVALIDATED | No validation attempted or no evidence found |
| INVALIDATED | Evidence contradicts the assumption |
| CONTESTED | Different sources/experts disagree |

### Dependencies

Document both directions:
- **depends_on**: What must be true for this assumption to hold
- **depended_on_by**: What relies on this assumption

### Invalidation Triggers

Be specific about what would falsify the assumption:

| Vague | Specific |
|-------|----------|
| "If things change" | "If CAC exceeds $75 for 2 consecutive months" |
| "If users don't adopt" | "If adoption rate < 50% at 4 weeks" |

---

## Summary Table Format (Alternative)

For quick reference, assumptions can be summarized in table format:

| ID | Statement | Types | Confidence | Status | Priority | Load-Bearing |
|----|-----------|-------|------------|--------|----------|--------------|
| A1 | [Statement] | IMPLICIT, BEHAVIORAL | 0.35 | UNVALIDATED | 4.2 | Yes |
| A2 | [Statement] | EXPLICIT | 0.85 | VALIDATED | 0.6 | No |
| A3 | [Statement] | STRUCTURAL | 0.50 | PARTIAL | 3.1 | Yes |

---

## Example Output (Condensed)

```xml
<assumption_inventory version="2.0">
  <metadata>
    <artifact_id>AI-2024-017</artifact_id>
    <created>2024-03-15T14:30:00Z</created>
    <subject_reference>ADR-042: Microservices Migration</subject_reference>
    <subject_type>architecture</subject_type>
    <related_risk_assessment ref="RA-2024-017"/>
  </metadata>

  <summary>
    <total_assumptions>14</total_assumptions>
    <by_type>
      <type name="EXPLICIT" count="4"/>
      <type name="IMPLICIT" count="6"/>
      <type name="STRUCTURAL" count="2"/>
      <type name="LOAD_BEARING" count="3"/>
      <type name="CONTEXTUAL" count="1"/>
      <type name="BEHAVIORAL" count="3"/>
    </by_type>
    <by_validation_status>
      <status name="VALIDATED" count="5"/>
      <status name="PARTIAL" count="3"/>
      <status name="UNVALIDATED" count="5"/>
      <status name="INVALIDATED" count="0"/>
      <status name="CONTESTED" count="1"/>
    </by_validation_status>
    <validation_coverage>57%</validation_coverage>
    <average_confidence>0.58</average_confidence>
    <load_bearing_count>3</load_bearing_count>
  </summary>

  <assumptions>
    <assumption id="A3" priority_rank="1">
      <statement>Engineering team has sufficient microservices expertise to execute migration</statement>
      <types>
        <type>BEHAVIORAL</type>
        <type>LOAD_BEARING</type>
      </types>

      <source>
        <technique>inversion</technique>
        <surfaced_by>Assumption Validator</surfaced_by>
      </source>

      <load_bearing_analysis>
        <dependency_score>5</dependency_score>
        <reversibility_score>4</reversibility_score>
        <validation_cost_score>2</validation_cost_score>
        <priority_score>4.0</priority_score>
        <is_load_bearing>true</is_load_bearing>
      </load_bearing_analysis>

      <confidence>
        <value>0.35</value>
        <epistemic_label>SPECULATIVE</epistemic_label>
        <confidence_rationale>Only 1 of 8 team members has production microservices experience</confidence_rationale>
      </confidence>

      <validation>
        <status>UNVALIDATED</status>
        <methods_applied>
          <method>expert_challenge</method>
          <method>historical_precedent</method>
        </methods_applied>
        <evidence>
          <evidence_item type="inference">
            <description>Team skills assessment shows 1/8 with relevant experience</description>
            <source>HR skills inventory</source>
            <quality_weight>0.4</quality_weight>
          </evidence_item>
        </evidence>
      </validation>

      <dependencies>
        <depended_on_by>
          <ref type="assumption" id="A2">Timeline depends on team capability</ref>
          <ref type="assumption" id="A9">Quality outcomes depend on expertise</ref>
          <ref type="decision" id="D1">Migration decision</ref>
        </depended_on_by>
      </dependencies>

      <invalidation>
        <triggers>
          <trigger>Team fails to deliver first service within timeline</trigger>
          <trigger>Architecture reviews identify significant design flaws</trigger>
        </triggers>
        <impact_if_wrong>
          <immediate>Delivery delays; poor architectural decisions</immediate>
          <cascade>Production incidents; technical debt; team burnout</cascade>
          <magnitude>MAJOR</magnitude>
        </impact_if_wrong>
      </invalidation>

      <related_risks>
        <ref risk_id="R1">Team capability gap risk</ref>
      </related_risks>

      <recommended_actions>
        <action priority="1">Hire 2+ experienced microservices engineers before kickoff</action>
        <action priority="2">Engage architecture consultancy for design reviews</action>
      </recommended_actions>
    </assumption>

    <!-- Additional assumptions... -->
  </assumptions>

  <clusters>
    <cluster id="CL1" name="Team Capability Assumptions">
      <description>Assumptions about team's ability to execute the migration</description>
      <members>
        <ref assumption_id="A3"/>
        <ref assumption_id="A9"/>
        <ref assumption_id="A12"/>
      </members>
      <cluster_risk>If any of these fail, execution capability is compromised</cluster_risk>
    </cluster>
  </clusters>

</assumption_inventory>
```

---

## Cross-Reference

| Topic | Reference |
|-------|-----------|
| Assumption types | `references/assumption-taxonomy.md` |
| Load-bearing scoring | `references/load-bearing-analysis.md` |
| Confidence calibration | `references/confidence-calibration.md` |
| Validation methods | `references/validation-methods.md` |
| Risk output | `templates/risk-assessment-output.md` |
