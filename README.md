# met_forcing_comparison

Title:

Clinton Alden
Geospatial Data Analysis
February 2024

This project will analyze the effectiveness of gridded meteorological 
products on forcing the Structure for Unifying Multiple Modeling Alternatives (SUMMA).

Forcing point snow models such as SUMMA typically draws on meteorological observations
using in situ observations as forcing. However, many of the snow-covered mountainous areas 
of Washington lack extensive meteorological observations. Additionally, many of 
the few meteorological sites that do exist lack radiative flux data that is critical 
to the accuracy of the modeled snowpack.

Research Questions - Can gridded meteorological products such as reanalysis and model
output from WRF be used as an accurate forcing dataset to force the SUMMA snow model?
How does the gridded data compare to meteorological observations within each grid cell
in complex topography?

Data - ERA5 reanalysis from the ECMWF, UW-Weather Research and Forecasting model from
the NASA Discover servers, meteorological and snow observations from NRCS SNOTEL network

Tools/packages - primarily xarray to access gridded products in netCDF format

Methodology - Data from SNOTEL sites will be compared to the grid cells they are located
in within the gridded model datasets to test the accuracy of these products in complex
topography. The SUMMA model will then be initialized using both gridded products and 
meteorological observations to further test the veracity of these data.

Expected Outcomes - Gridded products are hypothesized to not be an effective stand-in for
in situ observations for this purpose without further modifications to the original products. 
Additional analysis can be attempted to try to downscale gridded products to more accurately 
resolve complex topography with coarse reanalysis products that are widely available,
such as ERA5 from the ECMWF.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Repository Organization

`era5_analysis.ipynb` plots the era5 temperature and precipitation data for the Olympic
 Mountains and creates a gif of all daily plots for the water year.

`WA_DEM_plot.ipynb` reads in DEM data for the state of Washington and creates plots
to help orient the Buckinghorse SNOTEL station and adjacent topography.


