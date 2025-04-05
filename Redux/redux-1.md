# 🔄 Redux: From Basics to Advanced

## 📘 What is Redux?
Redux is a **predictable state container** for JavaScript apps. It helps manage application state globally.

## 🔧 Why Use Redux?
- Centralized state management
- Easier debugging
- Time-travel debugging
- Works with any UI layer (React, Angular, etc.)

---

## 🧱 Core Concepts
1. **Store** – Holds the state.
2. **Actions** – Describe events.
3. **Reducers** – Pure functions that modify state.
4. **Dispatch** – Sends actions to the store.
5. **Selector** – Retrieves specific data from state.

---

## 🛠️ Installation
```bash
npm install redux react-redux
```

---

## 🎯 Basic Redux Flow (No React)

```js
const { createStore } = require('redux');

// Action
const increment = () => ({ type: 'INCREMENT' });

// Reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    default:
      return state;
  }
};

// Store
const store = createStore(counter);

store.subscribe(() => console.log(store.getState()));

store.dispatch(increment());
```

---

## ⚛️ Redux with React

### 1. Create a Redux Store
```js
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

export const store = configureStore({
  reducer: {
    counter: counterReducer
  }
});
```

### 2. Create a Slice
```js
// counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: state => { state.value += 1; },
    decrement: state => { state.value -= 1; },
    incrementByAmount: (state, action) => {
      state.value += action.payload;
    }
  }
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;
```

### 3. Provide Store to React
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import { store } from './store';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

### 4. Access State and Dispatch Actions
```js
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './counterSlice';

function Counter() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <button onClick={() => dispatch(decrement())}>-</button>
      <span>{count}</span>
      <button onClick={() => dispatch(increment())}>+</button>
    </div>
  );
}
```

---

## 📦 Async with Redux Toolkit (createAsyncThunk)

```js
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchData = createAsyncThunk('data/fetch', async () => {
  const response = await fetch('https://api.example.com/data');
  return await response.json();
});

const dataSlice = createSlice({
  name: 'data',
  initialState: { items: [], status: 'idle' },
  reducers: {},
  extraReducers: (builder) => {
    builder
      .addCase(fetchData.pending, (state) => { state.status = 'loading'; })
      .addCase(fetchData.fulfilled, (state, action) => {
        state.status = 'succeeded';
        state.items = action.payload;
      })
      .addCase(fetchData.rejected, (state) => { state.status = 'failed'; });
  }
});

export default dataSlice.reducer;
```

---

## 🔌 Redux Middleware

### Logger Example
```js
const logger = store => next => action => {
  console.log('Dispatching:', action);
  let result = next(action);
  console.log('Next state:', store.getState());
  return result;
};
```

---

## 🧰 Redux DevTools
- Install extension in browser
- Add to store:
```js
const store = configureStore({
  reducer: rootReducer,
  devTools: process.env.NODE_ENV !== 'production'
});
```

---

## 📚 Best Practices
- Keep state flat
- Normalize data
- Use slices
- Keep logic in reducers, not components
- Use Redux Toolkit to avoid boilerplate

---

## 🚀 Useful Libraries
- `redux-thunk` – for async actions
- `redux-saga` – side-effect model
- `reselect` – memoized selectors
- `immer` – immutable state updates

---

## 🧪 Testing Redux
```js
import reducer, { increment } from './counterSlice';

test('should handle initial state', () => {
  expect(reducer(undefined, {})).toEqual({ value: 0 });
});

test('should handle increment', () => {
  const previousState = { value: 0 };
  expect(reducer(previousState, increment())).toEqual({ value: 1 });
});
```

---

## ✅ Conclusion
Redux simplifies and organizes application state management, especially for large-scale applications. With Redux Toolkit, writing Redux logic has become easier, cleaner, and more efficient.

---

**Happy State Managing! 🎯**

