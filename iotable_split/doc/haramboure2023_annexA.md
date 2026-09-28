---
title: "Vulnerabilities in the semiconductor supply chain — Annex A (Methodology)"
authors: [Antton Haramboure, Guy Lalanne, Cyrille Schwellnus, Joaquim Guilhoto]
series: OECD Science, Technology and Industry Working Papers, 2023/05
doi: 10.1787/6bed616f-en
source_pdf: doc/6bed616f-en.pdf (pp. 29-32)
transcription_notes: >
  Transcribed from pypdf text extraction (doc/haramboure_raw.txt). Equations re-typeset in LaTeX.
  Figure A A.1 is an image and NOT reproduced. Transcriber notes marked "[TN: ...]".
  Math VERIFIED against page images: NO (pending screenshots of pp. 30-32).
---

# Annex A. Methodology

[TN: Notation: $a^{r,s}_{i,j}$ = input of industry $i$ from economy $r$ per unit output of industry $j$ in
economy $s$; $Z^{r,s}_{i,j}$ = monetary flow. Codes: $26$ = ISIC Rev.4 div. 26 (original), $261S$ =
semiconductors, $26X$ = ICT & electronics excl. semiconductors, $26 = 261S + 26X$. Superscript $(k)$ = RAS
iteration. $t$ = year, $t_0$ = base year.]

This Annex describes how, starting from the ICIO data, a semiconductor-augmented ICIO table can be
estimated. Additional data (granular input-output tables for five economies and bilateral trade flows in
semiconductors) is used to obtain a semiconductor-augmented matrix of technical coefficients. From this
matrix, it is possible to estimate the rest of the semiconductor augmented ICIO data (gross output, flows of
intermediate inputs, value added). Guilhoto, Webb and Yamano (2022) provide an overview of the main ICIO
variables.

## Pre-processing the additional data

### Identifying bilateral trade flows in semiconductors

For each year and each economy pair, bilateral trade flows of semiconductors are obtained from the
'Bilateral Trade in Goods by Industry and End-use Category' database (http://oe.cd/btd). Flows of
semiconductors are identified by Harmonised Systems headings 8541 and 8542.

### Processing national IO tables for economies that provide sufficiently granular information to identify semiconductors

This step relies on granular input-output tables for Korea (2014), Japan (2011), Malaysia (2010), Chinese
Taipei (2016) and the United States (2012). These granular tables are aggregated up to the industry
classification used for ICIO, with the exception of the split between "Semiconductors" and "ICT and
electronics (excluding semiconductors)".

Even though disaggregated national input-output tables are only available for one year, the use of trade
data over the whole period (1995-2018) ensures that the semiconductor-augmented ICIO tables accurately
reflect the growth in semiconductor trade. However, they do not necessarily capture domestic trends.

## Estimating the matrix of technical coefficients

The split is first performed for the matrix of technical coefficients (the $A$ matrix following the notation
of Guilhoto, Webb and Yamano (2022)). For each producing economy, the coefficients for domestic and foreign
uses of 'Computer, electronic and optical equipment' (ISIC rev. 4 division 26) have to be split between uses
of semiconductors (261S) and ICT and electronics excluding semiconductors (26X) – rows in Figure A A.1.
Similarly, for each purchasing economy, the coefficients for domestic and intermediate inputs used by the
'Computer, electronic and optical equipment' have to be split between intermediate inputs purchased by the
semiconductor industry (261S) and those purchased by the ICT and electronics (excluding semiconductors)
industry (26X) – columns in Figure A A.1.

> **Figure A A.1. Estimating a semiconductor-augmented matrix of technical coefficients** —
> [TN: image not reproduced.] Source: OECD.

### Diagonal blocks of the matrix

Estimation of the split for the diagonal blocks of the $A$ matrix proceeds in two steps.

First, for economies for which granular input-output tables are available, diagonal blocks are directly
available for a base year from the pre-processing step described above. For other years, it is assumed that
the shares of the base year can be used to split the technical coefficients of 'Computer, electronic and
optical equipment' (e.g.

$$
{}^{t}a^{r,r}_{261S,j} = {}^{t}a^{r,r}_{26,j} \cdot \frac{{}^{t_0}a^{r,r}_{261S,j}}{{}^{t_0}a^{r,r}_{26,j}}
\quad\text{and}\quad
{}^{t}a^{r,r}_{i,261S} = {}^{t}a^{r,r}_{i,26} \cdot \frac{{}^{t_0}a^{r,r}_{i,261S}}{{}^{t_0}a^{r,r}_{i,26}}
\tag{A.1}
$$

where $t_0$ is the base year).

Second, for the rest of the economies, domestic technical coefficients are obtained as a linear combination
of domestic technical coefficients in these five economies. The following rules, based on a literature
review of their role in the semiconductor value chain (BCG and SIA, 2021; The White House, 2021; Institut
Montaigne, 2022; Abad et al., 2015; Kleinhans and Baisakova, 2020), have been applied:

- China is assumed to have the same domestic technical coefficients as Malaysia.
- Singapore is assumed to have domestic technical coefficients calculated as the average between those of
  Korea and Chinese Taipei.
- European Union member states are assumed to have domestic technical coefficients calculated as the
  average between those of Japan and the United States.
- Other economies are assumed to have domestic technical coefficients calculated as the average between
  those of Japan, Korea, Malaysia and Chinese Taipei.

At this stage, the methodology gives the diagonal blocks of the $A$ matrix. Omitting time indices, domestic
purchases of 'semiconductors' and 'ICT & electronics (excluding semiconductors)' products ($a^{r,r}_{261S,j}$
and $a^{r,r}_{26X,j}$) are available for each purchasing industry $j$ and economy $r$. In addition, domestic
purchases of 'semiconductors' and 'ICT & electronics (excluding semiconductors)' industries
($a^{r,r}_{i,261S}$ and $a^{r,r}_{i,26X}$) are available for each input $i$ and economy $r$.

### Off-diagonal blocks of the A matrix

The next step of the methodology aims at imputing the off-diagonal blocks of the $A$ matrix using trade data
and the diagonal blocks obtained in the previous step. The step can be decomposed into dealing with two
different questions: 1/ How to allocate imported inputs between the 'semiconductors' and 'ICT and
electronics (excluding semiconductors)' industries? and 2/ How to allocate imported 'semiconductors' and
'ICT and electronics (excluding semiconductors)' goods across domestic industries?

#### How to allocate imported inputs between the 'semiconductors' and 'ICT and electronics (excluding semiconductor)' industries?

This first step corresponds to splitting the columns in Figure A A.1. It requires calculating the
coefficients $a^{r,s}_{i,261S}$ and $a^{r,s}_{i,26X}$ for each producing industry $i$, economy of origin $r$
and economy of destination $s$ (with $r \neq s$).

To this end, imported intermediate inputs of product $i$ in economy $s$ are split between the two
sub-industries using the shares observed for domestic inputs of product $i$ in economy $s$:

$$
a^{r,s}_{i,261S} = a^{r,s}_{i,26} \cdot \frac{a^{s,s}_{i,261S}}{a^{s,s}_{i,26}}
\quad\text{and}\quad
a^{r,s}_{i,26X} = a^{r,s}_{i,26X} \cdot \frac{a^{s,s}_{i,26X}}{a^{s,s}_{i,26}},
\qquad \forall\, i, r, s,\ r \neq s
\tag{A.2}
$$

[TN: as printed. RHS factor $a^{r,s}_{i,26X}$ in the second equation is presumably a typo for
$a^{r,s}_{i,26}$. First numerator printed with lowercase "261s".]

#### How to allocate imported semiconductors across domestic industries?

This second step corresponds to splitting the rows in Figure A A.1. It requires calculating the coefficients
$a^{r,s}_{261S,j}$ and $a^{r,s}_{26X,j}$ for each importing industry $j$, economy of origin $r$ and economy
of destination $s$ (with $r \neq s$).

This estimation consists of three stages: 1/ estimating initial auxiliary values of intermediate flows in
monetary terms (the $Z$ matrix following the notations of Guilhoto, Webb and Yamano (2022) – here
$\tilde{Z}$ to indicate that it is an auxiliary matrix used in this step, whereas the final $Z$ matrix will be
calculated further down the line), 2/ balancing these auxiliary values to match trade data on
semiconductors and 3/ calculating the technical coefficients, based on the auxiliary values.

**Stage 1.** To initialise imports of semiconductors in purchasing industry $j$, it is assumed that the share
of semiconductors among computer and electronics inputs is the same for domestic and imported goods:

$$
Z^{r,s\,(0)}_{261S,j} = \frac{a^{s,s}_{261S,j}}{a^{s,s}_{26,j}} \cdot Z^{r,s}_{26,j}
\quad\text{and}\quad
Z^{r,s\,(0)}_{26X,j} = Z^{r,s}_{26,j} - Z^{r,s\,(0)}_{261S,j}
\tag{A.3}
$$

At this stage, there is no guarantee that the $Z^{(0)}$ matrix is consistent with trade flows. In particular,
the following equality, where $M^{r,s}_{261S}$ denotes imports of semiconductors from economy $r$ by economy
$s$, does not hold.

$$
\sum_j Z^{r,s\,(0)}_{261S,j} = M^{r,s}_{261S}
\tag{A.4}
$$

**Stage 2.** Therefore, the $Z^{(0)}$ matrix has to undergo a balancing procedure. A balanced system verifies

$$
\sum_j \tilde{Z}^{r,s}_{261S,j} = M^{r,s}_{261S}
\quad\text{and, for each industry } j,\quad
\tilde{Z}^{r,s}_{261S,j} + \tilde{Z}^{r,s}_{26X,j} = Z^{r,s}_{26,j}.
\tag{A.5}
$$

The RAS method, also called biproportional adjustment procedure, is used to balance the relevant rows and
columns of the auxiliary $Z^{(0)}$ matrix.

While the system is not balanced, the RAS procedure consists in:

- Calculating the error in rows
  $$\varepsilon^{r,s\,(i)}_{261S} = M^{r,s}_{261S} - \sum_j Z^{r,s\,(i)}_{261S,j} \tag{A.6}$$
  and allocating it proportionally to each cell:
  $$Z^{r,s\,(i+1)}_{261S,j} = Z^{r,s\,(i)}_{261S,j} + \frac{Z^{r,s\,(i)}_{261S,j}}{\sum_j Z^{r,s\,(i)}_{261S,j}}\,\varepsilon^{r,s\,(i)}_{261S} \tag{A.7}$$
  The same procedure is used to obtain $Z^{r,s\,(i+1)}_{26X,j}$.
- Calculating the error in columns (zero at iteration $i = 0$, but they are introduced by the balancing
  procedure starting in iteration 1)
  $$\varepsilon^{r,s\,(i+1)}_{j} = Z^{r,s}_{26,j} - Z^{r,s\,(i+1)}_{261S,j} - Z^{r,s\,(i+1)}_{26X,j} \tag{A.8}$$
  and allocating it proportionally to each cell:
  $$Z^{r,s\,(i+2)}_{261S,j} = Z^{r,s\,(i+1)}_{261S,j} + \frac{Z^{r,s\,(i+1)}_{261S,j}}{Z^{r,s\,(i+1)}_{261S,j} + Z^{r,s\,(i+1)}_{26X,j}}\,\varepsilon^{r,s\,(i+1)}_{j} \tag{A.9}$$
  The same procedure is used to obtain $Z^{r,s\,(i+2)}_{26X,j}$.

Bacharach (1970) shows that this procedure converges towards a balanced $\tilde{Z}$ matrix, as defined above.

[TN: iteration index $(i)$ reuses letter $i$ (also supplying industry). Row target for 26X not stated;
"same procedure" implies $M^{r,s}_{26X} = \sum_j Z^{r,s}_{26,j} - M^{r,s}_{261S}$.]

**Stage 3.** The estimated input inflows are used to calculate the technical coefficients.

$$
a^{r,s}_{261S,j} = \frac{\tilde{Z}^{r,s}_{261S,j}}{Z^{r,s}_{26,j}} \cdot a^{r,s}_{26,j}
\quad\text{and}\quad
a^{r,s}_{26X,j} = \frac{\tilde{Z}^{r,s}_{26X,j}}{Z^{r,s}_{26,j}} \cdot a^{r,s}_{26,j}
\tag{A.10}
$$

## Estimating gross output, value added and intermediate consumptions

The previous steps provide an $A$ matrix where 'semiconductors' and 'ICT and electronics (excluding
semiconductors)' are split.

In addition, a new vector of final demand is created, where it is assumed that final demand for
semiconductors is null ($Y^{r,s}_{261S} = 0$ and $Y^{r,s}_{26X} = Y^{r,s}_{26}$), i.e. semiconductors are
only used as intermediate inputs. This is a rather mild assumption, as semiconductors are rarely used for
consumption or investment, but are rather incorporated into other goods.

From the technical coefficients and final demand, it is possible to recover gross output ($X$), intermediate
consumption ($Z$) and value added as a share of gross output ($V$), where 'semiconductors' and 'ICT &
electronics (excluding semiconductors)' are split, as follows:

$$X = (I - A)^{-1} Y \tag{A.11}$$
$$Z = A \hat{X} \tag{A.12}$$
$$V = (I - A')\,\mathbf{1} \tag{A.13}$$

where $\hat{X}$ is a matrix with the $X^{r}_{i}$ on its diagonal and 0s for its other elements and
$\mathbf{1}$ is a vector of 1s.

[TN: equation numbers (A.1)–(A.13) added by transcriber; original equations unnumbered.]
