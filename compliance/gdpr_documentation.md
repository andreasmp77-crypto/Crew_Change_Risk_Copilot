# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-04
---

# GDPR Documentation — Crew Change Risk Copilot

**Project:** Crew Change Risk Copilot  
**Document type:** First-pass GDPR compliance assessment  
**Status:** Capstone / MVP documentation — not legal advice  
**Scope:** Current MVP and the likely data-protection considerations for a future production deployment

---

## 1. Purpose and scope

This document assesses the **Crew Change Risk Copilot** through a GDPR lens. It follows the principle that GDPR analysis starts with the **data being processed**, rather than with the AI system in isolation.

The current MVP is intentionally designed around **synthetic and public operational data**. Therefore, the preferred MVP position is to avoid processing real personal data wherever possible. However, a production version could process personal data because crew-change operations may involve identifiable seafarers and operational records linked to individuals.

This document therefore distinguishes between:

- **Current MVP:** synthetic/public data; no intentional use of real crew personal data.
- **Future production deployment:** potential processing of identifiable crew and operational data, requiring additional legal and organisational controls.

The analysis is based on the GDPR principles of lawfulness, fairness and transparency; purpose limitation; data minimisation; storage limitation; accuracy; integrity and confidentiality; and accountability.

> **Important:** This is a first-pass compliance assessment for a capstone project. Legal bases, controller/processor roles, retention periods and transfer mechanisms must be validated by qualified legal or data-protection professionals before production deployment.

---

# 2. Data Processing Brief

## 2.1 What personal data could the system process?

The intended production use case could involve the following categories:

- Crew member name and internal identifier.
- Nationality or other travel-relevant identity attributes, where operationally necessary.
- Crew assignment information, including vessel, port, planned joining/leaving dates and travel itinerary.
- Operational information associated with an identifiable individual, such as disruption status or missed connections.
- User account details for authorised Crew Managers and Operations Managers.
- System interaction and audit logs, which may identify users and record actions.

The system should **not require special-category personal data** for its core purpose. Health information, biometric data, religious information or other Article 9 data should be excluded from the AI input unless a separate, documented necessity and lawful condition have been established.

## 2.2 Where does the data come from?

Potential production data sources include:

1. Existing company crew-management or crewing systems.
2. Operational travel and crew-change planning systems.
3. Public operational sources, such as airport or travel disruption information.
4. Authorised system users interacting with the application.

The current MVP should use synthetic records or public data that do not identify real individuals.

## 2.3 What is the data used for?

Personal data, where present, would be processed for separate and defined purposes:

- identifying and reviewing upcoming crew-change cases;
- detecting operational risk indicators;
- prioritising cases for human attention;
- generating an AI-supported risk briefing;
- maintaining auditability and system monitoring;
- administering authorised user access.

## 2.4 Who processes the data?

A future production architecture may involve:

- the ship-management or crewing company as the **controller**;
- the application hosting/workflow provider as a **processor**, where applicable;
- an LLM API provider as a **processor**, subject to contractual and factual role assessment;
- monitoring/observability providers as processors if personal data enters logs;
- the implementation team as an authorised service provider or processor, depending on the contractual arrangement.

Exact roles must be confirmed contractually and operationally. A role should not be assigned solely because a vendor markets itself using a particular privacy label.

## 2.5 Where is data stored and processed?

For the MVP, infrastructure and vendor locations must be documented explicitly.

**Target design principle:** keep personal data processing and storage within the EEA where technically and commercially feasible.

Where a vendor processes or permits remote access to personal data outside the EEA, the transfer must be assessed separately under Chapter V GDPR.

## 2.6 Does the system make decisions affecting people?

The Crew Change Risk Copilot may **flag, prioritise and summarise operational risks associated with crew-change cases**. These outputs could indirectly affect an individual if operational action is taken regarding that person's travel or assignment.

However, the intended design is **decision support with meaningful human review**:

> AI identifies and explains potential exceptions → authorised Crew Manager reviews the evidence → human makes the operational decision.

The system must not autonomously approve, reject, penalise or otherwise make decisions with legal or similarly significant effects on individuals.

---

# 3. Data Flow Map

## 3.1 High-level data flow

```text
[Company Crew / Planning Systems]
              |
              |  Crew-change and operational data
              v
[Data Preparation / Minimisation Layer]
              |
              |  Only necessary fields
              v
[Risk Analysis Workflow / AI Application]
              |
       +------+-------------------+
       |                          |
       v                          v
[LLM / AI Provider]        [Rules / Operational Data]
       |                          |
       +-----------+--------------+
                   |
                   v
          [Risk Score / Briefing]
                   |
                   v
       [Crew Manager / Human Review]
                   |
                   v
          [Human Operational Decision]

Supporting flow:
[Application / AI Inputs and Outputs] --> [Logging & Monitoring]
                                          |
                                          v
                                  [Access-controlled Records]
```

## 3.2 Data minimisation control point

The most important GDPR design control is the **Data Preparation / Minimisation Layer**.

Before data reaches an AI model or third-party processor:

- remove fields that are not necessary;
- use internal pseudonymous identifiers where possible;
- avoid sending full crew profiles when a risk analysis only requires operational attributes;
- prevent Article 9 special-category data from entering prompts;
- define which fields are allowed in AI prompts and logs.

## 3.3 Personal data inventory

| Data category | Source | Purpose | Proposed retention | Cross-border risk |
|---|---|---|---|---|
| Crew name / internal ID | Company crew system | Link operational case to authorised human review | Only as long as required for active case and audit policy | Depends on infrastructure/vendor |
| Crew assignment and schedule | Planning system | Assess crew-change timing and operational risk | Operational lifecycle + documented retention | Depends on infrastructure/vendor |
| Travel / disruption information linked to a person | Planning and travel data | Identify potential disruption and exceptions | Active case period unless justified longer | Depends on source/vendor |
| Authorised user identity | Application authentication | Access control and accountability | Account lifecycle + security retention | Depends on identity provider |
| User actions / audit logs | Application | Security, accountability and investigation | Defined security retention schedule | Depends on logging provider |
| AI inputs and outputs | AI workflow | Generate risk briefing and explain factors | Minimise; short retention by default | High priority for vendor assessment |

**Purpose limitation check:** Data collected for crew administration or operational planning must not automatically be repurposed for unrelated employee profiling, performance management or disciplinary decisions.

---

# 4. Processing Activities Register

The following table is a simplified Record of Processing Activities (RoPA-style register) for the proposed system.

| Processing activity | Purpose | Data subjects / data | Proposed legal basis | Retention | Recipients |
|---|---|---|---|---|---|
| Crew-change risk analysis | Identify operational exceptions requiring review | Crew members; schedule and operational data | Art. 6(1)(f) legitimate interests — **TBD legal review** | Active case + justified audit period | Authorised operations staff; contracted processors |
| AI-supported risk briefing | Summarise relevant risk factors | Minimised operational data, potentially linked to crew ID | Same as above, subject to LIA | Short-lived where feasible | Authorised users; AI processor if used |
| User authentication and access control | Restrict system access | User name, business email, role | Art. 6(1)(f) legitimate interests and/or Art. 6(1)(b), depending on context | Account lifecycle + security retention | Identity/application providers |
| Audit logging | Investigate system use and maintain accountability | User ID, timestamp, action, system event | Art. 6(1)(f) legitimate interests | Defined security retention period | Security/monitoring processors |
| Model and system monitoring | Detect failures, unexpected outputs and performance issues | Preferably pseudonymised or anonymised logs | Art. 6(1)(f) — **TBD legal review** | Minimum period needed for monitoring | Authorised administrators; monitoring provider |

### Important legal-basis note

For this capstone, **legitimate interests is proposed only as a preliminary basis** for operational risk monitoring and security-related processing. Before production deployment, the controller should complete a documented Legitimate Interests Assessment (LIA) and confirm whether another legal basis is more appropriate for specific employment-related processing.

---

# 5. Legitimate Interests Assessment — Preliminary Three-Part Test

## 5.1 Legitimate interest

The proposed interest is to improve crew-change operational resilience, identify disruptions earlier and support authorised staff in managing exceptions.

**Preliminary result:** potentially legitimate, subject to legal review.

## 5.2 Necessity

The processing should be limited to information genuinely required to identify and explain operational risk. The system should not ingest full personnel records if a smaller operational dataset can achieve the same result.

**Preliminary result:** processing may be necessary if data minimisation and pseudonymisation are applied.

## 5.3 Balancing test

Potential impacts include increased visibility of individual travel or assignment circumstances and the risk that an operational risk flag could be misunderstood as a judgement about a person.

Safeguards should include:

- pseudonymisation where possible;
- strict role-based access;
- human review;
- explanation of risk factors;
- prohibition on using outputs for disciplinary or employment decisions without a separate assessment;
- limited retention.

**Preliminary result:** `TBD — legal review before production deployment`.

---

# 6. Roles and Responsibilities Map

| Entity | Proposed role | Processing activity | DPA required / status |
|---|---|---|---|
| Ship-management / crewing company | Controller | Determines purposes and means of crew operational processing | N/A |
| MVP implementation team | Depends on contract | Development and support | Role and agreement TBD |
| LLM API provider | Likely processor for customer-submitted data, subject to factual assessment | AI inference | DPA and vendor assessment required |
| Cloud / hosting provider | Processor | Infrastructure hosting | DPA required |
| Monitoring / observability provider | Processor if logs contain personal data | System monitoring | DPA required |
| Workflow / automation provider | Processor if personal data flows through workflow | Workflow execution | DPA required |

A processor relationship requires an appropriate Article 28 GDPR contractual arrangement. Vendor privacy documentation should also be reviewed to establish sub-processors, processing locations, retention and security measures.

---

# 7. Short DPIA — Highest-Risk Processing

## 7.1 Processing selected for assessment

The highest-risk foreseeable processing activity is:

> **Combining identifiable crew-change records with operational disruption information and using AI to generate a risk flag and explanatory briefing that is presented to operational staff.**

## 7.2 Necessity and proportionality

The business objective is to help Crew Managers identify exceptions earlier in a complex operational environment.

The system should therefore:

- process only data relevant to the crew-change event;
- avoid special-category data;
- use pseudonymous identifiers where feasible;
- provide explanations rather than unexplained scores;
- ensure a human reviews every consequential output.

## 7.3 DPIA screening against commonly used EDPB criteria

| Criterion | Potentially applicable? | Assessment |
|---|---|---|
| Evaluation or scoring | Yes | System flags/prioritises operational cases associated with individuals |
| Automated decision-making with significant effects | No — intended design | Human remains responsible for consequential decisions |
| Systematic monitoring | Limited / possible | Depends on scale and production design |
| Special-category data at scale | No — target design | Such data should be excluded |
| Large-scale processing | Unknown | Depends on future deployment scope |
| Matching / combining datasets | Yes | Operational and planning data may be combined |
| Vulnerable data subjects | No specific evidence | Not assumed in current scope |
| Innovative technology | Yes | AI-supported operational analysis |
| Transfer preventing rights exercise | Possible | Depends on third-country vendors and safeguards |

### Preliminary DPIA conclusion

The proposed production system may trigger multiple risk criteria, particularly **evaluation/scoring, dataset combination and innovative technology**. If deployed with real identifiable crew data at meaningful scale, a full DPIA should be completed before deployment.

For the current MVP using synthetic/public data, a full production DPIA is not necessarily triggered because no real data subjects are intentionally processed. This conclusion must be revisited immediately if real operational records are introduced.

## 7.4 Key risks and mitigations

| Risk | Potential impact | Mitigation |
|---|---|---|
| Excessive personal data sent to AI provider | Unnecessary disclosure | Data minimisation and pseudonymisation before AI processing |
| Incorrect risk flag | Poor operational action affecting an individual | Human review; explanation; ability to challenge/correct underlying data |
| Function creep | Operational data reused for employee profiling | Explicit purpose restrictions and access controls |
| Sensitive data entering prompts | Higher privacy risk | Input validation and field allow-list |
| Uncontrolled AI/log retention | Data retained beyond necessity | Retention policy and deletion controls |
| Unauthorised access | Confidentiality breach | Role-based access, authentication and audit logging |
| Third-country transfer | Reduced control over protection | EEA preference; adequacy/SCC assessment where needed |

## 7.5 Residual risk

After the proposed controls, residual risk remains **moderate** because AI-supported prioritisation can still influence human operational judgement. The human-in-the-loop model, transparency, logging and data minimisation are therefore core safeguards rather than optional features.

---

# 8. Special-Category Data and Article 22 Check

## 8.1 Special-category data — Article 9

The intended system does not require health, biometric, political, religious, ethnic, trade-union or other special-category data.

**Design requirement:** special-category data must be excluded from the MVP and production AI input unless a separate necessity assessment and Article 9 condition are established.

Potential risk: free-text notes or uploaded documents could unintentionally contain health or other sensitive information. A production system should therefore use controlled input fields or pre-processing controls.

## 8.2 Automated decision-making — Article 22

The intended system does not make solely automated decisions with legal or similarly significant effects.

The Copilot:

1. analyses available operational information;
2. flags potential risk indicators;
3. generates a briefing and explanation;
4. presents the result to an authorised human;
5. requires the human to make the operational decision.

The design must ensure that human review is **meaningful**, rather than a rubber-stamping step.

---

# 9. Data Subject Rights Support

The GDPR provides data subjects with rights including information, access, rectification, erasure, restriction, portability, objection and safeguards relating to automated decision-making/profiling.

## 9.1 Proposed operational support

| Right | System support approach |
|---|---|
| Right to be informed | Privacy notice explaining purposes, categories, recipients, retention and AI-supported processing |
| Right of access | Searchable records of source data, relevant outputs and processing information |
| Right to rectification | Correct inaccurate source data and regenerate/reassess AI output where appropriate |
| Right to erasure | Delete data where no overriding retention obligation applies; propagate deletion to relevant processors |
| Restriction of processing | Mark record as restricted and prevent further AI processing where legally required |
| Data portability | Export applicable user-provided data in a structured format where the right applies |
| Right to object | Workflow to assess objections, particularly where legitimate interests is the basis |
| Automated decision-making safeguards | Human review, explanation of relevant factors and no solely automated consequential decision |

## 9.2 Main rights friction

The most challenging areas are likely to be:

- locating personal data across source systems, AI workflows and logs;
- deleting data that has been copied into monitoring records;
- distinguishing original source data from AI-generated inferences;
- explaining how a risk flag was generated;
- responding to objections to processing based on legitimate interests.

The current MVP should therefore maintain a **data inventory and traceable case identifier** so records can be located without storing unnecessary copies.

Requests should be handled without undue delay and, in principle, within one month.

---

# 10. Third-Party and Cross-Border Transfers

## 10.1 Vendor assessment principle

Before real personal data is sent to any third party, the controller should document:

- vendor name and role;
- processing purpose;
- categories of data;
- processing and storage locations;
- sub-processors;
- retention/deletion terms;
- Article 28 contractual arrangements;
- international transfer mechanism, where applicable.

## 10.2 Preferred architecture

**Preferred:** EEA-based processing and storage for personal data.

This reduces transfer complexity but does not remove the need for GDPR-compliant controller/processor arrangements.

## 10.3 If personal data leaves the EEA

Where a transfer occurs outside the EEA, the organisation must assess the applicable Chapter V transfer mechanism.

Possible mechanisms include:

1. **European Commission adequacy decision**, where applicable.
2. **Standard Contractual Clauses (SCCs)** with appropriate contractual and supplementary safeguards where applicable.
3. Another GDPR-recognised transfer mechanism, following legal review.

The transfer assessment should not assume that a vendor's headquarters location alone determines where personal data is processed.

## 10.4 Project-specific position

For the current capstone MVP:

> **Do not send real crew personal data to third-party AI, monitoring or workflow providers unless their processing location, contractual role and transfer safeguards have been documented and approved.**

Synthetic and properly anonymised data should be used for demonstrations.

---

# 11. Data Protection by Design — MVP Checklist

| Design principle | Current target state | Status |
|---|---|---|
| Data minimisation | Synthetic/minimised operational data only | Target |
| Purpose limitation | Crew-change risk support only | Target |
| Access controls | Authorised operational users only | Target |
| Retention enforcement | Retention schedule to be implemented | Unknown / future control |
| Subject rights workflow | Process documented; technical workflow not yet production-tested | Partial |
| Incident response | Requires production procedure | Unknown / future control |
| AI input control | Allow-list and exclusion of unnecessary/sensitive fields | Target |
| Human oversight | Human decision required | Core design principle |
| Logging and monitoring | Inputs/outputs monitored proportionately | Core design principle |

---

# 12. Law Stacking Check

## AI Act cross-check

The current project has been assessed separately as an AI-supported operational decision-support system that is not intended to autonomously make consequential decisions. The GDPR and AI Act address different risks and should be assessed together rather than treated as substitutes.

## ePrivacy check

The current MVP scope does not intentionally include marketing cookies, tracking pixels or interception of private electronic communications.

**Status:** Not a primary issue for the current MVP, but must be reassessed if a web application introduces non-essential cookies or tracking technologies.

## Data Act check

The current use case does not primarily depend on connected-product or IoT data.

**Status:** Not applicable to the current MVP based on the defined scope.

---

# 13. Accountability Gap Assessment

Could the project currently demonstrate compliance to a regulator using only its existing documentation?

**Answer: Partially, but not yet for production deployment.**

The capstone documentation provides an initial basis, but a production deployment would require additional evidence.

| Document / control | Current capstone status |
|---|---|
| Data flow map | Included in this document |
| Data inventory | Included in this document |
| Processing activities register | Included in this document |
| Lawful basis assessment | Preliminary; legal review required |
| Legitimate Interests Assessment | Preliminary only |
| DPIA | Short screening included; full DPIA may be required |
| Privacy notice | Not yet drafted |
| Retention schedule | High-level only |
| Processor agreements / DPAs | Vendor-specific review required |
| International transfer assessment | Vendor-specific review required |
| Data subject rights procedure | High-level process included |
| Incident response procedure | Not yet documented for production |
| Technical access controls | MVP/production implementation dependent |

---

# 14. Official EU Sources

This assessment uses official EU sources as the regulatory basis:

1. **EUR-Lex — Regulation (EU) 2016/679 (General Data Protection Regulation)**
   https://eur-lex.europa.eu/eli/reg/2016/679/oj

2. **European Commission — Data protection explained**
   https://commission.europa.eu/law/law-topic/data-protection/data-protection-explained_en

3. **European Commission — Information for individuals and data subject rights**
   https://commission.europa.eu/law/law-topic/data-protection/information-individuals_en

4. **European Commission — Dealing with requests from individuals**
   https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/dealing-requests-individuals_en

5. **European Commission — Rules on international data transfers**
   https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/rules-international-data-transfers_en

6. **European Commission — Standard Contractual Clauses**
   https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en

7. **European Data Protection Board — Endorsed guidelines, including DPIA guidance**
   https://www.edpb.europa.eu/our-work-tools/general-guidance/guidelines-recommendations-best-practices_en
