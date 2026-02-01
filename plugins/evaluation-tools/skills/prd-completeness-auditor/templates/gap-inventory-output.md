# Gap Inventory Output Template

CONTRACT-07 compliant template for PRD audit gap inventories.

---

## Overview

This template produces output conforming to CONTRACT-07 (GAP-INVENTORY) from `@core/artifact-contracts.yaml`. Use this structure for all PRD completeness audit outputs.

---

## Template

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gap_inventory contract="CONTRACT-07" version="1.0">

  <!-- ═══════════════════════════════════════════════════════════════════════
       METADATA: Artifact identification and provenance
       ═══════════════════════════════════════════════════════════════════════ -->
  <metadata>
    <!-- Unique artifact identifier: GI-[date]-[5-char-hash] -->
    <artifact_id>GI-YYYY-MM-DD-XXXXX</artifact_id>

    <!-- Contract type - always GAP-INVENTORY for this skill -->
    <contract_type>GAP-INVENTORY</contract_type>

    <!-- Creation timestamp in ISO 8601 format -->
    <created_at>YYYY-MM-DDTHH:MM:SSZ</created_at>

    <!-- Producing skill identifier -->
    <created_by>prd-completeness-auditor</created_by>

    <!-- Overall confidence in audit accuracy (0.0-1.0) -->
    <confidence>0.XX</confidence>

    <!-- Audit provenance details -->
    <provenance>
      <!-- Reference to source PRD -->
      <source_artifact>[PRD title or identifier]</source_artifact>

      <!-- Date audit was performed -->
      <audit_date>YYYY-MM-DD</audit_date>

      <!-- Audit depth setting used -->
      <audit_depth>quick|standard|comprehensive</audit_depth>

      <!-- PRD type setting used -->
      <prd_type>feature|epic|product|initiative</prd_type>

      <!-- Version of checklist used -->
      <checklist_version>1.0</checklist_version>

      <!-- Number of checklist items evaluated -->
      <items_checked>NNN</items_checked>
    </provenance>
  </metadata>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SOURCE: What was audited
       ═══════════════════════════════════════════════════════════════════════ -->

  <!-- Identifier or hash of the PRD document audited -->
  <source_reference>[PRD document identifier, title, or content hash]</source_reference>

  <!-- Type of source - always "document" for PRD audits -->
  <source_type>document</source_type>

  <!-- ═══════════════════════════════════════════════════════════════════════
       AUDIT CRITERIA: What the PRD was checked against
       ═══════════════════════════════════════════════════════════════════════ -->
  <audit_criteria>
    <!-- Reference to the checklist used -->
    <checklist_reference>prd-requirements-checklist.md v1.0</checklist_reference>

    <!-- List of all criteria that were checked -->
    <criteria_list>
      <!-- Include all checked items with their IDs -->
      <criterion id="PC-01">Problem Statement</criterion>
      <criterion id="PC-02">Problem Evidence</criterion>
      <criterion id="PC-03">Current State</criterion>
      <!-- ... continue for all checked items ... -->
      <criterion id="TC-08">Monitoring/Observability</criterion>
    </criteria_list>

    <!-- Description of what this audit covered and did not cover -->
    <coverage_scope>
      Full audit of [prd_type] PRD covering [N] checklist items across
      [N] sections. Focus areas: [list if specified]. Anti-pattern
      scanning: [enabled/disabled].
    </coverage_scope>
  </audit_criteria>

  <!-- ═══════════════════════════════════════════════════════════════════════
       GAPS: All identified gaps with full details
       ═══════════════════════════════════════════════════════════════════════ -->
  <gaps>

    <!-- ─────────────────────────────────────────────────────────────────────
         Example Gap Entry (repeat for each gap found)
         ───────────────────────────────────────────────────────────────────── -->
    <gap id="GAP-001">
      <!-- Gap type from 6-type taxonomy -->
      <category>missing|incomplete|inconsistent|ambiguous|incorrect|outdated</category>

      <!-- Calculated severity level -->
      <severity>critical|high|medium|low</severity>

      <!-- Severity scoring breakdown -->
      <severity_score>
        <!-- Impact score (1-4) with 0.5 weight -->
        <impact>N</impact>
        <!-- Likelihood score (1-4) with 0.3 weight -->
        <likelihood>N</likelihood>
        <!-- Detectability score (1-4) with 0.2 weight -->
        <detectability>N</detectability>
        <!-- Calculated composite: (impact×0.5)+(likelihood×0.3)+(detectability×0.2) -->
        <composite>N.N</composite>
      </severity_score>

      <!-- Reference to checklist item(s) this gap relates to -->
      <checklist_ref>PC-01</checklist_ref>

      <!-- Location in the PRD where gap was found -->
      <location>[Section name, line number, or "N/A - missing"]</location>

      <!-- Clear description of the gap -->
      <description>
        [What is missing, incomplete, inconsistent, ambiguous, incorrect, or outdated]
      </description>

      <!-- Evidence that indicates this is a gap -->
      <evidence>
        [Quote from PRD, absence of expected content, or conflicting statements]
      </evidence>

      <!-- Downstream impact if gap is not addressed -->
      <impact>
        [What happens to development/quality/timeline if this isn't fixed]
      </impact>

      <!-- Remediation guidance -->
      <remediation>
        <!-- Recommended fix action -->
        <recommendation>
          [Specific action to resolve this gap]
        </recommendation>

        <!-- Reference to remediation pattern -->
        <pattern_ref>RP-PC-01</pattern_ref>

        <!-- Estimated effort to fix -->
        <effort>trivial|small|medium|large</effort>

        <!-- Recommended priority -->
        <priority>immediate|short_term|long_term|optional</priority>
      </remediation>
    </gap>

    <!-- Additional gaps follow same structure -->
    <gap id="GAP-002">
      <!-- ... -->
    </gap>

  </gaps>

  <!-- ═══════════════════════════════════════════════════════════════════════
       ANTI-PATTERNS: Detected systemic issues (if include_anti_patterns=true)
       ═══════════════════════════════════════════════════════════════════════ -->
  <anti_patterns>

    <!-- Example anti-pattern entry -->
    <pattern id="AP-02">
      <!-- Anti-pattern name from catalog -->
      <name>Solution Contamination</name>

      <!-- All instances where this pattern was detected -->
      <instances>
        <instance location="Requirements section, line 42">
          "Use React to build the component with Material UI..."
        </instance>
        <instance location="User Story ST-07">
          "Implement using Redux for state management..."
        </instance>
      </instances>

      <!-- Remediation for this anti-pattern -->
      <remediation>
        Reframe requirements to describe WHAT user needs, not HOW to implement.
        Move implementation details to technical design document.
      </remediation>
    </pattern>

    <!-- Additional anti-patterns follow same structure -->

  </anti_patterns>

  <!-- ═══════════════════════════════════════════════════════════════════════
       SUMMARY: Aggregate statistics and assessment
       ═══════════════════════════════════════════════════════════════════════ -->
  <summary>
    <!-- Total number of gaps found -->
    <total_gaps>NN</total_gaps>

    <!-- Gaps broken down by severity level -->
    <by_severity>
      <critical>N</critical>
      <high>N</high>
      <medium>N</medium>
      <low>N</low>
    </by_severity>

    <!-- Gaps broken down by gap type -->
    <by_category>
      <missing>N</missing>
      <incomplete>N</incomplete>
      <inconsistent>N</inconsistent>
      <ambiguous>N</ambiguous>
      <incorrect>N</incorrect>
      <outdated>N</outdated>
    </by_category>

    <!-- Count of anti-patterns detected -->
    <anti_patterns_detected>N</anti_patterns_detected>

    <!-- Overall assessment of PRD readiness -->
    <overall_assessment>critical_issues|significant_gaps|minor_issues|acceptable|excellent</overall_assessment>

    <!-- List of gaps that block development -->
    <blocking_issues>
      <issue ref="GAP-001">Missing problem statement - cannot define scope</issue>
      <issue ref="GAP-005">No acceptance criteria - cannot test features</issue>
      <!-- ... -->
    </blocking_issues>

    <!-- Checklist coverage statistics -->
    <coverage_score>
      <!-- Items that passed (present and clear) -->
      <items_passed>NN</items_passed>
      <!-- Total items checked -->
      <items_total>NN</items_total>
      <!-- Coverage percentage -->
      <percentage>NN%</percentage>
    </coverage_score>
  </summary>

  <!-- ═══════════════════════════════════════════════════════════════════════
       RECOMMENDATIONS: Prioritized next steps
       ═══════════════════════════════════════════════════════════════════════ -->
  <recommendations>

    <!-- Actions required before development can start -->
    <immediate_actions>
      <action ref="GAP-001" effort="medium">
        Write problem statement with stakeholder input - schedule 1-hour session
      </action>
      <action ref="GAP-005" effort="large">
        Define acceptance criteria for all user stories - 4-6 hour effort
      </action>
    </immediate_actions>

    <!-- Actions to complete before sprint begins -->
    <before_development>
      <action ref="GAP-008" effort="small">
        Clarify success metrics with specific targets and timelines
      </action>
      <action ref="GAP-012" effort="medium">
        Map external dependencies with timeline confirmation
      </action>
    </before_development>

    <!-- Actions that can be addressed during development -->
    <during_development>
      <action ref="GAP-015" effort="small">
        Expand edge case coverage in user stories
      </action>
      <action ref="GAP-018" effort="trivial">
        Update outdated stakeholder contacts
      </action>
    </during_development>

  </recommendations>

</gap_inventory>
```

---

## Field-by-Field Guidance

### Metadata Fields

| Field | Format | Example | Notes |
|-------|--------|---------|-------|
| `artifact_id` | GI-YYYY-MM-DD-XXXXX | GI-2024-03-15-7f8a2 | Use 5-char hash of PRD content |
| `created_at` | ISO 8601 | 2024-03-15T14:30:00Z | UTC timezone |
| `confidence` | 0.0-1.0 | 0.92 | Based on PRD clarity and audit coverage |
| `audit_depth` | enum | standard | Reflects parameter used |
| `items_checked` | integer | 106 | Actual count of items verified |

### Gap Fields

| Field | Format | Guidance |
|-------|--------|----------|
| `id` | GAP-NNN | Sequential within this audit |
| `category` | 6-type enum | Use decision tree from gap-taxonomy.md |
| `severity` | 4-level enum | Calculate using RUBRIC-07 formula |
| `location` | string | Be specific: "Section 3.2, line 47" or "Missing" |
| `evidence` | quote/description | Include actual PRD text when relevant |
| `remediation.effort` | 4-level enum | Based on remediation-patterns.md |
| `remediation.priority` | 4-level enum | Based on severity and development timeline |

### Summary Fields

| Field | Calculation | Notes |
|-------|-------------|-------|
| `total_gaps` | Count of `<gap>` elements | Must match actual gap count |
| `by_severity.*` | Count per severity level | Sum must equal total_gaps |
| `by_category.*` | Count per gap type | Sum must equal total_gaps |
| `overall_assessment` | Based on gap profile | See assessment rules below |
| `coverage_score.percentage` | (passed/total) × 100 | Round to nearest integer |

### Overall Assessment Rules

| Assessment | Criteria |
|------------|----------|
| `critical_issues` | Any CRITICAL gaps OR >5 HIGH gaps |
| `significant_gaps` | No CRITICAL but >3 HIGH gaps |
| `minor_issues` | No CRITICAL, ≤3 HIGH, some MEDIUM/LOW |
| `acceptable` | No CRITICAL/HIGH, only MEDIUM/LOW gaps |
| `excellent` | <5 total gaps, all LOW severity |

---

## Example Populated Output

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gap_inventory contract="CONTRACT-07" version="1.0">

  <metadata>
    <artifact_id>GI-2024-03-15-7f8a2</artifact_id>
    <contract_type>GAP-INVENTORY</contract_type>
    <created_at>2024-03-15T14:30:00Z</created_at>
    <created_by>prd-completeness-auditor</created_by>
    <confidence>0.92</confidence>
    <provenance>
      <source_artifact>Checkout Optimization PRD v2.1</source_artifact>
      <audit_date>2024-03-15</audit_date>
      <audit_depth>standard</audit_depth>
      <prd_type>feature</prd_type>
      <checklist_version>1.0</checklist_version>
      <items_checked>106</items_checked>
    </provenance>
  </metadata>

  <source_reference>checkout-optimization-prd-v2.1.md</source_reference>
  <source_type>document</source_type>

  <audit_criteria>
    <checklist_reference>prd-requirements-checklist.md v1.0</checklist_reference>
    <criteria_list>
      <criterion id="PC-01">Problem Statement</criterion>
      <criterion id="PC-02">Problem Evidence</criterion>
      <!-- ... 104 more items ... -->
    </criteria_list>
    <coverage_scope>
      Full audit of feature PRD covering 106 checklist items across
      10 sections. Anti-pattern scanning enabled.
    </coverage_scope>
  </audit_criteria>

  <gaps>
    <gap id="GAP-001">
      <category>missing</category>
      <severity>critical</severity>
      <severity_score>
        <impact>4</impact>
        <likelihood>4</likelihood>
        <detectability>1</detectability>
        <composite>3.4</composite>
      </severity_score>
      <checklist_ref>AC-01</checklist_ref>
      <location>User Stories section - no AC subsection exists</location>
      <description>
        User stories ST-03 through ST-08 have no acceptance criteria defined.
        Stories describe functionality but provide no verification criteria.
      </description>
      <evidence>
        ST-03: "As a customer, I want to save my cart so that I can return later."
        [No acceptance criteria section follows]
      </evidence>
      <impact>
        QA cannot write tests. Development may interpret requirements differently
        than intended. Likely rework when stories are reviewed.
      </impact>
      <remediation>
        <recommendation>
          Add Given/When/Then acceptance criteria for each user story.
          Minimum 2 criteria per story covering happy path and primary error case.
        </recommendation>
        <pattern_ref>RP-AC-01</pattern_ref>
        <effort>large</effort>
        <priority>immediate</priority>
      </remediation>
    </gap>

    <gap id="GAP-002">
      <category>ambiguous</category>
      <severity>high</severity>
      <severity_score>
        <impact>3</impact>
        <likelihood>3</likelihood>
        <detectability>2</detectability>
        <composite>2.8</composite>
      </severity_score>
      <checklist_ref>GS-03</checklist_ref>
      <location>Goals section, line 23</location>
      <description>
        Success metric "improved checkout completion" has no target or baseline.
      </description>
      <evidence>
        "Success: Checkout completion rate improves significantly."
      </evidence>
      <impact>
        Cannot determine if feature succeeds. Team may disagree on success post-launch.
      </impact>
      <remediation>
        <recommendation>
          Define specific target: "Checkout completion increases from 67% (baseline)
          to 78% within 30 days of launch."
        </recommendation>
        <pattern_ref>RP-GS-03</pattern_ref>
        <effort>small</effort>
        <priority>short_term</priority>
      </remediation>
    </gap>

    <gap id="GAP-003">
      <category>missing</category>
      <severity>high</severity>
      <severity_score>
        <impact>3</impact>
        <likelihood>3</likelihood>
        <detectability>2</detectability>
        <composite>2.8</composite>
      </severity_score>
      <checklist_ref>DP-01</checklist_ref>
      <location>N/A - no Dependencies section</location>
      <description>
        No dependencies section exists. PRD references "payment service" and
        "inventory system" without documenting integration requirements.
      </description>
      <evidence>
        Requirements mention: "integrate with payment service" (RQ-07)
        and "check inventory availability" (RQ-12) but no dependency mapping exists.
      </evidence>
      <impact>
        Unknown integration complexity. May be blocked by external team timelines.
        Risk of discovering issues late in development.
      </impact>
      <remediation>
        <recommendation>
          Add Dependencies section listing payment service and inventory system.
          Include: API versions, team contacts, timeline commitments.
        </recommendation>
        <pattern_ref>RP-DP-01</pattern_ref>
        <effort>medium</effort>
        <priority>short_term</priority>
      </remediation>
    </gap>
  </gaps>

  <anti_patterns>
    <pattern id="AP-06">
      <name>Edge Case Avoidance</name>
      <instances>
        <instance location="User Stories section">
          All 8 user stories describe happy paths only. No error handling,
          timeout scenarios, or edge cases documented.
        </instance>
      </instances>
      <remediation>
        Add user stories for: payment failure, inventory unavailable,
        session timeout, cart expiration. Minimum 3 error-path stories.
      </remediation>
    </pattern>
  </anti_patterns>

  <summary>
    <total_gaps>16</total_gaps>
    <by_severity>
      <critical>1</critical>
      <high>4</high>
      <medium>7</medium>
      <low>4</low>
    </by_severity>
    <by_category>
      <missing>6</missing>
      <incomplete>4</incomplete>
      <inconsistent>0</inconsistent>
      <ambiguous>5</ambiguous>
      <incorrect>0</incorrect>
      <outdated>1</outdated>
    </by_category>
    <anti_patterns_detected>1</anti_patterns_detected>
    <overall_assessment>significant_gaps</overall_assessment>
    <blocking_issues>
      <issue ref="GAP-001">Missing acceptance criteria for 6 user stories</issue>
    </blocking_issues>
    <coverage_score>
      <items_passed>78</items_passed>
      <items_total>106</items_total>
      <percentage>74%</percentage>
    </coverage_score>
  </summary>

  <recommendations>
    <immediate_actions>
      <action ref="GAP-001" effort="large">
        Write acceptance criteria for ST-03 through ST-08 before sprint planning
      </action>
    </immediate_actions>
    <before_development>
      <action ref="GAP-002" effort="small">Define success metric targets with baseline</action>
      <action ref="GAP-003" effort="medium">Map dependencies with payment and inventory teams</action>
    </before_development>
    <during_development>
      <action ref="GAP-008" effort="small">Expand edge case user stories</action>
    </during_development>
  </recommendations>

</gap_inventory>
```

---

## Validation Checklist

Before outputting GAP-INVENTORY:

```
[ ] artifact_id is unique and follows format
[ ] All required metadata fields present
[ ] source_reference identifies PRD
[ ] criteria_list matches items actually checked
[ ] Each gap has all required fields
[ ] Gap IDs are sequential (GAP-001, GAP-002, ...)
[ ] Severity scores calculate correctly
[ ] by_severity counts match gap list
[ ] by_category counts match gap list
[ ] total_gaps equals sum of by_severity
[ ] overall_assessment matches criteria
[ ] blocking_issues only includes CRITICAL gaps
[ ] coverage_score math is correct
[ ] All gap refs in recommendations exist
```
