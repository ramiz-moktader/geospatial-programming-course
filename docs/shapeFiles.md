# Spatial Datasets & Shapefiles

Essential boundary datasets and spatial layers for practicing Google Earth Engine and GIS mapping in Bangladesh.

---

## 🗺️ Administrative Boundaries of Bangladesh

- **Bangladesh Admin 1 to 4 Boundaries (Divisions, Districts, Upazilas, Unions)**:
  Download official COD-AB administrative boundary layers (Shapefile, GeoJSON, KML) from [HDX (Humanitarian Data Exchange)](https://data.humdata.org/dataset/cod-ab-bgd){target="_blank"}.
- **Population & Demographic Tables**:
  Download administrative boundary population statistics from [HDX COD-PS Dataset](https://data.humdata.org/dataset/cod-ps-bgd/resource/f23d4da2-e473-4960-9d94-37df92c8d044){target="_blank"}.

---

## 🌍 Google Earth Engine Built-in Datasets

In Google Earth Engine, you can often query administrative boundaries directly from the public catalog without manually uploading files:

- **FAO GAUL (Global Administrative Unit Layers)**:
  ```javascript
  // Country Boundary
  var bdCountry = ee.FeatureCollection("FAO/GAUL/2015/level0")
                    .filter(ee.Filter.eq('ADM0_NAME', 'Bangladesh'));

  // Level 1: Districts / Divisions
  var bdDistricts = ee.FeatureCollection("FAO/GAUL/2015/level1")
                      .filter(ee.Filter.eq('ADM0_NAME', 'Bangladesh'));

  // Level 2: Upazilas
  var bdUpazilas = ee.FeatureCollection("FAO/GAUL/2015/level2")
                     .filter(ee.Filter.eq('ADM0_NAME', 'Bangladesh'));
  ```

- **LSIB (Large Scale International Boundaries)**:
  ```javascript
  var bangladesh = ee.FeatureCollection("USDOS/LSIB_SIMPLE/2017")
                     .filter(ee.Filter.eq('country_na', 'Bangladesh'));
  ```

---

## 📁 How to Upload Shapefiles to GEE

1. Go to the **Assets** tab in the Google Earth Engine Code Editor.
2. Click **NEW** -> **Shape files (.shp, .shx, .dbf, .prj)** or **CSV file (.csv)**.
3. Select your local shapefile components (must include `.shp`, `.shx`, `.dbf`, and `.prj`).
4. Enter an Asset ID and click **Upload**.
5. Once processing finishes under the **Tasks** tab, import your asset with `ee.FeatureCollection("users/your-username/asset-id")`.