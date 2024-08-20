## 1.
```js
//BASIC Variable Declaration
let isDone: boolean = false;
const name: string = "John Doe";
var age: number = 30;
```

## 2.

```js
//Arrays Declaration
let list: number[] = [1, 2, 3];
let genericList: Array<number> = [4, 5, 6];
```

## 3.

```js
let x: [string, number];
x = ["hello", 10]; // OK
// x = [10, "hello"]; // Error
```

### 4. Enums allow you to define a set of named constants, either numeric or string-based.
```js
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

## 5.
```js
//When you're unsure of the type of a variable (similar to any), but want type safety, use unknown.
let notSure: unknown = 4;
notSure = "maybe a string instead";
```

## 6.

```js
//Use `any` for variables where you do not want TypeScript's type checking to apply. This is essentially opting out of type safety for that variable.

let looselyTyped: any = 4;
looselyTyped.ifItExists(); // OK, ifItExists might exist at runtime
```


## 7.

```js
//Used for functions that do not return a value.
function warnUser(): void {
    console.log("This is my warning message");
}
```

## 8.

```js
//TypeScript has both undefined and null as types.
let u: undefined = undefined;
let n: null = null;
```

## 9.

```js
// The never type represents the type of values that never occur. For functions that throw an exception or never return.
function error(message: string): never {
    throw new Error(message);
}
```

## 10.

```js
//object is a type that represents the non-primitive type.
declare function create(o: object | null): void;
create({ prop: 0 }); // OK
create(null); // OK
```

## 11.

```js
// Type assertions are a way to tell the compiler "trust me, I know what I'm doing." 
// They're like a type cast in other languages but perform no special checking or restructuring of data.
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length;
// Or
let strLengthAlternative: number = (<string>someValue).length;
```

## 12. Interfaces

```js
interface LabelledValue {
    label: string;
}

function printLabel(labelledObj: LabelledValue) {
    console.log(labelledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

-----

## 13. Diff between Interface, Type Alias in typescript
- are used to describe the shape of an object, but they have some differences in usage and capabilities:
### Interfaces:

#### 1. Extensibility: 
  - Interfaces are easily extendable. 
  - You can merge multiple declarations of the same interface to augment or extend its properties.
```js
// Interface Example
interface User {
  name: string;
  age: number;
}

// Extending the Interface
interface User {
  address?: string;
}

const user: User = { name: 'Alice', age: 30, address: '123 Main St' };
```

#### 2. Inheritance: 
  - Interfaces can extend other interfaces and classes using extends.


```js
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}

const employee: Employee = { name: 'Bob', employeeId: 123 };
```


### Type Aliases:

#### 1. Alias for Various Types: 
- Can represent any kind of type (including primitives, unions, intersections, and tuples), 
- whereas interfaces are primarily designed to represent object shapes.
```js
// Union Example
type StringOrNumber = string | number;

const value: StringOrNumber = 'hello';
const anotherValue: StringOrNumber = 42;

// Tuple Example
type Point = [number, number];

const point: Point = [5, 10];
```

#### 2. Composing Types:
- Type aliases allow you to use advanced features like intersection types to combine multiple types.

```js
// Intersection Example
type Draggable = {
  drag: () => void;
};

type Resizable = {
  resize: () => void;
};

type UIElement = Draggable & Resizable;

const uiElement: UIElement = {
  drag: () => console.log('Dragging'),
  resize: () => console.log('Resizing')
};
```

#### Unlike interfaces, type aliases cannot be merged or extended directly in the way that interfaces can.


### Summary:
- Interfaces are preferable when defining the shape of objects or contracts that need to be extended or implemented by other classes.
- Type Aliases are more versatile and can describe more complex types, such as unions and intersections. They are also useful for giving a name to any existing type.

----

