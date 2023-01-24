Code used for analysis in Amaya et al. _in review_, "Bottom marine heatwaves along the continental shelves of North America"

Bottom marine heatwave (BMHW) and surface marine heatwave (SMHW) statistics are calculated for nine different Large Marine Ecosystems (LMEs) using monthly mean bottom temperature and sea surface temperature output from the GLORYS 1/12˚ ocean reanalysis during the period 1993-2019. Included in this repository are matlab scripts and some data used to generate the results and figures of our study. Steps in the workflow, with associated matlab scripts, are:

## 1. Download GLORYS ocean reanalysis data

Data required to run the "master" script includes:  
GLORYS monthly mean bottomT, sst, and mld from 1993-2019. Available at: https://data.marine.copernicus.eu/product/GLOBAL_MULTIYEAR_PHY_001_030/description    
Other processed data (e.g., decorrelation maps, LME masks, etc) are provided in this repository.

## 2. Download zip file of MATLAB scripts

In this repository is a zip file called "bmhw_matlab_scripts.zip". When uncompressed, this files holds a folder with all of the MATLAB scripts/functions needed to reproduce every figure in our analysis. Also included in this folder is a "master" script (glorys_lme_bmhw_smhw_master.m), which is used to read in and process the GLORYS data before calculating the different BMHW/SMHW statistics. Data is then plotted using a series of functions at the end of the "master" script. 

## 3. Edit "master" script and run

Before running the "master" script, there are three areas for user input.  
  1. Change the pathID variables at Lines 4-6 to point to the GLORYS data on whatever system you're working with.  
  2. Decide whether or not to calculate BMHW/SMHW statistics with data that has had the warming trend removed. Do this by changing the value of the variable "M" at Line 144.  
  3. Pick which of the figures you'd like to plot using the variable "N" in the sections beginning at Line 528.  

The processing steps in the "master" script are implemented in sections. The sections are:

**Section A** - Reading in coordinate variables and LME masks.  
**Section B** - Reading in GLORYS monthly mean data, calculating monthly anomalies, and organizing by LME.  
**Section C** - Decide whether or not to removing warming trend.  
**Section D** - Calculate seasonally evolving 90th percentile.  
**Section E** - Calculate avg. BMHW/SMHW int. and dur. for months > 90th percentile for each grid cell in each LME.  
**Section F** - Calculating how often SMHW/BMHW events co-occur (i.e., synchrony) in each LME.  
**Section G** - Calculating area-average BMHW/SMHW int. and dur. across all grid cells in given depth range.  
**Section H** - Calculating fraction of LME's area that is in BMHW/SMHW conditions as a function of time.    
**Section I** - Calculating area-average BWTA/SSTA in BMHW grid cells as a function of time and LME.  
**Section J** - Creating figures.  

## 4. Additional functions/data

Additional functions required to run the "master" script are included in the zip file. These functions include:  

**anom5.m**           - Removes climatological seasonal cycle from a 3D monthly mean field based on a user inputs for start and end year.   
**anom_timeseries.m** - Removes climatological seasonal cycle from a 1D monthly mean field based on a user inputs for start and end year.   
**brewermap.m**       - A set of useful colormaps for plotting (see also 
                   https://www.mathworks.com/matlabcentral/fileexchange/45208-colorbrewer-attractive-and-distinctive-colormaps).  
**cmap_intv.m**       - Returns the RGB values for a user-specified _brewermap_ colormap based on a given timeseries of anomalies.  
**customcolormap.m**  - A set of useful colormaps for plotting (see also https://www.mathworks.com/matlabcentral/fileexchange/69470-custom-colormap).  
**default_colors.m**  - Returns the RGB values of the MATLAB default line colors based on user input.  
**haxby.m**           - Colormap for displaying bathymetry/topography data (see also https://www.mathworks.com/matlabcentral/fileexchange/25690-haxby-color-map).  
**snctools**          - Folder containing functions for reading NetCDF files into MATLAB.  
**time_array.m**      - Creates a character array with the timesteps between user specified years.  

Additional data required to run the "master" are also included in the zip file. This data includes:  

**bta_daily_decorr_timescale_lme.mat**  -  Decorrelation timescale of daily mean bottom temperature anomalies in each LME. Calculated using the script                                                bhw_glorys_figure_shw_decay_rate.m included in the zip file.  
**ssta_daily_decorr_timescale_lme.mat** -  Same as before, but for sea surface temperature anomalies.  
**lme_lat.mat** & **lme_lon.mat**          -  The lat/lon coordinates of the LME shape files.  
**lme_mask2.mat**                      -  Masks outlining the different LMEs on the GLORYS grid. 

## 5. Observational comparison to GLORYS bottom temperature

Near-bottom temperature (NBT) measurements from 10 observing stations were collected to assess the fideltiy of GLORYS bottom temperature output. Each of these 10 locations required a certain level of processing to generate timeseries for comparison with GLORYS. We include the following processed observational data, along with the corresponding nearest GLORYS grid cells, in the zip folder. For details on the specific processing steps undertaken and for references for each observed dataset, see the Supplementary Information of the paper. Figures comparing the observations and GLORYS are created using the script glorys_obs_compare_all_stations.m.

**Observed NBT timeseries:**  
**Bering Sea (BS-M5)** - BS.M5.mon.mean.2005-2018.mat  
**Bering Sea (BS-M8)** - BS_mooring/BS.M8.mon.mean.2005-2018.mat  
**Gulf of Alaska (GAK1)** - GAK.mon.mean.1998-2018.mat  
**California Current System (Newport Line)** - Newport.1997-2019.T3.mat  
**Gulf of Mexico (West End CP)** - GOM.mon.mean.2004-2018.mat  
**Southeast US (Walton Smith)** - FS_quarterly_cruise/FS.mon.mean.2001-2019.mat  
**Northeast US (Martha's Vineyard)** - MVCO.mon.mean.2001-2018.mat  
**Northeast US (Passamaquoddy Bay)** - PB.int.mon.mean.1993-2018.mat  
**Scotian (Halfiax Line)** - hf.mon.mean.2000-2019.mat  
**Labrador (Station 27)** - Newf.mon.mean.1993-2019.mat  

**GLORYS NBT timeseries at nearest grid cell:**  
**Bering Sea (BS-M5)** - glorys.BS.M5.mon.mean.2005-2018.mat  
**Bering Sea (BS-M8)** - glorys.BS_mooring/BS.M8.mon.mean.2005-2018.mat  
**Gulf of Alaska (GAK1)** - glorys.GAK.mon.mean.1998-2018.mat  
**California Current System (Newport Line)** - glorys.Newport.1997-2019.T3.mat  
**Gulf of Mexico (West End CP)** - glorys.GOM.mon.mean.2004-2018.mat  
**Southeast US (Walton Smith)** - glorys.FS_quarterly_cruise/FS.mon.mean.2001-2019.mat  
**Northeast US (Martha's Vineyard)** - glorys.MVCO.mon.mean.2001-2018.mat  
**Northeast US (Passamaquoddy Bay)** - glorys.PB.int.mon.mean.1993-2018.mat  
**Scotian (Halfiax Line)** - glorys.hf2.mon.mean.2000-2019.mat  
**Labrador (Station 27)** - glorys.Newf.mon.mean.1993-2019.mat  
