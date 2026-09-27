---
description: >-
  Nine class diagrams mapping the audit concepts tested in EPSO/AD/428/26 and
  the relationships between them.
---

# EPSO/AD/428/26

## Audit concepts and how they connect

Most MCQ distractors are not wrong facts, they are wrong _relationships_: the risk the auditor does not control, the element a finding is missing, the standard that governs the wrong audit type. Read the arrows, not just the boxes.

{% hint style="info" %}
**Reading the notation**

Composition (filled diamond) means _is made of_. Inheritance (hollow triangle) means _is a kind of_. A plain arrow means _acts on_. Half the content is in the arrow types.
{% endhint %}

### 1. The audit risk model

_Duty cluster: Risk-based audit work_

Audit risk decomposes once, into the risk that a misstatement exists and the risk that the audit fails to catch it. The first belongs to the entity and the auditor can only assess it; the second belongs to the auditor and is the only dial available.

```mermaid
classDiagram
    class AuditRisk {
        +risk of an inappropriate audit opinion
        +AR = IR x CR x DR
        +acceptable level chosen by the auditor
    }
    class RiskOfMaterialMisstatement {
        +RMM = IR x CR
        +exists whether or not an audit happens
    }
    class InherentRisk {
        +susceptibility before any control
        +drivers are complexity, judgement, change, cash
    }
    class ControlRisk {
        +a control fails to prevent or detect
        +assessed by testing controls
    }
    class DetectionRisk {
        +procedures fail to find a misstatement
        +the only component the auditor controls
        +lowered by nature, timing and extent of work
    }
    class SamplingRisk {
        +the sample is not representative
    }
    class NonSamplingRisk {
        +wrong procedure or misread result
    }
    class ResidualRisk {
        +inherent risk after management response
        +the basis for risk-based planning
    }
    class Materiality {
        +threshold above which a misstatement matters
        +ECA applies 2 percent to legality and regularity
    }
    AuditRisk *-- RiskOfMaterialMisstatement
    AuditRisk *-- DetectionRisk
    RiskOfMaterialMisstatement *-- InherentRisk
    RiskOfMaterialMisstatement *-- ControlRisk
    DetectionRisk *-- SamplingRisk
    DetectionRisk *-- NonSamplingRisk
    InherentRisk --> ResidualRisk : less the effect of controls
    RiskOfMaterialMisstatement --> DetectionRisk : higher RMM forces lower DR
    Materiality --> AuditRisk : calibrates
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Inherent before controls, residual after.** Residual risk is a management and planning concept; control risk is an audit assessment. They are not synonyms.
* **Only detection risk is the auditor's.** A question asking what the auditor does when control risk rises is answered by more substantive work, never by raising materiality or re-assessing inherent risk.
* **Sampling risk is a part of detection risk**, not a separate fourth term in the model.
{% endhint %}

### 2. Anatomy of a finding

_Duty cluster: Conclusions and recommendations_

A finding is a four-part structure, and each part does a distinct job downstream: criteria make the gap arguable, effect sets the priority, cause determines what the recommendation must address. Drop one element and the finding is only an observation.

```mermaid
classDiagram
    class Finding {
        +complete only with all four elements
        +classified by significance
    }
    class Criteria {
        +the benchmark, what should be
        +law, contract, standard, good practice
    }
    class Condition {
        +what the auditor observed, what is
    }
    class Cause {
        +why the gap exists
    }
    class Effect {
        +consequence, actual or potential
    }
    class Conclusion {
        +answers the audit question at objective level
    }
    class Recommendation {
        +addressed to whoever can implement it
        +specific, actionable, proportionate
        +does not design management's solution
    }
    class ManagementResponse {
        +accept, partially accept or reject
        +accepting risk is management's right
    }
    class FollowUp {
        +tests whether the action was effective
        +not whether management replied
    }
    class ContradictoryProcedure {
        +auditee confirms facts and comments
        +conclusions remain the auditor's
    }
    Finding *-- Criteria
    Finding *-- Condition
    Finding *-- Cause
    Finding *-- Effect
    Criteria --> Condition : compared with
    Effect --> Finding : sets priority
    Cause --> Recommendation : addressed by
    Finding "many" --> "1" Conclusion : aggregate into
    Recommendation --> ManagementResponse : triggers
    ManagementResponse --> FollowUp : verified by
    Finding --> ContradictoryProcedure : cleared through
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Recommendations attach to cause, not condition.** That is the whole point of root cause analysis, and the reason a recommendation that fixes the symptom is marked wrong.
* **Conclusion sits above findings.** It answers the audit question; findings support it.
* **The contradictory procedure validates facts, not conclusions.** Auditee agreement is never a condition of publication.
* **Follow-up tests effect, not response.** A management assertion that action was taken is not evidence that it worked.
{% endhint %}

### 3. Reports and opinions

_Duty cluster: Audit reporting_

Opinion type is decided by two questions in order: is the problem disagreement or missing evidence, and is it material but contained, or material and pervasive. Emphasis of matter sits outside that grid entirely.

```mermaid
classDiagram
    class AuditReport {
        +objective, scope, criteria, methodology
        +balanced, timely, evidence based
    }
    class ExecutiveSummary {
        +key messages for readers who stop there
    }
    class AuditOpinion
    class UnmodifiedOpinion {
        +no material misstatement found
    }
    class QualifiedOpinion {
        +material but not pervasive
    }
    class AdverseOpinion {
        +disagreement, material and pervasive
    }
    class DisclaimerOfOpinion {
        +evidence unobtainable, effect pervasive
    }
    class EmphasisOfMatter {
        +draws attention to a disclosed matter
        +does not modify the opinion
    }
    class FraudSuspicion {
        +reported to OLAF or the EPPO
        +the auditor reports, does not investigate
    }
    AuditReport *-- ExecutiveSummary
    AuditReport *-- AuditOpinion
    AuditOpinion <|-- UnmodifiedOpinion
    AuditOpinion <|-- QualifiedOpinion
    AuditOpinion <|-- AdverseOpinion
    AuditOpinion <|-- DisclaimerOfOpinion
    AuditReport --> EmphasisOfMatter : may carry
    AuditReport --> FraudSuspicion : channelled separately
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Adverse is disagreement, disclaimer is absence of evidence.** Both pervasive; the difference is the reason.
* **Emphasis of matter never modifies the opinion.** An option saying it substitutes for a qualification is always wrong.
* **Balance is not arithmetic.** It means context and the auditee's position, not equal counts of praise and criticism, and never dropping a contested finding.
* **Fraud goes through the channel, fast.** Not investigation, not confrontation, not waiting for proof.
{% endhint %}

### 4. Evidence and sampling

_Duty cluster: Evidence, data and documentation_

Evidence has two independent qualities and both must hold: more of a poor source never cures inappropriateness. The sampling branch decides one thing above all, whether you may extrapolate to the population.

```mermaid
classDiagram
    class Evidence {
        +sufficiency is quantity
        +appropriateness is quality
    }
    class Appropriateness
    class Relevance {
        +addresses the assertion being tested
    }
    class Reliability {
        +external over internal
        +auditor obtained over entity prepared
        +written over oral, original over copy
    }
    class Procedure
    class TestOfControls {
        +did the control operate
    }
    class SubstantiveProcedure {
        +is the amount itself correct
    }
    class AnalyticalProcedure
    class Sampling
    class StatisticalSampling {
        +permits extrapolation
    }
    class MonetaryUnitSampling {
        +selection proportional to value
        +effective against overstatement
    }
    class JudgementalSampling {
        +no statistical extrapolation
    }
    class ProjectedError {
        +sample error extrapolated to the population
    }
    class Materiality
    class AuditDocumentation {
        +the experienced auditor with no prior connection test
    }
    class AuditTrail {
        +reconciles declared amounts to records at every level
    }
    Evidence *-- Appropriateness
    Appropriateness *-- Relevance
    Appropriateness *-- Reliability
    Procedure --> Evidence : produces
    Procedure <|-- TestOfControls
    Procedure <|-- SubstantiveProcedure
    SubstantiveProcedure <|-- AnalyticalProcedure
    Sampling --> Procedure : selects items for
    Sampling <|-- StatisticalSampling
    Sampling <|-- JudgementalSampling
    StatisticalSampling <|-- MonetaryUnitSampling
    StatisticalSampling --> ProjectedError : yields
    ProjectedError --> Materiality : compared with
    Evidence --> AuditDocumentation : recorded in
    AuditDocumentation --> AuditTrail : underpins
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Sufficiency is how much, appropriateness is how good.** Appropriateness splits further into relevance and reliability; sufficiency does not split.
* **A test of controls asks whether the control operated.** Anything testing the amount itself is substantive, however it is dressed up.
* **The sample means nothing until projected** and compared with materiality. Extending a sample until errors vanish is bias.
* **Full-population analytics removes sampling risk on the exceptions found**, not the need to corroborate them, and never proves intent.
{% endhint %}

### 5. What kind of audit, under what standard

_Duty cluster: Audit types and standards_

Two taxonomies are in play and candidates conflate them. Financial, compliance and performance are _kinds of audit_. Internal and external are _functions_ defined by whom they serve. Either function can perform any kind.

```mermaid
classDiagram
    class Audit {
        +objective, scope and criteria
        +sufficient appropriate evidence
    }
    class FinancialAudit {
        +true and fair view
    }
    class ComplianceAudit {
        +conformity with the applicable authorities
    }
    class PerformanceAudit {
        +economy, efficiency, effectiveness
    }
    class InternalAudit {
        +serves the organisation's own governance
        +assurance and advisory services
    }
    class ExternalAudit {
        +reports to external stakeholders
        +independent of management
    }
    class ISSAI100 {
        +fundamental principles of public sector auditing
    }
    class ISSAI200
    class ISSAI300
    class ISSAI400
    class INTOSAI_P10 {
        +Mexico Declaration
        +eight principles of SAI independence
    }
    class GlobalInternalAuditStandards {
        +2024, effective 9 January 2025
        +5 domains, 15 principles, 52 standards
    }
    Audit <|-- FinancialAudit
    Audit <|-- ComplianceAudit
    Audit <|-- PerformanceAudit
    InternalAudit --> Audit : performs
    ExternalAudit --> Audit : performs
    ISSAI100 <|-- ISSAI200
    ISSAI100 <|-- ISSAI300
    ISSAI100 <|-- ISSAI400
    ISSAI200 --> FinancialAudit : governs
    ISSAI300 --> PerformanceAudit : governs
    ISSAI400 --> ComplianceAudit : governs
    GlobalInternalAuditStandards --> InternalAudit : governs
    INTOSAI_P10 --> ExternalAudit : underpins independence
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **ISSAI 100 / 200 / 300 / 400** — fundamental, financial, performance, compliance. Free marks if memorised.
* **Lima versus Mexico.** INTOSAI-P 1 states the broad precepts; INTOSAI-P 10 sets the eight independence principles.
* **Internal audit is defined by who it serves**, not by what it examines. An internal audit function can and does run performance audits.
* **The 2024 Standards replaced the IPPF.** An option citing the old _International Standards for the Professional Practice of Internal Auditing_ numbering may be the planted distractor.
{% endhint %}

### 6. Internal control and governance

_Duty cluster: Assessment of audited bodies_

Internal control is what the entity builds; the three lines describe who does what with it; governance oversees the whole arrangement. The auditor is in the third line and therefore inside the picture, not above it.

```mermaid
classDiagram
    class InternalControl {
        +reasonable, never absolute assurance
        +COSO 2013, 5 components, 17 principles
    }
    class ControlEnvironment {
        +integrity, ethical values, tone at the top
        +conditions every other component
    }
    class RiskAssessment
    class ControlActivities
    class InformationAndCommunication
    class MonitoringActivities
    class InherentLimitation {
        +human error and collusion
        +management override, cost benefit limits
    }
    class ThreeLinesModel
    class FirstLine {
        +owns and manages the risk
    }
    class SecondLine {
        +risk, compliance and controlling functions
    }
    class ThirdLine {
        +internal audit, independent assurance
    }
    class Governance
    class AuditCommittee {
        +oversees reporting, control and both audits
        +does not manage risk responses
    }
    class RiskAppetite {
        +risk accepted in pursuit of objectives
    }
    InternalControl *-- ControlEnvironment
    InternalControl *-- RiskAssessment
    InternalControl *-- ControlActivities
    InternalControl *-- InformationAndCommunication
    InternalControl *-- MonitoringActivities
    InternalControl --> InherentLimitation : constrained by
    ThreeLinesModel *-- FirstLine
    ThreeLinesModel *-- SecondLine
    ThreeLinesModel *-- ThirdLine
    FirstLine --> InternalControl : operates
    Governance *-- AuditCommittee
    Governance --> RiskAppetite : sets
    ThirdLine --> AuditCommittee : reports to
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Reasonable, not absolute.** The reason is inherent limitation, not weak audit work or incomplete documentation.
* **Second line supports and monitors; it does not own the risk.** The first line does.
* **The audit committee oversees.** It does not manage responses, approve financial statements on the board's behalf, or run investigations.
* **Economy, efficiency, effectiveness** — cost of inputs, output per input, objectives achieved. Expect a worked example rather than a definition.
{% endhint %}

### 7. General and application controls

_Duty cluster: IT system audits_

One dependency governs this whole area: application controls are only as trustworthy as the general controls beneath them. Everything else follows from that reliance chain.

```mermaid
classDiagram
    class ITGeneralControls {
        +the foundation for every application control
    }
    class AccessToProgramsAndData
    class ProgramChange
    class ProgramDevelopment
    class ComputerOperations
    class ApplicationControl {
        +input, processing and output controls
        +reliable only if the ITGC hold
    }
    class SegregationOfDuties {
        +developer with production access is the classic failure
    }
    class UserAccessReview {
        +compare rights to authorised roles and HR leavers
    }
    class BusinessContinuity
    class RecoveryTimeObjective {
        +tolerable time to restore service
    }
    class RecoveryPointObjective {
        +tolerable data loss, expressed in time
    }
    class COBIT {
        +governance and management of enterprise IT
    }
    class DataAnalytics {
        +tests the full population
        +requires data reliability first
    }
    ITGeneralControls *-- AccessToProgramsAndData
    ITGeneralControls *-- ProgramChange
    ITGeneralControls *-- ProgramDevelopment
    ITGeneralControls *-- ComputerOperations
    ITGeneralControls --> ApplicationControl : enables reliance on
    AccessToProgramsAndData --> SegregationOfDuties : enforces
    AccessToProgramsAndData --> UserAccessReview : tested by
    BusinessContinuity *-- RecoveryTimeObjective
    BusinessContinuity *-- RecoveryPointObjective
    COBIT --> ITGeneralControls : frames
    DataAnalytics --> ApplicationControl : substitutes testing of
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Weak ITGC means application controls cannot be relied on**, however well designed they are.
* **RPO is data loss, RTO is downtime.** Both in units of time, which is what makes the pair confusable.
* **COBIT governs, ISO 27001 certifies.** Different instruments, routinely swapped in distractors.
* **Access appropriateness is tested against current authorised roles**, not against the approval form filed when the system went live.
{% endhint %}

### 8. Who audits the EU budget

_Duty cluster: EU institutional framework_

The distinctions that carry marks here are external versus internal versus investigative, and which management mode puts which body in the chain. The Court audits and reports; Parliament discharges; OLAF and the EPPO investigate and prosecute, and are not auditors.

```mermaid
classDiagram
    class EUBudget {
        +Financial Regulation, 2024 recast
        +sound financial management is economy efficiency effectiveness
    }
    class ManagementMode
    class DirectManagement {
        +Commission services and executive agencies
    }
    class SharedManagement {
        +entrusted to the Member States
    }
    class IndirectManagement {
        +entrusted entities
    }
    class EuropeanCourtOfAuditors {
        +Article 287 TFEU
        +statement of assurance on accounts and transactions
        +2 percent materiality
    }
    class InternalAuditService {
        +assurance to the Commission
        +Audit Progress Committee oversees follow up
    }
    class AuthorisingOfficerByDelegation {
        +signs the declaration of assurance in the annual activity report
        +enters reservations where the impact is material
    }
    class Discharge {
        +Article 319 TFEU
        +Parliament decides on a Council recommendation
    }
    class ManagingAuthority {
        +selects and monitors operations
    }
    class AuditAuthority {
        +independent opinion on the accounts
    }
    class AssurancePackage {
        +accounts and management declaration
        +annual control report and audit opinion
    }
    class SingleAudit {
        +rely on work done below, do not duplicate
    }
    class OLAF_EPPO {
        +investigation and prosecution, not audit
    }
    EUBudget *-- ManagementMode
    ManagementMode <|-- DirectManagement
    ManagementMode <|-- SharedManagement
    ManagementMode <|-- IndirectManagement
    EuropeanCourtOfAuditors --> EUBudget : audits externally
    EuropeanCourtOfAuditors --> Discharge : reports for
    InternalAuditService --> AuthorisingOfficerByDelegation : recommends to
    AuthorisingOfficerByDelegation --> AssurancePackage : relies on
    SharedManagement *-- ManagingAuthority
    SharedManagement *-- AuditAuthority
    AuditAuthority --> AssurancePackage : gives the opinion in
    AuditAuthority --> SingleAudit : work relied on under
    OLAF_EPPO --> EUBudget : protects
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **Article 287 is the Court's mandate, Article 319 is discharge.** The Court does not grant discharge; Parliament does, on a Council recommendation.
* **The 2 percent recurs in three roles** — Court materiality, the residual error ceiling for cohesion accounts, and the trigger for further corrections. Read which one is being asked.
* **Shared management means Member States implement**; indirect means entrusted entities. Direct is the Commission itself.
* **Single audit avoids duplication; it does not limit who may audit.**
* **The Financial Regulation in force is the 2024 recast.** References to the 2018 regulation are superseded.
{% endhint %}

### 9. The engagement lifecycle

_Duty cluster: Planning, supervision and quality_

The universe narrows to a plan by risk, the plan resolves into engagements, and a quality programme sits across all of it. Note who owns each step: the chief audit executive develops the plan, the board approves it, management implements recommendations.

```mermaid
classDiagram
    class AuditUniverse {
        +everything auditable within the mandate
    }
    class RiskBasedPlan {
        +developed by the chief audit executive
        +approved by the board
        +revised when risks change
    }
    class AssuranceMap {
        +shows overlaps and gaps across providers
    }
    class Engagement
    class Planning {
        +objective, scope, criteria, programme
    }
    class Fieldwork {
        +procedures and evidence
    }
    class Reporting
    class FollowUp
    class Supervision {
        +documented review, review notes cleared
    }
    class QAIP {
        +internal and external components
    }
    class OngoingMonitoring
    class PeriodicSelfAssessment
    class ExternalQualityAssessment {
        +at least once every five years
        +qualified and independent provider
    }
    class PeerReview {
        +voluntary assessment by other SAIs
    }
    class ConformanceStatement {
        +only if the QAIP results support it
    }
    AuditUniverse --> RiskBasedPlan : filtered by risk into
    AssuranceMap --> RiskBasedPlan : informs
    RiskBasedPlan *-- Engagement
    Engagement *-- Planning
    Engagement *-- Fieldwork
    Engagement *-- Reporting
    Engagement *-- FollowUp
    Engagement --> Supervision : controlled by
    QAIP *-- OngoingMonitoring
    QAIP *-- PeriodicSelfAssessment
    QAIP *-- ExternalQualityAssessment
    QAIP --> ConformanceStatement : supports
    ExternalQualityAssessment --> PeerReview : public sector variant
    
```

{% hint style="warning" %}
**Where the MCQ bites**

* **The CAE develops, the board approves.** Management never owns the plan, and the external auditor never approves it.
* **External quality assessment at least every five years**, by a provider independent and free of conflicts.
* **Conformance cannot be claimed from a charter or from certifications** — only from QAIP results.
* **Hot review precedes issuance and can still change the report; cold review looks back.**
* **An uncovered high risk is reported, not hidden.** Any option that lowers a risk score for presentational reasons is wrong.
{% endhint %}

### 10. The pairs that generate distractors

_Duty cluster: Cross-cutting_

When a question offers two options that both sound right, it is usually one of these pairs. The distractor is the other half.

| Pair                                 | The distinction the question turns on                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------ |
| Inherent / residual                  | Before controls / after management's response                                        |
| Control risk / detection risk        | The entity's failure / the audit's failure — only the second is the auditor's to set |
| Sufficiency / appropriateness        | Quantity / quality, and quality splits into relevance and reliability                |
| Test of controls / substantive       | Did the control operate / is the amount correct                                      |
| Statistical / judgemental sampling   | Extrapolation permitted / conclusions confined to items examined                     |
| Finding / conclusion                 | A supported building block / the answer to the audit question                        |
| Cause / condition                    | What the recommendation targets / what the auditor observed                          |
| Qualified / adverse / disclaimer     | Material contained / material pervasive disagreement / evidence unobtainable         |
| Emphasis of matter / qualification   | Opinion unmodified / opinion modified                                                |
| Economy / efficiency / effectiveness | Input cost / output per input / objectives achieved                                  |
| ITGC / application control           | Foundation / the control relying on that foundation                                  |
| RTO / RPO                            | Downtime tolerated / data loss tolerated                                             |
| Hot / cold review                    | Before issuance, can still change it / after issuance, informs the next one          |
| Internal / external audit            | Serves its own governance / reports to outside stakeholders                          |
| Audit / investigation                | Assurance against criteria / OLAF and the EPPO establishing wrongdoing               |
| Shared / indirect management         | Member States implement / entrusted entities implement                               |

{% hint style="success" %}
Companion material: the 100-item MCQ bank and the drill app cover the same eleven clusters. Use this atlas to fix the relationships first — most wrong answers in the bank trace back to one of the arrows above rather than to a missing fact.
{% endhint %}
