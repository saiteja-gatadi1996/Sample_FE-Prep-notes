## Array.from:

**Definition**: creates a `new, shallow-copied array instance` from an `iterable` or `array-like` object

**Syntax**

```js
Array.from(arrayLike, mapFn, thisArg);
```

<strong>Approach Taken:</strong>

1. we need write a separate logic for `iterators` like (Strings, Set, Map, Array)
2. A separate logic for arrayLike `Objects`. Array like objects means that has the length property inside the object (`or not iterables`).
<u><b>The defining feature of an array-like object is not just having numeric keys, but also having a length property that accurately reflects the number of elements (based on the numeric keys).</b></u>
3. For iterators, `simply spread your inputArr`, if mapFn is provided then spreadArr.map(mapFn, thisArg) else spreadArr will be returned
4. for non-iterator, `create a dummy arr with the length` (ex: Array(length))
5. you can get length of inputArrayLike object with .length property (ex: Math.floor(inputArr.length))
6. do a basic for loop and at the end we need that dummyArr to be mapped with the providedParamInputArray (ex: `dummyArr[eachIteration] = providedParamInputArr[i]`)

```js
if (!Array.customFrom) {
  Array.customFrom = function (inputArr, mapFn, thisArg) {
    if (inputArr == null) {
      throw new TypeError('inputArr cannot be null or undefined');
    }

    if (typeof mapFn !== 'undefined' && typeof mapFn !== 'function') {
      throw new TypeError('The map function must be a function');
    }

    // if condition is true only for the iterables like Strings, Set, Map, Array (More examples are added in the separate code block)
    if (typeof Symbol === 'function' && inputArr[Symbol.iterator]) {
      const arr = [...inputArr]; // this will simply convert into an array ex: Set[ArrayYouProvide] ===> [ArrayYouProvide]
      return mapFn ? arr.map(mapFn, thisArg) : arr; //if mapFn is provided as per the syntax, then map it otherwise as it is.
    }

    // Below rest of the code will only get executed if it is not iterable ex: Objects {}
    const length = Math.floor(Math.abs(inputArr.length));
    const output = Array(length); // if length is 3 then it create 3 empty spaces [null, null, null]

    for (let i = 0; i < length; i++) {
      output[i] = inputArr[i]; // each empty space will be replaced with the inputArr[i]
    }

    return mapFn ? output.map(mapFn, thisArg) : output;
  };
}

// Example Usage:

// #1 An array-like object
const arrayLike = { 0: 'zero', 1: 'one', 2: 'two', length: 3 };

// Converting the array-like object to an array and transforming each element
const array = Array.customFrom(arrayLike, (value) => value.toUpperCase());

console.log(array); // Should log ["ZERO", "ONE", "TWO"]

// #2 Creating a Set
const set = new Set([1, 2, 3, 4, 5]);

// Converting the Set to an array using `Array.customFrom`
const setArray = Array.customFrom(set);

console.log(setArray); // Should log [1, 2, 3, 4, 5]

// Example 3:
console.log('foo', Array.customFrom('foo')); // ['f', 'o', 'o']

//Example 4
const map = new Map([
  [1, 2],
  [2, 4],
  [4, 8],
]);
console.log('foo', Array.customFrom(map)); // [[1, 2], [2, 4], [4, 8]]
```
