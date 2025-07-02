# Top 100 React.js Interview Questions and Answers

This document provides a comprehensive list of React.js interview questions along with detailed answers, designed to help you prepare for your next interview.

---

## **I. Core React Concepts**

### 1. What is React?
**Answer:** React is a free and open-source front-end JavaScript library for building user interfaces based on UI components. It's maintained by Meta and a community of individual developers and companies. It's often used for single-page applications.

### 2. What are the major features of React?
**Answer:**
* **JSX:** JavaScript XML, a syntax extension for JavaScript.
* **Virtual DOM:** A lightweight copy of the actual DOM, used for efficient UI updates.
* **Components:** Reusable and self-contained building blocks of a React application.
* **Unidirectional Data Flow:** Data flows in a single direction, making it easier to understand and debug.
* **Hooks:** Functions that let you use state and other React features in functional components.
* **Declarative UI:** React makes it easier to create interactive UIs.
* **Performance:** Optimized rendering due to Virtual DOM and reconciliation.

### 3. What is JSX?
**Answer:** JSX (JavaScript XML) is a syntax extension for JavaScript recommended by React. It allows you to write HTML-like code within JavaScript, making it easier to describe what the UI should look like. Browsers cannot directly read JSX, so it must be transpiled into regular JavaScript using a tool like Babel.

### 4. Explain the concept of Virtual DOM in React.
**Answer:** The Virtual DOM (VDOM) is a lightweight, in-memory representation of the actual DOM. When the state of a React component changes, React first updates its Virtual DOM. Then, it compares the current Virtual DOM with the previous one (a process called "diffing"). It calculates the minimal set of changes needed and then efficiently updates only those specific changes in the real DOM. This minimizes direct manipulation of the expensive real DOM, leading to better performance.

### 5. How does the Virtual DOM work?
**Answer:**
1.  **Render:** When a component's state or props change, React re-renders the component and creates a new Virtual DOM tree.
2.  **Diffing:** React then compares this new Virtual DOM tree with the previous one. It identifies the differences (the "diff").
3.  **Reconciliation:** Based on the diff, React calculates the most efficient way to update the actual DOM.
4.  **Update:** Only the changed parts are updated in the real DOM, rather than re-rendering the entire page.

### 6. What is the difference between an Element and a Component in React?
**Answer:**
* **Element:** A plain JavaScript object that describes what you want to see on the screen. It's like a description or a blueprint. `React.createElement()` creates React elements.
* **Component:** A function or a class that optionally takes inputs (props) and returns a React element. Components are the reusable building blocks of a React application.

### 7. What are the differences between functional and class components?
**Answer:**
* **Functional Components:** Simple JavaScript functions that receive props as an argument and return JSX. Before React 16.8, they were "stateless." With Hooks, they can now manage state and side effects. They are generally preferred in modern React development due to their simplicity and better performance characteristics in some cases.
* **Class Components:** ES6 classes that extend `React.Component`. They can hold local state, have lifecycle methods, and access them via `this`. They were traditionally used for components requiring state or lifecycle methods.

### 8. What are props in React?
**Answer:** Props (short for properties) are read-only inputs passed from a parent component to a child component. They allow you to pass data and event handlers down the component tree, enabling communication between components. Props are immutable within the child component.

### 9. What is state in React?
**Answer:** State is an object that holds data or information about a component that can change over time. It is internal to the component and is managed within it. When the state changes, the component re-renders. State is mutable and should be updated using `setState()` in class components or `useState()` hook in functional components.

### 10. What is the difference between state and props?
**Answer:**

| Feature     | Props                                          | State                                               |
| :---------- | :--------------------------------------------- | :-------------------------------------------------- |
| **Type** | Arguments/configurations                       | Internal data                                       |
| **Mutablity** | Immutable (read-only)                          | Mutable (can be changed)                            |
| **Origin** | Passed from parent component                   | Managed within the component itself                 |
| **Usage** | Used to pass data to child components          | Used to manage data that changes over time          |
| **Updates** | Re-render when parent re-renders with new props | Re-render when `setState` or `useState` is called |

### 11. Why should we not update the state directly?
**Answer:** Directly modifying `this.state` (in class components) or directly reassigning the state variable (in functional components) will not trigger a re-render. React's reconciliation process relies on the state being updated via `setState` or the state setter function from `useState` to detect changes and re-render the UI efficiently.

### 12. What is the purpose of the callback function as an argument of `setState()`?
**Answer:** The `setState()` method in class components is asynchronous. If you need to perform an action immediately after the state has been updated and the component has re-rendered, you can pass a callback function as the second argument to `setState()`. This callback will be executed after the state update is complete. For functional components with `useState`, you would use `useEffect` for similar post-render actions.

### 13. How to bind methods or event handlers in JSX callbacks?
**Answer:** There are several ways:
1.  **Arrow function in render (least recommended for performance):** `<button onClick={() => this.handleClick()}>Click Me</button>`
2.  **`bind` in render (performance implication on re-renders):** `<button onClick={this.handleClick.bind(this)}>Click Me</button>`
3.  **`bind` in constructor (most common for class components):**
    ```jsx
    constructor(props) {
      super(props);
      this.handleClick = this.handleClick.bind(this);
    }
    ```
4.  **Arrow function as class property (modern class component approach):**
    ```jsx
    handleClick = () => {
      // ...
    }
    ```

### 14. What are synthetic events in React?
**Answer:** React's synthetic event system is a cross-browser wrapper around the browser's native event system. It normalizes events so they have consistent properties across different browsers, preventing compatibility issues. Synthetic events are pooled, meaning the event object might be reused for performance, so you shouldn't access event properties asynchronously without `event.persist()`.

### 15. What is the "key" prop and what is its benefit when using it in arrays of elements?
**Answer:** The `key` prop is a special string attribute you need to include when creating lists of elements in React (e.g., using `map()`). Keys help React identify which items have changed, are added, or are removed. This helps React efficiently update the UI, especially when reordering, adding, or deleting items from a list, improving performance and preventing potential bugs. Keys should be unique among siblings.

### 16. What are fragments in React?
**Answer:** React Fragments allow you to group multiple elements returned by a component without adding an extra node to the DOM. This is useful when you want to return multiple elements but don't want to introduce an unnecessary wrapper `div` element, which can sometimes impact styling or semantic HTML. You can use `<React.Fragment>` or its shorthand `<>...</>`.

### 17. What are portals in React?
**Answer:** React Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. This is useful for things like modals, tooltips, and pop-ups, where you want the component's UI to appear outside the normal flow of the DOM while still maintaining its React component tree context (e.g., event bubbling). You use `ReactDOM.createPortal(child, domNode)`.

### 18. What are controlled and uncontrolled components?
**Answer:**
* **Controlled Components:** Form elements (like `<input>`, `<textarea>`, `<select>`) whose values are controlled by React state. The state acts as the "single source of truth." When the input changes, an `onChange` handler updates the state, and the input re-renders with the new value. This makes their behavior predictable and easy to validate.
* **Uncontrolled Components:** Form elements whose values are handled by the DOM itself, rather than by React state. You typically use refs to get their current value when needed. They are simpler for basic forms but offer less control and flexibility.

### 19. What is "Lifting State Up" in React?
**Answer:** "Lifting State Up" is a common pattern in React where if multiple sibling components need to share or react to the same data, the shared state is moved (lifted) to their closest common ancestor component. The parent component then passes the state down to its children via props. This ensures a single source of truth for the shared data.

### 20. What is reconciliation in React?
**Answer:** Reconciliation is the process by which React updates the actual DOM to match the changes in the Virtual DOM. When a component's state or props change, React creates a new Virtual DOM tree and then compares it with the previous one. It then determines the most efficient way to update the real DOM with the minimal number of changes, rather than rebuilding the entire DOM tree.

---

## **II. Component Lifecycle (Class Components) & Hooks (Functional Components)**

### 21. Explain the lifecycle methods of a React class component.
**Answer:** React class components go through three main phases:
* **Mounting:**
    * `constructor()`: Called first, for initializing state and binding methods.
    * `static getDerivedStateFromProps(props, state)`: Updates state based on props (rarely used).
    * `render()`: Renders the component's JSX.
    * `componentDidMount()`: Called after the component is rendered to the DOM. Good for data fetching, subscriptions.
* **Updating:**
    * `static getDerivedStateFromProps(props, state)`: Called when props or state change.
    * `shouldComponentUpdate(nextProps, nextState)`: Determines if a re-render is necessary (for performance optimization).
    * `render()`: Re-renders the component's JSX.
    * `getSnapshotBeforeUpdate(prevProps, prevState)`: Captures information from the DOM before updates (rarely used).
    * `componentDidUpdate(prevProps, prevState, snapshot)`: Called after the component updates in the DOM. Good for side effects dependent on updates.
* **Unmounting:**
    * `componentWillUnmount()`: Called right before the component is removed from the DOM. Good for cleanup (e.g., clearing timers, unsubscribing).

### 22. What are React Hooks?
**Answer:** React Hooks are functions that let you "hook into" React state and lifecycle features from functional components. They were introduced in React 16.8 to enable functional components to manage state and side effects, making them as capable as class components without the complexities of `this` and class lifecycle methods.

### 23. What are the rules that must be followed while using React Hooks?
**Answer:**
1.  **Only call Hooks at the top level:** Don't call Hooks inside loops, conditions, or nested functions.
2.  **Only call Hooks from React functions:** Call them from functional components or custom Hooks, not from regular JavaScript functions.

### 24. Explain the `useState()` Hook.
**Answer:** `useState()` is a Hook that allows functional components to have state. It takes an initial state value as an argument and returns an array containing:
1.  The current state value.
2.  A function to update that state value.
When the state update function is called, the component re-renders with the new state.

**Example:**
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

Explain the useEffect() Hook.
Answer: useEffect() is a Hook that lets you perform side effects in functional components. Side effects include data fetching, subscriptions, manually changing the DOM, timers, etc. It takes two arguments:

A function containing the side effect logic.

An optional dependency array.

Behavior based on dependency array:

No dependency array: Effect runs after every render.

Empty array ([]): Effect runs only once after the initial render (like componentDidMount).

Array with dependencies ([dep1, dep2]): Effect runs on initial render and whenever any of the dependencies change.

Cleanup function: The effect function can return a cleanup function. This function runs before the component unmounts or before the effect re-runs (if dependencies change), to clean up resources (e.g., unsubscribing, clearing timers).

Example:

JavaScript

import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    // This runs after the initial render and on subsequent updates (if no dependency array)
    // or when dependencies change.
    console.log('Component rendered or updated!');

    // Example of data fetching
    fetch('[https://api.example.com/data](https://api.example.com/data)')
      .then(response => response.json())
      .then(json => setData(json));

    // Cleanup function
    return () => {
      console.log('Cleanup before next effect or unmount');
      // For example, if you had a subscription, you'd unsubscribe here.
    };
  }, []); // Empty dependency array means it runs only once on mount
         // and cleanup runs on unmount.

  return (
    <div>
      {data ? <p>Data: {JSON.stringify(data)}</p> : <p>Loading...</p>}
    </div>
  );
}
26. What are Custom Hooks?
Answer: Custom Hooks are JavaScript functions whose names start with "use" (e.g., useMyHook) and can call other Hooks (like useState, useEffect, useContext, etc.). They allow you to extract reusable stateful logic from a component, making your code more modular, readable, and testable. They don't introduce new visual elements; they encapsulate behavior.

27. Explain useContext() Hook.
Answer: useContext() is a Hook that allows functional components to subscribe to React Context. Context provides a way to pass data through the component tree without having to pass props down manually at every level (prop drilling). It takes a Context object (created by React.createContext()) as an argument and returns the current context value for that context.

28. Explain useReducer() Hook.
Answer: useReducer() is an alternative to useState for managing more complex state logic, especially when the next state depends on the previous one or when you have multiple sub-values. It takes a reducer function and an initial state as arguments and returns the current state and a dispatch function. The dispatch function is used to trigger state updates by passing an "action" object to the reducer. It's often preferred for state management that involves complex state transitions or when using Redux-like patterns.

29. When would you use useMemo() and useCallback()?
Answer:

useMemo(): Used for memoizing (caching) the result of an expensive calculation. It only re-calculates the value if one of its dependencies changes. This prevents unnecessary re-executions of computations on every render, improving performance.
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

useCallback(): Used for memoizing functions. It returns a memoized version of the callback function that only changes if one of its dependencies has changed. This is particularly useful for preventing unnecessary re-renders of child components that receive callback props, as functions are recreated on every render by default.
const memoizedCallback = useCallback(() => { doSomething(a, b); }, [a, b]);

30. What is useRef() Hook?
Answer: useRef() is a Hook that returns a mutable ref object whose .current property is initialized to the passed argument (initialValue). The returned ref object will persist for the full lifetime of the component. It's primarily used for:

Accessing and interacting with DOM elements directly (e.g., focusing an input).

Storing a mutable value that doesn't cause a re-render when it changes (unlike state).

III. Advanced React Concepts
31. What are Higher-Order Components (HOCs)?
Answer: A Higher-Order Component (HOC) is a function that takes a component as an argument and returns a new component with enhanced functionalities. HOCs are a powerful pattern for reusing component logic. They are not part of the React API but are a pattern that emerges from React's compositional nature.

Example:

JavaScript

const withLogger = (WrappedComponent) => {
  return class extends React.Component {
    componentDidMount() {
      console.log(`Component ${WrappedComponent.name} mounted.`);
    }
    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
};

// Usage:
const EnhancedMyComponent = withLogger(MyComponent);
32. What is the Context API?
Answer: The React Context API provides a way to share values (like themes, authenticated user, locale) that are considered "global" for a tree of React components, without having to explicitly pass props down through every level of the tree. It consists of a Provider and a Consumer (or useContext Hook).

33. What is prop drilling? How can it be avoided?
Answer: Prop drilling is the process of passing data from a parent component down to deeply nested child components through intermediate components that don't directly need the data themselves. It can make code harder to maintain and understand.
It can be avoided using:

Context API: For truly global or widely used data.

State Management Libraries: Like Redux, Zustand, Recoil, Jotai, for more complex application state.

Component Composition: Restructuring your component hierarchy so that data is passed only to components that need it.

34. What are Error Boundaries?
Answer: Error Boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the entire application. They are class components that implement either static getDerivedStateFromError() or componentDidCatch() lifecycle methods. They only catch errors in the rendering, lifecycle methods, and constructors of children.

35. How do you optimize performance in React applications?
Answer:

React.memo() / PureComponent: Memoize functional components or use PureComponent for class components to prevent re-renders if props or state haven't shallowly changed.

useMemo() and useCallback(): Memoize expensive calculations and callback functions.

Virtualization/Windowing: For large lists, only render what's visible in the viewport (e.g., react-window, react-virtualized).

Code Splitting / Lazy Loading: Load components only when they are needed using React.lazy() and Suspense.

Optimizing Context: Avoid putting frequently changing values directly into Context if many components consume it.

Key prop optimization: Ensure correct and stable keys for list items.

Minimize Re-renders: Ensure setState is called only when necessary.

Bundle Optimization: Minify JavaScript, use tree-shaking, analyze bundle size.

36. What is React.memo()?
Answer: React.memo() is a Higher-Order Component (HOC) that memoizes functional components. It prevents a functional component from re-rendering if its props have not changed. It performs a shallow comparison of props. If you need a deep comparison, you can provide a custom comparison function as the second argument.

37. What is shouldComponentUpdate() and when would you use it?
Answer: shouldComponentUpdate(nextProps, nextState) is a lifecycle method in class components that allows you to control whether a component re-renders or not. It's used for performance optimization. By default, it returns true. If you return false, React will skip updating the component and its children. It should be used with caution, as incorrect implementation can lead to bugs. PureComponent implements a shallow comparison in this method by default.

38. Explain Server-Side Rendering (SSR) in React.
Answer: Server-Side Rendering (SSR) in React involves rendering the React components to HTML strings on the server and then sending that HTML to the client. The client-side React then "hydrates" this static markup, making it interactive.
Benefits:

Improved SEO: Search engines can crawl the full content of the page.

Faster perceived load times: Users see content sooner, even before JavaScript loads.

Better performance on slow networks/devices.

39. What is client-side rendering?
Answer: Client-side rendering (CSR) is the traditional way of rendering React applications where the browser receives a minimal HTML file (usually just a root div) and then downloads the JavaScript bundle. React then takes over, fetches data, renders the components, and builds the UI directly in the browser.

40. What is ReactDOM.render() and ReactDOM.createRoot()?
Answer:

ReactDOM.render(element, container, [callback]): The traditional way to render a React element into a DOM node in your application. It's synchronous.

ReactDOM.createRoot(container): Introduced in React 18, this is the new root API for concurrent rendering. It's asynchronous and enables new features like automatic batching, transitions, and Suspense. You then call .render(element) on the created root. This is the recommended approach for new React applications.

IV. State Management
41. What are the common ways to manage state in React applications?
Answer:

Component State (useState / this.state): For local component-specific state.

Lifting State Up: For sharing state between sibling components.

Context API (useContext): For passing "global" data down the component tree without prop drilling.

State Management Libraries: For complex, application-wide state.

Redux: Predictable state container for JavaScript apps.

Zustand: A small, fast, and scalable bear-necessities state-management solution.

Recoil: An experimental state management library for React.

Jotai: A primitive and flexible state management library.

42. What is Redux?
Answer: Redux is a predictable state container for JavaScript applications. It provides a centralized store for your application's state, making state management more predictable and easier to debug, especially in large and complex applications. It follows a strict unidirectional data flow.

43. What are the core principles of Redux?
Answer:

Single source of truth: The entire application's state is stored in a single plain JavaScript object tree within a single store.

State is read-only: The only way to change the state is to emit an action, an object describing what happened.

Changes are made with pure functions: To specify how the state tree is transformed by actions, you write pure reducers.

44. Explain the core components of Redux.
Answer:

Store: Holds the application state. There is only one store in a Redux application.

Actions: Plain JavaScript objects that describe what happened. They are the only way to send data from your application to your Redux store. They must have a type property.

Reducers: Pure functions that take the current state and an action as arguments, and return a new state. They specify how the application's state changes in response to actions.

Dispatch: A function (provided by the store) that takes an action object as an argument and sends it to the reducer.

Selectors: Functions that take the Redux state as an argument and return derived data.

45. What is redux-thunk?
Answer: redux-thunk is a middleware for Redux that allows you to write action creators that return a function instead of a plain action object. This function receives dispatch and getState as arguments, enabling asynchronous operations (like API calls) within Redux action creators before dispatching a final action.

46. What is redux-saga?
Answer: redux-saga is a middleware library for Redux that aims to make side effects (like asynchronous data fetching, accessing the browser cache, etc.) easier to manage, more efficient to execute, simple to test, and better at handling failures. It uses ES6 Generators to make asynchronous flows look like synchronous code.

47. What is the difference between redux-thunk and redux-saga?
Answer:

redux-thunk: Simple and easy to use for basic async logic. Handles asynchronous actions by allowing action creators to return functions. Uses Promises.

redux-saga: More powerful and complex. Handles side effects by treating them as declarative effects using Generator functions. Provides more control over complex async flows, error handling, and cancellation. Better for large, complex applications with many side effects.

48. What is connect() in React-Redux?
Answer: connect() is a Higher-Order Component (HOC) provided by the react-redux library. It connects a React component to the Redux store. It takes two optional arguments:

mapStateToProps: A function that receives the entire Redux state and returns an object of props that the connected component will receive.

mapDispatchToProps: A function or object that defines which actions your component can dispatch.

49. What are mapStateToProps and mapDispatchToProps?
Answer:

mapStateToProps(state, [ownProps]): A function used with connect() that maps parts of the Redux state to props that will be passed to your React component. It ensures that the component only re-renders when the specific pieces of state it cares about change.

mapDispatchToProps(dispatch, [ownProps]): A function or object used with connect() that maps Redux dispatch to props in your React component. It allows your component to trigger state changes by dispatching actions to the Redux store.

50. What is Redux Toolkit?
Answer: Redux Toolkit (RTK) is the official opinionated, batteries-included toolset for efficient Redux development. It simplifies common Redux tasks, reduces boilerplate, and provides good defaults. Key features include configureStore, createSlice (for reducers, actions, and types in one place), createAsyncThunk, and createEntityAdapter.

V. Routing & Form Handling
51. What is React Router?
Answer: React Router is a popular declarative routing library for React applications. It enables single-page applications to have multiple views or pages by managing and synchronizing the UI with the URL. It allows you to define routes, navigate between them, and pass data through URL parameters.

52. What is the difference between BrowserRouter and HashRouter?
Answer:

BrowserRouter: Uses the HTML5 history API (pushState, replaceState) to keep the UI in sync with the URL. It results in clean, "pretty" URLs (e.g., your-app.com/about). Requires server-side configuration to handle direct requests to sub-paths.

HashRouter: Uses the hash portion of the URL (e.g., your-app.com/#/about). It does not require any server-side configuration and works well with static file servers, but the URLs are less aesthetically pleasing and can sometimes interfere with SEO.

53. How do you navigate programmatically using React Router?
Answer: In React Router v6, you use the useNavigate() Hook. It returns a function that you can call to navigate to a new path.

Example:

JavaScript

import { useNavigate } from 'react-router-dom';

function MyComponent() {
  const navigate = useNavigate();

  const handleClick = () => {
    navigate('/dashboard');
    // or navigate(-1) for back
    // or navigate('/users', { state: { from: 'home' } });
  };

  return <button onClick={handleClick}>Go to Dashboard</button>;
}
54. What is the purpose of Link and NavLink in React Router?
Answer:

<Link to="/path">: Used to create navigation links within your application. When clicked, it prevents a full page reload and updates the URL, allowing React Router to render the appropriate component. It's rendered as an <a> tag in the DOM.

<NavLink to="/path">: A special version of Link that automatically adds styling attributes (like activeClassName or style function) to the rendered element when it matches the current URL. This is useful for highlighting the active navigation item.

55. How do you handle forms in React?
Answer: Forms in React are typically handled using controlled components, where the form's input values are stored in the component's state, and their changes are managed by event handlers (e.g., onChange). Alternatively, uncontrolled components use refs to get input values directly from the DOM, which is simpler for very basic forms.

56. What is Formik?
Answer: Formik is a popular open-source library that helps with building forms in React. It simplifies the process of managing form state, validation, error messages, and submission. It significantly reduces the boilerplate associated with form handling in React.

57. What is Yup?
Answer: Yup is a JavaScript schema builder for value parsing and validation. It's often used in conjunction with Formik to define validation schemas for form fields, making form validation robust and reusable.

VI. Testing in React
58. How do you test React components?
Answer: Common approaches include:

Unit Testing: Testing individual components in isolation (e.g., using Jest and React Testing Library).

Integration Testing: Testing how multiple components work together.

End-to-End (E2E) Testing: Testing the entire application flow from the user's perspective (e.g., Cypress, Playwright, Selenium).

59. What is Jest?
Answer: Jest is a popular JavaScript testing framework developed by Meta (Facebook). It's commonly used for unit and integration testing of React applications. It's a "zero-configuration" framework that comes with assertions, mocking, and coverage reporting built-in.

60. What is React Testing Library?
Answer: React Testing Library is a set of utilities for testing React components. Its guiding principle is to test components in a way that resembles how users interact with them. It focuses on querying the DOM as the user would, rather than testing implementation details, leading to more robust and maintainable tests.

61. What is the difference between Shallow Rendering and Full DOM Rendering?
Answer:

Shallow Rendering (Enzyme's shallow()): Renders only the component itself, without rendering its children components. This is good for unit testing a component in isolation, ensuring its internal logic and props are passed correctly without being affected by its children.

Full DOM Rendering (Enzyme's mount(), React Testing Library's render()): Renders the component along with all its children components into a full DOM environment (like JSDOM). This is suitable for integration testing, where you want to test the interactions between parent and child components and how they behave in a more realistic browser-like environment. React Testing Library primarily focuses on full DOM rendering.

VII. Development Workflow & Tools
62. What is Create React App (CRA)?
Answer: Create React App is an official command-line tool that allows you to quickly set up a new single-page React application with a predefined build setup (Webpack, Babel, ESLint, etc.) and development server, without needing to configure them manually. It provides a good starting point for learning React.

63. What is Babel?
Answer: Babel is a JavaScript compiler (transpiler) that converts modern JavaScript (ES6+, JSX, TypeScript) code into backward-compatible versions of JavaScript that can be understood by older browsers or environments. It's essential for running React code in production.

64. What is Webpack?
Answer: Webpack is a static module bundler for modern JavaScript applications. It takes all your project's assets (JavaScript, CSS, images, fonts, etc.), treats them as modules, and bundles them into a few optimized files (often a single file) for deployment. It also handles transformations (via loaders) and optimizations.

65. What is ESLint?
Answer: ESLint is a pluggable linting utility for JavaScript and JSX. It statically analyzes your code to find potential problems, enforce code style, and ensure best practices. It helps maintain code quality and consistency across a team.

66. What is the purpose of package.json in a React project?
Answer: package.json is a manifest file for your project. It contains:

Project metadata (name, version, description).

Scripts for common tasks (e.g., start, build, test).

Project dependencies (libraries your app needs to run).

Development dependencies (libraries needed only for development, like testing tools).

67. How do you start a new React project?
Answer: The recommended way is to use Create React App:
npx create-react-app my-app
Then navigate into the directory and start the development server:
cd my-app
npm start (or yarn start)

For more advanced projects or SSR, Next.js or Vite are often preferred.

68. What are React DevTools?
Answer: React DevTools are a browser extension (available for Chrome, Firefox, Edge, and as a standalone app) that allows you to inspect the React component hierarchy, view and edit component props and state, and debug your React application more effectively.

VIII. Styling in React
69. What are the different ways to style React components?
Answer:

Inline Styling: Using JavaScript objects directly in the style prop.
return <div style={{ color: 'red', fontSize: '16px' }}>Hello</div>;

CSS Stylesheets: Importing regular .css files.
import './MyComponent.css';

CSS Modules: Locally scoped CSS by default, preventing naming conflicts.
import styles from './MyComponent.module.css';
return <div className={styles.myClass}>Hello</div>;

Styled Components / Emotion (CSS-in-JS): Write CSS directly in JavaScript using tagged template literals.

Sass/Less: Preprocessed CSS that allows variables, nesting, mixins.

Utility-first CSS frameworks: Like Tailwind CSS.

70. What are CSS-in-JS libraries? Give examples.
Answer: CSS-in-JS libraries allow you to write CSS using JavaScript, enabling dynamic styling based on component props or state, and providing features like automatic vendor prefixing, unique class names, and theme support.
Examples: Styled Components, Emotion.

71. What is the benefit of CSS Modules?
Answer: CSS Modules solve the problem of global CSS scope by automatically generating unique class names for each CSS rule, effectively scoping styles to the component that imports them. This prevents naming collisions and makes styling more modular and maintainable, especially in larger applications.

IX. Performance & Optimizations (Deeper Dive)
72. What is Strict Mode in React?
Answer: React.StrictMode is a tool for highlighting potential problems in an application. Like Fragment, StrictMode does not render any visible UI. It activates additional checks and warnings for its descendants. It helps in:

Identifying components with unsafe lifecycles.

Warning about legacy string ref API usage.

Detecting unexpected side effects (e.g., in constructor or render).

Warning about deprecated findDOMNode usage.

Detecting legacy context API usage.

73. What is memoization in React?
Answer: Memoization is an optimization technique used to speed up computer programs by caching the results of expensive function calls and returning the cached result when the same inputs occur again. In React, React.memo(), useMemo(), and useCallback() are used for memoization to prevent unnecessary re-renders or re-calculations.

74. When should you not use memoization?
Answer: Memoization comes with a cost (memory for caching, and the overhead of the comparison). You should avoid memoization if:

The function/component renders very rarely.

The calculation is not expensive.

The comparison function for props/dependencies is more expensive than the re-render/re-calculation itself.

The component is frequently re-rendering with unique props.

75. Explain key prop in detail.
Answer: The key prop is crucial when rendering lists in React. React uses keys to efficiently update list items. When a list changes (items are added, removed, or reordered), React uses the keys to identify which specific elements have changed.

Unique: Keys must be unique among siblings within the same list.

Stable: Keys should ideally be stable, meaning they don't change between re-renders. Avoid using index as a key if the list items can be reordered, added, or removed, as this can lead to performance issues and bugs (e.g., incorrect state associated with the wrong item). Use a unique ID from your data.

76. What is the concept of Immutable Data Structures in React?
Answer: Immutable data structures are ones that cannot be changed after they are created. When a change is needed, a new data structure is created with the updated values, leaving the original intact. In React (especially with Redux or PureComponent / React.memo), using immutable data helps:

Detect changes efficiently: React can quickly compare references to see if an object has changed, rather than performing deep equality checks.

Predictable state updates: Prevents accidental mutations and makes debugging easier.
Libraries like Immer can simplify working with immutability.

X. Common Patterns & Best Practices
77. What is composition in React?
Answer: Composition is a core principle in React for building complex UIs by combining smaller, independent components. Instead of relying on inheritance, React encourages composition using props and the children prop. This allows for flexible and reusable components.

78. What is the difference between composition and inheritance?
Answer:

Inheritance (OOP concept): A class can inherit properties and methods from another class. While possible in React classes, it's generally discouraged for component reuse as it can lead to tight coupling and prop drilling issues.

Composition (React's preferred way): Components are built by combining other components. This is achieved by passing components as props or using the children prop, making components more independent, flexible, and reusable.

79. What is a controlled input in React?
Answer: A controlled input is a form input element (like <input>, <textarea>, <select>) whose value is controlled by React state. Every change to the input is handled by an event handler (e.g., onChange) that updates the component's state, and the input's value is then set by the state. This makes the input's behavior predictable and allows for easy validation.

80. What is an uncontrolled input in React?
Answer: An uncontrolled input is a form input element whose value is handled by the DOM itself, not by React state. You typically use a ref to get the input's value when you need it (e.g., on form submission). They are simpler for basic forms but offer less control and make validation more manual.

81. When would you use a Ref?
Answer: Refs are primarily used for:

Managing focus, text selection, or media playback.

Triggering imperative animations.

Integrating with third-party DOM libraries.
They should be used sparingly and only when you can't achieve something declaratively with props and state.

82. What is forwardRef?
Answer: React.forwardRef is a function that allows parent components to pass a ref down to a child component, even if the child is a functional component. This is necessary because functional components don't have instances, so they can't directly receive refs in the same way class components can. It's often used when building reusable component libraries.

83. What are defaultProps?
Answer: defaultProps is a property on a component that lets you define default values for props. If a prop is not provided by the parent component, the defaultProps value will be used instead. This ensures that your component always receives a value for that prop and can avoid errors.

84. What is PropTypes?
Answer: PropTypes is a library (originally part of React, now a separate package prop-types) used for type-checking props passed to React components. It helps catch bugs by warning developers if they pass incorrect types of data to components, making component APIs more explicit and robust.

85. What are the benefits of using TypeScript with React?
Answer:

Static Type Checking: Catches type-related errors at compile-time, reducing runtime bugs.

Improved Readability and Maintainability: Explicit types make code easier to understand and refactor.

Better Tooling and Autocompletion: IDEs can provide smarter suggestions and refactoring capabilities.

Enhanced Collaboration: Provides clear contracts for component props and state, aiding teamwork.

86. How do you integrate a third-party library into React?
Answer:

Install: Use npm or yarn to install the package (e.g., npm install moment).

Import: Import the library or specific functions/components into your React component.

Use: Integrate the library's functionality or UI components as per its documentation.
Sometimes, you might need to use useEffect for lifecycle integration (e.g., initializing a charting library) or useRef for direct DOM manipulation if the library directly interacts with the DOM.

87. What is Lazy Loading and Suspense in React?
Answer:

Lazy Loading (React.lazy()): Allows you to render a dynamic import as a regular component. It tells React to load the component's code only when it's actually rendered, not when the application initially loads. This helps reduce the bundle size and improve initial load times.

Suspense (React.Suspense): A component that lets you specify a fallback UI (e.g., a loading spinner) to show while React.lazy() components (or other data-fetching mechanisms) are loading their code.

Example:

JavaScript

import React, { Suspense, lazy } from 'react';

const OtherComponent = lazy(() => import('./OtherComponent'));

function MyPage() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
88. What is code splitting?
Answer: Code splitting is a technique that breaks down your application's large JavaScript bundle into smaller, more manageable chunks. This allows browsers to load only the code required for the current view, improving initial page load performance. React.lazy() and Suspense are React's built-in ways to achieve code splitting at the component level.

89. What is the significance of the index.js file in a typical React project?
Answer: index.js is typically the entry point of a React application. It's where:

The main React component (often App) is imported.

ReactDOM.render() (or createRoot().render()) is called to mount the root React component into the DOM (usually a div with id="root" in index.html).

Global styles or context providers might be imported and wrapped around the App component.

90. What is dangerouslySetInnerHTML?
Answer: dangerouslySetInnerHTML is a React prop that allows you to directly insert HTML into the DOM from a JavaScript string. It's React's equivalent of innerHTML. It should be used with extreme caution because it can expose your application to cross-site scripting (XSS) attacks if the HTML content is not sanitized and comes from an untrusted source.

XI. Conceptual & Miscellaneous
91. What is the difference between npm and npx?
Answer:

npm (Node Package Manager): A package manager for Node.js that handles installing, publishing, and managing node modules. When you run npm install package-name, it installs the package into your project's node_modules directory.

npx (Node Package eXecutor): A tool that comes with npm 5.2+ and allows you to run executables (like CLI tools) from npm packages without explicitly installing them globally or locally. For example, npx create-react-app runs create-react-app without it needing to be globally installed. It's good for running one-off commands.

92. What are the advantages of using React?
Answer:

Component-based architecture: Promotes reusability and modularity.

Declarative approach: Makes UI easier to reason about.

Virtual DOM: Improves performance by optimizing DOM updates.

Strong community support: Large ecosystem of libraries, tools, and resources.

Unidirectional data flow: Predictable state management.

Flexibility: Can be used with other libraries and frameworks.

93. What are the limitations of React?
Answer:

Just a library: Not a full-fledged framework, requires other libraries for routing, state management, etc.

Steep learning curve for beginners: JSX, Virtual DOM, state management concepts can be challenging initially.

Rapid development pace: Frequent updates can mean keeping up with changes.

View layer only: Does not provide solutions for backend or database.

94. What is a custom renderer in React?
Answer: A custom React renderer is a library that allows React to render to environments other than the traditional browser DOM. It provides a way to implement your own reconciliation algorithm and render to different platforms. Examples include React Native (for mobile), React VR (for virtual reality), React-ART (for 2D graphics), and Ink (for command-line interfaces).

95. Explain the concept of immutability in React state updates.
Answer: Immutability in React state updates means that you should never directly modify existing state objects or arrays. Instead, when you need to update state, you should create a new object or array with the desired changes. This is crucial for React's reconciliation process to detect changes efficiently (by comparing references) and ensure predictable state updates.

Incorrect (mutating):

JavaScript

this.state.items.push(newItem); // DO NOT DO THIS
this.setState({ items: this.state.items });
Correct (immutable update):

JavaScript

this.setState(prevState => ({
  items: [...prevState.items, newItem]
}));
// Or for objects:
this.setState(prevState => ({
  user: { ...prevState.user, name: 'New Name' }
}));
96. What is the difference between a class component and a PureComponent?
Answer:

A class component is a regular React class component. When its props or state change, it will re-render by default, even if the new props or state are shallowly equal to the previous ones.

A PureComponent is a class component that implements shouldComponentUpdate() with a shallow comparison of props and state. This means it will only re-render if there's a shallow difference in its props or state. It's a performance optimization.

97. What is HMR (Hot Module Replacement)?
Answer: Hot Module Replacement (HMR) is a Webpack feature that allows you to update modules (like React components) in a running application without a full page reload. When you make changes to your code, only the changed modules are replaced, and the application's state is preserved. This significantly speeds up development workflow.

98. How do you handle asynchronous operations in React?
Answer:

Functional Components: Use the useEffect Hook for data fetching and other side effects. You can use async/await inside useEffect (often by defining an inner async function).

Class Components: Use componentDidMount for initial data fetching and componentDidUpdate for fetching data based on prop/state changes. You can use Promises or async/await.

State Management Libraries: Redux with redux-thunk or redux-saga, or other libraries like React Query, SWR, Zustand, which have built-in async handling.

99. What are common pitfalls/anti-patterns in React development?
Answer:

Mutating state directly: Not using setState or useState setter functions correctly.

Using index as key: Can lead to bugs with reordered or changing lists.

Prop drilling: Passing props unnecessarily through many levels.

Over-optimization: Prematurely using memo, useMemo, useCallback when not needed.

Neglecting component cleanup: Not cleaning up subscriptions, timers in useEffect or componentWillUnmount.

Deep nesting of components: Can make debugging difficult.

Ignoring warnings: React DevTools and console warnings often point to potential issues.

100. What is a "Render Prop" in React?
Answer: A Render Prop is a pattern where a component's prop is a function that returns a React element. This pattern allows a component to share code or state with its child components in a flexible way, without explicit JSX nesting. The component essentially "renders" whatever the function passed to its render prop tells it to render.
