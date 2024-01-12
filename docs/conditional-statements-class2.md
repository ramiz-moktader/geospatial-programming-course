


**Operands and Operators**


- **Operands:** These are the values or variables that operators act upon. For example, in the expression 5 + 3, the operands are 5 and 3.

- **Operators:** These are symbols or keywords that perform operations on operands. In the expression 5 + 3, the plus sign (+) is the operator that adds the operands 5 and 3.

So, in short, operands are the things you operate on, and operators are the symbols or keywords that perform the operations.




**Conditional statements**

Conditional statements are essential tools in programming, allowing developers to execute different actions based on specific conditions. In JavaScript, several conditional statements facilitate this process, each serving a distinct purpose.

**1. The "if" Statement:**

The `if` statement is fundamental in JavaScript, enabling the execution of a block of code if a specified condition evaluates to true. For instance:

```javascript
if (condition) {
    // Code to be executed if the condition is true
}
```

```javascript
let temperature = 25;

if (temperature > 30) {
    console.log("It's a hot day!");
} else {
    console.log("The weather is pleasant.");
}
```

In this example, the `if` statement checks if the `temperature` variable is greater than 30. If this condition is true, it prints "It's a hot day!" to the console; otherwise, it prints "The weather is pleasant.

Suppose the current temperature is 25. In this case, the condition `temperature > 30` is false. Therefore, the code inside the `else` block is executed, and "The weather is pleasant." will be logged to the console.

**2. The "else" Statement:**

The `else` statement complements the `if` statement, providing an alternative block of code to be executed when the initial condition is false:

```javascript
if (condition) {
    // Code to be executed if the condition is true
} else {
    // Code to be executed if the condition is false
}
```

```javascript
let loggedIn = false;

if (loggedIn) {
    console.log("Welcome, user!");
} else {
    console.log("Please log in to access the content.");
}
```

In this example, the `if` statement checks if the `loggedIn` variable is true. If true, it welcomes the user; otherwise, it prompts the user to log in.

If the user is not logged in (`loggedIn` is false), the code inside the `else` block will be executed, and "Please log in to access the content." will be printed in the console.

**3. The "else if" Statement:**

The `else if` statement allows for the evaluation of additional conditions after the initial `if` statement. This is useful when multiple conditions need to be considered:

```javascript
if (condition1) {
    // Code to be executed if condition1 is true
} else if (condition2) {
    // Code to be executed if condition2 is true
} else {
    // Code to be executed if neither condition1 nor condition2 is true
}
```
```javascript
let hour = 15;

if (hour < 12) {
    console.log("Good morning!");
} else if (hour < 18) {
    console.log("Good afternoon!");
} else {
    console.log("Good evening!");
}
```

In this example, the `else if` statement provides an additional condition to check after the initial `if` condition. It prints a greeting based on the time of day.

If the `hour` is 15, the first condition (`hour < 12`) is false. The program then checks the next condition (`hour < 18`), which is true. Therefore, "Good afternoon!" will be printed in the console.
