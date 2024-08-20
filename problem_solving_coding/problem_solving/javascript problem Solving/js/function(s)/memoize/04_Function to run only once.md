
### Function to run only once

- ***To ensure a JavaScript function runs only once, you can use a closure to create a private execution context. This method involves defining a function within another function, and then immediately executing it. This pattern is often referred to as an "Immediately Invoked Function Expression" (IIFE)***

```js
var addUniqueButton = (function() {
  var executed = false;
  return function() {
    if (!executed) {
      executed = true;

      // Create a new button element
      var button = document.createElement('button');
      button.innerHTML = 'Click Me';
      button.onclick = function() {
        alert('Button clicked!');
      };

      // Add the button to the body of the document
      document.body.appendChild(button);
    }
  };
})();

// Usage
addUniqueButton(); // This will add the button to the page
addUniqueButton(); // Subsequent calls will not add another button (so even if addUniqueButton() is called multiple times, only one button will be added to the page)
```
