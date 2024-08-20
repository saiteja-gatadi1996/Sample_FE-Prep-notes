## Promise.all

**Definition**: takes an `iterable of promises as input` and returns a `single Promise`. This returned promise fulfills `when all of the input's promises fulfill` (including when an empty iterable is passed), with an array of the fulfillment values. `It rejects when any of the input's promises rejects`, with this first rejection reason.

<strong>Approach Taken:</strong>

1. arrayOfPromises is passed as a param and do a forEach (ex: promisesArr.forEach(promise))
2. forEach promise do Promise.resolve(promise) and then do the following .then and .catch
3. as Promise.all fulfills if all are fulfilled promise values, so we have to maintain an dummyArray (ex: results) and for each iteration dummyArray[index]= callbackValue (ex: results[index] = value) inside the .then block
4. also maintain a resolvedCount 
5. so when resolvedCount.length is equal to the passed promisesArray.length then resolve(results) with Aggregate Error saying that all the promises are rejected.

```js
if (typeof Promise.all !== 'function') {
  Promise.all = function (promises) {
    return new Promise((resolve, reject) => {
      if (!Array.isArray(promises)) {
        return reject(new TypeError('The input should be an array'));
      }

      let resolvedCount = 0;
      const results = new Array(promises.length);

      if (promises.length === 0) {
        // if the condition is true, it means there are no promises to process,
        // so the Promise.all promise is resolved immediately with an empty results array, and the function returns early.
        return resolve(results);
      }

      promises.forEach((promise, index) => {
        Promise.resolve(promise)
          .then((value) => {
            resolvedCount++;
            results[index] = value;

            if (resolvedCount === promises.length) {
              resolve(results);
            }
          })
          .catch((error) => {
            reject(error);
          });
      });
    });
  };
}

// Usage example
const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3])
  .then((values) => console.log(values)) // Logs: [1, 2, 3]
  .catch((error) => console.error(error));

//Example 2, empty array of promises
const urls = []; // In this case, the URLs array is empty
Promise.all(urls.map((url) => fetch(url)))
  .then((results) => console.log(results)) // Logs an empty array []
  .catch((error) => console.error(error));
```
