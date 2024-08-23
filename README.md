<p align="center">
  <img src="logo.png" alt="gopiscator Logo" height=200>
</p>
<hr>

`GOpiscator` is a command-line tool for performing gene set enrichment analysis using the Gene Ontology (GO) database.

### Installation

```
pip install gopiscator
```

### Usage

```
Usage: gopiscator [OPTIONS]

  GOpiscator (Tool for performing gene set enrichment analysis)

Options:
  -i, --gene-list FILE      Genes of interest list.  [required]
  -a, --go-annotation FILE  GO annotation file.  [required]
  -o, --output FILE         Write output to a file.  [default: (standard output)]
  -g, --ontology FILE       GO '.obo' file.  [default: ('go-basic.obo'; will be downloaded if absent)]
  --threshold FLOAT         P-value threshold.  [default: 0.05]
  --gene-count INTEGER      Minimum No. of genes annotated to the specific GO term.  [default: 2]
  -v, --version             Show the version and exit.
  -h, --help                Show this message and exit.
```