## Create a pipe() function, which chains multiple functions together to create a new function.

Suppose we have some simple functions like this

```js
const times = (y) =>  (x) => x * y
const plus = (y) => (x) => x + y
const subtract = (y) =>  (x) => x - y
const divide = (y) => (x) => x / y
```

```js

pipe([
  times(2),
  times(3)
])  
// x * 2 * 3

pipe([
  times(2),
  plus(3),
  times(4)
]) 
// (x * 2 + 3) * 4

pipe([
  times(2),
  subtract(3),
  divide(4)
]) 
// (x * 2 - 3) / 4
```

**Approach Taken**:
1. function pipe accepts functions as a param
2. which in turns returns another function which accept further argument
3. which in turns returns another function (but this time we are applying reduce logic for our param)
4. Call the current function with the result of the previous function


```js
//ACTUAL CODE
// Function to create a pipeline of functions that process an argument sequentially
function pipe(funcs) {
  // Return a function that takes an initial argument
  return function (arg) {
    // Use reduce to process the argument through each function in the funcs array
    return funcs.reduce((result, func) => {
      // Call the current function with the result of the previous function
      return func.call(this, result);
    }, arg);
  };
}

// Example: times(2) returns a function that multiplies its argument by 2
const times = (y) => (x) => x * y;
// Example: times(2)(3) -> 3 * 2 = 6

// Example: plus(3) returns a function that adds 3 to its argument
const plus = (y) => (x) => x + y;
// Example: plus(3)(4) -> 4 + 3 = 7

// Example: subtract(1) returns a function that subtracts 1 from its argument
const subtract = (y) => (x) => x - y;
// Example: subtract(1)(5) -> 5 - 1 = 4

// Example: divide(2) returns a function that divides its argument by 2
const divide = (y) => (x) => x / y;
// Example: divide(2)(8) -> 8 / 2 = 4

// Create a pipeline that multiplies by 2 and then by 3
const pipeline1 = pipe([times(2), times(3)]);

// Create a pipeline that multiplies by 2, adds 3, then multiplies by 4
const pipeline2 = pipe([times(2), plus(3), times(4)]);

// Create a pipeline that multiplies by 2, subtracts 3, then divides by 4
const pipeline3 = pipe([times(2), subtract(3), divide(4)]);

// Testing pipeline1 with initial argument 1
console.log(pipeline1(1)); // (1 * 2) * 3 = 6

// Testing pipeline2 with initial argument 1
console.log(pipeline2(1)); // ((1 * 2) + 3) * 4 = 20

// Testing pipeline3 with initial argument 1
console.log(pipeline3(1)); // ((1 * 2) - 3) / 4 = -0.25
```
