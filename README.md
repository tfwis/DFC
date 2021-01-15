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

Load data of from [GSE6731](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE67310) (Treutlein et. al., 2016).

```{r loadData, cache=TRUE, message=FALSE}
dat <- read_tsv("https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE67310&format=file&file=GSE67310%5FiN%5Fdata%5Flog2FPKM%5Fannotated.txt.gz") %>% filter(assignment!="Fibroblast") 
group <- with(dat,setNames(assignment,cell_name))
X <- dat[,-(1:5)] %>% as.matrix %>% t
# revert to FPKM and drop genes with var.=0
X <- 2^X[apply(X,1,var)>0,] - 1 
```
