
# Tree Migration Modeling with Remote Sensing and Climate Data

**Author: Ben Pace**

This project explores climate-driven tree species migration in the Northeastern U.S. using remote sensing and deep learning. Originally developed with a team, this version is a solo continuation with reduced scope.

##  Goal
Predict species distribution shifts (Red Maple, Balsam Fir, Yellow Birch) between 2018–2023 using satellite imagery and climate variables. A GRU model is used to capture temporal dynamics from multi-year input sequences.

##  Data Sources
- **Sentinel-2 Imagery** (2018–2023): spectral bands, NDVI, NBR  
- **GBIF Tree Occurrence Data**: ~7000 samples across 3 species  
- **Hansen Global Forest Change**: baseline forest mask  
- **CMIP6 Climate Data**: temperature & precipitation per year  

##  Model
A 2-layer GRU model:
- Inputs: (samples, 6 years, features)
- Features: spectral bands + NDVI/NBR + climate data
- Output: tree species classification (3 classes)
- Optimizer: Adam  
- Evaluation: Accuracy, confusion matrix

## limitations
- Limited species sample sizes
- Sparse tree presence data in some years
- Ongoing bottlenecks in spectral extraction for full spatial coverage

## Next Steps
- Improve species sample diversity
- Expand to seasonal-specific imagery (fall)
- Try alternative model architectures (Transformer?)
