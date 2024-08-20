### Number.isNaN:

**Definition:** Determines whether the passed value is an Number value NaN, and returns false if the input is not of the Number type.

```js
//Syntax:
Number.isNaN(value);
```

<strong>Approach Taken:</strong>

1. is a function that returns valueParam!==valueParam

```js
if (!Number.isCustomNaN) {
  Number.isCustomNaN = function (value) {
    return value !== value;
  };
}

//Example Usages:
console.log(Number.isCustomNaN(NaN)); // expected output: true
console.log(Number.isCustomNaN(undefined)); // expected output: false
console.log(Number.isCustomNaN(37)); // expected output: false

console.log('--------------------');

// All of them are non-numbers and returns false for every operation

console.log(Number.isCustomNaN('NaN')); //false
console.log(Number.isCustomNaN(undefined)); //false
console.log(Number.isCustomNaN({})); //false

console.log('--------------------');

console.log(Number.isCustomNaN('blabla')); //false
console.log(Number.isCustomNaN(true)); //false
console.log(Number.isCustomNaN(null)); //false

console.log('--------------------');

console.log(Number.isCustomNaN('37')); //false
console.log(Number.isCustomNaN('37.37')); //false
console.log(Number.isCustomNaN('')); //false
console.log(Number.isCustomNaN(' ')); //false

console.log('--------------------');

// All of them returns true
console.log(Number.isCustomNaN(NaN)); // expected output: true
console.log(Number.isCustomNaN(undefined / 5)); // expected output: true
console.log(Number.isCustomNaN('text' / 2)); // expected output: true
console.log(Number.isCustomNaN(Math.sqrt(-1))); // expected output: true
console.log(Number.isCustomNaN(Number.NaN)); // expected output: true
```
