
# 🌐 Node.js Basics Notes

---

## 📌 What is Node.js?
- Node.js is a **JavaScript runtime** built on Chrome’s V8 engine.  
- Lets you run JavaScript **outside the browser** (on servers).  
- Used for **APIs, web servers, and real-time applications**.  

---

## ⚡ Features of Node.js
- **Fast** → Powered by V8 engine.  
- **Asynchronous & Non-blocking** → Handles multiple requests without waiting.  
- **Event-driven** → Uses events & callbacks.  
- **Single-threaded** → Uses one main thread but handles many connections.  
- **Cross-platform** → Works on Windows, Linux, macOS.  

---

## 🛠️ Installation
1. Download Node.js from [nodejs.org](https://nodejs.org).  
2. Verify installation:  
   ```bash
   node -v
   npm -v
   ```

---

## 📂 Node.js Modules
- **Core Modules** → fs, http, path, os, events, etc.  
- **Local Modules** → Your own created modules.  
- **Third-party Modules** → Installed using `npm`.  

Example:  
```js
const fs = require("fs");
fs.writeFileSync("test.txt", "Hello Node.js");
```

---

## 🌍 Creating a Simple Server
```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello, Node.js!");
});

server.listen(3000, () => {
  console.log("Server running at http://localhost:3000");
});
```

---

## 📦 npm (Node Package Manager)
- Install a package:  
  ```bash
  npm install express
  ```
- Uninstall a package:  
  ```bash
  npm uninstall express
  ```
- Initialize project:  
  ```bash
  npm init -y
  ```

---

## 🔄 Event Loop in Node.js
- Handles asynchronous operations.  
- Uses **callbacks, promises, async/await**.  

Example:  
```js
setTimeout(() => {
  console.log("Hello after 2 seconds");
}, 2000);
```

---

## 🚀 Express.js Basics
```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Hello from Express!");
});

app.listen(5000, () => console.log("Server running on port 5000"));
```

---

## 📑 Summary
- Node.js = JavaScript runtime for server-side.  
- Uses **event-driven & non-blocking** architecture.  
- Works with **modules & npm**.  
- Commonly used with **Express.js** for web apps.  
