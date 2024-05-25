## Class 15

## Supervised and Unsupervised Machine Learning



#### 1. Definition and Purpose

- **Supervised Machine Learning:**
  - **Definition:** A type of machine learning where the model is trained on labeled data, meaning each training example is paired with an output label.
  - **Purpose:** To predict the output for new data based on the learned relationship from the training data. It is primarily used for classification and regression tasks.
  
- **Unsupervised Machine Learning:**
  - **Definition:** A type of machine learning where the model is trained on unlabeled data and tries to find hidden patterns or intrinsic structures in the input data.
  - **Purpose:** To discover the underlying structure of the data, group similar data points, and identify anomalies without prior knowledge of output labels. It is mainly used for clustering and dimensionality reduction.

#### 2. Data Requirements

- **Supervised Machine Learning:**
  - **Data Requirement:** Requires a labeled dataset, where each data point is annotated with the correct output.
  - **Example:** In land cover classification, each sample point needs a label indicating the type of land cover (e.g., forest, water, urban).

- **Unsupervised Machine Learning:**
  - **Data Requirement:** Works with unlabeled data, where no output labels are provided.
  - **Example:** In clustering land cover types, the algorithm groups pixels with similar spectral properties without needing predefined labels.

#### 3. Training Process

- **Supervised Machine Learning:**
  - **Training Process:** The algorithm learns from the labeled data by mapping input features to the correct output label. It uses this mapping to predict labels for new data.
  - **Example:** Training a classifier to distinguish between different types of land cover based on spectral signatures.

- **Unsupervised Machine Learning:**
  - **Training Process:** The algorithm explores the input data to identify natural groupings or patterns without any external guidance.
  - **Example:** Performing K-means clustering to segment an image into regions of similar spectral properties.

#### 4. Output

- **Supervised Machine Learning:**
  - **Output:** Produces a model that can predict the label or value for new, unseen data based on learned patterns from the training data.
  - **Example:** A classified map where each pixel is assigned a specific land cover type.

- **Unsupervised Machine Learning:**
  - **Output:** Generates a set of clusters or groups from the data, which can reveal patterns, relationships, or structures within the data.
  - **Example:** A segmented map showing distinct regions based on spectral similarity, without specific labels.

#### 5. Applications

- **Supervised Machine Learning:**
  - **Applications:** Used in scenarios where labeled training data is available, such as:
    - Land cover classification
    - Crop type identification
    - Predictive modeling in various fields (e.g., finance, healthcare)

- **Unsupervised Machine Learning:**
  - **Applications:** Suitable for exploratory data analysis and scenarios where labels are not available, such as:
    - Clustering similar regions in satellite imagery
    - Anomaly detection
    - Market basket analysis



### Introduction to Machine Learning Algorithms in Google Earth Engine (GEE) JavaScript API

Google Earth Engine (GEE) provides a powerful platform for geospatial analysis, including the implementation of machine learning algorithms. This tutorial will introduce you to supervised and unsupervised machine learning concepts, with examples using the GEE JavaScript API.

#### Supervised Machine Learning

Supervised learning involves training a model on labeled data. The model learns to predict the output based on input features.

**Example: Land Cover Classification**

1. **Prepare Training Data:**
   Collect samples representing different land cover types.

   ```javascript
   var trainingPolygons = ee.FeatureCollection([
     ee.Feature(geometry1, {'class': 0}), // e.g., water
     ee.Feature(geometry2, {'class': 1}), // e.g., forest
     ee.Feature(geometry3, {'class': 2})  // e.g., urban
   ]);
   ```

2. **Load and Prepare Imagery:**
   Use satellite imagery, such as Sentinel-2.

   ```javascript
   var image = ee.ImageCollection('COPERNICUS/S2')
                   .filterDate('2022-01-01', '2022-12-31')
                   .median();
   var bands = ['B2', 'B3', 'B4', 'B8']; // Blue, Green, Red, NIR
   var input = image.select(bands);
   ```

3. **Extract Training Data:**
   Sample the image using the training polygons.

   ```javascript
   var training = input.sampleRegions({
     collection: trainingPolygons,
     properties: ['class'],
     scale: 30
   });
   ```

4. **Train the Classifier:**
   Use a classifier like CART (Classification and Regression Trees).

   ```javascript
   var classifier = ee.Classifier.smileCart().train({
     features: training,
     classProperty: 'class',
     inputProperties: bands
   });
   ```

5. **Classify the Image:**

   ```javascript
   var classified = input.classify(classifier);
   Map.addLayer(classified, {min: 0, max: 2, palette: ['blue', 'green', 'red']}, 'Land Cover');
   ```

#### Unsupervised Machine Learning

Unsupervised learning finds patterns or groupings in data without labeled examples.

**Example: K-means Clustering for Land Cover Segmentation**

1. **Load and Prepare Imagery:**
   Use the same steps as in the supervised example.

   ```javascript
   var image = ee.ImageCollection('COPERNICUS/S2')
                   .filterDate('2022-01-01', '2022-12-31')
                   .median();
   var bands = ['B2', 'B3', 'B4', 'B8']; // Blue, Green, Red, NIR
   var input = image.select(bands);
   ```

2. **Sample the Image:**
   Randomly sample the image to create a dataset for clustering.

   ```javascript
   var sample = input.sample({
     region: regionOfInterest,
     scale: 30,
     numPixels: 5000
   });
   ```

3. **Perform K-means Clustering:**
   Cluster the samples into groups.

   ```javascript
   var clusterer = ee.Clusterer.wekaKMeans(3).train(sample);
   var result = input.cluster(clusterer);
   ```

4. **Visualize the Clusters:**

   ```javascript
   Map.addLayer(result.randomVisualizer(), {}, 'Clusters');
   ```

### **Assignmemnt 15**
1. Do a supervised classification by using Sentinel-2 for your upazila, export the classified image, prepare fine-tuned map 
2. Do a unsupervised classification by using Landsat-9 for your upazila, export the classified image, prepare fine-tuned map 

**Submision link**: Check your email

**Dead line**: <span style="color: red;"> 3 June, 2024 </span>