# socal-greenspace
 An analysis of access to green space in Southern California at the census tract level.

![Map of census tracts in Los Angeles and Orange Counties, color-coded by vegetation index.](https://github.com/jhirner/socal-greenspace/blob/95d5d0f2399121c3afa27c6fedb71566eb991f92/images/map.png "Vegetation Index in LA and Orange Counties by Census Tract")

## Motivation & Purpose
This project focuses on access to green space in Los Angeles and Orange counties in Southern California. To what extent is neighborhood access to parks, gardens, and other green space linked to socioeconomic factors.

This project aims to:

* Quantify differences in the "greenness" of each neighborhood in LA and Orange counties.

* Explore which socioeconomic and demographic factors, if any, correlate to each neighborhood's access to green spaces.


## Contents
This repository contains:

* A series of Jupyter notebooks in which the data is wrangled, cleaned, and analyzed:

    * Socioeconomic and demographic data were obtained at the census tract level from the US Census Bureau's [2020 American Community Survery five-year estimates](https://www.census.gov/programs-surveys/acs/news/data-releases/2020/release-schedule.html). Basic data wrangling & cleaning are shown in `1-census-data-cleaning.ipynb`.

    * Satellite imagery data ([MODIS/Aqua 16-day averged images, 250 meter resolution](https://lpdaac.usgs.gov/products/myd13q1v061/)) were used to determine amount of vegetation in 250 m<sup>2</sup> pixels in the two counties. Vegetation was quantified as the Normalized Difference Vegetation Index, or *NDVI*. Using [geographic boundaries](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.2020.html) provided by the Census Bureau, an average vegetation index was calculated for each census tract.(See `2-tract-vegetation.ipynb`).

    * Potential correlations are explored, quantified, and plotted in `3-join-and-visualize.ipynb`. Principal component analysis & additional visualization are shown in `4-dimensionality-reduction.ipynb`.

* The processed data necessary to reproduce & extend this analysis:

    * A SQLite database, `greenspace.db`, with cleaned, tract-level American Community Survey data in the `demographics`, `economics`, and `housing` tables. The database also contains tract-level vegetation indeces in the `ndvi` table.

    * Socioeconomic and demographic factors that were found to correlate to tract-level green space are extracted and highlighted in `greenspace_highlights.csv`.

* Within the `images` subdirectory, a select few images and plots generated during this analysis.


## Further work
There are a number of opportunities to extend this project. Some ideas that I may revisit in the future include:

* Extension to other parts of Southern California, particularly the remaining coastal counties (San Diego, Ventura, and Santa Barbara).

* Exploring how the correlations identified here have changed over time. Currently, the analysis only uses the most recent American Community Survey socioeconomic data (2020) and vegetation data from a 16-day period in 2021.

## Requirements
If you wish to reproduce or extend this analysis, the following Python 3 libraries or compatible versions are requried:

* contextily 1.2.0

* geopandas 0.9.0

* matplotlib 3.5.3

* numpy 1.22.2

* rasterio 1.3.2

* rioxarray 0.12.0

* seaborn 0.12.1

* scikit-learn 1.1.1

* scipy 0.9.0

* sqlalchemy 1.4.31

* xarray 2022.6.0
