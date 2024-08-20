**calculate sum of numbers in an nested array**

**Approach Taken**

1. maintain a sum to keep on adding it inside the for-of loop
2. during for of loop, check if each element is satisfies the Array.isArray(eachElement), if yes then simply mutate the el = recursiveFunction(el)
3. if that condition is not true then outside to that if condition, keep on adding the sum (ex: sum= sum + el, that means 1 + 2)
4. outside the for of loop, return that sum

```js
function sumArray(inputArray) {
  let sum = 0;
  for (let element of inputArray) {
    if (Array.isArray(element)) {
      sum = sum + sumArray(element); // Add the sum of the nested array
    } else {
      sum = sum + element; // For non-array elements, just add to sum
    }
  }
  return sum;
}

console.log(sumArray([1, 2, [3, [4], [5, 6]], [7]])); // 28
```
