## Find a first pair whose sum is zero using indexing

**Approach Taken**

1. input param accepts array
2. define two variables (left and right)
3. initialize left with 0 and right with array.length - 1 (it says max)
4. perform a while loop (left <right)
5. array[left] + array[right] will be stored in sum variable
6. if sum ===0 then simply return [array[left], array[right]]
7. else if sum > 0, decrement the right
8. else increment the left

```js
function getSumPairZero(array) {
  if (array.length === 0) {
    return 'Array is empty';
  }

  let left = 0;
  let right = array.length - 1;

  while (left < right) {
    let sum = array[left] + array[right];
    if (sum === 0) {
      return [array[left], array[right]];
    } else if (sum > 0) {
      right--;
    } else {
      left++;
    }
  }

  return 'No pair found that sums up to zero';
}

const result = getSumPairZero([-6, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 8]);
console.log(result); // [-6, 6]
```
