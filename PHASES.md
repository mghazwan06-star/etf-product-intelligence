# Phases

Six phases. I review the results at the end of each one before starting the next.

## 1. Choose the universe

Find out which global equity indices have enough UCITS ETFs to compare. I fill in `data/index_survey.csv` by hand from issuer websites (iShares, Vanguard, Xtrackers, Amundi, SPDR and others), checking each site's terms first. Then I count funds per index, chart it, and pick the index scope and the final 12 to 15 funds. The inclusion rule gets written down in DECISIONS.md.

Output: survey sheet and a funds-per-index chart.

## 2. Collect the documents

Download the factsheet and key document (KID/KIID) for each chosen fund, where the terms allow it. Files are named by ISIN and date accessed. The PDFs stay on my machine. Only the extracted figures go in the repo, with the source link and access date.

Output: a tracker showing which documents I have and which are missing.

## 3. AI extraction and accuracy check

An AI tool reads each document and pulls out the annual fee, index, fund size and replication method. The raw output is saved unchanged. I then read 10 funds myself and record the right values before looking at what the tool said. The accuracy figure is reported as the number of fields correct out of the number checked, for those 10 funds only.

Output: extracted dataset and an accuracy table.

## 4. Reconcile factsheet and key document

Compare the two documents for each fund on fee, size and index name. List every mismatch with both values and dates, work out why each one differs (timing, rounding, error, definition) and decide which value to use. After this the dataset is frozen. Any later change gets a log entry.

Output: mismatch table and a heatmap.

## 5. Analysis

Excel workbook with live formulas, plus SQL queries on the same data. Fees against fund size, fee ranking, and tracking difference if I can find a legitimate source of index return data. I'll settle that source and its terms before starting this phase. If there isn't one, tracking difference gets dropped and I'll say so in the brief.

Output: charts and the three or four findings the brief will lead with.

## 6. Product view and write-up

A break-even model for a possible new fund, with three scenarios. Launch size, fee, running costs and growth are all assumptions and are labelled that way. Then a gap map, the two-page brief, the Excel model and a short deck.

Output: brief (PDF), Excel model, deck.

## Open decisions

- Index scope (phase 1)
- Source for index returns (phase 5)
