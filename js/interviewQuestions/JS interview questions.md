**1. `Closures:` What is a `closure`? Can you provide an example where closures are useful?**

<details>
<summary>View Answer</summary>
A closure in programming refers to a function that has access to variables from its outer (enclosing) scope, even after the outer function has finished its execution. This provides a way to maintain state between function calls.

<b>Example:</b>

```javascript
function makeCounter() {
  let count = 0;

  return function () {
    return count++;
  };
}

let counter1 = makeCounter();
let counter2 = makeCounter();

console.log(counter1()); // Outputs: 0
console.log(counter1()); // Outputs: 1
console.log(counter2()); // Outputs: 0
console.log(counter1()); // Outputs: 2
```

In this example:

1. `makeCounter` is a function that defines a local variable `count` and returns an inner function.
2. The inner function, when called, increments and returns the current value of `count`.
3. We create two separate counters, `counter1` and `counter2`, each with its own separate `count` state.
4. Despite multiple calls to the counters, they maintain their respective states.

This is a useful feature in many situations, especially when you want to encapsulate some state within a function and expose only certain functionality related to that state. In the above example, we're ensuring that the `count` variable cannot be directly modified from outside, maintaining encapsulation.

</details>

---

**2. `this` keyword: How does the `this` keyword work? How can you change the context of `this`?**

<details>
<summary>View Answer</summary>

The `this` keyword in JavaScript refers to the object it belongs to. However, its value is determined based on how a function is called, Here's a brief overview:

1. **In a Method**: When a function is called as an object method, `this` refers to the object.

   ```javascript
   const obj = {
     value: 'Hello',
     say: function () {
       console.log(this.value);
     },
   };
   obj.say(); // Outputs: "Hello"
   ```

2. **Standalone Function**: When a function is called outside of an object context, `this` refers to the global object (`window` in a browser). But in "strict mode", it's `undefined`.

   ```javascript
   function standalone() {
     console.log(this);
   }
   standalone(); // Outputs: window (or undefined in strict mode)
   ```

3. **Constructor Function**: When a function is called with the `new` keyword, `this` refers to the newly created instance.

   ```javascript
   function Car(make) {
     this.make = make;
   }
   const myCar = new Car('Toyota');
   console.log(myCar.make); // Outputs: "Toyota"
   ```

4. **Event Listener**: In DOM event listeners, `this` refers to the element that received the event.
   ```javascript
   button.addEventListener('click', function () {
     console.log(this); // Outputs: <button> element
   });
   ```

You can change the context of `this` using these methods:

1. **`call()`**: Calls a function with a given `this` value and arguments provided individually.

   ```javascript
   function greet(greeting, punctuation) {
     console.log(greeting + ', ' + this.name + punctuation);
   }
   const person = { name: 'John' };
   greet.call(person, 'Hello', '!'); // Outputs: "Hello, John!"
   ```

2. **`apply()`**: Similar to `call()`, but arguments are provided as an array.

   ```javascript
   greet.apply(person, ['Hello', '!']); // Outputs: "Hello, John!"
   ```

3. **`bind()`**: Creates a new function with a given `this` value and optional arguments.

   ```javascript
   const greetJohn = greet.bind(person, 'Hi');
   greetJohn('!'); // Outputs: "Hi, John!"
   ```

4. **Arrow functions**: Arrow functions don't have their own `this`. They inherit the `this` value from the enclosing scope.
   ```javascript
   const obj = {
     value: 'Hello',
     say: function () {
       setTimeout(() => {
         console.log(this.value); // Outputs: "Hello"
       }, 1000);
     },
   };
   obj.say();
   ```

Understanding the behavior of `this` is crucial in JavaScript, as it's central to how objects and functions interact.

 </details>

---

**3. `Hoisting`: What is hoisting? Does it apply to both variables and functions?**

<details>
<summary>View Answer</summary>
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed. It's important to note that while the declarations are hoisted, the initializations are not.

Hoisting applies to both variables (declared with `var`) and function declarations:

1. **Variable Hoisting**: When variables are declared using `var`, they are hoisted to the top of their scope, but they are not initialized. They are assigned the value `undefined` until the code where they are defined runs.

   ```javascript
   console.log(foo); // Outputs: undefined
   var foo = 5;
   console.log(foo); // Outputs: 5
   ```

   In the above example, the variable declaration `var foo;` is hoisted, but the assignment `foo = 5` stays where it is.

2. **Function Hoisting**: Function declarations are hoisted to the top of their scope, including their definitions.

   ```javascript
   console.log(bar()); // Outputs: "Hello!"
   function bar() {
     return 'Hello!';
   }
   ```

   Here, the entire function `bar` is hoisted to the top, so it's available before its actual declaration in the code.

However, there are nuances:

- Variables declared with `let` and `const` are also hoisted to the top of their block scope, but accessing them before their actual declaration in the code will throw an error. This phenomenon is often referred to as the "Temporal Dead Zone."

  ```javascript
  console.log(baz); // Throws an error
  let baz = 5;
  ```

- Function expressions (including arrow functions) are not hoisted, because they involve variable assignments. If a function is assigned to a variable using `var`, the variable will be hoisted but not the function itself.

  ```javascript
  console.log(qux()); // Throws an error
  var qux = function () {
    return 'Hello!';
  };
  ```

  </details>

---

**4.`Prototypal Inheritance`: How does inheritance work in JavaScript? Explain with an example.**

<details>
<summary>View Answer</summary>

Inheritance in JavaScript is prototype-based, rather than class-based like in many other object-oriented languages. Each object in JavaScript has an internal link to another object called its "prototype." When you try to access a property on an object, JavaScript will first look for that property on the object itself. If it doesn't find it, it'll look on the object's prototype, and then the prototype's prototype, and so on, until it either finds the property or reaches an object with a null prototype.

Here's a step-by-step example:

**1. Create a constructor function:**
Constructor functions are used to instantiate new objects in JavaScript.

```javascript
function Animal(name) {
  this.name = name;
}
```

**2. Add methods to the prototype:**

```javascript
Animal.prototype.speak = function () {
  console.log(`${this.name} makes a noise.`);
};
```

**3. Create a new constructor for a derived class:**

```javascript
function Dog(name) {
  Animal.call(this, name); // Call the parent constructor
}
```

**4. Make the derived class inherit from the base class:**

To achieve this, we'll set the prototype of the `Dog` constructor to an instance of `Animal`.

```javascript
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // Fix the constructor property
```

**5. Add or override methods for the derived class:**

```javascript
Dog.prototype.speak = function () {
  console.log(`${this.name} barks.`);
};
```

**6. Instantiate and use:**

```javascript
let dog = new Dog('Rover');
dog.speak(); // Outputs: "Rover barks."
```

In this example, `Dog` inherits from `Animal`. When the `speak` method is called on a `Dog` instance, JavaScript will first look for the method on `Dog`. If not found (or before we added the override), it would look on `Dog's` prototype, which is an instance of `Animal`, and use the `speak` method from there.

With the introduction of ES6 (ECMAScript 2015), JavaScript now has a `class` syntax that makes it easier to write and understand inheritance. However, it's crucial to recognize that this `class` syntax is syntactic sugar over the existing prototype-based inheritance system; it doesn't introduce a new inheritance model to the language.

</details>

---

**5. `Event Loop`: Describe the Event Loop in JavaScript.**

<details>
<summary>View Answer</summary>

In JavaScript, the Event Loop is a mechanism that continuously checks if the call stack is empty and, if so, takes the next task from the task queue and pushes it to the call stack to be executed.

This allows JavaScript, which is single-threaded, to handle tasks like callbacks and promises asynchronously without blocking the main thread.

Here's a simple breakdown:

1. **Call Stack**: This is where your JavaScript code is executed, one line at a time. If a function is called, it's added to the call stack, and once it's executed, it's removed.

2. **Task Queue (or Callback Queue)**: When asynchronous operations like `setTimeout`, AJAX requests, or user interactions finish, their resulting callbacks are added to this queue.

3. **Web APIs**: Provided by the browser, these are where asynchronous operations like timers or AJAX requests run. Once they're done, they place their callbacks in the task queue.

The Event Loop's job is to look at the call stack and the task queue. If the call stack is empty and there's a task waiting in the queue, the Event Loop pushes the first task from the queue onto the call stack to be executed.

This process ensures that the main thread doesn't get blocked by long-running operations, allowing for a non-blocking, asynchronous behavior in JavaScript.

</details>

---

**6. `Promises`: What are promises? How do they differ from callbacks? Write a function that uses promises.**

<details>
<summary>View Answer</summary>
Promises are more convenient way to handle asynchronous operations compared to traditional callback methods. They represent a value which might be available now, or in the future, or never.

**Promises vs. Callbacks**:

1. **Readability**: Callbacks, especially when nested (often termed "callback hell" or "pyramid of doom"), can lead to less readable code. Promises provide a cleaner syntax with methods like `.then()` and `.catch()` for chaining.
2. **Error Handling**: With callbacks, each callback generally needs its own error handling. Promises allow centralized error handling using `.catch()`.
3. **Flexibility**: Promises have built-in methods, like `Promise.all()`, to work with multiple asynchronous operations conveniently.

_Here's a basic comparison:_

**Callback**:

```javascript
function fetchData(callback) {
  // Simulating async operation using setTimeout
  setTimeout(function () {
    callback('Data fetched!');
  }, 1000);
}

fetchData(function (data) {
  console.log(data);
});
```

**Promise**:

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulating async operation using setTimeout
    setTimeout(function () {
      resolve('Data fetched with promises!');
    }, 1000);
  });
}

fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

The Promise version provides a clear way to handle both success (using `.then()`) and failure (using `.catch()`) scenarios. As more asynchronous operations are chained, the advantages of using promises over callbacks become more pronounced.

</details>

---

**7.`Async/Await`: Explain the purpose of `async`/`await`. Refactor a promise-based function to use `async`/`await`.**

<details>
<summary>View Answer</summary>
The `async/await` syntax is a more recent addition to JavaScript that further simplifies asynchronous code, making it look and behave a bit more like synchronous code. Here's the purpose of `async/await`:

1. **Readability**: It offers a cleaner, more intuitive way to work with Promises, reducing the need for `.then()` and `.catch()` chains.

2. **Error Handling**: With `async/await`, you can use traditional `try/catch` blocks to handle asynchronous errors.

3. **Synchronous-Like Flow**: The code can be written in a way that appears linear, making it easier to follow the logic.

Let's refactor our previous Promise example to use `async/await`:

**Promise-based function**:

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      resolve('Data fetched with promises!');
    }, 1000);
  });
}

fetchData()
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

**Refactored with `async/await`**:

```javascript
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      resolve('Data fetched with async/await!');
    }, 1000);
  });
}

async function displayData() {
  try {
    let data = await fetchData();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

displayData();
```

_In the refactored example:_

- The function `displayData` is declared with the `async` keyword, indicating it's an asynchronous function.
- Inside this function, the `await` keyword is used to pause the execution until `fetchData()` resolves, and then assigns its value to the `data` variable.
- Errors can be caught using a conventional `try/catch` block.

This approach offers a more structured and readable way to handle asynchronous operations.

</details>

---

**8. `Module Patterns`: What are different module patterns in JavaScript? When would you use them?**

<details>
<summary>View Answer</summary>
- Module Patterns are design patterns that allow for the **encapsulation** of code, the creation of private and public methods and variables and the organization of code into modular, maintainable structures.

**1. Module Pattern**: This pattern uses an IIFE to create a scope for variables and functions, which prevents them from polluting the global namespace.

```js
var myModule = (function () {
  var privateVar = "I'm private";
  function privateMethod() {
    console.log(privateVar);
  }
  return {
    publicMethod: function () {
      privateMethod();
    },
  };
})();
myModule.publicMethod(); // Outputs: "I'm private"
```

**2. Revealing Module Pattern**: A variation where you reveal only the properties and methods you want to make public by returning an object literal.

```js
var revealingModule = (function () {
  var privateVar = "I'm private";
  function privateMethod() {
    console.log(privateVar);
  }
  function publicMethod() {
    privateMethod();
  }
  return {
    publicMethod: publicMethod,
  };
})();
revealingModule.publicMethod(); // Outputs: "I'm private"
```

**3. Singleton Pattern**: Ensures that a class has only one instance and provides a global point to access it.

```js
var singleton = (function () {
  var instance;
  function init() {
    return {
      publicMethod: function () {
        console.log("I'm a public method");
      },
    };
  }
  return {
    getInstance: function () {
      if (!instance) {
        instance = init();
      }
      return instance;
    },
  };
})();
var singleA = singleton.getInstance();
var singleB = singleton.getInstance();
console.log(singleA === singleB); // Outputs: true
```

**4. ES6 Modules (ES2015)**: The native module system in ES6. It allows for the export and import of modules.

```js
// file: moduleA.js
export function myFunction() {
  console.log('Hello from module A');
}

// file: main.js
import { myFunction } from './moduleA';
myFunction(); // Outputs: "Hello from module A"
```

</details>

---

**9. `Memory Leaks`: How can memory leaks occur in JavaScript? Can you provide an example?**

<details>
<summary>View Answer</summary>

- Memory leaks in js occur when objects are no longer needed but are still being referenced, preventing them from being garbage collected.

1. **Global Variables:**: If they reference to large data structures or other objects.

2. **Forgotten Timers or callbacks**: If you set up an interval or timeout and forget to clear it, or any event listeners and forget to remove them can cause memory leaks.

3. **Out of DOM references:** Keeping references to DOM elements that have been removed can cause those elements to remain in memory.

4. **Closures:** if they keep the references to objects longer than necessary

5. **Circular References:** Issue in older browsers where the browser couldn't break the cycle where two JS objects reference each other.

</details>

---

10. **`Error Handling`: How would you handle exceptions in JavaScript? Show with an example.**

<details>
<summary>View Answer</summary>

- Done with the try catch finally

```js
const axios = require('axios');

async function fetchData(url) {
  let response;
  try {
    response = await axios.get(url);
    // Handle the response (e.g., return the data or do something with it)
    return response.data;
  } catch (error) {
    console.error('An error occurred while fetching data:', error.message);
    // Depending on your use case, you might want to throw the error,
    // return a default value, or handle it in some other way.
    return null;
  } finally {
    console.log('API call finished.');
  }
}

// Usage:
(async () => {
  const data = await fetchData('https://api.example.com/data');
  console.log(data);
})();
```

</details>

---

11. **`Event Delegation`: What is event delegation and why is it useful? Can you provide an example?**

<details>
<summary>View Answer</summary>
- Is a technique where you delegate the handling of events to a common parent element rather than assigning event handlers to individual elements.

- based on the event bubbling principle, where an event propagates up from the target element through its ancestors in the DOM hierarchy.

##### Why it is useful?

**1. Efficiency**: Instead of attaching multiple event listeners you can attach a single event listener. Reduces overhead of managing multiple event listeners.

**2. Dynamic elements**: If elements are added or removed dynamically you don't have to attach or remove event listeners for each element. The parent event listenere will hanlde events for all current and future child elements.

**3. Less memory consumption**: Less event listeners means less memory consumption which can lead to performance improvements.

```js
// Example:

<ul id='itemList'>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

```js
// With event delegation:

const itemList = document.getElementById('itemlist');
itemList.addEventListener('click', function (event) {
  if (event.target.tagName === 'LI') {
    console.log(event.target.textContent);
  }
});
```

</details>

---

12. **`DOM Manipulation`**: Write a function to add an element to the DOM, update it, and eventually remove it.

<details>
<summary>View Answer</summary>

```js
function manipulateDOM() {
  // Parent element to which our new element will be appended
  const parentElement = document.body;

  // 1. Add an Element to the DOM
  const newElement = document.createElement('div');
  newElement.id = 'myElement';
  newElement.textContent = 'This is a new element!';
  parentElement.appendChild(newElement);

  // 2. Update the Element
  setTimeout(() => {
    const elementToUpdate = document.getElementById('myElement');
    elementToUpdate.textContent = 'This element has been updated!';
    elementToUpdate.style.color = 'blue';
  }, 2000); // Update after 2 seconds

  // 3. Remove the Element from the DOM
  setTimeout(() => {
    const elementToRemove = document.getElementById('myElement');
    parentElement.removeChild(elementToRemove);
  }, 4000); // Remove after 4 seconds
}

// Call the function
manipulateDOM();
```

</details>

---

13. **`Web APIs`**: Fetch data from a provided API and display it on the page.

<details>
<summary>View Answer</summary>

```js

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fetch API Data</title>
</head>
<body>

<div id="dataContainer"></div>

<script>
    const apiUrl = 'https://jsonplaceholder.typicode.com/posts/1';

    async function fetchDataAndDisplay() {
        try {
            const response = await fetch(apiUrl);
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            const data = await response.json();
            const dataContainer = document.getElementById('dataContainer');
            dataContainer.innerHTML = `
                <h2>${data.title}</h2>
                <p>${data.body}</p>
            `;
        } catch (error) {
            console.error('There was a problem with the fetch operation:', error.message);
        }
    }
    fetchDataAndDisplay();
</script>
</body>
</html>
```

</details>

---

14. **`Higher-Order Functions`**: Provide examples of higher-order functions you've used and describe their use cases.
<details>
<summary>View Answer</summary>

Higher-order functions are functions **that take one or more functions as arguments, return a function, or both**. They are a fundamental part of functional programming in JavaScript

**1. map**: Iterates over each item in an array and applies a function to each element. It returns a new array with the results

```js
const numbers = [1, 2, 3, 4];
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // [2, 4, 6, 8]
```

**2. filter**: Iterates over each item in an array and returns a new array with only the items for which the provided function returns true

```js
const numbers = [1, 2, 3, 4];
const evens = numbers.filter((num) => num % 2 === 0);
console.log(evens); // [2, 4]
```

**3. reduce**: Iterates over each item in an array and reduces the array to a single value using a function that you provide.

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 10
```

</details>

---

15. **`Functional Programming`**: How would you implement functional programming paradigms in JavaScript? Show with an example.

<details>
<summary>View Answer</summary>
- Avoids changing state and mutable data.

Here are some of the principles of functional programming.

**1. First-Class and Higher order functions:** Functions in javascript are first-class, meaning they can be passed as arguments to other functions, returned as value from other functions and assigned to variables.

**2. Pure Functions:** A function is pure if it's solely determined by its input and it doesn't have any observable side effects.

**3. Immutability**: In FP, once data is created, it cannot be changed. If you want to make a change, you create a new data strcuture.

- This is useful for concurrency and maintaining data integrity.

**4. Function Composition:** Process of combining two or more functions to produce a new function

**5. Avoid Side Effects:** This includes modifying a global object or modifying one of its arguments.

</details>

---

16. **`ES6 and Beyond`**: What are your favorite features from ES6 and later versions? How do they improve your code?

<details>
<summary>View Answer</summary>

**1. Arrow Functions:**

- Makes function syntax shorter and more concise.
- Lexcially binds the value of `this` which is useful in scenarios like event handlers and callbacks.

```js
const numbers = [1, 2, 3];
const doubled = numbers.map((num) => num * 2);
```

**2. Template Literals:**

- Allows for string interpolation and multi-line strings without hacks.

```js
const name = 'Alice';
const greeting = `Hello ${name}`;
```

**3. Destructuring**

- Provides a way to extract values from arrays or properties from objects into distinct variables.

```js
const person = { firstName: 'John', lastName: 'Doe' };
const { firstName, lastName } = person;
```

**4. Spread/Rest operator**:

- Userful for spreading elements of any array or object properties.
- Rest is for collecting all the rest of the element in an array.

```js
// Spread operator example
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
```

**5. Promises and async/await:**

- Provides a cleaner way to handle asynchronous operations compared to callbacks

```js
async function fetchData() {
  const response = await fetch(URL);
  const data = response.json();
  return data;
}
```

**6. Modules (import/export)**:

- Enables modular programming by allowing you to split your code into reusable pieces

```js
// math.js
export const add = (a, b) => a + b;

// app.js
import { add } from './math';
```

</details>

---

17. **`Throttling`**: Implement a throttle function.

<details>
<summary>View Answer</summary>

- Is a technique to limit the frequency at which a fucntion can be called.
- It's useful in scenarios like scroll events, window resizing, or any other events that fire at a higher rate

```js
function throttle(func, limit) {
  let inThrottle

  return (...args) {
      // Here, args is an array of all arguments passed to the function
      //  if the function is called with func(1, 2, 3, 4), then inside the function, args would be [1, 2, 3, 4].
    if (!inThrottle) {
      func(...args)
      // If args is [1, 2, 3, 4], the above is equivalent to calling func(1, 2, 3, 4).
      inThrottle = true
      setTimeout(() => (inThrottle = false), limit)
    }
  }
}
```

```js
// How to use:

// Example usage:
window.addEventListener('scroll', throttle(scrollHandlerFunc, 1000)); // This function will be called at most once every 1000ms (1 second)
```

</details>

---

18. **`Shadow DOM vs. Virtual DOM`**: What are the differences and use cases?

<details>
<summary>View Answer</summary>

_Shadow Dom_:

- offers encapsulation for DOM and CSS. It allows for the creation of a separate DOM tree with its styles and scripts which is attached to an element but doesn't interfere with the main Document's DOM.

_Uses_: Shadow DOM is used when you want to create reusable and isolated components.

- It's beneficial for widget development, plugins or any scenario where you don't want your component's internals to clash with the surrounding environment.
- Since the Shadow DOM is isolated from the main document, **changes made inside a shadow tree do not directly affect the main document's DOM**.

```js
const element = document.getElementById('myElement');
const shadowRoot = element.attachShadow({ mode: 'open' });
shadowRoot.innerHTML = `<style>p { color: red; }</style><p>Hello, Shadow DOM!</p>`;
```

_Virtual Dom_:

- Is Virtual representation of a UI kept in memory and synced with the `real DOM` through a process called reconciliation. Technique popular in React

**Differences:** Virtual DOM provides a way to update the view in a more optimized and efficient manner. Instead of making direct changes to the real DOM (which can be slow) changes are made to the virtual DOM, which then calculates the diff between the current and the new state and updates the real DOM in a minimal way.

**Not Native**: Virtual DOM is not a web standard. It's a technique used by specific libraries and frameworks

**Use Cases**: Virtual DOM is beneficial in scenarios where frequent updates to the UI can lead to the performance bottlenecks. Virtual DOM ensures a smoother User Experience.

**Summary**:

_Shadow DOM_: is about encapsulation, isolating components and their styles/scripts from the main document to prevent conflicts and leaks

_V Dom_: is about performance: optimizing the way the UI updates by minimizing direct interactions with the real DOM.

- If you're building a reusable widget or component that you want to remain isolated from the surrounding env, consider using Shadow DOM.

- If you're developing a dynamic web app where the UI changes frequently and you want to optimized those updates, consider using a library or framework that employs VDom like React.

</details>

---

1.  **`Spread/Rest Operator`**: Explain with examples.
<details>
<summary>View Answer</summary>

**1. Spread operator**:

- Spreads the elements of an iterable (like an array or an object) into individual elements

```js
// Arrays

const arr = [1, 2, 3];

const arr2 = [...arr, 4, 5]; // [1, 2, 3, 4, 5]
```

```js
// Objects
const obj1 = { a: 1, b: 3 };

const obj2 = { ...obj1, c: 4 }; // { a: 1, b: 2, c: 3 }
```

```js
// Function arguments

function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers)); // 6
```

**2. Rest operator**:

- Collects multiple individual elements into an array

**Functions**

- Collects all remaining function arguments into an array

```js
function collectIntoArray(...args) {
  return args;
}

console.log(collectIntoArray(1, 2, 3, 4)); // [1, 2, 3, 4]
```

</details>

---

20. **`Destructuring`**: How can you use destructuring in JavaScript? Provide examples with both arrays and objects.

<details>
<summary>View Answer</summary>

- Destructuring provides a way to extract multiple items from arrays, objects, and even nested structures into thier own variables.

**_Array Destructuring_**:

```js
const colors = ['red', 'green', 'blue'];

const [firstColor, secondColor, thirdColor] = colors;

console.log(firstColor); // red
console.log(secondColor); // green
console.log(thirdColor); // blue
```

```js
// if you skip items

const [, , lastColor] = colors;

console.log(lastColor); // blue
```

```js
//using rest parameter
const [primaryColor, ...otherColors] = colors;

console.log(primaryColor); // red
console.log(otherColors); // ['green', 'blue']
```

**_Object Destructuring_**:

- you can unpack properties from objects into variables

```js
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
};

const { firstName, lastName } = person;

console.log(firstName); // John
console.log(lastName); // Doe
```

```js
const { firstName: fName, lastName: lName } = person;

console.log(fName); // John
console.log(lName); // Doe
```

```js
const student = {
  name: 'Alice',
  scores: {
    math: 90,
    english: 85,
  },
};

const {
  scores: { math, english },
} = student;

console.log(math); // 90
console.log(english); // 85
```

</details>

---

21. **`Template Literals`**: How are they different from regular strings? Show some advanced usage.

<details>
<summary>View Answer</summary>

Template literals, introduced in ES6, offer a more powerful and flexible way to work with strings in JavaScript. They differ from regular strings in several key ways:

1. Syntax:
   Regular strings use single (' ') or double (" ") quotes.
   Template literals use backticks (````).
2. String Interpolation:
   With regular strings, you concatenate variables or expressions using the + operator.
   Template literals allow you to embed expressions directly using ${expression}.
3. Multi-line Strings:
   Regular strings don't handle multi-line text well. You'd typically use the \n escape character or concatenate multiple strings.
   Template literals support multi-line strings natively.

   ```js
   const multiLine = `
   This is a line.
   And this is another line.
   `;
   console.log(multiLine);
   ```

</details>

---

22. **`Custom Events`**: How would you create and dispatch a custom event?

<details>
<summary>View Answer</summary>

- In Javascript, custom events can be created and dispatched using the `CustomEvent` constructor.
- This allows you to create your own events that can carry custom data and be dispatched on any DOM element.

**1. Creating a Custom Event**

```js
const event = new CustomEvent('customStart', {
  detail: {
    message: 'Custom Event triggered!',
    time: new Date(),
  },
  bubbles: true,
  cancelable: true,
});
```

**2. Dispatching the Custom Event**

```js
const button = document.querySelector('button');
button.dispatchEvent(event); // you have to provide the varialbe that is used for creation of custom Event (ex: event)
```

**3. Listening the Custom Event**

```js
button.addEventListener('customStart', (e) => {
  console.log(e.detail.message); // Custom Event triggered!
  console.log(e.detail.time); // time when user clicked on button
});
```

</details>

---

23. **`Service Workers`**: How would you set up a basic service worker for caching?
<details>
<summary>View Answer</summary>

- Service workers are a powerful feature in modern web browsers that allow you **to intercept and cache network requests.** enabling features like offline access and performance improvments.

**1. Registering the Service Worker:**

```js
if ('serviceWorker' in navigator) {
  navigator.serviceWorker
    .register('/service-worker.js')
    .then((registration) => {
      console.log('Service Worker registered with scope'.registration.scope);
    })
    .catch((error) => {
      console.log('Service worker registration failed: ', error);
    });
}
```

**2. writing the service worker:**

```js
// service-worker.js

const CACHE_NAME = 'my-site-cache-v1';

const urlsToCache = [
  '/',
  '/styles/main.css',
  '/scripts/main.js',
  '/images/my-image.jpg',
];
```

**3. Install the service worker and cache the assets:**

```js
// install

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      console.log('Opened cache');
      return cache.addAll(urlsToCache);
    })
  );
});
```

**4. Intercept fetch requests and serve from cache if available:**

```js
// fetch

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      // Cache hit - return the response from the cached version
      if (response) {
        return response;
      }

      // If not in cache, fetch from the network
      return fetch(event.request).then((response) => {
        // Check if we received a valid response
        if (!response || response.status !== 200 || response.type !== 'basic') {
          return response;
        }

        // Clone the response so that it's stream remains readable in both cache and browser
        const responseToCache = response.clone();

        caches.open(CACHE_NAME).then((cache) => {
          cache.put(event.request, responseToCache);
        });

        return response;
      });
    })
  );
});
```

**5. update the service worker and manage old caches**

```js
// activate

self.addEventListener('activate', (event) => {
  const cacheWhitelist = [CACHE_NAME];

  event.waitUntil(
    caches.keys().then((cacheNames) => {
      return Promise.all(
        cacheNames.map((cacheName) => {
          if (cacheWhitelist.indexOf(cacheName) === -1) {
            // If this cache name isn't present in the array, delete it
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
});
```

</details>

---

24. **Websockets**: How would you establish a basic WebSocket connection and handle messages from a server?

---

25. **`Local Storage vs. Session Storage`**: Differences and use cases.

<details>
<summary>View Answer</summary>

**Local storage:**

- Data stored here persists even after the browser is closed. It has no expiration time.
- Typically allows for about 5-10 MB of data storage (varies by browser).

**_Use cases:_**

- Storing user preferences that persists across sessions
- Saving the state of a user's activity over a long period of time.
- Caching data for offline use.

**Session storage:**

- is cleared when the page session ends (i.e when the tab is closed)
- Typically allows for about 5-10 MB of data storage (varies by browser).
- Data in one tab's sessionStorage cannot be accessed by another tab.

**_Use cases:_**

- Storing temporary data like form inputs so that they can be restored if the page is accidentally refreshed.
- Keeping track of a user's activity within a single session, like items added to a shopping cart.

**Cookies:**

- Defined by the `expires` attribute. If not set, the cookie will last for the session (similar to session storage). If set, it will persist across sessions (similar to localStorage)

- Capactity is only 4KB per cookie
- Can be set to be accessible across subdomains.
- Cookies are sent with every HTTP request to the domain, which can impact performance if the cookie size is large.

**_Use cases:_**

- Storing session identifiers for user auth.
- Tracking user behaviour(ex: analytics or advertise)
- Storing small bits of data that need to be accessed server-side

**Summary**:
**_localStorage_**: Use for data that should persist across multiple sessions and doesn't need to be sent to the server with every request.
**_sessionStorage_**: Use for data that should last only for a single page session.
**_Cookies_**: Use for data that needs to be sent to the server with every request, or for smaller pieces of data with specific expiration requirements.

</details>

---

26. **`Web Components`**: Describe how to create a basic web component.

<details>
<summary>View Answer</summary>

</details>

---

27. **`Transpilers`**: How do tools like Babel help in writing modern JavaScript?

<details>
<summary>View Answer</summary>
-  take source code written in one language and produce the equivalent code in another language. Babel is one of the most popular JavaScript transpilers, and it plays a crucial role in modern web development

- Not all browsers, especially older ones, support the latest JavaScript features. Babel allows developers to write modern JavaScript while ensuring that the code runs in older browsers.

- Babel can transform JSX syntax (used by React and other libraries) into regular JavaScript function calls.

- Babel easily integrates with popular build tools like Webpack, Rollup, and Parcel. This seamless integration means that as developers save their modern JavaScript files, they are automatically transpiled to widely-supported JavaScript in the build process.

</details>

---

28. **`Immutable Data`**: Why is immutability important and how can you achieve it in JavaScript?

<details>
<summary>View Answer</summary>
- Immutability refers to the concept that once a data structure is created, it cannot be changed.

- If you want to make a change, you create a new data structure. This is in contrast to mutable data, which can be directly modified after its creation.

Immutability is a fundamental concept in functional programming and has several benefits when applied to application development.

### Why is Immutability Important?

1. **Predictability**: Immutable data structures reduce the chances of unintended side-effects. When data cannot change unexpectedly, it's easier to reason about the application's behavior.

2. **Simpler Change Detection**: In frameworks like React, immutable data can simplify change detection. If a reference to a data structure changes, the data has changed. This can lead to performance improvements.

3. **Concurrency**: Immutable data structures can be more safely used in concurrent scenarios (like multi-threaded environments) because there's no risk of one thread mutating data that another thread is using.

4. **History/Undo-Redo**: Keeping a history of immutable states allows for features like undo and redo, as seen in some state management libraries like Redux.

5. **Easier Debugging**: When data is immutable, it's easier to track when and where it was changed, making debugging more straightforward.

### How to Achieve Immutability in JavaScript:

JavaScript **_doesn't enforce immutability by default_**, but you can adopt practices and use libraries to ensure data remains immutable.

1. **Using Const**: The `const` keyword ensures that a variable cannot be reassigned. However, this doesn't make the value itself immutable, especially if it's an object or array.

   ```javascript
   const arr = [1, 2, 3];
   arr.push(4); // This is allowed, so the array itself isn't immutable.
   ```

2. **Avoid Mutating Methods**: For arrays, avoid methods like `push`, `pop`, `shift`, `splice`, and instead use methods like `map`, `filter`, `concat`, and the spread operator.

   ```javascript
   const arr = [1, 2, 3];
   const newArr = [...arr, 4]; // Instead of push
   ```

   For objects, you can use the spread operator or `Object.assign` to create new objects without mutating the original:

   ```javascript
   const obj = { a: 1, b: 2 };
   const newObj = { ...obj, c: 3 }; // Instead of direct assignment
   ```

3. **Object.freeze**: This method can make an object shallowly immutable, meaning you can't add, modify, or delete properties. However, nested objects remain mutable.

   ```javascript
   const obj = Object.freeze({ a: 1, b: 2 });
   obj.a = 3; // This will not work
   ```

4. **Use Libraries**: Libraries like [Immutable.js](https://immutable-js.com/) or [immer](https://immerjs.github.io/immer/) provide immutable data structures and helper functions to work with them. These libraries offer deep immutability and various utilities to manipulate data without mutations.

5. **Deep Cloning**: For deep immutability, you might need to deep clone objects. This can be achieved using libraries like [lodash's `cloneDeep`](https://lodash.com/docs/#cloneDeep) method, but be cautious about performance implications for large objects.

In conclusion, while JavaScript doesn't enforce immutability by default, understanding its importance and leveraging practices and tools to ensure data remains unchanged can lead to more robust and maintainable applications.

</details>

---

29. **`Reactive Programming`**: How would you set up a basic reactive data system without using frameworks?

<details>
<summary>View Answer</summary>

</details>

---

30. **`Dynamic Import`**: How can you use dynamic imports in JavaScript and why are they useful?

<details>
<summary>View Answer</summary>

</details>

---

31. **`Tree-shaking`**: What is it and why is it important?

<details>
<summary>View Answer</summary>

</details>

---

32. **`Lazy Loading`**: Implement lazy loading for images on a webpage.

<details>
<summary>View Answer</summary>

</details>

---

33. **How do I use JavaScript to `modify the URL without reloading the page`?**

<details>
<summary>View Answer</summary>

- We can achieve this using History API (pushState or replaceState)

#### History API:

- You can use either history.pushState() or history.replaceState() to modify the URL in the browser
- The arguments for both methods are the same, allowing you to pass a customized serializable state object as the first argument.
</details>

```js
// Current URL: https://my-website.com/page_a

const nextURL = 'https://my-website.com/page_b';
const nextTitle = 'My new page title';
const nextState = { additionalInformation: 'Updated the URL with JS' };

// This will create a new entry in the browser's history, without reloading
window.history.pushState(nextState, nextTitle, nextURL);

// This will replace the current entry in the browser's history without reloading
window.history.replaceState(nextState, nextTitle, nextURL);
```
