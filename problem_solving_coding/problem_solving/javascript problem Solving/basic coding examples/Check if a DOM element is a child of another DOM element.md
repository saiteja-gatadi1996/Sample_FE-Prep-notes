## Check if a DOM element is a child of another DOM element

**Approach Taken**

- contains is so simple, parent.contains(child) //false or true
- closest is applied on child (ex: child.closest) which takes args (ex: child.closest(parent.tagName))
- this one we are performing equality checking with the parent element itself

```js
// contains
const isChildOf = (child, parent) => parent.contains(child);

//closest
const isChildOf = (child, parent) => child.closest(parent.tagName) === parent;

// Ex:
const parent = document.getElementById('parent');
const child = document.getElementById('child');

console.log(isChildOf(child, parent)); // It will log true if child is a descendant of parent, otherwise false
```
