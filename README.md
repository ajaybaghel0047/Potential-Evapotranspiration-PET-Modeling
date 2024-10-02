# Potential-Evapotranspiration-PET-Modeling
Compute PET using Penman-Monteith method


Overview of Drought Analysis Workflow Using ERA5 Data
This workflow focuses on calculating potential evapotranspiration (PET) by leveraging historical data from ERA5 land datasets. The key steps in the process include downloading the necessary meteorological variables, merging the data, calculating potential evapotranspiration (PET), and clipping the data to a region of interest for further analysis. Below is an outline of the steps involved:

Step 1: Data Download from Copernicus Climate Data Store (CDS)
Data Source: ERA5 reanalysis data, which provides a comprehensive set of atmospheric, land, and ocean variables.
Variables Downloaded:
2m temperature
2m dew point temperature
10m u and v wind components
Mean sea level pressure
Surface pressure
Surface net thermal and solar radiation
Time Period: From 1990 to 2023.
Geographical Area: Bounding box set for a region in India (North: 27, West: 74, South: 21, East: 83).


Step 2: Merging Year-Wise NetCDF Files
The downloaded data is stored in NetCDF format for each year.
The individual year-wise NetCDF files are merged into a single dataset spanning from 1990 to 2023.
This merged dataset simplifies further processing and enables seamless access to the time-series data for drought assessment.


Step 3: Calculation of Hourly Potential Evapotranspiration (PET)
The Penman-Monteith equation is used to calculate hourly Potential Evapotranspiration (hPET) based on various meteorological parameters:
Surface pressure (converted to kPa)
Air temperature (converted from Kelvin to Celsius)
Wind speed (calculated from u and v components at 10m height)
Net radiation (calculated from surface solar and thermal radiation)
Hourly PET is calculated, incorporating factors like vapor pressure, psychrometric constant, and wind speed.


Step 4: Conversion of Hourly PET to Daily PET
Hourly PET data is resampled to daily values, summing up the hourly PET for each day.
The resulting Daily PET (dPET) dataset is saved as a separate NetCDF file, providing a smoother dataset for long-term drought trend analysis.

Step 5: Clipping Data to a Specific Region
The daily PET data is clipped to the region of interest using a shapefile. In this case, the region is defined by the Madhya Pradesh district boundaries.
GeoPandas and rioxarray are used to read the shapefile and clip the dataset to the geographical area defined by the shapefile.
This operation ensures that only data relevant to the region of interest is retained, facilitating more focused drought analysis.


Summary
The described workflow provides a systematic approach to downloading and processing large-scale meteorological datasets for the purpose of drought assessment. Key steps include downloading data from the Copernicus Climate Data Store (CDS), merging it into a single dataset, calculating potential evapotranspiration using the Penman-Monteith equation, and clipping the results to a specific region.
