- <strong>Scope: </strong> A set of code that has all your variables defined in it and those variables are only accessible inside that scope, anything outside that scope does not have access to those variables

#### Example 1 :

- variable b is only accessed in the function (Function scope)

```js
const a = 1

function test() {
  const b = 2
  console.log("Here is the values", a, b) // Here is the values 1 2
}

test()
console.log(a, b) // Reference Error: b is not defined
```

#### Example 2 :

```js
const a = 1

function test() {
  const b = 2
  console.log("Here is the values", a, b) // Here is the values 1 2
}

test()
console.log(a, b) // Reference Error: b is not defined
```

---

# <--- SAMPLE CONTENT ENDS --->

------

#### Example 3: Global Scope


---

#### Example 4: Module Scope


---

#### Example 5: Function Scope


---

#### Example 6: Function Scope (with var keyword declaration)

---

#### Example 7: Block Scope


---

#### Example 8: multiple variables with the same name

---
