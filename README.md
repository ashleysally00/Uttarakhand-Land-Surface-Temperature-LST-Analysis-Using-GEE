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
7. [References](#references)

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
If you want to learn more about this data and gain a better understanding of what it means, you can read more [here](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE/blob/main/understanding-the-data.md).

