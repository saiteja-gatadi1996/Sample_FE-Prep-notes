### Module Pattern using Closures

- The module pattern in javascript is a popular design pattern used for creating private variables and functions (while exposing a public API)
- It's a great way to encapsulate functionality and maintain state in a closure.

```js
// The counterModule is an Immediately Invoked Function Expression (IIFE). It runs as soon as it is defined and returns an object.
var counterModule = (function () {
  // Inside the IIFE, count is a private variable, and privateMethod is a private function. They are not accessible outside the IIFE.
  var count = 0;

  function privateMethod() {
    console.log('This is a private method');
  }

  // increment, decrement, and getCount are public functions that are exposed as a part of the returned object.
  // These functions have access to the private count variable and privateMethod function due to closures.
  function increment() {
    count++;
    privateMethod();
  }

  function decrement() {
    if (count > 0) {
      count--;
    }
    privateMethod();
  }

  function getCount() {
    return count;
  }

  return {
    increment,
    decrement,
    getCount,
  };
})();

console.log(counterModule.getCount()); //0
counterModule.increment();
counterModule.increment();
console.log(counterModule.getCount()); //2
counterModule.decrement();
console.log(counterModule.getCount()); //1
```
