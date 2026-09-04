# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-04
---

# MVP Documentation — Crew Change Risk Copilot

## 1. MVP Overview

The Crew Change Risk Copilot is a human-in-the-loop decision-support MVP for maritime crewing teams.

It helps users identify upcoming crew-change cases that may require attention, understand the main operational risk drivers, and review an AI-generated operational briefing.

The MVP is implemented in n8n and uses Airtable as the operational data store, external operational context, deterministic risk rules, OpenAI for AI interpretation, Notion for human-readable reporting, and LangSmith for monitoring.

The MVP is a functional capstone demonstrator. It is not a production-ready operational system.

---

## 2. Demo Prerequisite — Generate 5 New Cases

**The Demo Cases Generator workflow must be run first.**

Workflow:

`Demo Cases Generator for Crew Travel Copilot`

Purpose:

- create 5 new synthetic crew-change cases;
- assign new Crew Change IDs;
- use the existing Airtable airport and port reference data;
- create varied travel and operational conditions;
- set the new records to `processing_status = New`.

This provides fresh cases for the main MVP workflow to analyse.

### Demo sequence

```text
1. Run "Demo Cases Generator for Crew Travel Copilot"
                    ↓
2. 5 new Crew Change Plans created in Airtable
                    ↓
3. Run "Crew Change Copilot - MVP"
                    ↓
4. Risk analysis + external context + AI briefing
                    ↓
5. Airtable updated
                    ↓
6. Notion report created
                    ↓
7. LangSmith monitoring record created
````

The generator is intended for the capstone demonstration environment and uses synthetic/demo data.

---

## 3. MVP Workflow

The main workflow is:

`Crew Change Copilot - MVP`

The workflow starts by retrieving Crew Change Plans where:

```text
processing_status = New
```

The records are then normalised before risk assessment.

### End-to-end flow

```text
New Crew Change Plans
        ↓
Normalize Crew Change Data
        ↓
Deterministic Operational Risk Assessment
        ↓
Airport & Port Context
        ↓
Live Weather Data
        ↓
Merge Operational Context
        ↓
Prepare AI Input
        ↓
LLM Interpretation
        ↓
Structured Risk Briefing
        ↓
Airtable Update
        ↓
Notion Report
        ↓
LangSmith Monitoring
```

---

## 4. Data Sources

The MVP uses:

### Airtable

Airtable provides the main operational data for the demonstration.

The Crew Change Plans table contains information including:

* Crew Change ID
* vessel
* seafarer/rank
* movement type
* origin / connection / destination airports
* joining port
* connection time
* reporting deadline
* vessel ETA
* port transfer time
* visa status
* ticket status
* document verification
* vessel ETA confidence
* processing status

Airport and port reference information is stored in separate Airtable tables.

### External weather data

The workflow retrieves current weather information for:

* the origin airport;
* the joining port.

The weather data is used as additional operational context.

### Public operational context

The workflow also uses available public airport delay context stored with the crew-change data.

---

## 5. Deterministic Risk Assessment

The initial operational risk score is calculated using explicit business rules.

The workflow evaluates factors including:

* flight connection time;
* destination airport delay risk;
* airport-to-port transfer time;
* vessel ETA confidence;
* visa status;
* document verification;
* port agent confirmation;
* ticket status.

Each factor can add points to the risk score.

The workflow then assigns a risk level:

| Risk score | Risk level |
| ---------- | ---------- |
| 0–14       | Low        |
| 15–29      | Medium     |
| 30–49      | High       |
| 50+        | Critical   |

The deterministic layer produces:

* risk score;
* risk level;
* risk signals;
* recommended attention level.

The score is calculated before the LLM is called.

---

## 6. AI Interpretation

The LLM does not calculate the operational risk score.

Instead, it interprets the structured operational information already produced by the deterministic layer.

The AI is instructed to:

* use only the supplied information;
* not recalculate or modify the risk score;
* not invent missing information;
* explain the main risk drivers;
* provide practical recommendations;
* clearly distinguish assessment from recommendation;
* recommend human review for high-risk situations.

The AI output is structured as:

```text
Executive Assessment
Key Risk Drivers
Recommended Actions
AI Recommendation
Recommendation Rationale
Assessment Limitation
```

The current workflow uses OpenAI `gpt-4o-mini`.

---

## 7. Human-in-the-Loop

The MVP is a decision-support system.

The AI does not autonomously:

* approve or reject a crew change;
* purchase or cancel travel;
* change travel arrangements;
* make employment decisions;
* determine legal immigration status;
* make final operational decisions.

The Crew Manager remains responsible for reviewing the information and deciding what action is required.

---

## 8. Airtable Output

After the risk assessment, the workflow updates the Crew Change Plan record with fields including:

* live operational risk score;
* live operational risk level;
* live risk reasons;
* live weather summary;
* risk assessment timestamp;
* processing status.

This creates a structured record of the assessment that can be reviewed later.

---

## 9. Notion Reporting

The workflow creates a human-readable Crew Change Report in Notion.

The report contains the AI operational risk assessment for the processed case.

This creates a simple reporting layer for operational review and demonstration.

The project currently maintains a Notion Crew Change Reports area containing generated Crew Change Risk Briefings and Crew Change Reports.

---

## 10. LangSmith Monitoring

The MVP sends monitoring information to LangSmith.

The purpose is to demonstrate observability of the AI component, including information about:

* workflow execution;
* model used;
* AI assessment output;
* execution timing;
* workflow/source metadata.

LangSmith is used here as a monitoring demonstration rather than as a complete production observability architecture.

---

## 11. Demo Procedure

For a clean demonstration, use the following order.

### Step 1 — Generate demo cases

Open:

`Demo Cases Generator for Crew Travel Copilot`

Run the workflow.

Expected result:

**5 new synthetic Crew Change Plans** are created in Airtable with:

```text
processing_status = New
```

### Step 2 — Run the MVP

Open:

`Crew Change Copilot - MVP`

Execute the workflow.

The workflow retrieves the new records and processes them.

### Step 3 — Review Airtable

Confirm that the Crew Change Plans have been enriched with:

* operational risk score;
* risk level;
* risk reasons;
* weather information;
* assessment timestamp;
* processing status.

### Step 4 — Review Notion

Open the Crew Change Reports area and review the generated report.

### Step 5 — Review LangSmith

Open the LangSmith monitoring view and confirm that the AI execution information has been recorded.

---

## 12. Error Handling and Validation

The MVP includes basic validation and controlled processing logic.

The Demo Cases Generator validates that:

* existing Crew Change Plans are available;
* airport reference data is available;
* port reference data is available;
* Crew Change IDs can be determined;
* valid airport and port references are available;
* five cases are generated.

The main MVP normalises input data before downstream processing.

The next production version should strengthen:

* schema validation;
* retry handling;
* API failure handling;
* structured logging;
* monitoring and alerting;
* test coverage;
* failure recovery.

System inputs, outputs and processing events should be logged and monitored so unexpected behaviour can be investigated.

---

## 13. MVP Scope

The MVP demonstrates one core capability:

> **Analyse upcoming crew-change cases, prioritise operational risk, explain the main risk drivers, and provide an AI-assisted operational briefing for human review.**

The MVP deliberately does not attempt to automate the entire crew-change process.

Out of scope for this MVP:

* autonomous travel booking;
* autonomous travel changes;
* immigration decisions;
* employment decisions;
* medical decisions;
* guaranteed travel-success prediction;
* production integration with live crew-management systems.

---

## 14. Current Limitations

The MVP is a capstone demonstrator and has several limitations.

### Synthetic/demo data

The demonstration uses public and synthetic data rather than live client data.

### Rule-based risk model

The current risk score is based on explicitly defined deterministic rules. It is not a trained predictive model.

### External data dependency

Weather and other external information may be unavailable, delayed, or incomplete.

### Limited production controls

The current workflow does not represent a full production-grade architecture with comprehensive security, scalability, monitoring, testing and disaster recovery.

### n8n workflow complexity

The workflow contains several data transformation and merge stages. This is acceptable for the MVP demonstration, but a production implementation would require further architectural evaluation.

---

## 15. MVP Success Criteria

The MVP is considered successful when it can:

1. Generate 5 new synthetic crew-change cases for demonstration.
2. Process the new cases through the Crew Change Copilot workflow.
3. Calculate a deterministic operational risk score.
4. Assign a Low / Medium / High / Critical risk level.
5. Identify the main risk signals.
6. Enrich cases with operational context and weather information.
7. Generate a structured AI operational briefing.
8. Update the Airtable record.
9. Create a human-readable Notion report.
10. Record AI monitoring information in LangSmith.
11. Keep the final operational decision with the human user.

---

## 16. Repository Files

Relevant MVP files:

```text
mvp/
├── Demo Cases Generator for Crew Travel Copilot.json
├── Crew Change Copilot - MVP.json
├── mvp_documentation.md
├── Crew Change Copilot - MVP Screenshot ...
├── Demo Cases Generator for Crew Travel Copilot Screenshot ...
├── MVP LangSmith Screenshot ...
└── Notion Crew Change Reports Screenshot ...
```

---

## 17. MVP Status

### Working

* Demo case generation
* 5-case synthetic data generation
* Crew-change retrieval
* Data normalisation
* Deterministic risk scoring
* Risk classification
* Airport and port enrichment
* Live weather enrichment
* AI risk interpretation
* Structured AI output
* Airtable updates
* Notion reporting
* LangSmith monitoring

### Not production-ready

* Production security
* Full automated testing
* High-volume scalability
* Enterprise integration
* Advanced observability
* Automated recovery
* Production deployment architecture

---

## 18. Conclusion

The Crew Change Risk Copilot MVP demonstrates an end-to-end AI-assisted operational risk workflow for crew-change management.

The demonstration begins by running the **Demo Cases Generator for Crew Travel Copilot**, which creates five new synthetic cases.

The main MVP then analyses those cases using deterministic operational risk rules, enriches them with external context and live weather data, and uses an LLM to produce a concise operational briefing.

The resulting information is written back to Airtable, reported in Notion and monitored through LangSmith.

The solution remains a human-in-the-loop decision-support tool. It is intended to help crewing teams identify cases requiring attention earlier and understand why those cases were flagged, rather than replace professional operational judgement.