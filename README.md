

# 10x Visium Spatial Transcriptomics  Data Analysis Service


## Space Ranger 

Visium Spatial Gene Expression is a next-generation molecular profiling solution for classifying tissue based on gene and protein expression. Space Ranger is a set of analysis pipelines that process Visium Spatial Gene Expression data with brightfield and fluorescence microscope images. Space Ranger allows users to map the whole transcriptome in formalin- fixed paraffin-embedded (FFPE), fixed frozen (FxF), and fresh frozen (FF) tissues to discover novel insights into normal development, disease pathology, and clinical translational research.

- **spaceranger count** takes a microscope slide image and FASTQ files and performs alignment, tissue detection, fiducial detection, and barcode/UMI counting. The pipeline uses Visium Spatial Barcodes to generate feature-barcode matrices, determine clusters, and perform gene expression analysis. In addition to fresh-frozen tissues, spaceranger count is also used for single-library analysis of FFPE and Protein Expression.

- [Space Ranger Count Output Explanation](https://github.com/Margery0011/Visium_CSO_Service/blob/main/visium_output.md)


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