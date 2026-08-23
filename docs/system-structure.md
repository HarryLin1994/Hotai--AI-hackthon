# System Structure

## Goal

Build an AI-powered TOYOTA after-sales service experience that improves service reception communication and makes customer lounge waiting time more valuable.

The system should support both:
- Service advisors who need fast, consistent, easy-to-understand explanations during peak hours.
- Vehicle owners who need transparent, personalized, low-friction service information.

## Top-Level Folders

| Folder | Purpose |
| --- | --- |
| `backend/` | Future agent workflow, API layer, data tools, guardrail checks, and integrations. |
| `frontend/` | Future demo UI for advisor view, owner view, and customer lounge experience. |
| `docs/` | Challenge brief, planning, proposal, architecture, and guardrails. |
| `data/` | Raw, extracted, and processed reference data. |

## Proposed Flow

```text
Owner / Service Advisor
  -> Frontend
  -> Backend API
  -> Context Builder
  -> Service Flow Tool
  -> Explanation Agent
  -> Lounge Experience Agent
  -> Inspector / Guardrail Agent
  -> Personalized Output
```

## Agent Roles

### Context Builder

Builds the service context for the current visit.

Inputs may include:
- Visit purpose.
- Reservation data.
- Owner maintenance history.
- Vehicle driving data.
- App / LINE interaction history.
- Current service-flow state.

### Service Flow Tool

Uses structured TOYOTA service-process reference data to understand where the owner is in the visit.

Responsibilities:
- Identify service stage.
- Provide expected next steps.
- Support advisor and owner explanations.
- Avoid contradicting official service-process materials.

### Explanation Agent

Turns technical service items into clear, owner-friendly language.

Responsibilities:
- Explain what is being checked or repaired.
- Explain why an item matters.
- Surface likely customer questions.
- Generate service-advisor talking points.

### Lounge Experience Agent

Transforms waiting time into a personalized service experience.

Responsibilities:
- Provide service progress updates.
- Explain current and upcoming service steps.
- Offer personalized car-care tips.
- Suggest app / LINE interactions.
- Create a memorable peak experience during the waiting period.

### Inspector / Guardrail Agent

Checks all user-facing and advisor-facing outputs.

Responsibilities:
- Enforce official TOYOTA / Hotai materials as guardrails.
- Reject unsupported final-price, warranty, or availability claims.
- Ensure explanations are understandable and not misleading.
- Flag when a service advisor must confirm the answer.

## Initial Data Sources

| Data Source | MVP Form | Purpose |
| --- | --- | --- |
| Return-service process manual | Extracted PDF text / future structured process | Service-flow grounding. |
| LINE reservation operation guide | Image reference / future OCR or manual extraction | Reservation-flow understanding. |
| Owner maintenance history | Assumed mock data | Personalization and visit context. |
| Vehicle driving data | Assumed mock data | Personalized explanation and service suggestions. |
| App interaction behavior | Assumed mock data | Personalization and engagement design. |
| Public community data | To be collected | Pain-point and demand analysis. |

## Integration Concepts

Proposal-level integrations:
- TOYOTA app / LINE handoff.
- Customer lounge screen or kiosk.
- Advisor dashboard.
- Voice explanation or voice Q&A.
- Service progress notifications.

Integration guardrails:
- Do not claim live integration unless an official source exists.
- Do not expose personal data without consent.
- Do not make final service or pricing decisions without service-advisor confirmation.

## Discussion Backlog

- Extract service-flow states from the TOYOTA return-service process manual.
- Decide whether the first prototype is advisor-facing, owner-facing, or both.
- Define the customer lounge peak experience.
- Define public-opinion analysis workflow.
- Define measurable benefit assumptions.

