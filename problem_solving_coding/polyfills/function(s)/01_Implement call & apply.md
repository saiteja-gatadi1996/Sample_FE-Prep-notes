## call & apply

```js
// syntax
function.call(thisArg, arg1, arg2, ...);
```

- **Approach Taken for call**

1. Function.prototype.call is a function that takes context and `rest of the arguments`
2. create a unique temporary function using symbol
3. temporarily assign the function to the context (ex: context[tempFn] = this)
4. store into a variable and Invoke the function with rest of the args
5. delete the context[tempFn]
6. return the variable

```js
Function.prototype.myCall = function (context, ...args) {
  // Both globalThis and window are same
  context = context || globalThis; // Use the global object if no context is provided.

  // Create a unique temporary function name using Symbol
  const tempFn = Symbol('temp');

  // Temporarily assign the function to the context
  context[tempFn] = this;

  // Invoke the function using the context
  const result = context[tempFn](...args);

  // Clean up by deleting the temporary function reference
  delete context[tempFn];

  return result;
};

// Example:
function introduce(name, age) {
  console.log(`Hi, I am ${name}, ${age} years old from ${this.city}.`);
}

const person = {
  city: 'Los Angeles',
};

introduce.myCall(person, 'John', 30);
// Outputs: Hi, I am John, 30 years old from Los Angeles.
```

---

**Approach Taken for apply**

1. Function.prototype.call is a function that takes context and `just arguments`
2. create a unique temporary function using symbol
3. temporarily assign the function to the context (ex: context[tempFn] = this)
4. store into a variable and Invoke the function with rest of the args
5. delete the context[tempFn]
6. return the variable

```js
Function.prototype.myApply = function (context, args) {
  context = context || window; // Use the global object if no context is provided.

  // Create a unique temporary function name to avoid overriding existing properties
  const tempFn = Symbol('temp');

  // Temporarily assign the function to the context
  context[tempFn] = this;

  // Invoke the function using the context
  // We're using the spread operator here to spread the elements of the args array
  const result = context[tempFn](...args);

  // Clean up by deleting the temporary function reference
  delete context[tempFn];

  return result;
};

//Example
function greet(name, age) {
  console.log(
    `Hello, my name is ${name} and I am ${age} years old, and I live in ${this.city}.`
  );
}

const person = {
  city: 'New York',
};

greet.myApply(person, ['Alice', 25]); // Outputs: Hello, my name is Alice and I am 25 years old, and I live in New York.
```
