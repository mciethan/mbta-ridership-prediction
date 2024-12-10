# mbta-ridership-prediction
Predicting station-level MBTA rail transit ridership using open data

Collaborators: Emmett Greenberg, Ted Banken, Ethan McIntosh
 
These scripts were developed in support of a school report we submitted for CIVE 7381 (Transportation Demand Forecasting and Model Estimation), a course taught by Professor Haris Koutsopoulos at Northeastern University. 

Read the final report here: [Using Open Data to Enhance Station-Level Transit Ridership Models](https://docs.google.com/document/d/1bCEKMQc2sCZsuZDSd6N0AVITrZFgVIpXqUhIXhQ5qhY/edit?usp=sharing)

## Script descriptions

`model_building.Rmd` ingests and joins cleaned data at the route-station level to build the regression models, while also generating:
   - descriptive statistics of model variables (tables and charts)
   - formatted model outputs, including VIF and RMSE in addition to the default R regression outputs (exported to `formatted_output.csv`)
   - scatter plots of predicted vs actual ridership by route-station
   - maps summarizing over- and under-prediction per station
   - statistical tests and visualizations of the normality and spatial autocorrelation of residuals

`data_cleaning.Rmd` ingests and cleans data sources and aggregates them to the season/route/station level where applicable, including:
   - MBTA rail rapid transit ridership
   - MBTA recap GTFS feeds (to derive station locations, headways, terminal stops, interstation spacing, and bus + Commuter Rail connections)
   - MBTA travel times (to derive average travel times to the central business district)
   - Walking-distance buffer areas from the OpenRouteService API, with extra geoprocessing to compute non-overlapping walksheds per route
   - MBTA park-and-ride inventory from CTPS data
   - Straight-line distances from stations to the central business district
   - College locations and enrollments from NCES IPEDS data
   - Hotel and hospital locations from Analyze Boston

`get_land_use_entropy.ipynb` calculates land use entropy from MassGIS parcel data

`data/walk_score/get_walkscore.ipynb` queries the Walk Score API for rapid transit station coordinates

`data/airbnb/get_abnbs.ipynb` calculates Airbnb listing counts and densities from Inside Airbnb to the route-station walkshed level

`data/wac/cut_wac.ipynb` intersects census-block-level job counts from LODES with the route-station walksheds to calculate job densities