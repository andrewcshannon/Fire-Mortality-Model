# Fire-Mortality-Model
Parameterizing an empircal model of species-specfic, fire-induced tree mortality for the Southwest U.S. 

Here, we use plot-level tree mortality records from the Fire & Tree Mortality Database (Cansler et al. 2022) <a href="https://www.fs.usda.gov/rds/archive/catalog/RDS-2020-0001-2">Fire and tree mortality database</a>

``` r
library(data.table)
library(dplyr)
library(tigris)
library(ggplot2)
library(sf)
library(raster)
library("tidyverse")
```
![](imgs/StudyArea.svg)<!-- -->

![](imgs/WallowFireSev_withPlots.svg)<!-- -->
