# W8D5_Project_5_Capstone
- Week 8 / Day 5
- Student: Andreas Papachristophorou
- Course: AI Consulting & Integration 2026-07
- Date: 2026-09-02
---

# AI Capstone Project Round 2 — Crew Change Risk Copilot

## Overview

The **Crew Change Risk Copilot** is a human-in-the-loop decision-support system for maritime crew-change operations.

It helps crewing teams identify upcoming crew-change cases that may require attention, understand the main risk drivers, and review an AI-generated operational briefing.

The Round 2 project builds on the Round 1 Proof of Concept and develops a working MVP using **n8n, Airtable, OpenAI, Notion and LangSmith**.

---

## 1. What the System Does

The MVP combines:

**Operational data + external context → deterministic risk assessment → AI interpretation → structured risk briefing → human review**

The demonstration flow is:

```text
Generate 5 Demo Cases
        ↓
Crew Change Risk Assessment
        ↓
Operational Context + Weather
        ↓
AI Risk Briefing
        ↓
Airtable Update
        ↓
Notion Report
        ↓
LangSmith Monitoring
````

The deterministic layer calculates the risk score. The LLM interprets the structured information and provides recommendations for human review.

---

## 2. Important Design Principle

The Copilot is a **decision-support tool**, not an autonomous decision-maker.

The final operational decision remains with the human user.

The system does not autonomously approve or reject crew changes, change travel arrangements, make employment decisions, determine legal immigration status, or replace professional judgement.

---

## 3. Project Structure

```text
README.md

compliance/
├── eu_ai_act_compliance.md
└── gdpr_documentation.md

feedback/
└── round1_decision.md

mvp/
├── Crew Change Copilot - MVP.json
├── Demo Cases Generator for Crew Travel Copilot.json
├── mvp_documentation.md
└── screenshots

poc/

roi_risk_assessment.md
strategic_plan.md
use_case_definition.md
Crew_Change_Risk_Copilot_Final_Presentation.pdf
Crew_Change_Risk_Copilot_Final_Presentation.pptx
LICENSE
```

---

## 4. Where to Start

### 1. Use Case Definition

`use_case_definition.md`

Business problem, proposed solution, stakeholders, success criteria and Round 1 → Round 2 evolution.

### 2. MVP

`mvp/mvp_documentation.md`

Detailed MVP documentation and demonstration procedure.

**Important:** Run `Demo Cases Generator for Crew Travel Copilot` first. It creates **5 new synthetic cases** for the demonstration.

Then run:

`Crew Change Copilot - MVP`

Review the outputs in Airtable, Notion and LangSmith.

### 3. Strategic Plan

`strategic_plan.md`

Proposed implementation and development approach.

### 4. ROI & Risk Assessment

`roi_risk_assessment.md`

Business value, risks and implementation considerations.

### 5. Compliance

`compliance/`

EU AI Act and GDPR considerations.

### 6. Feedback

`feedback/round1_decision.md`

Round 1 feedback and project decision.

---

## Attribution and Use

This project was created by Andreas Papachristophorou as part of an AI Consulting & Integration Capstone Project.

The project uses public and synthetic data for demonstration purposes only and is not intended for real operational decision-making.

Third-party data, software, APIs and external resources remain subject to their respective licenses and terms of use.