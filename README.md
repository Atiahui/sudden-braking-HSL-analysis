# sudden-braking-HSL-analysis
Analysis of High Frequency Positioning (HFP) data from public transport system.

**Project Objectives**

The main goal of this project is to analyze high-frequency GPS positioning data from Helsinki Region Transport (HSL) vehicles to identify and study sudden braking events as a proxy for potential safety risks in the urban transport environment.

**Key Objectives**
**Anomaly Detection in Vehicle Movement**
- Detect and filter sudden deceleration events using acceleration thresholds
- Remove GPS noise, unrealistic speed values, and false positives
- Identify temporal and spatial patterns of braking incidents
  
**Clustering & Spatial Analysis**
- Apply clustering algorithms (DBSCAN, K-Means) to braking event locations
- Detect high-risk hotspots along bus and tram routes
- Relate braking clusters to intersections, pedestrian crossings, and urban features
  
**Statistical & Time-Series Analysis**
- Evaluate speed and acceleration profiles leading to braking events
- Compare event frequency across different times of day
  
**Visualization**
- Interactive maps of braking events and hotspots (Folium, GeoPandas)
- Scatter plots of speed vs. acceleration
- Heatmaps of spatial braking density

**Data Source**

The dataset originates from **High Frequency Positioning (HFP)** **data of HSL** public transport vehicles.
Raw data streams were originally collected from MQTT topics by **Forum Virium Helsinki**(https://github.com/ForumViriumHelsinki/hsl-rt-analysis), which converted them into CSV format suitable for analysis. This project applies additional data cleaning, filtering, and analysis steps on these datasets to detect and study sudden braking events.
The converted data included fields such as:
- Timestamp
- Vehicle ID
- Latitude, Longitude
- Speed (m/s)
- Acceleration (m/s²)
During this project, additional cleaning and filtering steps were applied to produce the final dataset

**Project Workflow**
**Data Preprocessing**
- Filtering invalid/missing GPS values
- Bounding box filtering (Helsinki–Espoo study area)
- Speed validation (removing impossible values)
- Acceleration thresholding to detect sudden braking
  
**Analysis & Modeling**
- Event detection based on acceleration < -2.0 m/s²
- Manual filtering of false positives (timestamp–vehicle ID combinations)
- Clustering with DBSCAN and K-Means on spatial and feature-based attributes
  
**Visualization**
- Interactive maps with Folium
- Static plots with Matplotlib & Seaborn
- Spatial heatmaps of braking hotspots
  
## Project Structure

```
├── data/                # Data storage
│   ├── raw/             # CSV files from Forum Virium
│   ├── processed/       # Cleaned datasets
│   └── results/         # Braking event datasets & final outputs
├── notebooks/           # Jupyter notebooks for detection & clustering
├── src/                 # Source code
│   ├── preprocessing/   # Data cleaning scripts
│   ├── detection/       # Sudden braking detection
│   ├── clustering/      # DBSCAN & K-Means analysis
│   └── visualization/   # Maps & plots
├── reports/             # Figures and analysis summaries
└── README.md            # Project documentation


## Required Libraries
- Core Analysis: pandas, numpy, scipy
- Geospatial: geopandas, shapely, folium
- Visualization: matplotlib, seaborn, plotly
- Machine Learning: scikit-learn
