# Data analysis for the demonstration of *Discriminative featrure of cells*

This is the repository to reproduce the results of DFC paper.  
Please see below when you use our DFC method in R.  
https://github.com/tfwis/alDFC

### Load packages

Please confirm that these packages are installed before trying this example.

``` {r loadLibs, message=FALSE}
library(tidyverse)
```

### Load scRNA-seq data

Load scRNA-seq data from [GSE143437](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE143437) (Andrea et al., 2020).

```{r loadData, cache=TRUE, message=FALSE}
Rawc <- read.table("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Frawdata%2Etxt%2Egz", sep="\t", header=T, row.names=1)
Normc <- read.table("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Fnormalizeddata%2Etxt%2Egz", sep="\t", header=T, row.names=1)
meta <- read_tsv("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE143437&format=file&file=GSE143437%5FDeMicheli%5FMuSCatlas%5Fmetadata%2Etxt%2Egz") 
```

#### Load STRING 

Load [STRING](https://string-db.org/) database for analysis on R.

```
st_link <- readr::read_delim("https://stringdb-static.org/download/protein.links.full.v11.0/10090.protein.links.full.v11.0.txt.gz",delim=" ")
st_info <- readr::read_tsv("https://stringdb-static.org/download/protein.info.v11.0/10090.protein.info.v11.0.txt.gz",col_types="cc__") %>% with(setNames(preferred_name,protein_external_id))
```
