# MelImmuneOmics

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![R](https://img.shields.io/badge/R-%3E%3D4.1-blue.svg)](https://www.r-project.org/)
[![GitHub repo](https://img.shields.io/badge/GitHub-OuLab--BioMed%2FMelImmuneOmics-green.svg)](https://github.com/OuLab-BioMed/MelImmuneOmics)

> An R package for melanoma immune microenvironment analysis: transcriptomics-based immune cell deconvolution, immune scoring, and spatial immune correlation with multi-color immunofluorescence and clinical data.

## Overview

`MelImmuneOmics` is a comprehensive R toolkit developed by **OuLab** for dissecting the tumor immune microenvironment (TIME) in melanoma. It integrates **bulk transcriptomics**, **multi-color immunofluorescence (mIF)**, and **clinical metadata** to enable:

- **Immune cell deconvolution** — estimate the abundance of immune cell populations from bulk RNA-seq data
- **Immune scoring** — compute multiple immune signature scores (e.g., IFN-γ, cytolytic activity, T-cell inflamed GEP)
- **Spatial immune correlation** — link transcriptomic immune features with spatial protein expression from mIF images
- **Survival & clinical association** — correlate immune features with patient outcomes and clinical covariates

## Features

| Module | Description |
|---|---|
| `deconvolute()` | Immune cell fraction estimation from bulk transcriptome |
| `immune_score()` | Calculate curated immune signature scores |
| `spatial_correlate()` | Correlate transcriptomic signals with spatial mIF markers |
| `clinical_assoc()` | Association with survival, response, and clinical variables |
| `viz_immune_landscape()` | Visualization of immune landscape across samples |

## Installation

```r
# Install from GitHub
if (!requireNamespace("devtools", quietly = TRUE))
  install.packages("devtools")
devtools::install_github("OuLab-BioMed/MelImmuneOmics")

# Load
library(MelImmuneOmics)
```

### Dependencies

- R >= 4.1
- Bioconductor packages (auto-installed): `Biobase`, `SummarizedExperiment`, `GSEABase`
- CRAN packages: `ggplot2`, `dplyr`, `tidyr`, `survival`, `survminer`, `pheatmap`

## Quick Start

```r
library(MelImmuneOmics)

# 1. Load example data (replace with your own)
data("example_expr")    # gene expression matrix (genes x samples)
data("example_clin")    # clinical data frame

# 2. Deconvolve immune cell fractions
immune_frac <- deconvolute(example_expr, method = "cibersort")

# 3. Compute immune scores
scores <- immune_score(example_expr, signatures = c("IFNG", "CYT", "TIGS"))

# 4. Correlate with survival
clinical_assoc(scores, example_clin, outcome = "OS", time = "OS_time")

# 5. Visualize immune landscape
viz_immune_landscape(immune_frac, scores, example_clin)
```

## Data Input Format

- **Expression matrix**: genes (rows) x samples (columns), normalized TPM/FPKM or log-CPM values
- **Clinical data**: data frame with one row per sample, including time-to-event and covariates
- **mIF spatial data**: cell-level marker expression with spatial coordinates (optional)

## Project Structure

```
MelImmuneOmics/
├── R/                  # Package source code
│   ├── deconvolution.R
│   ├── immune_score.R
│   ├── spatial.R
│   ├── clinical.R
│   └── visualization.R
├── data/               # Example datasets
├── man/                # Function documentation
├── vignettes/          # Tutorial vignettes
├── tests/              # Unit tests
├── DESCRIPTION
├── NAMESPACE
└── README.md
```

## Citation

If you use `MelImmuneOmics` in your research, please cite:

> Shen K-C, Ou [PI Name]. *MelImmuneOmics: An R package for melanoma immune microenvironment analysis.* [Journal], 2026. DOI: [pending]

```bibtex
@article{shen2026melimmuneomics,
  title   = {MelImmuneOmics: An R package for melanoma immune microenvironment analysis},
  author  = {Shen, Kai-Cheng and Ou, [PI Name]},
  journal = {[Journal Name]},
  year    = {2026},
  doi     = {[DOI pending]}
}
```

You can also click the **"Cite this repository"** button on the GitHub repo page for auto-generated citation.

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Contact

- **Doc.KCshen** (Kai-Cheng Shen) — [kaichengshen2@qq.com](mailto:kaichengshen2@qq.com)
- **OuLab** — BioMedical Institute
- **Issues**: [GitHub Issues](https://github.com/OuLab-BioMed/MelImmuneOmics/issues)

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://github.com/OuLab-BioMed">OuLab-BioMed</a></sub>
</p>
