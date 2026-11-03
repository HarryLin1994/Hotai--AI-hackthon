# Planning

## 0. Planning Status

Status: system design planning document completed for proposal and prototype planning.

Primary current source:
- `/Users/harrylin/Downloads/hotai-hackathon-proposal (1).pptx`

Repo reference documents:
- `README.md`
- `docs/jarvis-ppt-master-plan.md`
- `docs/system-structure.md`
- `docs/guardrails.md`
- `docs/data-inventory.md`
- `docs/proposal-working-draft.md`

This document is the working system design plan for **Jarvis 售後保修智慧語音代理**. It should guide both:
- the hackathon proposal narrative, and
- the MVP demo architecture.

Important distinction:
- Some items are available in the repo today.
- Some items are proposal assumptions.
- Some items are future production integrations.

The planning document must keep these categories separate so the proposal is ambitious but technically credible.

## 1. Product Direction

Product name:
- Jarvis 售後保修智慧語音代理
- Jarvis After-Sales Voice Agent

Challenge topic:
- 運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

Team:
- Jarvis計畫

One-sentence system goal:
- Build a voice-first AI service layer for TOYOTA after-sales journeys that reduces owner cognitive load, supports service advisors, follows official SOP guardrails, and converts after-sales interactions into measurable retention and revenue signals.

Core proposal thesis:
- After-sales service is not only an operational workflow. It is the retention battlefield after vehicle delivery.
- Jarvis should make owners feel that service is transparent, understandable, safe, and easy to act on.
- The system should help TOYOTA improve over-warranty return, urgent repair routing, app / LINE engagement, service advisor consistency, and customer satisfaction.

## 2. Target Users And Scenarios

### 2.1 Primary Users

Vehicle owners:
- TOYOTA owners returning for scheduled maintenance.
- Over-warranty owners at risk of leaving official service channels.
- Owners in urgent accident / roadside assistance scenarios.
- Older or stressed users who should not be forced through complex app menus.

Service advisors:
- Frontline service advisors handling high reception volume.
- Newer advisors who need official, standardized explanations.
- Advisors who need fast, owner-friendly wording for technical items.

Business and service operations:
- Service-center managers.
- Customer experience / NPS teams.
- After-sales revenue and retention teams.

### 2.2 MVP Demo Scenarios

Scenario A: over-warranty maintenance return

```text
Owner has a 60,000 km upcoming maintenance need.
Jarvis reads mock owner / vehicle / contract context.
Jarvis explains the maintenance need in plain language.
Jarvis suggests an official service appointment.
Service advisor receives a concise script and likely Q&A.
Owner receives a voice + text summary through the demo UI.
```

Scenario B: accident / urgent service routing

```text
Owner reports an accident by voice.
Jarvis asks only the minimum necessary safety and location questions.
Jarvis classifies the case as urgent.
Jarvis avoids final liability or price claims.
Jarvis routes to official roadside assistance / service advisor confirmation.
Jarvis shows a trace explaining what is official, assumed, and uncertain.
```

Scenario C: customer lounge transparency

```text
Owner waits during a service visit.
Jarvis shows the current service stage.
Owner asks why an item matters.
Jarvis explains using official process knowledge and owner-friendly wording.
Jarvis provides next-care suggestions after advisor confirmation.
```

MVP priority:
- Build Scenario A first because it demonstrates retention, personalization, advisor copilot, and guardrails with lower operational risk.
- Add Scenario B as a scripted high-impact demo path because it is persuasive for the proposal but requires stricter safety language.
- Use Scenario C to show the "waiting time becomes peak experience" concept.

## 3. System Scope

### 3.1 In Scope For Proposal MVP

The prototype should include:
- Owner voice / chat interface.
- Advisor copilot panel.
- Mock owner and vehicle profile.
- Mock maintenance history and contract state.
- Service-flow state model based on provided TOYOTA materials.
- Lightweight official knowledge lookup over extracted / manually structured content.
- Multi-agent or staged workflow: analyzer, inspector, proposer.
- Guardrail trace showing claim source and required human confirmation.
- App / LINE continuation simulated as UI actions.
- Metrics event logging for proposal KPIs.

### 3.2 Out Of Scope For MVP

The prototype should not claim to provide:
- real My Toyota App integration,
- real 車美仕 4G device integration,
- real-time service-bay availability,
- real-time parts inventory,
- real insurance policy lookup,
- real roadside dispatch,
- legally binding repair estimates,
- final warranty / liability decisions,
- production-grade identity, consent, or data governance.

These can appear in the roadmap as future integrations.

### 3.3 Production Vision

Production Jarvis may integrate:
- My Toyota App / LINE official account.
- 車美仕 connected vehicle data.
- owner maintenance history.
- warranty and contract data.
- official service manuals and price tables.
- dealer service-bay scheduling.
- official roadside assistance and body / paint center routing.
- NPS / satisfaction feedback.
- service manager analytics dashboard.

## 4. Core System Design Decisions

### Decision 001: Voice-First, Text-Supported Interaction

Status: accepted.

Decision:
- Jarvis should be designed voice-first because the strongest pain point is cognitive overload during maintenance, urgent repair, and older-user scenarios.
- Every voice answer should also produce a concise text card.

Reasoning:
- Voice reduces navigation burden in high-stress or low-digital-literacy contexts.
- Text cards preserve clarity, confirmation, and auditability.
- The deck's positioning depends on "0 認知負擔"; a chat-only MVP would weaken that story.

MVP implementation:
- Use browser speech APIs or scripted voice controls if time is limited.
- Keep an alternative path with text input so the demo remains stable.

### Decision 002: Structured Workflow First, RAG Second

Status: accepted for MVP; revisit for production.

Decision:
- Do not make a vector database the center of the MVP.
- First build structured tools for service stage, owner context, claim classification, and canned official snippets.
- Add lightweight retrieval only where a response needs an official evidence snippet.

Reasoning:
- Current provided materials are small and process-heavy.
- The highest-value behavior is workflow orchestration, not generic document Q&A.
- Structured state and explicit guardrails make the demo easier to explain to judges.

Production direction:
- Full RAG becomes important when TOYOTA manuals, warranty rules, price tables, FAQ, service Q&A, and model-specific documents are available.

### Decision 003: Three-Stage Agent Workflow

Status: accepted.

Decision:
- The system should use a staged agentic flow:

```text
Analyzer Agent
  -> Inspector / Guardrail Agent
  -> Proposal / Response Agent
```

Role split:
- Analyzer finds context, intent, service stage, likely need, and candidate next action.
- Inspector checks official boundary, uncertainty, safety, privacy, and forbidden claims.
- Proposal Agent rewrites the approved response in Jarvis's warm, plain-language tone.

Reasoning:
- This maps directly to the PPT story.
- It separates reasoning from compliance checking and final tone.
- It lets the UI show a trace that makes the system feel trustworthy.

### Decision 004: Human Confirmation For Operational Decisions

Status: accepted.

Decision:
- Jarvis may suggest, summarize, and prepare.
- A service advisor or official channel must confirm final service decisions, price, warranty, parts availability, dispatch, and appointment status.

Reasoning:
- After-sales service includes safety, liability, and cost expectations.
- Overclaiming would damage trust and proposal credibility.

### Decision 005: On-Premise As Production Direction, Local Mock For Demo

Status: accepted as proposal direction; demo uses local mock data.

Decision:
- The proposal can position on-premise / private-cloud deployment as a future enterprise architecture for privacy and cost control.
- The hackathon MVP should run locally or as a simple web prototype with mock data.

Reasoning:
- Real owner, vehicle, location, and accident data are sensitive.
- The demo does not need production infrastructure to prove the service workflow.

## 5. Logical Architecture

### 5.1 MVP Architecture

```text
Frontend Demo
  - Owner voice/chat view
  - Advisor copilot view
  - Guardrail trace view
  - Scenario selector

Backend API
  - Session and case state
  - Scenario orchestration
  - Tool execution
  - Metrics event logging

AI Workflow
  - Analyzer Agent
  - Inspector / Guardrail Agent
  - Proposal Agent

Tool Layer
  - Owner Context Tool
  - Vehicle Snapshot Tool
  - Maintenance History Tool
  - Service Flow Tool
  - Official Knowledge Tool
  - Appointment Suggestion Tool
  - Metrics Logger

Data Layer
  - Structured mock owner data
  - Structured mock vehicle data
  - Structured service-flow states
  - Extracted official document text
  - Manually curated official snippets
  - Demo metrics log
```

### 5.2 Production Reference Architecture

```text
My Toyota App / LINE / Car Device / Service Advisor Dashboard
  -> API Gateway and Auth / Consent Layer
  -> Jarvis Orchestration API
  -> Agentic Workflow
  -> Guardrail and Audit Service
  -> Integration Tools
      - CRM / owner profile
      - service history
      - connected vehicle telemetry
      - warranty / contract
      - official manuals and SOP
      - parts / price table
      - service-bay schedule
      - roadside assistance
      - NPS and feedback
  -> Analytics / Value Loop
  -> Data Governance / Observability / Human Review
```

### 5.3 Recommended MVP Tech Stack

Frontend:
- React / Next.js.
- Tailwind CSS.
- Web Speech API for demo STT/TTS when browser support is acceptable.
- Fallback text input and scripted playback.

Backend:
- Python FastAPI.
- Pydantic models for typed requests, tool outputs, and guardrail traces.
- SQLite or JSON files for local demo state.

AI layer:
- LLM API or local model wrapper depending on available environment.
- Tool-calling style orchestration.
- Deterministic pre-checks plus LLM inspector.

Data:
- JSON or YAML for mock owner / vehicle / maintenance data.
- JSON or YAML for service-flow states.
- Markdown / JSON snippets for official knowledge.
- JSONL metrics log for demo analytics.

Deployment:
- Local dev server for hackathon demo.
- Docker packaging if time permits.
- Future on-premise / private-cloud architecture for enterprise story.

## 6. Agent And Tool Design

### 6.1 Analyzer Agent

Purpose:
- Understand user intent and produce a candidate service plan.

Inputs:
- user utterance,
- active scenario,
- owner profile,
- vehicle snapshot,
- maintenance history,
- contract / warranty mock state,
- service-flow state,
- official knowledge snippets.

Outputs:
- intent classification,
- urgency level,
- service stage,
- candidate explanation,
- candidate action,
- required data sources,
- uncertainty list.

Example intents:
- scheduled maintenance question,
- over-warranty retention offer,
- accident / urgent help,
- cost explanation,
- service progress question,
- next-care recommendation,
- appointment request.

### 6.2 Inspector / Guardrail Agent

Purpose:
- Prevent unsafe, unsupported, or misleading output.

Checks:
- Does the response contradict official service materials?
- Does it state a final price without staff confirmation?
- Does it claim warranty / insurance responsibility without source?
- Does it claim live appointment, parts, or dispatch status without integration?
- Does it reveal personal data unnecessarily?
- Does it give unsafe accident guidance?
- Does it clearly distinguish official facts, mock assumptions, and AI suggestions?

Outputs:
- pass / fail / revise,
- blocked claims,
- required disclaimer,
- advisor-confirmation requirement,
- source classification.

### 6.3 Proposal / Response Agent

Purpose:
- Convert approved candidate output into Jarvis's final user-facing response.

Tone:
- plain language,
- calm,
- concise,
- warm but not salesy,
- specific about next action,
- explicit when confirmation is required.

Outputs:
- owner voice script,
- owner text card,
- advisor script,
- next action options,
- guardrail trace summary.

### 6.4 Core Tools

Owner Context Tool:
- Returns mock owner profile, communication preference, app / LINE behavior, and consent flags.

Vehicle Snapshot Tool:
- Returns mock mileage, model, age, connected-device status, and relevant vehicle signals.

Maintenance History Tool:
- Returns mock service history and upcoming maintenance threshold.

Service Flow Tool:
- Maps the case to service-flow stage and expected next steps.

Official Knowledge Tool:
- Looks up curated snippets from official TOYOTA / Hotai materials.
- Returns citations or snippet IDs for trace display.

Appointment Suggestion Tool:
- Demo-only tool that returns mock appointment options.
- Must label all availability as simulated.

Metrics Logger:
- Records demo events such as intent type, repeated question, advisor script generated, voice completion, appointment click, and satisfaction rating.

## 7. Data And Knowledge Plan

### 7.1 Current Repo Data

Current raw data:
- `data/raw/toyota_after_sales_competition_data.7z`

Current extracted data:
- `data/extracted/toyota_after_sales/`
- TOYOTA return-service process manual PDF.
- LINE reservation operation image.

Current processed data:
- `data/processed/toyota_after_sales/toyota_return_service_process_manual.txt`
- `data/processed/toyota_after_sales/toyota_return_service_process_manual.pages.jsonl`
- `data/processed/toyota_after_sales/manifest.json`

Known limitation:
- PDF text extraction is limited because the source is diagram-heavy.
- LINE reservation image likely needs OCR or manual extraction.

### 7.2 Required MVP Data Assets

Create or prepare:
- `mock_owner_profiles.json`
- `mock_vehicle_snapshots.json`
- `mock_maintenance_history.json`
- `service_flow_states.json`
- `official_knowledge_snippets.json`
- `demo_scenarios.json`
- `guardrail_rules.json`

These assets should support the three MVP demo scenarios without requiring real TOYOTA data.

### 7.3 Knowledge Authority Order

Use this authority order:

1. Official TOYOTA / Hotai service materials.
2. Approved internal data, if available in a real deployment.
3. Structured mock data for demo only.
4. Public research and customer voice analysis.
5. LLM-generated wording and suggestions.

The UI and trace should label the source category when a claim affects price, safety, warranty, service step, or appointment action.

### 7.4 RAG Plan

MVP:
- Use manually curated snippets and keyword lookup.
- Use structured service-flow states.
- Avoid presenting retrieval as full production RAG.

Pilot:
- Build a small vector index for official manuals, SOP, FAQ, warranty rules, price references, and service scripts.
- Add retrieval evaluation and human-reviewed answer templates.

Production:
- Use enterprise RAG with versioned document ingestion, permission control, audit logs, and approved-answer review.

## 8. Guardrail Policy

Jarvis can:
- explain service items in plain language,
- summarize known service-flow steps,
- prepare advisor scripts,
- recommend official-channel contact,
- provide simulated appointment options in demo,
- generate post-service recap drafts,
- ask clarifying questions.

Jarvis cannot:
- make final repair decisions,
- guarantee final price,
- determine warranty or insurance responsibility,
- claim live inventory / appointment / dispatch status without integration,
- replace emergency services,
- instruct unsafe accident behavior,
- expose unnecessary personal information,
- contradict official TOYOTA / Hotai materials.

Required escalation language:
- "This needs service advisor confirmation."
- "This estimate is for demo / initial explanation only."
- "Final cost depends on technician inspection and official quotation."
- "For accident or safety issues, please move to a safe location first and contact official assistance / emergency services as needed."

## 9. User Experience Plan

### 9.1 Owner View

The owner view should show:
- large voice entry point,
- concise text transcript,
- Jarvis response card,
- next action buttons,
- service stage / progress,
- confirmation status,
- app / LINE continuation action.

Avoid:
- deep menus,
- dense tables,
- technical jargon,
- unconfirmed prices as if final.

### 9.2 Advisor View

The advisor view should show:
- owner context card,
- vehicle / mileage / contract summary,
- current visit purpose,
- recommended explanation script,
- likely customer questions,
- guardrail warnings,
- items requiring advisor confirmation.

### 9.3 Trace View

The trace view should show:
- detected intent,
- data sources used,
- official snippets used,
- mock assumptions,
- blocked claims,
- final advisor-confirmation requirements.

This is important for judges because it makes "responsible AI" visible.

## 10. Metrics And Value Loop

### 10.1 Experience Metrics

- service-item comprehension score,
- perceived transparency score,
- customer satisfaction score,
- NPS after service,
- owner confidence / trust score,
- voice interaction completion rate.

### 10.2 Operational Metrics

- reception explanation time,
- advisor preparation time,
- repeated-question rate,
- service handover explanation time,
- guardrail intervention rate,
- advisor acceptance / edit rate.

### 10.3 Digital Engagement Metrics

- app / LINE interaction rate,
- recap open rate,
- appointment confirmation rate,
- follow-up Q&A rate,
- customer lounge interaction completion rate.

### 10.4 Business Metrics

- over-warranty return rate,
- official-channel accident / repair routing rate,
- incremental service revenue,
- incremental service gross profit,
- cost per AI-assisted case,
- ROI by scenario.

## 11. Cost And ROI Assumptions

The PPT contains strong ROI claims:
- over-warranty return uplift,
- accident routing uplift,
- NT$ 1.836 億 annual revenue uplift,
- NT$ 8,532 萬 annual gross profit uplift,
- NT$ 400 萬 annual cost,
- 2,033% first-year ROI scenario.

Planning guardrail:
- Treat these as proposal scenario assumptions until validated.

Known calculation issue to resolve:
- The deck says over-warranty return improves by 3% and uses 10,800 incremental visits.
- If the target over-warranty owner base is 108,000, then 3% equals 3,240 visits.
- 10,800 visits equals 10% of 108,000 or 3% of 360,000.
- The proposal should either clarify the denominator or use the sensitivity table from `docs/jarvis-ppt-master-plan.md`.

Recommended slide language:
- "Under the optimistic scenario..."
- "Assuming 360,000 connected members..."
- "Final ROI requires validation with internal owner base, return-rate baseline, accident case volume, gross margin, and implementation cost."

## 12. Implementation Roadmap

### Phase 0: Planning Finalization

Deliverables:
- completed planning document,
- confirmed MVP scenario list,
- confirmed system architecture,
- confirmed data assumptions,
- confirmed guardrail policy.

Status:
- this document completes the first draft.

### Phase 1: Data And Scenario Preparation

Deliverables:
- structured service-flow states,
- curated official knowledge snippets,
- mock owner profiles,
- mock vehicle snapshots,
- mock maintenance histories,
- demo scenario definitions.

Acceptance criteria:
- Scenario A can run end to end with deterministic data.
- Every service or price-related claim has a source category.
- Unknown items are marked for advisor confirmation.

### Phase 2: Backend Workflow Prototype

Deliverables:
- FastAPI endpoints,
- typed request / response schemas,
- analyzer / inspector / proposer workflow,
- tool layer over mock data,
- metrics logger,
- guardrail trace payload.

Acceptance criteria:
- Given a user utterance, backend returns owner response, advisor script, next actions, and trace.
- Guardrail agent blocks or revises unsupported price / warranty / dispatch claims.

### Phase 3: Frontend Demo Prototype

Deliverables:
- owner voice / chat view,
- advisor copilot view,
- trace view,
- scenario switcher,
- scripted voice fallback.

Acceptance criteria:
- Judges can understand the value proposition without reading backend logs.
- Demo can run even if browser voice input fails.

### Phase 4: Proposal And Pitch Alignment

Deliverables:
- updated proposal deck language,
- system architecture slide,
- responsible AI slide,
- demo script,
- ROI assumption notes,
- roadmap slide.

Acceptance criteria:
- Deck, demo, and planning document tell the same story.
- Future integrations are clearly labeled.
- ROI assumptions are defensible.

### Phase 5: Pilot Roadmap

Deliverables:
- data governance checklist,
- integration inventory,
- consent / privacy flow,
- retrieval evaluation plan,
- service-center pilot metrics.

Acceptance criteria:
- A real pilot can be scoped without pretending the MVP already has production integrations.

## 13. Immediate Next Actions

Recommended next steps:

1. Convert the provided PDF and LINE image into structured service-flow states.
2. Create mock data for Scenario A and Scenario B.
3. Define backend response schema for owner card, advisor script, trace, and next actions.
4. Build the first scripted agent workflow.
5. Build a split-screen demo: owner view, advisor view, trace view.
6. Update PPT claims to separate MVP, pilot, and production scope.
7. Validate the ROI denominator issue before final submission.

## 14. Open Questions

Product:
- Should the final pitch lead with over-warranty return, accident rescue, or all-age voice accessibility?
- Should the demo show one polished scenario or three shorter scenarios?
- Should "Jarvis" be presented as a standalone assistant or an embedded My Toyota App / LINE AI layer?

System:
- Should MVP use browser STT/TTS, external API voice, or scripted voice playback?
- Should the first backend be fully LLM-driven or mostly deterministic with LLM wording?
- How visible should the guardrail trace be in the main UI?

Data:
- Which official documents can be used beyond the provided process manual?
- Can we reference 車美仕 36 萬會員 as an assumption, internal estimate, or verified figure?
- Can pricing / warranty / insurance examples be shown as mock data?

Business:
- What denominator should the 3% return-rate uplift use?
- What baseline accident / repair case volume is defensible?
- Should the deck emphasize gross profit, ROI, NPS, or operational efficiency as the headline metric?

## 15. Planning Summary

The recommended system design is a **voice-first, guardrailed, multi-agent service workflow**:

```text
Owner / Advisor input
  -> Context and intent analysis
  -> Service-flow and official-knowledge lookup
  -> Safety / compliance / claim-boundary inspection
  -> Warm voice + text response
  -> Advisor confirmation where required
  -> Metrics and feedback loop
```

For the hackathon MVP, the strongest build path is:
- structured mock data,
- structured service-flow tools,
- deterministic guardrails,
- LLM-assisted wording,
- visible trace,
- polished split-screen demo.

For the production story, the strongest architecture is:
- on-premise or private-cloud deployment,
- enterprise RAG over official materials,
- integration with My Toyota App / LINE / connected vehicle data,
- service advisor and owner-facing workflows,
- analytics loop tied to retention, official-channel routing, NPS, and service revenue.
