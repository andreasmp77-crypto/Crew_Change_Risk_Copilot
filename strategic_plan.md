# Strategic Deployment and Commercialisation Plan

## 1. Executive Summary

The **Crew Change Risk Copilot** is a human-in-the-loop decision-support solution for maritime crew-management teams.

The Round 1 n8n Proof of Concept validated the core concept:

**Operational data + external context → deterministic risk assessment → AI interpretation → operational risk briefing → human review.**

Round 2 development showed that extending this approach into reliable batch processing requires stronger control of data structures, validation, error handling and orchestration.

The recommended deployment strategy is:

> **POC → Pilot → Full Deployment**

The existing n8n workflow remains the validated PoC. The next implementation stage should use a more suitable coded architecture, initially evaluating **Python + LangGraph**, potentially with n8n retained for selected integration and automation tasks.

Full deployment should only proceed if the Pilot demonstrates measurable operational value, technical reliability and governance readiness.

---

## 2. Deployment Strategy

### Phase 1 — POC

**Status: Completed**

The POC was developed using n8n and demonstrated the core Crew Change Risk Copilot workflow.

The POC demonstrated:

- retrieval of crew-change information;
- integration of external operational context;
- deterministic risk scoring;
- identification of risk drivers;
- AI-assisted interpretation;
- generation of a concise operational briefing;
- human review.

The POC established that the proposed hybrid approach is technically feasible at demonstration level.

### Phase 2 — Pilot

**Status: Proposed**

The Pilot will move from a single-case demonstration to a controlled operational test using multiple crew-change cases.

The Pilot should focus on one clearly defined workflow:

**New crew-change cases → data validation → risk analysis → prioritisation → AI briefing → human review → operational follow-up.**

The Pilot should use a limited user group and a defined number of vessels or crew-management cases.

The objective is not to automate the entire crew-management process. The objective is to determine whether the system helps Crew Managers identify and review potentially problematic cases earlier and more efficiently.

### Phase 3 — Full Deployment

**Status: Conditional**

Full deployment should only be considered after the Pilot demonstrates that the solution provides sufficient operational value and can be operated reliably and safely.

The production solution would include:

- stable data integrations;
- consistent data schemas;
- validation and error handling;
- production monitoring and logging;
- role-based access;
- auditability;
- user interface;
- operational support;
- appropriate compliance and security controls.

### Optional Phase 4 — Scale

After successful deployment, the solution could be extended to:

- additional vessels;
- additional crew-management teams;
- additional operational data sources;
- wider exception-management workflows;
- additional management dashboards;
- integration with existing maritime software platforms.

Scaling should follow evidence from the initial deployment rather than being assumed from the beginning.

---

## 3. Timeline and Milestones

The following timeline is an indicative planning estimate and should be validated during technical discovery.

| Phase | Indicative Duration | Main Milestones |
|---|---:|---|
| POC | Completed | Core workflow demonstrated |
| Technical discovery | 1–2 weeks | Architecture, data model, integration requirements |
| MVP / Pilot preparation | 4–6 weeks | Coded workflow, validation, UI, monitoring, testing |
| Pilot | 8–12 weeks | Controlled operational trial |
| Pilot evaluation | 1–2 weeks | KPI assessment and deployment decision |
| Full deployment | 8–16+ weeks | Production implementation and rollout |
| Scale | Optional | Additional users, vessels and integrations |

The estimate is intentionally broader than the original MVP timeline.

The Round 2 experience showed that time is required not only for AI workflow development, but also for data preparation, schema management, testing, monitoring and reliability.

The revised implementation planning assumption is **approximately €35,000 initial investment**, with approximately **€4,000 annual operating cost**. These are planning assumptions rather than supplier quotations and should be validated during technical discovery and the Pilot.

---

## 4. Technical Deployment Approach

### Recommended direction

The current n8n implementation should remain the Proof of Concept rather than being expanded indefinitely.

The next implementation should evaluate:

**Python + LangGraph**

Python would provide stronger control over:

- data structures;
- schema validation;
- batch processing;
- deterministic risk calculations;
- error handling;
- testing;
- integration.

LangGraph could provide orchestration for the AI-related stages and support stateful human-in-the-loop workflows.

n8n may still be useful for selected integrations and automation tasks where its low-code approach provides value.

The final architecture should be confirmed during technical discovery.

### Proposed high-level architecture

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

This architecture preserves the hybrid principle already demonstrated by the PoC:

> **Rules calculate operational risk; AI interprets the structured result; humans make the decision.**

---

## 5. Go-to-Market Strategy

### Target buyers

The initial target market is:

- medium-sized ship-management companies;
- crew-management companies;
- maritime operations teams;
- companies managing multiple vessels and regular crew changes.

The primary buyer is likely to be a senior operational or crewing decision maker.

Potential stakeholders involved in the buying decision include:

- Head of Crewing / Crew Manager;
- Operations Manager;
- COO;
- CIO / CTO;
- Compliance / Legal.

### Customer pain point

The commercial proposition is not simply "AI for crew management".

The proposition is:

> **Help crewing teams identify potentially problematic crew changes earlier, understand the main risk drivers, and focus human attention where it matters most.**

This positions the solution around operational efficiency and decision support rather than AI novelty.

### Sales channel

The initial route to market should be direct B2B sales supported by:

- pilot projects;
- maritime industry networking;
- ship-management relationships;
- partnerships with maritime software providers;
- demonstrations using representative data.

A pilot-led sales model is appropriate because customers will need evidence of operational value before committing to wider deployment.

### Differentiator

The primary differentiators are:

1. **Management by exception** — focus attention on cases requiring review.
2. **Hybrid risk approach** — deterministic risk rules combined with AI interpretation.
3. **Explainability** — show the main risk drivers rather than only producing a risk label.
4. **Human-in-the-loop** — the system supports rather than replaces the Crew Manager.
5. **Operational context** — combine crew-change information with external signals such as airport disruption and weather.

Management-by-exception is relevant to the maritime operating environment because it shifts attention from constant manual oversight toward exceptions and anomalies. See the Lloyd's List article referenced in the project research: **"AI-powered management by exception may transform shipmanagement."**

The importance of crew changes to seafarer wellbeing and operational continuity is also reflected in IMO guidance on **crew changes and repatriation of seafarers**. This source is useful for explaining why reliable crew-change planning is not only a logistics issue but also a crew welfare and operational concern.

**These two sources should also be referenced briefly in the final presentation, particularly when explaining the business rationale and the management-by-exception differentiator.**

---

## 6. Commercialisation Model

### Recommended model: Pilot → SaaS / Managed Service

The initial commercial model should be a **paid pilot**, followed by a subscription-based or managed-service model.

### Stage 1 — Pilot

A fixed-fee pilot would cover:

- implementation;
- configuration;
- data integration;
- limited users;
- defined pilot scope;
- KPI measurement;
- pilot evaluation.

The current business-case model uses an indicative **€35,000 initial implementation investment** as a planning assumption. This should not be presented as a final market price or supplier quotation.

### Stage 2 — Full deployment

A subscription model could be structured around:

- number of vessels;
- number of users;
- volume of crew-change cases;
- integrations;
- support level.

An alternative is a managed-service model for customers that do not want to operate the technical infrastructure themselves.

The commercial model should remain flexible until the first pilot provides evidence about customer willingness to pay and the true cost of operating the solution.

---

## 7. Stakeholder Communication Plan

| Stakeholder | What they need to know | Communication |
|---|---|---|
| Crew Managers | How the system helps daily prioritisation | Weekly pilot review |
| Crewing Officers | How cases are analysed and reviewed | Training + regular feedback |
| Operations Manager | Operational trends and exceptions | Weekly management summary |
| IT / CTO | Architecture, reliability and integration | Technical review meetings |
| Compliance / Legal | Data use, risk, human oversight and controls | Formal compliance review |
| Senior Management | Value, KPIs, risks and investment decision | Monthly steering review |

Communication should remain focused on **what the system does, why a case was flagged, and what the human needs to review**.

---

## 8. KPIs

### POC KPIs

The POC is considered successful when:

- the core workflow runs end to end;
- risk factors can be identified;
- AI-generated briefings can be produced;
- results can be reviewed by a human.

### Pilot KPIs

The Pilot should measure:

| KPI | Purpose |
|---|---|
| % of cases successfully processed | Technical reliability |
| % of flagged cases with understandable risk drivers | Explainability |
| Average review time per case/batch | Efficiency |
| % of high-priority cases correctly identified | Prioritisation quality |
| Average actual cost avoided per problematic case | Validates the €1,250 assumption |
| Time saved per Crew Manager | Identifies additional productivity value |
| False-positive rate | Tests trust and usability |
| False-negative rate | Tests reliability |
| User adoption | Tests operational viability |
| User satisfaction | Tests practical usefulness |
| System exceptions and errors | Supports monitoring and improvement |

Baseline measurements should be collected before or at the beginning of the Pilot.

### Pilot greenlight criteria

Proceed to Full Deployment only if the Pilot demonstrates:

- reliable processing of the agreed case volume;
- measurable reduction in initial review effort;
- acceptable prioritisation performance;
- clear and understandable risk explanations;
- positive user feedback;
- manageable error rates;
- required logging and monitoring are operational;
- no unresolved critical compliance or security issues;
- sufficient evidence that the measured operational value justifies the implementation and operating costs.

The exact numerical thresholds should be agreed with the pilot customer before the Pilot begins.

---

## 9. Full Deployment Decision Gate

The transition from Pilot to Full Deployment should be treated as a formal **Go / No-Go** decision.

### GREENLIGHT

Proceed when:

**Business**
- measurable operational value is demonstrated;
- users actively use the system;
- the customer confirms willingness to continue.

**Technical**
- reliability is acceptable;
- batch processing is stable;
- integrations are proven;
- monitoring and logging are operational.

**Governance**
- compliance requirements are addressed;
- human oversight is maintained;
- auditability is available.

**Commercial**
- pilot economics are understood;
- implementation and operating costs are realistic;
- the customer accepts the proposed commercial model.

### NO-GO / ITERATE

Do not proceed to full deployment if:

- operational value is not demonstrated;
- system reliability is insufficient;
- users do not trust or understand the outputs;
- data quality is inadequate;
- critical compliance or security gaps remain;
- operating costs are disproportionate to the value created.

In that case, return to the relevant development stage rather than scaling an unproven system.

---

## 10. Key Risks to Deployment

The main strategic risks are:

### Technical complexity

The data structure and batch-processing requirements may require more engineering effort than initially estimated.

**Mitigation:** establish the data model and technical architecture before scaling the workflow.

### Integration effort

Connecting the solution to existing crew-management systems may require additional development.

**Mitigation:** start the Pilot with a clearly bounded data interface.

### User trust

Crew Managers may be reluctant to use AI-generated risk information if the reasoning is unclear.

**Mitigation:** show risk drivers, maintain human review and provide clear monitoring and audit records.

### Data quality

Incomplete or inconsistent data could reduce the quality of risk assessment.

**Mitigation:** validation, schema controls and clear handling of missing data.

### Cost escalation

Production implementation will require more engineering, monitoring and support than the PoC.

**Mitigation:** keep MVP scope small; simplify architecture; use phased delivery; maintain contingency and a pilot Go/No-Go gate.

---

## 11. Strategic Recommendation

The recommended strategy is **not to treat the current n8n workflow as the final production architecture**.

The n8n PoC has achieved its purpose: it demonstrated that the proposed business process and hybrid AI approach are feasible.

The next investment should therefore be a controlled technical and operational Pilot based on a more suitable architecture.

The strategy should also remain conservative on the financial case. The current ROI model assumes **€35,000 initial investment, €4,000 annual operating cost, 15 avoided problematic crew changes per year and €1,250 avoided cost per case**. Under these assumptions, the model produces **−51.9% ROI at 12 months and 19.7% at 36 months**. Direct cost avoidance alone therefore does not justify an immediate full rollout; the Pilot must measure additional operational value, particularly Crew Manager time savings.

The strategic path is:

```text
Validated n8n PoC
        ↓
Technical discovery
        ↓
Python + LangGraph MVP
        ↓
Controlled Pilot
        ↓
KPI / ROI / Governance review
        ↓
GO → Full Deployment
        ↓
Optional Scale
```

The project should scale only when evidence from the Pilot demonstrates that the solution is useful, reliable, trusted and commercially justified.

---

## 12. Presentation Linkage

The final presentation should reinforce the same strategic story rather than introduce separate assumptions.

A concise strategy message for the presentation is:

> **The PoC proved the concept. The Pilot will prove the value. Full deployment will depend on the evidence.**

The presentation should also briefly reference the two industry sources used to support the rationale:

- **IMO — crew changes and repatriation of seafarers:** supports the importance of crew-change planning for seafarer wellbeing, safety and operational continuity.
- **Lloyd's List — "AI-powered management by exception may transform shipmanagement":** supports the management-by-exception direction and the idea of using technology to bring relevant exceptions to human attention.

These references should be used as supporting evidence, not as claims that the proposed solution has already been validated by those organisations.
