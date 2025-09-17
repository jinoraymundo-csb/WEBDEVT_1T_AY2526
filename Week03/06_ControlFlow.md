- [Objective](#objective)
- [if and else statements](#if-and-else-statements)
  - [Using else with if](#using-else-with-if)
  - [else if and Multiple Conditions](#else-if-and-multiple-conditions)
  - [Handling Multiple Conditions in a Single Check](#handling-multiple-conditions-in-a-single-check)
- [Ternary Operator](#ternary-operator)
- [Switch statements](#switch-statements)
- [Loops in JavaScript](#loops-in-javascript)
  - [For loop](#for-loop)
  - [while Loop](#while-loop)
  - [Do...While Loop](#dowhile-loop)
  - [forEach Loop](#foreach-loop)
  - [for...of Loop](#forof-loop)
- [Using Break and Continue Statements](#using-break-and-continue-statements)
  - [Break Statement](#break-statement)
  - [Continue Statement](#continue-statement)
- [Nullish Coalescing Operator (`??`)](#nullish-coalescing-operator-)
- [Logical Nullish Assignment (`??=`)](#logical-nullish-assignment-)
- [Comparing Control Flow Mechanisms](#comparing-control-flow-mechanisms)


# Objective

Control flow structures allow you to manage the flow of execution in your code based on different conditions and looping needs. Specifically, we’ll cover conditional logic with `if...else` and `switch` statements; looping with `for`, `while`, and `do...while`; and the shorthand options of the ternary and nullish coalescing operators.

# if and else statements

One of the most foundational aspects of control flow in JavaScript is the ability to make decisions using `if` and `else` statements. These statements evaluate conditions and execute different blocks of code based on whether the conditions are `true` or `false`. Think of them as the decision-makers in your code, allowing you to define logic that responds dynamically to different scenarios.

Syntax:

```
if (condition) {
  // code to be executed if condition is true
}
```

When JavaScript encounters an if statement, it checks the condition inside the parentheses. If this condition evaluates to `true`, it runs the code inside the curly braces. If the condition is `false`, it simply skips that block and moves on. This structure ensures your program behaves differently based on varying inputs or states.

For example, imagine you’re writing an application where users log in. You can use an `if` statement to display a welcome message only if the user is successfully logged in.

Example: 

```
let isLoggedIn = true;
if (isLoggedIn) {
  console.log("Welcome back!");
}
```

In this example, the condition `isLoggedIn` determines whether the message “Welcome back!” is displayed. If `isLoggedIn` were `false`, the `console.log` would never run.

## Using else with if

Syntax:

```
if (condition) {
  // code to be executed if condition is true
} else {
  // code to be executed if condition is false
}
```

Sometimes, you want to handle both cases: what happens when the condition is true and what happens when it’s false. This is where the else block comes in. It’s like saying, “If this happens, do this; otherwise, do that.”

Syntax:

```
let isLoggedIn = false;
if (isLoggedIn) {
  console.log("Welcome back!");
} else {
  console.log("Please log in.");
}
```

## else if and Multiple Conditions

Sometimes, you need to evaluate more than two possibilities. In such cases, you can use the `else if` statement to check additional conditions. This is like setting up a sequence of checks: if the first condition is `true`, execute its block; if not, move on to the next condition, and so on.

Syntax:

```
if (condition1) {
  // code to be executed if condition1 is true
} else if (condition2) {
  // code to be executed if condition2 is true
} else {
  // code to be executed if neither condition1 nor condition2 is true
}
```

Think of `else if` as a middle ground between if and else. It lets you create branching logic where multiple paths can be evaluated, and the first condition that matches will execute its block.

```
let score = 85;
if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else {
  console.log("Grade: F");
}
```

Here's how this script flows:

- If the score is 90 or above, it assigns an “A.”

- If it’s between 80 and 89, it assigns a “B.”

- If it’s between 70 and 79, it assigns a “C.”

- Anything below 70 results in an “F.”

> [!TIP]
> - JavaScript evaluates conditions in the order they appear. Once a true condition is found, the remaining else if and else blocks are skipped.
>
> - The else block is optional but serves as a fallback to handle cases where none of the conditions are met.

## Handling Multiple Conditions in a Single Check

You can also evaluate multiple conditions simultaneously using logical operators like `&&` (AND) and `||` (OR).

Example:

```
let age = 25;
if (age >= 18 && age <= 35) {
  console.log("You are in the target age group.");
} else {
  console.log("You are outside the target age group.");
}
```

Here, the condition `age >= 18 && age <= 35` ensures that both conditions are true for the message to be logged. If either one is false, the else block runs instead.

---

# Ternary Operator

The **ternary operator** is a shorthand for `if...else` statements. It’s a compact and concise expression that evaluates a condition and returns one value if the condition is `true` and another if it’s `false`.

Syntax:

```
condition ? expressionIfTrue : expressionIfFalse;
```

> [!TIP]
> The ? and : act as separators:
> - The ? divides the condition from the value to return if it’s true.
> - The : divides the true value from the false value.

Example:

```
let isLoggedIn = true;
let message = isLoggedIn ? "Welcome back!" : "Please log in.";
console.log(message);
```

Here's what happens:

- If `isLoggedIn` is true, the expression evaluates to "Welcome back!".
- If `isLoggedIn` is false, it evaluates to "Please log in.".

> [!TIP]
> The ternary operator allows you to condense the logic into a single line, making it easier to read for straightforward conditions.

---

# Switch statements

A **switch statement** is another way to handle multiple conditional branches. It is useful when you have many conditions that depend on the same value. The switch statement is a cleaner alternative to using multiple `if...else` conditions.

Syntax:

```
switch (expression) {
  case value1:
    // code to be executed if expression === value1
    break;
  case value2:
    // code to be executed if expression === value2
    break;
  default:
    // code to be executed if expression doesn't match any case
}
```

The switch statement evaluates an expression and compares it to the values in the case blocks. When a match is found, the corresponding block is executed. The `break` statement ensures the program exits the switch after the matched case. If no match is found, the `default` block is executed (if provided).

```
let fruit = "apple";
switch (fruit) {
  case "banana":
    console.log("Bananas are yellow.");
    break;
  case "apple":
    console.log("Apples are red or green.");
    break;
  case "orange":
    console.log("Oranges are orange.");
    break;
  default:
    console.log("Unknown fruit.");
}
```

Here, the fruit variable is compared to each case, and when it matches "apple", the corresponding message is logged.

> [!IMPORTANT]
> While `if...else` can handle multiple conditions, a switch statement is often more readable when all the conditions are based on a single expression or value. It organizes the logic into distinct cases, making it easier to manage and less prone to errors.

---

# Loops in JavaScript

Loops are a fundamental programming tool that allow you to execute a block of code multiple times. They’re incredibly powerful when working with repetitive tasks, such as iterating over an array, processing user inputs, or performing calculations. JavaScript offers several types of loops, each designed for specific scenarios: `for`, `while`, and `do...while`.

## For loop

A for loop is perfect when you know in advance how many times you want to repeat a block of code. It’s especially useful when iterating through a sequence of numbers or items in a collection, like an array.

Syntax:

```
for (initialization; condition; increment/decrement) {
  // code to be executed
}
```

- **Initialization**: Sets up a starting point, typically by defining a counter variable (e.g., let i = 0).

- **Condition**: A check that determines whether the loop should continue running. As long as this evaluates to true, the loop will execute.

- **Increment**: Updates the counter variable after each iteration (e.g., i++ to increment by 1).

## while Loop

The `while` loop is a versatile tool that runs a block of code as long as a specified condition is true. Unlike a for loop, which is often used when the number of iterations is predetermined, a while loop is ideal for situations where you may not know beforehand how many times the loop should run.

Syntax:

```
while (condition) {
  // code to be executed
}
```

## Do...While Loop

The `do...while` loop is a variation of the while loop, with one key difference: the code block inside a `do...while` loop is always executed at least once, regardless of the condition. This makes it particularly useful when you want to ensure that a block of code runs before evaluating a condition.

Syntax:

```
do {
  // code to be executed
} while (condition);
```

## forEach Loop

The `forEach` loop is a modern, elegant way to iterate over arrays in JavaScript. Unlike traditional loops, which require manual handling of loop counters and conditions, the `forEach` loop focuses purely on executing a provided function for each element in the array. This makes it especially useful for writing cleaner, more readable code.

Syntax:

```
array.forEach(function(element, index, array) {
  // Code to execute for each element
});
```

- `element` is the current element being processed.

- `index` (optional) is the index of the current element.

- `array` (optional) is the array that `forEach` is being called on.

```
const fruits = ["apple", "banana", "cherry"];
fruits.forEach((fruit, index) => {
  console.log(`Fruit ${index + 1}: ${fruit}`);
});
// Output:
// Fruit 1: apple
// Fruit 2: banana
// Fruit 3: cherry
```

	
1. The forEach method is called on the fruits array.

 
2. For each element in the array, the callback function is executed with the current fruit and its index as arguments.

 
3. The loop automatically moves to the next element after each iteration, without the need to manually increment a counter.

## for...of Loop

The `for...of` loop is a modern JavaScript construct designed specifically for iterating over iterable objects like arrays, strings, maps, sets, and more. Unlike the traditional for loop or forEach, the `for...of` loop gives you direct access to the values of an iterable without dealing with counters or indices.

Syntax:

```
for (const value of iterable) {
  // Code to execute for each value
}
```

- `value` represents the current value in the iterable object.

- `iterable` is the collection or object being iterated over (e.g., an array, string, or set).

Example:

```
const colors = ["red", "blue", "green"];
for (const color of colors) {
  console.log(color);
}
```

---

# Using Break and Continue Statements

In JavaScript, the break and continue statements allow you to modify the default flow of loops, making your code more flexible and adaptive to complex scenarios. While `break` stops the loop entirely, `continue` skips the current iteration and proceeds to the next one.

These tools are particularly useful for handling edge cases, filtering data, or managing early exits when certain conditions are met.

## Break Statement

The `break` statement immediately terminates the loop when encountered. This is helpful when you’ve found what you’re looking for or no longer need to continue iterating.

Example:

```
const numbers = [1, 2, 3, 4, 5];
for (const num of numbers) {
  if (num === 3) {
    console.log("Found 3, stopping the loop.");
    break;
  }
  console.log(num);
}
```

What Happens Here:

1. The loop starts iterating over the `numbers` array.
2. When the value 3 is encountered, the `break` statement is executed.
3. The loop stops completely, and the remaining numbers are not processed.

Output:

```
1
2
Found 3, stopping the loop.
```

## Continue Statement

The `continue` statement skips the current iteration and moves on to the next one. It’s ideal for cases where you want to exclude specific values or handle them differently without breaking the loop.

Example:

```
const numbers = [1, 2, 3, 4, 5];
for (const num of numbers) {
  if (num % 2 === 0) {
    continue; // Skip even numbers
  }
  console.log(num);
}
```

What Happens Here:

1. The loop starts iterating over the `numbers` array.
2. For each even number (2 and 4 in this case), the continue statement is executed, skipping the `console.log` for that iteration.
3. Odd numbers are logged as usual.

Output:

```
1
3
5
```

> [!TIP]
> Why Use Break and Continue?
>
> 1. **Optimize Loops:** Stop processing early when you’ve found what you need.
> 2. **Handle Special Cases:** Skip over unwanted elements or manage exceptions without cluttering your loop logic.
> 3. **Improve Readability:** By reducing the need for deeply nested conditionals, break and continue make your loops cleaner and easier to follow.

---

# Nullish Coalescing Operator (`??`)

In JavaScript, there are a few ways to check for missing or `undefined` values, but the nullish coalescing operator (`??`) brings a more targeted approach. It allows you to provide a fallback value only when the left-hand side is `null` or `undefined`. This is particularly helpful when you’re dealing with variables that could be falsy but are still valid, like 0 or an empty string.

The **nullish coalescing operator** checks if the value on the left is `null` or `undefined`. If it is, it returns the value on the right-hand side. Otherwise, it returns the value on the left. This behavior is different from the logical OR (`||`), which checks for any falsy value, including `0`, `false`, or an empty string.

Syntax:

```
let result = value1 ?? value2;
```

- If `value1` is `null` or `undefined`, `result` will be assigned `value2`.
- Otherwise, `result` will take the value of value1.

Example:

```
let username = null;
let defaultName = "Guest";
let user = username ?? defaultName;
console.log(user);  // Output: Guest
```

What Happens Here?

- The `username` is `null`, so the **nullish coalescing operator** falls back to the `defaultName`, which is "Guest".
- If `username` were an empty string or `0`, the value would have stayed as "" or `0`, respectively, because those values are not considered *nullish* (`null` or `undefined`).

---

# Logical Nullish Assignment (`??=`)

The logical nullish assignment (`??=`) operator is a shorthand way of assigning a value to a variable only if that variable is `null` or `undefined`. This can save you from having to write out more verbose checks when you want to ensure that a variable has a default value if it hasn’t been set yet.

How it Works:

The `??=` operator checks if the variable on the left is `null` or `undefined`. If it is, it assigns the value on the right to that variable. If the variable already has a valid value (i.e., not `null` or `undefined`), it keeps its original value.

Syntax:

```
variable ??= value;
```

- If `variable` is `null` or `undefined`, `variable` will be assigned `value`.
- Otherwise, `variable` will keep its current value.

Example:

```
let userPreference = null;
let defaultPreference = "dark mode";
userPreference ??= defaultPreference;
console.log(userPreference);  // Output: dark mode
```

What Happens Here:

- Since `userPreference` is `null`, the `??=` operator assigns `defaultPreference` to `userPreference`.
- If `userPreference` had been something like "light mode", the `??=` operator would have left it unchanged.

---

# Comparing Control Flow Mechanisms

| Control Flow | Description | Use Case | 
| --- | --- | --- |
| if/else statements | Conditional statements used to evaluate expressions and execute code based on whether the condition is true or false. | When you need to evaluate one or more conditions and take different actions. |
| `switch` | A clean way to handle multiple conditions based on a single value. It has fall-through behavior, which requires careful handling. | Use when you need to handle several possible conditions based on a single value. |
| for loop | Used when you know how many times you need to iterate through the code block. | When you need a fixed number of iterations. | 
| while loop | Continues to run as long as the condition is true. The number of iterations is not known ahead of time. | When you don’t know how many times you need to repeat a block of code. |
| do...while loop | Similar to while, but guarantees at least one iteration before checking the condition. | When you want the code block to run at least once before checking the condition. |
| `forEach` | An array-specific method for iterating through the elements in an array. | For array manipulation or iteration. |
| for...of loop | Iterates over iterable objects (arrays, strings, maps, etc.), providing a simpler alternative to a for loop. | When you need to iterate over arrays, strings, or any iterable objects. |
| `break` | Immediately exits the loop, stopping further iterations. | Use to exit a loop early based on a condition. |
| `continue` | Skips the current iteration and moves to the next one. | When you need to skip an iteration based on a condition. |
| Nullish Coalescing Operator (`??`) | Returns the right-hand operand when the left-hand operand is `null` or `undefined`. | To provide a fallback value when dealing with null or undefined. |
| Logical Nullish Assignment (`??=`) | Assigns a value only if the variable is `null` or `undefined`. | To assign a default value to a variable only when it is null or undefined. |

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0