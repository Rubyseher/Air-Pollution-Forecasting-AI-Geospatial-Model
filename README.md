🌍 **1 km × 1 km Air Pollution Forecasting (AI + Geospatial Model)**

### *Near-real-time PM2.5 & PM10 prediction using Satellite, Weather & Ground sensor data*

This repository contains the full workflow, code, and documentation for building a **geospatial AI model** that forecasts air pollution (PM2.5 & PM10) at a **1 km × 1 km resolution**.
It uses **satellite data, ground-monitoring sensors, weather data, LULC, elevation, road density** and multiple urban-growth proxies to model spatio-temporal pollution patterns.

---

## 📌 **Project Aim**

To develop a **grid-based, 1 km × 1 km AI model** that predicts PM2.5 and PM10 across the study region using 5+ years of hourly satellite, weather, and ground-based data.

---

## 📁 **Repository Structure**

```
📦 air-pollution-forecasting
│
├── data/
│   ├── raw/                # Raw satellite, pollution & weather datasets
│   ├── processed/          # Cleaned & aligned grid-wise data
│   ├── grids/              # 1km×1km grid shapefiles & geospatial layers
│   └── external/           # NCMRWF, ERA5, Bhuvan, LULC, DEM, etc.
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_model_training.ipynb
│   └── 05_evaluation.ipynb
│
├── src/
│   ├── preprocessing/      # Scripts to clean, interpolate, merge data
│   ├── geospatial/         # Grid generation, LULC extraction, DEM, buffers
│   ├── modeling/           # XGBoost, RF, Deep Learning models
│   └── utils/              # Helper functions
│
├── reports/
│   ├── DSU-init-Report.docx
│   ├── charts/
│   └── project_presentation/
│
└── README.md
```

---

# 🛰️ **1. Data Sources**

### **Time Period:**

**2017 → 2022 (5 years)**

### **Data Types:**

* Hourly pollution data
* Hourly weather data
* Satellite-based parameters
* Urban morphology & surface characteristics
* Elevation, road density, land-use analysis

---

## 🛰️ **2. Satellite Data**

| Source           | Resolution    | Parameters          | Notes                       |
| ---------------- | ------------- | ------------------- | --------------------------- |
| **NCMRWF**       | 12 km × 12 km | Weather parameters  | Uses INSAT-3D/3DR           |
| **ERA5**         | 27.8 km       | Weather reanalysis  | Backup for missing data     |
| **INSAT-3D/3DR** | ~1 km         | **AOD** (preferred) | Higher temporal frequency   |
| **MODIS**        | 1 km          | AOD                 | Used when INSAT AOD missing |

### ⭐ *Major Satellite Requirement:*

Obtain **Aerosol Optical Depth (AOD)** aligned to the **1 km grid**.

---

# 🌡️ **3. Ground Data**

### **Pollutants**

* **PM2.5** — fine particles (≤ 2.5 μm)
* **PM10** — coarse particles (≤ 10 μm)

### **Sources**

* Government APCBs
* Open APIs
* Monitoring stations
* Scraped portals for hourly data

### **COVID vs Non-COVID Split**

COVID period = baseline for *low-mobility emissions*
Non-COVID = current behaviour emissions

---

# 🌦️ **4. Weather Parameters**

* Temperature
* Relative Humidity
* Mean Sea-Level Pressure
* Wind Speed
* Wind Direction (converted to u,v vector components)
* Rainfall

---

# 🏙️ **5. Urban & Geospatial Parameters**

### **Land Use / Land Cover (LULC)**

Annual LULC → Compiled from 3 seasonal layers
(Bhuvan platform, 5-year interval)

Categories:

* Urban built-up (Red)
* Vegetation (Green)
* Water bodies (Blue)
* Fallow/Barren (Yellow)
* Rocky/Bright (Pink)

### **Urban Fraction**

% of each grid categorized as urban.

### **Elevation (DEM)**

* Derived from CARTOSAT stereo images

### **Road Density (Traffic Proxy)**

Road categories:

1. Minor (Residential)
2. Intermediate (Light vehicles)
3. Major (Highways, heavy vehicles)

Used as proxy for **traffic-induced pollution**.

---

# 🧠 **6. Final Goal**

Build a **Dynamic, Geospatial AI Model** for every **1 km grid cell** by stacking:

* Satellite data
* Weather data
* Ground pollutant data
* Urban growth indicators
* Road density
* Elevation
* AOD

Model forecasts **near-real-time PM2.5 & PM10** with spatial precision.

---

# 🔧 **7. Tools & Technologies**

### **Core**

* **Python**
* **XGBoost / Random Forest / LightGBM**
* **PyTorch (if Deep Learning is used)**
* **QGIS**
* **PostGIS / GeoPandas**

### **Processing**

* Rasterio
* Shapely
* Scikit-learn
* NumPy / Pandas
* OpenCV (for super-resolution)

---

# 🗺️ **8. High-Level Workflow**

```
1. Create 1 km × 1 km grids for the study region
2. Download satellite + weather + AOD data (2017–2022)
3. Download ground-based pollution data (hourly)
4. Clean, interpolate, and align data onto the grid
5. Extract LULC, DEM, road density for each grid
6. Merge all parameters into grid-wise dataset
7. Train forecasting models
8. Evaluate performance (MAE, RMSE, R²)
9. Deploy model for near-real-time prediction
```

---

# 🧮 **9. Assignments & Work Breakdown**

* Download hourly pollution data
* Understand all datasets
* Learn QGIS + geospatial operations
* Build the AI model
* Perform interpolations & dynamic calculations
* Create super-resolution pipeline (future expansion)

---

# 📊 **10. Flowchart (Text Version)**

```
Satellite Data → Preprocessing → AOD extraction →
                                   |
                                   v
Weather Data → Harmonization → Grid alignment →
                                   |
                                   v
Ground Data → Cleaning → Time sync →
                                   |
                                   v
Urban/LULC/DEM/Road Density → Feature Engineering
                                   |
                                   v
       Merge → Master Dataset → Train AI Model → Predict PM2.5/PM10
```

---

# 🤝 **Contributions**

Feel free to open issues or submit PRs for:

* New data processing scripts
* Better interpolation techniques
* Improved model architecture
* Visualization dashboards

---

# 📜 **License**

MIT License (or whichever you choose — tell me if you want me to add it.)

---

# 🚀 Want me to generate versions?

I can generate:

✔ A **short, aesthetic README**
✔ A **fully formatted README with icons & badges**
✔ A **README with diagrams**
✔ A **one-page scientific-style README**
✔ A **README tailored for recruiters**

Just tell me the style you want!
