- **process.nextTick()**: Have highest priority. The callback is executed immediately after the current operation completes but before the event loop moves on to the next phase.
- **promise**: executed after process.nextTick()
- **setTimeout**: are placed in the timer phase of the event loop. These will be executed after promises as per priority.
- **setImmediate**: This <u>_*schedules the callback to be executed **on the next iteration** of the event loop*_</u>. It <u>**_checks the queue after the current operation completes_**</u> and <u>before setTimeout is called.</u>
- **callback**: regular callbacks have the lowest priority. They execute at last when compared to the above 3

### 1. Promise vs setTimeout()

<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*aQnD1G3m3rBHOv-uGLRW1A.png">

### Output:

```js
Promise first!
Timed out second!
```

---

### 2. setTimeout vs setImmediate()

<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*VoDEl5MPXUpkXT2IePUx3w.png">

### Output:

```js
Timed out with 0 second!
setImmediate called
Timed out with 10 second!
```

**Reason**: setTimeout with 0 milliseconds is placed on the timers queue, **_which is processed before the check phase_** where setImmediate callbacks are executed.

<u>**Note:**</u> - timers being checked first.

<u>**Detailed Explanation:**</u>

- **Timed out with 0 seconds** : Even though setTimeout is set with 0 seconds, it won't execute immediately. It will be placed on the event queue and will execute once the current call stack is clear and after the execution of any microtasks.

- **setImmediate called** : setImmediate is designed to execute a script once the current poll phase of the event loop is complete.
- Typically executes right after any scripts with a 0 millisecond setTimeout, but before any longer timeouts (This is the reason for that above output order)

- **Timed out with 10 second!** : will execute after the setImmediate and any 0 setTimeout timer.

---

# <--- SAMPLE CONTENT ENDS --->
