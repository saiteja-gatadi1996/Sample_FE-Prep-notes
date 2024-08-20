```js
- This was near about to 1 hour round,
- conducted by 1 senior and 1 lead,  
- senior dev took the first 30 mins and it was on theory discussion
- Then followed by System Design Question from the Lead
```

----
## Theory:

### 1. What is asynchronous programming in javascript?

<details>

- Asynchronous programming is a programming paradigm that **facilitates `non-blocking` operations**, 
- <ins>**allowing a program to perform tasks concurrently *without waiting for each task to complete* before moving on to the next one**</ins>.


#### Key Concepts of Asynchronous Programming:
1. **Non-blocking Operations**: 
   - In `synchronous` programming, the program execution **blocks or waits** for an operation to complete `before` moving to the next line of code. 
   - `Asynchronous` programming, however, `allows` the execution to proceed to the next operations **without** **waiting** for the previous ones to complete.
<br/>

2. **Concurrency**: 
   - `Asynchronous` programming **enables** **concurrency**, which involves <ins>**making progress on multiple tasks simultaneously**</ins>. 
   - This doesn't necessarily mean that tasks are completed at the same time but rather that <ins>**multiple tasks can be in progress at once**</ins>, optimizing the usage of available resources.
<br/>

3. **Event Loop**: 
   - Many `asynchronous` programming environments **use an event loop** that continuously checks for and manages events or tasks that need to be executed.
   - This loop plays a crucial role in managing and dispatching tasks as they become ready for execution.
<br/>

4. **Callbacks**: 
   - A common pattern in `asynchronous` programming involves `callbacks`. 
   - A callback is <ins>**a function that is specified to run after a task completes**</ins>. 
   - However, excessive use of callbacks can lead to complex and hard-to-manage code, often referred to as "`callback hell`."
<br/>

5. **Promises**: 
   - To `address` some of the challenges of callbacks, `promises` are used as abstractions that represent the completion or failure of an asynchronous operation. 
   - They <ins>**simplify the chaining of operations and improve error handling**.</ins>
<br/>

6. **Async/Await**: 
   - Modern programming languages like JavaScript implement `async/await` syntax <ins>**to make asynchronous code easier to write and read**.</ins> 
   - The `async` keyword is used to declare a function that handles asynchronous operations, 
   - and `await` is **used <ins>to pause the execution of the function until a Promise is resolved or rejected</ins>**.

#### Benefits of Asynchronous Programming:
- **Improved Performance**: 
  - By **`not`** blocking the main thread with time-consuming operations, applications **can remain responsive** to user interactions or other critical tasks.
<br/>

- **Resource Efficiency**: 
  - `Asynchronous` programming **can lead to <ins>more efficient use of system resources</ins>**, particularly in I/O-bound and network-bound scenarios.
<br/>

- **Scalability**: 
  - Applications designed with `asynchronous` principles <ins>**can handle more operations with fewer resources**</ins>, thus scaling better as user demand increases.
<br/>

#### Applications:
- **Web Development**: 
  - Handling HTTP requests, 
  - performing API calls, 
  - and interacting with databases without blocking user interactions.
<br/>

- **Data Processing**: 
  - Large-scale data processing where tasks can be distributed and handled in parallel.
<br/>

- **Real-time Systems**: 
  - Systems like chat applications or live updates where immediate response to user actions is crucial.

<summary>
View Answer
</summary>
</details>




----

### 2. What are promises ?

<details>

- `Promises` are a fundamental concept in `asynchronous` programming, 
- A `Promise` represents a placeholder for the eventual result of an asynchronous operation. 
- Essentially, <ins>**it's an object that encapsulates the state of an operation that will complete at some point in the future, either `successfully` or with an `error`**</ins>.

#### Key Features of Promises:
- `States`: A promise can be in one of three states:
- `Pending`: The **initial state** of the promise. The operation has not completed yet.
- `Fulfilled`: The operation **completed** successfully, and the promise now holds the resulting value.
- `Rejected`: The operation **failed**, and the promise holds the reason for the failure.
- `Immutability`: Once a promise resolves to either a fulfilled or rejected state, **it cannot change its state again**. 
  - The value or the rejection reason it holds becomes immutable, and all further attempts to `resolve` or `reject` it are ineffective.

#### Creating a Promise:
```js
let promise = new Promise((resolve, reject) => {
    // Asynchronous operation code
    setTimeout(() => {
        if ("operation_successful") {
            resolve("Data retrieved");
        } else {
            reject("Error occurred");
        }
    }, 2000);
});
```
```js
//USAGE OF PROMISES (DON'T FORGET THIS😁)

promise.then((data) => {
    console.log(data);  // Handle success
}).catch((error) => {
    console.error(error);  // Handle error
});
```
<summary>
View Answer
</summary>
</details>

--- 

### 3. Difference between Redux saga vs Redux Thunk?


<details>

- Both are `middleware` libraries **for managing side effects** in Redux-based applications, 
- but they use `different` approaches and philosophies for handling asynchronous operations. 

#### <ins>Redux Thunk:</ins>
- Allows you to <ins>**write action creators that return a function instead of an action**.</ins> 
- The function **`can`** contain asynchronous logic and can `dispatch actions` at appropriate times.

#### <ins>Key Features:</ins>
- **Simplicity**: 
  - `Thunks` are straightforward to use and easy to integrate, making them an **excellent choice for simple scenarios**.
<br/>

- **Flexibility**: 
  - You can ***include*** both `synchronous` and `asynchronous` logic **<ins>inside a single thunk**</ins>.
<br/>

- **Control**: 
  - Thunks give you **direct control over the dispatch process**, allowing you to dispatch multiple actions in response to asynchronous events.

#### <ins>Usage:</ins>
- Thunks are primarily **used for <ins>simple asynchronous operations</ins>** like API calls, 
- where you might want to <ins>**dispatch an action when a request starts and another when it completes**</ins>.

#### <ins>Redux Saga:</ins>

- Redux Saga uses ES6 generator functions to make asynchronous flows easy to read, write, and test. 
- It **handles complex scenarios more seamlessly than thunks** due to its declarative approach and powerful suite of effects.

#### <ins>Key Features:</ins>

- **Declarative Approach**: 
  - Sagas use `yield` statements to express asynchronous flows in a synchronous-like manner, which can be easier to manage and reason about.
- **Effect Creators**: 
  - These are functions provided by Redux Saga that return plain JavaScript objects describing the intended side effect, which keeps your saga logic pure.
- **Testing**: 
  - Testing sagas is generally more straightforward because you can test the generator functions by checking the yielded effects without performing the actual side effect.
- **Concurrency Management**: 
  - Sagas offer built-in ways to handle common concurrent patterns, such as starting, pausing, and cancelling tasks.

#### <ins>Usage</ins>:
- `Sagas` are **beneficial** for <ins>**handling complex sequences of asynchronous operations**</ins>. 
- and scenarios **where you <ins>need fine-grained control over side effects**</ins>, 
- **`concurrency`**, or where related asynchronous operations might overlap.
<summary>
View Answer
</summary>
</details>




----

### 4. Which one you would prefer and why? (Class components vs React Hooks)

<details>

### Class Components
**Syntax**: 
Class components use ES6 classes and extend React.Component.

**State**: 
They maintain local state using this.state.

**Lifecycle Methods**: 
Support lifecycle methods directly (**`componentDidMount`**, **`componentDidUpdate`**, etc.).

**Event Handling**: 
Use this for event handlers that must be bound explicitly, or use arrow functions to retain the context.

----

### Functional Components
**Syntax**: 
Functions that receive props as an argument and return JSX.

**State & Side Effects**: 
Use hooks (useState, useEffect, etc.) for state management and side effects.

**Simplicity**: 
Smaller and simpler code structure.

**Performance**: 
Potentially more performant due to the lack of this and lifecycle methods.

### When to Use Which?

#### Use Functional Components If:
- You want to write **`concise`**, **`readable`**, and **`maintainable`** code.
- You don't require lifecycle methods explicitly or are comfortable using hooks for similar functionality.
- The component is relatively **`simple`** and doesn't need complex logic.


#### Use Class Components If:
- You're maintaining **`legacy`** code or adding features to existing class components.
- Your team or existing codebase uses class components consistently.


### General Recommendation:

- Modern best practice leans towards functional components due to the powerful and flexible hooks API.
- If starting new projects or refactoring old code, it's beneficial to use functional components whenever possible.

<summary>
View Answer
</summary>
</details>

-----

### 5. Git commit strategy

<details>

**1. Commit Frequency**
- Commit `often` and `early`. 
- Frequent commits help in keeping track of changes incrementally and make it easier to locate and understand changes, or revert them if necessary.

**2. Atomic Commits**
- Each commit **should represent <ins>a single logical change</ins>**. 
- This makes the commit history easier to understand and debug. 

**3. Commit Messages**
- Good commit messages are critical. 
- They <ins>**should clearly explain what the commit does and why the change is needed**</ins>, not just what was changed.

**4. Branching Strategy**
- **Ex1**: Feature Branch Workflow: Developers create branches for each new feature, keeping the main branch clean.
- **Ex2**: branching model designed around project releases, which distinguishes between different types of branches: feature, release, and hotfix.

**5. Commit Revisions**
- `Before` committing, it's good practice **to use git diff to review your changes** or git add -p to interactively choose chunks of code to commit. 
- This helps in <ins>**making sure only intended changes are committed**</ins>.

**6. Squashing and Rebase**
- `Squashing` turns <ins>**many commits into a single commit</ins>**, which can make the history cleaner and more understandable. 
- `Rebasing` is another technique used to **maintain a clean project history by moving or <ins>combining a sequence of commits to a new base commit</ins>**.

**7. Commit Tags**
- `Tags` are typically **used for marking releases** (v1.0, v2.0) and are immutable points that <ins>can help in rolling back to stable states in production</ins>.
<summary>
View Answer
</summary>
</details>

---

## Practical:

### Given a trading application and there are two lists
- one list is for `getAllStocks`
- second list is for saving the stocks
- Whenever a user clicks on a specific stock, it should navigate to that page.

### q1) How can you achieve above functionality?

<details>

- #### To navigate to a specific stock page when a user clicks on a stock from the stock list, you can follow these steps:

**1. Routing Setup**: 
  - Application is set up with React Router and that the stock pages are associated with dynamic routes.

```js
// App.js or a similar main file
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import AllStocks from './components/AllStocks';
import StockDetail from './components/StockDetail';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<AllStocks />} />
        <Route path="/stock/:stockId" element={<StockDetail />} />
      </Routes>
    </Router>
  );
}
```

**2. Click Handler:**
  - Attach a click handler to each stock item in the AllStocks component that uses the **`useNavigate`** hook from React Router to navigate to the corresponding stock page.

```js
// AllStocks.js
import { useNavigate } from 'react-router-dom';

function AllStocks({ stocks }) {
  const navigate = useNavigate();

  const handleStockClick = (stockId) => {
    navigate(`/stock/${stockId}`);
  };

  return (
    <ul>
      {stocks.map(stock => (
        <li key={stock.id} onClick={() => handleStockClick(stock.id)}>
          {stock.name}
        </li>
      ))}
    </ul>
  );
}
```

#### 3. Stock Detail Page: 
  - Create a detail page that extracts the stock ID from the URL parameters to fetch and display the relevant stock information.


```js
// StockDetail.js
import { useParams } from 'react-router-dom';

function StockDetail() {
  const { stockId } = useParams();

  // Fetch stock details with `stockId`

  return <div>Stock Details for {stockId}</div>;
}
```

<summary>
View Answer
</summary>
</details>

----

### q2) What is the scope of `Reusable components` in those two lists ?

<details>

#### 1. Stock List Component:

- A reusable stock list component can be created that accepts an array of stocks and an onClick function as props.

```js
// StockList.js
function StockList({ stocks, onClick }) {
  return (
    <ul>
      {stocks.map(stock => (
        <li key={stock.id} onClick={() => onClick(stock.id)}>
          {stock.name}
        </li>
      ))}
    </ul>
  );
}
```


#### 2. Stock Item Component:
- A reusable stock item component can encapsulate the layout and appearance of each stock item.

```js
// StockItem.js
function StockItem({ stock, onClick }) {
  return (
    <div onClick={() => onClick(stock.id)}>
      <h4>{stock.name}</h4>
      <p>{stock.price}</p>
    </div>
  );
}
```





<summary>
View Answer
</summary>
</details>

----

### q3) If a user `purchase` a stock, how can you update his purchases right away (without `reloading` or `clicking` on back button) ?


<details>

#### 1. State Management: 
  - I said I will use Redux, to maintain a centralized list of purchased stocks.

#### 2. Action Dispatch: 
  - When a purchase is completed, dispatch an action to update the purchased stocks list.

```js
// Purchase action
export const purchaseStock = (stock) => ({
  type: 'PURCHASE_STOCK',
  payload: stock
});


export const revertPurchase = stock => ({
  type: 'REVERT_PURCHASE',
  payload: stock
});

```

#### 3. Reducer
-  Update the reducer to add the new purchase to the state.

```js
// stocksReducer.js
const initialState = {
  purchasedItems: [],
};

function stocksReducer(state = initialState, action) {
  switch (action.type) {
    case 'PURCHASE_STOCK':
      return {
        ...state,
        purchasedItems: [...state.purchasedItems, action.payload]
      };
    case 'REVERT_PURCHASE':
      return {
        ...state,
        purchasedItems: state.purchasedItems.filter(item => item.id !== action.payload.id)
      };
    default:
      return state;
  }
}
```


#### 4. Optimistic UI Update:

- As soon as a purchase is confirmed, update the local state optimistically before waiting for server confirmation. This provides instant visual feedback.

```js
// PurchaseStock.js
import { useDispatch } from 'react-redux';
import { purchaseStock, revertPurchase } from '../actions/purchaseActions';

function PurchaseStock({ stock }) {
  const dispatch = useDispatch();

  const handlePurchase = async () => {
    // Optimistically update the UI
    dispatch(purchaseStock(stock));

    try {
      // Simulate API request
      const response = await fetch('/api/purchase', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(stock),
      });
      const data = await response.json();

      // Handle response based on server confirmation
      if (!response.ok || data.error) {
        throw new Error(data.message || 'Purchase failed');
      }
      console.log('Purchase confirmed by server');
    } catch (error) {
      console.error(error);
      // Roll back if there is an error
      dispatch(revertPurchase(stock));
      alert('Purchase failed: ' + error.message);
    }
  };

  return (
    <button onClick={handlePurchase}>
      Purchase {stock.name}
    </button>
  );
}
```
<summary>
View Answer
</summary>
</details>




----

### q4) How can you `minimize` the API requests using Redux ?


<details>


#### - offers a straightforward way to persist state across sessions, suitable for data that doesn't change often and isn't sensitive.


```js
npm install redux-persist
```

```js
// configureStore.js
import { configureStore } from '@reduxjs/toolkit';
import storage from 'redux-persist/lib/storage'; // defaults to localStorage for web
import { combineReducers } from 'redux';
import { persistReducer, persistStore } from 'redux-persist';

import apiReducer from './apiReducer';

const rootReducer = combineReducers({
    api: apiReducer,
});

const persistConfig = {
    key: 'root',
    storage,
    whitelist: ['api'] // Specify which reducers should be persisted
};

const persistedReducer = persistReducer(persistConfig, rootReducer);

const store = configureStore({
    reducer: persistedReducer,
    middleware: (getDefaultMiddleware) =>
        getDefaultMiddleware({
            serializableCheck: {
                ignoredActions: ['persist/PERSIST']
            }
        })
});

const persistor = persistStore(store);

export { store, persistor };
```
<summary>
View Answer
</summary>
</details>

-----

