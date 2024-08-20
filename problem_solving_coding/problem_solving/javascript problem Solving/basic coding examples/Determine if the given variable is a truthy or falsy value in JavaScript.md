## Determine if the given variable is a truthy or falsy value in JavaScript

<strong>Approach Taken:</strong>

1. if you add double exclamation that means it returns boolean (true/false)

```js
const isTruthy = (value) => !!value;

console.log(isTruthyTernary(1)); // true
console.log(isTruthyTernary(0)); // false
console.log(isTruthyTernary('hello')); // true
console.log(isTruthyTernary('')); // false
```
