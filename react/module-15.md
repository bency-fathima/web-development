# React Formik — Quick Guide

Formik is a popular React library for building forms with less boilerplate, built-in validation, and better structure.

---

## 1) Installation

```bash
npm install formik yup
```

---

## 2) Basic Formik Example

```jsx
import { Formik, Form, Field } from "formik";

export default function SignupForm() {
  return (
    <Formik
      initialValues={{ name: "", email: "" }}
      onSubmit={(values) => {
        alert(JSON.stringify(values, null, 2));
      }}
    >
      {() => (
        <Form>
          <Field name="name" placeholder="Name" />
          <Field name="email" type="email" placeholder="Email" />
          <button type="submit">Submit</button>
        </Form>
      )}
    </Formik>
  );
}
```

✅ `Formik` manages state and submission.
✅ `Field` automatically hooks into state.

---

## 3) Accessing Errors & Touched

```jsx
import { Formik, Form, Field, ErrorMessage } from "formik";

export default function SignupForm() {
  return (
    <Formik
      initialValues={{ name: "", email: "" }}
      validate={(values) => {
        const errors = {};
        if (!values.name) errors.name = "Required";
        if (!values.email) errors.email = "Required";
        return errors;
      }}
      onSubmit={(values) => console.log(values)}
    >
      {() => (
        <Form>
          <div>
            <Field name="name" placeholder="Name" />
            <ErrorMessage name="name" component="div" />
          </div>
          <div>
            <Field name="email" type="email" placeholder="Email" />
            <ErrorMessage name="email" component="div" />
          </div>
          <button type="submit">Submit</button>
        </Form>
      )}
    </Formik>
  );
}
```

✅ `validate` adds custom validation logic.
✅ `ErrorMessage` displays validation messages.

---

## 4) Yup Validation Schema

Formik works great with Yup for schema-based validation.

```jsx
import { Formik, Form, Field, ErrorMessage } from "formik";
import * as Yup from "yup";

const SignupSchema = Yup.object().shape({
  name: Yup.string().required("Name is required"),
  email: Yup.string().email("Invalid email").required("Email is required"),
});

export default function SignupForm() {
  return (
    <Formik
      initialValues={{ name: "", email: "" }}
      validationSchema={SignupSchema}
      onSubmit={(values) => console.log(values)}
    >
      {() => (
        <Form>
          <Field name="name" placeholder="Name" />
          <ErrorMessage name="name" component="div" />

          <Field name="email" type="email" placeholder="Email" />
          <ErrorMessage name="email" component="div" />

          <button type="submit">Submit</button>
        </Form>
      )}
    </Formik>
  );
}
```

---

## 5) Handling Checkboxes, Radio, Select

```jsx
<Formik
  initialValues={{ role: "", terms: false }}
  onSubmit={(values) => console.log(values)}
>
  {() => (
    <Form>
      {/* Radio */}
      <label>
        <Field type="radio" name="role" value="admin" /> Admin
      </label>
      <label>
        <Field type="radio" name="role" value="user" /> User
      </label>

      {/* Checkbox */}
      <label>
        <Field type="checkbox" name="terms" /> Accept Terms
      </label>

      {/* Select */}
      <Field as="select" name="role">
        <option value="">Select role</option>
        <option value="admin">Admin</option>
        <option value="user">User</option>
      </Field>

      <button type="submit">Submit</button>
    </Form>
  )}
</Formik>
```

---

## 6) Formik Hooks (Alternative API)

Formik also provides hooks like `useFormik` for more control.

```jsx
import { useFormik } from "formik";

export default function HookForm() {
  const formik = useFormik({
    initialValues: { name: "" },
    onSubmit: (values) => console.log(values),
  });

  return (
    <form onSubmit={formik.handleSubmit}>
      <input
        name="name"
        value={formik.values.name}
        onChange={formik.handleChange}
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 7) Common Tips

* Use `validationSchema` with Yup for clean validation.
* Use `ErrorMessage` or `touched` for showing error states.
* Use `FieldArray` for dynamic lists of inputs.
* Combine with UI libs (Material UI, Tailwind) for styling.

---

## 🚀 Mini Tasks (Practice)

1. Create a signup form with `username`, `email`, and `password` using Formik.
2. Add Yup validation for all fields.
3. Add a checkbox for “Accept terms” and validate it.
4. Try `useFormik` instead of `<Formik>` component.

---

**Formik makes form state + validation simple and declarative.** 🎉
