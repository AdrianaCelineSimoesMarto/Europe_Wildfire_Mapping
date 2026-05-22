# Europe-Wildfire-Mapping

## Project Title & Description:

- Title: Wildfire Detection and Visualization in Europe using NASA FIRMS Data

This project aims to answer the following Question: **Where are active wildfire detections located across Europe, how do they vary in intensity and confidence and which countries experience the highest concentration of wildfire activity?**

The project combines data acquisition, spatial filtering, geospatial visualization and spatial aggregation techniques to provide an overview of current wildfire activity in Europe.

## Data Sources: 

The project uses two different data sources:

1. **NASA FIRMS MODIS Near Real-Time (NRT) wildfire data**, which is accessed directly through the NASA API and therefore does not need to be stored in the repository -> URL: https://firms.modaps.eosdis.nasa.gov/api/ 
2. A **European country boundary shapefile** used for the spatial join and country-level wildfire analysis. Due to file size limitations, the shapefile is not included in this repository. It needs to be downloaded separately. -> Available for download at: https://data.dtu.dk/articles/dataset/Shapefile_of_European_countries/23686383 

To run the project, place the shapefile and all associated files (`.shp`, `.shx`, `.dbf`, `.prj`, `.cpg`) inside the `data/` directory and ensure that the file path matches the one used in the notebook:

```python
europe_countries = gpd.read_file("data/Europe_merged.shp")
```

## Setup Instructions: 

This projects require the following libraries: 
```python
requests
pandas
geopandas
folium
matplotlib
contextily
```
Install the required packages using:

```bash
!pip install requests pandas geopandas folium matplotlib contextily
```
Before running the project, ensure that:

1. The European country shapefile and all associated files (`.shp`, `.shx`, `.dbf`, `.prj`, etc.) are stored in the `data/` directory.
2. A valid NASA FIRMS API key is available and inserted into the script. A key can be generated on the linked NASA website
3. All required Python libraries are installed.

## Execution Order: 

The project consists of a single notebook that performs the complete workflow.

Run the notebook from top to bottom in the following order:

1. Import libraries and connect to the NASA FIRMS API.
2. Download and filter wildfire detections for Europe.
3. Convert the data into a GeoDataFrame.
4. Create the interactive wildfire maps:
   - Confidence and Day/Night Detection Map
   - Confidence and Fire Radiative Power (FRP) Intensity Map
5. Perform the spatial join between wildfire detections and European country boundaries.
6. Generate the country-level wildfire count analysis.
7. Create the final choropleth map showing wildfire detections per country.

All sections should be executed sequentially, as later analyses depend on data generated in earlier steps.
