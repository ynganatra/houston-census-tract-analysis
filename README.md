# Diabetes-Obesity Co-Hotspots in Greater Houston

This repository contains the Google Colab notebook used for the tract-level analysis in the study:

**"Diabetes-Obesity Co-Hotspots in Greater Houston Were Associated with Social Vulnerability and Limited Food Access."**

## Repository contents

- `Houston_Census_Tract_Analysis.ipynb`  
  Main notebook for data preprocessing, tract harmonization, spatial analysis, statistical testing, and figure generation.

- `requirements.txt`  
  Python packages used in the notebook.

- `CITATION.cff`  
  Citation metadata for this repository.

## Study overview

This notebook integrates publicly available tract-level datasets for Greater Houston and performs the analysis used to:

- identify diabetes hotspots
- identify obesity hotspots
- define diabetes-obesity co-hotspots
- evaluate association with social vulnerability
- evaluate association with low-income, low-access food access status
- assess spatial clustering using Moran’s I
- generate the manuscript figures

## Data sources

The analysis uses publicly available government datasets referenced in the manuscript, including:

- CDC PLACES 2025
- CDC/ATSDR Social Vulnerability Index 2022
- USDA Food Access Research Atlas 2019
- U.S. Census tract relationship files
- U.S. Census TIGER/Line tract boundary files

## Study area

The study covers the nine-county Greater Houston metropolitan statistical area:

- Austin
- Brazoria
- Chambers
- Fort Bend
- Galveston
- Harris
- Liberty
- Montgomery
- Waller

## License

This repository is released under the MIT License.
