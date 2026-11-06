# Extraction prompt (Phase 3)

This is the exact prompt given to the AI tool for every document. It is run once per document, factsheet and key document separately. The output is saved as it comes back, before anything is checked or corrected.

## Fields

| Field | What counts |
|---|---|
| isin | The share class ISIN the document is about |
| doc_type | factsheet or kid |
| doc_date | The date the document is dated or "valid as at" |
| fee_pct | Ongoing charges figure or TER, in percent, as printed |
| fee_label | The words the document uses for that fee |
| index_name | The benchmark index name, as printed |
| fund_size | Fund size (whole fund, not share class), as printed |
| fund_size_currency | Currency of the fund size |
| fund_size_date | The date the fund size is given at |
| replication | Replication method, as printed (physical, optimised, sampling, swap, synthetic and so on) |

## Prompt

> You are reading one document about one exchange-traded fund. Extract the fields below. Copy values exactly as printed. Do not calculate, convert, round or guess. If a field is not in the document, return null for it. For every non-null value, also return a short quote from the document that contains it, and the page number.
>
> Fields: isin, doc_type, doc_date, fee_pct, fee_label, index_name, fund_size, fund_size_currency, fund_size_date, replication.
>
> Return JSON only, in this shape:
> {"file": "...", "fields": {"<field>": {"value": ..., "quote": "...", "page": n}}}

## Rules around it

- One run per document. No re-runs to get a better answer. If a run fails, that is logged in MISTAKES.md and run again once.
- Raw output goes to data/extraction/raw/ unchanged, one JSON file per document.
- Ten funds are then read by hand. The hand values are written down before opening the tool output for that fund.
- Accuracy is reported as fields correct out of fields checked, for those ten funds only.
