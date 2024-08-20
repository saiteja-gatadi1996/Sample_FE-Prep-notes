### Theory questions based on React and JS

- Redux state
- Async calls in Redux
- some other questions related to React

### Problem solving questions

##### 1) Write a function to count the occurrence of each character in the input string.

```js
// Input: “abbcccd”
// Output: a: 1, b: 2, c: 3, d: 1
```

###### constraints: Use Array.reduce method to get the output

Certainly! Here's a JavaScript function that uses the `Array.reduce` method to count the occurrence of each character in the input string:

```javascript
function countOccurrences(inputString) {
  const charCount = inputString.split('').reduce((acc, char) => {
    if (acc[char]) {
      acc[char]++;
    } else {
      acc[char] = 1;
    }
    return acc;
  }, {});
  
  return charCount;
}

const inputString = "abbcccd";
const result = countOccurrences(inputString);

for (const char in result) {
  console.log(`${char}: ${result[char]}`);
}
```

In this code, the `countOccurrences` function splits the input string into an array of characters and then uses the `Array.reduce` method to accumulate the character counts in an object. The final object contains the counts of each character.

The loop at the end iterates through the object properties to display the desired output:

```
a: 1
b: 2
c: 3
d: 1
```

---

##### 2) Write a function for the desired output as:

```js
// Input: sum(2)(3)()
// Output: 5

// Input: sum(2)(3)(4)()
// Output: 9
```

Sure! You can achieve this using function currying in JavaScript. Here's how you can write the `sum` function to achieve the desired output:

```javascript
function sum(x) {
  let currentSum = x;

  function innerSum(y) {
    if (y === undefined) {
      return currentSum;
    }
    currentSum += y;
    return innerSum;
  }

  return innerSum;
}

console.log(sum(2)(3)());         // Output: 5
console.log(sum(2)(3)(4)());      // Output: 9
```

In this code, the `sum` function returns an inner function `innerSum` which either adds the provided number to the current sum or, if no argument is provided, returns the current sum. This allows you to chain multiple calls together as shown in your examples.

The first call to `sum(2)` returns the `innerSum` function. The second call to `(3)` adds 3 to the current sum of 2. The third call to `()` with no arguments returns the final result of 5.

Similarly, the first call to `sum(2)` returns the `innerSum` function. The second call to `(3)` adds 3 to the current sum of 2. The third call to `(4)` adds 4 to the current sum of 5. The fourth call to `()` with no arguments returns the final result of 9.

---

##### 3) Write a program to convert the below given input format into given output format

##### Input:

```js
{
   "user":{
      "name":"John",
      "tech":"Frontend",
      "address":{
         "home":{
            "add_1":"home_dummy_add_1",
            "add_2":"home_dummy_add_2"
         },
         "office":{
            "add_1":"off_dummy_add_1",
            "add_2":"off_dummy_add_2"
         }
      }
   }

```

##### Expected Output:

```js
{
  user_name: 'John';
  user_tech: 'frontend';
  user_address_home_add_1: 'home_dummy_add_1';
  user_address_home_add_2: 'home_dummy_add_2';
  user_address_office_add_1: 'off_dummy_add_1';
  user_address_office_add_2: 'off_dummy_add_2';
}
```
