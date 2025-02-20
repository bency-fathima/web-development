# State in React

## 1. **Introduction**
State in React is an object that allows components to hold and manage dynamic data. It enables reactivity, meaning that when the state changes, the component re-renders to reflect the new data.

---

## 2. **Why Use State?**
- **Manages Dynamic Data**: React components can update and track changes efficiently.
- **Triggers UI Updates**: When the state changes, React automatically re-renders the component.
- **Encapsulated Data**: Each component maintains its own state, making it modular and predictable.

---


# Props in React

## 1. **Introduction**
Props (short for "properties") in React are a way to pass data from a parent component to a child component. Props are read-only and allow components to be dynamic and reusable.

---

## 2. **Why Use Props?**
- **Pass Data**: Transfer data from parent to child components.
- **Reusability**: Create reusable components by passing different values.
- **Dynamic Rendering**: Modify the component's content dynamically.

---

## 3. **How Props Work**
Props are passed to components as attributes and accessed inside the component using `props`.

### **Example of Props Usage**
#### **Parent to Child Component Communication**
```jsx
import React from 'react';

// Child Component
function Greeting(props) {
  return <h2>Hello, {props.name}!</h2>;
}

// Parent Component
function App() {
  return (
    <div>
      <h1>Using Props in React</h1>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
    </div>
  );
}

export default App;
```

### **Explanation**
- The `App` component (parent) passes a `name` prop to `Greeting` (child).
- The `Greeting` component receives `props` and dynamically renders different greetings.

---

## 4. **Props with Objects and Arrays**
Props can also pass objects and arrays.

### **Passing an Object as a Prop**
```jsx
function UserProfile(props) {
  return (
    <div>
      <h3>Name: {props.user.name}</h3>
      <p>Age: {props.user.age}</p>
    </div>
  );
}

function App() {
  const user = { name: "John", age: 28 };
  return <UserProfile user={user} />;
}
```

### **Passing an Array as a Prop**
```jsx
function ItemList(props) {
  return (
    <ul>
      {props.items.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}

function App() {
  const fruits = ["Apple", "Banana", "Cherry"];
  return <ItemList items={fruits} />;
}
```

---

## 5. **Default Props**
If no prop value is passed, you can define default props.

```jsx
function Greeting(props) {
  return <h2>Hello, {props.name}!</h2>;
}

Greeting.defaultProps = {
  name: "Guest"
};
```
If `name` is not provided, "Guest" will be used as the default value.

---

--

## 5. **State vs Props**
| Feature   | State | Props |
|-----------|-------|-------|
| Mutability | Mutable (can be changed) | Immutable (cannot be changed) |
| Scope | Local to the component | Passed from parent to child |
| Updates | Triggers re-renders | Does not trigger re-renders |

---



## 6. **Conclusion**
Props are essential in React for making components dynamic and reusable. They allow communication between components and improve modularity in React applications.

