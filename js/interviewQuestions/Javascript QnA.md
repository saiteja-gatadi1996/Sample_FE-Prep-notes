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

# <--- SAMPLE CONTENT ENDS --->
