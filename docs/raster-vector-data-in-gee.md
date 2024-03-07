
### Creating a GEE account

Google Earth Engine is free for non-commercial and research purposes. You can create a GEE account in two ways: by registering a project in Google Cloud or by filling out a form.

1) [Register a cloud project](https://code.earthengine.google.com/register)

2) [Fill this form and submit your applicaiton](https://signup.earthengine.google.com/#!/no_redirect)

You can also [Watch this video.](https://www.youtube.com/watch?v=NQDSess-HBQ&t=85s)

<iframe width="560" height="315" src="https://www.youtube.com/embed/NQDSess-HBQ?si=a1ZL5hfO1NDPJWTA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Raster and Vector data 

Raster and vector data are two fundamental types of spatial data used in Geographic Information Systems (GIS) and computer graphics. 

### Normal Computer Graphics:

In computer graphics, two primary methods are used to represent images: **vector graphics** and **raster graphics**.

**Raster Graphics**:

- Raster graphics, also known as bitmap graphics, are composed of a grid of pixels, where each pixel contains color information.
- These images are resolution-dependent, meaning they can lose quality when scaled up.
- Common file formats for raster graphics include JPEG, PNG, and GIF.
- Raster images are suitable for photographs and complex images with varying colors and shades.

**Vector Graphics**:

- Vector graphics are composed of mathematical formulas that define shapes and lines.
- Instead of using pixels, vector graphics use points, lines, curves, and shapes (e.g., circles, rectangles).
- These images are resolution-independent, meaning they can be scaled up without losing quality.
- Common file formats for vector graphics include SVG (Scalable Vector Graphics), AI (Adobe Illustrator), and EPS (Encapsulated PostScript).
- Vector images are suitable for illustrations, logos, and diagrams.

### Transition to GIS (Geographic Information Systems):

When we transition to the realm of Geographic Information Systems (GIS), both vector and raster data play essential roles in representing spatial information.

**Raster Data** in GIS:

- In GIS, raster data represents geographic phenomena as a grid of cells, where each cell has a value representing a certain attribute (e.g., elevation, temperature, land cover).
- Satellite imagery, aerial photographs, and digital elevation models (DEMs) are common examples of raster data.
- Raster data is suitable for continuous spatial phenomena where values change continuously across the landscape.

**Vector Data** in GIS:

- Vector data represents geographic features using discrete geometric objects such as points, lines, and polygons.
- Points represent specific locations (e.g., cities, sampling sites), lines represent linear features (e.g., roads, rivers), and polygons represent areas (e.g., administrative boundaries, land parcels).
- Vector data is used to represent discrete features and can store attribute information associated with each feature.

### Applications in GIS:

In GIS applications, both raster and vector data are utilized for various purposes:

**Raster data** is used for tasks such as:

  - Terrain analysis (e.g., slope, aspect, visibility analysis).
  - Land cover classification and change detection.
  - Remote sensing applications (e.g., satellite image analysis).
  - Continuous surface modeling (e.g., interpolation, hydrological modeling).

<figure markdown="span">
![Raster image](images/raster-data.jpg)
  <figcaption>Figrue: Raster data source: arcgis.com </figcaption>
</figure>

**Vector data** is used for tasks such as:

  - Geospatial analysis (e.g., buffer analysis, overlay operations).
  - Network analysis (e.g., routing, transportation planning).
  - Asset management (e.g., tracking infrastructure, facilities management).
  - Cartographic representation (e.g., map production, thematic mapping).

<figure markdown="span">
  ![Vector image](images/vector-data.jpg)
  <figcaption>Figrue: Vector data </figcaption>
</figure>

### Types of Vector data

Different types of vector data commonly used in Geographic Information Systems (GIS) include:

**Points**:

 - Points represent specific locations on the Earth's surface or within a geographical area. Examples include:

  - City locations
  - Sampling sites
  - GPS coordinates

**Lines**:

   - Lines represent linear features and are composed of a sequence of connected points. Examples include:

     - Roads and highways
     - Rivers and streams
     - Utility lines (e.g., pipelines, power lines)

**Polygons**:

   - Polygons represent enclosed areas and are defined by a series of connected lines forming a closed loop. Examples include:

  - Administrative boundaries (e.g., country borders, state boundaries)
  - Land parcels
  - Ecological zones

**Multi-Points**:
   - Multi-points represent collections of individual points grouped together. Examples include:

     - Sets of landmarks or features with multiple points of interest (e.g., tourist attractions within a park)

**Multi-Lines**:
   - Multi-lines represent collections of individual lines grouped together. Examples include:
     - Transportation networks with multiple road segments forming a route
     - River networks with multiple streams or tributaries

**Multi-Polygons**:
   - Multi-polygons represent collections of individual polygons grouped together. Examples include:

     - Complex land use zones with multiple discrete areas (e.g., residential, commercial, industrial)
     - Administrative regions composed of multiple subunits (e.g., districts within a city, counties within a state)

These are some common types of vector data used in GIS applications. Each type serves a specific purpose and can be used individually or in combination to represent spatial features and attributes accurately.

### Vector data in GEE 

In the context of the Google Earth Engine (GEE) JavaScript API, geometry, feature, and feature collection are fundamental concepts used to represent and work with spatial data. Here's a discussion on each:

1. **Geometry**:

   - In GEE, a geometry represents a geometric shape or spatial extent defined by points, lines, or polygons in geographic coordinates (latitude and longitude).
   - Geometries can be simple, such as a single point or a line, or complex, such as a polygon representing the boundary of a region.
   - Geometries are often used to define regions of interest, boundaries, or areas for spatial analysis and processing.
   - Common geometry types include Point, LineString, LinearRing, Polygon, MultiPoint, MultiLineString, and MultiPolygon.


   1.1 **Point**:

```javascript
// Create a Point geometry
var point = ee.Geometry.Point([-122.084, 37.422]);

// Center the map on the point
Map.centerObject(point, 10);

// Add point as a layer to the map
Map.addLayer(point, {color: 'red'}, 'Point');
```

1.2 **LineString**:

```javascript
// Create a LineString geometry
var lineString = ee.Geometry.LineString(
  [[-122.092, 37.424], [-122.086, 37.418], [-122.084, 37.422]]
);

// Center the map on the lineString
Map.centerObject(lineString, 10);

// Add lineString as a layer to the map
Map.addLayer(lineString, {color: 'blue'}, 'LineString');

```

1.3 **Polygon**:

```javascript
// Create a Polygon geometry
var polygon = ee.Geometry.Polygon(
  [[[-122.088, 37.426], [-122.082, 37.426], [-122.082, 37.422], [-122.088, 37.422]]]
);

// Center the map on the polygon
Map.centerObject(polygon, 10);

// Add polygon as a layer to the map
Map.addLayer(polygon, {color: 'green'}, 'Polygon');
```


2. **Feature**:

- A feature in GEE represents a spatially explicit object associated with a geometry and a set of properties or attributes.
- Features can represent real-world entities such as cities, rivers, buildings, or administrative boundaries.
- Each feature contains a geometry (described above) and a collection of key-value pairs representing properties. These properties could include information like name, population, elevation, or any other relevant attribute.
- Features are often used to organize and analyze spatial data, enabling users to attach additional information to geometries and perform queries or analysis based on these attributes.

```javascript
// Define a feature with a point geometry and properties
var cityFeature = ee.Feature(point, {name: 'San Francisco', population: 884363});


// Center the map on the feature
Map.centerObject(cityFeature, 10);

// Add feature as a layer to the map
Map.addLayer(cityFeature, {}, 'City Feature');
```

3. **Feature Collection**:
- A feature collection is a group or collection of features, each with its own geometry and properties.
- Feature collections allow users to organize and manage multiple spatial features within a single data structure.
- Feature collections can represent various types of spatial data, including point clouds, vector datasets, or even collections of satellite imagery.
- Feature collections are often used as inputs for spatial analysis algorithms, visualization layers on maps, or storage containers for spatial datasets.
- Feature collections can be created by importing data from external sources, generating geometries programmatically, or aggregating individual features into a collection.


```javascript
// Create a feature collection and add features to it
var featureCollection = ee.FeatureCollection([
  ee.Feature(point, {name: 'San Francisco', population: 884363}),
  ee.Feature(polygon, {name: 'San Francisco Bay Area', areaSqKm: 10685})
]);

// Center the map on the feature collection
Map.centerObject(featureCollection, 10);

// Add feature collection as a layer to the map
Map.addLayer(featureCollection, {}, 'Feature Collection');
```
### Assignment 8 

- Draw a  rectangle, a point, and a polygon in Google Earth Engine, take a screenshot, and upload the screenshot and the code in your github repo. Submit your github repo link below.
- Draw a feature collection of 5 polygons covering water bodies in your area. Take a screenshot. Then, upload the code and screenshot in your github repo. Submit your github repo link 
- Open this code in GEE  and take a screenshot of the boundary of Bangladesh. Upload in your github repo and submit the repo link 
- Open this code in GEE and change the division name to yours. Take a screenshot of your division map and upload it to github. Submit the repo link. 

**Submssion link**: [Click here to sbumit via google form](https://docs.google.com/forms/d/e/1FAIpQLSfQZDJ2rmIbnNsuyt5Nf6txCaUL9qOwYGaRSBRjOCaM7qEK9w/viewform?usp=sf_link)

**Dead line**: <span style="color: red;">10 March, 2024</span>


