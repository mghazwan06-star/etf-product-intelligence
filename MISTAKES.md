# Mistake Log

Record every error, what caused it, how it was caught, and the fix.

| Date | Phase | Mistake | How caught | Fix |
|---|---|---|---|---|
| 2026-11-05 | 1 | First attempt to read issuer fund lists returned almost nothing | Results were near empty (2 funds) | Lists are built by JavaScript; switched to reading them in a real browser |
| 2026-11-05 | 1 | Adding a search word to the Amundi list address did nothing; the list came back unfiltered | Results included S&P 500 and bond funds | Read the whole list and filtered it ourselves |
| 2026-11-05 | 1 | Fund classifier counted "FTSE All-World ex-US" as a core fund (rule missed the spelling "ex-US") and counted an active "Enhanced" fund under MSCI ACWI | Listed every fund marked core and read the names | Fixed the rule, re-ran; core count went from 19 to 17 |
| 2026-11-05 | 1 | Funds-per-index chart cut off the longest label and said "1 variants" | Looked at the rendered chart | Widened the right margin, fixed the plural |
| 2026-11-06 | 2 | First download of the iShares MSCI World (IWRD) factsheet saved an 87-byte error message as a .pdf | Checked file types after downloading | Deleted it and downloaded again; now a real 4-page PDF |
| 2026-11-06 | 2 | Invesco downloads left 4 empty .pdf files after the site refused them | Checked file types after downloading | Deleted the empty files; marked the 4 documents as to save from the browser |
| 2026-11-06 | 3 | Tried to read only the first pages of each factsheet; the page-range option needs a tool that isn't installed | Error on the first try | Read each factsheet in full instead (4 pages each) |
