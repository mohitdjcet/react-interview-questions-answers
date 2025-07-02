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
