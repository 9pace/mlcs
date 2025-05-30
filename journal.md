# Project Journal (Solo)

**Author: Ben Pace**

## 04/16/25

- Restarted work on the final project after being separated from group due to delays.
- Reviewed all prior work with Divya, including project goals, dataset sources, and model plans.
- Reorganized priorities to focus on a simplified version of the project that can be completed solo.
- Decided to focus on tree species migration prediction using GRU-based time series modeling.
- Prepared README documentation with updated scope and clear model goals.

## 04/16

- Reached out to Alp with project update and repo link.

## 04/17

- Didn’t make major technical progress this week, but I’ve reengaged with the project and am preparing to focus on smaller, clearer goals. Hoping to re-scope data ingestion and GRU integration soon.
- Found landset data through GEE and started data processing script, may need debugging for alignment issues

## 04/18

- Find and download appropriate atlas data
- Added GEE script to consolidate acadian region hansen/landsat data
- Finalize GitHub repository with README and journal logs.

## 04/19

- Initialized GCP project instance for GEE
- updated GEE script to landset 2 data
- created mask function for c02 sensor pixel band applied l2 scale factors. (updated collection ids) indices are calculated after masking and scaling.
- debug GEE script
- image of acadian region for data available

## 04/20

- Successfully configured and executed Google Earth Engine script to generate and export core datasets (annual Landsat C02 L2 composites 2000-2021 with indices, Hansen loss/cover, annual climate, DEM/slope) for the Northern Mainie study area (EPSG:32619, 30m res).
- Set up local project structure, Git repository (configured Git LFS for GeoTIFFs), and Python virtual environment with necessary libraries. Data currently downloading from Google Drive.

## 04/21

- Discussed with Alp and TAs about prior work use (I am able to use it and iterate on anything if necessary).

- Completed initial ML pipeline setup (Sections 1-5): Imported core libraries (numpy, pandas, rasterio, sklearn) and configured project paths.
  Implemented a crucial data verification function (verify_raster_alignment) using rasterio to ensure CRS, transform, and dimensions match across input GeoTIFFs before proceeding.
- Implemented the feature extraction loop: Iterates through sampled points, opens relevant GeoTIFFs (Landsat t-1, Climate t-1, Climate t, DEM, Slope) using rasterio, reads pixel values efficiently using 1x1 windows, and assembles features into a list of dictionaries, later converted to a pandas DataFrame. Includes basic dropna() for handling potential NoData values read from rasters.

## 04/22

- adding temproal split, rf model training and evaluation
- Implements temporal train/test split based on target year to prevent data leakage.
- Initializes and trains a scikit-learn RandomForestClassifier using balanced class weights.
- Saves the trained model using joblib for persistence.
- Adds model evaluation code using scikit-learn metrics: classification report, confusion matrix, ROC AUC score, and plots.

## 04/23 - 24

- adding model interpretation and final sections:
- Extracts and plots feature importances (Gini) from the trained RF model using scikit-learn attributes and matplotlib.
- Includes function skeleton for optional spatial prediction map generation using rasterio block processing.
- Adds markdown structure for project conclusion, limitations, and future work

# 04/26

- Setup minimal dataset for proceeding, with hansen, landsat, climate data in place

# 04/27

- Experimenting with resampling, data nan issues are present. Trying to find reducable scope here.
- Experimenting with feature extraction

# 04/28

- Completed MVP with test run and random forest analysis. Low roc and auc due to data imputation issues. This will be the next point to focus on, perhaps will also attempt to try other models.
- Discussed after class with Alp on project progress. He mentioned to document progress in paper, and to show the full journey. Appreciate his help and guidance.

# 04/29 - 05/03

- It was difficult to do too much this week I tried to integrate more datasets, but ran into NAN issues with much of the data, tried data imputation as well. Was able to improve slightly on ROC, not quite ideal though.

# 05/03 - 06

- Worked on final paper for this class. Finals coming up so going to need to consolidate soon.
- Gave video presentation with progress and next steps to alp.
- Worked on trying out new model architecture, data bottleneck here. Had to try again through resampling with smaller data since the data takes very long to be able to compile.. this lead to worse results
- Interested if smaller timeseries yields results, ran on 1 year time difference with not great results on ROC curve, better than random
- Would like to rerun on longer timeseries seperation but time constraints mean I will probably have to just outline these results

# 05/9 - 05/11

- Had to rebase due to data issues, threw of commit times on github (hopefuly this is understandable)
- Finished paper and completed data analysis, steps for moving forward
- Restructured filed and fixed notebook presentability, completed documentation work
