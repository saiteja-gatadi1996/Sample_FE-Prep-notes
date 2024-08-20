## Object.assign()

**Definition**: copies from one or more source objects to a target object. It returns the modified target object

```js
//syntax:
Object.assign(target, source1, source2, /* …, */ sourceN);
```

<strong>Approach Taken:</strong>

- customAssign function takes two arguments, one is target and the object that user declares
- while passing as params we would do some manipulating like we use spread operator for user provided object so that we can use for looping
- just convert your target which is {} into Object(target) ex: target = Object(target)
- sources.forEach and you will get the each and every object and do the Object.keys(passSourceObject) which is nothing but an array so do another forEach and you can access the key of it and save your target[key] with already provided source[key]

```js
if (typeof Object.customAssign !== 'function') {
  Object.customAssign = function (target, ...sources) {
    // sources will be part of the array and can used for looping ex: [{a:1}]
    if (target === null || target === undefined) {
      throw new TypeError('Cannot convert undefined or null to object');
    }

    // converting any non-object if provided to object at the end (so target has to be Object at the end)
    target = Object(target);

    sources.forEach((source) => {
      // source is an object ex: {a:1}
      if (source !== null && source !== undefined) {
        Object.keys(source).forEach((key) => {
          // It checks if the source object has its own property (not inherited) with the given key, and if so, it assigns that property and value to the target object.
          if (Object.prototype.hasOwnProperty.call(source, key)) {
            // whatever is already provided as part of args will be stored in the target object ex: target[key]
            target[key] = source[key];
          }
        });
      }
    });

    return target;
  };
}

// Example usage
const obj1 = { a: 1 };
const copyObj1 = Object.customAssign({}, obj1);
copyObj1.a = 2;

console.log('copyObj1', copyObj1); //copyObj1 {a: 2}
console.log('obj1', obj1); // obj1 {a:1}
```
