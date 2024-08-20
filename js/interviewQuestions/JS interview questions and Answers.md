#### 1. What are object literals?

- Are key-value pair.
- Can be of any Datatype inclduing(array, function and nested objects)

---

#### What is JSON?

- Javascript Object notation is a text-based data format and lightweight. It is a subset of JS language.
- JSON follows the JS object syntax.

```js
const employees = [
  { name: 'SaiTeja', email: 'saitejagatadi543@gmai.com' },
  { name: 'RaviTeja', email: 'raviteja543@gmai.com' },
  { name: 'DharmaTeja', email: 'dharmai543@gmai.com' },
];
```

---

#### What are first class functions ?

- Functions that are treated like any other variable.

- Function can pass as an argument to other functions
- Function can be returned by another function
- We can assign as a value to a variable

```js
function getGreet() {
  return 'Hello, how are you?';
}

//functions that are tread like variable
const message = function (getMsg, name) {
  console.log(`${getMsg()}, ${name}`);
};

// function passing as an argument to other function
message(getGreet, 'IMRAN');
```

---

#### 4. What is first order function?

- Function does not accept another function as an argument and does not return a function as it's own value.

```js
const firstOrder = () => console.log('I am a first order function!');
```

---

#### What is a higher order function?

- Function that accepts another function as an argument and returns as well.

Some of them like map, filter, reduce.

```js
const firstOrderFunc = () => {
  console.log('Hello, I am first order function');
};

const higherOrder = (returnFirstOrderFunc) => returnFirstOrderFunc();

higherOrder(firstOrderFunc);
```

---

#### 6. Unary function?

- Function that accepts only one argument.

```js
const unaryFunction = (a) => console.log(a + 10);

unaryFunction(10); //20
```

---

#### 7. Temporal Dead Zone?

- The phase between the starting of the execution of block in which the let or const <strong>variable is declared till that variable is being initialized</strong> is called Temporal Dead Zone

- If we log before the value is assigned, then we would get Reference error

---

#### 8. What is IIFE?

Immediately Invoked Function Expression is a function that runs by itself without invoking separately.

- IIFE is mainly used for data privacy.

```js
(function () {
  var message = 'IIFE';
  console.log(messasge);
})();
console.log(messasge); // message is not defined
```

---

#### 9. Promise ?

- The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

A Promise is in one of these states:

<strong>pending: </strong>initial state, neither fulfilled nor rejected.

<strong>fulfilled: </strong>meaning that the operation was completed successfully.

<strong>rejected: </strong>meaning that the operation failed.

---

#### What is callback?

- Callback is a function passed into another function as an argument which is invoked inside the outer function to complete some kind of routine or action.

```js
function greeting(name) {
  alert(`Hello ${name}`);
}

function processUserInput(callback) {
  const name = prompt('enter name');
  callback(name);
}

processUserInput(greeting);
```

---

#### 10. What is hoisting?

- Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Inevitably, this means that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local.

---

#### 11. undefined vs null


---

#### 12. What is NAN?

---

#### 13. What are global variables?


---

#### 14. How can you access if a key exists or Not in an object?

- Using in operator

```js
'key' in obj;
```

- Using hasOwnProperty operator

```js
obj.hasOwnProperty('key');
```

- Using undefined comparsion

```js
user.name !== undefined;
```

---

#### 15. How can you assign a default value?

- Using Logical OR operator

```js
const a = b || c;
```

---

#### 16. What is web storage?

- The Web Storage API provides mechanisms by which browsers can store key/value pairs which is more intuitive way when compared to using cookies.

- sessionStorage
- localStorage

---

#### 17. Methods in sessionStorage?

- setItem
- getItem
- removeItem
- Clear

---

#### 18. Promise chaining?

- performing a sequence of asynchronous tasks one after another using promise.

---

#### 19. race method in promise?

- race method will return the promise instance that is firsty resolved and reject.

---

#### 20. purpose of JSON stringify ?

- When we send data to a web server, the data has to be in string formats. And JSON.stringify will helps us achieve to this.

---

#### 21. JSON.parse

- When receiving the data from the server, then the data is always in string formats.

---

#### 22. How to get Keys, Values, and Entries in JavaScript Object?

- <strong>Object.keys(obj) </strong>– returns all the keys of object as array.

- <strong>Object.values(obj)</strong> – returns all the values of the object as array.

- <strong>Object.entries(obj)</strong> – returns an array of [key, value]

---

#### 23. various ways of Error handling ?

- Try (the asynchronous try calls)
- Catch (API failures)
- Throw (intentional/custom errors)
- finally (always gets executed)

---

### Writing more than one constructor in a class will get unCaught errors.

---

### We use the super keyword to access the parent constructor into the child class

---

### ENUM feature is available in typescript.

--------------