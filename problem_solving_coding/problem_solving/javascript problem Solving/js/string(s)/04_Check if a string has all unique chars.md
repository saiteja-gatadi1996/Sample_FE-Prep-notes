## Check if a string has all unique characters

- <strong>Approach Taken for Set:</strong>

1. When you apply `new Set` to the string, it will return the unique characters.
2. So by simply checking the set size with the original string length with `===` results in unique or not.

```js
// Using a Set:
function hasAllUniqueCharsSet(str) {
  return new Set(str).size === str.length;
}

// Example:
console.log(hasAllUniqueCharsSet('hello')); // false
console.log(hasAllUniqueCharsSet('abcde')); // true
```

<ins>**Time Complexity**</ins>: O(n)
- **Reasoning**: Constructing a `Set` from a `string` iterates through each character of the string once to determine if it is unique, making it O(n) where n is the length of the string.

---

- <strong>Approach Taken for indexOf:</strong>

1. indexOf and lastIndexOf has to be applied on the character (ex: 's')
2. apply a `for of loop` to the str and you will get each and every character
3. str.indexOf(char), str.lastIndexOf(char), if both are not equal return false (ex: "hello" has l at 2 and l at 3)
4. if both are same (ex: string `abcde` has both indexOf and lastIndexOf same), it should exit for loop and return true (so make sure return true is outside of for loop)

```js
// using indexOf and lastIndexOf

function hasAllUniqueCharsIndexOf(str) {
  for (let char of str) {
    if (str.indexOf(char) !== str.lastIndexOf(char)) {
      return false;
    }
  }
  return true;
}

// Example:
console.log(hasAllUniqueCharsIndexOf('hello')); // false
console.log(hasAllUniqueCharsIndexOf('abcde')); // true
```

<ins>**Time Complexity**</ins>: O(n^2)
**Reasoning**: For each character in the string, the `indexOf` and `lastIndexOf` methods search through the entire string to find the first and last occurrence of that character, respectively. Since these searches are performed for every character, the overall time complexity is O(n^2), where n is the length of the string.