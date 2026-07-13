# Tract-Level Combined Diabetes-Obesity Burden in Greater Houston

[![Open in Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ynganatra/houston-census-tract-analysis/blob/main/Houston_Census_Tract_Analysis.ipynb)

This repository contains the Python and Google Colab code used for the tract-level analysis in the manuscript:

**“Tract-Level Combined Diabetes-Obesity Burden in Greater Houston: Clustering, Vulnerability, and Low-Income Status.”**

**Publication status:** Accepted for publication in the National High School Journal of Science (NHSJS).

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

The source datasets are not stored in this repository and must be obtained from their respective government sources.

## Data Preparation and Tract Harmonization

The PLACES and SVI datasets used 2020 census tract geography, while the USDA Food Access Research Atlas used 2010 census tract geography.

For each relationship between a 2020 tract and a 2010 tract, the area-based weight was calculated as:

```text
Weight = AREALANDPART / AREALANDTRACT20
```

The weighted values were then aggregated to the corresponding 2010 tract:

```text
X2010 = sum(X2020 × Weight) / sum(Weight)
```

The harmonized health and SVI variables were merged with the USDA indicators and the 2010 census tract boundary file.

Tracts with missing diabetes prevalence, obesity prevalence, SVI, or USDA classification values were excluded from the final analysis.

## Continuous Combined Diabetes-Obesity Score

For each census tract, diabetes and obesity prevalence estimates were standardized separately:

```text
z = (X - mean) / standard deviation
```

The diabetes and obesity z-scores were averaged with equal weighting:

```text
Combined z-score = (Diabetes z-score + Obesity z-score) / 2
```

The resulting average z-score was linearly rescaled to a 0-to-1 range. The transformation preserved the rank order of the tracts while making higher values consistently represent higher modeled combined diabetes-obesity burden.

The continuous combined score was the primary measure used for the main analyses.

## High-Burden Overlap Analysis

Diabetes and obesity prevalence estimates were ranked separately across census tracts.

For the primary overlap analysis:

- tracts in the highest 20% of diabetes prevalence estimates were classified as high diabetes burden tracts
- tracts in the highest 20% of obesity prevalence estimates were classified as high obesity burden tracts
- tracts meeting both criteria were classified as high-burden overlap tracts

The corresponding cutoff was the 80th percentile for each condition.

The observed overlap was compared with the overlap expected if the high-diabetes and high-obesity classifications were independent. The analysis reported:

- observed overlap
- expected overlap under independence
- enrichment ratio
- Jaccard overlap
- blocked permutation P value

The analysis was repeated at the 75th- and 85th-percentile thresholds to determine whether the result depended on the selected cutoff.

The percentile thresholds were analytical definitions of high burden and were not clinical thresholds or national public health benchmarks.

## Blocked Permutation Test

The blocked permutation test evaluated whether high diabetes and high obesity estimates appeared together in the same tracts more often than expected by chance.

The high-diabetes classifications were held fixed, while the high-obesity classifications were randomly shuffled within the same:

- county
- urban or rural group

This preserved major geographic structure during randomization.

The main permutation test used:

- 10,000 permutations
- random seed 12345
- a one-sided upper-tail test
- a standard +1 correction for the permutation P value

## Social Vulnerability Analysis

The relationship between the continuous combined diabetes-obesity score and the overall SVI percentile was evaluated using:

- Spearman rank correlation
- median combined scores across SVI quartiles

The continuous combined score increased steadily from the lowest to the highest SVI quartile.

Because both PLACES and SVI are area-level measures that incorporate demographic or socioeconomic information, the observed relationship was interpreted as alignment between tract-level measures rather than evidence of an independent cause-and-effect relationship.

## USDA Income and Access Analyses

The continuous combined score was compared across three USDA tract classifications:

- low-income status
- low-access status
- combined Low-Income, Low-Access status

Median combined scores and differences in medians were calculated for tracts with and without each classification.

The results showed a clearer relationship with low-income status than with low-access status alone. Therefore, the higher combined score observed in LILA tracts should not be interpreted as evidence of a relationship with food access alone.

## Multivariable Models

Two multivariable linear models used the continuous combined score as the outcome.

### Model A

Model A included:

- SVI percentile
- LILA status
- county controls
- neighbor-average spatial-lag covariate

### Model B

Model B included:

- SVI percentile
- low-income status
- low-access status
- county controls
- neighbor-average spatial-lag covariate

Both models used standard errors clustered by county.

The neighbor-average spatial-lag covariate was calculated as the average continuous combined score among neighboring tracts using row-standardized Queen contiguity weights.

## Spatial Analysis

Global spatial autocorrelation was evaluated using Global Moran’s I with:

- row-standardized Queen contiguity weights
- 999 permutations

Under Queen contiguity, tracts were considered neighbors if they shared a boundary or a corner.

Local high-score clustering was evaluated using Getis-Ord Gi* with:

- binary Queen contiguity weights
- 999 permutations
- a one-sided high-cluster interpretation

Local statistical significance was adjusted using the Benjamini-Hochberg False Discovery Rate procedure.

The analysis reported both nominally significant and FDR-significant high-cluster counts.

## Spatial-Weight Sensitivity Analysis

Spatial results were recomputed using:

- Queen contiguity
- Rook contiguity
- four-nearest-neighbor weights
- eight-nearest-neighbor weights
- distance-band weights

The sensitivity analysis evaluated whether the spatial findings depended on the definition and scale of neighboring tracts.

## Main Results

Among the 1,069 analyzed census tracts:

- diabetes and obesity prevalence estimates were strongly related across tracts: Spearman ρ = 0.857
- the continuous combined score was strongly correlated with SVI percentile: Spearman ρ = 0.882
- the continuous combined score increased steadily across SVI quartiles
- low-income and LILA tracts had higher median combined scores
- low-access status alone did not show the same direct median pattern
- the continuous combined score showed strong spatial autocorrelation: Moran’s I = 0.719
- 170 tracts were identified as FDR-significant Getis-Ord Gi* high clusters using Queen contiguity
- 163 tracts met both 80th-percentile high-burden criteria
- 43.4 overlapping tracts were expected under independence
- the enrichment ratio was 3.75
- the Jaccard overlap was 0.608
- the blocked permutation result was P < .001

The high-burden overlap result remained statistically significant at the 75th-, 80th-, and 85th-percentile thresholds.

## Figures and Tables

The notebook generates or supports the following manuscript materials:

- Greater Houston census tract study-area map
- SVI choropleth map
- continuous combined diabetes-obesity score map
- diabetes and obesity prevalence maps
- diabetes-obesity rank relationship plot
- USDA indicator comparison figure
- Moran scatterplot
- Getis-Ord Gi* high-cluster map
- high-burden overlap map
- sample and variable summary table
- SVI quartile summary table
- multivariable model table
- spatial-weight sensitivity table
- blocked permutation summary table
- overlap-threshold sensitivity table

## Reproducibility

The analysis was developed in Python and is designed to run in Google Colab.

Install the required packages using:

```bash
pip install -r requirements.txt
```

Then open and run:

```text
Houston_Census_Tract_Analysis.ipynb
```

The final notebook should be run from the first cell through the final cell in a clean runtime.

Dataset sources, variable definitions, tract harmonization methods, random seeds, statistical settings, and figure-generation procedures are documented in the notebook and manuscript.

## Interpretation and Limitations

This study was ecological and cross-sectional.

The PLACES values were modeled small-area estimates rather than direct clinical measurements of every census tract resident.

The findings describe geographic patterns and statistical associations at the census tract level. They should not be interpreted as:

- individual-level diagnoses
- evidence that every resident of a higher-score tract has diabetes or obesity
- proof that social vulnerability, income status, or food access caused diabetes or obesity
- clinical risk predictions for individual people

The continuous combined score was a relative study measure created from diabetes and obesity prevalence estimates across the analyzed Greater Houston tracts.

## Citation

Citation metadata for the repository are provided in `CITATION.cff`.

GitHub’s **Cite this repository** feature can be used to generate a citation for the code repository.

## License

This repository is released under the MIT License. See `LICENSE` for details.
