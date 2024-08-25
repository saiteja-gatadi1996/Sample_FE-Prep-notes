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
# <--- SAMPLE CONTENT ENDS --->
