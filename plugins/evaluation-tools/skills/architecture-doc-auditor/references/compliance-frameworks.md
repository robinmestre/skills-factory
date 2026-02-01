# Compliance Frameworks Reference

This reference documents architecture documentation requirements for major compliance frameworks: SOC 2, GDPR, PCI-DSS, HIPAA, and FedRAMP.

---

## Framework Overview

| Framework | Scope | Key Architecture Concerns | Severity if Missing |
|-----------|-------|--------------------------|---------------------|
| **SOC 2** | Service organizations | Access control, monitoring, encryption | HIGH |
| **GDPR** | EU personal data | Data protection, consent, rights | HIGH (if applicable) |
| **PCI-DSS** | Payment card data | CDE scope, encryption, segmentation | CRITICAL (if applicable) |
| **HIPAA** | Healthcare data (US) | PHI protection, access controls | CRITICAL (if applicable) |
| **FedRAMP** | US federal systems | Comprehensive security controls | CRITICAL (if applicable) |

---

## 1. SOC 2 (System and Organization Controls)

### Overview

SOC 2 is an auditing framework for service organizations based on Trust Services Criteria. It focuses on security, availability, processing integrity, confidentiality, and privacy.

### Trust Services Criteria

| Criteria | Description | Architecture Relevance |
|----------|-------------|----------------------|
| **Security** | Protection against unauthorized access | V7 (Security Architecture) |
| **Availability** | System available for operation | V4 (Deployment), V8 (Operations) |
| **Processing Integrity** | Complete, valid, accurate processing | V5 (Data), V6 (Integration) |
| **Confidentiality** | Data protected as committed | V5 (Data), V7 (Security) |
| **Privacy** | Personal info handling | V5 (Data), V7 (Security) |

### Architecture Documentation Requirements

#### Access Control (CC6.1-CC6.8)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Logical access controls | Authentication architecture | V7 |
| User access provisioning | User management flows | V7 |
| Access removal process | Deprovisioning flows | V7 |
| Role-based access | Authorization model | V7 |
| Physical access controls | Data center security | V4 |
| System boundaries | Network segmentation | V4, V7 |

**Checklist Items:**
```
CF-SOC2-01: Authentication mechanism documented
CF-SOC2-02: Authorization model (RBAC/ABAC) documented
CF-SOC2-03: Access provisioning process defined
CF-SOC2-04: Access removal process defined
CF-SOC2-05: Network segmentation documented
CF-SOC2-06: Session management approach defined
```

#### Change Management (CC8.1)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Change control process | CI/CD pipeline | V4 |
| Change authorization | Approval workflows | V10 |
| Change testing | Testing strategy | V3 |
| Change deployment | Deployment process | V4 |

**Checklist Items:**
```
CF-SOC2-07: CI/CD pipeline documented
CF-SOC2-08: Change approval process defined
CF-SOC2-09: Testing strategy documented
CF-SOC2-10: Rollback procedure defined
```

#### Monitoring (CC7.1-CC7.4)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Security event monitoring | Audit logging | V7, V8 |
| Incident detection | Alerting rules | V8 |
| Incident response | IR procedures | V7 |
| Vulnerability management | Security testing | V7 |

**Checklist Items:**
```
CF-SOC2-11: Audit logging strategy documented
CF-SOC2-12: Security monitoring approach defined
CF-SOC2-13: Alerting rules documented
CF-SOC2-14: Incident response process defined
CF-SOC2-15: Vulnerability management approach defined
```

#### Encryption (CC6.7)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Encryption at rest | Data encryption | V5, V7 |
| Encryption in transit | TLS configuration | V6, V7 |
| Key management | KMS approach | V7 |

**Checklist Items:**
```
CF-SOC2-16: Encryption at rest documented
CF-SOC2-17: Encryption in transit (TLS) documented
CF-SOC2-18: Key management approach defined
CF-SOC2-19: Certificate management documented
```

### SOC 2 Architecture Audit Checklist

| # | Item | Severity | Viewpoints |
|---|------|----------|------------|
| 1 | Authentication architecture | HIGH | V7 |
| 2 | Authorization model | HIGH | V7 |
| 3 | Audit logging | HIGH | V7, V8 |
| 4 | Encryption at rest | HIGH | V5, V7 |
| 5 | Encryption in transit | HIGH | V6, V7 |
| 6 | Key management | MEDIUM | V7 |
| 7 | Change management | MEDIUM | V4, V10 |
| 8 | Incident response | HIGH | V7, V8 |
| 9 | Monitoring strategy | HIGH | V8 |
| 10 | Network segmentation | MEDIUM | V4, V7 |

---

## 2. GDPR (General Data Protection Regulation)

### Overview

GDPR is the EU regulation for personal data protection. Architecture documentation must demonstrate data protection by design and default.

### Key Principles

| Principle | Description | Architecture Relevance |
|-----------|-------------|----------------------|
| **Lawfulness** | Legal basis for processing | V5 (Data flows) |
| **Purpose limitation** | Specific, explicit purposes | V5, V10 |
| **Data minimization** | Adequate, relevant, limited | V5 |
| **Accuracy** | Kept up to date | V5 |
| **Storage limitation** | Kept no longer than necessary | V5 |
| **Integrity/Confidentiality** | Appropriate security | V7 |

### Architecture Documentation Requirements

#### Data Protection by Design (Article 25)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Privacy by design | Data classification | V5 |
| Data minimization | Data collection points | V5 |
| Purpose limitation | Data flow documentation | V5 |
| Default privacy | Consent management | V5, V6 |

**Checklist Items:**
```
CF-GDPR-01: Personal data inventory documented
CF-GDPR-02: Data classification scheme applied
CF-GDPR-03: Data flow diagrams show PII flows
CF-GDPR-04: Purpose for each data element documented
CF-GDPR-05: Consent management approach defined
```

#### Data Subject Rights (Articles 15-22)

| Right | Architecture Element | Viewpoint |
|-------|---------------------|-----------|
| Access | Data export capability | V5, V6 |
| Rectification | Data update flows | V5 |
| Erasure | Deletion capability | V5 |
| Portability | Data export format | V5, V6 |
| Restriction | Processing control | V5 |

**Checklist Items:**
```
CF-GDPR-06: Data subject access capability documented
CF-GDPR-07: Data deletion (erasure) capability documented
CF-GDPR-08: Data portability export format defined
CF-GDPR-09: Processing restriction capability documented
CF-GDPR-10: Data rectification process defined
```

#### Security of Processing (Article 32)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Pseudonymization | Data masking approach | V5, V7 |
| Encryption | Encryption standards | V7 |
| Resilience | DR/backup strategy | V4 |
| Testing | Security testing | V7 |

**Checklist Items:**
```
CF-GDPR-11: Pseudonymization approach documented
CF-GDPR-12: Encryption standards defined
CF-GDPR-13: Data backup strategy documented
CF-GDPR-14: Disaster recovery for personal data defined
```

#### Data Transfers (Chapter V)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Cross-border transfers | Data location | V4 |
| Adequacy decisions | Transfer mechanisms | V5 |
| Standard clauses | Contractual basis | V1 |

**Checklist Items:**
```
CF-GDPR-15: Data location/region documented
CF-GDPR-16: Cross-border transfer mechanisms documented
CF-GDPR-17: Third-party data processors identified
```

### GDPR Architecture Audit Checklist

| # | Item | Severity | Viewpoints |
|---|------|----------|------------|
| 1 | Personal data inventory | HIGH | V5 |
| 2 | Data flow documentation | HIGH | V5 |
| 3 | Data subject rights support | HIGH | V5, V6 |
| 4 | Deletion capability | HIGH | V5 |
| 5 | Data location documentation | HIGH | V4 |
| 6 | Encryption | HIGH | V7 |
| 7 | Consent management | MEDIUM | V5, V6 |
| 8 | Data retention policies | HIGH | V5 |
| 9 | Third-party processors | MEDIUM | V1, V5 |
| 10 | Breach notification capability | HIGH | V7, V8 |

---

## 3. PCI-DSS (Payment Card Industry Data Security Standard)

### Overview

PCI-DSS applies to any organization handling payment card data. Architecture documentation must clearly define the Cardholder Data Environment (CDE).

### Requirements Categories

| Requirement | Description | Architecture Relevance |
|-------------|-------------|----------------------|
| **Build/Maintain Secure Network** | Firewall, no defaults | V4, V7 |
| **Protect Cardholder Data** | Encryption, storage limits | V5, V7 |
| **Vulnerability Management** | Anti-malware, secure systems | V7 |
| **Access Control** | Need-to-know, unique IDs | V7 |
| **Monitor/Test** | Logging, testing | V7, V8 |
| **Security Policy** | Information security policy | V10 |

### Architecture Documentation Requirements

#### Cardholder Data Environment (Requirement 1)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| CDE scope definition | System boundary | V1 |
| Network segmentation | Network topology | V4 |
| Data flow documentation | CHD flows | V5 |
| Connected systems | Integration inventory | V1, V6 |

**Checklist Items:**
```
CF-PCI-01: CDE scope explicitly defined
CF-PCI-02: CDE boundary diagram present
CF-PCI-03: Network segmentation documented
CF-PCI-04: All CHD flows documented
CF-PCI-05: Connected systems inventory complete
```

#### Encryption (Requirements 3, 4)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Stored CHD protection | Encryption approach | V5, V7 |
| Transmission encryption | TLS configuration | V6, V7 |
| Key management | KMS, key lifecycle | V7 |

**Checklist Items:**
```
CF-PCI-06: CHD encryption at rest documented
CF-PCI-07: CHD encryption in transit documented
CF-PCI-08: Key management procedures defined
CF-PCI-09: PAN masking/truncation approach defined
```

#### Access Control (Requirements 7, 8)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Restrict access | Authorization model | V7 |
| Unique IDs | Authentication system | V7 |
| MFA | MFA implementation | V7 |

**Checklist Items:**
```
CF-PCI-10: CDE access control documented
CF-PCI-11: Unique ID assignment documented
CF-PCI-12: MFA for CDE access documented
CF-PCI-13: Admin access controls documented
```

#### Logging and Monitoring (Requirement 10)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Audit trails | Logging architecture | V7, V8 |
| Log protection | Log storage security | V8 |
| Log review | Monitoring approach | V8 |

**Checklist Items:**
```
CF-PCI-14: CDE audit logging documented
CF-PCI-15: Log storage and retention defined
CF-PCI-16: Log review process documented
CF-PCI-17: Security monitoring for CDE defined
```

### PCI-DSS Architecture Audit Checklist

| # | Item | Severity | Viewpoints |
|---|------|----------|------------|
| 1 | CDE scope definition | CRITICAL | V1 |
| 2 | Network segmentation | CRITICAL | V4, V7 |
| 3 | CHD encryption at rest | CRITICAL | V5, V7 |
| 4 | CHD encryption in transit | CRITICAL | V6, V7 |
| 5 | Key management | CRITICAL | V7 |
| 6 | Access control model | HIGH | V7 |
| 7 | MFA implementation | HIGH | V7 |
| 8 | Audit logging | HIGH | V7, V8 |
| 9 | Vulnerability scanning | HIGH | V7 |
| 10 | Penetration testing | HIGH | V7 |

---

## 4. HIPAA (Health Insurance Portability and Accountability Act)

### Overview

HIPAA applies to covered entities and business associates handling Protected Health Information (PHI) in the US healthcare system.

### Security Rule Categories

| Safeguard | Description | Architecture Relevance |
|-----------|-------------|----------------------|
| **Administrative** | Policies, procedures, training | V10 |
| **Physical** | Facility access, workstation security | V4 |
| **Technical** | Access control, audit, encryption | V7 |

### Architecture Documentation Requirements

#### Technical Safeguards (§164.312)

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Access control | Authentication/authorization | V7 |
| Audit controls | Logging architecture | V7, V8 |
| Integrity controls | Data integrity mechanisms | V5, V7 |
| Transmission security | Encryption in transit | V6, V7 |

**Checklist Items:**
```
CF-HIPAA-01: PHI access control architecture documented
CF-HIPAA-02: Unique user identification documented
CF-HIPAA-03: Emergency access procedure defined
CF-HIPAA-04: Automatic logoff implemented
CF-HIPAA-05: PHI audit logging documented
CF-HIPAA-06: PHI integrity mechanisms documented
CF-HIPAA-07: PHI transmission encryption documented
```

#### Addressable Specifications

| Specification | Architecture Element | Viewpoint |
|---------------|---------------------|-----------|
| Encryption at rest | Data encryption | V5, V7 |
| Mechanism verification | Entity authentication | V7 |
| Authentication | User verification | V7 |

**Checklist Items:**
```
CF-HIPAA-08: PHI encryption at rest documented
CF-HIPAA-09: Entity authentication mechanisms defined
CF-HIPAA-10: Encryption key management documented
```

### HIPAA Architecture Audit Checklist

| # | Item | Severity | Viewpoints |
|---|------|----------|------------|
| 1 | PHI access controls | CRITICAL | V7 |
| 2 | Audit logging | HIGH | V7, V8 |
| 3 | Encryption in transit | CRITICAL | V6, V7 |
| 4 | Encryption at rest | HIGH | V5, V7 |
| 5 | Emergency access | MEDIUM | V7 |
| 6 | Automatic logoff | MEDIUM | V7 |
| 7 | Integrity controls | HIGH | V5, V7 |
| 8 | Entity authentication | HIGH | V7 |

---

## 5. FedRAMP (Federal Risk and Authorization Management Program)

### Overview

FedRAMP is the US government's standardized approach to security assessment for cloud services used by federal agencies.

### Impact Levels

| Level | Description | Control Count |
|-------|-------------|---------------|
| **Low** | Limited adverse effect | ~125 controls |
| **Moderate** | Serious adverse effect | ~325 controls |
| **High** | Severe/catastrophic effect | ~425 controls |

### Key Architecture Requirements

#### Boundary Definition

| Requirement | Architecture Element | Viewpoint |
|-------------|---------------------|-----------|
| Authorization boundary | System scope | V1 |
| Data flow diagrams | All data flows | V5 |
| Network diagrams | Network topology | V4 |
| Interconnections | External connections | V1, V6 |

**Checklist Items:**
```
CF-FEDRAMP-01: Authorization boundary defined
CF-FEDRAMP-02: Complete data flow diagrams
CF-FEDRAMP-03: Network architecture diagrams
CF-FEDRAMP-04: All interconnections documented
CF-FEDRAMP-05: External interfaces documented
```

#### Access Control (AC Family)

| Control | Architecture Element | Viewpoint |
|---------|---------------------|-----------|
| AC-2: Account management | User management | V7 |
| AC-3: Access enforcement | Authorization | V7 |
| AC-4: Information flow | Data flow control | V5, V7 |
| AC-17: Remote access | Remote access architecture | V7 |

**Checklist Items:**
```
CF-FEDRAMP-06: Account management architecture
CF-FEDRAMP-07: Access enforcement mechanisms
CF-FEDRAMP-08: Information flow controls
CF-FEDRAMP-09: Remote access architecture
```

#### Audit and Accountability (AU Family)

| Control | Architecture Element | Viewpoint |
|---------|---------------------|-----------|
| AU-2: Audit events | Logging scope | V8 |
| AU-3: Audit content | Log format | V8 |
| AU-6: Audit review | Log analysis | V8 |

**Checklist Items:**
```
CF-FEDRAMP-10: Audit event types documented
CF-FEDRAMP-11: Audit log content defined
CF-FEDRAMP-12: Audit log review process
CF-FEDRAMP-13: Log retention policy
```

### FedRAMP Architecture Audit Checklist

| # | Item | Severity | Viewpoints |
|---|------|----------|------------|
| 1 | Authorization boundary | CRITICAL | V1 |
| 2 | Data flow diagrams | CRITICAL | V5 |
| 3 | Network diagrams | CRITICAL | V4 |
| 4 | Interconnection docs | HIGH | V1, V6 |
| 5 | Access control model | CRITICAL | V7 |
| 6 | Audit logging | HIGH | V8 |
| 7 | Encryption requirements | HIGH | V7 |
| 8 | Incident response | HIGH | V7, V8 |
| 9 | Contingency planning | HIGH | V4 |
| 10 | Configuration management | MEDIUM | V4, V9 |

---

## Compliance Detection Algorithm

```python
def detect_compliance_requirements(document: str, context: dict) -> list:
    """
    Detect applicable compliance frameworks from document content.
    """
    frameworks = []

    # Explicit mentions
    if has_compliance_signals(document, ['soc 2', 'soc2', 'trust services']):
        frameworks.append('SOC2')

    if has_compliance_signals(document, ['gdpr', 'personal data', 'data subject']):
        frameworks.append('GDPR')

    if has_compliance_signals(document, ['pci', 'payment card', 'cardholder']):
        frameworks.append('PCI-DSS')

    if has_compliance_signals(document, ['hipaa', 'phi', 'protected health']):
        frameworks.append('HIPAA')

    if has_compliance_signals(document, ['fedramp', 'federal', 'fisma']):
        frameworks.append('FedRAMP')

    # Context-based inference
    if context.get('industry') == 'healthcare':
        if 'HIPAA' not in frameworks:
            frameworks.append('HIPAA')  # Should be there

    if context.get('handles_payments'):
        if 'PCI-DSS' not in frameworks:
            frameworks.append('PCI-DSS')  # Should be there

    return frameworks
```

---

## Compliance Matrix Output Format

```xml
<compliance_assessment>
  <framework name="SOC2">
    <status>PARTIAL</status>
    <controls_documented>15</controls_documented>
    <controls_required>19</controls_required>
    <gaps>
      <gap control="CC7.2" severity="HIGH">
        Incident response process not documented
      </gap>
    </gaps>
  </framework>
  <framework name="GDPR">
    <status>ADEQUATE</status>
    <controls_documented>16</controls_documented>
    <controls_required>17</controls_required>
    <gaps>
      <gap control="Article-17" severity="MEDIUM">
        Data deletion capability unclear
      </gap>
    </gaps>
  </framework>
</compliance_assessment>
```

---

## References

- [SOC 2 Trust Services Criteria](https://us.aicpa.org/interestareas/frc/assuranceadvisoryservices/aaboratifications)
- [GDPR Official Text](https://gdpr.eu/tag/gdpr/)
- [PCI-DSS Requirements](https://www.pcisecuritystandards.org/document_library)
- [HIPAA Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/index.html)
- [FedRAMP Documentation](https://www.fedramp.gov/documents/)
