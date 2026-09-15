# Audit — 2026-09-14 (eseguito 2026-09-15 20:39)
I cinque: NUTX · APPS · APP · CVNA · DAVE. Esito: 18 PASS, 2 WARN, 1 FAIL.

## Freschezza
- **FAIL** `A1-S&P 1500` ultimo prezzo S&P 1500 — 2026-09-04, 6 sedute fa
- **PASS** `A1-small cap` ultimo prezzo small cap — 2026-09-11, 1 sedute fa
- **PASS** `A1-ACWI` ultimo prezzo ACWI — 2026-09-11, 1 sedute fa
- **PASS** `A2` calendari utili (ultimo aggiornamento file) — 2026-09-14, 0 giorni fa
- **PASS** `A3` bundle della pagina — generato 2026-09-14, 0 giorni fa

## Prezzi
- **PASS** `B1` buchi nelle ultime 252 sedute (cinque + primi 40) — 43 nomi; con piu' di 5 giorni mancanti: nessuno
- **PASS** `B2` salti giornalieri oltre il 60% fra gli ammessi — nessuno (filtro |mossa| <= 60%)
- **PASS** `B3` seconda fonte prezzi (storico Nasdaq): max |differenza rendimento giornaliero| ultime 20 sedute — max 0.0000 su 9 nomi; non verificabili: nessuno

## Calendari
- **PASS** `C1` prossima data nei file = prossima data usata dal motore (ammessi) — 1528 nomi; incoerenti: nessuno
- **WARN** `C2` seconda fonte date (calendario Nasdaq) — nomi ammessi — 1020 uguali, 51 assenti su Nasdaq, 457 diverse su 1528; i cinque: {'NUTX': 'assente su Nasdaq', 'APPS': 'uguale', 'APP': 'uguale', 'CVNA': 'diversa (2026-10-28 yahoo vs 2026-11-04 nasdaq)', 'DAVE': 'diversa (2026-11-04 yahoo vs 2026-11-03 nasdaq)'}; le date diverse restano dentro la finestra: da confermare sul terminale
- **PASS** `C3` date storiche Yahoo vs 8-K item 2.02 su EDGAR (ultime 12, tolleranza ±1 giorno) — i cinque — copertura per nome: {'NUTX': '12/12', 'APPS': '12/12', 'APP': '12/12', 'CVNA': '12/12', 'DAVE': '12/12'}

## Ricalcolo
- **PASS** `D1` beta, s_ord, s_ann, sigma finestra ricalcolati da zero per 43 nomi vs motore — max differenza relativa 0.000% (LUNR/s_ann 0.00%, RGTI/beta 0.00%, KEEL/s_ann 0.00%, EOSE/beta 0.00%, RGTI/s_ann 0.00%)
- **PASS** `D2` correlazioni residue dei cinque, indipendenti vs motore — max |differenza| 0.0000; corr max fuori diagonale 0.294
- **PASS** `D3` sigma del libro e P(1°) dei cinque, ricalcolati vs report — sigma 13.51% (report 13.51%), mu +0.75%, P(1°) 15.43% (report 15.43%)
- **PASS** `D4` vincoli del report sui cinque (beta<=2, corr<=0.35, dentro, n>=13, ADV>=10M, cap>=1.2B, |mossa|<=60%) — tutti rispettati — beta medio 1.81, corr max 0.29
- **PASS** `D5` il giorno di reazione porta varianza (|residuo| reazione / mediana ordinaria, ultime 252) — {'NUTX': 5.5, 'APPS': 9.2, 'APP': 5.7, 'CVNA': 4.1, 'DAVE': 3.7}

## Bundle
- **PASS** `E1` candidati: numerici presenti per gli ammessi, tutti i preset nel bundle — 2432 candidati, 1528 ammessi; nulli: nessuno
- **PASS** `E2` residui nel bundle (1000 nomi × 252 sedute): correlazioni dei cinque ricalcolate dal bundle = motore — max |differenza| 0.0001
- **PASS** `E3` quantili del campo monotoni; barra (mediana del massimo) fra 12% e 18% — mediana 14.4%, 400 quantili
- **PASS** `E4` sigma dei cinque nel bundle = motore — coerenti
- **WARN** `E5` dati incorporati in index.html = dati.json — diversi: ricostruire la pagina
