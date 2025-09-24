- [Functions](#functions)
  - [Defining functions: `function` Keyword](#defining-functions-function-keyword)
    - [Function Declaration](#function-declaration)
    - [Function Expressions](#function-expressions)
    - [Function Hoisting](#function-hoisting)
  - [Function Parameters and Return Values](#function-parameters-and-return-values)
    - [Function Parameters](#function-parameters)
    - [Default Parameters](#default-parameters)
    - [Rest Parameters](#rest-parameters)
    - [Destructured Parameters](#destructured-parameters)
    - [Returning Values from Functions](#returning-values-from-functions)
  - [Arrow Functions](#arrow-functions)
    - [Single Parameter](#single-parameter)


# Functions

**Functions** in JavaScript are one of the fundamental building blocks of the language. A `function` is a block of code designed to perform a particular task. Functions allow us to group code together, execute it multiple times, and return values.


## Defining functions: `function` Keyword

### Function Declaration

The most common way to define a function in JavaScript is using the `function` keyword.

```
function greet(name) {
  console.log(`Hello, ${name}!`);
}
greet("Alice");  // Output: Hello, Alice!
```

In this example:

- The `function` keyword is followed by the function name (`greet`).

- The `function` takes one parameter, `name`, and prints a greeting message.

- The `function` is invoked with the argument "Alice", which results in the output "Hello, Alice!".

### Function Expressions

In addition to declarations, JavaScript also supports **function expressions**, which define functions inside expressions. These can be anonymous or named.

```
const greet = function(name) {
  console.log(`Hello, ${name}!`);
};
greet("Bob");  // Output: Hello, Bob!
```

The primary difference between a function declaration and a function expression is that **function expressions are not hoisted**, whereas function declarations are. This means that function expressions must be defined before they are called.

### Function Hoisting

With function declarations, the entire function is hoisted to the top of its scope, meaning you can call the function before it’s defined.

```
greet("Charlie");  // Output: Hello, Charlie!
function greet(name) {
  console.log(`Hello, ${name}!`);
}
```

However, **function expressions are not hoisted**:

```
greet("Charlie");  // Error: greet is not a function
const greet = function(name) {
  console.log(`Hello, ${name}!`);
};
```


---

## Function Parameters and Return Values

Functions can accept parameters and return values, allowing them to be more dynamic and flexible. They behave like local variables and cannot be changed or accessed outside the function.


### Function Parameters

Parameters are the values you pass to a function when calling it. These values are used inside the function. In JavaScript, function parameters are **optional**, and if you don’t pass an argument for a parameter, the parameter gets a value of `undefined`.

```
function add(a, b) {
  return a + b;
}
console.log(add(5, 3));  // Output: 8
console.log(add(5));     // Output: NaN
console.log(add());      // Output: NaN
```


### Default Parameters

You can assign default values to parameters in case they are not passed in the function call. Default values only apply when no parameters are provided or when the provided value is `undefined`.

```
function greet(name = "Stranger") {
  console.log(`Hello, ${name}!`);
}
greet("Alice");  // Output: Hello, Alice!
greet();         // Output: Hello, Stranger!
```

### Rest Parameters

If you need to pass a variable number of arguments, you can use the **rest parameter** syntax. This allows you to collect all remaining arguments into an array.

```
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}
console.log(sum(1, 2, 3, 4));  // Output: 10
```

> [!TIP]
> In this example, numbers will be an array containing all the passed arguments to the function.

### Destructured Parameters

**Destructured parameters** simplify working with objects or arrays directly in function signatures, making the code cleaner and more readable. To highlight the value of destructuring, let’s first look at how similar examples would appear without destructuring.

Without destructuring (objects):
```
function displayUser(user) {
  const name = user.name;
  const age = user.age;
  const city = user.city;
  console.log(`Name: ${name}, Age: ${age}, City: ${city}`);
}
const user = { name: 'Alice', age: 30, city: 'Toronto' };
displayUser(user);
```

With destructuring (objects):
```
function displayUser({ name, age, city }) {
  console.log(`Name: ${name}, Age: ${age}, City: ${city}`);
}
const user = { name: 'Alice', age: 30, city: 'Toronto' };
displayUser(user);
```

Without destructuring (arrays):
```
function calculate(numbers) {
  const a = numbers[0];
  const b = numbers[1];
  return a + b;
}
console.log(calculate([3, 5]));
```

With destructuring (arrays):
```
function calculate([a, b]) {
  return a + b;
}
console.log(calculate([3, 5])); // Output: 8
```

### Returning Values from Functions

> [!TIP]
> In JavaScript, functions can return values, which are sent back to the caller using the `return` statement. This is an essential feature of functions, as it allows them to produce and send results for further use.

Returning single values

```
function multiply(a, b) {
  return a * b;
}
let result = multiply(4, 5);
console.log(result);  // Output: 20
```

Returning multiple values (objects)
```
function getStats(numbers) {
  const sum = numbers.reduce((a, b) => a + b, 0);
  const average = sum / numbers.length;
  return { sum, average };
}
const stats = getStats([10, 20, 30]);
console.log(stats); // Output: { sum: 60, average: 20 }
```

Returning multiple values (arrays)
```
function getMinMax(numbers) {
  return [Math.min(...numbers), Math.max(...numbers)];
}
const [min, max] = getMinMax([5, 10, 15]);
console.log(`Min: ${min}, Max: ${max}`); // Output: Min: 5, Max: 15
```

---

## Arrow Functions

Arrow functions, introduced in ES6 (ECMAScript 2015), offer a more concise and readable syntax for defining functions. They are commonly used for inline functions, and they simplify function expressions by eliminating the need for the `function` keyword, curly braces, and the `return` statement in certain cases. Arrow functions are particularly useful in array methods such as `.map()`, .`filter()`, and `.reduce()`, where they make the code more concise and readable.

Basic Syntax:

```
const functionName = (parameter1, parameter2) => expression;
```

Example:

```
const add = (a, b) => a + b;
console.log(add(3, 4));  // Output: 7
```

### Single Parameter

```
const square = x => x * x;
console.log(square(5));  // Output: 25
```

> [!TIP]
> If the function has only one parameter, you can omit the parentheses around the parameter. This is another feature that reduces the verbosity of arrow functions.

---

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0