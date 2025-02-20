# Using Variables in Functional Components

## 1. **Introduction**
In React functional components, we can declare and use different types of variables such as strings, numbers, arrays, objects, and booleans. These variables can be directly used in JSX to display values dynamically.

---

## 2. **Declaring Variables in a Functional Component**
React functional components use regular JavaScript variables and `useState` for managing stateful data.

### **Example Code**
```jsx
import React from 'react';

function VariableDemo() {
  // String Variable
  const message = "Hello, React!";
  
  // Number Variable
  const number = 42;
  
  // Array Variable
  const fruits = ["Apple", "Banana", "Cherry"];
  
  // Object Variable
  const user = {
    name: "John Doe",
    age: 30,
    city: "New York"
  };
  
  // Boolean Variable
  const isReactAwesome = true;
  
  return (
    <div>
      <h2>Variable Demonstration in React</h2>
      <p>String: {message}</p>
      <p>Number: {number}</p>
      <p>Array: {fruits.join(", ")}</p>
      <p>Object: Name - {user.name}, Age - {user.age}, City - {user.city}</p>
      <p>Boolean: {isReactAwesome ? "Yes, React is awesome!" : "No, React is not cool."}</p>
    </div>
  );
}

export default VariableDemo;
```

---

## 3. **Explanation of the Code**
- **String Variable (`message`)**: Stores a simple text message.
- **Number Variable (`number`)**: Holds a numeric value.
- **Array Variable (`fruits`)**: Contains a list of strings and is displayed using `.join()` to format the output.
- **Object Variable (`user`)**: Stores multiple key-value pairs representing user data.
- **Boolean Variable (`isReactAwesome`)**: Used in a conditional expression to display different messages.

---

## 4. **Rendering in JSX**
- Variables are directly inserted inside JSX using `{}`.
- Arrays are displayed using `.join()` to format them as a string.
- Objects require dot notation (`user.name`) to access properties.
- Booleans can be used in conditional rendering using the ternary operator.

---

## 5. **Conclusion**
This example demonstrates how to declare and use different types of variables in a React functional component. Understanding how to work with variables is crucial for building dynamic user interfaces in React applications.

