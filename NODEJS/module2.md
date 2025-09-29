# 🌐 Node.js Complete Notes (Beginner → Advanced)

---

## 📌 What is Node.js?
- Node.js is a **JavaScript runtime** built on Chrome’s V8 engine.  
- Lets you run JavaScript **outside the browser** (on servers).  
- Used for **APIs, web servers, and real-time applications**.  

---

## ⚡ Features
- **Fast** → Powered by V8 engine.  
- **Asynchronous** → Non-blocking I/O.  
- **Single-threaded** but can handle thousands of requests.  
- **Cross-platform** → Runs on Windows, Linux, Mac.  
- **NPM** → Largest open-source package ecosystem.  

---

## ✅ Advantages
- Easy to learn for JS developers.  
- Great for APIs and real-time apps.  
- Large community + strong ecosystem.  

### ❌ Limitations
- Not suitable for **CPU-heavy tasks** (e.g., ML, image processing).  
- Single-threaded → heavy tasks may block execution.  

---

## 🏗️ Node.js Architecture
- Based on **Single-threaded Event Loop**.  
- Handles **non-blocking I/O** requests efficiently.  
- Uses **Worker Threads** for CPU-intensive tasks.  

---

## ⚙️ Install Node.js & NPM
1. Download from [https://nodejs.org](https://nodejs.org).  
2. Install → Choose **LTS version**.  
3. Verify installation:
   ```bash
   node -v
   npm -v
🚀 First Node.js Program
Example 1: Hello World
js
Copy code
// app.js
console.log("Hello, Node.js!");
Run:

bash
Copy code
node app.js
Example 2: Simple Server
js
Copy code
// server.js
const http = require('http');

http.createServer((req, res) => {
  res.end("Hello World from Node.js");
}).listen(3000);

console.log("Server running at http://localhost:3000");
📘 Node.js Fundamentals
⚡ Node.js REPL
REPL = Read, Eval, Print, Loop

Built-in interactive shell for Node.js.

Used for quick testing and debugging.

Start REPL
bash
Copy code
node
REPL Example
bash
Copy code
> 2 + 3
5
> console.log("Hello")
Hello
undefined
REPL Commands
.help → show help

.exit → quit

.save file.js → save session

.load file.js → load file

📦 Node.js Modules
Modules = Reusable blocks of code.

Each file is a module in Node.js.

Types:

Built-in Modules → (http, fs, path, etc.)

Custom Modules → (your own code)

Third-party Modules → (installed via npm)

🔧 Built-in Modules
Some common built-in modules:

fs → File system

http → Create servers

os → System info

path → Work with file paths

events → Event handling

url → Parse URLs

Example: fs module
js
Copy code
const fs = require('fs');

// Write to file
fs.writeFileSync('data.txt', 'Hello Node');

// Read file
const data = fs.readFileSync('data.txt', 'utf8');
console.log(data);
✍️ Creating Custom Modules
Example: math.js
js
Copy code
function add(a, b) {
  return a + b;
}
function sub(a, b) {
  return a - b;
}

// Export
module.exports = { add, sub };
📥 Importing & Exporting
js
Copy code
const math = require('./math');

console.log(math.add(5, 3));  // 8
console.log(math.sub(10, 4)); // 6
module.exports → Export from a file.

require() → Import into another file.

📦 NPM (Node Package Manager)
Comes with Node.js by default.

Lets you install and manage dependencies.

Provides access to thousands of open-source packages.

Check NPM version
bash
Copy code
npm -v
📥 Installing Packages
Local Installation
bash
Copy code
npm install express
Installed in node_modules/ inside the project.

Saved in package.json dependencies.

Global Installation
bash
Copy code
npm install -g nodemon
Available system-wide.

Used for CLI tools.

📂 package.json
Project metadata + dependencies list.

Created using:

bash
Copy code
npm init -y
Example package.json
json
Copy code
{
  "name": "myapp",
  "version": "1.0.0",
  "description": "My first Node.js app",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
name → project name

scripts → run commands (npm start)

dependencies → required packages

devDependencies → only for development

📂 package-lock.json
Auto-generated file by npm.

Stores exact versions of installed dependencies.

Ensures same versions across environments.

Example
package.json → "express": "^4.18.0" (any 4.x version).

package-lock.json → "express": "4.18.2" (exact).

