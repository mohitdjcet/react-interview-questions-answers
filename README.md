# ReactJS Interview Questions & Answers (Split by Level)

---

## 🟢 Beginner Level

### 1. What is React?
React is a JavaScript library developed by Facebook for building fast and interactive user interfaces.

### 2. Why use React?
React allows efficient updating and rendering of components in response to data changes.

### 3. What is JSX?
JSX stands for JavaScript XML and allows HTML to be written within JavaScript.

### 4. What are components in React?
Components are self-contained modules that return HTML elements.

### 5. What is Virtual DOM?
A lightweight JavaScript representation of the real DOM used to improve performance.

### 6. What is a functional component?
A JavaScript function that returns React elements.

### 7. What is a class component?
A component defined with ES6 class that can manage its own state.

### 8. What are props in React?
Props are inputs to components passed as attributes.

### 9. What is state in React?
State is a local data storage that is mutable within the component.

### 10. What is useState?
A React hook that lets you add state to a functional component.

### 11. What is useEffect?
A hook for performing side effects like fetching data, subscriptions, etc.

### 12. What are fragments in React?
Fragments allow multiple elements to be grouped without adding extra nodes to the DOM.

### 13. What is an event in React?
A way to capture user interactions like clicks, form submissions, etc.

### 14. What are controlled components?
Form inputs whose values are controlled by React state.

### 15. What are uncontrolled components?
Form elements that manage their own state using refs.

---

## 🟡 Intermediate Level

### 16. What is Context API?
Allows global state sharing across components without prop drilling.

### 17. What is prop drilling?
Passing data through multiple layers of components manually.

### 18. What is React Router?
A routing library that enables single-page app navigation.

### 19. What is Redux?
A predictable state container for managing application-level state.

### 20. What are actions in Redux?
Plain JavaScript objects that describe what happened.

### 21. What is a reducer?
A function that determines state changes in response to actions.

### 22. What is middleware in Redux?
Functions that intercept actions before they reach the reducer.

### 23. What is useReducer?
A React hook used as an alternative to useState for complex state logic.

### 24. What is lazy loading in React?
Loading components only when needed to improve performance.

### 25. What is Suspense?
A component that shows a fallback until a lazy-loaded component finishes loading.

### 26. What is memoization in React?
Optimization technique to avoid expensive calculations by caching results.

### 27. What is React.memo?
A higher-order component that prevents unnecessary re-renders of functional components.

### 28. What is useMemo?
A hook that memoizes a computed value.

### 29. What is useCallback?
A hook that returns a memoized version of a callback function.

### 30. What are portals?
Allow rendering a component outside the parent DOM hierarchy.

### 31. What is useRef?
A hook that provides a mutable ref object.

### 32. What is forwardRef?
A technique for passing refs to child components.

### 33. What is shallow rendering?
Rendering a component without its children to test in isolation.

### 34. What is StrictMode?
A wrapper that checks for potential issues in development mode.

### 35. How to optimize performance?
Using memoization, avoiding unnecessary re-renders, and code splitting.

---

## 🔴 Advanced Level

### 36. What is Server-Side Rendering (SSR)?
Rendering components on the server instead of in the browser.

### 37. What is hydration?
Making server-rendered HTML interactive by attaching event listeners.

### 38. What is Concurrent Mode?
A new feature that allows React to interrupt rendering to handle urgent updates first.

### 39. What is startTransition?
A method that lets you mark updates as non-urgent.

### 40. What is an Error Boundary?
A component that catches errors in child components and displays a fallback UI.

### 41. How to create custom hooks?
By writing functions that use built-in React hooks.

### 42. What are render props?
A technique for sharing code between components using a function as a child.

### 43. What are compound components?
Components that work together as a group, sharing internal state via context.

### 44. What is a higher-order component (HOC)?
A function that takes a component and returns a new component with added props or behavior.

### 45. What are synthetic events?
A cross-browser wrapper around the browser’s native event system.

### 46. What is reconciliation in React?
The process of comparing the new virtual DOM with the previous one and applying necessary changes to the real DOM.

### 47. What is the difference between SSR and CSR?
SSR renders on the server, CSR renders on the client after the JS bundle loads.

### 48. What is hydration error?
When the server-rendered HTML doesn't match the client-rendered HTML.

### 49. What is React Profiler?
A tool to measure the performance of React components.

### 50. What are the best practices in large-scale React apps?
Component reusability, state management separation, folder structure, lazy loading, and consistent patterns.
