### 1. When JS is after the body tag

```js
<html>
  <head>Title</head>
  <body></body>
  <script src='script.js'></script>
</html>
```

**Ex**: <ins>**Once HTML parsing is done**</ins>, it encounters the JS, it downloads the JS and then it executes the JS.

![alt text](/web_dev/network_optimization/imagesUsed/HTML_parsing-1.png)

---

### 2. When JS is in HEAD tag

```js
<html>
  <head>
    <title>Title</title>
    <script src='script.js'></script>
  </head>
  <body></body>
</html>
```

**Ex**: During HTML parsing it encounters the JS and <ins>**it pauses the HTML parsing and it downloads the JS and then it executes the JS**</ins> and then HTML parsing is resumed.

**Cons**: It stops the execution of DOM tree which is a bad User experience.

![alt text](/web_dev/network_optimization/imagesUsed/HTML_parsing-2.png)


---

### 3. When async attribute is in HEAD tag

```js
<html>
  <head>
    <title>Title</title>
    <script async src='script.js'></script>
  </head>
  <body></body>
</html>
```

**Ex**:

- During HTML parsing it encounters the JS and the **HTML parsing is continued during download phase**

- But when it starts executing the JS, the HTML parsing is paused and once it completes executing the JS then HTML parsing is resumed.

**Cons**: It stops the execution of DOM tree which is a bad User experience.

![alt text](/web_dev/network_optimization/imagesUsed/HTML_parsing-3.png)



---

### 4. When defer attribute is in HEAD tag

```js
<html>
  <head>
    <title>Title</title>
    <script defer src='script.js'></script>
  </head>
  <body></body>
</html>
```

**Ex**:

- During HTML parsing it encounters the JS and the **HTML parsing is continued during download phase**

- After HTML parsing is completed, it executes the JS.

**Note**: This is more optimized approach when compared to others because we are prefetch the Javascript code during the parsing phase.

![alt text](/web_dev/network_optimization/imagesUsed/HTML_parsing-4.png)

---
