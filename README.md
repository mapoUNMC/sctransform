# sctransform with SCENIC support 
## R package for normalization and variance stabilization of single-cell RNA-seq data using regularized negative binomial regression and Beurnolli SCENIC regression

The sctransform package was developed by Christoph Hafemeister in [Rahul Satija's lab](https://satijalab.org/) at the New York Genome Center and described in [Hafemeister and Satija, Genome Biology 2019](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-019-1874-1). Recent updates are described in [(Choudhary and Satija, Genome Biology, 2022)](https://doi.org/10.1186/s13059-021-02584-9).
Core functionality of this package has been integrated into [Seurat](https://satijalab.org/seurat/), an R package designed for QC, analysis, and exploration of single cell RNA-seq data.

## Quick start

Installation:

```r
# Install sctransform from CRAN
install.packages("sctransform")

# Or the development version from GitHub:
remotes::install_github("satijalab/sctransform", ref="develop")
```

Running sctransform:

```r
# Runnning sctransform on a AUC  matrix after output from SCENIC
AUC = getAUC(AUC_mtx) #3.4_regulonAUC_matrix.Rds
normalized_data <- sctransform::vst(umi_count_matrix)$y
# v2 regularization
normalized_data <- sctransform::vst(umi_count_matrix, vst.flavor="v2")$y

# Runnning sctransform on a Seurat object
seurat_object <- Seurat::SCTransform(seurat_object)
#v2 regularization
seurat_object <- Seurat::SCTransform(seurat_object, vst.flavor="v2")
```

## Help

For usage examples see vignettes in inst/doc or use the built-in help after installation  
`?sctransform::vst`  

Available vignettes:  

- [Variance stabilizing transformation](https://htmlpreview.github.io/?https://github.com/satijalab/sctransform/blob/supp_html/supplement/variance_stabilizing_transformation.html)  
- [Using sctransform in Seurat](https://htmlpreview.github.io/?https://github.com/satijalab/sctransform/blob/supp_html/supplement/seurat.html)
- [Examples of how to perform normalization, feature selection, integration, and differential expression with sctransform v2 regularization](https://satijalab.org/seurat/articles/sctransform_v2_vignette.html)
- [Example to how to perform SCENIC normalization](https://mapounmc.github.io/sctransform/variance_stabilizing_transformation-copy.html)
- [10X Genomics PBMC](https://mapounmc.github.io/sctransform/seurat-copy_pbmc.html)
- [Acute Infected Brain and Blood](https://mapounmc.github.io/sctransform/seurat-copy_SIV_monkey_brain_blood.html)

## References

- Hafemeister, C. & Satija, R. Normalization and variance stabilization of single-cell RNA-seq data using regularized negative binomial regression. Genome Biology 20, 296 (2019).  [https://doi.org/10.1186/s13059-019-1874-1](https://doi.org/10.1186/s13059-019-1874-1). An early version of this work was used in the paper [Developmental diversification of cortical inhibitory interneurons, Nature 555, 2018](https://github.com/ChristophH/in-lineage).

- Choudhary, S. & Satija, R. Comparison and evaluation of statistical error models for scRNA-seq. Genome Biology 23.1 (2022). [https://doi.org/10.1186/s13059-021-02584-9](https://doi.org/10.1186/s13059-021-02584-9)

- FOX [https://github.com/Howard-Fox-Lab/FOX-Functional-OMIC-eXploration](https://github.com/Howard-Fox-Lab/FOX-Functional-OMIC-eXploration)

