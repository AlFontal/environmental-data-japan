# Japan's environmental Data

Repository collecting and organizing environmental data sources for Japan. 

Here, we have downloaded and processed the data available through the site made available by the Japanese National Institute for Environmental Studies (NIES) (https://tenbou.nies.go.jp/download/). 

More specifically, we have downloaded the Air Pollution Monitoring data for a total of 2039 stations located around the whole country (represented as red dots in the map below):

<img src="https://github.com/AlFontal/environmental-data-japan/raw/main/data/air_pollution/stations/doc/stations_map.png" alt="Japanese Monitoring Stations Map" title="Japanese Monitoring Stations Map">


## The stations

Information for the exact location of each station (latitude, longitude and altitude) and the environmental variables available can be found in the table in [`/data/air_pollution/stations/doc/stations_info.csv`](data/air_pollution/stations/doc/stations_info.csv)

## Variables measured

Since the repository includes data for over 2000 stations, the measured variables in each of them are rather heterogeneous. The data is provided in hourly format by the Japanese NIES, and the processed files available in this repository provide the data with a daily frequency, so an aggregation method has been used. The following table summarizes the selected variables, their units, and the aggregation method used to summarize them.

| **Variable** 	| **Name**                             	| **Units** 	|  **Aggregation Method** 	|
|:------------:	|--------------------------------------	|:---------:	|:-----------------------:	|
| **SO2**      	| Sulfur Dioxide                       	| ppm       	| Daily Mean              	|
| **NO**       	| Nitric Oxide                         	| ppm       	| Daily Mean              	|
| **NO2**      	| Nitrogen Dioxide                     	| ppm       	| Daily Mean              	|
| **NOX**      	| Nitrogen Oxides                      	| ppm       	| Daily Mean              	|
| **CO**       	| Carbon Monoxide                      	| ppm       	| Daily Mean              	|
| **OX**       	|    Photochemical Oxidants                                  	| ppm       	| Daily Mean              	|
| **NMHC**     	| Non-methane Hydrocarbons             	| ppmC      	| Daily Mean              	|
| **CH4**      	| Methane                              	| ppmC      	| Daily Mean              	|
| **THC**      	| Total Hydrocarbons                   	| ppmC      	| Daily Mean              	|
| **SPM**      	| Suspended Particulate Matter (<10µm) 	| mg/m³     	| Daily Mean              	|
| **PM2.5**    	| Particulate matter (<2.5µm)          	| µg/m³     	| Daily Mean              	|
| **TEMP**     	| Temperature                          	| °C        	| Daily Min, Mean and Max 	|
| **HUM**      	| Relative Humidity                    	| %         	| Daily Mean              	|
| **RAIN**     	| Total Precipitation                  	| mm        	| Daily Sum               	|


## Datasets


### Station data

Daily data for each station and its measured variables from 2011-01-01 to 2018-12-31 can be accessed in the [`data/air_pollution/stations/clean`](data/air_pollution/stations/clean) folder, classified in subfolders according to the prefecture where they are located.

### Municipalities 

Averaged daily data for all stations within each municipality in Japan during the same period can be found in the [`data/air_pollution/municipalities`](data/air_pollution/municipalities/) folder, with the first 2 digits of each CSV file indicating the prefecture code and the last 3 digits indicating the municipal code.

### Prefectures

Averaged daily data for all municipalities within each prefecture in Japan can be found in the [`data/air_pollution/prefectures`](data/air_pollution/prefectures/) folder. Since the objective of the prefectural averages is to represent the *exposure* of the population to the measured environmental variables, the municipal values are averaged weighting by the share of population living in them. At this moment, the only available values are those averaged weighting by the population of children under 5 years old in each municipal term, but more will likely be added.

