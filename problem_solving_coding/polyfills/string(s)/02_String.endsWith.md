## String.prototype.endsWith:

```js
//syntax:
endsWith(searchString, endPosition);
```

<strong>Approach Taken:</strong>


```js
// ex: "Hello world".substring(6, 11) === "world"
this.substring(this_len - searchElement.length, this_len)
```

- if no position is provided then 
  - we are considering length as the entire string length 
  - ex: 11 for "Hello world".


```js
if (!String.prototype.customEndsWith) {
  String.prototype.customEndsWith = function (searchElement, endPosition) {
    if (endPosition === undefined || endPosition > this.length) {
      // if no position is provided then consider it as Entire string length ex: 11 for Hello world
      endPosition = this.length;
    }
    // "Hello world".substring(6, 11) === "world"
    return this.substring(endPosition - searchElement.length, endPosition) === searchElement;
  };
}

// Example Usage
const str1 = 'Cats are the best!';

console.log(str1.customEndsWith('best!'));
// Expected output: true

console.log(str1.customEndsWith('best', 17));
// Expected output: true

const str2 = 'Is this a question?';

console.log(str2.customEndsWith('question'));
// Expected output: false

console.log('--------------------------------------');

// //Example 2:
const str = 'To be, or not to be, that is the question.';

console.log(str.customEndsWith('question.')); // true
console.log(str.customEndsWith('to be')); // false
console.log(str.customEndsWith('to be', 19)); // true
```
