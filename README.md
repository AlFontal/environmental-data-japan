# Japan's environmental Data

![License Badge](https://img.shields.io/github/license/AlFontal/environmental-data-japan?color=blue)
![Pages Badge](https://github.com/AlFontal/environmental-data-japan/actions/workflows/deploy.yml/badge.svg)
[![Pages site badge](https://img.shields.io/badge/Pages%20Site-Online-green)](https://alfontal.github.io/environmental-data-japan)

[![Stations data](https://img.shields.io/badge/Stations-Download-orange)](https://github.com/AlFontal/environmental-data-japan/tree/main/data/air_pollution/stations/clean)
[![Municipal data](https://img.shields.io/badge/Municipalities-Download-orange)](https://github.com/AlFontal/environmental-data-japan/tree/main/data/air_pollution/municipalities)
[![Prefectures data](https://img.shields.io/badge/Prefectures-Download-orange)](https://github.com/AlFontal/environmental-data-japan/tree/main/data/air_pollution/prefectures)

Repository collecting and organizing environmental data sources for Japan.

Here, we have downloaded and processed the data available through the site made available by the Japanese National Institute for Environmental Studies (NIES) (<https://tenbou.nies.go.jp/download/>).

More specifically, we have downloaded the Air Pollution Monitoring data for a total of 2039 stations located around the whole country (represented as red dots in the map below):

<img src="https://github.com/AlFontal/environmental-data-japan/raw/main/data/air_pollution/stations/doc/stations_map.png" alt="Japanese Monitoring Stations Map" title="Japanese Monitoring Stations Map" width=500px>

## The stations

Information for the exact location of each station (latitude, longitude and altitude) and the environmental variables available can be found in the table in [`/data/air_pollution/stations/doc/stations_info.csv`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/stations/doc/stations_info.csv)

## Variables measured

Since the repository includes data for over 2000 stations, the measured variables in each of them are rather heterogeneous. The data is provided in hourly format by the Japanese NIES, and the processed files available in this repository provide the data with a daily frequency, so an aggregation method has been used. The following table summarizes the selected variables, their units, and the aggregation method used to summarize them.

| **Variable**  | **Name**                              | **Units**  |  **Aggregation Method**  |
|:------------: |-------------------------------------- |:---------: |:-----------------------: |
| **SO2**       | Sulfur Dioxide                        | ppm        | Daily Mean               |
| **NO**        | Nitric Oxide                          | ppm        | Daily Mean               |
| **NO2**       | Nitrogen Dioxide                      | ppm        | Daily Mean               |
| **NOX**       | Nitrogen Oxides                       | ppm        | Daily Mean               |
| **CO**        | Carbon Monoxide                       | ppm        | Daily Mean               |
| **OX**        | Photochemical Oxidants                | ppm        | Daily Mean               |
| **NMHC**      | Non-methane Hydrocarbons              | ppmC       | Daily Mean               |
| **CH4**       | Methane                               | ppmC       | Daily Mean               |
| **THC**       | Total Hydrocarbons                    | ppmC       | Daily Mean               |
| **SPM**       | Suspended Particulate Matter (<10µm)  | mg/m³      | Daily Mean               |
| **PM2.5**     | Particulate matter (<2.5µm)           | µg/m³      | Daily Mean               |
| **TEMP**      | Temperature                           | °C         | Daily Min, Mean and Max  |
| **HUM**       | Relative Humidity                     | %          | Daily Min, Mean and Max  |
| **RAIN**      | Total Precipitation                   | mm         | Daily Sum                |



## Datasets

### (1) Station data

Daily data for each station and its measured variables from 2011-01-01 to 2018-12-31 can be accessed in the [`data/air_pollution/stations/clean`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/stations/clean) folder, classified in subfolders according to the prefecture where they are located.

### (2) Municipalities

Averaged daily data for all stations within each municipality in Japan during the same period can be found in the [`data/air_pollution/municipalities`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/municipalities/) folder, with the first 2 digits of each CSV file indicating the prefecture code and the last 3 digits indicating the municipal code.

### (3) Prefectures

Estimates of the daily data for each prefecture have been estimated by averaging over the municipal averages in each prefecture.

At this point, three different methods have been used to compute the averages, weighing the municipalities differently according to diverse criteria:

+ **Area-based weighted averages**: These averages are completely population-naïve and try to better estimate the overall values for each variable across the whole area of the prefecture, wheighing high and low population density areas exactly the same. The time-series for these can be found in [`data/air_pollution/prefectures/area_weighted`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/prefectures/area_weighted).

+ **Population-weighted averages**: These averages are computed trying to estimate the values of each variable that represent the most accurate exposure of the population of each prefecture to each pollutant/meteorological variable. For these purpose, the values for each variable have been averaged weighing every municipal term according to their population share in the prefecture. The time-series for these can be found in [`data/air_pollution/prefectures/population_weighted`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/prefectures/population_weighted).

+ **Infant population-weighted averages**: Following the same principal as the previous averages, these include the daily prefecture-level estimates of each measured variable based on the share of *children under 5 years old* in each municipal term. The time-series for these can be found in [`data/air_pollution/prefectures/under_5_weighted`](https://github.com/AlFontal/environmental-data-japan/data/air_pollution/prefectures/under_5_weighted).
