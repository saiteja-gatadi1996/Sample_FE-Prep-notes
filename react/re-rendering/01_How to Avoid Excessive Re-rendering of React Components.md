## Avoid Excessive Rendering

##### 1. Always use the key while mapping (don't use index as a key)
- **Using unique identifiers** as `keys` instead of indices ensures that React can accurately and efficiently update the DOM by reordering elements instead of re-rendering the entire list.

```js
// never do this, it is a bad idea due to specific React library

list.map((item, index) => {
  return <div key={index}>Hello</div>;
});
```

---

#### 2. Pay attention to the nesting of elements and their types
- **Avoid deep nesting of components** and be mindful of the types of elements used to prevent unnecessary re-renders.

#### 3. Selectors and Redux

- Every time the dispatch of a action occurs modifying the state of the Redux Store, the corresponding useSelector will be called.
- It is essential to understand that if the useSelector returns an object or an array. (If the references differ then re-render will be performed)

- **Immutable patterns** or libraries like `Reselect` can help in returning memoized selectors to avoid redundant computations and re-renders.

##### Wrong way

```js
export const selectTagsByProductId = (state, id) =>
  state.product[id].tags || [];
```

##### Right way

```js
const EMPTY_ARRAY = Immutable([]);

export const selectTagsByProductId = (state, id) =>
  state.product[id].tags || EMPTY_ARRAY;
```

##### Redux in its official documentation, recommends the following optimization methods

1. Return Scalar data types (string, number, boolean, undefined)
2. Use libraries like reselect or similar
3. Use the shallowEqual function from the 'react-redux' package as the second argument

```js
// Typical example of reselect usage
const selectUserTagById = (state, userId) => state.user[userId].tag;

const selectPictures = (state) => state.picture;

const selectRelatedPictureIds = createSelector(
  [selectUserTagById, selectPictures],
  (tag, pictures) =>
    Object.values(pictures)
      .filter((picture) => picture.tags.includes(tag))
      .map((picture) => picture.id)
);
```

- reselect understands on when to take from cache and when to recalculate based on the shallowEqual

- Ex: if the selector arguments have not changed
- Ex: if the results of inputSelectors have not changed

---

#### 4. Memoization

**1. React.memo**

- React.memo caches the component and re-renders only if the properties have been changed.
- It's important to understand that reference will affect the rendering (when a new value comes for the component each time). In this case there will be no benefit to use memoization at all.

```js
const MemoizedComponent = React.memo((props) => (
  <SomeComponent props={props} />
));
```

**2. React.useCallback**

- It returns a new function if something in the dependencyList changes. Otherwise it produces the reference to the function in memory, which will return true(due to comparing prevProps vs nextProps).

- useCallback is only needed to check references.
- Don't use useCallback for native DOM element as it don't compare references.

```js
const onClick = useCallback(callbackFunc, dependencyList);
```

**3. React.useMemo**

- Works same as useCallback but don't forget to add the second argument which is dependency array

```js
const filteredArrary = useMemo(() => someExpensiveFunction(), dependencyList);
```

###### However, it’s important to remember that these hooks work effectively only together with memoised components, but not separately.

---

In addition to existing best practices, 

- **Careful State Management**: Be judicious in how state is updated and managed to minimize re-renders.
<br/>
- **Use of Pure Components**: For class components, extending **React.PureComponent** can prevent unnecessary re-renders by shallowly comparing props and state.
<br/>

- **Avoiding** `Inline` Functions and Objects in JSX: Inline functions and objects are created anew on each render, triggering re-renders.***Where possible, these should be defined outside the component or memoized***
<br/>

- ***Debouncing and Throttling Event Handlers:*** For events that trigger updates frequently (like window resizing or scrolling), debouncing or throttling can reduce the number of set state calls.
<br/>

- ***Lazy Loading of Components and Images***: This can significantly reduce the initial load time and improve performance, especially for large applications and assets.
<br/>

```js
// WITHOUT useCallback, on every click, ChildComponent re-renders
import React, { useState, useCallback } from 'react';

const ChildComponent = React.memo(({ onClick }) => {
  console.log('Child is rendering...');
  return <button onClick={onClick}>Click me</button>;
});

export function App() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount((prevCount)=> prevCount + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <ChildComponent onClick={incrementCount} />
    </div>
  );
}
```

```js
// WITH useCallback, no matter how many times you click on the button
// only counts gets incremented whereas ChildComponent rendered only once.
import React, { useState, useCallback } from 'react';

const ChildComponent = React.memo(({ onClick }) => {
  console.log('Child is rendering...');
  return <button onClick={onClick}>Click me</button>;
});

export function App() {
  const [count, setCount] = useState(0);

  const incrementCount = useCallback(() => {
    setCount((prevCount)=> prevCount + 1);
  },[]);

  return (
    <div>
      <p>Count: {count}</p>
      <ChildComponent onClick={incrementCount} />
    </div>
  );
}
```
---

#### Reference to medium article:

https://medium.com/@ownger/how-to-avoid-excessive-re-rendering-of-react-components-c6b9a5f0c722
