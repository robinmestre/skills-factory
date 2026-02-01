# GAP-INVENTORY Output Template

This template defines the CONTRACT-07 compliant output format for the Architecture Documentation Auditor, including architecture-specific extensions for health scoring and technical debt.

---

## Template Structure

The GAP-INVENTORY output consists of these major sections:

1. **Metadata** - Artifact identification and provenance
2. **Source Reference** - What was audited
3. **Audit Criteria** - What it was checked against
4. **Gaps** - Identified gaps with classification
5. **Anti-Patterns** - Detected architecture anti-patterns
6. **Technical Debt** - Debt indicators found
7. **Architecture Health** - Health score and viewpoint coverage
8. **Summary** - Aggregate statistics

---

## Complete XML Template

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gap_inventory contract="CONTRACT-07" version="1.0">

  <!-- ============================================ -->
  <!-- SECTION 1: METADATA                          -->
  <!-- ============================================ -->
  <metadata>
    <!-- Unique identifier for this audit artifact -->
    <artifact_id>GI-ARCH-[YYYY-MM-DD]-[5-char-hash]</artifact_id>

    <!-- Contract type (always GAP-INVENTORY) -->
    <contract_type>GAP-INVENTORY</contract_type>

    <!-- When this audit was performed -->
    <created_at>[ISO 8601 datetime]</created_at>

    <!-- Skill that produced this artifact -->
    <created_by>architecture-doc-auditor</created_by>

    <!-- Overall confidence in audit completeness (0.0-1.0) -->
    <confidence>[0.0-1.0]</confidence>

    <!-- Audit provenance information -->
    <provenance>
      <!-- Original document identifier -->
      <source_artifact>[Document identifier or path]</source_artifact>

      <!-- When the audit was conducted -->
      <audit_date>[ISO 8601 date]</audit_date>

      <!-- Audit depth setting -->
      <audit_depth>[surface|standard|exhaustive]</audit_depth>

      <!-- Document type audited -->
      <document_type>[adr|design_doc|system_context|container|component|deployment|sequence|data_flow]</document_type>

      <!-- Framework detected or specified -->
      <framework_detected>[togaf|c4|arc42|ieee_42010|custom]</framework_detected>

      <!-- Checklist version used -->
      <checklist_version>1.0</checklist_version>

      <!-- Number of items actually checked -->
      <items_checked>[N]</items_checked>

      <!-- Viewpoints that were assessed -->
      <viewpoints_assessed>
        <viewpoint>V1</viewpoint>
        <viewpoint>V2</viewpoint>
        <!-- All assessed viewpoints -->
      </viewpoints_assessed>

      <!-- Governance context -->
      <governance_context>[enterprise|team|project]</governance_context>
    </provenance>
  </metadata>

  <!-- ============================================ -->
  <!-- SECTION 2: SOURCE REFERENCE                  -->
  <!-- ============================================ -->

  <!-- Identifier for the audited document -->
  <source_reference>[Document identifier or title]</source_reference>

  <!-- Type of thing audited (always 'architecture' for this skill) -->
  <source_type>architecture</source_type>

  <!-- ============================================ -->
  <!-- SECTION 3: AUDIT CRITERIA                    -->
  <!-- ============================================ -->
  <audit_criteria>
    <!-- Reference to checklist used -->
    <checklist_reference>architecture-checklist.md v1.0</checklist_reference>

    <!-- Reference to viewpoint framework -->
    <viewpoint_framework>viewpoint-catalog.md v1.0</viewpoint_framework>

    <!-- List of criteria that were checked -->
    <criteria_list>
      <criterion id="V1-01" viewpoint="V1">System Boundary Definition</criterion>
      <criterion id="V1-02" viewpoint="V1">External User Identification</criterion>
      <!-- All checked items -->
    </criteria_list>

    <!-- Scope description -->
    <coverage_scope>
      [Description of what this audit covered and any limitations]
    </coverage_scope>
  </audit_criteria>

  <!-- ============================================ -->
  <!-- SECTION 4: GAPS                              -->
  <!-- ============================================ -->
  <gaps>
    <!-- Repeat for each identified gap -->
    <gap id="GAP-001">
      <!-- Gap type from 6-type taxonomy -->
      <category>[missing|incomplete|inconsistent|ambiguous|incorrect|outdated]</category>

      <!-- Severity level -->
      <severity>[critical|high|medium|low]</severity>

      <!-- Detailed severity scoring (RUBRIC-07) -->
      <severity_score>
        <impact>[1-4]</impact>
        <likelihood>[1-4]</likelihood>
        <detectability>[1-4]</detectability>
        <composite>[calculated: (impact*0.5)+(likelihood*0.3)+(detectability*0.2)]</composite>
      </severity_score>

      <!-- Which viewpoint this gap belongs to -->
      <viewpoint>[V1-V14]</viewpoint>

      <!-- Reference to specific checklist item -->
      <checklist_ref>[V1-01]</checklist_ref>

      <!-- Where in the document this gap was found -->
      <location>[Section name, diagram reference, or page]</location>

      <!-- Human-readable description of the gap -->
      <description>[Clear description of what is missing/wrong]</description>

      <!-- Evidence that indicates this gap -->
      <evidence>[Quote from document or observation]</evidence>

      <!-- Impact if not addressed -->
      <impact>[Consequence of leaving this gap unaddressed]</impact>

      <!-- Remediation guidance -->
      <remediation>
        <!-- How to fix this gap -->
        <recommendation>[Specific action to address this gap]</recommendation>

        <!-- Effort required -->
        <effort>[trivial|small|medium|large]</effort>

        <!-- Priority for fixing -->
        <priority>[immediate|short_term|medium_term|long_term]</priority>
      </remediation>
    </gap>

    <!-- Example populated gap -->
    <gap id="GAP-002">
      <category>missing</category>
      <severity>critical</severity>
      <severity_score>
        <impact>4</impact>
        <likelihood>4</likelihood>
        <detectability>2</detectability>
        <composite>3.6</composite>
      </severity_score>
      <viewpoint>V4</viewpoint>
      <checklist_ref>V4-18</checklist_ref>
      <location>Deployment Section</location>
      <description>No disaster recovery plan documented</description>
      <evidence>Deployment section covers deployment process but has no DR subsection. No RTO/RPO targets found anywhere in document.</evidence>
      <impact>Extended outage with no recovery path; potential data loss; business continuity risk</impact>
      <remediation>
        <recommendation>Create DR section documenting: RTO/RPO targets, failover process, backup strategy, and recovery procedures</recommendation>
        <effort>medium</effort>
        <priority>immediate</priority>
      </remediation>
    </gap>
  </gaps>

  <!-- ============================================ -->
  <!-- SECTION 5: ANTI-PATTERNS                     -->
  <!-- ============================================ -->
  <anti_patterns>
    <!-- Repeat for each detected anti-pattern -->
    <pattern id="AA-02">
      <!-- Anti-pattern name -->
      <name>Distributed Monolith</name>

      <!-- Severity level -->
      <severity>CRITICAL</severity>

      <!-- Instances where this pattern was detected -->
      <instances>
        <instance location="Container Diagram">
          "All services connect to SharedDB"
        </instance>
        <instance location="Deployment Section">
          "Services must be deployed together to maintain consistency"
        </instance>
      </instances>

      <!-- How to address this anti-pattern -->
      <remediation>
        Define data ownership per service. Introduce async communication
        to enable independent deployment. Consider data duplication for
        query optimization.
      </remediation>
    </pattern>
  </anti_patterns>

  <!-- ============================================ -->
  <!-- SECTION 6: TECHNICAL DEBT                    -->
  <!-- ============================================ -->
  <technical_debt>
    <!-- Repeat for each debt indicator detected -->
    <indicator id="TD-A01">
      <!-- Debt category -->
      <category>architectural</category>

      <!-- Indicator name -->
      <name>Shared database between services</name>

      <!-- Severity -->
      <severity>HIGH</severity>

      <!-- Where this was detected -->
      <evidence>Container diagram shows Order, User, and Payment services all connecting to PostgreSQL</evidence>

      <!-- Estimated remediation cost -->
      <remediation_cost>large</remediation_cost>

      <!-- Recommendation -->
      <recommendation>
        Define data ownership boundaries. Create service-specific databases.
        Implement event-driven data synchronization.
      </recommendation>
    </indicator>
  </technical_debt>

  <!-- ============================================ -->
  <!-- SECTION 7: ARCHITECTURE HEALTH               -->
  <!-- ============================================ -->
  <architecture_health>
    <!-- Overall health score (0-100) -->
    <overall_score>[0-100]</overall_score>

    <!-- Overall health status -->
    <overall_status>[HEALTHY|ADEQUATE|AT_RISK|CRITICAL]</overall_status>

    <!-- Score breakdown by viewpoint -->
    <by_viewpoint>
      <viewpoint id="V1" name="Context & Scope">
        <score>[0-100]</score>
        <status>[HEALTHY|ADEQUATE|AT_RISK|CRITICAL]</status>
        <items_passed>[N]</items_passed>
        <items_total>[N]</items_total>
      </viewpoint>
      <viewpoint id="V2" name="Container Architecture">
        <score>[0-100]</score>
        <status>[HEALTHY|ADEQUATE|AT_RISK|CRITICAL]</status>
        <items_passed>[N]</items_passed>
        <items_total>[N]</items_total>
      </viewpoint>
      <!-- All assessed viewpoints -->
    </by_viewpoint>

    <!-- Quality attribute coverage assessment -->
    <by_quality_attribute>
      <attribute name="Performance">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V4, V5</primary_viewpoints>
      </attribute>
      <attribute name="Security">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V7</primary_viewpoints>
      </attribute>
      <attribute name="Reliability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V8, V4</primary_viewpoints>
      </attribute>
      <attribute name="Scalability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V4, V2</primary_viewpoints>
      </attribute>
      <attribute name="Maintainability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V3, V10</primary_viewpoints>
      </attribute>
      <attribute name="Interoperability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V6, V1</primary_viewpoints>
      </attribute>
      <attribute name="Portability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V4, V2</primary_viewpoints>
      </attribute>
      <attribute name="Usability">
        <coverage>[EXPLICIT|IMPLICIT|MISSING]</coverage>
        <primary_viewpoints>V6, V10</primary_viewpoints>
      </attribute>
    </by_quality_attribute>

    <!-- Technical debt summary -->
    <technical_debt_summary>
      <total_indicators>[N]</total_indicators>
      <by_category>
        <architectural>[N]</architectural>
        <documentation>[N]</documentation>
        <infrastructure>[N]</infrastructure>
        <security>[N]</security>
        <api>[N]</api>
      </by_category>
    </technical_debt_summary>

    <!-- C4 model maturity (if C4 framework detected) -->
    <c4_maturity>
      <level_1_complete>[true|false]</level_1_complete>
      <level_2_complete>[true|false]</level_2_complete>
      <level_3_complete>[true|false]</level_3_complete>
      <level_4_complete>[true|false]</level_4_complete>
    </c4_maturity>

    <!-- ADR health (if ADRs present) -->
    <adr_health>
      <total_adrs>[N]</total_adrs>
      <complete_adrs>[N]</complete_adrs>
      <coverage_gaps>
        <gap>Technology selection decisions</gap>
        <gap>Security approach decisions</gap>
      </coverage_gaps>
    </adr_health>
  </architecture_health>

  <!-- ============================================ -->
  <!-- SECTION 8: SUMMARY                           -->
  <!-- ============================================ -->
  <summary>
    <!-- Total gap count -->
    <total_gaps>[N]</total_gaps>

    <!-- Gaps by severity level -->
    <by_severity>
      <critical>[N]</critical>
      <high>[N]</high>
      <medium>[N]</medium>
      <low>[N]</low>
    </by_severity>

    <!-- Gaps by type category -->
    <by_category>
      <missing>[N]</missing>
      <incomplete>[N]</incomplete>
      <inconsistent>[N]</inconsistent>
      <ambiguous>[N]</ambiguous>
      <incorrect>[N]</incorrect>
      <outdated>[N]</outdated>
    </by_category>

    <!-- Gaps by viewpoint -->
    <by_viewpoint>
      <v1>[N]</v1>
      <v2>[N]</v2>
      <v3>[N]</v3>
      <v4>[N]</v4>
      <v5>[N]</v5>
      <v6>[N]</v6>
      <v7>[N]</v7>
      <v8>[N]</v8>
      <v9>[N]</v9>
      <v10>[N]</v10>
      <!-- Conditional viewpoints if assessed -->
    </by_viewpoint>

    <!-- Anti-pattern count -->
    <anti_patterns_detected>[N]</anti_patterns_detected>

    <!-- Debt indicator count -->
    <debt_indicators_detected>[N]</debt_indicators_detected>

    <!-- Overall assessment -->
    <overall_assessment>[critical_issues|significant_gaps|minor_issues|acceptable|excellent]</overall_assessment>

    <!-- Blocking issues that must be fixed -->
    <blocking_issues>
      <issue ref="GAP-001">[Brief description]</issue>
      <issue ref="GAP-002">[Brief description]</issue>
    </blocking_issues>

    <!-- Checklist coverage statistics -->
    <coverage_score>
      <items_passed>[N]</items_passed>
      <items_total>[N]</items_total>
      <percentage>[X%]</percentage>
    </coverage_score>
  </summary>

</gap_inventory>
```

---

## Field-by-Field Guidance

### Metadata Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| artifact_id | string | YES | Format: GI-ARCH-YYYY-MM-DD-[hash] |
| contract_type | enum | YES | Always "GAP-INVENTORY" |
| created_at | datetime | YES | ISO 8601 format |
| created_by | string | YES | Always "architecture-doc-auditor" |
| confidence | float | YES | 0.0-1.0 based on audit completeness |

### Gap Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| id | string | YES | Format: GAP-NNN |
| category | enum | YES | missing\|incomplete\|inconsistent\|ambiguous\|incorrect\|outdated |
| severity | enum | YES | critical\|high\|medium\|low |
| viewpoint | string | YES | V1-V14 |
| checklist_ref | string | YES | Item ID from checklist |
| location | string | NO | Where in document |
| description | string | YES | What the gap is |
| evidence | string | NO | Supporting evidence |
| impact | string | NO | Consequence |

### Health Score Calculation

```
viewpoint_score = (items_passed / items_total) × 100

severity_penalties:
  CRITICAL gap = -10 points
  HIGH gap = -5 points
  Anti-pattern = -3 points
  Debt indicator = -2 points

overall_score = weighted_average(viewpoint_scores) - sum(severity_penalties)
overall_score = max(0, min(100, overall_score))  # Clamp to 0-100

status_thresholds:
  HEALTHY: 80-100
  ADEQUATE: 60-79
  AT_RISK: 40-59
  CRITICAL: 0-39
```

---

## Validation Checklist

Before outputting GAP-INVENTORY, verify:

- [ ] artifact_id is unique and correctly formatted
- [ ] created_at is valid ISO 8601
- [ ] All gaps have unique IDs
- [ ] All gaps have required fields (category, severity, viewpoint, checklist_ref, description)
- [ ] Severity scores are correctly calculated
- [ ] Summary counts match gap list
- [ ] Blocking issues reference existing gap IDs
- [ ] Coverage percentage is mathematically correct
- [ ] Overall assessment matches severity profile
- [ ] Health score is within 0-100 range
- [ ] All viewpoint scores are within 0-100 range
- [ ] Anti-pattern IDs match catalog
- [ ] Debt indicator IDs match catalog
