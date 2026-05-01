# sebocyte-lipidomics-analysis
Python workflow for LC-MS lipidomics analysis of sebocytes treated with MSCs and MSC-derived exosomes.
# Sebocyte Lipidomics Analysis

This repository contains the Python workflow used for LC–MS lipidomics data processing and analysis in sebocytes treated with mesenchymal stem cells (MSCs) or MSC-derived exosomes.

## Overview

The workflow includes:

1. Feature filtering based on Compound Discoverer output
2. Peak-rating-based feature detection filtering
3. Median normalization
4. log2 transformation
5. Pareto scaling for PCA and heatmap visualization
6. Principal component analysis (PCA)
7. Hierarchical clustering heatmap
8. Volcano plot analysis
9. Lipid-class-level comparison among experimental groups

## Experimental groups

The analysis includes four groups:

- Control sebocytes
- Exo1: low-dose MSC-derived exosome treatment
- Exo5: high-dose MSC-derived exosome treatment
- MSC: MSC co-culture

## Input data

The expected input file is a CSV file exported from Compound Discoverer after initial filtering. The file should contain:

- Compound name
- m/z
- Retention time
- Peak area values for biological samples
- Peak rating values for individual raw files

The main input file used in the workflow is expected to have columns similar to:

- Name
- m/z
- RT [min]
- Control_1 to Control_4
- Exo1_1 to Exo1_3
- Exo5_1 to Exo5_3
- MSC_1 to MSC_4
- Peak Rating columns for each raw file

## Data processing

Lipid features were filtered using peak-rating information. Features were retained if they showed detectable peak ratings in at least 50% of samples in at least one experimental group.

Quantitative analyses were performed using peak-area values. Peak-area values were median-normalized, log2-transformed, and Pareto-scaled before PCA and heatmap analysis.

## Statistical analysis

Pairwise comparisons between each treatment group and control were performed using Welch’s t-test. P-values were adjusted using the Benjamini-Hochberg false discovery rate method. Volcano plots were generated for:

- Exo1 vs Control
- Exo5 vs Control
- MSC vs Control

Lipid-class-level analysis was performed by assigning lipid features to lipid classes based on annotated compound names and summing peak areas within each class.

## Requirements

Install required Python packages using:

```bash
pip install -r requirements.txt
