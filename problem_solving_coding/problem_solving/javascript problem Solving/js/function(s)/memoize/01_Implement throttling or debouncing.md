## Throttling and Debouncing

**Throttling**

- A function doesn't get called often more than a specified interval, even if it's invoked multiple times.
- Ex: If you throttle a function to be called at most once every 300 ms, it will ignore any additional calls that happen before the 300 ms have passed.

```js
function updateLayout() {
  console.log('Updating layout...');
}

function throttle(func, limit) {
  //maintain a variable for mutation (ex: isThrottle = false)
  let isThrottle = false;
  // return another function with args
  return function (...args) {
    // check the variable is not true, if yes then mutate the variable to true,
    if (!isThrottle) {
      isThrottle = true;
      func.apply(this, args);
      setTimeout(() => {
        isThrottle = false;
      }, limit);
    }
  };
}

let isThrottled = throttle(updateLayout, 300);

window.addEventListener('resize', () => {
  isThrottled();
});
```


### With lastArgs

```js
// Define a throttle function which takes a function 'func' and a wait time 'wait' as arguments
function throttle(func, wait) {
  // Initialize 'waiting' flag to false, indicating if the function is currently throttled
  let waiting = false, 

      // Initialize 'lastArgs' to null, which will store the last arguments passed to the function
      lastArgs = null;

  // Return a new function that takes any number of arguments using the rest operator
  return function(...args) {

    // Check if the function is not currently throttled
    if (!waiting) {

      // Call the 'func' with the provided arguments
      func.apply(this, args);

      // Set 'waiting' to true, to throttle further calls
      waiting = true;
      
      // Define a timeout function
      let timeout = () => setTimeout(() => {

        // Reset 'waiting' to false after the wait time has passed
        waiting = false;

        // If there are any stored arguments in 'lastArgs'
        if (lastArgs) {

          // Call the 'func' with the last stored arguments
          func.apply(this, lastArgs);

          // Set 'waiting' to true again to continue throttling
          waiting = true;

          // Clear the stored arguments
          lastArgs = null;

          // Recurse to handle any additional stored calls
          timeout();
        }
      }, wait);

      // Call the timeout function to start the initial delay
      timeout();

    } else {
      // If the function is currently throttled, store the latest arguments
      lastArgs = args;
    }
  }
}

// Function invocation:

function handleResize() {
  console.log('Window resized:', new Date());
}

// Now, the handleResize function will only be called at most once every 2000 milliseconds (2 seconds)
const throttledResize = throttle(handleResize, 2000);

window.addEventListener('resize', throttledResize);
```
---

### Key Differences and Use Cases
#### 1. Handling Calls During Wait Time:

**With lastArgs:**

- If a call is made during the waiting period, the arguments of this last call are stored in lastArgs.
Once the waiting period is over, the stored call (with lastArgs) is executed.

- This ensures that the last call made during the wait period is not lost, which can be useful in scenarios where the latest state needs to be processed.

**Without lastArgs:**

- Any calls made during the waiting period are ignored.
- This is simpler but means some calls might be dropped, which is suitable for cases where it's acceptable to skip some intermediate calls (e.g., to reduce processing load).

--- 

#### 2. Use Cases:

**With lastArgs:**

- Useful when you need to ensure the function processes the latest state or arguments provided during the waiting period.

- **Example**: 
  - Updating UI components that depend on the latest user input but should not be updated too frequently.

- The version with **`lastArgs`** can lead to more frequent function executions if calls are continuously made during the wait period since it ensures the latest call is processed after each wait period.



**Without lastArgs:**


- Suitable when it's acceptable to ignore intermediate calls during the wait period.
- **Example**: 
  - Logging events or making API requests where it's fine to miss some intermediate state changes as long as calls are throttled.

- The simpler version without lastArgs **`reduces`** the number of function executions, potentially leading to better performance under heavy load.

- The simpler version may result in **`less`** consistent updates but simpler logic and potentially lower resource usage.


----

## Debouncing

- A function doesn't get called until after a specified amount of time has passed since it was last invoked.

- Ex: execute this function only if 300 milliseconds have passed without it being called


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Javascript Coding</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <h1>Hello Javascript</h1>
    <input type="text" id="searchInput" placeholder="Search here.." />
    <script src="index.js"></script>
  </body>
</html>
```

```js
// Debounce function
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, args);
    }, delay);
  };
}

// Function that performs the search
function searchQuery(query) {
  console.log(`Searching for: ${query}`);
}

// Create a debounced version of the search function
const debouncedSearch = debounce(searchQuery, 300);

// Function to attach event listeners after the page loads
const input = document.getElementById('searchInput');
input.addEventListener('input', function (event) {
  debouncedSearch(event.target.value);
});
```
