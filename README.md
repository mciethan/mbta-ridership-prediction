# mbta-ridership-prediction
Predicting station-level MBTA rail transit ridership using open data

Collaborators: Emmett Greenberg, Ted Banken, Ethan McIntosh
 
These scripts were developed in support of a school report we submitted for CIVE 7381 (Transportation Demand Forecasting and Model Estimation), a course taught by Professor Haris Koutospoulos at Northeastern University. 

Read the final report here: [Using Open Data to Enhance Station-Level Transit Ridership Models](https://docs.google.com/document/d/1bCEKMQc2sCZsuZDSd6N0AVITrZFgVIpXqUhIXhQ5qhY/edit?usp=sharing)

## Script descriptions

`model_building.Rmd` ingests and joins cleaned data at the route-station level to build the regression models, while also:
   - generating tables and charts of descriptive statistics
   - exporting formatted model outputs to `formatted_output.csv`
   - generating scatter plots of predicted vs actual ridership by route-station
   - generating maps summarizing model over- and under-prediction per station
   - conducting statistical tests and visualizations of residual normality and spatial autocorrelation

`data_cleaning.Rmd` ingests and cleans data sources and aggregates them to the season/route/station level where applicable, including:
   - MBTA rail rapid transit ridership
   - MBTA recap GTFS (to derive station locations, headways, terminal stops, interstation spacing, and bus + Commuter Rail connections)
   - MBTA travel times (to derive average travel times to the central business district)
   - Walking-distance buffer areas from the OpenRouteService API, with extra geoprocessing to compute non-overlapping areas per route
   - MBTA park-and-ride inventory from CTPS data
   - Calculating crow-flies distances from stations to the central business district
   - College locations and enrollments from NCES IPEDS data
   - Hotel and hospital locations from Analyze Boston
