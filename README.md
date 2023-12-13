

# 10x Visium Spatial Transcriptomics  Data Analysis Service


## Space Ranger 

Visium Spatial Gene Expression is a next-generation molecular profiling solution for classifying tissue based on gene and protein expression. Space Ranger is a set of analysis pipelines that process Visium Spatial Gene Expression data with brightfield and fluorescence microscope images. Space Ranger allows users to map the whole transcriptome in formalin- fixed paraffin-embedded (FFPE), fixed frozen (FxF), and fresh frozen (FF) tissues to discover novel insights into normal development, disease pathology, and clinical translational research.

- **spaceranger count** takes a microscope slide image and FASTQ files and performs alignment, tissue detection, fiducial detection, and barcode/UMI counting. The pipeline uses Visium Spatial Barcodes to generate feature-barcode matrices, determine clusters, and perform gene expression analysis. In addition to fresh-frozen tissues, spaceranger count is also used for single-library analysis of FFPE and Protein Expression.

- [Space Ranger Count Output Explanation](https://github.com/Margery0011/Visium_CSO_Service/blob/main/visium_output.md)


## Downstream Analysis

### R

- [**Seurat**: Analysis, visualization, and integration of spatial datasets with Seurat
](https://satijalab.org/seurat/articles/spatial_vignette.html)

```
# Load Visium data in Seurat

Load10X_Spatial(
  data.dir,
  filename = "filtered_feature_bc_matrix.h5",
  assay = "Spatial",
  slice = "slice1",
  filter.matrix = TRUE,
  to.upper = FALSE,
  image = NULL,
  ...
)

```

### Python

- [**Scanpy**: Analysis and visualization of spatial transcriptomics data](https://scanpy-tutorials.readthedocs.io/en/latest/spatial/basic-analysis.html)

```
# Load Visium data in Scanpy

scanpy.read_visium(path, genome=None, *, count_file='filtered_feature_bc_matrix.h5', library_id=None, load_images=True, source_image_path=None)
```
-  [**Squidpy**: Analyze Visium H&E data](https://squidpy.readthedocs.io/en/stable/notebooks/tutorials/tutorial_visium_hne.html)

```
# Load Visium data in Squidpy

squidpy.read.visium(path, *, counts_file='filtered_feature_bc_matrix.h5', library_id=None, load_images=True, source_image_path=None, **kwargs)

```

### Loupe Browser

**No Programming Required**
- [Loupe Browser Tutorial](https://www.10xgenomics.com/support/software/loupe-browser/tutorials/introduction/lb-navigation-for-spatial)

## Deconvolotion

[Integrating Single Cell and Visium Spatial Gene Expression Data](https://www.10xgenomics.com/resources/analysis-guides/integrating-single-cell-and-visium-spatial-gene-expression-data)

### Background

- **Problem**: Single Cell RNAseq methods resolve gene expression at the single cell level, but lose the spatial context of the cells. Visium spatial gene expression maintains spatial information, but the resolution of each spot can cover is limited with each spot covering multiple cells (typically 1-10 cells).
  
- **Solution**: With their complementary strengths these data types are a prime target for integration. The current computational tools for single cell and Visium integration fall on a continuum between deconvolution and mapping approaches. Deconvolution methods aim to identify the cell types and their relative proportions contributing to a spot, while mapping methods seek to assign the most likely dominant cell type to a spot.

### Somedeveloped tools and algorithms

- Spacexr/Robust cell-type decomposition (RCTD)
- Seurat label transfer
- Cell2location
- STdeconvolve