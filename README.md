# Bulk RNA Deconvolution and Pathway Analysis of Matched Tumour–Normal RNA-seq Samples

## Overview

This project investigates changes in the tumour microenvironment of matched tumour and normal tissue samples using bulk RNA-seq data from five patients. Multiple deconvolution approaches were applied to estimate immune and stromal cell composition, followed by pathway-level analysis using Gene Set Variation Analysis (GSVA).

The study compares tumour and normal samples using complementary computational frameworks to identify reproducible cellular and biological signals associated with tumour development.

## Detailed report with codes and entire analysis is available in this repo as TME.pdf

---

## Objectives

1. Perform bulk RNA deconvolution using:

   * EPIC
   * MCP-counter
   * Decosus (consensus deconvolution)

2. Compare tumour and normal cellular compositions.

3. Identify significantly altered cell populations using paired statistical testing.

4. Perform GSVA-based pathway analysis using KEGG gene sets.

5. Evaluate biological consistency across independent deconvolution methods.

---

## Dataset

* 10 bulk RNA-seq samples
* 5 matched patient pairs
* Patients: S02, S03, S05, S06, and S10
* Sample types:

  * Normal tissue
  * Tumour tissue

Expression matrices were generated from a DESeq2 normalization workflow and used as input for downstream analyses.

---

## Methods

### 1. EPIC

EPIC was used to estimate:

* B cells
* CD4 T cells
* CD8 T cells
* NK cells
* Macrophages
* Endothelial cells
* Cancer-associated fibroblasts (CAFs)
* Other cells

Outputs included:

* Cell fractions
* mRNA proportions
* Clustered heatmaps
* Paired tumour-normal comparisons

### 2. MCP-counter

MCP-counter was used to estimate enrichment scores for:

* T cells
* CD8 T cells
* Cytotoxic lymphocytes
* B lineage
* Monocytic lineage
* Myeloid dendritic cells
* Neutrophils
* Endothelial cells
* Fibroblasts

Outputs included:

* Cell abundance scores
* Clustered heatmaps
* Paired t-tests

### 3. Decosus

Decosus was used as a consensus deconvolution framework integrating multiple deconvolution algorithms including:

* ssGSEA
* quanTIseq

Consensus scores were generated across multiple immune and stromal populations.

### 4. GSVA

GSVA was performed using KEGG pathway gene sets to identify pathway-level differences between tumour and normal tissues.

Analysis was conducted using a paired design incorporating patient-specific effects.

---

## Key Findings

### Tumour Microenvironment Composition

Across all three deconvolution approaches:

* Samples did not cluster cleanly by tumour versus normal status.
* One normal sample (S06_Normal) consistently emerged as a strong stromal outlier.
* Fibroblast/CAF enrichment was observed across EPIC, MCP-counter, and Decosus.
* Tumour samples showed evidence of increased B-cell infiltration.

---

## Significant Cell Types

### EPIC

| Cell Type | Direction           |
| --------- | ------------------- |
| B cells   | Increased in tumour |

**p = 0.045**

### MCP-counter

| Cell Type | Direction           |
| --------- | ------------------- |
| B lineage | Increased in tumour |

**p = 0.037**

### Decosus

Eleven significant cell populations were identified.

#### Increased in Tumour

* Class-switched memory B cells
* Regulatory T cells (Tregs)
* NK CD56dim cells
* Co-stimulation T cells
* Co-inhibition T cells
* Epithelial cells

#### Decreased in Tumour

* Adipocytes
* Macrophage M1
* Hematopoietic stem cells (HSC)
* Preadipocytes
* Conventional dendritic cells (cDC)

---

## Cross-Method Biological Consensus

A key observation was the reproducibility of two biological signals across independent methods:

1. Fibroblast/CAF enrichment, particularly in sample S06_Normal.
2. Increased B-cell signatures in tumour samples.

The convergence of EPIC, MCP-counter, and Decosus strengthens confidence in these findings.

---

## GSVA Pathway Analysis

No KEGG pathway remained significant after applying the assignment threshold:

**Adjusted p-value ≤ 0.01**

This was attributed primarily to:

* Small cohort size (5 matched pairs)
* Reduced degrees of freedom from paired modelling
* Multiple testing correction across hundreds of pathways

Despite this, several pathways showed strong nominal significance.

### Top Differential KEGG Pathways

* Histidine Metabolism
* Drug Metabolism – Cytochrome P450
* Starch and Sucrose Metabolism
* Lysosome
* p53 Signaling Pathway
* Pyrimidine Metabolism
* Metabolism of Xenobiotics by Cytochrome P450
* Cell Cycle
* Ether Lipid Metabolism
* DNA Replication

---

## Software and Packages

* R
* DESeq2
* EPIC
* MCP-counter
* Decosus
* GSVA
* limma
* ggplot2
* pheatmap
* tidyverse

---

## Key Skills Demonstrated

* Bulk RNA-seq analysis
* Tumour microenvironment profiling
* Immune deconvolution
* Consensus cell-type estimation
* Statistical hypothesis testing
* Pathway enrichment analysis
* Data visualization
* Reproducible computational biology workflows


