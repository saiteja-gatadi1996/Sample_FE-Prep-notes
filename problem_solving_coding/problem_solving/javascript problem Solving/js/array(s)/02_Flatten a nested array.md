## Flatten a nested array

**Approach Taken:**

1. maintain a finalArray to return (ex: const result = [])
2. for of loop to the paramArr (ex: for(let item of arr))
3. if the item satisfies the Array.isArray(item) then simply use the recursion technique (ex: result.push(...yourFunction(item)))
3. else result.push(item)

```js
function flattenRecursive(arr) {
  let result = [];
  for (let item of arr) {
    if (Array.isArray(item)) {
      result.push(...flattenRecursive(item));
    } else {
      result.push(item);
    }
  }
  return result;
}

// Test
const nestedArray = [1, [2, 3, [4, 5]], 6, [[7], [8, 9]]];
console.log(flattenRecursive(nestedArray)); // Expected output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
