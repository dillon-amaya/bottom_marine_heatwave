Code used to create forecasts in Amaya et al. _in review_, "Bottom marine heatwaves along the continental shelves of North America"

Bottom marine heatwve (BMHW) and surface marine heatwave SMHW) statistics are calculated using monthly mean bottom temperature and sea surface temperature output from the GLORYS 1/12˚ ocean reanalysis during the period 1993-2019. Included in this repository are matlab scripts and some data used to generate the results and figures of our study. Steps in the workflow, with associated matlab scripts, are:

## 1. Download GLORYS ocean reanalysis data

Data required to run the "master" script includes: GLORYS monthly mean bottomT, sst, and mld from 1993-2019. Available at: https://data.marine.copernicus.eu/product/GLOBAL_MULTIYEAR_PHY_001_030/description

Other processed data (e.g., decorrelation maps, LME masks, etc) are provided in our github repository https://github.com/dillon-amaya/bottom_marine_heatwave

## 2. Download zip file of MATLAB scripts

In this repository is a zip file, which when uncompressed holds a folder with all of the MATLAB scripts/functions needed to reproduce every figure in our analysis. Also included in this folder is a "master" script, which is used to read in and process the GLORYS data before calculating the different BMHW/SMHW statistics. Data is then plotted using a series of functions at the end of the "master" script. User input near the beginning of the "master" script decides whether to process detrended or raw (e.g., not detrended data). User input also determines which figures to make at the end of the "master" script.

## 3. Edit "master" script and run
