- [Objective](#objective)
  - [What are Arrays in JavaScript?](#what-are-arrays-in-javascript)
  - [Creating an Array](#creating-an-array)
    - [Using Array Literals](#using-array-literals)
    - [Using the Array Constructor](#using-the-array-constructor)
    - [Using `Array.of()`](#using-arrayof)
    - [Using `Array.from()`](#using-arrayfrom)
  - [Accessing and Modifying Arrays](#accessing-and-modifying-arrays)
    - [Accessing Elements](#accessing-elements)
    - [Modifying Elements](#modifying-elements)
    - [Adding Elements](#adding-elements)
    - [Removing Elements](#removing-elements)
    - [Iterating over Arrays](#iterating-over-arrays)
      - [Traditional Loops](#traditional-loops)
      - [`forEach` Loop](#foreach-loop)
  - [Array Methods](#array-methods)
    - [Transformation Methods](#transformation-methods)
    - [Search Methods](#search-methods)
    - [Sorting Methods](#sorting-methods)


# Objective

Arrays are fundamental data structures in JavaScript, allowing you to store, manage, and manipulate collections of data efficiently. They are versatile, supporting a wide range of operations and methods, and are commonly used in almost every application to handle lists, sequences, or collections of items.

## What are Arrays in JavaScript?

An **array** is a special type of object in JavaScript that stores ordered collections of items. Each item, or element, is identified by its index, which starts at 0. Arrays can hold elements of any data type, including other arrays, creating multidimensional arrays.

Why use arrays?

- **Data Storage**: Store lists or sequences of data compactly.

- **Iteration**: Process elements efficiently using loops or higher-order methods.

- **Dynamic Size**: Arrays in JavaScript are dynamic and can grow or shrink as needed.

- **Diverse Operations**: Built-in methods simplify common tasks like sorting, filtering, and mapping.

## Creating an Array

### Using Array Literals

The simplest way to create an array is using square brackets `[]`. This method initializes an array with specified elements or as an empty array.

<details>
<summary>Example - Creating Arrays with Literals</summary>

```
const fruits = ["apple", "banana", "cherry"];
const emptyArray = [];
console.log(fruits[0]); // Output: apple
console.log(emptyArray.length); // Output: 0
```

</details>

> [!TIP]
> Advantages:
>
> - Concise syntax
> - Ideal for static or predefined data

### Using the Array Constructor

The `Array` constructor creates arrays dynamically. You can pass either a single numeric value to define the array length or multiple elements.

<details>
<summary>Example - Using the Array constructor</summary>

```
const numbers = new Array(5); // Creates an array with 5 undefined slots
const mixed = new Array(1, "hello", true); // Creates an array with specified elements
console.log(numbers.length); // Output: 5
console.log(mixed[1]); // Output: hello
```

</details>

> [!NOTE]
> When to use:
>
> - For dynamic array creation
> - When defining arrays programmatically

### Using `Array.of()`

`Array.of()` creates arrays from its arguments. Unlike the `Array` constructor, it avoids ambiguity when handling numbers.

<details>
<summary>Example - Array.of()</summary>

```
const arr = Array.of(5); // Creates an array with one element: 5
console.log(arr); // Output: [5]
```

</details>

> [!NOTE]
> Benefits:
>
> - Eliminates confusion with single numeric arguments
> - Useful for uniform array initialization

### Using `Array.from()`

`Array.from()` creates arrays from array-like or iterable objects, such as strings, sets, or NodeLists.

<details>
<summary>Example - Converting a NodeList to an Array:</summary>

```
const divsList= document.querySelectorAll('div');
const divsListArray = Array.from(divsList);
console.log(divsListArray); // Output: List of divs
```

</details>

<details>
<summary>Example - Using a Mapping Function:</summary>

```
const doubled = Array.from([1, 2, 3], (x) => x * 2);
console.log(doubled); // Output: [2, 4, 6]
```

</details>

---

## Accessing and Modifying Arrays

Access elements using their index, which starts at `0`. Negative indices are not supported directly but can be emulated with helper functions.


### Accessing Elements

<details>
<summary>Example - Index Access:</summary>

```
const colors = ["red", "green", "blue"];
console.log(colors[0]); // Output: red
console.log(colors[2]); // Output: blue
```

</details>

### Modifying Elements

Assign a new value to an existing index to modify it.

<details>
<summary>Example - Modifying an Array:</summary>

```
const numbers = [10, 20, 30];
numbers[1] = 25;
console.log(numbers); // Output: [10, 25, 30]
```

</details>

### Adding Elements

- **Using `push()`**: Adds elements to the end of the array

- **Using `unshift()`**: Adds elements to the beginning

<details>
<summary>Example – Adding Elements:</summary>

```
const animals = ["dog", "cat"];
animals.push("rabbit");
console.log(animals); // Output: ['dog', 'cat', 'rabbit']
animals.unshift("bird");
console.log(animals); // Output: ['bird', 'dog', 'cat', 'rabbit']
```
</details>

### Removing Elements

- **Using `pop()`**: Removes the last element

- **Using `shift()`**: Removes the first element

<details>
<summary>Example - Removing Elements</summary>

```
const items = ["a", "b", "c"];
items.pop();
console.log(items); // Output: ['a', 'b']
items.shift();
console.log(items); // Output: ['b']
```

</details>

### Iterating over Arrays

#### Traditional Loops

<details>
<summary>Example - for Loop</summary>

```
const scores = [10, 20, 30];
for (let i = 0; i < scores.length; i++) {
  console.log(scores[i]);
}
```

</details>

#### `forEach` Loop

<details>
<summary>Example - forEach Loop</summary>

```
const cities = ["Toronto", "New York", "Berlin"];
cities.forEach((city) => console.log(city));
```

</details>

---

## Array Methods

### Transformation Methods

- `map()`: Creates a new array with transformed elements

- `filter()`: Creates a new array with elements that pass a condition

<details>
<summary>Example - Using map and filter</summary>

```
const numbers = [1, 2, 3, 4];
const squared = numbers.map((num) => num * num);
console.log(squared); // Output: [1, 4, 9, 16]
const even = numbers.filter((num) => num % 2 === 0);
console.log(even); // Output: [2, 4]
```

</details>

### Search Methods

- `find()`: Finds the first element that matches a condition

- `includes()`: Checks if an element exists in the array

<details>
<summary>Example - Using find and includes</summary>

```
const ages = [15, 20, 25];
const adult = ages.find((age) => age >= 18);
console.log(adult); // Output: 20
console.log(ages.includes(15)); // Output: true
```

</details>

### Sorting Methods

- `sort()`: Sorts an array in place

- `reverse()`: Reverses the array order

<details>
<summary>Example - Sorting an Array</summary>

```
const names = ["Charlie", "Alice", "Bob"];
names.sort();
console.log(names); // Output: ['Alice', 'Bob', 'Charlie']
```

</details>

---

References[^1]

[^1]: Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0