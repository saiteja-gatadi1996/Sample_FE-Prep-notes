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

----

# <--- SAMPLE CONTENT ENDS --->
