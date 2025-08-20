# 📘 useContext Hook in React

The **`useContext`** hook in React allows you to share data (state, functions, or values) globally across components without passing props manually at every level (prop drilling).  

---

## 🔹 Basic Syntax

```jsx
const value = useContext(MyContext);
MyContext → The context object created using React.createContext().

value → The current context value provided by the nearest <MyContext.Provider>.

🔹 Step 1: Create a Context
jsx
Copy
Edit
import React, { createContext, useState } from "react";

export const ThemeContext = createContext();

export const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme((prev) => (prev === "light" ? "dark" : "light"));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};
🔹 Step 2: Consume Context
jsx
Copy
Edit
import React, { useContext } from "react";
import { ThemeContext } from "./ThemeContext";

export default function Navbar() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <nav style={{ background: theme === "light" ? "#fff" : "#333", color: theme === "light" ? "#000" : "#fff" }}>
      <h1>My App</h1>
      <button onClick={toggleTheme}>Switch Theme</button>
    </nav>
  );
}
🔹 Step 3: Wrap in App.js
jsx
Copy
Edit
import React from "react";
import { ThemeProvider } from "./ThemeContext";
import Navbar from "./Navbar";

export default function App() {
  return (
    <ThemeProvider>
      <Navbar />
    </ThemeProvider>
  );
}
⚡ Advanced Usage of useContext
✅ 1. Multiple Contexts
You can nest multiple providers if you need different global states.

jsx
Copy
Edit
<AuthProvider>
  <ThemeProvider>
    <App />
  </ThemeProvider>
</AuthProvider>
jsx
Copy
Edit
const auth = useContext(AuthContext);
const theme = useContext(ThemeContext);
✅ 2. Updating Context Dynamically
Context can store state and functions so that components can update global values.

jsx
Copy
Edit
const { user, setUser } = useContext(AuthContext);

setUser({ name: "John", loggedIn: true });
✅ 3. Avoiding Re-Renders with useMemo
If context values are objects/functions, React might re-render unnecessarily. Use useMemo.

jsx
Copy
Edit
const value = useMemo(() => ({ theme, toggleTheme }), [theme]);
<ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>
✅ 4. Combining with Custom Hooks
Create a custom hook for cleaner usage.

jsx
Copy
Edit
export const useTheme = () => {
  return useContext(ThemeContext);
};

// Usage
const { theme, toggleTheme } = useTheme();
⚠️ Pitfalls & Best Practices
❌ Don’t:
Overuse context for every piece of state (use props if local).

Store frequently updated state (like input fields) in context → leads to re-renders.

✅ Do:
Use context for global state: authentication, theme, language, cart, etc.

Wrap context values with useMemo to optimize performance.

Create custom hooks (useAuth, useTheme) for clean abstraction.

🔹 Example: Auth Context (Deep Example)
jsx
Copy
Edit
// AuthContext.js
import React, { createContext, useState, useContext } from "react";

const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  const login = (name) => setUser({ name });
  const logout = () => setUser(null);

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};

// Custom Hook
export const useAuth = () => useContext(AuthContext);
jsx
Copy
Edit
// Dashboard.js
import React from "react";
import { useAuth } from "./AuthContext";

export default function Dashboard() {
  const { user, logout } = useAuth();

  return (
    <div>
      <h1>Welcome {user?.name}</h1>
      <button onClick={logout}>Logout</button>
    </div>
  );
}
jsx
Copy
Edit
// App.js
import React from "react";
import { AuthProvider } from "./AuthContext";
import Dashboard from "./Dashboard";

export default function App() {
  return (
    <AuthProvider>
      <Dashboard />
    </AuthProvider>
  );
}
✅ Summary
useContext removes prop drilling.

Use with createContext + Provider.

Best for auth, theme, language, cart, settings.

Optimize with useMemo & custom hooks.

Don’t overuse for frequently updated values.

