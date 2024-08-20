## Add comma to the number

**Approach Taken**:

1. numberParam.toLocaleString('en-US')

```js
function addComma(num) {
  // if your provided argument has some decimal part then we split according the dot operator and add the core logic to it and then concat with next half of the splitted part(Ex: parts[0] is before the dot operator and parts[1] is supposed to be the after dot operator, we are concatenating both of them)
  if (Math.floor(num) !== num) {
    // If the number has a decimal part
    let parts = num.toString().split('.');
    return parseInt(parts[0]).toLocaleString('en-US') + '.' + parseInt(parts[1]);
  }
  // this is the core logic, which runs for every non-decimal part of the number
  return num.toLocaleString('en-US');
}

console.log(addComma(1)); // '1'
console.log(addComma(1000)); // '1,000'
console.log(addComma(-12345678)); // '-12,345,678'
console.log(addComma(12345678.12345)); // '12,345,678.12345'
```
