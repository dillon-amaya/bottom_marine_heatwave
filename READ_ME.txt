%This code calculates average intensity, duration, spatial extent, and synchrony for
%BMHWs and SMHWs in each LME. All main text Figures and most of the
%Supplementary Information Figures are then made at the end of this script
%using series of functions. User input decides which figure to make. User
%also decides whether to process detrended or raw (e.g., not detrended) by
%changing the parameter "M" in the section titled "Decide whether or not to
%removing warming trend". 

%Data required to run this script includes: GLORYS monthly mean bottomT,
%sst, and mld from 1993-2019. Available at: https://data.marine.copernicus.eu/product/GLOBAL_MULTIYEAR_PHY_001_030/description
%Other processed data (e.g., decorrelation maps, lme masks, etc) are provided in our github repository https://github.com/dillon-amaya/bottom_marine_heatwave
%You'll need to change the paths to point to the GLORYS data on whatever system you're working with.



Attached are two items: 1. A zip file, which has all the data and MATLAB scripts/functions needed to reproduce every figure I've shown you so far, and 2. A "master" script, which you should be able to run out of the box that controls everything. To make the master script work, you'll need to change the "pathID" variable at the top to point to the unzipped folder. 

Inside the master script, there are two choices you can make to process the data differently or plot different things. 1. You can decide what order polynomial fit to use when detrending the data (starting at Line 67), and 2. You can choose whether to process/plot the detrended or raw data (starting at Line 94). To make the changes, you'll have to go in and uncomment a section of code or change the value of a variable. At the end of the master script are 3 functions that make the plots I've shown. They require the MATLAB Mapping Toolbox, so hopefully they'll still work for you.

Please let me know if this package works for y'all or if you see any issues with the code. I've tried to comment throughout to make it more clear what the code is trying to do in each section, but please also let me know if you have any questions.
