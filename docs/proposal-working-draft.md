# Proposal Working Draft

Source template:
- `docs/proposal-template.pptx`

Current proposal direction:
- 運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

## Slide 2: Proposal Summary

### Team Name

Jarvis計畫.

### Product / Service Name

Working name: TOYOTA Care Concierge AI.

Chinese working name: TOYOTA 智慧售後服務助理.

### Enterprise Challenge Topic

運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

### Target Audience

Primary:
- TOYOTA owners returning to service centers for maintenance or repair.

Secondary:
- Service advisors who need to explain service items clearly during high-traffic periods.
- Service-center operators who want better communication quality and customer satisfaction.

### Solution Design Highlights

1. Advisor Copilot: helps service advisors generate plain-language explanations, likely customer questions, and concise scripts.
2. Customer Lounge AI: turns waiting time into a transparent, personalized, interactive service experience.
3. Guardrailed AI: checks explanations against official TOYOTA / Hotai service materials and escalates uncertain items to staff.

### AI Technologies / Services / Models

Working list:
- LLM for service-item explanation, scenario simulation, and owner-friendly summaries.
- Structured service-flow tool based on provided process materials.
- Public-opinion and interview analysis for pain-point discovery.
- Inspector / Guardrail Agent for official-material non-violation.
- App / LINE interaction design for owner communication.
- Voice or kiosk interaction for customer lounge experience.

### Expected Benefits

Working claim:
- Shorten reception explanation time.
- Reduce repeated owner questions.
- Improve owner understanding of service items.
- Increase app / LINE interaction.
- Improve customer satisfaction and return-service intent.

Quantitative targets are TBD and should be finalized after research.

## Slide 3: 1. Proposal Overview

### Proposal Name

TOYOTA Care Concierge AI.

### Core Value Proposition

Create a next-generation after-sales service experience where every owner receives clear, personalized, trustworthy explanations before, during, and after the service visit.

### Core Problem

During peak hours, service advisors face high reception volume and limited explanation time. Owners may not fully understand technical service items, expected waiting time, or why a maintenance or repair recommendation matters.

The customer lounge also remains underused as a service-experience touchpoint. Waiting can become a moment for transparency, education, personalization, and brand trust.

### Target

Build an AI service assistant that:
- Reduces communication pressure on service advisors.
- Reduces information asymmetry for owners.
- Makes waiting time valuable.
- Creates a memorable peak experience in the after-sales journey.

## Slide 4: 2. Target Audience And Pain Point Analysis

### User Profile

Primary user:
- TOYOTA owner returning for maintenance or repair.
- Wants clear, trustworthy, easy-to-understand service information.
- May use LINE / app for reservation and updates.

Operational user:
- Service advisor handling many owners during peak hours.
- Needs fast access to vehicle context and explanation support.

### Pain Points

For owners:
- Technical service explanations are hard to understand.
- Costs and service items may feel opaque.
- Waiting time feels passive and low value.
- Owners may repeatedly ask similar questions.
- App / LINE touchpoints may not feel personalized enough.

For service advisors:
- High peak-hour reception load.
- Limited time to tailor explanations.
- Repetitive questions.
- Need to maintain consistent explanation quality.

### Analysis Method

Use:
- Provided return-service process material.
- LINE reservation operation reference.
- Public online discussion analysis.
- Interview or simulated interview data.
- GenAI scenario simulation.

## Slide 5: 3. Solution Design

### Overall Flow

```text
Before visit
  -> AI prepares owner and vehicle context

Reception
  -> Advisor Copilot generates explanation support
  -> Owner receives plain-language visit summary

Customer lounge
  -> Owner sees progress, explanations, and personalized tips
  -> Owner asks follow-up questions through app / LINE / kiosk

Handover
  -> AI generates service recap and next-care suggestions

After visit
  -> Owner receives a clear app / LINE summary
```

### Key Features

- Pre-visit context card.
- Advisor explanation script.
- Owner-friendly service item explanation.
- Customer lounge progress and education cards.
- Personalized car-care tips.
- Follow-up Q&A.
- Final service recap.

### Guardrail Design

The system must distinguish:
- Official service-process information.
- Assumed internal data.
- Public-opinion insights.
- AI-generated suggestions.

Final service decisions, prices, and warranty responsibility must remain confirmed by staff.

## Slide 6: 4. AI Application Method

### AI Roles

Context Builder:
- Combines reservation, maintenance history, vehicle data, and app behavior assumptions.

Pain Point Analyzer:
- Analyzes public opinion, interview notes, and simulated scenarios.

Service Explanation Agent:
- Converts technical service content into owner-friendly language.

Advisor Copilot:
- Suggests talking points and likely customer questions.

Lounge Experience Agent:
- Generates personalized waiting-room updates and educational content.

Inspector / Guardrail Agent:
- Checks official-material non-violation and prevents overclaims.

## Slide 7: 5. Unique Advantages And Differentiation

### Differentiation

This proposal is not a generic chatbot. It redesigns the after-sales journey around high-value moments:
- Reception explanation.
- Waiting-room transparency.
- Personalized recap.
- App / LINE continuity.

### Innovation Points

- Turns waiting time into a peak experience.
- Helps advisors communicate faster and more consistently.
- Uses AI to reduce information asymmetry.
- Combines public pain-point analysis with assumed internal personalization data.
- Uses guardrails to keep AI explanations operationally safe.

## Slide 8: 6. Expected Benefits And Landing Assessment

### Expected Benefits

Customer experience:
- Better understanding of service items.
- More transparent waiting experience.
- Higher trust in service recommendations.

Operational efficiency:
- Shorter reception explanation time.
- Lower repeated-question rate.
- More consistent advisor communication.

Digital engagement:
- Higher app / LINE interaction.
- More useful post-visit follow-up.

### Candidate Metrics

- Average reception explanation time.
- Repeated-question rate.
- Service-item comprehension score.
- Customer satisfaction score.
- App / LINE interaction rate.
- Return-service intention.

### Landing Plan

Phase 1:
- Structure service-flow data.
- Build proposal prototype for advisor and owner views.

Phase 2:
- Add app / LINE style interaction and customer lounge screen.

Phase 3:
- Pilot with mock service-center scenarios.

Phase 4:
- Connect official systems if approved.

## Slide 9: 7. Supplementary Materials

### Current Repo Materials

- Challenge brief: `docs/challenge-toyota-after-sales-service.md`
- Planning doc: `docs/planning.md`
- Guardrails: `docs/guardrails.md`
- System structure: `docs/system-structure.md`
- Data inventory: `docs/data-inventory.md`

### Provided Data

- `TOYOTA回廠服務流程手冊.pdf`
- `附件_LINE預約操作說明.jpg`
- Processed text and manifest under `data/processed/toyota_after_sales/`

### Reference / Evidence To Add Later

- Public-opinion analysis.
- Interview notes.
- Service-flow structured extraction.
- Prototype screenshots.
- Quantitative benefit assumptions.

