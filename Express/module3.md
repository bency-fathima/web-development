# 🧩 Middleware in Express.js

## 📘 Introduction
Middleware in **Express.js** are functions that execute during the **request-response cycle**. They have access to the **request (`req`)**, **response (`res`)**, and the **next middleware function** in the application’s request-response cycle.

Middleware is the **heart of Express.js**, allowing developers to:
- Modify request and response objects.
- Execute any code.
- End the request-response cycle.
- Call the next middleware in the stack.

---

## ⚙️ Basic Syntax

```js
app.use((req, res, next) => {
  console.log('Middleware executed!'); 
  next(); // passes control to the next middleware
});
```

---

## 🧭 Types of Middleware

### 1. **Application-Level Middleware**
These are bound to an instance of `express()` using `app.use()` or `app.METHOD()`.

```js
const express = require('express');
const app = express();

// Application-level middleware
app.use((req, res, next) => {
  console.log('Application-level middleware executed');
  next();
});


app.get('/', (req, res) => {
  res.send('Home Page');
});
```

---

### 2. **Router-Level Middleware**
Works exactly like application-level middleware, except it is bound to an instance of `express.Router()`.

```js
const express = require('express');
const router = express.Router();

router.use((req, res, next) => {
  console.log('Router-level middleware executed');
  next();
});

router.get('/users', (req, res) => {
  res.send('Users Page');
});

const app = express();
app.use('/api', router);
```

---

### 3. **Built-in Middleware**
Express comes with some **built-in middleware**:

| Middleware | Description |
|-------------|--------------|
| `express.json()` | Parses incoming JSON requests |
| `express.urlencoded()` | Parses URL-encoded data (form data) |
| `express.static()` | Serves static files (images, CSS, etc.) |

```js
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static('public'));
```

---

### 4. **Third-Party Middleware**
You can use npm packages as middleware to extend Express functionality.

**Examples:**
- `morgan` – for logging requests
- `cors` – to enable Cross-Origin Resource Sharing
- `helmet` – for securing HTTP headers

```js
const morgan = require('morgan');
const cors = require('cors');
const helmet = require('helmet');

app.use(morgan('tiny'));
app.use(cors());
app.use(helmet());
```

---

### 5. **Error-Handling Middleware**
Used to handle errors. It has **four parameters**: `(err, req, res, next)`.

```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something went wrong!');
});
```

> ⚠️ If you don’t call `next(err)`, Express will not recognize it as an error-handling middleware.

---

## 🧱 Execution Flow

When a request hits your server:
1. Express executes the middleware functions **in order**.
2. Each middleware can:
   - Modify `req` and `res`
   - End the request-response cycle
   - Pass control using `next()`

### Example:
```js
app.use((req, res, next) => {
  console.log('First middleware');
  next();
});

app.use((req, res, next) => {
  console.log('Second middleware');
  next();
});

app.get('/', (req, res) => {
  res.send('Hello World!');
});
```

**Output in console:**
```
First middleware
Second middleware
```

---

## 📦 Example Project Structure

```
middleware-demo/
│
├── server.js
├── routes/
│   └── userRoutes.js
└── middleware/
    ├── logger.js
    └── errorHandler.js
```

### logger.js
```js
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

module.exports = logger;
```

### errorHandler.js
```js
const errorHandler = (err, req, res, next) => {
  res.status(500).json({ message: err.message });
};

module.exports = errorHandler;
```

### server.js
```js
const express = require('express');
const logger = require('./middleware/logger');
const errorHandler = require('./middleware/errorHandler');

const app = express();
app.use(logger);

app.get('/', (req, res) => {
  res.send('Home Page');
});

app.use(errorHandler);

app.listen(3000, () => console.log('Server running on port 3000'));
```

---

## 🧠 Summary

| Type | Description | Example |
|------|--------------|----------|
| **Application-level** | Runs for every request in app | `app.use()` |
| **Router-level** | Runs only on a specific route | `router.use()` |
| **Built-in** | Provided by Express | `express.json()` |
| **Third-party** | Installed from npm | `morgan`, `cors` |
| **Error-handling** | Handles app errors | `(err, req, res, next)` |

---

## 💡 Best Practices

✅ Always use `express.json()` before routes that handle JSON data.  
✅ Place error-handling middleware **at the end** of all middleware.  
✅ Modularize middleware functions (keep them in a separate folder).  
✅ Use `next()` properly to prevent request hanging.  
✅ Use third-party middleware for common tasks (logging, security, etc.).

---

## 🏁 Conclusion

Middleware makes Express.js **powerful, modular, and customizable**.  
It allows developers to handle requests efficiently, log data, secure applications, and handle errors gracefully.

---
