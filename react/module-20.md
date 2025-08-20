Perfect 👍 Here’s a full Markdown (MD) file that explains Context API in React from beginner to advanced:

# React Context API (Beginner to Advanced)

The **Context API** in React allows you to share data (state) globally across components **without prop drilling**.

---

## 🟢 Beginner: What is Context API?

Normally, props are passed **top-down** (parent → child).  
When multiple levels exist, **prop drilling** happens, making code messy.  

**Context API** solves this problem by providing a way to share values between components directly.

---

## 🔹 Basic Example: Without Context

```jsx
function App() {
  const user = "Alice";
  return <Parent user={user} />;
}

function Parent({ user }) {
  return <Child user={user} />;
}

function Child({ user }) {
  return <h1>Hello, {user}</h1>;
}


Here, user must be passed through every component → prop drilling.

🔹 With Context API
import React, { createContext, useContext } from "react";

const UserContext = createContext();

function App() {
  return (
    <UserContext.Provider value="Alice">
      <Child />
    </UserContext.Provider>
  );
}

function Child() {
  const user = useContext(UserContext);
  return <h1>Hello, {user}</h1>;
}


✅ No prop drilling.
useContext consumes values directly.

🟡 Intermediate: Context with State
import React, { createContext, useContext, useState } from "react";

const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <div>
      <p>Current Theme: {theme}</p>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
        Toggle Theme
      </button>
    </div>
  );
}


Here, both state and function are shared via context.

🟠 Advanced: Using Multiple Contexts

You can use multiple contexts to manage different data.

const AuthContext = createContext();
const ThemeContext = createContext();

function App() {
  return (
    <AuthContext.Provider value={{ user: "Alice" }}>
      <ThemeContext.Provider value={{ theme: "dark" }}>
        <Dashboard />
      </ThemeContext.Provider>
    </AuthContext.Provider>
  );
}

function Dashboard() {
  const { user } = useContext(AuthContext);
  const { theme } = useContext(ThemeContext);

  return (
    <h1>
      {user}'s Dashboard - Theme: {theme}
    </h1>
  );
}

🔵 Expert: Context + useReducer

For complex state management, combine Context API with useReducer.

import React, { createContext, useContext, useReducer } from "react";

const CounterContext = createContext();

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function CounterProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <CounterContext.Provider value={{ state, dispatch }}>
      {children}
    </CounterContext.Provider>
  );
}

function Counter() {
  const { state, dispatch } = useContext(CounterContext);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </div>
  );
}

function App() {
  return (
    <CounterProvider>
      <Counter />
    </CounterProvider>
  );
}

⚡ Best Practices

Keep contexts focused → One context per concern (e.g., AuthContext, ThemeContext).

Avoid overuse → Too many contexts can make code hard to follow.

Use custom hooks for cleaner access.

function useAuth() {
  return useContext(AuthContext);
}

✅ Summary

Beginner → Avoid prop drilling using createContext & useContext.

Intermediate → Share state + functions.

Advanced → Use multiple contexts.

Expert → Combine Context API with useReducer for scalable state management.
