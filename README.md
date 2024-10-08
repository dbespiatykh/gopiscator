<p align="center">
  <img src="https://github.com/dbespiatykh/gopiscator/blob/main/logo.png?raw=true" alt="gopiscator logo" height=200>
</p>
<hr>

`GOpiscator` is a command-line tool for performing gene set enrichment analysis using the Gene Ontology (GO) database.

[![PyPI version](https://badge.fury.io/py/gopiscator.svg)](https://badge.fury.io/py/gopiscator)

### Installation

```
pip install gopiscator
```

### Usage

```
Usage: gopiscator [OPTIONS]

  GOpiscator (Tool for performing gene set enrichment analysis)

Options:
  -i, --gene-list FILE        Genes of interest list.  [required]
  -a, --go-annotation FILE    GO annotation file.  [required]
  -o, --output FILE           Write output to a file.  [default: (standard output)]
  -g, --ontology FILE         GO '.obo' file.  [default: ('go-basic.obo'; will be downloaded if absent)]
  -b, --background-list FILE  Background gene list file.  [default: (All genes from 'go-annotation' file)]
  --threshold FLOAT           P-value threshold.  [default: 0.05]
  --gene-count INTEGER        Minimum No. of genes annotated to the specific GO term.  [default: 2]
  -v, --version               Show the version and exit.
  -h, --help                  Show this message and exit.
```
<hr>

> [!NOTE]
> `gene-list` should have your genes of interest, one gene per line:
> ||
>| --- |
>| Rv3861 |
>| Rv3862c |
>| Rv0083 |
>| Rv3371 |
>
> `go-annotation` should be tab-delimited with genes in the first column and GO terms in the second column (separated by comma):
> |||
>| --- | --- |
>| Rv0001 |	GO:0006172,GO:0006275,GO:0006270 |
>| Rv0002 |	GO:0046677,GO:0006260 |
>| Rv0003 |	GO:0009432,GO:0000731,GO:0006260 |
>| Rv0005 |	GO:0046677,GO:0006265,GO:0006261 |
>
> `background-list` if you want to use background list of genes, it should have one gene per line:
> ||
>| --- |
>| Rv0001 |
>| Rv0002 |
>| Rv0003 |
>| Rv0005 |

<hr>

> [!TIP]
> <details>
>  <summary>If you do not provide <code>-o, --output</code> then the results will be shown in terminal like this:</summary>
>
>```
>╒════╤════════════╤════════════════════╤═══════════════════════════════╤═══════════╤════════════════════╤═══════════════╕
>│    │ GOID       │ Ontology           │ GO_term_name                  │   P-value │   Enrichment_score │   Rich_factor │
>╞════╪════════════╪════════════════════╪═══════════════════════════════╪═══════════╪════════════════════╪═══════════════╡
>│  0 │ GO:0045926 │ biological_process │ negative regulation of growth │     0     │               4.36 │           0.2 │
>├────┼────────────┼────────────────────┼───────────────────────────────┼───────────┼────────────────────┼───────────────┤
>│  1 │ GO:0098754 │ biological_process │ detoxification                │     0.015 │               1.82 │           0.2 │
>╘════╧════════════╧════════════════════╧═══════════════════════════════╧═══════════╧════════════════════╧═══════════════╛
>```
>
></details>
>
> <details>
>  <summary>When the <code>-o, --output</code> is provided the the output file will look like this:</summary>
>
>| GOID       | Ontology           | GO_term_name                  | Definition        | P-value    | FDR        | Enrichment_score | Fold_enrichment | Rich_factor | GeneRatio | BgRatio  | Count | Genes                                              |
>| ---------- | ------------------ | ----------------------------- | ----------------- | ---------- | ---------- | ---------------- | --------------- | ----------- | --------- | -------- | ----- | -------------------------------------------------- |
>| GO:0045926 | biological_process | negative regulation of growth | Any process that… | 4.40E-05   | 0.00171655 | 4.35640751       | 9.81395349      | 0.1627907   | 7[35]     | 43[2110] | 7     | Rv0299,Rv0609,Rv1114,Rv2010,Rv2866,Rv3384c,Rv3697c |
>| GO:0098754 | biological_process | detoxification                | Any process that… | 0.01503798 | 0.29324058 | 1.82281055       | 15.0714286      | 0.25        | 3[35]     | 12[2110] | 3     | Rv1560,Rv2550c,Rv2801A                             |
>
> </details>
