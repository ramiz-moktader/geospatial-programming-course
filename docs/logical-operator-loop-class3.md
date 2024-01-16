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