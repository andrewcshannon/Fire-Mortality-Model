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

# Read in Study Area Boundary
fri <- sf::st_read("../boundaries/4FRI_Dissolved.gpkg")
plot(fri$geom)

# Read in all 4FRI area
all_fri <- sf::st_read("../boundaries/4FRI_CFLR_InitiativeArea.gdb")
plot(all_fri$SHAPE)

# Read in Wallow Fire plots
W_sf <- sf::st_read("./NAU_fire_mort/Wallow/Wallow.gpkg")
plot(W_sf)

# Read in Leroux Fire plots 
L_sf <- sf::st_read("./NAU_fire_mort/Wallow/Leroux.gpkg")
plot(L_sf)

# Read in San Juan Fire plots
SJ_sf <- sf::st_read("./NAU_fire_mort/Wallow/SJ.gpkg")
plot(SJ_sf)

### PLOT STATES WITH NAU SF OBJECTS

us_states <- states(cb = TRUE, resolution = "20m") %>%
  shift_geometry()%>%
  sf::st_transform(st_crs(W_sf))

AZ <- us_states[us_states$STUSPS == "AZ",]

ggplot() +
  geom_sf(data=AZ) +
  geom_sf(data=all_fri, col='purple') +
  #geom_sf(data=fri) +
  geom_sf(data=W_sf, col = "red", size =2) +
  geom_sf(data=L_sf, col = "blue", size =2) +
  geom_sf(data=SJ_sf, col = "forestgreen", size =2)

```
![](imgs/StudyArea.svg)<!-- -->

![](imgs/WallowFireSev_withPlots.svg)<!-- -->
