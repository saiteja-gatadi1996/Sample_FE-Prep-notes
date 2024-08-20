## 1. Prime Number

<details>
<summary>Solution</summary>

- The reason for using Math.sqrt(number) in the loop condition when checking for prime numbers <u>**is an optimization technique**</u>.
- To determine if a number is prime, **you need to check if it has any divisors other than 1 and itself**.
- If a number is not prime, it means it is divisible by some number other than 1 and itself.

```js
const number = parseInt(prompt('Enter a number'), 10); // Parse the input as an integer

if (!isNaN(number) && number > 1) {
  // Ensure the number is valid and greater than 1
  let isPrime = true; // Assume the number is prime until proven otherwise

  for (let i = 2; i <= Math.sqrt(number); i++) {
    // Optimization: only go up to the square root of the number
    if (number % i === 0) {
      isPrime = false; // Found a divisor, so the number is not prime
      break; // No need to check further if the number is not prime
    }
  }

  if (isPrime) {
    console.log(`${number} is a prime number.`);
  } else {
    console.log(`${number} is not a prime number.`);
  }
} else {
  console.log('You did not enter a valid positive number greater than 1.');
}
```

</details>

---

## 2. Fibonacci

<details>
<summary>Solution</summary>

```js
const number = parseInt(prompt('Enter a number'), 10); // Parse the input as an integer

if (!isNaN(number)) {
  let n1 = 0,
    n2 = 1,
    sum;

  for (let n = 0; n < number; n++) {
    console.log(n1); // Output the current number in the sequence
    sum = n1 + n2; // Calculate the next number in the sequence
    n1 = n2; // Update n1 to the next number
    n2 = sum; // Update n2 to the new sum
  }
} else {
  console.log('You did not enter a valid number.');
}
```

</details>

---

## 3. Armstrong

- A number that equals the **sum of its digits**, each raised to a power.
- For example, if you have a number like `153`, it's an Armstrong number because `1^3 + 5^3 + 3^3` equals `153`

<details>
<summary>Solution</summary>

```js
const number = prompt('Enter a number');
const numberOfDigits = number.length;
let temp = parseInt(number, 10);
let sum = 0;

while (temp > 0) {
  let digit = temp % 10;
  sum += Math.pow(digit, numberOfDigits);
  temp = Math.floor(temp / 10); // Use floor to handle floating-point issues
}

if (sum === parseInt(number, 10)) {
  console.log(`${number} is an Armstrong number.`);
} else {
  console.log(`${number} is not an Armstrong number.`);
}
```

 </details>

---

## 4. Star pattern

i)
![alt text](https://user-images.githubusercontent.com/42731246/142737086-21951694-10a3-406a-b729-64b6e3323a1d.png)

<details>
<summary>Solution</summary>

```js
for (let i = 1; i <= 5; i++) {
  let line = '';
  for (let j = 1; j <= i; j++) {
    line += '*';
  }
  console.log(line);
}
```

</details>

---

ii)
![alt text](https://user-images.githubusercontent.com/42731246/142737093-88975450-44bd-4d05-870e-e8ea5664eb14.png)

<details>
<summary>Solution</summary>

```js
for (let i = 5; i >= 1; i--) {
  let line = '';
  for (let j = 1; j <= i; j++) {
    line += '*';
  }
  console.log(line);
}
```

</details>

---

## 5. Fizzbuzz

<details>
<summary>Solution</summary>

```js
for (let i = 1; i <= 100; i++) {
  let output =
    i % 3 === 0 && i % 5 === 0
      ? 'FizzBuzz'
      : i % 3 === 0
      ? 'Fizz'
      : i % 5 === 0
      ? 'Buzz'
      : i;
  console.log(output);
}
```

</details>

---

## 6. Sort an float array

<details>
<summary>Solution</summary>

```js
// Define the array of numbers
const arrayNums = [86.999385869, 67.2645807464, 12.5768967449, 55.978746363];

// Sort the array in ascending order using the sort function
const sortedArrayNums = arrayNums.sort((a, b) => a - b);

// Log the sorted array to the console
console.log(sortedArrayNums);
```

</details>

---

## 7. Maximum and Minimum values

<details>
<summary>Solution</summary>

#### Approach 1

```js
// Define the array of numbers
const arrayItems = [10, 20, 11, 35, 12, 40, 13, 65, 14, 78, 16];

// Find the maximum value in the array
const max = Math.max(...arrayItems);
console.log(max); // Output: 78

// Find the minimum value in the array
const min = Math.min(...arrayItems);
console.log(min); // Output: 10
```

#### Approach 2

```js
const arrayItems = [10, 20, 11, 35, 12, 40, 13, 65, 14, 78, 16];

let max = arrayItems[0];
let min = arrayItems[0];

for (let i = 1; i < arrayItems.length; i++) {
  if (arrayItems[i] > max) {
    max = arrayItems[i];
  }
  if (arrayItems[i] < min) {
    min = arrayItems[i];
  }
}

console.log(max); // This will log the maximum value in the array
console.log(min); // This will log the minimum value in the array
```

</details>

---

## 8. Output as per the questions

```js
// Given two arrays, output should be c=[1,2,3,4,6,8,9]
// merge a and b and remove duplicates
// sort the array in ascending
```

<details>
<summary>Solution</summary>

```js
let a = [6, 2, 8, 1, 2];
let b = [4, 2, 1, 3, 9];

// Merge the arrays and remove duplicates by converting to a Set and back to an Array
let merged = [...new Set([...a, ...b])];

// Sort the array in ascending order
merged.sort((x, y) => x - y);

console.log(merged); // Output will be [1, 2, 3, 4, 6, 8, 9]
```

</details>

---

## 9. Counter example in React

<details>
<summary>Solution</summary>

```js
import React, { useState } from 'react';
import './styles.css';

export default function App() {
  const [counter, setCounter] = useState(0);

  const incrementCounter = () => {
    setCounter(counter + 1);
  };

  const decrementCounter = () => {
    setCounter(counter - 1);
  };

  return (
    <div className='App'>
      <h1>{counter}</h1>
      <button onClick={incrementCounter}>+</button>
      <button onClick={decrementCounter}>-</button>
    </div>
  );
}
```

</details>

---

## 10.

```js
// 1. Given the below array
let a = [
  { key: '1', name: 'AAA', field: 'Software', location: 'Bangalore' },
  { key: '2', name: 'BBB', field: 'Hardware', location: 'Bangalore' },
  { key: '3', name: 'CCC', field: 'SW&HW', location: 'Bangalore' },
];

// 2. key 2 should be modified into Software and Delhi
```

<details>
<summary>Solution</summary>

```js
let a = [
  { key: '1', name: 'AAA', field: 'Software', location: 'Bangalore' },
  { key: '2', name: 'BBB', field: 'Hardware', location: 'Bangalore' },
  { key: '3', name: 'CCC', field: 'SW&HW', location: 'Bangalore' },
];

// Assuming we want to update the object with key '2'
let b = a.map((item) => {
  if (item.key === '2') {
    return { ...item, field: 'Software', location: 'Delhi' };
  }
  return item;
});

console.log(b);
/* [
    {
        "key": "1",
        "name": "AAA",
        "field": "Software",
        "location": "Bangalore"
    },
    {
        "key": "2",
        "name": "BBB",
        "field": "Software",
        "location": "Delhi"
    },
    {
        "key": "3",
        "name": "CCC",
        "field": "SW&HW",
        "location": "Bangalore"
    }
]
*/
```

</details>

---

## 11. Destructuring Example (Nested one)

```js
// Destructure nested city into a plain so that when I log city it should be logging Noida
var obj = { name: 'Raj', address: { city: 'Noida' } };
```

i)

<details>
<summary>Solution</summary>

```js
var obj = { name: 'Raj', address: { city: 'Noida' } };

const {
  name,
  address: { city },
} = obj;

console.log(city); // Noida
```

</details>

---

ii)

<details>
<summary>Solution</summary>

```js
var a = { no1: 10 };
var b = a;

b.no1++;

console.log(a, b); // Output will be: { no1: 11 } { no1: 11 }
```

</details>

---

## 12. Rest Operator Basic Example

<details>
<summary>Solution</summary>

```js
function add(...args) {
  return args.reduce((a, b) => a + b);
}

console.log(add(1, 2, 3, 4, 5, 6, 7)); // 28
```

</details>

---

## 13. Palindrome

<details>
<summary>Solution</summary>

```js
function isPalindrome(str) {
  // Remove non-alphanumeric characters and convert to lowercase for a case-insensitive comparison
  const cleanedStr = str.replace(/[\W_]/g, '').toLowerCase();

  // Check if the cleaned string is a palindrome
  let start = 0;
  let end = cleanedStr.length - 1;

  while (start < end) {
    if (cleanedStr[start] !== cleanedStr[end]) {
      return false; // If characters don't match, it's not a palindrome
    }
    start++;
    end--;
  }

  return true; // If the loop completes, all characters matched and it's a palindrome
}

// Example usage:
console.log(isPalindrome('A man, a plan, a canal: Panama')); // should return true
console.log(isPalindrome('racecar')); // should return true
console.log(isPalindrome('hello')); // should return false
console.log(isPalindrome('malayalam')); // should return true
```

</details>

---

## 14. Count the 'a' passed in the array of items

<details>
<summary>Solution</summary>

```js
const names = [
  'Tom',
  'Charlie',
  'Harry',
  'Sarah',
  'Huda',
  'Samantha',
  'Emily',
  'Elizabeth',
];

names.forEach((name) => {
  // added reference screenshot on this piece of line actually works in the background
  const count = name.toLowerCase().split('a').length - 1;
  console.log(`There are ${count} 'a's in name ${name}`);
});
```

```js
/*
There are 0 'a's in name Tom
index.js:14 There are 1 'a's in name Charlie
index.js:14 There are 1 'a's in name Harry
index.js:14 There are 2 'a's in name Sarah
index.js:14 There are 1 'a's in name Huda
index.js:14 There are 3 'a's in name Samantha
index.js:14 There are 0 'a's in name Emily
index.js:14 There are 1 'a's in name Elizabeth
*/
```

</details>

---

## 15. Count the duplicate number that has repeated more number of times

```js
//inputArr
let a = [5, 6, 7, 5, 8, 5, 2, 5, 9];

//outputArr
5 is the most frequent appearing 5 times
```

<details>
<summary>Solution</summary>

```js
let inputArr = [5, 6, 7, 5, 8, 5, 2, 5, 9];

// Function to count duplicates and find the number with the highest count
function countDuplicates(arr) {
  let counts = {};
  let maxCount = 0;
  let mostFrequent;

  // Count occurrences of each number
  arr.forEach((item) => {
    counts[item] = (counts[item] || 0) + 1;

    // Keep track of the most frequently occurring number
    if (counts[item] > maxCount) {
      maxCount = counts[item];
      mostFrequent = item;
    }
  });

  return { mostFrequent, maxCount };
}

const result = countDuplicates(inputArr);
console.log(
  `Number ${result.mostFrequent} is the most frequent, appearing ${result.maxCount} times.`
);

// Number 5 is the most frequent, appearing 4 times.
```

</details>

---

## 16. How to implement your own Custom Event in JavaScript?

<details>
<summary>Solution</summary>

- You can use the CustomEvent constructor to create an custom event.
- The CustomEvent Constructor accepts two arguments, (eventName, optionalObject)
- You can use the dispatchEvent method to dispatch the custom event on the target element/document

```js
const event = new CustomEvent('event1', {
  detail: { name: 'Javascript' },
});

element.dispatchEvent(event);
```

```js
// listening the events

element.addEventListener('event1', (event) => {
  console.log(event.detail);
});
```

</details>

---
