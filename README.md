# Tract-Level Combined Diabetes-Obesity Burden in Greater Houston

[![Open in Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ynganatra/houston-census-tract-analysis/blob/main/Houston_Census_Tract_Analysis.ipynb)

This repository contains the Python and Google Colab code used for the tract-level analysis in the manuscript:

**“Tract-Level Combined Diabetes-Obesity Burden in Greater Houston: Clustering, Vulnerability, and Low-Income Status.”**

**Publication status:** Accepted for publication in the National High School Journal of Science (NHSJS). The final journal citation and DOI will be added after publication.

## Repository Contents

- `Houston_Census_Tract_Analysis.ipynb` — Main analysis notebook for data preparation, census tract harmonization, statistical testing, spatial analysis, sensitivity analysis, and figure generation.
- `requirements.txt` — Python packages required to run the analysis.
- `CITATION.cff` — Citation metadata for this repository.
- `LICENSE` — MIT License.
- `.gitignore` — Files and folders excluded from version control.

## Study Overview

This ecological, cross-sectional study examined modeled diabetes and obesity burden across census tracts in the ten-county Houston-Pasadena-The Woodlands Metropolitan Statistical Area, referred to in the manuscript as Greater Houston.

The primary measure was a continuous combined diabetes-obesity score. Diabetes and obesity prevalence estimates were standardized separately using z-scores, averaged with equal weighting, and linearly rescaled to a 0-to-1 range.

A secondary high-burden overlap analysis tested whether tracts with high estimated diabetes prevalence and high estimated obesity prevalence appeared together more often than expected under independence.

The study also examined relationships between the continuous combined score and:

- Social Vulnerability Index (SVI) percentile
- USDA low-income tract status
- USDA low-access tract status
- USDA Low-Income, Low-Access (LILA) tract status
- neighboring tract conditions
- global and local spatial clustering

## Study Area

The study included the following ten Greater Houston counties:

- Austin
- Brazoria
- Chambers
- Fort Bend
- Galveston
- Harris
- Liberty
- Montgomery
- San Jacinto
- Waller

The final analysis included 1,069 census tracts.

## Data Sources

The analysis used publicly available government datasets:

- CDC PLACES 2025 census tract data
- CDC/ATSDR Social Vulnerability Index 2022
- USDA Food Access Research Atlas 2019
- U.S. Census Bureau 2020 Census Tract to 2010 Census Tract Relationship File
- U.S. Census Bureau TIGER/Line census tract boundary files

CDC PLACES health estimates and SVI percentile values were harmonized from 2020 census tracts to 2010 census tracts using area-based crosswalk weights. The harmonized variables were then merged with the USDA indicators and 2010 census tract boundaries.

## Continuous Combined Diabetes-Obesity Score

For each census tract, diabetes and obesity prevalence estimates were standardized separately:

```text
z = (X - mean) / standard deviation
