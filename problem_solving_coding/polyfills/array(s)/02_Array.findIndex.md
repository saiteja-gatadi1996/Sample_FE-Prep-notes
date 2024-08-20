### Array.prototype.findIndex

**Definition**: 
- The **`findIndex`**() method of Array Instances returns the <ins>**index of the first element**</ins> in an array that satisfies the provided testing function.
- If **`no`** elements are matched, it returns **`-1`**

```js
//Syntax:
findIndex(callbackFn, thisArg);
```

```js
// Realtime example usage
const arr = [1,2,3]
console.log(arr.finIndex((item)=>item===3)) //2, because we are returning index
```

<strong>Approach Taken:</strong>

```js
//core logic
if(callbackFunctionParam.call(thisArg, inputArr[index], index, inputArr )) {
  return index
}
```

1. **`const inputArr = Object(this)`**
2. **`const inputArrLength = Number(inputArr.length) || 0`**
3. perform a basic **`for`** loop
4. CORE LOGIC
5. outside the for loop **return `-1`**

```js
if (!Array.prototype.customFindIndex) {
  Array.prototype.customFindIndex = function (callbackFunc, thisArg) {
    if (this == null) {
      throw new TypeError('"this" is null or not defined');
    }

    if (typeof callbackFunc !== 'function') {
      throw new TypeError('callback must be a function');
    }

    //your inputArr
    var inputArr = Object(this);

    //your inputArrLength
    var inputArrLen = Number(inputArr.length) || 0;

    //basic "for" loop based on "inputArrLength"
    for (let i = 0; i < inputArrLen; i++) {
      //thisArg, searchElement, index, array
      if (callbackFunc.call(thisArg, inputArr[i], i, inputArr)) {
        return i; //return index if condition is true
      }
    }
    //outside for loop
    return -1;
  };
}

//Example 1
const array1 = [5, 12, 8, 130, 44];
const isLargeNumber = (element) => element > 13;
console.log(array1.customFindIndex(isLargeNumber));
// Expected output: 3, because 130 is at index 3

//Example 2
const numbers = [-3, 8, 9, -5, 7, -2];
const index = numbers.customFindIndex((num) => num < 0);
console.log(index); // Output:  (because -3 is the first negative number and its index is 0)

//Example 3
const people = [
  { name: 'John', age: 15 },
  { name: 'Doe', age: 17 },
  { name: 'Anna', age: 22 },
  { name: 'Mike', age: 19 },
];
const index1 = people.customFindIndex((person) => person.age >= 18);
console.log(index1); // Output: 2 (because Anna is the first adult and her index is 2)

//Example 4
const words = ['apple', 'banana', 'cherry', 'date'];
const index2 = words.customFindIndex((word) => word.length > 5);
console.log(index2); // Output: 1 (because "banana" has a length of 6 and its index is 1)

//Example 5
const library = [
  { title: 'Moby Dick', author: 'Herman Melville' },
  { title: '1984', author: 'George Orwell' },
  { title: 'Brave New World', author: 'Aldous Huxley' },
];
const index3 = library.customFindIndex((book) => book.title === '1984');
console.log(index3); // Output: 1

//Example 4
const words3 = ['apple', 'banana', 'cherry', 'date'];
const index4 = words3.customFindIndex((word) => word === 'cherry'); //2
console.log(index4); // Output: 2 (because "cherry" is at its index is 2)
```
