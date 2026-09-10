# NetSAM

[![Bioconductor build (release)](https://bioconductor.org/shields/build/release/bioc/NetSAM.svg)](https://bioconductor.org/checkResults/release/bioc-LATEST/NetSAM/)
[![Bioconductor build (devel)](https://bioconductor.org/shields/build/devel/bioc/NetSAM.svg)](https://bioconductor.org/checkResults/devel/bioc-LATEST/NetSAM/)
[![Years in Bioconductor](https://bioconductor.org/shields/years-in-bioc/NetSAM.svg)](https://bioconductor.org/packages/release/bioc/html/NetSAM.html)
[![Downloads](https://bioconductor.org/shields/downloads/release/NetSAM.svg)](https://bioconductor.org/packages/stats/bioc/NetSAM/)

**Net**work **S**eriation **A**nd **M**odularization.

NetSAM identifies the hierarchical modules of a network (*network
modularization*) and finds a suitable linear ordering for all leaves of the
identified hierarchy (*network seriation*). It takes an edge-list
representation of a weighted or unweighted network as input and writes files
that can be used directly by the one-dimensional network visualization tool
[NetGestalt](http://www.netgestalt.org), or fed into other network analyses.

NetSAM can also build a correlation network (e.g. a co-expression network)
from a data matrix, seriate and modularize that network, and then relate the
resulting modules back to sample features or to Gene Ontology terms.

Unlike plain hierarchical clustering, NetSAM optimizes the leaf ordering,
assesses the statistical significance of a network's modular organization, and
identifies relevant hierarchical levels and modules at different scales.

## Installation

NetSAM is distributed through [Bioconductor](https://bioconductor.org/packages/NetSAM):

```r
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("NetSAM")
```

To install the development version from this repository:

```r
BiocManager::install("bzhanglab/NetSAM")
```

## Quick start

```r
library("NetSAM")

inputNetworkDir <- system.file("extdata", "exampleNetwork.net", package = "NetSAM")
outputFileName <- file.path(getwd(), "NetSAM")

result <- NetSAM(inputNetwork = inputNetworkDir, outputFileName = outputFileName,
                 outputFormat = "nsm", edgeType = "unweighted",
                 map_to_genesymbol = FALSE, organism = "hsapiens",
                 minModule = 0.003, modularityThr = 0.2, nThreads = 3)
```

## Main functions

| Function | Purpose |
| --- | --- |
| `NetSAM()` | Network seriation and modularization |
| `MatSAM()` | Correlation network construction, seriation and modularization from a matrix |
| `MatNet()` | Construction of a correlation network from a matrix |
| `consensusNet()` | Construction of a consensus co-expression network |
| `NetAnalyzer()` | Network analyzer |
| `featureAssociation()` | Calculate the associations between modules and sample features |
| `GOAssociation()` | Identify the associated GO terms for each module |
| `mapToSymbol()` | Map other ids to gene symbols |
| `mergeDuplicate()` | Merge duplicate ids in matrix data |
| `testFileFormat()` | Test whether the data matrix and annotation have a correct format |

Note that `mapToSymbol()` — and any function called with
`map_to_genesymbol = TRUE` — queries Ensembl BioMart and therefore needs a
working internet connection.

## Documentation

- [Package vignette](https://bioconductor.org/packages/release/bioc/vignettes/NetSAM/inst/doc/NetSAM.pdf)
- [Bioconductor landing page](https://bioconductor.org/packages/release/bioc/html/NetSAM.html)
- From R: `browseVignettes("NetSAM")`

## Citation

If you use NetSAM, please cite:

> Shi Z, Wang J, Zhang B. NetGestalt: integrating multidimensional omics data
> over biological networks. *Nature Methods* **10**, 597–598 (2013).
> <https://doi.org/10.1038/nmeth.2517>

## License

LGPL. Maintained by Zhiao Shi (<zhiao.shi@gmail.com>); originally authored by
Jing Wang.
