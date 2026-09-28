# CLAUDE.md

## Project goal

Split OECD ICIO industry **D26 "Computer, electronic and optical equipment"** (ISIC Rev.4 div. 26) into
**261S Semiconductors** and **26X ICT & electronics excl. semiconductors**, following Annex A of
Haramboure, Lalanne, Schwellnus & Guilhoto (2023), *Vulnerabilities in the semiconductor supply chain*,
OECD STI WP 2023/05, doi:10.1787/6bed616f-en.

Current phase: **understand every derivation in Annex A** before writing code.

## Files

| Path | What |
|---|---|
| `doc/6bed616f-en.pdf` | Original paper (Read tool reports "password-protected"; pypdf reads it fine) |
| `doc/haramboure_raw.txt` | pypdf text dump, page-marked. Math sub/superscripts garbled |
| `doc/haramboure2023_annexA.md` | Clean Annex A transcription, equations in LaTeX, labelled (A.1)-(A.13). Not yet verified against page images |
| `doc/guide/annexA_guide.tex` | Step-by-step LaTeX guide to Annex A (derivations, worked RAS example, ambiguities, algorithm) |

Compile guide: `pdflatex annexA_guide.tex` (TeX Live 2023 at `C:/texlive/2023`). Run twice for TOC/refs.

## Data available

- OECD ICIO tables.
- National IO tables for the reference economies **except Malaysia** (paper uses KOR 2014, JPN 2011,
  MYS 2010, TWN 2016, USA 2012). Missing MYS matters: paper maps China <- Malaysia, "other economies" <-
  mean(JPN, KOR, MYS, TWN). See guide, Ambiguity "No Malaysian table".
- Trade: paper uses OECD BTDIxE, HS 8541 + 8542 (not yet obtained).

## Method in brief (details in guide)

1. Domestic blocks, reference economies: base-year row shares `sigma_j = a0[261S,j]/a0[26,j]`, column
   ratios `rho_i = a0[i,k]/a0[i,26]`, applied to ICIO coefficients of every year (A.1).
2. Domestic blocks, other economies: averaged ratios from mapped reference economies.
3. Import columns: buyer's domestic column ratios (A.2).
4. Import rows: init with buyer's domestic row shares (A.3), RAS per (r,s) pair so semis row sums to
   bilateral trade `M[r,s]` and each column sums to ICIO `Z[r,s][26,j]` (A.4-A.9), back to coefficients (A.10).
5. Final demand for 261S = 0; `X = (I-A)^-1 y`, `Z = A diag(X)`, `V = 1 - colsum(A)` (A.11-A.13).

Key algebra: row splits are shares (sum to 1); column splits are relative intensities whose
output-weighted average is 1 (weight `w = X_261S / X_26`). Most paper ambiguities come from this.

## Known issues in the paper (resolutions in guide)

- (A.2) typo: 26X equation has `a[i,26X]` on RHS; should be `a[i,26]`.
- RAS iteration index `i` clashes with industry index.
- 26X row target in RAS unstated; implied `sum_j Z[26,j] - M_261S`.
- Order of column vs row split for import blocks; recommended row split first.
- Averaging column ratios across economies breaks aggregation; average flow shares instead.
- Recomputed X can deviate from published ICIO when model output share differs from base-year share.

## Conventions

- Notation follows guide: `a^{r,s}_{i,j}`, r/s = origin/destination, i/j = supplying/purchasing industry.
- Language for code: not yet decided (ask before starting).
- Every numerical step must end with checks: non-negativity, aggregation back to original D26, row/column
  identities, trade match.
- Do not modify raw data.
