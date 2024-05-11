# Class 14


## Working with Feature Collections and Exports in GEE JS API

The GEE JavaScript API offers powerful tools for manipulating and exporting geospatial data. This article explores techniques for adding properties, exporting and importing features as Shapefiles and CSVs, creating feature collections with null geometries, and exporting classified images.

### 1. Adding Properties by Mapping to a Feature Collection

To add properties to an existing feature collection, leverage the `map` method:

```javascript
// Sample feature collection
var features = ee.FeatureCollection([
  ee.Feature(ee.Geometry.Point([92, 21]), {'prop1': 10, 'prop2': 'value'}),
  ee.Feature(ee.Geometry.Polygon([[[89, 21.6], [92.6,21.8], [91.3, 20.5]]]), {'prop1': 20})
]);

// Function to add a new property based on existing ones
var addAreaProperty = function(feature) {
  return feature.set('area', feature.geometry().area());
};

// Apply the mapping function to add the 'area' property
var featuresWithArea = features.map(addAreaProperty);

print(featuresWithArea);
Map.centerObject(featuresWithArea)
Map.addLayer(featuresWithArea)
```

This code defines two features and a function `addAreaProperty` that calculates the area of each feature's geometry and adds it as a new property named 'area'. The `map` method applies this function to each feature in the collection, creating a new collection with the additional property.

### 2. Exporting feacture collection as Shapefile

**Exporting:**

Use the `Export.table.toDrive` function to export a feature collection as a Shapefile to your Google Drive:

```javascript
Export.table.toDrive({
  collection: featuresWithArea,
  description: 'My feature collection as Shapefile',
  fileFormat: 'SHP', 
  folder: "GEE_exports"
});

```


### 3. Exporting feature collection/ vector Data as CSV

**Exporting:**

Similar to Shapefiles, use the `Export.table.toDrive` function but with a different file format:

```javascript
Export.table.toDrive({
  collection: featuresWithArea,
  description: 'My feature collection as Shapefile',
  fileFormat: 'CSV', 
  folder: "GEE_exports"
});
```

### 4. Mapping over a List and Creating Feature Collection with Null Geometry


* **Creating a FeatureCollection from a List of Numbers in Google Earth Engine**

We'll use the `ee.List` class to create the list and the `map` function to transform each element of the list into a feature with null geometry.

* Define the List

First, let's define a list of numbers. We'll use the `ee.List` class to create the list.

```javascript
// Create a list of numbers
var mylist = ee.List([2, 4, 6, 8, 10]);
```

* Map over the List and Create Features

Next, we'll use the `map` function to iterate over each element in the list. For each element, we'll create a feature with null geometry. We'll set the "value" property of each feature to the corresponding number from the list.

```javascript
// Map over each element in the list and create a Feature with null geometry
var listWithFt = mylist.map(function(el) {
  return ee.Feature(null, {"value": el});
});
```

* Convert Mapped List to FeatureCollection

Now that we have a mapped list of features, we'll convert it to a `FeatureCollection` using the `ee.FeatureCollection` constructor.

```javascript
// Convert the mapped list to a FeatureCollection
var fcWithNullGm = ee.FeatureCollection(listWithFt);
```

* Visualize the FeatureCollection

Finally, let's print the resulting `FeatureCollection` to visualize the features in the Google Earth Engine Console.

```javascript
// Print the FeatureCollection
print(fcWithNullGm, "FeatureCollection from list");
```

### **Exporting a Clipped Image from Google Earth Engine**

 We'll use the `ee.ImageCollection` class to access the dataset, apply a clipping region using a geometry, and then export the clipped image to Google Drive.

* Access the Image Collection

First, we'll access the ESA WorldCover dataset using the `ee.ImageCollection` class. We'll chain the `.first()` method to select the first image in the collection, which represents the most recent data.

```javascript
// Access the ESA WorldCover dataset and select the first image
var imgs = ee.ImageCollection("ESA/WorldCover/v200")
          .first();
```

* Clip the Image

Next, we'll clip the selected image using a specified region. We'll use the `.clip()` function and provide a geometry (`features`) as the clipping region.

```javascript
// Clip the image to a specified region
var clippedImage = imgs.clip(features);
```

* Export the Clipped Image

Now that we have the clipped image, we'll export it to Google Drive using the `Export.image.toDrive()` function. We'll specify the image, scale, region, and output folder.

```javascript
// Export the clipped image to Google Drive
Export.image.toDrive({
  image: clippedImage,
  scale: 10,
  region: features.geometry(),
  folder: "geocoder"
});
```
