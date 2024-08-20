### 3. Garbage Collection:

- Javascript is a <ins>**garbage collected**</ins> language
- That means when Javascript allocates memory (e.g. within a `function`, we create an `object` and that objects gets `stored` somewhere in our `memory heap`. Automatically with javascript **when we finish calling the function** and **if we don't need that object anymore**, <ins>**_it's going to be garbage collected_**)</ins>
- So Javascript <ins>**_automatically frees up this memory_**</ins> that we no longer use and well collect our garbage.
- Garbage collector <ins>frees up the memory and prevents from Memory leaks</ins>
- Garbage collection in javascript actually works on **algorithm called** <ins>**_Mark & Sweep_**</ins>

#### Imagine the left ones are the variables and these variables point to different objects

- ##### In the below picture, `Object 5` and `Object 7, 8` are not being referenced to any, <ins>so they will be garbage collected.</ins>

![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Mark_&_Sweep_algorithm-1.png)
![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Mark_&_Sweep_algorithm-2.png)