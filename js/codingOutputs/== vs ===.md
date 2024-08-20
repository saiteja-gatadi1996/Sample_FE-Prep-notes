```js
console.log(1 == "1")
```

<details>
<summary>Solution</summary>

- true

<strong>Reason:</strong> double equal doesn't do strict check and it converts it so that they're both the same

- In this case, string will be converted into number

</details>

---

```js
console.log(1 === "1")
```

<details>
<summary>Solution</summary>

- false

<strong>Reason:</strong> tripe equal do strict check (as it checks both dataType and numbers)

- In this case, number is not equal to a string

</details>

---

```js
console.log(0 == "")
```

<details>
<summary>Solution</summary>

- true

<strong>Reason:</strong> Converting it types

- In this case, empty string means 0

</details>

---

```js
console.log(0 === "")
```

<details>
<summary>Solution</summary>

- false

<strong>Reason:</strong> As this checks the dataType, so returns false

</details>

---

```js
console.log(0 == false)
```

<details>
<summary>Solution</summary>

- true

<strong>Reason:</strong> Converting it types

- In this case, false means 0

</details>

---

```js
console.log(0 === false)
```

<details>
<summary>Solution</summary>

- false

<strong>Reason:</strong> Converting it types

- In this case, false means 0

</details>

---

```js
console.log(null == null)
```

<details>
<summary>Solution</summary>

- true

</details>

---

# <--- SAMPLE CONTENT ENDS --->
