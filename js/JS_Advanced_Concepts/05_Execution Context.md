### 5. Execution Context:

- Whenever our code runs in Javascript, <ins>**it is run inside an Execution Context**</ins>. (This might be of `Global` or `Inside function` that we call).
  <br/>
- The base execution context that runs is called <ins>**Global Execution Context**</ins>
  <br/>

- `Initially` our Javascript engine is going to create a <ins>**_global execution context_**</ins> <ins>_and on top of that we start adding the functions (ex: sayMyName()) in our case_</ins>.
  <br/>

- And as the execution context(s) gets `popped` off, the last thing that remains is `Global Execution context`.
  <br/>
- And <ins>when the final line of our code runs</ins> and we're done with the JS engine, this `GEC` is going to be `popped` off.
  <br/>

- Whenever the Javascript engine sees `those brackets () which are used for invoking the function`, **_it's going to run a function and create execution context_**.
  <br/>

- So first thing it does, <ins>**it creates the execution context sayMyName() and adds this execution context onto the Call Stack**</ins>
  <br/>

- And then it tries to run the function and **sees that this function is calling another function**. **_So a new execution context is now created_** for findMyName
  <br/>

- Now the Javascript engine comes across another function called printName for which it creates a new execution context.
  <br/>

- the Last function after creating its own execution context (printName()), it returns the string output and this gets returned to findMyName function and this gets returned to sayMyName function and then eventually call stack gets popped off and we return onto the screen the string output.
  <br/>

![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Execution_Context-1.png)


![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Execution_Context-2.png)

##### <ins>Global Execution Context:</ins>

- <ins>After creating GEC, JS engines creates two things.</ins>
- First thing is **_global object_**, and the other thing is **_this keyword_** in Javascript.


![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Execution_Context-3.png)

**_Global Object means Window_**

![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Execution_Context-4.png)

- We **can** **add** `variables/functions` and many more to our `global object` (e.g. let a = "saiteja" will be part of window.a)

- So the above is called **_creation phase_**
- The second phase is called as **_execution phase._** (Where you actually run your code)

##### <ins>Note:</ins> If you're using Node, the global object wouldn't be window, instead it would be called `global`

---

## The execution context has two main phases: the creation phase and the execution phase.

#### <ins>Creation Phase:</ins>

- During the creation phase, the JavaScript engine performs several steps <ins>**_before executing the code_**</ins>:
  <br/>

##### <ins>Following are the steps that are being performed:</ins>

1. Creates the <ins>**_Global Execution Context (GEC) for the entire script_**</ins> or a <ins>_Function Execution Context (FEC) for each function call_</ins>.
   <br/>

2. `Hoists` <ins>**_function declarations and variable declarations (var) to the top_** of their respective contexts.</ins>

   - Note that **function expressions are <ins>not hoisted**</ins>.
     <br/>

3. **Initializes** **memory** space for `variables` and `functions`. Functions are **fully** initialized, <ins>**_but variables are initially set to undefined_**</ins>.
   <br/>

4. Determines the value of `this` <ins>_in the current execution context_.</ins>

   <br/>

##### Example: <ins>Creation Phase</ins>

```js
console.log(greeting);
var greeting = 'Hello, world!';
```

##### <ins>What happens during the creation phase:</ins>

- The variable `greeting` is <ins>_hoisted to the top of its execution context_</ins>. Initially, it's set to `undefined`.
  <br/>

- When console.log(greeting) is executed in the execution phase, **it logs undefined, not "Hello, world!"**, because the assignment happens **after** the console.log statement.

---

#### <ins>Execution Phase</ins>:

- **After** the creation phase, the **execution phase begins**.
  - This is where the **_JavaScript engine <ins>executes the code line by line_**</ins>

1. **Assigns** values to `variables` and executes functions.
2. **Interprets** and executes statements and expressions written in the code.
3. **Updates** the Call Stack and manages function calls and returns.

##### Example: <ins>Execution Phase</ins>

```js
var status = 'Ready';
function displayStatus() {
  console.log(status);
  var status = 'Busy';
  console.log(status);
}

displayStatus();
```

- During the creation phase of displayStatus(), the local variable status is hoisted and initialized to undefined.
- In the **execution phase**, the `first` console.log(status) logs `undefined` because it executes before status is assigned "Busy".
- After the local status variable is assigned "Busy", the **second** console.log(status) logs **"Busy".**

---

##### A good example to illustrate execution contexts, hoisting, and the execution phases is <ins>by mixing function declarations and expressions with conditional statements</ins>:

```js
function decideAction() {
  if (action() === 'Work') {
    console.log('Working!');
  } else {
    console.log('Resting!');
  }

  function action() {
    return 'Work';
  }

  var action = function () {
    return 'Rest';
  };
}

decideAction();

//Output: Working!
```

#### Explanation:

1. During the **creation** phase of decideAction(), the **_function declaration action() is hoisted and initialized_**, and the variable action is hoisted but initialized to **undefined**.
2. The **function declaration action() is overwritten by the function expression assigned to action** due to variable hoisting and the way JavaScript treats function declarations and variable assignments.
3. However, the <ins></ins>**_if condition executes before the variable action is assigned the function expression_**.
4. <ins>Thus, it calls the hoisted function declaration action() which returns "Work".</ins>
