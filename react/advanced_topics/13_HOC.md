## HOC
- High-Order Components (HOCs) are an advanced pattern in React **for `reusing` component logic**. 
- They are functions that <ins>**take a component and return a new component**</ins>, effectively "wrapping" the original component with additional functionalities or data.
- Useful in **handling** cross-cutting concerns like
  -  `logging`, 
  -  `data fetching`, or 
  -  `state management interactions`.

#### q1) Why it is required?

- **Code Reuse**: 
  - HOCs allow you to **reuse common functionalities across multiple components**, reducing duplication and keeping your code DRY (Don't Repeat Yourself).
- **Abstraction and Isolation**: 
  - They help in abstracting complex logic and state interactions **away from the component** logic. 
  - This separation of concerns makes the base component simpler and focuses primarily on presenting the UI.
- **Prop Manipulation**: 
  - HOCs can abstract and manipulate props **before passing them down to the wrapped component**, allowing for more controlled and flexible component implementations.
- **Conditional Rendering**: 
  - They can be used to **conditionally render components** based on certain conditions or permissions, which is particularly **useful in scenarios like `authentication` and `authorization`**.

---

#### q2) How to write multiples HOCs in a regular component?

```js
// withUserData.js
import React, { useState, useEffect } from 'react';

const withUserData = WrappedComponent => {
  return function(props) {
    const [user, setUser] = useState(null);

    useEffect(() => {
      // Simulate fetching user data
      const timer = setTimeout(() => {
        setUser({ name: "John Doe", id: "1" });
      }, 1000);

      // Cleanup timeout if the component unmounts
      return () => clearTimeout(timer);
    }, []);

    return <WrappedComponent {...props} user={user} />;
  };
};


// withLogging.js
import React, { useEffect } from 'react';

const withLogging = WrappedComponent => {
  return function(props) {
    useEffect(() => {
      console.log('Component did mount or update', props);

      // Optionally: Add return function to mimic componentWillUnmount
      return () => {
        console.log('Component will unmount', props);
      };
    }, [props]); // You can adjust dependency array based on specific prop changes if needed

    return <WrappedComponent {...props} />;
  };
};
```

```js
import MyComponent from './MyComponent';
import withUserData from './withUserData';
import withLogging from './withLogging';

// Manual composition
const EnhancedComponent = withLogging(withUserData(MyComponent));
```

----