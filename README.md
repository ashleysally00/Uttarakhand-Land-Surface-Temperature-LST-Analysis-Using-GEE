# Uttarakhand Land Surface Temperature (LST) Analysis for Fire Prediction ML

This repository contains a Python notebook that uses Google Earth Engine (via its Python API) to preprocess Land Surface Temperature (LST) data for a machine learning project focused on wildfire prediction. Land Surface Temperature (LST) measures the temperature of the Earth's surface, which includes soil, vegetation, and built-up areas. It is derived from satellite thermal infrared data and reflects the heat emitted from the ground. This thermal information helps assess how different surfaces interact with heat - a critical factor in determining wildfire risk.

To better predict how fires might behave in the future, we analyzed data from **January 2012 to June 30, 2024**, focusing on Uttarakhand (though you can modify the geographic region to suit your specific research).

The analysis uses Google Earth Engine (GEE) to process the `MODIS/061/MOD11A1` dataset. The data is clipped to any user-defined region using a shapefile, resampled to 500m resolution, and exported for further analysis.

## Collaborator Checklist
Before starting work on this project, ensure you have:
- [ ] Google account with access to Google Colab
- [ ] Google Earth Engine account with approved access
- [ ] Google Cloud Console project set up
- [ ] Google Drive API enabled (if planning to export results)
- [ ] Access to the project's shapefile assets
- [ ] Tested your GEE authentication in Colab

## Table of Contents
1. [Objective](#objective)
2. [Requirements](#requirements)
3. [Setup Instructions](#setup-instructions)
4. [Data Workflow](#data-workflow)
5. [How to Use](#how-to-use)
6. [Output](#output)
7. [Handling Task Queue Errors](#handling-task-queue-errors)
8. [Further Exploration](#further-exploration)

## Objective

This project provides a framework for analyzing daily LST data for any user-defined region. It is designed to:
- Extract daytime and nighttime LST data from the MODIS `MOD11A1` dataset
- Allow users to specify their region of interest (ROI) by uploading a shapefile
- Resample the data from 1 km to 500m resolution for more accurate analysis

## Requirements

To reproduce the results, the following tools and libraries are required:
- A Google account with access to:
  - [Google Earth Engine](https://earthengine.google.com/)
  - [Google Cloud Console](https://console.cloud.google.com/)
  - [Google Colab](https://colab.research.google.com/)
- Python libraries:
  - `earthengine-api`
  - `geemap`

## Setup Instructions

### Google Earth Engine
1. **Register for Google Earth Engine**:
   - Visit [Google Earth Engine](https://earthengine.google.com/) and sign in with your Google account
   - Apply for access (if not already approved)

   ![Earth Engine Sign Up](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/blob/main/get%20started.png?raw=true)

2. **Choose Your Account Type:**
   For academic research purposes, select "Unpaid Usage":

   ![Earth Engine Account Type](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/blob/main/unpaid.png?raw=true)

   - Once approved, you'll see the Code Editor interface:

   <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/GEE-code-editor.png" width="740" alt="Google Earth Engine Code Editor Interface"/>

2. **Upload a Shapefile**:
   - Go to the **Earth Engine Code Editor**
   - In the **Assets** tab, click the "NEW" button and select "Shape files"

   - You'll see this upload interface:

   <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/uploadfile-shapefile-gee.png" width="300" alt="Shapefile upload interface in GEE"/>

<br>
<br>
<br>
   - After successfully uploading, you'll see your shapefile in the Assets tab:
<br>
<br>
<br>
<br>
   <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/shapefile-in-GEE%20.png" width="700" alt="Uttarakhand Boundary Shapefile in GEE"/>

   - Note the **Asset ID** for use in your code
   
### Google Cloud Console
1. **Create a Project**:
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project or select an existing one:

   <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/google-cloud-console-project.png" width="720" alt="Google Cloud Console Project Interface"/>

<br>

2. **Enable Earth Engine API**:
   - In the **APIs & Services > Library** section, search for **Earth Engine API**
   - You should see the following screen:

   <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/GEEAPI.png" width="300" alt="Google Earth Engine API Screen"/>
   
   - Click "MANAGE" or "ENABLE" (if not already enabled)
   - When successfully enabled, you'll see a green checkmark with "API Enabled" as shown in the image above

3. **Optional: Enable Google Drive API**:
   - If exporting results to Google Drive, enable the **Google Drive API**

### Google Colab Setup
1. Open a new notebook in Colab

2. Install required libraries:
   ```bash
   !pip install earthengine-api geemap
   ```

3. Authenticate Earth Engine:
   ```python
   import ee
   ee.Authenticate()
   ee.Initialize()
   ```

## Data Workflow

1. **Load MODIS Dataset**:
   - The MODIS/061/MOD11A1 dataset is filtered for the user-specified time range

2. **Clip to User-Defined ROI**:
   - The dataset is clipped to the boundary defined by the uploaded shapefile

3. **Resample to 500m**:
   - The data is resampled from 1 km to 500m resolution using bilinear interpolation

4. **Extract and Scale LST**:
   - Daytime (LST_Day_1km) and nighttime (LST_Night_1km) bands are extracted
   - Data is scaled to Kelvin (value * 0.02)

5. **Export**:
   - Mean LST for the time range or daily time-series data is exported as GeoTIFF or CSV to Google Drive

## How to Use

1. **Open the Colab Notebook**:
   - Download the .ipynb file from the shared repository or run it directly in Colab

2. **Update the Parameters**:
   - Replace `users/your_username/Region_Boundary` with your shapefile's Asset ID
   - Specify the date range (e.g., 2012-01-01 to 2024-06-30)

3. **Run the Notebook**:
   - Authenticate GEE and Google Drive when prompted

4. **Download the Outputs**:
   - Access the exported files from your Google Drive folder (default: EarthEngineExports)

## Output

### 1. Mean LST (Day and Night)
- The Colab notebook processes and exports the **mean daytime and nighttime LST** data for the entire time range (**January 2012 to June 30, 2024**).
- These GeoTIFF files summarize the average Land Surface Temperature for the given period.
- **Accessing the Output**:
  - The files are saved in Google Drive under the folder `EarthEngineExports`.
  - The filenames are:
    - `Mean_LST_Day.tif` (for daytime mean)
    - `Mean_LST_Night.tif` (for nighttime mean).

### 2. Daily Time-Series LST (Day and Night)
To extract daily LST data for the specified time range (**January 2012 to June 30, 2024**), additional Python code needs to be added to the Colab notebook. This processes and exports daily LST data as GeoTIFF files for both daytime and nighttime.

### 3. Accessing Daily LST Outputs
- **Google Drive Location**:
  - Daily LST outputs are saved in the folder `EarthEngineExports/Daily` in your Google Drive.
  - Each file is named in the format:
    - `LST_Day_YYYY-MM-DD.tif` (e.g., `LST_Day_2012-01-01.tif` for daytime LST on January 1, 2012)
    - `LST_Night_YYYY-MM-DD.tif` (e.g., `LST_Night_2012-01-01.tif` for nighttime LST on January 1, 2012).

- **Processing Time**:
  - Exporting daily LST data for an extended time range (**January 2012 to June 30, 2024**) may take a while.
  - Below is an example of the Colab output during the process:

 <img src="https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/processingdaily-LST.png" alt="Processing Daily LST Data" width="500"/>



#### Python Code for Daily LST Exports
Add the following Python code to the end of your Colab notebook to generate and export the daily LST data:

```python
import datetime
import ee

# Authenticate and initialize Earth Engine (if not already done)
ee.Authenticate()
ee.Initialize()

# Load the MODIS LST dataset
modis = ee.ImageCollection("MODIS/061/MOD11A1")

# Load the Uttarakhand shapefile (replace with your shapefile's Asset ID)
uttarakhand = ee.FeatureCollection("projects/ee-your-project-id/assets/Uttarakhand-boundary")

# Generate a list of dates from 2012-01-01 to 2024-06-30
start_date = datetime.date(2012, 1, 1)
end_date = datetime.date(2024, 6, 30)
dates = [start_date + datetime.timedelta(days=i) for i in range((end_date - start_date).days + 1)]

# Iterate through each date and process LST data
for date in dates:
    date_str = date.strftime('%Y-%m-%d')
    print(f"Processing LST data for {date_str}...")
    
    # Filter MODIS dataset for the specific date
    daily_modis = modis.filterDate(date_str, (date + datetime.timedelta(days=1)).strftime('%Y-%m-%d'))
    
    # Clip and resample to 500m
    daily_modis_clipped = daily_modis.map(lambda img: img.clip(uttarakhand))
    daily_modis_resampled = daily_modis_clipped.map(
        lambda img: img.resample('bilinear').reproject(crs='EPSG:4326', scale=500)
    )
    
    # Extract Daytime and Nighttime LST
    daily_lst_day = daily_modis_resampled.select('LST_Day_1km').mean().multiply(0.02).rename('LST_Day_K')
    daily_lst_night = daily_modis_resampled.select('LST_Night_1km').mean().multiply(0.02).rename('LST_Night_K')

    # Export daily data to Google Drive
    ee.batch.Export.image.toDrive(
        image=daily_lst_day,
        description=f'LST_Day_{date_str}',
        folder='EarthEngineExports/Daily',
        fileNamePrefix=f'LST_Day_{date_str}',
        region=uttarakhand.geometry(),
        scale=500,
        crs='EPSG:4326',
        maxPixels=1e13
    ).start()

    ee.batch.Export.image.toDrive(
        image=daily_lst_night,
        description=f'LST_Night_{date_str}',
        folder='EarthEngineExports/Daily',
        fileNamePrefix=f'LST_Night_{date_str}',
        region=uttarakhand.geometry(),
        scale=500,
        crs='EPSG:4326',
        maxPixels=1e13
    ).start()


The following outputs are generated:

1. **Mean LST (Day and Night)**:
   - GeoTIFF files summarizing mean daytime and nighttime LST over the specified time range

2. **Daily Time-Series**:
   - A stack of daily LST data as GeoTIFF or CSV files for analysis

## References
- [Google Earth Engine Documentation](https://developers.google.com/earth-engine)
- [MODIS/061/MOD11A1 Dataset](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MOD11A1)
- [Google Colab Documentation](https://colab.research.google.com/)
   ```
## Handling Task Queue Errors

When processing and downloading large datasets such as daily LST data over a long time range, you may encounter the following error:

![Too Many Tasks Error](https://raw.githubusercontent.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/main/too-many-tasks-gee.png)

### What Does This Mean?

This error occurs because Google Earth Engine enforces a limit of 3000 queued tasks per user. When exporting data for each day across multiple years, the number of tasks can easily exceed this limit.
Solutions to Address the Task Limit
1. Filter by Year and Process One Year at a Time
   To avoid submitting too many tasks at once, you can filter the dataset to process and export data one year at a time:
```
# Define the year to process
year = 2012
start_date = datetime.date(year, 1, 1)
end_date = datetime.date(year, 12, 31)
dates = [start_date + datetime.timedelta(days=i) for i in range((end_date - start_date).days + 1)]

# Iterate through each date and process LST data for the selected year
for date in dates:
    date_str = date.strftime('%Y-%m-%d')
    print(f"Processing LST data for {date_str}...")
    
    # Rest of your processing code remains the same
```
2. Use Task Monitoring
   To avoid overwhelming the task queue, modify the code to submit tasks one at a time and wait for their completion:

### Export daily data to Google Drive with task monitoring
```
export_task_day = ee.batch.Export.image.toDrive(
    image=daily_lst_day,
    description=f'LST_Day_{date_str}',
    folder='EarthEngineExports/Daily',
    fileNamePrefix=f'LST_Day_{date_str}',
    region=uttarakhand.geometry(),
    scale=500,
    crs='EPSG:4326',
    maxPixels=1e13
)
export_task_day.start()

export_task_night = ee.batch.Export.image.toDrive(
    image=daily_lst_night,
    description=f'LST_Night_{date_str}',
    folder='EarthEngineExports/Daily',
    fileNamePrefix=f'LST_Night_{date_str}',
    region=uttarakhand.geometry(),
    scale=500,
    crs='EPSG:4326',
    maxPixels=1e13
)
export_task_night.start()
```

### Wait for the tasks to complete before starting the next iteration
``
while export_task_day.active() or export_task_night.active():
    print(f"Waiting for tasks to complete for {date_str}...")
    time.sleep(60)  # Wait for 60
``

## Further Exploration 

If you'd like to delve deeper into the significance of this data and its role in wildfire prediction, you can read more [here](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/blob/main/understanding-the-data.md). This section also includes a glossary to help you better understand the terminology.

To understand why this data matters from the perspective of a wildfire public information officer and volunteer firefighter, you can read more in [this interview](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/blob/main/Interview-with-wildfire-PIO.md).

