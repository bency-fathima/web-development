# React: Lists & Keys — Quick Guide

A compact, practical reference for rendering collections in React and choosing the right `key`.

---

## 1) Rendering Lists in React

Use JavaScript’s `Array.map()` to transform data into elements.

```jsx
const fruits = ["Apple", "Banana", "Cherry"];

export default function FruitList() {
  return (
    <ul>
      {fruits.map((fruit) => (
        <li key={fruit}>{fruit}</li>
      ))}
    </ul>
  );
}
```

**Notes:**

* Each sibling element needs a **stable** `key` prop.
* Keys help React identify which items changed, were added, or removed.

---

## 2) What is a `key`?

`key` is a special prop (read-only by React) that must be **unique among siblings** and **stable across renders**.

> Stable means: the key for the same logical item should not change between renders.

---

## 3) Why keys matter (Reconciliation)

React uses keys to efficiently update the DOM:

* **Correct identity:** Maintains component state per item.
* **Performance:** Avoids re-creating unchanged elements.
* **Predictability:** Prevents UI bugs when items reorder.

---

## 4) Good vs Bad Keys

### ✅ Good

* **Database IDs** or **UUIDs** that uniquely identify items
* **Immutable unique fields** (e.g., email, slug)
* **Composite keys** when needed: `${user.id}-${role}`

### ❌ Bad

* **Array index** (especially for dynamic lists — insertions/reorders/removals)
* **Random keys per render** (e.g., `Math.random()` inside render)

> **When is index OK?**
>
> * Static lists (no reordering/insert/delete)
> * Render-once content
> * Performance-sensitive lists where data never mutates

---

## 5) Examples

### A) Objects with IDs

```jsx
const users = [
  { id: 101, name: "Asha" },
  { id: 102, name: "Ben" },
  { id: 103, name: "Chen" }
];

function UserList() {
  return (
    <ul>
      {users.map((u) => (
        <li key={u.id}>{u.name}</li>
      ))}
    </ul>
  );
}
```

### B) Nested Lists (use different key spaces per level)

```jsx
const categories = [
  { id: "c1", name: "Fruits", items: ["Apple", "Banana"] },
  { id: "c2", name: "Veg", items: ["Carrot", "Peas"] }
];

function Catalog() {
  return (
    <div>
      {categories.map((cat) => (
        <section key={cat.id}>
          <h3>{cat.name}</h3>
          <ul>
            {cat.items.map((item) => (
              <li key={`${cat.id}-${item}`}>{item}</li>
            ))}
          </ul>
        </section>
      ))}
    </div>
  );
}
```

### C) Dynamic List with Add/Remove/Reorder

```jsx
import { useState } from "react";

let nextId = 3;
const initial = [
  { id: 1, text: "Learn React" },
  { id: 2, text: "Build a project" }
];

export default function Todos() {
  const [todos, setTodos] = useState(initial);

  const addTodo = () => {
    setTodos([...todos, { id: nextId++, text: `Task ${nextId}` }]);
  };

  const removeTodo = (id) => setTodos(todos.filter((t) => t.id !== id));

  const reorder = () => setTodos([...todos].reverse());

  return (
    <div>
      <button onClick={addTodo}>Add</button>
      <button onClick={reorder}>Reorder</button>
      <ul>
        {todos.map((t) => (
          <li key={t.id}>
            {t.text}
            <button onClick={() => removeTodo(t.id)}>x</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

### D) When You Only Have Index (and it’s safe)

```jsx
const staticFacts = ["JSX is syntax sugar", "Keys are not passed as props", "Fragments can have keys"];

function Facts() {
  return (
    <ul>
      {staticFacts.map((fact, index) => (
        <li key={index}>{fact}</li>
      ))}
    </ul>
  );
}
```

---

## 6) Common Pitfalls & Warnings

* **Warning: Each child in a list should have a unique "key" prop.**

  * Cause: Missing `key` or duplicates.
  * Fix: Provide a unique, stable key at the element returned by `map`.
* **Using index key on dynamic lists** can cause:

  * Wrong item state kept after reorder
  * Unintended re-renders
  * Animation glitches
* **Don’t pass key via props** (e.g., `<Item keyProp={id} />`). React only reads `key` directly on the element in the list, not inside the child via props.

---

## 7) Fragments & Keys

Use keyed fragments when returning multiple siblings from `map` without wrappers.

```jsx
const pairs = [
  { id: "p1", left: "👈", right: "👉" },
  { id: "p2", left: "⬅️", right: "➡️" }
];

function Arrows() {
  return (
    <ul>
      {pairs.map((p) => (
        <React.Fragment key={p.id}>
          <li>{p.left}</li>
          <li>{p.right}</li>
        </React.Fragment>
      ))}
    </ul>
  );
}
```

Short syntax works too: `<></>` cannot take a key; use `<Fragment key=...>` or `React.Fragment`.

---

## 8) Keys and Controlled Inputs

If you dynamically change keys on a subtree with inputs, React will **remount** them and **reset input state**.

```jsx
// Toggling key forces remount (resets input value)
<input key={theme} value={value} onChange={...} />
```

Use this deliberately to reset forms, but avoid accidental key changes.

---

## 9) Performance Tips

* Prefer stable IDs from data source.
* Avoid computing new keys per render.
* Memoize item components if heavy (e.g., `React.memo`).
* Virtualize large lists with libraries (e.g., `react-window`, `react-virtualized`).

---

## 10) FAQ

**Q: Are keys available in the child component via props?**
A: No. `key` is used internally by React and isn’t accessible in the child.

**Q: Where should the key go?**
A: On the **top-level** element inside the array you return from `map`.

**Q: Do keys need to be globally unique?**
A: No. Only among siblings at the same level.

---

## 11) Mini Tasks (Practice)

1. Render a list of products with `id`, `title`, and `price`. Use `id` as key.
2. Build a todo app with add/remove/reorder and demonstrate why index keys break state.
3. Implement a grouped list (categories → items) with composite keys.
4. Add a search filter and verify keys stay stable when filtering.

---

## 12) Interview-Ready Sound Bites

* “Keys must be stable and unique among siblings; they guide React’s diffing.”
* “Avoid index keys for dynamic lists because reordering breaks item identity.”
* “Keys aren’t passed to children; they’re consumed by React’s reconciliation.”

---

## 13) Cheatsheet (TL;DR)

* Use `id` → ✅ Best
* Use composite → ✅ If needed
* Use index → ⚠️ Static only
* Random per render → ❌ Never
* Put key on the element you return from `map`

---

**Happy rendering!** ✨
