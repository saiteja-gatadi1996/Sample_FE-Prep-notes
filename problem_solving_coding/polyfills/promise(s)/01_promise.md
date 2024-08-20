## Promise:

#### Implement a basic promise with `resolve`, `reject`, `then`, and `catch`.

<strong>Approach Taken:</strong>

```javascript
const PENDING = 'pending';
const FULFILLED = 'fulfilled';
const REJECTED = 'rejected';

function CustomPromise(executor) {
  var state = PENDING;
  var value = null;
  var handlers = [];

  function settle(finalState, finalValue) {
    setTimeout(() => {
      if (state !== PENDING) return;

      state = finalState;
      value = finalValue;
      //invoking each of these waiting callbacks with the settled value or error. The handle function checks the state of the promise and accordingly calls either the onFulfilled or onRejected function.
      handlers.forEach(handle);
      //Once the promise is settled and all waiting callbacks are called, the handlers array isn't needed anymore. Setting it to null:
      handlers = null;
    }, 0);
  }

  function resolve(result) {
    settle(FULFILLED, result);
  }

  function reject(error) {
    settle(REJECTED, error);
  }

  function handle(handler) {
    if (state === PENDING) {
      //storing the callback handler if the promise is still in a PENDING state.
      handlers.push(handler);
      return;
    }
    if (state === FULFILLED && typeof handler.onFulfilled === 'function') {
      //If the promise is fulfilled:
      handler.onFulfilled(value);
    }
    if (state === REJECTED && typeof handler.onRejected === 'function') {
      //If the promise is rejected
      handler.onRejected(value);
    }
  }

  this.then = function (onFulfilled, onRejected) {
    //The method itself returns a new promise. This is what enables promise chaining, allowing you to execute asynchronous operations in sequence.
    return new CustomPromise((resolveNext, rejectNext) => {
      handle({
        //If the promise is already resolved (fulfilled),
        //Any return value from onFulfilled will be used to resolve the new promise (resolveNext(value)).
        onFulfilled: (val) => {
          try {
            resolveNext(onFulfilled(val));
          } catch (err) {
            rejectNext(err);
          }
        },
        //If there's an error while executing the onFulfilled function, the new promise is rejected with this error (rejectNext(err)).
        onRejected: (err) => {
          try {
            //If onRejected has been provided, it will call that function with the error (err) and attempt to resolve the returned value from that function as the next promise in the chain (resolveNext(onRejected(err))).
            onRejected ? resolveNext(onRejected(err)) : rejectNext(err);
          } catch (ex) {
            rejectNext(ex);
          }
        },
      });
    });
  };

  this.catch = function (onRejected) {
    return this.then(null, onRejected);
  };

  try {
    executor(resolve, reject);
  } catch (error) {
    reject(error);
  }
}

CustomPromise.resolve = (value) => new CustomPromise((fulfil) => fulfil(value));
CustomPromise.reject = (error) =>
  new CustomPromise((res, reject) => reject(error));

// Scenario 1: Only using `then` with both onFulfilled and onRejected.
let successfulPromise = CustomPromise.resolve('Success');
let failedPromise = CustomPromise.reject('Failed');

successfulPromise.then(
  (result) => console.log('Success result:', result),
  (error) => console.log('Error in success promise:', error)
);

failedPromise.then(
  (result) => console.log('Result from failed promise:', result),
  (error) => console.log('Failed error:', error)
);

// Output:
// Success result: Success
// Failed error: Failed

//Scenario 2: Using `then` for success and `catch` for errors.
successfulPromise
  .then((result) => console.log('2nd Success result:', result))
  .catch((error) => console.log('2nd Error in success promise:', error));

failedPromise
  .then((result) => console.log('2nd Result from failed promise:', result))
  .catch((error) => console.log('2nd Failed error:', error));

// Output:
// Success result: Success
// Failed error: Failed

// Scenario 3: Transforming errors with then.

failedPromise
  .then(
    null, // We're not handling success here
    (error) => 'Handled error: ' + error
  )
  .then((result) => console.log('Transformed result:', result))
  .catch((error) => console.log('Error after transformation:', error));

// Output:
// Transformed result: Handled error: Failed

//Example 2: With onRejected Provided:
const myFailedPromise = new CustomPromise((resolve, reject) => {
  reject('Something went wrong');
});

myFailedPromise
  .then(
    null, // We don't provide onFulfilled here
    (error) => 'Recovered from: ' + error
  )
  .then(
    (value) => console.log(value),
    (error) => console.log('Still an error:', error)
  );

// Output: "Recovered from: Something went wrong"

//Example 3: Without onRejected function

myFailedPromise
  .then(
    null // No handlers provided
  )
  .then(
    (value) => console.log(value),
    (error) => console.log('Error caught:', error)
  );

// Output: "Error caught: Something went wrong"
```
