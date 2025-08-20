# Lifting State Up in React

In React, **lifting state up** refers to moving the state from a child component to a common parent component so that multiple child components can share and synchronize the same state.

---

## Why Lift State Up?

- To share data between sibling components.
- To avoid duplication of state across components.
- To keep data consistent in the UI.

---

## Example: Without Lifting State Up

```jsx
function TemperatureInput() {
  const [temperature, setTemperature] = useState("");

  return (
    <div>
      <input 
        value={temperature} 
        onChange={(e) => setTemperature(e.target.value)} 
      />
      <p>{temperature}</p>
    </div>
  );
}
Here, if you had two inputs (Celsius and Fahrenheit), they would each maintain separate state, which would cause inconsistencies.

Example: With Lifting State Up
jsx
Copy
Edit
function TemperatureInput({ temperature, onTemperatureChange }) {
  return (
    <input 
      value={temperature} 
      onChange={(e) => onTemperatureChange(e.target.value)} 
    />
  );
}

function Calculator() {
  const [temperature, setTemperature] = useState("");

  return (
    <div>
      <TemperatureInput 
        temperature={temperature} 
        onTemperatureChange={setTemperature} 
      />
      <p>Temperature: {temperature}</p>
    </div>
  );
}
Here, the state is lifted to the Calculator component, making it the single source of truth.
Both inputs (if you had multiple) can now remain in sync.
