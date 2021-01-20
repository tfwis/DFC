#### Load packages

Please confirm that these packages are installed before trying this example.

``` {r loadLibs, message=FALSE}
library(ddhodge)
library(dplyr)
library(readr)
library(ggsci)
library(ggraph)
```

#### Load scRNA-seq data

Load data of from [GSE143437](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE143437) (Andrea et. al., 2020).

```{r loadData, cache=TRUE, message=FALSE}
Rawc <- read.table("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Frawdata%2Etxt%2Egz", sep="\t", header=T, row.names=1)
Normc <- read.table("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Fnormalizeddata%2Etxt%2Egz", sep="\t", header=T, row.names=1)
meta <- read_tsv("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Fmetadata%2Etxt%2Egz") 
```