## SOLID principles



- The `SOLID` principles <ins>**are a set of five**</ins> design guidelines 
- This will help developers create software that is easier to `understand`, `maintain`, and `extend`.
- can be applied in JavaScript development <ins>**to improve code quality and modularity**</ins>. 

#### 1. Single Responsibility Principle (SRP)

<ins>**Principle**:</ins> 
  - A class <ins>**should have one, and only one**</ins>, reason to change.

<ins>**Problem it solves**:</ins>  
  - SRP <ins>**reduces** the complexity of code</ins>, making it easier to maintain and less susceptible to bugs because changes in one part of the system are less likely to affect other parts.

```js
// Bad practice: 
// A class that handles both user data management and JSON serialization
class UserData {
    constructor(user) {
        this.user = user;
    }

    saveUser() {
        // Save the user data to a database
    }

    serializeUser() {
        return JSON.stringify(this.user);
    }
}

// Good practice: 
// Separate classes with single responsibilities
class UserData {
    constructor(user) {
        this.user = user;
    }

    saveUser() {
        // Save the user data to a database
    }
}

class UserSerializer {
    static serialize(user) {
        return JSON.stringify(user);
    }
}
```
----

#### 2. Open/Closed Principle (OCP)

<ins>**Principle**:</ins> 
  - Software entities should be open for extension, but closed for modification.  

<ins>**Problem it solves**:</ins>  
  -  This principle helps in <ins>managing future changes and new functionalities in an application **without altering existing code**</ins>, thus reducing the risk of introducing bugs.

```js
// Bad practice: A function that is modified every time a new shape is added
function drawShape(shape) {
    if (shape.type === 'circle') {
        drawCircle(shape.radius);
    } else if (shape.type === 'square') {
        drawSquare(shape.side);
    }
}

// Good practice: Use polymorphism to handle different shapes
class Shape {
    draw() {}
}

class Circle extends Shape {
    constructor(radius) {
        super();
        this.radius = radius;
    }

    draw() {
        drawCircle(this.radius);
    }
}

class Square extends Shape {
    constructor(side) {
        super();
        this.side = side;
    }

    draw() {
        drawSquare(this.side);
    }
}

function drawShape(shape) {
    shape.draw();
}
```
---

# <--- SAMPLE CONTENT ENDS --->
