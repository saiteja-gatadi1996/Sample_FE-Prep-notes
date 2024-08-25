#### 1. What is a potential pitfall with using typeof bar === "object" to determine if bar is an object? How can this pitfall be avoided?

- In Javascript, the `Arrays` are technically objects,

```js
type of [] === "object" //  true;
```

- the value `null` is considered an object type in Javascript.

```js
typeof null === 'object' //true
```

- While functions are callable objects in javascript, This means that while functions can be invoked, they still have properties and methods like any other object. (Ex: call, bind methods)

```js
typeof function () {} // "function"
```

```js
typeof function () {} === 'object' // false
```

##### There are three ways to avoid these pitfalls

###### 1. Basic Object Check:

```js
if (bar !== null && typeof bar === 'object' && !(bar instanceof Array)) {
  // bar is an object
}
```

###### 2. Object.prototype.toString:

```js
if(Object.prototype.toString.call(bar) === "[object Object]")

// bar is an object
```

###### 3. constructor:

```js
if (bar && bar.constructor === Object) {
  // bar is an plain object
}
```

##### Problems with using constructor property:

<strong>Inheritance:</strong> If you're working with objects that might have been created through custom constructors or classes then they will not match the basic `Object` constructor. <strong>if you have a class `Foo` an instance of `Foo` would fail the above check even though it's an object.</strong>

<strong>Modified Constructor:</strong> The constructor property can be changed, making it a potentially unreliable way to check for an object's type.

<strong>Objects from different Windows:</strong> If you are working in a browser env with multiple frames or windows, objects from one frame will have a different constructor than objects from another frame.

##### Examples:

```js
// Plain Objects
let obj1 = {}
console.log(obj1.constructor === Object) // true

let obj2 = new Object()
console.log(obj2.constructor === Object) // true
```

```js
// Arrays
let arr = []
console.log(arr.constructor === Object) // false
```

```js
function MyClass() {}
let myInstance = new MyClass()
console.log(myInstance.constructor === Object) // false
```

```js
let str = new String('hello')
console.log(str.constructor === Object) // false

let num = new Number(10)
console.log(num.constructor === Object) // false
```

---

```js
// Plain Objects
let obj1 = {}
console.log(Object.prototype.toString.call(obj1)) // "[object Object]"

let obj2 = new Object()
console.log(Object.prototype.toString.call(obj2)) // "[object Object]"
```

```js
// Arrays
let arr = []
console.log(Object.prototype.toString.call(arr)) // "[object Array]"
```

```js
function MyClass() {}
let myInstance = new MyClass()
console.log(Object.prototype.toString.call(myInstance)) // "[object Object]"
```

```js
let str = new String('hello')
console.log(Object.prototype.toString.call(str)) // "[object String]"

let num = new Number(10)
console.log(Object.prototype.toString.call(num)) // "[object Number]"
```

---

#### 2. What will the code below output to the console and why?

```js
;(function () {
  var a = (b = 3)
})()

console.log('a defined? ' + (typeof a !== 'undefined'))
console.log('b defined? ' + (typeof b !== 'undefined'))
```

<details>
<summary>View Answer</summary>

false
true

```js
typeof a // "undefined"
typeof b // "number"
```

</details>

---

#### 3.Output ?

```js
var myObject = {
  foo: 'bar',
  func: function () {
    var self = this
    console.log('outer func:  this.foo = ' + this.foo)
    console.log('outer func:  self.foo = ' + self.foo)(function () {
      console.log('inner func:  this.foo = ' + this.foo)
      console.log('inner func:  self.foo = ' + self.foo)
    })()
  },
}
myObject.func()
```

<details>
<summary>View Answer</summary>

```js
outer func:  this.foo = bar
outer func:  self.foo = bar
inner func:  this.foo = undefined
inner func:  self.foo = bar
```

##### In the outer function, both this and self refer to myObject and therefore both can properly reference and access foo.

##### In the inner function, though, this no longer refers to myObject. As a result, this.foo is undefined in the inner function, whereas the reference to the local variable self remains in scope and is accessible there.

</details>

---

# <--- SAMPLE CONTENT ENDS --->
