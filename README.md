# glowing-spoon
Final Project – Detection and Stability Analysis of Broomrape Infestation Using Satellite Imagery, Ben-Gurion University
# Detection and Stability Analysis of Broomrape Infestation Using Satellite Imagery

## 🌿 Project Overview

This project was conducted as part of my final-year B.Sc. in Industrial and Management Engineering at Ben-Gurion University of the Negev. The study focuses on detecting and analyzing **broomrape (Phelipanche aegyptiaca)** infestation in tomato fields using remote sensing data and GIS tools. The goal is to develop a reliable method for **early detection and targeted treatment** of persistent infestation zones.

## 🎯 Objectives

- Filter out border noise to isolate the actual crop area.
- Normalize NDVI values to enable cross-field and multi-year comparison.
- Identify the statistical relationship between NDVI and infestation levels.
- Detect stable, long-term infestation hotspots.
- Develop a logistic regression model to **predict infestation risk** based on satellite data.

## 🔍 Methodology

### Step 1: Geometric Border Filtering
- Compared NDVI and GRVI in inner vs. outer field zones using 30m buffer rings.
- Determined that a 30m inward cut is optimal to avoid distortion from field edges.
- GRVI was found ineffective for this step and excluded from further analysis.

### Step 2: NDVI Normalization
- Normalized each pixel’s NDVI to a 0–1 scale using reference infestation points:
  - `NDVI_min`: Average NDVI of the 10 worst-affected pixels.
  - `NDVI_max`: Average NDVI of the 10 healthiest pixels.
- Used quantiles as fixed anchors to apply consistent normalization across years.

### Step 3: Statistical Testing
- Merged normalized field data into one dataset.
- Used **Kruskal-Wallis** and **Spearman correlation** to assess the relationship between NDVI and infestation levels (Aleket 0–3).
- Identified 4 key fields with statistically significant results (p < 0.05).

### Step 4: Spatial Consistency Over Time
- Isolated only the consistent agricultural zones in each field from 2011 to 2024.
- Created intersection polygons to track NDVI evolution in stable field areas.

### Step 5: Infestation Hotspot Extraction
- Selected pixels with Aleket ≥ 2 in the reference year.
- Extracted NDVI for these patches across all subsequent years.

### Step 6: Logistic Regression Modeling
- Built a **GLM model** using:
  - `Y`: Binary infestation (Aleket ≥ 2 = 1, else 0)
  - `X`: Normalized NDVI
- Improved with a **GLMM model** that included `Field` as a random effect to account for field-specific differences.
- Chose a **prediction threshold of 0.45** for best trade-off between accuracy and false positives.

## 🛠 Tools & Technologies
- **Google Earth Engine** – NDVI map generation
- **QGIS** – Raster filtering, clipping, and visual analysis
- **R** – Data processing, statistical tests, regression modeling
- **Python** – Scripting and automation


## 📈 Key Outcomes
- Identified four fields with consistent NDVI-infestation relationships.
- Built a generalizable model for predicting broomrape risk zones.
- Developed a framework for long-term monitoring of infestation hotspots.

## 📍 Dataset & Years
- Imagery: NDVI from 2011–2024
- Infestation ground truth: Aleket classification from 2010
- Fields analyzed: Yifat V, Ya’an, Bialik West, and others

## 👩‍💻 Author
**Shaine Ashtamkar**  
B.Sc. Industrial and Management Engineering  
Ben-Gurion University of the Negev  
📫 [shaineashtamkar099@gmail.com](mailto:shaineashtamkar099@gmail.com)

---

*This project highlights the intersection of remote sensing, data analysis, and agricultural sustainability.*

