## DeepClone of an object

- <strong>Approach Taken :</strong>

1. An input obj can have an object or null or an array
2. Write three conditions, one for handling objects, arrays, (null and not object)
3. If it is not object (ex: a: 6), then return as it is (i.e the obj passed)
4. If it is array, map with each and every item and pass that item into the function (Which will satisfy one of the three conditions)
5. If it is an object, use a `for-in` loop to iterate inside the object and for each property of the source object (obj), it calls the deepClone function recursively

```js
const obj1 = { a: 1, b: 2, c: { d: 4, e: 5, f: { g: 6 } } };
const shallowClone = { ...obj1 };
console.log('shallowCloned Obj', shallowClone);
console.log('Testing shallowCloned Obj', obj1.c === shallowClone.c); //true, because it doesn't apply to the nested objects

function deepClone(inputObj) {
  // logic 1 is to check if inputParam is of null or not an object (Primitives and null)
  if (inputObj === null || typeof inputObj !== 'object') {
    return inputObj;
  }
  // logic 2 is Array.isArray(inputParam), inputParam.map((item)=>deepClone(item))
  if (Array.isArray(inputObj)) {
    return inputObj.map((item) => deepClone(item));
  }
  // logic 3 is typeof inputParam === 'object', maintain a copyObj, for in loop on inputParam and check if inputParam.hasOwnProperty(key) then copyObj[key] = deepClone(inputParam[key])
  if (typeof inputObj === 'object') {
    const copyObj = {};

    for (let key in inputObj) {
      if (inputObj.hasOwnProperty(key)) {
        copyObj[key] = deepClone(inputObj[key]);
      }
    }
    return copyObj;
  }
}

const obj2 = { a: 1, b: 2, c: { d: 4, e: 5, f: { g: 6 } } };
const deepClonedObject = deepClone(obj2);
console.log('deepClonedObj', deepClonedObject);
console.log('Testing deepClonedObj', obj2.c === deepClonedObject.c); //false, because references are not same
```

<ins>**Time Complexity**</ins>: O(n)