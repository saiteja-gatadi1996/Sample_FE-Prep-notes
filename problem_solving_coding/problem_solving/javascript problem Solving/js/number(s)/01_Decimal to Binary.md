## Decimal to Binary

```js
// Using loops:
function decimalToBinaryLoop(decimal) {
  let binary = '';
  let num = decimal;

  // Edge case for 0
  if (num === 0) {
    return '0';
  }

  while (num > 0) {
    binary = (num % 2) + binary;
    num = Math.floor(num / 2);
  }

  return binary;
}

const decimalNumber = 13;
console.log(decimalToBinaryLoop(decimalNumber)); // Outputs: "1101"
```

```js
// Using Recursion:
function decimalToBinaryRecursive(decimal) {
  if (decimal === 0) {
    return '0';
  }

  function convert(num) {
    if (num === 0) {
      return '';
    } else {
      return convert(Math.floor(num / 2)) + (num % 2).toString();
    }
  }

  return convert(decimal);
}

const decimalNumber = 13;
console.log(decimalToBinaryRecursive(decimalNumber)); // Outputs: "1101"
```