# Progress

Single source of truth for where this project stands. Updated at the end of every step.

Last updated: 2026-11-06

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
- D-003 / D-008: index scope is MSCI World, MSCI ACWI and FTSE All-World
- D-004: six gated phases; source PDFs are not committed to the repo
- D-005: raw collected data stays local; the repo publishes analysis only
- D-006: SPDR's UK site excluded (professionals only)
- D-007: never read behind a terms box without accepting it
- D-009: inclusion rule (plain index, no tilts, not hedged-only)
- D-010: one share class per fund, chosen by a fixed rule
- D-011: tracking difference from issuer calendar-year tables, our own calculation
- D-012: Xtrackers figures flagged before any public use
- D-013: source PDFs kept locally in data/docs; files a site won't serve to a script get saved from the browser
- D-014: no Vanguard factsheet on its UK investor site; product page figures stand in for it
- D-015: fund size is taken from factsheets only, since key documents don't report it
- D-016: the hand check is written into data/extraction/hand_check.csv with the tool column left empty until the hand values are in

## Current position

Phase 1 is done. Phase 2 is half done: 13 of 28 documents saved, 14 still to save from the browser, 1 not published. Phase 3 has started: the extraction has run on the 13 saved documents.

What the survey found (5 Nov 2026):
- 79 global equity UCITS ETFs (125 share classes) on the UK sites of iShares, Vanguard, Xtrackers and Invesco.
- 17 of them are plain broad-index funds. The rest are ESG, factor, sector, size or regional versions.
- MSCI World is by far the most crowded index (7 core funds, 43 variants). MSCI ACWI has 3 core funds, FTSE All-World 4.
- Amundi and HSBC show no broad global ETF on their UK individual-investor lists. SPDR's UK site is for professionals only.
- Final comparison set: 14 funds across 3 indices and 4 issuers (list kept locally in data/final_funds.csv).
- Chart: charts/funds_per_index.svg

Early signals worth testing later (not findings yet, nothing checked against key documents):
- Fees for the same MSCI World index range widely across funds and even across share classes of one fund.
- Swap-based funds appear to have beaten their index in recent years on issuer pages.
- Issuer pages give fund vs index returns at different precision (0.1 vs 0.01 points), which limits tracking difference accuracy.
- One issuer page shows a listing date earlier than the fund's launch date. A candidate for the Phase 4 mismatch list.

Spot-check (6 Nov 2026): 5 random survey rows checked against the live issuer pages. All 5 fees match. One note: the lowest fee shown for the Xtrackers MSCI World Swap fund (0.04%) belongs to unlisted institutional classes, not something a UK individual can buy on an exchange. It doesn't affect the chosen share class.

Documents (6 Nov 2026), tracked in data/doc_tracker.csv:
- iShares: all 6 funds, factsheet and KID saved (12 files).
- Vanguard: KIID saved. No factsheet on the UK investor site.
- Xtrackers (5 funds): documents sit behind download buttons with no plain link. To save from the browser.
- Invesco (2 funds): the site refuses non-browser downloads. To save from the browser.

Extraction (6 Nov 2026): prompt fixed in method/extraction_prompt.md. Run once on each of the 13 saved documents. Raw output in data/extraction/raw/ (one file per document), flattened into data/extraction/extracted.csv. Nothing has been checked against it yet.

Things noticed while the documents were read (to test in Phase 4, not findings yet):
- Index names are written differently between a fund's two documents, and sometimes inside one document (with and without "Net", "ACWI" vs "All Country World").
- One iShares factsheet says the fund holds the index securities "in similar proportions" on the same page that labels the method "Optimised".
- The two iShares swap funds list the index itself as a top holding at close to 100%, so their top 10 adds up to well over 100%.
- Factsheets give calendar-year fund and index returns to two decimals; key documents give them to one. The factsheet tables are the better source for tracking difference.
- Key documents carry dates from February to October 2026, so some are nine months older than the factsheets.

**Next action:** save the 14 Xtrackers and Invesco files from the browser into data/docs, named ISIN_type_YYYY-MM-DD.pdf, and mark them in data/doc_tracker.csv. Then run the same prompt on them.

**After that:** pick the 10 funds for the hand check and fill data/extraction/hand_check.csv by reading the PDFs, before opening the tool output.

## Checklist

### Setup
- [x] Folder, logs and repo created
- [x] Phased plan written (PHASES.md)

### Phase 1: Choose the universe
- [x] Survey collected: 79 funds, 125 share classes, 4 issuers (data/survey_funds.csv)
- [x] Terms of use noted for every issuer site (data/terms_notes.md)
- [x] Funds-per-index bar chart made (charts/funds_per_index.svg)
- [x] Index scope decided (D-008)
- [x] Inclusion rule written (D-009, D-010)
- [x] Final list of 14 funds (data/final_funds.csv)
- [x] Spot-check of 5 random survey rows (all fees match)

### Phase 2: Collect the documents
- [x] PDFs stored locally only, not in the repo (D-013)
- [ ] Factsheet saved for each fund (6 of 13 available; Vanguard has none)
- [ ] Key document (KID/KIID) saved for each fund (7 of 14)
- [x] Files named ISIN_type_YYYY-MM-DD
- [x] Tracker made (data/doc_tracker.csv)
- [ ] Tracker complete

### Phase 3: AI extraction and accuracy check
- [x] Fields fixed: annual fee, index, fund size, replication method (plus as-of date for each)
- [x] Extraction prompt written and saved (method/extraction_prompt.md)
- [ ] Extraction run on all documents, raw output saved unchanged (13 of 27 done)
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
- [x] Source for index return data: issuer calendar-year tables (D-011)
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

- Whether any source documents can be stored beyond local use (Phase 2)
- Whether Xtrackers figures can appear in public outputs (D-012)
- How to handle different return precision across issuers (Phase 5)

## Known risks

- Tracking difference: issuer pages give fund vs index returns, but at different precision and over different periods (calendar year vs Nov to Oct). Several funds launched in 2024 to 2026 have one year or less of history.
- Fund sizes are reported in different currencies (USD on iShares, Vanguard, Invesco; GBP on Xtrackers). Must convert before comparing.
- Xtrackers MSCI World Swap II fund size reads "843,696.25" on the list page with no unit, unlike every other row. Check it against the factsheet.
- Survey coverage gaps: Invesco list pages 3 to 6 did not load (funds checked by name instead), UBS ETF page not found, Amundi showed 50 of 53 products.
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
- charts/: public charts
- method/: extraction prompt
- data/ (local only): raw issuer lists, survey, final fund list, return tables, terms notes, build scripts, doc_tracker.csv, docs/ (source PDFs), extraction/ (raw tool output, extracted table, hand-check sheet)

## History

- 2026-10-20: project scoped, repo created, logs set up, Phase 1 template made
- 2026-11-05: phased plan written, this file expanded
- 2026-11-05: 2 iShares rows pre-filled from public pages (to verify by hand); product lists on iShares and Amundi do not load without a browser
- 2026-11-05: 7 Vanguard funds collected; terms gates found on iShares, Xtrackers, Amundi, HSBC, Invesco; SPDR UK excluded
- 2026-11-05: issuer terms checked for five issuers; decided raw data stays local (D-005)
- 2026-11-05: terms accepted on five issuer sites; survey finished (79 funds); chart made; scope, inclusion rule and share class rule set (D-008 to D-012); Phase 1 done pending spot-check
- 2026-11-06: 5 survey rows spot-checked, all fees match; Phase 2 started, 13 documents saved, tracker made (D-013, D-014)
- 2026-11-06: extraction prompt written; extraction run on the 13 saved documents (D-015, D-016)
