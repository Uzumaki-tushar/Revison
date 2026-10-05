# Javascript Revision

1. What is DOM? What is the difference between HTML and DOM?
DOM = Document Object Model
The DOM is a tree-like representation of an HTML page created by the browser.
When the browser loads an HTML file, it reads the HTML and converts it into objects/nodes that JavaScript can access and modify
HTML is the source/code. DOM is the browser's object representation of that HTML.
2. what is Javascript? what is the role of JS engine?
**JavaScript (JS)** is a **programming language** mainly used to make web pages **dynamic and interactive**.
HTML gives the page its **structure**, CSS gives it **styling**, and JavaScript provides **behavior/logic**.
Function→ what will happen when user click a button, form submittion, change html/css dynamically, call apis ,etc.
Javascript Engine→ A **JavaScript engine** is a program that **takes JavaScript code and executes it**.
Ex→ v8 used in chrome browser.
3. What are Client side and Server side?
Client-side code runs on the client's device, usually inside the web browser.
**Server-side code runs on a server**, not directly in the user's browser.
Client-side refers to code that executes on the user's device, usually in the browser, and is primarily responsible for the user interface and interactions. Server-side refers to code that executes on a server and handles things such as business logic, authentication, API requests, and database operations. The client and server communicate through protocols such as HTTP/HTTPS.
4. What is Scope in JS?
Scope determines where a variable can be accessed in your JavaScript code.
There are mainly 4 scopes :
Global Scope
Function Scope
Block Scope
Module Scope
IMP:  let and const → block scope {}.  var → functional scope.
5. What is the type of a variable in JS when it is declared without using the var, let or const keywords?
If you declare a variable without var, let, or const, JavaScript treats it as an implicit global variable in non-strict mode.
6. What is Hoisting in Javascript?
Hoisting is JavaScript's behavior where declarations of variables, functions, and classes are processed before the code is executed.

| Declaration | Hoisted? | Can access before declaration? | Initial value |
| --- | --- | --- | --- |
| `var` | ✅ | ✅ | `undefined` |
| `let` | ✅ | ❌ | TDZ |
| `const` | ✅ | ❌ | TDZ |
| Function declaration | ✅ | ✅ | Function itself |
| Function expression | Depends on declaration (`var`/`let`/`const`) | Usually ❌ | Depends |
1. What is JSON?
JSON = JavaScript Object Notation
JSON is a **text-based data format** used to **store and exchange data**, especially between a **client and server**.
ex→
{
"name": "Tushar",
"age": 23,
"skills": ["Java", "Python", "JavaScript"]
}

2. What are variables? What is the difference between var, let and const?
A **variable** is a named container/reference used to store a value that your program can use and work with.
The main differences are **scope, redeclaration, reassignment, and hoisting behavior.**

| Feature | `var` | `let` | `const` |
| --- | --- | --- | --- |
| Scope | Function | Block | Block |
| Reassign | ✅ Yes | ✅ Yes | ❌ No |
| Redeclare same scope | ✅ Yes | ❌ No | ❌ No |
| Must initialize immediately | ❌ No | ❌ No | ✅ Yes |
| Hoisted | ✅ Yes | ✅ Yes* | ✅ Yes* |
| Temporal Dead Zone | ❌ No | ✅ Yes | ✅ Yes |
1. **What are Data Types in JavaScript?**
A **data type** tells JavaScript **what kind of value** a variable contains.

2. what is the difference between primitive and non-primitive data types?

| Primitive | Non-Primitive |
| --- | --- |
| Represents a simple value | Represents a complex structure |
| 7 primitive types | Objects and their specialized forms |
| Immutable values | Objects can generally be mutated |
| Variables hold the value itself | Variables hold a reference to an object |
| Compared by value | Objects are compared by reference |
| Usually simpler | Can contain multiple values/properties |
1. what is the difference between null and undefined in JS?

| `undefined` | `null` |
| --- | --- |
| Value is not assigned | Intentionally represents no value |
| Usually happens automatically | Usually assigned explicitly |
| `let x;` → `undefined` | `let x = null` |
| Means "not available/not assigned" | Means "empty/nothing intentionally" |
| `typeof undefined` → `"undefined"` | `typeof null` → `"object"` ⚠️ historical JS bug |
1. what is type coercion in JS?
Type coercion in JavaScript means converting a value from one data type to another, often automatically by JavaScript when an operation requires it.
ex→
let a = "10";
let b = 5;
console.log(a + b); // "105”

2. What is operator precedence? 
**Operator precedence** in JavaScript determines **which operator gets executed first when an expression contains multiple operators**.

3. What is the difference between unary, binay and ternary operators? 

| Type | Number of operands | Example |
| --- | --- | --- |
| **Unary** | 1 | `-x` |
| **Binary** | 2 | `x + y` |
| **Ternary** | 3 | `x > 5 ? "Yes" : "No"` |
1. What is short-circuit evaluation in JS?
**Short-circuit evaluation** in JavaScript means that JavaScript **stops evaluating an expression as soon as it already knows the final result**.
It mainly happens with the logical operators:
&& → AND
|| → OR
?? → Nullish coalescing

2. What are the types of conditions statements in JS?
If else, switch, ternary

3. What is the difference between == and === ?
The main difference between **`==` and `===`** is **type coercion**.
- `==` → **loose equality** → allows type coercion
- `===` → **strict equality** → does not perform type coercion
1. What is the difference between Spread and Rest operator in JS?
**Spread = expand/unpack
Rest = collect/pack
ex→ spread**
let a = [1, 2, 3];
let b = [4, 5, 6];
let result = [...a, ...b];  //spread operator
console.log(result);
output→ [1, 2, 3, 4, 5, 6]

ex→ rest
function add(...numbers) {
let sum = 0;

```
for (let num of numbers) {
    sum += num;
}

return sum;
```

}

console.log(add(10, 20, 30)); // 60

1. What are Arrays in JS? How to get, add & remove elements from arrays?
An **array** is a data structure used to store **multiple values in a single variable**.

| Method | Purpose | Example |
| --- | --- | --- |
| `push()` | Add at end | `arr.push(10)` |
| `pop()` | Remove from end | `arr.pop()` |
| `unshift()` | Add at beginning | `arr.unshift(10)` |
| `shift()` | Remove from beginning | `arr.shift()` |
| `splice()` | Add/remove at specific position | `arr.splice(1, 1)` |
| `at()` | Get element by index | `arr.at(-1)` |
| `length` | Get array size | `arr.length` |
1.  What is the indexOf() method of an Array?
To get the index of the particular element

2. What is the difference between find() and filter() method of an array?
Both find() and filter() are used to search an array based on a condition, but the key difference is:
find() → returns the first matching element
filter() → returns all matching elements

ex → find
let numbers = [10, 15, 20, 25, 30];
let result = numbers.find(num => num > 18);
console.log(result);

ex → filter
let numbers = [10, 15, 20, 25, 30];
let result = numbers.filter(num => num > 18);
console.log(result);

3. What is the slice() method of an Array?
`slice()` is an **Array method used to extract a portion of an array without modifying the original array**.
array.slice(start, end)

4. What is the difference between push() and concat() methods of an Array?
`push()` modifies the original array, while `concat()` creates and returns a new array.

|  | `push()` | `concat()` |
| --- | --- | --- |
| Modifies original array | ✅ Yes | ❌ No |
| Returns | New array length | New array |
| Adds to end | ✅ | ✅ |
| Combines arrays | Not directly | ✅ |
| `a.push(b)` | `[1, 2, [3, 4]]` | — |
| `a.concat(b)` | — | `[1, 2, 3, 4]` |
1. What is the splice() method of an Array?
`splice()` is an **Array method used to add, remove, or replace elements at a specific position in an array**.
`splice()` modifies the original array.
Syntax
array.splice(start, deleteCount, item1, item2, ...);

splice(start, deleteCount, items to add)
               ↓             ↓                          ↓
         where      how many       what to add

2. What is the difference between map() and forEach()?
Both map() and forEach() are array methods used to iterate over array elements, but their main purpose is different.
map() → transforms an array and returns a new array
forEach() → performs an action for each element and returns undefined

Use `forEach()` when you want to **do something with each element**, but don't need a new array.
ex→
let numbers = [1, 2, 3, 4];
numbers.forEach(num => {
       console.log(num);
});
output→ 1,2,3,4,5

Use `map()` when you want to **transform each element and create a new array**.
ex→
let numbers = [1, 2, 3, 4];
let result = numbers.map(num => num * 2);
console.log(result);
output→ [2, 4, 6, 8]

3. How do you sort and reverse an array?
array.sort() ,  array.reverse()

| Method | Purpose | Modifies original? |
| --- | --- | --- |
| `sort()` | Sort elements | ✅ Yes |
| `reverse()` | Reverse elements | ✅ Yes |
| `toReversed()` | Reverse elements | ❌ No |
| `[...arr].sort()` | Sort a copy | ❌ No |
1. what is Array Destructing in JS?
**Array destructuring** is a way to **extract values from an array and store them in separate variables** in a single statement.
ex→
let numbers = [10, 20, 30, 40, 50];
let [first, second, ...remaining] = numbers;
console.log(first);     // 10
console.log(second);    // 20
console.log(remaining); // [30, 40, 50]

2. what are array-like objects in JS?
An array-like object is an object that looks and behaves somewhat like an array, because it has:
Numeric indexes (0, 1, 2, ...)
A length property
But it is not actually an Array.

3. How to convert an array-like object into an array?
let arr = Array.from(arrayLike);
console.log(arr);

4. what are loops? what are the types of loops in JS?
A loop is used to execute a block of code repeatedly as long as a particular condition is satisfied or for each item in a collection.
syntax

for (initialization; condition; update) {
// code
}

while (condition) {
// code
}

let i = 10;
do {
console.log(i);
} while (i < 5);

for          → general-purpose loop
while        → condition first
do...while   → execute first, condition later
for...of     → values
for...in     → keys

5. What is the difference break and continue statement?
`break` — Stop the entire loop
`continue` — Skip the current iteration

6. What are Functions in JS? what are the types of functions?
A **function** is a reusable block of code designed to perform a particular task.

7. What is the difference between named and anonymous functions? When to use what in applications?
A named function has an explicit name and is generally used for reusable or important pieces of logic. An anonymous function doesn't have an explicit name and is commonly used for one-time operations, especially callbacks passed to methods such as map(), filter(), and forEach(). In modern JavaScript, anonymous callbacks are often written using arrow functions.

8. What is function expression in JS?
A function expression is a function that is created as part of an expression and assigned to a variable or another value. It can be anonymous or named, and arrow functions are also a form of function expression. Unlike function declarations, function expressions cannot be called before their assignment is executed.

9. What are Arrow Functions in JS? What is its use?
An **arrow function** is a shorter way to write a function in JavaScript. It was introduced in **ES6 (ECMAScript 2015)**.

10. What is a callback function in JavaScript?
A **callback function** is a function that is **passed as an argument to another function** and is called/executed later by that function.

11. What is Higher-order function in JS? 
A Higher-Order Function (HOF) is a function that does at least one of these:
Takes another function as an argument, or
Returns another function
ex→ map, filter, forEach

12. What is the difference between arguments and parameters?
**Parameters are variables defined in the function declaration.
Arguments are the actual values passed when calling the function.**

13. Default Parameters in functions in JS?
Default parameters allow you to assign a default value to a function parameter when no value (or undefined) is provided for that parameter.
ex→
function greet(name = "Guest") {
console.log("Hello " + name);
}
greet("Tushar");
// Hello Tushar
greet();
// Hello Guest

14. what are First-Class functions in JS?
JavaScript treats functions as first-class citizens, meaning functions can be treated like any other value. They can be stored in variables, passed as arguments, returned from other functions, and stored in data structures such as arrays and objects. This feature enables concepts such as callbacks, higher-order functions, and closures.

15. what are Pure and Impure functions in JS?
A pure function is a function that always produces the same output for the same inputs and has no side effects. An impure function may depend on or modify external state, perform side effects, or produce different results for the same input. Pure functions are predictable, easier to test, and easier to maintain.

16. what is Function Currying in JS?
Function currying is a technique in JavaScript where a function that takes multiple arguments is transformed into a sequence of functions that each take one argument. For example, `add(a, b, c)` becomes `add(a)(b)(c)`. Currying is useful for creating reusable and configurable functions and is commonly associated with functional programming.

17. call() & apply() & bind() methods in JS?
`call()`, `apply()`, and `bind()` are methods used to control the `this` value of a function. `call()` invokes the function immediately with arguments passed individually, `apply()` invokes it immediately with arguments passed as an array or array-like object, while `bind()` returns a new function with `this` bound to the specified object and executes it later.

| Method | Executes immediately? | How arguments are passed? | Returns |  |
| --- | --- | --- | --- | --- |
| `call()` | ✅ Yes | Individually | Function result |  |
| `apply()` | ✅ Yes | Array/array-like | Function result |  |
| `bind()` | ❌ No | Individually | New function |  |
1. Template Literals and String Interpolation
**Template literals** are a way to create strings using backticks
**String interpolation** means inserting variables or expressions directly inside that string using ${}.

2. single quotes vs double quotes vs backticks

| Feature | `' '` Single | `" "` Double | `` `` Backticks |
| --- | --- | --- | --- |
| Creates a string | ✅ | ✅ | ✅ |
| String interpolation `${}` | ❌ | ❌ | ✅ |
| Multiline strings | ❌* | ❌* | ✅ |
| Escape quotes | ✅ | ✅ | ✅ |
| Template literals | ❌ | ❌ | ✅ |
1. String Operations in JS

| Method | Purpose |
| --- | --- |
| `length` | Get string length |
| `charAt()` | Get character at index |
| `toUpperCase()` | Convert to uppercase |
| `toLowerCase()` | Convert to lowercase |
| `concat()` | Join strings |
| `includes()` | Check if substring exists |
| `startsWith()` | Check beginning |
| `endsWith()` | Check ending |
| `indexOf()` | Find first position |
| `lastIndexOf()` | Find last position |
| `slice()` | Extract part of string |
| `substring()` | Extract part of string |
| `replace()` | Replace text |
| `replaceAll()` | Replace all occurrences |
| `trim()` | Remove spaces from both ends |
| `split()` | Convert string into array |
| `repeat()` | Repeat string |
1. what is string immutability?
**String immutability** means that **once a string is created, its individual characters cannot be changed directly**.

2. what is DOM? what is the difference between HTML and DOM?
DOM stands for Document Object Model.
The DOM is a **programming representation of an HTML document** that the browser creates when it loads a webpage.

3. How do you select, modify, or remove DOM elements?
We can manipulate DOM elements in three main steps: first select the element using methods such as getElementById(), querySelector(), or querySelectorAll(). Then modify it using properties and methods such as textContent, innerHTML, style, classList, and setAttribute(). Finally, we can remove elements using remove() or removeChild().

4. What is the difference between getElementById, getElementByClassName and getElementsByTagName? 

| Method | Searches by | Number of elements | Return type |
| --- | --- | --- | --- |
| `getElementById()` | ID | One | Element / `null` |
| `getElementsByClassName()` | Class | One or more | HTMLCollection |
| `getElementsByTagName()` | Tag | One or more | HTMLCollection |
1. What is the difference between querySelector() and querySelectorAll()?

| Feature | `querySelector()` | `querySelectorAll()` |
| --- | --- | --- |
| Returns | First matching element | All matching elements |
| Return type | Element / `null` | NodeList |
| Multiple matches | Only first | All |
| No match | `null` | Empty NodeList |
| CSS selectors | ✅ Yes | ✅ Yes |
| `forEach()` directly | ❌ No | ✅ Yes |
| Collection type | Single element | Static NodeList |
1. what are the methods to manipulate elements, properties and attributes of JS DOM?

| Purpose | Methods / Properties |
| --- | --- |
| Change text | `textContent`, `innerText` |
| Change HTML | `innerHTML` |
| Change DOM properties | `value`, `checked`, `disabled`, `href`, `src`, etc. |
| Get attribute | `getAttribute()` |
| Set attribute | `setAttribute()` |
| Remove attribute | `removeAttribute()` |
| Check attribute | `hasAttribute()` |
| Add class | `classList.add()` |
| Remove class | `classList.remove()` |
| Toggle class | `classList.toggle()` |
| Check class | `classList.contains()` |
| Change CSS | `style` |
| Create element | `createElement()` |
| Add element | `append()`, `appendChild()`, `prepend()` |
| Remove element | `remove()`, `removeChild()` |
1. what is the difference between innerHTML vs textContent?
`textContent` is used to get or set the text content of an element and treats HTML tags as plain text. `innerHTML` is used to get or set the HTML content inside an element and parses HTML tags. Because `innerHTML` parses HTML, using it with untrusted input can introduce XSS vulnerabilities.

2. How to add or remove properties of HTML elements from the DOM using JS?

| Operation | Method |
| --- | --- |
| Add/change attribute | `setAttribute()` |
| Get attribute | `getAttribute()` |
| Remove attribute | `removeAttribute()` |
| Check attribute | `hasAttribute()` |
| Add class | `classList.add()` |
| Remove class | `classList.remove()` |
| Toggle class | `classList.toggle()` |
| Change DOM property | `element.property = value` |
1. How to add or remove style of HTML elements in the DOM using JS?
We can manipulate an element's style using the `.style` property, such as `element.style.color = "red"`. We can remove an inline style by setting it to an empty string or using `style.removeProperty()`. For predefined or multiple styles, it's usually cleaner to use `classList.add()`, `classList.remove()`, and `classList.toggle()` to add or remove CSS classes.

2. How to create new elements in DOM using JS? What is the difference between createElements() and cloneNode()?
createElement() creates a completely new DOM element from scratch, while cloneNode() creates a copy of an existing DOM element. cloneNode(false) creates a shallow copy containing only the element itself, while cloneNode(true) creates a deep copy including its child nodes. Event listeners added with addEventListener() are not copied by cloneNode().

| `createElement()` | `cloneNode()` |
| --- | --- |
| Creates a new element from scratch | Copies an existing element |
| Doesn't require an existing element | Requires an existing DOM node |
| Starts with no attributes/content unless you add them | Copies attributes/content depending on depth |
| `document.createElement("div")` | `element.cloneNode(true)` |
| Useful for dynamically building new elements | Useful for duplicating existing structures |
1. What is Error Handling in JS?
**Error handling** is the process of **detecting, handling, and responding to errors** that occur while a JavaScript program is running.

The most common way to handle errors is using `try...catch`.

try {
// code that might cause an error
} catch (error) {
// handle the error
}
finally{
}

JavaScript also allows you to **manually generate an error** using `throw`.

Error handling in JavaScript is the process of detecting and managing runtime errors so that the application can respond gracefully instead of unexpectedly stopping. JavaScript provides `try`, `catch`, `finally`, and `throw` for error handling. `try` contains potentially failing code, `catch` handles the error, `finally` executes regardless of whether an error occurred, and `throw` allows us to create custom errors.

1. What is the role of finally block in JS?
The **`finally` block** is used to execute code **regardless of whether an error occurs or not**.

2. What is the purpose of the throw statement in JS?
The **`throw` statement** is used to **manually generate an error** in JavaScript.
basic syntax
throw new Error("Something went wrong");

3. what is Error Propagation in JS?
**Error propagation** means an error **moves up through the chain of function calls until it is caught and handled**.
If a function encounters an error and doesn't handle it, the error is passed to the function that called it.
Error propagation in JavaScript is the process by which an uncaught error moves up through the call stack from the function where it occurred to its callers until a `catch` block handles it. If no function handles the error, it eventually becomes an uncaught error. A function can also catch an error, perform some processing such as logging, and rethrow it using `throw` so that a higher-level handler can deal with it.

4. Error Handling Best Practices

| Best Practice | Purpose |
| --- | --- |
| `try...catch` | Handle runtime errors |
| `throw new Error()` | Create proper errors |
| Meaningful messages | Easier debugging |
| `finally` | Cleanup |
| Handle Promise errors | Prevent unhandled rejections |
| Validate input | Prevent invalid operations |
| Log errors | Debug production problems |
| Don't expose sensitive data | Security |
| Don't silently ignore errors | Avoid hidden bugs |
| Propagate when appropriate | Centralized error handling |
1. what are the different types of error in JS?

SyntaxError    → Syntax is wrong
ReferenceError → Variable/reference is wrong
TypeError      → Type/operation is wrong
RangeError     → Value range is wrong
URIError       → URI is wrong
EvalError      → eval-related (legacy)
AggregateError → Multiple errors
Error          → General error

1. what are objects in JS? 
An **object in JavaScript is a collection of related data and functionality stored as key-value pairs**.

const person = {
name: "Tushar",
age: 23,
city: "Delhi",

```
greet: function() {
    console.log("Hello!");
}
```

};

64. In how many ways we can create an object?

| Method | Example | Common Use |
| --- | --- | --- |
| **Object Literal** | `{ name: "Tushar" }` | Simple objects |
| **`new Object()`** | `new Object()` | Rarely used |
| **Constructor Function** | `new Person()` | Older JS / prototypes |
| **Class** | `new Person()` | Modern OOP-style JS |
| **`Object.create()`** | `Object.create(proto)` | Prototypes/inheritance |
| **Factory Function** | `createPerson()` | Creating objects without `new` |
1. what is the difference between an array and an object?
An object stores data as key-value pairs and is generally used to represent an entity with named properties, whereas an array stores an ordered collection of values accessed using numeric indexes. Arrays are technically a special type of object in JavaScript, but they provide additional methods and behavior for working with ordered collections.

2. How to manipulate Objects in JS?

| Operation | Method / Syntax |
| --- | --- |
| Access | `obj.name` / `obj["name"]` |
| Add | `obj.key = value` |
| Update | `obj.key = newValue` |
| Delete | `delete obj.key` |
| Check property | `"key" in obj` |
| Get keys | `Object.keys(obj)` |
| Get values | `Object.values(obj)` |
| Get entries | `Object.entries(obj)` |
| Copy | `{ ...obj }` |
| Merge | `{ ...obj1, ...obj2 }` |
| Destructure | `const { name } = obj` |
| Prevent modification | `Object.freeze(obj)` |
| Prevent add/delete | `Object.seal(obj)` |
1. Dot Notation vs Bracket Notation
Dot notation and bracket notation are both used to access object properties. Dot notation uses `object.property` and is simpler and more readable for fixed, valid property names. Bracket notation uses `object["property"]` and is more flexible because it supports dynamic property names, variables, expressions, and property names containing spaces or special characters.

2. How to iterate through Objects in JS?

| Method | Iterates Over | Example |
| --- | --- | --- |
| `for...in` | Keys | `for (const key in obj)` |
| `Object.keys()` | Keys | `Object.keys(obj)` |
| `Object.values()` | Values | `Object.values(obj)` |
| `Object.entries()` | Key-value pairs | `Object.entries(obj)` |
| `entries + for...of` | Key-value pairs | `for (const [k,v] of ...)` |
1. How to check if a property exists or not?
We can check whether a property exists using the `in` operator, `hasOwnProperty()`, or the modern `Object.hasOwn()` method. The `in` operator checks both the object and its prototype chain, while `Object.hasOwn()` checks only properties directly owned by the object. Checking `property !== undefined` is not reliable because a property can exist with an `undefined` value.

2. How to clone an object?
shallow copy→ A **shallow copy** creates a new object, but nested objects/arrays are still shared between the original and the copy.

1) using spread operator {…}
const person = {
name: "Tushar",
age: 23,
city: "Delhi"
};
const copy = { ...person };
console.log(copy);

2) using object.assign()
const person = {
name: "Tushar",
age: 23,
city: "Delhi"
};
const copy = { ...person };
console.log(copy);

Important Problem with Shallow Copy→ The outer objects are different, but the nested `address` object is the **same reference

Deep Copy→** 
A **deep copy** creates a completely independent copy, including nested objects and arrays.

1) using structuredClone()
const copy = structuredClone(person);

3. Sets in JS
A **Set** in JavaScript is a built-in collection that stores **unique values**.
A Set is a built-in JavaScript collection used to store unique values. Unlike arrays, a Set automatically ignores duplicate values. We can add values using `add()`, check for values using `has()`, remove values using `delete()`, clear all values using `clear()`, and get the number of values using `size`. A common use case is removing duplicates from an array using `[...new Set(array)]`.

4. Map Object in JS
A **Map** is a built-in JavaScript data structure used to store **key-value pairs**.
const map = new Map();
users.set(1, "Tushar");
users.set(2, "Rahul");
users.set(3, "Aman");
users.delete(2);

5. Events in JS
In JavaScript, **events** are actions that happen in the browser—such as a user clicking a button, typing, submitting a form, or moving the mouse. JavaScript can **listen** for these events and run code when they occur.

| Event | Happens when... |
| --- | --- |
| `click` | User clicks an element |
| `dblclick` | User double-clicks |
| `mouseover` | Mouse enters an element |
| `mouseout` | Mouse leaves an element |
| `keydown` | A keyboard key is pressed |
| `keyup` | A keyboard key is released |
| `input` | Input value changes |
| `change` | Form value is changed/committed |
| `submit` | A form is submitted |
| `focus` | An input receives focus |
| `blur` | An input loses focus |
| `DOMContentLoaded` | HTML has been parsed |
1. Event Delegation in JS
**Event Delegation** is a technique where we attach **one event listener to a parent element instead of adding separate event listeners to each child element**.
It works because of **event bubbling**.
Event delegation is a JavaScript technique where we attach a single event listener to a parent element to handle events from its child elements. It relies on event bubbling and uses `event.target` or methods like `matches()` and `closest()` to identify the child that triggered the event. It reduces the number of event listeners and is especially useful for dynamically generated elements.

2. Event Bubbling and Event Capturing in JS
Both event bubbling and event capturing describe how an event travels through the DOM when an event occurs.
Capturing:  Parent → Child
Bubbling:   Child  → Parent

3. event.preventDefault() method in JS
`event.preventDefault()` is used to **stop the browser's default behavior** associated with an event.
It **does not stop the event itself**. It only prevents the browser's built-in/default action.

4. The use of "this" keyword in the context of event handling in JS
In **event handling**, `this` usually refers to the **DOM element on which the event handler is attached**.

Regular function:
this → element with the listener

Arrow function:
this → inherited from surrounding scope

event.target:
→ element that actually triggered the event

event.currentTarget:
→ element whose listener is running

5. How to remove (unattach) an event handler from an element in JS
element.removeEventListener("event", handler);