# MODIS_SNOW_GAPFILL
Google Earth Engine script for gap-filling MODIS MOD10A1/MYD10A1 snow cover products and aggregating to monthly Fractional Snow Cover (FSC) and Snow Cover Days (SCD).
This repository contains a Google Earth Engine (GEE) script for gap-filling MODIS Terra/Aqua daily snow cover products (MOD10A1/MYD10A1 v6.1) and aggregating daily data to monthly Fractional Snow Cover (FSC) and Snow Cover Days (SCD). The code supports the research paper: Thermal regimes shift dominant controls on Northern Hemisphere urban snow deficits (under review).
📋 Overview
Key Functions
Data Loading & Quality Filtering: Load MOD10A1/MYD10A1 datasets and filter valid snow cover pixels using QA bands (values 0–2 indicate high-quality data).
Cross-Sensor Fusion: Fill missing data in MOD10A1 (Terra) with MYD10A1 (Aqua) observations, available from July 14, 2002 onward.
Temporal Interpolation: Apply linear interpolation to remaining gaps within a 10-day moving window to ensure continuous time series.
Monthly Aggregation: Compute monthly mean FSC (scaled 0–100) and count Snow Cover Days (SCD, days with FSC > 50%).
Export: Export monthly FSC/SCD results to GEE Assets for downstream analysis.
Study Scope
Time Range: 2000–2024 (easily configurable via script parameters)
Spatial Scope: Northern Hemisphere (0°E–180°E, 22.5°N–90°N)
Spatial Resolution: 500 m (native MODIS resolution)
🛠️ Usage
Prerequisites
A valid Google Earth Engine account with access to MODIS snow cover datasets.
A pre-created GEE Asset folder named FSCSCD (or adjust the ASSET_FOLDER variable in the script to match your own).
Running the Script
Copy the full script (modis_snow_gapfill.txt) into the GEE Code Editor.
Modify configuration parameters in the CONFIGURATION section (time range, study region, correction coefficients, etc.) to match your study needs.
Run the script sequentially; check the GEE console for progress updates and error messages.
Completed monthly FSC/SCD outputs will be exported to your specified GEE Asset folder.
Key Configurable Parameters
START_DATE/END_DATE: Define the analysis time window (default: 2000-01-01 to 2024-09-30).
REGION_OF_INTEREST: Adjust the study area geometry (default: Northern Hemisphere rectangle).
CORRECTION_PARAMS: Calibrated coefficients to convert MODIS NDSI values to standard FSC (0–100).
INTERP_WINDOW_DAYS: Length of the temporal interpolation window (default: 10 days).
EXPORT_SCALE: Output resolution in meters (default: 500 m).
📊 Datasets
Input Datasets (Publicly Available)
MOD10A1 (Terra Daily Snow Cover, v6.1): Provided by the NSIDC DAAC, https://doi.org/10.5067/MODIS/MOD10A1.061
MYD10A1 (Aqua Daily Snow Cover, v6.1): Provided by the NSIDC DAAC, https://doi.org/10.5067/MODIS/MYD10A1.061
Output Datasets
The gap-filled monthly FSC/SCD dataset is accessible for review via Google Earth Engine Assets:
https://code.earthengine.google.com/?asset=projects/ee-dechengzhou2018/assets/FSCSCD
Upon publication, the dataset will be permanently archived on Zenodo with a persistent DOI to ensure long-term accessibility.
📝 Citation
For citation details, refer to the published version of:
Thermal regimes shift dominant controls on Northern Hemisphere urban snow deficits
📄 License
This project is licensed under the MIT License. See the LICENSE file for full terms.
📧 Contact
For questions about the code or dataset, please contact the corresponding author of the associated research paper.
Last updated: March 2026
