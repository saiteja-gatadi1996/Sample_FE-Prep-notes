
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

# <--- SAMPLE CONTENT ENDS --->
