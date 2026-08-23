# Data Inventory

## Current Competition Data

The active reference archive has been copied into the repo:

- Raw archive: `data/raw/toyota_after_sales_competition_data.7z`
- Extracted folder: `data/extracted/toyota_after_sales/`
- Processed folder: `data/processed/toyota_after_sales/`

## Extracted Contents

The archive contains:

- `TOYOTA回廠服務流程手冊.pdf`
- `附件_LINE預約操作說明.jpg`

## Processed Artifacts

- `data/processed/toyota_after_sales/toyota_return_service_process_manual.txt`
- `data/processed/toyota_after_sales/toyota_return_service_process_manual.pages.jsonl`
- `data/processed/toyota_after_sales/manifest.json`

PDF extraction summary:
- Page count: 11
- Extracted text characters: about 1.3k
- Note: text extraction is limited because the source appears process/diagram-heavy. OCR or manual structure extraction may be needed.

Image reference:
- `附件_LINE預約操作說明.jpg`
- Size: 10000 x 4677
- Likely requires OCR or manual review to extract reservation steps.

## What This Data Can Support

### 1. Service Flow Grounding

The return-service process manual can support:
- Mapping the official return-service journey.
- Identifying reception, waiting, inspection, explanation, and handover stages.
- Designing advisor and owner touchpoints around the existing flow.

### 2. LINE Reservation Journey Understanding

The LINE operation image can support:
- Understanding current reservation UX.
- Identifying friction in app / LINE interaction.
- Designing future AI-assisted reservation and pre-visit preparation.

### 3. Proposal Guardrails

The provided materials should act as official or semi-official reference points for:
- Service-process sequence.
- Reservation interaction assumptions.
- What the AI should avoid contradicting.

## Data Still Needed

For pain-point analysis:
- Public online discussions about TOYOTA service-center experiences.
- Review comments, forum posts, article comments, or social posts.
- Interview notes or simulated interview transcripts.
- Service-flow observation notes.

For personalization design:
- Mock owner maintenance history.
- Mock vehicle driving data.
- Mock app / LINE interaction behavior.
- Mock current visit record.

For benefit estimation:
- Assumptions for reception explanation time.
- Repeated-question rate.
- Customer satisfaction baseline.
- App / LINE interaction rate.
- Return-service intention or retention proxy.

## Product Direction Impact

The active data pushes the proposal toward an after-sales service experience platform:

1. Advisor explanation support.
2. Customer lounge waiting experience.
3. App / LINE service communication.
4. Personalized recap and next-care recommendations.

