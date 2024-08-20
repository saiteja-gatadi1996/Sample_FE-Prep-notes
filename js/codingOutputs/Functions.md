### Question 1:

```js
console.log(square)
console.log(square(5))

const square = function (n) {
  return n * n
}
```

<details>
<summary>Solution</summary>

Reference Error: Cannot access 'square' before initialization
<i>you won't next line of console.log before the it is run time error.</i>

</details>

---

### Question 2:

```js
console.log(square)
console.log(square(5))

var square = function (n) {
  return n * n
}
```

<details>
<summary>Solution</summary>

undefined
Reference Error: Cannot access 'square' before initialization

Reason for Reference Error : <i> function block is not hoisted</i>

</details>

---

# <--- SAMPLE CONTENT ENDS --->
