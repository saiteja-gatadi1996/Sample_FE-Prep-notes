
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
