### 1. What is JSX?

JSX stands for JavaScript XML. JSX allows us to write HTML in React. JSX makes it easier to write and add HTML in React.

### 2.

![image](https://user-images.githubusercontent.com/42731246/151151328-2a575f80-1e86-4f4a-b9ab-a6f9197e7344.png)

### 3. What is SPA?

An SPA (Single-page application) is a web app implementation that loads only a single web document, and then updates the body content of that single document via JavaScript APIs such as XMLHttpRequest and Fetch when different content is to be shown.

This therefore allows users to use websites without loading whole new pages from the server, which can result in performance gains and a more dynamic experience, with some tradeoff disadvantages such as SEO, more effort required to maintain state, implement navigation, and do meaningful performance monitoring.

### 4. Render prop

The term “render prop” refers to a technique for sharing code between React components using a prop whose value is a function.

```js
class Cat extends React.Component {
  render() {
    const mouse = this.props.mouse;
    return (
      <img
        src='/cat.jpg'
        style={{ position: 'absolute', left: mouse.x, top: mouse.y }}
      />
    );
  }
}

class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY,
    });
  }

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>
        {/*
          Instead of providing a static representation of what <Mouse> renders,
          use the `render` prop to dynamically determine what to render.
        */}
        {this.props.render(this.state)}
      </div>
    );
  }
}

class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>Move the mouse around!</h1>
        <Mouse render={(mouse) => <Cat mouse={mouse} />} />
      </div>
    );
  }
}
```

### 5. ServiceWorker vs Web Worker?

#### ServiceWorker:

Rich offline experiences, periodic background syncs, push notifications. A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction.The reason this is such an exciting API is that it allows you to support offline experiences, giving developers complete control over the experience.

It's a JavaScript Worker, so it can't access the DOM directly. Instead, a service worker can communicate with the pages it controls by responding to messages sent via the postMessage interface, and those pages can manipulate the DOM if needed.

#### Web Worker:

Web Workers are a simple means for web content to run scripts in background threads. The worker thread can perform tasks without interfering with the user interface. In addition, they can perform I/O using XMLHttpRequest (although the responseXML and channel attributes are always null) or fetch (with no such restrictions). Once created, a worker can send messages to the JavaScript code that created it by posting messages to an event handler specified by that code (and vice versa).

### 6. Lazy Loading/Code Splitting?

It is a new function in react that lets you load react components lazily through code splitting without help from any additional libraries. Lazy loading is the technique of rendering only-needed or critical user interface items first, then quietly unrolling the non-critical items later.

lazy(() => import('./OtherComponent')); This will automatically load the bundle containing the OtherComponent when this component is first rendered. React. lazy takes a function that must call a dynamic import() .

Code-splitting your app can help you “lazy-load” just the things that are currently needed by the user, which can dramatically improve the performance of your app. While you haven’t reduced the overall amount of code in your app, you’ve avoided loading code that the user may never need, and reduced the amount of code needed during the initial load.

Before:

```js
import { add } from './math';

console.log(add(16, 26));
```

After:

```js
import('./math').then((math) => {
  console.log(math.add(16, 26));
});
```

#### React.lazy

Before:

```js
import OtherComponent from './OtherComponent';
```

After:

```js
const OtherComponent = React.lazy(() => import('./OtherComponent'));
```

React.lazy currently only supports default exports. If the module you want to import uses named exports, you can create an intermediate module that reexports it as the default. This ensures that tree shaking keeps working and that you don’t pull in unused components.

### 7. SEO in React?

Prerendering, Server Side rendering, Isomorphic React apps, Next.js

### 8. D3.js?

### 9. Reconciliation?

Reconciliation is the process through which React updates the DOM. When a component's state changes, React has to calculate if it is necessary to update the DOM. It does this by creating a virtual DOM and comparing it with the current DOM. In this context, the virtual DOM will contain the new state of the component.

The process of checking the difference between the new VDOM tree and the old VDOM tree is called "diffing".

### 10. Testing libraries?

### 11. Babel and Webpack?

<u>**Babel**:</u>

- Babel is a transpiler that compiles JavaScript new code to JavaScript old ones allowing you to write JavaScript “from the future” so that current browsers will understand it

<u>**Webpack**:</u>

- Webpack is a modular build tool that has two sets of functionality —> Loaders and Plugins.
- Loaders <u>**_transform the source code of a module_**</u>.
- For example, <u>**_style-loader adds CSS to DOM_**</u> using style tags. <u>**_sass-loader compiles SASS files to CSS_**</u>. babel-loader transpile JS code given the presets.
- Plugins are the core of Webpack. They can do things that loaders can't.
- For example, there is a <u>**_plugin called UglifyJS that minifies and uglifies the output of webpack_**.</u>

### 12. Disadvantages of React?

i) ReactJS Covers only the UI Layers of the app and nothing else. So you still need to choose some other technologies to get a complete tooling set for development in the project.

ii) ReactJS uses JSX. It's a syntax extension that allows HTML with JavaScript mixed together. This approach has its own benefits, but some members of the development community consider JSX as a barrier, especially for new developers. Developers complain about its complexity in the learning curve.

### 13. Super keyword?

super() will calls the constructor of its parent class. This is required when you need to access some variables from the parent class. In React, when you call super with props. React will make props available across the component through this.props .

### 14. This keyword?

The JavaScript this keyword refers to the object it belongs to. ... In a function, this refers to the global object. In a function, in strict mode, this is undefined . In an event, this refers to the element that received the event. Methods like call() , and apply() can refer this to any object.

### 15. Fetch vs Axios?

Key Differences: With Axios, the data is sent through the data property of the options, but Fetch API uses the body property. Fetch response requires additional validation as it always returns a response object no matter whether it is successful or not. The data in fetch() has been serialized to a String (Stringified).

![image](https://user-images.githubusercontent.com/42731246/151424487-44dc66a1-2beb-45ca-aa00-15d2903969b7.png)

### 16. Render() vs return()

Essentially render is kind of a lifecycle method which is invoked whenever the component needs to update.

In react, render is a method that tell react what to display. return in a method or function is the output of the method or function

### 17. PropsType?

PropTypes is a library that helps in minimizing this problem in React by checking the types passed in the props object against a specification we set beforehand and to raise a warning if the types passed don't match the types expected.

### 18. Differences between Class Components vs Functional Components?

#### Functional Components

i) A functional component is just a plain JavaScript function that accepts props as an argument and returns a React element.

ii) There is no render method used in functional components.

iii)React lifecycle methods (for example, componentDidMount) cannot be used in functional components. Constructors are not used .React lifecycle methods can be used inside class components (for example, componentDidMount).

#### Class Components:

i)A class component requires you to extend from React Component and create a render function which returns a React element.

ii)It must have the render() method returning HTML.

iii)Constructor are used as it needs to store state.

### 19. Lifecycle methods in react javascript? Explain each and every?

### 20. Correct sequence of constructor, render, componentDidMount, componentWillMount?

### 21. What is the use of hooks?

Hooks allow you to use local state and other React features without writing a class.
Hooks are the new feature introduced in the React 16.8 version.

### 22. Some of the hooks and their example

### 23. useCallback hooks usage

### 24. What is HOC

![image](https://user-images.githubusercontent.com/42731246/151151594-44c9033f-d185-4b17-8dfe-e67faf004ba1.png)

### 25. How to add one component in another

Ans:
![image](https://user-images.githubusercontent.com/42731246/151151609-3bd82e2a-e6f2-4790-bd63-3caee331358c.png)

### 26. How to pass function (ex: addTodo) from Parent component to Child?

![image](https://user-images.githubusercontent.com/42731246/151151624-04da35e2-1925-4f22-83a0-b95def36de59.png)

### 27. What is redux

![image](https://user-images.githubusercontent.com/42731246/151427141-83f2e284-7a13-49da-aebf-3f265901728c.png)

Ans: Redux is a predictable state container that helps in storing the entire application state by avoiding prop-drilling.

### 28. What is store?

A store holds the whole state tree of your application. The only way to change the state inside it is to dispatch an action on it.
A store is not a class. It's just an object with a few methods on it. To create it, pass your root reducing function to createStore.

### 29. How to communicate both the Child elements without props?

### 30. Components of redux

There are three building parts: actions, store, and reducers.

#### Actions in Redux

Simply put, actions are events. They are the only way you can send data from your application to your Redux store.

Actions are sent using the store.dispatch() method. Actions are plain JavaScript objects, and they must have a type property to indicate the type of action to be carried out. They must also have a payload that contains the information that should be worked on by the action. Actions are created via an action creator.

Here’s an example of an action that can be carried out during login in an app:

```js
const setLoginStatus = (name, password) => {
  return {
    type: 'LOGIN',
    payload: {
      username: 'foo',
      password: 'bar',
    },
  };
};
```

#### Reducers in Redux

Reducers are pure functions that take the current state of an application, perform an action, and return a new state. These states are stored as objects, and they specify how the state of an application changes in response to an action sent to the store.

As pure functions, they do not change the data in the object passed to them or perform any side effect in the application. Given the same object, they should always produce the same result.

```js
const LoginComponent = (state = initialState, action) => {
  switch (action.type) {
    // This reducer handles any action with type "LOGIN"
    case 'LOGIN':
      return state.map((user) => {
        if (user.username !== action.username) {
          return user;
        }

        if (user.password == action.password) {
          return {
            ...user,
            login_status: 'LOGGED IN',
          };
        }
      });
    default:
      return state;
  }
};
```

### Store in Redux

The store holds the application state. It is highly recommended to keep only one store in any Redux application. You can access the state stored, update the state, and register or unregister

listeners via helper methods.

```js
import { Provider } from 'react-redux';
import store from './store/store';
import { BrowserRouter as Router } from 'react-router-dom';

ReactDOM.render(
  <Provider store={store}>
    <React.StrictMode>
      <App />
    </React.StrictMode>
  </Provider>,
  document.getElementById('root')
);
```

### 31. Principles of Redux?

a. Single source of truth. The global state of your application is stored in an object tree within a single store.

```js
console.log(store.getState());
```

b. State is read-only. The only way to change the state is to emit an action, an object describing what happened. ...

The only way to change the state is to emit an action, an object describing what happened.

c. Changes are made with pure functions.
To specify how the state tree is transformed by actions, you write pure reducers.

### 32. Redux thunk middleware?

### 33. Difference between props and state

Ans: Both store information of the components but state is managed within the component whereas props is used to pass the data from parent to child component.

### 34. Is react support two-way binding.

Ans: React support Uni Directional data binding. i.e(from Parent to child),

### 35. What is ref in react?

Ans: Refs are a function provided by React to access the DOM element and the React element that you might have created on your own. They are used in cases where we want to change the value of a child component, without making use of props and all.

### When to Use Refs

There are a few good use cases for refs:

Managing focus, text selection, or media playback.
Triggering imperative animations.
Integrating with third-party DOM libraries.

### 36. How to focus the filed when the component is loaded

Ans:
![image](https://user-images.githubusercontent.com/42731246/151151731-93cd7a49-629c-436e-9253-3a7b34fdac9b.png)
![image](https://user-images.githubusercontent.com/42731246/151151743-9c469641-42db-4055-b6bc-3ebdcff93b2d.png)

### 37. What is the use of reducers?

A reducer is a function which takes two arguments — the current state and an action — and returns based on both arguments a new state

![image](https://user-images.githubusercontent.com/42731246/151151769-23860186-440c-42e2-867e-89ec487fdfbf.png)

### 38. Can I have more than one store in one application

Ans: No, in redux

### 39. How to pass data from A to C

Ans: Declare C component in A component

### 40. What is context API

React's context allows you to share information to any component, by storing it in a central place and allowing access to any component that requests it (usually you are only able to pass data from parent to child via props).

### 41. Import vs required

Ans The major difference between require and import , is that require will automatically scan node_modules to find modules, but import , which comes from ES6, won't. Most people use babel to compile import and export , which makes import act the same as require .

### 42. Explain ES6 Features,

1. const and let keywords
2. forEach, map, filter, every, some, find,
3. Arrow functions
4. Classes
5. Enhanced Object literals
6. Template strings
7. Rest and spread operators
8. Destructuring
9. Promises

### 43. What is the use of Object Destructuring?

It's a JavaScript feature that allows us to extract multiple pieces of data from an array or object and assign them to their own variables.

### 44. How I can migrate from current React 15 project to React 16.8?

### 45. Virtual DOM vs Shadow DOM?

Ans: Virtual DOM is creating a copy of the whole DOM object, and Shadow DOM creates small pieces of the DOM object which has their own, isolated scope for the element they represent.

### 46. How to control the re- render cycle in react js

Ans: useMemo()- stores the state in cache and prevents unnecessary rerenders

### 47. useMemo vs memo

Ans: Both memo and useMemo are used to memoize the result of a function, the only difference is memo is a HOC (and can be used to wrap both class and functional components) which useMemo is a hook (and can only be used inside functional components)

### 48. combineReducers?

The combineReducers helper function turns an object whose values are different reducing functions into a single reducing function you can pass to createStore . The resulting reducer calls every child reducer, and gathers their results into a single state object.

### 49. What actually setState does in Class components?

### 50. Client-side rendering vs Server-side Rendering?

### 51. setState inside constructor?

setState" causes React to re-render your application and update the DOM. If you use setState in constructor you would get error like this:Can only update a mounted or mounting component. This usually means you called setState() on an unmounted component.

### 52. What is strict mode react?

StrictMode is a tool for highlighting potential problems in an application. Like Fragment, StrictMode does not render any visible UI. It activates additional checks and warnings for its descendants. Note: Strict mode checks are run in development mode only; they do not impact the production build.

### 53. Error boundaries

If the other module fails to load (for example, due to network failure), it will trigger an error. You can handle these errors to show a nice user experience and manage recovery with Error Boundaries. Once you’ve created your Error Boundary, you can use it anywhere above your lazy components to display an error state when there’s a network error.

```js
import React, { Suspense } from 'react';
import MyErrorBoundary from './MyErrorBoundary';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

const MyComponent = () => (
  <div>
    <MyErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </MyErrorBoundary>
  </div>
);
```

### 54. When should we use arrow functions with React?

##### Arrow functions in React are used primarily for two reasons:

- their concise syntax
- the way they handle the `this` keyword.

**Concise Syntax:**

1. ##### Arrow functions are commonly used for event handlers

```js
const MyComponent = () => {
  const handleClick = () => {
    console.log('Button clicked');
  };

  return <button onClick={handleClick}>Click me</button>;
};
```

2. ##### In class components, arrow functions can be used to automatically bind methods

```js
class MyComponent extends React.Component {
  handleClick = () => {
    console.log('Button clicked');
  };

  render() {
    return <button onClick={this.handleClick}>Click me</button>;
  }
}
```

3. ##### Custom Hooks: Due to their concise syntax and readability.

```js
const useCustomHook = () => {
  // Hook logic here
};
```

4. ##### Inline Event Handlers

```js
<button onClick={() => console.log('Button clicked')}>Click me</button>
```

#### When not to use arrow functions?

- Avoid using arrow functions in render methods or **_functional components that re-render frequently_**, as they create new instances of the function on each render, potentially leading to performance issues.

- Using arrow functions **_inside dependency arrays of hooks like useEffect_**. Since they are recreated on each render, they can cause unnecessary re-runs of effects.

### 55. How can automated tooling be used to improve the accessibility of a React application?

##### There are two main categories:

**- Static Analysis Tools**:

- Linting tools like **ESLint** can be used with plugins such as <u>**_eslint-plugin-jsx-a11y_** </u> **_to analyze React projects at a component level._**

**- Browser Tools**:

- Browser accessibility tools such as <u>**_aXe_**</u> and <u>**_Google Lighthouse_**</u> perform automated accessibility at the app level.

---

### 56. Why should not we update the state directly?

- **Updating the state directly** is a common pitfall that **_can lead to several issues_**
- **When you update the state directly** (i.e., mutating the state), <u>**_React won't be aware of the changes_**</u>, and as a result, the component won't re-render.

<u>**Points to remember on why not to update state directly:**</u>

- React's design philosophy **_treats state as immutable_**. This means once a state is set, you do not modify it directly. **_Instead, you should use the setState method_** (or the state updater function with hooks) to change the state.

<br/>

- **Component Will Not Re-render:** If you mutate the state directly, React will not know that the state has changed because setState or the state updater function from hooks also triggers the re-render process.

<br/>

- **Unexpected Behavior in Component Lifecycle:** Mutating state directly can **_lead to unexpected behavior_** in various lifecycle methods, **as React relies on the previous state to determine if a re-render is necessary**.

```js
//Wrong way
function MyComponent() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    count = count + 1; // Wrong: Directly mutating state
    console.log(count); // This might log the updated count
  };

  return (
    <div>
      <button onClick={handleIncrement}>Increment</button>
      <p>{count}</p> {/* This won't update as expected */}
    </div>
  );
}
```

```js
//correct way
function MyComponent() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <button onClick={handleIncrement}>Increment</button>
      <p>{count}</p> {/* This will update correctly */}
    </div>
  );
}
```

---

### 57. How can find the version of React at runtime in the browser?

- Chrome Dev Tools

```js
window.React.version;
```

---

### 58. How to use https instead of http in create-react-app?

- set the HTTPS environment variable to true, then start the dev server as usual with npm start:

```js
#Windows
set HTTPS=true && npm start
```

---

### 59. React Router Features

1. **useHistory**

- Provides access to the history prop
- Refers to the history package dependency that the router uses
- primary use case would be for push, replace

```js
import { useHistory } from 'react-router-dom';

function Home() {
  const history = useHistory();
  return <button onClick={() => history.push('/profile')}>Profile</button>;
}
```

2. **useLocation**

- similar to **window.location** in the browser itself, <u>but this is accessible everywhere</u> as it represents the Router state and location.
- A primary use case for this would be <u>**_to access the query params or the complete route string_**.</u>

```js
import {useLocation} from 'react-router-dom'
import React, {useEffect} from 'react'


function Profile(){
  const location = useLocation()
   useEffect(()=>{
    const currentPath = window.location.pathname
    const searchParams = new URLSearchParams(location.search)
   })
},[location]

return <p>Profile</p>
```

3. **useParams**

- provides access to search params in the URl

```js
import { useParams, Route } from 'react-router-dom';

function Profile() {
  const { name } = useParams();
  return <p>{name}'s Profile</p>;
}

function Dashboard() {
  return (
    <>
      <nav>
        <Link to={`/profile/alex`}>Alex Profile</Link>
      </nav>
      <main>
        <Route path='/profile/:name'>
          <Profile />
        </Route>
      </main>
    </>
  );
}
```

---

### 60. What is the difference between NavLink and Link?

- The Link component is used to navigate the different routes on the site
- NavLink is used to add the style attributes to the active routes

```js
<Link to='/'>Home</Link>
```

```js
<NavLink to='/' activeClassName='active'>
  Home
</NavLink>
```

```js
// index.css
.active {
  color: blue;
}
```

---

### 61. What is withRouter for in react-router-dom?

- withRouter() is a higher-order component that allows to get access to the history object's properties and the closest <Route>'s match.
- It is **_used to pass updated match, location, and history props to a functional component_** whenever it renders.

```js
import React from 'react';
import { withRouter } from 'react-router-dom';

const MyComponent = (props) => {
  // Accessing the history, location, and match props
  const { history, location, match } = props;

  // Example usage: Navigate to a different route
  const navigateToHome = () => {
    history.push('/');
  };

  // Example usage: Read data from the URL
  const productId = match.params.id;

  return (
    <div>
      <h1>Product ID: {productId}</h1>
      <button onClick={navigateToHome}>Go Home</button>
      <p>Current location: {location.pathname}</p>
    </div>
  );
};

export default withRouter(MyComponent);
```
