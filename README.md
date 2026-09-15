# bloomberg-data

Nightly outputs of the *Boosting the Upside* engine (Bloomberg Global Trading Challenge 2026, Team LUISS).
The shared page reads these files at load time; if this repo is unreachable it falls back to the copy embedded in the page.

- `dati.json` — the bundle: every screened name with σ, drift, dates, filters; daily residuals of the 1,000 most volatile names; field quantiles; sets.
- `audit.json` / `AUDIT.md` — the independent audit (`verifica.py`): recomputation of every number from the raw files, second-source checks (Nasdaq calendar, SEC EDGAR 8-K filings, Nasdaq historical prices).
- `date_nasdaq.json` — next report dates per name from the Nasdaq calendar (second source).

Code, data and protocols live in the private repo `Bloomberg_Challenge_2026`. No API keys, no credentials, nothing here is secret.
