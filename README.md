# GSE65194-Data-Normalization-and-Subtype-Analysis
GSE65194 Data Normalization and Subtype Analysis
# 📊 Microarray Preprocessing and Subtype Clustering Pipeline (GSE65194)

This R script automates the critical initial steps of microarray gene expression data analysis, focusing on quality control (QC), data normalization, and preliminary visualization of sample clustering. The pipeline is designed around the **GSE65194** dataset, which studies gene expression in human **glioma** tissues.

It prepares the data for downstream analysis, such as Differential Gene Expression (DGE) or survival modeling, ensuring sample quality and comparability.

## 🚀 Key Features

* **Automated Data Retrieval:** Fetches expression data and metadata directly from the **GEO database (GSE65194)** using `GEOquery`.
* **Quantile Normalization:** Applies **quantile normalization** (`limma::normalizeBetweenArrays`) to correct for technical variation and ensure comparable gene distributions across all samples.
* **Quality Control (QC) Visualization:** Generates **boxplots** before and after normalization to visually confirm data distribution consistency.
* **Low-Expression Filtering:** Filters out genes with mean expression in the lowest quartile (25th percentile), removing noise and speeding up subsequent analyses.
* **Subtype Clustering:** Performs and visualizes **Principal Component Analysis (PCA)** to check if known sample groups (subtypes) cluster correctly in low-dimensional space.
* **Data Persistence:** Saves the fully processed and filtered expression matrix, metadata, and subtype information to an `.RData` file.

---

## 🔬 Analysis Overview

| Component | Method / Test | Purpose |
| :--- | :--- | :--- |
| **Dataset** | GSE65194 | Gene expression data from human glioma tissues. |
| **Normalization** | Quantile Normalization | Standardizes the empirical distribution of gene expression across all samples. |
| **Filtering** | Interquartile Range (IQR) Filtering | Removes non-informative, low-expressed genes. |
| **Clustering** | PCA | Assesses overall sample similarity and the fidelity of experimental groups. |

---

## 🛠️ Prerequisites and Setup

### 📦 Packages

The script automatically installs and loads the necessary Bioconductor and CRAN packages:
* `GEOquery` (For data retrieval)
* `limma` (For normalization)
* `dplyr` (For data manipulation)
* `ggplot2` (For visualization)

### ⚙️ Execution

1.  **Download** the `GSE65194 Data Normalization and Subtype Analysis.R` file.
2.  **Ensure a save path exists:** The script assumes the save path is the working directory where the script is run.
3.  **Execute** the script in your R environment:
    ```R
    source("GSE65194 Data Normalization and Subtype Analysis.R")
    ```

---

## 📁 Output Files (3 Plots + 1 Data File)

All output files are saved to the current working directory.

### Processed Data

| Filename | Type | Description |
| :--- | :--- | :--- |
| `processed_data_step1.RData` | R Binary Data | Contains the final, filtered, and normalized `expression_data`, `metadata`, and `subtype` factors for downstream use. |

### Quality Control and Visualization Plots

| Filename | Analysis Stage | Description |
| :--- | :--- | :--- |
| `boxplot_before_normalization.png` | QC | Boxplot illustrating raw data distributions, usually showing significant technical variation. |
| `boxplot_after_normalization.png` | QC | Boxplot confirming uniform data distributions across all samples after quantile normalization. |
| `pca_plot.png` | Clustering | **Principal Component Analysis (PCA)** plot, showing sample clustering colored by the extracted sample subtype. |
