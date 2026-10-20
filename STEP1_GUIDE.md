# Step 1 Guide: Index Survey

Goal: find out which global equity indices have enough UCITS ETFs to compare, so we can decide the index scope (D-003).

You collect this by hand. Nothing is automated in this step.

## Plain-English terms

- **ETF**: a fund you buy on a stock exchange that holds a basket of shares.
- **Index**: the list of shares the ETF is trying to copy (e.g. MSCI World).
- **UCITS**: the EU/UK rulebook for funds sold to ordinary investors.
- **ISIN**: a 12-character code that uniquely identifies a fund. We use it as the fund's ID so we never mix up two funds with similar names.
- **TER / ongoing charge**: the yearly fee, as a % of what you invest.
- **AUM (fund size)**: how much money is in the fund.
- **KID / KIID**: the official short key document every fund must publish.

## What to do

1. For each issuer below, open their public ETF list or search page.
2. **Before copying anything**, find the site's "Terms of use" or "Legal" page. Note in the sheet whether it allows copying by hand for non-commercial research. If it is unclear, write "unclear" and tell me. Do not copy from that site until we decide.
3. Look for ETFs that track a **global** equity index (covers developed and/or emerging markets worldwide). Skip regional (Europe only, US only) and single-country funds.
4. For each fund found, add one row to `data/index_survey.csv`.
5. Do not guess. If a field is missing, leave it blank.

## Issuers to start with

These are starting points only, not a complete or verified list. Add any issuer you find.

iShares, Vanguard, Xtrackers (DWS), Amundi, SPDR (State Street), Invesco, UBS, HSBC, Lyxor (now part of Amundi), L&G, Fidelity.

## Fields in the survey sheet

| Column | What goes in it |
|---|---|
| fund_name | Exactly as written on the issuer page |
| isin | 12-character code |
| issuer | e.g. iShares |
| index_name | The index it says it tracks |
| index_provider | e.g. MSCI, FTSE |
| source_url | Page you got it from |
| date_accessed | Today's date, YYYY-MM-DD |
| terms_checked | yes / no / unclear |
| notes | Anything odd |

## What we do with it

When you have a decent number of rows, tell me. I will count funds per index, make a bar chart, and we pick the scope together. You decide; I advise.
