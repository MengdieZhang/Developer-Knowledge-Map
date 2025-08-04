cat <<EOF > react-questions.md
# React Interview Questions and Answers

---

### 1. What is the relationship between React and react-dom?  
- **React** provides the core library for building components, managing state, and rendering virtual DOM.  
- **react-dom** is responsible for rendering React components into the actual DOM in web browsers. It contains methods like `ReactDOM.render()`.

---

### 2. Why doesn't React directly use `requestIdleCallback`?  
- `requestIdleCallback` is not supported in all browsers, leading to inconsistent behavior.  
- React’s scheduling via Fiber uses its own custom scheduler for fine-grained control and prioritization of tasks, beyond what `requestIdleCallback` provides.

---

### 3. Explain React's `render` method principle and when it is triggered.  
- The `render` method returns React elements describing the UI for that component.  
- It's triggered on initial mount and on state or prop updates to compute the virtual DOM tree.

---

### 4. Discuss the execution order of React events vs native events.  
- React uses a Synthetic Event system which delegates events to the root document.  
- React events are invoked during the bubbling phase after native events, ensuring consistency across browsers.

---

### 5. Explain controlled vs uncontrolled components and their use cases.  
- **Controlled components:** Form inputs controlled by React state, allowing easy validation and dynamic UI updates.  
- **Uncontrolled components:** Inputs manage their own state, accessed via refs. Useful for simple forms or integrating with non-React code.

---

### 6. How do you use Redux in your React projects? How do you organize your project structure?  
- Typically set up a global store with reducers and middleware.  
- Use `Provider` to pass store down via context.  
- Organize folders by feature: components, actions, reducers, selectors, middleware.

---

### 7. What are Redux middlewares? Common middlewares and their principles?  
- Middleware intercepts actions between dispatch and reducers, enabling async actions, logging, etc.  
- Common middlewares: `redux-thunk` (for async actions), `redux-saga` (using generator functions for side effects), logger middleware.  
- Principle: Functions with signature `({getState, dispatch}) => next => action`.

---

### 8. Your understanding of Redux and its working principle?  
- Redux manages app state in a single immutable store.  
- State changes via pure reducer functions responding to dispatched actions.  
- Ensures predictable state changes and time-travel debugging.

---

### 9. Is `setState` synchronous or asynchronous?  
- `setState` is **asynchronous** in event handlers to batch multiple updates for performance.  
- It can behave synchronously outside React event lifecycle (e.g., in `setTimeout`).

---

### 10. Briefly describe React's event delegation mechanism.  
- React attaches a single event listener to the root of the DOM (document).  
- Events bubble up to the root, and React's SyntheticEvent system dispatches to components accordingly.

---

### 11. Briefly describe React lifecycle methods and their purposes.  
- **Mounting:** `constructor`, `render`, `componentDidMount`.  
- **Updating:** `shouldComponentUpdate`, `render`, `componentDidUpdate`.  
- **Unmounting:** `componentWillUnmount`.  
- Newer lifecycle methods include `getDerivedStateFromProps`, `getSnapshotBeforeUpdate`.

---

### 12. Why can't hooks be called inside loops, conditions, or nested functions?  
- Hooks must be called in the same order on every render to preserve state consistency.  
- Violating rules breaks React’s internal hooks tracking, causing bugs.

---

### 13. Explain your understanding of custom hooks.  
- Custom hooks are reusable functions encapsulating logic using built-in hooks.  
- They improve code modularity and reuse without changing component hierarchy.

---

### 14. How to make `useEffect` support `async/await`?  


### 15. (From previous set) React diff algorithm explanation
React compares old and new virtual DOM trees, identifies minimal changes (node type, props, children), and applies efficient updates to the real DOM, optimizing rendering.

### 16. React component reuse methods
Props, Higher-Order Components (HOCs), Render Props, Custom Hooks, Component Composition.

### 17. Deprecated and new lifecycle methods in React 16 and reasons
Deprecated: componentWillMount, componentWillReceiveProps, componentWillUpdate due to async rendering issues.
New: getDerivedStateFromProps, getSnapshotBeforeUpdate.

### 18. React performance optimizations
Use React.memo, shouldComponentUpdate, memoize callbacks/values, code-splitting, virtualization, avoid unnecessary renders.

### 19. React event binding principles
React uses a synthetic event system with event delegation at the root, ensuring cross-browser consistency and performance.

### 20. React key role
- Helps React identify elements in lists for efficient re-rendering and DOM updates.

### 21. Class components vs functional components
- Class components use lifecycle methods and this.state. Functional components use hooks, are more concise, and avoid this.

