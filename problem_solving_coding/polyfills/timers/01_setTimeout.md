### Implement a custom function similar to `SetTimeout` without using native `setTimeout` or `setInterval` functions\*\* using Web workers or requestAnimationFrame

<strong>Approach Taken:</strong>

- requestAnimationFrame accepts the function as a param
- the passed function in the requestAnimationFrame will get its own timestamp which we use this with performance.now (startTime) with the delay passed while invocation (ex: timestamp - startTime >= delay)
- in the else condition we will be doing the same thing by invoking the requestAnimationFrame(func)
- if condition simply executes the callback
- for better understanding breakdown the code from the output point of view or invocation point of view ex: how do you call the function

```js
function customSetTimeout(callback, delay) {
  const startTime = performance.now();
  console.log('startTime', (startTime / 1000).toFixed(2), 's');
  function checkTime(timestamp) {
    if (timestamp - startTime >= delay) {
      const currentTime = performance.now();
      console.log('currentTime', (currentTime / 1000).toFixed(2), 's');
      const difference = currentTime - startTime;
      console.log('diff', (difference / 1000).toFixed(2), 's');
      callback();
    } else {
      requestAnimationFrame(checkTime);
    }
  }
  requestAnimationFrame(checkTime);
}

customSetTimeout(() => {
  console.log('Executed after delay');
}, 4000);
```
