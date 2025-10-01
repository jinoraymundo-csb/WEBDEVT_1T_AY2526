- [Objective](#objective)
  - [What are JavaScript objects?](#what-are-javascript-objects)
  - [Why use objects?](#why-use-objects)
  - [Methods for Creating Objects](#methods-for-creating-objects)
    - [Object Literals](#object-literals)
    - [Using the `Object` constructor](#using-the-object-constructor)
    - [Using `Object.create()`](#using-objectcreate)
    - [Constructor Functions](#constructor-functions)
    - [Classes (ES6 Syntax)](#classes-es6-syntax)
  - [Adding Methods to Objects](#adding-methods-to-objects)
  - [Dynamic Object Properties and Computed Property Names](#dynamic-object-properties-and-computed-property-names)
    - [Dynamic Property Asssignment](#dynamic-property-asssignment)
    - [Computed Property Names](#computed-property-names)


# Objective

Objects and arrays are fundamental data structures in JavaScript, allowing you to store and organize data. While arrays are collections of items arranged in an indexed order, objects are collections of properties, where each property is defined by a key–value pair.

## What are JavaScript objects?

An object in JavaScript is a collection of **key–value pairs**, where the keys are property names (strings or symbols) and the values can be any valid JavaScript data type, including functions. Objects allow you to create structured, reusable code for real-world entities like users, products, or systems.

## Why use objects?

- **Model Real-World Entities**: Group related properties and behaviors.

- **Organize Code**: Encapsulate functionality to avoid clutter in your programs.

- **Enable Reusability**: Share and manipulate structured data easily.

Example - Defining an Object with Properties and Methods:: 

```
const car = {
  make: "Tesla",
  model: "Model S",
  year: 2023,
  start() {
    console.log(`${this.make} ${this.model} is starting...`);
  },
  stop() {
    console.log(`${this.make} ${this.model} has stopped.`);
  },
};
console.log(car.make); // Output: Tesla
car.start(); // Output: Tesla Model S is starting...
car.stop(); // Output: Tesla Model S has stopped.
```

In this example, `start` and `stop` are **methods**, while `make`, `model`, and `year` are **properties**. Methods define the behavior of the object.

## Methods for Creating Objects

### Object Literals

The simplest way to create an object is through **object literals**, which use curly braces `{}` to define properties and methods.

<details>
<summary>Example - A Simple Object</summary>

```
const user = {
  name: "Alice",
  age: 30,
  greet() {
    console.log(`Hi, I'm ${this.name}.`);
  },
};
user.greet(); // Output: Hi, I'm Alice.
```

</details>

> [!TIP] Advantages:
>
> - Concise syntax for static objects.
> - Directly initialize properties and methods.

> [!TIP] Use Case:
>
> Best for defining small, standalone objects without dynamic logic.


### Using the `Object` constructor

The `Object` constructor creates a new object dynamically. Properties can then be added to the object using dot notation or square brackets.

<details>
<summary>Example - Object constructor</summary>

```
const person = new Object();
person.name = "John";
person.age = 25;
person.sayHello = function () {
  console.log(`Hello, I'm ${this.name}.`);
};
person.sayHello(); // Output: Hello, I'm John
```

</details>

> [!TIP]
> When to Use?
> 
> Useful when you need to dynamically create an object but is less preferred compared with literals due to verbosity.

### Using `Object.create()`

The `Object.create()` method allows you to create an object with a specific prototype. This approach is beneficial for inheritance and prototype-based object creation.

<details>
<summary>Example - Prototypal Inheritance</summary>

```
const animal = {
  speak() {
    console.log("Generic animal sound");
  },
};
const dog = Object.create(animal);
dog.speak(); // Output: Generic animal sound
dog.bark = function () {
  console.log("Woof!");
};
dog.bark(); // Output: Woof!
```

</details>

> [!TIP]
> Benefits:
>
> - Precise control over prototypes
> - Usefol for performance-critical applications where inheritance is key

### Constructor Functions

Constructor functions serve as blueprints for objects. Using the `new` keyword automatically creates a new object, binds `this`, and sets up inheritance from `Function.prototype`.

<details>
<summary>Example - Car Constructor</summary>

```
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
  this.start = function () {
    console.log(`${this.make} ${this.model} is starting.`);
  };
}
const myCar = new Car("Toyota", "Camry", 2023);
myCar.start(); // Output: Toyota Camry is starting.
```

</details>

> [!TIP]
> Best Practices:
>
> - Use meaningful names for constructor functions (capitalize the name).
> Avoid defining methods directly on the object for memory efficiency; prefer `prototype`.

### Classes (ES6 Syntax)

Classes provide a more structured and intuitive way to define objects and their behaviors. They act as syntactic sugar over constructor functions.

<details>
<summary>Example -  Class Syntax</summary>

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  greet() {
    console.log(`Hello, my name is ${this.name}.`);
  }
}
const person1 = new Person("Emma", 28);
person1.greet(); // Output: Hello, my name is Emma.
```

</details>

> [!TIP]
> Advantages:
> 
> - Readable and consistent syntax
> - Supports inheritance via `extends`

---

## Adding Methods to Objects

Methods define the behavior of objects. They are functions stored as properties.

<details>
<summary>Example - Object with Methods</summary>

```
const calculator = {
  add(a, b) {
    return a + b;
  },
  subtract(a, b) {
    return a - b;
  },
};
console.log(calculator.add(5, 3)); // Output: 8
console.log(calculator.subtract(5, 3)); // Output: 2
```

</details>

<details>
<summary>Example - Dynamic Method Assignment</summary>

```
const operations = {};
operations.multiply = function (a, b) {
  return a * b;
};
console.log(operations.multiply(2, 3)); // Output: 6
```

</details>

---

## Dynamic Object Properties and Computed Property Names

### Dynamic Property Asssignment

You can add, modify, or delete properties after an object is created.

<details>
<summary>Example - Dynamic Method Assignment</summary>

```
const user = {};
user.name = "Alice";
user.age = 30;
console.log(user); // Output: { name: 'Alice', age: 30 }
delete user.age;
console.log(user); // Output: { name: 'Alice' }
```

</details>

### Computed Property Names

Use expressions to create property names dynamically.

<details>
<summary>Example - Dynamic Property Assignment</summary>

```
const key = "age";
const person = {
  name: "John",
  [key]: 25,
};
console.log(person); // Output: { name: 'John', age: 25 }
```

</details>

---

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0