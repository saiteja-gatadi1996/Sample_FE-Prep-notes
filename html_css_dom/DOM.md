## 1. What is the DOM, and how does it relate to HTML?

#### DOM

- The DOM, or Document Object Model, is a programming interface for web documents.
- It **_<u>represents the page so that programs can change the document structure, style, and content</u>_**.
- The **_<u>DOM provides a representation of the document as a structured group of nodes and objects that have properties and methods</u>_**.

#### HTML

- describes the structure of web pages using markup
- **When a web page is loaded, <u>the browser creates a DOM of the page</u>**.
- The **_<u>HTML document serves as the blueprint for the DOM</u>_**.
- **Once the HTML code is parsed by the browser**, **_<u>it is converted into a DOM</u>_**
- This process allows dynamic access and manipulation of the content, structure, and style of the document.

##### In summary, while <u>HTML provides the raw material (markup) for the page</u>, the <u>_DOM is what browsers actually use to render the page and enable dynamic interaction and manipulation_</u> through scripting languages like JavaScript.

---

## 2. How can you access elements in the DOM using JavaScript?

Following are the most commonly used methods to access and manipulate elements in the DOM:

```js
//getElementById(id):
// Selects a single element by its ID. This is one of the most efficient ways to select an element.
var element = document.getElementById('myElementId');
```

```js
//Returns a live HTMLCollection of all elements with the specified class name.
var elements = document.getElementsByClassName('myClassName');
```

```js
//Returns a live HTMLCollection of elements with the given tag name.
var elements = document.getElementsByTagName('div');
```

```js
// Returns the first element that matches a specified CSS selector(s) in the document.
var element = document.querySelector('.myClassName');
```

```js
//Returns a static NodeList containing all elements that match a specified CSS selector(s) in the document.
var elements = document.querySelectorAll('p.myClassName');
```

```js
//Returns a NodeList of all elements with a specified name attribute.
var elements = document.getElementsByName('myElementName');
```

For example, once you have selected an element, you can change its properties, apply styles, add event listeners, or even remove it from the document. Here's a simple example of how you might change the text content of an element:

```js
document.getElementById('myElementId').textContent = 'New text content!';
```

---

## 3. How can you dynamically create HTML elements using JavaScript?

#### 1. Create the Element

```js
var newDiv = document.createElement('div');
newDiv.id = 'myNewDiv';
newDiv.className = 'my-div-class';
newDiv.setAttribute('data-custom', 'value');
newDiv.textContent = 'Hello, world!';
// OR
newDiv.innerHTML = '<strong>Hello, world!</strong>';
```

#### 2. Append the Element to the DOM

```js
document.body.appendChild(newDiv);
// OR
var parentDiv = document.getElementById('parentDiv');
parentDiv.appendChild(newDiv);
```

---

## 4. How can you modify CSS properties of an element in the DOM using JavaScript?

- Using the style Property

```js
var element = document.getElementById('myElement');
element.style.color = 'blue';
element.style.fontSize = '20px';
```

- Using setProperty

```js
var element = document.getElementById('myElement');
element.style.setProperty('--my-custom-color', 'green');
element.style.setProperty('background-color', 'yellow');
```

- Modify CSS classes

```js
// Modify classes
element.classList.add('new-class');
element.classList.remove('old-class');
```

---

## 5. Explain the purpose of the setAttribute and getAttribute methods in DOM manipulation.

#### setAttribute

- is used to **_<u>set or update the value of an existing attribute on the specified element</u>_** on a specified element

```js
//syntax
element.setAttribute(attributeName, value);
```

```js
var button = document.getElementById('myButton');
button.setAttribute('type', 'button');
button.setAttribute('disabled', '');
```

#### getAttribute

- The getAttribute method is used to retrieve the value of a specified attribute on an element.
- If the element does not have the specified attribute, null is returned.

```js
var buttonType = button.getAttribute('type');
console.log(buttonType); // Outputs: button
```

---

# <--- SAMPLE CONTENT ENDS --->
