# Microclimate Sensors Data Cleaning & Preprocessing

## Project Overview

This project focuses on cleaning and preprocessing the **Microclimate Sensors** dataset, which contains environmental sensor readings collected from various locations. The objective is to prepare the dataset for reliable analysis and modeling by handling missing values, encoding spatial data appropriately, and normalizing continuous features.

---

## Dataset Description

The dataset includes the following key features:

- **Device_id:** Unique identifier of the sensor device.
- **Time:** Timestamp of the measurement.
- **SensorLocation:** The physical location where the sensor is installed.
- **LatLong:** Geospatial coordinates in `(Latitude, Longitude)` format.
- **Environmental sensor readings:** Includes wind direction and speed, air temperature, relative humidity, atmospheric pressure, particulate matter concentrations (PM2.5, PM10), noise levels, and more.

---

## Data Cleaning & Preprocessing Steps

### 1. Missing Data Analysis

- Calculated the number of missing values per feature to understand data quality.

### 2. Location Data Handling

- Dropped rows missing `SensorLocation` and `LatLong` simultaneously, as location data is critical.
- For rows with missing `LatLong` but present `SensorLocation`, imputed `LatLong` using the first known coordinate for that location.

### 3. Missing Value Imputation

- Imputed missing values in numeric sensor readings using the **mean** or **median** of each feature based on skewness:
  - Features with skewness magnitude > 1 used **median**.
  - Others used **mean**.
- This approach balances robustness to outliers and preserving central tendency.

### 4. Encoding Geospatial Data

- Split `LatLong` into separate numeric features: `Latitude` and `Longitude`.
- This continuous numeric encoding preserves spatial information and enables geospatial analysis.

### 5. Feature Scaling

- Applied **Min-Max scaling** to `Latitude` and `Longitude` to normalize values to the range [0, 1].
- Visualized feature distributions before and after scaling to confirm preservation of shape and scale normalization.
- Scaling ensures compatibility and better convergence in downstream machine learning models.

---

## Usage Instructions

1. Place the raw dataset file `microclimate-sensors-data.csv` in the working directory.
2. Run the preprocessing script to clean, impute, encode, and scale the data.
3. The cleaned and processed dataset can be exported for further analysis or modeling.

---

## Dependencies

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

Install dependencies via:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
