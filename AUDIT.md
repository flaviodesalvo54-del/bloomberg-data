# Audit — 2026-09-15 (run 2026-09-15 21:13)
The five: NUTX · APPS · APP · CVNA · DAVE. Result: 19 PASS, 1 WARN, 0 FAIL.

## Freshness
- **PASS** `A1-S&P 1500` last price, S&P 1500 — 2026-09-15, 0 sessions ago
- **PASS** `A1-small cap` last price, small cap — 2026-09-15, 0 sessions ago
- **PASS** `A1-ACWI` last price, ACWI — 2026-09-15, 0 sessions ago
- **PASS** `A2` earnings calendars (file refresh) — 2026-09-15, 0 days ago
- **PASS** `A3` page bundle — generated 2026-09-15, 0 days ago

## Prices
- **PASS** `B1` gaps in the last 252 sessions (the five + top 40) — 43 names; more than 5 missing days: none
- **PASS** `B2` daily moves above 60% among admitted names — none (filter |move| <= 60%)
- **PASS** `B3` second price source (Nasdaq historical): max |daily-return difference| over the last 20 sessions — max 0.0004 across 9 names; not verifiable: none

## Calendars
- **PASS** `C1` next date in the files = next date used by the engine (admitted names) — 1529 names; inconsistent: none
- **WARN** `C2` second calendar source (Nasdaq earnings calendar), admitted names — 1020 same, 52 not on Nasdaq, 457 differ out of 1529; the five: {'NUTX': 'not on Nasdaq', 'APPS': 'same', 'APP': 'same', 'CVNA': 'differs (2026-10-28 Yahoo vs 2026-11-04 Nasdaq)', 'DAVE': 'differs (2026-11-04 Yahoo vs 2026-11-03 Nasdaq)'}; the differing dates stay inside the window: confirm on the terminal
- **PASS** `C3` historical Yahoo dates vs SEC EDGAR 8-K item 2.02 filings (last 12, ±1 day), the five — matched per name: {'NUTX': '12/12', 'APPS': '12/12', 'APP': '12/12', 'CVNA': '12/12', 'DAVE': '12/12'}

## Recomputation
- **PASS** `D1` β, σ ordinary, σ announcement, σ window recomputed from the raw files for 43 names vs the engine — max relative difference 0.000% (GLUE/beta 0.00%, GLUE/s_ann 0.00%, WGS/beta 0.00%, TE/beta 0.00%, IOVA/beta 0.00%)
- **PASS** `D2` residual correlations of the five, independent vs the engine — max |difference| 0.0000; max off-diagonal correlation 0.301
- **PASS** `D3` book σ and P(1st) of the five, recomputed vs the report — σ 13.53% (report 13.53%), drift +0.76%, P(1st) 15.47% (report 15.47%)
- **PASS** `D4` the report's constraints on the five (β<=2, corr<=0.35, inside, n>=13, ADV>=10M, cap>=1.2B, |move|<=60%) — all satisfied; mean β 1.77, max corr 0.30
- **PASS** `D5` the reaction day carries variance (|residual| on reaction days ÷ ordinary median, last 252) — {'NUTX': 5.9, 'APPS': 9.6, 'APP': 5.7, 'CVNA': 4.1, 'DAVE': 3.6}

## Bundle
- **PASS** `E1` candidates: numeric fields present for admitted names, every preset in the bundle — 2434 names, 1529 admitted; nulls: none
- **PASS** `E2` residuals in the bundle (1000 names × 252 sessions): correlations of the five recomputed from the bundle = engine — max |difference| 0.0001
- **PASS** `E3` field quantiles monotone; bar (median of the rivals' maximum) between 12% and 18% — median 14.4%, 400 quantiles
- **PASS** `E4` σ of the five in the bundle = engine — consistent
