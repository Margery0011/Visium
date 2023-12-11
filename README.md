

# 10x Visium Spatial Transcriptomics  Data Analysis Service


## Where to find 

- [Space Ranger Output Explanation](https://github.com/Margery0011/Visium_CSO_Service/blob/main/visium_output.md)


## Downstream Analysis

### R

- [**Seurat**: Analysis, visualization, and integration of spatial datasets with Seurat
](https://satijalab.org/seurat/articles/spatial_vignette.html)

### Python

- [**Scanpy**: Analysis and visualization of spatial transcriptomics data](https://scanpy-tutorials.readthedocs.io/en/latest/spatial/basic-analysis.html)
-  [**Squidoy**: Analyze Visium H&E data](https://squidpy.readthedocs.io/en/stable/notebooks/tutorials/tutorial_visium_hne.html)

### Loupe Browser

**No Programming Required**
- [Loupe Browser Tutorial](https://www.10xgenomics.com/support/software/loupe-browser/tutorials/introduction/lb-navigation-for-spatial)

## Deconvolotion

[Integrating Single Cell and Visium Spatial Gene Expression Data](https://www.10xgenomics.com/resources/analysis-guides/integrating-single-cell-and-visium-spatial-gene-expression-data)

Integrating Single Cell RNAseq and Visium spatial gene expression offers a powerful solution to the problem of losing spatial context in gene expression analysis. While Single Cell RNAseq provides detailed gene expression data at the cellular level, it lacks spatial information, a gap filled by Visium, which maintains spatial context but with lower resolution. By utilizing computational tools that range from deconvolution to mapping approaches, this integration effectively combines the strengths of both methods. Deconvolution techniques discern cell types and their proportions within each Visium spot, whereas mapping assigns a predominant cell type to each spot. Importantly, for effective integration, the single cell and Visium datasets need not be from the same sample but should be biologically similar, allowing the use of established single cell datasets from large consortiums like the Human Cell Atlas. This approach not only facilitates a deeper understanding of cell-cell communication and identification of rare cell populations but also enhances the overall analysis capability by leveraging the complementary features of both single cell and spatial gene expression data.

### Somedeveloped tools and algorithms

- Spacexr/Robust cell-type decomposition (RCTD)
- Seurat label transfer
- Cell2location
- STdeconvolve: