
---

### **Array**

An array is a powerful data structure for managing and handling data in any programming language. While the syntax and notation of arrays vary from language to language, the fundamental concepts remain similar.

## Why Use Arrays?

Suppose you want to print the names of five land-use types. Without using an array, you would do it like this:

```javascript
console.log("Waterbody");
console.log("Bare_land");
console.log("Settlement");
console.log("Vegetation");
```

Instead of storing each land-use name in separate variables, using an array makes it more convenient and easier to manage. For instance:

```javascript
var landUseType = ["Waterbody", "Bare_land", "Settlement", "Vegetation"];

for (var i = 0; i < landUseType.length; i++) {
  console.log(landUseType[i]);
}
```

Arrays provide a structured way to store and access multiple values under a single variable, especially helpful when dealing with extensive lists.

## Creating an Array

Creating arrays in JavaScript can be done using an array literal:

```javascript
var landUseType = ["Waterbody", "Bare_land", "Settlement", "Vegetation"];
```

You can also declare an empty array and assign values later:

```javascript
var landUseType = [];
landUseType[0] = "Waterbody";
landUseType[1] = "Bare_land";
landUseType[2] = "Settlement";
```

## Accessing Array Elements

Arrays use index numbers to access elements, starting from 0. We can access any element of an array by its relevant index. In all programming languages, indexing starts from 0.

For example:

```javascript
var ar = ["Padma", "Meghna", "Jamuna"];
```

In this array, the index of "Padma" is 0, "Meghna" is 1, and "Jamuna" is 2. The index number will increase by 1 if we add more elements. To get the first element of this array, we will use `ar[0]`.

More examples:

```javascript
var landUseType = ["Waterbody", "Bare_land", "Settlement", "Vegetation"];

var waterbody = landUseType[0]; // Accesses the first element
```

## Modifying Array Elements

You can easily change the value of an array element by referencing its index:

```javascript
var ar = ["Padma", "Meghna", "Jamuna"];
ar[0] = "Tista"; // Changes "Padma" to "Tista"
```
---
## Array Properties and Methods

JavaScript arrays come with built-in properties and methods that enhance their functionality. Some of those are:

- `length`: Returns the total number of elements in an array.
- `sort()`: Sorts the elements of the array.


### Example of `length` Property:

The `length` property returns the number of elements in an array. Here's an example:

```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];

// Get the length of the array
var arrayLength = fruits.length;

console.log("Number of elements in the array: " + arrayLength);
// Output: Number of elements in the array: 4
```

### Example of `sort()` Method:

The `sort()` method is used to sort the elements of an array. By default, it sorts elements as strings, so for numbers, you need to provide a comparison function:

```javascript
var numbers = [10, 5, 8, 2, 7];

// Sorting the array
numbers.sort(function(a, b) {
  return a - b; // Ascending order
});

console.log("Sorted numbers: " + numbers);
// Output: Sorted numbers: 2,5,7,8,10
```

For sorting strings alphabetically, you don't need to provide a comparison function:

```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];

// Sorting the array alphabetically
fruits.sort();

console.log("Sorted fruits: " + fruits);
// Output: Sorted fruits: Apple,Banana,Mango,Orange
```

## Looping Through Arrays

You can iterate through array elements using a `for` loop or the `forEach()` function:

```javascript
// Using a for loop
var landUseType = ["Waterbody", "Bare_land", "Settlement", "Vegetation"];

for (var i = 0; i < landUseType.length; i++) {
  // Process each element
}

// Using forEach
landUseType.forEach(function (value) {
  // Process each element
});
```

## Adding Array Elements

To add new elements to an array, you can use the `push()` method or directly assign values using the length property:

```javascript
var fruits = ["Banana", "Orange", "Apple"];
fruits.push("Lemon"); // Adds "Lemon" to fruits

// Alternatively
fruits[3] = "Lemon";
```