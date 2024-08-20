### Why Capital Letters for a Component?

- In JSX, lowercase tag names **_are considered to be HTML tags_**.
- However lowercase **tag names with a dot (property) aren't**

- #### When an element type starts with a lower letter, it <ins>refers to built-in component</ins> and results in a string div block or span block.

- #### Type that <ins>start with a capital letter compile to React.createElement(FooComponent)</ins> and correspond to a component defined or imported in your JS file.

```js
// compiles to React.createElement('component') (html tag)
<component />

// compiles to React.createElement(Component)
<Component />


// compiles to React.createElement(obj.component)
<obj.component />
```
