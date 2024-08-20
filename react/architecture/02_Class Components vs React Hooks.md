## <ins>Class Components vs React Hooks</ins>:


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
