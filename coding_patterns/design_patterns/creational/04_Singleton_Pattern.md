## SingleTon Design Pattern

- Restricts the instantiation of a class to ***one single instance***. 
- This is ***useful when exactly one object is needed*** to coordinate actions across the system. 
- The pattern <ins>***ensures that a class has only one instance***</ins> and provides a global point of access to that instance. 
- It is implemented by creating a class with a method that creates a new instance of the class if one doesn't exist. 
- If an instance already exists, it simply returns a reference to that object.

```js
// Traditional way

var Singleton = (function () {
  var instance;

  function createInstance() {
    var object = new Object('I am the instance');
    return object;
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

// Usage:
var instance1 = Singleton.getInstance();
var instance2 = Singleton.getInstance();

console.log(instance1 === instance2); // Output: true
```


---

```js
//ES6

class Singleton {
  static instance;

  constructor() {
    if (!Singleton.instance) {
      Singleton.instance = this;
    }
    return Singleton.instance;
  }

  // Example method
  sayHello() {
    console.log('Hello, I am the singleton instance.');
  }
}

// Usage:
const instance1 = new Singleton();
const instance2 = new Singleton();

instance1.sayHello(); // Output: Hello, I am the singleton instance.
console.log(instance1 === instance2); // Output: true
```

----


### Real-Time Example: Database Connection
- Ideally, your application should have a single database connection instance running throughout its lifecycle.

```JS
// Traditional way

var DatabaseConnection = (function() {
  var instance;

  function createInstance() {
    var object = new Object("Database connection instance");
    // Initialize connection...
    return object;
  }

  return {
    getInstance: function() {
      if (!instance) {
        instance = createInstance();
        console.log("Creating new instance");
      }
      return instance;
    }
  };
})();

// Usage:
var db1 = DatabaseConnection.getInstance(); // Creating new instance
var db2 = DatabaseConnection.getInstance();

console.log(db1 === db2);  // Output: true
```

----

```js
//ES6

class DatabaseConnection {
  static instance;

  constructor() {
    if (!DatabaseConnection.instance) {
      DatabaseConnection.instance = this;
      // Initialize connection...
      console.log("Creating new instance");
    }
    return DatabaseConnection.instance;
  }

  // Additional methods to interact with the database can be added here
}

// Usage:
const db1 = new DatabaseConnection(); // Creating new instance
const db2 = new DatabaseConnection();

console.log(db1 === db2);  // Output: true
```