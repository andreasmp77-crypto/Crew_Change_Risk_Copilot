# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-04
---

# Use Case Definition — Crew Change Risk Copilot

## 1. Business Problem Statement

Crew-change planning in maritime ship management involves multiple operational factors that may affect whether a planned crew change can be completed as expected.

These factors can include:

- documentation and visa status;
- ticket status;
- flight connection times;
- arrival buffers;
- airport disruption;
- weather conditions; and
- vessel schedule information.

The operational challenge is not only the amount of information involved, but also the need for the Crew Manager or crewing officer to identify which cases require attention first and understand why they may be risky.

The **Crew Change Risk Copilot** is designed to support this process by bringing relevant operational signals together, identifying potentially risky cases, and providing a concise explanation for human review.

The central project hypothesis is:

> **Earlier and clearer identification of combined warning signs may help a crewing officer intervene sooner.**

The system is intended as a **decision-support tool**. It does not replace the professional judgement of the Crew Manager and does not autonomously make crew-management decisions.

---

## 2. Company Profile

**Industry:** Maritime ship management / crew management

**Company size:** Medium-sized company

**Current state:** Crew-change information and relevant operational context may come from multiple sources. Crewing staff need to review upcoming cases and determine which cases require earlier attention.

The current Proof of Concept demonstrates how operational crew-change data can be combined with airport information and live weather data to support a structured operational risk assessment.

---

## 3. Proposed AI Solution and System Type

The proposed solution is the **Crew Change Risk Copilot**, a human-in-the-loop operational decision-support system.

At Proof of Concept level, the workflow combines:

**Operational data + external context → deterministic risk assessment → AI interpretation → structured risk briefing → human review**

The solution uses a **hybrid approach**:

- **Deterministic business rules** calculate the operational risk score and identify specific risk drivers.
- An **LLM** interprets the structured information, produces a concise operational briefing, and suggests actions for consideration.
- The **human user remains responsible** for the final operational decision.

The Round 1 n8n workflow demonstrated this approach.

For a future production-oriented implementation, a coded architecture such as **Python with LangGraph** could provide a more suitable foundation for orchestration, testing, maintainability, monitoring, and further development.

---

## 4. Key Stakeholders and Interests

| Stakeholder | Main Interest |
|---|---|
| **Crew Manager** | Quickly identify priority crew-change cases and understand why they require attention. |
| **Crewing Officers / Crewing Team** | Reduce manual review effort and improve visibility of potential operational issues. |
| **Operations Manager** | Gain a clearer overview of recurring crew-change risks and operational exceptions. |
| **Compliance / Legal** | Ensure the system supports decisions without making autonomous legal, immigration, medical, or employment decisions. |
| **IT / Technical Team** | Ensure the solution is maintainable, observable, secure, and suitable for future production use. |
| **Management** | Understand the operational value, implementation risks, and potential return from the solution. |

---

## 5. Success Criteria

The initial MVP and future pilot should be evaluated against measurable outcomes.

### Success Criterion 1 — Risk Prioritisation

The system should analyse a batch of upcoming crew-change cases and identify cases requiring attention based on defined operational risk criteria.

**Measure:** Percentage of analysed cases successfully assigned a risk level and prioritised for review.

### Success Criterion 2 — Risk Explanation

Each flagged case should provide the main risk drivers in a form that a Crew Manager can understand and review.

**Measure:** Percentage of flagged cases for which the system produces a clear explanation of the main contributing risk factors.

### Success Criterion 3 — Review Efficiency

The system should reduce the time required for the initial review and prioritisation of upcoming crew-change cases compared with the current manual process.

**Measure:** Average review time per batch before and during the pilot.

### Success Criterion 4 — Human Oversight

The system should support human decision-making without taking autonomous operational action.

**Measure:** 100% of operational actions remain subject to human review and approval.

The baseline and final target values for efficiency and accuracy should be validated during the pilot using actual process measurements.

---

## 6. Out-of-Scope Boundaries

The Crew Change Risk Copilot is not intended to:

- determine whether a person is legally permitted to travel;
- replace immigration, medical, or legal advice;
- make employment or personnel decisions;
- autonomously purchase, cancel, or change travel arrangements;
- guarantee that a journey or crew change will succeed;
- autonomously approve, reject, or reschedule a crew change;
- replace the professional judgement of a Crew Manager;
- make autonomous crew-management decisions.

For the capstone project, the system uses **public or synthetic data only** and does not operate on real client personal data.

---

## 7. Evolution from Round 1 to Round 2

### Round 1

Round 1 focused on validating the **Crew Change Risk Copilot** concept through:

- maritime sector research;
- opportunity and risk analysis;
- use-case assessment;
- user stories;
- data research and dashboards;
- an n8n automation Proof of Concept;
- AI-generated crew-change risk briefings; and
- LangSmith monitoring and observability testing.

The Round 1 PoC demonstrated that a hybrid approach combining deterministic risk assessment with AI-generated interpretation could produce structured risk information and concise operational briefings.

### Round 1 Decision

**Decision: KEEP**

The maritime ship-management / crew-management industry and the **Crew Change Risk Copilot** use case remain suitable for further development.

The Round 1 feedback supported continuing with the selected use case while narrowing the next development stage around improving the operational workflow rather than adding unnecessary functionality.

There was therefore **no change to the industry or primary use case**.

### Round 2 Evolution

The main evolution from Round 1 to Round 2 is a move from a **single-case demonstration** toward a more realistic **management-by-exception workflow**.

The intended workflow is:

> **New crew-change cases → Batch risk analysis → Prioritisation → Database update → Concise management summary → Human review and team discussion**

The solution therefore focuses on helping the crewing team identify the cases that deserve attention during the daily operational review.

The technical direction has also become clearer.

The **n8n workflow remains the Round 1 Proof of Concept**, demonstrating that the core concept can work.

For a future production-oriented implementation, the system would likely move to a coded architecture such as **Python + LangGraph**, providing greater flexibility for orchestration, testing, monitoring, maintainability, and integration with a dedicated application.

The Round 2 development therefore keeps the same validated business problem and use case while improving the operational workflow and defining a clearer path from **PoC → MVP → Pilot → Production**.