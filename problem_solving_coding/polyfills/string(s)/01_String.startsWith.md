## String.prototype.startsWith:

**Definition**: 
- Determines whether this **<ins>string begins with the characters of a specified string</ins>** 
- returning **`true`** or **`false`** as appropriate.

```js
//syntax:
startsWith(searchString, position);
```

<strong>Approach Taken:</strong>


```js
// core logic
this.substring(finalPosition, finalPosition + searchElement.length) === searchElement
```

- `String.prototype` is equal to a function that accepts two parameters, 
  - first one is **what you want to `search`** 
  - second param is **from which `position` you want to start** ex: 0 or 1 or 10
<br/>

- if no position is passed, 
  - consider it as 0, 
  - else consider whatever is passed (using ternary operator)
<br/>

- **`this`** keyword **points to the <ins>complete string</ins>** 
  - performing **`.substring`** to **`this`** with **`pos`**, **`pos+ searchElement.length`** and do triple equal check with the searchElement param to return **`boolean`** value

```js
//Example
"Hello world".substring(0, 5) === "Hello" //returns true
```

```js
// Actual Code
if (typeof String.prototype.customStartsWith !== 'function') {
  String.prototype.customStartsWith = function (searchElement, position) {
    // if your input param position is greater than 0 then final position will hold that value, else 0
    var finalPosition = position > 0 ? position : 0;
    // this.substring(finalPosition, finalPosition + searchElement.length) is nothing but
    // "To be".substring(0, 0+5) 
    return this.substring(finalPosition, finalPosition + searchElement.length) === searchElement;
  };
}

// Example Usage
const str = 'To be, or not to be, that is the question.';

console.log(str.customStartsWith('To be')); // true
console.log(str.customStartsWith('not to be')); // false
console.log(str.customStartsWith('not to be', 10)); // true, because at index 10 it starts with `not to be`
```
