- [Variables: `var`, `let`, and `const`](#variables-var-let-and-const)
  - [Declaring Variables with `var`](#declaring-variables-with-var)
  - [Declaring Variables with `let`](#declaring-variables-with-let)
  - [Declaring Variables with `const`](#declaring-variables-with-const)
  - [Problems with `var` in JavaScript](#problems-with-var-in-javascript)
- [Comments and Code Readability](#comments-and-code-readability)
  - [Single-Line Comments](#single-line-comments)
  - [Multi-line Comments](#multi-line-comments)
- [Using Operators: Arithmetic, Assignment, Comparisons and Operator Precedence](#using-operators-arithmetic-assignment-comparisons-and-operator-precedence)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Assignment Operators](#assignment-operators)
  - [Comparison Operators](#comparison-operators)
  - [Operator Precedence](#operator-precedence)
    - [Common Operator Precedence](#common-operator-precedence)
    - [Parentheses for Clarity](#parentheses-for-clarity)
    - [Associativity](#associativity)
- [Constants and Immutability in JavaScript](#constants-and-immutability-in-javascript)
  - [1. Understanding `const` and Immutability](#1-understanding-const-and-immutability)
  - [2. Why use `const`?](#2-why-use-const)
  - [3. Immutability with primitive types](#3-immutability-with-primitive-types)
  - [4. Immutability with Objects and Arrays](#4-immutability-with-objects-and-arrays)
  - [5. Achieving Immutability: `Object.freeze()`](#5-achieving-immutability-objectfreeze)
  - [6. When to use `const`](#6-when-to-use-const)
  - [7. Practical Use Cases for `const`](#7-practical-use-cases-for-const)


# Variables: `var`, `let`, and `const`

In JavaScript, **variables** are used to store data that can be referenced and manipulated in code. They allow developers to save values, which can then be retrieved or updated later on. JavaScript provides three primary ways to declare variables: `var`, `let`, and `const`.

## Declaring Variables with `var`

Before 2015, var was the only way to declare variables in JavaScript. However, var has certain characteristics that make it less ideal in modern programming.

- **Scope**: Variables declared with `var` are function-scoped. This means they are accessible only within the function they are declared in or globally if declared outside any function.

- **Hoisting**: JavaScript “hoists” `var` declarations to the top of their scope, meaning they are accessible even before the line where they are declared. This can lead to unintended behaviors.

```
var name = "John";
console.log(name); // Output: John
```

## Declaring Variables with `let`

Introduced in ES6 (ECMAScript 2015), let provides a more predictable way to declare variables:

- **Scope**: `let` is **block-scoped**, meaning it is only accessible within the block (like an if statement or loop) where it was declared.
- **No Hoisting**: Unlike `var`, `let` does not hoist in the same way, making it less prone to accidental bugs from early references

```
let age = 25;
if (age >= 18) {
    let isAdult = true;
    console.log(isAdult); // Output: true
}
console.log(isAdult); // Error: isAdult is not defined
```

## Declaring Variables with `const`

Also introduced in ES6, `const` is used for declaring constants, which are variables with a fixed value that cannot be reassigned:

- **Immutability**: Variables declared with `const` cannot be reassigned once given an initial value.
- **Scope**: Like `let`, `const` is also **block-scoped**.

```
const birthYear = 1990;
console.log(birthYear); // Output: 1990
birthYear = 2000; // Error: Assignment to constant variable
```

> [!TIP]
> **const with Objects**
> While `const` prevents reassignment of the variable itself, it **does not make objects immutable**. The object’s properties can still be modified:
> ```
> const user = { name: "Alice" };
> user.name = "Bob"; // ✅ Allowed: Modifying object properties
> console.log(user.name); // Bob
> user = { name: "Charlie" }; // ❌ Error: Assignment to constant variable
> ```

## Problems with `var` in JavaScript

> [!WARNING]
> **Function Scope vs. Block Scope**
> 
> One of the most significant issues with `var` is that it is **function-scoped** rather than **block-scoped**. In other words, `var` variables are only [scoped to the function they are defined in, not the individual blocks within that function]() (like if statements, loops, or try-catch blocks). This behavior can lead to unexpected issues, especially within loops. In contrast, `let` and `const` are **block-scoped**, [meaning they only exist within the block `{}` they are declared in]().

<details>
<summary>Example 1 – Scope Issue with var in a Loop:</summary>

```
for (var i = 0; i < 3; i++) {
  setTimeout(function() {
      console.log(i);
  }, 1000);
}
// Expected Output: 0, 1, 2
// Actual Output after 1 second: 3, 3, 3
```

Since `var` is function-scoped, the same i is shared across all loop iterations. By the time the setTimeout executes, i has already incremented to 3.

**Fix** – Use `let` for Block Scope:

```
for (let i = 0; i < 3; i++) {
  setTimeout(function () {
      console.log(i);
  }, 1000);
}
// Output after 1 second: 0, 1, 2 (Correct behavior)
```

With `let`, a new `i` is created for each loop iteration, keeping the expected value inside the callback function.
</details>

<details>
<summary>Example 2 – Function Scope Issue with var:</summary>

```
function testVar() {
    if (true) {
        var x = 10;
    }
    console.log(x); // ✅ 10 (x is accessible outside the if block)
}
testVar();
```

However, using `let` instead of `var` makes the variable **block-scoped**:

```
function testLet() {
    if (true) {
        let y = 20;
    }
    console.log(y); // ❌ ReferenceError: y is not defined
}
testLet();
```
</details>

<details>
<summary>Example 3 – var Hoisting Within a Function:</summary>

```
function hoistingExample() {
    console.log(a); // ✅ Undefined (var is hoisted but not initialized)
    var a = 5;
    console.log(a); // ✅ 5
}
hoistingExample();
```

With let:

```
function hoistingError() {
    console.log(b); // ❌ ReferenceError: Cannot access 'b' before initialization
    let b = 10;
}
hoistingError();
```

With `var`, the declaration is hoisted to the top, but not its assignment. With `let`, the variable remains in a **"temporal dead zone"** until it's assigned a value.

</details>

> [!WARNING]
> **Hoisting and Accidental Use of Undefined Variables**
> JavaScript hoists `var` declarations, meaning [it moves the declaration of variables to the top of their scope, but not their initialization](). This behavior can lead to variables being accessible before they are actually assigned a value, which often results in unexpected undefined values.

<details>
<summary>Example of Hoisting Issue with var:</summary>

```
console.log(name); // Output: undefined
var name = "Alice";
console.log(name); // Output: Alice
```

In this example, the first `console.log(name)` statement does not throw an error, even though name has not yet been assigned a value. Because `var` declarations are *hoisted*, the code behaves as if the `var name; statement` was at the top of its scope, resulting in `undefined` instead of an error.

This can lead to confusing bugs, as developers may not realize why `undefined` is appearing instead of throwing a reference error

</details>

<details>
<summary>Avoiding the Issue with let or const:</summary>

```
console.log(name); // ReferenceError: Cannot access 'name' before initialization
let name = "Alice";
console.log(name); // Output: Alice
```

With `let` (and `const`), *hoisting* still occurs, but JavaScript throws an error if you try to access the variable before its initialization.

</details>

> [!WARNING]
> **Redeclaration and Accidental Overwrites**
> Since `var` allows redeclaration within the same scope, it is possible to accidentally overwrite variables, which can cause hard-to-track bugs in complex code.

<details>
<summary>Example of Accidental Redeclaration with var:</summary>

```
var message = "Hello";
var message = "Goodbye";
console.log(message); // Output: Goodbye
```

In this example, the `var` message variable is redeclared without any issues, which can sometimes cause unexpected values to appear. This can be especially problematic if the variable is overwritten in large codebases where multiple developers are working on the same code.

</details>

<details>
<summary>Using let or const for Safety:</summary>

```
let message = "Hello";
let message = "Goodbye";  // Error: Identifier 'message' has already been declared
```

By preventing redeclarations, `let` and `const` help avoid potential errors and ensure that each variable is defined only once in its scope.

</details>

---

# Comments and Code Readability

Comments are lines in your code that are ignored by the JavaScript engine. They are used to explain code logic, making it easier for you and others to understand

## Single-Line Comments

Single-line comments are created by using `//` at the start of a line.

```
// This is a single-line comment
let userName = "Alice";
```

## Multi-line Comments

Multi-line comments are enclosed between /* and */.

```
/*
This is a multi-line comment.
It can span multiple lines.
*/
let userAge = 30;
```

---

# Using Operators: Arithmetic, Assignment, Comparisons and Operator Precedence

Operators are symbols that perform operations on values. JavaScript provides various operators, each with specific uses.

## Arithmetic Operators

Arithmetic operators are used to perform simple mathematical calculations:

- `+` **(Addition)**: Adds two values
- `-` **(Subtraction)**: Subtracts one value from another
- `*` **(Multiplication)**: Multiplies two values
- `/` **(Division)**: Divides one value by another
- `%` **(Modulus)**: Returns the remainder of a division

```
let sum = 10 + 5;        // 15
let difference = 10 - 5; // 5
let product = 10 * 5;    // 50
let quotient = 10 / 5;   // 2
let remainder = 10 % 3;  // 1
```

## Assignment Operators

Assignment operators assign values to variables. The most common assignment operator is `=`. JavaScript also provides **compound assignment operators**, such as `+=` and `-=`.

```
let x = 10;
x += 5; // x = x + 5; x is now 15
```

## Comparison Operators

Comparison operators compare two values and return a boolean result (`true` or `false`):

- `==`: Equal to
- `!=`: Not equal to
- `===`: Strictly equal to: (checks both value and type)
- `!==`: Strictly not equal to
- `<`, `>`, `<=`, `>=`: Less than, greater than, less than or equal to, greater than or equal to

```
let a = 10;
let b = 5;
console.log(a > b);   // Output: true
console.log(a === b); // Output: false
```

## Operator Precedence

Operator precedence determines the order in which operators are evaluated in an expression. When multiple operators are used in an expression, the ones with higher precedence are evaluated first. If operators have the same precedence, the order of evaluation is determined by their associativity (whether they are evaluated left to right or right to left), for example:

```
let result = 5 + 3 * 2;  // 11, not 16
```

> [!important]
> In this expression, the multiplication (`*`) has higher precedence than addition (`+`), so `3 * 2` is evaluated first, and then `5 + 6` is evaluated, resulting in `11`

### Common Operator Precedence

Here are some common operators and their precedence from highest to lowest:

- **Parentheses** `()`: Expressions inside parentheses are evaluated first.
- **Exponentiation** `**`: Used for powers, e.g., `2 ** 3`.
- **Multiplication** `*`, **Division** `/`, and **Modulus** `%`: Evaluated left to right.
- **Addition** `+` and **Subtraction** `-`: Also evaluated left to right.
- **Comparison Operators** (`==`, `!=`, `>`, `<`): These have lower precedence than arithmetic operations.
- **Logical Operators** (`&&`, `||`): **Logical AND** (`&&`) has higher precedence than **logical OR** (`||`).

### Parentheses for Clarity

Using parentheses can help clarify operator precedence in complex expressions, ensuring they are evaluated in the desired order:

```
let result = (5 + 3) * 2;  // 16, ensures addition happens first
```

### Associativity

- **Left-to-Right Associativity**: Most operators like **addition**, **subtraction**, **multiplication**, etc. are evaluated from left to right.
- **Right-to-Left Associativity**: The exponentiation operator (`**`) and assignment operators (`=`, `+=`, etc.) evaluate from right to left.

---

# Constants and Immutability in JavaScript

## 1. Understanding `const` and Immutability

In JavaScript, the `const` keyword is used to [declare a variable whose reference cannot be reassigned](). This means that once a variable is declared with `const`, its value cannot be changed to point to a different object or primitive value.

However, **immutability** here is a bit nuanced. While the reference to the value is fixed, the content of the object or array itself can still be modified. This distinction is important when working with complex data structures like objects or arrays.

<details>
<summary>Examples of const Behavior:</summary>

```
const number = 42;
number = 50;  // Error: Assignment to constant variable
const person = { name: "John", age: 30 };
person.age = 31; // Allowed: Mutating properties is fine
person = { name: "Jane", age: 28 };  // Error: Cannot reassign a constant object
```

> [!NOTE]
> - The variable number is declared using `const`, and attempting to reassign it results in an error.
> - The `person` object is also declared with `const`, but we can still modify its properties (`person.age = 31` is valid)
> - However, reassigning the person `object` itself to a new object will throw an error

</details>

## 2. Why use `const`?

There are several reasons to prefer const when declaring variables in JavaScript:

- **Prevents Reassignments**: It prevents accidental reassignments, ensuring that once a value is assigned to a variable, it remains the same throughout the code, leading to fewer bugs.
- **Improves Code Readability**: By using `const`, you're signaling that the value is not meant to change. This helps make the code more predictable and easier to understand
- **Optimized for Performance**: Some JavaScript engines can optimize `const` variables for better performance since they know the variable won’t be reassigned

## 3. Immutability with primitive types

For **primitive types** (like **numbers**, **strings**, and **booleans**), const guarantees full immutability. Once assigned, their values cannot be changed.

```
const pi = 3.14159;
pi = 3.14;  // Error: Cannot reassign a constant variable
```

> [!NOTE]
> This ensures that values such as numbers or strings, once assigned, cannot be altered.

## 4. Immutability with Objects and Arrays

While `const` prevents reassigning the reference to an **object** or **array**, [it does not prevent modification of the object’s or array’s properties or elements]()

<details>
<summary>Examples with Arrays:</summary>

```
const numbers = [1, 2, 3];
numbers.push(4);  // Allowed: Mutating the array content
console.log(numbers);  // [1, 2, 3, 4]
numbers = [5, 6];  // Error: Cannot reassign the array itself
```

</details>

<details>
<summary>Examples with Objects:</summary>

```
const car = { make: "Toyota", model: "Corolla" };
car.model = "Camry";  // Allowed: Modifying properties of the object
console.log(car);  // { make: "Toyota", model: "Camry" }
car = { make: "Honda", model: "Civic" };  // Error: Cannot reassign the object
```

</details>

## 5. Achieving Immutability: `Object.freeze()`

If you want to ensure true **immutability** for objects or arrays, you can use `Object.freeze()`. This method prevents modifications to the object by making it immutable at the shallow level

<details>
<summary>Examples with Object.freeze():</summary>

```
const car = Object.freeze({ make: "Toyota", model: "Corolla" });
car.model = "Camry";  // Error: Cannot modify frozen object
console.log(car);  // { make: "Toyota", model: "Corolla" }
```

> [!CAUTION]
> However, note that `Object.freeze()` only performs a shallow freeze, meaning nested objects or arrays inside the object can still be modified unless they are also frozen.

</details>

## 6. When to use `const`

- **Immutable References**: When you want to ensure that the reference to a value or object doesn't change, use `const`. This is particularly useful when working with **data integrity**

- **Avoid Accidental Reassignments**: Use `const` when declaring variables whose values should remain constant throughout the scope
  
- **Ensuring Predictability**: If you want to make it clear that a variable shouldn't be changed, `const` makes your intentions clear to other developers (or to your future self)

## 7. Practical Use Cases for `const`

- **Configuration Values**: For settings or configurations that should not change, such as API keys, URLs, or constant values
- **Function Expressions**: When you assign a function to a variable, declare it as const to avoid reassignment

```
const fetchData = async () => {
  // code to fetch data
};
```

> [!TIP]
> This ensures that `fetchData` remains a constant function and cannot be accidentally overwritten

---

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0