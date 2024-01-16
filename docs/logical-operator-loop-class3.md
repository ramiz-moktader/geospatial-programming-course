**Logical Operators**

Logical operators in programming are symbols or keywords that are used to perform logical operations on Boolean values. Boolean values represent true or false, and logical operators allow you to combine or manipulate these values to make decisions in your program. 

### Logical Operators in JavaScript

JavaScript supports three main logical operators: **AND (`&&`)**, **OR (`||`)**, and **NOT (`!`)**.

1. **AND (`&&`):**
   The AND operator returns `true` only if both operands are `true`. Otherwise, it evaluates to `false`.

   ```javascript
   var result = true && false; // result is false
   ```

2. **OR (`||`):**
   The OR operator returns `true` if at least one of the operands is `true`. It evaluates to `false` only when both operands are `false`.

   ```javascript
   var result = true || false; // result is true
   ```

3. **NOT (`!`):**
   The NOT operator negates the boolean value of its operand. If the operand is `true`, it becomes `false`; if it's `false`, it becomes `true`.

   ```javascript
   var result = !true; // result is false
   ```

### Truth Tables

A truth table is a tabular representation of all possible outcomes of a logical expression. Let's create truth tables for the AND, OR, and NOT operators.

1. **AND Truth Table (`&&`):**


   | Operand 1 | Operand 2 | Result |
   |-----------|-----------|--------|
   |   true    |   true    |  true  |
   |   true    |   false   |  false |
   |   false   |   true    |  false |
   |   false   |   false   |  false |

2. **OR Truth Table (`||`):**


   | Operand 1 | Operand 2 | Result |
   |-----------|-----------|--------|
   |   true    |   true    |  true  |
   |   true    |   false   |  true  |
   |   false   |   true    |  true  |
   |   false   |   false   |  false |


3. **NOT Truth Table (`!`):**


   | Operand | Result |
   |---------|--------|
   |  true   |  false |
   |  false  |  true  |

### Practical Use Cases

Logical operators are frequently employed in conditional statements and loops, enhancing the decision-making capabilities of programs. Here's a simple example:

```javascript
var x = 5;
var y = 10;

if (x > 0 && y > 0) {
  console.log("Both x and y are positive.");
} else {
  console.log("At least one of x or y is not positive.");
}
```


### Loop

A loop is a programming construct that allows a set of instructions to be repeated multiple times. JavaScript provides several types of loops, but the most common ones are the "for" loop and the "while" loop.

## The For Loop in JavaScript: 

The `for` loop in JavaScript is a powerful tool that allows you to repeat a set of instructions for a specified number of times. It consists of three optional expressions enclosed in parentheses, followed by a code block. Let's break down the structure of the `for` loop:

```javascript
for (expression1; expression2; expression3) {
  // code block to be executed
}
```

### Expression 1:
The first expression, `expression1`, is executed once before the code block. This part of the loop is typically used to initialize a variable. For example:

```javascript
for (var i = 0; i < 5; i++) {
  // code block to be executed
}
```

In this example, `let i = 0` initializes a variable `i` to 0 before the loop begins.

### Expression 2:
The second expression, `expression2`, defines the condition for executing the code block. The loop will continue running as long as this condition is true. Using the previous example:

```javascript
for (var i = 0; i < 5; i++) {
  // code block to be executed
}
```

Here, `i < 5` is the condition. The loop will keep running as long as `i` is less than 5.

### Expression 3:
The third expression, `expression3`, is executed after each execution of the code block. It is commonly used for incrementing or decrementing a variable. Continuing with the example:

```javascript
for (var i = 0; i < 5; i++) {
  // code block to be executed
}
```

In this case, `i++` increments the value of `i` by 1 after each iteration.



Another example that counts from 1 to 5:

```javascript
for (var i = 1; i <= 5; i++) {
  console.log(i);
}
```

Explanation:
- `var i = 1`: This initializes a variable `i` to 1.
- `i <= 5`: This is the condition that determines whether the loop should continue. It says, "Continue looping as long as `i` is less than or equal to 5."
- `i++`: This increments the value of `i` by 1 after each iteration.

The loop prints the values of `i` to the console from 1 to 5.

