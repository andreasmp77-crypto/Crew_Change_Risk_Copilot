# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-04
---


# MVP Documentation — Crew Change Risk Copilot

## 1. MVP Overview

The **Crew Change Risk Copilot** is intended to support maritime crewing teams by identifying upcoming crew-change cases that may require earlier attention and by explaining the operational factors contributing to the identified risk.

The Round 1 Proof of Concept (PoC) was implemented in **n8n** and demonstrated the core concept using a single crew-change case.

During Round 2, an attempt was made to extend the n8n workflow to process a batch of approximately 5–10 new crew-change cases and produce a management-level summary.

The batch-processing extension exposed significant workflow and data-structure limitations within the available development time.

As a result, the n8n implementation remains the validated **PoC**, while the recommended MVP / production implementation would use a more suitable coded architecture, likely **Python + LangGraph**.

---

## 2. What the PoC Demonstrates

The Round 1 n8n workflow demonstrates the following end-to-end concept:

```text
Crew Change Record
        ↓
Airport Information
        ↓
Live Weather Data
        ↓
Data Preparation
        ↓
Deterministic Risk Assessment
        ↓
Risk Score + Risk Drivers
        ↓
AI Interpretation
        ↓
Operational Risk Briefing
        ↓
Human Review
````

The workflow combines operational data with external context and applies deterministic risk rules before using an LLM to interpret the results.

The PoC demonstrated that the system can:

* retrieve a crew-change record;
* retrieve relevant airport information;
* obtain live weather information;
* calculate an operational risk score;
* classify the case as Low / Medium / High risk;
* identify contributing risk factors;
* generate an AI-assisted operational briefing;
* store the result for human review.

The PoC therefore validates the core business and technical concept.

---

## 3. Round 2 MVP Development

The intended Round 2 MVP direction was to move from a single-case workflow toward a more realistic **management-by-exception** process.

The intended process was:

```text
Generate New Crew-Change Cases
        ↓
Batch Risk Analysis
        ↓
Risk Prioritisation
        ↓
Database Update
        ↓
Management Summary
        ↓
Human Review
        ↓
Morning Crewing Briefing
```

The goal was to demonstrate how a Crew Manager could review several newly created or upcoming crew-change cases and focus attention on those with the highest operational risk.

---

## 4. Technical Findings

The batch-processing implementation was explored using n8n.

The main technical challenge was the **structure and schema of the data moving between workflow nodes**.

When processing multiple records, the workflow required increasingly frequent data transformation, cleaning and parsing between nodes.

As a result, Python Code nodes had to be introduced at several points to reshape and prepare data before it could be consumed by subsequent nodes.

This increased workflow complexity and created additional points of failure.

The batch workflow experienced repeated execution problems during development.

The main issues identified were:

* inconsistent data structures between nodes;
* schema changes and data-shape mismatches;
* repeated data cleaning and parsing;
* increasing complexity as multiple records were processed;
* difficulty maintaining a consistent schema throughout the workflow;
* repeated execution failures requiring manual troubleshooting; and
* limited time available to stabilise the extended workflow.

The conclusion was that continuing to increase the complexity of the n8n workflow was not the most effective way to deliver a reliable MVP within the project timeframe.

---

## 5. MVP Scope Decision

The project timeframe for this development stage was approximately **2–3 days**.

Within this timeframe, building and reliably testing a more advanced multi-case application in n8n was not considered realistic.

The MVP scope was therefore narrowed.

The project will retain the working n8n workflow as the **validated Proof of Concept** and use its findings to define the architecture for the next implementation stage.

This is a deliberate scope decision rather than a change to the business use case.

The **Crew Change Risk Copilot** remains the selected use case.

---

## 6. Proposed MVP / Production Architecture

The next implementation should evaluate a coded architecture, most likely:

**Python + LangGraph**

Python would provide stronger control over:

* data structures and schemas;
* data validation;
* data transformation;
* batch processing;
* deterministic risk calculations;
* error handling;
* testing; and
* integration with external systems.

LangGraph could be used to orchestrate the AI-related stages of the workflow while maintaining state and supporting human-in-the-loop processes.

A future application layer could then provide a dedicated interface for Crew Managers.

Conceptually:

```text
Operational Data
      ↓
Data Validation
      ↓
Risk Assessment
      ↓
Risk Prioritisation
      ↓
AI Interpretation
      ↓
Management Summary
      ↓
Human Review
      ↓
Operational Action
```

The final production architecture would be confirmed during a technical discovery and pilot phase.

---

## 7. AI Capability

The core AI capability demonstrated by the PoC is **AI-assisted operational risk interpretation**.

The system does not rely on the LLM to independently calculate the operational risk score.

Instead:

### Deterministic layer

Defined business rules identify measurable operational risk factors and calculate a risk score.

### AI layer

The LLM interprets the structured risk information and generates a concise operational briefing for the human user.

### Human layer

The Crew Manager reviews the information and decides whether operational action is required.

This hybrid approach is intended to improve transparency and reduce the risk of treating an LLM-generated recommendation as an unexplained decision.

---

## 8. Human-in-the-Loop Principle

The system is designed as a **decision-support tool**.

The AI should support the Crew Manager by:

* identifying potentially important cases;
* explaining the main risk drivers;
* summarising relevant information; and
* suggesting possible actions for consideration.

The system should not autonomously:

* approve or reject a crew change;
* purchase or cancel travel;
* change travel arrangements;
* make employment decisions;
* determine legal immigration status; or
* make final operational decisions.

The final operational decision remains with the human user.

---

## 9. MVP Success Criteria

The future coded MVP should demonstrate at least the following:

### 1. Batch Analysis

The system can process multiple upcoming crew-change cases in a consistent and reliable manner.

### 2. Risk Prioritisation

The system can identify and prioritise cases requiring attention based on defined operational risk factors.

### 3. Explainability

The system provides the main contributing risk factors for each prioritised case.

### 4. Management Summary

The system can generate a concise summary showing:

* number of cases analysed;
* number of Low / Medium / High risk cases;
* highest-priority cases;
* main risk drivers; and
* suggested areas for human attention.

### 5. Human Review

The workflow clearly presents AI-generated information as decision support and keeps the final operational decision with the Crew Manager.

---

## 10. Error Handling Requirements

The current n8n batch-processing experience identified error handling and data consistency as important requirements for the next implementation.

The future MVP should therefore include:

* input validation;
* schema validation;
* clear handling of missing or invalid data;
* controlled API failures;
* logging of processing errors;
* retry handling where appropriate;
* clear error messages; and
* preservation of the original input data for investigation.

System outputs and processing events should also be logged and monitored so that unexpected behaviour can be investigated.

---

## 11. Data Considerations

The capstone project uses **public or synthetic data only**.

The future production system would require a clear data model defining:

* crew-change records;
* operational risk indicators;
* airport information;
* external operational data;
* risk scores;
* risk drivers;
* AI-generated outputs; and
* audit / monitoring information.

A consistent schema should be established before expanding the number of processing stages.

This is one of the main technical lessons from the Round 2 n8n extension attempt.

---

## 12. Current Status

### Validated

* Crew Change Risk Copilot use case;
* single-case operational risk workflow;
* deterministic risk calculation;
* external operational context integration;
* AI-assisted interpretation;
* structured operational briefing;
* human-in-the-loop approach.

### Not yet production-ready

* reliable batch processing;
* scalable multi-case workflow;
* production application interface;
* comprehensive automated testing;
* production-grade monitoring and logging;
* full security controls; and
* deployment architecture.

---

## 13. Development Path

The proposed development path is:

```text
Round 1
Validated n8n PoC
        ↓
Round 2
Architecture and MVP definition
        ↓
Next Stage
Python + LangGraph MVP
        ↓
Pilot
Realistic operational validation
        ↓
Production
Scalable application and integrations
```

The n8n workflow remains an important part of the project because it validated the concept and helped identify the technical requirements for a more robust implementation.

---

## 14. Conclusion

The Round 1 n8n PoC successfully demonstrated the core concept of the **Crew Change Risk Copilot**.

The Round 2 attempt to extend the workflow to batch processing provided an additional technical learning: multi-case processing with several transformations and dependencies requires stronger control of schemas, state, validation and error handling than the current low-code workflow could reliably provide within the available project timeframe.

The project therefore does not continue expanding the n8n workflow indefinitely.

Instead, the PoC findings are used to define the requirements for a more robust MVP implementation, likely using **Python and LangGraph**.

The target remains:

> **New crew-change cases → Risk analysis → Prioritisation → AI briefing → Human review**

The long-term objective is to provide Crew Managers with earlier, clearer visibility of potentially problematic crew changes while keeping operational decisions under human control.