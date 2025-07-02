# ReactJS Interview Questions & Answers (Split by Level)

---

## 🟢 Beginner Level – ReactJS Interview Questions

### 1. What is React?
React is a **JavaScript library** developed by **Facebook** for building **user interfaces**, especially for single-page applications. It allows developers to create large web applications that can update and render efficiently in response to data changes without reloading the page.

---

### 2. Why use React?
React offers several benefits:
- **Declarative syntax** makes code more predictable and easier to debug.
- **Component-based architecture** encourages reusable, maintainable code.
- It uses a **Virtual DOM** for faster rendering.
- It's backed by a strong community and ecosystem.

---

### 3. What is JSX?
JSX stands for **JavaScript XML**. It allows developers to write HTML-like syntax directly in JavaScript files. JSX makes it easier to visualize the UI structure and is compiled to `React.createElement()` calls under the hood.

```jsx
const element = <h1>Hello, React!</h1>;
```

---

### 4. What are components in React?
Components are the **building blocks of a React application**. They are reusable pieces of UI that return React elements. There are two types of components: **functional components** and **class components**.

```jsx
function Welcome() {
  return <h1>Hello, world!</h1>;
}
```

---

### 5. What is Virtual DOM?
The **Virtual DOM (VDOM)** is a lightweight JavaScript representation of the real DOM. When changes are made to the UI, React updates the Virtual DOM first and then efficiently updates the real DOM only where changes occurred, improving performance.

---

### 6. What is a functional component?
A **functional component** is a simple JavaScript function that returns JSX. It doesn't have its own state unless you use React hooks like `useState`.

```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

---

### 7. What is a class component?
A **class component** is an ES6 class that extends `React.Component` and has a `render()` method. It can maintain its own state and lifecycle methods.

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

---

### 8. What are props in React?
**Props (short for properties)** are inputs to React components. They are passed from a parent component to a child component and are read-only. Props allow you to make your components dynamic and reusable.

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

---

### 9. What is state in React?
**State** is a built-in object in class and functional components that allows components to create and manage their own data. State is mutable and used to store information that can change over the component's lifecycle.

```jsx
const [count, setCount] = useState(0);
```

---

### 10. What is useState?
`useState` is a **React Hook** that allows you to add state to functional components. It returns an array with two values: the current state and a function to update it.

```jsx
const [name, setName] = useState('Mohit');
```

---

### 11. What is useEffect?
`useEffect` is a **hook** used to perform side effects in functional components. Common use cases include data fetching, setting up subscriptions, and manually changing the DOM.

```jsx
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

---

### 12. What are fragments in React?
**Fragments** let you group a list of children elements without adding extra nodes to the DOM.

```jsx
<>
  <td>Hello</td>
  <td>World</td>
</>
```

---

### 13. What is an event in React?
Events in React are handled using camelCase syntax and JavaScript functions. They are used to respond to user actions like clicks, typing, or form submissions.

```jsx
<button onClick={handleClick}>Click Me</button>
```

---

### 14. What are controlled components?
**Controlled components** are form elements whose values are controlled by React state. The value of the input field is set by the component's state.

```jsx
<input type="text" value={name} onChange={(e) => setName(e.target.value)} />
```

---

### 15. What are uncontrolled components?
**Uncontrolled components** manage their own state using the DOM, typically accessed via **refs** in React.

```jsx
const inputRef = useRef();

function handleSubmit() {
  alert(`Input: ${inputRef.current.value}`);
}

<input ref={inputRef} type="text" />
```

---


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

### 36. What are custom hooks?
Functions that use built-in React hooks to reuse component logic.

### 37. What is defaultProps?
An attribute used to set default values for props.

### 38. How to handle forms in React?
By using controlled or uncontrolled components with appropriate state or refs.

### 39. What is React Developer Tools?
A Chrome/Firefox extension to inspect and debug React components.

### 40. What is the difference between children and props?
`children` is a prop that refers to nested elements between a component's opening and closing tags.
