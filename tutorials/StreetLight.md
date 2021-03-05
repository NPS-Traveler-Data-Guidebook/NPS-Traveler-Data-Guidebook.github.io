# StreetLight data

source: `{{ page.path }}`

## Evaluation of Bicyclist and Pedestrian Streetlight Data

This tutorial is hosted at [this Github respository](https://github.com/VolpeUSDOT/PLT-Web-Map). The repo contains an number of scripts to process and analyze data from the Streetlight Data platform for pedestrian and bicyclist crash rate evaluation.

The data was obtained by the Office of the Undersecretary of Transportation for Policy for evaluation purposes. The pilot focuses on 50 intersections in Philadelphia, Pennsylvania, located along the High Injury Network in Philadelphia.

## Obtain data and code

To conduct evaluation of the data, contact Paul Teicher (paul.teicher@dot.gov) for access to the data zip file.

## Using this code

The working code is written in R. Recommended setup is to use [the latest version of R](https://cran.r-project.org/) with the optional open-source development environment [RStudio](https://rstudio.com/).

Once the data is obtained an unzipped in a folder `data` inside this directory, the following code can be run. First, if using RStudio, double-click `stld.Rproj` to launch R with the working directory set to this code respository.

1. `Compile_monthly.R`
  + Compiles the downloaded files across the study period into a single data frame  
  + Produces plots of bicyclists trip length, trip duration, and index values for each month as time-series plots.

2. `Join_Calc_Crash.R`
  + Uses the annual total files for Pedestrians, Bicyclists, and Vehicles from Streetlight Data, and joins with crash data from PennDOT.
  + Produces crash rate calculations using FHWA methodology for intersections, using vehicle counts as the denominator
  + Produces plots and analysis of crash rates for bicyclists, pedestrians, and vehicles for a given study year (2018 or 2019).

Experimental code includes `Calibrate_Bicyclists.R`, which assesses which locations with ground-truth crash data could potentially have been used for calibration of the Streetlight Data Index values for bicyclists. Additional code was written in Python in the directory `code_v0`, which is kept as reference but was not used in generating the report.
