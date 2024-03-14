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

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

Repository Organization

`era5_analysis.ipynb` plots the era5 temperature and precipitation data for the Olympic
 Mountains and creates a gif of all daily plots for the water year.

`WA_DEM_plot.ipynb` reads in DEM data for the state of Washington and creates plots
to help orient the Buckinghorse SNOTEL station and adjacent topography.

`buck_era5_proc.ipynb` processed era5 netcdf data using xarray and creates a forcing 
netcdf that can be used to initialize SUMMA. This same script can also be used to process
the WRF forcing as well with modifications to the variable names that WRF uses.

`buckinghorse_summa.ipynb` runs the SUMMA snow model using the pysumma fortran wrapper
using the era5 forcing dataset created with processing notebook.
	-note: there are many other set up files needed to run summa that are not
	included in this repo to keep it cleaner. See 
	https://pysumma.readthedocs.io/en/latest/index.html
	for further documentation on SUMMA initialization.
This script also plots several of the forcing and output variables and compares to
SNOTEL observations.

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

Results

In general, forcing a point snow model such as SUMMA with a course dataset such as ERA5
is not effective. This resolution of gridded reanalysis prodect fails to capture the true
complexity of the terrain in the Olympic Mountains and thus underrepresents precipitation in
upper elevation locations such as the Buckinghorse SNOTEL. Higher resolution products such as
the 4/3 km resolution UW-WRF has much higher skill in representing the precipitation in this 
complex topography and thus the SUMMA run forced by WRF had significatly lower Snow Water 
Equivalent RMSE than the ERA5 run when compared to SNOTEL SWE observations. Moving forward
with this work, higher resolution mesoscale models are the most appropriate for forcing 
point or high resolution snow models. In general, the resolution of the snow model should
somewhat approximate the resolution of the forcing data set to effectively capture the 
topographic complexity of mountains in Western Washington. Pulling points from gridded 
meteorological datasets to force SUMMA is a successful method of generating skillful
forcings as demonstrated with the WRF-initialized SUMMA run.
