## Virtual DOM is not what you are thinking!

- The virtual DOM is **only a virtual representation** of the DOM.
- Every time the ***state of our application changes***, the **_virtual DOM gets updated_** instead of the real DOM.

<ins>**Points to remember**</ins>:

- When **new elements are added** to the UI, a **virtual DOM**, which is represented as a tree **_is created_**.

- <ins> **If the state of any of these elements changes, a new virtual DOM tree is created.**</ins>

- This tree is then compared or **“diffed”** <ins>***with the previous virtual DOM tree***</ins>.

- Once this is done, the <ins>***virtual DOM calculates the best possible method to make these changes to the real DOM***</ins>.

<ins>**Deep Dive into Virtual DOM Mechanisms**:</ins>
 - **Batch Updates**:
    - Virtual DOM allows for batch updates, meaning ***it can perform multiple DOM updates in a single operation***. 
    -  This ***reduces the performance cost associated with frequent***, individual DOM manipulations.
  <br/>

 - **Efficient Diffing Algorithm**:
   - The Virtual DOM employs a diffing algorithm that efficiently <ins>**identifies differences between the old and the new Virtual DOM trees**</ins>. 
   - By pinpointing the exact changes needed, it ***minimizes the operations required to update the real DOM***.
  <br/>

 - **Reconciliation**: 
   -  This process involves the Virtual DOM <ins>***calculating the most efficient way to update the real DOM to match the Virtual DOM***</ins>.
   - It <ins>***ensures that only the components that have actually changed are re-rendered***</ins>, rather than updating the entire tree. 
   - This selective rendering significantly improves application performance, especially in complex interfaces.
 


----

### **Expanded Benefits**:

 - **Improved User Experience**: 
    - <ins>***By minimizing unnecessary DOM updates***</ins>, **the Virtual DOM ensures smoother and more responsive user interactions**. This is particularly noticeable in dynamic, data-driven applications where the UI needs to update frequently.
<br/>

- **Development Efficiency**: 
  - The **abstraction provided by the Virtual DOM <ins>simplifies the development process**</ins>. 
  - Developers can focus on the state and logic of their applications, ***without worrying about the intricacies of DOM manipulation and performance optimization***.

<br/>


- **Cross-Platform Consistency**: 
  - The concept of the Virtual DOM is not limited to web applications. Frameworks like React Native leverage this idea to provide a consistent development experience across web and mobile platforms, enabling the creation of performant, native-like applications.
<br/>

- **SEO Friendly**: 
  - While not a direct benefit of the Virtual DOM itself, frameworks that utilize Virtual DOM often come with server-side rendering capabilities. 
  - This means that <ins>***applications can render the initial state on the server, improving load times and making content indexable by search engines, which is crucial for SEO***</ins>.


<img src="https://github.com/krishnakiriti04/react-interview-questions/raw/master/assets/dom.png">


----

#### Reduced Direct DOM Manipulation
- **Direct DOM Manipulation is Slow**: 
  - Manipulating the actual DOM is expensive in terms of performance. 
  - **Each change can trigger `reflows` and `repaints`** which are computationally costly operations.
- **Virtual DOM Minimizes Changes:** 
  - The Virtual DOM allows <ins>**updates to happen in memory rather than directly in the DOM**</ins>. 
  - It does this by creating a lightweight representation of the DOM. 
  - When changes are made, **they are <ins>first applied to the Virtual DOM</ins>**.
