# Class 13 

### Introduction to Group Reducer in Google Earth Engine

In Google Earth Engine (GEE), the Group Reducer is a powerful tool used to perform statistical computations on grouped data within feature collections or tables. This functionality allows users to aggregate data based on specific groupings, such as administrative boundaries, land cover types, or any other categorical variable present in the dataset. By applying reducers to grouped data, analysts can derive valuable insights and summaries for further analysis and visualization.

### Understanding Group Reducer

#### What is Grouping?
Grouping refers to the process of categorizing data based on common attributes or values within a specified field. For instance, if we have a feature collection representing administrative districts, grouping the data by district name would create distinct groups, with each group containing features associated with a particular district.

#### What is a Reducer?
A reducer is a function used to aggregate data within a feature collection or table. Common reducers include calculating statistics such as mean, median, sum, standard deviation, etc. Reducers can operate on individual values or groups of values within the dataset.

#### Group Reducer in GEE:
The Group Reducer in GEE combines the concepts of grouping and reducing, allowing users to calculate aggregate statistics for each group within a feature collection. It enables users to specify the field for grouping and apply a reducer function to compute statistics for each group.

### How `reduceColumns` Works on Feature Collections

The `reduceColumns` function in GEE is used to aggregate data across the columns of a feature collection or table. It allows users to specify selectors (columns) on which to perform the reduction operation and applies a reducer function to compute the result.

#### Syntax:
```javascript
featureCollection.reduceColumns({
  selectors: ["selector1", "selector2", ...],
  reducer: ee.Reducer.function()
});
```

#### Working Principle:
1. **Selectors**:
   - Selectors are the columns or properties within the feature collection on which the reduction operation will be performed. Users specify the selectors as an array of strings.

2. **Reducer**:
   - The reducer defines the operation to be applied to the selected columns. It could be a basic statistical function like mean, sum, median, or a custom reducer function.

3. **Reduction Operation**:
   - The `reduceColumns` function aggregates the data across the specified selectors using the provided reducer. It computes the result for each selector, producing a single value for each.

4. **Output**:
   - The output of `reduceColumns` is a dictionary-like object containing the computed result for each selector.

### **Example**

Suppose we have a `featureCollection` or shapefile named `table`, containing numerical values in the columns "F_TL" and "M_TL", and text values in the column "ADM2_NAME". Now, let's see how we can apply group reducers for the columns holding numerical values.

**[Download the dummy data set from here](https://data.humdata.org/dataset/cod-ps-bgd/resource/f23d4da2-e473-4960-9d94-37df92c8d044)**
```javascript
// Define the featureCollection or shapefile named table
// var table = ...

// Perform the reduction operation
var reducedVal = table.reduceColumns({
  selectors: ["F_TL","M_TL","ADM2_NAME"],
  reducer: ee.Reducer.mean().repeat(2).group({
    groupField: 2,
    groupName: "District"
  })
});
```

1. **Selectors**:
   - The `selectors` parameter specifies which columns of the feature collection (`table` in this case) to include in the reduction operation. In this code, the columns "F_TL" and "M_TL" will be reduced.

2. **Reducer**:
   - The `reducer` parameter defines the operation to be applied to the selected columns. In this code:
     - `ee.Reducer.mean()` specifies that the mean (average) of the values should be calculated.
     - `.repeat(2)` indicates that the mean operation should be repeated twice. This means that for each selected column, the mean will be calculated twice.
     - `.group({ groupField: 2, groupName: "District" })` specifies that the results should be grouped by the values in the "ADM2_NAME" column, which contains the names of districts. Each group will be assigned the name "District".

4. **Output**:
   - The result of the reduction operation is stored in the variable `reducedVal`. It contains the aggregated statistics for each district (group) within the feature collection. The statistics include the mean values of "F_TL" and "M_TL" for each district.


### **Introduction to Group Reducer for Raster Images:**

In Google Earth Engine (GEE), the group reducer is a powerful tool used to aggregate and summarize data within raster images based on specific criteria, such as land cover classes or other categorical variables. It allows users to efficiently group and analyze pixel values within an image, providing valuable insights into the spatial distribution of features. Let's see an example: 

```javascript
// Define the region of interest (ROI)
// var roi =..........;

// Import the "ESA/WorldCover/v200" image collection and clip to ROI
var img = ee.ImageCollection("ESA/WorldCover/v200")
            .first().clip(roi);

// Calculate pixel area and add bands
var areaImage = ee.Image.pixelArea().addBands(img);

// Reduce regions to aggregate pixel area by land cover class within ROI
var lcArea = areaImage.reduceRegions({
                collection: roi,
                reducer: ee.Reducer.sum().group({
                  groupField: 1, 
                  groupName: "Class"
                }),
                scale: 10
              });

// Print the results of land cover area calculation
print(lcArea);

// Visualize the original satellite imagery clipped to the ROI
Map.addLayer(img);
```



### Steps:

1. **Importing and Clipping Satellite Imagery**:
   - Import the "ESA/WorldCover/v200" image collection using `ee.ImageCollection("ESA/WorldCover/v200")`.
   - Select the first image from the collection using `.first()`.
   - Clip the selected image to a specified region of interest (ROI) using `.clip(roi)`.

2. **Calculating Pixel Area and Adding Bands**:
   - Calculate the pixel area using `ee.Image.pixelArea()`.
   - Add bands from the original image to the pixel area image using `.addBands(img)`.

3. **Reducing Regions with Group Reducer**:
   - Use the `reduceRegions` function to aggregate pixel area by land cover class within the ROI.
   - Specify the ROI using the `collection` parameter.
   - Apply the `ee.Reducer.sum()` to calculate the sum of pixel area.
   - Group the results by the land cover class using `.group({ groupField: 1, groupName: "Class" })`. Here, `groupField: 1` indicates the band index of the land cover class.
   - Set the scale to 10 meters.

4. **Printing and Visualizing Results**:
   - Print the results of land cover area calculation using `print(lcArea)`.
   - Visualize the original satellite imagery clipped to the ROI using `Map.addLayer(img)`.

### Understanding the Group Reducer:

In this code, we utilize the `ee.Reducer.sum().group()` function to calculate the sum of pixel area for each land cover class within the ROI. Here's how the group reducer works:

- **Grouping by Land Cover Class**:
  - We specify `groupField: 1` to indicate that we want to group the results by the second band of the image, which represents the land cover class.
  - The `groupName: "Class"` parameter assigns the name "Class" to the grouped field in the output.

- **Applying Reducer to Grouped Data**:
  - After grouping by land cover class, we apply the `ee.Reducer.sum()` to calculate the sum of pixel area within each land cover class.


 ### **Assignmemnt 13**

- **[Download this dummy data set from here](https://data.humdata.org/dataset/cod-ps-bgd/resource/f23d4da2-e473-4960-9d94-37df92c8d044)**. Reduce any three column, and group division. Upload the code, code link, and screenshot in your github repo. Submit the repo link.- 3
 
- **[Use this landcover data set](https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MCD12Q1)** and calculate the sum of each class of the band `LC_Type1` for your upazila for the year 2021. Upload the code, code link, and screenshot in your github repo. Submit the repo link. -3


- **[Watch this tutorial](https://www.youtube.com/watch?v=mrGqVM7Ww44)**, and make a map of your district by using QGIS. Upload the map in your github repo, share your map in  **[our facebook group](https://www.facebook.com/groups/902693884377077/)**. Give hashtags: **#assignment13**, **#QGISMapping**, **#geospatialProgramming** in your post. Submit the link of your facebook post. -4

**Submision link**: Check your email

**Dead line**: <span style="color: red;"> 15 May, 2024 </span>