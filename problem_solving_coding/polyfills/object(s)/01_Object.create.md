## Object.create:

**Definition:** 
- Is used to **<ins>create a new object using an existing object</ins>** as the **`prototype`** of the newly created object.

```js
//Syntax
Object.create(proto, propertiesObject);
```

<strong>Approach Taken:</strong>


```js
//core logic
yourFunction.prototype = proto;
```

```js
Object.prototype.customCreate = function (proto) {
    if (proto === null || typeof proto !== 'object') {
      throw new Error('Argument must be the object, or null');
    }
    //empty function
    function F() {}
    //prototype chaining with proto as the value
    F.prototype = proto;
    //return the new Function
    return new F();
  };

const obj1 = {
  key: 1,
  sayHello() {
    return 'Hello';
  },
};

const newObj1 = Object.customCreate(obj1);
console.log('newObj1', newObj1);
console.log('newObj1 Key', newObj1.key);
console.log('newObj1 sayHello', newObj1.sayHello());
```

  ![alt text](/problem_solving_coding/polyfills/0_imagesUsed/Object_Create_1.png)
  ![alt text](/problem_solving_coding/polyfills/0_imagesUsed/Object_Create_2.png)

### new keyword usage:

- The `new` keyword is used to create an instance of function F. 
- Because **`F`** is a constructor function, using **`new F()`** ***creates a `new` object***.