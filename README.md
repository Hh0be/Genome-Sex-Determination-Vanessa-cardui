# Genome Sex Determination Analysis of *Vanessa cardui*

## 1. Introduction

This project investigates the genetic sex of *Vanessa cardui* (painted lady butterfly) using whole-genome sequencing coverage analysis.

In Lepidoptera, the typical sex-determination system is **ZZ in males** and **ZW in females**. Comparing sequencing depth across autosomes and sex chromosomes can provide evidence for identifying the chromosomal sex of a sequenced individual.

## 2. Objectives

1. Analyze sequencing coverage across the chromosomes of *Vanessa cardui*.
2. Compare the mean sequencing depth of autosomes, the Z chromosome, and the W chromosome.
3. Calculate Z-to-autosome (Z/A) and W-to-autosome (W/A) coverage ratios.
4. Infer the likely chromosomal sex of the sequenced specimen based on coverage patterns.

## 3. Reference Genome Information

| Parameter | Information |
| --- | --- |
| Species | *Vanessa cardui* |
| Common name | Painted lady butterfly |
| NCBI GenBank assembly | GCA_905220365.2 |
| NCBI RefSeq assembly | GCF_905220365.2 |
| Assembly name | ilVanCard2 |
| Assembly level | Chromosome |
| Genome size | Approximately 424.8 Mb |
| Sequencing data | ERR12506741 |
| Analysis platforms | Galaxy and RStudio |

Reference assembly: [www.ncbi.nlm.nih.gov/datasets/genome/GCA_905220365.2](https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_905220365.2/)

## 4. Methodology

### 4.1 Sequencing Data Processing

Whole-genome sequencing reads were processed using the Galaxy bioinformatics platform.

The workflow included:

1. Retrieval of sequencing data.
2. FASTQ quality assessment using FastQC.
3. Alignment of sequencing reads using BWA-MEM.
4. Generation of BAM alignment files.
5. Examination of chromosome-level alignment statistics using Samtools idxstats.
6. Calculation of sequencing coverage using Samtools coverage.
7. Extraction of sequencing depth information using Samtools depth.

### 4.2 Chromosome Classification

Chromosome accession numbers were organized into groups representing autosomes, the Z chromosome, and the W chromosome.

A chromosome classification table was prepared and merged with the sequencing coverage dataset using RStudio.

### 4.3 Coverage Analysis

Mean sequencing depth was calculated for each chromosome group.

The following ratios were used:

**Z-to-autosome coverage ratio:**

Z/A = Mean Z depth / Mean autosomal depth

**W-to-autosome coverage ratio:**

W/A = Mean W depth / Mean autosomal depth

### 4.4 Data Visualization

RStudio was used to generate graphical representations of chromosome sequencing depth and mean coverage by chromosome group.

## 5. Results

### 5.1 Sequencing Depth Summary

| Parameter | Value |
| --- | --- |
| Mean autosomal depth | 34.27562× |
| Mean Z depth | 38.78260× |
| Mean W depth | 4.65912× |
| Z/A ratio | 1.131492 |
| W/A ratio | 0.135931 |

### 5.2 Chromosome Coverage

## Figures

### Figure 1. Chromosome Sequencing Depth

![Chromosome Sequencing Depth](figures/chromosome_coverage.png)

*Figure 1. Mean sequencing depth across the chromosomes of Vanessa cardui.*

### Figure 2. Mean Coverage by Chromosome Group

![Mean Coverage by Chromosome Group](figures/group_coverage_comparison.png)

*Figure 2. Comparison of mean sequencing depth among autosomes, Z chromosome, and W chromosome.*

## 6. Discussion

The results indicate that the mean autosomal sequencing depth was approximately 34.28×, while the Z chromosome exhibited a mean depth of approximately 38.78×.

The calculated Z/A ratio of 1.13 indicates that the Z chromosome has sequencing coverage comparable to the autosomes.

The W chromosome exhibited substantially lower coverage, with a mean depth of approximately 4.66× and a W/A ratio of 0.136.

Under the typical lepidopteran ZZ/ZW sex-determination system, a Z/A ratio approaching 1 is expected in ZZ males, whereas ZW females generally exhibit reduced Z-chromosome coverage relative to autosomes.

The observed coverage pattern is therefore **consistent with a ZZ (male) individual**.

However, the nonzero W-chromosome coverage requires additional investigation. Possible explanations include ambiguous read mapping, repetitive genomic sequences, or differences in reference assembly representation.

The interpretation remains provisional until the chromosome annotations, alignment specificity, and coverage calculations have been independently validated.

## 7. Conclusion

Whole-genome sequencing coverage analysis of *Vanessa cardui* revealed a Z/A ratio of 1.131492 and a W/A ratio of 0.135931.

These results provisionally support a **ZZ (male) chromosomal sex assignment**, based on the relatively similar sequencing depths of the Z chromosome and autosomes and the substantially reduced W-chromosome coverage.

Further validation is recommended to confirm the chromosome classifications and investigate the residual W-chromosome alignments.

## 8. Project Files

### Input Data

- `chromosome_coverage.tsv` — Chromosome-level coverage data exported from Galaxy.
- `chromosome_groups.csv` — Chromosome classification table.

### Analysis Script

- `sex_determination_analysis.R` — R script used for data processing, calculations, and visualization.

### Results

- `results/chromosome_coverage_merged.csv` — Merged chromosome coverage dataset.
- `results/sex_determination_summary.csv` — Summary of sequencing depth and coverage ratios.
- `results/sex_determination_report.txt` — Text report containing the sex-determination interpretation.

### Figures

- `figures/chromosome_coverage.png` — Chromosome-level sequencing depth.
- `figures/group_coverage_comparison.png` — Comparison of mean coverage by chromosome group.

## 9. Software and Tools

- Galaxy
- FastQC
- BWA-MEM
- Samtools
- R
- RStudio

## 10. References

National Center for Biotechnology Information (NCBI). *Vanessa cardui* genome assembly, GCA_905220365.2.

[www.ncbi.nlm.nih.gov/datasets/genome/GCA_905220365.2](https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_905220365.2/)

Galaxy Project. Galaxy bioinformatics analysis platform.

[usegalaxy.org](https://usegalaxy.org/)

R Core Team. R: A Language and Environment for Statistical Computing.

[www.r-project.org](https://www.r-project.org/)
