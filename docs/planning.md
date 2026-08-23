# Planning

## Current Direction

Build an AI after-sales service assistant for TOYOTA service centers.

The system should help service advisors communicate maintenance and repair information more clearly, while giving vehicle owners a more transparent and personalized waiting-room experience.

## Primary Proposal Focus

The current proposal should focus on:

1. Reception explanation support.
2. Customer lounge waiting-time experience.
3. Personalized service communication based on assumed internal data.
4. Pain-point discovery using public data, interviews, service-flow observation, or GenAI simulation.

## Decision Log

### Decision 001: Official Service Materials Are Guardrails

Status: accepted for proposal planning; final spec pending.

Decision:
- Official TOYOTA / Hotai service materials must act as non-violation guardrails.
- The AI may summarize, simplify, and personalize explanations, but must not contradict official service-process documents or approved service information.
- If final price, responsibility, warranty, parts availability, or live schedule status is uncertain, the system must disclose uncertainty and route to the service advisor or official channel.

Reasoning:
- After-sales service communication affects trust, cost expectations, and customer satisfaction.
- AI-generated explanations must be easy to understand but still operationally safe.
- A proposal is stronger when it shows how AI improves consistency without replacing official service judgment.

### Decision 002: Start With Structured Workflow And Explanation Tools, Not Full RAG

Status: accepted for proposal planning; final spec pending.

Decision:
- Do not start with a full vector database as the core architecture.
- First extract service-flow structure, customer pain points, and explanation rules.
- Use lightweight manual search or citations only when the answer needs official evidence.

Reasoning:
- The provided materials are small and process-oriented.
- Many useful behaviors are workflow states, checklist items, and explanation templates.
- The core value is service experience design, not generic document Q&A.

## Planned Product Concept

Working name:
- TOYOTA Care Concierge AI

Working Chinese name:
- TOYOTA 智慧售後服務助理

## Planned Experience Flow

```text
Before visit / reservation
  -> AI prepares owner and vehicle context

Service reception
  -> Service advisor receives AI-generated explanation support
  -> Owner receives plain-language service summary

Customer lounge waiting
  -> Owner sees personalized progress and service explanation
  -> Owner can ask AI follow-up questions through app / LINE / kiosk

Before handover
  -> AI generates final service summary and next-care suggestions

After leaving
  -> Owner receives a clear recap through app / LINE
```

## Planned AI Components

- Context Builder: combines assumed maintenance history, vehicle data, app behavior, and current visit purpose.
- Pain Point Analyzer: analyzes public opinions, interview notes, and simulated service scenarios.
- Service Explanation Agent: converts technical service items into plain-language owner explanations.
- Advisor Copilot: suggests concise explanation scripts and likely customer questions.
- Lounge Experience Agent: creates personalized waiting-room updates and educational content.
- Inspector / Guardrail Agent: checks that explanations do not contradict official service materials.

## Data Layer Plan

Current provided materials:

```text
data/raw/toyota_after_sales_competition_data.7z
data/extracted/toyota_after_sales/
data/processed/toyota_after_sales/
```

Provided reference contents:
- TOYOTA return-service process manual PDF.
- TOYOTA official LINE reservation operation image.

Assumed internal data for proposal design:
- Owner maintenance history.
- Vehicle driving data.
- App interaction behavior.

External public data for pain-point analysis:
- Online community posts.
- Reviews and forum discussions.
- YouTube/article comments where available.
- Interview or observation notes if collected.

## Spec Finalization Backlog

- Choose final product name.
- Define primary user journey: service advisor, vehicle owner, or both.
- Define pain-point analysis method and source set.
- Define service-flow states from the provided manual.
- Define AI feature list for the proposal.
- Define prototype scope.
- Define measurable benefits and ROI assumptions.
- Define how app / LINE / kiosk / voice interactions are represented.
- Define which integrations are demo-only versus official-service integrations.

## Open Questions

- Should the proposal emphasize service-advisor efficiency, customer lounge experience, or a full end-to-end journey?
- Should the prototype be owner-facing, advisor-facing, or a split-screen demo?
- How much public-opinion analysis can we complete before submission?
- Which measurable metric should be the headline: reception time, repeated-question rate, satisfaction, app/LINE interaction rate, or return-service intent?

