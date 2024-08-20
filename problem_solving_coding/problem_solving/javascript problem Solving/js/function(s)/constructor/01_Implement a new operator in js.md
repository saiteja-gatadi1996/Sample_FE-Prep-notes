## new operator custom implementation

**Approach Taken**

1. newOperator accepts the constructor and rest of the args
2. Step 1 to create an object with the constructor's prototype (ex: Object.create(constructor.prototype))
3. Step 2 to call the constructor with the created object and the args (ex: ConstructorParam.call(createdObj, ...args))
4. if that stored result is object then return the result else return obj
   (ex: return result && typeof result === 'object' ? result, obj)

```js
function newOperator(Constructor, ...args) {
  // Step 1: Create a new object with the constructor's prototype
  const obj = Object.create(Constructor.prototype);

  // Step 2: Apply the constructor to the new object using call() instead of apply()
  const result = Constructor.call(obj, ...args);

  // Step 3: Return the object, unless the constructor returns an object
  return result && typeof result === 'object' ? result : obj;
}

// Example usage:
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
};

const john = newOperator(Person, 'John', 30);
john.sayHello(); // Output: Hello, my name is John and I am 30 years old.
```
