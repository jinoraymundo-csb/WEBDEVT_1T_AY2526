- [Objective](#objective)
- [String Literals and Template Strings](#string-literals-and-template-strings)
  - [String Literals](#string-literals)
  - [When to use which?](#when-to-use-which)
- [String Methods, Manipulation and Comparison](#string-methods-manipulation-and-comparison)
  - [Common String Attributes and Methods](#common-string-attributes-and-methods)
  - [String Comparisons](#string-comparisons)
    - [Basic String Comparison (Lexical Comparison)](#basic-string-comparison-lexical-comparison)
    - [Case Sensitivity in Comparisons](#case-sensitivity-in-comparisons)
    - [String Comparisons with Special Characters](#string-comparisons-with-special-characters)
    - [Locale-Sensitive Comparisons](#locale-sensitive-comparisons)
    - [Using `includes()`, `startsWith()`, and `endsWith()` for Substring Comparisons](#using-includes-startswith-and-endswith-for-substring-comparisons)
- [Working with Numbers: Math Operations and Methods](#working-with-numbers-math-operations-and-methods)
  - [Basic Math Operations](#basic-math-operations)
  - [Math Methods and Rounding](#math-methods-and-rounding)
- [Type Coercion and Equality](#type-coercion-and-equality)
  - [What is Type Coercion?](#what-is-type-coercion)
  - [Equality in JavaScript](#equality-in-javascript)
    - [Why does this Matter?](#why-does-this-matter)
- [Implicit String and Number Conversion](#implicit-string-and-number-conversion)
- [Precision Limitations with Floating-Point Numbers](#precision-limitations-with-floating-point-numbers)
- [The NaN Type and Its Unusual Properties](#the-nan-type-and-its-unusual-properties)
- [The Strange Case of `typeof` and `null`](#the-strange-case-of-typeof-and-null)


# Objective

A key focus will be on understanding JavaScript’s unique type system, covering topics such as string literals and operations, number precision and its issues, type coercion, equality quirks, and common pitfalls. By recognizing these type quirks early on, you’ll gain insight into how JavaScript interprets data in different contexts and avoid common errors that can arise from implicit type conversion and unexpected behavior. This foundation will prepare you to write more predictable and reliable JavaScript code.

# String Literals and Template Strings

In JavaScript, **strings** are used to represent text. Strings are sequences of characters and are one of the most widely used data types in web development, essential for everything from storing user input to displaying dynamic content.

## String Literals

String literals are simply a series of characters enclosed in quotes. JavaScript offers single (`' '`), double (`" "`), and backticks (\`\`) for string declarations.

<details>
<summary>Example: </summary>

```
let singleQuote = 'Hello, World!';
let doubleQuote = "Hello, World!";
let templateString = `Hello, World!`; // Introduced in ES6
```

> [!TIP]
> While single and double quotes are functionally the same, backticks are part of template literals in JavaScript, which allow for more flexibility in creating dynamic strings.

</details>

## When to use which?

> [!TIP]
> **Use single or double quotes** when you have simple strings and don’t need string interpolation or multi-line support. They are often used when the string does not require dynamic expressions or formatting.

> [!TIP]
> **Use template literals** when you need to embed expressions within the string or when you have a multi-line string. Template literals improve readability, especially when dealing with HTML, JSON, or complex strings.


<details>
<summary>Example: Choosing Between Single and Double Quotes</summary>

When your string contains quotes inside it, using one type of quote can help you avoid the need for escaping:

```
let sentence1 = "He said, 'Hello!'"; // No escaping needed for single quotes inside double quotes
let sentence2 = 'He said, "Hello!"'; // No escaping needed for double quotes inside single quotes
```

**Template literals** are useful when you need to interpolate variables or expressions:

```
let age = 30;
let message = `I am ${age} years old.`; // String interpolation
```

In short, use template literals when you need dynamic content or multi-line strings, and stick to single or double quotes for simpler cases.

</details>

---

# String Methods, Manipulation and Comparison

JavaScript includes a variety of string methods that let you manipulate text in ways that enhance readability and functionality.

## Common String Attributes and Methods

1. `length` - Returns the number of characters in a string.
  
```
let text = "JavaScript";
console.log(text.length); // Output: 10
```

2. `toUpperCase()` and `toLowerCase()` - Converts a string to uppercase or lowercase

```
console.log("hello".toUpperCase());  // Output: HELLO
```

3. `trim()` - Removes a whitespace from both sides of a string

```
let padded = "   hello world   ";
console.log(padded.trim()); // Output: "hello world"
```

4. `indexOf()` and `includes()` - Finds the position of a substring within a string (`indexOf`) or checks if a substring exists (`includes`)

```
let sentence = "JavaScript is fun";
console.log(sentence.indexOf("fun")); // Output: 14
console.log(sentence.includes("Java")); // Output: true
```

5. `slice()` and `substring()` - Extracts part of a string and returns a new string. Both methods are similar, but `substring` does not accept negative indices. Using a single input, will extract the length of the characters from the start

```
let phrase = "JavaScript";
console.log(phrase.slice(0, 4));  // Output: "Java"
```

## String Comparisons

In JavaScript, comparing strings is a common operation, and it’s important to understand the behavior of string comparisons, especially with respect to case sensitivity, locale, and special characters.

### Basic String Comparison (Lexical Comparison)

JavaScript compares strings lexicographically (i.e., based on their Unicode values). The comparison uses the == (loose equality) or === (strict equality) operators.

- **Loose Equality** (`==`): Checks if the two strings are equal after type coercion.
- **Strict Equality** (`===`): Checks if the two strings are equal without type coercion. This is the more reliable method for comparison in most cases.

```
let str1 = "apple";
let str2 = "apple";
let str3 = "banana";
console.log(str1 === str2); // true: exact match
console.log(str1 === str3); // false: different strings
```

### Case Sensitivity in Comparisons

> [!IMPORTANT]
> String comparisons in JavaScript are **case-sensitive**. This means that uppercase and lowercase letters are treated as distinct characters.

```
let str1 = "hello";
let str2 = "Hello";
console.log(str1 === str2); // false: different case
```

> [!TIP]
> If you want to perform a case-insensitive comparison, you can convert both strings to the same case using `.toLowerCase()` or `.toUpperCase()`.
> ```
> let str1 = "hello";
> let str2 = "HELLO";
> console.log(str1.toLowerCase() === str2.toLowerCase()); // true: case-insensitive comparison
> ```

### String Comparisons with Special Characters

JavaScript also compares strings with special characters based on their Unicode values. For example, an exclamation mark (`!`) has a lower Unicode value than an uppercase letter (`A`).

```
let str1 = "A";
let str2 = "!";
console.log(str1 > str2); // true: 'A' comes after '!'
```

### Locale-Sensitive Comparisons

To handle string comparisons that respect different languages and alphabets, JavaScript provides the `.localeCompare()` method. This method compares two strings based on the current locale and returns:

- 0 if the strings are equal
- -1 if the first string is lexicographically less than the second
- 1 if the first string is lexicographically greater than the second

```
let str1 = "apple";
let str2 = "banana";
console.log(str1.localeCompare(str2)); // -1: 'apple' comes before 'banana'
```

You can also pass additional parameters to `.localeCompare()` to tailor the comparison for specific locales or sensitivity types (e.g., accent-sensitive comparisons).

### Using `includes()`, `startsWith()`, and `endsWith()` for Substring Comparisons

While not direct equality checks, these string methods allow you to compare substrings within strings:

- `includes()`: Checks if a string contains a certain substring
  
- `startsWith()`: Checks if a string starts with a given substring

- `endsWith()`: Checks if a string ends with a given substring

```
let str = "JavaScript is awesome";
console.log(str.includes("Java")); // true: 'Java' is in 'JavaScript'
console.log(str.startsWith("JavaScript")); // true: starts with 'JavaScript'
console.log(str.endsWith("awesome")); // true: ends with 'awesome'
```

---

# Working with Numbers: Math Operations and Methods

Numbers in JavaScript are primarily used for calculations, measurements, and other numerical tasks. JavaScript has a single Number type (there’s no need to specify `int` or `float`), which simplifies arithmetic operations but has some quirks due to its use of **floating-point** arithmetic.

## Basic Math Operations

JavaScript provides operators for standard arithmetic operations:

- **Addition** (`+`)
```
let sum = 5 + 10; // 15
```

- **Subtraction** (`-`)
```
let difference = 20 - 10; // 10
```

- **Multiplication** (`*`)
```
let product = 3 * 4; // 12
```

- **Division** (`/`)
```
let quotient = 20 / 4; // 5
```

- **Modulus** (`%`) - Returns the remainder of division
```
let remainder = 10 % 3; // 1
```

## Math Methods and Rounding

The `Math` object in JavaScript offers several helpful methods for working with numbers.

1. `Math.round()` - Rounds a number to the nearest integer
```
console.log(Math.round(4.7)); // Output: 5
```
2. `Math.ceil()` and `Math.floor()` - Rounds up (`ceil`) or down (`floor`) to the nearest integer.
```
console.log(Math.ceil(4.3)); // Output: 5
console.log(Math.floor(4.7)); // Output: 4
```
3. `Math.random()` - Generates a random number between 0 and 1.
```
console.log(Math.random()); // Output: (random number, e.g., 0.2345)
```
4. `Math.max()` and `Math.min()` - Returns the maximum or minimum value in a set of numbers.
```
console.log(Math.max(10, 20, 30)); // Output: 30
```
5. `toFixed()` and `toPrecision()` - These methods allow for control over the number of decimal places.
```
let pi = 3.14159;
console.log(pi.toFixed(2)); // Output: 3.14
let num1 = 123.456789;
let num2 = 0.000123456;
console.log(num1.toPrecision(5)); // "123.46"
console.log(num2.toPrecision(4)); // "0.0001235"
```

---

# Type Coercion and Equality

**Type coercion** in JavaScript is the automatic or implicit conversion of values from one data type to another. While convenient in some scenarios, it can also lead to unexpected behavior if not properly understood

## What is Type Coercion?

Type coercion occurs when JavaScript automatically converts a value into another type to perform an operation or comparison.

<details>
<summary>Example: </summary>

```
console.log('5' - 2); // 3 ('5' is coerced into a number)
console.log('5' + 2); // "52" (2 is coerced into a string)
```
</details>

Here, JavaScript guesses the intended operation based on the operator. Subtraction expects numbers, so it converts '5' into 5. Addition involves strings, so it concatenates.

## Equality in JavaScript

JavaScript provides two types of equality operators:

1. **Loose Equality** (`==`)

Converts operands to the same type before comparison.

Example:
```
console.log(5 == '5');  // true
console.log(false == 0); // true
console.log(null == undefined); // true
```
 
2. **Strict Equality** (`===`)

Does not perform type conversion. Values must be of the same type to evaluate to true.

Example:
```
console.log(5 === '5');  // false
console.log(false === 0); // false
console.log(null === undefined); // false
```

### Why does this Matter?
Misunderstanding coercion can lead to subtle bugs, especially in comparisons and conditionals. Let’s explore a few real-world examples.

<details>
<summary>Example 1 – User Input Validation:</summary>

Suppose you’re validating user input on a form where the field age is expected to be a number:

```
function validateAge(age) {
  if (age == 18) {
    console.log("Access granted!");
  } else {
    console.log("Access denied!");
  }
}
validateAge('18'); // "Access granted!"
```

Here, the loose equality (`==`) operator coerces the string '18' into a number. This may seem fine, but it opens the door to unintended behavior. For example, an input of '18.0' would also pass validation. Using strict equality ensures no coercion occurs.

```
if (age === 18) {
  console.log("Access granted!");
}
```

</details>

<details>
<summary>Example 2 - Object Comparisons: </summary>

Coercion can result in false positives during object comparisons, for instance:

```
console.log([] == false);  // true
console.log({} == false);  // false
```

- An empty array (`[]`) is coerced into an empty string ('') and then into 0, making it equal to false.

- An empty object (`{}`) remains an object, so the comparison fails.

This behavior can cause unintended issues in conditions like

```
if (userInput == false) {
  console.log("No input provided!");
}
```

If userInput is `[]`, this condition evaluates as true, even though an empty array is technically a valid input.


</details>

> [!CAUTION]
> Pitfall: Truty and Falsy in Conditionals


Type coercion affects truthy and falsy values in conditionals. Common falsy values include

- `false`
- `0`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

Example: 

```
if ('0') {
  console.log("Truthy!");
}
```

---

# Implicit String and Number Conversion

JavaScript can sometimes surprise you by converting values unexpectedly when dealing with numbers and strings, especially when using the + operator, which is both for addition and string concatenation.

<details>
<summary>Example: </summary>

```
console.log(5 + '5');  // "55" - the number 5 is coerced into a string
console.log('5' - 3);  // 2 - the string "5" is coerced into a number
console.log(5 + +'5'); // 10 - using the unary +, which coerces "5" to a number
```

</details>

The `+` operator will favor string concatenation **if at least one operand is a string**. The `-`, `*`, and `/` operators, however, do not concatenate and instead **coerce both operands into numbers**.

---

# Precision Limitations with Floating-Point Numbers

JavaScript uses **64-bit floating-point arithmetic** (based on the IEEE 754 standard), which means it can represent numbers very precisely, but with certain limits. Small inaccuracies can appear when working with decimals, especially in calculations.

<details>
<summary>Example: </summary>

```
console.log(0.1 + 0.2); // 0.30000000000000004 - not exactly 0.3
console.log(0.1 + 0.2 === 0.3); // false
```

> [!CAUTION]
> These rounding errors stem from how floating-point numbers are stored, a common issue in programming. In situations where precision is crucial (like financial calculations), JavaScript libraries such as Big.js or Decimal.js are useful for managing floating-point precision.

</details>

---

# The NaN Type and Its Unusual Properties

JavaScript has a special numeric value, `NaN` (Not-a-Number), which represents an invalid number result. One of the strangest quirks of `NaN` is that it’s the only value in JavaScript that **is not equal to itself**.

<details>
<summary>Example: </summary>

```
console.log(NaN === NaN); // false
console.log(isNaN(NaN));  // true - the only reliable way to check for NaN
```

</details>

> [!TIP]
> To check if a value is `NaN`, use the `isNaN()` function or `Number.isNaN()`, as comparing `NaN` directly will always result in `false`.

---

# The Strange Case of `typeof` and `null`

The `typeof` operator in JavaScript returns a string indicating the type of a value, but there’s a well-known quirk with `null` that can trip up beginners: `typeof` null returns "object". This is actually a historical bug in JavaScript that has remained due to backward compatibility.

```
console.log(typeof null); // "object"
```

---

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0