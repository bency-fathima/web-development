# React Form Handling — Quick Guide

A handy reference for managing form inputs, state, and submissions in React.

---

## 1) Controlled Components

Inputs are bound to React state and updated via `onChange`.

```jsx
import { useState } from "react";

export default function FormExample() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Name: ${name}, Email: ${email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="Enter name"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <input
        type="email"
        placeholder="Enter email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 2) Handling Multiple Fields with One State Object

Use dynamic keys to handle many inputs with a single state object.

```jsx
import { useState } from "react";

export default function MultiFieldForm() {
  const [formData, setFormData] = useState({
    username: "",
    password: ""
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({ ...formData, [name]: value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        name="username"
        placeholder="Username"
        value={formData.username}
        onChange={handleChange}
      />
      <input
        type="password"
        name="password"
        placeholder="Password"
        value={formData.password}
        onChange={handleChange}
      />
      <button type="submit">Login</button>
    </form>
  );
}
```

---

## 3) Checkbox, Radio, Select

```jsx
import { useState } from "react";

export default function ExtraInputs() {
  const [gender, setGender] = useState("");
  const [terms, setTerms] = useState(false);

  return (
    <form>
      {/* Radio buttons */}
      <label>
        <input
          type="radio"
          name="gender"
          value="male"
          checked={gender === "male"}
          onChange={(e) => setGender(e.target.value)}
        />
        Male
      </label>
      <label>
        <input
          type="radio"
          name="gender"
          value="female"
          checked={gender === "female"}
          onChange={(e) => setGender(e.target.value)}
        />
        Female
      </label>

      {/* Checkbox */}
      <label>
        <input
          type="checkbox"
          checked={terms}
          onChange={(e) => setTerms(e.target.checked)}
        />
        Accept Terms
      </label>

      {/* Select */}
      <select value={gender} onChange={(e) => setGender(e.target.value)}>
        <option value="">--Select Gender--</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
      </select>
    </form>
  );
}
```

---

## 4) Resetting Form

```jsx
const handleReset = () => {
  setFormData({ username: "", password: "" });
};
```

---

## 5) Form Libraries for Complex Forms

When forms grow large or need validation, use:

* **Formik** — popular form state library
* **React Hook Form** — lightweight & performant
* **Yup** — schema-based validation

---

## ✨ Key Takeaways

* Use **controlled components**: inputs bound to state.
* Always prevent default form reload with `e.preventDefault()`.
* Use dynamic `name` keys for multiple fields.
* For big forms, rely on libraries to simplify state & validation.

---

## 🚀 Mini Tasks (Practice)

1. Build a login form with `username` and `password`.
2. Add a checkbox for “Remember me” and a select for “Role”.
3. Implement a reset button to clear inputs.
4. Extend the form with validation (e.g., required fields).

---

**Happy coding!** 🎉
