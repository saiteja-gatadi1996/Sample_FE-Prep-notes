### Array.isArray:

**Definition:** 
- Determines whether the <ins>passed value is an **Array**</ins>

```js
//Syntax:
Array.isArray(value);
```

<strong>Approach Taken:</strong>

```js
//core logic
Object.prototype.toString.call(inputItem) === '[object Array]'
```

- One common approach is to use the `Object.prototype.toString.call()` method to get the object type as a string and check if it is **`"[object Array]"`**. 
- Here is an example implementation:

```javascript
//customArray function is the correct way
Array.customArray = function (input) {
  return Object.prototype.toString.call(input) === '[object Array]';
};

//isArray
console.log('Array.isArray([])', Array.isArray([])); //true
console.log('Array.isArray({})', Array.isArray({})); //false
--------------------------------------------------------
//customArray
console.log('Array.customArray([])', Array.customArray([])); //true
console.log('Array.customArray({})', Array.customArray({})); //false
```

----

#### Prototype fashion:

```js
//if you want to achieve in prototype fashion then below is the way
Array.prototype.customArray = function () {
  return Object.prototype.toString.call(this) === '[object Array]';
};

const arr = [];
console.log('arr.customArray', arr.customArray()); //true
const obj = {};
console.log('obj.customArray', obj.customArray); // undefined
```
