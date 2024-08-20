# JavaScript:

## 1. How JavaScript works?

JavaScript is a single-threaded programming language, which means it has a single Call Stack. Therefore, it can do one thing at a time. The Call Stack is a data structure which records basically where in the program we are. If we step into a function, we put it on the top of the stack. If we return from a function, we pop off the top of the stack.

## 2. Event bubbling and capturing are two ways of event propagation in the HTML DOM API, when an event occurs in an element inside another element, and both elements have registered a handle for that event. The event propagation mode determines in which order the elements receive the event.

With bubbling, the event is first captured and handled by the innermost element and then propagated to outer elements.
With capturing, the event is first captured by the outermost element and propagated to the inner elements.

## 3.

![alt text](https://user-images.githubusercontent.com/42731246/142735150-21d18fcc-2df0-4ed2-a85a-b849270b3240.png)

## 4. Event loop?

This monitors the Call Stack and the Call-back Queue. If the Call Stack is empty, it will take the first event from the queue and will push it to the Call Stack, which effectively runs it.

## 5. Function declaration vs Function expression

This is due to hoisting.

Note: Only Variable declarations or functional declarations are moved to top.

![image](https://user-images.githubusercontent.com/42731246/152095426-c7074419-f6d3-4067-8964-2a480a6d032c.png)

![image](https://user-images.githubusercontent.com/42731246/152095693-ac9e3eae-db1c-4265-a04e-0429b560ee5f.png)

Data flow when a function gets called inside another function
![alt text](https://user-images.githubusercontent.com/42731246/142735165-cdbae898-cf1d-4185-8964-80ca0066903d.png)

## 6. return keyword immediately exits without executing the next line

Ex: if console.log(line 101, line 104) are written after return keyword (return retirement or return -1), you don’t see your log statement getting printed.

![alt text](https://user-images.githubusercontent.com/42731246/142735172-e9045505-a7ec-4ebe-ac35-6b67ba865829.png)

## 7. Three different types of functions

![alt text](https://user-images.githubusercontent.com/42731246/142735186-86a3c555-d324-4ff6-b089-54e2c695d43c.png)

## 8. params() vs args()

params: while function declaration or initialization we pass params
args: while calling the function we pass args

![alt text](https://user-images.githubusercontent.com/42731246/142735206-29838d26-0864-480b-bf09-d1c8e245e78a.png)

## 9. this keyword example

![alt text](https://user-images.githubusercontent.com/42731246/142735231-0b0bd898-246e-4344-95c8-6bf6ededf9fe.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735233-a6a92525-1513-4c72-bcf6-616cde83ad6e.png)

## 10. Examples of Objects

![alt text](https://user-images.githubusercontent.com/42731246/142735245-43113dd4-270f-4ab6-accb-aa3dcb43298f.png)

## 11. break vs continue

break will terminate the loop, continue will exits from the current iteration not from the loop

Ex: if(typeof teja[i] !==string) continue
this will only print numbers (reason: number or array is not a string and it exits the iteration and move it)

if(typeof teja[i] ==string) break
whenever a string is found, it will terminate the entire loop.

## 12. Loops in Loops

![alt text](https://user-images.githubusercontent.com/42731246/142735259-a76fef73-1be2-4b55-8378-5b07f766acc0.png)

## 13. What is DOM ?

DOM gets automatically created when html page loads and it is stored in a tree structure like below. In this tree, each html element is the object.

![alt text](https://user-images.githubusercontent.com/42731246/142735264-4918d871-e2cd-4cce-ba43-774ea8e9bba0.png)

## 14. DOM ! = javascript

JavaScript is actually just a dialect of the ECMAScript specification,

![alt text](https://user-images.githubusercontent.com/42731246/142735281-ebc62d8b-c08f-4126-bd22-4bd4dc48dd66.png)

## 15. First Class Functions

![alt text](https://user-images.githubusercontent.com/42731246/142735287-adc5ea06-72a9-48c2-af2a-3cd797dc0662.png)

## 16. Dynamically Typed Language

![alt text](https://user-images.githubusercontent.com/42731246/142735297-1b985863-0b33-4655-bd41-be43ddb53516.png)

## 17. Non Blocking Event Loop

![alt text](https://user-images.githubusercontent.com/42731246/142735301-f0478f0d-3559-4fed-a9a8-2fb414f52222.png)

## 18. JS Engine

![alt text](https://user-images.githubusercontent.com/42731246/142735305-b1bf0eed-4d7f-43da-91ac-bbde8084a9ea.png)

## 19. Javascript Engine now uses JIT Compilation

![alt text](https://user-images.githubusercontent.com/42731246/142735311-65e4dac6-89f7-4948-9a7a-3fe3619d4274.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735315-e22bd241-f1c4-48cc-b648-a4af644cd53f.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735318-4938044b-4e57-41e4-971d-9e352a7bdcb3.png)

## 20. Execution Context

Our code was just finished compiling. So, the code is now ready to be executed. What happens then, is that a so-called global execution context is created for the top-level code. And top-level code is basically code that is not inside any function. So again, in the beginning only the code that is outside of functions will be executed. Functions should only be executed when they are called. But the code inside the functions, will only be executed when the functions are called.

An execution context is basically an environment in which a piece of JavaScript is executed that stores all the necessary information for some code to be executed. Such as local variables or arguments passed into a function. So, JavaScript code always runs inside an execution context. Now, in any JavaScript project, no matter how large it is, there is only ever one global execution context. It's always there as the default context, and its where top-level code will execute. Okay, and once this first code, so the top-level of code is finished, functions finally start to execute as well.

And here is how that works. For each and every function call, execution context will be created containing all the information that is necessary to run exactly that function. And the same goes for methods, of course, because they're simply functions attached to objects. Anyway, all these execution contexts together, make up the call stack that I mentioned before. But more on that in a second. Now, when all functions are done executing, the engine will basically keep waiting for callback functions to arrive so that it can execute these.

And the first thing that's inside any execution context is a so-called variable environment. In this environment, all our variables and function declarations are stored, and there is also a special arguments object.

This object contains, as the name says all the arguments that were passed into the function that the current execution context belongs to.
Because remember each function gets its own execution context as soon as the function is called. So basically, all the variables that are somehow declared inside a function, will end up in its variable environment.

However, a function can also access variables outside of the function. And this works because of something called the scope chain. The scope chain basically consists of references to variables that are located outside of the current function. And to keep track of the scope chain, it is stored in each execution context. Finally, each context also gets a special variable called this keyword.

Now, the content of the execution context, so variable environment, scope chain and this keyword is generated in a so-called creation phase which happens right before execution. Execution contexts belonging to arrow functions, do not get their own arguments keyword, nor do they get this keyword, So, basically arrow functions don't have the arguments object and this keyword.

Instead, they can use the arguments object, and this keyword from their closest regular function parent. We will get one global execution context one for each function. So one for the first function, and one for the second function. In the global context, we have the name variable declaration, the first and second function declarations, as well as the X variable declaration.

For the functions, the variable environment will literally contain all the code of a particular function. But now imagine there are hundreds of execution contexts for hundreds of functions. How will the engine keep track of the order in which functions we're called? And how will it know where it currently is in the execution? Well, that's where the call stack finally comes in. And remember that the call stack, together with the memory heap, makes up the JavaScript engine itself.

Call stack? Well, it's basically a place where execution contexts get stacked on top of each other, in order to keep track of where we are in the program’s execution. So, the execution context that is on top of the stack, is the one that is currently running. And when it's finished running, it will be removed from the stack, and execution will go back to the previous execution context. So, once the code is compiled, top-level code will start execution and global execution context will be created for the top-level of code

So, this is where all the code outside of any function will be executed. And what happens with this execution context? It will be put in the call stack. And since this context is now at the top of the stack, it is the one where the code is currently being executed.

JavaScript has only one thread of execution. And so, it can only do one thing at a time. Okay? Never forget that. Now, moving to the next line, we have a return statement meaning that the function will finish its execution. So, what does that mean for the call stack? Well, it basically means that the function's execution context, will be popped off the stack and disappear from the computer's memory. At least that's what you need to know for now because actually the popped off execution context might keep living in memory.
Anyway, what happens next, is that the previous execution context, will now be back to being the active execution context again.

You start to see how the call stack really keeps track of the order of execution here. Without the call stack, how would the engine know which function was being executed before? It wouldn't know where to go back to, right? And that's the beauty of the call stack. It makes this process almost effortless. and then finally this first function also returns. And so here the same as before happens. So, the current execution context gets popped off the stack, and the previous context is now the current context where code is executed.

In this case, we're back to the global execution context and the line of code where the first function was first called. So here, the return value is finally assigned to X and the execution is finished. Now the program will now actually stay in this state for forever until it is eventually really finished. And that only happens like when we close the browser tab, or the browser window. Only when the program is really finished like this, is when the global execution context is also popped off the stack. Code runs inside of execution contexts that are in the stack.

![alt text](https://user-images.githubusercontent.com/42731246/142735407-76524f93-46fc-4c82-8eeb-3d77b01b17e4.png)

## 21. Scope Concepts

![alt text](https://user-images.githubusercontent.com/42731246/142735429-6afca4d1-20af-4324-a08b-71144e9851af.png)

## 22. Different types of scopes

![alt text](https://user-images.githubusercontent.com/42731246/142735437-c299fb85-d39c-4e1d-bf67-435cb8c9aaae.png)

## 23. Example of Scope Chain in code

![alt text](https://user-images.githubusercontent.com/42731246/142735444-05b7a423-2103-4181-b0b4-cc1801a36b03.png)

## 24. Scope Chain vs Callback (Very Imp)

![alt text](https://user-images.githubusercontent.com/42731246/142735448-a29ad4c3-7f14-4950-8ac9-88d9cae8f408.png)

## 25. Points to remember for Scoping

![alt text](https://user-images.githubusercontent.com/42731246/142735455-843826b7-c481-4b8f-85aa-f64527207581.png)

## 26. let and const variables are in Temporal Dead Zone (can’t be accessible before they are initialization)

![alt text](https://user-images.githubusercontent.com/42731246/142735484-ae0327a2-f9f2-4ee4-9007-499e66476b6f.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735489-2a816f98-0139-4a5d-b091-664f089c90ce.png)

## 27. Hoisting in Javascript:

![alt text](https://user-images.githubusercontent.com/42731246/142735501-b95a8817-77ef-4303-83e4-75467cd66080.png)

## 28. Hoisting Code Examples

i) logging var before initialization results in undefined whereas results Reference Error for let or const variables

![alt text](https://user-images.githubusercontent.com/42731246/142735508-a6cc21e0-2aa1-45ae-81d9-03daf750f70f.png)

ii) Functional declarations vs Functional Expressions
Functional declarations results with a value before initialization whereas Functional Expressions throws a Reference Error due to Temporal Dead Zone.

![alt text](https://user-images.githubusercontent.com/42731246/142735517-d6419865-7b54-4dc3-93eb-79d85bd2f4fe.png)

iii) Replacing Functional Expressions with var results in TypeError because var results in undefined before initialization

![alt text](https://user-images.githubusercontent.com/42731246/142735521-e2512bfb-3de7-4c17-89ee-b86a7be7cf5a.png)

iv) var gets declared in the window object, so that is the reason it results true and let & const results false

![alt text](https://user-images.githubusercontent.com/42731246/142735528-964a47f7-5d51-475e-8cc8-ca946c09d1f1.png)

## 29. How this keyword works ?

![alt text](https://user-images.githubusercontent.com/42731246/142735560-90d9dc19-9a71-4d14-9875-2fe1c229bdc9.png)

## 30. Code examples of this keyword

line 92  will log Window object
line 96  will log undefined (because we are in strict mode)
line 101  will log Window object (Arrow func doesn’t get his own this keyword)

function this keyword points to its own function, whereas arrow function this keyword points to global scope

![alt text](https://user-images.githubusercontent.com/42731246/142735566-b2622af5-4e47-41f6-8e21-26fd1bf36ad1.png)

## 31. Line 113 results (year: 1991, calcAge function) and 46

Line 120 results (year:2017, calcAge function) and 20
Line 123 results (undefined) and TypeError

![alt text](https://user-images.githubusercontent.com/42731246/142735568-40f7dad3-9a06-4e60-80b3-6fbc097e78fa.png)

## 32.

This is because arrow function doesn’t have its own this keyword, it looks for the global and the global is undefined
![alt text](https://user-images.githubusercontent.com/42731246/142735578-aa33b765-5e83-43c2-b533-08a5e22fa0f5.png)

This is because arrow function looks for the global and the global is Matilda, This proves that don’t use var while declaring, but still above case (undefined) also is a bug
![alt text](https://user-images.githubusercontent.com/42731246/142735591-e08e4d89-d444-4e8a-bbc0-758a0c80bfc5.png)

To solve the above scenarios, we should declare using regular function
![alt text](https://user-images.githubusercontent.com/42731246/142735595-0af301c6-b6e4-4aa8-a751-5af1ebf31344.png)

## 33. More code examples on this keyword

Line 138 returns undefined because of the rule (inside a regular function call, this keyword must be undefined), even if we copy this isMillenial function outside (line 151), we should also see same behaviour

![alt text](https://user-images.githubusercontent.com/42731246/142735603-d84e1743-5378-4649-b127-183ef5769852.png)

Solution 1 (pre ES6)
const self= this (and log self inside isMillenial function)

![alt text](https://user-images.githubusercontent.com/42731246/142735620-5d926de3-d0ce-4d64-a243-b2ad82cf3ace.png)

Solution 2: Is to use arrow function, because this keyword in arrow function looks for global(parent scope), isMillenial is inside Jonas (this keyword will take the parent ref)

![alt text](https://user-images.githubusercontent.com/42731246/142735629-8e975e37-c633-4661-b76d-ef0f0df824a9.png)

## 34. arguments keyword in the console.log behaviour inside regular vs arrow functions

![alt text](https://user-images.githubusercontent.com/42731246/142735636-7c640dad-bfdb-4317-9d06-5ce769ff8c69.png)

## 35. Primitives vs Objects

Primitives: This is because oldAge at line 178 takes the value of age that was defined on line 177. (age at line 180 is dynamically changed, so obviously logging age will result as 31)

![alt text](https://user-images.githubusercontent.com/42731246/142735651-64e8a5c4-e42c-4956-9d93-3f703314c543.png)

Objects: This is due to the reason that Objects (Reference types) are stored in Heap
![alt text](https://user-images.githubusercontent.com/42731246/142735661-aeaa7a9e-1868-40a4-8ac2-735fa5ccf3e8.png)

## 36. Primitives vs Objects (Example)

![alt text](https://user-images.githubusercontent.com/42731246/142735675-7375833d-7c22-4feb-b6a4-718906647d7a.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735679-757e70e5-4d8b-40dc-bfdb-1bddf0492959.png)

## 37. Code Examples of Primitives vs Objects

i) lastName is different in jessica2 vs jessicaCopy but family returns same for both. Both points to same object in the heap.
ii) Object.assign creates a new reference in the heap, but the problem with this will be when we start using nested objects like family object (in this case). A deep clone is what we need here as it performs Shallow over here.

![alt text](https://user-images.githubusercontent.com/42731246/142735682-ae64e0ab-78c3-46ed-a1d1-915ed4bf08ce.png)

## 38. Object Destructuring and Changing the default key names

![alt text](https://user-images.githubusercontent.com/42731246/142735688-2d664822-a561-47c4-a21b-5da05ee229e2.png)

## 39. Assigning a default value if the property doesn’t exist

![alt text](https://user-images.githubusercontent.com/42731246/142735691-0ca1f56b-5248-46a4-8c71-2ee162099257.png)

If we don’t assign a default value it returns as undefined

![alt text](https://user-images.githubusercontent.com/42731246/142735716-4929db0c-1ccd-469a-a5e7-4936b115a368.png)

## 40. Code examples of Overriding the existing values to apply Destructuring values

![alt text](https://user-images.githubusercontent.com/42731246/142735725-0c82e5c2-4467-4e0f-b9a6-57b81c9edfc5.png)

## 41. Object Destructuring inside a nested object

Question)

![alt text](https://user-images.githubusercontent.com/42731246/142735745-a01ac3df-d10a-457f-987f-96995573092d.png)

Answer:

![alt text](https://user-images.githubusercontent.com/42731246/142735753-b5ac1ccb-6538-4d7b-bd27-74fbaed1e0da.png)

## 42. Spread Operator & Code Example

Spread Operator takes all the elements from the array and also it doesn’t create new variables. We can only use it where we need values separated by commas.

![alt text](https://user-images.githubusercontent.com/42731246/142735760-6b295779-7b28-41ad-890f-8586aeea8be3.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735762-131fca04-98b7-4358-a9b3-8f29e1e4769e.png)

line 54 creates shallow copy,
line 57 is to merge 2 arrays.
Note: All built in data-structures are now iterables except objects

![alt text](https://user-images.githubusercontent.com/42731246/142735768-e649883d-72ad-41f7-8b68-90d17ead9bf4.png)

Spread Operator on string

![alt text](https://user-images.githubusercontent.com/42731246/142735778-fab91aaf-6aef-48e6-8cd3-f51c56d5f597.png)

Spread Operator actually takes the copy of the object instead of changing the value like earlier

![alt text](https://user-images.githubusercontent.com/42731246/142735784-c85c9273-451f-4f23-afb3-17d0a3c0d6b8.png)

## 43. Nullish coalescing operator returns 0 if it is defined as zero, if the value is null or undefined then it results with default value which we provide. Ex: 10 would be the result on line 57 if line 51 is commented.

![alt text](https://user-images.githubusercontent.com/42731246/142735787-d3c92618-3837-4853-b22c-789de11428dc.png)

## 44. for-of loop

![alt text](https://user-images.githubusercontent.com/42731246/142735797-ae728589-fbfb-4d59-a650-0a32c227ff68.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735799-91c3ba0e-22e3-496a-8b72-7d6b3b640401.png)

## 45. ES6 Enhanced Object Literals

We moved openingHours nested object outside to restaurant object. We can still access that object inside restaurant object.

Note: if we want to use the same name, then we can refactor to only openingHours and access it.

Ex: openingHours:openingHours

![alt text](https://user-images.githubusercontent.com/42731246/142735806-97b3dd76-df5b-4079-9fb2-9b2d48797110.png)

## 46. ES6 enhancement

Ex:

![alt text](https://user-images.githubusercontent.com/42731246/142735813-1f9a1dd8-3654-435a-973e-164437aa9635.png)

Below refactor works same as above scenario(func expression)
![alt text](https://user-images.githubusercontent.com/42731246/142735817-657c1535-1a21-4b28-a270-de897abc8056.png)

## 47. Another ES6 Enhancement

Ex:
![alt text](https://user-images.githubusercontent.com/42731246/142735843-73278dc5-4c4e-44fe-8d44-dd8b76b95d51.png)

Above scenario can be refactored like below Scenario

![alt text](https://user-images.githubusercontent.com/42731246/142735845-3e2eea99-d2a0-43f4-9081-5c71e4387cc0.png)

## 48. Optional Chaining

Previously (line 51) vs New (line 58)
![alt text](https://user-images.githubusercontent.com/42731246/142735854-bd23988a-d29f-49ea-8ac3-2aadfda7a0f9.png)

Example:
Note: On line 64 we cannot write openingHours.day because that is not actual property name, if we need to use the variable name as the property name we need to use [ ]

![alt text](https://user-images.githubusercontent.com/42731246/142735861-dd36c24f-e036-4c60-b8be-e6200261d5d0.png)

## 49. Optional Chaining on Methods

![alt text](https://user-images.githubusercontent.com/42731246/142735870-e6c1ad31-6985-4bcb-8f89-ca752f7a4f86.png)

## 50. Optional Chaining on Arrays

i)
![alt text](https://user-images.githubusercontent.com/42731246/142735876-b84dbc03-cdc3-44f6-afc2-0895352b6d1e.png)

Output:
![alt text](https://user-images.githubusercontent.com/42731246/142735884-8cd30d55-162c-40bb-89a1-1362a319f051.png)

ii)
![alt text](https://user-images.githubusercontent.com/42731246/142735887-87663602-aebe-457a-9c22-43798c3f3c0a.png)

O/P:
![alt text](https://user-images.githubusercontent.com/42731246/142735891-f1050b2a-1cd2-44a5-8598-704bd22be41d.png)

iii) Without Optional Chaining Example
![alt text](https://user-images.githubusercontent.com/42731246/142735897-f61a7286-fef9-4894-b81a-754455779ab2.png)

## 51. pop(): Remove an item from the end of an array.

push(): Add items to the end of an array.
shift(): Remove an item from the beginning of an array.
unshift(): Add items to the beginning of an array.

## 52.

![alt text](https://user-images.githubusercontent.com/42731246/142735908-916258b7-2514-42b2-b132-be6b9fae3507.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735910-b44d3dda-6944-45ad-b26f-f723f617d462.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735913-76431b1c-2db2-4f6f-b6b6-6928157ae282.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735917-8ed74cc8-8b35-4cf1-afba-00e3743f9258.png)

## 53. Slice vs Splice

Slice doesn’t modify the original array whereas Splice modifies the original array.

![alt text](https://user-images.githubusercontent.com/42731246/142735924-05070293-95af-41fb-a4c2-33394e0b2216.png)

## 54. How to merge two arrays of different sizes?

![alt text](https://user-images.githubusercontent.com/42731246/142735930-3041e815-3b0e-4f68-a856-bcd10f4ee71f.png)

## 55. Synchronous vs Asynchronous programming?

Ans: synchronous means to be in a sequence, i.e. every statement of the code gets executed one by one. So, basically a statement has to wait for the earlier statement to get executed. While asynchronous operations can execute without blocking other operations.

![alt text](https://user-images.githubusercontent.com/42731246/142735938-82c933c5-2726-4b44-b7ff-314101d44278.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735942-9f9aac23-d1c9-4a8f-a219-29ceb56c32c7.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735944-9ea960df-6ab2-43db-8b89-68edb7fb7671.png)

## 56. AJAX

![alt text](https://user-images.githubusercontent.com/42731246/142735946-49fbb0ae-14ad-456d-9e7c-9eec4362d247.png)

## 57. Promises vs async await

- A Promise is an object representing the eventual completion or failure of an asynchronous operation. Promises deal with one asynchronous event at a time, Instead of expecting callbacks as arguments to your functions, you can easily return a Promise object..

![alt text](https://user-images.githubusercontent.com/42731246/142735958-8d082738-103a-42dd-aacf-38a6de7fc0cf.png)

await only blocks the code execution within the async function. It only makes sure that the next line is executed when the promise resolves. So, if an asynchronous activity has already started, await will not have any effect on it.

![alt text](https://user-images.githubusercontent.com/42731246/142735961-4cec1be5-d171-4999-afdd-e58f7f843b19.png)

## 58. What is a Callback?

A callback function is usually used as a parameter to another function. The function that receives the callback function as a parameter is normally fetching data from a database, downloading a file, making an API request, or completing some other task that could block the code thread for a notable amount of time.

Ex: You are going to download an image. The download takes about 2 seconds, and you don't want your program to stop on this line of execution as you wait for the download to finish. A callback allows you to keep running other functions and "call back" the image after the download is complete.

![alt text](https://user-images.githubusercontent.com/42731246/142735968-2ee2b811-97be-43d4-bd32-dfe11faeb2d0.png)

![alt text](https://user-images.githubusercontent.com/42731246/142735970-5c86ab14-29d3-496b-9f36-ce756be9b2a2.png)

## 59. What are Promises?

A promise is an object that represents something that will be available in the future. Promises propose that instead of waiting for the value we want (e.g. the image download), we receive something that represents the value in that instant so that we can "get on with our lives" and then at some point go back and use the value generated by this promise.

## 60. Key Difference Between Callbacks and Promises

A key difference between the two is when using the callback approach, we’d normally just pass a callback into a function that would then get called upon completion in order to get the result of something. In promises, however, you attach callbacks on the returned promise object.

## 61. Advantages of Promises over Call-back?

Easy to manage when dealing with multiple asynchronous operations where callbacks can create callback hell leading to unmanageable code.
Improves Code Readability, Better Error Handling

## 62. What is closure and what makes it special?

Closures is an ability of a function to remember the variables and functions that are declared in its outer scope, a closure gives you access to an outer function's scope from an inner function

![alt text](https://user-images.githubusercontent.com/42731246/142736002-cf2da971-5314-4311-8751-a3964fcce64d.png)

## 63. What is hoisting?

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. Inevitably, this means that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local

## 64. let vs var vs const

var declarations are globally scoped or function scoped while let and const are block scoped. var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared.

## 65. How to get the keys from a map using javascript?

![alt text](https://user-images.githubusercontent.com/42731246/142736010-d6082c80-bcef-4e71-b819-d2a22970a0d7.png)

## 66. array methods like forEach, map, filter, reduce etc.

![alt text](https://user-images.githubusercontent.com/42731246/142736014-9b8b8513-1831-4318-8d75-40d2f79bf206.png)

forEach() method doesn’t need to create a new array

The map() method creates a new array with the results of calling a function for every array element.

.filter() when you want to select a subset of multiple elements from an array.

![alt text](https://user-images.githubusercontent.com/42731246/142736019-e6fce49d-69be-4420-893c-cb9f3f3b9315.png)

.reduce() when you want derive a single value from multiple elements in an array.
![alt text](https://user-images.githubusercontent.com/42731246/142736024-8136ec3f-4b28-471f-b572-8aba32e80a83.png)

## 67. ‘use Strict’ operator?

preventing you from using undeclared variables

![alt text](https://user-images.githubusercontent.com/42731246/142736028-c79fc3b7-6bcb-4550-8e92-ce74c31262ea.png)

## 68. Higher order functions

Higher-order functions are functions that take other functions as arguments or return functions as their results.

![alt text](https://user-images.githubusercontent.com/42731246/142736037-83f76afe-ae3a-48b5-a249-9f70aae6f04e.png)

## 69. What is the difference between == and ===?

== in JavaScript is used for comparing two variables, but it ignores the datatype of variable. === is used for comparing two variables, but this operator also checks datatype and compares two values. Checks the equality of two operands without considering their type

## 70. What is spread and rest operator? (unpack vs pack)

Ans: Rest parameter collects all remaining elements into an array.
var myName = ["Marina" , "Magdy" , "Shafiq"] ;
const [firstName , ...familyName] = myName ;
console.log(firstName); // Marina ;
console.log(familyName); // [ "Magdy" , "Shafiq"] ;

Spread operator: allows iterables (arrays / objects / strings) to be expanded into single arguments/elements
var myName = ["Marina”, "Magdy" , "Shafiq"];
var newArr = [...myName ,"FrontEnd" , 24];
console.log(newArr) ; // ["Marina" , "Magdy" , "Shafiq" , "FrontEnd" , 24 ] ;

i) Spread operator means Right Side, Rest defined in the left side

![alt text](https://user-images.githubusercontent.com/42731246/142736062-b3f946d0-b1e9-4a3a-a6c4-3e82b42c3235.png)

ii)

![alt text](https://user-images.githubusercontent.com/42731246/142736067-7c384657-dcec-4fb1-be1b-512e1af3d388.png)

![alt text](https://user-images.githubusercontent.com/42731246/142736069-511de2fb-fd9c-4cf9-9fdf-9d9135516797.png)

iii) Rest element must be the last element

![alt text](https://user-images.githubusercontent.com/42731246/142736075-e32494e0-bf64-47ea-a1c9-34046cb08ceb.png)

iv) Objects

![alt text](https://user-images.githubusercontent.com/42731246/142736080-0a3e6963-eb2d-4b8b-9681-c0993b247a12.png)

rest are thu,fri (so that is the reason it returns these objects)

![alt text](https://user-images.githubusercontent.com/42731246/142736081-057f8d65-e8a9-432b-bf0a-e66ab528f34b.png)

v) Functions
Rest syntax is taking multiple numbers(values) and then packs them all into one array

![alt text](https://user-images.githubusercontent.com/42731246/142736082-edfc39d1-32c4-483f-9255-6690a67a600c.png)

## 71. What is mutation

Ans: By mutation I mean changing or affecting a source element.

## 72. What is the use of isNAN function?

Ans: The isNaN() function determines whether a value is an illegal number (Not-a-Number). This function returns true if the value equates to NaN. Otherwise it returns false. This function is different from the Number specific Number.

![alt text](https://user-images.githubusercontent.com/42731246/142736090-5dcb0f2b-70bf-4d69-badb-5d4ebdadf087.png)

## 73. What is the meaning of NULL in JS?

Ans: The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values and is treated as falsy for boolean operations.

## 74. How to define an Object in JavaScript?

Ans: var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

## 75. Call-back hell and how to avoid it?

Using Promises or Async/Await

## 76. What is prototype

Ans: The JavaScript prototype property allows you to add new properties to object constructors:

## 77. How to compare to date object in javascript

Ans: getTime

## 78. Local storage vs session storage

Ans: the difference is that while data in localStorage doesn't expire, data in sessionStorage is cleared when the page session ends. A page session lasts as long as the tab or the browser is open, and survives over page reloads and restores.

## 79. Difference between null and undefined

Ans: null is an assigned value. It means nothing. undefined means a variable has been declared but not defined yet.

## 80. CORS, preflight request

A CORS preflight request is a CORS request that checks to see if the CORS protocol is understood and a server is aware using specific methods and headers. It is an OPTIONS request, using three HTTP request headers: Access-Control-Request-Method , Access-Control-Request-Headers , and the Origin header.

## 81. Data types in JavaScript?

Number
String
Boolean
Object
Undefined

## 83. Call, apply, bind

a) Call invokes the function and allows you to pass in arguments one by one.
b) Apply invokes the function and allows you to pass in arguments as an array.
c) Bind returns a new function, allowing you to pass in this array and any number of arguments.

## 84. Dynamic Object Keys

#### Normal Procedure

![image](https://user-images.githubusercontent.com/42731246/148685749-b1fd5d4e-3a16-4f2d-a380-7c013bbb3692.png)

#### i) Square Notation Example

![image](https://user-images.githubusercontent.com/42731246/148685845-cdf33029-b5cb-40e7-9b43-bf59a78702f4.png)

#### ii) Square Notation Example

![image](https://user-images.githubusercontent.com/42731246/148685885-5b329f23-067a-4537-b8e7-a0279e12c4bc.png)

#### iii) Square Notation Example

![image](https://user-images.githubusercontent.com/42731246/148685975-cbb7ab59-ae79-4784-8186-2ded7ba0d96a.png)

### Dynamically changing the Object Keys

![image](https://user-images.githubusercontent.com/42731246/148686048-8b582345-6468-4a63-b524-3a462acb6a28.png)

![image](https://user-images.githubusercontent.com/42731246/148686169-1612e014-7d59-4055-ba37-67e0aaf0faff.png)

![image](https://user-images.githubusercontent.com/42731246/148686189-46e0aee3-f688-4c06-af5d-15bb86b4b3ce.png)

![image](https://user-images.githubusercontent.com/42731246/148686211-454f2074-57e7-4cda-a6cf-03e7329d35d7.png)

#### overriding name key and value

![image](https://user-images.githubusercontent.com/42731246/148686257-cc70316c-643f-493e-99e5-97084ce30a3e.png)

---

## 85. When should we use generators in ES6?

- **Handing Asynchronous operations**: Generators can be used to simplify the code for asynchronous operations making it easier to read and maintain.
- **Lazy Evaluation**: Generators allow you to define a potentially infinite sequence and compute its values on demand. This is useful when dealing with large datasets where you don't need all values immediately and want to avoid the memory overhead of storing them all at once.
- **Stateful Iterations**: Generators maintain their state during executions. This makes them to create custom iterators where you need to maintain state across iterations.
- **Complex Control Flow**: You might have code that is hard to read. Generators provide readable and maintainable solution in these cases
- **Multitasking**: Generators can be used to implement cooperative multitasking within a single thread. By yielding control back to the scheduler different tasks can be interleaved in a controlled manner.
- **Pause and Resume execution**- Generators can pause the execution and resume it later, which can be useful in scenarios where you need to wait for an external process or input before continuing.
- **Custom Data Producers** - Like a specific range of numbers or a unique sequence, generators are more elegant solution than building an iterator using traditional methods.

---

## 86. When should we use Arrow functions in ES6?

- **Shorter Syntax**: Shorter syntax is particularly useful for inline functions or callbacks
- **No this binding**: Arrow functions do not have their own `this` context. They inherit `this` from `parent scope` at the time they are defined.
- **Implicit return**: For functions, they simple return a value, whereas arrow functions can be written with an implicit return making the code shorter and cleaner. (useful for map, filter, reduce)
- **Functional Programming**: Well suited for FP patterns due to their syntax + no context binding (ex: this, arguments, super, new.target)
- **Non method Functions**: Arrow functions are ideal for non-method functions. They are not suitable as object methods when you need to access the object's properties using `this` will refer to the outer context.

```js
// An arrow function in the global scope
const checkThis = () => {
  console.log(this === window); // true in a non-strict mode browser environment
};

checkThis(); // Calls the arrow function
```

```js
function MyObject() {
  this.value = 10;

  this.increment = function () {
    // Arrow function captures 'this' from the enclosing scope (MyObject instance)
    setTimeout(() => {
      this.value++;
      console.log(this.value); // Correctly refers to the MyObject instance
    }, 1000);
  };
}

let obj = new MyObject();
obj.increment(); // After 1 second, it will log '11'
```

---

## 87. const vs Object.freeze()?

**const**

- The const keyword is used to declare a variable
- It ensures that the variable identifier cannot be reassigned to a different value
- But it doesn't make the value it holds as immutable. **For instance, if the const variable holds an object, the properties of that object can still be modified.**

Ex:

```js
const myConst = { a: 1 };
myConst = { b: 2 }; // Error: Assignment to constant variable.
myConst.a = 2; // This is fine, myConst now is { a: 2 }
```

**Object.freeze()**

- This is a method that acts on an object
- Makes an object immutable meaning its **properties cannot be added, removed or changed**.
- This is a shallow freeze, so it only applies to the immediate properties of the object.
- **Nested objects can still be modified** unless they are also frozen

```js
const myObject = { a: 1 };
Object.freeze(myObject);
myObject.a = 2; // No effect, myObject is still { a: 1 }
myObject.b = 3; // No effect, can't add new properties
```

---

## 88. How do you compare two objects in javascript ?

Comparing objects is tricky, because objects are compared by the reference not by value. This means that even if two objects contain exactly the same properties with the same values, they are considered different if they are not the same instance.

Below are some of the methods to compare objects based on criteria

**1. Shallow Comparison**: considers immediate properties of two objects are equal. **Doesn't consider nested objects**

```js
function shallowEqual(object1, object2) {
  const keys1 = Object.keys(object1);
  const keys2 = Object.keys(object2);

  if (keys1.length !== keys2.length) {
    return false;
  }

  for (let key of keys1) {
    if (object1[key] !== object2[key]) {
      return false;
    }
  }

  return true;
}
```

**2. Deep comparison**: Is necessary if the objects may have nested objects or arrays. This checks every property (and sub-property) for equality.

```js
function deepEqual(object1, object2) {
  if (object1 === object2) {
    return true;
  }

  if (
    typeof object1 !== 'object' ||
    object1 === null ||
    typeof object2 !== 'object' ||
    object2 === null
  ) {
    return false;
  }

  const keys1 = Object.keys(object1);
  const keys2 = Object.keys(object2);

  if (keys1.length !== keys2.length) {
    return false;
  }

  for (let key of keys1) {
    if (!keys2.includes(key) || !deepEqual(object1[key], object2[key])) {
      return false;
    }
  }

  return true;
}
```

3. **JSON Stringify**: Quick and dirty way to compare objects. However it has limitations it doesn't handle functions or `undefined` properties and the order of the properties matters

```js
const areEqual = JSON.stringify(object1) === JSON.stringify(object2);
```

**4. Using Loadash libraries**

```js
// Using Lodash
const areEqual = _.isEqual(object1, object2);
```

---

## 89. document `load` event vs document `DOMContentLoaded` event ?

### DOMContentLoaded

- Triggered when the DOMContentLoaded event is fired when the `initial HTML document has been completely loaded and parsed` `without waiting for stylesheets, images and subframes to finish loading`.

- **Use case:** If you're adding event listeners or manipulating the DOM, this is the best case.

- **Faster than the `load` event for initiating DOM-related scripts**

```js
document.addEventListener('DOMContentLoaded', function () {
  console.log('DOM fully loaded and parsed');
});
```

### load event

- triggered when the load event is fired, when the whole page has loaded, including all dependent resources such as stylesheets and images.
- used when you need to perform actions that require all resources on the page to be fully loaded. **Ideal for actions that need dimensions of images or styles applied from CSS**

```js
window.addEventListener('load', function () {
  console.log('Entire page is fully loaded');
});
```

**Note:**

- DOMContentLoaded is typically added to the `document`
- `load` can be added to the `window` object to detect the complete page load.

---

## 90. Motivation behind introduction of Symbol in ES6?

**Unique Identifiers**- Particularly useful when you create an object property that doesn't clash with any other property, it's a way to add `private` properties to objects

**Property Key privacy**: Before ES6, object properties were either strings or numbers, which could lead to naming collisions. Symbols offer a way to create `hidden` properties on objects that are not enumerable in traditional for-in loops and are not part of the object's public when using libraries.

```js
let mySymbol = Symbol('myPrivateProperty');

let myObject = {
  [mySymbol]: 'This is a private property',
  publicProperty: 'This is a public property',
};

console.log(myObject.publicProperty); // Accessible and outputs: This is a public property

// Accessing the private property with the symbol
console.log(myObject[mySymbol]); // Outputs: This is a private property

// Demonstrating the privacy
for (let prop in myObject) {
  console.log(prop); // Only logs "publicProperty", not the symbol property
}

console.log(Object.keys(myObject)); // Outputs: ["publicProperty"], symbol property is not listed

console.log(JSON.stringify(myObject)); // Outputs: {"publicProperty":"This is a public property"}, symbol property is not included
```

**Symbol.iterator**- is used to make an object iterable and compatible with the new `for of` loop.

---

## 91. Prototype Design Pattern

----

## 92. JS module Design Pattern

-----

## 93. Actual uses of ES6 WeakMap ?

### 1. Private Data

- WeakMap can be used to store private data for an object
- Since the keys are weakly referenced the private data will be garbage collected when the object is no longer in use, helping to prevent memory leaks.

```js
const privateData = new WeakMap();

function MyClass(privateContent) {
  privateData.set(this, privateContent);
}

MyClass.prototype.doSomething = function () {
  console.log(privateData.get(this));
};
```

### 2. Caching data:

- Caching results of a function for memoization

```js
const cache = new WeakMap();

function computeExpensiveValue(obj) {
  if (!cache.has(obj)) {
    const result = {
      /*some expensive operation */
    };
    cache.set(obj, result);
  }
  return cache.get(obj);
}
```

### 3. Security:

- Since the keys of WeakMap are not enumerable (no way to get the list of keys), it can add a layer of security where the association between the object and its data in the `WeakMap` is not easily discoverable from outside code.

**Realtime Scenario**:

- Managing Sessions in a Web Application:

```js
const sessionData = new WeakMap();

class Session {
  constructor(userId) {
    this.userId = userId;
    sessionData.set(this, {
      /* private data */
    });
  }

    endSession(){
      sessionData.delete(this)
    }

}
  function createSession(userId){
    return new Session(userId)
  }
```

---

## 94. Map vs WeakMap

----

## 95. Is it possible to reset an ES6 generator to its initial state?
----

## 96. What is the difference between host objects and native objects?
----

## 97. What is the difference between an "attribute" and a "property" ?
----

## 98. Explain the same-origin policy with regards to JavaScript.
----

## 99. Explain Ajax in as much detail as possible.
----

## 100. Why would you use something like the load event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
----

## 101. Explain what a single page app is and how to make one SEO-friendly.
----

## 102. Why you might want to create static class members?
