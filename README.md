# Hotai-AI-hackthon 2026

Team: Jarvis計畫

Active challenge topic: 運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

## Main Goal

Build **Jarvis**, a voice-first after-sales service AI agent that turns TOYOTA service and repair interactions into a measurable customer-retention and revenue-growth loop.

The current main reference is:

- `docs/jarvis-after-sales-voice-agent-report.docx`

## Core Proposal Axis

Jarvis is positioned as an **售後保修智慧代理與全年齡無障礙語音助理**.

The proposal focuses on using GenAI, official service knowledge, and assumed internal vehicle/customer data to:

- Reduce owner cognitive load in maintenance, repair, and urgent service situations.
- Make technical service explanations easier to understand through voice-first interaction.
- Help service advisors communicate more consistently and efficiently.
- Turn after-sales service from a passive cost center into a measurable retention and profit engine.
- Increase over-warranty owner return rate and improve accident/service case routing back to official channels.

## Strategic Thesis

After-sales service is the core loyalty battlefield after vehicle delivery.

Jarvis should create value by removing "認知摩擦" across the service journey:

```text
Vehicle / owner data
  -> AI pattern discovery
  -> Official domain knowledge
  -> Jarvis voice assistant
  -> Worry-free service experience
  -> NPS and service behavior feedback loop
```

## Product Direction

The current solution should combine:

- **Voice-first assistant**: voice input with voice + text output for all-age accessibility.
- **Service advisor copilot**: plain-language explanations, likely customer questions, and communication support.
- **Customer lounge assistant**: transparent service progress, service education, and personalized car-care interaction.
- **Official knowledge guardrails**: AI output must not contradict official TOYOTA / Hotai service information.
- **Value loop analytics**: use interaction, service, and satisfaction data to improve retention and service conversion.

## Data And Knowledge Assumptions

The proposal may reasonably assume access to:

- Owner maintenance history.
- Vehicle driving data.
- App / LINE interaction behavior.
- Official TOYOTA service-process information.
- Public online community discussions and interview / observation notes.

Current imported reference data:

- `data/raw/toyota_after_sales_competition_data.7z`
- `data/extracted/toyota_after_sales/`
- `data/processed/toyota_after_sales/`

## Expected Benefits

Working benefit targets from the current report:

- Shorten service reception explanation time.
- Reduce repeated owner questions.
- Improve owner understanding and trust.
- Increase APP / LINE interaction rate.
- Improve return-service intent.
- Increase over-warranty owner return and official service routing.
- Build a measurable ROI model around retention and service revenue.

Financial numbers such as the report's ROI estimate should be treated as **working assumptions pending validation** until we finish source checking and calculation review.

## Repo Structure

| Folder | Purpose |
| --- | --- |
| `backend/` | Future API, agent workflow, tools, guardrails, and integrations. |
| `frontend/` | Future demo UI and prototype experience. |
| `docs/` | Challenge brief, Jarvis report, planning, proposal draft, guardrails, and system structure. |
| `data/` | Raw, extracted, and processed reference data. |

## Main Documents

- `docs/jarvis-ppt-master-plan.md`
- `docs/jarvis-after-sales-voice-agent-report.docx`
- `docs/challenge-toyota-after-sales-service.md`
- `docs/proposal-working-draft.md`
- `docs/planning.md`
- `docs/system-structure.md`
- `docs/data-inventory.md`
- `docs/guardrails.md`
