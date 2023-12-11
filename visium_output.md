
# Visium 

## Where to find Visium output files
- To be decided



# Space Ranger Output Files Summary 


Following is the output folder we will get from `spaceranger`. The outs folder contains the final pipeline output files which including what we want for downstream analysis.

![Alt text](https://github.com/Margery0011/Visium_CSO_Service/blob/main/Figures/Screenshot%202023-12-11%20at%209.36.12%20AM.png?raw=true)


    Figure 1.1: Overview of the folder generate from sapceranger

![Alt text for second image](https://github.com/Margery0011/Visium_CSO_Service/blob/main/Figures/Screenshot%202023-12-11%20at%209.42.50%20AM.png?raw=true)


    Figure 1.2: Overview of the outs folder


Above is what we can find in the `outs` folder. It contains some summary information of the sequencing data, the annotated read sequences, and gene expression matrices we commonly work on. Following is some important output files we want to look at.

- [Web Summary](https://www.10xgenomics.com/support/software/space-ranger/analysis/outputs/space-ranger-web-summary)
-  [Matrices](https://www.10xgenomics.com/support/software/space-ranger/analysis/outputs/space-ranger-feature-barcode-matrices)
-  [Loupe File (.cloupe)](https://support.10xgenomics.com/spatial-gene-expression/software/visualization/latest/what-is-loupe-browser?src=social&lss=twitter&cnm=soc-twi-ra_g-program&cid=7011a0000003KRm)

## spaceranger count for Gene Expression

 The outputs generated from the primary analysis pipeline spaceranger count for Gene Expression (GEX) contained in the outs/ directory are summarized below:

| Output   | Description|
| -------- | ------- |
| web_summary.html | Data summary with images, metrics, and plots that can be used for quality assessment as well as errors and warnings related to data quality   |
| metrics_summary.csv| 	Metrics for quality assessment    |
| cloupe.cloupe   | Loupe Browser file for data visualization and analysis |
|analysis/spatial/spatial_enrichment.csv |Secondary analysis results (clustering, DGE, Moran's I)|
|spatial/|	Folder containing Visium-specific outs: QC images to check image processing pipeline, downsampled input images, and files that describe spot barcode locations in the images|
|molecule_info.h5|Molecule level information used in additional pipelines (spaceranger aggr, spaceranger targeted-compare|
|Barcoded BAM (optional)possorted_genome_bam.bam possorted_genome_bam.bai possorted_genome_bam.csi | Read alignment files|
|**Filtered GEX Matrix MEX: filtered_feature_bc_matrix HD5F: filtered_feature_bc_matrix.h5** | Feature barcode matrices that contains both tissue-associated as well as background barcodes and are used in secondary analysis in R/Python|
|Unfiltered GEX Matrix MEX: raw_feature_bc_matrix HD5F: raw_feature_bc_matrix.h5|Feature barcode matrices that contains both tissue-associated as well as background barcodes and are used in secondary analysis in R/Python|
|deconvolution/| Folder containing outputs of LDA-based spot deconvolution for the range of K topics|

### Web Summary 

The top of the page will display the title of the run and the pipeline used. There are also tabs for **Summary**, **Gene Expression**, and **Antibody**.

#### Summary tab


![Alternative text for third image](https://github.com/Margery0011/Visium_CSO_Service/blob/main/Figures/Screenshot%202023-12-11%20at%2010.29.15%20AM.png?raw=true)

    Figure 1.3 Summary tab example


The summary tab starts with hero metrics and sequencing metrics. Click the `?` for definitions of each metric.


    Table 1.  Sequencing Metrics in the Space Ranger summary file


| Metrics                          | Definition                                                                                             | Expected Value          | Notes                                                                                                                                                              |
|----------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          |                                                                                                        |                         |                                                                                                                                                                    |
| Number of reads                  | Total number of read pairs that were assigned to this library in demultiplexing                         | Sequencing output dependent | Lower than expected may indicate poor sequencing run (overclustering, underclustering, low % passing filter).                                                        |
| Valid barcodes                   | Fraction of reads with barcodes that match the whitelist* after barcode correction                     | >75%                    | Low valid barcodes may indicate sequencing issues (such as low Read 1 Q30 score).                                                                                  |
| Valid UMIs                       | Fraction of reads with valid UMIs; i.e. UMI sequences that do not contain Ns and that are not homopolymers | >75%                    | Low valid UMIs may indicate issues with sequencing or library quality.                                                                                             |
| Sequencing saturation            | The fraction of reads originating from an already-observed UMI. This is a function of library complexity and sequencing depth | Dependent upon sequencing depth and sample complexity | Dependent on library complexity, sequencing depth, and experiment analysis goals. Lower sequencing saturation indicates a high proportion of the library complexity has not been captured by sequencing. |
| Q30 bases in barcode, Sample Index, or UMI | Fraction of tissue-associated barcode, Sample Index, or UMI bases with Q-Score ≥30, excluding very low quality/no call (Q≤2) bases from the denominator | Sequencing platform dependent | Low Q30 base percentages could indicate sequencing issue such as sub-optimal loading concentration.                                                                 |
| Q30 bases in probe read          | Fraction of RNA read bases with Q-score ≥ 30, excluding very low quality/no-call (Q ≤2) bases from the denominator. This is Read 2 for the Visium v1 chemistry | Sequencing platform dependent, ideally >65% | Expected to be lower than Q30 bases in barcode or UMI (Read 1) or Sample Index (i7 or i5 read) and is sequencing platform dependent. Low Q30 base percentages could indicate sequencing issue such as sub-optimal loading concentration. |

    Table 2.  Spots Metrics in the Space Ranger summary file

| Metric            | Definition                                                              | Expected Value                         | Notes |
|-------------------|-------------------------------------------------------------------------|----------------------------------------|-------|
| Fraction reads in spots under tissue | The fraction of valid barcode, confidently mapped to transcriptome reads with tissue-associated barcodes | Ideally >50%                           | Low fraction reads in spots under the tissue indicate that many of the reads were not assigned to tissue covered spots. This could be caused by high levels of ambient RNA resulting from inefficient permeabilization, because the incorrect image or orientation was used, or because of poor tissue detection. The latter case can be addressed by using the manual tissue selection option through Loupe. |
| Mean reads per spot | The number of reads, both under and outside of tissue, divided by the number of barcodes associated with a spot under tissue | 25,000 reads pairs/tissue covered spot minimum recommended | The necessary sequencing depth per tissue covered spot depends on the sample type (high or low RNA) and the desired analysis. |
| Mean reads under tissue per spot | The number of reads under tissue divided by the number of barcodes associated with a spot under tissue | Dependent on tissue type, RNA quality, and sequencing depth | Lower than expected values may be biological (low transcriptional diversity) or may indicate low sequencing depth, library complexity, or quality. |
| Median UMI counts per spot    | The median number of UMI counts per tissue covered spot                     | Dependent on tissue type, RNA quality, and sequencing depth |                                                                                                                       |
| Median genes per spot        | The median number of genes detected per tissue covered spot. Detection is defined as the presence of at least one UMI count | Dependent on tissue type, RNA quality, and sequencing depth |                                                                                                                       |
| Genes detected                | The number of unique genes from the filtered probe set with at least one UMI count in any tissue covered spot | Dependent on tissue type, RNA quality, and sequencing depth |                                                                   
    Table 3.  Maps Metrics in the Space Ranger summary file

| Metric            | Definition                                                              | Expected Value                         | Notes |
|-------------------|-------------------------------------------------------------------------|----------------------------------------|-------|
| Reads mapped to probe set          | Fraction of reads that mapped to the probe set                              | Variable                       | Lower than expected values could be indicative of low library or sample quality or the use of the wrong probe set.    |
| Reads mapped confidently to probe set | Fraction of reads that mapped uniquely to a probe in the probe set           | Ideally >50%                   | Lower than expected values could be indicative of low aggregate expression, use of the wrong probe set, or inefficient targeting to the probe set. |
| Reads mapped confidently to the filtered probe set | Fraction of reads from probes that map to a unique gene. These reads are considered for UMI counting by default. This metric will be None when probe filtering is disabled. For more information on probe filtering visit the 10x Genomics Support website | Ideally >50% | |

![Alternative text for fourth image](https://github.com/Margery0011/Visium_CSO_Service/blob/main/Figures/Screenshot%202023-12-11%20at%201.43.26%20PM.png?raw=true)

    Figure 1.4 Tissue Detection and Fiducial Alignment


The **Tissue Detection and Fiducial Alignment image** shows the tissue image in gray tones with an overlay of the aligned fiducial frame (open blue circles) and the capture area spots (gray circles). For the latter, the circles filled in red denote selected tissue-associated spots and the remaining open gray circles denote unselected spots. Hover mouse cursor over the image to magnify the view. Confirm fiducial frame aligns well with fiducial spots, e.g. the corner shapes match, and confirm selection of tissue-covered spots. If the result shows poor fiducial alignment or tissue detection, consider sharing the image with support@10xgenomics.com so they can improve the algorithm. Otherwise, perform manual alignment and spot selection with Loupe Browser.



### Matrices

Space Ranger outputs unfiltered (raw_feature_bc_matrix) and filtered feature-barcode (filtered_feature_bc_matrix) matrices in two file formats: the Market Exchange Format (MEX, described on this page) and Hierarchical Data Format (HDF5).

| Type                               | Description |
|------------------------------------|-------------|
| Unfiltered feature-barcode matrix  | Contains **every barcode** from fixed list of known-good barcode sequences that has at least one read. This includes background and tissue-associated barcodes. |
| Filtered feature-barcode matrix    | Contains **only tissue-associated barcodes**. For Visium probe-based assays, genes not in the filtered probe set are removed from the filtered matrix by default. |
| Raw probe-barcode matrix           | Contains columns that indicate the probes in the filtered probe reference, the probes that passed gDNA filtering, and the probe barcodes that are in spots. It is similar to the feature-barcode matrix, but is organized at the probe level rather than the gene level. |

### Loupe File (.cloupe)

Loupe Browser is an easy-to-use visualization software that offers interactive support for upstream image processing required for Space Ranger as well as downstream visualization and analysis of your spatial gene expression data. No programming required.

Loupe Browser provides many powerful analysis capabilities including the ability to perform the following analysis all within the spatial context of a tissue image:

- Interrogate significant genes.
- Characterize and refine clusters.
- Perform differential expression analysis.

For more information:
1. https://www.10xgenomics.com/support/software/space-ranger/getting-started/what-is-space-ranger
2. https://www.10xgenomics.com/support/software/space-ranger/analysis/outputs/output-overview