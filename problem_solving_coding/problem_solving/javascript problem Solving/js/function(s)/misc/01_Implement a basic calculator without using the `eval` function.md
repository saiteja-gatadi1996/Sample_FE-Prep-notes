### We need at least +, -, x, %,

```js
function Calculator() {
  // logic 1: maintain a variable called value and mutate this value variable (ex: for add: function (){value = value + num})
  let value = 0;
  // logic 2: create Higher Order Function
  function method(callback) {
    return function (num) {
      value = callback(value, num);
      return this;
    };
  }
  return {
    add: method((value, num) => value + num),
    subtract: method((value, num) => value - num),
    multiply: method((value, num) => value * num),
    modulus: method((value, num) => value % num),
    result: () => value,
  };
}

// Usage
const calc = Calculator();
const res = calc.add(10).multiply(5).subtract(30).add(10).modulus(7).result();
console.log(res); // 2, because that is the remainder
```
