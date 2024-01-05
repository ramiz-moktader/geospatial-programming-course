# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit. opps tired

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

### Assignment Operator (`=`)

The assignment operator (`=`) is used to assign a value to a variable. It takes the value on its right and assigns it to the variable on its left.

```javascript
var x = 10; // The value 10 is assigned to the variable x
```

In this example, the value `10` is assigned to the variable `x`.

### Comparison Operators

Comparison operators are used to compare values and return a Boolean result (`true` or `false`). They are commonly used in conditional statements and loops. Here are some common comparison operators:

- **Equality (`==`):** Checks if two values are equal.

  ```javascript
  var a = 5;
  var b = '5';

  console.log(a == b); // true (loose equality, type coercion)
  ```

- **Strict Equality (`===`):** Checks if two values are equal without type coercion.

  ```javascript
  console.log(a === b); // false (strict equality, considers data type)
  ```

- **Inequality (`!=` or `!==`):** Checks if two values are not equal.

  ```javascript
  console.log(a != b); // false (loose inequality, type coercion)
  console.log(a !== b); // true (strict inequality, considers data type)
  ```

- **Greater Than (`>`), Less Than (`<`), Greater Than or Equal To (`>=`), Less Than or Equal To (`<=`):** Compare numerical values.

  ```javascript
  var c = 8;
  var d = 12;

  console.log(c > d); // false
  console.log(c < d); // true
  console.log(c >= d); // false
  console.log(c <= d); // true
  ```

### Arithmetic Operators

Arithmetic operators perform mathematical operations on numerical values. Here are the basic arithmetic operators:

- **Addition (`+`):** Adds two values.

  ```javascript
  var sum = 3 + 5; // sum is 8
  ```

- **Subtraction (`-`):** Subtracts the right operand from the left operand.

  ```javascript
  var difference = 10 - 3; // difference is 7
  ```

- **Multiplication (`*`):** Multiplies two values.

  ```javascript
  var product = 4 * 6; // product is 24
  ```

- **Division (`/`):** Divides the left operand by the right operand.

  ```javascript
  var quotient = 15 / 3; // quotient is 5
  ```

- **Modulus (`%`):** Returns the remainder of the division of the left operand by the right operand.

  ```javascript
  var remainder = 17 % 5; // remainder is 2
  ```

- **Increment (`++`):** Increases the value of a variable by 1.

  ```javascript
  var counter = 10;
  counter++; // counter is now 11
  ```

- **Decrement (`--`):** Decreases the value of a variable by 1.

  ```javascript
  var countDown = 8;
  countDown--; // countDown is now 7
  ```

These operators are fundamental to performing various operations in JavaScript, whether it's basic arithmetic or more complex comparisons and assignments. Understanding how to use them effectively is essential for writing functional and expressive code.