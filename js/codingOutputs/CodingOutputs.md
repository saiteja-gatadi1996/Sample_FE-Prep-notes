## 1.

```js
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
```

<details>
<summary>Solution</summary>

```js
console.log(0.1 + 0.2); //0.3
console.log(0.1 + 0.2 == 0.3); //false, because adding 0.1 + 0.2 prints 0.30000000000000004
```

- To mitigate such issues, especially in comparisons, **it's often recommended to check if the numbers are "close enough" to each other rather than exactly equal**.
- This can be done by defining a small threshold (epsilon) and checking if the absolute difference between the numbers is smaller than this threshold.

```js
const a = 0.1 + 0.2;
const b = 0.3;
const epsilon = 0.000001; // Define a small threshold
console.log(Math.abs(a - b) < epsilon); // Use this to check for "equality"
```

</details>

---

## 2.

### i)

```js
(function () {
  var a = (b = 3);
})();

console.log('a defined? ' + (typeof a !== 'undefined'));
console.log('b defined? ' + (typeof b !== 'undefined'));
```

<details>
<summary>Solution</summary>

```js
console.log('a defined? ' + (typeof a !== 'undefined')); //false
console.log('b defined? ' + (typeof b !== 'undefined')); //true
```

</details>

### ii)

```js
'use strict';
(function () {
  var a = (b = 3);
})();

console.log('a defined? ' + (typeof a !== 'undefined'));
console.log('b defined? ' + (typeof b !== 'undefined'));
```

<details>
<summary>Solution</summary>

```js
// because use strict doesn't allow you to declare global variables, here b is a global variable
ReferenceError: b is not defined
```

</details>

---


## 33.

```js
var a = 2;
a++;
console.log(a);
const d = [1, 2, 3];
d.push(5);
console.log(d);
const b = 2;
b++;
console.log(b);
const c = [2];
c[0]++;
console.log(c);
```

<details>
<summary>Solution</summary>

```js
var a = 2;
a++;
console.log(a); // 3
const d = [1, 2, 3];
d.push(5);
console.log(d); // [1,2,3,5]
const b = 2;
b++;
console.log(b); // TypeError: Assignment to constant variable
const c = [2]; //nothing prints from this line
c[0]++;
console.log(c);
```

</details>

---

## 34

```js
var a = b();
console.log(a);
var c = d();
function b() {
  return c;
}
console.log(a);
var d = function () {
  return b();
};
```

<details>
<summary>Solution</summary>

```js
undefined
TypeError: d is not a function
```

</details>

---

## 35.

```js
var myObject = {
  foo: 'bar',
  func: function () {
    var self = this;
    console.log('outer func: this.foo = ' + this.foo);
    console.log('outer func: self.foo = ' + self.foo);
    (function () {
      console.log('inner func: this.foo = ' + this.foo);
      console.log('inner func: self.foo = ' + self.foo);
    })();
  },
};
myObject.func();
```

<details>
<summary>Solution</summary>

```js
outer func: this.foo = bar
outer func: self.foo = bar
inner func: this.foo = undefined
inner func: self.foo = bar
```

</details>

---

## 36.

```js
var output = (function (x) {
  delete x;

  return x;
})(0);

console.log(output);
```

<details>
<summary>Solution</summary>

```js
0;
```

</details>

---

## 37 How to empty an array

```js
let a = [1, 6, 8, 9];
```

<details>
<summary>Solution</summary>

```js
//1
a.length = 0;

//2
a = [];

//3
a.splice(0, a.length);

//4
while (a.length) {
  a.shift();
}

//5
Array.from(a.fill());
```

</details>

---

## 38 only print defined values

```js
let b = [1, 2, , 4, 5];

// output should be [1, 2, 4, 5]
```

<details>
<summary>Solution</summary>

```js
//1
// This will filter out any undefined slots in the array
let cleanedArray = b.filter((item) => item !== undefined);

console.log(cleanedArray); // Output will be [1, 2, 4, 5]

//2 -> Shortcut
let cleanedArray = b.filter(Boolean);

console.log(cleanedArray); // Output will be [1, 2, 4, 5]
```

</details>

---

## 39 Nested Arrays

```js
let a = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];

// output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

<details>
<summary>Solution</summary>

```js
let a = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];

// Flattens the array completely
let flatArray = a.flat(Infinity);

console.log(flatArray); // Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

</details>

---

## 40

```js
const arr = [1, 2, undefined, NaN, null, false, true, '', 'abc', 3];
console.log(arr.filter(Boolean)); //[1, 2, true, 'abc', 3]

const arr1 = [1, 2, undefined, NaN, null, false, true, '', 'abc', 3];
console.log(arr1.filter(!Boolean));
```

<details>
<summary>Solution</summary>

```js
const arr = [1, 2, undefined, NaN, null, false, true, '', 'abc', 3];
console.log(arr.filter(Boolean));

//This operation evaluates to false because !Boolean (the negation of a truthy value, which the Boolean function is considered to be) is false.
// Therefore, when you try to pass !Boolean to .filter(), you're essentially trying to pass a boolean value (false) instead of a function, which is why you get the error "boolean false is not a function."
const arr1 = [1, 2, undefined, NaN, null, false, true, '', 'abc', 3];
console.log(arr1.filter(!Boolean));
```

</details>

---

## 41

```js
var a = 3;
var b = {
  a: 9,
  b: ++a,
};
console.log(a + b.a + ++b.b);
```

<details>
<summary>Solution</summary>

```js
18;
```

1. var a = 3; sets a to 3.

2. In the object b, a is set to 9. This does not affect the variable a defined outside; they are two separate entities.

3. Still inside object b, b: ++a is evaluated. The prefix increment ++a increases a by 1 before assigning it to b.b, making a now 4 and b.b also 4.

4. At this point:

The standalone variable a is 4.
The object b looks like this: { a: 9, b: 4 }.
console.log(a + b.a + ++b.b); computes the sum:

- a is 4.
- `b.a` is 9.
- `++b.b` is a prefix increment of `b.b`, so `b.b` is increased to 5 before it's added to the sum.
  Therefore, the calculation is 4 + 9 + 5, which equals 18.

</details>

---

## 42. What will be the output of the code below?

```js
function foo() {
  return "I'm the outer function";
}

function test() {
  console.log(bar);
  return foo();
  var bar = "I'm a variable";
  function foo() {
    return "I'm the inner function";
  }
}
console.log(test());
```

<details>
  <summary>View Answer</summary>
 undefined 
 I’m the inner function
</details>

---

## 43. What will be the output of the code below?

```js
const nums = [1,2,3,4,5,6,7];
nums.forEach((n) => {
    if(n%2 === 0)
      break;
    console.log(n);
});
```

<details>
  <summary>View Answer</summary>
  
##### Syntax Error ( because you cannot use break within a forEach)

```js
//correct solution would be by using loops

const nums = [1, 2, 3, 4, 5, 6, 7];

for (let n of nums) {
  if (n % 2 === 0) break;
  console.log(n);
}
```

</details>

---

## 44. What will be the output of the code below?

```js
async function foo() {
  console.log('A');
  await Promise.resolve();
  console.log('B');
  await new Promise((resolve) => setTimeout(resolve, 0));
  console.log('C');
}

console.log('D');
foo();
console.log('E');
```

<details>
  <summary>View Answer</summary>
Output: D, A, E, B, C
</details>

---

### 49. ;

```js
console.log(1 < 2 < 3);
```

<details>
<summary>Solution</summary>

```js
true;
```

</details>

---

### 50.

```js
console.log(3 < 2 < 1);
```

<details>
<summary>Solution</summary>

```js
true;
```

</details>

---

### 51.

```js
console.log(typeof NaN);
```

<details>
<summary>Solution</summary>

```js
number;
```

</details>

---

### 52.

```js
console.log(typeof typeof 1);
```

<details>
<summary>Solution</summary>

```js
string;
```

</details>

---

### 53.

```js
console.log(1 + '1' - 1);
```

<details>
<summary>Solution</summary>

```js
10;
```

</details>

---

### 54.

```js
console.log([] + [] + 'foo'.split(''));
```

<details>
<summary>Solution</summary>

```js
'f,o,o';
```

Reason:
--> [] + [] effectively becomes "" + "", which results in an empty string "".
---> 'foo'.split('') result is ["f", "o", "o"].
---> In JavaScript, when you use the + operator with a string and an array, the array is converted to its string representation before the concatenation.
---> The string representation of an array is obtained by joining its elements with commas. For the array ["f", "o", "o"], the string representation is "f,o,o".

</details>

---

### 55.

```js
var x = 0;
console.log(x++);
console.log(++x);
```

<details>
<summary>Solution</summary>

```js
0;
2;
```

</details>

---

### 58.

```js
console.log('1' - -'1');
```

<details>
<summary>Solution</summary>

```js
2;
```

---> '1' is converted to the number 1.
---> -1 negates the value of '1', turning it into -1.

---> The subtraction '1' - -1 is performed, resulting in 1 - (-1) = 2.

</details>

---

### 56.

```js
console.log(!!null);
```

<details>
<summary>Solution</summary>

```js
false;
```

</details>

---

### 57.

```js
console.log(!!undefined);
```

<details>
<summary>Solution</summary>

```js
false;
```

</details>

---

#


### 66. 

```js
console.log(1);
 
setTimeout(() => console.log(2));
 
Promise.resolve().then(() => console.log(3));
 
Promise.resolve().then(() => setTimeout(() => console.log(4)));
 
Promise.resolve().then(() => console.log(5));
 
setTimeout(() => console.log(6));
 
console.log(7);

```

<details>
<summary>Solution</summary>

```js
1
7
3
5
2
6
4 
```

- console.log(1); - This is a synchronous operation. It logs 1 immediately.
- setTimeout(() => console.log(2)); - This schedules a macrotask to log 2. It is put into the macrotask queue (also known as the task queue) and will execute after all currently scheduled macrotasks and the current execution context is complete.
- Promise.resolve().then(() => console.log(3)); - This schedules a microtask. Microtasks are used for promises and queues that are processed at the end of the current task before the JavaScript runtime starts the next task. It will log 3 as soon as the current script finishes, but before any tasks (such as setTimeout) are executed.
- Promise.resolve().then(() => setTimeout(() => console.log(4))); - This is scheduling a microtask that itself schedules a macrotask. First, the microtask will run after the current script (to log 4 but within a setTimeout, making it a macrotask).
- Promise.resolve().then(() => console.log(5)); - This schedules another microtask to log 5, similar to the earlier promise.
- setTimeout(() => console.log(6)); - This schedules another macrotask to log 6, added to the macrotask queue.
- console.log(7); - Another synchronous operation, logs 7 immediately after 1.


</details>

----

# <--- SAMPLE CONTENT ENDS --->
