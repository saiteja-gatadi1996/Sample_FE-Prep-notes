#### 1. document.getElementById() vs document.querySelector

- Both are Javascript methods used to select and retrieve elements from the DOM element in a web page.

- <strong>document.getElementById()</strong>: This method is used to select an element from the DOM based on the unique ID attribute.

```js
const mainId = document.getElementById("main-id");
```

- <strong>document.querySelector()</strong>: This method allows you to select elements using more complex CSS selectors. It takes a CSS selector as a argument and <strong>returns the first matching element that matches the selector.</strong>

```js
const mainClass = document.querySelector(".main-class");
```

##### Return value:

- <strong>document.getElementById()</strong>: This method returns a single DOM element (if found) or null if no element with specified ID is present in the document.

- <strong>document.querySelector()</strong>: This method returns the first element that matches the specified CSS selector or null (if no matching element is found)

##### Limitations:

- <strong>document.getElementById()</strong>: As it selects elements <strong>solely based on their unique IDs</strong>, it can select a single element at a time.

- <strong>document.querySelector()</strong>: This method provides more flexibility as it can <strong>select elements based on classes, attributes, tag names</strong>. It can select any element that matches the provided selector <b><i>not just the ID.</i></b>

##### Performance:

- <strong>document.getElementById()</strong>: generally faster than the querySelector (since the browser can use an optimized lookup based on the ID).

- <strong>document.querySelector()</strong>: this might require more processing (as it selects elements using more complex CSS selectors)

---

#### 2. When to use reduce(), map(), foreach() and filter() in JavaScript?

##### reduce:

- When you want to accumulate values from an array into a single value (summing up values, avg calculation, concatenating strings)

- takes accumulator and current as arguments and returns the accumulated result.

- You can also provide an initial value for the accumulator as the second argument.

```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, current) => accumulator + current, 0);
console.log(sum); // 15
```

##### map:

- When you want to transform each and every element of an array into a new value based on the specified logic.

- It creates a new array.

```js
const numbers = [1, 2, 3, 4];

const doubledNums = numbers.map((item) => item * 2);
console.log(doubledNums); //[2, 4, 6, 8]
```

##### foreach():

- When you want to iterate through an array and perform an action on each element, but you don't want to create a new array or accumulate a single value.

```js
const nums = [1, 2, 3, 4];

nums.forEach((num) => console.log(num * 2)); //[2, 4, 6, 8]
```

- Modifies the original array

##### filter:

- When you want to create a new array containing elements that pass the condition (returns the new array that includes only elements that satisfied the condition)

```js
const numbers = [1, 2, 3, 4, 5, 6];

const filteredArray = numbers.filter((item) => item % 2 === 0);

console.log(filteredArray); // [2, 4, 6]
```

---

#### 3. What is Hoisting in JavaScript?

- Hoisting is the behaviour of javascript where variables and functional declartions are moved to top of the scope during the compilation phases before the code is executed.

- This means you can use variables and declartions before they are declared in the code.

  <u><b>Note:</b></u> Only the declarations are hoisted not the initializations or assignments.

  <b><u>Example:</u></b> Variables initialized with var are hoisted and assigned with default value <strong>undefined</strong>. let and const variables are also hoisted but not initialized until their actual declaration in the code.

  ```js
  console.log(name); // Output: undefined
  var name = "John Doe";
  console.log(name); // Output: John Doe
  ```

  ```js
  var name;
  console.log(name); // Output: undefined
  name = "John Doe";
  console.log(name); // Output: John Doe
  ```

```js
sayHello(); // Output: "Hello, World!"

function sayHello() {
  console.log("Hello, World!");
}
```

```js
function sayHello() {
  console.log("Hello, World!");
}

sayHello(); // Output: "Hello, World!"
```

```js
console.log(age); // Output: ReferenceError: Cannot access 'age' before initialization
let age = 30;
```

---

#### 4. What are closures ?

- A closure is created when a function is defined within another function and retains the access of the outer function variables <strong>even after the outer function has finished executing.</strong>

<i>In simpler terms, closure <b>closes over the variables</b> of its outer function, preserving their values and scope. </i>

```js
function outerFunction() {
  let num = 5;

  function innerFunction() {
    console.log(num);
  }

  return innerFunction;
}

const closureFunction = outerFunction();
console.log(closureFunctio()); // 5
```

##### Key points of Closures:

- Ability to remember the values of the outer function even after outer function has returned.

- Closures remember the environment which they were created including variables and scope.
- Useful for creating private variables and encapsulating functionality in JS.
- Can help in avoiding global space naming pollution and maintain data privacy.
- Used in Module, Factory (design patterns)

---

#### 5. How do you clone an object in JavaScript?

- Shallow Clone using Object.assign()

```js
const originalObject = { key1: "value1", key2: "value2" };
const clonedObj = Object.assign({}, originalObject);
```

- Shallow Clone using Spread operator

```js
const originalObject = { key1: "value1", key2: "value2" };
const clonedObj = { ...originalObject };
```

- Shallow Clone using Object.create()

```js
const originalObject = { key1: "value1", key2: "value2" };
const clonedObj = Object.create{Object.getPrototypeOf(originalObject), Object.getOwnPropertyDescriptors(originalObject)}
```

- Deep Clone using JSON.parse() and JSON.stringify():

```js
const originalObject = { key1: "value1", key2: "value2" };
const deepCloneObject = JSON.parse(JSON.stringify(originalObject));
```

- using loadash

```js
const _ = require("lodash");
const originalObject = { key1: "value1", key2: { nestedKey: "nestedValue" } };
const clonedObject = _.cloneDeep(originalObject);
```

---

#### 6. What are the possible ways to create objects in JavaScript?

##### 1. Object Literal

```js
const person = {
  name: "John Doe",
  age: 30,
  occupation: "Engineer",
};
```

##### 2. Object Constructor

```js
const person = new Object();

person.name = "John Doe";
person.age = 30;
person.occupation = "Engineer";
```

##### 3. Object.create()

```js
const prototypeObj = {
  greet: function () {
    console.log(`Hello, my name is ${this.name}.`);
  },
};

const person = Object.create(prototypeObj);
person.name = "John Doe";
person.age = 30;
person.occupation = "Engineer";
```

##### 4. Function constructor

```js
function Person(name, age, occupation) {
  this.name = name;
  this.age = age;
  this.occupation = occupation;
}

const person = new Person("John Doe", 30, "Engineer");
```

##### 5. ES6 Classes

```js
class Person {
  constructor(name, age, occupation) {
    this.name = name;
    this.age = age;
    this.occupation = occupation;
  }
  greet() {
    console.log(`Hello, my name is ${this.name}.`);
  }
}

const person = new Person("John Doe", 30, "Engineer");
```

##### 6. Factory Functions:

```js
function Person(name, age, occupation) {
  return {
    name,
    age,
    occupation,
  };
}

const person = Person("John Doe", 30, "Engineer");
```

---

#### 7. What are the javascript data types?

##### 1. Primitive Data Types:

- number
- string
- boolean
- null: Represents an intentional absence of any value.
- undefined: Represents a variable that has been declared but not assigned a value.
- symbol: Represents a unique and immutable value, often used as a property key in objects (added in ECMAScript 6).

##### 2. Object Data Types:

- object - Represents a collection of key-value pairs (keys as strings, values can be of any data type)

##### 3. Special Data Types:

- function - Reusable block of code that can be called with arguments.
- BigInt - Represents integers with arbitrary precision (Added in Ecmascript 2020)

---

#### 8. What are global variables ?

- Variables those are declared outside of the function or any block (it has global visibility and can be accessed and modified from any part of the code.)
- They are accessible anywhere in the code (including all functions and blocks within the same script or module)

```js
// Global variable
let globalVar = "I am a global variable";

function foo() {
  console.log(globalVar); // Accessing the global variable inside a function
}

foo(); // Output: "I am a global variable"
console.log(globalVar); // Output: "I am a global variable"
```

###### Global variables are generally discouraged in JavaScript because of their potential to cause issues like: <strong>Name clashes, Difficulty in tracking, Code pollution </strong>
