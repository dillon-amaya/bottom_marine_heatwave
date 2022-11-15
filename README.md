Code used to create forecasts in Amaya et al. _in review_, "Bottom marine heatwaves along the continental shelves of North America"

Bottom marine heatwve (BMHW) and surface marine heatwave (SMHW) statistics are calculated for nine different Large Marine Ecosystems (LMEs) using monthly mean bottom temperature and sea surface temperature output from the GLORYS 1/12˚ ocean reanalysis during the period 1993-2019. Included in this repository are matlab scripts and some data used to generate the results and figures of our study. Steps in the workflow, with associated matlab scripts, are:

## 1. Download GLORYS ocean reanalysis data

Data required to run the "master" script includes: GLORYS monthly mean bottomT, sst, and mld from 1993-2019. Available at: https://data.marine.copernicus.eu/product/GLOBAL_MULTIYEAR_PHY_001_030/description

Other processed data (e.g., decorrelation maps, LME masks, etc) are provided in our github repository https://github.com/dillon-amaya/bottom_marine_heatwave

## 2. Download zip file of MATLAB scripts

In this repository is a zip file, which when uncompressed holds a folder with all of the MATLAB scripts/functions needed to reproduce every figure in our analysis. Also included in this folder is a "master" script, which is used to read in and process the GLORYS data before calculating the different BMHW/SMHW statistics. Data is then plotted using a series of functions at the end of the "master" script. User input near the beginning of the "master" script decides whether to process detrended or raw (e.g., not detrended data). User input at the end of the "master script" also determines which figures to plot.

## 3. Edit "master" script and run

Before running the "master" script, there are three areas for user input.
  1. Change the pathID variables at Lines 4-6 to point to the GLORYS data on whatever system you're working with.
  2. Decide whether or not to calculate BMHW statistics with data that has had the warming trend removed. Do this by changing the value of the variable "M"      at Line 142.
  3. Pick which of the figures you'd like to plot using the variable "N" in the sections beginning at Line 528.

The processing steps in the "master" script are implemented in sections. The sections are:

Section A - Reading in coordinate variables and LME masks <br />
Section B - Reading in GLORYS monthly mean data, calculating monthly anomalies, and organizing by LME <br />
Section C - Decide whether or not to removing warming trend <br />
Section D - Calculate seasonally evolving 90th percentile <br />
Section E - Calculate average BMHW/SMHW intensity and duration for months above 90th percentile for each grid cell in each LME <br />
Section F - Calculating how often SMHW/BMHW events co-occur (i.e., synchrony) in each LME <br />
Section G - Calculating area-average BMHW/SMHW intensity and duration across all grid cells in given depth range <br />
Section H - Calculating fraction of LME's area that is in BMHW/SMHW conditions as a function of time <br />
Section I - Calculating area-average BWTA/SSTA in grid cells experiencing BMHW conditions as a function of time and LME <br />
Section J - Creating figures <br />

## 4. Additional information

Additional functions required to run the "master" are included in the zip file. These functions include: <br />

anom5.m          - Removes the climatological seasonal cycle from a 3D monthly mean dataset based on a user inputs for start and end year. <br />
brewermap.m      - A set of useful colormaps for plotting (see also 
                   https://www.mathworks.com/matlabcentral/fileexchange/45208-colorbrewer-attractive-and-distinctive-colormaps) <br />
cmap_intv.m      - Returns the RGB values for a user-specified _brewermap_ colormap based on a given timeseries of anomalies. <br />
customcolormap.m - A set of useful colormaps for plotting (see also https://www.mathworks.com/matlabcentral/fileexchange/69470-custom-colormap) <br />
default_colors.m - Returns the RGB values of the MATLAB default line colors based on user input. <br />
haxby.m          - Colormap for displaying bathymetry/topography data (see also https://www.mathworks.com/matlabcentral/fileexchange/25690-haxby-color-map) <br />
snctools         - Folder containing functions for reading NetCDF files into MATLAB. <br />
time_array.m.    - Creates a character array with the timesteps between user specified years. <br />

Additional data required to run the "master" are also included in the zip file. This data includes: <br />

bta_daily_decorr_timescale_lme.mat  -  Decorrelation timescale of daily mean bottom temperature anomalies in each LME. Calculated using the script                                                bhw_glorys_figure_shw_decay_rate.m included in the zip file. <br />
ssta_daily_decorr_timescale_lme.mat -  Same as before, but for sea surface temperature anomalies.
lme_lat.mat & lme_lon.mat.          -  The lat/lon coordinates of the LME shape files
lme_mask2.mat                       -  Masks outlining the different LMEs on the GLORYS grid
