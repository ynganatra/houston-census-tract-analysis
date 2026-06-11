# Overlapping Diabetes and Obesity Burden in Greater Houston

This repository contains the Google Colab notebook used for the tract-level analysis in the study:

**"Overlapping Diabetes and Obesity Burden in Greater Houston Was Associated With Social Vulnerability and Low-Income, Low-Access Status."**

## Repository contents

* `Houston_Census_Tract_Analysis.ipynb`
  Main notebook for data preprocessing, tract harmonization, spatial analysis, statistical testing, sensitivity analysis, and figure generation.

* `requirements.txt`
  Python packages used in the notebook.

* `CITATION.cff`
  Citation metadata for this repository.

## Study overview

This notebook integrates publicly available tract-level datasets for Greater Houston and performs the analysis used to:

* identify high diabetes burden tracts
* identify high obesity burden tracts
* define diabetes-obesity high-burden overlap tracts
* evaluate association with Social Vulnerability Index (SVI)
* evaluate association with Low-Income, Low-Access (LILA) tract status
* assess overall spatial clustering using Global Moran’s I
* identify local high clusters using Getis-Ord Gi*
* apply False Discovery Rate (FDR) adjustment as a sensitivity check for local cluster results
* perform threshold sensitivity analysis using 75th-, 80th-, and 85th-percentile cutoffs
* generate the manuscript figures and summary tables

## Data sources

The analysis uses publicly available government datasets referenced in the manuscript, including:

* CDC PLACES 2025
* CDC/ATSDR Social Vulnerability Index 2022
* USDA Food Access Research Atlas
* U.S. Census tract relationship files
* U.S. Census TIGER/Line tract boundary files

## Study area

The study covers the nine-county Greater Houston metropolitan statistical area:

* Austin
* Brazoria
* Chambers
* Fort Bend
* Galveston
* Harris
* Liberty
* Montgomery
* Waller

## License

This repository is released under the MIT License.
