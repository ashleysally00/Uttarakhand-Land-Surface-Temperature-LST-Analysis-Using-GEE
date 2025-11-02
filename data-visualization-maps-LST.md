
# Data Visualization: Land Surface Temperature (LST) Analysis for Uttarakhand

These Land Surface Temperature (LST) maps visualize temperature patterns across Uttarakhand for the year 2024. Understanding temperature distribution for day and night can help identify high-risk areas and supports better emergency response planning in the region.

### Daytime LST

![Mean Daytime LST Map for Uttarakhand 2024](./images/MeanLSTday2024.png)

* Description: This map shows how the Earth's surface heats up during the day in 2024. Urban areas, bare soil, and low-lying regions absorb more heat, leading to higher temperatures (red areas).
* Use Case: Identifying regions prone to excessive daytime heating, which can influence wildfire risk.

### Nighttime LST

![Mean Nighttime LST Map for Uttarakhand 2024](./images/meanLSTnight2024.png)


* Description: This map shows how the Earth's surface cools down at night. Vegetation and water bodies lose heat faster, resulting in cooler temperatures (blue areas), while urban regions retain heat, forming urban heat islands (red areas).
* Use Case: Understanding nighttime cooling dynamics, crucial for wildfire spread predictions and ecosystem resilience.

## Why Are These Maps Important for the Project?

The project focuses on wildfire prediction, and temperature dynamics play a significant role in:

### Wildfire Risk Assessment
* Hotter surface areas (day or night) are more likely to dry vegetation, increasing fire susceptibility.
* Urban heat islands can exacerbate fire risks near cities.

### Environmental Patterns
* Comparing daytime and nighttime temperatures highlights areas with extreme fluctuations, which could affect fire behavior.

### Resource Allocation
* Identifying high-risk areas enables better planning for fire mitigation and emergency responses.

## What Type of Maps Are These?

These are Land Surface Temperature (LST) Maps, which visualize the average temperature of the Earth's surface in Kelvin for a given time frame (2024 in this case).

* Daytime LST Map: Captures the average surface temperature during the daytime for the entire year.
* Nighttime LST Map: Captures the average surface temperature during the nighttime for the entire year.

These maps are generated from MODIS satellite data, specifically the MOD11A1 product, which measures thermal infrared radiation emitted by the Earth's surface. They are not traditional heat maps but scientific temperature maps that represent real satellite measurements.

## Color-Coding on the Maps

* Blue: Cooler areas such as water bodies, vegetated regions, or high-altitude areas.
* Green to Red: Warmer areas, including urban regions, bare ground, or low-lying areas.

## How Were These Maps Made?

The maps were created using the following steps in Python, leveraging Google Earth Engine (GEE) and the geemap library:

### Dataset
The MODIS/061/MOD11A1 dataset was loaded, which provides daily Land Surface Temperature (LST) data at a 1 km resolution.

### Region of Interest
The dataset was clipped to the Uttarakhand boundary using a shapefile stored in the GEE assets.

### Date Range
The dataset was filtered for the year 2024, selecting images between 2024-01-01 and 2024-12-31.

### Daytime and Nighttime LST Bands
Two specific bands were extracted:

- LST_Day_1km: Daytime surface temperature
- LST_Night_1km: Nighttime surface temperature

### Mean Calculation
The mean was computed over the entire year for both daytime and nighttime bands to generate a single annual summary for each.

### Scaling
The raw MODIS data values were scaled to Kelvin by multiplying by 0.02.

### Visualization
The processed LST data was visualized on interactive maps using the geemap library, with a color gradient ranging from blue (cool) to red (warm).

### Python Code for Map Creation
The following Python code was used to create the Mean Daytime LST Map:
```
# Install required libraries (if not installed)
!pip install geemap earthengine-api

# Import libraries
import ee
import geemap

# Authenticate and Initialize Earth Engine
ee.Authenticate()
ee.Initialize()

# Load the Uttarakhand shapefile from Earth Engine Assets
uttarakhand = ee.FeatureCollection("projects/ee-ashleysally00/assets/Uttarakhand-boundary")

# Load the MODIS dataset
modis = ee.ImageCollection("MODIS/061/MOD11A1")

# Clip MODIS dataset to the Uttarakhand boundary
modis_clipped = modis.map(lambda img: img.clip(uttarakhand))

# Define the date range (e.g., 2024)
start_date = '2024-01-01'
end_date = '2024-12-31'

# Filter MODIS dataset for the date range
modis_filtered = modis_clipped.filterDate(start_date, end_date)

# Extract and process the daytime LST band
mean_lst_day = modis_filtered.select('LST_Day_1km').mean().multiply(0.02).rename('Mean_LST_Day')

# Initialize a map using geemap
Map = geemap.Map()

# Center the map on Uttarakhand
Map.centerObject(uttarakhand, 8)

# Add the mean daytime LST layer to the map
Map.addLayer(
    mean_lst_day, 
    {'min': 250, 'max': 320, 'palette': ['blue', 'green', 'red']}, 
    'Mean Daytime LST'
)

# Display the map
Map
```
The following Python code was used to create the Mean Nighttime LST Map:

```
# Install required libraries (if not installed)
!pip install geemap earthengine-api

# Import libraries
import ee
import geemap

# Authenticate and Initialize Earth Engine
ee.Authenticate()
ee.Initialize()

# Load the Uttarakhand shapefile from Earth Engine Assets
uttarakhand = ee.FeatureCollection("projects/ee-ashleysally00/assets/Uttarakhand-boundary")

# Load the MODIS dataset
modis = ee.ImageCollection("MODIS/061/MOD11A1")

# Clip MODIS dataset to the Uttarakhand boundary
modis_clipped = modis.map(lambda img: img.clip(uttarakhand))

# Define the date range (e.g., 2024)
start_date = '2024-01-01'
end_date = '2024-12-31'

# Filter MODIS dataset for the date range
modis_filtered = modis_clipped.filterDate(start_date, end_date)

# Extract and process the nighttime LST band
MeanLSTNight2024 = modis_filtered.select('LST_Night_1km').mean().multiply(0.02).rename('Mean_LST_Night_2024')

# Initialize a map using geemap
Map = geemap.Map()

# Center the map on Uttarakhand
Map.centerObject(uttarakhand, 8)

# Add the mean nighttime LST layer to the map
Map.addLayer(
    MeanLSTNight2024, 
    {'min': 250, 'max': 320, 'palette': ['blue', 'green', 'red']}, 
    'Mean Nighttime LST 2024'
)

# Display the map
Map

```
