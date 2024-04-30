# Class 12 
### **Normalized difference indices Thresholding and Area Calculation using Google Earth Engine**

Normalized Difference inidices, thresholding is a widely used technique in remote sensing and satellite imagery analysis for classifying different land coveer conditions. In this lecture we will demonstrate how to perform NDVI thresholding and calculate the area for each threshold class using the Google Earth Engine JavaScript API.

### **Step 1: Import Image Collection**

First, import the image collection containing the satellite images with bands required for NDVI calculation. We'll use Landsat 8 data in this example.


```javascript
var collection = ee.ImageCollection('LANDSAT/LC08/C02/T1_L2')
                  .filterDate('2019-01-01', '2019-12-31')
                  .filterBounds(geometry);

```

### **Step 2: Calculate NDVI**

Next, calculate the NDVI for each image in the collection using the formula: (NIR - Red) / (NIR + Red), where NIR (Near-Infrared) is band 5 and Red is band 4.

```javascript
var addNDVI = function(image) {
  var img = image.select("SR_B5","SR_B4")
  var ndvi = img.normalizedDifference(['SR_B5', 'SR_B4']).rename('NDVI');
  return image.addBands(ndvi);
};
var collectionNDVI = collection.map(addNDVI).mean();
Map.addLayer(collectionNDVI.clip(geometry))
```

### **Step 3: Thresholding**
Define threshold classes based on NDVI values to classify different vegetation types or conditions. For example, we'll define classes for bare land, low vegetation, and high vegetation. You can change the upper and lower limit of the value as far your requirement. 

```javascript
var bareLand = collectionNDVI.select('NDVI').lt(0.1);
var lowVegetation = collectionNDVI.select('NDVI').gte(0.1).and(collectionNDVI.select('NDVI').lt(0.5));
var highVegetation = collectionNDVI.select('NDVI').gte(0.5);
```
### **Step 4: Area Calculation**
Calculate the area for each threshold class using area-weighted multiplication and the `reduceRegion` function. 

```javascript
var areaBareLand = bareLand.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

var areaLowVegetation = lowVegetation.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

var areaHighVegetation = highVegetation.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

print('Area of Bare Land (in square meters):', areaBareLand.get('NDVI'));
print('Area of Low Vegetation (in square meters):', areaLowVegetation.get('NDVI'));
print('Area of High Vegetation (in square meters):', areaHighVegetation.get('NDVI'));
```

If you use a featureCollection or Shape file as your ROI, replace the `geometry: geometry` line by  by `geometry:roi.geometry()` 


### **Full code**

```javascript
var collection = ee.ImageCollection('LANDSAT/LC08/C02/T1_L2')
                  .filterDate('2019-01-01', '2019-12-31')
                  .filterBounds(geometry);
var addNDVI = function(image) {
  var img = image.select("SR_B5","SR_B4")
  var ndvi = img.normalizedDifference(['SR_B5', 'SR_B4']).rename('NDVI');
  return image.addBands(ndvi);
};

var collectionNDVI = collection.map(addNDVI).mean();

Map.addLayer(collectionNDVI.clip(geometry))

var bareLand = collectionNDVI.select('NDVI').lt(0.1);
var lowVegetation = collectionNDVI.select('NDVI').gte(0.1).and(collectionNDVI.select('NDVI').lt(0.5));
var highVegetation = collectionNDVI.select('NDVI').gte(0.5);

var areaBareLand = bareLand.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

var areaLowVegetation = lowVegetation.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

var areaHighVegetation = highVegetation.multiply(ee.Image.pixelArea()).reduceRegion({
  reducer: ee.Reducer.sum(),
  geometry: geometry,
  scale: 30,
  maxPixels: 1e9
});

print('Area of Bare Land (in square meters):', areaBareLand.get('NDVI'));
print('Area of Low Vegetation (in square meters):', areaLowVegetation.get('NDVI'));
print('Area of High Vegetation (in square meters):', areaHighVegetation.get('NDVI'));

```
### **Assignmemnt 12**

- Make a NDVI map of your upazila by using Landsat 9 imagery for 2022. Generate 4 different classes and calculate area for each class by thresholding. Upload the code, code link, and screenshot in your github repo. Submit the repo link.- 5 

- Make a Normalized Difference Moisture Index (NDMI)  map of your upazila by using Landsat 9 imagery for 2023. Upload the code, code link, and screenshot in your github repo. Submit the repo link. -3


- Generate two PNG image of your NDVI, and NDMI map by using `getThumbURL()` function. Upload the code, code link, and screenshot in your github repo. Submit the repo link. - 2 

**Submision link**: Check your email

**Dead line**: <span style="color: red;">10 May, 2024 </span>

