## Range Generator function

**Approach Taken**

1. while invoking your rangeGenerator pass start and end values
2. perform a basic for loop with i=start ; i<=end, i++
3. yield i inside the for loop
4. these values are not straight forward so spread it and use forEach and log it

```js
function* rangeGenerator(start, end) {
  for (let i = start; i <= end; i++) {
    yield i;
  }
}

const range = rangeGenerator(1, 5);

const numbers = [...range].forEach((num) => console.log(num));
```
