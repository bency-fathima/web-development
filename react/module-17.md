# useEffect Hook in React

The `useEffect` hook is one of the most important hooks in React. It allows you to perform side effects in function components.

---

## 📌 What is a Side Effect?

Side effects are operations that affect something outside the scope of the function being executed. Examples:

* Fetching data from an API
* Directly updating the DOM
* Setting up subscriptions or timers

---

## 🛠️ Basic Syntax

```jsx
useEffect(() => {
  // code to run
  return () => {
    // cleanup (optional)
  };
}, [dependencies]);
```

### Parameters:

1. **Effect function** – The logic you want to run.
2. **Cleanup function** *(optional)* – Runs before the component unmounts or before the effect runs again.
3. **Dependency array** – Determines when the effect should run.

---

## 🚀 Examples

### 1. Run on Every Render

```jsx
useEffect(() => {
  console.log("Component rendered");
});
```

(No dependency array → runs on every render)

### 2. Run Only Once (on Mount)

```jsx
useEffect(() => {
  console.log("Component mounted");
}, []);
```

(Empty dependency array → runs only on mount)

### 3. Run When Dependencies Change

```jsx
useEffect(() => {
  console.log("Count changed:", count);
}, [count]);
```

(Runs when `count` changes)

### 4. Cleanup Function

```jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Timer running");
  }, 1000);

  return () => clearInterval(timer); // cleanup
}, []);
```

---

## 🌐 Fetching Data with useEffect

```jsx
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

---

## ⚠️ Common Mistakes

* ❌ Missing dependency array → unintended multiple runs
* ❌ Wrong dependencies → stale data or infinite loops
* ❌ Not cleaning up → memory leaks

---

## ✅ Best Practices

1. Always list dependencies in the array.
2. Use cleanup for subscriptions, timers, or event listeners.
3. Split effects if they handle unrelated logic.

---

## 📝 Practice Tasks

1. Create a counter and use `useEffect` to log the count whenever it changes.
2. Fetch data from an API and display it using `useEffect`.
3. Implement a timer that starts on mount and cleans up on unmount.
4. Add an event listener for window resize using `useEffect` and clean it up.

---

## 🔑 Summary

* `useEffect` lets you run side effects in functional components.
* Dependency array controls when the effect runs.
* Cleanup prevents memory leaks.
* Commonly used for fetching data, timers, and event listeners.
