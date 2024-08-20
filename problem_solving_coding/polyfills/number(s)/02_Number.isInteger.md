### Number.isInteger:

**Definition:** Determines whether the passed value is an Integer

<strong>Approach Taken:</strong>

1. Check typeOf value is number, isFinite(value) is true and compare it is the same value you passed after round off ex: Math.floor(value) === value
2. isFinite says that it is a number and that number is neither positive Infinity, negative Infinity or NaN

```js
if (!Number.isCustomInteger) {
  Number.isCustomInteger = function (value) {
    return (
      typeof value === 'number' &&
      isFinite(value) &&
      Math.floor(value) === value
    );
  };
}

console.log(Number.isCustomInteger(0)); // expected output: true
console.log(Number.isCustomInteger(1)); // expected output: true
console.log(Number.isCustomInteger(-100000)); // expected output: true
console.log(Number.isCustomInteger(9999999999)); // expected output: true
console.log(Number.isCustomInteger(0.1)); // expected output: false
console.log(Number.isCustomInteger(Math.PI)); // expected output: false
console.log(Number.isCustomInteger(NaN)); // expected output: false
console.log(Number.isCustomInteger(Infinity)); // expected output: false
console.log(Number.isCustomInteger(-Infinity)); // expected output: false
console.log(Number.isCustomInteger('10')); // expected output: false
console.log(Number.isCustomInteger(true)); // expected output: false
console.log(Number.isCustomInteger(false)); // expected output: false
console.log(Number.isCustomInteger([1])); // expected output: false
console.log(Number.isCustomInteger(5.0)); // expected output: true
```
