## Output the longest prefix that is found in the array of arguments

```js
function lcp(arr) {
}

// Test cases
console.log(lcp(['flower', 'flag', 'flutter'])); // Test Case 1 should return 'fl'
console.log(lcp(['racedog', 'car', 'racecar'])); // Test Case 2 should return ''

```


```js
// SOLUTION
function lcp(arr) {
  if (arr.length === 0) return ''; // Step 1: Check if the array is empty

  let prefix = arr[0]; // Step 2: Initialize the prefix

  for (let i = 1; i < arr.length; i++) {
    // Step 3: Loop through each string

    // while loop is checking whether the current prefix is not at the start of the string arr[i].
    // If this condition is true, it indicates that the current prefix is not a common prefix for arr[i]
    while (arr[i].indexOf(prefix) !== 0) {
      // Step 4: Update the prefix
      prefix = prefix.substring(0, prefix.length - 1);
      if (prefix === '') return ''; // If prefix is empty, return it
    }
  }

  return prefix; // Step 5: Return the longest common prefix
}

// Test cases
console.log(lcp(['flower', 'flag', 'flutter'])); // Test Case 1 should return 'fl'
console.log(lcp(['racedog', 'car', 'racecar'])); // Test Case 2 should return ''

```