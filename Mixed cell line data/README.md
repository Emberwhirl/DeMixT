# Mixed cell line RNA-seq dataset

To generate this dataset in RNA-seq, we performed a mixing experiment, in which we mixed mRNAs from three cell lines: lung adenocarcinoma in humans (H1092), cancer-associated fibroblasts (CAFs) and tumor infiltrating lymphocytes (TIL), at different proportions to generate 32 samples, including 9 samples that correspond to three repeats of a pure cell line sample for three cell lines. The RNA amount of each tissue in the mixture samples was calculated on the basis of real RNA concentrations tested in the biologist’s lab

This dataset was generated in house. We mapped raw reads generated from pair- end Illumina sequencing to the human reference genome build 37.2 from NCBI through Tophat (default parameters and supplying the -G option with GTF anno- tation file downloaded from NCBI genome browser). The mapped reads obtained from Tophat output were cleaned by Samtools to remove improperly mapped and duplicated reads. We then used Picard tools to sort those cleaned sam files accord- ing to their reference sequence names and create an index for the reads. The gene level expression was quantified by applying the R packages GenomicFeatures and GenomicRanges. We generated a reference table from the human reference genome hg19 and then used the function findOverlaps to count the number of reads mapped to each exon for all the samples. This count data is pre-processed by total count normalization and genes that contained zero counts are removed. The pre-processed count data are used as input for DeMixT and ISOpure.

"ENSG.txt" is the table of raw read count data we processed for each mixed sample (two technical replicates). "info.xlsx" is the description file for each sample. "MixingPurity.csv" is the table of mixing proportions for each sample.