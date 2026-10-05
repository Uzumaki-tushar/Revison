# ⚡ JavaScript Quick Revision & Technical Reference

> A comprehensive, interview-ready reference guide covering JavaScript fundamentals, DOM manipulation, functions, object-oriented concepts, and event handling.

---

## 📑 Table of Contents
- [1. Fundamental Concepts](#1-fundamental-concepts)
- [2. Variables, Scope & Hoisting](#2-variables-scope--hoisting)
- [3. Data Types & Type Coercion](#3-data-types--type-coercion)
- [4. Operators & Control Flow](#4-operators--control-flow)
- [5. Arrays & Methods](#5-arrays--methods)
- [6. Functions & Modern Mechanics](#6-functions--modern-mechanics)
- [7. Strings & Literals](#7-strings--literals)
- [8. DOM Manipulation](#8-dom-manipulation)
- [9. Error Handling](#9-error-handling)
- [10. Objects, Sets & Maps](#10-objects-sets--maps)
- [11. Event Handling & Architecture](#11-event-handling--architecture)

---

## 1. Fundamental Concepts

### 1.1 What is the DOM? (HTML vs. DOM)
* **DOM (Document Object Model):** A tree-like programming interface created by the browser representing the structured HTML document. It converts HTML nodes into objects that JavaScript can dynamically inspect, update, or delete.
* **HTML vs. DOM:**
  * **HTML:** Static source text/markup stored on disk.
  * **DOM:** Dynamic live memory representation created inside the browser rendering engine.

```
+------------------+         Browser Parses          +---------------------+
| HTML Source Code |  --------------------------->   | Dynamic DOM Tree    |
| (Static Markup)  |                                 | (JavaScript Object) |
+------------------+                                 +---------------------+
```

### 1.2 What is JavaScript & the JS Engine?
* **JavaScript:** A high-level, single-threaded, dynamic programming language used to execute complex interactive behaviors, state modifications, API interactions, and user interface logic.
* **JS Engine:** A specialized executable program (e.g., **V8** in Chrome/Node.js, **SpiderMonkey** in Firefox, **JavaScriptCore** in Safari) that parses, compiles (JIT), and executes JavaScript code into machine code.

### 1.3 Client-Side vs. Server-Side

```
+-----------------------------------------------------------------------+
|                             HTTP Request                              |
|   +-------------------+                      +-------------------+    |
|   |    Client-Side    |   ---------------->  |    Server-Side    |    |
|   | (Browser Executed)|                      | (Node/Java/Python)|    |
|   | UI, Input, DOM    |   <----------------  | DB, Auth, Logic   |    |
|   +-------------------+     HTTP Response    +-------------------+    |
+-----------------------------------------------------------------------+
```

| Dimension | Client-Side | Server-Side |
| :--- | :--- | :--- |
| **Execution Context** | User's local browser instance | Remote host server environment |
| **Primary Focus** | User Interface, interactivity, local state | Business logic, authentication, database ops |
| **Security Risk** | High exposure (code visible to user) | Low exposure (protected execution) |

---

## 2. Variables, Scope & Hoisting

### 2.1 JavaScript Scopes
Scope dictates where declared variables are accessible in your code:
1. **Global Scope:** Accessible anywhere in the application.
2. **Function Scope:** Accessible only within the declaring function (`var`).
3. **Block Scope:** Accessible only inside curly braces `{}` (`let`, `const`).
4. **Module Scope:** Accessible only within the specific JS module file.

> [!NOTE]
> Declaring a variable without `var`, `let`, or `const` in non-strict mode assigns it as an **implicit global variable**, attaching it directly to the `window` object in browsers.

### 2.2 `var` vs `let` vs `const`

| Feature | `var` | `let` | `const` |
| :--- | :---: | :---: | :---: |
| **Scope** | Function | Block | Block |
| **Reassignable** | ✅ Yes | ✅ Yes | ❌ No |
| **Redeclarable** | ✅ Yes | ❌ No | ❌ No |
| **Initialization** | Optional | Optional | **Required** |
| **Hoisting Behavior** | Hoisted (`undefined`) | Hoisted (TDZ) | Hoisted (TDZ) |

### 2.3 Hoisting Mechanics
Hoisting is the engine's phase where declarations are moved into memory during the creation phase prior to code execution.

```javascript
// Hoisting with 'var'
console.log(a); // Output: undefined
var a = 10;

// Hoisting with 'let' / 'const' (Temporal Dead Zone)
console.log(b); // Throws ReferenceError!
let b = 20;
```

#### Hoisting Behavior Reference Table

| Declaration Type | Hoisted? | Accessible Before Line? | Initial Value |
| :--- | :---: | :---: | :--- |
| **`var`** | ✅ | ✅ | `undefined` |
| **`let` / `const`** | ✅ | ❌ | Uninitialized (**Temporal Dead Zone**) |
| **Function Declaration** | ✅ | ✅ | Complete Function Body |
| **Function Expression** | Depends | ❌ | `undefined` (if `var`) or TDZ (if `let`/`const`) |

---

## 3. Data Types & Type Coercion

### 3.1 Primitive vs. Non-Primitive Data Types

```
JavaScript Data Types
 ├── Primitives (Value Types)
 │    ├── String, Number, BigInt, Boolean
 │    └── Undefined, Null, Symbol
 └── Non-Primitives (Reference Types)
      ├── Object, Array
      └── Function, Set, Map
```

| Characteristic | Primitive Types | Non-Primitive (Reference) Types |
| :--- | :--- | :--- |
| **Storage** | Value stored directly in stack memory | Reference pointer stored in stack pointing to heap memory |
| **Mutability** | Immutable (value itself cannot change) | Mutable (properties and elements can change) |
| **Comparison** | Compared by **Value** (`10 === 10`) | Compared by **Reference** (`{} === {}` is `false`) |

### 3.2 `undefined` vs `null`

```javascript
let uninitializedVar;      // undefined (automatically assigned)
let emptyValue = null;     // null (explicitly assigned)

console.log(typeof uninitializedVar); // "undefined"
console.log(typeof emptyValue);        // "object" (Legacy JS bug)
```

| Scenario | `undefined` | `null` |
| :--- | :--- | :--- |
| **Meaning** | Variable declared, but no value set | Intentional absence of value |
| **Source** | Set by engine automatically | Set explicitly by programmer |
| **`typeof` Output** | `"undefined"` | `"object"` *(Historical JS implementation defect)* |

---

## 4. Operators & Control Flow

### 4.1 Type Coercion & Equality

Type coercion is the automatic conversion of values from one data type to another.

```javascript
// Implicit Coercion Example
console.log("10" + 5);  // "105" (String concatenation)
console.log("10" - 5);  // 5     (Numeric subtraction)

// Equality Comparison
console.log(5 == "5");  // true  (Loose: coerces string to number)
console.log(5 === "5"); // false (Strict: checks both type and value)
```

### 4.2 Short-Circuit Evaluation
JavaScript short-circuits evaluation when the outcome of a logical expression is decided before reaching the end.

* **`&&` (AND):** Returns first falsy value, or last truthy value if all are truthy.
* **`||` (OR):** Returns first truthy value, or last falsy value if all are falsy.
* **`??` (Nullish Coalescing):** Returns right operand only if left operand is `null` or `undefined`.

```javascript
let user = null;
let defaultName = user ?? "Guest"; // "Guest"
```

### 4.3 Operator Categories

| Category | Operands Count | Example |
| :--- | :---: | :--- |
| **Unary** | `1` | `typeof x`, `-y`, `++i` |
| **Binary** | `2` | `a + b`, `x && y`, `i > j` |
| **Ternary** | `3` | `condition ? trueVal : falseVal` |

---

## 5. Arrays & Methods

### 5.1 Common Array Operations

```javascript
let arr = [10, 20, 30];

arr.push(40);     // Adds to END       -> [10, 20, 30, 40]
arr.pop();        // Removes from END  -> [10, 20, 30]
arr.unshift(5);   // Adds to START     -> [5, 10, 20, 30]
arr.shift();      // Removes from START-> [10, 20, 30]
```

### 5.2 Array Method Quick Reference

| Method | Returns | Modifies Original? | Use Case |
| :--- | :--- | :---: | :--- |
| **`push()`** | New length | ✅ | Add item(s) to end |
| **`pop()`** | Removed item | ✅ | Remove last item |
| **`unshift()`** | New length | ✅ | Add item(s) to start |
| **`shift()`** | Removed item | ✅ | Remove first item |
| **`slice(start, end)`** | Shallow copy array | ❌ | Extract slice without mutating original |
| **`splice(s, delCount, ...items)`** | Array of deleted items | ✅ | Delete, insert, or replace items at index |
| **`concat()`** | New array | ❌ | Merge multiple arrays |
| **`map()`** | New transformed array | ❌ | Transform every element |
| **`filter()`** | Filtered array | ❌ | Get subset of items matching predicate |
| **`find()`** | Single item or `undefined` | ❌ | Locate first item matching condition |
| **`forEach()`** | `undefined` | ❌ | Execute side-effect per item |

### 5.3 `map()` vs `forEach()`

```javascript
const numbers = [1, 2, 3];

// forEach: used for side effects
numbers.forEach(num => console.log(num * 2)); // Logs 2, 4, 6 (Returns undefined)

// map: used to transform array into new array
const doubled = numbers.map(num => num * 2);  // [2, 4, 6]
```

### 5.4 Spread (`...`) vs Rest (`...`) Operators

```javascript
// Spread: Expands elements out of array/object
const arr1 = [1, 2];
const combined = [...arr1, 3, 4]; // [1, 2, 3, 4]

// Rest: Collects multiple elements into an array parameter
function sum(...args) {
  return args.reduce((acc, val) => acc + val, 0);
}
```

---

## 6. Functions & Modern Mechanics

### 6.1 Function Types Comparison

| Type | Syntax Example | Hoisted? | Has Own `this`? |
| :--- | :--- | :---: | :---: |
| **Declaration** | `function add(a, b) { return a + b; }` | ✅ Yes | ✅ Yes |
| **Expression** | `const add = function(a, b) { return a + b; };` | ❌ No | ✅ Yes |
| **Arrow Function** | `const add = (a, b) => a + b;` | ❌ No | ❌ (Lexical `this`) |

> [!TIP]
> **First-Class Citizens:** In JavaScript, functions can be assigned to variables, passed as arguments to other functions, and returned from functions—just like any other value.

### 6.2 Pure vs. Impure Functions

```javascript
// Pure Function: Deterministic, no side effects
function addPure(a, b) {
  return a + b;
}

// Impure Function: Relies on / modifies external state
let total = 0;
function addImpure(a) {
  total += a; // Mutates outer scope variable
  return total;
}
```

### 6.3 Function Currying
Currying transforms a function taking multiple parameters into a chain of unary functions:

```javascript
// Standard Function
const multiply = (a, b, c) => a * b * c;

// Curried Function
const curriedMultiply = a => b => c => a * b * c;
console.log(curriedMultiply(2)(3)(4)); // Output: 24
```

### 6.4 `call()`, `apply()`, and `bind()`

```javascript
const person = { name: "Tushar" };

function greet(greeting, punctuation) {
  console.log(`${greeting}, ${this.name}${punctuation}`);
}

// call: Invokes function immediately, arguments passed individually
greet.call(person, "Hello", "!"); // Output: "Hello, Tushar!"

// apply: Invokes function immediately, arguments passed as array
greet.apply(person, ["Hi", "."]);  // Output: "Hi, Tushar."

// bind: Returns a new function with bound context for future invocation
const boundGreet = greet.bind(person, "Hey");
boundGreet("!");                   // Output: "Hey, Tushar!"
```

---

## 7. Strings & Literals

### 7.1 String Quote Comparison

| Feature | Single `' '` | Double `" "` | Backticks `` ` ` |
| :--- | :---: | :---: | :---: |
| **String Creation** | ✅ | ✅ | ✅ |
| **Interpolation `${}`** | ❌ | ❌ | ✅ |
| **Multi-line Strings** | ❌ | ❌ | ✅ |

### 7.2 Core String Methods

```javascript
const str = "  JavaScript Revision  ";

console.log(str.trim().toLowerCase());  // "javascript revision"
console.log(str.includes("Script"));    // true
console.log(str.slice(2, 12));          // "JavaScript"
console.log(str.replace("a", "@"));     // "  J@vascript Revision  "
console.log(str.replaceAll("a", "@"));  // "  J@v@script Revision  "
```

> [!NOTE]
> **String Immutability:** Strings in JavaScript are immutable. Method calls like `.replace()` or `.toUpperCase()` return a new string rather than modifying the original value.

---

## 8. DOM Manipulation

### 8.1 Selector Methods

```javascript
// Single Element Selection (Returns Element or null)
const mainHeader = document.getElementById("header");
const firstCard = document.querySelector(".card");

// Multiple Element Selection (Returns HTMLCollection / NodeList)
const allButtons = document.getElementsByTagName("button"); // HTMLCollection (Live)
const cardItems  = document.querySelectorAll(".card-item");  // NodeList (Static)
```

| Selection Method | Return Type | Accepts CSS Selectors? | Live / Static |
| :--- | :--- | :---: | :--- |
| **`getElementById()`** | Element / `null` | ❌ | Live |
| **`getElementsByClassName()`** | HTMLCollection | ❌ | Live |
| **`querySelector()`** | Element / `null` | ✅ | Static |
| **`querySelectorAll()`** | NodeList | ✅ | Static |

### 8.2 Manipulating Elements, Classes, & Attributes

```javascript
const element = document.querySelector("#content");

// Text Content Updates
element.textContent = "Safe Text"; // Replaces content safely (No HTML parsing)
element.innerHTML = "<b>Bold</b>"; // Parses string as HTML elements

// Class Manipulation
element.classList.add("active");
element.classList.remove("hidden");
element.classList.toggle("selected");

// Attribute Operations
element.setAttribute("data-id", "101");
const id = element.getAttribute("data-id");
element.removeAttribute("disabled");
```

---

## 9. Error Handling

### 9.1 `try...catch...finally` Architecture

```javascript
try {
  // Code block that may throw an error
  let result = parseUserData(jsonString);
} catch (error) {
  // Executes if an exception is thrown in try block
  console.error(`Name: ${error.name} | Message: ${error.message}`);
} finally {
  // Executes regardless of success or failure
  cleanupResources();
}
```

### 9.2 Standard JavaScript Errors

```
Error Types
 ├── SyntaxError     (Invalid syntax)
 ├── ReferenceError  (Accessing undeclared variables)
 ├── TypeError       (Invalid operation on incompatible type)
 └── RangeError      (Numeric value out of allowable bounds)
```

---

## 10. Objects, Sets & Maps

### 10.1 Object Creation Patterns

```javascript
// 1. Object Literal
const obj = { name: "Tushar" };

// 2. Class Constructor
class Person {
  constructor(name) { this.name = name; }
}
const person1 = new Person("Tushar");

// 3. Object.create (Prototypal Inheritance)
const proto = { greet() { return "Hello"; } };
const person2 = Object.create(proto);
```

### 10.2 Copying Objects (Shallow vs. Deep Copy)

```javascript
const original = { name: "Tushar", details: { age: 23 } };

// Shallow Copy (Nested object references are shared!)
const shallowCopy = { ...original };

// Deep Copy (Nested objects are copied independently)
const deepCopy = structuredClone(original);
```

### 10.3 Sets & Maps

```javascript
// Set: Store unique values of any type
const uniqueNumbers = new Set([1, 2, 2, 3, 4]);
uniqueNumbers.add(5);
console.log(uniqueNumbers.has(2)); // true
console.log([...uniqueNumbers]);  // [1, 2, 3, 4, 5]

// Map: Store key-value pairs with ANY data type as key
const map = new Map();
const keyObj = {};
map.set(keyObj, "Metadata value");
console.log(map.get(keyObj));      // "Metadata value"
```

---

## 11. Event Handling & Architecture

### 11.1 Event Propagation (Capturing vs. Bubbling)

When an event occurs on a DOM element, it travels through two primary phases:

```
                  DOCUMENT / WINDOW
                         | ^
  1. Capturing Phase     | |  3. Bubbling Phase
  (Parent down to Child) | |  (Child up to Parent)
                         v |
                  TARGET ELEMENT (2. Target Phase)
```

* **Capturing Phase:** Event trickles down from `window` through parent elements to target.
* **Bubbling Phase:** Event bubbles up from target back through parent elements to `window`.

### 11.2 Event Delegation Pattern
Instead of adding event listeners to multiple child elements, attach a single event listener to a common parent element.

```javascript
// Attach single listener to parent list element
document.querySelector("#user-list").addEventListener("click", (event) => {
  // Target refers to the exact element that triggered the click
  if (event.target.matches("li.user-item")) {
    console.log("Clicked user item:", event.target.textContent);
  }
});
```

### 11.3 Event Control Methods

```javascript
// Prevents default browser actions (e.g., stopping form navigation on submit)
event.preventDefault();

// Prevents further propagation (bubbling/capturing) up or down the DOM tree
event.stopPropagation();
```