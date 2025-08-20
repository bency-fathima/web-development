# React Router — Complete Guide

A step-by-step reference to using React Router (v6+).

---

## 1) Installation

```bash
npm install react-router-dom
```

---

## 2) Basic Setup

Wrap your app in a `BrowserRouter`.

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from "./Home";
import About from "./About";

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 3) Navigation with `Link` and `NavLink`

```jsx
import { Link, NavLink } from "react-router-dom";

export default function Navbar() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <NavLink
        to="/about"
        style={({ isActive }) => ({ color: isActive ? "red" : "blue" })}
      >
        About
      </NavLink>
    </nav>
  );
}
```

✅ `Link` → basic navigation.
✅ `NavLink` → applies styles when active.

---

## 4) Nested Routes

```jsx
import { Routes, Route, Outlet } from "react-router-dom";

function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <Outlet /> {/* renders child routes here */}
    </div>
  );
}

function Profile() { return <h3>Profile Page</h3>; }
function Settings() { return <h3>Settings Page</h3>; }

export default function App() {
  return (
    <Routes>
      <Route path="dashboard" element={<Dashboard />}>
        <Route path="profile" element={<Profile />} />
        <Route path="settings" element={<Settings />} />
      </Route>
    </Routes>
  );
}
```

---

## 5) Route Parameters

```jsx
import { useParams } from "react-router-dom";

function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}

<Routes>
  <Route path="user/:id" element={<User />} />
</Routes>
```

✅ URL: `/user/42` → renders "User ID: 42"

---

## 6) Query Params with `useSearchParams`

```jsx
import { useSearchParams } from "react-router-dom";

function Search() {
  const [searchParams, setSearchParams] = useSearchParams();
  const q = searchParams.get("q");

  return (
    <div>
      <input
        value={q || ""}
        onChange={(e) => setSearchParams({ q: e.target.value })}
      />
      <p>Search Query: {q}</p>
    </div>
  );
}
```

---

## 7) Navigate Programmatically

```jsx
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  const handleLogin = () => {
    // after login success
    navigate("/dashboard");
  };

  return <button onClick={handleLogin}>Login</button>;
}
```

---

## 8) Redirects

```jsx
import { Navigate } from "react-router-dom";

function Protected({ isAuth, children }) {
  if (!isAuth) return <Navigate to="/login" />;
  return children;
}
```

---

## 9) 404 Not Found Page

```jsx
<Routes>
  <Route path="*" element={<h2>Page Not Found</h2>} />
</Routes>
```

---

## 10) Layout Routes

Shared layouts with headers/footers.

```jsx
function Layout() {
  return (
    <div>
      <h1>Site Layout</h1>
      <Outlet />
    </div>
  );
}

<Routes>
  <Route path="/" element={<Layout />}>
    <Route index element={<Home />} />
    <Route path="about" element={<About />} />
  </Route>
</Routes>
```

---

## 11) Relative Links

```jsx
<Link to="profile">Profile</Link>  // relative to parent route
<Link to="/profile">Profile</Link> // absolute from root
```

---

## 12) Data Loading with `useLoaderData` (React Router v6.4+)

```jsx
import { createBrowserRouter, RouterProvider, useLoaderData } from "react-router-dom";

function Users() {
  const users = useLoaderData();
  return <ul>{users.map((u) => <li key={u.id}>{u.name}</li>)}</ul>;
}

const router = createBrowserRouter([
  {
    path: "users",
    element: <Users />,
    loader: async () => fetch("/api/users").then((res) => res.json()),
  },
]);

export default function App() {
  return <RouterProvider router={router} />;
}
```

---

## 13) Actions (Form Submissions in v6.4+)

```jsx
import { Form, useActionData } from "react-router-dom";

export async function action({ request }) {
  const formData = await request.formData();
  return { name: formData.get("name") };
}

function Contact() {
  const data = useActionData();
  return (
    <div>
      <Form method="post">
        <input name="name" placeholder="Your Name" />
        <button type="submit">Send</button>
      </Form>
      {data && <p>Submitted: {data.name}</p>}
    </div>
  );
}
```

---

## 14) BrowserRouter vs HashRouter

* **BrowserRouter**: clean URLs (`/about`).
* **HashRouter**: uses `#/about`, useful for static hosting without server config.

---

## 15) Performance Tips

* Use **lazy loading** with `React.lazy` for big routes.
* Wrap routes in **`Suspense`** for fallback loading UI.
* Use `Outlet` for nested UI sharing.

---

## 🚀 Mini Tasks (Practice)

1. Build a small site with Home, About, and Contact pages.
2. Add a dashboard with nested routes for Profile and Settings.
3. Implement a login page that redirects to dashboard.
4. Add a 404 page for unmatched routes.
5. Try out loader + action for a simple form.

---

**React Router makes client-side navigation seamless.** 🎉
