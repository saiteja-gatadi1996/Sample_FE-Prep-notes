## Custom implementation of `instanceof` operator

**Approach Taken**

1. your function accepts two params, one is `instanceObj` and second is `constructor class/functions`
2. basic level of checks (if your typeof constructorFunc is not function or constructorFunc.prototype === undefined) directly return false
3. By doing `Object.getPrototypeOf(objInstance)` we will get proto, we can store it in variable (ex: let proto = Object.getPrototype(objInstance))
4. now perform a `while loop on this stored proto variable` (ex: while(proto!==null))
5. core logic is: `if(proto === constructorFunc.prototype) return true`
6. inside the while loop we are mutating the proto property by deep level nesting of prototype (ex; proto = Object.getPrototype(proto))

```js
function myInstanceOf(obj, constructor) {
  // If the constructor isn't a function or the prototype isn't defined, return false
  if (
    typeof constructor !== 'function' ||
    constructor.prototype === undefined
  ) {
    return false;
  }

  // Loop through the prototype chain of the object
  let proto = Object.getPrototypeOf(obj);
  while (proto !== null) {
    if (proto === constructor.prototype) {
      return true; // Found the constructor's prototype in the prototype chain
    }
    //checks inside prototype chain and goes back to while loop
    proto = Object.getPrototypeOf(proto);
  }

  return false; // Didn't find the constructor's prototype in the prototype chain
}

// Test cases
class A {}
class B extends A {}

const b = new B();
console.log(myInstanceOf(b, B)); // true
console.log(myInstanceOf(b, A)); // true
console.log(myInstanceOf(b, Object)); // true

function C() {}
console.log(myInstanceOf(b, C)); // false
C.prototype = B.prototype;
console.log(myInstanceOf(b, C)); // true
C.prototype = {};
console.log(myInstanceOf(b, C)); // false
```
