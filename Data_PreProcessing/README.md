# Microclimate Sensors Data Cleaning & Preprocessing

## Project Overview
This project focuses on cleaning and preprocessing the **Microclimate Sensors dataset**, which contains environmental sensor readings collected from various locations. The goal is to prepare the data for reliable analysis and modeling by handling missing values, encoding spatial data appropriately, and preserving critical patterns related to sensor locations.

---

## Dataset Description
The dataset includes features such as:

- **Device_id:** Unique identifier for each sensor device.
- **Time:** Timestamp of the recording.
- **SensorLocation:** Location name or code where the sensor is deployed.
- **LatLong:** Geospatial coordinates in `(Latitude, Longitude)` format.
- **Environmental sensor readings:** Wind directions and speeds, air temperature, humidity, atmospheric pressure, particulate matter (PM2.5, PM10), noise levels, etc.

---

## Cleaning & Preprocessing Steps

### 1. Missing Data Analysis
- Calculated missing value counts for each feature.
- Identified critical columns with missing data and formulated handling strategies.

### 2. Handling Location Data
- Dropped rows missing `SensorLocation` since location data is essential.
- For missing `LatLong` values, imputed latitude and longitude based on the corresponding `SensorLocation` to preserve spatial integrity.

### 3. Imputation of Sensor Readings
- Grouped data by `SensorLocation` to respect local environmental characteristics.
- Imputed missing sensor readings using:
  - **Median** for features with skewed distributions.
  - **Mean** for features approximating normal distributions.

### 4. Encoding Geospatial Data
- Split the `LatLong` string into two numeric features: `Latitude` and `Longitude`.
- Converted these to float types for compatibility with numerical analyses and modeling.
- Avoided categorical encodings for geospatial continuous data.

---

## Usage

1. **Load Data:** Load the raw sensor dataset (CSV format).
2. **Run Cleaning Scripts:** Apply the preprocessing steps to handle missing values and transform features.
3. **Save Processed Data:** Export the cleaned dataset for further analysis or machine learning tasks.

---

## Key Benefits

- Maintains spatial relationships by group-wise imputation.
- Preserves the quality of critical ground truth data.
- Prepares data for advanced analytics including geospatial analysis, visualization, and predictive modeling.

---

## Dependencies

- Python 3.x  
- Pandas  
- NumPy  
- (Optional) Matplotlib / Seaborn for visualization

---

## How to Run

```bash
# Install required packages (if not installed)
pip install pandas numpy matplotlib seaborn


