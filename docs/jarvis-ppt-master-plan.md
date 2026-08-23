# Jarvis PPT Master Planning Brief

## 0. Purpose

This document is the single planning brief for generating the hackathon proposal deck.

It consolidates:
- Spec.
- Features.
- Tech stack.
- Cost model.
- ROI model.
- Data assumptions.
- Landing plan.

Primary source:
- `docs/jarvis-after-sales-voice-agent-report.docx`

Challenge topic:
- 運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

Team:
- Jarvis計畫

## 1. One-Sentence Pitch

Jarvis 是一套 voice-first 的 TOYOTA 售後保修智慧代理，透過 GenAI、原廠知識 guardrails 與車主/車輛資料，降低車主在保養、維修與緊急服務情境中的認知摩擦，並把售後服務轉化為可衡量的顧客留存與營收成長閉環。

## 2. Strategic Thesis

交車不是顧客關係的終點，而是售後服務關係的起點。

TOYOTA 售後服務的核心挑戰不是只有「如何加速流程」，而是如何在高入廠量、高資訊落差與高等待焦慮的情境下，讓車主感受到：

- 我知道現在發生什麼事。
- 我聽得懂服務專員說明。
- 我相信原廠建議不是黑箱。
- 我願意下次繼續回廠。

Jarvis 的戰略角色：

```text
Vehicle / owner data
  -> AI pattern discovery
  -> Official domain knowledge
  -> Jarvis voice assistant
  -> Worry-free service experience
  -> NPS and service behavior feedback loop
```

## 3. Problem Definition

### 3.1 Owner Pain Points

- 維修與保養說明太技術化，車主不容易理解。
- 尖峰時段服務專員時間有限，說明容易變短或不完整。
- 客休等待時間被動，車主不知道車子正在經歷什麼流程。
- 費用、必要性、風險與下次保養建議缺乏清楚脈絡。
- 高齡或不熟悉 App 的車主，在緊急或保修情境下不適合操作複雜 GUI。

### 3.2 Service Advisor Pain Points

- 尖峰時段接待量高。
- 同樣問題重複解釋。
- 需要在短時間內把技術內容轉成車主聽得懂的語言。
- 不同服務專員的說明品質難以標準化。
- 顧客個人化資料分散，接待前準備成本高。

### 3.3 Business Pain Points

- 售後服務是顧客留存與經銷商利潤的關鍵。
- 過保車主容易流向民間保養廠。
- 事故、保修與非預期維修情境若體驗不佳，會傷害 NPS 與品牌信任。
- 服務體驗若無數據閉環，難以量化改善效益。

## 4. Product Spec

### 4.1 Product Name

Working English name:
- Jarvis After-Sales Voice Agent

Working Chinese name:
- Jarvis 售後保修智慧語音代理

### 4.2 Product Positioning

Jarvis 是 TOYOTA 售後服務場景中的 AI service layer。

它不是取代服務專員，而是同時服務兩種角色：

- 對服務專員：接待與說明 copilot。
- 對車主：全年齡無障礙語音助理與客休室透明化互動入口。

### 4.3 Target Users

Primary:
- TOYOTA 回廠保養/維修車主。
- 過保後仍有保修需求的車主。
- 不熟悉 App 或不想操作複雜介面的車主。

Secondary:
- TOYOTA 服務專員。
- 服務廠營運管理者。
- 客服與售後營運團隊。

### 4.4 Core User Journey

```text
Before visit
  -> Jarvis reads reservation / owner / vehicle context
  -> Generates advisor context card

Reception
  -> Service advisor uses Jarvis to explain service items in plain language
  -> Owner receives voice + text summary

Customer lounge
  -> Owner asks questions by voice / app / LINE / kiosk
  -> Jarvis explains current stage, service item meaning, and car-care tips

Handover
  -> Jarvis generates final service recap
  -> Advisor confirms final decisions, price, and next steps

After visit
  -> Owner receives app / LINE recap
  -> Feedback and behavior enter the value loop
```

### 4.5 Guardrail Principle

Official TOYOTA / Hotai service information is a hard guardrail.

Jarvis can:
- Summarize.
- Simplify.
- Translate technical language into owner-friendly language.
- Personalize using assumed internal data.

Jarvis cannot:
- Invent final repair prices.
- Invent warranty responsibility.
- Claim live service progress without integration.
- Override service advisor judgment.
- Contradict official service-process materials.

## 5. Feature Set

### 5.1 MVP Features

#### Feature 1: Voice-First Owner Assistant

Purpose:
- Let owners ask service questions by voice and receive voice + text responses.

Core functions:
- Voice input.
- Voice output.
- Text summary.
- All-age accessible UI.
- Simple action buttons for app / LINE continuation.

Value:
- Reduces cognitive load.
- Helps older users or stressed users.
- Avoids deep menu navigation.

#### Feature 2: Service Advisor Copilot

Purpose:
- Help advisors explain service items faster and more consistently.

Core functions:
- Owner context card.
- Maintenance history summary.
- Current visit purpose summary.
- Plain-language service explanation.
- Likely customer questions.
- Suggested explanation script.

Value:
- Shortens reception explanation time.
- Reduces repeated questions.
- Standardizes communication quality.

#### Feature 3: Customer Lounge AI Experience

Purpose:
- Turn waiting time into a transparent, useful, personalized experience.

Core functions:
- Service stage explanation.
- Waiting progress card.
- "What is being checked now?" explanation.
- Personalized car-care tips.
- Follow-up Q&A.
- App / LINE interaction prompts.

Value:
- Makes waiting less passive.
- Improves trust and perceived transparency.
- Creates a memorable peak experience.

#### Feature 4: Official Knowledge Guardrail

Purpose:
- Prevent hallucination and unsafe operational claims.

Core functions:
- Service-process grounding.
- Official material citation when available.
- Claim classification: official fact / assumption / AI suggestion.
- Inspector agent rejection for unsupported claims.

Value:
- Keeps AI operationally safe.
- Makes the solution credible for a real dealership environment.

#### Feature 5: Value Loop Analytics

Purpose:
- Turn after-sales interactions into measurable service-improvement signals.

Core functions:
- Interaction log.
- Repeated-question tracking.
- NPS / satisfaction feedback capture.
- Return-service intent tracking.
- App / LINE interaction tracking.

Value:
- Converts experience improvement into measurable ROI.
- Creates a feedback loop for continuous optimization.

### 5.2 Extension Features

- Accident / urgent repair routing back to official service channels.
- Predictive maintenance nudges from vehicle driving data.
- CRM integration.
- Live parts and service-bay availability.
- Official LINE advanced flow integration.
- Multi-language support.
- Service advisor quality dashboard.

## 6. System Architecture

### 6.1 Logical Architecture

```text
Frontend
  -> Owner voice/chat UI
  -> Advisor dashboard
  -> Customer lounge display / kiosk

Backend API
  -> Authentication and consent
  -> Session and case state

AI Layer
  -> Context Builder
  -> Service Explanation Agent
  -> Lounge Experience Agent
  -> Inspector / Guardrail Agent
  -> Value Loop Analyzer

Tool Layer
  -> Service Flow Tool
  -> Official Knowledge Search
  -> Owner History Tool
  -> Vehicle Data Tool
  -> App / LINE Interaction Tool
  -> Metrics Logger

Data Layer
  -> Official service materials
  -> Owner maintenance history
  -> Vehicle driving data
  -> App / LINE interaction behavior
  -> Public-opinion analysis dataset
```

### 6.2 Data Sources

Provided:
- `TOYOTA回廠服務流程手冊.pdf`
- `附件_LINE預約操作說明.jpg`

Assumed internal:
- 車主歷史保養紀錄。
- 車輛行車數據。
- APP / LINE 互動行為數據。

To collect:
- Public TOYOTA service-center discussion data.
- Interview notes.
- Service-flow observation notes.

### 6.3 Data Status

Current repo artifacts:
- `data/raw/toyota_after_sales_competition_data.7z`
- `data/extracted/toyota_after_sales/`
- `data/processed/toyota_after_sales/`

Current limitation:
- PDF text extraction is limited because the source appears diagram-heavy.
- LINE operation image likely needs OCR or manual extraction.

## 7. Tech Stack

### 7.1 Recommended MVP Stack

Frontend:
- React / Next.js for web prototype.
- Tailwind CSS for fast UI iteration.
- Browser Web Speech API for demo-grade STT/TTS if acceptable.
- Alternative voice stack: Whisper API for STT and OpenAI TTS for voice output.

Backend:
- Python FastAPI.
- Pydantic schemas for typed case/session/tool outputs.
- SQLite for local prototype state.
- PostgreSQL for deployable pilot.

AI / Agent Layer:
- OpenAI Responses API or equivalent LLM API.
- Structured tool calling for service-flow and owner-context tools.
- Lightweight manual search over extracted official materials.
- Guardrail inspector using deterministic checks + LLM review.

Data / Search:
- JSON / YAML structured service-flow rules for MVP.
- Local keyword search for official snippets.
- Vector DB only if document volume grows.

Integrations:
- App / LINE handoff simulated in prototype.
- Future LINE Messaging API integration.
- Future CRM / service system integration.
- Metrics logging for repeated questions, interaction rate, and satisfaction.

Deployment:
- Docker for backend packaging.
- Vercel or similar for frontend prototype.
- Render / Fly.io / cloud VM for demo backend.
- Future on-prem or private cloud deployment if data security requires.

### 7.2 Why Not Full RAG First

The initial provided materials are small and process-oriented. The first value should come from:

- Structured workflow states.
- Explanation templates.
- Guardrails.
- Advisor/owner experience design.

Full vector RAG becomes useful later when the document set includes:
- Maintenance manuals.
- Service SOPs.
- Warranty rules.
- FAQ.
- Historical service Q&A.
- Model-specific repair information.

## 8. Cost Model

### 8.1 Report Baseline

The current report uses the following working assumptions:

- Annual total operating cost: **NT$ 400 萬 / year**.
- API / token cost range after prompt engineering and token optimization: **NT$ 3 萬 - 30 萬 / year**.
- Remaining cost covers development, integration, maintenance, governance, and personnel allocation.

### 8.2 Cost Breakdown For PPT

Use this as proposal-level structure:

| Cost Item | Annual Estimate | Notes |
| --- | ---: | --- |
| LLM / STT / TTS API | NT$ 3 萬 - 30 萬 | Report assumption; depends on usage and model choice. |
| Cloud / storage / logging | TBD | Needs deployment sizing. |
| Integration and data pipeline | TBD | Depends on internal systems and LINE/app integration. |
| Security / privacy / governance | TBD | Required for real owner and vehicle data. |
| Product maintenance and operations | Included in annual model | Part of NT$ 400 萬 total assumption. |
| Total annual operating model | NT$ 400 萬 | Current report baseline. |

### 8.3 Cost Guardrail

For the proposal deck, state:

- Cost model is a working estimate.
- API cost is controllable through prompt engineering, caching, smaller models for classification, and structured tools.
- Real deployment cost depends on traffic, integration scope, data governance, and voice usage.

## 9. ROI Model

### 9.1 Current Report ROI

The current report estimates ROI from two value sources:

1. 過保車主回流效益。
2. 事故 / 保修引流回原廠效益。

### 9.2 Scenario 1: Over-Warranty Owner Return

Working assumptions from report:

- Connected member base: 360,000.
- Over-warranty owner target: 108,000.
- Incremental return visits used in report: 10,800.
- Average service revenue per visit: NT$ 12,000.
- Gross margin: 45%.

Calculation:

```text
10,800 visits x NT$ 12,000 x 45%
= NT$ 58.32 million gross profit
```

### 9.3 Scenario 2: Accident / Service Case Routing

Working assumptions from report:

- Annual accident/service opportunity rate: 1% of 360,000 = 3,600 cases.
- Incremental official-channel routing uplift: 30% = 1,080 cases.
- Average body/paint or repair value: NT$ 50,000.
- Gross margin: 50%.

Calculation:

```text
1,080 cases x NT$ 50,000 x 50%
= NT$ 27.00 million gross profit
```

### 9.4 Combined ROI

```text
Annual gross profit uplift:
NT$ 58.32 million + NT$ 27.00 million
= NT$ 85.32 million

Annual operating cost:
NT$ 4.00 million

Net benefit:
NT$ 85.32 million - NT$ 4.00 million
= NT$ 81.32 million

ROI:
NT$ 81.32 million / NT$ 4.00 million
= 20.33x
= 2,033%
```

### 9.5 ROI Validation Notes

Important for the slide deck:

- Treat 2,033% as a **working ROI scenario**, not a verified actual result.
- The report says "回流率提升 3%" and also uses "新增 10,800 輛次"; this needs validation because 3% of 108,000 is 3,240, while 10,800 equals 10% of 108,000 or 3% of 360,000.
- Keep the financial slide transparent by labeling assumptions clearly.
- A sensitivity table should be added if time permits.

### 9.6 Suggested Sensitivity Table

| Incremental Return Visits | Return Gross Profit | Accident Routing Profit | Total Gross Profit | Cost | ROI |
| ---: | ---: | ---: | ---: | ---: | ---: |
| 3,240 | NT$ 17.50M | NT$ 27.00M | NT$ 44.50M | NT$ 4.00M | 1,013% |
| 5,400 | NT$ 29.16M | NT$ 27.00M | NT$ 56.16M | NT$ 4.00M | 1,304% |
| 10,800 | NT$ 58.32M | NT$ 27.00M | NT$ 85.32M | NT$ 4.00M | 2,033% |

## 10. Success Metrics

### Experience Metrics

- Service-item comprehension score.
- Customer satisfaction score.
- NPS change after service visit.
- Perceived transparency score.
- Return-service intention.

### Operational Metrics

- Average reception explanation time.
- Repeated-question rate.
- Advisor preparation time.
- Service handover explanation time.
- Customer lounge interaction completion rate.

### Digital Metrics

- App / LINE interaction rate.
- Voice interaction completion rate.
- Post-visit recap open rate.
- Follow-up Q&A rate.

### Business Metrics

- Over-warranty return rate.
- Official-channel routing rate for service/repair cases.
- Incremental service gross profit.
- Retention uplift.
- Cost per AI-assisted service interaction.

## 11. Prototype Scope

### MVP Demo

Build a split experience:

1. Advisor view:
   - Owner context card.
   - Visit summary.
   - Plain-language explanation script.
   - Likely questions and recommended answers.

2. Owner / lounge view:
   - Voice or chat interaction.
   - Service stage explanation.
   - Personalized car-care card.
   - Final recap preview.

3. Guardrail trace:
   - Shows official / assumed / AI-generated distinction.
   - Flags items requiring service advisor confirmation.

### Demo Scenario

Recommended first scenario:

```text
Owner returns for scheduled maintenance.
System reads assumed maintenance history and current visit.
Advisor receives a concise explanation script.
Owner waits in lounge and asks Jarvis why a service item matters.
Jarvis answers in plain language with voice + text.
Before handover, Jarvis generates a recap and next-care suggestions.
```

## 12. Landing Plan

### Phase 1: Proposal Prototype

- Extract service-flow states from provided materials.
- Build mock owner data.
- Build advisor and owner UI.
- Implement scripted Jarvis agent flow.
- Add guardrail trace.

### Phase 2: Pilot Design

- Validate with interviews or simulated service scenarios.
- Add public-opinion analysis.
- Define measurable baseline metrics.
- Refine service scripts.

### Phase 3: Controlled Service-Center Pilot

- Integrate with limited service records.
- Use approved service materials.
- Capture interaction and satisfaction metrics.

### Phase 4: Scale

- Integrate app / LINE.
- Add voice stack at production quality.
- Add predictive maintenance and retention analytics.
- Build dashboard for service managers.

## 13. Slide Deck Structure

Use this structure for PPT generation:

1. Title: Jarvis計畫 / TOYOTA 售後服務 AI 再造。
2. Proposal Summary.
3. Strategic Context: after-sales as retention and profit engine.
4. Pain Points: owner, advisor, business.
5. Product Concept: Jarvis voice-first after-sales AI agent.
6. User Journey: before visit, reception, lounge, handover, after visit.
7. Feature Set: advisor copilot, lounge AI, voice assistant, guardrails, analytics.
8. Tech Architecture and Stack.
9. Data Strategy and Responsible AI Guardrails.
10. Cost Model.
11. ROI Model and Sensitivity.
12. Expected Benefits and KPIs.
13. Landing Roadmap.
14. Demo / Prototype Plan.
15. References and Appendix.

## 14. Open Items Before Final PPT

- Validate ROI assumptions and the 3% vs 10,800-visit calculation.
- Decide final product name.
- Extract structured service-flow stages from the PDF and LINE image.
- Add public-opinion findings.
- Decide prototype UI style.
- Decide whether voice demo uses browser STT/TTS or external API.
- Add source references for financial and NPS claims.

