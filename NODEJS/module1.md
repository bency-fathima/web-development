🌐 Node.js Basics
📌 What is Node.js?

Node.js is a JavaScript runtime built on Chrome’s V8 engine.

Lets you run JavaScript outside the browser (on servers).

Used for APIs, web servers, real-time apps.

⚡ Features

Fast → Powered by V8 engine.

Asynchronous → Non-blocking I/O.

Single-threaded but handles many requests.

Cross-platform (Windows, Linux, Mac).

NPM → Huge package library.

✅ Advantages

Easy for JS developers.

Good for APIs and real-time apps.

Large community support.

❌ Limitations

Not best for CPU-heavy tasks (e.g., image processing).

Single-threaded → heavy tasks block execution.

🏗️ Node.js Architecture

Event Loop handles requests.

Non-blocking I/O for fast response.

Uses Worker Threads for heavy tasks.

⚙️ Install Node.js & NPM

Download from nodejs.org
.

Install → Choose LTS version.

Verify:

node -v
npm -v

🚀 First Node.js Program
Example 1: Hello World
// app.js
console.log("Hello, Node.js!");


Run:

node app.js

Example 2: Simple Server
// server.js
const http = require('http');

http.createServer((req, res) => {
  res.end("Hello World from Node.js");
}).listen(3000);

console.log("Server running at http://localhost:3000");
