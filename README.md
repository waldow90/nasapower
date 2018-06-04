nasapower: NASA-POWER Agroclimatology Data from R
================

[![Travis-CI Build
Status](https://travis-ci.org/adamhsparks/nasapower.svg?branch=master)](https://travis-ci.org/adamhsparks/nasapower)
[![AppVeyor Build
Status](https://ci.appveyor.com/api/projects/status/github/adamhsparks/nasapower?branch=master&svg=true)](https://ci.appveyor.com/project/adamhsparks/nasapower)
[![Coverage
Status](https://img.shields.io/codecov/c/github/adamhsparks/nasapower/master.svg)](https://codecov.io/github/adamhsparks/nasapower?branch=master)
[![DOI](https://zenodo.org/badge/109224461.svg)](https://zenodo.org/badge/latestdoi/109224461)
[![Project Status: WIP – Initial development is in progress, but there
has not yet been a stable, usable release suitable for the
public.](http://www.repostatus.org/badges/latest/wip.svg)](http://www.repostatus.org/#wip)

## Introduction

<img align="right" src="man/figures/nasapower-hex.png"> *nasapower* aims
to make it quick and easy to automate downloading
[NASA-POWER](https://power.larc.nasa.gov) agroclimatology data in your R
session as a tidy data frame for agricultural analysis and use in
modelling or other purposes. POWER (Prediction Of Worldwide Energy
Resource) data are freely available for download through a web interface
at a resolution of 0.5˚ longitude by 0.5˚ latitude.

Please see <https://power.larc.nasa.gov/> for more on the data and other
ways to access it and other forms of data available, e.g. an ESRI REST
API.

### Quick start

With the changes to the NASA/POWER data and API, this package is a
work-in-progress under active development, install at your own risk.

*nasapower* is not available from CRAN, only GitHub. It can easily be
installed using the following code:

``` r
if (!require(devtools)) {
  install.packages("devtools")
  library(devtools)
}

devtools::install_github("adamhsparks/nasapower", build_vignettes = TRUE)
```

## Introduction

*nasapower* aims to make it quick, easy and efficient to automate
downloading NASA-POWER agroclimatology data in your R session as a tidy
data frame.

*nasapower* only provides one function, `get_power()`, which will
download specified variables and return a tidy data frame of the
requested data. Weather variables can be specified by using the `pars`
argument.

## Using get\_power()

The `get_power()` function requires five arguments as seen in this
example, which will fetch relative humidity (RH2M) and temperature (T2M)
for the year 1985 on a daily time-step.

``` r
power <- get_power(community = "AG",
                   latlon = c(-89.5, -179.5),
                   pars = c("RH2M", "T2M"),
                   dates = c("1985-01-01", "1985-12-31"),
                   temporal_average = "daily")
```

The arguments are:

  - `community`, a text string with valid values of: “AG”
    (Agroclimatology), “SSE” (Surface meteorology and Solar Energy) or
    “SB” (Sustainable Buildings). The selected user community will
    affect the units of the parameter and the temporal display of time
    series data (*e.g.* Agroclimatology will use MJ/m<sup>2</sup>/day
    for radiation units, while SSE and SB use kW/m<sup>2</sup>/day as
    units).

  - `latlon`, a length-2 numeric vector giving the decimal degree
    latitude and and longitude coordinates in that order for cell data
    to download or a length-4 numeric vector giving the decimal degree
    longitude and and latitude coordinates forming a bounding box as
    ymin, xmin, ymax, xmax in that order.

  - `pars`, a character vector of weather variables to query for
    download. For a complete listing of valid `pars`, please see column
    1 of the package included data, `parameters`, e.g., using RStudio,
    `View(parameters)`.

  - `dates`, a vector of start and end dates for which to query the
    NASA-POWER API

  - `temporal_average`, a character vector of the desired temporal
    average(s). Valid values are “DAILY”, “INTERANNUAL” and
    “CLIMATOLOGY”.

## Documentation

More documentation is available in the vignette in your R session,
`vignette("nasapower")` or available online,
<https://adamhsparks.github.io/nasapower/articles/nasapower.html>.

## Use of POWER Data

While *nasapower* does not redistribute the data or provide it in any
way, we encourage users to follow the requests of the POWER Project
Team.

> When POWER data products are used in a publication, we request the
> following acknowledgment be included: “These data were obtained from
> the NASA Langley Research Center POWER Project funded through the NASA
> Earth Science Directorate Applied Science Program.”

## Meta

  - Please [report any issues or
    bugs](https://github.com/adamhsparks/nasapower/issues).

  - License: MIT

  - Get citation information for `nasapower` in R by typing
    `citation(package = "nasapower")`.

  - Please note that this project is released with a [Contributor Code
    of Conduct](CONDUCT.md). By participating in this project you agree
    to abide by its terms.

  - The U.S. Earth System Research Laboratory, Physical Science Division
    of the National Atmospheric & Oceanic Administration (NOAA)
    maintains a list of gridded climate data sets that provide different
    data and different resolutions
    <https://www.esrl.noaa.gov/psd/data/gridded/>.

## References

<https://power.larc.nasa.gov>

<https://power.larc.nasa.gov/documents/Agroclimatology_Methodology.pdf>
