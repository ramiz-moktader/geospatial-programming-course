# **Arithmetic operators**

- **Operands:** These are the values or variables that operators act upon. For example, in the expression `5 + 3`, the operands are 5 and 3.. We can say 5 is the **left operand**, and 3 is the **right operand**.

- **Operators:** These are symbols or keywords that perform operations on operands. In the expression 5 + 3, the plus sign (+) is the operator that adds the operands 5 and 3.
In JavaScript, arithmetic operators perform mathematical operations on numeric values. Here are the main arithmetic operators:

1.**Addition (+):** Adds two values together.

   ```javascript
   var sum = 5 + 3;  // sum is 8
   ```

2.**Subtraction (-):** Subtracts the right operand from the left operand.

   ```javascript
   var difference = 10 - 4;  // difference is 6
   ```

3.**Multiplication (*):** Multiplies two values.

   ```javascript
   var product = 2 * 6;  // product is 12
   ```

4.**Division (/):** Divides the left operand by the right operand.

   ```javascript
   var quotient = 8 / 2;  // quotient is 4
   ```

5.**Remainder (%):** Returns the remainder of the division of the left operand by the right operand.

   ```javascript
   var remainder = 10 % 3;  // remainder is 1
   ```

6.**Exponentiation (** or Math.pow()):** Raises the left operand to the power of the right operand.

   ```javascript
   var power = 2 ** 3;  // power is 8
   ```



# **Conditional statements**

Conditional statements are essential tools in programming, allowing developers to execute different actions based on specific conditions. In JavaScript, several conditional statements facilitate this process, each serving a distinct purpose.

### **1. The "if" Statement:**

The `if` statement is fundamental in JavaScript, enabling the execution of a block of code if a specified condition evaluates to true. For instance:

```javascript
if (condition) {
    // Code to be executed if the condition is true
}
```

```javascript
var temperature = 25;

if (temperature > 30) {
    console.log("It's a hot day!");
} else {
    console.log("The weather is pleasant.");
}
```

In this example, the `if` statement checks if the `temperature` variable is greater than 30. If this condition is true, it prints "It's a hot day!" to the console; otherwise, it prints "The weather is pleasant.

Suppose the current temperature is 25. In this case, the condition `temperature > 30` is false. Therefore, the code inside the `else` block is executed, and "The weather is pleasant." will be logged to the console.

### **2. The "else" Statement:**

The `else` statement complements the `if` statement, providing an alternative block of code to be executed when the initial condition is false:

```javascript
if (condition) {
    // Code to be executed if the condition is true
} else {
    // Code to be executed if the condition is false
}
```

```javascript
var loggedIn = false;

if (loggedIn) {
    console.log("Welcome, user!");
} else {
    console.log("Please log in to access the content.");
}
```

In this example, the `if` statement checks if the `loggedIn` variable is true. If true, it welcomes the user; otherwise, it prompts the user to log in.

If the user is not logged in (`loggedIn` is false), the code inside the `else` block will be executed, and "Please log in to access the content." will be printed in the console.

### **3. The "else if" Statement:**

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
var hour = 15;

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

### **Exercise** 

1. Suppose you have a login system where you can log in by using only any of three names.

    - Determine three names inside your code.
    - Write a code that takes the user input.
    - If the user provided name doesn’t match with none of your predetermined names it will display “Sorry! We don’t find you in the system.” Otherwise, it will display “Welcome! “.

2. Write a code that prompts the user to enter a year. The code should display a message indicating whether the year is a leap year or not.

3. Create a simple shopping cart program. The program should:

    - Prompt the user to enter the price of three items one by one.

    - Apply a discount based on the total cost:

    - If the total cost is greater than 50 TK, apply a 10% discount. If the total cost is greater than 100, apply a 20% discount. Use the formula: discountedCost = totalCost - (totalCost * discount)

    - Display the final cost after applying the discount.

4. Write a code that calculates the final grade for a student based on his scores in different subjects. The program should:

    - Prompt the user to enter the scores for three subjects: Math, English, and Science.

    - Calculate the average score using the formula: average = (mathScore + englishScore + scienceScore) / 3.

    - Display the final average score.

    - Use conditional statements to determine and display the corresponding letter grade based on the following grading scale:

        - A:  > 60 

        - F: <60