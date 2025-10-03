
# 📦 Node.js Modules (Detailed Notes)

---

## 🏷️ What are Modules in Node.js?
- A **module** is a reusable block of code whose existence does not accidentally impact other code.  
- Node.js has a **modular system** to organize code into separate files and reuse them.  
- Helps in **maintainability, scalability, and reusability** of code.

---

## 📂 Types of Modules in Node.js

### 1. Core Modules (Built-in)
- Provided by Node.js itself.  
- Can be imported directly without installation.  

**Examples:**
- `fs` → File System
- `http` → Server creation
- `path` → File paths
- `os` → System information
- `events` → Event handling  

**Example:**
```js
const fs = require("fs");

// Write file
fs.writeFileSync("hello.txt", "Hello Node.js");

// Read file
const data = fs.readFileSync("hello.txt", "utf-8");
console.log(data);
```

---

### 2. Local Modules (User-defined)
- Created by developers inside the project.  
- Exported using `module.exports` and imported using `require()`.  

**Example:**  
```js
// math.js
function add(a, b) {
  return a + b;
}
function subtract(a, b) {
  return a - b;
}
module.exports = { add, subtract };

// index.js
const math = require("./math");
console.log(math.add(5, 3));  // 8
console.log(math.subtract(10, 4)); // 6
```

---

### 3. Third-party Modules (via npm)
- Installed from npm (Node Package Manager).  
- Examples: `express`, `mongoose`, `lodash`.  

**Install a module:**  
```bash
npm install express
```

**Use it in code:**  
```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Hello from Express!");
});

app.listen(3000, () => console.log("Server running on port 3000"));
```

---

## 📥 Import & Export in Node.js

### CommonJS (Default in Node.js)
- Uses `require()` and `module.exports`.  

**Example:**  
```js
// utils.js
module.exports.sayHello = function() {
  return "Hello!";
}

// app.js
const utils = require("./utils");
console.log(utils.sayHello());
```

### ES Modules (ESM)
- Uses `import` and `export`.  
- Enable by adding `"type": "module"` in `package.json`.  

**Example:**  
```js
// math.mjs
export function multiply(a, b) {
  return a * b;
}

// index.mjs
import { multiply } from "./math.mjs";
console.log(multiply(4, 5)); // 20
```

---

## 🔄 Difference Between CommonJS & ES Modules

| Feature             | CommonJS          | ES Modules |
|---------------------|------------------|------------|
| Import Syntax       | `require()`       | `import`   |
| Export Syntax       | `module.exports`  | `export`   |
| File Extension      | `.js`             | `.mjs` (or `"type":"module"`) |
| Loading             | Synchronous       | Asynchronous |
| Default in Node.js  | ✅ Yes             | ❌ No (needs config) |

---

## 📑 Summary
- **Core modules** → Provided by Node.js.  
- **Local modules** → Created by developers.  
- **Third-party modules** → Installed using `npm`.  
- **CommonJS** is the default module system in Node.js.  
- **ES Modules** are modern and use `import/export`.  

---
