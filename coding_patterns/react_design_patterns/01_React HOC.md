### React HOC Pattern (Higher Order Component)

#### What is HOC ?

- **_Higher Order Component <u>receives a component</u>_**, applies a certain logic and **_<u>then return that component with those additional logics</u>_**

#### When to use HOC?

- When we want **_<u>to apply same logic to multiple components</u>_**

```js
// Component1.jsx
const Component1 = () => {
  return <div>This is Component 1</div>;
};

export default Component1;
```

```js
// Component2.jsx
const Component2 = () => {
  return <div>This is Component 2</div>;
};

export default Component2;
```

```js
//Login.jsx
const Login = ({ onClick }) => {
  return <button onClick={onClick}>Login</button>;
};
export default Login;
```

```js
// withAuthorization.jsx
const withAuthorization = (WrappedComponent) => {
  return function (props) {
    if (!props.isLoggedIn) {
      return;
    }
    return <WrappedComponent {...props} />;
  };
};

export default withAuthorization;
```

```js
// App.jsx
import { useState } from 'react';
import Component1 from './components/Component1';
import Component2 from './components/Component2';
import withAuthorization from './HOC/withAuthorization';
import Login from './components/Login';

export default function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);
  const AuthComponent1 = withAuthorization(Component1);
  const AuthComponent2 = withAuthorization(Component2);

  const handleClick = () => setIsLoggedIn(true);

  return (
    <div className='App'>
      <div>
        <Login onClick={handleClick} />
        <AuthComponent1 isLoggedIn={isLoggedIn} />
        <AuthComponent2 isLoggedIn={isLoggedIn} />
      </div>
    </div>
  );
}
```

### Project Structure

![Alt text](/coding_patterns/react_design_patterns/images_used/HOC.png)