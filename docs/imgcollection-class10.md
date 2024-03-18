# Class 10

####  **Understanding Google Earth Engine (GEE) Image Collection**

Google Earth Engine (GEE) offers a powerful platform for analyzing and processing geospatial data at scale. Central to its functionality is the concept of image collections, which comprise a vast array of satellite imagery, each with its unique characteristics and applications. In this article, we will delve into the intricacies of GEE image collections, covering various satellite sources, resolutions, filtering, reduction techniques, and metadata. Additionally, we'll explore the creation of simple RGB and false-color composites using GEE.

## 1. Different Types of Satellite Collections

GEE hosts an extensive collection of satellite imagery from various sources, each serving distinct purposes and possessing specific characteristics. Some prominent satellite collections include Landsat, Sentinel, MODIS, and more.
[See GEE data catalog for more details](https://developers.google.com/earth-engine/datasets)
### Example: Accessing Landsat Image Collection

```javascript
//Landsat 8, collection 2 tierl 1, TOA data set 
var l8 = ee.ImageCollection("LANDSAT/LC08/C02/T1_TOA")

//now let's take the first image from the collection and print it            
print(l8.first())

```

## 2. Different Resolutions: Spectral, Spatial, Temporal

Satellite imagery varies in resolution across different dimensions: spectral bands, spatial resolution, and temporal frequency.

* **Spectral Resolution:** This refers to the number of wavelengths (bands) captured by the satellite sensor.  Landsat, for example, provides data in several bands, allowing analysis of vegetation health or differentiating between different types of rock. 
* **Spatial Resolution:** This defines the level of detail captured in an image. High-resolution satellites like WorldView provide pixel sizes of less than a meter, enabling visualization of individual objects. 
* **Temporal Resolution:**  This indicates the frequency with which a satellite revisits the same location. Landsat revisits every 16 days, while Sentinel-2 offers 5-day revisits, allowing for more frequent monitoring of dynamic phenomena.




## 3. Filtering Image Collection

Filtering an image collection is crucial to narrow down to specific imagery relevant to the analysis. Filters can be applied based on criteria like date, location, cloud cover, and metadata properties.

### Example: Filtering Landsat by Cloud Cover

```javascript
var maxCloudCover = 20; // Maximum allowable cloud cover percentage
var filteredLandsat = landsatCollection
  .filterDate(startDate, endDate)
  .filterBounds(regionOfInterest)
  .filterMetadata('CLOUD_COVER', 'less_than', maxCloudCover);
print(filteredLandsat);
```
### Example: Filtering Landsat by Date and Region

```javascript
var startDate = '2020-01-01';
var endDate = '2020-12-31';
var regionOfInterest = ee.Geometry.Point(91.79, 22.34);
Map.centerObject(regionOfInterest)
var filteredLandsat = l8
  .filterDate(startDate, endDate)
  .filterBounds(regionOfInterest);
print(filteredLandsat);
```
## 4. Reducing Image Collection

Reducing an image collection involves aggregating multiple images into a single composite image, often through operations like median or mean, to obtain a clearer representation of the data.

### Example: Reducing Landsat Collection to Median Composite

```javascript
var medianComposite = filteredLandsat.median();
print('Median Composite:', medianComposite);
Map.addLayer(medianComposite, {bands: ['B4', 'B3', 'B2'], min: 0, max: 3000}, 'Median Composite');
```

## 5. Metadata of Image Collection

Understanding the metadata associated with satellite imagery is essential for proper interpretation and analysis. Metadata includes information about acquisition date, sensor characteristics, cloud cover, and more.

### Example: Display Metadata of Landsat Image

```javascript
var image = ee.Image(filteredLandsat.first());
print('Metadata:', image.getInfo());
```
### Capture Date of a Single Image

To get the capture date of a single image in Google Earth Engine (GEE), you can use the `.get()` function to retrieve metadata properties associated with the image. Here's how you can do it:

```javascript

// Select a single image from the collection
var singleImage = ee.Image(landsatCollection.first());

// Get the capture date metadata property
var captureDate = singleImage.get('system:time_start');

// Print the capture date
print('Capture Date:', ee.Date(captureDate).format('YYYY-MM-dd'));
```

Explanation:

1. We select a single image from the filtered collection using `first()`.
2. We use `.get()` to retrieve the metadata property `'system:time_start'`, which represents the capture date/time of the image.
3. We convert the capture date/time to a human-readable format using `ee.Date().format()` and print it out.

This code will print out the capture date of the selected Landsat image in the format 'YYYY-MM-dd'. You can adjust the image collection, point of interest, and date range as per your requirements.








## Creating Simple RGB Composite and False-Color Composite

Simple RGB composites combine the red, green, and blue bands to visualize natural colors, while false-color composites utilize other spectral bands to enhance certain features, such as vegetation or urban areas.

### Example: Creating Simple RGB Composite

```javascript
var simpleRGB = medianComposite.visualize({bands: ['B4', 'B3', 'B2'], min: 0, max: 3000});
Map.addLayer(simpleRGB, {}, 'Simple RGB Composite');
```

### Example: Creating False-Color Composite

```javascript
var falseColor = medianComposite.visualize({bands: ['B5', 'B4', 'B3'], min: 0, max: 3000});
Map.addLayer(falseColor, {}, 'False-Color Composite');
```
In a false color composite: 

- Plant-covered land: Deep red
- Denser plant growth: Darker red
- Cities and exposed ground: Gray or tan
- Water: Blue or black