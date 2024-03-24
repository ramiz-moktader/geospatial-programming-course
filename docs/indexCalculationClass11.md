# Class 11

## Calculating Spectral Indices in Google Earth Engine (GEE)
Spectral indices leverage the unique reflectance properties of Earth's features in various electromagnetic spectrum bands captured by satellite sensors. By combining these bands with specific mathematical formulas, these indices enhance specific features, aiding in tasks like land cover analysis, vegetation monitoring, and other remote sensing applications.

### Understanding Spectral Indices:

Each Earth feature has a characteristic spectral signature – how it reflects radiation across different wavelengths. Spectral indices exploit these differences to isolate and map specific features of interest. They are calculated by performing mathematical operations (typically subtraction and division) on specific bands from a satellite image. The resulting values often range from -1 to 1, with higher (or lower) values indicating a greater abundance of the target feature.

### Common Indices and Band Selection for Sentinel-2:

Here are some commonly used indices and the Sentinel-2 bands employed for their calculation:

- **Normalized Difference Vegetation Index (NDVI):** Measures vegetation greenness by contrasting near-infrared (NIR) and red bands. Higher NDVI values indicate denser vegetation.
  - Formula: `(B8 - B4) / (B8 + B4)` (where B8 is the near-infrared band and B4 is the red band in Sentinel-2)
- **Normalized Difference Water Index (NDWI):** Differentiates water bodies from land by contrasting green and near-infrared bands. Higher NDWI values suggest water presence.
  - Formula: `(B3 - B8) / (B3 + B8)` (where B3 is the green band)
- **Normalized Burn Ratio (NBR):** Identifies burned areas by exploiting the distinct reflectance patterns of burned and healthy vegetation in near-infrared and shortwave-infrared bands. Lower NBR values indicate burn scars.
  - Formula: `(B8 - B11) / (B8 + B11)` (where B11 is the shortwave-infrared band)

### Additional Normalized Difference Indices:

Here are a few more commonly used normalized difference indices and their purposes:

- **Normalized Difference Soil Index (NDSI):**
  - Formula: `(Shortwave-infrared1 - Red) / (Shortwave-infrared1 + Red)`
  - Purpose: Differentiates bare soil from vegetation. Higher NDSI values indicate exposed soil.
- **Soil-Adjusted Vegetation Index (SAVI):**
  - Formula: `((NIR - Red) * (1 + L)) / (NIR + Red + L)` (where L is a soil adjustment factor, typically between 0.01 and 0.5)
  - Purpose: Accounts for soil background effects, making it more sensitive to vegetation changes than NDVI, particularly in areas with low vegetation cover.
- **Normalized Difference Drought Index (NDDI):**
  - Formula: `(NDVI - NDVI_min) / (NDVI_max - NDVI_min)` (where NDVI_min and NDVI_max are the minimum and maximum NDVI values for a specific region or time period)
  - Purpose: Monitors drought stress in vegetation. Decreasing NDDI values over time might suggest drought conditions.

These are just a few examples, and numerous other normalized difference indices exist, each tailored to specific applications in remote sensing. Remember to consult relevant scientific literature or GEE documentation for the most suitable index for your analysis.


### Example (NDVI Calculation):

```javascript
// Import Sentinel-2 collection, filtered for 2023
var sentinel2 = ee.ImageCollection("COPERNICUS/S2/SR")
  .filterBounds(roi) //replace your ROI variable by your desired area
  .filterDate("2023-01-01", "2023-12-31")
   .first();

// Select the desired bands
var nir = sentinel2.select("B8");
var red = sentinel2.select("B4");

// Calculate NDVI
var ndvi = nir.subtract(red).divide(nir.add(red));

// Add NDVI layer to the map with a green-to-yellow color palette
map.addLayer(ndvi, {min: 0, max: 1, palette: ["white", "yellow", "green"]});

// Optionally, export the NDVI image
Export.image(ndvi, "NDVI_2023_Sentinel2", {scale: 10});
```

### Why Those Bands Are Chosen for Specific Indices

The choice of bands for calculating spectral indices hinges on the unique reflectance properties of different Earth features across the electromagnetic spectrum. Here's a deeper dive into why specific bands are used for the common indices mentioned earlier:

**Normalized Difference Vegetation Index (NDVI):**

- **Near-infrared (NIR):** Healthy vegetation has high reflectance in the NIR band due to its cellular structure and chlorophyll content.
- **Red:** Chlorophyll strongly absorbs red light for photosynthesis.

By contrasting these bands, NDVI effectively highlights areas with denser vegetation, as healthy plants reflect more NIR and absorb more red light, resulting in a higher NDVI value.

**Normalized Difference Water Index (NDWI):**

- **Green:** Water bodies exhibit high reflectance in the green band.
- **Near-infrared:** Water absorbs NIR radiation.

The difference between these bands emphasizes water features. High NDWI values indicate areas with a larger water presence.

**Normalized Burn Ratio (NBR):**

- **Near-infrared:** Healthy vegetation reflects strongly in NIR.
- **Shortwave-infrared (SWIR):** Burned areas have increased reflectance in SWIR compared to healthy vegetation.

By exploiting this contrasting behavior, NBR helps identify burned areas. Lower NBR values suggest burn scars, as burned materials tend to reflect more SWIR and less NIR