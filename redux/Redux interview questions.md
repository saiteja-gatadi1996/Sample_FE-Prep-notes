## 1.  What is Redux?
   
- Redux **is a predictable state container** for JavaScript applications. *(Yes, it can be used with any other JavaScript framework or library)*. 
- It ***helps you write applications that <ins>behave consistently</ins>, run in different environments*** (client, server, and native), and are easy to test.
-  With Redux, **<ins>the entire state of your application is kept in a store</ins>**, **and <ins>each component can access any state *without having to send down props* from one component to another</ins> that it needs from this store**.

- ##### There are `three` building parts: `actions`, `store`, and `reducers`.

#### Benefits and limitations of Redux:

**1. <ins>State transfer**</ins>

- State is stored together in a single place called the ‘store.’ 
- While you do not need to store all the state variables in the ‘store,’ it is especially important to when state is being shared by multiple components or in a more complex architecture. 
- It also allows you to call state data from any component easily.

**2. <ins>Predictability**</ins>

- Redux is **predictable state container for Javascript apps.**
- Because reducers are pure functions, the same result will always be produced when a same state and action are passed in.

**3. <ins>Maintainability**</ins>

- Redux provides a strict structure for how the code and state should be managed, which makes the architecture easy to replicate and scale for somebody who has previous experience with Redux.

**4. <ins>Ease of testing and debugging**</ins>

Redux makes it easy to test and debug your code since it offers powerful tools such as Redux DevTools in which you can time travel to debug, track your changes, and much more to streamline your development process.


-----

## 2. Explain pros and cons of Redux?

### Pros using redux:
- Central store (any component can access any state from the store)
- Store **<ins>persists the state of a component</ins> *even after the component has unmounted***.
- ***Prevents unnecessary re-renders***, as when the state changes <ins>**it returns new state which uses shallow copy.**</ins>
- Testing will be easy as UI and data management are separated.
- **History of state is maintained** which helps in implementing features like undo very easily.


### Cons using redux:
- No encapsulation. Any component can access the data which can cause security issues.
- Boilerplate code. Restricted design.
- ***As state is immutable in redux, the reducer updates the state by returning a new state every time*** which can cause excessive use of memory.

-----

## 3. Explain the concept of a `thunk` in Redux.
- Redux Thunk is a middleware that **lets you call action creators <ins>that return a function instead of an action object</ins>**. 
- The `primary` use of Redux Thunk is to ***handle asynchronous operations*** within the Redux ecosystem
- It **provides a way to delay the dispatch of an action, or to dispatch only if a certain condition is met**. 
- This capability is particularly useful for complex synchronous logic, such as conditional dispatching of actions, or for asynchronous processes like API calls.

<br/>

- <ins>**Asynchronous Actions**</ins>: In standard Redux, action creators return an action object, and these actions are immediately dispatched by the store.** Redux Thunk extends this model by allowing action creators to return a function**. This function can perform asynchronous operations (e.g., API requests) and dispatch actions based on the outcome of those operations.
<br/>

- <ins>**Conditional Dispatching**</ins>: Redux Thunk **allows for conditional dispatching of actions within its returned function**. This is useful when you want to dispatch actions only if certain conditions are met, avoiding unnecessary updates to the state or API calls.
<br/>

- <ins>**Complex Synchronous Logic**</ins>: Beyond asynchronous actions, **Thunks can be used to encapsulate complex synchronous logic that needs access to the dispatch method or the current state of the store**. <ins>This keeps the logic outside of components, making them cleaner and focusing them on the UI</ins> rather than on how the state is managed or updated.
<br/>

- <ins>**Access to `Dispatch` and `GetState`**</ins>: The functions returned by thunk action creators **receive the store's dispatch and getState methods as arguments**. This allows the action creators to dispatch other actions or access the current state of the Redux store as needed during asynchronous operations or complex logic.

-----

## 4. Example of a Redux Thunk Action Creator

```js
function fetchUserData(userId) {
  // This function is the thunk and gets dispatch and getState as arguments
  return async (dispatch, getState) => {
    dispatch({ type: 'USER_FETCH_REQUEST', userId });

    try {
      const response = await fetch(`https://api.example.com/user/${userId}`);
      const data = await response.json();
      dispatch({ type: 'USER_FETCH_SUCCESS', userId, data });
    } catch (error) {
      dispatch({ type: 'USER_FETCH_FAILURE', userId, error });
    }
  };
}

```

```js
npm install redux react-redux redux-thunk
```
```js
// Import the required libraries
import React from 'react';
import { createStore, applyMiddleware } from 'redux';
import { Provider } from 'react-redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers'; // Import your root reducer
import AppContent from './AppContent'; // This is your application's main component

// Create the Redux store, applying the thunk middleware
const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
);

function App() {
  return (
    <Provider store={store}>
      <AppContent />
    </Provider>
  );
}

export default App;

```
------

## 5. What are redux core concepts?
   

![alt text](/redux/images_used/redux-components.jpg)

### **1. <ins>Actions in Redux**</ins>
- Actions **are plain JavaScript objects** that represent the payloads of information that send data from your application to your store.
- They are the **only source of information for the store**
- Actions must have a `type` property that indicates the <ins>type of action being performed</ins>. `Types` should typically be **defined as string constants**. 
- Once an action is created, it is dispatched to the store to trigger updates to the state.

##### Key concepts related to actions in Redux:

1. <ins>**Action Creators**</ins>: 
   - These are **functions that create or return an action**. <ins>Instead of directly dispatching an action object, you often use action creators to encapsulate the process of creating an action</ins>.
<br/>
1. <ins>**Action Types**</ins>: 
   - These are usually **defined as string constants** and help identify the action that needs to be performed. Defining them as constants helps avoid typos and provides an easy way to manage all actions in larger applications.
<br/>

1. <ins>**Dispatching an Action**</ins>: 
   - This is the <ins>**process of sending an action to the Redux store to invoke state changes**</ins>. The store's dispatch function is used for this purpose.
<br/>

```js
const ADD_TODO = 'ADD_TODO';

// Action Creator
function addTodo(text) {
  return {
    type: ADD_TODO,
    text
  }
}

// Dispatching an Action (dispatch function is then used to send this action to the Redux store)
dispatch(addTodo('Learn Redux'));
```

### **2. <ins>Reducers**:</ins> 

- Reducers in Redux are **pure functions** that take the `current state` of an application and an `action` as arguments, and ***return a new state***. 
- The term "reducer" comes from the concept of a reducing function in functional programming, which is used to reduce a collection of values down to a single value

#### The key principles of reducers in Redux are:

1. <ins>**Pure Functions**:</ins> 
   - Reducers **must** be pure functions. 
   - This means they **should not produce side effects**, such as API calls or routing transitions, and they should not modify the state passed to them. 
   - Instead, **they should return a new object if any changes are made**.
<br/>

2. <ins>**State Shape**:</ins> 
   - The state shape (structure) is determined by the reducers. 
   - You can have multiple reducers, each managing its own part of the global state. 
   - The Redux <ins>**combineReducers helper function can be used to combine them into a single root reducer**</ins>.
<br/>

3. <ins>**Handling Actions**:</ins> 
   - Reducers **specify how the application's state changes in response to actions**. 
   - <ins>**They use the action's type**</ins> to determine how to transform the current state into a new state.
<br/>

4. <ins>**Immutability**:</ins> 
   - When changing the state, reducers must return a new object or array rather than modifying the existing state. 
   - This immutability principle ensures that Redux can efficiently track changes and update the UI.
<br/>

5. <ins>**Initialization and Resetting:**</ins>
   -  Reducers can set up the initial state and handle actions that reset the state back to the initial state.


```js
const initialState = {
  todos: []
};

function todoReducer(state = initialState, action) {
  switch (action.type) {
    case 'ADD_TODO':
      return {
        ...state,
        todos: [...state.todos, action.text]
      };
    case 'REMOVE_TODO':
      return {
        ...state,
        todos: state.todos.filter(todo => todo !== action.text)
      };
    default:
      return state;
  }
}
```

### **3. <ins>Store in Redux**</ins>

- A Store ***is an object that holds the whole state tree of your application***. 
- Whenever the `store` is updated, <ins>it will update the React components subscribed to it.</ins> 
- The store has the responsibility of `storing`, `reading`, and `updating state`.

```js
import React from 'react'
import { render } from 'react-dom'
import { Provider } from 'react-redux'
import { createStore } from 'redux'
import rootReducer from './reducers'
import App from './components/App'

const store = createStore(rootReducer)
 render (
   <Provider store="{store}">
     <App>
   </App></Provider>,
   document.getElementById('root')
 )
```

### **4. <ins>Dispatching Actions</ins>** 

- ##### This dispatch call sends an action to the store,

```js
store.dispatch({
  type: 'ADD_TODO',
  text: 'Learn Redux'
});

```

### **5. <ins>Subscribing to changes:</ins>**
- used to subscribe data/state from the Store.

```js
store.subscribe()
```

### **6. <ins>Middleware**</ins>

- Middlewares are **used to dispatch async functions**. 
- We configure Middleware's while creating a store.


```js
const store = createStore(reducers, initialState, middleware);
```

----


## 6.  What do you understand by "Single source of truth" in Redux?
  
- refers to the principle that the <ins>***state of your whole application is stored in an object tree within a single store***</ins>. 

- This means that instead of having multiple, possibly inconsistent sources of state scattered throughout your application, there is one central place where the state is managed and stored. 
  
1. <ins>**Predictability**</ins>: 
   - Because there is only one place where the state is stored, it becomes much easier to track changes, debug, and understand how state changes over time
   - This predictability is crucial for large applications, making them easier to maintain.
   <br/>

2. <ins>**Maintainability**</ins>:
   - With all state changes flowing through a centralized store, it's easier to impose rules on how state can be updated, ensuring consistency across the application. 
   - This centralized control aids in maintaining and scaling the application.
   <br/>

3. <ins>**Debugging**:</ins> 
   - The single state tree makes it possible to implement powerful debugging tools, such as logging every state change, traveling back and forth in time to understand how state mutations lead to bugs, and even rehydrating state from a previous session.
   <br/>

4. <ins>**Serialization**:</ins> 
   - Having the entire application state in one place **makes it possible to serialize the state (e.g., to localStorage) and deserialize it later**, potentially enabling features like undo/redo or saving the state of the application to be resumed later.
   <br/>

5. <ins>**Simplifies Data Flow**:</ins> 
   - The single source of truth simplifies data flow in the application by **adhering to unidirectional data flow**, <ins>*where state flows down from the store to the UI components*</ins>, and actions flow up from the components to update the state.

   <br/>

------

## 7. What are the features of Workflow in Redux?


- When using Redux with React, **states will no longer need to be lifted up**. Everything is handled by Redux. 
- Redux offers a solution for **storing all your application state in one place**, called a store.
- Components then **dispatch state changes to the store**, not directly to other components.
- The components **that need to be aware of state changes can subscribe to the store**.
- The store can be thought of as a "middleman" for all state changes in the application.
- With Redux involved, <ins>components don't communicate directly with each other</ins>. **Rather, all state changes must go through the single source of truth**, the store.

-----

## 8. Redux has three core principles:

1. <ins>**Single Source of Truth**:</ins> 
   -    The state of your whole application is stored in an object tree within a single store.

2. <ins>**State Is Read-Only**:</ins> 
   - The only way to change the state is to dispatch an action, an object describing what happened.
3. <ins>**Changes Are Made With Pure Functions**:</ins> 
   - To specify how the state tree is transformed by actions, you write pure reducers.


### The following are details of how Redux works:
- When UI Event triggers (OnClick, OnChange, etc) it can dispatch Actions based on the event.
- Reducers process Actions and return a new state as an Object.
- The new state of the whole application goes into a single Store.
- Components can easily subscribe to the Store.

-------

## 9.  What is difference between presentational component and container component in react redux?
    
- ***Represent a <ins>pattern for organizing code</ins>*** that helps in managing complexity, particularly in large applications. 
- This pattern helps in separating the concerns between how things look (UI) and how things work (logic and state management). 

##### Here's a breakdown of the differences:


###<ins>**Container Components**:</ins> 
   
- **Purpose**: 
  - Container components are **concerned with how things work**. They provide the `data` and `behavior` to presentational or other container components.
<br/>

- **State**: 
  - They are **more likely to maintain state and handle state updates**. They connect to the Redux store and dispatch actions to update the store based on user interactions.
<br/>

- **Redux**: 
  - They use Redux-specific functions like `connect` (in React-Redux bindings) to read from a Redux store and dispatch actions. With the introduction of hooks in React, container components might also use hooks like `useSelector` and `useDispatch` for a similar purpose.
<br/>

- **Reusability**: 
  - They are **less reusable since they are tightly coupled** with the business logic and data fetching mechanisms.

<ins>**Example**</ins>: A TodoListContainer component that fetches todo items from the Redux store and passes them to a TodoList presentational component to render.






### <ins>**Presentational Components**:</ins> 

- **Purpose**: 
  - Are primarily **concerned with how things look**. They render the UI based on the props passed to them.
<br/>

- **State**: 
  - They **usually don't manage state** (except for local UI state) and **receive data and callbacks exclusively via `props`**.
<br/>

- **Redux**: 
  - They are unaware of Redux. **They don't dispatch actions or directly interact with the Redux store**.
<br/>

- **Reusability**: 
  -  Since they focus on the UI without embedding business logic, they tend to be more reusable across different parts of the application or even in different applications..

<ins>**Example**</ins>: Button component that receives a label and an onClick callback as props.


- #### It's worth noting that with the advent of React Hooks (useState, useEffect, useContext, useReducer, and custom hooks), the distinction between presentational and container components <ins>*has become less clear and less necessary*</ins>.

----
## 10.  How to split the reducers?

- In Redux, splitting reducers is a common practice to manage the complexity of handling a large state object. 
- This process is known as `"reducer composition"` and is **facilitated by the combineReducers utility function provided by Redux**. 
- The <ins>***idea is to create multiple smaller reducer functions, each managing its own slice of the state, and then combine them into one root reducer</ins>***. Each of these smaller reducers is responsible for updating a specific piece of state based on the action dispatched.

#### Here's a step-by-step guide on how to split reducers:

### 1. <ins>Create Individual Reducers</ins>

```js
// todosReducer.js
function todosReducer(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return [...state, action.payload];
    case 'REMOVE_TODO':
      return state.filter(todo => todo.id !== action.payload);
    // Add other cases as needed
    default:
      return state;
  }
}

// visibilityFilterReducer.js
function visibilityFilterReducer(state = 'SHOW_ALL', action) {
  switch (action.type) {
    case 'SET_VISIBILITY_FILTER':
      return action.payload;
    // Add other cases as needed
    default:
      return state;
  }
}
```
### 2. <ins>Combine Reducers</ins>



```js
import { combineReducers } from 'redux';
import todosReducer from './todosReducer';
import visibilityFilterReducer from './visibilityFilterReducer';

const rootReducer = combineReducers({
  todos: todosReducer,
  visibilityFilter: visibilityFilterReducer,
});

export default rootReducer;

```

### 3. <ins>Create the Redux Store</ins>

```js
import { createStore } from 'redux';
import rootReducer from './reducers'; // The combined reducers

const store = createStore(rootReducer);
```

----
# <--- SAMPLE CONTENT ENDS --->
