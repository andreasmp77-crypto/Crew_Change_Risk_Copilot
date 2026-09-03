# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-04
---

# EU AI Act Compliance Documentation

## Project: Crew Change Risk Copilot

**Document purpose:** Initial EU AI Act classification and compliance assessment for the proposed Crew Change Risk Copilot MVP.

**Important note:** This is a project-level compliance assessment based on the intended purpose and scope of the MVP. A production deployment should be reviewed against the final system design, deployment context and applicable EU AI Act guidance.

---

# 1. Risk Classification and Step-by-Step Reasoning

## 1.1 System description

The **Crew Change Risk Copilot** is an AI-supported decision-support system designed for crew and operations managers.

Its purpose is to:

- analyse available crew-change and operational data;
- identify cases with potential risk indicators or exceptions;
- explain the factors contributing to a flag;
- provide a concise operational risk briefing;
- help users prioritise attention and investigation.

The system **does not autonomously make operational decisions**. A human user reviews the information and remains responsible for deciding whether and how to act.

This human-in-the-loop design is consistent with the core user stories developed for the project, particularly transparency, explainability, operational decision support and human control.

## 1.2 Classification reasoning

### Step 1 — Does the system qualify as an AI system?

**Yes.**

The solution uses AI capabilities to analyse operational information and generate risk-related insights, explanations and briefings. It therefore falls within the scope of an AI-system assessment under the EU AI Act.

### Step 2 — Is the intended use prohibited?

**No.**

The system is not designed for prohibited practices such as manipulation, social scoring, prohibited biometric categorisation or other practices listed in Article 5 of the EU AI Act.

### Step 3 — Is it a High-Risk AI System?

**No, based on the current MVP scope and intended purpose.**

The system is not intended to:

- make decisions on employment, recruitment or worker management;
- determine access to essential public or private services;
- perform law-enforcement, migration, asylum or border-control functions;
- support judicial decision-making;
- act as a safety component of a regulated product;
- perform another use listed as high risk under Annex III.

The system supports operational prioritisation of crew-change cases. It does **not** autonomously decide whether a person may work, travel, be employed, be promoted or be dismissed.

### Step 4 — Does a transparency obligation apply?

**Potentially yes.**

The system is intended to interact directly with human users through a Copilot-style interface and presents AI-generated analysis and summaries. Under Article 50, systems intended to interact directly with natural persons must be designed so that users are informed that they are interacting with an AI system, unless this is obvious from the circumstances and context.

For this project, applying an explicit transparency measure is the prudent approach.

### Final classification

> **Current classification: Non-high-risk AI system with applicable transparency considerations (“limited/transparency risk” in the common AI Act risk model).**

The Crew Change Risk Copilot is therefore **not classified as High Risk** under its current intended purpose. Its primary EU AI Act compliance focus is transparency and good governance.

**Classification caveat:** The classification must be reassessed if the intended purpose changes. For example, the assessment could change if future versions make or materially influence employment decisions about individual seafarers, or are deployed as a safety component within a regulated product.

---

# 2. Mandatory Requirements Summary

## 2.1 Requirements applicable to the current MVP

Because the current system is not High Risk, the full High-Risk conformity requirements do not apply.

The main applicable transparency measure is:

| Requirement | Application to Crew Change Risk Copilot | Proposed implementation |
|---|---|---|
| Inform users about AI interaction | Users should understand when they are interacting with an AI-supported system | Clear label such as **“AI-assisted Crew Change Risk Copilot”** and an AI disclosure in the interface |
| Transparency about AI-generated outputs | Users should understand that risk summaries and explanations are AI-generated assistance | Label AI-generated briefings and insights where appropriate |
| Clear system limitations | Users should not assume that AI output is a final operational decision | UI statement: **“AI-generated decision support — human review required”** |
| Human control | Operational decisions remain with qualified users | No autonomous action; user reviews risk flags and decides follow-up |
| Internal traceability and monitoring | Not a general Article 12 obligation for this non-high-risk system, but good governance practice | Log system inputs, outputs, model/version information and user feedback where appropriate |

## 2.2 Good-practice controls included beyond the minimum

Although the strict High-Risk requirements do not apply to the current MVP, the project will adopt proportionate governance controls:

- logging and monitoring of system outputs and relevant records;
- clear visibility of why a case was flagged;
- human review before operational action;
- clear and intuitive UI/UX to reduce misunderstanding;
- monitoring of unexpected or incorrect outputs;
- version control for prompts, models and workflow logic;
- periodic review of system performance and classification.

These controls support transparency, traceability and responsible deployment without incorrectly claiming that the system is a High-Risk AI system.

---

# 3. Conformity Assessment Summary

## 3.1 Assessment conclusion

Based on the current intended purpose, the Crew Change Risk Copilot is **not a High-Risk AI system** under Article 6 and Annex III of the EU AI Act.

Therefore, the formal conformity assessment procedures applicable specifically to High-Risk AI systems under Article 43 and Annexes VI/VII are **not required for the current MVP classification**.

However, this conclusion does not mean that no compliance work is required. Before production deployment, the provider/deployer should document the intended purpose, confirm the classification, implement applicable transparency measures and reassess the system whenever its scope or use changes.

## 3.2 Compliance approach for the MVP

The proposed proportionate compliance process is:

1. **Document the intended purpose**
   - Define exactly what the system does and does not do.
   - Confirm that it provides operational decision support only.

2. **Confirm risk classification**
   - Check prohibited practices under Article 5.
   - Check High-Risk categories under Article 6 and Annex III.
   - Record the rationale for the non-high-risk conclusion.

3. **Implement transparency controls**
   - Inform users that they are using an AI-supported system.
   - Clearly identify AI-generated insights where appropriate.
   - Explain that human users remain responsible for decisions.

4. **Implement governance controls**
   - Maintain logs of relevant system activity.
   - Monitor outputs and errors.
   - Maintain version information for the AI workflow.
   - Capture user feedback and investigate significant unexpected results.

5. **Reassess before production deployment**
   - Recheck the classification against the final functionality.
   - Review any changes in the AI Act, Commission guidance or harmonised standards.
   - Confirm alignment with GDPR and other applicable legislation.

## 3.3 What would trigger a stronger conformity assessment?

A new assessment would be required if the system evolves into a use case covered by High-Risk categories. Examples could include:

- using AI output to make employment or worker-management decisions about individual seafarers;
- automatically approving or rejecting employment-related opportunities;
- materially determining access to essential services;
- integration into a regulated safety-critical product.

If the system became High Risk, the provider would need to meet the applicable requirements for risk management, data governance, technical documentation, record-keeping, transparency to deployers, human oversight, accuracy, robustness and cybersecurity, as well as complete the relevant conformity assessment procedure.

## 3.4 Production readiness statement

**Current MVP status:** Suitable for demonstration as an AI-assisted decision-support concept, subject to transparent user communication and human oversight.

**Production status:** Not yet compliance-certified. A formal pre-deployment assessment would be required using the final system architecture, intended purpose, data flows and deployment environment.

---

# 4. Technical Documentation Outline

The following skeleton is based on the structure expected for technical documentation of High-Risk systems under Article 11 and Annex IV. For this non-high-risk MVP, it is used as a **proportionate best-practice documentation structure**.

## Table of Contents

### 1. General System Information
1.1 System name and version  
1.2 Provider / organisation  
1.3 Date and document owner  
1.4 System description  
1.5 Intended purpose  
1.6 Intended users  
1.7 Deployment environment  
1.8 Out-of-scope uses  

### 2. EU AI Act Classification
2.1 AI system assessment  
2.2 Prohibited-practice assessment  
2.3 High-Risk assessment  
2.4 Annex III assessment  
2.5 Transparency obligation assessment  
2.6 Final classification and rationale  
2.7 Reassessment triggers  

### 3. System Architecture
3.1 End-to-end workflow  
3.2 Input sources  
3.3 Data processing steps  
3.4 AI model/provider  
3.5 Prompting and workflow logic  
3.6 Output generation  
3.7 User interface  
3.8 External systems and APIs  

### 4. Data and Input Management
4.1 Data categories  
4.2 Data sources  
4.3 Data quality controls  
4.4 Data limitations  
4.5 Data retention approach  
4.6 Personal data considerations  
4.7 Synthetic/public data used in the MVP  

### 5. AI Functionality
5.1 Core AI capability  
5.2 Risk identification logic  
5.3 Explanation generation  
5.4 Operational risk briefing generation  
5.5 Known limitations and failure modes  

### 6. Human Oversight and User Controls
6.1 Human-in-the-loop design  
6.2 User responsibilities  
6.3 Escalation process  
6.4 Override and correction mechanisms  
6.5 Prevention of automation bias  

### 7. Transparency and User Information
7.1 AI interaction disclosure  
7.2 AI-generated output labelling  
7.3 Explanation of system purpose  
7.4 Limitations statement  
7.5 User guidance  

### 8. Monitoring and Logging
8.1 Events logged  
8.2 Input/output monitoring  
8.3 Model and prompt version tracking  
8.4 Error and incident monitoring  
8.5 User feedback  
8.6 Periodic performance review  

### 9. Risk Management
9.1 Risk identification  
9.2 Likelihood and impact assessment  
9.3 Mitigation measures  
9.4 Residual risks  
9.5 Incident response process  

### 10. Testing and Evaluation
10.1 Test methodology  
10.2 Test cases  
10.3 Expected results  
10.4 Accuracy and quality checks  
10.5 Human evaluation  
10.6 Known performance limitations  

### 11. Change Management
11.1 Model changes  
11.2 Prompt/workflow changes  
11.3 Data-source changes  
11.4 Classification reassessment process  
11.5 Documentation update process  

### 12. Compliance Evidence
12.1 EU AI Act classification record  
12.2 Transparency implementation evidence  
12.3 Risk assessment  
12.4 Test results  
12.5 Monitoring evidence  
12.6 GDPR documentation reference  
12.7 Production deployment checklist  

---

# 5. Official EU Sources Used

This assessment was prepared using official EU sources only:

1. **Regulation (EU) 2024/1689 — Artificial Intelligence Act (EUR-Lex)**
   - Article 5: Prohibited AI practices
   - Article 6 and Annex III: Classification of High-Risk AI systems
   - Article 11 and Annex IV: Technical documentation
   - Article 43 and Annexes VI/VII: Conformity assessment for High-Risk AI systems
   - Article 50: Transparency obligations

2. **European Commission — AI Act regulatory framework**
   - EU AI Act risk-based approach
   - Overview of High-Risk and transparency obligations

3. **European Commission — Guidelines on transparency obligations under Article 50**
   - Practical guidance on transparency obligations for providers and deployers

---

## Overall Compliance Position

> **The Crew Change Risk Copilot is currently assessed as a non-high-risk AI-supported decision-support system with transparency obligations/considerations. The system does not autonomously make operational or employment decisions. Human users remain responsible for reviewing AI-generated insights and taking any resulting action. The classification must be reassessed if the intended purpose or deployment context materially changes.**
