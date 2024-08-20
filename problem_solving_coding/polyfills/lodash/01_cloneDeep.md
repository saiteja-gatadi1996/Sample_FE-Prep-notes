## cloneDeep

**Definition**: Loadash.cloneDeep() method is used to `create a deep copy` of the value and it `recursively clones` the value. The newly created object has the `same value as the original` but they are `not the same object in the memory`.

<strong>Approach Taken:</strong>

1. one condition for primitives and null (ex: typeof value!==object || value === null)
2. one condition for Array.isArray(value)
3. another condition for typeof value === 'object'
4. for primitives & null (I mean for condition 1), simply return the param that you have passed (ex: value)
5. for Array condition, write a basic for loop based on the value.length. Maintain an array for recursion (ex: finalArr[i] = cloneDeep(value[i])). Post for loop ends, return that stored/created finalArr
6. for object condition, maintain an empty object and perform a for-in-loop and pass recursively (ex: finalObj[key] = cloneDeep(value[key])). Post for loop ends, return the finalObj

```js
function deepCloneCustom(obj) {
  //primitives and null
  if (obj === null || typeof obj !== 'object') {
    return obj;
  }
  // Arrays
  if (Array.isArray(obj)) {
    const arrCopy = [];
    for (let value of obj) {
      arrCopy.push(deepCloneCustom(value));
    }
    return arrCopy;
  }

  // object
  if (typeof obj === 'object') {
    const objCopy = {};
    for (let key in obj) {
      if (obj.hasOwnProperty(key)) {
        objCopy[key] = deepCloneCustom(obj[key]);
      }
    }
    return objCopy;
  }
}

// Usage example
const original = {
  name: 'Alice',
  age: 30,
  address: {
    street: '123 Main St',
    city: 'Nowhere',
  },
  hobbies: ['reading', 'coding'],
};

const deepClonedObj = deepCloneCustom(original);

console.log(deepClonedObj); // Outputs cloned object
console.log(deepClonedObj.address === original.address); // Outputs: false
console.log(deepClonedObj.hobbies === original.hobbies); // Outputs: false
```
