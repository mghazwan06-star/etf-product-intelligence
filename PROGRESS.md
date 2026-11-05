# Progress

Single source of truth for where this project stands. Updated at the end of every step.

Last updated: 2026-11-05

## The project

Title: Global Equity ETFs: Fees, Tracking and Product Gaps

Question: among UCITS ETFs that track a global equity index, which give investors good value, and where is there a product gap?

Repo: https://github.com/mghazwan06-star/etf-product-intelligence (public, started 2026-10-20)

Deliverables: a two-page brief, an Excel model, a short deck. A separate portfolio page will also be built for readers.

## Rules

1. Every number comes from real work. No estimates.
2. Public repo: no personal data, no CV, no private notes, no source PDFs, no raw issuer data.
3. Keep this file, DECISIONS.md and MISTAKES.md up to date.
4. Each step is explained in plain English and needs an explicit OK before it starts.
5. Real commit history. Never rewrite or backdate it.
6. Check a source's terms of use before using it. If unclear, ask first.
7. Any assumption in the break-even model is labelled as an assumption.

## Decisions so far

Full detail is in DECISIONS.md.

- D-001: public GitHub with honest history, plus a separate portfolio page
- D-002: universe is UCITS ETFs sold in the UK and EU
- D-003: index scope undecided, to be chosen after the survey
- D-004: six gated phases; source PDFs are not committed to the repo
- D-005: raw collected data stays local; the repo publishes analysis only

## Current position

Phase 1 is in progress. `data/index_survey.csv` has headers only, no rows yet. The data folder is local only and not in the repo (D-005).

**Next action:** fill the survey sheet by hand from issuer sites (iShares, Vanguard, Xtrackers, Amundi, SPDR, Invesco, UBS, HSBC, L&G, Fidelity and others), checking each site's terms first. Aim for roughly 20 to 30 rows across several issuers. Then count funds per index and chart it.

Survey columns: fund_name, isin, issuer, index_name, index_provider, source_url, date_accessed, terms_checked (yes/no/unclear), notes. ISIN is the unique ID. Leave blanks rather than guess.

## Checklist

### Setup
- [x] Folder, logs and repo created
- [x] Phased plan written (PHASES.md)

### Phase 1: Choose the universe
- [ ] Survey rows added to data/index_survey.csv
- [ ] Terms of use noted for every issuer site (iShares, Amundi, SPDR checked 2026-11-05; Vanguard and Xtrackers still to do)
- [ ] Funds-per-index bar chart made
- [ ] Index scope decided (closes D-003)
- [ ] Inclusion rule written in DECISIONS.md (UCITS, replication type, accumulating or distributing, base currency)
- [ ] Final list of 12 to 15 funds, each with ISIN, issuer, index and source URL

### Phase 2: Collect the documents
- [ ] Decide whether PDFs may be stored anywhere (default: local only, not in repo)
- [ ] Factsheet downloaded for each fund
- [ ] Key document (KID/KIID) downloaded for each fund
- [ ] Files named ISIN_type_YYYY-MM-DD
- [ ] Missing-documents tracker complete

### Phase 3: AI extraction and accuracy check
- [ ] Fields fixed: annual fee, index, fund size, replication method (plus as-of date for each)
- [ ] Extraction prompt written and saved
- [ ] Extraction run on all documents, raw output saved unchanged
- [ ] 10 funds read by hand, correct values recorded before looking at the tool output
- [ ] Accuracy table: fields correct out of fields checked, per field
- [ ] Decision on how to handle errors (fix by hand, re-run, or exclude) logged

### Phase 4: Reconcile factsheet and key document
- [ ] Side-by-side comparison on fee, size, index name
- [ ] Every mismatch listed with both values and dates
- [ ] Cause of each mismatch decided (timing, rounding, error, definition)
- [ ] Mismatch heatmap made
- [ ] Dataset frozen; later changes need a log entry

### Phase 5: Analysis
- [ ] Source and terms for index return data agreed (needed for tracking difference)
- [ ] If no legitimate source: tracking difference dropped and the brief says so
- [ ] SQL tables and queries built
- [ ] Excel workbook with live formulas
- [ ] Charts: fee vs fund size, fee ranking, tracking difference (if data allowed)
- [ ] One plain-English sentence per finding; three or four headline findings chosen

### Phase 6: Product view and write-up
- [ ] Assumptions chosen for three scenarios (launch size, fee, running costs, growth)
- [ ] Break-even model built
- [ ] Gap map made
- [ ] Two-page brief written
- [ ] Short deck made
- [ ] Portfolio page built
- [ ] Every number traced to a source row or a labelled assumption
- [ ] Final read-through done

## Open decisions

- Index scope (Phase 1)
- Whether any source documents can be stored beyond local use (Phase 2)
- Source for index returns (Phase 5)

## Known risks

- Tracking difference needs index and fund return data. Key documents only show limited past performance. A legitimate source with workable terms is not yet identified.
- Ten hand-checked funds is a small sample. The accuracy figure must always be quoted with its denominator, never as a general claim.
- "Global equity" covers several different indices (MSCI World, MSCI ACWI, FTSE All-World and others). Mixing them without labelling would make fee comparisons misleading.
- Issuer sites may restrict copying. Terms get checked before any data is taken.

## What can be said on a CV

Only what has actually been done, with real numbers.

- Now: project in progress, scope as described. No figures.
- After Phase 1: number of funds and number of indices surveyed.
- After Phase 3: fields correct out of fields checked, across 10 funds.
- After Phase 4: number of mismatches found.
- After Phase 5: findings as stated in the brief.
- After Phase 6: deliverables complete; break-even results described as scenarios under stated assumptions.

## Files

- README.md: public overview
- PHASES.md: the plan in prose
- PROGRESS.md: this file
- DECISIONS.md: every choice and why
- MISTAKES.md: every error and the fix
- data/ (local only): survey sheet and terms notes

## History

- 2026-10-20: project scoped, repo created, logs set up, Phase 1 template made
- 2026-11-05: phased plan written, this file expanded
- 2026-11-05: 2 iShares rows pre-filled from public pages (to verify by hand); product lists on iShares and Amundi do not load without a browser
- 2026-11-05: issuer terms checked for five issuers; decided raw data stays local (D-005)
