## Find the largest elements from the 2 dimensional array

**Approach Taken:**

1. assume matrix as rows
2. assume matrix[i] as columns
3. perform a for loop for matrix and one for loop for matrix[i]
4. assume 1st element in the matrix as the max `ex: matrix[0][0]`
5. if matrix[i][j] > max then max = matrix[i][j]
6. finally return the max

```js
function findLargestElement(matrix) {
  if (!matrix.length || !matrix[0].length) return null; // If empty array

  let max = matrix[0][0]; // Assume the first element is the largest

  //first for loop is based on the rows (ex: matrix, I mean matrix is entire array you are passing as part of param here, this says that you have 3 rows here)
  for (let i = 0; i < matrix.length; i++) {
    //second for loop is based on the columns (ex: matrix[i] logs [1,2,3] which means it has 3 columns)
    for (let j = 0; j < matrix[i].length; j++) {
      if (matrix[i][j] > max) {
        max = matrix[i][j];
      }
    }
  }

  return max;
}

// Test
const arr = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
console.log(findLargestElement(arr)); // Output: 9
```
