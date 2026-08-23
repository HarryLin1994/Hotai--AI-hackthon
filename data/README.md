# Data

Raw, extracted, and processed data used by the TOYOTA after-sales service proposal.

Current imported data:
- `raw/toyota_after_sales_competition_data.7z`: original TOYOTA after-sales service reference archive.
- `extracted/toyota_after_sales/`: extracted PDF and image reference files.
- `processed/toyota_after_sales/`: extracted text, page-level JSONL, and manifest.

Current data assessment:
- Useful for understanding the return-service process and LINE reservation flow.
- PDF text extraction is limited because the source appears process/diagram-heavy.
- The LINE reservation image likely needs OCR or manual extraction.

Future data categories:
- Public online community discussions.
- Interview notes.
- Service-flow observation notes.
- Mock owner maintenance history.
- Mock vehicle driving data.
- Mock app / LINE interaction behavior.

