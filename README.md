# MODIS_SNOW_GAPFILL
Google Earth Engine script for gap-filling MODIS MOD10A1/MYD10A1 daily snow-cover products and aggregating them into monthly snow-cover fraction (SCF) and snow-cover days (SCD).

This repository provides a Google Earth Engine (GEE) script for gap-filling MODIS Terra/Aqua daily snow-cover products (MOD10A1/MYD10A1 Collection 6.1) and aggregating daily observations into monthly snow-cover fraction (SCF) and snow-cover days (SCD). The code accompanies the manuscript “Cities erode seasonal snow retention in a warming climate”.

Note: Some script variables, file names or asset folders may use the legacy abbreviation FSC for fractional snow cover. In the associated manuscript, the same fractional snow-cover metric is reported as snow cover faction (SCF) to maintain consistent terminology.

Overview
Key Functions
Data loading and quality filtering
Loads MODIS Terra and Aqua daily snow-cover products and retains valid snow-cover observations using QA information, with QA values 0–2 treated as high-quality data.

Cross-sensor fusion
Fills missing Terra MOD10A1 observations with Aqua MYD10A1 observations where available, starting from 14 July 2002.

Temporal interpolation
Applies linear interpolation to remaining gaps within a 10-day moving window to generate more complete daily snow-cover time series.

Monthly aggregation
Aggregates gap-filled daily observations into monthly snow-cover fraction, reported as SCF in the manuscript, and snow-cover days, defined as the number of days with snow cover exceeding 50%.

Export
Exports monthly SCF/SCD outputs to Google Earth Engine Assets for downstream analysis.

Study Scope
Time range: 2000–2024, configurable through script parameters
Spatial scope: Northern Hemisphere study domain, configurable through the region-of-interest parameter
Spatial resolution: 500 m, corresponding to the native MODIS resolution

Usage
Prerequisites
A valid Google Earth Engine account with access to MODIS snow-cover datasets.
A pre-created GEE Asset folder, for example FSCSCD, or a customized folder specified through the ASSET_FOLDER variable in the script.
Running the Script
Copy the full script, modis_snow_gapfill.txt, into the GEE Code Editor.
Modify the configuration parameters, including the time range, study region, correction coefficients and export settings, as needed.
Run the script sequentially and check the GEE console for progress updates and error messages.
Completed monthly SCF/SCD outputs will be exported to the specified GEE Asset folder.
Key Configurable Parameters
START_DATE / END_DATE: Define the analysis period, with the default range from 2000-01-01 to 2024-09-30.
REGION_OF_INTEREST: Defines the study area geometry.
CORRECTION_PARAMS: Coefficients used to convert MODIS NDSI snow-cover values to fractional snow cover.
INTERP_WINDOW_DAYS: Length of the temporal interpolation window, with a default value of 10 days.
EXPORT_SCALE: Output spatial resolution in metres, with a default value of 500 m.
Datasets
Input Datasets
The input MODIS snow-cover datasets are publicly available from the NSIDC DAAC:

MOD10A1, Terra Snow Cover Daily Global 500 m, Collection 6.1: 
MYD10A1, Aqua Snow Cover Daily Global 500 m, Collection 6.1: 
Output Datasets
The gap-filled monthly SCF/SCD dataset is accessible for review through Google Earth Engine Assets:

https://code.earthengine.google.com/?asset=projects/ee-dechengzhou2018/assets/FSCSCD

Upon publication, the dataset will be permanently archived on Zenodo with a persistent DOI to ensure long-term accessibility.

Citation
For citation details, please refer to the published version of:

“Cities erode seasonal snow retention in a warming climate”

License
This project is licensed under the MIT License. See the LICENSE file for full terms.

Contact
For questions about the code or dataset, please contact the first or corresponding author of the associated manuscript.
First author: Decheng Zhou (decheng.zhou@hainanu.edu.cn)
Corresponding author: Decheng Zhou (shuqing.zhao@hainanu.edu.cn)

Last updated: June 2026
